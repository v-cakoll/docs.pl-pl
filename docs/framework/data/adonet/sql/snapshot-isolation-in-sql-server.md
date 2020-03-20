---
title: Izolacja migawki w programie SQL Server
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 43ae5dd3-50f5-43a8-8d01-e37a61664176
ms.openlocfilehash: 8313ffc8eef70c1e5efc24b09a160edb7cec1595
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174267"
---
# <a name="snapshot-isolation-in-sql-server"></a>Izolacja migawki w programie SQL Server
Izolacja migawki zwiększa współbieżność aplikacji OLTP.  
  
## <a name="understanding-snapshot-isolation-and-row-versioning"></a>Opis izolacji migawki i przechowywania wersji wiersza  
 Po włączeniu izolacji migawki zaktualizowane wersje wierszy dla każdej transakcji muszą być zachowane.  Przed programem SQL Server 2019 wersje te były przechowywane w **programie tempdb**. SQL Server 2019 wprowadza nową funkcję, Przyspieszone odzyskiwanie bazy danych (ADR), która wymaga własnego zestawu wersji wierszy.  Tak, od SQL Server 2019, jeśli ADR nie jest włączona, wersje wierszy są przechowywane w **tempdb** jak zawsze.  Jeśli ADR jest włączona, wszystkie wersje wierszy, zarówno związane z izolacją migawki i ADR, są przechowywane w magazynie wersji trwałych ADR (PVS), który znajduje się w bazie danych użytkowników w grupie plików, którą określa użytkownik. Unikatowy numer sekwencyjny transakcji identyfikuje każdą transakcję, a te unikatowe numery są rejestrowane dla każdej wersji wiersza. Transakcja działa z najnowszymi wersjami wierszy o numerze sekwencyjnym przed numerem sekwencyjnym transakcji. Nowsze wersje wierszy utworzone po rozpoczęciu transakcji są ignorowane przez transakcję.  
  
 Termin "migawka" odzwierciedla fakt, że wszystkie zapytania w transakcji zobacz tę samą wersję lub migawkę bazy danych, na podstawie stanu bazy danych w momencie rozpoczęcia transakcji. Żadne blokady nie są nabywane na podstawowych wierszy danych lub stron danych w transakcji migawki, która umożliwia inne transakcje do wykonania bez blokowane przez poprzednią nieukończonej transakcji. Transakcje modyfikując dane nie blokują transakcji, które odczytują dane, a transakcje odczytywane dane nie blokują transakcji, które zapisują dane, tak jak zwykle w ramach domyślnego poziomu izolacji ODCZYTU POPEŁNIONE w programie SQL Server. To zachowanie nieblokujące również znacznie zmniejsza prawdopodobieństwo zakleszczenia dla złożonych transakcji.  
  
 Izolacja migawki używa modelu współbieżności optymistyczne. Jeśli transakcja migawki próbuje zatwierdzić modyfikacje danych, które uległy zmianie od momentu rozpoczęcia transakcji, transakcja zostanie wycofana i zostanie zgłoszony błąd. Można tego uniknąć, używając wskazówek UPDLOCK dla instrukcji SELECT, które mają być modyfikowane przez dane dostępu. Aby uzyskać więcej informacji, zobacz "Wskazówki dotyczące blokowania" w programie SQL Server Books Online.  
  
 Izolacja migawki musi być włączona, ustawiając opcję bazy danych ALLOW_SNAPSHOT_ISOLATION ON, zanim będzie używana w transakcjach. Aktywuje to mechanizm przechowywania wersji wiersza w tymczasowej bazie danych (**tempdb**). Izolacja migawki w każdej bazie danych, która używa go z Instrukcja Transact-SQL ALTER DATABASE. W związku z tym izolacja migawki różni się od tradycyjnych poziomów izolacji ODCZYT COMMITTED, REPEATABLE READ, SERIALIZABLE i READ UNCOMMITTED, które nie wymagają konfiguracji. Następujące instrukcje aktywują izolację migawki i zastępują domyślne zachowanie READ COMMITTED migawką:  
  
