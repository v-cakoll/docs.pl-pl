---
title: Izolacja migawki w programie SQL Server
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 43ae5dd3-50f5-43a8-8d01-e37a61664176
ms.openlocfilehash: 2f17e9828f46e6355cdbbddb1b8a83f1188b1a01
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791742"
---
# <a name="snapshot-isolation-in-sql-server"></a>Izolacja migawki w programie SQL Server
Izolacja migawki podwyższa poziom współbieżności dla aplikacji OLTP.  
  
## <a name="understanding-snapshot-isolation-and-row-versioning"></a>Omówienie izolacji migawek i przechowywania wersji wierszy  
 Gdy izolacja migawki jest włączona, zaktualizowane wersje wierszy dla każdej transakcji są zachowywane w **bazie danych tempdb**. Unikatowy numer sekwencyjny transakcji identyfikuje każdą transakcję, a te unikatowe numery są rejestrowane dla każdej wersji wiersza. Transakcja współdziała z najnowszymi wersjami wierszy mającymi numer sekwencyjny przed numerem sekwencyjnym transakcji. Nowsze wersje wierszy utworzone po rozpoczęciu transakcji są ignorowane przez transakcję.  
  
 Termin "migawka" odzwierciedla fakt, że wszystkie zapytania w transakcji widzą tę samą wersję lub migawkę bazy danych, na podstawie stanu bazy danych w momencie rozpoczęcia transakcji. Żadne blokady nie są uzyskiwane na bazowych wierszach danych lub stronach danych w transakcji migawek, co umożliwia wykonywanie innych transakcji bez blokowania przez poprzednią nieukończoną transakcję. Transakcje, które modyfikują dane, nie blokują transakcji, które odczytują dane, a transakcje, które odczytują dane, nie blokują transakcji, które zapisują dane, tak jak zwykle w ramach domyślnego, ZATWIERDZONEgo poziomu izolacji odczytu w SQL Server. Takie zachowanie bez blokowania znacznie zmniejsza prawdopodobieństwo zakleszczenia złożonych transakcji.  
  
 Izolacja migawki używa optymistycznego modelu współbieżności. Jeśli transakcja migawki próbuje zatwierdzić modyfikacje danych, które uległy zmianie od momentu rozpoczęcia transakcji, transakcja zostanie wycofana i zostanie zgłoszony błąd. Można uniknąć tego za pomocą wskazówek UPDLOCK dla instrukcji SELECT, które uzyskują dostęp do danych do zmodyfikowania. Aby uzyskać więcej informacji, zobacz "wskazówki dotyczące blokowania" w temacie SQL Server Books Online.  
  
 Izolacja migawki musi być włączona przez ustawienie opcji ALLOW_SNAPSHOT_ISOLATION w bazie danych, zanim zostanie użyta w transakcjach. Aktywuje to mechanizm przechowywania wersji wierszy w tymczasowej bazie danych (**tempdb**). Należy włączyć izolację migawki w każdej bazie danych, która używa jej z instrukcją ALTER DATABASE języka Transact-SQL. W tym aspekcie izolacja migawki różni się od tradycyjnego poziomu izolacji odczytu ZATWIERDZONEgo, POWTARZALNEgo odczytu, serializacji i odczytu niezatwierdzonego, co nie wymaga konfiguracji. Poniższe instrukcje aktywują izolację migawki i zastępują domyślne zachowanie podczas odczytu zatwierdzone z MIGAWKą:  
  
```sql  
ALTER DATABASE MyDatabase  
SET ALLOW_SNAPSHOT_ISOLATION ON  
  
ALTER DATABASE MyDatabase  
SET READ_COMMITTED_SNAPSHOT ON  
```  
  
 Ustawienie opcji READ_COMMITTED_SNAPSHOT na umożliwia dostęp do wierszy z wersjami w ramach domyślnego poziomu izolacji READ COMMITTED. Jeśli opcja READ_COMMITTED_SNAPSHOT jest wyłączona, należy jawnie ustawić poziom izolacji migawki dla każdej sesji w celu uzyskania dostępu do wierszy z uruchomioną wersją.  
  
