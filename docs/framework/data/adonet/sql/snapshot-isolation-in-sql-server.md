---
title: Izolacja migawki w programie SQL Server
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 43ae5dd3-50f5-43a8-8d01-e37a61664176
ms.openlocfilehash: 52c5dba1a21b0e8d8e5af1dc159941e5f4b4aa5f
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44221678"
---
# <a name="snapshot-isolation-in-sql-server"></a>Izolacja migawki w programie SQL Server
Izolacja migawki zwiększa współbieżności dla aplikacji OLTP.  
  
## <a name="understanding-snapshot-isolation-and-row-versioning"></a>Opis izolacji migawki i przechowywania wersji wierszy  
 Po włączeniu izolacji migawki wersji zaktualizowany wiersz dla każdej transakcji są obsługiwane w **bazy danych tempdb**. Numer sekwencyjny transakcji unikatowy identyfikuje każdej transakcji, a te unikatowe numery są rejestrowane dla każdej wersji wierszy. Transakcja współpracuje z najnowsze wersje wiersza, posiada numer sekwencji przed numer sekwencyjny transakcji. Nowsze wersje wiersza utworzone po rozpoczęciu transakcji są ignorowane przez transakcję.  
  
 Termin "snapshot" odzwierciedla fakt, że wszystkie zapytania w transakcji, zobacz inna wersja lub migawka bazy danych, w oparciu o stan bazy danych w tej chwili w czasie, gdy rozpoczyna się transakcja. Blokady nie są nabywane na wiersze danych lub stron danych w transakcji migawki, która pozwala na inne transakcje, które można wykonać bez blokowane przez wcześniejsze niedokończonej transakcji. Transakcje, które modyfikują dane nie blokują transakcje, które odczytują dane, a transakcje, które odczytują dane nie blokują transakcjami zapisu danych, tak jak zwykle w ramach domyślnego poziomu izolacji READ COMMITTED w programie SQL Server. To zachowanie, nieblokującą Ponadto znacząco zmniejsza prawdopodobieństwo zakleszczenia transakcji złożone.  
  
 Izolacja migawki używają modelu optymistycznej współbieżności. Jeśli transakcja migawki próbuje zatwierdzić modyfikacji danych, które uległy zmianie od chwili rozpoczęcia transakcji, transakcja zostanie wycofać i zostanie zgłoszony błąd. Można tego uniknąć, za pomocą UPDLOCK wskazówki dla instrukcji SELECT, uzyskujących dostęp do danych do zmodyfikowania. Aby uzyskać więcej informacji, zobacz "Ze sobą warunki blokady" w podręcznikach Online programu SQL Server.  
  
 Izolacja migawki musi być włączona przez ustawienie opcji bazy danych na ALLOW_SNAPSHOT_ISOLATION, zanim zostaną one użyte w transakcji. Aktywuje to mechanizm do przechowywania wersji wierszy w bazie danych tymczasowych (**bazy danych tempdb**). Należy włączyć izolację migawki w każdej bazie danych, która używa go za pomocą instrukcji języka Transact-SQL ALTER DATABASE. W związku z tym izolację migawki różni się od poziomów tradycyjnych izolacji READ COMMITTED, REPEATABLE READ, SERIALIZABLE i READ UNCOMMITTED, które nie wymagają konfiguracji. Poniższe instrukcje Aktywacja izolacji migawki i zastąpić domyślne zachowanie READ COMMITTED SNAPSHOT:  
  
```  
ALTER DATABASE MyDatabase  
SET ALLOW_SNAPSHOT_ISOLATION ON  
  
ALTER DATABASE MyDatabase  
SET READ_COMMITTED_SNAPSHOT ON  
```  
  
 Opcja READ_COMMITTED_SNAPSHOT ON umożliwia dostęp do wersjonowanych wierszy w ramach domyślnego poziomu izolacji READ COMMITTED. Jeśli opcja READ_COMMITTED_SNAPSHOT ma wartość OFF, należy jawnie ustawić poziom izolacji migawki dla każdej sesji, aby uzyskać dostęp do wersjonowanych wierszy.  
  
