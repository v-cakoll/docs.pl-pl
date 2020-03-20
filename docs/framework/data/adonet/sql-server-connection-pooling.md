---
title: Buforowanie połączeń programu SQL Server
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e51d44e-7c4e-4040-9332-f0190fe36f07
ms.openlocfilehash: 149511bd4e84baabf11eca014257127b587830df
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149001"
---
# <a name="sql-server-connection-pooling-adonet"></a>Buforowanie połączenia z programem SQL Server (ADO.NET)
Łączenie się z serwerem bazy danych zazwyczaj składa się z kilku czasochłonnych kroków. Kanał fizyczny, taki jak gniazdo lub nazwany potok, musi nastąpić początkowy uścisk dłoni z serwerem, informacje o ciągu połączenia muszą być analizowane, połączenie musi być uwierzytelnione przez serwer, kontrole muszą być uruchamiane w celu zarejestrowania w bieżącej transakcji itd.  
  
 W praktyce większość aplikacji używa tylko jednej lub kilku różnych konfiguracji dla połączeń. Oznacza to, że podczas wykonywania aplikacji wiele identycznych połączeń będzie wielokrotnie otwieranych i zamykanych. Aby zminimalizować koszt otwierania połączeń, ADO.NET stosuje technikę optymalizacji zwaną *buforowaniem połączeń*.  
  
 Buforowanie połączeń zmniejsza liczbę nowych połączeń. *Pooler* zachowuje własność połączenia fizycznego. Zarządza połączeniami, utrzymując przy życiu zestaw aktywnych połączeń dla każdej konfiguracji danego połączenia. Za każdym razem, gdy użytkownik wywołuje `Open` połączenie, pooler szuka dostępnego połączenia w puli. Jeśli połączenie w puli jest dostępne, zwraca go do obiektu wywołującego zamiast otwierania nowego połączenia. Gdy aplikacja `Close` wywołuje połączenie, pooler zwraca go do puli zestaw aktywnych połączeń zamiast zamykania go. Po powrocie połączenia do puli, jest gotowy do ponownego `Open` użycia przy następnym wywołaniu.  
  
 Tylko połączenia z tą samą konfiguracją mogą być łączone. ADO.NET przechowuje kilka pul jednocześnie, po jednym dla każdej konfiguracji. Połączenia są podzielone na pule według ciągu połączenia i przez tożsamość systemu Windows, gdy używane są zintegrowane zabezpieczenia. Połączenia są również łączone na podstawie tego, czy są one zarejestrowane w transakcji. Podczas <xref:System.Data.SqlClient.SqlConnection.ChangePassword%2A>korzystania <xref:System.Data.SqlClient.SqlCredential> wystąpienie wpływa na pulę połączeń. Różne wystąpienia <xref:System.Data.SqlClient.SqlCredential> będą używać różnych pul połączeń, nawet jeśli identyfikator użytkownika i hasło są takie same.  
  
 Łączenie połączeń może znacznie zwiększyć wydajność i skalowalność aplikacji. Domyślnie buforowanie połączeń jest włączone w ADO.NET. Jeśli nie zostanie jawnie wyłączyć, pooler optymalizuje połączenia, ponieważ są one otwarte i zamknięte w aplikacji. Można również podać kilka modyfikatorów ciągu połączenia, aby kontrolować zachowanie buforowania połączeń. Aby uzyskać więcej informacji, zobacz "Kontrolowanie buforowania połączeń za pomocą słów kluczowych ciągu połączenia" w dalszej części tego tematu.  
  
> [!NOTE]
> Gdy buforowanie połączeń jest włączone i jeśli wystąpi błąd limitu czasu lub inny błąd logowania, zostanie zgłoszony wyjątek, a kolejne próby połączenia nie powiodą się przez następne pięć sekund, "okres blokowania". Jeśli aplikacja próbuje połączyć się w okresie blokowania, pierwszy wyjątek zostanie zgłoszony ponownie. Kolejne awarie po zakończeniu okresu blokowania spowoduje nowe okresy blokowania, który jest dwa razy dłuższy niż poprzedni okres blokowania, maksymalnie do jednej minuty.  
  