```sql  
ALTER DATABASE MyDatabase  
SET ALLOW_SNAPSHOT_ISOLATION ON  
  
ALTER DATABASE MyDatabase  
SET READ_COMMITTED_SNAPSHOT ON  
```  
  
 Ustawienie opcji READ_COMMITTED_SNAPSHOT ON umożliwia dostęp do wierszy wersjonowanych pod domyślnym poziomem izolacji ODCZYTU POPEŁNIONE. Jeśli opcja READ_COMMITTED_SNAPSHOT jest ustawiona na OFF, należy jawnie ustawić poziom izolacji migawki dla każdej sesji, aby uzyskać dostęp do wierszy wersjonowanych.  
  
## <a name="managing-concurrency-with-isolation-levels"></a>Zarządzanie współbieżnością z poziomami izolacji  
 Poziom izolacji, na którym wykonuje instrukcja Transact-SQL określa jego zachowanie blokowania i przechowywania wersji wiersza. Poziom izolacji ma zakres całego połączenia i po ustawieniu połączenia z instrukcją SET TRANSACTION ISOLATION LEVEL pozostaje w mocy, dopóki połączenie nie zostanie zamknięte lub zostanie ustawiony inny poziom izolacji. Gdy połączenie jest zamknięte i zwrócone do puli, poziom izolacji z ostatniej instrukcji SET TRANSACTION ISOLATION LEVEL jest zachowywany. Kolejne połączenia ponownie korzystające z połączenia pooled używają poziomu izolacji, który obowiązywał w momencie połączenia.  
  
 Poszczególne zapytania wydane w ramach połączenia mogą zawierać wskazówki blokady, które modyfikują izolację dla pojedynczej instrukcji lub transakcji, ale nie wpływają na poziom izolacji połączenia. Poziomy izolacji lub wskazówki blokady ustawione w procedurach składowanych lub funkcji nie zmieniają poziomu izolacji połączenia, które je wywołuje i obowiązują tylko przez czas trwania procedury składowanej lub wywołania funkcji.  
  
 Cztery poziomy izolacji zdefiniowane w standardzie SQL-92 były obsługiwane we wczesnych wersjach programu SQL Server:  
  
- READ UNCOMMITTED jest najmniej restrykcyjny poziom izolacji, ponieważ ignoruje blokady umieszczone przez inne transakcje. Transakcje wykonywane w ramach odczytu BEZKOMIENIA można odczytać zmodyfikowane wartości danych, które nie zostały jeszcze zatwierdzone przez inne transakcje; są one nazywane "brudne" odczyty.  
  
- READ COMMITTED jest domyślnym poziomem izolacji dla programu SQL Server. Zapobiega odczyty brudne, określając, że instrukcje nie można odczytać wartości danych, które zostały zmodyfikowane, ale jeszcze nie zatwierdzone przez inne transakcje. Inne transakcje mogą nadal modyfikować, wstawiać lub usuwać dane między wykonaniami poszczególnych instrukcji w ramach bieżącej transakcji, co powoduje powtarzalne odczyty lub dane "fantomowe".  
  
- ODCZYT POWTARZALNY jest bardziej restrykcyjnym poziomem izolacji niż odczyt committed. Obejmuje ona read committed i dodatkowo określa, że żadne inne transakcje można modyfikować lub usuwać dane, które zostały odczytane przez bieżącą transakcję, dopóki bieżąca transakcja zatwierdza. Współbieżność jest niższa niż dla ODCZYTU POPEŁNIONE, ponieważ blokady udostępnione na odczyt danych są przechowywane przez czas trwania transakcji, a nie są zwalniane na końcu każdej instrukcji.  
  
- SERIALIZABLE jest najbardziej restrykcyjny poziom izolacji, ponieważ blokuje całe zakresy kluczy i przechowuje blokady, dopóki transakcja nie zostanie zakończona. Obejmuje powtarzalny odczyt i dodaje ograniczenie, że inne transakcje nie można wstawić nowe wiersze do zakresów, które zostały odczytane przez transakcję, dopóki transakcja nie zostanie zakończona.  
  
 Aby uzyskać więcej informacji, zapoznaj się z [przewodnikiem blokowania transakcji i wersji wiersza](/sql/relational-databases/sql-server-transaction-locking-and-row-versioning-guide).  
  
