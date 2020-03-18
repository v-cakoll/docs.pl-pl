---
title: Relacyjne a dane NoSQL
description: Dowiedz się więcej o danych relacyjnych i NoSQL w aplikacjach natywnych dla chmury
author: robvet
ms.date: 01/22/2020
ms.openlocfilehash: 04693e30ba3848f1e51f1c69a75be5f18ead4cf1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141422"
---
# <a name="relational-vs-nosql-data"></a>Relacyjne a dane NoSQL

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Relacyjne i NoSQL to dwa typy systemów baz danych często implementowanych w aplikacjach natywnych dla chmury. Są one zbudowane inaczej, przechowują dane w różny sposób i mają inny dostęp. W tej sekcji przyjrzymy się obu. W dalszej części tego rozdziału przyjrzymy się powstającej technologii bazy danych o nazwie *NewSQL*.

*Relatory baz danych* są rozpowszechnioną technologią od dziesięcioleci. Są dojrzałe, sprawdzone i szeroko wdrażane. Konkurencyjne produkty bazy danych, oprzyrządowanie i wiedza specjalistyczna obfitują. Relatory bazy danych zapewniają magazyn powiązanych tabel danych. Te tabele mają stały schemat, użyj SQL (Structured Query Language) do zarządzania danymi i obsługuje gwarancje ACID.

*Bazy danych no-SQL* odnoszą się do wysokiej wydajności, nierelacyjnych magazynów danych. Wyróżniają się łatwością obsługi, skalowalnością, odpornością i dostępnością. Zamiast łączyć tabele znormalizowanych danych, NoSQL przechowuje dane nieustrukturyzowane lub częściowo ustrukturyzowane, często w parach klucz-wartość lub dokumentach JSON. Bazy danych bez SQL zazwyczaj nie zapewniają gwarancji ACID poza zakresem pojedynczej partycji bazy danych. Usługi o dużej objętości, które wymagają czasu odpowiedzi poniżej drugiego, faworyzują magazyny danych NoSQL.

