---
title: Korzystanie z baz danych NoSQL jako infrastruktury trwałości
description: Zrozumieć użycie baz danych NoSql w ogóle i usługi Azure Cosmos DB w szczególności jako opcja implementowania trwałości.
ms.date: 01/30/2020
ms.openlocfilehash: 7da4141d9aadc4aaa265ac97d328bc4b7569a0cb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77502393"
---
# <a name="use-nosql-databases-as-a-persistence-infrastructure"></a>Używanie baz danych NoSQL jako infrastruktury trwałości

Korzystając z baz danych NoSQL dla warstwy danych infrastruktury, zazwyczaj nie używasz ORM jak Entity Framework Core. Zamiast tego używasz interfejsu API dostarczonego przez aparat NoSQL, takich jak Azure Cosmos DB, MongoDB, Cassandra, RavenDB, CouchDB lub Tabele magazynu Azure.

Jednak w przypadku korzystania z bazy danych NoSQL, zwłaszcza bazy danych zorientowanych na dokumenty, takich jak Azure Cosmos DB, CouchDB lub RavenDB, sposób projektowania modelu za pomocą agregatów DDD jest częściowo podobny do sposobu, w jaki można to zrobić w EF Core, w odniesieniu do identyfikacji zagregowane katalogi główne, klasy jednostek podrzędnych i klasy obiektów wartości. Ale ostatecznie wybór bazy danych wpłynie na projekt.

Korzystając z bazy danych zorientowanej na dokument, należy zaimplementować agregacji jako pojedynczy dokument, serializowany w JSON lub w innym formacie. Jednak użycie bazy danych jest nieprzezroczyste z punktu widzenia kodu modelu domeny. Korzystając z bazy danych NoSQL, nadal używasz klas jednostek i klas głównych agregacji, ale z większą elastycznością niż podczas korzystania z EF Core, ponieważ trwałość nie jest relacyjna.

Różnica polega na tym, jak utrwalić tego modelu. Jeśli zaimplementowano model domeny na podstawie klas jednostek POCO, agnostyk do trwałości infrastruktury, może to wyglądać, że można przenieść do innej infrastruktury trwałości, nawet z relacyjnych do NoSQL. Jednak to nie powinno być twoim celem. Zawsze istnieją ograniczenia i kompromisy w różnych technologiach bazy danych, więc nie będzie można mieć tego samego modelu dla relacyjnych lub nosql baz danych. Zmiana modeli trwałości nie jest zadaniem trywialnym, ponieważ transakcje i operacje trwałości będą bardzo różne.

Na przykład w bazie danych zorientowanych na dokument jest w porządku dla katalogu głównego agregacji mieć wiele właściwości kolekcji podrzędnej. W relacyjnej bazie danych wykonywanie zapytań dotyczących wielu właściwości kolekcji podrzędnych nie jest łatwo zoptymalizowane, ponieważ otrzymasz instrukcję UNION ALL SQL z powrotem z EF. Posiadanie tego samego modelu domeny dla relacyjnych baz danych lub baz danych NoSQL nie jest proste i nie należy próbować tego robić. Naprawdę trzeba zaprojektować model ze zrozumieniem, jak dane będą używane w każdej określonej bazie danych.

Korzyścią podczas korzystania z baz danych NoSQL jest to, że jednostki są bardziej zdenormalizowane, więc nie można ustawić mapowanie tabeli. Model domeny może być bardziej elastyczny niż w przypadku korzystania z relacyjnej bazy danych.

Podczas projektowania modelu domeny na podstawie agregacji przejście do bazy danych NoSQL i zorientowanych na dokumenty może być jeszcze łatwiejsze niż przy użyciu relacyjnej bazy danych, ponieważ agregaty, które projektujesz, są podobne do dokumentów seryjnych w bazie danych zorientowanych na dokumenty. Następnie można dołączyć do tych "worków" wszystkie informacje, które mogą być potrzebne do tego agregacji.

