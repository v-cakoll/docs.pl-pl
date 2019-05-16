---
title: Korzystanie z baz danych NoSQL jako infrastruktury trwałości
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | W szczególności należy zrozumieć korzystanie z bazy danych NoSql w ogólne i Azure Cosmos DB jako opcja do zaimplementowania utrwalania.
ms.date: 10/08/2018
ms.openlocfilehash: 023904319651ec91000ff036850c773f66d1a267
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65644466"
---
# <a name="use-nosql-databases-as-a-persistence-infrastructure"></a>Użyj bazy danych NoSQL jako infrastruktury trwałości

Korzystając z bazy danych NoSQL dla warstwy danych Twojej infrastruktury, zazwyczaj nie używasz ORM, takich jak Entity Framework Core. Zamiast tego należy użyć interfejsów API dostarczonych przez aparat NoSQL, takie jak usługi Azure Cosmos DB, bazy danych MongoDB, Cassandra, RavenDB, CouchDB lub tabele magazynu platformy Azure.

Jednak gdy używasz bazę danych NoSQL, szczególnie korzystający z dokumentów bazy danych, takich jak usługi Azure Cosmos DB, CouchDB lub RavenDB, sposób projektowania modelu za pomocą agregacji DDD przypomina częściowo jak można to zrobić w programie EF Core w odniesieniu do identyfikacji Łączny katalogów głównych klas jednostek podrzędnych i klasy obiektu wartości. Jednak ostatecznie wybranych baz danych będzie mieć wpływ na w projekcie.

Korzystając z bazy danych korzystający z dokumentów, możesz zaimplementować agregacji jako pojedynczy dokument zserializowane w formacie JSON lub w innym formacie. Jednak korzystanie z bazy danych jest niewidoczny z domeny modelu kodu punktu widzenia. Podczas korzystania z bazy danych NoSQL, nadal używasz klas jednostek i klasy głównego agregacji, ale bardziej elastyczne niż przy użyciu programu EF Core, ponieważ nie ma charakteru relacyjnego trwałości.

Różnica polega na w sposób utrzymują się tego modelu. Jeśli zaimplementowano modelu domeny oparte na klasach jednostki POCO niezależny od trwałości infrastruktury jego może wyglądać tak, jak można przenieść do infrastruktury trwałości różne, nawet z relacyjnych, NoSQL. Który nie powinien być cel. Zawsze istnieją ograniczenia wady i zalety technologii innej bazy danych, dlatego nie można mieć ten sam model dla relacyjnych lub bazy danych NoSQL. Zmiana modeli trwałości nie jest jest prostym zadaniem, ponieważ transakcje i operacji utrwalania będzie zbytnio.

Na przykład korzystający z dokumentów bazy danych jest akceptowalne dla agregacji głównego mieć wielu właściwości kolekcji podrzędnej. W relacyjnej bazie danych wykonywania zapytania o wiele właściwości kolekcji podrzędnej nie jest łatwo zoptymalizowany, ponieważ wrócisz instrukcję SQL wszystkie związek z programów EF. O tym samym modelu domeny dla relacyjnych baz danych lub bazy danych NoSQL nie jest proste i nie powinno się to zrobić. Masz naprawdę projektowania modelu za pomocą zrozumienia sposobu dane będzie można używać w każdej określonej bazy danych.

Korzyści, w przypadku korzystania z bazy danych NoSQL jest czy jednostki są bardziej nieznormalizowany, więc nie należy ustawiać Mapowanie tabeli. Model domeny może być bardziej elastyczne niż przy użyciu relacyjnej bazy danych.

Podczas projektowania modelu domeny na podstawie na agregacji, przenoszenie, NoSQL i korzystający z dokumentów bazy danych może być jeszcze łatwiejsze niż przy użyciu relacyjnej bazy danych, ponieważ agregacje, których można projektować są podobne do serializacji dokumenty w bazie danych korzystający z dokumentów. Następnie można uwzględnić w tych "zbiory" wszystkie informacje potrzebne do tej agregacji.

Na przykład poniższy kod JSON jest przykład implementacji agregacji zamówienie, podczas korzystania z bazy danych korzystający z dokumentów. Jest on podobny do agregacji kolejności wprowadziliśmy w ramach aplikacji eShopOnContainers przykładu, ale bez korzystania z programu EF Core poniżej.