## <a name="pool-creation-and-assignment"></a>Tworzenie i przypisywanie puli  
 Po pierwszym otwarciu połączenia pula połączeń jest tworzona na podstawie algorytmu dokładnego dopasowywania, który kojarzy pulę z ciągiem połączenia w połączeniu. Każda pula połączeń jest skojarzona z odrębnym ciągiem połączenia. Po otwarciu nowego połączenia, jeśli parametry połączenia nie jest dokładne dopasowanie do istniejącej puli, tworzony jest nowy puli. Połączenia są łączone według procesu, domeny aplikacji, ciągu połączenia i gdy używane są zintegrowane zabezpieczenia, według tożsamości systemu Windows. Parametry połączenia muszą być również dokładne dopasowanie; słowa kluczowe podane w innej kolejności dla tego samego połączenia będą łączone oddzielnie.  
  
 W poniższym przykładzie języka <xref:System.Data.SqlClient.SqlConnection> C# tworzone są trzy nowe obiekty, ale tylko dwa pule połączeń są wymagane do zarządzania nimi. Należy zauważyć, że pierwszy i drugi ciąg połączeń `Initial Catalog`różnią się wartością przypisaną do .  
  
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
  
 Jeśli `MinPoolSize` nie jest określony w ciągu połączenia lub jest określony jako zero, połączenia w puli zostaną zamknięte po okresie braku aktywności. Jednak jeśli określony `MinPoolSize` jest większy niż zero, pula połączeń `AppDomain` nie jest niszczony, dopóki nie zostanie zwolniony i proces kończy. Konserwacja nieaktywnych lub pustych pul wiąże się z minimalnym obciążeniem systemu.  
  
> [!NOTE]
> Pula jest automatycznie czyszczona po wystąpieniu błędu krytycznego, takiego jak przełącznie w stan failover.  
  
## <a name="adding-connections"></a>Dodawanie połączeń  
 Pula połączeń jest tworzona dla każdego unikatowego ciągu połączenia. Podczas tworzenia puli, wiele obiektów połączenia są tworzone i dodawane do puli, tak aby spełnione jest minimalne wymagania dotyczące rozmiaru puli. Połączenia są dodawane do puli w razie potrzeby, do maksymalnego rozmiaru puli określony (100 jest ustawieniem domyślnym). Połączenia są zwalniane z powrotem do puli, gdy są zamknięte lub usunięte.  
  
 Gdy <xref:System.Data.SqlClient.SqlConnection> obiekt jest wymagany, jest uzyskiwany z puli, jeśli dostępne jest połączenie użyteczne. Aby można było konfigurować, połączenie musi być nieużywane, mieć pasujący kontekst transakcji lub być niezwiązane z żadnym kontekstem transakcji i mieć prawidłowe łącze do serwera.  
  
 Pooler połączenia spełnia żądania połączeń przez ponowne przydzielanie połączeń, ponieważ są one zwalniane z powrotem do puli. Jeśli osiągnięto maksymalny rozmiar puli i nie jest dostępne połączenie użytkowe, żądanie jest umieszczane w kolejce. Pooler następnie próbuje odzyskać wszelkie połączenia, dopóki nie zostanie osiągnięty limit czasu (wartość domyślna to 15 sekund). Jeśli pooler nie może spełnić żądania przed upłyniem czasu połączenia, wyjątek.  
  
> [!CAUTION]
> Zdecydowanie zaleca się, aby zawsze zamknąć połączenie po zakończeniu korzystania z niego, tak aby połączenie zostanie zwrócone do puli. Można to zrobić za `Close` pomocą `Dispose` lub `Connection` metody obiektu lub otwierając wszystkie `using` połączenia wewnątrz instrukcji w `Using` języku C#lub instrukcji w języku Visual Basic. Połączenia, które nie są jawnie zamknięte, mogą nie zostać dodane lub zwrócone do puli. Aby uzyskać więcej informacji, zobacz [korzystanie z instrukcji](../../../csharp/language-reference/keywords/using-statement.md) lub [jak: Usuwanie zasobu systemowego](../../../visual-basic/programming-guide/language-features/control-flow/how-to-dispose-of-a-system-resource.md) dla języka Visual Basic.  
  