## <a name="managing-concurrency-with-isolation-levels"></a>Zarządzanie współbieżnością z poziomami izolacji  
 Poziom izolacji, w ramach którego wykonywana jest instrukcja języka Transact-SQL określa zachowanie funkcji blokowania i obsługi wersji wierszy. Poziom izolacji ma zakres połączenia, a po ustawieniu dla połączenia z instrukcją Ustaw poziom izolacji transakcji nadal obowiązuje do momentu zamknięcia połączenia lub ustawienia innego poziomu izolacji. Gdy połączenie jest zamknięte i zwracane do puli, jest zachowywany poziom izolacji z ostatniej instrukcji poziomu izolacji transakcji. Kolejne połączenia, które używają połączenia w puli, używają poziomu izolacji, który obowiązywał w chwili, gdy połączenie jest w puli.  
  
 Poszczególne zapytania wydawane w ramach połączenia mogą zawierać wskazówki blokad, które modyfikują izolację pojedynczej instrukcji lub transakcji, ale nie wpływają na poziom izolacji połączenia. Poziomy izolacji lub wskazówki blokady ustawione w procedurach lub funkcjach składowanych nie zmieniają poziomu izolacji połączenia, które je wywołuje, i obowiązują tylko w czasie trwania procedury składowanej lub wywołania funkcji.  
  
 Na wczesnych wersjach SQL Server obsługiwane są cztery poziomy izolacji zdefiniowane w standardzie SQL-92:  
  
- Odczytanie niezatwierdzone to najmniej restrykcyjny poziom izolacji, ponieważ powoduje ignorowanie blokad umieszczonych w innych transakcjach. Transakcje wykonywane w ramach odczytu niezatwierdzonego mogą odczytywać zmodyfikowane wartości danych, które nie zostały jeszcze zatwierdzone przez inne transakcje; są one nazywane odczytami "Dirty".  
  
- Uprawnienie READ COMMITTED jest domyślnym poziomem izolacji dla SQL Server. Uniemożliwia to przeczytanie przez określenie, że te instrukcje nie mogą odczytywać wartości danych, które zostały zmodyfikowane, ale nie zostały jeszcze zatwierdzone przez inne transakcje. Inne transakcje nadal mogą modyfikować, wstawiać i usuwać dane między wykonaniami poszczególnych instrukcji w ramach bieżącej transakcji, co oznacza, że odczyty niepowtarzalne lub dane "fantomu".  
  
- POWTARZAjący się odczyt to bardziej restrykcyjny poziom izolacji niż w przypadku zatwierdzenia. Obejmuje to uprawnienie Odczyt i Ponadto określa, że żadne inne transakcje nie mogą modyfikować ani usuwać danych odczytanych przez bieżącą transakcję do momentu zatwierdzenia bieżącej transakcji. Współbieżność jest mniejsza niż w przypadku odczytu ZATWIERDZONEgo, ponieważ blokady udostępnione dla odczytu danych są przechowywane na czas trwania transakcji zamiast zwalniania na końcu każdej instrukcji.  
  
- SERIALIZABLE to najbardziej restrykcyjny poziom izolacji, ponieważ blokuje całe zakresy kluczy i utrzymuje blokady do momentu ukończenia transakcji. Obejmuje to powtarzalny odczyt i dodaje ograniczenie, że inne transakcje nie mogą wstawiać nowych wierszy do zakresów, które zostały odczytane przez transakcję do momentu ukończenia transakcji.  
  
 Aby uzyskać więcej informacji, zapoznaj się z [przewodnikiem blokowanie transakcji i przechowywanie wersji wierszy](/sql/relational-databases/sql-server-transaction-locking-and-row-versioning-guide).  
  
