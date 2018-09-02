---
title: Połączenie z serwerem SQL buforowanie (ADO.NET)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e51d44e-7c4e-4040-9332-f0190fe36f07
ms.openlocfilehash: f416ae8252d9991905da7eeaf4ce6398ff0e7461
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43406499"
---
# <a name="sql-server-connection-pooling-adonet"></a>Połączenie z serwerem SQL buforowanie (ADO.NET)
Nawiązywanie połączenia z serwerem bazy danych zazwyczaj składa się z kilku kroków czasochłonne. Kanał fizycznych, takich jak gniazda lub nazwany potok należy ustalić, musi nastąpić uzgadnianie początkową z serwerem, informacje o parametrach połączenia musi zostać przeanalizowany, połączenie musi zostać uwierzytelniony przez serwer, należy uruchomić testy dla rejestrowanie w Bieżąca transakcja i tak dalej.  
  
 W praktyce większość aplikacji używa tylko jednej lub kilku różnych konfiguracji dla połączenia. Oznacza to, że podczas wykonywania aplikacji wiele połączeń identyczne będzie wielokrotnie otwierania i zamykania. Aby zminimalizować koszty otwarcia połączeń, [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] wykorzystuje technikę optymalizacji o nazwie *buforowanie połączeń*.  
  
 Pula połączeń zmniejsza liczbę razy, które muszą być otwarte nowe połączenia. *Pulę* zachowuje własność połączenie fizyczne. Zarządza połączeń przechowując aktywny zestaw aktywnych połączeń dla każdej konfiguracji danego połączenia. Zawsze, gdy użytkownik wywołuje `Open` połączenia, pulę szuka dostępnych połączeń w puli. Jeśli w puli połączeń jest dostępny, zwraca go do obiektu wywołującego, zamiast otwierać nowe połączenie. Gdy aplikacja wywołuje `Close` w ramach połączenia pulę zwraca go do puli zestawów aktywnych połączeń, a nie jej zamknięciem. Gdy połączenie jest zwracany do puli, jest gotowy do można użyć ponownie w następnym `Open` wywołania.  
  
 Tylko na połączenia z taką samą konfigurację można puli. [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] zapewnia kilka pul w tym samym czasie, jedną dla każdej konfiguracji. Połączenia są podzielone na pule przy użyciu parametrów połączenia, a także przez tożsamość w Windows stosowania zintegrowanych zabezpieczeń. Połączenia są również grupowane w pulach w oparciu czy biorących udział w transakcji. Korzystając z <xref:System.Data.SqlClient.SqlConnection.ChangePassword%2A>, <xref:System.Data.SqlClient.SqlCredential> wystąpienia ma wpływ na puli połączeń. Różne wystąpienia <xref:System.Data.SqlClient.SqlCredential> użyje pule inne połączenie, nawet jeśli identyfikator użytkownika i hasło są takie same.  
  
 Tworzenie puli połączeń mogą znacznie poprawić wydajność i skalowalność aplikacji. Domyślnie, połączenie jest włączone buforowanie w [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]. Chyba że jawnie wyłączyć ją, pulę optymalizuje połączenia, ponieważ są otwarte i zamknięte w aplikacji. Można też podać kilka modyfikatorów parametrów połączenia do sterowania zachowaniem buforowania połączeń. Aby uzyskać więcej informacji zobacz "Kontrolowanie połączenia puli za pomocą połączenia ciągu słowa kluczowe" w dalszej części tego tematu.  
  
> [!NOTE]
>  Gdy jest włączone buforowanie połączeń, a jeśli wystąpi błąd upływu limitu czasu lub inny błąd logowania, zostanie zgłoszony wyjątek i kolejnych próbach połączenia zakończy się niepowodzeniem dla następnego pięć sekund, "okres blokowanie". Jeśli aplikacja próbuje nawiązać połączenie przed upływem blokowania, pierwszy wyjątek zostanie zgłoszony ponownie. Kolejne błędy po upływie okresu blokowania spowoduje nowych okresów blokujące, które jest dwa razy tak długo, jak w poprzednim okresie blokowania, maksymalnie do jednej minuty.  
  
