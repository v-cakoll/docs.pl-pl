---
title: Izolacja migawki w programie SQL Server
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 43ae5dd3-50f5-43a8-8d01-e37a61664176
caps.latest.revision: "6"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: a1d263f74f312b34c97f54cd970334017a797652
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="snapshot-isolation-in-sql-server"></a>Izolacja migawki w programie SQL Server
Izolacja migawki zwiększa współbieżności dla aplikacji OLTP.  
  
## <a name="understanding-snapshot-isolation-and-row-versioning"></a>Opis izolacji migawki i przechowywania wersji wierszy  
 Po włączeniu izolacji migawki wersji zaktualizowany wiersz dla każdej transakcji są obsługiwane w **tempdb**. Numer sekwencyjny transakcji unikatowy identyfikuje każdą transakcję i te unikatowe numery są rejestrowane dla każdej wersji wiersza. Transakcja współpracuje z najnowszymi wersjami wiersza, posiada numer sekwencji przed numer sekwencji transakcji. Nowsze wersje wierszy utworzonych po rozpoczęciu transakcji są ignorowane przez transakcję.  
  
 Termin "snapshot" odzwierciedla fakt, że wszystkie zapytania w transakcji Zobacz inna wersja lub migawka bazy danych, w zależności od stanu bazy danych w chwili rozpoczęcia transakcji. Nie blokad są uzyskiwane na stronach danych w transakcji migawki, która pozwala na inne transakcje bez blokowane przez wcześniejsze transakcji nieukończone lub wiersze danych. Transakcje, które modyfikują dane nie blokują transakcje, które zapoznały danych i transakcje, które zapoznały danych nie blokują transakcjami zapisu danych, tak jak zwykle w obszarze domyślnego poziomu izolacji READ COMMITTED w programie SQL Server. To zachowanie nieblokujące również znacznie ogranicza prawdopodobieństwo zakleszczenie złożonych transakcji.  
  
 Izolacja migawki używają modelu optymistycznej współbieżności. Jeśli transakcja migawki próbował zatwierdzić zmiany w danych, które uległy zmianie od chwili rozpoczęcia transakcji, transakcja cofnie i zostanie wygenerowany błąd. Można tego uniknąć, za pomocą UPDLOCK wskazówki dla instrukcji SELECT, które uzyskują dostęp do danych ma być zmodyfikowana. Aby uzyskać więcej informacji, zobacz "Wskazówki blokowania" w dokumentacji SQL Server — książki Online.  
  
 Izolacja migawki musi być włączony, ustawiając opcję bazy danych ALLOW_SNAPSHOT_ISOLATION przed jego użyciem w transakcji. Aktywuje mechanizm do przechowywania wersji wierszy w bazie danych tymczasowych (**tempdb**). Należy włączyć izolację migawki w każdej bazie danych, których używa go z instrukcji języka Transact-SQL ALTER DATABASE. W związku z tym izolację migawki różni się od poziomów tradycyjnych izolacji READ COMMITTED, REPEATABLE READ SERIALIZABLE i READ UNCOMMITTED, które nie wymagają konfiguracji. Poniższe instrukcje Aktywacja izolacji migawki i zastąpić domyślne zachowanie READ COMMITTED SNAPSHOT:  
  
```  
ALTER DATABASE MyDatabase  
SET ALLOW_SNAPSHOT_ISOLATION ON  
  
ALTER DATABASE MyDatabase  
SET READ_COMMITTED_SNAPSHOT ON  
```  
  
 Opcja READ_COMMITTED_SNAPSHOT ON zezwala na dostęp do określonej wersji wierszy w obszarze poziomu izolacji READ COMMITTED domyślne. Jeśli opcja READ_COMMITTED_SNAPSHOT ma wartość OFF, musisz jawnie ustawić poziom izolacji migawki dla każdej sesji Aby uzyskać dostęp do określonej wersji wierszy.  
  
## <a name="managing-concurrency-with-isolation-levels"></a>Zarządzanie współbieżności z poziomu izolacji  
 Poziom izolacji, pod którą wykonuje instrukcję Transact-SQL określa zachowanie przechowywania wersji wierszy i blokowania. Poziom izolacji ma zasięg połączenia i po ustawieniu dla połączenia z instrukcją Ustaw poziom izolacji transakcji pozostaje obowiązują do momentu połączenie jest zamknięte lub innego poziomu izolacji została ustawiona. Gdy połączenie jest zamknięte i zwrócony do puli, poziom izolacji od ostatniej instrukcji Ustaw poziom izolacji transakcji są zachowywane. Ponowne użycie połączenia z puli, który poziom izolacji, który był obowiązująca w momencie połączenia w puli kolejnych połączeń.  
  
 Pojedynczych zapytań wydane w ciągu połączenia może zawierać wskazówki blokady, zmodyfikuj izolację jednej instrukcji lub transakcji, które nie mają wpływu na poziom izolacji połączenia. Poziom izolacji lub wskazówki blokady ustawić procedury składowanej lub funkcji nie należy zmieniać poziom izolacji połączenia, które je wywołuje i obowiązują tylko na czas trwania wywołania procedury lub funkcji składowanej.  
  
 Czterech poziomów izolacji zdefiniowane w normie SQL 92 są obsługiwane w Wczesne wersje programu SQL Server:  
  