### <a name="snapshot-isolation-level-extensions"></a>Rozszerzenia poziomu izolacji migawek  
 SQL Server wprowadził rozszerzenia na poziomy izolacji SQL-92 z wprowadzeniem poziomu izolacji migawki oraz dodatkową implementacją PRZEKAZANEgo odczytu. Poziom izolacji READ_COMMITTED_SNAPSHOT może w sposób przezroczysty zastąpić odczyt PRZYDZIELONY dla wszystkich transakcji.  
  
- Izolacja migawki określa, że dane odczytane w ramach transakcji nigdy nie będą odzwierciedlać zmian wprowadzonych przez inne równoczesne transakcje. W transakcji są używane wersje wierszy danych, które istnieją po rozpoczęciu transakcji. Podczas odczytywania danych nie są umieszczane żadne blokady, więc transakcje migawek nie blokują innych transakcji zapisu danych. Transakcje, które zapisują dane, nie blokują transakcji migawek odczytywania danych. Aby można było używać izolacji migawek, należy ustawić opcję bazy danych ALLOW_SNAPSHOT_ISOLATION.  
  
- Opcja bazy danych READ_COMMITTED_SNAPSHOT określa zachowanie domyślnego, ZATWIERDZONEgo poziomu izolacji odczytu, gdy izolacja migawki jest włączona w bazie danych. Jeśli nie określisz jawnie READ_COMMITTED_SNAPSHOT ON, uprawnienie READ COMMITTED jest stosowane do wszystkich niejawnych transakcji. Daje to takie samo zachowanie jak ustawienie READ_COMMITTED_SNAPSHOT (domyślnie). Gdy READ_COMMITTED_SNAPSHOT jest wyłączona, aparat bazy danych używa blokad współużytkowanych w celu wymuszenia domyślnego poziomu izolacji. Jeśli ustawisz opcję bazy danych READ_COMMITTED_SNAPSHOT na włączone, aparat bazy danych domyślnie korzysta z funkcji przechowywania wersji wierszy i izolacji migawek, a nie do ochrony danych.  
  
## <a name="how-snapshot-isolation-and-row-versioning-work"></a>Jak działa izolacja migawek i przechowywanie wersji wierszy  
 Gdy poziom izolacji migawki jest włączony, za każdym razem, gdy wiersz jest aktualizowany, aparat bazy danych SQL Server przechowuje kopię pierwotnego wiersza w **tempdb**i dodaje do wiersza numer sekwencyjny transakcji. Poniżej przedstawiono sekwencję zdarzeń:  
  
- Zostanie zainicjowana Nowa transakcja, która ma przypisany numer sekwencyjny transakcji.  
  
- Aparat bazy danych odczytuje wiersz transakcji i Pobiera wersję wiersza z **bazy danych tempdb** , której numer sekwencyjny jest najbliższy i niższy niż numer sekwencyjny transakcji.  
  
- Aparat bazy danych sprawdza, czy numer sekwencyjny transakcji nie znajduje się na liście numerów sekwencji transakcji dla niezatwierdzonych transakcji aktywnych, gdy transakcja migawki została uruchomiona.  
  
- Transakcja odczytuje wersję wiersza z **bazy danych tempdb** , która była aktualna względem początku transakcji. Po uruchomieniu transakcji nie będą widoczne nowe wiersze wstawione, ponieważ te wartości numeru sekwencyjnego będą większe niż wartość numeru sekwencji transakcji.  
  
- Bieżąca transakcja zobaczy wiersze, które zostały usunięte po rozpoczęciu transakcji, ponieważ w **bazie danych tempdb** będzie dostępna wersja wiersza o niższej wartości numeru sekwencji.  
  
 Efektem netto izolacji migawki jest fakt, że transakcja zobaczy wszystkie dane, które istniały na początku transakcji, bez przestrzegania ani umieszczania blokad w tabelach bazowych. Może to skutkować zwiększeniem wydajności w sytuacjach, gdy istnieje rywalizacja.  
  
 Transakcja migawki zawsze korzysta z optymistycznej kontroli współbieżności, co powoduje wstrzymanie wszelkich blokad, które mogłyby uniemożliwić innym transakcjom aktualizowanie wierszy. Jeśli transakcja migawki próbuje zatwierdzić aktualizację wiersza, który został zmieniony po rozpoczęciu transakcji, transakcja zostanie wycofana i zostanie zgłoszony błąd.  
  