Na przykład następujący kod JSON jest przykładową implementacją agregacji zamówienia podczas korzystania z bazy danych zorientowanej na dokument. Jest on podobny do agregacji zamówienia zaimplementowaliśmy w eShopOnContainers próbki, ale bez użycia EF Core pod spodem.

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

## <a name="introduction-to-azure-cosmos-db-and-the-native-cosmos-db-api"></a>Wprowadzenie do usługi Azure Cosmos DB i natywnego interfejsu API usługi Cosmos DB

[Usługa Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction) to globalnie rozproszona usługa bazy danych firmy Microsoft dla aplikacji o znaczeniu krytycznym. Usługa Azure Cosmos DB zapewnia [kompleksową globalną dystrybucję](https://docs.microsoft.com/azure/cosmos-db/distribute-data-globally), [elastyczne skalowanie przepływności i pamięci](https://docs.microsoft.com/azure/cosmos-db/partition-data) w skali globalnej, milisekundowe opóźnienia w 99. percentylu, [pięć odpowiednio zdefiniowanych poziomów spójności](https://docs.microsoft.com/azure/cosmos-db/consistency-levels) oraz gwarantowaną wysoką dostępność, wspierane przez [wiodące w branży umowy SLA](https://azure.microsoft.com/support/legal/sla/cosmos-db/). Usługa Azure Cosmos DB [automatycznie indeksuje dane](https://www.vldb.org/pvldb/vol8/p1668-shukla.pdf) bez konieczności zarządzania schematami i indeksami. To usługa wielomodelowa, obsługująca modele oparte na dokumentach, parach klucz-wartość, grafach i kolumnach.

![Diagram przedstawiający globalną dystrybucję usługi Azure Cosmos DB.](./media/nosql-database-persistence-infrastructure/azure-cosmos-db-global-distribution.png)

**Rysunek 7-19**. Globalna dystrybucja usługi Azure Cosmos DB

Korzystając z modelu\# C do zaimplementowania agregacji do użycia przez interfejs API usługi\# Azure Cosmos DB, agregacji może być podobny do klas POCO C używane z EF Core. Różnica polega na sposobie ich używania z warstw aplikacji i infrastruktury, jak w poniższym kodzie:

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

Można zobaczyć, że sposób pracy z modelem domeny może być podobny do sposobu, w jaki używasz go w warstwie modelu domeny, gdy infrastruktura jest EF. Nadal używasz tych samych metod root agregacji, aby zapewnić spójność, invariants i sprawdzania poprawności w agregacji.

Jednak po utrwalić modelu do bazy danych NoSQL, kod i interfejs API zmieniają się dramatycznie w porównaniu do kodu EF Core lub innego kodu związanego z relacyjnych baz danych.

## <a name="implement-net-code-targeting-mongodb-and-azure-cosmos-db"></a>Implementowanie kodu .NET dla usługi MongoDB i usługi Azure Cosmos DB

### <a name="use-azure-cosmos-db-from-net-containers"></a>Korzystanie z usługi Azure Cosmos DB z kontenerów platformy .NET

Dostęp do baz danych usługi Azure Cosmos DB można uzyskać z kodu .NET działającego w kontenerach, podobnie jak z dowolnej innej aplikacji .NET. Na przykład locations.API i Marketing.API mikrousług w eShopOnContainers są implementowane, dzięki czemu mogą korzystać z baz danych usługi Azure Cosmos DB.

Istnieje jednak ograniczenie w usłudze Azure Cosmos DB z punktu widzenia środowiska programistycznego platformy Docker. Mimo że istnieje lokalny [emulator usługi Azure Cosmos DB,](https://docs.microsoft.com/azure/cosmos-db/local-emulator) który można uruchomić na komputerze deweloperskim, obsługuje tylko system Windows. Systemy Linux i macOS nie są obsługiwane.

Istnieje również możliwość uruchomienia tego emulatora na platformie Docker, ale tylko w kontenerach systemu Windows, a nie z kontenerami systemu Linux. Jest to początkowe utrudnienie dla środowiska programistycznego, jeśli aplikacja jest wdrażana jako kontenery systemu Linux, ponieważ obecnie nie można wdrożyć kontenerów systemu Linux i Windows na platformie Docker dla systemu Windows w tym samym czasie. Wszystkie kontenery wdrażane muszą być dla systemu Linux lub windows.

Idealne i bardziej proste wdrożenie dla rozwiązania dewelopera/testu jest możliwość wdrażania systemów baz danych jako kontenerów wraz z kontenerów niestandardowych, dzięki czemu środowiska deweloperów/testów są zawsze spójne.

### <a name="use-mongodb-api-for-local-devtest-linuxwindows-containers-plus-azure-cosmos-db"></a>Użyj interfejsu API MongoDB dla lokalnych kontenerów deweloperskich/testowych systemu Linux/Windows oraz usługi Azure Cosmos DB

Bazy danych usługi Cosmos DB obsługują interfejs API MongoDB dla .NET, a także natywny protokół przewodowy MongoDB. Oznacza to, że przy użyciu istniejących sterowników, aplikacja napisana dla MongoDB może teraz komunikować się z usługą Cosmos DB i używać baz danych usługi Cosmos DB zamiast baz danych MongoDB, jak pokazano na rysunku 7-20.

![Diagram pokazujący, że usługa Cosmos DB obsługuje protokół drutu .NET i MongoDB.](./media/nosql-database-persistence-infrastructure/mongodb-api-wire-protocol.png)

**Rysunek 7-20**. Korzystanie z interfejsu API i protokołu MongoDB w celu uzyskania dostępu do usługi Azure Cosmos DB

Jest to bardzo wygodne podejście do sprawdzania pojęć w środowiskach platformy Docker z kontenerami systemu Linux, ponieważ [obraz docker MongoDB](https://hub.docker.com/r/_/mongo/) jest obrazem wielołukowym obsługującym kontenery docker Linux i kontenery systemu Windows platformy Docker.

Jak pokazano na poniższej ilustracji, przy użyciu interfejsu API MongoDB, eShopOnContainers obsługuje kontenery MongoDB Linux i Windows dla lokalnego środowiska programistycznego, ale następnie można przejść do skalowalne, paas rozwiązanie w chmurze jako usługi Azure Cosmos DB, po prostu [zmieniając ciąg połączenia MongoDB do punktu usługi Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account).

![Diagram pokazujący, że mikrousługi lokalizacji w eShopOnContainers można użyć usługi Cosmos DB lub Mongo DB.](./media/nosql-database-persistence-infrastructure/eshoponcontainers-mongodb-containers.png)

**Rysunek 7-21**. eShopOnContainers przy użyciu kontenerów MongoDB dla dev-env lub usługi Azure Cosmos DB dla produkcji

Produkcyjne usługi Azure Cosmos DB będzie działać w chmurze platformy Azure jako PaaS i skalowalne usługi.

Niestandardowe kontenery .NET Core można uruchomić na lokalnym hoście platformy Docker rozwoju (który używa platformy Docker dla systemu Windows na komputerze z systemem Windows 10) lub być wdrożone w środowisku produkcyjnym, takich jak Kubernetes w usłudze Azure AKS lub sieci szkieletowej usług Azure. W tym drugim środowisku można wdrożyć tylko kontenery niestandardowe .NET Core, ale nie kontener Akcjonord y dostępu do usługi MongoDB, ponieważ chcesz używać usługi Azure Cosmos DB w chmurze do obsługi danych w środowisku produkcyjnym.

Wyraźną zaletą korzystania z interfejsu API MongoDB jest to, że rozwiązanie może działać w obu aparatach baz danych, MongoDB lub usłudze Azure Cosmos DB, więc migracje do różnych środowisk powinny być łatwe. Jednak czasami warto użyć natywnego interfejsu API (który jest macierzystym interfejsem API usługi Cosmos DB), aby w pełni wykorzystać możliwości określonego aparatu bazy danych.

Aby uzyskać dalsze porównanie między po prostu przy użyciu usługi MongoDB i usługi Cosmos DB w chmurze, zobacz [korzyści z korzystania z usługi Azure Cosmos DB na tej stronie](https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction).

### <a name="analyze-your-approach-for-production-applications-mongodb-api-vs-cosmos-db-api"></a>Analizuj swoje podejście do zastosowań produkcyjnych: Interfejs API MongoDB w porównaniu z interfejsem API usługi Cosmos DB

W eShopOnContainers używamy interfejsu API MongoDB, ponieważ naszym priorytetem było zasadniczo mieć spójne środowisko deweloperów/testów przy użyciu bazy danych NoSQL, która może również współpracować z usługi Azure Cosmos DB.

Jeśli jednak planujesz użyć interfejsu API MongoDB do uzyskiwania dostępu do usługi Azure Cosmos DB na platformie Azure dla aplikacji produkcyjnych, należy przeanalizować różnice w możliwościach i wydajności podczas korzystania z interfejsu API MongoDB w celu uzyskania dostępu do baz danych usługi Azure Cosmos DB w porównaniu z użyciem natywnych Interfejs API usługi Azure Cosmos DB. Jeśli jest podobny, możesz użyć interfejsu API MongoDB i możesz korzystać z obsługi dwóch aparatów baz danych NoSQL w tym samym czasie.

Można również użyć klastrów MongoDB jako produkcyjnej bazy danych w chmurze platformy Azure, zbyt, z [MongoDB Usługi Azure](https://www.mongodb.com/scale/mongodb-azure-service). Ale to nie jest usługa PaaS świadczona przez Firmę Microsoft. W takim przypadku platforma Azure jest tylko hosting tego rozwiązania pochodzącego z MongoDB.

Zasadniczo jest to tylko zastrzeżenie stwierdzające, że nie zawsze należy używać interfejsu API MongoDB w usłudze Azure Cosmos DB, tak jak to miało miejsce w eShopOnContainers, ponieważ był to wygodny wybór dla kontenerów systemu Linux. Decyzja powinna być oparta na konkretnych potrzebach i testach, które należy wykonać dla aplikacji produkcyjnej.

### <a name="the-code-use-mongodb-api-in-net-core-applications"></a>Kod: Użyj interfejsu API MongoDB w aplikacjach .NET Core

Interfejs API MongoDB dla .NET jest oparty na pakietach NuGet, które należy dodać do projektów, takich jak w projekcie Locations.API pokazanym na poniższej stronie.

![Zrzut ekranu przedstawiający zależności w pakietach NuGet MongoDB.](./media/nosql-database-persistence-infrastructure/mongodb-api-nuget-packages.png)

**Rysunek 7-22**. Odwołania pakietów MongoDB API NuGet w projekcie .NET Core

Zbadajmy kod w poniższych sekcjach.

#### <a name="a-model-used-by-mongodb-api"></a>Model używany przez Interfejs API MongoDB

Najpierw należy zdefiniować model, który będzie przechowywać dane pochodzące z bazy danych w przestrzeni pamięci aplikacji. Oto przykład modelu używanego dla lokalizacji w eShopOnContainers.

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

Możesz zobaczyć, że istnieje kilka atrybutów i typów pochodzących z pakietów NuGet MongoDB.

Bazy danych NoSQL są zwykle bardzo dobrze przystosowane do pracy z nierelacyjnymi danymi hierarchicznymi. W tym przykładzie używamy typów MongoDB specjalnie dla lokalizacji `GeoJson2DGeographicCoordinates`geograficznych, takich jak .

#### <a name="retrieve-the-database-and-the-collection"></a>Pobieranie bazy danych i kolekcji

W eShopOnContainers utworzyliśmy kontekst niestandardowej bazy danych, w którym implementujemy kod do pobierania bazy danych i MongoCollections, jak w poniższym kodzie.

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

W kodzie Języka C#, takich jak kontrolery interfejsu API sieci Web lub implementacja niestandardowych repozytoriów, można napisać podobny kod do następującego podczas wykonywania zapytań za pośrednictwem interfejsu API MongoDB. Należy zauważyć, że `_context` obiekt jest `LocationsContext` wystąpieniem poprzedniej klasy.

```csharp
public async Task<Locations> GetAsync(int locationId)
{
    var filter = Builders<Locations>.Filter.Eq("LocationId", locationId);
    return await _context.Locations
                            .Find(filter)
                            .FirstOrDefaultAsync();
}
```

#### <a name="use-an-env-var-in-the-docker-composeoverrideyml-file-for-the-mongodb-connection-string"></a>Użyj pliku env-var w pliku docker-compose.override.yml dla ciągu połączenia MongoDB

Podczas tworzenia MongoClient obiektu, potrzebuje parametru podstawowego, który jest właśnie `ConnectionString` parametr wskazujący na prawej bazy danych. W przypadku eShopOnContainers parametry połączenia można wskazać lokalnego kontenera platformy Docker MongoDB lub "produkcyjnej" bazy danych usługi Azure Cosmos DB.  Ten ciąg połączenia pochodzi ze zmiennych `docker-compose.override.yml` środowiskowych zdefiniowanych w plikach używanych podczas wdrażania z docker-compose lub Visual Studio, jak w poniższym kodzie yml.

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

Zmienna środowiskowa `ConnectionString` jest rozpoznawana w ten sposób: Jeśli zmienna `ESHOP_AZURE_COSMOSDB` globalna jest zdefiniowana w `.env` pliku z parametryą połączenia usługi Azure Cosmos DB, użyje jej do uzyskania dostępu do bazy danych usługi Azure Cosmos DB w chmurze. Jeśli nie jest zdefiniowany, zajmie `mongodb://nosqldata` wartość i użyć kontenera MongoDB rozwoju.

Poniższy kod przedstawia `.env` plik z globalną zmienną środowiskową ciągu połączenia usługi Azure Cosmos DB, zaimplementowany w eShopOnContainers:

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

Odkomentuj wiersz ESHOP_AZURE_COSMOSDB i zaktualizuj go za pomocą ciągu połączenia usługi Azure Cosmos DB uzyskanego z witryny Azure portal, jak [wyjaśniono w połącz aplikację MongoDB z usługą Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account).

Jeśli `ESHOP_AZURE_COSMOSDB` zmienna globalna jest pusta, co `.env` oznacza, że jest komentowana w pliku, kontener używa domyślnego ciągu połączenia MongoDB. Ten ciąg połączeń wskazuje lokalny kontener MongoDB wdrożony w eShopOnContainers, który został nazwany `nosqldata` i został zdefiniowany w pliku docker-compose, jak pokazano w następującym kodzie .yml:

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

- **Vaughn Vernon. Idealny magazyn agregacji projektowej oparty na domenie?** \
  <https://kalele.io/blog-posts/the-ideal-domain-driven-design-aggregate-store/>

- **Wprowadzenie do usługi Azure Cosmos DB: interfejs API dla usługi MongoDB**  \
  <https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction>

- **Usługa Azure Cosmos DB: tworzenie aplikacji sieci Web interfejsu API MongoDB przy platformie .NET i witrynie Azure portal**  \
  <https://docs.microsoft.com/azure/cosmos-db/create-mongodb-dotnet>

- **Użyj emulatora usługi Azure Cosmos DB do lokalnego programowania i testowania**  \
  <https://docs.microsoft.com/azure/cosmos-db/local-emulator>

- **Łączenie aplikacji MongoDB z usługą Azure Cosmos DB**  \
  <https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account>

- **Obraz platformy Docker emulatora usługi Cosmos DB (kontener systemu Windows)**  \
  <https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator/>

- **Obraz platformy Docker MongoDB (kontener Linux i Windows)**  \
  <https://hub.docker.com/_/mongo/>

- **Korzystanie z usługi MongoChef (Studio 3T) z kontem usługi Azure Cosmos DB: API dla konta MongoDB**  \
  <https://docs.microsoft.com/azure/cosmos-db/mongodb-mongochef>

>[!div class="step-by-step"]
>[Poprzedni](infrastructure-persistence-layer-implemenation-entity-framework-core.md)
>[następny](microservice-application-layer-web-api-design.md)
