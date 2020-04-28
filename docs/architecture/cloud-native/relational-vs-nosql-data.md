---
title: Dane relacyjne a NoSQL
description: Informacje o relacyjnych i NoSQL danych w aplikacjach natywnych w chmurze
author: robvet
ms.date: 01/22/2020
ms.openlocfilehash: c074be0c973156c1757b97ffc727711d5dd072af
ms.sourcegitcommit: 5988e9a29cedb8757320817deda3c08c6f44a6aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2020
ms.locfileid: "82199989"
---
# <a name="relational-vs-nosql-data"></a>Dane relacyjne a NoSQL

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Relacyjne i NoSQL są dwa typy systemów baz danych, które są powszechnie zaimplementowane w aplikacjach natywnych w chmurze. Są one budowane inaczej, przechowują dane inaczej i są dostępne inaczej. W tej sekcji przejdziemy do obu tych elementów. W dalszej części tego rozdziału Przyjrzyjmy się nowemu technologii bazy danych o nazwie *NewSQL*.

*Relacyjne bazy danych* zostały rozpowszechnioną technologią dla dekad. Są one dojrzałe, sprawdzone i szeroko implementowane. Konkurencyjne produkty bazy danych, narzędzia i Abound wiedzy. Relacyjne bazy danych zapewniają magazyn powiązanych tabel danych. Te tabele mają stały schemat, używają programu SQL (Structured Query Language) do zarządzania danymi i obsługi gwarancji KWASowej.

*Bazy danych bez programu SQL nie* odnoszą się do magazynów o wysokiej wydajności, które nie są relacyjne. Są one w programie Excel w ich łatwość użycia, skalowalności, odporności i dostępności. Zamiast sprzęgać tabele znormalizowanych danych, NoSQL przechowuje dane bez struktury lub częściowo strukturalne, często w parach klucz-wartość lub dokumenty JSON. Nie — bazy danych SQL zazwyczaj nie zapewniają gwarancji KWAŚNych wykraczających poza zakres jednej partycji bazy danych. Usługi o dużych ilościach, które wymagają podrzędnego czasu odpowiedzi NoSQL datastores.

