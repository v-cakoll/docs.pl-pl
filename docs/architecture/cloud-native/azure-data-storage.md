---
title: Magazyn danych na platformie Azure
description: Tworzenie architektury natywnych aplikacji .NET w chmurze dla platformy Azure | Magazyn danych na platformie Azure
ms.date: 06/30/2019
ms.openlocfilehash: ef9a83745b723dce90bc3e48eecbc9690fd386ab
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183631"
---
# <a name="data-storage-in-azure"></a>Magazyn danych na platformie Azure

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Jak widać w tej książce, Chmura zmienia sposób, w jaki aplikacje są zaprojektowane, wdrażane i zarządzane. W przypadku przejścia do chmury pytanie krytyczne polega na tym, jak przenieść dane? Na szczęście usługa Azure Cloud oferuje wiele opcji.

Możesz jedynie zainicjować obsługę administracyjną maszyny wirtualnej platformy Azure i zainstalować wybraną bazę danych. Jest to tzw. [infrastruktura jako usługa (IaaS)](https://www.techopedia.com/definition/141/infrastructure-as-a-service-iaas). Takie podejście upraszcza przeniesienie lokalnej bazy danych do chmury. jest to możliwe, ale przenosi to obciążenie związane z zarządzaniem maszyną wirtualną i bazą danych.  

Zamiast tego jest lepszym rozwiązaniem w pełni zarządzana [baza danych jako usługa (DBaaS)](https://www.stratoscale.com/blog/dbaas/what-is-database-as-a-service/) . Użytkownik otrzymuje wiele wbudowanych funkcji, gdy hosting, konserwacja i Licencjonowanie są zarządzane przez firmę Microsoft. Platforma Azure oferuje różne rodzaje w pełni zarządzanych opcji przechowywania danych, z których każdy ma określone zalety. Wszystkie te działy obsługują funkcję just in Time oraz model płatność zgodnie z rzeczywistym użyciem.

Będziemy dalej korzystać z opcji DBaaS dostępnych na platformie Azure. Zobaczysz, jak firma Microsoft kontynuuje zaangażowanie w utrzymywanie na platformie Azure "otwartej platformy", oferującej wsparcie zarządzane dla wielu baz danych relacyjnych i NoSQLych Open Source oraz wprowadzanie kluczowych udziałów do różnych wykrytych elementów Open Source jako aktywnego

## <a name="azure-sql-database"></a>Azure SQL Database

[Azure SQL Database](https://docs.microsoft.com/azure/sql-database/) to rozbudowana funkcja relacyjnej bazy danych ogólnego przeznaczenia jako usługi (DBaaS) oparta na aparacie Microsoft SQL Server Database. Jest ona w pełni zarządzana przez firmę Microsoft i jest wysoce wydajną, niezawodną i bezpieczną bazą danych w chmurze. Usługa udostępnia wiele funkcji dostępnych w lokalnej wersji programu SQL Server. 

Serwer SQL Database i bazę danych można zainicjować w kilka minut. Gdy zapotrzebowanie na aplikację rośnie od kilku klientów do milionów, Azure SQL Database skalowanie na bieżąco przy minimalnym przestoju. Można dynamicznie dodawać i usuwać zasoby, w tym moc procesora CPU, pamięć, przepływność we/wy i magazyn przydzieloną do baz danych.

Na rysunku 5-12 przedstawiono opcje wdrażania dla Azure SQL Database.

![Opcje wdrażania usługi Azure SQL](./media/azure-sql-database-deployment-options.png)

**Rysunek 5-12**. Opcje wdrażania usługi Azure SQL

Zanotuj alternatywy na poprzednim rysunku podczas wdrażania SQL Database:

- [Pojedyncza baza danych](https://docs.microsoft.com/azure/sql-database/sql-database-single-database) z własnym zestawem zasobów zarządzanych przez [serwer SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-servers). Pojedyncza baza danych jest podobna do [zawartej bazy danych](https://docs.microsoft.com/sql/relational-databases/databases/contained-databases) w lokalnym wdrożeniu SQL Server.

- [Pula elastyczna](https://docs.microsoft.com/azure/sql-database/sql-database-elastic-pool) , w której kolekcja baz danych SQL współużytkuje jeden serwer SQL Database z ustawioną ceną. Pojedyncze bazy danych można przenieść do i z elastycznej puli w miarę potrzeby w celu zoptymalizowania wydajności cen dla grupy baz danych.

- [Wystąpienie zarządzane](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) , w którym jest kolekcją baz danych systemu i użytkowników, zapewnia niemal 100% zgodności z lokalnym SQL Server. Ta opcja obsługuje większe bazy danych, do 35 TB i jest umieszczana w [Virtual Network platformy Azure](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview) w celu lepszego odizolowania.

Azure SQL Database to aparat bazy danych w pełni zarządzanej [platformy jako usługi (PaaS)](https://docs.microsoft.com/azure/sql-database/sql-database-paas) , który obsługuje uaktualnianie, stosowanie poprawek, kopii zapasowych i monitorowanie bez zaangażowania użytkowników. Zawsze działa Najnowsza stabilna wersja aparatu bazy danych SQL Server i poprawiony system operacyjny i gwarantuje dostępność na 99,99%. Jedna z funkcji, [Aktywna replikacja geograficzna](https://docs.microsoft.com/azure/sql-database/sql-database-active-geo-replication), umożliwia tworzenie odczytanych pomocniczych baz danych w tym samym lub innym centrum danych platformy Azure. W przypadku awarii można zainicjować tryb failover do pomocniczej bazy danych. W tym momencie inne pomocnicze serwery zostaną automatycznie połączone z nowym podstawowym. Maksymalnie cztery repliki pomocnicze są obsługiwane w tym samym lub w różnych regionach. te serwery pomocnicze mogą być również używane na potrzeby zapytań dostępu tylko do odczytu.

Azure SQL Database obejmuje [wbudowane funkcje monitorowania i inteligentnego dostrajania](https://docs.microsoft.com/azure/sql-database/sql-database-monitoring-tuning-index) , które mogą pomóc w maksymalizacji wydajności i zmniejszeniu kosztów operacyjnych. Na przykład funkcja [dostrajania automatycznego](https://docs.microsoft.com/azure/sql-database/sql-database-automatic-tuning) zapewnia ciągły sposób dostrajania wydajności na podstawie systemu AI i uczenia maszynowego. Usługa uczy się od uruchomionych obciążeń i może stosować zalecenia dotyczące dostrajania. Im dłuższy Azure SQL Database jest uruchamiany z włączoną funkcją dostrajania automatycznego, tym lepiej.

[Azure SQL Database bezserwerowe](https://docs.microsoft.com/azure/sql-database/sql-database-serverless) (dostęp do wersji zapoznawczej w czasie pisania tej książki) jest warstwą obliczeniową dla pojedynczych baz danych, które są automatycznie skalowane na podstawie zapotrzebowania na obciążenia, a opłaty są naliczane za ilość używanych obliczeń na sekundę. Warstwa obliczeniowa bezserwerowa również automatycznie wstrzymuje bazy danych w trakcie okresów nieaktywnych, aby rozliczać tylko opłaty za magazyn. Wznawia się automatycznie po powrocie działania.

Na koniec jest dostępna nowa warstwa cenowa [Azure SQL Database](https://azure.microsoft.com/services/sql-database/) . Jest on obsługiwany przez wysoce skalowalną architekturę magazynu i umożliwia zwiększenie wydajności bazy danych w miarę potrzeb, eliminując konieczność wstępnego udostępnienia zasobów magazynu. Zasoby obliczeniowe i magazynowe można skalować niezależnie, zapewniając elastyczność optymalizacji wydajności dla każdego obciążenia. Skalowanie Azure SQL Database jest zoptymalizowane pod kątem przetwarzania [OLTP](https://en.wikipedia.org/wiki/Online_transaction_processing) i obciążeń analitycznych o wysokiej przepływności z magazynem do 100 TB.  W przypadku obciążeń intensywnie korzystających z odczytu skalowanie umożliwia szybkie skalowanie w poziomie przez inicjowanie obsługi dodatkowych replik odczytu w miarę potrzeb do odciążania operacji odczytu. 

Oprócz tradycyjnego stosu Microsoft SQL Server platforma Azure oferuje także zarządzane wersje kilku popularnych baz danych typu open source.

## <a name="azure-database-for-mysql"></a>Azure Database for MySQL

[](https://en.wikipedia.org/wiki/MySQL)MySQL to [relacyjna baza danych](https://en.wikipedia.org/wiki/Relational_database_management_system) [Open Source](https://en.wikipedia.org/wiki/Open-source_software). Jest to składnik ze [stosu oprogramowania lampy](https://en.wikipedia.org/wiki/LAMP_(software_bundle)) i używany przez wiele dużych organizacji, w tym Facebook, Twitter i YouTube. Wersja Community jest dostępna bezpłatnie, a wersja Enterprise wymaga zakupu licencji. Pierwotnie utworzony w 1995, produkt został zakupiony przez firmę Sun Microsystems w 2008, który został uzyskany przez firmę Oracle w 2010.

[Azure Database for MySQL](https://azure.microsoft.com/services/mysql/) to w pełni zarządzana usługa relacyjnej bazy danych w przedsiębiorstwie oparta na aparacie serwera MySQL typu open source. Wdrożenie programu MySQL Community Edition obejmuje następujące możliwości PaaS bez dodatkowych kosztów:

- Wbudowana [wysoka dostępność](https://docs.microsoft.com/azure/mysql/concepts-high-availability).

- Przewidywalna wydajność przy użyciu [cen z płatnością zgodnie z rzeczywistym](https://docs.microsoft.com/azure/mysql/concepts-pricing-tiers)użyciem. 

- [Skalowanie](https://docs.microsoft.com/azure/mysql/concepts-high-availability) w razie konieczności w ciągu kilku sekund.

- Zabezpieczony, aby chronić poufne dane w czasie spoczynku i ruchowo.

- [Automatyczne kopie zapasowe](https://docs.microsoft.com/azure/mysql/concepts-backup) i [przywracanie do punktu w czasie](https://docs.microsoft.com/azure/mysql/concepts-backup) przez maksymalnie 35 dni.

- Bezpieczeństwo i zgodność klasy korporacyjnej.

Te wbudowane funkcje PaaS są ważne dla organizacji, które mają setki baz danych "taktycznych" (niestrategicznych) w swoich centrach danych, ale nie mają zasobów do wykonywania poprawek, kopii zapasowych, zabezpieczeń i monitorowania wydajności. 

Ponadto [usługa migracji danych platformy Azure](https://azure.microsoft.com/services/database-migration/) może migrować dane z wielu źródeł baz danych na platformy danych platformy Azure z minimalnym czasem przestoju. Usługa generuje raporty oceny i zawiera zalecenia, które przeprowadzą Cię przez zmiany wymagane do przeprowadzenia migracji, zarówno małych, jak i dużych.

Zarządzany [serwer usługi Azure MySQL](https://docs.microsoft.com/azure/mysql/concepts-servers) jest centralnym punktem administracyjnym usługi. Jest to ten sam aparat serwera MySQL używany do wdrożeń lokalnych. Dzięki niej można utworzyć pojedynczą bazę danych na każdym serwerze, aby korzystać z wszystkich zasobów, lub utworzyć wiele baz danych na serwer, aby udostępnić zasoby. Zespół może nadal opracowywać aplikacje za pomocą narzędzi typu "open source" i wybranej platformy bez konieczności uczenia się nowych umiejętności ani zarządzania maszynami wirtualnymi i infrastrukturą.

## <a name="azure-database-for-mariadb"></a>Azure Database for MariaDB

[MariaDB](https://mariadb.com/) Serwer jest innym popularnym serwerem baz danych open source. Został utworzony jako rozwidlenie MySQL przez pierwotnych deweloperów MySQL w momencie zakupionej przez firmę Oracle firmy Sun Microsystems, która jest własnością firmy MySQL. Celem było upewnienie się, że MariaDB pozostawała Open-Source.

Ponieważ MariaDB to [rozwidlenie programu MySQL](https://blog.panoply.io/a-comparative-vmariadb-vs-mysql), definicje danych i tabel są zgodne, a protokoły, struktury i interfejsy API są bliski-spojit. Łączniki danych MySQL będą działały MariaDB bez żadnych modyfikacji.

MariaDB jest silnie stosowana i jest używana przez wiele dużych przedsiębiorstw. Mimo że firma Oracle nadal utrzymuje, ulepsza i obsługuje MySQL, MariaDB jest zarządzana przez MariaDB Foundation, umożliwiając publicznego wkład do produktu i dokumentacji.

[Azure Database for MariaDB](https://azure.microsoft.com/services/mariadb/) to w pełni zarządzana baza danych jako usługa w chmurze platformy Azure. Jest on oparty na aparacie serwera [MariaDB Community Edition](https://mariadb.org/download/) . Może obsługiwać obciążenia o znaczeniu krytycznym z przewidywalną wydajnością i dynamiczną skalowalnością. Podobnie jak w przypadku innych platform usługi Azure Database, obejmuje wiele możliwości platformy jako usługi bez dodatkowych kosztów:

- Wbudowana [wysoka dostępność](https://docs.microsoft.com/azure/mariadb/concepts-high-availability).

- Przewidywalna wydajność przy użyciu [cen z płatnością zgodnie z rzeczywistym](https://docs.microsoft.com/azure/mariadb/concepts-pricing-tiers)użyciem. 
 
- [Skalowanie](https://docs.microsoft.com/azure/mariadb/concepts-high-availability) w razie konieczności w ciągu kilku sekund.

- Zabezpieczona ochrona poufnych danych przechowywanych i ruchowo.

- [Automatyczne kopie zapasowe](https://docs.microsoft.com/azure/mariadb/concepts-backup) i [przywracanie do punktu w czasie](https://docs.microsoft.com/azure/mariadb/concepts-backup) przez maksymalnie 35 dni.

- Bezpieczeństwo i zgodność klasy korporacyjnej.

## <a name="azure-database-for-postgresql"></a>Azure Database for PostgreSQL 

[PostgreSQL](https://www.postgresql.org/) to kolejna popularna relacyjna baza danych typu open source, która jest w ciągu 30 lat aktywnego programowania. Jest to system zarządzania bazami danych ogólnego przeznaczenia i obiektu. Jego Licencjonowanie jest uznawane za "zliberalizowane", a produkt jest bezpłatny do używania, modyfikowania i dystrybucji w dowolnej postaci. Wiele dużych przedsiębiorstw, takich jak Apple, Red Hat i Fujitsu, są zbudowane jako produkty korzystające z usługi PostgreSQL.

[Azure Database for PostgreSQL](https://azure.microsoft.com/services/postgresql/) to w pełni zarządzana usługa relacyjnej bazy danych w oparciu o aparat bazy danych Postgres typu open source. Może obsłużyć obciążenia o znaczeniu krytycznym z przewidywalną wydajnością, bezpieczeństwem, wysoką dostępnością i dynamiczną skalowalnością. Obsługuje ona kilka języków i platform "open source", w C++tym Java, Python, Node, C\#i php. Umożliwia ona [migrację](https://datamigration.microsoft.com/scenario/postgresql-to-azurepostgresql?step=1) baz danych PostgreSQL za pomocą interfejsu wiersza polecenia lub [usługi Azure Data Migration Service](https://azure.microsoft.com/services/database-migration/).

Usługa zawiera [wbudowaną analizę](https://docs.microsoft.com/azure/postgresql/concepts-monitoring) , która umożliwia badanie unikatowych wzorców baz danych i udostępnia dostosowane zalecenia i szczegółowe informacje ułatwiające zmaksymalizowanie wydajności bazy danych PostgreSQL. [Zaawansowana ochrona przed zagrożeniami](https://docs.microsoft.com/azure/postgresql/concepts-data-access-and-security-threat-protection) monitoruje bazę danych wokół zegara i wykrywa potencjalne złośliwe działania, co pozwala na natychmiastowe wykrycie.

Azure Database for PostgreSQL jest dostępna jako dwie opcje wdrażania: Pojedynczy serwer i funkcja do skalowania (Citus), dostępne w wersji zapoznawczej w czasie pisania tej książki

- Opcja wdrożenia [pojedynczego serwera](https://docs.microsoft.com/azure/postgresql/concepts-servers) to centralny punkt administracyjny dla wielu baz danych. Jest to ten sam aparat serwera PostgreSQL, który jest dostępny dla wdrożeń lokalnych. Dzięki niej można utworzyć pojedynczą bazę danych na każdym serwerze, która będzie korzystała ze wszystkich zasobów, lub utworzyć wiele baz danych, aby udostępnić zasoby. Ceny są ustalane na podstawie rdzeni i magazynu.

- [Opcja Citus)](https://azure.microsoft.com/blog/get-high-performance-scaling-for-your-azure-database-workloads-with-hyperscale/) jest obsługiwana przez technologię [danych](https://www.citusdata.com/) Citus. Umożliwia skalowanie o wysokiej wydajności przez skalowanie pojedynczej bazy danych na setki węzłów w celu zapewnienia szybkiej wydajności i skalowania niezwykle. Ta opcja umożliwia aparatowi dopasowanie większej ilości danych do pamięci, zrównoleglanie zapytań na setki węzłów oraz szybsze indeksowanie danych. Funkcja przedskalowania jest zgodna z najnowszymi innowacje, wersjami i narzędziami dla programu PostgreSQL, dzięki czemu możesz korzystać z istniejącej ekspertyzy PostgreSQL.

## <a name="cosmos-db"></a>Cosmos DB

Azure Cosmos DB to w pełni zarządzana, globalnie dystrybuowana usługa bazy danych NoSQL, która została zaprojektowana w celu zapewnienia małych opóźnień, elastycznej skalowalności, spójności danych zarządzanych i wysokiej dostępności. W krótkim przypadku, jeśli aplikacja wymaga zagwarantowania szybkiego czasu odpowiedzi w dowolnym miejscu na świecie, jeśli jest wymagane, aby zawsze była w trybie online i była nieograniczona i elastyczna skalowalność przepływności i magazynu, Cosmos DB to doskonały wybór. Rysunek 5-13 zawiera ogólne omówienie Cosmos DB.

![Omówienie Cosmos DB](./media/cosmos-db-overview.png)

**Rysunek 5-13**: Omówienie Cosmos DB

Zwróć uwagę na rysunek 5-13 jak Cosmos DB jest niezawodna i wysoce uniwersalna usługa bazy danych z wieloma wbudowanymi możliwościami macierzystymi w chmurze. W tej sekcji zajmiemy się nimi bliżej.

### <a name="global-support"></a>Globalna obsługa

Można globalnie dystrybuować bazy danych Cosmos we wszystkich regionach świadczenia usługi Azure na całym świecie, umieszczając dane blisko użytkowników, ulepszać czas odpowiedzi i redukując opóźnienia. Bazę danych można dodać lub usunąć z regionu bez wstrzymywania lub ponownego wdrażania aplikacji. W tle Cosmos DB w sposób przezroczysty replikuje dane do wszystkich skonfigurowanych regionów.

Cosmos DB obsługuje [aktywną/aktywną](https://kemptechnologies.com/white-papers/unfog-confusion-active-passive-activeactive-load-balancing/) klastrowanie na poziomie globalnym, umożliwiając Konfigurowanie dowolnego lub wszystkich regionów bazy danych do obsługi zarówno zapisu, jak i odczytu.

Funkcja [wieloskładnikowego](https://docs.microsoft.com/azure/cosmos-db/how-to-multi-master) protokołu w Cosmos DB umożliwia korzystanie z następujących funkcji:

- Nieograniczone elastyczne zapisywanie i skalowalność.

- 99,999% dostępności odczytu i zapisu na całym świecie.

- Gwarantowane odczyty i zapisy obsługiwane w czasie krótszym niż 10 milisekund w 99 percentylu.

Wewnętrznie program Cosmos DB obsługuje replikację danych między regionami z gwarancją poziomu spójności i finansowymi umowami dotyczącymi poziomu usług.

Korzystając z Cosmos DB [interfejsów API multihostingu](https://docs.microsoft.com/azure/cosmos-db/distribute-data-globally), aplikacja może automatycznie uzyskać dostęp do najbliższego regionu platformy Azure i wysyłać do niego żądania. Najbliższy region jest identyfikowany przez Cosmos DB bez żadnych zmian w konfiguracji. Jeśli region staje się niedostępny, Cosmos DB obsługuje automatyczne przełączanie do trybu failover, a funkcja Multihostingu automatycznie kieruje żądanie do następnego najbliższego dostępnego regionu.

### <a name="multi-model-support"></a>Obsługa wielomodelowa

Cosmos DB to *wielomodelowa platforma danych* umożliwiająca współdziałanie z danymi przy użyciu wielu obsługiwanych modeli NoSQL, w tym dokumentów, par klucz-wartość, szerokiej kolumny i reprezentacji grafów. Wewnętrznie dane są przechowywane w prostym formacie [struktury](https://docs.microsoft.com/dotnet/csharp/programming-guide/classes-and-structs/using-structs) składającym się z typów danych pierwotnych, takich jak ciągi, BOOLs i Numbers. Dla każdego żądania aparat bazy danych tłumaczy dane na wybraną reprezentację modelu. Można wybierać spośród Cosmos DB własnościowego interfejsu API opartego na języku SQL lub dowolnych [interfejsów API zgodności](https://www.wikiwand.com/en/Cosmos_DB) przedstawionych na rysunku 5-14.

![Dostawcy Cosmos DB](./media/cosmos-db-providers.png)

**Rysunek 5-14**: Dostawcy Cosmos DB

Zanotuj na rysunku 5-14, jak Cosmos DB obsługuje [Table Storage](https://azure.microsoft.com/services/storage/tables/). Zarówno Cosmos DB, jak i [Azure Table Storage](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview) współdzielą ten sam model tabeli i uwidaczniają wiele z tych samych operacji w tabeli. Jednak [interfejs API tabel Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/table-introduction) zawiera wiele ulepszeń Premium, które nie są dostępne w interfejsie API usługi Azure Storage. Te funkcje są zróżnicowane na rysunku 5-15.

![interfejs API tabel platformy Azure](./media/azure-table-api.png)

**Rysunek 5-15**: interfejs API tabel platformy Azure

Aplikacje przeznaczone dla usługi Azure Table Storage można migrować do Azure Cosmos DB przy użyciu interfejs API tabel bez zmian w kodzie.

W [brownfield] (https://en.wikipedia.org/wiki/Brownfield_(software_development) scenariusze aplikacji, zespoły programistyczne mogą migrować istniejące bazy danych Mongo, Gremlin lub Cassandra do Cosmos dB przy minimalnych zmianach w istniejących danych lub kodzie aplikacji. W scenariuszach [Greenfield](https://en.wikipedia.org/wiki/Greenfield_project) zespoły deweloperów mogą wybrać model danych, który najlepiej spełnia ich wymagania i preferencje, w tym w pełni obsługiwane opcje "open source" dla platform MongoDB, Cassandra i Gremlin.

### <a name="consistency-models"></a>Modeli spójności

Wcześniej w sekcji *relacyjnej i NoSQL* został omówiony temat *spójności danych*, czyli termin odnoszący się do integralności danych. Rozproszone bazy danych korzystające z replikacji w celu zapewnienia wysokiej dostępności, małych opóźnień lub obu muszą mieć zasadnicze kompromisy między spójnością odczytu, dostępnością i opóźnieniem.

Większość rozproszonych baz danych umożliwia deweloperom wybór dwóch modeli spójności: [silną spójność](https://en.wikipedia.org/wiki/Strong_consistency) i [spójność ostateczna](https://en.wikipedia.org/wiki/Eventual_consistency). *Silna spójność* to złoty standard programowania danych. Gwarantuje to, że wynik zapytania zawsze zwróci najbardziej aktualne dane, nawet jeśli system musi nawiązać opóźnienie oczekujące na przereplikację aktualizacji we wszystkich kopiach baz danych. Z drugiej strony system skonfigurowany pod kątem *spójności ostatecznej* zwróci dane natychmiast, nawet jeśli te dane nie są najbardziej aktualną kopią. Ta opcja zapewnia wyższą dostępność, większą skalę i zwiększoną wydajność.

Azure Cosmos DB oferuje szeroki zakres [pięciu dobrze zdefiniowanych modeli spójności](https://docs.microsoft.com/azure/cosmos-db/consistency-levels) przedstawionych na rysunku 5-16. Te opcje umożliwiają precyzyjne wybór i szczegółowe kompromisy w odniesieniu do dostępności i wydajności w zależności od potrzeb aplikacji. Modele te są dobrze zdefiniowane, intuicyjne i obsługiwane przez umowy dotyczące poziomu usług (umowy SLA). 

![Cosmos DB poziomów spójności](./media/cosmos-db-consistency-levels.png)

**Rysunek 5-16**: Cosmos DB poziomów spójności

### <a name="partitioning"></a>Partycjonowanie

Azure Cosmos DB używa automatycznego [partycjonowania](https://docs.microsoft.com/azure/cosmos-db/partitioning-overview) do skalowania bazy danych w celu spełnienia wymagań dotyczących wydajności aplikacji. 

Zarządzanie danymi w Cosmos DB danych przez tworzenie [baz danych, kontenerów i elementów](https://docs.microsoft.com/azure/cosmos-db/databases-containers-items)przedstawiono na rysunku 5-17.

![Jednostki Cosmos DB](./media/cosmos-db-entities.png)

**Rysunek 5-17**: Hierarchia Cosmos DB jednostek

Zanotuj na rysunku 5-17, jak zacząć od utworzenia bazy danych Cosmos DB w ramach konta platformy Azure. Ta baza danych jest jednostką zarządzania dla zestawu kontenerów. Kontener jest grupą niezależny od elementów, które mogą być wyrażone jako kolekcja, tabela lub Graf, w oparciu o wybranego dostawcę interfejsu API (omówione w poprzedniej sekcji). Elementy to dane, które można dodać do kontenera i są reprezentowane jako dokumenty, wiersze, węzły lub krawędzie. Domyślnie wszystkie elementy dodawane do kontenera są automatycznie indeksowane bez konieczności jawnego indeksowania lub zarządzania schematem.

Do partycjonowania kontenera elementy są podzielone na odrębne podzestawy o nazwie [partycje logiczne](https://docs.microsoft.com/azure/cosmos-db/partition-data). Partycje logiczne są tworzone na podstawie wartości klucza partycji, który jest skojarzony z każdym elementem w kontenerze. Rysunek 5-18 pokazuje, jak wszystkie elementy w partycji logicznej mają tę samą wartość klucza partycji.

![Mechanics partycjonowanie Cosmos DB](./media/cosmos-db-partitioning.png)

**Rysunek 5-18**: Mechanics partycjonowanie Cosmos DB

Zwróć uwagę na rysunek 5-18 jak każdy element zawiera klucz partycji "miasto" lub "Lotnisko". Ten klucz partycji Określa partycję logiczną elementu. Każdy kod miasta jest przypisywany do partycji logicznej w kontenerze po lewej stronie i z kodem lotniska do kontenera z prawej strony. Połączenie wartości klucza partycji z wartością identyfikatora elementu tworzy indeks elementu, który jednoznacznie identyfikuje element.

Wewnętrznie program Cosmos DB automatycznie zarządza umieszczaniem [partycji logicznych](https://docs.microsoft.com/azure/cosmos-db/partition-data) w [partycjach fizycznych](https://docs.microsoft.com/azure/cosmos-db/partition-data) , aby skutecznie spełnić wymagania dotyczące skalowalności i wydajności kontenera. W miarę wzrostu wymagań dotyczących przepływności i magazynowania aplikacji Azure Cosmos DB przenosi partycje logiczne, aby redystrybuować obciążenie na większą liczbę serwerów. Te operacje redystrybucji są zarządzane przez Cosmos DB i wykonywane bez przerwy ani przestojów.

## <a name="azure-redis-cache"></a>Azure Redis Cache

Zalety buforowania w celu poprawy wydajności i skalowalności. 

W przypadku aplikacji natywnej w chmurze wspólna lokalizacja służąca do dodawania buforowania znajduje się wewnątrz bramy interfejsu API. Brama służy jako fronton dla wszystkich żądań przychodzących. Dzięki dodaniu buforowania można zwiększyć wydajność i czas odpowiedzi, zwracając dane w pamięci podręcznej i unikając operacji rundy do lokalnej bazy danych lub usługi podrzędnej. Rysunek 5-19 przedstawia architekturę pamięci podręcznej dla aplikacji natywnej w chmurze.

![Buforowanie w aplikacji natywnej w chmurze](./media/caching-in-a-cloud-native-app.png)

**Rysunek 5-19**: Buforowanie w aplikacji natywnej w chmurze

Typowym wzorcem buforowania jest wzorzec z odkładaniem do [pamięci podręcznej](https://docs.microsoft.com/azure/architecture/patterns/cache-aside). W przypadku żądania przychodzącego należy najpierw wykonać zapytanie dotyczące pamięci podręcznej odpowiedzi, pokazanej w kroku #1 na rysunku 5-19. Jeśli ta wartość zostanie znaleziona, dane są zwracane natychmiast. Jeśli dane nie znajdują się w pamięci podręcznej (nazywanej brakiem [pamięci podręcznej](https://www.techopedia.com/definition/6308/cache-miss)), są pobierane z lokalnej bazy danych lub usługi podrzędnej (krok #2), zapisane w pamięci podręcznej w celu przyszłego żądania (krok #3) i zwracane do obiektu wywołującego. Należy zachować ostrożność, aby okresowo wykluczać dane z pamięci podręcznej, aby system był spójny i dokładny.

Ponadto Zwróć uwagę na rysunek 5-19, jak pamięć podręczna nie jest zaimplementowana lokalnie w granicach usługi, ale zamiast tego jest używana jako usługa do tworzenia kopii zapasowych oparta na chmurze, zgodnie z opisem w rozdziale 1.

[Azure Redis Cache](https://azure.microsoft.com/services/cache/) to usługa buforowania danych i brokera obsługi komunikatów. Zapewnia wysoką przepływność i dostęp do danych w przypadku małych opóźnień dla aplikacji. Jest ona w pełni zarządzana przez firmę Microsoft, hostowana na platformie Azure i dostępna dla każdej aplikacji w ramach platformy Azure lub poza nią.

Wewnętrznie usługa Azure cache for Redis jest obsługiwana przez [serwer Redis](https://redis.io/) typu open source i natywnie obsługuje struktury danych, takie jak [ciągi](https://redis.io/topics/data-types#strings), [skróty](https://redis.io/topics/data-types#hashes), [listy](https://redis.io/topics/data-types#sets), [zestawy](https://redis.io/topics/data-types#sets)i [zestawy posortowane](https://redis.io/topics/data-types#sorted-sets). Jeśli aplikacja używa Redis, będzie działała tak, jakby była usługą Azure cache for Redis.

Pamięć podręczna platformy Azure dla usługi Redis może być również używana jako pamięć podręczna danych w pamięci, rozproszona baza danych nierelacyjna i Broker komunikatów. Jest on dostępny w trzech różnych warstwach cenowych. Warstwa Premium oferuje wiele funkcji na poziomie przedsiębiorstwa, takich jak klastrowanie, trwałość danych, replikacja geograficzna oraz bezpieczeństwo i izolacja sieci wirtualnej.

>[!div class="step-by-step"]
>[Poprzedni](data-patterns.md)
>[Następny](resiliency.md) <!-- Next Chapter -->