Wpływ technologii [NoSQL](https://www.geeksforgeeks.org/introduction-to-nosql/) na systemy rozproszone natywne dla chmury nie może być zawyżony. Rozprzestrzenianie się nowych technologii danych w tej przestrzeni zakłóciło rozwiązania, które kiedyś opierały się wyłącznie na relacyjnych bazach danych.

Bazy danych NoSQL zawierają kilka różnych modeli uzyskiwania dostępu do danych i zarządzania nimi, z których każdy nadaje się do określonych przypadków użycia. Rysunek 5-9 przedstawia cztery wspólne modele.

![Modele danych NoSQL](./media/types-of-nosql-datastores.png)

**Rysunek 5-9**: Modele danych dla baz danych NoSQL

| Model | Właściwości |
| :-------- | :-------- |
| Magazyn dokumentów | Dane i metadane są przechowywane hierarchicznie w dokumentach opartych na JSON wewnątrz bazy danych. |
| Magazyn wartości kluczy | Najprostszyz baz danych NoSQL, dane są reprezentowane jako zbiór par klucz wartość. |
| Sklep z szerokimi kolumnami | Powiązane dane są przechowywane jako zestaw par zagnieżdżonych klucz/wartość w jednej kolumnie. |
| Sklep z wykresami | Dane są przechowywane w strukturze wykresu jako właściwości węzła, krawędzi i danych. |

## <a name="the-cap-theorem"></a>Wpr

Aby zrozumieć różnice między tymi typami baz danych, należy wziąć pod uwagę twierdzenie WPR, zbiór zasad stosowanych do systemów rozproszonych, które przechowują stan. Rysunek 5-10 przedstawia trzy właściwości orszaków WPR.

![WPR – powszewierzenie](./media/cap-theorem.png)

**Rysunek 5-10**. Wpr

Twierdzenie stwierdza, że systemy danych rozproszonych będzie oferować kompromis między spójności, dostępności i tolerancji partycji. I, że każda baza danych może zagwarantować tylko *dwie* z trzech właściwości:

- *Spójności.* Każdy węzeł w klastrze odpowiada z najnowszymi danymi, nawet jeśli system musi zablokować żądanie, dopóki wszystkie repliki nie zostaną zaktualizowane. Jeśli kwerenda "spójny system" dla elementu, który jest aktualnie aktualizowany, będziesz czekać na tę odpowiedź, aż wszystkie repliki pomyślnie zaktualizować. Jednak otrzymasz najbardziej aktualne dane.

- *Dostępność.* Każdy węzeł zwraca natychmiastową odpowiedź, nawet jeśli ta odpowiedź nie jest najnowszymi danymi. Jeśli zapytasz o "dostępny system" dla elementu, który jest aktualizowany, otrzymasz najlepszą możliwą odpowiedź, jaką usługa może zapewnić w tym momencie.

- *Tolerancja partycji.* Gwarantuje, że system będzie nadal działać, nawet jeśli zreplikowany węzeł danych ulegnie awarii lub utraci łączność z innymi replikowanymi węzłami danych.

Relacyjne bazy danych zazwyczaj zapewniają spójność i dostępność, ale nie tolerancję partycji. Zazwyczaj są one aprowizowane do jednego serwera i skalować w pionie, dodając więcej zasobów do komputera.

Wiele relacyjnych systemów baz danych obsługuje wbudowane funkcje replikacji, w których kopie podstawowej bazy danych mogą być dokonywane do innych wystąpień serwera pomocniczego. Operacje zapisu są dokonywane w wystąpieniu podstawowym i replikowane do każdego z dodatkowych. W przypadku awarii wystąpienia podstawowego można przejść awaryjnie do pomocniczego, aby zapewnić wysoką dostępność. Pomocnicze mogą być również używane do dystrybucji operacji odczytu. Podczas gdy operacje zapisu zawsze są sprzeczne z repliką podstawową, operacje odczytu mogą być kierowane do dowolnego pomocniczego, aby zmniejszyć obciążenie systemu.

Dane mogą być również podzielone poziomo na wiele węzłów, takich jak z [dzielenia na rozdęcia](https://docs.microsoft.com/azure/sql-database/sql-database-elastic-scale-introduction). Jednak odłamki znacznie zwiększają obciążenie operacyjne, plując dane na wiele elementów, które nie mogą łatwo się komunikować. Zarządzanie może być kosztowne i czasochłonne. Może skończyć się wpływ na wydajność, sprzężenia tabeli i więzów integralności.

Jeśli repliki danych miałyby utracić łączność sieciową w "wysoce spójnym" klastrze relacyjnych baz danych, nie można zapisać w bazie danych. System odrzuci operację zapisu, ponieważ nie może replikować tej zmiany do innej repliki danych. Każda replika danych musi zostać zaktualizowana przed zakończeniem transakcji.

Bazy danych NoSQL zazwyczaj obsługują wysoką dostępność i tolerancję partycji. Są one skalowane poziomo, często na serwerach towarowych. Takie podejście zapewnia ogromną dostępność, zarówno w obrębie regionów geograficznych, jak i między nimi, przy niższych kosztach. Partycjonowanie i replikowanie danych między tymi komputerami lub węzłami, zapewniając nadmiarowość i odporność na uszkodzenia. Minusem jest spójność. Zmiana danych w jednym węźle NoSQL może zająć trochę czasu, aby propagować do innych węzłów. Zazwyczaj węzeł bazy danych NoSQL zapewni natychmiastową odpowiedź na kwerendę — nawet jeśli prezentowane dane są przestarzałe i nie zostały jeszcze zaktualizowane.

Jeśli repliki danych miałyby utracić łączność w "wysoce dostępnym" klastrze bazy danych NoSQL, nadal można ukończyć operację zapisu w bazie danych. Klaster bazy danych pozwoli na operację zapisu i zaktualizować każdą replikę danych, gdy stanie się dostępna.

Ten rodzaj wyniku jest znany jako spójność ostateczna, cecha rozproszonych systemów danych, w których transakcje ACID nie są obsługiwane. Jest to krótkie opóźnienie między aktualizacją elementu danych a czasem potrzebnym do propagowania tej aktualizacji do każdego z węzłów repliki. W normalnych warunkach opóźnienie jest zazwyczaj krótkie, ale może wzrosnąć, gdy pojawią się problemy. Na przykład co by się stało, gdyby zaktualizować produkt w bazie danych NoSQL w Stanach Zjednoczonych i zbadać ten sam element danych z węzła repliki w Europie? Otrzymasz wcześniejsze informacje o produkcie, dopóki klaster nie zaktualizuje węzła europejskiego ze zmianą produktu. Natychmiast zwracawynik zapytania i nie czekając na aktualizację wszystkich węzłów replik, zyskujesz ogromną skalę i objętość, ale z możliwością prezentacji starszych danych.

Wysoka dostępność i ogromna skalowalność są często bardziej istotne dla firmy niż silna spójność. Deweloperzy mogą implementować techniki i wzorce, takie jak Sagas, CQRS i asynchroniczne wiadomości do przyjęcia spójności ostatecznej.

> W dzisiejszych czasach należy zadbać o to, by zdjęć ograniczenia dotyczące wpr. Pojawił się nowy typ bazy danych o nazwie NewSQL, który rozszerza silnik relacyjnych baz danych, aby obsługiwać zarówno skalowalność poziomą, jak i skalowalną wydajność systemów NoSQL.

## <a name="considerations-for-relational-vs-nosql-systems"></a>Zagadnienia dotyczące systemów relacyjnych i NoSQL

Na podstawie określonych wymagań dotyczących danych mikrousługi oparte na chmurze mogą implementować relacyjny magazyn danych NoSQL lub oba te elementy.

|  Należy wziąć pod uwagę magazyn danych NoSQL, gdy: | Należy wziąć pod uwagę relacyjnej bazy danych, gdy: |
| :-------- | :-------- |
| Masz duże obciążenia woluminów, które wymagają dużej skali | Głośność obciążenia jest spójna i wymaga średniej i dużej skali |
| Obciążenia nie wymagają gwarancji ACID |  Wymagane są gwarancje ACID |
| Twoje dane są dynamiczne i często się zmieniają | Twoje dane są przewidywalne i wysoce ustrukturyzowane |
| Dane mogą być wyrażane bez relacji | Dane najlepiej wyrażać w relacji |  
| Musisz szybko pisać i pisać bezpieczeństwo nie jest krytyczne | Bezpieczeństwo zapisu jest wymogiem |  
| Pobieranie danych jest proste i ma tendencję do | Pracujesz ze złożonymi zapytaniami i raportami|
| Twoje dane wymagają szerokiej dystrybucji geograficznej | Twoi użytkownicy są bardziej scentralizowani |
| Aplikacja zostanie wdrożona na sprzęcie towarowym, na przykład w chmurach publicznych | Aplikacja zostanie wdrożona na dużym, wysokiej klasy sprzęcie |
|||

W następnych sekcjach przeanalizujemy opcje dostępne w chmurze platformy Azure do przechowywania danych natywnych dla chmury i zarządzania nimi.

## <a name="database-as-a-service"></a>Baza danych jako usługa

Aby rozpocząć, można aprowizować maszynę wirtualną platformy Azure i zainstalować bazę danych z wyboru dla każdej usługi. Chociaż masz pełną kontrolę nad środowiskiem, zrezygowatoby wiele wbudowanych funkcji platformy w chmurze. Należy również być odpowiedzialny za zarządzanie maszyną wirtualną i bazą danych dla każdej usługi. Takie podejście może szybko stać się czasochłonne i kosztowne.

Zamiast tego aplikacje natywne dla chmury faworyzują usługi danych udostępniane jako [baza danych jako usługa (DBaaS).](https://www.stratoscale.com/blog/dbaas/what-is-database-as-a-service/) W pełni zarządzane przez dostawcę chmury te usługi zapewniają wbudowane zabezpieczenia, skalowalność i monitorowanie. Zamiast posiadania usługi, po prostu zużywają go jako [usługę tworzenia kopii zapasowych](./definition.md#backing-services). Dostawca zarządza zasobem na dużą skalę i ponosi odpowiedzialność za wydajność i konserwację.

Można je skonfigurować w strefach dostępności chmury i regionach, aby osiągnąć wysoką dostępność. Wszystkie one obsługują zdolność just-in-time i model płatności zgodnie z rzeczywistym uchem. Platforma Azure oferuje różne rodzaje opcji zarządzanych usług danych, z których każda ma określone korzyści.

Najpierw przyjrzymy się relacyjnym usługom DBaaS dostępnym na platformie Azure. Zobaczysz, że flagowa baza danych programu SQL Server firmy Microsoft jest dostępna wraz z kilkoma opcjami open source. Następnie porozmawiamy o usługach danych NoSQL na platformie Azure.

## <a name="azure-relational-databases"></a>Relacyjne bazy danych platformy Azure

W przypadku mikrousług natywnych dla chmury, które wymagają danych relacyjnych, platforma Azure oferuje cztery zarządzane relacyjne bazy danych jako usługi (DBaaS) oferty, przedstawione na rysunku 5-11.

![Zarządzane relacyjne bazy danych na platformie Azure](./media/azure-managed-databases.png)

**Rysunek 5-11**. Zarządzane relacyjne bazy danych dostępne na platformie Azure

Na poprzedniej rysunku należy pamiętać, jak każdy siedzi na wspólnej infrastruktury DBaaS, który oferuje kluczowe możliwości bez dodatkowych kosztów.

Te funkcje są szczególnie ważne dla organizacji, które aprowizacją dużej liczby baz danych, ale mają ograniczone zasoby do administrowania nimi.
Można aprowizować bazę danych platformy Azure w ciągu kilku minut, wybierając ilość rdzeni przetwarzania, pamięci i podstawowego magazynu. Można skalować bazę danych w locie i dynamicznie dostosowywać zasoby z niewielkim lub żadnym przestojem.

## <a name="azure-sql-database"></a>Baza danych SQL Azure

Zespoły programistyczne z doświadczeniem w programie Microsoft SQL Server powinny rozważyć [azure sql database](https://docs.microsoft.com/azure/sql-database/). Jest to w pełni zarządzana relacyjna baza danych jako usługa (DBaaS) oparta na aparatie baz danych programu Microsoft SQL Server. Usługa udostępnia wiele funkcji znalezionych w lokalnej wersji programu SQL Server i uruchamia najnowszą stabilną wersję aparatu bazy danych programu SQL Server.

Do użytku z mikrousługą natywną w chmurze usługa Azure SQL Database jest dostępna z trzema opcjami wdrażania:

- Pojedyncza baza danych reprezentuje w pełni zarządzaną bazę danych SQL działającą na [serwerze bazy danych SQL platformy Azure](https://docs.microsoft.com/azure/sql-database/sql-database-servers) w chmurze platformy Azure. Baza danych jest uważana za [*zawartą,*](https://docs.microsoft.com/sql/relational-databases/databases/contained-databases) ponieważ nie ma zależności konfiguracyjnych na podstawowym serwerze bazy danych.
  
- [Wystąpienie zarządzane](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) jest w pełni zarządzanym wystąpieniem aparatu bazy danych programu Microsoft SQL Server, które zapewnia prawie 100% zgodności z lokalnym programem SQL Server. Ta opcja obsługuje większe bazy danych o pojemności do 35 TB i jest umieszczana w [sieci wirtualnej platformy Azure](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview) w celu lepszej izolacji.

- [Usługa Azure SQL Database bez serwerów](https://docs.microsoft.com/azure/sql-database/sql-database-serverless) to warstwa obliczeniowa dla pojedynczej bazy danych, która automatycznie skaluje się na podstawie zapotrzebowania na obciążenie. Rozlicza tylko kwotę obliczeń używanych na sekundę. Usługa jest dobrze nadaje się do obciążeń z przerywany, nieprzewidywalne wzorce użycia, przeplatane okresami braku aktywności. Warstwa obliczeniowa bezserwerowa również automatycznie wstrzymuje bazy danych w okresach nieaktywnych, dzięki czemu są rozliczane tylko opłaty za magazyn. Automatycznie wznawia działanie po powrocie działania.

Oprócz tradycyjnego stosu programu Microsoft SQL Server platforma Azure oferuje również zarządzane wersje trzech popularnych baz danych typu open source.

## <a name="open-source-databases-in-azure"></a>Bazy danych typu open source na platformie Azure

Relacyjne bazy danych typu open source stały się popularnym wyborem dla aplikacji natywnych dla chmury. Wiele przedsiębiorstw faworyzuje je za komercyjne produkty bazdanych, zwłaszcza w celu oszczędności kosztów. Wiele zespołów programistycznych korzysta z elastyczności, rozwoju wspieranego przez społeczność oraz ekosystemu narzędzi i rozszerzeń. Bazy danych typu open source można wdrażać u wielu dostawców chmury, co pomaga zminimalizować obawy związane z "blokadą dostawcy".

Deweloperzy mogą łatwo samodzielnie hostować dowolną bazę danych typu open source na maszynie wirtualnej platformy Azure. Zapewniając pełną kontrolę, takie podejście stawia cię na haku do zarządzania, monitorowania i konserwacji bazy danych i maszyn wirtualnych.

Firma Microsoft kontynuuje jednak swoje zobowiązanie do utrzymywania platformy Azure jako "otwartej platformy", oferując kilka popularnych baz danych typu open source jako *w pełni zarządzane* usługi DBaaS.

### <a name="azure-database-for-mysql"></a>Azure Database for MySQL

[MySQL](https://en.wikipedia.org/wiki/MySQL) to relacyjna baza danych open source i filar dla aplikacji zbudowanych na [stosie oprogramowania LAMP.](https://en.wikipedia.org/wiki/LAMP_(software_bundle)) Powszechnie wybierany do *czytania dużych* obciążeń, jest używany przez wiele dużych organizacji, w tym Facebook, Twitter i YouTube. Wersja społecznościowa jest dostępna bezpłatnie, a wersja enterprise wymaga zakupu licencji. Pierwotnie stworzony w 1995 roku, produkt został zakupiony przez Sun Microsystems w 2008 roku. Oracle przejęło Sun i MySQL w 2010 roku.

[Usługa Azure Database for MySQL](https://azure.microsoft.com/services/mysql/) to zarządzana relacyjna usługa bazy danych oparta na otwartym silniku programu MySQL Server. Używa wersji MySQL Community. Serwer Azure MySQL jest punktem administracyjnym usługi. Jest to ten sam aparat serwera MySQL używany do wdrożeń lokalnych. Aparat może utworzyć jedną bazę danych na serwer lub wiele baz danych na serwer, które współużytkują zasoby. Można nadal zarządzać danymi przy użyciu tych samych narzędzi open source bez konieczności uczenia się nowych umiejętności lub zarządzania maszynami wirtualnymi.

### <a name="azure-database-for-mariadb"></a>Azure Database for MariaDB

[MariaDB (MariaDB)](https://mariadb.com/) Serwer to kolejny popularny serwer baz danych typu open source. Został on stworzony jako *widelec* MySQL, gdy Oracle kupił Sun Microsystems, który był właścicielem MySQL. Celem było zapewnienie, że MariaDB pozostał open-source. Ponieważ MariaDB jest rozwidleniem MySQL, definicje danych i tabel są zgodne, a protokoły klientów, struktury i interfejsy API są ściśle związane.

MariaDB ma silną społeczność i jest używany przez wiele dużych przedsiębiorstw. Podczas gdy Oracle nadal utrzymuje, ulepsza i wspiera MySQL, fundacja MariaDB zarządza Usługą MariaDB, umożliwiając publiczny wkład w produkt i dokumentację.

[Usługa Azure Database for MariaDB](https://azure.microsoft.com/services/mariadb/) to w pełni zarządzana relacyjna baza danych jako usługa w chmurze platformy Azure. Usługa jest oparta na silniku serwera mariadb community edition. Może obsługiwać obciążenia o znaczeniu krytycznym z przewidywalną wydajnością i dynamiczną skalowalnością.

### <a name="azure-database-for-postgresql"></a>Azure Database for PostgreSQL

[PostgreSQL](https://www.postgresql.org/) to relacyjna baza danych typu open source z ponad 30-letnim aktywnym rozwojem. PostgresSQL ma silną reputację niezawodności i integralności danych. Jest bogaty w funkcje, zgodny z SQL i uważany za bardziej wydajniejszy niż MySQL — szczególnie w przypadku obciążeń ze złożonymi zapytaniami i ciężkimi zapisami. Wiele dużych przedsiębiorstw, w tym Apple, Red Hat i Fujitsu, zbudowało produkty wykorzystujące PostgreSQL.

[Usługa Azure Database for PostgreSQL](https://azure.microsoft.com/services/postgresql/) to w pełni zarządzana relacyjna usługa bazy danych oparta na otwartym źródłowym silniku bazy danych Postgres. Usługa obsługuje wiele platform programistycznych, w tym C++, Java, Python, Node, C\#i PHP. Można migrować bazy danych PostgreSQL do niego za pomocą narzędzia [interfejsu wiersza polecenia](https://datamigration.microsoft.com/scenario/postgresql-to-azurepostgresql?step=1) lub usługi azure data migration service.

Usługa Azure Database for PostgreSQL jest dostępna z dwiema opcjami wdrażania:

- Opcja wdrażania [pojedynczego serwera](https://docs.microsoft.com/azure/postgresql/concepts-servers) jest centralnym punktem administracyjnym dla wielu baz danych, do których można wdrożyć wiele baz danych. Ceny są uporządkowane dla podlanego serwera na podstawie rdzeni i pamięci masowej.

- [Opcja Hiperskala (Citus)](https://azure.microsoft.com/blog/get-high-performance-scaling-for-your-azure-database-workloads-with-hyperscale/) jest obsługiwana przez technologię Citus Data. Umożliwia wysoką wydajność przez *poziome skalowanie* pojedynczej bazy danych w setkach węzłów, aby zapewnić wysoką wydajność i skalowanie. Ta opcja umożliwia aparatowi, aby zmieścić więcej danych w pamięci, równoległość zapytań w setkach węzłów i indeks danych szybciej.

## <a name="nosql-data-in-azure"></a>Dane NoSQL na platformie Azure

Usługa Cosmos DB to w pełni zarządzana, globalnie rozproszona usługa bazy danych NoSQL w chmurze platformy Azure. Został przyjęty przez wiele dużych firm na całym świecie, w tym Coca-Cola, Skype, ExxonMobil i Liberty Mutual.

Jeśli usługi wymagają szybkiej reakcji z dowolnego miejsca na świecie, wysokiej dostępności lub elastycznej skalowalności, usługa Cosmos DB jest doskonałym wyborem. Rysunek 5-12 przedstawia usługę Cosmos DB.

![Przegląd usługi Cosmos DB](./media/cosmos-db-overview.png)

**Rysunek 5-12**: Przegląd usługi Cosmos DB

Poprzednia liczba przedstawia wiele wbudowanych funkcji natywnych dla chmury dostępnych w usłudze Cosmos DB. W tej sekcji przyjrzymy się im bliżej.

### <a name="global-support"></a>Wsparcie globalne

Aplikacje natywne dla chmury często mają globalną grupę odbiorców i wymagają globalnej skali.

Można rozpowszechniać bazy danych Cosmos między regionami lub na całym świecie, umieszczając dane blisko użytkowników, skracając czas odpowiedzi i zmniejszając opóźnienia. Można dodać lub usunąć bazę danych z regionu bez wstrzymywania lub ponownego wdrażania usług. W tle usługi Cosmos DB w sposób niewidoczny dla środowiska replikuje dane do każdego ze skonfigurowanych regionów.

Usługa Cosmos DB obsługuje [klastrowanie aktywne/aktywne](https://kemptechnologies.com/white-papers/unfog-confusion-active-passive-activeactive-load-balancing/) na poziomie globalnym, umożliwiając skonfigurowanie dowolnego regionu bazy danych do obsługi *zapisów i odczytów.*

Protokół [Multi-Master](https://docs.microsoft.com/azure/cosmos-db/multi-master-benefits) jest ważną funkcją usługi Cosmos DB, która umożliwia następujące funkcje:

- Nieograniczona elastyczna skalowalność zapisu i odczytu.

- 99.999% dostępności do odczytu i zapisu na całym świecie.

- Gwarantowane odczyty i zapisy serwowane w mniej niż 10 milisekund na 99 percentylu.

Za pomocą interfejsów [API multi-Homing](https://docs.microsoft.com/azure/cosmos-db/distribute-data-globally)usługi Cosmos DB mikrousługa jest automatycznie świadoma najbliższego regionu platformy Azure i wysyła do niego żądania. Najbliższy region jest identyfikowany przez usługę Cosmos DB bez żadnych zmian konfiguracji. Jeśli region stanie się niedostępny, funkcja Multi-Homing automatycznie rozsyła żądania do następnego najbliższego dostępnego regionu.

### <a name="multi-model-support"></a>Obsługa wielu modeli

Podczas replatforming aplikacje monolityczne do architektury natywnej dla chmury, zespoły programistyczne czasami trzeba migrować open source, magazyny danych NoSQL. Usługa Cosmos DB może pomóc w zachowaniu inwestycji w te magazyny danych NoSQL dzięki *wielomodelowej* platformie danych. Rysunek 5-13 przedstawia obsługiwane [interfejsy API zgodności](https://www.wikiwand.com/en/Cosmos_DB)NoSQL .

![Dostawcy usługi Cosmos DB](./media/cosmos-db-providers.png)

**Rysunek 5-13**: Dostawcy usługi Cosmos DB

Zespoły programistyczne mogą migrować istniejące bazy danych Mongo, Gremlin lub Cassandra do usługi Cosmos DB przy minimalnych zmianach danych lub kodu. W przypadku nowych aplikacji zespoły programistyczne mogą wybierać spośród opcji typu open source lub wbudowanego modelu interfejsu API SQL.

> Wewnętrznie Cosmos przechowuje dane w prostym formacie struct składa się z pierwotnych typów danych. Dla każdego żądania aparat bazy danych tłumaczy dane pierwotne na reprezentację modelu, który został wybrany.

Na poprzednim rysunku 5-13 zwróć uwagę na opcję [Interfejsu API tabeli.](https://docs.microsoft.com/azure/cosmos-db/table-introduction) Ten interfejs API jest ewolucją usługi Azure Table Storage. Oba współużytkują ten sam podstawowy model tabeli, ale interfejs API tabeli usługi Cosmos DB dodaje ulepszenia premium niedostępne w interfejsie API usługi Azure Storage. Cechy te są kontrastowane na rysunku 5-4.

![Interfejs API tabel platformy Azure](media/azure-table-api.png)

**Rysunek 5–14**: Dostawcy interfejsu API tabel platformy Azure

Mikrousługi, które korzystają z magazynu tabeli platformy Azure można łatwo migrować do interfejsu API tabeli usługi Cosmos DB. Nie są wymagane żadne zmiany kodu.

### <a name="tunable-consistency"></a>Przestrajana konsystencja

Wcześniej w sekcji *Relacyjne vs NoSQL* omówiliśmy temat *spójności danych*. Spójność danych odnosi się do *integralności* danych. Usługi natywne dla chmury z rozproszonymi danymi opierają się na replikacji i muszą wprowadzać podstawowe kompromisy między spójnością odczytu, dostępnością i opóźnieniem.

Większość rozproszonych baz danych umożliwia deweloperom wybór między dwoma modelami spójności: silną spójność i spójność ostateczna. *Silna spójność* to złoty standard programowalności danych. Gwarantuje, że kwerenda zawsze będzie zwracać najbardziej aktualne dane — nawet jeśli system musi ponieść opóźnienie oczekiwania na aktualizację do replikacji we wszystkich kopiach bazy danych. Podczas gdy baza danych skonfigurowana do *ostatecznej spójności* zwróci dane natychmiast, nawet jeśli te dane nie są najbardziej bieżącą kopią. Ta ostatnia opcja umożliwia większą dostępność, większą skalę i zwiększoną wydajność.

Usługa Azure Cosmos DB oferuje pięć dobrze zdefiniowanych [modeli spójności](https://docs.microsoft.com/azure/cosmos-db/consistency-levels) pokazano na rysunku 5-15.

![Wykres spójności usługi Cosmos DB](./media/cosmos-consistency-level-graph.png)

**Rysunek 5-15**: Poziomy spójności usługi Cosmos DB

 Te opcje umożliwiają dokonywanie precyzyjnych wyborów i szczegółowych kompromisów w celu zapewnienia spójności, dostępności i wydajności danych. Rysunek 5-16 opisuje każdy poziom.

![Poziomy spójności usługi Cosmos DB](./media/cosmos-db-consistency-levels.png)

**Rysunek 5-16**: Opis poziomu spójności usługi Cosmos DB

W artykule [Getting Behind the 9-Ball: Cosmos DB Consistency Levels Explained](https://blog.jeremylikness.com/blog/2018-03-23_getting-behind-the-9ball-cosmosdb-consistency-levels/), Microsoft Cloud Developer Advocate Jeremy Likeness zapewnia doskonałe wyjaśnienie pięciu modeli.

### <a name="partitioning"></a>Partycjonowanie

Usługa Azure Cosmos DB obejmuje automatyczne [partycjonowanie](https://docs.microsoft.com/azure/cosmos-db/partitioning-overview) w celu skalowania bazy danych w celu zaspokojenia potrzeb wydajności usług natywnych dla chmury.

Zarządzanie danymi w danych usługi Cosmos DB przez tworzenie baz danych, kontenerów i elementów.

Kontenery znajdują się w bazie danych usługi Cosmos DB i reprezentują grupowanie elementów niezależne od schematu. Elementy są dane, które można dodać do kontenera. Są one reprezentowane jako dokumenty, wiersze, węzły lub krawędzie. Wszystkie elementy dodane do kontenera są automatycznie indeksowane.

Aby podzielić kontener, elementy są podzielone na różne podzestawy zwane partycjami logicznymi. Partycje logiczne są wypełniane na podstawie wartości klucza partycji, który jest skojarzony z każdym elementem w kontenerze. Rysunek 5-18 przedstawia dwa kontenery z partycją logiczną opartą na wartości klucza partycji.

![Mechanika partycjonowania usługi Cosmos DB](./media/cosmos-db-partitioning.png)

**Rysunek 5-18**: Mechanika partycjonowania cosmos DB

Uwaga na poprzednim rysunku, w jaki sposób każdy element zawiera klucz partycji "miasto" lub "lotnisko". Klucz określa partycję logiczną elementu. Elementy z kodem miasta są przypisane do kontenera po lewej stronie i elementy z kodem lotniska, do kontenera po prawej stronie. Połączenie wartości klucza partycji z wartością identyfikatora tworzy indeks elementu, który jednoznacznie identyfikuje element.

Wewnętrznie usługa Cosmos DB automatycznie zarządza umieszczenie [partycji logicznych](https://docs.microsoft.com/azure/cosmos-db/partition-data) na partycjach fizycznych w celu zaspokojenia potrzeb skalowalności i wydajności kontenera. Wraz ze wzrostem wymagań dotyczących przepływów aplikacji i magazynu usługi Azure Cosmos DB dystrybuuje partycje logiczne na większej liczbie serwerów. Operacje redystrybucji są zarządzane przez usługę Cosmos DB i wywoływane bez przerw lub przestojów.

## <a name="newsql-databases"></a>Bazy danych NewSQL

*NewSQL* to nowa technologia baz danych, która łączy rozproszoną skalowalność NoSQL z gwarancjami ACID relacyjnej bazy danych. Bazy danych NewSQL są ważne dla systemów biznesowych, które muszą przetwarzać duże ilości danych w rozproszonych środowiskach, z pełną obsługą transakcyjną i zgodnością acid. Podczas gdy baza danych NoSQL może zapewnić ogromną skalowalność, nie gwarantuje spójności danych. Sporadyczne problemy wynikające z niespójnych danych mogą stanowić obciążenie dla zespołu programistów. Deweloperzy muszą konstruować zabezpieczenia do kodu mikrousługi do zarządzania problemami spowodowanymi przez niespójne dane.

Cloud Native Computing Foundation (CNCF) zawiera kilka projektów bazy danych NewSQL.

| Project | Właściwości |
| :-------- | :-------- |
| Karaluch DB |Relacyjna baza danych zgodna z ACID, która jest skalowana globalnie. Dodaj nowy węzeł do klastra, a karaluchdb zajmuje się równoważeniem danych między wystąpieniami i obszarami geograficznymi. Tworzy, zarządza i dystrybuuje repliki, aby zapewnić niezawodność. Jest open source i swobodnie dostępny.  |
| Baza danych TiDB | Baza danych typu open source obsługująca obciążenia HTAP (Hybrid Transactional and Analytical Processing). Jest kompatybilny z MySQL i oferuje skalowalność poziomą, silną spójność i wysoką dostępność.  TiDB działa jak serwer MySQL. Można nadal korzystać z istniejących bibliotek klienta MySQL, bez konieczności wprowadzania rozległych zmian kodu w aplikacji. |
| YugabyteDB (yugabyteDB) | Baza danych sql typu open source o wysokiej wydajności. Obsługuje małe opóźnienie zapytań, odporność na błędy i globalną dystrybucję danych. YugabyteDB jest zgodny z PostgressSQL i obsługuje skalowane w skali rdbms i internetowe obciążenia OLTP. Produkt obsługuje również NoSQL i jest kompatybilny z Cassandrą. |
|Okręg wyborczy Vitess | Vitess to rozwiązanie bazodadowe do wdrażania, skalowania i zarządzania dużymi klastrami wystąpień MySQL. Można go uruchomić w architekturze chmury publicznej lub prywatnej. Łączy i rozszerza wiele ważnych funkcji MySQL i oferuje zarówno pionowe, jak i poziome wsparcie odcinkowania. Zainspirowany youtube, Vitess obsługuje cały ruch bazy danych YouTube od 2011 . |

Projekty typu open source na poprzedniej figurze są dostępne w Cloud Native Computing Foundation. Trzy oferty są produkty pełnej bazy danych, które obejmują .NET Core wsparcia. Drugi, Vitess, jest systemem klastrowania bazy danych, który poziomo skaluje duże klastry wystąpień MySQL.

Kluczowym celem projektu dla baz danych NewSQL jest praca natywnie w Kubernetes, korzystając z odporności i skalowalności platformy.

Bazy danych NewSQL są zaprojektowane tak, aby rozwijać się w tymczasowych środowiskach chmury, w których podstawowe maszyny wirtualne mogą być ponownie uruchamiane lub ponownie zaplanowane w jednej chwili. Bazy danych są przeznaczone do przetrwania awarii węzłów bez utraty danych lub przestojów. KaraluchDB, na przykład, jest w stanie przetrwać utratę maszyny, utrzymując trzy spójne repliki wszelkich danych w węzłach w klastrze.

Kubernetes używa *konstrukcji Usług,* aby umożliwić klientowi adresgrupy identycznych procesów baz danych NewSQL z jednego wpisu DNS. Oddzielając wystąpienia bazy danych od adresu usługi, z którą jest skojarzona, możemy skalować bez zakłócania istniejących wystąpień aplikacji. Wysłanie żądania do dowolnej usługi w danym momencie zawsze przyniesie ten sam wynik.

W tym scenariuszu wszystkie wystąpienia bazy danych są równe. Nie ma żadnych relacji podstawowych lub pomocniczych. Techniki, takie jak *replikacja konsensusu* znalezione w KaraluchDB, umożliwiają dowolnemu węzłowi bazy danych obsługę dowolnego żądania. Jeśli węzeł, który odbiera żądanie równoważenia obciążenia ma dane, których potrzebuje lokalnie, natychmiast odpowiada. Jeśli nie, węzeł staje się bramą i przekazuje żądanie do odpowiednich węzłów, aby uzyskać poprawną odpowiedź. Z punktu widzenia klienta każdy węzeł bazy danych jest taki sam: są wyświetlane jako pojedyncza *logiczna* baza danych z gwarancjami spójności systemu jednomaszynowego, pomimo dziesiątek, a nawet setek węzłów, które działają za kulisami.

Aby uzyskać szczegółowe spojrzenie na mechanikę baz danych NewSQL, zobacz [DASH: Cztery właściwości Kubernetes-Native Databases](https://thenewstack.io/dash-four-properties-of-kubernetes-native-databases/) artykułu.

## <a name="data-migration-to-the-cloud"></a>Migracja danych do chmury

Jednym z bardziej czasochłonnych zadań jest migracja danych z jednej platformy danych do drugiej. [Usługa migracji danych Azure](https://azure.microsoft.com/services/database-migration/) może pomóc przyspieszyć takie działania. Można migrować dane z kilku zewnętrznych źródeł bazy danych do platform y Azure Data przy minimalnych przestojach. Platformy docelowe obejmują następujące usługi:

- Baza danych SQL Azure
- Azure Database for MySQL
- Azure Database for MariaDB
- Azure Database for PostgreSQL
- CosmosDB
  
Usługa zawiera zalecenia, które poprowadzą Cię przez zmiany wymagane do wykonania migracji, zarówno małych, jak i dużych.

>[!div class="step-by-step"]
>[Poprzedni](Database-per-microservice.md)
>[następny](azure-caching.md)
