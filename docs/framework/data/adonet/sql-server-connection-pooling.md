---
title: Połączenie z serwerem SQL buforowanie (ADO.NET)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e51d44e-7c4e-4040-9332-f0190fe36f07
ms.openlocfilehash: 78e852e2f1894f92e5b43228faedfad0d78981fa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33364480"
---
# <a name="sql-server-connection-pooling-adonet"></a>Połączenie z serwerem SQL buforowanie (ADO.NET)
Łączenie z serwerem bazy danych zazwyczaj składa się z kilku kroków czasochłonna. Kanału fizycznego, takie jak gniazda lub nazwanego potoku należy ustalić, musi nastąpić początkowego uzgadniania z serwerem, musi zostać przeanalizowany informacje o parametrach połączenia, połączenie musi zostać uwierzytelniony przez serwer, kontroli musi zostać uruchomione dla rejestrowanie w Bieżąca transakcja i tak dalej.  
  
 W praktyce większość aplikacji, należy użyć tylko jednej lub kilku różnych konfiguracji dla połączenia. Oznacza to, że podczas uruchamiania aplikacji i wiele połączeń identyczne będzie wielokrotnie otwierania i zamykania. Aby zminimalizować koszty otwarcia połączeń, [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] korzysta z techniki optymalizacji o nazwie *puli połączeń*.  
  
 Pula połączeń zmniejsza liczbę razy, które muszą być otwarte nowe połączenia. *Pulę* zachowuje własność fizycznego połączenia. Zarządza połączeń przy zachowaniu aktywności zestaw aktywnych połączeń dla każdej konfiguracji danego połączenia. Zawsze, gdy użytkownik wywołuje `Open` połączenia i pulę szuka dostępnych połączeń w puli. Jeśli w puli połączeń jest dostępny, zwraca go do obiektu wywołującego, zamiast Otwieranie nowego połączenia. Gdy aplikacja wywołuje `Close` połączenia i pulę zwraca go do puli zestawów aktywnych połączeń zamiast jego zamknięciem. Gdy połączenie jest zwracany do puli, po wykonaniu tych czynności można użyć ponownie przy następnym `Open` wywołania.  
  
 Tylko połączenia z taką samą konfigurację można puli. [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] zapewnia wiele pul w tym samym czasie, po jednej dla każdej konfiguracji. Połączenia są podzielone na pule przez ciąg połączenia i tożsamości systemu Windows, gdy jest używane zintegrowane zabezpieczenia. Połączenia są również puli według tego, czy są zarejestrowane w transakcji. Korzystając z <xref:System.Data.SqlClient.SqlConnection.ChangePassword%2A>, <xref:System.Data.SqlClient.SqlCredential> wystąpienie ma wpływ na puli połączeń. Różnych wystąpień <xref:System.Data.SqlClient.SqlCredential> użyje pule innego połączenia, nawet jeśli identyfikator użytkownika i hasło są takie same.  
  
 Tworzenie puli połączeń może znacznie zwiększyć wydajność i skalowalność aplikacji. Domyślnie buforowanie połączeń jest włączone w [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]. Chyba że jawnie wyłączyć ją, pulę optymalizuje połączenia otwarte i zamknięte w aplikacji. Może też podawać wiele modyfikatorów ciąg połączenia kontrolowanie zachowania buforowania połączeń. Aby uzyskać więcej informacji zobacz "Kontrolowanie połączenia buforowanie ze słowami kluczowymi parametrów połączenia" w dalszej części tego tematu.  
  
> [!NOTE]
>  Gdy buforowanie połączeń jest włączone, jeśli wystąpi błąd upływu limitu czasu lub inny błąd logowania, zostanie wygenerowany wyjątek i kolejne próby połączenia zakończy się niepowodzeniem dla następnego pięć sekund, "okresu blokowania". Jeśli aplikacja próbuje nawiązać połączenia w okresie blokowania, pierwszy wyjątek zostanie ponownie wygenerowany. Kolejne błędy po zakończeniu okresu blokowania spowoduje nowych okresów blokujące, które jest dwa razy tak długo, jak poprzedniego okresu blokowania maksymalnie jedną minutę.  
  
