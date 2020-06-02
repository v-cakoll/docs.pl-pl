---
title: SQL Server puli połączeń
description: Dowiedz się, w jaki sposób ADO.NET minimalizuje koszt otwierania połączeń przy użyciu puli połączeń SQL Server, co zmniejsza obciążenie dla nowych połączeń.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e51d44e-7c4e-4040-9332-f0190fe36f07
ms.openlocfilehash: 1a95aab9e09d69a3d26b3404d4cb2b70371a3fe8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286562"
---
# <a name="sql-server-connection-pooling-adonet"></a>Buforowanie połączenia z programem SQL Server (ADO.NET)
Połączenie z serwerem bazy danych zwykle składa się z kilku czasochłonnych kroków. Musi zostać ustanowiony kanał fizyczny, taki jak gniazdo lub nazwany potok, początkowe uzgadnianie z serwerem, muszą zostać przeanalizowane informacje o parametrach połączenia, połączenie musi być uwierzytelniane przez serwer, podczas gdy w bieżącej transakcji i tak dalej należy uruchomić testy.  
  
 W tym przypadku większość aplikacji używa tylko jednej lub kilku różnych konfiguracji dla połączeń. Oznacza to, że podczas wykonywania aplikacji wiele identycznych połączeń zostanie wielokrotnie otwarte i zamknięte. Aby zminimalizować koszt otwarcia połączeń, ADO.NET korzysta z techniki optymalizacji zwanej *pulą połączeń*.  
  
 Buforowanie połączeń zmniejsza liczbę przypadków otwarcia nowych połączeń. *Pulę* utrzymuje własność połączenia fizycznego. Zarządza on połączeniami przez utrzymywanie zestawu aktywnych połączeń dla każdej danej konfiguracji połączenia. Za każdym razem, gdy użytkownik wywołuje `Open` połączenie, pulę szuka dostępnego połączenia w puli. Jeśli połączenie z pulą jest dostępne, zwraca je do obiektu wywołującego, zamiast otwierać nowe połączenie. Gdy aplikacja wywołuje `Close` połączenie, pulę zwraca go do zestawu aktywnych połączeń w puli, zamiast go zamknąć. Gdy połączenie zostanie zwrócone do puli, jest gotowe do ponownego użycia przy następnym `Open` wywołaniu.  
  
 Tylko połączenia z tą samą konfiguracją mogą być w puli. ADO.NET przechowuje kilka pul w tym samym czasie, po jednej dla każdej konfiguracji. Połączenia są rozdzielone na pule przez parametry połączenia oraz przez tożsamość systemu Windows, gdy są używane zintegrowane zabezpieczenia. Połączenia są również w puli zależnie od tego, czy są one zarejestrowane w transakcji. W przypadku korzystania <xref:System.Data.SqlClient.SqlConnection.ChangePassword%2A> z programu <xref:System.Data.SqlClient.SqlCredential> wystąpienie ma wpływ na pulę połączeń. Różne wystąpienia <xref:System.Data.SqlClient.SqlCredential> będą korzystać z różnych pul połączeń, nawet jeśli identyfikator użytkownika i hasło są takie same.  
  
 Połączenia w puli mogą znacząco zwiększyć wydajność i skalowalność aplikacji. Domyślnie pule połączeń są włączone w ADO.NET. O ile nie zostanie on jawnie wyłączony, pulę optymalizuje połączenia w miarę ich otwierania i zamykania w aplikacji. Możesz również podać kilka modyfikatorów parametrów połączenia, aby kontrolować zachowanie puli połączeń. Aby uzyskać więcej informacji, zobacz "kontrolowanie puli połączeń ze słowami kluczowymi parametrów połączenia" w dalszej części tego tematu.  
  
> [!NOTE]
> Po włączeniu puli połączeń, jeśli wystąpi błąd limitu czasu lub inny błąd logowania, zostanie zgłoszony wyjątek, a kolejne próby połączenia będą kończyć się niepowodzeniem przez kolejne pięć sekund, "okres blokowania". Jeśli aplikacja próbuje nawiązać połączenie w okresie blokowania, zostanie zgłoszony pierwszy wyjątek. Kolejne błędy po zakończeniu okresu blokowania spowodują nowe okresy blokowania, które są dwa razy większe niż w poprzednim okresie blokowania, maksymalnie do minuty.  
  
