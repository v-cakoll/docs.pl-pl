---
title: Korzystanie z baz danych NoSQL jako infrastruktury trwałości
description: Architektura mikrousług platformy .NET dla aplikacji platformy .NET w kontenerze | Informacje ogólne na temat używania baz danych NoSql, a w szczególności Azure Cosmos DB jako opcji wdrożenia utrwalania.
ms.date: 10/08/2018
ms.openlocfilehash: 44fc2fa01e2d19efed7314f421a682c0a635a9f6
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73737405"
---
# <a name="use-nosql-databases-as-a-persistence-infrastructure"></a>Korzystanie z baz danych NoSQL jako infrastruktury trwałości

W przypadku korzystania z baz danych NoSQL dla warstwy dane infrastruktury zazwyczaj nie używasz ORM, takiego jak Entity Framework Core. Zamiast tego należy użyć interfejsu API dostarczonego przez aparat NoSQL, takiego jak Azure Cosmos DB, MongoDB, Cassandra, RavenDB, CouchDB lub tabel usługi Azure Storage.

Jednak w przypadku korzystania z bazy danych NoSQL, w szczególności bazy danych zorientowanej na dokumenty, takiej jak Azure Cosmos DB, CouchDB lub RavenDB, sposób projektowania modelu z użyciem wartości DDD jest częściowo podobny do tego, jak można to zrobić w EF Core, w odniesieniu do identyfikacji Agregowanie elementów głównych, klas jednostek podrzędnych i klas obiektów wartości. Ostatecznie wybór bazy danych będzie miał wpływ na projekt.

W przypadku korzystania z bazy danych zorientowanej na dokumenty należy zaimplementować agregację jako pojedynczy dokument, zserializowaną w formacie JSON lub inny format. Jednak użycie bazy danych jest niewidoczne z punktu widzenia kodu modelu domeny. W przypadku korzystania z bazy danych NoSQL nadal używasz klas jednostek i agregacji klas głównych, ale z większą elastycznością niż w przypadku używania EF Core, ponieważ trwałość nie jest relacyjna.

Różnica polega na tym, jak utrzymywać ten model. Jeśli model domeny został zaimplementowany na podstawie klas jednostek POCO, niezależny od do trwałości infrastruktury, może to wyglądać podobnie do innej infrastruktury trwałości, nawet od relacyjnej do NoSQL. Jednak nie powinno to być cel. Istnieją zawsze ograniczenia i wady dotyczące różnych technologii baz danych, dzięki czemu nie będzie można korzystać z tego samego modelu dla baz danych relacyjnych lub NoSQL. Zmiana modeli trwałości nie jest zadaniem prostym, ponieważ transakcje i operacje trwałości będą bardzo różne.

Na przykład w bazie danych zorientowanej na dokument nie jest możliwe, aby zagregowany element główny miał wiele właściwości kolekcji podrzędnych. W relacyjnej bazie danych zapytania z wieloma podrzędnymi właściwościami kolekcji nie są łatwo zoptymalizowane, ponieważ z powrotem uzyskuje się instrukcję UNION ALL języka SQL od EF. Posiadanie tego samego modelu domeny dla relacyjnych baz danych lub baz danych NoSQL nie jest proste i nie należy go podejmować. Naprawdę musisz zaprojektować model, aby zrozumieć, w jaki sposób dane będą używane w każdej konkretnej bazie danych.

Zaletą korzystania z baz danych NoSQL jest to, że jednostki są bardziej znormalizowane, dlatego nie należy ustawiać mapowania tabeli. Model domeny może być bardziej elastyczny niż w przypadku korzystania z relacyjnej bazy danych.

Podczas projektowania modelu domeny opartego na agregacjach, przeniesienie do NoSQL i baz danych zorientowane na dokumenty może być jeszcze łatwiejsze niż używanie relacyjnej bazy danych, ponieważ zagregowane wartości są podobne do serializowanych dokumentów w bazie danych zorientowanej na dokument. Następnie można dołączyć do tych "toreb" wszystkie informacje, które mogą być potrzebne dla tego agregacji.

