---
title: Korzystanie z baz danych NoSQL jako infrastruktury trwałości
description: Zrozumienie korzystania z baz danych NoSql w ogóle, a azure cosmos DB w szczególności jako opcja do zaimplementowania trwałości.
ms.date: 01/30/2020
ms.openlocfilehash: 9c51e48d82aa0cf0234275f09df43f7a654f0ca8
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988443"
---
# <a name="use-nosql-databases-as-a-persistence-infrastructure"></a>Używanie baz danych NoSQL jako infrastruktury trwałości

Korzystając z baz danych NoSQL dla warstwy danych infrastruktury, zazwyczaj nie należy używać ORM jak Entity Framework Core. Zamiast tego należy użyć interfejsu API dostarczonego przez aparat NoSQL, takich jak Azure Cosmos DB, MongoDB, Cassandra, RavenDB, CouchDB lub Tabele usługi Azure Storage.

Jednak podczas korzystania z bazy danych NoSQL, zwłaszcza bazy danych zorientowanych na dokumenty, takich jak Azure Cosmos DB, CouchDB lub RavenDB, sposób projektowania modelu za pomocą agregacji DDD jest częściowo podobny do jak można to zrobić w EF Core, w odniesieniu do identyfikacji zagregowanych korzeni, klas jednostek podrzędnych i klas obiektów wartości. Ale ostatecznie wybór bazy danych będzie miał wpływ na projekt.

Korzystając z bazy danych zorientowanej na dokument, należy zaimplementować agregację jako pojedynczy dokument, serializowany w formacie JSON lub innym formacie. Jednak użycie bazy danych jest przezroczyste z punktu widzenia kodu modelu domeny. Podczas korzystania z bazy danych NoSQL, nadal używasz klas jednostek i zagregowanych klas głównych, ale z większą elastycznością niż podczas korzystania z EF Core, ponieważ trwałość nie jest relacyjne.

Różnica polega na tym, jak utrwalić tego modelu. Jeśli zaimplementowano model domeny na podstawie klas jednostek POCO, niezależny od trwałości infrastruktury, może wyglądać, że można przenieść do innej infrastruktury trwałości, nawet z relacyjne do NoSQL. Jednak to nie powinno być twoim celem. Zawsze istnieją ograniczenia i kompromisy w różnych technologii bazy danych, więc nie będzie można mieć tego samego modelu dla relacyjnych lub NoSQL baz danych. Zmiana modeli trwałości nie jest trywialnym zadaniem, ponieważ operacje transakcji i trwałości będą bardzo różne.

Na przykład w bazie danych zorientowanej na dokument jest w porządku dla agregacji katalogu głównego mieć wiele właściwości kolekcji podrzędnej. W relacyjnej bazie danych wykonywanie zapytań o wiele właściwości kolekcji podrzędnej nie jest łatwo zoptymalizowane, ponieważ otrzymasz instrukcję UNION ALL SQL z ef. Posiadanie tego samego modelu domeny dla relacyjnych baz danych lub baz danych NoSQL nie jest proste i nie należy próbować tego robić. Naprawdę trzeba zaprojektować model ze zrozumieniem, jak dane będą używane w każdej konkretnej bazie danych.

Zaletą podczas korzystania z baz danych NoSQL jest to, że jednostki są bardziej zdenormalizowane, więc nie należy ustawiać mapowania tabeli. Model domeny może być bardziej elastyczny niż przy użyciu relacyjnej bazy danych.

Podczas projektowania modelu domeny na podstawie agregatów przejście do bazy danych zorientowanych na dokument może być jeszcze łatwiejsze niż przy użyciu relacyjnej bazy danych, ponieważ agregaty, które projektujesz, są podobne do dokumentów szeregowanych w bazie danych zorientowanej na dokument. Następnie można uwzględnić w tych "workach" wszystkie informacje, które mogą być potrzebne do tego agregacji.

Na przykład następujący kod JSON jest przykładową implementacją agregacji zamówień podczas korzystania z bazy danych zorientowanej na dokument. Jest podobny do agregacji zamówień zaimplementowaliśmy w przykładzie eShopOnContainers, ale bez użycia EF Core pod spodem.

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