```json
{
    "id": "2017001",
    "orderDate": "2/25/2017",
    "buyerId": "1234567",
    "address": [
        {
        "street": "100 One Microsoft Way",
        "city": "Redmond",
        "state": "WA",
        "zip": "98052",
        "country": "U.S."
        }
    ],
    "orderItems": [
        {"id": 20170011, "productId": "123456", "productName": ".NET T-Shirt",
        "unitPrice": 25, "units": 2, "discount": 0},
        {"id": 20170012, "productId": "123457", "productName": ".NET Mug",
        "unitPrice": 15, "units": 1, "discount": 0}
    ]
}
```

## <a name="introduction-to-azure-cosmos-db-and-the-native-cosmos-db-api"></a>Wprowadzenie do usługi Azure Cosmos DB i natywnego interfejsu API Cosmos DB

[Usługa Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction) to usługa globalnie rozproszona baza danych firmy Microsoft dla aplikacji o kluczowym znaczeniu. Usługa Azure Cosmos DB zapewnia [kompleksowa dystrybucja globalna](https://docs.microsoft.com/azure/cosmos-db/distribute-data-globally), [elastyczne skalowanie przepływności i przestrzeni dyskowej](https://docs.microsoft.com/azure/cosmos-db/partition-data) na całym świecie, oznaczona jedną cyfrą milisekundowe opóźnienie w 99. percentylu, [pięć dobrze zdefiniowanych poziomów spójności](https://docs.microsoft.com/azure/cosmos-db/consistency-levels)oraz gwarantowaną wysoką dostępność, wspierane przez [wiodące w branży umowy SLA](https://azure.microsoft.com/support/legal/sla/cosmos-db/). Usługa Azure Cosmos DB [automatycznie indeksuje dane](https://www.vldb.org/pvldb/vol8/p1668-shukla.pdf) bez konieczności zarządzania schematami i indeksami. Jest wiele modeli i obsługuje dokumentów, pary klucz wartość, wykres i modele dokumentowe.

![Usługa Azure Cosmos DB to globalnie dystrybuowana gwarantowane małe opóźnienia bazy danych, która jest możliwy za pomocą cztery Protokoły interfejsu API. ](./media/image19.1.png)
**Rysunek 7-19**. Dystrybucję globalną usługi Azure Cosmos DB

Kiedy używasz C\# modelu implementacji agregacji, który będzie używany przez usługi Azure Cosmos DB interfejsu API, agregacja może mieć postać podobną do C\# klasy POCO używane z programem EF Core. Różnica polega na w taki sposób, aby ich używać z warstw aplikacji i infrastruktury, zgodnie z poniższym kodem:

```csharp
// C# EXAMPLE OF AN ORDER AGGREGATE BEING PERSISTED WITH AZURE COSMOS DB API
// *** Domain Model Code ***
// Aggregate: Create an Order object with its child entities and/or value objects.
// Then, use AggregateRoot’s methods to add the nested objects so invariants and
// logic is consistent across the nested properties (value objects and entities).

Order orderAggregate = new Order
{
    Id = "2017001",
    OrderDate = new DateTime(2005, 7, 1),
    BuyerId = "1234567",
    PurchaseOrderNumber = "PO18009186470"
}

Address address = new Address
{
    Street = "100 One Microsoft Way",
    City = "Redmond",
    State = "WA",
    Zip = "98052",
    Country = "U.S."
}

orderAggregate.UpdateAddress(address);

OrderItem orderItem1 = new OrderItem
{
    Id = 20170011,
    ProductId = "123456",
    ProductName = ".NET T-Shirt",
    UnitPrice = 25,
    Units = 2,
    Discount = 0;
};

//Using methods with domain logic within the entity. No anemic-domain model
orderAggregate.AddOrderItem(orderItem1);
// *** End of Domain Model Code ***

// *** Infrastructure Code using Cosmos DB Client API ***
Uri collectionUri = UriFactory.CreateDocumentCollectionUri(databaseName,
    collectionName);

await client.CreateDocumentAsync(collectionUri, orderAggregate);

// As your app evolves, let's say your object has a new schema. You can insert
// OrderV2 objects without any changes to the database tier.
Order2 newOrder = GetOrderV2Sample("IdForSalesOrder2");
await client.CreateDocumentAsync(collectionUri, newOrder);
```

Widać, że sposób pracy z modelu domeny może być w podobny sposób, możesz użyć go w warstwie modelu domeny podczas infrastruktury jest EF. Zapewnienie spójności, invariants i sprawdzania poprawności w agregacji są nadal używać tych samych metod głównego agregacji.

Jednak gdy można utrwalić modelu w bazie danych NoSQL, kod i zmiany interfejsu API, które znacznie w porównaniu do kod programem EF Core lub innego kodu, związane z relacyjnych baz danych.

## <a name="implement-net-code-targeting-mongodb-and-azure-cosmos-db"></a>Implementowanie kodu platformy .NET dla bazy danych MongoDB i usługi Azure Cosmos DB

### <a name="use-azure-cosmos-db-from-net-containers"></a>Użyj usługi Azure Cosmos DB z kontenerami .NET

Możesz uzyskać dostęp baz danych Azure Cosmos DB z kodu .NET działających w kontenerach, takich jak z dowolnej aplikacji platformy .NET. Na przykład Locations.API i Marketing.API mikrousług w ramach aplikacji eShopOnContainers są implementowane, dzięki czemu mogą one wykorzystywać baz danych Azure Cosmos DB.

Jednak jest to ograniczenie w usłudze Azure Cosmos DB z platformy Docker rozwoju środowiska punktu widzenia. Nawet w przypadku lokalnych [emulatora usługi Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/local-emulator) można uruchamiać w lokalnym komputerem deweloperskim (np. komputer), jako późnego 2017 po prostu obsługuje on Windows i Linux nie. 

Istnieje również możliwość uruchomienia tego emulatora na platformy Docker, ale tylko na kontenery Windows, a nie z kontenerów systemu Linux. Jeśli aplikacja jest wdrażana jako kontenerów systemu Linux, ponieważ obecnie jest początkowa przeszkoda dla środowiska programistycznego, nie można wdrożyć systemu Linux i kontenerów Windows w Docker for Windows, które znajdują się w tym samym czasie. Albo wszystkie kontenery wdrażane trzeba dla systemu Linux lub Windows.

Idealnym rozwiązaniem i bardziej bezpośredni wdrożenie rozwiązania i testowania aplikacji jest mogli wdrażać swoje systemy baz danych jako kontenery wraz z kontenerów niestandardowych, więc swoje środowiska deweloperskie i testowe zawsze są spójne.

### <a name="use-mongodb-api-for-local-devtest-linuxwindows-containers-plus-azure-cosmos-db"></a>Użyj interfejsu API usługi MongoDB dla kontenerów systemu Linux/Windows lokalnego i testowania oraz usługi Azure Cosmos DB

Cosmos DB w bazach danych obsługują interfejsu API usługi MongoDB dla platformy .NET, a także natywny protokół przewodowy MongoDB. Oznacza to, że przy użyciu istniejących sterowników aplikacji napisanych dla usługi MongoDB może teraz komunikować się z usługą Cosmos DB i używać baz danych Cosmos DB zamiast bazy danych MongoDB, jak pokazano w rysunek 7-20.

![Usługa cosmos DB obsługuje interfejsu API usługi MongoDB dla platformy .NET i usługi MongoDB protokół przewodowy, można łatwo przełączać z bazy danych MongoDb do usługi Cosmos DB. ](./media/image19.2.png)
 **Rysunek 7-20**. Dostęp do usługi Azure Cosmos DB przy użyciu interfejsu API usługi MongoDB i protokół

Jest to wygodna metoda weryfikację koncepcji w środowiskach platformy Docker z kontenerami systemu Linux, ponieważ [obrazu platformy Docker z bazy danych MongoDB](https://hub.docker.com/r/_/mongo/) jest obrazem wielu architektury, który obsługuje kontenery platformy Docker w systemie Linux i kontenerów platformy Docker, Windows.

Jak pokazano na poniższej ilustracji, korzystając z interfejsu API usługi MongoDB, ramach aplikacji eShopOnContainers obsługuje bazy danych MongoDB, Linux i Windows kontenery dla lokalnego środowiska deweloperskiego, ale następnie można przenieść do skalowalnych, PaaS rozwiązania w chmurze jako usługi Azure Cosmos DB, po prostu [ Zmiana parametrów połączenia usługi MongoDB, aby wskazywała usługę Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account).

![Mikrousługi lokalizacji, w ramach aplikacji eShopOnContainers jest implementowany przy użyciu bazy danych MongoDB, ale mogą być przełączane do usługi Cosmos DB, po prostu zmieniając parametry połączenia. ](./media/image20-bis.png)
 **Rysunek 7-21**. przy użyciu bazy danych MongoDB kontenery Środowisko deweloperskie i usługi Azure Cosmos DB dla środowiska produkcyjnego w ramach aplikacji eShopOnContainers

Azure Cosmos DB w środowisku produkcyjnym będzie działać w chmurze platformy Azure PaaS i skalowalna usługa.

Niestandardowe kontenerów platformy .NET Core można uruchomić na rozwoju lokalnego hosta platformy Docker, (który jest przy użyciu platformy Docker for Windows na maszynie z systemem Windows 10), lub można wdrożyć w środowisku produkcyjnym, takich jak Kubernetes w usłudze AKS Azure lub usługi Azure Service Fabric. W tym środowisku drugi będzie wdrożyć tylko kontenerów niestandardowych platformy .NET Core, ale nie w kontenerze bazy danych MongoDB, ponieważ jak się przy użyciu usługi Azure Cosmos DB w chmurze do obsługi danych w środowisku produkcyjnym.

Wyczyść korzyść wynikająca z użycia interfejsu API usługi MongoDB jest, że rozwiązania może działać w obu baz danych, bazy danych MongoDB lub Azure Cosmos DB, dzięki migracji do różnych środowisk powinno być łatwe. Jednak czasami warto używać natywnych interfejsów API (czyli natywnego interfejsu API Cosmos DB), aby w pełni korzystać z możliwości aparatu konkretnej bazy danych.

Aby uzyskać dalsze porównania po prostu przy użyciu bazy danych MongoDB i Cosmos DB w chmurze, zobacz [korzyści z używania usługi Azure Cosmos DB na tej stronie](https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction). 

### <a name="analyze-your-approach-for-production-applications-mongodb-api-vs-cosmos-db-api"></a>Analizuj swoje podejście przez aplikacje produkcyjne: Vs interfejsu API usługi MongoDB. Interfejs API usługi cosmos DB

W ramach aplikacji eShopOnContainers, firma Microsoft korzysta z interfejsu API usługi MongoDB ponieważ priorytetu było całkowicie w środowisku spójne tworzenie i testowanie przy użyciu bazy danych NoSQL, która może również działać z usługą Azure Cosmos DB.

Jednakże jeśli planujesz uzyskiwanie dostępu do usługi Azure Cosmos DB na platformie Azure dla aplikacji produkcyjnych za pomocą interfejsu API bazy danych MongoDB, możesz powinieneś przeanalizować, różnice w możliwości i wydajność podczas dostępu do baz danych Azure Cosmos DB w porównaniu do przy użyciu natywnych przy użyciu interfejsu API usługi MongoDB Interfejs API usługi Azure Cosmos DB. Jeśli jest on podobny można użyć interfejsu API usługi MongoDB i skorzystać z zalet obsługi dwóch baz danych NoSQL, w tym samym czasie.

Można także użyć klastry bazy danych MongoDB jako produkcyjnej bazy danych w chmurze platformy Azure, za pomocą [bazy danych MongoDB usługi Azure Service](https://www.mongodb.com/scale/mongodb-azure-service). Ale nie jest obsługiwane przez firmę Microsoft usługa PaaS. W tym przypadku hostingu platformy Azure jest po prostu rozwiązanie pochodzące z bazy danych MongoDB.

Zasadniczo jest to po prostu zastrzeżenie, podając nie należy zawsze używać interfejsu API usługi MongoDB względem usługi Azure Cosmos DB, ile My mieliśmy, w ramach aplikacji eShopOnContainers, ponieważ jest to wygodne wybór dla kontenerów systemu Linux. Decyzja powinna być oparta na konkretnych potrzeb i testy, które należy wykonać dla aplikacji produkcyjnych.

### <a name="the-code-use-mongodb-api-in-net-core-applications"></a>Kod: Używanie interfejsu API usługi MongoDB w aplikacjach platformy .NET Core

Interfejsu API usługi MongoDB dla platformy .NET jest oparty na pakietach NuGet, należy dodać do swoich projektów, takich jak w projekcie Locations.API pokazano na poniższej ilustracji.

![Widok Eksploratora rozwiązań przedstawiający zależności NuGet bazy danych MongoDB pakietów.](./media/image21-bis.png)

**Rysunek 7-22**. NuGet interfejsu API usługi MongoDB pakietów odwołań w projekcie platformy .NET Core

Teraz Zbadaj kod w poniższych sekcjach.

#### <a name="a-model-used-by-mongodb-api"></a>Model używany przez interfejs API usługi MongoDB

Najpierw należy zdefiniować model, w którym będą przechowywane dane pochodzące z bazy danych w obszarze pamięci aplikacji. Oto przykład model, używane dla lokalizacji, w ramach aplikacji eShopOnContainers.

```csharp
using MongoDB.Bson;
using MongoDB.Bson.Serialization.Attributes;
using MongoDB.Driver.GeoJsonObjectModel;
using System.Collections.Generic;

public class Locations
{
    [BsonId]
    [BsonRepresentation(BsonType.ObjectId)]
    public string Id { get; set; }
    public int LocationId { get; set; }
    public string Code { get; set; }
    [BsonRepresentation(BsonType.ObjectId)]
    public string Parent_Id { get; set; }
    public string Description { get; set; }
    public double Latitude { get; set; }
    public double Longitude { get; set; }
    public GeoJsonPoint<GeoJson2DGeographicCoordinates> Location 
                                                             { get; private set; }
    public GeoJsonPolygon<GeoJson2DGeographicCoordinates> Polygon 
                                                             { get; private set; }
    public void SetLocation(double lon, double lat) => SetPosition(lon, lat);
    public void SetArea(List<GeoJson2DGeographicCoordinates> coordinatesList) 
                                                    => SetPolygon(coordinatesList);

    private void SetPosition(double lon, double lat)
    {
        Latitude = lat;
        Longitude = lon;
        Location = new GeoJsonPoint<GeoJson2DGeographicCoordinates>(
            new GeoJson2DGeographicCoordinates(lon, lat));
    }

    private void SetPolygon(List<GeoJson2DGeographicCoordinates> coordinatesList)
    {
        Polygon = new GeoJsonPolygon<GeoJson2DGeographicCoordinates>(
                  new GeoJsonPolygonCoordinates<GeoJson2DGeographicCoordinates>(
                  new GeoJsonLinearRingCoordinates<GeoJson2DGeographicCoordinates>(
                                                                 coordinatesList)));
    }
}
```

Widać, że nie ma kilka atrybutów i typy pochodzące z pakietów NuGet bazy danych MongoDB.

Bazy danych NoSQL są zazwyczaj bardzo dobrze nadaje się do pracy z danymi hierarchicznymi nierelacyjnych. W tym przykładzie używamy typów bazy danych MongoDB, szczególnie wprowadzone dla lokalizacji geograficznej, takich jak `GeoJson2DGeographicCoordinates`.

#### <a name="retrieve-the-database-and-the-collection"></a>Pobieranie bazy danych i kolekcji

W ramach aplikacji eShopOnContainers utworzyliśmy kontekstu niestandardowej bazy danych, gdzie wdrażamy kod, aby pobrać bazy danych i MongoCollections, tak jak w poniższym kodzie.

```csharp
public class LocationsContext
{
    private readonly IMongoDatabase _database = null;

    public LocationsContext(IOptions<LocationSettings> settings)
    {
        var client = new MongoClient(settings.Value.ConnectionString);
        if (client != null)
            _database = client.GetDatabase(settings.Value.Database);
    }

    public IMongoCollection<Locations> Locations
    {
        get
        {
            return _database.GetCollection<Locations>("Locations");
        }
    }       
}
```

#### <a name="retrieve-the-data"></a>Pobieranie danych

W kodzie języka C#, takie jak kontrolerów internetowych interfejsów API lub implementację niestandardową repozytoriów można napisać kod podobny do następującego podczas wykonywania zapytania za pomocą interfejsu API usługi MongoDB. Należy pamiętać, że `_context` obiekt jest wystąpieniem poprzedniego `LocationsContext` klasy.

```csharp
public async Task<Locations> GetAsync(int locationId)
{
    var filter = Builders<Locations>.Filter.Eq("LocationId", locationId);
    return await _context.Locations
                            .Find(filter)
                            .FirstOrDefaultAsync();
}
```

#### <a name="use-an-env-var-in-the-docker-composeoverrideyml-file-for-the-mongodb-connection-string"></a>Użyj env-var w pliku docker-compose.override.yml dla parametrów połączenia bazy danych MongoDB

Podczas tworzenia obiektu klucza MongoClient, potrzebuje podstawowych parametr, który dokładnie `ConnectionString` parametrem odpowiednią bazę danych. W przypadku ramach aplikacji eShopOnContainers parametry połączenia mogą wskazać, lokalny kontener platformy Docker z bazy danych MongoDB lub z bazą danych Azure Cosmos DB "produkcyjne".  Te parametry połączenia pochodzą ze zmiennych środowiskowych zdefiniowanych w `docker-compose.override.yml` pliki używane podczas wdrażania za pomocą docker-compose lub Visual Studio, tak jak w poniższym kodzie yml.

```yml
# docker-compose.override.yml
version: '3.4'
services:
  # Other services
  locations.api:
    environment:
      # Other settings
      - ConnectionString=${ESHOP_AZURE_COSMOSDB:-mongodb://nosql.data}

```

`ConnectionString` Zmiennej środowiskowej zostanie rozwiązany w ten sposób: Jeśli `ESHOP_AZURE_COSMOSDB` zmienna globalna jest zdefiniowany w `.env` pliku przy użyciu parametrów połączenia usługi Azure Cosmos DB, użyje on dostępu do bazy danych Azure Cosmos DB w chmurze. Jeśli nie jest zdefiniowany, wówczas przyjąć wartość mongodb://nosql.data i użyć kontenera bazy danych mongodb rozwoju.

Poniższy kod przedstawia `.env` plików za pomocą usługi Azure Cosmos DB globalnego zmienna środowiskowa parametrów połączenia, zgodnie z implementacją w ramach aplikacji eShopOnContainers:

```yml
# .env file, in eShopOnContainers root folder
# Other Docker environment variables

ESHOP_EXTERNAL_DNS_NAME_OR_IP=localhost
ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP=<YourDockerHostIP>

#ESHOP_AZURE_COSMOSDB=<YourAzureCosmosDBConnData>

#Other environment variables for additional Azure infrastructure assets
#ESHOP_AZURE_REDIS_BASKET_DB=<YourAzureRedisBasketInfo>
#ESHOP_AZURE_STORAGE_CATALOG_URL=<YourAzureStorage_Catalog_BLOB_URL>
#ESHOP_AZURE_SERVICE_BUS=<YourAzureServiceBusInfo>
```

Powinien usuń znaczniki komentarza wierszu ESHOP_AZURE_COSMOSDB i aktualizacji za pomocą usługi Azure Cosmos DB parametry połączenia uzyskane w witrynie Azure portal jako wyjaśnione w [połączyć aplikację MongoDB w usłudze Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account).

Jeśli `ESHOP_AZURE_COSMOSDB` zmienna globalna jest pusta, co oznacza, że zostanie ona opatrzona komentarzem na zewnątrz w `.env` pliku, kontener używa domyślne parametry połączenia bazy danych MongoDB wskazujący lokalny kontener bazy danych MongoDB, wdrożonych w ramach aplikacji eShopOnContainers, który nosi nazwę `nosql.data`i została zdefiniowana w pliku docker-compose, jak pokazano w poniższym kodzie yml. 

``` yml
# docker-compose.yml
version: '3.4'
services:
  # ...Other services...
  nosql.data:
    image: mongo
```

#### <a name="additional-resources"></a>Dodatkowe zasoby

- **Modelowanie danych dokumentu dla baz danych NoSQL** \
  <https://docs.microsoft.com/azure/cosmos-db/modeling-data>

- **Vaughn Vernon. Idealne rozwiązanie oparte na domenie projektu agregacji Store?** \
  <https://kalele.io/blog-posts/the-ideal-domain-driven-design-aggregate-store/>

- **Wprowadzenie do usługi Azure Cosmos DB: Interfejs API dla bazy danych MongoDB**  \
  <https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction>

- **Azure Cosmos DB: Tworzenie aplikacji internetowej interfejsu API usługi MongoDB przy użyciu platformy .NET i witryny Azure portal**  \
  [https://docs.microsoft.com/azure/cosmos-db/create-mongodb-dotnet](https://docs.microsoft.com/azure/cosmos-db/create-mongodb-dotnet )

- **Korzystanie z emulatora usługi Azure Cosmos DB do lokalnego tworzenia i testowania**  \
  <https://docs.microsoft.com/azure/cosmos-db/local-emulator>

- **Łączenie aplikacji bazy danych MongoDB w usłudze Azure Cosmos DB**  \
  <https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account>

- **Obraz Cosmos DB Emulator Docker (kontener Windows)**  \
  <https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator/>

- **Obraz platformy Docker z bazy danych MongoDB (Linux i kontenerów Windows)**  \
  <https://hub.docker.com/\_/mongo/>

- **Korzystanie z programu MongoChef (z programu z programu Studio 3T), za pomocą usługi Azure Cosmos DB: Interfejs API dla konta bazy danych MongoDB**  \
  <https://docs.microsoft.com/azure/cosmos-db/mongodb-mongochef>

>[!div class="step-by-step"]
>[Poprzednie](infrastructure-persistence-layer-implemenation-entity-framework-core.md)
>[dalej](microservice-application-layer-web-api-design.md)
