---
title: Przy użyciu bazy danych NoSQL jako infrastruktury trwałości
description: Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Przy użyciu bazy danych NoSQL jako infrastruktury trwałości
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/12/2017
ms.openlocfilehash: 2618e8c068ec538f5bfed2f8243d1c594478fcb0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="using-nosql-databases-as-a-persistence-infrastructure"></a><span data-ttu-id="2be8a-103">Przy użyciu bazy danych NoSQL jako infrastruktury trwałości</span><span class="sxs-lookup"><span data-stu-id="2be8a-103">Using NoSQL databases as a persistence infrastructure</span></span>

<span data-ttu-id="2be8a-104">Korzystając z bazy danych NoSQL dla warstwy danych Twojej infrastruktury, należy zwykle nie należy używać ORM, takich jak Entity Framework Core.</span><span class="sxs-lookup"><span data-stu-id="2be8a-104">When you use NoSQL databases for your infrastructure data tier, you typically do not use an ORM like Entity Framework Core.</span></span> <span data-ttu-id="2be8a-105">Zamiast niej używać interfejsu API dostarczonych przez aparat NoSQL, takie jak bazy danych Azure rozwiązania Cosmos, bazy danych MongoDB, Cassandra, RavenDB, CouchDB lub tabel magazynu Azure.</span><span class="sxs-lookup"><span data-stu-id="2be8a-105">Instead you use the API provided by the NoSQL engine, such as Azure Cosmos DB, MongoDB, Cassandra, RavenDB, CouchDB, or Azure Storage Tables.</span></span>

<span data-ttu-id="2be8a-106">Jednak podczas korzystania z bazy danych NoSQL, szczególnie zorientowane na dokument bazy danych, takich jak bazy danych Azure rozwiązania Cosmos, CouchDB lub RavenDB, sposób projektowania modelu za pomocą wartości zagregowanych DDD jest częściowo podobnie jak można to zrobić w podstawowej EF w odniesieniu do identyfikacji Łączny katalogów głównych klas jednostek podrzędnych klasy i wartość obiektu.</span><span class="sxs-lookup"><span data-stu-id="2be8a-106">However, when you use a NoSQL database, especially a document-oriented database like Azure Cosmos DB, CouchDB, or RavenDB, the way you design your model with DDD aggregates is partially similar to how you can do it in EF Core, in regards to the identification of aggregate roots, child entity classes, and value object classes.</span></span> <span data-ttu-id="2be8a-107">Ale ostatecznie wpłynie wybranych baz danych w projekcie.</span><span class="sxs-lookup"><span data-stu-id="2be8a-107">But, ultimately, the database selection will impact in your design.</span></span>

<span data-ttu-id="2be8a-108">Korzystając z bazy danych zorientowane na dokumentu, można zaimplementować agregacji jako pojedynczego dokumentu zserializowane w formacie JSON lub innego formatu.</span><span class="sxs-lookup"><span data-stu-id="2be8a-108">When you use a document-oriented database, you implement an aggregate as a single document, serialized in JSON or another format.</span></span> <span data-ttu-id="2be8a-109">Jednak użycie bazy danych jest przezroczysty z domeny modelu kodu punktu widzenia.</span><span class="sxs-lookup"><span data-stu-id="2be8a-109">However, the use of the database is transparent from a domain model code point of view.</span></span> <span data-ttu-id="2be8a-110">Podczas korzystania z bazy danych NoSQL, nadal używasz klas jednostek i klasy głównym agregacji, ale większą elastyczność niż przy użyciu EF Core, ponieważ nie jest relacyjna trwałość.</span><span class="sxs-lookup"><span data-stu-id="2be8a-110">When using a NoSQL database, you still are using entity classes and aggregate root classes, but with more flexibility than when using EF Core because the persistence is not relational.</span></span>

<span data-ttu-id="2be8a-111">Różnica polega na tym w sposób utrwalić modelu.</span><span class="sxs-lookup"><span data-stu-id="2be8a-111">The difference is in how you persist that model.</span></span> <span data-ttu-id="2be8a-112">Jeśli zaimplementowano modelu domeny oparte na klasach jednostki POCO niezależny od trwałości infrastruktury może prawdopodobnie może przenieść się do infrastruktury różnych trwałości, nawet od relacyjne do NoSQL.</span><span class="sxs-lookup"><span data-stu-id="2be8a-112">If you implemented your domain model based on POCO entity classes, agnostic to the infrastructure persistence, it might look like you could move to a different persistence infrastructure, even from relational to NoSQL.</span></span> <span data-ttu-id="2be8a-113">Który nie powinien być poznasz.</span><span class="sxs-lookup"><span data-stu-id="2be8a-113">However, that should not be your goal.</span></span> <span data-ttu-id="2be8a-114">Zawsze są ograniczenia w różnych baz danych przeprowadzi wypychanie możesz ponownie, nie można mieć ten sam model dla relacyjnego lub bazy danych NoSQL.</span><span class="sxs-lookup"><span data-stu-id="2be8a-114">There are always constraints in the different databases will push you back, so you will not be able to have the same model for relational or NoSQL databases.</span></span> <span data-ttu-id="2be8a-115">Zmiana modeli trwałości nie jest prosta, ponieważ transakcje i operacji utrwalania będą bardzo różnią się.</span><span class="sxs-lookup"><span data-stu-id="2be8a-115">Changing persistence models would not be trivial, because transactions and persistence operations will be very different.</span></span>