## <a name="managing-concurrency-with-isolation-levels"></a>Zarządzanie współbieżnością za poziomy izolacji  
 Poziom izolacji, w którym wykonuje instrukcję Transact-SQL określa jego zachowanie przechowywania wersji wierszy i blokowanie. Poziom izolacji ma połączenia na poziomie zakresu, a po ustawieniu dla połączenia z instrukcją Ustaw poziom izolacji transakcji, jego pozostaje, dopóki połączenie jest zamknięte lub innego poziomu izolacji została ustawiona. Gdy połączenie jest zamknięte i zwrócony do puli, poziom izolacji od ostatniej instrukcji Ustaw poziom izolacji transakcji są zachowywane. Ponowne użycie Użyj połączenia z puli, których poziom izolacji, który został obowiązuje w czasie połączenia w puli kolejnych połączeń.  
  
 Pojedynczych zapytań wydane w ciągu połączenia mogą zawierać wskazówki blokady, zmodyfikować izolacji transakcji lub pojedynczej instrukcji, ale nie ma wpływu na poziom izolacji połączenia. Poziomy izolacji lub Zablokuj podpowiedzi ustawione w procedurach składowanych lub funkcji, nie należy zmieniać poziom izolacji połączenia, które je wywołuje i są stosowane tylko na czas przechowywane wywołanie procedury lub funkcji.  
  
 Cztery poziomy izolacji, zdefiniowane w normie SQL 92 były obsługiwane w wcześniejsze wersje programu SQL Server:  
  
-   READ UNCOMMITTED jest najmniej restrykcyjny poziom izolacji, ponieważ ignoruje ona blokad umieszczonych przez inne transakcje. Wykonywanie w obszarze odczytu NIEZATWIERDZONE transakcje można odczytać wartości zmodyfikowane dane, które nie zostały jeszcze zatwierdzone przez inne transakcje; są one nazywane "odczytów".  
  
-   READ COMMITTED jest domyślny poziom izolacji dla programu SQL Server. Uniemożliwia ona odczytów, określając, że instrukcji nie można odczytać wartości danych, które zostały zmodyfikowane, ale nie zostały jeszcze zatwierdzone przez inne transakcje. Inne transakcje nadal można modyfikować, wstawiania lub usuwania danych między wykonaniami pojedyncze instrukcje w ramach bieżącej transakcji,-powtarzalnego odczytu lub data "fantomu".  
  
-   REPEATABLE READ jest bardziej restrykcyjny poziom izolacji, niż READ COMMITTED. Jego obejmuje zatwierdzone odczytu, a ponadto określa, że żadne inne transakcje modyfikować lub usuwać dane, który został odczytany przez bieżącą transakcję do czasu zatwierdzenia bieżącej transakcji. Współbieżność jest niższy niż w przypadku odczytu zatwierdzone, ponieważ udostępnionego blokady odczytu danych są przechowywane na czas trwania transakcji, a nie zostały udostępnione na końcu każdej instrukcji.  
  
-   Możliwy do SERIALIZACJI jest najbardziej restrykcyjny poziom izolacji, ponieważ umożliwia zablokowanie całych zakresów kluczy i posiada blokady do czasu ukończenia transakcji. On obejmuje odczyt POWTARZALNY i dodaje ograniczenie, które inne transakcje nie można wstawić nowe wiersze do zakresów, które zostały odczytane przez transakcję do czasu ukończenia transakcji.  
  
 Aby uzyskać więcej informacji zobacz "Poziomy izolacji" w podręcznikach Online programu SQL Server.  
  
### <a name="snapshot-isolation-level-extensions"></a>Rozszerzeń poziomu izolacji migawki  
 SQL Server wprowadził rozszerzenia do poziomu izolacji SQL 92 z wprowadzeniem poziomie izolacji MIGAWKI i implementację dodatkowych READ COMMITTED. Poziom izolacji READ_COMMITTED_SNAPSHOT przezroczyste zastąpić READ COMMITTED dla wszystkich transakcji.  
  