## <a name="pool-creation-and-assignment"></a>Tworzenie puli i przypisanie  
 Przy pierwszym otwarciu połączenia, puli połączeń jest oparta na dokładne algorytm dopasowania, które kojarzy puli przy użyciu parametrów połączenia w połączeniu. Każdej puli połączeń jest skojarzony z parametrami połączenia distinct. Po otwarciu nowego połączenia, jeśli parametry połączenia nie jest dokładnie dopasowany do istniejącej puli, tworzona jest nowa pula. Połączenia są grupowane w pulach na proces w każdej domenie aplikacji, na parametry połączenia i używane są zabezpieczenia zintegrowane na Windows identity. Parametry połączenia muszą również być dokładnym dopasowaniem; słowa kluczowe w innej kolejności dla tego samego połączenia będą puli oddzielnie.  
  
 W języku C# przykładzie trzy nowe <xref:System.Data.SqlClient.SqlConnection> obiekty są tworzone, ale tylko dwóch pul połączeń są wymagane do zarządzania nimi. Należy pamiętać, że parametry połączenia pierwszego i drugiego różnią się wartość przypisana do `Initial Catalog`.  
  
```  
using (SqlConnection connection = new SqlConnection(  
  "Integrated Security=SSPI;Initial Catalog=Northwind"))  
    {  
        connection.Open();        
        // Pool A is created.  
    }  
  
using (SqlConnection connection = new SqlConnection(  
  "Integrated Security=SSPI;Initial Catalog=pubs"))  
    {  
        connection.Open();        
        // Pool B is created because the connection strings differ.  
    }  
  
using (SqlConnection connection = new SqlConnection(  
  "Integrated Security=SSPI;Initial Catalog=Northwind"))  
    {  
        connection.Open();        
        // The connection string matches pool A.  
    }  
```  
  
 Jeśli `MinPoolSize` nie została określona w parametrach połączenia lub określone jako zero, połączeń w puli zostaną zamknięte po okresie braku aktywności. Jednakże jeśli określony `MinPoolSize` jest większa od zera, puli połączeń nie jest niszczony, aż do `AppDomain` jest zwalniana i kończy proces. Konserwacja pule nieaktywne lub jest pusty obejmuje koszty minimalny system.  
  
> [!NOTE]
>  Puli są automatycznie usuwane, gdy wystąpi błąd krytyczny, takich jak przejścia w tryb failover.  
  
## <a name="adding-connections"></a>Dodawanie połączeń  
 Puli połączeń jest tworzony dla każdego ciągu unikatowego połączenia. Po utworzeniu puli wielu obiektów połączeń są tworzone i dodawane do puli, dzięki czemu puli minimalny wymagany rozmiar jest spełniony. Połączenia są dodawane do puli zgodnie z potrzebami, maksymalnie maksymalny rozmiar puli określony (wartość domyślna to 100). Połączenia są wydawane do puli, gdy są one zamknięte lub usunięty.  
  
 Gdy <xref:System.Data.SqlClient.SqlConnection> Zażądano obiektu, jest uzyskiwana z puli, jeśli można używać połączenia jest dostępny. Może być używany, połączenie musi być nieużywane, mają pasujących kontekstu transakcji lub być nieskojarzone z żadnym z kontekstem transakcji i mają prawidłowe łącze do serwera.  
  
 Pulę połączeń spełnia żądań dla połączeń przez ponowne przydzielanie połączenia po ich wydaniu do puli. Jeśli osiągnięty maksymalny rozmiar puli, a nie można używać połączenia jest dostępna, żądanie znajduje się w kolejce. Pulę następnie próbuje odzyskać wszystkie połączenia, dopóki nie zostanie osiągnięty limit czasu (wartość domyślna wynosi 15 sekund). Jeśli pulę nie może zrealizować żądanie, zanim upłynie limit czasu połączenia, zwracany jest wyjątek.  
  
> [!CAUTION]
>  Zdecydowanie zaleca się zawsze zamykaj połączenie po zakończeniu korzystania z niego, tak aby połączenie zostanie zwrócony do puli. Można to zrobić za pomocą `Close` lub `Dispose` metody `Connection` obiektu lub otwierając wszystkich połączeń wewnątrz `using` instrukcji w języku C# lub `Using` instrukcji w języku Visual Basic. Połączenia, które nie są jawnie zamknięty, nie może dodać lub zwrócone do puli. Aby uzyskać więcej informacji, zobacz [za pomocą instrukcji](~/docs/csharp/language-reference/keywords/using-statement.md) lub [porady: usuwanie zasobu systemu](~/docs/visual-basic/programming-guide/language-features/control-flow/how-to-dispose-of-a-system-resource.md) dla języka Visual Basic.  
  