<span data-ttu-id="2be8a-116">Na przykład w bazie danych zorientowane na dokument jest poprawny dla elementu głównego agregacji ma wiele właściwości kolekcji podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="2be8a-116">For example, in a document-oriented database, it is okay for an aggregate root to have multiple child collection properties.</span></span> <span data-ttu-id="2be8a-117">Relacyjnej bazy danych zapytań wiele właściwości kolekcji podrzędnych jest awful, ponieważ wracając instrukcję SQL wszystkie związek z EF.</span><span class="sxs-lookup"><span data-stu-id="2be8a-117">In a relational database, querying multiple child collection properties is awful, because you get a UNION ALL SQL statement back from EF.</span></span> <span data-ttu-id="2be8a-118">O tym samym modelu domeny relacyjnych baz danych lub bazy danych NoSQL nie jest proste, a nie należy dążyć.</span><span class="sxs-lookup"><span data-stu-id="2be8a-118">Having the same domain model for relational databases or NoSQL databases is not simple, and you should not try it.</span></span> <span data-ttu-id="2be8a-119">Masz naprawdę projektowania modelu za pomocą zrozumienia sposobu danych będzie można używać w każdej określonej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="2be8a-119">You really have to design your model with an understanding of how the data is going to be used in each particular database.</span></span>

<span data-ttu-id="2be8a-120">Korzyści, w przypadku korzystania z bazy danych NoSQL to jednostek więcej nieznormalizowany, dlatego nie należy ustawiać mapowania tabeli.</span><span class="sxs-lookup"><span data-stu-id="2be8a-120">A benefit when using NoSQL databases is that the entities are more denormalized, so you do not set a table mapping.</span></span> <span data-ttu-id="2be8a-121">Model domeny może być bardziej elastyczne niż przy użyciu relacyjnej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="2be8a-121">Your domain model can be more flexible than when using a relational database.</span></span>

<span data-ttu-id="2be8a-122">Podczas projektowania modelu domeny wartościami zagregowanymi, w oparciu przechodzenia do NoSQL i zorientowane na dokument baz danych może być łatwiejsze niż przy użyciu relacyjnej bazy danych, ponieważ agregacje, którą można zaprojektować są podobne do serializacji dokumenty w bazie danych zorientowane na dokument.</span><span class="sxs-lookup"><span data-stu-id="2be8a-122">When you design your domain model based on aggregates, moving to NoSQL and document-oriented databases might be even easier than using a relational database, because the aggregates you design are similar to serialized documents in a document-oriented database.</span></span> <span data-ttu-id="2be8a-123">Następnie można uwzględnić w tych "torbach" wszystkich informacji potrzebnych do tej agregacji.</span><span class="sxs-lookup"><span data-stu-id="2be8a-123">Then you can include in those “bags” all the information you might need for that aggregate.</span></span>

<span data-ttu-id="2be8a-124">Na przykład następujący kod JSON jest przykładowa implementacja agregacji kolejności podczas korzystania z bazy danych zorientowane na dokument.</span><span class="sxs-lookup"><span data-stu-id="2be8a-124">For instance, the following JSON code is a sample implementation of an order aggregate when using a document-oriented database.</span></span> <span data-ttu-id="2be8a-125">Jest on podobny do agregacji kolejności zaimplementowano w przykładowym eShopOnContainers, ale bez użycia rdzeni EF poniżej.</span><span class="sxs-lookup"><span data-stu-id="2be8a-125">It is similar to the order aggregate we implemented in the eShopOnContainers sample, but without using EF Core underneath.</span></span>

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

## <a name="introduction-to-azure-cosmos-db-and-the-native-cosmos-db-api"></a><span data-ttu-id="2be8a-126">Wprowadzenie do bazy danych Azure rozwiązania Cosmos i natywnego interfejsu API DB rozwiązania Cosmos</span><span class="sxs-lookup"><span data-stu-id="2be8a-126">Introduction to Azure Cosmos DB and the native Cosmos DB API</span></span>