## <a name="introduction-to-azure-cosmos-db-and-the-native-cosmos-db-api"></a>Wprowadzenie do usługi Azure Cosmos DB i macierzystego interfejsu API usługi Cosmos DB

[Usługa Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction) to globalnie rozproszona usługa bazy danych firmy Microsoft dla aplikacji o znaczeniu krytycznym. Usługa Azure Cosmos DB zapewnia [kompleksową globalną dystrybucję](https://docs.microsoft.com/azure/cosmos-db/distribute-data-globally), [elastyczne skalowanie przepływności i pamięci](https://docs.microsoft.com/azure/cosmos-db/partition-data) w skali globalnej, milisekundowe opóźnienia w 99. percentylu, [pięć odpowiednio zdefiniowanych poziomów spójności](https://docs.microsoft.com/azure/cosmos-db/consistency-levels) oraz gwarantowaną wysoką dostępność, wspierane przez [wiodące w branży umowy SLA](https://azure.microsoft.com/support/legal/sla/cosmos-db/). Usługa Azure Cosmos DB [automatycznie indeksuje dane](https://www.vldb.org/pvldb/vol8/p1668-shukla.pdf) bez konieczności zarządzania schematami i indeksami. To usługa wielomodelowa, obsługująca modele oparte na dokumentach, parach klucz-wartość, grafach i kolumnach.

![Diagram przedstawiający globalną dystrybucję usługi Azure Cosmos DB.](./media/nosql-database-persistence-infrastructure/azure-cosmos-db-global-distribution.png)

**Rysunek 7-19**. Globalna dystrybucja usługi Azure Cosmos DB

Korzystając z modelu\# C do zaimplementowania agregacji, która ma być używana przez\# interfejs API usługi Azure Cosmos DB, agregacja może być podobna do klas POCO C używanych z EF Core. Różnica polega na sposobie korzystania z nich z warstw aplikacji i infrastruktury, jak w poniższym kodzie:

```csharp
// C# EXAMPLE OF AN ORDER AGGREGATE BEING PERSISTED WITH AZURE COSMOS DB API
// *** Domain Model Code ***
// Aggregate: Create an Order object with its child entities and/or value objects.
// Then, use AggregateRoot's methods to add the nested objects so invariants and
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

Widać, że sposób pracy z modelem domeny może być podobny do sposobu, w jaki używasz go w warstwie modelu domeny, gdy infrastruktura jest EF. Nadal używasz tych samych metod głównego agregacji, aby zapewnić spójność, invariants i sprawdzania poprawności w ramach agregacji.

Jednak po utrwaleniu modelu w bazie danych NoSQL, kod i interfejs API zmieniają się dramatycznie w porównaniu do kodu EF Core lub innego kodu związanego z relacyjnych baz danych.

## <a name="implement-net-code-targeting-mongodb-and-azure-cosmos-db"></a>Implementowanie kodu platformy NET kierowanego na usługi MongoDB i usługę Azure Cosmos DB

### <a name="use-azure-cosmos-db-from-net-containers"></a>Korzystanie z bazy danych usługi Azure Cosmos DB z kontenerów platformy .NET

Dostęp do baz danych usługi Azure Cosmos DB można uzyskać z kodu platformy .NET uruchomionego w kontenerach, na przykład z dowolnej innej aplikacji platformy .NET. Na przykład lokalizacje.API i marketing.API mikrousług w eShopOnContainers są implementowane, dzięki czemu mogą korzystać z baz danych usługi Azure Cosmos DB.

Jednak istnieje ograniczenie w usłudze Azure Cosmos DB z punktu widzenia środowiska deweloperskiego platformy Docker. Mimo że istnieje lokalna [azure cosmos db emulator,](https://docs.microsoft.com/azure/cosmos-db/local-emulator) który można uruchomić na komputerze deweloperskim lokalnym, obsługuje tylko system Windows. Linux i macOS nie są obsługiwane.

Istnieje również możliwość uruchomienia tego emulatora na platformy Docker, ale tylko na kontenerach systemu Windows, a nie z kontenerami systemu Linux. Jest to początkowy handicap dla środowiska programistycznego, jeśli aplikacja jest wdrażana jako kontenery systemu Linux, ponieważ obecnie nie można wdrożyć kontenerów systemu Linux i Windows w programie Docker dla systemu Windows w tym samym czasie. Albo wszystkie kontenery są wdrażane muszą być dla Systemu Linux lub dla systemu Windows.

Idealnym i prostszym wdrożeniem dla rozwiązania deweloperskiego/testowego jest możliwość wdrażania systemów bazy danych jako kontenerów wraz z kontenerami niestandardowymi, dzięki czemu środowiska deweloperów/testów są zawsze spójne.

### <a name="use-mongodb-api-for-local-devtest-linuxwindows-containers-plus-azure-cosmos-db"></a>Użyj interfejsu API MongoDB dla lokalnych kontenerów deweloperskich/testowych systemu Linux/Windows oraz usługi Azure Cosmos DB

Bazy danych Usługi Cosmos DB obsługują interfejs API MongoDB dla platformy .NET oraz macierzysty protokół przewodowy MongoDB. Oznacza to, że przy użyciu istniejących sterowników, aplikacja napisana dla MongoDB może teraz komunikować się z usługą Cosmos DB i używać baz danych usługi Cosmos DB zamiast baz danych MongoDB, jak pokazano na rysunku 7-20.

![Diagram pokazujący, że usługa Cosmos DB obsługuje protokół przewodowy .NET i MongoDB.](./media/nosql-database-persistence-infrastructure/mongodb-api-wire-protocol.png)

**Rysunek 7-20**. Korzystanie z interfejsu API i protokołu MongoDB w celu uzyskania dostępu do usługi Azure Cosmos DB

Jest to bardzo wygodne podejście do weryfikacji pojęć w środowiskach platformy Docker z kontenerami systemu Linux, ponieważ [obraz platformy Docker MongoDB](https://hub.docker.com/r/_/mongo/) jest obrazem wielokołowym, który obsługuje kontenery Systemu Docker Linux i kontenery systemu Windows platformy Docker.

Jak pokazano na poniższej ilustracji, za pomocą interfejsu API MongoDB, eShopOnContainers obsługuje kontenery MongoDB Linux i Windows dla lokalnego środowiska programistycznego, ale następnie można przejść do skalowalnego rozwiązania chmury PaaS jako usługi Azure Cosmos DB, po prostu [zmieniając ciąg połączenia MongoDB, aby wskazać usługę Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account).

![Diagram pokazujący, że mikrousługa lokalizacji w eShopOnContainers można użyć usługi Cosmos DB lub Mongo DB.](./media/nosql-database-persistence-infrastructure/eshoponcontainers-mongodb-containers.png)

**Rysunek 7-21**. EShopOnContainers przy użyciu kontenerów MongoDB dla dev-env lub Azure Cosmos DB dla produkcji

Produkcyjna usługa Azure Cosmos DB będzie działać w chmurze platformy Azure jako usługa PaaS i skalowalna.

Niestandardowe kontenery .NET Core można uruchomić na lokalnym hoście platformy Docker rozwoju (który używa platformy Docker dla systemu Windows na komputerze z systemem Windows 10) lub zostać wdrożone w środowisku produkcyjnym, takich jak Kubernetes w usłudze Azure AKS lub azure service service fabric. W tym drugim środowisku można wdrożyć tylko kontenery niestandardowe .NET Core, ale nie kontener MongoDB, ponieważ można używać usługi Azure Cosmos DB w chmurze do obsługi danych w środowisku produkcyjnym.

Wyraźną zaletą korzystania z interfejsu API mongodb jest, że rozwiązanie może działać w obu aparatach bazy danych, MongoDB lub Azure Cosmos DB, więc migracje do różnych środowisk powinny być łatwe. Jednak czasami warto użyć natywnego interfejsu API (czyli natywnego interfejsu API usługi Cosmos DB), aby w pełni wykorzystać możliwości określonego aparatu bazy danych.

Aby uzyskać dalsze porównanie po prostu przy użyciu MongoDB i Cosmos DB w chmurze, zobacz [korzyści z używania usługi Azure Cosmos DB na tej stronie](https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction).

### <a name="analyze-your-approach-for-production-applications-mongodb-api-vs-cosmos-db-api"></a>Analizowanie podejścia pod kątem aplikacji produkcyjnych: interfejs API mongodb vs. Cosmos DB API

W eShopOnContainers używamy interfejsu API MongoDB, ponieważ naszym priorytetem było zasadniczo mieć spójne środowisko deweloper/test przy użyciu bazy danych NoSQL, która może również współpracować z usługą Azure Cosmos DB.

Jednak jeśli planujesz używać interfejsu API mongodb do uzyskiwania dostępu do usługi Azure Cosmos DB na platformie Azure dla aplikacji produkcyjnych, należy przeanalizować różnice w możliwościach i wydajności podczas korzystania z interfejsu API mongodb, aby uzyskać dostęp do baz danych usługi Azure Cosmos DB w porównaniu z przy użyciu natywnego interfejsu API usługi Azure Cosmos DB. Jeśli jest podobny, możesz użyć interfejsu API MongoDB i uzyskać korzyści z obsługi dwóch aparatów bazy danych NoSQL w tym samym czasie.

Klastry MongoDB można również użyć jako produkcyjnej bazy danych w chmurze platformy Azure, również z [usługą MongoDB Azure Service.](https://www.mongodb.com/scale/mongodb-azure-service) Ale to nie jest usługa PaaS świadczona przez firmę Microsoft. W takim przypadku platforma Azure jest po prostu hosting tego rozwiązania pochodzących z MongoDB.

Zasadniczo jest to tylko zastrzeżenie stwierdzające, że nie zawsze należy używać interfejsu API MongoDB przeciwko usłudze Azure Cosmos DB, tak jak to miało miejsce w eShopOnContainers, ponieważ był to wygodny wybór dla kontenerów systemu Linux. Decyzja powinna być oparta na konkretnych potrzebach i testach, które należy wykonać dla aplikacji produkcyjnej.

### <a name="the-code-use-mongodb-api-in-net-core-applications"></a>Kod: Użyj interfejsu API MongoDB w aplikacjach .NET Core

Interfejs API mongodb dla platformy .NET jest oparty na pakietach NuGet, które należy dodać do projektów, na przykład w projekcie Locations.API pokazanym na poniższym rysunku.

![Zrzut ekranu przedstawiający zależności w pakietach MongoDB NuGet.](./media/nosql-database-persistence-infrastructure/mongodb-api-nuget-packages.png)

**Rysunek 7-22**. Odwołania do pakietów NuGet interfejsu API mongodb w projekcie .NET Core

Zbadajmy kod w poniższych sekcjach.

#### <a name="a-model-used-by-mongodb-api"></a>Model używany przez interfejs API MongoDB

Najpierw należy zdefiniować model, który będzie przechowywać dane pochodzące z bazy danych w pamięci aplikacji. Oto przykład modelu używanego dla lokalizacji w eShopOnContainers.

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

Widać, że istnieje kilka atrybutów i typów pochodzących z pakietów MongoDB NuGet.

Bazy danych NoSQL są zwykle bardzo dobrze przystosowane do pracy z nierelacyjnymi danymi hierarchicznymi. W tym przykładzie używamy typów MongoDB specjalnie dla `GeoJson2DGeographicCoordinates`lokalizacji geograficznych, takich jak .

#### <a name="retrieve-the-database-and-the-collection"></a>Pobieranie bazy danych i kolekcji

W eShopOnContainers utworzyliśmy niestandardowy kontekst bazy danych, w którym implementujemy kod do pobierania bazy danych i MongoCollections, jak w poniższym kodzie.

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

W kodzie języka C#, takich jak kontrolery interfejsu API sieci Web lub implementacji repozytoriów niestandardowych, można napisać podobny kod do następujących podczas wykonywania zapytań za pośrednictwem interfejsu API mongodb. Należy zauważyć, że `_context` obiekt jest `LocationsContext` wystąpieniem poprzedniej klasy.

```csharp
public async Task<Locations> GetAsync(int locationId)
{
    var filter = Builders<Locations>.Filter.Eq("LocationId", locationId);
    return await _context.Locations
                            .Find(filter)
                            .FirstOrDefaultAsync();
}
```

#### <a name="use-an-env-var-in-the-docker-composeoverrideyml-file-for-the-mongodb-connection-string"></a>Użyj env-var w pliku docker-compose.override.yml dla ciągu połączenia mongodb

Podczas tworzenia obiektu MongoClient, potrzebuje parametru fundamentalnego, `ConnectionString` który jest dokładnie parametr wskazujący na właściwą bazę danych. W przypadku eShopOnContainers parametry połączenia można wskazać lokalnego kontenera platformy Docker MongoDB lub do "produkcyjnej" bazy danych usługi Azure Cosmos DB.  Ten ciąg połączenia pochodzi ze zmiennych `docker-compose.override.yml` środowiskowych zdefiniowanych w plikach używanych podczas wdrażania za pomocą docker-compose lub Visual Studio, jak w poniższym kodzie yml.

```yml
# docker-compose.override.yml
version: '3.4'
services:
  # Other services
  locations-api:
    environment:
      # Other settings
      - ConnectionString=${ESHOP_AZURE_COSMOSDB:-mongodb://nosqldata}

```

Zmienna środowiskowa jest rozpoznawana `ESHOP_AZURE_COSMOSDB` w ten sposób: `.env` Jeśli zmienna globalna `ConnectionString` jest zdefiniowana w pliku z ciągiem połączenia usługi Azure Cosmos DB, użyje jej do uzyskania dostępu do bazy danych usługi Azure Cosmos DB w chmurze. Jeśli nie jest zdefiniowany, zajmie `mongodb://nosqldata` wartość i użyje deweloperskiego kontenera MongoDB.

Poniższy kod `.env` przedstawia plik z globalną zmienną środowiska parametry połączenia usługi Azure Cosmos DB, zgodnie z implementacji w eShopOnContainers:

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

Odkomentuj wiersz ESHOP_AZURE_COSMOSDB i zaktualizuj ją za pomocą ciągu połączenia usługi Azure Cosmos DB uzyskanego z portalu Azure, jak wyjaśniono w [temacie Połącz aplikację MongoDB z usługą Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account).

Jeśli `ESHOP_AZURE_COSMOSDB` zmienna globalna jest pusta, co `.env` oznacza, że jest komentowana w pliku, kontener używa domyślnego ciągu połączenia MongoDB. Ten ciąg połączenia wskazuje na lokalny kontener MongoDB wdrożony w `nosqldata` eShopOnContainers, który jest nazwany i został zdefiniowany w pliku docker-compose, jak pokazano w następującym kodzie .yml:

``` yml
# docker-compose.yml
version: '3.4'
services:
  # ...Other services...
  nosqldata:
    image: mongo
```

#### <a name="additional-resources"></a>Zasoby dodatkowe

- **Modelowanie danych dokumentu dla baz danych NoSQL** \
  <https://docs.microsoft.com/azure/cosmos-db/modeling-data>

- **Vaughn Vernon. Idealny sklep z agregatami projektów opartych na domenie?** \
  <https://kalele.io/blog-posts/the-ideal-domain-driven-design-aggregate-store/>

- **Wprowadzenie do usługi Azure Cosmos DB: INTERFEJS API dla mongodb**  \
  <https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction>

- **Usługa Azure Cosmos DB: Tworzenie aplikacji sieci Web interfejsu API witryny MongoDB za pomocą platformy .NET i portalu Azure**  \
  <https://docs.microsoft.com/azure/cosmos-db/create-mongodb-dotnet>

- **Użyj emulatora usługi Azure Cosmos DB do lokalnego rozwoju i testowania**  \
  <https://docs.microsoft.com/azure/cosmos-db/local-emulator>

- **Łączenie aplikacji MongoDB z usługą Azure Cosmos DB**  \
  <https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account>

- **Obraz platformy Dokatora emulatora bazy danych usługi Cosmos (kontener systemu Windows)**  \
  <https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator/>

- **Obraz platformy MongoDB Docker (Linux i Windows Container)**  \
  <https://hub.docker.com/_/mongo/>

- **Korzystanie z usługi MongoChef (Studio 3T) z usługą Azure Cosmos DB: API dla konta MongoDB**  \
  <https://docs.microsoft.com/azure/cosmos-db/mongodb-mongochef>

>[!div class="step-by-step"]
>[Poprzedni](infrastructure-persistence-layer-implemenation-entity-framework-core.md)
>[następny](microservice-application-layer-web-api-design.md)