> [!NOTE]
>  Nie wywołuj `Close` lub `Dispose` na `Connection`, `DataReader`, lub inne obiekt zarządzany w `Finalize` metody klasy. W finalizatora zwolnić tylko niezarządzane zasoby, które należą bezpośrednio do swojej klasy. Jeśli klasa nie ma żadnych niezarządzanych zasobów, nie dołączaj `Finalize` metody w swojej definicji klasy. Aby uzyskać więcej informacji, zobacz [wyrzucania elementów bezużytecznych](../../../../docs/standard/garbage-collection/index.md).  
  
Aby uzyskać więcej informacji na temat zdarzeń powiązanych ze otwierające i zamykające połączeń, zobacz [klasa zdarzenia logowania inspekcji](/sql/relational-databases/event-classes/audit-login-event-class) i [klasa zdarzenia wylogowania inspekcji](/sql/relational-databases/event-classes/audit-logout-event-class) w dokumentacji programu SQL Server.  
  
## <a name="removing-connections"></a>Usuwanie połączeń  
 Pulę połączeń usuwa połączenie z puli, po była bezczynna przez około 4 – 8 minut lub pulę wykryje, że zostały oddzielone połączenia z serwerem. Należy pamiętać, że ODCIĘTA połączenia można wykryć tylko po próby komunikacji z serwerem. Jeśli połączenie zostanie znaleziony, który nie jest już połączony z serwerem, jest oznaczona jako niepoprawna. Nieprawidłowy połączeń są usuwane z puli połączeń, tylko wtedy, gdy są one zamknięte lub odzyskać.  
  
 Jeśli połączenie istnieje na serwerze, na którym nie zniknie, to połączenie może być pobierana z puli, nawet jeśli nie wykryto połączenia ODCIĘTA i ona oznaczona jako niepoprawna pulę połączeń. Jest to wymagane, ponieważ obciążenie sprawdzania, czy połączenie jest nadal ważny wyeliminować korzyści pulę, powodując innej komunikacji dwustronnej z serwerem występuje. W takiej sytuacji pierwsza próba połączenia z wykryje, że połączenia zostały oddzielone, i zgłaszany jest wyjątek.  
  
## <a name="clearing-the-pool"></a>Czyszczenie puli  
 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] w wersji 2.0 wprowadzono dwie nowe metody, aby wyczyścić puli: <xref:System.Data.SqlClient.SqlConnection.ClearAllPools%2A> i <xref:System.Data.SqlClient.SqlConnection.ClearPool%2A>. `ClearAllPools` Czyści pul połączeń dla danego dostawcy i `ClearPool` czyści puli połączeń, który jest skojarzony z określonego połączenia. W przypadku połączenia używane w momencie zgłoszenia wywołania zostały odpowiednio oznaczone. Po zamknięciu, są ignorowane zamiast zwracane do puli.  
  
## <a name="transaction-support"></a>Obsługa transakcji  
 Połączenia są pobierane z puli i przypisane transakcji na podstawie kontekstu. Chyba że `Enlist=false` określono w parametrach połączenia puli połączeń upewnia się, że połączenie jest zarejestrowany w <xref:System.Transactions.Transaction.Current%2A> kontekstu. Po zamknięciu i zwrócone do puli za pomocą zobowiązaniom połączenie `System.Transactions` transakcji, jego została odłożona w taki sposób, że następne żądania dla tej puli połączeń o takiej samej `System.Transactions` transakcji zwróci tego samego połączenia, jeśli jest ona dostępna. Jeśli takie żądanie zostało wydane, a brak puli połączeń, połączenie jest rysowana od składnika nietransakcyjnego puli i zarejestrowany. Jeśli w dowolnym z tych obszarów puli dostępnych żadnych połączeń, nowe połączenie jest utworzony i zarejestrowany.  
  
 Gdy połączenie jest zamknięte, jest on zwalniany powrót do puli i odpowiednie części pola na podstawie jego kontekstu transakcji. W związku z tym, można zamknąć połączenia nie generuje błąd, mimo że transakcja rozproszona jest nadal oczekujące. Dzięki temu można zatwierdzić lub przerwać transakcję rozproszoną później.  
  
## <a name="controlling-connection-pooling-with-connection-string-keywords"></a>Kontrolowanie buforowania połączeń ze słowami kluczowymi ciąg połączenia  
 `ConnectionString` Właściwość <xref:System.Data.SqlClient.SqlConnection> obiekt obsługuje pary klucz/wartość ciągu połączenia, których można użyć, aby dostosować zachowanie buforowania logiki połączeń. Aby uzyskać więcej informacji, zobacz <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