-   Izolacja MIGAWKI Określa, czy dane odczytane wewnątrz transakcji nigdy nie będzie odzwierciedlać zmiany wprowadzone przez innych równoczesnych transakcji. Transakcja korzysta z wersji wierszy danych, znajdujące się po rozpoczęciu transakcji. Blokady nie są umieszczane w danych podczas jej odczytywania tak transakcji MIGAWKI nie blokują inne transakcje z zapisywania danych. Transakcje zapisu danych nie blokują transakcji migawki na podstawie odczytu danych. Musisz włączyć izolację migawki przez ustawienie opcji bazy danych ALLOW_SNAPSHOT_ISOLATION, aby można było go używać.  
  
-   Bazy danych READ_COMMITTED_SNAPSHOT określa zachowanie domyślne poziomu izolacji READ COMMITTED, gdy izolacja migawki jest włączona w bazie danych. Jeśli nie zostanie jawnie READ_COMMITTED_SNAPSHOT ON, READ COMMITTED jest stosowany do wszystkich transakcji niejawnej. Daje to samo jak opcja READ_COMMITTED_SNAPSHOT wyłączone (ustawienie domyślne). Gdy READ_COMMITTED_SNAPSHOT wyłączone są włączone, aparatu bazy danych używa udostępnionego blokady do wymuszania domyślny poziom izolacji. Jeśli bazy danych READ_COMMITTED_SNAPSHOT jest ustawiona na wartość ON, aparat bazy danych używa izolacji migawki i przechowywania wersji wierszy jako domyślne, zamiast używania blokad, aby chronić dane.  
  
## <a name="how-snapshot-isolation-and-row-versioning-work"></a>Izolacja jak migawki i pracy przechowywania wersji wierszy  
 Gdy poziom izolacji SNAPSHOT jest włączona, każdorazowo zostanie zaktualizowany wiersz, aparatu bazy danych programu SQL Server przechowuje kopię oryginalnego wiersza w **bazy danych tempdb**i dodaje kolejny numer transakcji do wiersza. Poniżej przedstawiono sekwencję zdarzeń, który występuje:  
  
-   Nowa transakcja jest inicjowany, i ma przypisany numer sekwencyjny transakcji.  
  
-   Aparat bazy danych odczytuje wiersz w ramach transakcji i pobiera wersję wiersza z **bazy danych tempdb** którego numer sekwencji jest najbliżej i mniejsza niż numer sekwencyjny transakcji.  
  
-   Aparat bazy danych sprawdza, czy numer sekwencyjny transakcji nie jest na liście numerów sekwencyjnych transakcji niezatwierdzonych transakcji aktywne po uruchomieniu transakcji migawki.  
  
-   Transakcja odczytuje wersję wiersza od **bazy danych tempdb** było aktualne początku transakcji. Nie będą widoczne nowe wiersze wstawione po transakcja została uruchomiona, ponieważ te wartości liczbowe sekwencja będzie wyższa niż wartość numer sekwencyjny transakcji.  
  
-   Bieżąca transakcja zostanie wyświetlony wierszy, które zostały usunięte po chwili rozpoczęcia transakcji, ponieważ będzie istniało wersji wierszy w **bazy danych tempdb** z niższą wartość numeru sekwencji.  
  
 Net izolacji migawki powoduje, że transakcji widzi wszystkie dane, jaka istniała na początku transakcji, bez uznania lub wprowadzania żadnych blokad na tabel podstawowych. Może to spowodować ulepszenia wydajności w sytuacjach, w przypadku, gdy ma rywalizacji.  
  
 Transakcja migawki, który jest zawsze używa mechanizmu kontroli optymistycznej współbieżności, wstrzymanie żadnych blokad, które uniemożliwiłyby innych transakcji z aktualizowanie wierszy. Jeśli transakcja migawki próbuje zatwierdzić aktualizację do wiersza, który został zmieniony po chwili rozpoczęcia transakcji, transakcja zostanie wycofana i występuje błąd.  
  