-   READ UNCOMMITTED jest najmniej restrykcyjny poziom izolacji, ponieważ ignoruje ona blokad umieszczonych przez inne transakcje. Wykonywanie w obszarze odczytu NIEZATWIERDZONE transakcje mogą odczytywać wartości zmodyfikowane dane, które nie zostało przekazane przez inne transakcje; są one nazywane "odczytów".  
  
-   READ COMMITTED jest domyślny poziom izolacji dla programu SQL Server. Zapobiega odczytów, określając, że instrukcji nie można odczytać wartości danych, które zostały zmodyfikowane, ale nie zostały jeszcze zatwierdzone przez inne transakcje. Inne transakcje nadal można zmodyfikować, Wstaw lub usunąć dane między wykonaniami pojedynczych instrukcji w bieżącej transakcji-powtarzalne odczyty lub "fantomu" danych.  
  
-   REPEATABLE READ jest bardziej restrykcyjne poziom izolacji niż READ COMMITTED. Obejmuje zatwierdzone odczytu, a ponadto określa, że żadne inne transakcje można zmodyfikować lub usunąć dane odczytane przez bieżącą transakcję do momentu zatwierdza bieżącej transakcji. Współbieżność jest niższa niż zatwierdzone odczytu, ponieważ udostępniony blokady odczytu danych są przechowywane na czas trwania transakcji zamiast udostępniane na końcu każdej instrukcji.  
  
-   Możliwy do SERIALIZACJI jest najbardziej restrykcyjne poziomu izolacji, ponieważ blokuje cały zakresy kluczy i przechowuje blokad, aż do ukończenia transakcji. Obejmuje POWTARZALNEGO odczytu, a dodaje ograniczenia inne transakcje nie można wstawić nowe wiersze do zakresów, które zapoznały przez transakcję do czasu ukończenia transakcji.  
  
 Aby uzyskać więcej informacji zobacz "Poziomów izolacji" w dokumentacji SQL Server — książki Online.  
  
### <a name="snapshot-isolation-level-extensions"></a>Rozszerzeń poziomu izolacji migawki  
 SQL Server wprowadzone rozszerzenia do poziomu izolacji SQL 92 z wprowadzenia poziom izolacji MIGAWKI i implementacja dodatkowe READ COMMITTED. Poziom izolacji READ_COMMITTED_SNAPSHOT niewidocznie zastąpić READ COMMITTED dla wszystkich transakcji.  
  
-   Izolacja MIGAWKI Określa, czy dane odczytane w obrębie transakcji nigdy nie zostaną one zastosowane zmiany wprowadzone przez innych równoczesnych transakcji. Transakcja korzysta z wersji wierszy danych znajdujące się po rozpoczęciu transakcji. Nie blokad są umieszczane w danych po jest do odczytu, więc transakcji MIGAWKI nie blokują inne transakcje zapisywania danych. Transakcje, które zapisywania danych nie blokują transakcji migawki odczytywania danych. Musisz włączyć izolację migawki przez ustawienie opcji bazy danych ALLOW_SNAPSHOT_ISOLATION, aby można było go używać.  
  
-   Bazy danych READ_COMMITTED_SNAPSHOT określa zachowanie poziomu izolacji READ COMMITTED domyślne włączenie izolację migawki w bazie danych. Jeśli nie zostanie jawnie READ_COMMITTED_SNAPSHOT ON, READ COMMITTED jest stosowany do wszystkich transakcji niejawnej. Daje to samo jak opcja READ_COMMITTED_SNAPSHOT wyłączone (ustawienie domyślne). Gdy READ_COMMITTED_SNAPSHOT poza jest włączone, aparatu bazy danych używa blokady współużytkowane wymusić domyślny poziom izolacji. Jeśli bazy danych READ_COMMITTED_SNAPSHOT jest ustawiona na wartość on, aparatu bazy danych używa izolacji wersji i migawki wiersza jako domyślny, zamiast blokady do ochrony danych.  
  
## <a name="how-snapshot-isolation-and-row-versioning-work"></a>Jak migawki izolacji i pracy przechowywania wersji wierszy  
 Po włączeniu poziom izolacji MIGAWKI, zawsze wiersz jest aktualizowany, aparatu bazy danych programu SQL Server jest przechowywana kopia oryginalnego wiersza w **tempdb**i dodaje kolejny numer transakcji do wiersza. Poniżej przedstawiono sekwencję zdarzeń, która występuje:  
  