Nie można nadkładać wpływu technologii [NoSQL](https://www.geeksforgeeks.org/introduction-to-nosql/) na rozproszone systemy natywne w chmurze. Rozprzestrzenianie się nowych technologii danych w tym miejscu ma zakłócone rozwiązania, które są dostępne tylko w odniesieniu do relacyjnych baz danych.

Bazy danych NoSQL obejmują kilka różnych modeli do uzyskiwania dostępu do danych i zarządzania nimi, które są odpowiednie dla konkretnych przypadków użycia. Rysunek 5-9 przedstawia cztery popularne modele.

![NoSQL modele danych](./media/types-of-nosql-datastores.png)

**Rysunek 5-9**: modele danych dla baz danych NoSQL

| Model | Właściwości |
| :-------- | :-------- |
| Magazyn dokumentów | Dane i metadane są przechowywane hierarchicznie w dokumentach opartych na notacji JSON w bazie danych. |
| Magazyn wartości klucza | Najprostszym z baz danych NoSQL, dane są reprezentowane jako kolekcja par klucz-wartość. |
| Magazyn szerokiej kolumny | Powiązane dane są przechowywane jako zestaw zagnieżdżonych par klucz-wartość w jednej kolumnie. |
| Sklep Graph | Dane są przechowywane w strukturze grafu jako właściwości węzła, krawędzi i danych. |

## <a name="the-cap-theorem"></a>Theorem zakończenia

Aby zrozumieć różnice między tymi typami baz danych, należy wziąć pod uwagę limit theorem, zestaw zasad stosowanych w systemach rozproszonych, które są przechowywane w stanie. Rysunek 5-10 pokazuje trzy właściwości CAP theorem.

![Theorem CAP](./media/cap-theorem.png)

**Rysunek 5-10**. Theorem zakończenia

Theorem określa, że rozproszone systemy danych będą oferować kompromis między spójnością, dostępnością i tolerancją partycji. I, że każda baza danych może zagwarantować tylko *dwie* z trzech właściwości:

- *Zachowania.* Każdy węzeł w klastrze reaguje na najnowsze dane, nawet jeśli system musi zablokować żądanie do momentu aktualizacji wszystkich replik. W przypadku wykonywania zapytania o "spójny system" dla elementu, który jest obecnie aktualizowany, poczekaj na tę odpowiedź, dopóki wszystkie repliki nie zostaną pomyślnie zaktualizowane. Otrzymasz jednak najnowsze dane.

- *Opóźnienie.* Każdy węzeł zwraca natychmiastową odpowiedź, nawet jeśli ta odpowiedź nie jest najnowszymi danymi. W przypadku wysyłania zapytania do "dostępnego systemu" dla elementu, który jest aktualizowany, uzyskasz najlepszą możliwą odpowiedź, którą usługa może w tej chwili zapewnić.

- *Tolerancja partycji.* Gwarantuje, że system nadal działa nawet wtedy, gdy replikowany węzeł danych ulegnie awarii lub utraci łączność z innymi replikowanymi węzłami danych.

Relacyjne bazy danych zwykle zapewniają spójność i dostępność, ale nie tolerancję partycji. Są one zazwyczaj inicjowane na jednym serwerze i skalowanie w pionie poprzez dodanie większej liczby zasobów do maszyny.

Wiele systemów relacyjnych baz danych obsługuje wbudowane funkcje replikacji, w których kopie podstawowej bazy danych można wykonać w innych wystąpieniach serwera pomocniczego. Operacje zapisu są wykonywane w wystąpieniu podstawowym i replikowane do poszczególnych serwerów pomocniczych. Po awarii wystąpienie podstawowe może działać w trybie failover w celu zapewnienia wysokiej dostępności. Serwery pomocnicze mogą być również używane do dystrybucji operacji odczytu. Podczas gdy operacje zapisu są zawsze wykonywane względem repliki podstawowej, operacje odczytu mogą być kierowane do dowolnej z serwerów pomocniczych w celu ograniczenia obciążenia systemu.

Dane mogą również być podzielone na partycje w wielu węzłach, na przykład z [fragmentowania](https://docs.microsoft.com/azure/sql-database/sql-database-elastic-scale-introduction). Jednak fragmentowania znacząco zwiększa koszty operacyjne przez Spitting dane w wielu kawałkach, które nie mogą się łatwo komunikować. Zarządzanie nimi może być kosztowne i czasochłonne. Może to mieć wpływ na wydajność, sprzężenia tabel i integralność referencyjną.

Jeśli repliki danych zostały utracone w klastrze relacyjnej bazy danych "wysoce spójnym", nie będzie można zapisywać w bazie danych. System odrzuci operację zapisu, ponieważ nie może replikować zmiany do innej repliki danych. Każdą replikę danych należy zaktualizować przed ukończeniem transakcji.

Bazy danych NoSQL zazwyczaj obsługują wysoką dostępność i tolerancję partycji. Są one skalowane w poziomie, często na różnych serwerach. Takie podejście zapewnia ogromne dostępność, zarówno w regionie, jak i w regionach geograficznych, przy niższych kosztach. Można dzielić i replikować dane na tych maszynach lub w węzłach, zapewniając nadmiarowość i odporność na uszkodzenia. Minusem jest spójna. Zmiana danych w jednym węźle NoSQL może zająć trochę czasu do innych węzłów. Zazwyczaj węzeł bazy danych NoSQL będzie dostarczać natychmiastową odpowiedź do zapytania — nawet wtedy, gdy prezentowane dane są przestarzałe i nie zostały jeszcze zaktualizowane.

Jeśli repliki danych utraciły łączność w klastrze bazy danych NoSQL o wysokiej dostępności, można nadal wykonać operację zapisu w bazie danych. Klaster bazy danych zezwoli na operację zapisu i aktualizuje każdą replikę danych, gdy staną się dostępne.

Ten rodzaj wyników jest znany jako spójność ostateczna, charakterystyczne dla rozproszonych systemów danych, w których nie są obsługiwane transakcje KWASowe. Jest to krótkie opóźnienie między aktualizacją elementu danych i czasu potrzebnego do propagowania tej aktualizacji do poszczególnych węzłów repliki. W normalnych warunkach zwłoka jest zwykle krótka, ale może zwiększyć się w przypadku wystąpienia problemów. Na przykład, co się stanie w przypadku zaktualizowania elementu produktu w bazie danych NoSQL w Stany Zjednoczone i zazapytanie tego samego elementu danych z węzła repliki w Europie? Zostaną wyświetlone wcześniejsze informacje o produkcie, do momentu zaktualizowania węzła Europejskiego przy użyciu zmiany produktu przez klaster. Bezpośrednio zwracając wynik zapytania i nie czekając na aktualizację wszystkich węzłów repliki, uzyskasz olbrzymią skalę i pojemność, ale z możliwością prezentowania starszych danych.

Wysoka dostępność i ogromne skalowalność są często bardziej krytyczne dla działalności firmy niż silna spójność. Deweloperzy mogą zaimplementować techniki i wzorce, takie jak sagach, CQRS i asynchroniczne komunikaty, aby zachować spójność ostateczną.

> Obecnie należy zachować ostrożność podczas conidering ograniczeń theorem CAP. Nowy typ bazy danych o nazwie NewSQL, spowodował, że rozszerza aparat relacyjnej bazy danych w celu zapewnienia obsługi skalowalnej w poziomie i skalowalnej wydajności systemów NoSQL.

## <a name="considerations-for-relational-vs-nosql-systems"></a>Zagadnienia dotyczące systemów relacyjnych i NoSQL

W oparciu o określone wymagania dotyczące danych, Wielousługowa oparta na chmurze może zaimplementować relacyjny magazyn danych NoSQL lub oba te elementy.

|  Uwzględnij magazyn danych NoSQL, gdy: | Należy wziąć pod uwagę relacyjną bazę danych, gdy: |
| :-------- | :-------- |
| Masz duże obciążenia zbiorcze, które wymagają dużej skali | Wolumin obciążenia jest spójny i wymaga średniej do dużej skali |
| Twoje obciążenia nie wymagają gwarancji KWAŚNych |  Wymagane są gwarancje KWAŚNe |
| Dane są dynamiczne i często ulegają zmianie | Dane są przewidywalne i wysoce strukturalne |
| Dane można wyrazić bez relacji | Dane są najlepiej wyrażone w sposób relacyjny |  
| Potrzebne są szybkie zapisy i bezpieczeństwo zapisu nie jest krytyczne | Bezpieczeństwo zapisu jest wymagane |  
| Pobieranie danych jest proste i ma być płaskie | Pracujesz z złożonymi kwerendami i raportami|
| Dane wymagają szerokiej dystrybucji geograficznej | Użytkownicy są bardziej scentralizowani |
| Aplikacja zostanie wdrożona na sprzęcie z asortymentami, na przykład z chmurami publicznymi | Aplikacja zostanie wdrożona na dużym sprzęcie wysokiej klasy |
|||

W następnych sekcjach zapoznajemy się z opcjami dostępnymi w chmurze platformy Azure w celu przechowywania danych natywnych w chmurze i zarządzania nimi.

## <a name="database-as-a-service"></a>Baza danych jako usługa

Aby rozpocząć, można zainicjować obsługę administracyjną maszyny wirtualnej platformy Azure i zainstalować wybraną bazę danych dla każdej usługi. Mimo że masz pełną kontrolę nad środowiskiem, forgo wiele wbudowanych funkcji platformy w chmurze. Użytkownik jest również odpowiedzialny za zarządzanie maszyną wirtualną i bazą danych dla każdej usługi. Takie podejście może szybko stać się czasochłonne i kosztowne.

Zamiast tego aplikacje natywne w chmurze preferują usługi danych udostępniane jako [Usługa (DBaaS)](https://www.stratoscale.com/blog/dbaas/what-is-database-as-a-service/). W pełni zarządzane przez dostawcę chmury, te usługi zapewniają wbudowane zabezpieczenia, skalowalność i monitorowanie. Zamiast korzystać z usługi, wystarczy ją wykorzystać jako [usługę zapasową](./definition.md#backing-services). Dostawca obsługuje zasób w odpowiedniej skali i nosi odpowiedzialność za wydajność i konserwację.

Można je skonfigurować w strefach dostępności chmury i regionach w celu zapewnienia wysokiej dostępności. Wszystkie te działy obsługują funkcję just in Time oraz model płatność zgodnie z rzeczywistym użyciem. Platforma Azure oferuje różne rodzaje opcji usługi zarządzania danymi, z których każdy ma określone zalety.

Najpierw należy zapoznać się z relacyjnymi usługami DBaaS dostępnymi na platformie Azure. Zobaczysz, że baza danych sztandarowe SQL Server firmy Microsoft jest dostępna wraz z kilkoma opcjami "open source". Następnie porozmawiamy o usługach danych NoSQL na platformie Azure.

## <a name="azure-relational-databases"></a>Relacyjne bazy danych platformy Azure

W przypadku mikrousług natywnych w chmurze, które wymagają danych relacyjnych, platforma Azure oferuje cztery zarządzane relacyjne bazy danych jako usługi (DBaaS), pokazane na rysunku 5-11.

![Zarządzane relacyjne bazy danych na platformie Azure](./media/azure-managed-databases.png)

**Rysunek 5-11**. Zarządzane relacyjne bazy danych dostępne na platformie Azure

Na poprzedniej ilustracji należy zwrócić uwagę na to, jak każdy z nich znajduje się w oparciu o wspólną infrastrukturę DBaaS, która cechuje kluczowe możliwości bez dodatkowych kosztów.

Te funkcje są szczególnie ważne dla organizacji, które inicjują obsługę dużej liczby baz danych, ale mają ograniczone zasoby do ich administrowania.
Usługę Azure Database można zainicjować w kilka minut, wybierając liczbę rdzeni przetwarzania, pamięci i magazynu bazowego. Bazę danych można skalować na bieżąco i dynamicznie dostosowywać zasoby bez przestoju.

## <a name="azure-sql-database"></a>Azure SQL Database

Zespoły programistyczne z doświadczeniem w Microsoft SQL Server powinni rozważyć [Azure SQL Database](https://docs.microsoft.com/azure/sql-database/). Jest to w pełni zarządzana relacyjna baza danych jako usługa (DBaaS) oparta na aparacie Microsoft SQL Server Database. Usługa udostępnia wiele funkcji dostępnych w lokalnej wersji SQL Server i uruchamia najnowszą stabilną wersję aparatu bazy danych SQL Server Database.

Do użytku z mikrousługą natywną w chmurze Azure SQL Database jest dostępny z trzema opcjami wdrażania:

- Pojedyncza baza danych reprezentuje w pełni zarządzane SQL Database uruchomione na [serwerze Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-servers) w chmurze platformy Azure. Baza danych jest uznawana za [*zawartą*](https://docs.microsoft.com/sql/relational-databases/databases/contained-databases) , ponieważ nie ma żadnych zależności konfiguracji na źródłowym serwerze bazy danych.
  
- [Wystąpienie zarządzane](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) jest w pełni zarządzanym wystąpieniem aparatu bazy danych Microsoft SQL Server, które zapewnia niemal 100% zgodności z SQL Server lokalnymi. Ta opcja obsługuje większe bazy danych, do 35 TB i jest umieszczana w [Virtual Network platformy Azure](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview) w celu lepszego odizolowania.

- [Azure SQL Database bezserwerowy](https://docs.microsoft.com/azure/sql-database/sql-database-serverless) jest warstwą obliczeniową dla pojedynczej bazy danych, która automatycznie skaluje się w oparciu o zapotrzebowanie na obciążenie. Są one rozliczane tylko za ilość obliczeń użytych w ciągu sekundy. Usługa jest doskonale nadaje się do obciążeń z sporadycznymi, nieprzewidywalnymi wzorcami użycia, odplatanymi okresami braku aktywności. Warstwa obliczeniowa bezserwerowa również automatycznie wstrzymuje bazy danych w trakcie okresów nieaktywnych, aby rozliczać tylko opłaty za magazyn. Wznawia się automatycznie po powrocie działania.

Poza tradycyjnym stosem Microsoft SQL Server platforma Azure oferuje także zarządzane wersje trzech popularnych baz danych typu open source.

## <a name="open-source-databases-in-azure"></a>Bazy danych open source na platformie Azure

Relacyjne bazy danych typu open source stają się popularnym wyborem dla aplikacji natywnych w chmurze. Wiele przedsiębiorstw preferuje je za pośrednictwem produktów komercyjnej bazy danych, szczególnie w przypadku oszczędności kosztów. Wiele zespołów programistycznych korzysta z elastyczności, opracowywania przez społeczność i ekosystemów narzędzi i rozszerzeń. Bazy danych typu "open source" można wdrożyć dla wielu dostawców chmury, pomagając zminimalizować problem dotyczący "blokady dostawcy".

Deweloperzy mogą łatwo hostować dowolną bazę danych open source na maszynie wirtualnej platformy Azure. Zapewniając pełną kontrolę, ta metoda umożliwia przejście do punktu zaczepienia służącego do zarządzania, monitorowania i konserwacji bazy danych i maszyny wirtualnej.

Jednak firma Microsoft kontynuuje zobowiązania do utrzymania platformy Azure jako "otwartej platformy", oferując kilka popularnych baz danych open source jako w *pełni zarządzanych* usług DBaaS.

### <a name="azure-database-for-mysql"></a>Azure Database for MySQL

[MySQL](https://en.wikipedia.org/wiki/MySQL) to relacyjna baza danych typu open source oraz filar dla aplikacji zbudowanych na [stosie oprogramowania lampy](https://en.wikipedia.org/wiki/LAMP_(software_bundle)). Szeroko wybierany do *odczytu* dużych obciążeń, jest używany przez wiele różnych organizacji, w tym Facebook, Twitter i YouTube. Wersja Community jest dostępna bezpłatnie, podczas gdy wersja Enterprise wymaga zakupu licencji. Pierwotnie utworzony w 1995, produkt został zakupiony przez Sun Microsystems w 2008. Firma Oracle nabyła słońce i MySQL w 2010.

[Azure Database for MySQL](https://azure.microsoft.com/services/mysql/) to zarządzana usługa relacyjnej bazy danych oparta na aparacie serwera MySQL typu open source. Używa programu MySQL Community Edition. Serwer Azure MySQL jest punktem administracyjnym usługi. Jest to ten sam aparat serwera MySQL używany do wdrożeń lokalnych. Aparat może utworzyć pojedynczą bazę danych na serwer lub wiele baz danych na serwer, który współużytkuje zasoby. Można nadal zarządzać danymi za pomocą tych samych narzędzi "open source" bez konieczności uczenia się nowych umiejętności ani zarządzania maszynami wirtualnymi.

### <a name="azure-database-for-mariadb"></a>Azure Database for MariaDB

[MariaDB](https://mariadb.com/) Serwer jest innym popularnym serwerem baz danych open source. Został utworzony jako *rozwidlenie* MySQL, gdy firma Oracle zakupiła Sun Microsystems, który jest własnością MySQL. Celem było upewnienie się, że MariaDB pozostawała Open-Source. Ponieważ MariaDB to rozwidlenie programu MySQL, definicje danych i tabel są zgodne, a protokoły, struktury i interfejsy API są bliski-spojit.

MariaDB ma silną społeczność i jest używana przez wiele dużych przedsiębiorstw. Mimo że firma Oracle nadal utrzymuje, ulepsza i obsługuje MySQL, MariaDB Foundation zarządza MariaDB, umożliwiając publicznego wkład do produktu i dokumentacji.

[Azure Database for MariaDB](https://azure.microsoft.com/services/mariadb/) to w pełni zarządzana relacyjna baza danych jako usługa w chmurze platformy Azure. Usługa jest oparta na aparacie serwera MariaDB Community Edition. Może obsługiwać obciążenia o znaczeniu krytycznym z przewidywalną wydajnością i dynamiczną skalowalnością.

### <a name="azure-database-for-postgresql"></a>Azure Database for PostgreSQL

[PostgreSQL](https://www.postgresql.org/) to relacyjna baza danych typu "open source" z ponad 30-letnim aktywnym programowaniem. PostgresSQL ma silną reputację, aby zapewnić niezawodność i integralność danych. Funkcja jest zaawansowana, zgodna z językiem SQL i jest traktowana jako większa niż MySQL — szczególnie w przypadku obciążeń ze złożonymi zapytaniami i bardzo dużymi zapisami. Wiele dużych przedsiębiorstw, takich jak Apple, Red Hat i Fujitsu, są zbudowane jako produkty korzystające z usługi PostgreSQL.

[Azure Database for PostgreSQL](https://azure.microsoft.com/services/postgresql/) to w pełni zarządzana usługa relacyjnej bazy danych w oparciu o aparat bazy danych Postgres typu open source. Usługa obsługuje wiele platform deweloperskich, w tym C++, Java, Python, Node,\#C i php. Do tego celu można migrować bazy danych PostgreSQL przy użyciu narzędzia [interfejsu wiersza polecenia](https://datamigration.microsoft.com/scenario/postgresql-to-azurepostgresql?step=1) lub usługi Azure Data Migration Service.

Azure Database for PostgreSQL jest dostępny z dwiema opcjami wdrażania:

- Opcja wdrożenia [pojedynczego serwera](https://docs.microsoft.com/azure/postgresql/concepts-servers) to centralny punkt administracyjny dla wielu baz danych, w których można wdrożyć wiele baz danych. Ceny są ustalane na podstawie rdzeni i magazynu.

- [Opcja Citus)](https://azure.microsoft.com/blog/get-high-performance-scaling-for-your-azure-database-workloads-with-hyperscale/) jest obsługiwana przez technologię danych Citus. Zapewnia wysoką wydajność dzięki *skalowaniu w poziomie* pojedynczej bazy danych w setkach węzłów w celu zapewnienia szybkiej wydajności i skalowania. Ta opcja umożliwia aparatowi dopasowanie większej ilości danych do pamięci, zrównoleglanie zapytań na setki węzłów oraz szybsze indeksowanie danych.

## <a name="nosql-data-in-azure"></a>NoSQL danych na platformie Azure

Cosmos DB to w pełni zarządzana, globalnie dystrybuowana usługa bazy danych NoSQL w chmurze platformy Azure. Został on przyjęty przez wiele dużych firm na całym świecie, w tym Coca-receptura coli, Skype, ExxonMobil i wolności wzajemne.

Jeśli usługi wymagają szybkiej odpowiedzi z dowolnego miejsca na świecie, wysokiej dostępności lub elastycznej skalowalności, Cosmos DB to doskonały wybór. Rysunek 5-12 zawiera Cosmos DB.

![Omówienie Cosmos DB](./media/cosmos-db-overview.png)

**Rysunek 5-12**: Omówienie Cosmos DB

Powyższy rysunek przedstawia wiele wbudowanych funkcji natywnych w chmurze dostępnych w Cosmos DB. W tej sekcji zajmiemy się nimi bliżej.

### <a name="global-support"></a>Wsparcie globalne

Aplikacje natywne w chmurze często mają globalną grupę odbiorców i wymagają skali globalnej.

Można dystrybuować bazy danych Cosmos w różnych regionach lub na całym świecie, umieszczając dane blisko użytkowników, poprawiając czas odpowiedzi i redukując opóźnienia. Bazę danych można dodać lub usunąć z regionu bez wstrzymywania lub ponownego wdrażania usług. W tle Cosmos DB w sposób przezroczysty replikuje dane do każdego ze skonfigurowanych regionów.

Cosmos DB obsługuje klastrowanie [aktywne/aktywne](https://kemptechnologies.com/white-papers/unfog-confusion-active-passive-activeactive-load-balancing/) na poziomie globalnym, co umożliwia skonfigurowanie dowolnych regionów bazy danych do obsługi *zarówno zapisu, jak i odczytu*.

Protokół [wielu wzorców](https://docs.microsoft.com/azure/cosmos-db/multi-master-benefits) jest ważną funkcją w Cosmos DB, która zapewnia następujące funkcje:

- Nieograniczone elastyczne zapisywanie i skalowalność.

- 99,999% dostępności odczytu i zapisu na całym świecie.

- Gwarantowane odczyty i zapisy obsługiwane w czasie krótszym niż 10 milisekund w 99 percentylu.

Korzystając z Cosmos DB [interfejsów API multihostingu](https://docs.microsoft.com/azure/cosmos-db/distribute-data-globally), mikrousługi są automatycznie świadomi najbliższego regionu platformy Azure i wysyła do niego żądania. Najbliższy region jest identyfikowany przez Cosmos DB bez żadnych zmian w konfiguracji. Jeśli region staje się niedostępny, funkcja wiele Multihostingu będzie automatycznie kierować żądania do następnego najbliższego dostępnego regionu.

### <a name="multi-model-support"></a>Obsługa wielomodelowa

Podczas zmiany platformy monolitycznych aplikacji na architekturę natywną w chmurze, zespoły programistyczne czasami muszą migrować NoSQL magazyny danych typu open source. Cosmos DB może pomóc w zachowaniu inwestycji w te NoSQLe magazyny danych przy użyciu *wielomodelowej* platformy z danymi. Na rysunku 5-13 przedstawiono obsługiwane [interfejsy API zgodności](https://www.wikiwand.com/en/Cosmos_DB)NoSQL.

![Dostawcy Cosmos DB](./media/cosmos-db-providers.png)

**Rysunek 5-13**: dostawcy Cosmos DB

Zespoły programistyczne mogą migrować istniejące bazy danych Mongo, Gremlin lub Cassandra do Cosmos DB przy minimalnych zmianach w danych lub kodzie. W przypadku nowych aplikacji zespoły deweloperów mogą wybierać spośród opcji "open source" lub wbudowanego modelu interfejsu API SQL.

> Wewnętrznie Cosmos przechowuje dane w prostym formacie struktury składającym się z typów danych pierwotnych. Dla każdego żądania aparat bazy danych tłumaczy dane pierwotne na wybraną reprezentację modelu.

Na poprzedniej ilustracji 5-13 opcję [interfejs API tabel](https://docs.microsoft.com/azure/cosmos-db/table-introduction) . Ten interfejs API to ewolucja Table Storage platformy Azure. Oba te elementy mają ten sam model tabeli podstawowej, ale interfejs API tabel Cosmos DB dodaje usprawnienia Premium niedostępne w interfejsie API usługi Azure Storage. Te funkcje są zróżnicowane na rysunku 5-4.

![Interfejs API tabel platformy Azure](media/azure-table-api.png)

**Rysunek 5-14**: dostawcy interfejs API tabel platformy Azure

Mikrousługi korzystające z usługi Azure Table Storage można łatwo migrować do interfejs API tabel Cosmos DB. Nie są wymagane żadne zmiany w kodzie.

### <a name="tunable-consistency"></a>Możliwość dostosowania spójność

Wcześniej w sekcji *relacyjnej i NoSQL* został omówiony temat *spójności danych*. Spójność danych oznacza *integralność* danych. Usługi natywne w chmurze z rozproszonymi danymi są zależne od replikacji i muszą mieć zasadniczą kompromis między spójnością odczytu, dostępnością i opóźnieniem.

Większość rozproszonych baz danych umożliwia deweloperom wybór dwóch modeli spójności: silną spójność i spójność ostateczna. *Silna spójność* to złoty standard programowania danych. Gwarantuje to, że zapytanie zawsze zwróci najbardziej aktualne dane — nawet jeśli system musi nawiązać opóźnienie, czekając na przereplikację aktualizacji we wszystkich kopiach baz danych. Baza danych skonfigurowana pod kątem *spójności ostatecznej* zwróci dane natychmiast, nawet jeśli te dane nie są najbardziej aktualną kopią. Ta ostatnia opcja zapewnia wyższą dostępność, większą skalę i zwiększoną wydajność.

Azure Cosmos DB oferuje pięć dobrze zdefiniowanych [modeli spójności](https://docs.microsoft.com/azure/cosmos-db/consistency-levels) przedstawionych na rysunku 5-15.

![Wykres spójności Cosmos DB](./media/cosmos-consistency-level-graph.png)

**Rysunek 5-15**: Cosmos DB poziomów spójności

 Te opcje umożliwiają precyzyjne wybór i szczegółowe kompromisy dotyczące spójności, dostępności i wydajności danych. Rysunek 5-16 opisuje każdy poziom.

![Cosmos DB poziomów spójności](./media/cosmos-db-consistency-levels.png)

**Rysunek 5-16**: Cosmos DB opis poziomu spójności

W artykule w odnoszącym [się do 9-piłkę: Cosmos DB poziomów spójności wyjaśnione](https://blog.jeremylikness.com/blog/2018-03-23_getting-behind-the-9ball-cosmosdb-consistency-levels/)Microsoft Cloud, że deweloperzy rozwiązań deweloperskich Jeremy Likeness zapewnia doskonałe wyjaśnienie pięciu modeli.

### <a name="partitioning"></a>Partycjonowanie

Azure Cosmos DB obejmuje automatyczne [partycjonowanie](https://docs.microsoft.com/azure/cosmos-db/partitioning-overview) w celu skalowania bazy danych w celu spełnienia wymagań dotyczących wydajności usług natywnych w chmurze.

Zarządzanie danymi w Cosmos DB danych przez tworzenie baz danych, kontenerów i elementów.

Kontenery na żywo w bazie danych Cosmos DB i reprezentują grupowanie elementów w schemacie niezależny od. Elementy to dane dodawane do kontenera. Są one reprezentowane jako dokumenty, wiersze, węzły lub krawędzie. Wszystkie elementy dodane do kontenera są automatycznie indeksowane.

Do partycjonowania kontenera elementy są podzielone na odrębne podzestawy o nazwie partycje logiczne. Partycje logiczne są wypełniane na podstawie wartości klucza partycji, który jest skojarzony z każdym elementem w kontenerze. Rysunek 5-18 przedstawia dwa kontenery z partycji logicznej na podstawie wartości klucza partycji.

![Mechanics partycjonowanie Cosmos DB](./media/cosmos-db-partitioning.png)

**Rysunek 5-18**: Cosmos DB partycjonowanie Mechanics

Zwróć uwagę na powyższym rysunku, jak każdy element zawiera klucz partycji "City" lub "Lotnisko". Klucz Określa partycję logiczną elementu. Elementy o kodzie miejscowości są przypisywane do kontenera po lewej stronie i elementy z kodem lotniska, do kontenera po prawej stronie. Połączenie wartości klucza partycji z wartością identyfikatora tworzy indeks elementu, który jednoznacznie identyfikuje element.

Wewnętrznie program Cosmos DB automatycznie zarządza umieszczaniem [partycji logicznych](https://docs.microsoft.com/azure/cosmos-db/partition-data) w partycjach fizycznych w celu spełnienia wymagań dotyczących skalowalności i wydajności kontenera. W miarę wzrostu wymagań dotyczących przepływności i magazynu aplikacji Azure Cosmos DB redystrybuuje partycje logiczne na większą liczbę serwerów. Operacje redystrybucji są zarządzane przez Cosmos DB i wywoływane bez przeszkód lub przestojów.

## <a name="newsql-databases"></a>Bazy danych NewSQL

*NewSQL* to rozwijana technologia baz danych, która łączy rozproszoną skalowalność NoSQL przy użyciu gwarancji kwaśnych relacyjnej bazy danych. Bazy danych NewSQL są ważne dla systemów firmowych, które muszą przetwarzać duże ilości danych, w środowiskach rozproszonych, z pełną obsługą transakcyjną i zgodnością KWASów. Baza danych NoSQL może zapewniać ogromną skalowalność, ale nie gwarantuje spójności danych. Sporadyczne problemy z niespójnymi danymi mogą stanowić obciążenie zespołu deweloperów. Deweloperzy muszą konstruować zabezpieczenia w swoim kodzie mikrousług, aby zarządzać problemami spowodowanymi niespójnymi danymi.

Natywna platforma obliczeniowa w chmurze (CNCF) zawiera kilka projektów bazy danych NewSQL.

| Projekt | Właściwości |
| :-------- | :-------- |
| Baza danych Cockroach |Zgodna z KWASem relacyjna baza danych, która skaluje się globalnie. Dodaj nowy węzeł do klastra, a CockroachDB Zadbaj o zrównoważenie danych w różnych wystąpieniach i lokalizacje geograficzne. Tworzy, zarządza i dystrybuuje repliki w celu zapewnienia niezawodności. Jest to open source i dostępne bezpłatnie.  |
| TiDB | Baza danych open source, która obsługuje obciążenia hybrydowe i analityczne przetwarzania (HTAP). Jest to zgodne z bazą danych MySQL i funkcje skalowalności w poziomie, silnej spójności i wysokiej dostępności.  TiDB działa jak serwer MySQL. Można nadal używać istniejących bibliotek klienta programu MySQL, bez konieczności wprowadzania szczegółowych zmian w kodzie aplikacji. |
| YugabyteDB | Baza danych SQL Open Source o wysokiej wydajności i rozproszonej. Obsługuje ono małe opóźnienia zapytań, odporność na awarie i globalną dystrybucję danych. YugabyteDB jest zgodne z PostgressSQL i obsługuje skalowanie w poziomie, RDBMS i skalowanie Internetu. Produkt obsługuje również NoSQL i jest zgodny z Cassandra. |
|Vitess | Vitess to rozwiązanie bazy danych służące do wdrażania i skalowania dużych klastrów wystąpień MySQL oraz zarządzania nimi. Można go uruchomić w architekturze chmury publicznej lub prywatnej. Łączy i rozszerza wiele ważnych funkcji i funkcji programu MySQL zarówno w pionie, jak i w poziomie fragmentowania. Pochodzące z serwisu YouTube, Vitess obsłużył cały ruch bazy danych w usłudze YouTube od 2011. |

Projekty open source na powyższym rysunku są dostępne z natywnej platformy obliczeniowej w chmurze. Trzy oferty to produkty z pełnymi bazami danych, w tym obsługa platformy .NET Core. Druga, Vitess, jest systemem klastrowania bazy danych, który w poziomie skaluje duże klastry wystąpień MySQL.

Najważniejszym celem projektowania baz danych NewSQL jest natywne działanie w Kubernetes, dzięki czemu można korzystać z odporności i skalowalności platformy.

Bazy danych NewSQL są przeznaczone do rozpoczęcia pracy w tymczasowych środowiskach w chmurze, w których można ponownie uruchomić maszyny wirtualne lub ponownie zaplanować ich ponowne zaplanowanie. Bazy danych są przeznaczone do obsłużenia awarii węzłów bez utraty danych ani przestojów. CockroachDB, na przykład, może przetrwać utratę maszyny przez utrzymywanie trzech spójnych replik wszelkich danych w węzłach w klastrze.

Kubernetes używa *konstrukcji usług* , aby umożliwić klientowi adresowanie grupy identycznych procesów baz danych NewSQL z jednego wpisu DNS. Poprzez oddzielenie wystąpień bazy danych od adresu usługi, z którą jest ona skojarzona, możemy skalować bez zakłócania istniejących wystąpień aplikacji. Wysłanie żądania do dowolnej usługi w danym momencie zawsze zwróci ten sam wynik.

W tym scenariuszu wszystkie wystąpienia bazy danych są równe. Brak relacji podstawowej lub pomocniczej. Techniki, takie jak *jednomyślna replikacja* znaleziono w CockroachDB, zezwalają dowolnym węzłowi bazy danych na obsługę dowolnego żądania. Jeśli węzeł, który odbiera żądanie o zrównoważonym obciążeniu, ma wymagane dane lokalnie, reaguje natychmiast. W przeciwnym razie węzeł jest bramą i przekazuje żądanie do odpowiednich węzłów w celu uzyskania prawidłowej odpowiedzi. Z punktu widzenia klienta każdy węzeł bazy danych jest taki sam: pojawia się jako pojedyncza *logiczna* baza danych z gwarancjami spójności jednego systemu komputera, pomimo że mają dziesiątki lub nawet setki węzłów, które działają w tle.

Aby zapoznać się ze szczegółowymi informacjami o Mechanics za bazami danych NewSQL, zobacz [myślnik: cztery właściwości artykułu bazy danych Kubernetes-Native](https://thenewstack.io/dash-four-properties-of-kubernetes-native-databases/) .

## <a name="data-migration-to-the-cloud"></a>Migracja danych do chmury

Jednym z bardziej czasochłonnych zadań jest Migrowanie danych z jednej platformy danych do innej. [Usługa migracji danych platformy Azure](https://azure.microsoft.com/services/database-migration/) może ułatwić przyspieszenie takich wysiłków. Umożliwia Migrowanie danych z kilku zewnętrznych źródeł baz danych do platformy danych platformy Azure z minimalnym przestojem. Platformy docelowe obejmują następujące usługi:

- Azure SQL Database
- Azure Database for MySQL
- Azure Database for MariaDB
- Azure Database for PostgreSQL
- CosmosDB
  
Usługa zawiera zalecenia, które przeprowadzą Cię przez zmiany wymagane do przeprowadzenia migracji, zarówno małych, jak i dużych.

>[!div class="step-by-step"]
>[Poprzedni](distributed-data.md)
>[Następny](azure-caching.md)