### <a name="snapshot-isolation-level-extensions"></a>Rozszerzenia poziomu izolacji migawki  
 SQL Server wprowadzono rozszerzenia do poziomów izolacji SQL-92 z wprowadzeniem poziomu izolacji migawki i dodatkowej implementacji READ COMMITTED. Poziom izolacji READ_COMMITTED_SNAPSHOT może w sposób przejrzysty zastąpić READ COMMITTED dla wszystkich transakcji.  
  
- Izolacja migawka określa, że dane odczytane w ramach transakcji nigdy nie będą odzwierciedlać zmian wprowadzonych przez inne transakcje jednoczesne. Transakcja używa wersji wiersza danych, które istnieją po rozpoczęciu transakcji. Żadne blokady są umieszczane na danych, gdy jest odczytywany, więc transakcje MIGAWKA nie blokują innych transakcji z zapisywania danych. Transakcje, które zapisują dane, nie blokują transakcji migawki z odczytu danych. Aby ją użyć, należy włączyć izolację migawki, ustawiając opcję ALLOW_SNAPSHOT_ISOLATION bazy danych.  
  
- Opcja READ_COMMITTED_SNAPSHOT bazy danych określa zachowanie domyślnego poziomu izolacji ODCZYTU POPEŁNIONE, gdy izolacja migawki jest włączona w bazie danych. Jeśli nie zostanie jawnie określić READ_COMMITTED_SNAPSHOT ON, READ COMMITTED jest stosowany do wszystkich transakcji niejawnych. Powoduje to takie samo zachowanie jak ustawienie READ_COMMITTED_SNAPSHOT OFF (domyślnie). Gdy READ_COMMITTED_SNAPSHOT OFF jest w mocy, Aparat baz danych używa blokad udostępnionych w celu wymuszenia domyślnego poziomu izolacji. Jeśli ustawisz opcję READ_COMMITTED_SNAPSHOT bazy danych na ON, aparat bazy danych używa przechowywania wersji wiersza i izolacji migawki jako domyślnej, zamiast używać blokad do ochrony danych.  
  
## <a name="how-snapshot-isolation-and-row-versioning-work"></a>Jak działa izolacja migawki i przechowywanie wersji wiersza  
 Po włączeniu poziomu izolacji migawki, za każdym razem, gdy wiersz jest aktualizowany, aparat baz danych programu SQL Server przechowuje kopię oryginalnego wiersza w **programie tempdb**i dodaje numer sekwencyjny transakcji do wiersza. Poniżej przedstawiono sekwencję zdarzeń, które występują:  
  
- Nowa transakcja jest inicjowana i jest przypisywana numer sekwencyjny transakcji.  
  
- Aparat baz danych odczytuje wiersz w ramach transakcji i pobiera wersję wiersza z **tempdb,** którego numer sekwencyjny jest najbliżej i niższy niż numer sekwencyjny transakcji.  
  
- Aparat baz danych sprawdza, czy numer sekwencyjny transakcji nie znajduje się na liście numerów sekwencyjnych transakcji niezakończonej transakcji aktywnych po rozpoczęciu transakcji migawkowej.  
  
- Transakcja odczytuje wersję wiersza z **tempdb,** który był bieżący od początku transakcji. Nie będzie widać nowych wierszy wstawionych po rozpoczęciu transakcji, ponieważ te wartości numerów sekwencyjnych będą wyższe niż wartość numeru sekwencyjnyego transakcji.  
  
- Bieżąca transakcja zobaczy wiersze, które zostały usunięte po rozpoczęciu transakcji, ponieważ w **pliku tempdb** będzie dostępna wersja wiersza o niższej wartości numeru sekwencowego.  
  
 Efekt netto izolacji migawki jest, że transakcja widzi wszystkie dane, jak istniały na początku transakcji, bez honorowania lub umieszczania żadnych blokad na tabelach źródłowych. Może to spowodować poprawę wydajności w sytuacjach, w których istnieje rywalizacja.  
  
 Transakcja migawka zawsze używa kontroli współbieżności optymistyczne, wstrzymanie wszelkich blokad, które uniemożliwiłyby inne transakcje aktualizowanie wierszy. Jeśli transakcja migawki próbuje zatwierdzić aktualizację do wiersza, który został zmieniony po rozpoczęciu transakcji, transakcja jest przywracana i zgłaszany jest błąd.  
  