-   Nowa transakcja jest inicjowane, i ma przypisany numer sekwencji transakcji.  
  
-   Aparat bazy danych odczytuje wiersz w obrębie transakcji i pobiera wersji wierszy z **tempdb** którego numer sekwencji jest znajdujący się najbliżej i mniejszy niż liczba sekwencji transakcji.  
  
-   Aparat bazy danych sprawdza Jeśli numer sekwencji transakcji nie jest na liście numerów sekwencyjnych niezatwierdzone transakcje aktywnej transakcji po rozpoczęciu transakcji migawki.  
  
-   Transakcja odczytuje wersji wiersza z **tempdb** która była bieżąca od rozpoczęcia transakcji. Nie będą widzieć nowe wiersze wstawione po transakcji został uruchomiony, ponieważ te wartości liczbowe sekwencji będzie wyższa niż wartość numer sekwencji transakcji.  
  
-   Bieżąca transakcja zostanie wyświetlony wierszy, które zostały usunięte po rozpoczęciu transakcji, ponieważ będzie wersji wierszy w **tempdb** z niższą wartość numeru sekwencji.  
  
 Net izolacji migawki powoduje, że transakcja widzi wszystkie dane, który istniał w chwili rozpoczęcia transakcji, bez ramach lub wprowadzania żadnych blokad na tabel. Może to spowodować ulepszenia wydajności w sytuacjach, w przypadku rywalizacji.  
  
 Transakcja migawki zawsze używa kontrolki optymistycznej współbieżności, wstrzymanie żadnych blokad, które uniemożliwiłyby inne transakcje aktualizowania wierszy. Jeśli transakcja migawki spróbuje przekazać aktualizację do wiersza, który został zmieniony po rozpoczęciu transakcji, transakcja zostanie wycofana i występuje błąd.  
  
## <a name="working-with-snapshot-isolation-in-adonet"></a>Praca z izolację migawki w ADO.NET  
 Izolacja migawki jest obsługiwana w ADO.NET przez <xref:System.Data.SqlClient.SqlTransaction> klasy. Jeśli została włączona dla izolacji migawki bazy danych, ale nie jest skonfigurowany dla READ_COMMITTED_SNAPSHOT ON, konieczne jest zainicjowanie <xref:System.Data.SqlClient.SqlTransaction> przy użyciu **IsolationLevel.Snapshot** wartość wyliczenia podczas wywoływania metody <xref:System.Data.SqlClient.SqlConnection.BeginTransaction%2A> Metoda. Fragmentu kodu zakłada, że połączenie jest otwarte <xref:System.Data.SqlClient.SqlConnection> obiektu.  
  
```vb  
Dim sqlTran As SqlTransaction = _  
  connection.BeginTransaction(IsolationLevel.Snapshot)  
```  
  
```csharp  
SqlTransaction sqlTran =   
  connection.BeginTransaction(IsolationLevel.Snapshot);  
```  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano zachowanie izolacji różne poziomy przez podejmowanie próby dostępu do danych zablokowane, a nie jest on przeznaczony do użycia w kodzie produkcyjnym.  
  
 Ten kod łączy się z **AdventureWorks** przykładowe bazy danych w programie SQL Server i tworzy tabelę o nazwie **TestSnapshot** i wstawia jeden wiersz danych. Kod używa instrukcji bazy danych języka Transact-SQL ALTER, aby włączyć funkcję izolacji migawki bazy danych, ale nie ustawia opcja READ_COMMITTED_SNAPSHOT, pozostawiając domyślne zachowanie poziomu izolacji READ COMMITTED obowiązywać. Kod następnie wykonuje następujące czynności:  
  
-   Rozpoczyna się, ale nie zostanie ukończone, sqlTransaction1, który używa poziomu izolacji o wartości SERIALIZABLE można uruchomić transakcji aktualizacji. Skutkuje to blokowania w tabeli.  
  
-   Otwiera drugie połączenie i inicjuje transakcję drugi przy użyciu poziomu izolacji MIGAWKI na odczytywanie danych w **TestSnapshot** tabeli. Ponieważ izolacja migawki jest włączona, ta transakcja mogą odczytywać dane, które istniały przed uruchomieniem sqlTransaction1.  
  
-   Otwiera połączenie trzeci i inicjuje transakcję przy użyciu poziomu izolacji zatwierdzone odczytu spróbował odczytać dane w tabeli. W takim przypadku kodu nie można odczytać danych, ponieważ nie można odczytać poza blokad umieszczone w tabeli w pierwszej transakcji i limit. Ten sam rezultat może mieć miejsce, jeśli poziom izolacji POWTARZALNEGO odczytu i SERIALIZABLE zostały użyte, ponieważ te poziomy izolacji także nie można odczytać poza blokad umieszczane w pierwszej transakcji.  
  
