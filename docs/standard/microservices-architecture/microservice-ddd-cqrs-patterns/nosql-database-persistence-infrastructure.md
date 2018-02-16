---
title: "Przy użyciu bazy danych NoSQL jako infrastruktury trwałości"
description: "Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Przy użyciu bazy danych NoSQL jako infrastruktury trwałości"
keywords: Docker, Microservices, ASP.NET, Container
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/12/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: a6f3a991529aea6560eb12f1400ba2750795ebff
ms.sourcegitcommit: 08684dd61444c2f072b89b926370f750e456fca1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="using-nosql-databases-as-a-persistence-infrastructure"></a>Przy użyciu bazy danych NoSQL jako infrastruktury trwałości

Korzystając z bazy danych NoSQL dla warstwy danych Twojej infrastruktury, należy zwykle nie należy używać ORM, takich jak Entity Framework Core. Zamiast niej używać interfejsu API dostarczonych przez aparat NoSQL, takie jak bazy danych Azure rozwiązania Cosmos, bazy danych MongoDB, Cassandra, RavenDB, CouchDB lub tabel magazynu Azure.

Jednak podczas korzystania z bazy danych NoSQL, szczególnie zorientowane na dokument bazy danych, takich jak bazy danych Azure rozwiązania Cosmos, CouchDB lub RavenDB, sposób projektowania modelu za pomocą wartości zagregowanych DDD jest częściowo podobnie jak można to zrobić w podstawowej EF w odniesieniu do identyfikacji Łączny katalogów głównych klas jednostek podrzędnych klasy i wartość obiektu. Ale ostatecznie wpłynie wybranych baz danych w projekcie.

Korzystając z bazy danych zorientowane na dokumentu, można zaimplementować agregacji jako pojedynczego dokumentu zserializowane w formacie JSON lub innego formatu. Jednak użycie bazy danych jest przezroczysty z domeny modelu kodu punktu widzenia. Podczas korzystania z bazy danych NoSQL, nadal używasz klas jednostek i klasy głównym agregacji, ale większą elastyczność niż przy użyciu EF Core, ponieważ nie jest relacyjna trwałość.

Różnica polega na tym w sposób utrwalić modelu. Jeśli zaimplementowano modelu domeny oparte na klasach jednostki POCO niezależny od trwałości infrastruktury może prawdopodobnie może przenieść się do infrastruktury różnych trwałości, nawet od relacyjne do NoSQL. Który nie powinien być poznasz. Zawsze są ograniczenia w różnych baz danych przeprowadzi wypychanie możesz ponownie, nie można mieć ten sam model dla relacyjnego lub bazy danych NoSQL. Zmiana modeli trwałości nie jest prosta, ponieważ transakcje i operacji utrwalania będą bardzo różnią się.

Na przykład w bazie danych zorientowane na dokument jest poprawny dla elementu głównego agregacji ma wiele właściwości kolekcji podrzędnych. Relacyjnej bazy danych zapytań wiele właściwości kolekcji podrzędnych jest awful, ponieważ wracając instrukcję SQL wszystkie związek z EF. O tym samym modelu domeny relacyjnych baz danych lub bazy danych NoSQL nie jest proste, a nie należy dążyć. Masz naprawdę projektowania modelu za pomocą zrozumienia sposobu danych będzie można używać w każdej określonej bazy danych.

Korzyści, w przypadku korzystania z bazy danych NoSQL to jednostek więcej nieznormalizowany, dlatego nie należy ustawiać mapowania tabeli. Model domeny może być bardziej elastyczne niż przy użyciu relacyjnej bazy danych.

Podczas projektowania modelu domeny wartościami zagregowanymi, w oparciu przechodzenia do NoSQL i zorientowane na dokument baz danych może być łatwiejsze niż przy użyciu relacyjnej bazy danych, ponieważ agregacje, którą można zaprojektować są podobne do serializacji dokumenty w bazie danych zorientowane na dokument. Następnie można uwzględnić w tych "torbach" wszystkich informacji potrzebnych do tej agregacji.

Na przykład następujący kod JSON jest przykładowa implementacja agregacji kolejności podczas korzystania z bazy danych zorientowane na dokument. Jest on podobny do agregacji kolejności zaimplementowano w przykładowym eShopOnContainers, ale bez użycia rdzeni EF poniżej.

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