## <a name="working-with-snapshot-isolation-in-adonet"></a>Praca z użyciem izolacji migawki w ADO.NET  
 Izolacja migawki jest obsługiwana w ADO.NET przez <xref:System.Data.SqlClient.SqlTransaction> klasy. Jeśli bazy danych dla izolację migawki zostało włączone, ale nie jest skonfigurowany dla READ_COMMITTED_SNAPSHOT ON, musisz zainicjować <xref:System.Data.SqlClient.SqlTransaction> przy użyciu **IsolationLevel.Snapshot** wartość wyliczenia podczas wywoływania <xref:System.Data.SqlClient.SqlConnection.BeginTransaction%2A> Metoda. Ten fragment kodu zakłada, że połączenie jest otwarty <xref:System.Data.SqlClient.SqlConnection> obiektu.  
  
```vb  
Dim sqlTran As SqlTransaction = _  
  connection.BeginTransaction(IsolationLevel.Snapshot)  
```  
  
```csharp  
SqlTransaction sqlTran =   
  connection.BeginTransaction(IsolationLevel.Snapshot);  
```  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak zachowanie izolacji różne poziomy, próbując uzyskać dostęp do danych zablokowane i nie jest on przeznaczony do użycia w kodzie produkcyjnym.  
  
 Kod umożliwia nawiązanie **AdventureWorks** przykładowe bazy danych w programie SQL Server i tworzy tabelę o nazwie **TestSnapshot** i wstawia jeden wiersz danych. Kod używa instrukcji ALTER DATABASE języka Transact-SQL, aby włączyć funkcję izolacji migawki bazy danych, ale nie ustawia opcja READ_COMMITTED_SNAPSHOT, pozostawiając domyślne zachowanie poziomu izolacji READ COMMITTED obowiązywać. Kod następnie wykonuje następujące czynności:  
  
-   Rozpoczyna się, ale nie zostanie ukończone, sqlTransaction1, korzystającą z poziomu izolacji o wartości SERIALIZABLE uruchomić transakcji aktualizacji. Skutkuje to blokowania w tabeli.  
  
-   Otwiera drugie połączenie i inicjuje drugi transakcji przy użyciu poziomu izolacji MIGAWKI na odczytywanie danych w **TestSnapshot** tabeli. Ponieważ izolacja migawki jest włączona, ta transakcja może odczytywać dane, które istniały przed rozpoczęciem sqlTransaction1.  
  
-   Otwiera trzecie połączenie i inicjuje transakcji przy użyciu poziomu izolacji COMMITTED odczytu spróbował odczytać dane w tabeli. W tym przypadku kod nie może odczytać dane ponieważ nie można odczytać ostatnie blokad umieszczone w tabeli w pierwszej transakcji i limit czasu. Ten sam wynik może wystąpić, jeśli poziomy izolacji POWTARZALNEGO odczytu i SERIALIZABLE zostały użyte, ponieważ te poziomy izolacji również nie można odczytać ostatnie blokad, umieszczane w pierwszej transakcji.  
  
-   Otwiera połączenie czwarty i inicjuje transakcji przy użyciu poziomu izolacji odczyt NIEPRZEKAZANY wykonuje odczyt niezatwierdzonych wartości niezatwierdzone sqlTransaction1. Ta wartość faktycznie nigdy nie może istnieć w bazie danych, jeśli pierwszy transakcja nie została zatwierdzona.  
  
-   Powoduje wycofanie transakcji pierwszym i czyści, usuwając **TestSnapshot** izolacji dla migawki w tabeli i wyłączenie **AdventureWorks** bazy danych.  
  