## <a name="pool-creation-and-assignment"></a>Tworzenie i przypisywanie puli  
 Po pierwszym otwarciu połączenia tworzona jest pula połączeń oparta na dokładnie zgodnym algorytmie, który kojarzy pulę z parametrami połączenia w połączeniu. Każda pula połączeń jest skojarzona z unikatowymi parametrami połączenia. W przypadku otwarcia nowego połączenia, jeśli parametry połączenia nie są dokładnie zgodne z istniejącą pulą, tworzona jest nowa pula. Połączenia są w puli według poszczególnych procesów, poszczególnych domen aplikacji, na parametry połączenia oraz w przypadku użycia zintegrowanych zabezpieczeń na tożsamość systemu Windows. Parametry połączenia muszą być również dokładnymi dopasowaniami; Słowa kluczowe podane w innej kolejności dla tego samego połączenia będą dzielone osobno.  
  
 W poniższym przykładzie w języku C# <xref:System.Data.SqlClient.SqlConnection> tworzone są trzy nowe obiekty, ale zarządzanie nimi wymaga tylko dwóch pul połączeń. Należy zauważyć, że pierwsze i drugie parametry połączenia różnią się wartością przypisaną dla `Initial Catalog` .  
  
```csharp
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
  
 Jeśli `MinPoolSize` nie jest określony w parametrach połączenia lub jest określony jako zero, połączenia w puli zostaną zamknięte po okresie braku aktywności. Jeśli jednak wartość określona `MinPoolSize` jest większa od zera, pula połączeń nie zostanie zniszczona, dopóki nie `AppDomain` zostanie zwolnione, a proces zakończy się. Obsługa pul nieaktywnych lub pustych obejmuje minimalne obciążenie systemu.  
  
> [!NOTE]
> Pula jest automatycznie czyszczona po wystąpieniu błędu krytycznego, na przykład w trybie failover.  
  
## <a name="adding-connections"></a>Dodawanie połączeń  
 Pula połączeń jest tworzona dla każdego unikatowego ciągu połączenia. Po utworzeniu puli do puli są tworzone i dodawane wiele obiektów połączeń, aby zapewnić spełnienie minimalnych wymagań dotyczących rozmiaru puli. Połączenia są dodawane do puli, w razie potrzeby, do maksymalnego określonego rozmiaru puli (100 jest domyślnie). Połączenia są zwalniane z powrotem do puli, gdy są zamknięte lub usuwane.  
  
 Po <xref:System.Data.SqlClient.SqlConnection> zażądaniu obiektu jest on uzyskiwany z puli, jeśli dostępne jest połączenie użyteczne. Aby można było korzystać z usługi, połączenie musi być nieużywane, mieć pasujący kontekst transakcji lub być nieskojarzone z dowolnym kontekstem transakcji i mieć prawidłowe połączenie z serwerem.  
  
 Połączenie pulę spełnia żądania połączeń przez ponowne przypisanie połączeń po ich ponownym wydaniu do puli. Jeśli maksymalny rozmiar puli został osiągnięty i nie jest dostępne żadne możliwe połączenie, żądanie jest umieszczane w kolejce. Pulę próbuje odnowić wszelkie połączenia do momentu osiągnięcia limitu czasu (wartość domyślna to 15 sekund). Jeśli pulę nie może spełnić żądania przed upływem limitu czasu połączenia, zostanie zgłoszony wyjątek.  
  
> [!CAUTION]
> Zdecydowanie zalecamy, aby zawsze zamykać połączenie po zakończeniu korzystania z niego, aby połączenie zostało zwrócone do puli. Można to zrobić przy użyciu albo `Close` metod lub `Dispose` `Connection` przez otwarcie wszystkich połączeń wewnątrz `using` instrukcji w języku C# lub `Using` instrukcji w Visual Basic. Połączenia, które nie zostały jawnie zamknięte, mogą nie zostać dodane lub zwrócone do puli. Aby uzyskać więcej informacji, zobacz [using instrukcji](../../../csharp/language-reference/keywords/using-statement.md) lub [How to: Dispose a Resource system](../../../visual-basic/programming-guide/language-features/control-flow/how-to-dispose-of-a-system-resource.md) for Visual Basic.  
  
> [!NOTE]
> Nie wywołuj `Close` ani `Dispose` w `Connection` , a `DataReader` , ani żadnego innego obiektu zarządzanego w `Finalize` metodzie klasy. W finalizatorze zwalniane są tylko niezarządzane zasoby, które są własnością klasy bezpośrednio. Jeśli Klasa nie jest własnością żadnych niezarządzanych zasobów, nie Uwzględniaj `Finalize` metody w definicji klasy. Aby uzyskać więcej informacji, zobacz [odzyskiwanie pamięci](../../../standard/garbage-collection/index.md).  
  
Aby uzyskać więcej informacji na temat zdarzeń skojarzonych z otwieraniem i zamykaniem połączeń, zobacz [Inspekcja klas zdarzeń logowania](/sql/relational-databases/event-classes/audit-login-event-class) i [zdarzeń inspekcji](/sql/relational-databases/event-classes/audit-logout-event-class) w dokumentacji SQL Server.  
  
## <a name="removing-connections"></a>Usuwanie połączeń  
 Pulę połączenia usuwa połączenie z puli, gdy było ono bezczynne przez około 4-8 minut, lub jeśli pulę wykryje, że połączenie z serwerem zostało odłączone. Należy zauważyć, że pociągnięcie może być wykrywane tylko po próbie nawiązania połączenia z serwerem. Jeśli zostanie znalezione połączenie, które nie jest już połączone z serwerem, jest oznaczone jako nieprawidłowe. Nieprawidłowe połączenia są usuwane z puli połączeń tylko wtedy, gdy są zamknięte lub odzyskiwane.  
  
 Jeśli połączenie istnieje na serwerze, który został wyświetlony, to połączenie może być narysowane z puli, nawet jeśli połączenie pulę nie wykryło poprawnego połączenia i oznaczenie go jako nieprawidłowe. Dzieje się tak, ponieważ obciążenie związane z sprawdzeniem, czy połączenie jest nadal ważne, eliminuje korzyści płynące z pulę, powodując wystąpienie kolejnej podróży z serwerem. W takim przypadku pierwsza próba użycia połączenia wykryje, że połączenie zostało porzucone i zostanie zgłoszony wyjątek.  
  
## <a name="clearing-the-pool"></a>Czyszczenie puli  
 W ADO.NET 2,0 wprowadzono dwie nowe metody czyszczenia puli: <xref:System.Data.SqlClient.SqlConnection.ClearAllPools%2A> i <xref:System.Data.SqlClient.SqlConnection.ClearPool%2A> . `ClearAllPools`czyści pule połączeń dla danego dostawcy i `ClearPool` czyści pulę połączeń skojarzoną z określonym połączeniem. Jeśli w momencie wywołania są używane połączenia, są one odpowiednio oznaczone. Po ich zamknięciu są one odrzucane, nie są zwracane do puli.  
  
## <a name="transaction-support"></a>Obsługa transakcji  
 Połączenia są rysowane z puli i przypisywane na podstawie kontekstu transakcji. O ile nie `Enlist=false` zostanie określony w parametrach połączenia, pula połączeń sprawdza, czy połączenie jest zarejestrowane w <xref:System.Transactions.Transaction.Current%2A> kontekście. Gdy połączenie jest zamykane i zwracane do puli z zarejestrowaną `System.Transactions` transakcją, zostaje odłożone w taki sposób, że następne żądanie dla tej puli połączeń z tą samą `System.Transactions` transakcją zwróci to samo połączenie, jeśli jest dostępne. Jeśli takie żądanie jest wydawane, a połączenia w puli nie są dostępne, połączenie jest naliczane z nietransakcyjnej części puli i zarejestrowane. Jeśli w obu obszarach puli nie ma dostępnych połączeń, zostanie utworzone i zarejestrowane nowe połączenie.  
  
 Gdy połączenie jest zamknięte, zostaje wydane z powrotem do puli i do odpowiedniej części pola na podstawie kontekstu transakcji. W związku z tym możesz zamknąć połączenie bez generowania błędu, mimo że transakcja rozproszona nadal oczekuje. Dzięki temu możesz zatwierdzić lub przerwać transakcję rozproszoną później.  
  
## <a name="controlling-connection-pooling-with-connection-string-keywords"></a>Kontrolowanie puli połączeń przy użyciu słów kluczowych parametrów połączenia  
 `ConnectionString`Właściwość <xref:System.Data.SqlClient.SqlConnection> obiektu obsługuje pary klucz/wartość parametrów połączenia, których można użyć do dostosowania zachowania logiki puli połączeń. Aby uzyskać więcej informacji, zobacz <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
## <a name="pool-fragmentation"></a>Fragmentacja puli  
 Fragmentacja puli to typowy problem w wielu aplikacjach sieci Web, w których aplikacja może utworzyć dużą liczbę pul, które nie są zwalniane do momentu zakończenia procesu. Pozostawia to dużą liczbę połączeń, które otwierają i zużywają pamięć, co skutkuje niską wydajnością.  
  
### <a name="pool-fragmentation-due-to-integrated-security"></a>Fragmentacja puli ze względu na zabezpieczenia zintegrowane  
 Połączenia są w puli zgodne z parametrami połączenia i tożsamością użytkownika. Z tego względu, jeśli używasz uwierzytelniania podstawowego lub uwierzytelniania systemu Windows w witrynie sieci Web i zintegrowanego logowania zabezpieczeń, uzyskasz jedną pulę dla każdego użytkownika. Chociaż zwiększa to wydajność kolejnych żądań bazy danych dla jednego użytkownika, użytkownik nie może korzystać z połączeń wykonywanych przez innych użytkowników. Powoduje to również co najmniej jedno połączenie dla użytkownika z serwerem bazy danych. Jest to efekt uboczny konkretnej architektury aplikacji sieci Web, którą deweloperzy muszą odważyć przed wymaganiami dotyczącymi zabezpieczeń i inspekcji.  
  
### <a name="pool-fragmentation-due-to-many-databases"></a>Fragmentacja puli ze względu na wiele baz danych  
 Wielu usługodawców internetowych obsługuje kilka witryn sieci Web na jednym serwerze. Mogą oni użyć pojedynczej bazy danych, aby potwierdzić Logowanie przy użyciu uwierzytelniania formularzy, a następnie otworzyć połączenie z określoną bazą danych dla tego użytkownika lub grupy użytkowników. Połączenie z bazą danych uwierzytelniania jest w puli używane przez wszystkich użytkowników. Istnieje jednak oddzielna pula połączeń z każdą bazą danych, która zwiększa liczbę połączeń z serwerem.  
  
 Jest to również efektem ubocznym projektu aplikacji. Istnieje stosunkowo prosty sposób, aby uniknąć tego efektu ubocznego bez naruszania zabezpieczeń podczas łączenia się z SQL Server. Zamiast łączyć się z oddzielną bazą danych dla każdego użytkownika lub grupy, nawiąż połączenie z tą samą bazą danych na serwerze, a następnie wykonaj instrukcję USE języka Transact-SQL, aby zmienić żądaną bazę danych. Poniższy fragment kodu pokazuje, jak utworzyć początkowe połączenie z `master` bazą danych, a następnie przełączyć się na żądaną bazę danych określoną w `databaseName` zmiennej ciągu.  
  
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
 Po aktywowaniu SQL Server roli aplikacji przez wywołanie `sp_setapprole` procedury składowanej system nie można zresetować kontekstu zabezpieczeń tego połączenia. Jeśli jednak włączono obsługę puli, połączenie zostanie zwrócone do puli i wystąpi błąd, gdy połączenie z pulą jest ponownie używane. Aby uzyskać więcej informacji, zobacz artykuł w bazie wiedzy "[Błędy ról aplikacji SQL z pulą zasobów OLE DB](https://support.microsoft.com/default.aspx?scid=KB;EN-US;Q229564)".  
  
### <a name="application-role-alternatives"></a>Alternatywy ról aplikacji  
 Zalecamy skorzystanie z mechanizmów zabezpieczeń, których można używać zamiast ról aplikacji. Aby uzyskać więcej informacji, zobacz [Tworzenie ról aplikacji w SQL Server](./sql/creating-application-roles-in-sql-server.md).  
  
## <a name="see-also"></a>Zobacz także

- [Buforowanie połączeń](connection-pooling.md)
- [SQL Server i ADO.NET](./sql/index.md)
- [Liczniki wydajności](performance-counters.md)
- [Omówienie ADO.NET](ado-net-overview.md)