## <a name="pool-creation-and-assignment"></a>Tworzenie puli i przypisania  
 Przy pierwszym otwarciu połączenia, puli połączeń jest utworzony oparte na dokładne algorytm dopasowania, które kojarzy puli przy użyciu parametrów połączenia dla połączenia. Każdej puli połączeń jest skojarzony z ciągu połączenia distinct. Po otwarciu nowego połączenia, jeśli ciąg połączenia nie jest dokładnego dopasowania do istniejącej puli, jest tworzona nowa pula. Połączenia są grupowane w pulach jednego procesu, domena aplikacji, na ciąg połączenia i używane są zabezpieczenia zintegrowane na tożsamość systemu Windows. Parametry połączenia należy również dokładnego dopasowania; słowa kluczowe dostarczone w innej kolejności dla tego samego połączenia będzie można osobno puli.  
  
 W poniższym C# przykładzie trzy nowe <xref:System.Data.SqlClient.SqlConnection> obiekty są tworzone, ale tylko dwa pul połączeń są wymagane do zarządzania nimi. Należy pamiętać, że parametry połączenia pierwszego i drugiego różnią się wartość przypisana do `Initial Catalog`.  
  
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
  
 Jeśli `MinPoolSize` nie została określona w parametrach połączenia lub określone jako zero, połączeń w puli, które zostaną zamknięte po okresie braku aktywności. Jednak jeśli określonego `MinPoolSize` jest większa od zera, dopóki nie jest niszczony puli połączeń `AppDomain` zostanie zwolniona i kończy proces. Konserwacja pul nieaktywne lub jest pusty obejmuje koszty minimalny system.  
  
> [!NOTE]
>  Puli są automatycznie usuwane, gdy wystąpi błąd krytyczny, takie jak tryb failover.  
  
## <a name="adding-connections"></a>Dodawanie połączenia  
 Puli połączeń jest tworzona dla każdej parametry połączenia unikatowy. Po utworzeniu puli wielu obiektów połączenia są tworzone i dodawane do puli, dzięki czemu puli minimalny wymagany rozmiar jest spełniony. Połączenia są dodawane do puli, zgodnie z potrzebami, maksymalnie maksymalny rozmiar puli określony (wartość domyślna to 100). Połączenia są wydawane do puli, gdy są one zamknięty lub usunięty.  
  
 Gdy <xref:System.Data.SqlClient.SqlConnection> wymagany jest obiekt, są uzyskiwane z puli, jeśli jest dostępne połączenie można używać. Może być używany, połączenie musi używana, mają pasujących kontekst transakcji lub być nieskojarzone z żadnym kontekstem transakcji i mają prawidłowe łącze do serwera.  
  
 Pulę połączeń spełnia żądań połączeń przez ponowne przydzielanie połączeń po ich wydaniu do puli. Jeśli został osiągnięty maksymalny rozmiar puli i nie można używać połączenie nie jest dostępne, żądanie jest przechowywane w kolejce. Pulę próbuje odzyskać wszystkie połączenia, aż do osiągnięcia limitu czasu (wartość domyślna wynosi 15 sekund). Jeśli pulę nie może spełnić żądania, zanim upłynie limit czasu połączenia, jest zwracany wyjątek.  
  
> [!CAUTION]
>  Zdecydowanie zaleca się zawsze zamknąć połączenie po zakończeniu używa go, tak aby połączenie zostanie zwrócony do puli. Można to zrobić za pomocą `Close` lub `Dispose` metody `Connection` obiektu lub przez otwarcie wszystkich połączeń wewnątrz `using` instrukcji w języku C# lub `Using` instrukcji w języku Visual Basic. Połączenia, które nie są jawnie zamknięty, nie może dodać lub zwrócony do puli. Aby uzyskać więcej informacji, zobacz [za pomocą instrukcji](~/docs/csharp/language-reference/keywords/using-statement.md) lub [porady: usuwanie zasobu systemu](~/docs/visual-basic/programming-guide/language-features/control-flow/how-to-dispose-of-a-system-resource.md) dla języka Visual Basic.  
  
> [!NOTE]
>  Nie wywołuj `Close` lub `Dispose` na `Connection`, `DataReader`, lub innego obiektu zarządzanego w `Finalize` metody klasy. W finalizator zwolnić tylko niezarządzane zasoby, które bezpośrednio należą do klasy. Jeśli klasa nie ma żadnych niezarządzanych zasobów, nie dołączaj `Finalize` metody w definicji klasy. Aby uzyskać więcej informacji, zobacz [wyrzucanie elementów bezużytecznych](../../../../docs/standard/garbage-collection/index.md).  
  