> [!NOTE]
> Nie należy `Close` `Dispose` wywoływać `Connection`ani `DataReader`na , a , `Finalize` lub innego obiektu zarządzanego w metodzie klasy. W finalizatorze tylko zwolnić niezarządzanych zasobów, które posiada bezpośrednio klasy. Jeśli klasa nie jest właścicielem żadnych zasobów niezarządzanych, nie należy uwzględniać `Finalize` metody w definicji klasy. Aby uzyskać więcej informacji, zobacz [Wyrzucanie elementów bezużytecznych](../../../standard/garbage-collection/index.md).  
  
Aby uzyskać więcej informacji na temat zdarzeń skojarzonych z otwieraniem i zamykaniem połączeń, zobacz [Inspekcja klasy zdarzeń logowania](/sql/relational-databases/event-classes/audit-login-event-class) i [klasa zdarzenia wylogowania inspekcji](/sql/relational-databases/event-classes/audit-logout-event-class) w dokumentacji programu SQL Server.  
  
## <a name="removing-connections"></a>Usuwanie połączeń  
 Pooler połączenia usuwa połączenie z puli po jego bezczynny przez około 4-8 minut lub jeśli pooler wykryje, że połączenie z serwerem zostało zerwane. Należy zauważyć, że zerwane połączenie można wykryć tylko po próbie komunikowania się z serwerem. Jeśli zostanie znalezione połączenie, które nie jest już połączone z serwerem, jest oznaczone jako nieprawidłowe. Nieprawidłowe połączenia są usuwane z puli połączeń tylko wtedy, gdy są zamknięte lub odzyskane.  
  
 Jeśli istnieje połączenie z serwerem, który zniknął, to połączenie można wyciągnąć z puli, nawet jeśli pooler połączenia nie wykrył zerwane połączenie i oznaczone jako nieprawidłowe. Dzieje się tak, ponieważ obciążenie związane z sprawdzaniem, czy połączenie jest nadal prawidłowe, wyeliminowałoby korzyści wynikające z posiadania poolera, powodując wystąpienie innej podróży w obie strony do serwera. W takim przypadku pierwsza próba użycia połączenia wykryje, że połączenie zostało zerwane i zostanie zgłoszony wyjątek.  
  
## <a name="clearing-the-pool"></a>Czyszczenie basenu  
 ADO.NET 2.0 wprowadzono dwie nowe metody oczyszczania <xref:System.Data.SqlClient.SqlConnection.ClearAllPools%2A> <xref:System.Data.SqlClient.SqlConnection.ClearPool%2A>puli: i . `ClearAllPools`czyści pule połączeń dla danego `ClearPool` dostawcy i czyści pulę połączeń skojarzoną z określonym połączeniem. Jeśli istnieją połączenia używane w czasie połączenia, są one odpowiednio oznaczone. Gdy są zamknięte, są odrzucane zamiast zwracać do puli.  
  
## <a name="transaction-support"></a>Obsługa transakcji  
 Połączenia są pobierane z puli i przypisywane na podstawie kontekstu transakcji. O `Enlist=false` ile nie określono w ciągu połączenia, pula połączeń zapewnia, że połączenie jest zarejestrowane w <xref:System.Transactions.Transaction.Current%2A> kontekście. Gdy połączenie jest zamknięte i zwrócone do `System.Transactions` puli z zarejestrowaną transakcją, jest odłożone w `System.Transactions` taki sposób, że następne żądanie dla tej puli połączeń z tą samą transakcją zwróci to samo połączenie, jeśli jest dostępne. Jeśli takie żądanie zostanie wystawione i nie ma dostępnych połączeń w puli, połączenie jest pobierane z nieprzekonanej części puli i zarejestrowane. Jeśli w żadnym z obszarów puli nie są dostępne żadne połączenia, zostanie utworzone i zarejestrowane nowe połączenie.  
  
 Po zamknięciu połączenia jest zwalniany z powrotem do puli i do odpowiedniego podpodziału na podstawie kontekstu transakcji. W związku z tym można zamknąć połączenie bez generowania błędu, nawet jeśli transakcja rozproszona jest nadal oczekująca. Dzięki temu można zatwierdzić lub przerwać transakcję rozproszoną później.  
  
## <a name="controlling-connection-pooling-with-connection-string-keywords"></a>Kontrolowanie buforowania połączeń za pomocą słów kluczowych ciągu połączenia  
 Właściwość `ConnectionString` <xref:System.Data.SqlClient.SqlConnection> obiektu obsługuje pary klucza/wartości ciągu połączenia, które mogą służyć do dostosowywania zachowania logiki buforowania połączeń. Aby uzyskać więcej informacji, zobacz <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