<span data-ttu-id="2be8a-127">[Azure DB rozwiązania Cosmos](https://docs.microsoft.com/en-us/azure/cosmos-db/introduction) jest usługą globalnie rozproszoną bazę danych firmy Microsoft dla aplikacji o krytycznym znaczeniu.</span><span class="sxs-lookup"><span data-stu-id="2be8a-127">[Azure Cosmos DB](https://docs.microsoft.com/en-us/azure/cosmos-db/introduction) is Microsoft's globally distributed database service for mission-critical applications.</span></span> <span data-ttu-id="2be8a-128">Udostępnia bazę danych systemu Azure rozwiązania Cosmos [dystrybucji globalne gotowe](https://docs.microsoft.com/en-us/azure/cosmos-db/distribute-data-globally), [elastyczne skalowanie przepływność i magazyn](https://docs.microsoft.com/en-us/azure/cosmos-db/partition-data) na całym świecie, jednocyfrowej milisekundy opóźnienia w 99-ty percentyl [pięć dobrze zdefiniowane poziomy spójności](https://docs.microsoft.com/en-us/azure/cosmos-db/consistency-levels), zagwarantować wysokiej dostępności, wszystkie kopie przez [SLA branży](https://azure.microsoft.com/support/legal/sla/cosmos-db/).</span><span class="sxs-lookup"><span data-stu-id="2be8a-128">Azure Cosmos DB provides [turn-key global distribution](https://docs.microsoft.com/en-us/azure/cosmos-db/distribute-data-globally), [elastic scaling of throughput and storage](https://docs.microsoft.com/en-us/azure/cosmos-db/partition-data) worldwide, single-digit millisecond latencies at the 99th percentile, [five well-defined consistency levels](https://docs.microsoft.com/en-us/azure/cosmos-db/consistency-levels), and guaranteed high availability, all backed by [industry-leading SLAs](https://azure.microsoft.com/support/legal/sla/cosmos-db/).</span></span> <span data-ttu-id="2be8a-129">Azure DB rozwiązania Cosmos [automatycznie indeksuje danych](http://www.vldb.org/pvldb/vol8/p1668-shukla.pdf) bez konieczności postępowania w przypadku zarządzania schematu i indeksu.</span><span class="sxs-lookup"><span data-stu-id="2be8a-129">Azure Cosmos DB [automatically indexes data](http://www.vldb.org/pvldb/vol8/p1668-shukla.pdf) without requiring you to deal with schema and index management.</span></span> <span data-ttu-id="2be8a-130">Jest wiele modeli i obsługuje dokumentu, klucz wartość, wykres i modeli danych kolumnowym.</span><span class="sxs-lookup"><span data-stu-id="2be8a-130">It is multi-model and supports document, key-value, graph, and columnar data models.</span></span>

<span data-ttu-id="2be8a-131">![](./media/image19.1.png) Rysunek 9-19.</span><span class="sxs-lookup"><span data-stu-id="2be8a-131">![](./media/image19.1.png) Figure 9-19.</span></span> <span data-ttu-id="2be8a-132">Azure DB rozwiązania Cosmos dystrybucji globalne</span><span class="sxs-lookup"><span data-stu-id="2be8a-132">Azure Cosmos DB global distribution</span></span>

<span data-ttu-id="2be8a-133">Jeśli używasz C\# model implementacji agregacji, które mają być używane przez rozwiązania Cosmos DB interfejsu API Azure, agregacji może być podobne do C\# klasy POCO używane EF podstawowych.</span><span class="sxs-lookup"><span data-stu-id="2be8a-133">When you use a C\# model to implement the aggregate to be used by the Azure Cosmos DB API, the aggregate can be similar to the C\# POCO classes used with EF Core.</span></span> <span data-ttu-id="2be8a-134">Jest to różnica w taki sposób, aby użyć ich z warstwy aplikacji i infrastruktury, zgodnie z poniższym kodem:</span><span class="sxs-lookup"><span data-stu-id="2be8a-134">The difference is in the way to use them from the application and infrastructure layers, as in the following code:</span></span>

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

<span data-ttu-id="2be8a-135">Widać, że sposób pracy z modelem domeny może być podobny do sposobu używania jej w Twojej warstwy modelu domeny po EF infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="2be8a-135">You can see that the way you work with your domain model can be similar to the way you use it in your domain model layer when the infrastructure is EF.</span></span> <span data-ttu-id="2be8a-136">Do zapewnienia spójności, invariants i sprawdzanie poprawności w agregacji są nadal używać tych samych metod głównego agregacji.</span><span class="sxs-lookup"><span data-stu-id="2be8a-136">You still use the same aggregate root methods to ensure consistency, invariants, and validations within the aggregate.</span></span>

<span data-ttu-id="2be8a-137">Jednak gdy można utrwalić modelu do bazy danych NoSQL, kod i zmiany interfejsu API znacznie w porównaniu do kodu EF Core lub inny kod powiązany relacyjnych baz danych.</span><span class="sxs-lookup"><span data-stu-id="2be8a-137">However, when you persist your model into the NoSQL database, the code and API change dramatically compared to EF Core code or any other code related to relational databases.</span></span>

## <a name="implementing-net-code-targeting-mongodb-and-azure-cosmos-db"></a><span data-ttu-id="2be8a-138">Wdrażanie kodu platformy .NET przeznaczonych dla bazy danych MongoDB i bazy danych Azure rozwiązania Cosmos</span><span class="sxs-lookup"><span data-stu-id="2be8a-138">Implementing .NET code targeting MongoDB and Azure Cosmos DB</span></span>

### <a name="using-azure-cosmos-db-from-net-containers"></a><span data-ttu-id="2be8a-139">Przy użyciu bazy danych rozwiązania Cosmos Azure z kontenerów .NET</span><span class="sxs-lookup"><span data-stu-id="2be8a-139">Using Azure Cosmos DB from .NET containers</span></span>

<span data-ttu-id="2be8a-140">Dostępne bazy danych Azure rozwiązania Cosmos baz danych z systemem w kontenerach, takich jak z dowolnej aplikacji .NET kodu platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="2be8a-140">You can access Azure Cosmos DB databases from .NET code running in containers, like from any other .NET application.</span></span> <span data-ttu-id="2be8a-141">Na przykład mikrousług Locations.API i Marketing.API w eShopOnContainers są implementowane, można korzystać z bazy danych Azure rozwiązania Cosmos baz danych.</span><span class="sxs-lookup"><span data-stu-id="2be8a-141">For instance, the Locations.API and Marketing.API microservices in eShopOnContainers are implemented so they can consume Azure Cosmos DB databases.</span></span>

<span data-ttu-id="2be8a-142">Istnieje jednak ograniczenia w usłudze Azure DB rozwiązania Cosmos z Docker programowanie środowiska punktu widzenia.</span><span class="sxs-lookup"><span data-stu-id="2be8a-142">However, there’s a limitation in Azure Cosmos DB from a Docker development environment point of view.</span></span> <span data-ttu-id="2be8a-143">Nawet wtedy, gdy istnieje lokalnie [Azure rozwiązania Cosmos DB emulatora](https://docs.microsoft.com/en-us/azure/cosmos-db/local-emulator) można uruchomić na maszynie lokalnej (np. komputer), jako późnego 2017 właśnie obsługuje on Windows, Linux nie.</span><span class="sxs-lookup"><span data-stu-id="2be8a-143">Even when there’s a on-premises [Azure Cosmos DB Emulator](https://docs.microsoft.com/en-us/azure/cosmos-db/local-emulator) able to run in a local development machine (like a PC), as of late 2017, it just supports Windows, not Linux.</span></span> 

<span data-ttu-id="2be8a-144">Istnieje również możliwość uruchomienia tego emulatora Docker, ale tylko kontenery systemu Windows z użyciem not kontenery systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="2be8a-144">There is also the possibility to run this emulator on Docker, but just on Windows Containers with the , not Linux Containers.</span></span> <span data-ttu-id="2be8a-145">Jeśli aplikacja jest wdrożona jako kontenery systemu Linux, ponieważ, obecnie jest początkowej przeszkoda dla środowiska programowania, w tym samym momencie nie można wdrożyć systemu Linux i Windows kontenerów na Docker dla systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="2be8a-145">That is an initial handicap for the development environment if your application is deployed as Linux containers, since, currently, you cannot deploy Linux and Windows Containers on Docker for Windows at the same time.</span></span> <span data-ttu-id="2be8a-146">Albo wszystkie kontenery wdrażany trzeba dla systemu Linux lub dla systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="2be8a-146">Either all containers being deployed have to be for Linux or for Windows.</span></span>  

<span data-ttu-id="2be8a-147">Rozwiązanie: tworzenie i testowanie wdrożenia idealne i bardziej bezpośrednie jest można wdrażać systemy bazy danych jako kontenery wraz z kontenerów niestandardowych, tak aby środowiska i testowania zawsze są spójne.</span><span class="sxs-lookup"><span data-stu-id="2be8a-147">The ideal and more straightforward deployment for a dev/test solution is to be able to deploy your database systems as containers along with your custom containers so your dev/test environments are always consistent.</span></span>

### <a name="use-mongodb-api-for-local-devtest-linuxwindows-containers-plus-azure-cosmos-db"></a><span data-ttu-id="2be8a-148">Za pomocą interfejsu API bazy danych MongoDB dla kontenery systemu Linux i Windows lokalnych i testowania oraz bazy danych Azure rozwiązania Cosmos</span><span class="sxs-lookup"><span data-stu-id="2be8a-148">Use MongoDB API for local dev/test Linux/Windows containers plus Azure Cosmos DB</span></span>

<span data-ttu-id="2be8a-149">Bazy danych DB rozwiązania cosmos obsługuje API bazy danych MongoDB dla platformy .NET, a także natywny protokół bazy danych MongoDB.</span><span class="sxs-lookup"><span data-stu-id="2be8a-149">Cosmos DB databases support MongoDB API for .NET as well as the native MongoDB wire protocol.</span></span> <span data-ttu-id="2be8a-150">Oznacza to, że przy użyciu istniejących sterowników aplikacji napisanych dla bazy danych MongoDB mogą teraz komunikować się z rozwiązania Cosmos bazy danych i użyj bazy danych DB rozwiązania Cosmos zamiast bazy danych MongoDB, jak pokazano w rysunku 9-20.</span><span class="sxs-lookup"><span data-stu-id="2be8a-150">This means that by using existing drivers, your application written for MongoDB can now communicate with Cosmos DB and use Cosmos DB databases instead of MongoDB databases, as shown in Figure 9-20.</span></span>

<span data-ttu-id="2be8a-151">![](./media/image19.2.png) Rysunek 9-20.</span><span class="sxs-lookup"><span data-stu-id="2be8a-151">![](./media/image19.2.png) Figure 9-20.</span></span> <span data-ttu-id="2be8a-152">Otwieranie bazy danych rozwiązania Cosmos Azure za pomocą interfejsu API bazy danych MongoDB i protokół</span><span class="sxs-lookup"><span data-stu-id="2be8a-152">Using MongoDB API and protocol to access Azure Cosmos DB</span></span>

<span data-ttu-id="2be8a-153">Ponieważ jest to bardzo wygodny podejście dowodu koncepcji w środowiskach Docker z kontenerami Linux [MongoDB Docker obrazu](https://hub.docker.com/r/_/mongo/) jest wiele architektury obrazu, który obsługuje kontenery Docker Linux i kontenery Docker systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="2be8a-153">This is a very convenient approach for proof of concepts in Docker environments with Linux containers because the [MongoDB Docker image](https://hub.docker.com/r/_/mongo/) is a multi-arch image that supports Docker Linux containers and Docker Windows containers.</span></span>

<span data-ttu-id="2be8a-154">Jak pokazano w obrazie 9-21 przy użyciu interfejsu API bazy danych MongoDB, eShopOnContainers obsługuje bazy danych MongoDB Linux i Windows kontenery lokalne Środowisko deweloperskie, ale następnie można przenieść na skalowalnych, PaaS w chmurze rozwiązania jako bazy danych rozwiązania Cosmos Azure przez po prostu [zmiana Parametry połączenia bazy danych MongoDB do punktu do bazy danych Azure rozwiązania Cosmos](https://docs.microsoft.com/en-us/azure/cosmos-db/connect-mongodb-account).</span><span class="sxs-lookup"><span data-stu-id="2be8a-154">As shown in the image 9-21, by using the MongoDB API, eShopOnContainers supports MongoDB Linux and Windows containers for the local development environment but then, you can move to a scalable, PaaS cloud solution as Azure Cosmos DB by simply [changing the MongoDB connection string to point to Azure Cosmos DB](https://docs.microsoft.com/en-us/azure/cosmos-db/connect-mongodb-account).</span></span> 

<span data-ttu-id="2be8a-155">![](./media/image20-bis.png) Rysunek 9-21.</span><span class="sxs-lookup"><span data-stu-id="2be8a-155">![](./media/image20-bis.png) Figure 9-21.</span></span> <span data-ttu-id="2be8a-156">Używanie kontenerów bazy danych MongoDB dla deweloperów env lub bazy danych Azure rozwiązania Cosmos w środowisku produkcyjnym eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="2be8a-156">eShopOnContainers using MongoDB containers for dev-env or Azure Cosmos DB for production</span></span>

<span data-ttu-id="2be8a-157">Produkcyjnej bazy danych Azure rozwiązania Cosmos będzie działać w chmurze platformy Azure jako PaaS i skalowalne usługi.</span><span class="sxs-lookup"><span data-stu-id="2be8a-157">The production Azure Cosmos DB would be running in Azure’s cloud as a PaaS and scalable service.</span></span>

<span data-ttu-id="2be8a-158">Niestandardowe kontenerów .NET Core może działać na hostach Docker lokalne działania projektowe (który jest przy użyciu rozwiązania Docker dla systemu Windows na komputerze z systemem Windows 10) lub można wdrożyć w środowisku produkcyjnym, takich jak Kubernetes Azure AKS lub sieć szkieletowa usług Azure.</span><span class="sxs-lookup"><span data-stu-id="2be8a-158">Your custom .NET Core containers can run on a local development Docker host (that is using Docker for Windows in a Windows 10 machine) or be deployed into a production environment, like Kubernetes in Azure AKS or Azure Service Fabric.</span></span> <span data-ttu-id="2be8a-159">W tym środowisku drugi czy wdrożyć tylko kontenery niestandardowych .NET Core, ale nie w kontenerze bazy danych MongoDB, ponieważ będą stosowane bazy danych Azure rozwiązania Cosmos w chmurze do obsługi danych w środowisku produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="2be8a-159">In this second environment, you would deploy only the .NET Core custom containers but not the MongoDB container since you’d be using Azure Cosmos DB in the cloud for handling the data in production.</span></span>

<span data-ttu-id="2be8a-160">Wyczyść zaletą korzystania z bazy danych MongoDB interfejsu API jest, że rozwiązania można uruchomić w obu baz danych, bazy danych MongoDB lub bazy danych rozwiązania Cosmos platformy Azure, więc migracje w różnych środowiskach powinno być łatwe.</span><span class="sxs-lookup"><span data-stu-id="2be8a-160">A clear benefit of using the MongoDB API is that your solution could run in both database engines, MongoDB or Azure Cosmos DB, so migrations to different environments should be easy.</span></span> <span data-ttu-id="2be8a-161">Jednak czasami warto użyć natywnego interfejsu API (która jest natywnego interfejsu API DB rozwiązania Cosmos) aby w pełni korzystać z możliwości aparatu określonej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="2be8a-161">However, sometimes it is worthwhile to use a native API (that is the native Cosmos DB API) in order to take full advantage of the capabilities of a specific database engine.</span></span>

<span data-ttu-id="2be8a-162">Aby uzyskać dalsze porównania po prostu przy użyciu bazy danych MongoDB i DB rozwiązania Cosmos w chmurze, zobacz [zalety używania bazy danych Azure rozwiązania Cosmos na tej stronie](https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb-introduction).</span><span class="sxs-lookup"><span data-stu-id="2be8a-162">For further comparison between simply using MongoDB versus Cosmos DB in the cloud, see the [Benefits of using Azure Cosmos DB in this page](https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb-introduction).</span></span> 


### <a name="analyze-your-approach-for-production-applications-mongodb-api-vs-cosmos-db-api"></a><span data-ttu-id="2be8a-163">Analizowanie swoje podejście przez aplikacje produkcyjne: vs API bazy danych MongoDB. Interfejs API rozwiązania cosmos bazy danych</span><span class="sxs-lookup"><span data-stu-id="2be8a-163">Analyze your approach for production applications: MongoDB API vs. Cosmos DB API</span></span>

<span data-ttu-id="2be8a-164">W eShopOnContainers firma Microsoft korzysta z interfejsu API bazy danych MongoDB powodu naszych priorytet zasadniczo do środowiska i testowania spójne korzystanie z bazy danych NoSQL, który może również współpracować z bazy danych Azure rozwiązania Cosmos.</span><span class="sxs-lookup"><span data-stu-id="2be8a-164">In eShopOnContainers, we’re using MongoDB API because our priority was fundamentally to have a consistent dev/test environment using a NoSQL database that could also work with Azure Cosmos DB.</span></span>

<span data-ttu-id="2be8a-165">Jednak jeśli planowanie na potrzeby bazy danych MongoDB API uzyskiwać dostęp do bazy danych rozwiązania Cosmos Azure na platformie Azure dla aplikacji produkcyjnych, które powinny analizować różnic w wydajności i możliwości, korzystając z interfejsu API bazy danych MongoDB dostępu do baz danych Azure DB rozwiązania Cosmos w porównaniu do za pomocą natywnego Interfejs API Azure rozwiązania Cosmos bazy danych.</span><span class="sxs-lookup"><span data-stu-id="2be8a-165">However, if you planning to use MongoDB API to access Azure Cosmos DB in Azure for production applications, you should analyze the differences in capabilities and performance when using MongoDB API to access Azure Cosmos DB databases compared to using the native Azure Cosmos DB API.</span></span> <span data-ttu-id="2be8a-166">Jeśli jest on podobny można użyć interfejsu API bazy danych MongoDB i skorzystać z zalet obsługi dwóch baz danych NoSQL, w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="2be8a-166">If it is similar you can use MongoDB API, and you get the benefit of supporting two NoSQL database engines at the same time.</span></span> 

<span data-ttu-id="2be8a-167">Można także użyć klastrów bazy danych MongoDB jako produkcyjną bazę danych w chmurze platformy Azure, z [usługę Azure bazy danych MongoDB](https://www.mongodb.com/scale/mongodb-azure-service).</span><span class="sxs-lookup"><span data-stu-id="2be8a-167">You could also use MongoDB clusters as the production database in Azure’s cloud, too, with [MongoDB Azure Service](https://www.mongodb.com/scale/mongodb-azure-service).</span></span> <span data-ttu-id="2be8a-168">Ale nie jest usługą PaaS obsługiwane przez firmę Microsoft.</span><span class="sxs-lookup"><span data-stu-id="2be8a-168">But that is not a PaaS service provided by Microsoft.</span></span> <span data-ttu-id="2be8a-169">W takim przypadku Azure jest po prostu tego rozwiązania hostingu pochodzących z bazy danych MongoDB.</span><span class="sxs-lookup"><span data-stu-id="2be8a-169">In this case, Azure is just hosting that solution coming from MongoDB.</span></span>

<span data-ttu-id="2be8a-170">Zasadniczo to po prostu zastrzeżenie, podając nie należy zawsze używać interfejsu API bazy danych MongoDB względem bazy danych rozwiązania Cosmos platformy Azure, jak robiliśmy w eShopOnContainers powodu wygodny wybór dla systemu Linux kontenerów.</span><span class="sxs-lookup"><span data-stu-id="2be8a-170">Basically, this is just a disclaimer stating that you shouldn’t always use MongoDB API against Azure Cosmos DB, as we did in eShopOnContainers because it was a convenient choice for Linux containers.</span></span> <span data-ttu-id="2be8a-171">Decyzja powinny być oparte na określonych potrzeb i testy, które należy wykonać w przypadku aplikacji produkcyjnej.</span><span class="sxs-lookup"><span data-stu-id="2be8a-171">The decision should be based on the specific needs and tests you need to do for your production application.</span></span>  

### <a name="the-code-using-mongodb-api-in-net-core-applications"></a><span data-ttu-id="2be8a-172">Kod: przy użyciu interfejsu API bazy danych MongoDB w aplikacjach .NET Core</span><span class="sxs-lookup"><span data-stu-id="2be8a-172">The code: Using MongoDB API in .NET Core applications</span></span>

<span data-ttu-id="2be8a-173">Interfejs API bazy danych MongoDB dla platformy .NET jest oparta na pakietów NuGet, których konieczne jest dodanie do projektów, takich jak Locations.API wyświetlany w rysunek 9-22.</span><span class="sxs-lookup"><span data-stu-id="2be8a-173">MongoDB API for .NET is based on NuGet packages that you need to add to your projects, like the Locations.API shown in Figure 9-22.</span></span>

<span data-ttu-id="2be8a-174">![](./media/image21-bis.png) Rysunek 9-22.</span><span class="sxs-lookup"><span data-stu-id="2be8a-174">![](./media/image21-bis.png) Figure 9-22.</span></span> <span data-ttu-id="2be8a-175">Odwołań w projekcie platformy .NET Core pakietów NuGet interfejsu API bazy danych MongoDB</span><span class="sxs-lookup"><span data-stu-id="2be8a-175">MongoDB API NuGet packages references in a .NET Core project</span></span>

<span data-ttu-id="2be8a-176">Teraz należy zbadać kod w następujących sekcjach.</span><span class="sxs-lookup"><span data-stu-id="2be8a-176">Let's investigate the code in the following sections.</span></span>

#### <a name="a-model-used-by-mongodb-api"></a><span data-ttu-id="2be8a-177">Model używany przez interfejs API bazy danych MongoDB</span><span class="sxs-lookup"><span data-stu-id="2be8a-177">A Model used by MongoDB API</span></span>

<span data-ttu-id="2be8a-178">Najpierw należy zdefiniować modelu, w którym będą przechowywane dane pochodzące z bazy danych w obszarze pamięci aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2be8a-178">First, you need to define a model that will hold the data coming from the database in your application’s memory space.</span></span> <span data-ttu-id="2be8a-179">Oto przykład używane w przypadku lokalizacji w eShopOnContainers modelu.</span><span class="sxs-lookup"><span data-stu-id="2be8a-179">Here’s an example of the model used for Locations at eShopOnContainers.</span></span>

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

<span data-ttu-id="2be8a-180">Można zauważyć, że istnieje kilka atrybutów i typy pochodzące z pakietami NuGet bazy danych MongoDB.</span><span class="sxs-lookup"><span data-stu-id="2be8a-180">You can see there are a few attributes and types coming from the MongoDB NuGet packages.</span></span>

<span data-ttu-id="2be8a-181">Bazy danych NoSQL są zazwyczaj bardzo dobrze nadają się do pracy z danymi hierarchicznymi nierelacyjnych.</span><span class="sxs-lookup"><span data-stu-id="2be8a-181">NoSQL databases are usually very well suited for working with non-relational hierarchical data.</span></span> <span data-ttu-id="2be8a-182">W tym przykładzie używamy expecially typy bazy danych MongoDB przewidzieć lokalizacje geograficzne, takie jak `GeoJson2DGeographicCoordinates`.</span><span class="sxs-lookup"><span data-stu-id="2be8a-182">In this example, we are using MongoDB types expecially made for geo-locations, like `GeoJson2DGeographicCoordinates`.</span></span>

#### <a name="retrieve-the-database-and-the-collection"></a><span data-ttu-id="2be8a-183">Pobieranie bazy danych i kolekcji</span><span class="sxs-lookup"><span data-stu-id="2be8a-183">Retrieve the database and the collection</span></span>

<span data-ttu-id="2be8a-184">W eShopOnContainers został utworzony w kontekście niestandardowej bazy danych, gdzie wdrożymy kod, aby pobrać bazy danych i MongoCollections, zgodnie z poniższym kodem.</span><span class="sxs-lookup"><span data-stu-id="2be8a-184">In eShopOnContainers, we have created a custom database context where we implement the code to retrieve the database and the MongoCollections, as in the following code.</span></span>

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

#### <a name="retrieve-the-data"></a><span data-ttu-id="2be8a-185">Pobieranie danych</span><span class="sxs-lookup"><span data-stu-id="2be8a-185">Retrieve the data</span></span>

<span data-ttu-id="2be8a-186">W kodu C#, takimi jak kontrolery interfejsu API sieci Web lub niestandardowe repozytoria implementacji można napisać kod podobny do następującego podczas wykonywania zapytania za pomocą interfejsu API bazy danych MongoDB.</span><span class="sxs-lookup"><span data-stu-id="2be8a-186">In C# code, like Web API controllers or custom Repositories implementation, you can write similar code to the following when querying through the MongoDB API.</span></span> <span data-ttu-id="2be8a-187">Należy pamiętać, że `_context` obiekt jest wystąpieniem poprzedniego `LocationsContext` klasy.</span><span class="sxs-lookup"><span data-stu-id="2be8a-187">Note that the `_context` object is an instance of the previous `LocationsContext` class.</span></span>

```csharp
public async Task<Locations> GetAsync(int locationId)
{
    var filter = Builders<Locations>.Filter.Eq("LocationId", locationId);
    return await _context.Locations
                            .Find(filter)
                            .FirstOrDefaultAsync();
}
```

#### <a name="use-an-env-var-in-the-docker-composeoverrideyml-file-for-the-mongodb-connection-string"></a><span data-ttu-id="2be8a-188">Użyj env-var w pliku docker compose.override.yml ciągu połączenia bazy danych MongoDB</span><span class="sxs-lookup"><span data-stu-id="2be8a-188">Use an env-var in the docker-compose.override.yml file for the MongoDB connection string</span></span>

<span data-ttu-id="2be8a-189">Podczas tworzenia obiektu MongoClient, musi on podstawowych parametr, który jest dokładnie `ConnectionString` parametr wskazujący właściwej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="2be8a-189">When creating a MongoClient object, it needs a fundamental parameter which is precisely the `ConnectionString` parameter pointing to the right database.</span></span> <span data-ttu-id="2be8a-190">W przypadku eShopOnContainers ciąg połączenia może wskazywać kontenerze MongoDB Docker lokalnego lub w bazie danych bazy danych Azure rozwiązania Cosmos "production".</span><span class="sxs-lookup"><span data-stu-id="2be8a-190">In the case of eShopOnContainers, the connection string can point to a local MongoDB Docker container or to a “production” Azure Cosmos DB database.</span></span>  <span data-ttu-id="2be8a-191">Ten ciąg połączenia pochodzi z określonych w zmiennych środowiskowych `docker-compose.override.yml` pliki używane podczas wdrażania z docker-compose lub Visual Studio, tak jak w poniższym kodzie yml.</span><span class="sxs-lookup"><span data-stu-id="2be8a-191">That connection string comes from the environment variables defined in the `docker-compose.override.yml` files used when deploying with docker-compose or Visual Studio, as in the following yml code.</span></span>

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

<span data-ttu-id="2be8a-192">`ConnectionString` Zmiennej środowiskowej zostanie rozwiązany w ten sposób: Jeśli `ESHOP_AZURE_COSMOSDB` — zmienna globalna jest zdefiniowany w `.env` plik z parametrami połączenia bazy danych Azure rozwiązania Cosmos, użyje on dostęp do bazy danych Azure DB rozwiązania Cosmos w chmurze.</span><span class="sxs-lookup"><span data-stu-id="2be8a-192">The `ConnectionString` environment variable is resolved this way: If the `ESHOP_AZURE_COSMOSDB` global variable is defined in the `.env` file with the Azure Cosmos DB connection string, it will use it to access the Azure Cosmos DB database in the cloud.</span></span> 

<span data-ttu-id="2be8a-193">Poniższy kod przedstawia `.env` plików ze zmienną środowiskową globalne ciągu połączenia bazy danych Azure rozwiązania Cosmos w eShopOnContainers:</span><span class="sxs-lookup"><span data-stu-id="2be8a-193">The following code shows the `.env` file with the Azure Cosmos DB connection string global environment variable, as implemented in eShopOnContainers:</span></span>

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

<span data-ttu-id="2be8a-194">Należy Usuń komentarz linii ESHOP_AZURE_COSMOSDB i aktualizacji za pomocą parametrów połączenia bazy danych Azure rozwiązania Cosmos uzyskane z portalu Azure, jak wyjaśniono w [połączyć aplikację bazy danych MongoDB do bazy danych Azure rozwiązania Cosmos](https://docs.microsoft.com/en-us/azure/cosmos-db/connect-mongodb-account).</span><span class="sxs-lookup"><span data-stu-id="2be8a-194">You should uncomment the ESHOP_AZURE_COSMOSDB line and update it with your Azure Cosmos DB connection string obtained from the Azure portal as explained in [Connect a MongoDB application to Azure Cosmos DB](https://docs.microsoft.com/en-us/azure/cosmos-db/connect-mongodb-account).</span></span>

<span data-ttu-id="2be8a-195">Jeśli `ESHOP_AZURE_COSMOSDB` — zmienna globalna jest pusta, co oznacza, że jej jest oznaczone jako limit w `.env` pliku, a następnie kontenera korzysta z domyślnego ciągu połączenia bazy danych MongoDB wskazanie w kontenerze lokalnej bazy danych MongoDB wdrożone w eShopOnContainers o nazwie `nosql.data`, jak pokazano w poniższym kodzie .yml.</span><span class="sxs-lookup"><span data-stu-id="2be8a-195">If the `ESHOP_AZURE_COSMOSDB` global variable is empty, meaning that it is commented out in the `.env` file, then the container uses a default MongoDB connection string pointing to the local MongoDB container deployed in eShopOnContainers which is named `nosql.data`, as shown in the following .yml code.</span></span> 

#### <a name="additional-resources"></a><span data-ttu-id="2be8a-196">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="2be8a-196">Additional resources</span></span>

-   <span data-ttu-id="2be8a-197">**Modelowanie danych dokumentów NoSQL baz danych**
    [*https://docs.microsoft.com/en-us/azure/cosmos-db/modeling-data*](https://docs.microsoft.com/en-us/azure/cosmos-db/modeling-data)</span><span class="sxs-lookup"><span data-stu-id="2be8a-197">**Modeling document data for NoSQL databases**
[*https://docs.microsoft.com/en-us/azure/cosmos-db/modeling-data*](https://docs.microsoft.com/en-us/azure/cosmos-db/modeling-data)</span></span>

-   <span data-ttu-id="2be8a-198">**Vaughn Vernon. Nadaje się doskonale oparte na domenie projektu agregacji sklepu?**
    [*https://vaughnvernon.co/?p=942*](https://vaughnvernon.co/?p=942)</span><span class="sxs-lookup"><span data-stu-id="2be8a-198">**Vaughn Vernon. The Ideal Domain-Driven Design Aggregate Store?**
[*https://vaughnvernon.co/?p=942*](https://vaughnvernon.co/?p=942)</span></span>

-   <span data-ttu-id="2be8a-199">**Wprowadzenie do platformy Azure rozwiązania Cosmos DB: interfejs API dla bazy danych MongoDB** 
    [*https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb-introduction*](https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb-introduction)</span><span class="sxs-lookup"><span data-stu-id="2be8a-199">**Introduction to Azure Cosmos DB: API for MongoDB** 
[*https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb-introduction*](https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb-introduction)</span></span>

-   <span data-ttu-id="2be8a-200">**Azure rozwiązania Cosmos bazy danych: Tworzenie aplikacji sieci web interfejsu API bazy danych MongoDB z usług .NET i portalu Azure** 
    [*https://docs.microsoft.com/en-us/azure/cosmos-db/create-mongodb-dotnet *](https://docs.microsoft.com/en-us/azure/cosmos-db/create-mongodb-dotnet )</span><span class="sxs-lookup"><span data-stu-id="2be8a-200">**Azure Cosmos DB: Build a MongoDB API web app with .NET and the Azure portal** 
[*https://docs.microsoft.com/en-us/azure/cosmos-db/create-mongodb-dotnet *](https://docs.microsoft.com/en-us/azure/cosmos-db/create-mongodb-dotnet )</span></span>

-   <span data-ttu-id="2be8a-201">**Użyj emulatora usługi Azure rozwiązania Cosmos bazy danych dla lokalnych projektowania i testowania** 
    [*https://docs.microsoft.com/en-us/azure/cosmos-db/local-emulator*](https://docs.microsoft.com/en-us/azure/cosmos-db/local-emulator)</span><span class="sxs-lookup"><span data-stu-id="2be8a-201">**Use the Azure Cosmos DB Emulator for local development and testing** 
[*https://docs.microsoft.com/en-us/azure/cosmos-db/local-emulator*](https://docs.microsoft.com/en-us/azure/cosmos-db/local-emulator)</span></span>

-   <span data-ttu-id="2be8a-202">**Łączenie aplikacji bazy danych MongoDB, do bazy danych Azure rozwiązania Cosmos** 
    [*https://docs.microsoft.com/en-us/azure/cosmos-db/connect-mongodb-account*](https://docs.microsoft.com/en-us/azure/cosmos-db/connect-mongodb-account)</span><span class="sxs-lookup"><span data-stu-id="2be8a-202">**Connect a MongoDB application to Azure Cosmos DB** 
[*https://docs.microsoft.com/en-us/azure/cosmos-db/connect-mongodb-account*](https://docs.microsoft.com/en-us/azure/cosmos-db/connect-mongodb-account)</span></span>

-   <span data-ttu-id="2be8a-203">**Obraz Docker emulatora DB rozwiązania Cosmos (kontenera systemu Windows)** 
    [*https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator/*](https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator/)</span><span class="sxs-lookup"><span data-stu-id="2be8a-203">**The Cosmos DB Emulator Docker image (Windows Container)** 
[*https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator/*](https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator/)</span></span>

-   <span data-ttu-id="2be8a-204">**Obraz Docker bazy danych MongoDB (Linux i kontenera systemu Windows)** 
    [*https://hub.docker.com/r/_/mongo/*](https://hub.docker.com/r/_/mongo/)</span><span class="sxs-lookup"><span data-stu-id="2be8a-204">**The MongoDB Docker image (Linux and Windows Container)** 
[*https://hub.docker.com/r/_/mongo/*](https://hub.docker.com/r/_/mongo/)</span></span>

-   <span data-ttu-id="2be8a-205">**Użyj MongoChef (3T w Studio) z bazy danych Azure rozwiązania Cosmos: interfejsu API dla konta bazy danych MongoDB** 
    [*https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb-mongochef*](https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb-mongochef)</span><span class="sxs-lookup"><span data-stu-id="2be8a-205">**Use MongoChef (Studio 3T) with an Azure Cosmos DB: API for MongoDB account** 
[*https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb-mongochef*](https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb-mongochef)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="2be8a-206">[Previous] (infrastructure-persistence-layer-implemenation-entity-framework-core.md) [Next] (microservice-application-layer-web-api-design.md)</span><span class="sxs-lookup"><span data-stu-id="2be8a-206">[Previous] (infrastructure-persistence-layer-implemenation-entity-framework-core.md) [Next] (microservice-application-layer-web-api-design.md)</span></span>