Na przykład poniższy kod JSON to Przykładowa implementacja agregacji zamówienia przy użyciu bazy danych zorientowanej na dokument. Jest to podobne do kolejności agregowania wdrożonej w przykładzie eShopOnContainers, ale bez użycia EF Core poniżej.

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

## <a name="introduction-to-azure-cosmos-db-and-the-native-cosmos-db-api"></a>Wprowadzenie do Azure Cosmos DB i natywnego interfejsu API Cosmos DB

[Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction) to usługa dystrybuowana globalnie bazy danych firmy Microsoft dla aplikacji o znaczeniu strategicznym. Azure Cosmos DB zapewnia [globalną dystrybucję](https://docs.microsoft.com/azure/cosmos-db/distribute-data-globally), [elastyczne skalowanie przepływności i magazynu](https://docs.microsoft.com/azure/cosmos-db/partition-data) na całym świecie, opóźnienia o pojedynczej liczbie milisekund w 99 percentylu, [pięć dobrze zdefiniowanych poziomów spójności](https://docs.microsoft.com/azure/cosmos-db/consistency-levels)oraz gwarantowaną wysoką dostępność, a wszystko to dzięki [wiodącym w branży umowy SLA](https://azure.microsoft.com/support/legal/sla/cosmos-db/). Azure Cosmos DB [automatycznie indeksuje dane](https://www.vldb.org/pvldb/vol8/p1668-shukla.pdf) bez konieczności postępowania z zarządzaniem schematami i indeksami. Jest to wiele modeli i obsługuje modele danych Document, key-value, Graph i kolumnowy.

![Diagram przedstawiający dystrybucję globalną Azure Cosmos DB.](./media/nosql-database-persistence-infrastructure/azure-cosmos-db-global-distribution.png)

**Rysunek 7-19**. Azure Cosmos DB dystrybucji globalnej

W przypadku używania modelu języka C\# do zaimplementowania agregacji, która ma być używana przez interfejs API Azure Cosmos DB, agregacja może być podobna do klas POCO języka\# C używanych z EF Core. Różnica polega na sposobie korzystania z nich z warstw aplikacji i infrastruktury, jak w poniższym kodzie:

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

Możesz zobaczyć, że sposób pracy z modelem domeny może być podobny do sposobu korzystania z niego w warstwie modelu domeny, gdy infrastruktura jest Dr. Nadal używasz tych samych agregacji metod głównych w celu zapewnienia spójności, nieodmian i walidacji w ramach agregacji.

Jednak w przypadku utrwalania modelu w bazie danych NoSQL zmiana kodu i interfejsu API znacznie porównana z kodem EF Core lub innym kodem związanym z relacyjnymi bazami danych.

## <a name="implement-net-code-targeting-mongodb-and-azure-cosmos-db"></a>Implementowanie kodu platformy .NET dla MongoDB i Azure Cosmos DB

### <a name="use-azure-cosmos-db-from-net-containers"></a>Używanie Azure Cosmos DB z kontenerów platformy .NET

Dostęp do Azure Cosmos DB baz danych można uzyskać z kodu platformy .NET działającego w kontenerach, podobnie jak w przypadku dowolnej innej aplikacji platformy .NET. Na przykład w programie eShopOnContainers są implementowane mikrousługi lokalizacji. API i marketingu. API, dzięki czemu mogą korzystać z Azure Cosmos DB baz danych.

Istnieje jednak ograniczenie Azure Cosmos DB z punktu widzenia środowiska projektowania platformy Docker. Nawet wtedy, gdy [Azure Cosmos DB emulatora](https://docs.microsoft.com/azure/cosmos-db/local-emulator) lokalnego można uruchomić na lokalnym komputerze deweloperskim (na przykład na komputerze), od momentu do późnego 2017, tylko system Windows, a nie Linux.

Istnieje również możliwość uruchomienia tego emulatora na platformie Docker, ale tylko w kontenerach systemu Windows, a nie w przypadku kontenerów z systemem Linux. Jest to wstępna niepełnosprawność środowiska programistycznego, jeśli aplikacja jest wdrażana jako kontenery systemu Linux, ponieważ obecnie nie można wdrażać kontenerów systemów Linux i Windows na Docker for Windows w tym samym czasie. Wszystkie wdrażane kontenery muszą być przeznaczone dla systemu Linux lub Windows.

Idealnym i bardziej prostym wdrożeniem rozwiązania deweloperskiego/testowego jest możliwość wdrażania systemów baz danych jako kontenerów wraz z niestandardowymi kontenerami, dzięki czemu środowiska deweloperskie/testowe są zawsze spójne.

### <a name="use-mongodb-api-for-local-devtest-linuxwindows-containers-plus-azure-cosmos-db"></a>Korzystanie z interfejsu API MongoDB na potrzeby lokalnego tworzenia i testowania kontenerów systemu Linux/Windows oraz Azure Cosmos DB

Bazy danych Cosmos DB obsługują interfejs API MongoDB dla platformy .NET oraz natywny protokół MongoDB. Oznacza to, że korzystając z istniejących sterowników, aplikacja zapisywana dla MongoDB może teraz komunikować się z Cosmos DB i używać Cosmos DB baz danych zamiast baz danych MongoDB, jak pokazano na rysunku 7-20.

![Diagram przedstawiający, że Cosmos DB obsługuje protokoły sieciowe .NET i MongoDB.](./media/nosql-database-persistence-infrastructure/mongodb-api-wire-protocol.png)

**Rysunek 7-20**. Używanie interfejsu API MongoDB i protokołu do uzyskiwania dostępu Azure Cosmos DB

Jest to bardzo wygodne podejście do weryfikacji koncepcji w środowiskach platformy Docker z kontenerami systemu Linux, ponieważ [obraz platformy](https://hub.docker.com/r/_/mongo/) Docker MongoDB jest obrazem wielodostępnym, który obsługuje kontenery platformy Docker Linux i kontenery platformy Docker.

Jak pokazano na poniższej ilustracji, za pomocą interfejsu API MongoDB, eShopOnContainers obsługuje kontenery systemu Linux i Windows dla lokalnego środowiska programistycznego, ale można przenieść do skalowalnego rozwiązania w chmurze PaaS jako Azure Cosmos DB przez [zmianę parametrów połączenia MongoDB w taki sposób, aby wskazywały Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account).

![Diagram przedstawiający, że mikrousługa lokalizacji w eShopOnContainers może używać Cosmos DB lub Mongo DB.](./media/nosql-database-persistence-infrastructure/eshoponcontainers-mongodb-containers.png)

**Rysunek 7-21**. eShopOnContainers przy użyciu kontenerów MongoDB do celów deweloperskich lub Azure Cosmos DB produkcyjnych

Azure Cosmos DB produkcyjne będzie działać w chmurze platformy Azure jako usługa PaaS i skalowalna.

Niestandardowe kontenery programu .NET Core można uruchamiać na lokalnym hoście platformy Docker (używanym Docker for Windows na komputerze z systemem Windows 10) lub wdrożyć w środowisku produkcyjnym, takim jak Kubernetes na platformie Azure AKS lub platformie Azure Service Fabric. W tym drugim środowisku wdrożono tylko kontenery niestandardowe platformy .NET Core, ale nie kontener MongoDB, ponieważ do obsługi danych w środowisku produkcyjnym jest używany Azure Cosmos DB w chmurze.

Oczywistą zaletą korzystania z interfejsu API MongoDB jest to, że rozwiązanie może działać zarówno w aparatach baz danych, MongoDB, jak i Azure Cosmos DB, dzięki czemu migracja do różnych środowisk powinna być łatwa. Jednak czasami jest wartościowa użycie natywnego interfejsu API (jest to natywny interfejs API Cosmos DB) w celu pełnego wykorzystania możliwości określonego aparatu bazy danych.

Aby uzyskać dalsze porównanie między zwykłym użyciem MongoDB a Cosmos DB w chmurze, zobacz [zalety korzystania z Azure Cosmos DB na tej stronie](https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction).

### <a name="analyze-your-approach-for-production-applications-mongodb-api-vs-cosmos-db-api"></a>Analizowanie podejścia do aplikacji produkcyjnych: MongoDB API a interfejs API Cosmos DB

W eShopOnContainers korzystamy z interfejsu API MongoDB, ponieważ naszym priorytetem było podstawowe środowisko deweloperskie/testowe przy użyciu bazy danych NoSQL, która może również współejść z Azure Cosmos DB.

Jeśli jednak planujesz używać interfejsu API MongoDB do uzyskiwania dostępu do Azure Cosmos DB na platformie Azure dla aplikacji produkcyjnych, należy przeanalizować różnice w zakresie możliwości i wydajności podczas korzystania z interfejsu API MongoDB w celu uzyskania dostępu do Azure Cosmos DB baz danych w porównaniu z użyciem natywnego Interfejs API Azure Cosmos DB. Jeśli jest podobna, można użyć interfejsu API MongoDB i uzyskać korzyści z obsługi dwóch aparatów bazy danych NoSQL w tym samym czasie.

Klastry MongoDB można również używać jako produkcyjnej bazy danych w chmurze platformy Azure, za pomocą [usługi MongoDB platformy Azure](https://www.mongodb.com/scale/mongodb-azure-service). Ale nie jest to usługa PaaS świadczona przez firmę Microsoft. W takim przypadku platforma Azure obsługuje tylko to rozwiązanie pochodzące z MongoDB.

Zasadniczo jest to tylko oświadczenie stwierdzające, że nie należy zawsze używać interfejsu API MongoDB w odniesieniu do Azure Cosmos DB, tak jak w eShopOnContainers, ponieważ było to wygodne rozwiązanie dla kontenerów systemu Linux. Decyzja powinna być oparta na określonych wymaganiach i testach, które należy wykonać w przypadku aplikacji produkcyjnej.

### <a name="the-code-use-mongodb-api-in-net-core-applications"></a>Kod: Użyj interfejsu API MongoDB w aplikacjach .NET Core

Interfejs API MongoDB dla platformy .NET jest oparty na pakietach NuGet, które należy dodać do projektów, takich jak w projekcie Locations. API pokazane na poniższej ilustracji.

![Zrzut ekranu zależności w pakietach NuGet MongoDB.](./media/nosql-database-persistence-infrastructure/mongodb-api-nuget-packages.png)

**Rysunek 7-22**. Pakiety NuGet interfejsu API MongoDB w projekcie .NET Core

Zbadamy kod w poniższych sekcjach.

#### <a name="a-model-used-by-mongodb-api"></a>Model używany przez interfejs API MongoDB

Najpierw należy zdefiniować model, który będzie przechowywać dane pochodzące z bazy danych w przestrzeni pamięci aplikacji. Poniżej przedstawiono przykładowy model używany do lokalizacji w eShopOnContainers.

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

Można zobaczyć kilka atrybutów i typów pochodzących z pakietów NuGet MongoDB.

Bazy danych NoSQL są zwykle bardzo dobrze dopasowane do pracy z nierelacyjnymi danymi hierarchicznymi. W tym przykładzie używamy typów MongoDB, szczególnie dla lokalizacji geograficznych, takich jak `GeoJson2DGeographicCoordinates`.

#### <a name="retrieve-the-database-and-the-collection"></a>Pobieranie bazy danych i kolekcji

W eShopOnContainers został utworzony niestandardowy kontekst bazy danych, w którym implementujemy kod w celu pobrania bazy danych i MongoCollections, jak w poniższym kodzie.

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

W C# kodzie, takim jak kontrolery interfejsu API sieci Web lub implementacji niestandardowych repozytoriów, można napisać podobny kod do poniższego zapytania przy użyciu interfejsu API MongoDB. Należy zauważyć, że obiekt `_context` jest wystąpieniem poprzedniej klasy `LocationsContext`.

```csharp
public async Task<Locations> GetAsync(int locationId)
{
    var filter = Builders<Locations>.Filter.Eq("LocationId", locationId);
    return await _context.Locations
                            .Find(filter)
                            .FirstOrDefaultAsync();
}
```

#### <a name="use-an-env-var-in-the-docker-composeoverrideyml-file-for-the-mongodb-connection-string"></a>Użyj funkcji ENV-var w pliku Docker-Compose. override. yml dla parametrów połączenia MongoDB

Podczas tworzenia obiektu MongoClient musi on mieć podstawowy parametr, który jest precyzyjnym parametrem `ConnectionString` wskazującym odpowiednią bazę danych. W przypadku eShopOnContainers parametry połączenia mogą wskazywać lokalny kontener platformy Docker MongoDB lub do bazy danych Azure Cosmos DB produkcyjnych.  Te parametry połączenia pochodzą ze zmiennych środowiskowych zdefiniowanych w plikach `docker-compose.override.yml` używanych podczas wdrażania przy użyciu platformy Docker-redagowanie lub Visual Studio, jak w poniższym kodzie YML.

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

Zmienna środowiskowa `ConnectionString` jest rozwiązywana w ten sposób: Jeśli `ESHOP_AZURE_COSMOSDB` zmienna globalna jest zdefiniowana w pliku `.env` z Azure Cosmos DB parametrów połączenia, będzie używać jej do uzyskiwania dostępu do bazy danych Azure Cosmos DB w chmurze. Jeśli nie jest on zdefiniowany, zajmie `mongodb://nosql.data` wartość i użyje kontenera Development MongoDB.

Poniższy kod ilustruje `.env` plik ze zmienną środowiskową globalną ciąg połączenia Azure Cosmos DB, zgodnie z zaimplementowaną w eShopOnContainers:

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

Należy usunąć komentarz z wiersza ESHOP_AZURE_COSMOSDB i zaktualizować go przy użyciu parametrów połączenia Azure Cosmos DB uzyskanych z Azure Portal, jak wyjaśniono w temacie [łączenie aplikacji MongoDB z Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account).

Jeśli `ESHOP_AZURE_COSMOSDB` zmienna globalna jest pusta, co oznacza, że jest ona oznaczona w pliku `.env`, kontener używa domyślnych parametrów połączenia MongoDB wskazujących na lokalny kontener MongoDB wdrożony w eShopOnContainers o nazwie `nosql.data` i został zdefiniowany w pliku Docker-Zredaguj, jak pokazano w poniższym kodzie. yml.

``` yml
# docker-compose.yml
version: '3.4'
services:
  # ...Other services...
  nosql.data:
    image: mongo
```

#### <a name="additional-resources"></a>Dodatkowe zasoby

- **Dane dokumentu modelowania dla baz danych NoSQL** \
  <https://docs.microsoft.com/azure/cosmos-db/modeling-data>

- **Vaughn Vernon. Idealny magazyn agregacji projektu opartego na domenie?** \
  <https://kalele.io/blog-posts/the-ideal-domain-driven-design-aggregate-store/>

- **Wprowadzenie do Azure Cosmos DB: interfejs API dla MongoDB**  \
  <https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction>

- **Azure Cosmos DB: Tworzenie aplikacji internetowej interfejsu API MongoDB za pomocą platformy .NET i Azure Portal**  \
  <https://docs.microsoft.com/azure/cosmos-db/create-mongodb-dotnet>

- **Użyj emulatora Azure Cosmos DB na potrzeby lokalnego tworzenia i testowania**  \
  <https://docs.microsoft.com/azure/cosmos-db/local-emulator>

- **Połącz aplikację MongoDB z Azure Cosmos DB**  \
  <https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account>

- **Obraz Cosmos DB Docker emulatora (kontener systemu Windows)**   \
  <https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator/>

- **Obraz platformy Docker MongoDB (kontener Linux i Windows)**   \
  <https://hub.docker.com/_/mongo/>

- **Użyj korzystanie programu mongochef (Studio 3T) z Azure Cosmos DB: interfejs API dla konta MongoDB**  \
  <https://docs.microsoft.com/azure/cosmos-db/mongodb-mongochef>

>[!div class="step-by-step"]
>[Poprzedni](infrastructure-persistence-layer-implemenation-entity-framework-core.md)
>[Następny](microservice-application-layer-web-api-design.md)