## <a name="working-with-snapshot-isolation-in-adonet"></a>Praca z izolacją migawek w ADO.NET  
 Izolacja migawki jest obsługiwana <xref:System.Data.SqlClient.SqlTransaction> w ADO.NET przez klasę. Jeśli baza danych została włączona dla izolacji migawki, ale nie jest skonfigurowany do READ_COMMITTED_SNAPSHOT ON, należy zainicjować <xref:System.Data.SqlClient.SqlTransaction> przy użyciu **IsolationLevel.Snapshot** wartość wyliczenia podczas wywoływania <xref:System.Data.SqlClient.SqlConnection.BeginTransaction%2A> metody. Ten fragment kodu zakłada, że <xref:System.Data.SqlClient.SqlConnection> połączenie jest obiektem otwartym.  
  
```vb  
Dim sqlTran As SqlTransaction = _  
  connection.BeginTransaction(IsolationLevel.Snapshot)  
```  
  
```csharp  
SqlTransaction sqlTran =
  connection.BeginTransaction(IsolationLevel.Snapshot);  
```  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak zachowują się różne poziomy izolacji, próbując uzyskać dostęp do zablokowanych danych i nie jest przeznaczony do użycia w kodzie produkcyjnym.  
  
 Kod łączy się z przykładową bazą danych **AdventureWorks** w programie SQL Server i tworzy tabelę o nazwie **TestSnapshot** i wstawia jeden wiersz danych. Kod używa alter database Transact-SQL instrukcji, aby włączyć izolację migawki dla bazy danych, ale nie ustawia READ_COMMITTED_SNAPSHOT, pozostawiając domyślne odczytu popełnione zachowanie na poziomie izolacji w efekcie. Następnie kod wykonuje następujące akcje:  
  
- Rozpoczyna się, ale nie kończy, sqlTransaction1, który używa poziomu izolacji serializable, aby rozpocząć transakcję aktualizacji. Ma to wpływ na zablokowanie tabeli.  
  
- Otwiera drugie połączenie i inicjuje drugą transakcję przy użyciu poziomu izolacji MIGAWKA do odczytu danych w **tabeli TestSnapshot.** Ponieważ izolacja migawki jest włączona, ta transakcja może odczytać dane, które istniały przed sqlTransaction1 rozpoczęte.  
  
- Otwiera trzecie połączenie i inicjuje transakcję przy użyciu poziomu izolacji READ COMMITTED, aby spróbować odczytać dane w tabeli. W takim przypadku kod nie może odczytać danych, ponieważ nie można odczytać obok blokad umieszczonych w tabeli w pierwszej transakcji i upoicie limit czasu. Ten sam wynik będzie występować, jeśli powtarzalne odczytu i serializable poziomy izolacji zostały użyte, ponieważ te poziomy izolacji również nie można odczytać przeszłości blokady umieszczone w pierwszej transakcji.  
  
- Otwiera czwarte połączenie i inicjuje transakcję przy użyciu poziomu izolacji UNCOMMITTED ODCZYTu, który wykonuje brudny odczyt niezatwierdzonej wartości w sqlTransaction1. Ta wartość może nigdy nie istnieć w bazie danych, jeśli pierwsza transakcja nie jest zatwierdzona.  
  
- Wycofuje pierwszą transakcję i czyści przez usunięcie **TestSnapshot** tabeli i wyłączenie izolacji migawki dla **adventureworks** bazy danych.  
  
