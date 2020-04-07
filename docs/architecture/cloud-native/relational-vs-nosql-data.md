---
title: Dane relacyjne a NoSQL
description: Dowiedz się więcej o danych relacyjnych i NoSQL w aplikacjach natywnych dla chmury
author: robvet
ms.date: 01/22/2020
ms.openlocfilehash: 3fb3dcc3a87e278c05f3e15d261245f4d61453d1
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805808"
---
# <a name="relational-vs-nosql-data"></a>Dane relacyjne a NoSQL

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Relacyjne i NoSQL to dwa typy systemów baz danych często implementowanych w aplikacjach natywnych dla chmury. Są one zbudowane inaczej, przechowują dane w inny sposób i są dostępne w inny sposób. W tej sekcji przyjrzymy się obu. W dalszej części tego rozdziału przyjrzymy się nowej technologii baz danych o nazwie *NewSQL.*

*Relacyjne bazy danych* są od dziesięcioleci powszechną technologią. Są dojrzałe, sprawdzone i szeroko wdrożone. Konkurencyjne produkty baz danych, oprzyrządowanie i wiedza specjalistyczna obfitują. Relacyjne bazy danych zapewniają magazyn powiązanych tabel danych. Tabele te mają stały schemat, użyj SQL (Structured Query Language) do zarządzania danymi i obsługuje gwarancje ACID.

*Bazy danych no-SQL* odnoszą się do wysokowydajnych, nierelacyjnych magazynów danych. Wyróżniają się one w ich łatwość użycia, skalowalność, odporność i dostępność charakterystyki. Zamiast łączenia tabel znormalizowanych danych, NoSQL przechowuje dane nieustrukturyzowane lub częściowo ustrukturyzowane, często w parach klucz-wartość lub dokumentach JSON. Bazy danych no-SQL zazwyczaj nie zapewniają gwarancje ACID poza zakresem pojedynczej partycji bazy danych. Usługi o dużej objętości, które wymagają czasu odpowiedzi poniżej sekundy, faworyzują magazyny danych NoSQL.