## <a name="working-with-snapshot-isolation-in-adonet"></a>Praca z izolacją migawki w ADO.NET  
 Izolacja migawki jest obsługiwana w ADO.NET przez <xref:System.Data.SqlClient.SqlTransaction> klasę. Jeśli baza danych została włączona na potrzeby izolacji migawki, ale nie jest skonfigurowana do READ_COMMITTED_SNAPSHOT na, należy zainicjować <xref:System.Data.SqlClient.SqlTransaction> przy użyciu <xref:System.Data.SqlClient.SqlConnection.BeginTransaction%2A> wartości wyliczenia **IsolationLevel. snapshot** podczas wywoływania metody. W tym fragmencie kodu założono, że połączenie <xref:System.Data.SqlClient.SqlConnection> jest otwartym obiektem.  
  
```vb  
Dim sqlTran As SqlTransaction = _  
  connection.BeginTransaction(IsolationLevel.Snapshot)  
```  
  
```csharp  
SqlTransaction sqlTran =   
  connection.BeginTransaction(IsolationLevel.Snapshot);  
```  
  
### <a name="example"></a>Przykład  
 Poniższy przykład demonstruje zachowanie różnych poziomów izolacji, próbując uzyskać dostęp do zablokowanych danych i nie jest przeznaczony do użycia w kodzie produkcyjnym.  
  
 Kod nawiązuje połączenie z przykładową bazą danych **AdventureWorks** w SQL Server i tworzy tabelę o nazwie **TestSnapshot** i wstawia jeden wiersz danych. Kod używa instrukcji ALTER DATABASE Transact-SQL, aby włączyć izolację migawki dla bazy danych, ale nie ustawi opcji READ_COMMITTED_SNAPSHOT, pozostawiając domyślne zachowanie na poziomie izolacji dotyczącej odczytu. Następnie kod wykonuje następujące czynności:  
  
- Rozpocznie się, ale nie kończy, sqlTransaction1, który używa poziomu izolacji możliwej do serializacji, aby rozpocząć transakcję aktualizacji. Ma to wpływ na blokowanie tabeli.  
  
- Otwiera drugie połączenie i inicjuje drugą transakcję przy użyciu poziomu izolacji migawki w celu odczytania danych w tabeli **TestSnapshot** . Ponieważ izolacja migawki jest włączona, ta transakcja może odczytywać dane, które istniały przed rozpoczęciem sqlTransaction1.  
  
- Otwiera trzecie połączenie i inicjuje transakcję przy użyciu poziomu izolacji READ COMMITTED, aby próbować odczytać dane z tabeli. W takim przypadku kod nie może odczytać danych, ponieważ nie może odczytywać wcześniejszych blokad umieszczonych w tabeli w pierwszej transakcji i przekroczenia limitu czasu. Ten sam wynik wystąpi, jeśli są używane powtarzalne poziomy izolacji odczytu i serializacji, ponieważ te poziomy izolacji nie mogą odczytywać poza blokadami umieszczonymi w pierwszej transakcji.  
  
- Otwiera czwarte połączenie i inicjuje transakcję przy użyciu niezatwierdzonego poziomu izolacji, co powoduje przeczytanie niezatwierdzonej wartości w sqlTransaction1. Ta wartość może nigdy nie istnieć w bazie danych, jeśli pierwsza transakcja nie została zatwierdzona.  
  
- Wycofuje ona pierwszą transakcję i czyści je, usuwając tabelę **TestSnapshot** i wyłączając izolację migawki dla bazy danych **AdventureWorks** .  
  