> [!NOTE]
>  Zdarzenia logowania i wylogowywania nie zostanie wygenerowany na serwerze, gdy połączenie jest pobranych z lub zwrócony do puli połączeń. Jest tak, ponieważ połączenie nie jest w rzeczywistości zamknięte zwracanie do puli połączeń. Aby uzyskać więcej informacji, zobacz [klasa zdarzeń inspekcji logowania](http://msdn2.microsoft.com/library/ms190260.aspx) i [klasa zdarzeń inspekcji wylogowania](http://msdn2.microsoft.com/library/ms175827.aspx) w dokumentacji SQL Server — książki Online.  
  
## <a name="removing-connections"></a>Usuwanie połączenia  
 Pulę połączeń usuwa połączenie z puli, po był bezczynny około 4-8 minut lub jeśli pulę wykryje, że zostały Przerwano połączenie z serwerem. Należy pamiętać, że ODCIĘTA połączenia można wykryć tylko po próbie do komunikowania się z serwerem. Jeśli połączenie zostanie znaleziony, który nie jest już połączony z serwerem, jest oznaczony jako nieprawidłowy. Nieprawidłowy połączenia zostaną usunięte z puli połączeń, tylko wtedy, gdy są one zamknięte lub odzyskać.  
  
 Jeśli istnieje połączenie z serwerem nie zniknie, to połączenie można nakreślić z puli, nawet jeśli pulę połączeń nie wykryto połączenia ODCIĘTA i nie ona oznaczona jako niepoprawna. Jest to możliwe, ponieważ korzyści pulę powodując innego obiegu do serwera występuje wyeliminować koszty sprawdzanie, czy połączenie jest nadal ważny. W takiej sytuacji pierwsza próba połączenia z wykryje połączenia zostały oddzielone, czy jest zgłaszany wyjątek.  
  
## <a name="clearing-the-pool"></a>Wyczyszczenie puli  
 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 2.0 wprowadzono dwie nowe metody Wyczyść puli: <xref:System.Data.SqlClient.SqlConnection.ClearAllPools%2A> i <xref:System.Data.SqlClient.SqlConnection.ClearPool%2A>. `ClearAllPools` Czyści pul połączeń dla danego dostawcy i `ClearPool` czyści puli połączeń, który jest skojarzony z określonego połączenia. W przypadku połączeń używana w momencie wywołania one są odpowiednio oznaczone. Po zamknięciu, są ignorowane zamiast zwracanych do puli.  
  
## <a name="transaction-support"></a>Obsługa transakcji  
 Połączenia są pobierane z puli i przypisane transakcji na podstawie kontekstu. O ile `Enlist=false` określono w parametrach połączenia puli połączeń upewnia się, że połączenie jest zarejestrowane w <xref:System.Transactions.Transaction.Current%2A> kontekstu. Gdy połączenie jest zamknięte i zwrócony do puli z zarejestrowane `System.Transactions` transakcji, jest ustawiona Odłóż w taki sposób, że następne żądania dla tej puli połączeń z tym samym `System.Transactions` transakcji zwróci tego samego połączenia, jeśli jest dostępna. Jeśli takie żądania, a nie ma dostępnych żadnych puli połączeń, połączenie jest od nietransakcyjnej częścią puli i zarejestrowany. Jeśli żadne połączenia są dostępne w każdym obszarze puli, nowe połączenie jest tworzony i zarejestrowany.  
  
 Gdy połączenie jest zamknięte, zwolnieniu do puli, jak i w odpowiednich części, na podstawie jego kontekstu transakcji. W związku z tym można zamknąć połączenia bez wygenerowaniem błędu, nawet jeśli transakcja rozproszona jest nadal oczekujące. Dzięki temu można zatwierdzić lub przerwać transakcję rozproszoną później.  
  
## <a name="controlling-connection-pooling-with-connection-string-keywords"></a>Kontrolowanie użycia puli połączeń ze słowami kluczowymi parametrów połączenia  
 `ConnectionString` Właściwość <xref:System.Data.SqlClient.SqlConnection> obiekt obsługuje pary klucz wartość ciągu połączenia, które pozwalają dostosować zachowanie logiki buforowania połączeń. Aby uzyskać więcej informacji, zobacz <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
## <a name="pool-fragmentation"></a>Fragmentacja puli  
 Fragmentacja puli jest to powszechny problem w wiele aplikacji sieci Web, w której aplikacja może tworzyć wiele pul, które nie są zwalniane dopóki proces kończy się. Duża liczba połączeń to pozostawia otwarty i spójniejsze pamięci, co prowadzi do niskiej wydajności.  
  
### <a name="pool-fragmentation-due-to-integrated-security"></a>Fragmentacja puli z powodu zabezpieczeń zintegrowanych  
 Połączenia są grupowane w pulach zgodnie z parametrów połączenia i tożsamości użytkownika. W związku z tym użycie uwierzytelniania podstawowego lub uwierzytelniania systemu Windows w witrynie sieci Web i logowania zabezpieczeń zintegrowanych, Pobierz jedną pulę dla każdego użytkownika. Mimo że poprawia to wydajność żądań kolejnych bazy danych dla jednego użytkownika, ten użytkownik nie może korzystać z połączenia nawiązywane przez innych użytkowników. Powoduje ona również co najmniej jednego połączenia na użytkownika na serwerze bazy danych. To jest efektem ubocznym określonej architektury aplikacji sieci Web, który deweloperzy należy porównać przed inspekcji wymagania dotyczące zabezpieczeń i.  
  
### <a name="pool-fragmentation-due-to-many-databases"></a>Fragmentacja puli z powodu wielu baz danych  
 Usługodawcy internetowi obsługiwać kilka witryn sieci Web na jednym serwerze. Aby potwierdzić logowania uwierzytelniania formularzy, a następnie otworzyć połączenia z określoną bazą danych dla tego użytkownika lub grupy użytkowników mogą używać pojedynczej bazy danych. Połączenie z bazą danych uwierzytelniania jest buforowany i korzystanie z niej. Istnieje jednak oddzielne puli połączeń dla każdej bazy danych, które zwiększyć liczbę połączeń z serwerem.  
  
 Dotyczy to również efekt uboczny projektowania aplikacji. Istnieje stosunkowo proste sposób, aby uniknąć tego efektu ubocznego bez naruszania zabezpieczeń podczas łączenia z programem SQL Server. Zamiast połączenie z oddzielnej bazy danych dla każdego użytkownika lub grupy, nawiązać połączenia z tej samej bazy danych na serwerze, a następnie wykonaj [!INCLUDE[tsql](../../../../includes/tsql-md.md)] użycie instrukcji, aby zmienić żądanej bazy danych. Poniższy fragment kodu pokazano tworzenie początkowego połączenia `master` bazy danych, a następnie przechodząc do żądanej bazy danych określonej w `databaseName` zmiennej ciągu.  
  
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
  
## <a name="application-roles-and-connection-pooling"></a>Role aplikacji i użycia puli połączeń  
 Po programu SQL Server roli aplikacji został aktywowany przez wywołanie metody `sp_setapprole` procedury składowanej systemu, nie można zresetować to połączenie w kontekście zabezpieczeń. Jednak jeśli buforowanie jest włączone, połączenie jest zwracana do puli, a błąd występuje, gdy zostanie ponownie użyty puli połączeń. Aby uzyskać więcej informacji, zobacz artykuł bazy wiedzy, "[błędów roli aplikacji SQL z puli zasobów OLE DB](http://support.microsoft.com/default.aspx?scid=KB;EN-US;Q229564)."  
  
### <a name="application-role-alternatives"></a>Alternatywy roli aplikacji  
 Zaleca się, że możesz korzystać z mechanizmów zabezpieczeń korzystających zamiast ról aplikacji. Aby uzyskać więcej informacji, zobacz [tworzenia ról aplikacji w programie SQL Server](../../../../docs/framework/data/adonet/sql/creating-application-roles-in-sql-server.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Pula połączeń](../../../../docs/framework/data/adonet/connection-pooling.md)  
 [SQL Server i ADO.NET](../../../../docs/framework/data/adonet/sql/index.md)  
 [Liczniki wydajności](../../../../docs/framework/data/adonet/performance-counters.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