## <a name="introduction-to-azure-cosmos-db-and-the-native-cosmos-db-api"></a>Wprowadzenie do bazy danych Azure rozwiązania Cosmos i natywnego interfejsu API DB rozwiązania Cosmos

[Azure DB rozwiązania Cosmos](https://docs.microsoft.com/en-us/azure/cosmos-db/introduction) jest usługą globalnie rozproszoną bazę danych firmy Microsoft dla aplikacji o krytycznym znaczeniu. Udostępnia bazę danych systemu Azure rozwiązania Cosmos [dystrybucji globalne gotowe](https://docs.microsoft.com/en-us/azure/cosmos-db/distribute-data-globally), [elastyczne skalowanie przepływność i magazyn](https://docs.microsoft.com/en-us/azure/cosmos-db/partition-data) na całym świecie, jednocyfrowej milisekundy opóźnienia w 99-ty percentyl [pięć dobrze zdefiniowane poziomy spójności](https://docs.microsoft.com/en-us/azure/cosmos-db/consistency-levels), zagwarantować wysokiej dostępności, wszystkie kopie przez [SLA branży](https://azure.microsoft.com/support/legal/sla/cosmos-db/). Azure DB rozwiązania Cosmos [automatycznie indeksuje danych](http://www.vldb.org/pvldb/vol8/p1668-shukla.pdf) bez konieczności postępowania w przypadku zarządzania schematu i indeksu. Jest wiele modeli i obsługuje dokumentu, klucz wartość, wykres i modeli danych kolumnowym.

![](./media/image19.1.png) Rysunek 9-19. Azure DB rozwiązania Cosmos dystrybucji globalne

Jeśli używasz C\# model implementacji agregacji, które mają być używane przez rozwiązania Cosmos DB interfejsu API Azure, agregacji może być podobne do C\# klasy POCO używane EF podstawowych. Jest to różnica w taki sposób, aby użyć ich z warstwy aplikacji i infrastruktury, zgodnie z poniższym kodem:

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
orderAggregate.AddOrderItem(orderItem2);
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

Widać, że sposób pracy z modelem domeny może być podobny do sposobu używania jej w Twojej warstwy modelu domeny po EF infrastruktury. Do zapewnienia spójności, invariants i sprawdzanie poprawności w agregacji są nadal używać tych samych metod głównego agregacji.

Jednak gdy można utrwalić modelu do bazy danych NoSQL, kod i zmiany interfejsu API znacznie w porównaniu do kodu EF Core lub inny kod powiązany relacyjnych baz danych.

## <a name="implementing-net-code-targeting-mongodb-and-azure-cosmos-db"></a>Wdrażanie kodu platformy .NET przeznaczonych dla bazy danych MongoDB i bazy danych Azure rozwiązania Cosmos

### <a name="using-azure-cosmos-db-from-net-containers"></a>Przy użyciu bazy danych rozwiązania Cosmos Azure z kontenerów .NET

Dostępne bazy danych Azure rozwiązania Cosmos baz danych z systemem w kontenerach, takich jak z dowolnej aplikacji .NET kodu platformy .NET. Na przykład mikrousług Locations.API i Marketing.API w eShopOnContainers są implementowane, można korzystać z bazy danych Azure rozwiązania Cosmos baz danych.

Istnieje jednak ograniczenia w usłudze Azure DB rozwiązania Cosmos z Docker programowanie środowiska punktu widzenia. Nawet wtedy, gdy istnieje lokalnie [Azure rozwiązania Cosmos DB emulatora](https://docs.microsoft.com/en-us/azure/cosmos-db/local-emulator) można uruchomić na maszynie lokalnej (np. komputer), jako późnego 2017 właśnie obsługuje on Windows, Linux nie. 

Istnieje również możliwość uruchomienia tego emulatora Docker, ale tylko kontenery systemu Windows z użyciem not kontenery systemu Linux. Jeśli aplikacja jest wdrożona jako kontenery systemu Linux, ponieważ, obecnie jest początkowej przeszkoda dla środowiska programowania, w tym samym momencie nie można wdrożyć systemu Linux i Windows kontenerów na Docker dla systemu Windows. Albo wszystkie kontenery wdrażany trzeba dla systemu Linux lub dla systemu Windows.  

Rozwiązanie: tworzenie i testowanie wdrożenia idealne i bardziej bezpośrednie jest można wdrażać systemy bazy danych jako kontenery wraz z kontenerów niestandardowych, tak aby środowiska i testowania zawsze są spójne.

### <a name="use-mongodb-api-for-local-devtest-linuxwindows-containers-plus-azure-cosmos-db"></a>Za pomocą interfejsu API bazy danych MongoDB dla kontenery systemu Linux i Windows lokalnych i testowania oraz bazy danych Azure rozwiązania Cosmos

Bazy danych DB rozwiązania cosmos obsługuje API bazy danych MongoDB dla platformy .NET, a także natywny protokół bazy danych MongoDB. Oznacza to, że przy użyciu istniejących sterowników aplikacji napisanych dla bazy danych MongoDB mogą teraz komunikować się z rozwiązania Cosmos bazy danych i użyj bazy danych DB rozwiązania Cosmos zamiast bazy danych MongoDB, jak pokazano w rysunku 9-20.

![](./media/image19.2.png) Rysunek 9-20. Otwieranie bazy danych rozwiązania Cosmos Azure za pomocą interfejsu API bazy danych MongoDB i protokół

Ponieważ jest to bardzo wygodny podejście dowodu koncepcji w środowiskach Docker z kontenerami Linux [MongoDB Docker obrazu](https://hub.docker.com/r/_/mongo/) jest wiele architektury obrazu, który obsługuje kontenery Docker Linux i kontenery Docker systemu Windows.

Jak pokazano w obrazie 9-21 przy użyciu interfejsu API bazy danych MongoDB, eShopOnContainers obsługuje bazy danych MongoDB Linux i Windows kontenery lokalne Środowisko deweloperskie, ale następnie można przenieść na skalowalnych, PaaS w chmurze rozwiązania jako bazy danych rozwiązania Cosmos Azure przez po prostu [zmiana Parametry połączenia bazy danych MongoDB do punktu do bazy danych Azure rozwiązania Cosmos](https://docs.microsoft.com/en-us/azure/cosmos-db/connect-mongodb-account). 

![](./media/image20-bis.png) Rysunek 9-21. Używanie kontenerów bazy danych MongoDB dla deweloperów env lub bazy danych Azure rozwiązania Cosmos w środowisku produkcyjnym eShopOnContainers

Produkcyjnej bazy danych Azure rozwiązania Cosmos będzie działać w chmurze platformy Azure jako PaaS i skalowalne usługi.

Niestandardowe kontenerów .NET Core może działać na hostach Docker lokalne działania projektowe (który jest przy użyciu rozwiązania Docker dla systemu Windows na komputerze z systemem Windows 10) lub można wdrożyć w środowisku produkcyjnym, takich jak Kubernetes Azure AKS lub sieć szkieletowa usług Azure. W tym środowisku drugi czy wdrożyć tylko kontenery niestandardowych .NET Core, ale nie w kontenerze bazy danych MongoDB, ponieważ będą stosowane bazy danych Azure rozwiązania Cosmos w chmurze do obsługi danych w środowisku produkcyjnym.

Wyczyść zaletą korzystania z bazy danych MongoDB interfejsu API jest, że rozwiązania można uruchomić w obu baz danych, bazy danych MongoDB lub bazy danych rozwiązania Cosmos platformy Azure, więc migracje w różnych środowiskach powinno być łatwe. Jednak czasami warto użyć natywnego interfejsu API (która jest natywnego interfejsu API DB rozwiązania Cosmos) aby w pełni korzystać z możliwości aparatu określonej bazy danych.

Aby uzyskać dalsze porównania po prostu przy użyciu bazy danych MongoDB i DB rozwiązania Cosmos w chmurze, zobacz [zalety używania bazy danych Azure rozwiązania Cosmos na tej stronie](https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb-introduction). 


### <a name="analyze-your-approach-for-production-applications-mongodb-api-vs-cosmos-db-api"></a>Analizowanie swoje podejście przez aplikacje produkcyjne: vs API bazy danych MongoDB. Interfejs API rozwiązania cosmos bazy danych

W eShopOnContainers firma Microsoft korzysta z interfejsu API bazy danych MongoDB powodu naszych priorytet zasadniczo do środowiska i testowania spójne korzystanie z bazy danych NoSQL, który może również współpracować z bazy danych Azure rozwiązania Cosmos.

Jednak jeśli planowanie na potrzeby bazy danych MongoDB API uzyskiwać dostęp do bazy danych rozwiązania Cosmos Azure na platformie Azure dla aplikacji produkcyjnych, które powinny analizować różnic w wydajności i możliwości, korzystając z interfejsu API bazy danych MongoDB dostępu do baz danych Azure DB rozwiązania Cosmos w porównaniu do za pomocą natywnego Interfejs API Azure rozwiązania Cosmos bazy danych. Jeśli jest on podobny można użyć interfejsu API bazy danych MongoDB i skorzystać z zalet obsługi dwóch baz danych NoSQL, w tym samym czasie. 

Można także użyć klastrów bazy danych MongoDB jako produkcyjną bazę danych w chmurze platformy Azure, z [usługę Azure bazy danych MongoDB](https://www.mongodb.com/scale/mongodb-azure-service). Ale nie jest usługą PaaS obsługiwane przez firmę Microsoft. W takim przypadku Azure jest po prostu tego rozwiązania hostingu pochodzących z bazy danych MongoDB.

Zasadniczo to po prostu zastrzeżenie, podając nie należy zawsze używać interfejsu API bazy danych MongoDB względem bazy danych rozwiązania Cosmos platformy Azure, jak robiliśmy w eShopOnContainers powodu wygodny wybór dla systemu Linux kontenerów. Decyzja powinny być oparte na określonych potrzeb i testy, które należy wykonać w przypadku aplikacji produkcyjnej.  

### <a name="the-code-using-mongodb-api-in-net-core-applications"></a>Kod: przy użyciu interfejsu API bazy danych MongoDB w aplikacjach .NET Core

Interfejs API bazy danych MongoDB dla platformy .NET jest oparta na pakietów NuGet, których konieczne jest dodanie do projektów, takich jak Locations.API wyświetlany w rysunek 9-22.

![](./media/image21-bis.png) Rysunek 9-22. Odwołań w projekcie platformy .NET Core pakietów NuGet interfejsu API bazy danych MongoDB

Teraz należy zbadać kod w następujących sekcjach.

#### <a name="a-model-used-by-mongodb-api"></a>Model używany przez interfejs API bazy danych MongoDB

Najpierw należy zdefiniować modelu, w którym będą przechowywane dane pochodzące z bazy danych w obszarze pamięci aplikacji. Oto przykład używane w przypadku lokalizacji w eShopOnContainers modelu.

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

Można zauważyć, że istnieje kilka atrybutów i typy pochodzące z pakietami NuGet bazy danych MongoDB.

Bazy danych NoSQL są zazwyczaj bardzo dobrze nadają się do pracy z danymi hierarchicznymi nierelacyjnych. W tym przykładzie używamy expecially typy bazy danych MongoDB przewidzieć lokalizacje geograficzne, takie jak `GeoJson2DGeographicCoordinates`.

#### <a name="retrieve-the-database-and-the-collection"></a>Pobieranie bazy danych i kolekcji

W eShopOnContainers został utworzony w kontekście niestandardowej bazy danych, gdzie wdrożymy kod, aby pobrać bazy danych i MongoCollections, zgodnie z poniższym kodem.

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

W kodu C#, takimi jak kontrolery interfejsu API sieci Web lub niestandardowe repozytoria implementacji można napisać kod podobny do następującego podczas wykonywania zapytania za pomocą interfejsu API bazy danych MongoDB. Należy pamiętać, że `_context` obiekt jest wystąpieniem poprzedniego `LocationsContext` klasy.

```csharp
public async Task<Locations> GetAsync(int locationId)
{
    var filter = Builders<Locations>.Filter.Eq("LocationId", locationId);
    return await _context.Locations
                            .Find(filter)
                            .FirstOrDefaultAsync();
}
```

#### <a name="use-an-env-var-in-the-docker-composeoverrideyml-file-for-the-mongodb-connection-string"></a>Użyj env-var w pliku docker compose.override.yml ciągu połączenia bazy danych MongoDB

Podczas tworzenia obiektu MongoClient, musi on podstawowych parametr, który jest dokładnie `ConnectionString` parametr wskazujący właściwej bazy danych. W przypadku eShopOnContainers ciąg połączenia może wskazywać kontenerze MongoDB Docker lokalnego lub w bazie danych bazy danych Azure rozwiązania Cosmos "production".  Ten ciąg połączenia pochodzi z określonych w zmiennych środowiskowych `docker-compose.override.yml` pliki używane podczas wdrażania z docker-compose lub Visual Studio, tak jak w poniższym kodzie yml.

```yml
# docker-compose.override.yml
version: '3'
services:
  # Other services
  locations.api:
    environment:
      # Other settings
      - ConnectionString=${ESHOP_AZURE_COSMOSDB:-mongodb://nosql.data}

```

`ConnectionString` Zmiennej środowiskowej zostanie rozwiązany w ten sposób: Jeśli `ESHOP_AZURE_COSMOSDB` — zmienna globalna jest zdefiniowany w `.env` plik z parametrami połączenia bazy danych Azure rozwiązania Cosmos, użyje on dostęp do bazy danych Azure DB rozwiązania Cosmos w chmurze. 

Poniższy kod przedstawia `.env` plików ze zmienną środowiskową globalne ciągu połączenia bazy danych Azure rozwiązania Cosmos w eShopOnContainers:

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

Należy Usuń komentarz linii ESHOP_AZURE_COSMOSDB i aktualizacji za pomocą parametrów połączenia bazy danych Azure rozwiązania Cosmos uzyskane z portalu Azure, jak wyjaśniono w [połączyć aplikację bazy danych MongoDB do bazy danych Azure rozwiązania Cosmos](https://docs.microsoft.com/en-us/azure/cosmos-db/connect-mongodb-account).

Jeśli `ESHOP_AZURE_COSMOSDB` — zmienna globalna jest pusta, co oznacza, że jej jest oznaczone jako limit w `.env` pliku, a następnie kontenera korzysta z domyślnego ciągu połączenia bazy danych MongoDB wskazanie w kontenerze lokalnej bazy danych MongoDB wdrożone w eShopOnContainers o nazwie `nosql.data`, jak pokazano w poniższym kodzie .yml. 

#### <a name="additional-resources"></a>Dodatkowe zasoby

-   **Modelowanie dokumentów danych dla bazy danych NoSQL**
    [*https://docs.microsoft.com/en-us/azure/cosmos-db/modeling-data*](https://docs.microsoft.com/en-us/azure/cosmos-db/modeling-data)

-   **Vaughn Vernon. Nadaje się doskonale oparte na domenie projektu agregacji sklepu? ** 
     [ *https://vaughnvernon.co/?p=942*](https://vaughnvernon.co/?p=942)

-   **Wprowadzenie do platformy Azure rozwiązania Cosmos DB: interfejs API dla bazy danych MongoDB** 
    [*https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb-introduction*](https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb-introduction)

-   **Azure rozwiązania Cosmos bazy danych: Tworzenie aplikacji sieci web interfejsu API bazy danych MongoDB z usług .NET i portalu Azure** 
    [* https://docs.microsoft.com/en-us/azure/cosmos-db/create-mongodb-dotnet *](https://docs.microsoft.com/en-us/azure/cosmos-db/create-mongodb-dotnet )

-   **Użyj emulatora usługi Azure rozwiązania Cosmos bazy danych dla lokalnych projektowania i testowania** 
    [*https://docs.microsoft.com/en-us/azure/cosmos-db/local-emulator*](https://docs.microsoft.com/en-us/azure/cosmos-db/local-emulator)

-   **Łączenie aplikacji bazy danych MongoDB, do bazy danych Azure rozwiązania Cosmos** 
    [*https://docs.microsoft.com/en-us/azure/cosmos-db/connect-mongodb-account*](https://docs.microsoft.com/en-us/azure/cosmos-db/connect-mongodb-account)

-   **Obraz Docker emulatora DB rozwiązania Cosmos (kontenera systemu Windows)** 
    [*https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator/*](https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator/)

-   **Obraz Docker bazy danych MongoDB (Linux i Windows kontenera)** 
    [*https://hub.docker.com/r/_/mongo/*](https://hub.docker.com/r/_/mongo/)

-   **Użyj MongoChef (3T w Studio) z bazy danych Azure rozwiązania Cosmos: interfejsu API dla konta bazy danych MongoDB** 
    [*https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb-mongochef*](https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb-mongochef)


>[!div class="step-by-step"]
[Previous] (infrastructure-persistence-layer-implemenation-entity-framework-core.md) [Next] (microservice-application-layer-web-api-design.md)