-   Otwiera połączenie czwarty i inicjuje transakcję przy użyciu poziomu izolacji odczytu NIEZATWIERDZONE wykonuje odczyt niezatwierdzonych wartości niezatwierdzone sqlTransaction1. Ta wartość nigdy może istnieć w bazie danych, jeśli pierwsza transakcja nie została przekazana.  
  
-   Przywraca stan sprzed pierwszej transakcji i czyści przez usunięcie **TestSnapshot** tabeli i wyłączenie izolację migawki **AdventureWorks** bazy danych.  
  
> [!NOTE]
>  W poniższych przykładach użyto tych samych parametrach połączenia z puli połączeń wyłączone. Połączenie w puli, resetowanie jego poziom izolacji nie powoduje resetowania poziom izolacji na serwerze. W związku z tym kolejnych połączeń używające tej samej puli połączeń wewnętrzny rozpoczynać się od ich izolacji ustawione poziomów do tej puli połączeń. Zamiast wyłączania puli połączeń jest ustawiony poziom izolacji jawnie dla każdego połączenia.  
  
 [!code-csharp[DataWorks SnapshotIsolation.Demo#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SnapshotIsolation.Demo/CS/source.cs#1)]
 [!code-vb[DataWorks SnapshotIsolation.Demo#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SnapshotIsolation.Demo/VB/source.vb#1)]  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano zachowanie funkcji izolacji migawki podczas modyfikacji danych. Kod wykonuje następujące czynności:  
  
-   Łączy się z **AdventureWorks** przykładowej bazy danych i umożliwia izolację MIGAWKI.  
  
-   Tworzy tabelę o nazwie **TestSnapshotUpdate** i wstawia trzy wiersze przykładowych danych.  
  
-   Rozpoczyna się, ale nie zostanie ukończone, sqlTransaction1 przy użyciu izolacji MIGAWKI. Trzy wiersze danych są zaznaczone w transakcji.  
  
-   Tworzy drugi **SqlConnection** do **AdventureWorks** i tworzy drugi transakcji przy użyciu poziomu izolacji READ COMMITTED aktualizuje wartość w jednym z wybranych w sqlTransaction1 wierszy.  
  
-   SqlTransaction2 zatwierdzeń.  
  
-   Zwraca sqlTransaction1 i prób aktualizacji w tym samym wierszu tej sqlTransaction1 już zadeklarowane. 3960 błąd i sqlTransaction1 jest przywracana automatycznie. **SqlException.Number** i **SqlException.Message** są wyświetlane w oknie konsoli.  
  
-   Wykonuje kod czyszczenia, aby wyłączyć izolację migawki w **AdventureWorks** i usunąć **TestSnapshotUpdate** tabeli.  
  
 [!code-csharp[DataWorks SnapshotIsolation.DemoUpdate#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SnapshotIsolation.DemoUpdate/CS/source.cs#1)]
 [!code-vb[DataWorks SnapshotIsolation.DemoUpdate#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SnapshotIsolation.DemoUpdate/VB/source.vb#1)]  
  
### <a name="using-lock-hints-with-snapshot-isolation"></a>Za pomocą wskazówki blokady z użyciem izolacji migawki  
 W poprzednim przykładzie pierwsza transakcja wybiera danych i druga transakcja aktualizuje dane przed Pierwsza transakcja jest w stanie wykonać, powoduje konflikt aktualizacji, jeśli pierwsza transakcja ma podejmować próbę aktualizacji w tym samym wierszu. Można zmniejszyć ryzyko wystąpienia konfliktów aktualizacji w transakcji migawki długotrwałe, podając wskazówki blokady na początku transakcji. Następująca instrukcja SELECT używa wskazówka UPDLOCK do zablokowania zaznaczone wiersze:  
  
```  
SELECT * FROM TestSnapshotUpdate WITH (UPDLOCK)   
  WHERE PriKey BETWEEN 1 AND 3  
```  
  
 Przy użyciu bloków wskazówki blokady UPDLOCK wszystkie wiersze podjęto próbę zaktualizowania wiersze przed zakończeniem pierwszej transakcji. Gwarantuje to, że zaznaczone wiersze mają żadne konflikty po zaktualizowaniu później w transakcji. Zobacz "Wskazówek blokowania" w dokumentacji SQL Server Books Online.  
  
 Jeśli aplikacja ma wiele konfliktów, izolacji migawki nie może być najlepszym rozwiązaniem. Wskazówek dotyczących serwerów należy używać tylko w przypadku, gdy są naprawdę potrzebne. Aplikacja nie należy tak zaprojektować, aby wykorzystuje on stale wskazówki blokady dla tej operacji.  
  
## <a name="see-also"></a>Zobacz też  
 [SQL Server i ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