> [!NOTE]
>  W poniższych przykładach używane te same parametry połączenia z puli połączeń wyłączone. Połączenie w puli, zresetowanie jej poziom izolacji nie powoduje resetowania poziom izolacji na serwerze. Co w efekcie kolejne połączenia, które używają tej samej puli połączeń wewnętrzny rozpoczynać ich izolacji ustawionych poziomów do tej puli połączeń. Alternatywa wyłączenie buforowania połączeń jest ustawiony poziom izolacji jawnie dla każdego połączenia.  
  
 [!code-csharp[DataWorks SnapshotIsolation.Demo#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SnapshotIsolation.Demo/CS/source.cs#1)]
 [!code-vb[DataWorks SnapshotIsolation.Demo#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SnapshotIsolation.Demo/VB/source.vb#1)]  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano zachowanie izolacji migawki po zmodyfikowaniu danych. Kod wykonuje następujące czynności:  
  
-   Łączy się z **AdventureWorks** przykładowe bazy danych i umożliwia izolację MIGAWKI.  
  
-   Tworzy tabelę o nazwie **TestSnapshotUpdate** i wstawia trzy wiersze przykładowych danych.  
  
-   Rozpoczyna się, ale nie zostanie ukończone, sqlTransaction1 przy użyciu izolacji MIGAWKI. Trzy wiersze danych są wybierane w transakcji.  
  
-   Tworzy drugi **SqlConnection** do **AdventureWorks** i tworzy drugi transakcji przy użyciu poziomu izolacji READ COMMITTED zaktualizowanie wartości w jednym z wybranych w sqlTransaction1 wierszy.  
  
-   SqlTransaction2 zatwierdzeń.  
  
-   Zwraca sqlTransaction1, że została już przydzielona sqlTransaction1 i próbuje zaktualizować tego samego wiersza. 3960 błąd i sqlTransaction1 zostanie wycofana automatycznie. **SqlException.Number** i **SqlException.Message** są wyświetlane w oknie konsoli.  
  
-   Wykonuje kod czyszczenia, aby wyłączyć izolację migawki w **AdventureWorks** i Usuń **TestSnapshotUpdate** tabeli.  
  
 [!code-csharp[DataWorks SnapshotIsolation.DemoUpdate#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SnapshotIsolation.DemoUpdate/CS/source.cs#1)]
 [!code-vb[DataWorks SnapshotIsolation.DemoUpdate#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SnapshotIsolation.DemoUpdate/VB/source.vb#1)]  
  
### <a name="using-lock-hints-with-snapshot-isolation"></a>Za pomocą wskazówki blokady z użyciem izolacji migawki  
 W poprzednim przykładzie pierwszej transakcji wybiera dane, a druga transakcja aktualizuje dane, zanim pierwszej transakcji będzie mógł ukończyć, powodując konflikt aktualizacji, podczas pierwszej transakcji próbuje zaktualizować tego samego wiersza. Można zmniejszyć prawdopodobieństwo konflikty aktualizacji w długotrwałych transakcji migawki, podając wskazówki blokady na początku transakcji. Poniższa instrukcja SELECT używa wskazówka UPDLOCK zablokować wybrane wiersze:  
  
```  
SELECT * FROM TestSnapshotUpdate WITH (UPDLOCK)   
  WHERE PriKey BETWEEN 1 AND 3  
```  
  
 Przy użyciu bloków wskazówki blokady UPDLOCK wszystkie wiersze, które podjęto próbę zaktualizowania wiersze przed zakończeniem pierwszej transakcji. Gwarantuje to, że wybrane wiersze zostaną zaktualizowane w dalszej części transakcji, mają żadne konflikty. Zobacz "Blokowanie wskazówki" programu SQL Server — książki Online.  
  
 Jeśli aplikacja ma wiele konfliktów, izolacji migawki nie może być najlepszym wyborem. Wskazówki dotyczące powinna służyć wyłącznie po naprawdę potrzebne. Aplikacji nie powinna być zaprojektowana tak, aby stale opiera się na wskazówki blokady do swoich operacji.  
  
## <a name="see-also"></a>Zobacz też  
 [SQL Server i ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)  
 [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