## <a name="pool-fragmentation"></a>Fragmentacja puli  
 Fragmentacja puli jest częstym problemem w wielu aplikacjach sieci Web, gdzie aplikacja może utworzyć dużą liczbę pul, które nie są zwalniane, dopóki proces nie zostanie zakończy. Pozostawia to dużą liczbę połączeń otwartych i zużywa pamięć, co powoduje niską wydajność.  
  
### <a name="pool-fragmentation-due-to-integrated-security"></a>Fragmentacja puli ze względu na zintegrowane zabezpieczenia  
 Połączenia są łączone zgodnie z ciągiem połączenia oraz tożsamością użytkownika. W związku z tym jeśli używasz uwierzytelniania podstawowego lub uwierzytelniania systemu Windows w witrynie sieci Web i zintegrowanego logowania zabezpieczeń, otrzymasz jedną pulę na użytkownika. Mimo że zwiększa to wydajność kolejnych żądań bazy danych dla pojedynczego użytkownika, ten użytkownik nie może korzystać z połączeń nawiązynych przez innych użytkowników. Powoduje to również co najmniej jedno połączenie na użytkownika z serwerem bazy danych. Jest to efekt uboczny określonej architektury aplikacji sieci Web, którą deweloperzy muszą ważyć z wymaganiami dotyczącymi zabezpieczeń i inspekcji.  
  
### <a name="pool-fragmentation-due-to-many-databases"></a>Fragmentacja puli z powodu wielu baz danych  
 Wielu dostawców usług internetowych hostuje kilka witryn sieci Web na jednym serwerze. Mogą użyć jednej bazy danych, aby potwierdzić identyfikator logowania do uwierzytelniania formularzy, a następnie otworzyć połączenie z określoną bazą danych dla tego użytkownika lub grupy użytkowników. Połączenie z bazą danych uwierzytelniania jest łączone i używane przez wszystkich. Istnieje jednak oddzielna pula połączeń z każdą bazą danych, które zwiększają liczbę połączeń z serwerem.  
  
 Jest to również efekt uboczny projektu aplikacji. Istnieje stosunkowo prosty sposób, aby uniknąć tego efektu ubocznego bez uszczerbku dla zabezpieczeń podczas łączenia się z programem SQL Server. Zamiast łączyć się z oddzielną bazą danych dla każdego użytkownika lub grupy, połącz się z tą samą bazą danych na serwerze, a następnie wykonaj instrukcję Transact-SQL USE, aby zmienić żądaną bazę danych. Poniższy fragment kodu demonstruje tworzenie `master` początkowego połączenia z bazą danych, `databaseName` a następnie przełączanie do żądanej bazy danych określonej w zmiennej ciągu.  
  
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
  
## <a name="application-roles-and-connection-pooling"></a>Role aplikacji i buforowanie połączeń  
 Po aktywowaniu roli aplikacji programu SQL `sp_setapprole` Server przez wywołanie procedury składowanej systemu nie można zresetować kontekstu zabezpieczeń tego połączenia. Jednak jeśli buforowanie jest włączone, połączenie jest zwracane do puli, a błąd występuje, gdy połączenie w puli jest ponownie. Aby uzyskać więcej informacji, zobacz artykuł z bazy wiedzy Knowledge Base, "[Błędy roli aplikacji SQL z buforowania zasobów OLE DB](https://support.microsoft.com/default.aspx?scid=KB;EN-US;Q229564)."  
  
### <a name="application-role-alternatives"></a>Alternatywy roli aplikacji  
 Zaleca się korzystanie z mechanizmów zabezpieczeń, których można użyć zamiast ról aplikacji. Aby uzyskać więcej informacji, zobacz [Tworzenie ról aplikacji w programie SQL Server](./sql/creating-application-roles-in-sql-server.md).  
  
## <a name="see-also"></a>Zobacz też

- [Buforowanie połączeń](connection-pooling.md)
- [SQL Server i ADO.NET](./sql/index.md)
- [Liczniki wydajności](performance-counters.md)
- [Omówienie ADO.NET](ado-net-overview.md)