## <a name="pool-fragmentation"></a>Fragmentacja puli  
 Fragmentacja puli jest to powszechny problem w wielu aplikacjach sieci Web, w której aplikacja może tworzyć dużej liczby pul, które nie są zwalniane, dopóki nie kończy procesu. Spowoduje to pozostawienie dużą liczbę połączeń otwartych i korzystanie z nich pamięci, co powoduje spadek wydajności.  
  
### <a name="pool-fragmentation-due-to-integrated-security"></a>Fragmentacja puli ze względu na zabezpieczenia zintegrowane  
 Połączenia są grupowane w pulach zgodnie z parametrów połączenia, a także tożsamości użytkownika. W związku z tym Jeśli używasz uwierzytelniania podstawowego lub uwierzytelniania Windows w witrynie sieci Web i identyfikator logowania zintegrowanych zabezpieczeń, otrzymasz jedną pulę dla każdego użytkownika. Mimo że poprawia to wydajność bazy danych w kolejnych żądań dla pojedynczego użytkownika, ten użytkownik nie mogą korzystać z połączenia nawiązywane przez innych użytkowników. Powoduje ona również co najmniej jedno połączenie na użytkownika na serwerze bazy danych. To jest efektem szczególna Architektura aplikacji sieci Web, który deweloperzy należy porównać względem zabezpieczeń i wymogów dotyczących audytu.  
  
### <a name="pool-fragmentation-due-to-many-databases"></a>Fragmentacja puli z powodu wielu baz danych  
 Usługodawcy internetowi hostować wiele witryn sieci Web na jednym serwerze. Aby potwierdzić logowania uwierzytelniania formularzy, a następnie otworzyć połączenia z określoną bazą danych dla tego użytkownika lub grupy użytkowników mogą używać jednej bazy danych. Połączenie z bazą danych uwierzytelniania jest puli i używana przez wszystkich użytkowników. Jednak jest oddzielną pulę połączeń dla każdej bazy danych, które zwiększają liczbę połączeń serwera.  
  
 Dotyczy to również efekt uboczny projektowania aplikacji. Istnieje stosunkowo prosty sposób, aby uniknąć tego efektu bez uszczerbku dla zabezpieczeń podczas nawiązywania połączenia programu SQL Server. Zamiast nawiązywania połączenia z oddzielnej bazy danych dla każdego użytkownika lub grupy, należy nawiązać połączenie z tej samej bazy danych na serwerze, a następnie wykonaj [!INCLUDE[tsql](../../../../includes/tsql-md.md)] użycie instrukcji, aby przejść do żądanej bazy danych. Poniższy fragment kodu przedstawia tworzenie początkowego połączenia `master` bazy danych, a następnie przechodząc do żądanego bazą danych określoną w `databaseName` zmiennej ciągu.  
  
```vb  
' Assumes that command is a valid SqlCommand object and that  
' connectionString connects to master.  
    command.Text = "USE DatabaseName"  
Using connection As New SqlConnection(connectionString)  
    connection.Open()  
    command.ExecuteNonQuery()  
End Using  
```  
  
```csharp  
// Assumes that command is a SqlCommand object and that  
// connectionString connects to master.  
command.Text = "USE DatabaseName";  
using (SqlConnection connection = new SqlConnection(  
  connectionString))  
  {  
    connection.Open();  
    command.ExecuteNonQuery();  
  }  
```  
  
## <a name="application-roles-and-connection-pooling"></a>Role aplikacji i pule połączeń  
 Po programu SQL Server został aktywowany roli aplikacji, wywołując `sp_setapprole` systemowej procedury składowanej, nie można zresetować w kontekście zabezpieczeń tego połączenia. Jednak jeśli włączone jest buforowanie, połączenie jest zwracany do puli i występuje błąd podczas połączenia z puli zostanie ponownie użyty. Aby uzyskać więcej informacji, zobacz artykuł bazy wiedzy, "[błędów roli aplikacji SQL z puli zasobów OLE DB](https://support.microsoft.com/default.aspx?scid=KB;EN-US;Q229564)."  
  
### <a name="application-role-alternatives"></a>Alternatywy ról aplikacji  
 Zaleca się, że możesz korzystać z mechanizmami zabezpieczeń, które można użyć zamiast ról aplikacji. Aby uzyskać więcej informacji, zobacz [tworzenie ról aplikacji w programie SQL Server](../../../../docs/framework/data/adonet/sql/creating-application-roles-in-sql-server.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Pula połączeń](../../../../docs/framework/data/adonet/connection-pooling.md)  
 [SQL Server i ADO.NET](../../../../docs/framework/data/adonet/sql/index.md)  
 [Liczniki wydajności](../../../../docs/framework/data/adonet/performance-counters.md)  
 [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