> [!NOTE]
> W poniższych przykładach użyto tych samych parametrów połączenia z wyłączoną pulą połączeń. Jeśli połączenie jest w puli, zresetowanie jego poziomu izolacji nie powoduje zresetowania poziomu izolacji na serwerze. W związku z tym kolejne połączenia, które używają tego samego połączenia wewnętrznego w puli, zaczynają się od poziomów izolacji ustawionych dla połączenia w puli. Alternatywą dla wyłączenia puli połączeń jest ustawienie poziomu izolacji jawnie dla każdego połączenia.  
  
 [!code-csharp[DataWorks SnapshotIsolation.Demo#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SnapshotIsolation.Demo/CS/source.cs#1)]
 [!code-vb[DataWorks SnapshotIsolation.Demo#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SnapshotIsolation.Demo/VB/source.vb#1)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykład ilustruje zachowanie izolacji migawki, gdy dane są modyfikowane. Kod wykonuje następujące czynności:  
  
- Nawiązuje połączenie z przykładową bazą danych **AdventureWorks** i włącza izolację migawki.  
  
- Tworzy tabelę o nazwie **TestSnapshotUpdate** i wstawia trzy wiersze przykładowych danych.  
  
- Rozpoczyna, ale nie kończy, sqlTransaction1 przy użyciu izolacji migawki. W transakcji są wybrane trzy wiersze danych.  
  
- Tworzy drugie **SqlConnection** to **AdventureWorks** i tworzy drugą transakcję przy użyciu poziomu izolacji Read Committed, która aktualizuje wartość w jednym z wierszy wybranych w sqlTransaction1.  
  
- Zatwierdza sqlTransaction2.  
  
- Powraca do sqlTransaction1 i próbuje zaktualizować ten sam wiersz, który sqlTransaction1 już zatwierdzony. Błąd 3960 jest wywoływany, a sqlTransaction1 jest wycofywany automatycznie. **SqlException. Number** i **SqlException. Message** są wyświetlane w oknie konsoli.  
  
- Wykonuje czysty kod, aby wyłączyć izolację migawki w **AdventureWorks** i usunąć tabelę **TestSnapshotUpdate** .  
  
 [!code-csharp[DataWorks SnapshotIsolation.DemoUpdate#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SnapshotIsolation.DemoUpdate/CS/source.cs#1)]
 [!code-vb[DataWorks SnapshotIsolation.DemoUpdate#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SnapshotIsolation.DemoUpdate/VB/source.vb#1)]  
  
### <a name="using-lock-hints-with-snapshot-isolation"></a>Używanie wskazówek blokady z izolacją migawki  
 W poprzednim przykładzie pierwsza transakcja wybiera dane, a druga transakcji aktualizuje dane, zanim pierwsza transakcja jest w stanie zakończyć, powodując konflikt aktualizacji, gdy pierwsza transakcja próbuje zaktualizować ten sam wiersz. Można zmniejszyć prawdopodobieństwo konfliktu aktualizacji w długotrwałych transakcjach migawek, dostarczając wskazówki blokady na początku transakcji. Poniższa instrukcja SELECT używa wskazówki UPDLOCK, aby zablokować zaznaczone wiersze:  
  
```sql  
SELECT * FROM TestSnapshotUpdate WITH (UPDLOCK)   
  WHERE PriKey BETWEEN 1 AND 3  
```  
  
 Użycie wskazówki blokady UPDLOCK blokuje wszystkie wiersze próbujące zaktualizować wiersze przed ukończeniem pierwszej transakcji. Gwarantuje to, że w wybranych wierszach nie występują konflikty, gdy są one aktualizowane w dalszej części transakcji. Zobacz "wskazówki dotyczące blokowania" w temacie SQL Server Books Online.  
  
 Jeśli aplikacja ma wiele konfliktów, izolacja migawki może nie być najlepszym wyborem. Wskazówki powinny być używane tylko wtedy, gdy jest to konieczne. Aplikacja nie powinna być zaprojektowana tak, aby stale opierał się na wskazówkach blokady dla operacji.  
  
## <a name="see-also"></a>Zobacz także

- [SQL Server i ADO.NET](index.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
- [Przewodnik blokowania transakcji i obsługi wersji wierszy](/sql/relational-databases/sql-server-transaction-locking-and-row-versioning-guide)