Nie można przecenić wpływu technologii [NoSQL](https://www.geeksforgeeks.org/introduction-to-nosql/) na rozproszone systemy natywne chmury. Rozprzestrzenianie się nowych technologii danych w tej przestrzeni zakłóciło rozwiązania, które kiedyś opierały się wyłącznie na relacyjnych bazach danych.

Bazy danych NoSQL zawierają kilka różnych modeli uzyskiwania dostępu do danych i zarządzania nimi, z których każdy jest dostosowany do określonych przypadków użycia. Rysunek 5-9 przedstawia cztery wspólne modele.

![Modele danych NoSQL](./media/types-of-nosql-datastores.png)

**Rysunek 5-9**: Modele danych dla baz danych NoSQL

| Model | Właściwości |
| :-------- | :-------- |
| Magazyn dokumentów | Dane i metadane są przechowywane hierarchicznie w dokumentach opartych na JSON wewnątrz bazy danych. |
| Magazyn wartości kluczy | Najprostsze z baz danych NoSQL, dane są reprezentowane jako zbiór par klucz-wartość. |
| Magazyn z szerokimi kolumnami | Powiązane dane są przechowywane jako zestaw par zagnieżdżonych klucz/wartość w jednej kolumnie. |
| Sklep z wykresami | Dane są przechowywane w strukturze wykresu jako właściwości węzła, krawędzi i danych. |

## <a name="the-cap-theorem"></a>W przedwzmo

Aby zrozumieć różnice między tego typu bazami danych, należy wziąć pod uwagę zasadę CAP, zestaw zasad stosowanych do systemów rozproszonych, które przechowują stan. Rysunek 5-10 przedstawia trzy właściwości wpr.

![Ws.](./media/cap-theorem.png)

**Rysunek 5-10**. W przedwzmo

W oświadczeniu stwierdza się, że rozproszone systemy danych oferują kompromis między spójnością, dostępnością i tolerancją partycji. I, że każda baza danych może zagwarantować tylko *dwie* z trzech właściwości:

- *Spójności.* Każdy węzeł w klastrze odpowiada najnowszymi danymi, nawet jeśli system musi zablokować żądanie, dopóki wszystkie repliki nie zaktualizują się. Jeśli kwerendy "spójny system" dla elementu, który jest aktualnie aktualizowany, będziesz czekać na tę odpowiedź, aż wszystkie repliki pomyślnie zaktualizować. Jednak otrzymasz najbardziej aktualne dane.

- *Dostępność.* Każdy węzeł zwraca natychmiastową odpowiedź, nawet jeśli ta odpowiedź nie jest najnowszymi danymi. Jeśli kwerendy "dostępny system" dla elementu, który jest aktualizowany, otrzymasz najlepszą możliwą odpowiedź, jaką usługa może zapewnić w tym momencie.

- *Tolerancja partycji.* Gwarantuje, że system będzie nadal działać, nawet jeśli replikowany węzeł danych ulegnie awarii lub utraci łączność z innymi replikowanymi węzłami danych.

Relacyjne bazy danych zazwyczaj zapewniają spójność i dostępność, ale nie tolerancji partycji. Zazwyczaj są one aprowiowane na jednym serwerze i skalowane w pionie przez dodanie większej ilości zasobów do komputera.

Wiele relacyjnych systemów baz danych obsługuje wbudowane funkcje replikacji, w których kopie podstawowej bazy danych mogą być wykonane do innych pomocniczych wystąpień serwera. Operacje zapisu są dokonywane w wystąpieniu podstawowym i replikowane do każdego z pomocniczych. Po awarii wystąpienia podstawowego można awaryjnie do pomocniczego, aby zapewnić wysoką dostępność. Pomocnicze mogą być również używane do dystrybucji operacji odczytu. Podczas zapisu operacje zawsze są sprzeczne z repliką podstawową, operacje odczytu mogą być kierowane do dowolnego z pomocniczych w celu zmniejszenia obciążenia systemu.

Dane mogą być również poziomo podzielone na wiele węzłów, na przykład za pomocą [dzielenia na fragmenty.](https://docs.microsoft.com/azure/sql-database/sql-database-elastic-scale-introduction) Ale dzielenie na fragmenty znacznie zwiększa obciążenie operacyjne przez plucie danych na wiele elementów, które nie mogą łatwo komunikować się. Zarządzanie tym może być kosztowne i czasochłonne. Może to mieć wpływ na wydajność, sprzężenia tabeli i więzów integralności.

Jeśli repliki danych miałyby utracić łączność sieciową w "wysoce spójnym" klastrze relacyjnej bazy danych, nie można zapisać w bazie danych. System odrzuci operację zapisu, ponieważ nie może replikować tej zmiany na inną replikę danych. Każda replika danych musi być aktualizowana przed zakończeniem transakcji.

Bazy danych NoSQL zazwyczaj obsługują wysoką dostępność i tolerancję partycji. Skalują się w poziomie, często na serwerach towarowych. Takie podejście zapewnia ogromną dostępność, zarówno w obrębie regionów geograficznych, jak i między regionami geograficznymi przy obniżonych kosztach. Partycjonowanie i replikowanie danych na tych komputerach lub węzłach, zapewniając nadmiarowość i odporność na uszkodzenia. Minusem jest spójność. Zmiana danych w jednym węźle NoSQL może zająć trochę czasu, aby propagować do innych węzłów. Zazwyczaj węzeł bazy danych NoSQL zapewni natychmiastową odpowiedź na kwerendę — nawet jeśli dane, które są prezentowane są przestarzałe i nie zostały jeszcze zaktualizowane.

Jeśli repliki danych miały utracić łączność w "wysoce dostępnym" klastrze bazy danych NoSQL, nadal można wykonać operację zapisu w bazie danych. Klaster bazy danych zezwalałby na operację zapisu i aktualizowanie każdej repliki danych, gdy tylko stanie się dostępna.

Ten rodzaj wyniku jest znany jako spójność ostateczna, charakterystyczna dla rozproszonych systemów danych, w których transakcje ACID nie są obsługiwane. Jest to krótkie opóźnienie między aktualizacją elementu danych a czasem potrzebnym do propagacji tej aktualizacji do każdego węzła repliki. W normalnych warunkach opóźnienie jest zazwyczaj krótkie, ale może wzrosnąć, gdy pojawią się problemy. Na przykład co by się stało, gdyby zaktualizować produkt w bazie danych NoSQL w Stanach Zjednoczonych i zbadać ten sam element danych z węzła repliki w Europie? Wcześniejsze informacje o produkcie będą otrzymywać, dopóki klaster nie zaktualizuje węzła europejskiego wraz ze zmianą produktu. Natychmiast zwracając wynik kwerendy i nie czekając na aktualizację wszystkich węzłów repliki, zyskujesz ogromną skalę i wolumin, ale z możliwością przedstawienia starszych danych.

Wysoka dostępność i ogromna skalowalność są często bardziej istotne dla firmy niż silna spójność. Deweloperzy mogą implementować techniki i wzorce, takie jak Sagas, CQRS i asynchronicznych wiadomości, aby objąć spójność ostateczną.

> W dzisiejszych czasach należy zadbać o to, by w przypadku ograniczenia wyw. Pojawił się nowy typ bazy danych o nazwie NewSQL, który rozszerza aparat relacyjnej bazy danych, aby obsługiwać zarówno skalowalność poziomą, jak i skalowalną wydajność systemów NoSQL.

## <a name="considerations-for-relational-vs-nosql-systems"></a>Zagadnienia dotyczące systemów relacyjnych i NoSQL

Na podstawie określonych wymagań dotyczących danych mikrousługi oparte na chmurze można zaimplementować relacyjne, NoSQL magazynu danych lub obu.

|  Należy wziąć pod uwagę magazyn danych NoSQL, gdy: | Należy wziąć pod uwagę relacyjnej bazy danych, gdy: |
| :-------- | :-------- |
| Masz duże obciążenia, które wymagają dużej skali | Wielkość obciążenia jest spójna i wymaga średniej lub dużej skali |
| Twoje obciążenia nie wymagają gwarancji ACID |  Wymagane są gwarancje ACID |
| Twoje dane są dynamiczne i często się zmieniają | Twoje dane są przewidywalne i wysoce ustrukturyzowane |
| Dane mogą być wyrażane bez relacji | Dane najlepiej wyrażać relacyjne |  
| Potrzebujesz szybkich zapisów, a bezpieczeństwo zapisu nie jest krytyczne | Bezpieczeństwo zapisu jest wymogiem |  
| Pobieranie danych jest proste i wydaje się być płaskie | Pracujesz ze złożonymi zapytaniami i raportami|
| Twoje dane wymagają szerokiego rozkładu geograficznego | Użytkownicy są bardziej scentralni |
| Aplikacja zostanie wdrożona na sprzęcie towarowym, na przykład w chmurach publicznych | Aplikacja zostanie wdrożona na dużym, wysokiej klasy sprzęcie |
|||

W następnych sekcjach przyjrzymy się opcjom dostępnym w chmurze platformy Azure do przechowywania danych natywnych dla chmury i zarządzania nimi.

## <a name="database-as-a-service"></a>Baza danych jako usługa

Aby rozpocząć, można aprowizować maszynę wirtualną platformy Azure i zainstalować bazę danych z wyboru dla każdej usługi. Chociaż masz pełną kontrolę nad środowiskiem, chcesz zrezygnować z wielu wbudowanych funkcji platformy w chmurze. Należy również być odpowiedzialny za zarządzanie maszyną wirtualną i bazą danych dla każdej usługi. Takie podejście może szybko stać się czasochłonne i kosztowne.

Zamiast tego aplikacje natywne dla chmury faworyzują usługi danych udostępniane jako [baza danych jako usługa (DBaaS).](https://www.stratoscale.com/blog/dbaas/what-is-database-as-a-service/) W pełni zarządzane przez dostawcę chmury, te usługi zapewniają wbudowane zabezpieczenia, skalowalność i monitorowanie. Zamiast posiadać usługę, po prostu zużywają ją jako [usługę zapasową.](./definition.md#backing-services) Dostawca obsługuje zasób na dużą skalę i ponosi odpowiedzialność za wydajność i konserwację.

Można je skonfigurować w różnych strefach dostępności chmury i regionach, aby osiągnąć wysoką dostępność. Wszystkie one obsługują just-in-time zdolności i pay-as-you-go modelu. Platforma Azure oferuje różne rodzaje opcji usługi danych zarządzanych, z których każda ma określone korzyści.

Najpierw przyjrzymy się relacyjnej usługom DBaaS dostępnym na platformie Azure. Zobaczysz, że flagowa baza danych PROGRAMU SQL Server firmy Microsoft jest dostępna wraz z kilkoma opcjami open source. Następnie omówimy usługi danych NoSQL na platformie Azure.

## <a name="azure-relational-databases"></a>Relacyjne bazy danych platformy Azure

W przypadku mikrousług natywnych dla chmury, które wymagają danych relacyjnych, platforma Azure oferuje cztery zarządzane relacyjne bazy danych jako usługi (DBaaS), przedstawione na rysunku 5-11.

![Zarządzane relacyjne bazy danych na platformie Azure](./media/azure-managed-databases.png)

**Rysunek 5-11**. Zarządzane relacyjne bazy danych dostępne na platformie Azure

Na poprzednim rysunku należy zwrócić uwagę, jak każdy z nich znajduje się na wspólnej infrastrukturze DBaaS, która oferuje kluczowe możliwości bez dodatkowych kosztów.

Te funkcje są szczególnie ważne dla organizacji, które aprowizują dużą liczbę baz danych, ale mają ograniczone zasoby do administrowania nimi.
Można aprowizować bazę danych platformy Azure w ciągu kilku minut, wybierając ilość rdzeni przetwarzania, pamięci i magazynu źródłowego. Można skalować bazę danych w locie i dynamicznie dostosowywać zasoby przy niewielkim lub żadnym przestoju.

## <a name="azure-sql-database"></a>Azure SQL Database

Zespoły programistyczne z doświadczeniem w programie Microsoft SQL Server powinny wziąć pod uwagę [usługę Azure SQL Database](https://docs.microsoft.com/azure/sql-database/). Jest to w pełni zarządzana relacyjna baza danych jako usługa (DBaaS) oparta na silniku bazy danych programu Microsoft SQL Server. Usługa udostępnia wiele funkcji znalezionych w lokalnej wersji programu SQL Server i uruchamia najnowszą stabilną wersję aparatu baz danych programu SQL Server.

Do użytku z mikrousługą natywną dla chmury usługa Azure SQL Database jest dostępna z trzema opcjami wdrażania:

- Pojedyncza baza danych reprezentuje w pełni zarządzaną bazę danych SQL działającą na [serwerze bazy danych SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-servers) w chmurze platformy Azure. Baza danych jest uważana za [*zawartą,*](https://docs.microsoft.com/sql/relational-databases/databases/contained-databases) ponieważ nie ma zależności konfiguracyjnych na serwerze podstawowej bazy danych.
  
- [Wystąpienie zarządzane](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) jest w pełni zarządzanym wystąpieniem aparatu bazy danych programu Microsoft SQL Server, które zapewnia niemal 100% zgodności z lokalnym programem SQL Server. Ta opcja obsługuje większe bazy danych, do 35 TB i jest umieszczana w [sieci wirtualnej platformy Azure](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview) w celu lepszej izolacji.

- [Usługa Azure SQL Database serverless](https://docs.microsoft.com/azure/sql-database/sql-database-serverless) to warstwa obliczeniowa dla pojedynczej bazy danych, która automatycznie skaluje się na podstawie zapotrzebowania na obciążenia. Rozlicza się tylko za ilość obliczeń używanych na sekundę. Usługa jest dobrze nadaje się do obciążeń z przerywane, nieprzewidywalne wzorców użycia, przeplatane okresami braku aktywności. Warstwa obliczeniowa bezserwerowa automatycznie wstrzymuje również bazy danych w okresach nieaktywnych, dzięki czemu naliczane są tylko opłaty za magazyn. Jest on automatycznie wznawiany po powrocie aktywności.

Oprócz tradycyjnego stosu programu Microsoft SQL Server platforma Azure oferuje również zarządzane wersje trzech popularnych baz danych typu open source.

## <a name="open-source-databases-in-azure"></a>Bazy danych typu open source na platformie Azure

Relacyjne bazy danych typu open source stały się popularnym wyborem dla aplikacji natywnych dla chmury. Wiele przedsiębiorstw faworyzuje je w stosunku do komercyjnych produktów baz danych, szczególnie w celu oszczędności kosztów. Wiele zespołów programistycznych korzysta z elastyczności, rozwoju wspieranego przez społeczność oraz ekosystemu narzędzi i rozszerzeń. Bazy danych typu open source można wdrożyć w wielu dostawcach chmury, co pomaga zminimalizować obawy o "blokadę dostawcy".

Deweloperzy mogą łatwo samodzielnie hostować dowolną bazę danych typu open source na maszynie Wirtualnej platformy Azure. Zapewniając pełną kontrolę, to podejście stawia cię na haku do zarządzania, monitorowania i konserwacji bazy danych i maszyny Wirtualnej.

Firma Microsoft kontynuuje jednak swoje zobowiązanie do utrzymania platformy Azure jako "otwartej platformy", oferując kilka popularnych baz danych typu open source jako *w pełni zarządzanych* usług DBaaS.

### <a name="azure-database-for-mysql"></a>Azure Database for MySQL

[MySQL](https://en.wikipedia.org/wiki/MySQL) to relacyjna baza danych typu open source i filar dla aplikacji zbudowanych na [stosie oprogramowania LAMP.](https://en.wikipedia.org/wiki/LAMP_(software_bundle)) Jest powszechnie wybierany do *odczytu ciężkich* obciążeń, jest używany przez wiele dużych organizacji, w tym Facebook, Twitter i YouTube. Wersja społecznościowa jest dostępna za darmo, podczas gdy wersja enterprise wymaga zakupu licencji. Pierwotnie stworzony w 1995 roku, produkt został zakupiony przez Sun Microsystems w 2008 roku. Oracle nabył Sun i MySQL w 2010 roku.

[Usługa Azure Database for MySQL](https://azure.microsoft.com/services/mysql/) to zarządzana relacyjne usługi bazy danych oparte na silniku serwera MySQL typu open source. Używa edycji Społeczności MySQL. Serwer Azure MySQL jest punktem administracyjnym dla usługi. Jest to ten sam aparat serwera MySQL używany do wdrożeń lokalnych. Aparat może utworzyć pojedynczą bazę danych na serwer lub wiele baz danych na serwer, które współużytkuje zasoby. Możesz nadal zarządzać danymi przy użyciu tych samych narzędzi typu open source bez konieczności uczenia się nowych umiejętności lub zarządzania maszynami wirtualnymi.

### <a name="azure-database-for-mariadb"></a>Azure Database for MariaDB

[MariaDB (MariaDB)](https://mariadb.com/) Serwer to kolejny popularny serwer bazy danych typu open source. Został stworzony jako *rozwidla* MySQL, gdy Oracle zakupił Sun Microsystems, który był właścicielem MySQL. Celem było zapewnienie, że MariaDB pozostanie open-source. Ponieważ MariaDB jest rozwidlenia MySQL, definicje danych i tabel są zgodne, a protokoły klienta, struktury i interfejsy API, są ściśle połączone.

MariaDB ma silną społeczność i jest używany przez wiele dużych przedsiębiorstw. Podczas gdy Oracle nadal utrzymuje, ulepsza i wspiera MySQL, fundacja MariaDB zarządza MariaDB, umożliwiając publiczne wkłady w produkt i dokumentację.

[Usługa Azure Database for MariaDB](https://azure.microsoft.com/services/mariadb/) to w pełni zarządzana relacyjnej bazy danych jako usługa w chmurze platformy Azure. Usługa jest oparta na silniku serwera mariadb w wersji społecznościowej. Może obsługiwać obciążenia o znaczeniu krytycznym z przewidywalną wydajnością i dynamiczną skalowalnością.

### <a name="azure-database-for-postgresql"></a>Azure Database for PostgreSQL

[PostgreSQL](https://www.postgresql.org/) to relacyjna baza danych typu open source z ponad 30-letnim aktywnym rozwojem. PostgresSQL ma silną reputację niezawodności i integralności danych. Jest bogaty w funkcje, zgodny z SQL i uważany za bardziej wydajny niż MySQL — szczególnie w przypadku obciążeń ze złożonymi zapytaniami i dużymi zapisami. Wiele dużych przedsiębiorstw, w tym Apple, Red Hat i Fujitsu, zbudowało produkty za pomocą PostgreSQL.

[Usługa Azure Database for PostgreSQL](https://azure.microsoft.com/services/postgresql/) to w pełni zarządzana usługa relacyjnej bazy danych, oparta na silniku bazy danych postgres typu open source. Usługa obsługuje wiele platform programistów, w tym C++, Java, Python, Node, C\#i PHP. Bazy danych PostgreSQL można migrować do niego za pomocą narzędzia [interfejsu wiersza polecenia](https://datamigration.microsoft.com/scenario/postgresql-to-azurepostgresql?step=1) lub usługi Azure Data Migration Service.

Usługa Azure Database for PostgreSQL jest dostępna z dwiema opcjami wdrażania:

- Opcja wdrażania [pojedynczego serwera](https://docs.microsoft.com/azure/postgresql/concepts-servers) jest centralnym punktem administracyjnym dla wielu baz danych, do których można wdrożyć wiele baz danych. Ceny są ustrukturyzowane dla serwera na podstawie rdzeni i pamięci masowej.

- [Opcja Hiperskala (Citus)](https://azure.microsoft.com/blog/get-high-performance-scaling-for-your-azure-database-workloads-with-hyperscale/) jest obsługiwana przez technologię Citus Data. Umożliwia wysoką wydajność, *skalując poziomo* pojedynczą bazę danych w setkach węzłów, aby zapewnić szybką wydajność i skalę. Ta opcja umożliwia aparatowi dopasowanie większej ilości danych w pamięci, równoległość zapytań w setkach węzłów i szybsze indeksowanie danych.

## <a name="nosql-data-in-azure"></a>Dane NoSQL na platformie Azure

Usługa Cosmos DB to w pełni zarządzana, globalnie rozproszona usługa bazy danych NoSQL w chmurze platformy Azure. Został przyjęty przez wiele dużych firm na całym świecie, w tym Coca-Cola, Skype, ExxonMobil i Liberty Mutual.

Jeśli twoje usługi wymagają szybkiej odpowiedzi z dowolnego miejsca na świecie, wysokiej dostępności lub elastycznej skalowalności, usługa Cosmos DB jest doskonałym wyborem. Rysunek 5-12 przedstawia Cosmos DB.

![Przegląd usługi Cosmos DB](./media/cosmos-db-overview.png)

**Rysunek 5-12**: Przegląd usługi Cosmos DB

Poprzednia rysunek przedstawia wiele wbudowanych możliwości natywnych dla chmury dostępnych w usłudze Cosmos DB. W tej sekcji przyjrzymy się im bliżej.

### <a name="global-support"></a>Wsparcie globalne

Aplikacje natywne dla chmury często mają odbiorców na całym świecie i wymagają skali globalnej.

Bazy danych usługi Cosmos można rozpowszechniać w różnych regionach lub na całym świecie, umieszczając dane blisko użytkowników, skracając czas odpowiedzi i zmniejszając opóźnienia. Można dodać lub usunąć bazę danych z regionu bez wstrzymywania lub ponownego rozmieszczania usług. W tle usługa Cosmos DB w sposób przezroczysty replikuje dane do każdego ze skonfigurowanych regionów.

Usługa Cosmos DB obsługuje [aktywne/aktywne](https://kemptechnologies.com/white-papers/unfog-confusion-active-passive-activeactive-load-balancing/) klastrowanie na poziomie globalnym, umożliwiając skonfigurowanie dowolnego regionu bazy danych do obsługi *zarówno zapisów, jak i odczytów.*

Protokół [Multi-Master](https://docs.microsoft.com/azure/cosmos-db/multi-master-benefits) jest ważną funkcją w usłudze Cosmos DB, która umożliwia następujące funkcje:

- Nieograniczona elastyczna skalowalność zapisu i odczytu.

- Dostępność i zapisy na całym świecie jest 99,999%.

- Gwarantowane odczyty i zapisy serwowane w mniej niż 10 milisekund na 99 percentylu.

Za pomocą interfejsów [API multi-homing](https://docs.microsoft.com/azure/cosmos-db/distribute-data-globally)usługi Cosmos DB twoja mikrousługa jest automatycznie zna najbliższy region platformy Azure i wysyła do niego żądania. Najbliższy region jest identyfikowany przez usługi Cosmos DB bez żadnych zmian konfiguracji. Jeśli region stanie się niedostępny, funkcja Multi-Homing automatycznie przekieruje żądania do najbliższego dostępnego regionu.

### <a name="multi-model-support"></a>Obsługa wielu modeli

Podczas replatformowania aplikacji monolitycznych do architektury natywnej w chmurze zespoły programistyczne czasami muszą migrować magazyny danych nosql typu open source. Usługa Cosmos DB może pomóc w zachowaniu inwestycji w te magazyny danych NoSQL za pomocą *wielomodelowej* platformy danych. Rysunek 5-13 przedstawia obsługiwane [interfejsy API zgodności](https://www.wikiwand.com/en/Cosmos_DB)NoSQL .

![Dostawcy usługi Cosmos DB](./media/cosmos-db-providers.png)

**Rysunek 5-13**: Dostawcy usługi Cosmos DB

Zespoły programistyczne mogą migrować istniejące bazy danych Mongo, Gremlin lub Cassandra do bazy danych Usługi Cosmos z minimalnymi zmianami danych lub kodu. W przypadku nowych aplikacji zespoły programistyczne mogą wybierać spośród opcji typu open source lub wbudowanego modelu interfejsu API SQL.

> Wewnętrznie cosmos przechowuje dane w prostym formacie struktury składa się z typów danych pierwotnych. Dla każdego żądania aparat bazy danych tłumaczy dane pierwotne na wybraną reprezentację modelu.

Na poprzednim rysunku 5-13 zanotuj opcję [Interfejsu API tabeli.](https://docs.microsoft.com/azure/cosmos-db/table-introduction) Ten interfejs API jest ewolucją usługi Azure Table Storage. Oba współużytkują ten sam podstawowy model tabeli, ale interfejs API tabeli usługi Cosmos DB dodaje ulepszenia w wersji premium, które nie są dostępne w interfejsie API usługi Azure Storage. Funkcje te są kontrastowane na rysunku 5-4.

![Interfejs API tabel platformy Azure](media/azure-table-api.png)

**Rysunek 5-14**: Dostawcy interfejsu API tabeli platformy Azure

Mikrousługi, które korzystają z usługi Azure Table Storage można łatwo migrować do interfejsu API tabeli usługi Cosmos DB. Nie są wymagane żadne zmiany kodu.

### <a name="tunable-consistency"></a>Przestrajalna spójność

Wcześniej w sekcji *Relacja vs. NoSQL* omówiliśmy temat *spójności danych*. Spójność danych odnosi się do *integralności* danych. Usługi natywne dla chmury z rozproszonymi danymi opierają się na replikacji i muszą stanowić podstawowy kompromis między spójnością odczytu, dostępnością i opóźnieniem.

Większość rozproszonych baz danych umożliwiają deweloperom wybór między dwoma modelami spójności: silną spójnością i spójnością ostateczną. *Silna spójność* jest złotym standardem programowalności danych. Gwarantuje, że kwerenda zawsze zwróci najbardziej aktualne dane — nawet jeśli system musi ponieść opóźnienia oczekiwania na aktualizację do replikacji we wszystkich kopiach bazy danych. Gdy baza danych skonfigurowana dla *spójności ostatecznej* zwróci dane natychmiast, nawet jeśli te dane nie są najbardziej aktualną kopią. Ta ostatnia opcja umożliwia większą dostępność, większą skalę i zwiększoną wydajność.

Usługa Azure Cosmos DB oferuje pięć dobrze zdefiniowanych [modeli spójności](https://docs.microsoft.com/azure/cosmos-db/consistency-levels) pokazanych na rysunku 5-15.

![Wykres spójności usługi Cosmos DB](./media/cosmos-consistency-level-graph.png)

**Rysunek 5-15**: Poziomy spójności bazy danych Cosmos

 Te opcje umożliwiają dokonywanie precyzyjnych wyborów i szczegółowe kompromisy dla spójności, dostępności i wydajności danych. Rysunek 5-16 opisuje każdy poziom.

![Poziomy spójności usługi Cosmos DB](./media/cosmos-db-consistency-levels.png)

**Rysunek 5-16**: Opis poziomu spójności bazy danych cosmosu

W artykule [Getting Behind 9-Ball: Cosmos DB Consistency Levels Explained](https://blog.jeremylikness.com/blog/2018-03-23_getting-behind-the-9ball-cosmosdb-consistency-levels/), Microsoft Cloud Developer Advocate Jeremy Likeness zapewnia doskonałe wyjaśnienie pięciu modeli.

### <a name="partitioning"></a>Partycjonowanie

Usługa Azure Cosmos DB obejmuje automatyczne [partycjonowanie](https://docs.microsoft.com/azure/cosmos-db/partitioning-overview) w celu skalowania bazy danych w celu zaspokojenia potrzeb w zakresie wydajności usług natywnych dla chmury.

Zarządzanie danymi w usłudze Cosmos DB przez tworzenie baz danych, kontenerów i elementów.

Kontenery są aktywne w bazie danych usługi Cosmos DB i reprezentują niezależną od schematu grupowanie elementów. Elementy są dane, które można dodać do kontenera. Są one reprezentowane jako dokumenty, wiersze, węzły lub krawędzie. Wszystkie elementy dodane do kontenera są automatycznie indeksowane.

Aby podzielić kontener, elementy są podzielone na różne podzbiory zwane partycjami logicznymi. Partycje logiczne są wypełniane na podstawie wartości klucza partycji, który jest skojarzony z każdym elementem w kontenerze. Rysunek 5-18 przedstawia dwa kontenery, każdy z partycją logiczną opartą na wartości klucza partycji.

![Cosmos DB mechanika partycjonowania](./media/cosmos-db-partitioning.png)

**Rysunek 5-18**: Mechanika partycjonowania Cosmos DB

Na poprzednim rysunku należy zwrócić uwagę na to, w jaki sposób każdy element zawiera klucz partycji "miasto" lub "lotnisko". Klucz określa partycję logiczną elementu. Elementy z kodem miasta są przypisywane do kontenera po lewej stronie, a elementy z kodem lotniska do kontenera po prawej stronie. Połączenie wartości klucza partycji z wartością identyfikatora tworzy indeks elementu, który jednoznacznie identyfikuje element.

Wewnętrznie usługa Cosmos DB automatycznie zarządza rozmieszczeniem [partycji logicznych](https://docs.microsoft.com/azure/cosmos-db/partition-data) na partycjach fizycznych, aby zaspokoić potrzeby dotyczące skalowalności i wydajności kontenera. Wraz ze wzrostem wymagań dotyczących przepływności i magazynu aplikacji usługa Azure Cosmos DB rozdziela partycje logiczne na większą liczbę serwerów. Operacje redystrybucji są zarządzane przez usługi Cosmos DB i wywoływane bez przerw lub przestojów.

## <a name="newsql-databases"></a>Bazy danych NewSQL

*NewSQL* to nowa technologia baz danych, która łączy skalowalność rozproszonej NoSQL z gwarancją ACID relacyjnej bazy danych. Bazy danych NewSQL są ważne dla systemów biznesowych, które muszą przetwarzać duże ilości danych w środowiskach rozproszonych, z pełną obsługą transakcyjną i zgodnością acid. Podczas gdy baza danych NoSQL może zapewnić ogromną skalowalność, nie gwarantuje spójności danych. Sporadyczne problemy z niespójnych danych może stanowić obciążenie dla zespołu programistycznego. Deweloperzy muszą skonstruować zabezpieczenia w ich kod mikrousług, aby zarządzać problemami spowodowanymi przez niespójne dane.

Cloud Native Computing Foundation (CNCF) oferuje kilka projektów bazy danych NewSQL.

| Projekt | Właściwości |
| :-------- | :-------- |
| Karaluch DB |Zgodna ze specyfikacją ACID, relacyjnej bazy danych, która jest skalowana globalnie. Dodaj nowy węzeł do klastra, a baza danych Karaluchów dba o równoważenie danych między wystąpieniami i regionami geograficznymi. Tworzy, zarządza i dystrybuuje repliki w celu zapewnienia niezawodności. Jest open source i swobodnie dostępny.  |
| TiDB (TiDB) | Baza danych typu open source obsługująca hybrydowe obciążenia transakcyjne i analityczne (HTAP). Jest kompatybilny z MySQL i oferuje skalowalność poziomą, silną spójność i wysoką dostępność.  TiDB działa jak serwer MySQL. Można nadal używać istniejących bibliotek klienta MySQL, bez konieczności rozbudowanych zmian kodu do aplikacji. |
| YugabyteDB (YugabyteDB) | Rozproszona baza danych SQL typu open source o wysokiej wydajności. Obsługuje małe opóźnienie kwerendy, odporność na błędy i globalnej dystrybucji danych. YugabyteDB jest zgodny z PostgressSQL i obsługuje skalowanie w poziomie RDBMS i internet skali obciążeń OLTP. Produkt obsługuje również NoSQL i jest kompatybilny z Cassandra. |
|Witesa | Vitess to rozwiązanie bazy danych do wdrażania, skalowania i zarządzania dużymi klastrami wystąpień MySQL. Można go uruchomić w architekturze chmury publicznej lub prywatnej. Łączy i rozszerza wiele ważnych funkcji MySQL i posiada zarówno pionowe, jak i poziome wsparcie dzielenia na fragmenty. Pochodzi z YouTube, Vitess obsługuje cały ruch w bazie danych YouTube od 2011 roku. |

Projekty typu open source w poprzedniej ilustracji są dostępne w Cloud Native Computing Foundation. Trzy oferty są pełne produkty bazy danych, które obejmują .NET Core wsparcia. Drugi, Vitess, to system klastrowania baz danych, który skaluje poziomo duże klastry wystąpień MySQL.

Kluczowym celem projektu dla baz danych NewSQL jest praca natywnie w umięsień, wykorzystując odporność i skalowalność platformy.

Bazy danych NewSQL są zaprojektowane tak, aby rozwijać się w tymczasowych środowiskach chmury, w których podstawowe maszyny wirtualne mogą być ponownie uruchamiane lub przełożone w mgnieniu oka. Bazy danych są przeznaczone do przetrwania awarii węzłów bez utraty danych ani przestojów. KaraluchDB, na przykład, jest w stanie przetrwać utratę maszyny, utrzymując trzy spójne repliki dowolnych danych w węzłach w klastrze.

Kubernetes używa *konstrukcji usług,* aby umożliwić klientowi adres grupy identycznych procesów baz danych NewSQL z jednego wpisu DNS. Oddzielając wystąpienia bazy danych od adresu usługi, z którą jest skojarzona, możemy skalować bez zakłócania istniejących wystąpień aplikacji. Wysyłanie żądania do dowolnej usługi w danym momencie zawsze przyniesie ten sam wynik.

W tym scenariuszu wszystkie wystąpienia bazy danych są równe. Nie ma żadnych relacji podstawowych lub pomocniczych. Techniki, takie jak *replikacja konsensusu* znalezione w CockroachDB pozwalają dowolny węzeł bazy danych do obsługi każdego żądania. Jeśli węzeł, który odbiera żądanie równoważenia obciążenia ma dane, których potrzebuje lokalnie, natychmiast odpowiada. Jeśli nie, węzeł staje się bramą i przekazuje żądanie do odpowiednich węzłów, aby uzyskać poprawną odpowiedź. Z punktu widzenia klienta, każdy węzeł bazy danych jest taka sama: pojawiają się one jako pojedyncza *logiczna* baza danych z gwarancjami spójności systemu jednopowiedziałowego, pomimo dziesiątek lub nawet setek węzłów, które pracują za kulisami.

Aby uzyskać szczegółowe spojrzenie na mechaniki za newsql baz danych, zobacz [DASH: Cztery właściwości Kubernetes-Natywne bazy danych](https://thenewstack.io/dash-four-properties-of-kubernetes-native-databases/) artykułu.

## <a name="data-migration-to-the-cloud"></a>Migracja danych do chmury

Jednym z bardziej czasochłonnych zadań jest migracja danych z jednej platformy danych do drugiej. [Usługa migracji danych platformy Azure](https://azure.microsoft.com/services/database-migration/) może pomóc przyspieszyć takie działania. Może migrować dane z kilku zewnętrznych źródeł bazy danych do platform Azure Data przy minimalnym przestoju. Platformy docelowe obejmują następujące usługi:

- Azure SQL Database
- Azure Database for MySQL
- Azure Database for MariaDB
- Azure Database for PostgreSQL
- CosmosDB
  
Usługa zawiera zalecenia, aby poprowadzić Cię przez zmiany wymagane do wykonania migracji, zarówno małe, jak i duże.

>[!div class="step-by-step"]
>[Poprzedni](database-per-microservice.md)
>[następny](azure-caching.md)