> [!NOTE]
> W poniższych przykładach użyto tego samego ciągu połączenia z wyłączonym buforem połączeń. Jeśli połączenie jest połączone, zresetowanie jego poziomu izolacji nie resetuje poziomu izolacji na serwerze. W rezultacie kolejne połączenia, które używają tego samego połączenia wewnętrznego puli rozpocząć z ich poziomów izolacji ustawiona na to, że połączenie w puli. Alternatywą dla wyłączania buforowania połączeń jest jawne ustawienie poziomu izolacji dla każdego połączenia.  
  
 [!code-csharp[DataWorks SnapshotIsolation.Demo#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SnapshotIsolation.Demo/CS/source.cs#1)]
 [!code-vb[DataWorks SnapshotIsolation.Demo#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SnapshotIsolation.Demo/VB/source.vb#1)]  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano zachowanie izolacji migawki, gdy dane są modyfikowane. Kod wykonuje następujące akcje:  
  
- Łączy się z **adventureworks** przykładowej bazy danych i umożliwia izolację MIGAWKI.  
  
- Tworzy tabelę o nazwie **TestSnapshotUpdate** i wstawia trzy wiersze przykładowych danych.  
  
- Rozpoczyna się, ale nie kończy, sqlTransaction1 przy użyciu izolacji migawki. W transakcji są wybierane trzy wiersze danych.  
  
- Tworzy drugi **SqlConnection** do **AdventureWorks** i tworzy drugą transakcję przy użyciu odczytu popełnione poziom izolacji, który aktualizuje wartość w jednym z wierszy wybranych w sqlTransaction1.  
  
- Zatwierdza sqlTransaction2.  
  
- Zwraca do sqlTransaction1 i próbuje zaktualizować ten sam wiersz, który sqlTransaction1 już zatwierdzone. Błąd 3960 jest wywoływany, a sqlTransaction1 jest przywracany automatycznie. **SqlException.Number** i **SqlException.Message** są wyświetlane w oknie konsoli.  
  
- Wykonuje kod oczyszczania, aby wyłączyć izolację migawki w **AdventureWorks** i usunąć **testsnapshotUpdate** tabeli.  
  
 [!code-csharp[DataWorks SnapshotIsolation.DemoUpdate#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SnapshotIsolation.DemoUpdate/CS/source.cs#1)]
 [!code-vb[DataWorks SnapshotIsolation.DemoUpdate#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SnapshotIsolation.DemoUpdate/VB/source.vb#1)]  
  
### <a name="using-lock-hints-with-snapshot-isolation"></a>Korzystanie z wskazówek dotyczących blokowania z izolacją migawki  
 W poprzednim przykładzie pierwsza transakcja wybiera dane, a druga transakcja aktualizuje dane przed pierwszą transakcją jest w stanie zakończyć, powodując konflikt aktualizacji, gdy pierwsza transakcja próbuje zaktualizować ten sam wiersz. Można zmniejszyć ryzyko konfliktów aktualizacji w długotrwałych transakcji migawki, podając wskazówki blokady na początku transakcji. Następująca instrukcja SELECT używa wskazówki UPDLOCK do blokowania wybranych wierszy:  
  
```sql  
SELECT * FROM TestSnapshotUpdate WITH (UPDLOCK)
  WHERE PriKey BETWEEN 1 AND 3  
```  
  
 Za pomocą wskazówki blokady UPDLOCK blokuje wiersze próby aktualizacji wierszy przed zakończeniem pierwszej transakcji. Gwarantuje to, że wybrane wiersze nie mają konfliktów, gdy są aktualizowane w dalszej części transakcji. Zobacz "Wskazówki dotyczące blokowania" w programie SQL Server Books Online.  
  
 Jeśli aplikacja ma wiele konfliktów, izolacja migawki może nie być najlepszym wyborem. Wskazówki powinny być używane tylko wtedy, gdy naprawdę potrzebne. Aplikacja nie powinna być zaprojektowana tak, aby stale opiera się na wskazówki blokady dla jego działania.  
  
## <a name="see-also"></a>Zobacz też

- [SQL Server i ADO.NET](index.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
- [Przewodnik po blokowaniu transakcji i wersjowaniu wierszy](/sql/relational-databases/sql-server-transaction-locking-and-row-versioning-guide)
