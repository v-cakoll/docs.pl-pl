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
# <a name="use-nosql-databases-as-a-persistence-infrastructure"></a><span data-ttu-id="2c5fa-103">Używanie baz danych NoSQL jako infrastruktury trwałości</span><span class="sxs-lookup"><span data-stu-id="2c5fa-103">Use NoSQL databases as a persistence infrastructure</span></span>

<span data-ttu-id="2c5fa-104">Korzystając z baz danych NoSQL dla warstwy danych infrastruktury, zazwyczaj nie należy używać ORM jak Entity Framework Core.</span><span class="sxs-lookup"><span data-stu-id="2c5fa-104">When you use NoSQL databases for your infrastructure data tier, you typically do not use an ORM like Entity Framework Core.</span></span> <span data-ttu-id="2c5fa-105">Zamiast tego należy użyć interfejsu API dostarczonego przez aparat NoSQL, takich jak Azure Cosmos DB, MongoDB, Cassandra, RavenDB, CouchDB lub Tabele usługi Azure Storage.</span><span class="sxs-lookup"><span data-stu-id="2c5fa-105">Instead you use the API provided by the NoSQL engine, such as Azure Cosmos DB, MongoDB, Cassandra, RavenDB, CouchDB, or Azure Storage Tables.</span></span>

<span data-ttu-id="2c5fa-106">Jednak podczas korzystania z bazy danych NoSQL, zwłaszcza bazy danych zorientowanych na dokumenty, takich jak Azure Cosmos DB, CouchDB lub RavenDB, sposób projektowania modelu za pomocą agregacji DDD jest częściowo podobny do jak można to zrobić w EF Core, w odniesieniu do identyfikacji zagregowanych korzeni, klas jednostek podrzędnych i klas obiektów wartości.</span><span class="sxs-lookup"><span data-stu-id="2c5fa-106">However, when you use a NoSQL database, especially a document-oriented database like Azure Cosmos DB, CouchDB, or RavenDB, the way you design your model with DDD aggregates is partially similar to how you can do it in EF Core, in regards to the identification of aggregate roots, child entity classes, and value object classes.</span></span> <span data-ttu-id="2c5fa-107">Ale ostatecznie wybór bazy danych będzie miał wpływ na projekt.</span><span class="sxs-lookup"><span data-stu-id="2c5fa-107">But, ultimately, the database selection will impact in your design.</span></span>

<span data-ttu-id="2c5fa-108">Korzystając z bazy danych zorientowanej na dokument, należy zaimplementować agregację jako pojedynczy dokument, serializowany w formacie JSON lub innym formacie.</span><span class="sxs-lookup"><span data-stu-id="2c5fa-108">When you use a document-oriented database, you implement an aggregate as a single document, serialized in JSON or another format.</span></span> <span data-ttu-id="2c5fa-109">Jednak użycie bazy danych jest przezroczyste z punktu widzenia kodu modelu domeny.</span><span class="sxs-lookup"><span data-stu-id="2c5fa-109">However, the use of the database is transparent from a domain model code point of view.</span></span> <span data-ttu-id="2c5fa-110">Podczas korzystania z bazy danych NoSQL, nadal używasz klas jednostek i zagregowanych klas głównych, ale z większą elastycznością niż podczas korzystania z EF Core, ponieważ trwałość nie jest relacyjne.</span><span class="sxs-lookup"><span data-stu-id="2c5fa-110">When using a NoSQL database, you still are using entity classes and aggregate root classes, but with more flexibility than when using EF Core because the persistence is not relational.</span></span>

<span data-ttu-id="2c5fa-111">Różnica polega na tym, jak utrwalić tego modelu.</span><span class="sxs-lookup"><span data-stu-id="2c5fa-111">The difference is in how you persist that model.</span></span> <span data-ttu-id="2c5fa-112">Jeśli zaimplementowano model domeny na podstawie klas jednostek POCO, niezależny od trwałości infrastruktury, może wyglądać, że można przenieść do innej infrastruktury trwałości, nawet z relacyjne do NoSQL.</span><span class="sxs-lookup"><span data-stu-id="2c5fa-112">If you implemented your domain model based on POCO entity classes, agnostic to the infrastructure persistence, it might look like you could move to a different persistence infrastructure, even from relational to NoSQL.</span></span> <span data-ttu-id="2c5fa-113">Jednak to nie powinno być twoim celem.</span><span class="sxs-lookup"><span data-stu-id="2c5fa-113">However, that should not be your goal.</span></span> <span data-ttu-id="2c5fa-114">Zawsze istnieją ograniczenia i kompromisy w różnych technologii bazy danych, więc nie będzie można mieć tego samego modelu dla relacyjnych lub NoSQL baz danych.</span><span class="sxs-lookup"><span data-stu-id="2c5fa-114">There are always constraints and trade-offs in the different database technologies, so you will not be able to have the same model for relational or NoSQL databases.</span></span> <span data-ttu-id="2c5fa-115">Zmiana modeli trwałości nie jest trywialnym zadaniem, ponieważ operacje transakcji i trwałości będą bardzo różne.</span><span class="sxs-lookup"><span data-stu-id="2c5fa-115">Changing persistence models is not a trivial task, because transactions and persistence operations will be very different.</span></span>

<span data-ttu-id="2c5fa-116">Na przykład w bazie danych zorientowanej na dokument jest w porządku dla agregacji katalogu głównego mieć wiele właściwości kolekcji podrzędnej.</span><span class="sxs-lookup"><span data-stu-id="2c5fa-116">For example, in a document-oriented database, it is okay for an aggregate root to have multiple child collection properties.</span></span> <span data-ttu-id="2c5fa-117">W relacyjnej bazie danych wykonywanie zapytań o wiele właściwości kolekcji podrzędnej nie jest łatwo zoptymalizowane, ponieważ otrzymasz instrukcję UNION ALL SQL z ef.</span><span class="sxs-lookup"><span data-stu-id="2c5fa-117">In a relational database, querying multiple child collection properties is not easily optimized, because you get a UNION ALL SQL statement back from EF.</span></span> <span data-ttu-id="2c5fa-118">Posiadanie tego samego modelu domeny dla relacyjnych baz danych lub baz danych NoSQL nie jest proste i nie należy próbować tego robić.</span><span class="sxs-lookup"><span data-stu-id="2c5fa-118">Having the same domain model for relational databases or NoSQL databases is not simple, and you should not try to do it.</span></span> <span data-ttu-id="2c5fa-119">Naprawdę trzeba zaprojektować model ze zrozumieniem, jak dane będą używane w każdej konkretnej bazie danych.</span><span class="sxs-lookup"><span data-stu-id="2c5fa-119">You really have to design your model with an understanding of how the data is going to be used in each particular database.</span></span>

<span data-ttu-id="2c5fa-120">Zaletą podczas korzystania z baz danych NoSQL jest to, że jednostki są bardziej zdenormalizowane, więc nie należy ustawiać mapowania tabeli.</span><span class="sxs-lookup"><span data-stu-id="2c5fa-120">A benefit when using NoSQL databases is that the entities are more denormalized, so you do not set a table mapping.</span></span> <span data-ttu-id="2c5fa-121">Model domeny może być bardziej elastyczny niż przy użyciu relacyjnej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="2c5fa-121">Your domain model can be more flexible than when using a relational database.</span></span>

<span data-ttu-id="2c5fa-122">Podczas projektowania modelu domeny na podstawie agregatów przejście do bazy danych zorientowanych na dokument może być jeszcze łatwiejsze niż przy użyciu relacyjnej bazy danych, ponieważ agregaty, które projektujesz, są podobne do dokumentów szeregowanych w bazie danych zorientowanej na dokument.</span><span class="sxs-lookup"><span data-stu-id="2c5fa-122">When you design your domain model based on aggregates, moving to NoSQL and document-oriented databases might be even easier than using a relational database, because the aggregates you design are similar to serialized documents in a document-oriented database.</span></span> <span data-ttu-id="2c5fa-123">Następnie można uwzględnić w tych "workach" wszystkie informacje, które mogą być potrzebne do tego agregacji.</span><span class="sxs-lookup"><span data-stu-id="2c5fa-123">Then you can include in those "bags" all the information you might need for that aggregate.</span></span>

<span data-ttu-id="2c5fa-124">Na przykład następujący kod JSON jest przykładową implementacją agregacji zamówień podczas korzystania z bazy danych zorientowanej na dokument.</span><span class="sxs-lookup"><span data-stu-id="2c5fa-124">For instance, the following JSON code is a sample implementation of an order aggregate when using a document-oriented database.</span></span> <span data-ttu-id="2c5fa-125">Jest podobny do agregacji zamówień zaimplementowaliśmy w przykładzie eShopOnContainers, ale bez użycia EF Core pod spodem.</span><span class="sxs-lookup"><span data-stu-id="2c5fa-125">It is similar to the order aggregate we implemented in the eShopOnContainers sample, but without using EF Core underneath.</span></span>

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

## <a name="introduction-to-azure-cosmos-db-and-the-native-cosmos-db-api"></a><span data-ttu-id="2c5fa-126">Wprowadzenie do usługi Azure Cosmos DB i macierzystego interfejsu API usługi Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="2c5fa-126">Introduction to Azure Cosmos DB and the native Cosmos DB API</span></span>

<span data-ttu-id="2c5fa-127">[Usługa Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction) to globalnie rozproszona usługa bazy danych firmy Microsoft dla aplikacji o znaczeniu krytycznym.</span><span class="sxs-lookup"><span data-stu-id="2c5fa-127">[Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction) is Microsoft's globally distributed database service for mission-critical applications.</span></span> <span data-ttu-id="2c5fa-128">Usługa Azure Cosmos DB zapewnia [kompleksową globalną dystrybucję](https://docs.microsoft.com/azure/cosmos-db/distribute-data-globally), [elastyczne skalowanie przepływności i pamięci](https://docs.microsoft.com/azure/cosmos-db/partition-data) w skali globalnej, milisekundowe opóźnienia w 99. percentylu, [pięć odpowiednio zdefiniowanych poziomów spójności](https://docs.microsoft.com/azure/cosmos-db/consistency-levels) oraz gwarantowaną wysoką dostępność, wspierane przez [wiodące w branży umowy SLA](https://azure.microsoft.com/support/legal/sla/cosmos-db/).</span><span class="sxs-lookup"><span data-stu-id="2c5fa-128">Azure Cosmos DB provides [turn-key global distribution](https://docs.microsoft.com/azure/cosmos-db/distribute-data-globally), [elastic scaling of throughput and storage](https://docs.microsoft.com/azure/cosmos-db/partition-data) worldwide, single-digit millisecond latencies at the 99th percentile, [five well-defined consistency levels](https://docs.microsoft.com/azure/cosmos-db/consistency-levels), and guaranteed high availability, all backed by [industry-leading SLAs](https://azure.microsoft.com/support/legal/sla/cosmos-db/).</span></span> <span data-ttu-id="2c5fa-129">Usługa Azure Cosmos DB [automatycznie indeksuje dane](https://www.vldb.org/pvldb/vol8/p1668-shukla.pdf) bez konieczności zarządzania schematami i indeksami.</span><span class="sxs-lookup"><span data-stu-id="2c5fa-129">Azure Cosmos DB [automatically indexes data](https://www.vldb.org/pvldb/vol8/p1668-shukla.pdf) without requiring you to deal with schema and index management.</span></span> <span data-ttu-id="2c5fa-130">To usługa wielomodelowa, obsługująca modele oparte na dokumentach, parach klucz-wartość, grafach i kolumnach.</span><span class="sxs-lookup"><span data-stu-id="2c5fa-130">It is multi-model and supports document, key-value, graph, and columnar data models.</span></span>

![Diagram przedstawiający globalną dystrybucję usługi Azure Cosmos DB.](./media/nosql-database-persistence-infrastructure/azure-cosmos-db-global-distribution.png)

<span data-ttu-id="2c5fa-132">**Rysunek 7-19**.</span><span class="sxs-lookup"><span data-stu-id="2c5fa-132">**Figure 7-19**.</span></span> <span data-ttu-id="2c5fa-133">Globalna dystrybucja usługi Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="2c5fa-133">Azure Cosmos DB global distribution</span></span>

<span data-ttu-id="2c5fa-134">Korzystając z modelu\# C do zaimplementowania agregacji, która ma być używana przez\# interfejs API usługi Azure Cosmos DB, agregacja może być podobna do klas POCO C używanych z EF Core.</span><span class="sxs-lookup"><span data-stu-id="2c5fa-134">When you use a C\# model to implement the aggregate to be used by the Azure Cosmos DB API, the aggregate can be similar to the C\# POCO classes used with EF Core.</span></span> <span data-ttu-id="2c5fa-135">Różnica polega na sposobie korzystania z nich z warstw aplikacji i infrastruktury, jak w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="2c5fa-135">The difference is in the way to use them from the application and infrastructure layers, as in the following code:</span></span>

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

<span data-ttu-id="2c5fa-136">Widać, że sposób pracy z modelem domeny może być podobny do sposobu, w jaki używasz go w warstwie modelu domeny, gdy infrastruktura jest EF.</span><span class="sxs-lookup"><span data-stu-id="2c5fa-136">You can see that the way you work with your domain model can be similar to the way you use it in your domain model layer when the infrastructure is EF.</span></span> <span data-ttu-id="2c5fa-137">Nadal używasz tych samych metod głównego agregacji, aby zapewnić spójność, invariants i sprawdzania poprawności w ramach agregacji.</span><span class="sxs-lookup"><span data-stu-id="2c5fa-137">You still use the same aggregate root methods to ensure consistency, invariants, and validations within the aggregate.</span></span>

<span data-ttu-id="2c5fa-138">Jednak po utrwaleniu modelu w bazie danych NoSQL, kod i interfejs API zmieniają się dramatycznie w porównaniu do kodu EF Core lub innego kodu związanego z relacyjnych baz danych.</span><span class="sxs-lookup"><span data-stu-id="2c5fa-138">However, when you persist your model into the NoSQL database, the code and API change dramatically compared to EF Core code or any other code related to relational databases.</span></span>

## <a name="implement-net-code-targeting-mongodb-and-azure-cosmos-db"></a><span data-ttu-id="2c5fa-139">Implementowanie kodu platformy NET kierowanego na usługi MongoDB i usługę Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="2c5fa-139">Implement .NET code targeting MongoDB and Azure Cosmos DB</span></span>

### <a name="use-azure-cosmos-db-from-net-containers"></a><span data-ttu-id="2c5fa-140">Korzystanie z bazy danych usługi Azure Cosmos DB z kontenerów platformy .NET</span><span class="sxs-lookup"><span data-stu-id="2c5fa-140">Use Azure Cosmos DB from .NET containers</span></span>

<span data-ttu-id="2c5fa-141">Dostęp do baz danych usługi Azure Cosmos DB można uzyskać z kodu platformy .NET uruchomionego w kontenerach, na przykład z dowolnej innej aplikacji platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="2c5fa-141">You can access Azure Cosmos DB databases from .NET code running in containers, like from any other .NET application.</span></span> <span data-ttu-id="2c5fa-142">Na przykład lokalizacje.API i marketing.API mikrousług w eShopOnContainers są implementowane, dzięki czemu mogą korzystać z baz danych usługi Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="2c5fa-142">For instance, the Locations.API and Marketing.API microservices in eShopOnContainers are implemented so they can consume Azure Cosmos DB databases.</span></span>

<span data-ttu-id="2c5fa-143">Jednak istnieje ograniczenie w usłudze Azure Cosmos DB z punktu widzenia środowiska deweloperskiego platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="2c5fa-143">However, there’s a limitation in Azure Cosmos DB from a Docker development environment point of view.</span></span> <span data-ttu-id="2c5fa-144">Mimo że istnieje lokalna [azure cosmos db emulator,](https://docs.microsoft.com/azure/cosmos-db/local-emulator) który można uruchomić na komputerze deweloperskim lokalnym, obsługuje tylko system Windows.</span><span class="sxs-lookup"><span data-stu-id="2c5fa-144">Even though there’s an on-premises [Azure Cosmos DB Emulator](https://docs.microsoft.com/azure/cosmos-db/local-emulator) that can run in a local development machine, it only supports Windows.</span></span> <span data-ttu-id="2c5fa-145">Linux i macOS nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="2c5fa-145">Linux and macOS aren't supported.</span></span>

<span data-ttu-id="2c5fa-146">Istnieje również możliwość uruchomienia tego emulatora na platformy Docker, ale tylko na kontenerach systemu Windows, a nie z kontenerami systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="2c5fa-146">There's also the possibility to run this emulator on Docker, but just on Windows Containers, not with Linux Containers.</span></span> <span data-ttu-id="2c5fa-147">Jest to początkowy handicap dla środowiska programistycznego, jeśli aplikacja jest wdrażana jako kontenery systemu Linux, ponieważ obecnie nie można wdrożyć kontenerów systemu Linux i Windows w programie Docker dla systemu Windows w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="2c5fa-147">That's an initial handicap for the development environment if your application is deployed as Linux containers, since, currently, you can't deploy Linux and Windows Containers on Docker for Windows at the same time.</span></span> <span data-ttu-id="2c5fa-148">Albo wszystkie kontenery są wdrażane muszą być dla Systemu Linux lub dla systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="2c5fa-148">Either all containers being deployed have to be for Linux or for Windows.</span></span>

<span data-ttu-id="2c5fa-149">Idealnym i prostszym wdrożeniem dla rozwiązania deweloperskiego/testowego jest możliwość wdrażania systemów bazy danych jako kontenerów wraz z kontenerami niestandardowymi, dzięki czemu środowiska deweloperów/testów są zawsze spójne.</span><span class="sxs-lookup"><span data-stu-id="2c5fa-149">The ideal and more straightforward deployment for a dev/test solution is to be able to deploy your database systems as containers along with your custom containers so your dev/test environments are always consistent.</span></span>

### <a name="use-mongodb-api-for-local-devtest-linuxwindows-containers-plus-azure-cosmos-db"></a><span data-ttu-id="2c5fa-150">Użyj interfejsu API MongoDB dla lokalnych kontenerów deweloperskich/testowych systemu Linux/Windows oraz usługi Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="2c5fa-150">Use MongoDB API for local dev/test Linux/Windows containers plus Azure Cosmos DB</span></span>

<span data-ttu-id="2c5fa-151">Bazy danych Usługi Cosmos DB obsługują interfejs API MongoDB dla platformy .NET oraz macierzysty protokół przewodowy MongoDB.</span><span class="sxs-lookup"><span data-stu-id="2c5fa-151">Cosmos DB databases support MongoDB API for .NET as well as the native MongoDB wire protocol.</span></span> <span data-ttu-id="2c5fa-152">Oznacza to, że przy użyciu istniejących sterowników, aplikacja napisana dla MongoDB może teraz komunikować się z usługą Cosmos DB i używać baz danych usługi Cosmos DB zamiast baz danych MongoDB, jak pokazano na rysunku 7-20.</span><span class="sxs-lookup"><span data-stu-id="2c5fa-152">This means that by using existing drivers, your application written for MongoDB can now communicate with Cosmos DB and use Cosmos DB databases instead of MongoDB databases, as shown in Figure 7-20.</span></span>

![Diagram pokazujący, że usługa Cosmos DB obsługuje protokół przewodowy .NET i MongoDB.](./media/nosql-database-persistence-infrastructure/mongodb-api-wire-protocol.png)

<span data-ttu-id="2c5fa-154">**Rysunek 7-20**.</span><span class="sxs-lookup"><span data-stu-id="2c5fa-154">**Figure 7-20**.</span></span> <span data-ttu-id="2c5fa-155">Korzystanie z interfejsu API i protokołu MongoDB w celu uzyskania dostępu do usługi Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="2c5fa-155">Using MongoDB API and protocol to access Azure Cosmos DB</span></span>

<span data-ttu-id="2c5fa-156">Jest to bardzo wygodne podejście do weryfikacji pojęć w środowiskach platformy Docker z kontenerami systemu Linux, ponieważ [obraz platformy Docker MongoDB](https://hub.docker.com/r/_/mongo/) jest obrazem wielokołowym, który obsługuje kontenery Systemu Docker Linux i kontenery systemu Windows platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="2c5fa-156">This is a very convenient approach for proof of concepts in Docker environments with Linux containers because the [MongoDB Docker image](https://hub.docker.com/r/_/mongo/) is a multi-arch image that supports Docker Linux containers and Docker Windows containers.</span></span>

<span data-ttu-id="2c5fa-157">Jak pokazano na poniższej ilustracji, za pomocą interfejsu API MongoDB, eShopOnContainers obsługuje kontenery MongoDB Linux i Windows dla lokalnego środowiska programistycznego, ale następnie można przejść do skalowalnego rozwiązania chmury PaaS jako usługi Azure Cosmos DB, po prostu [zmieniając ciąg połączenia MongoDB, aby wskazać usługę Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account).</span><span class="sxs-lookup"><span data-stu-id="2c5fa-157">As shown in the following image, by using the MongoDB API, eShopOnContainers supports MongoDB Linux and Windows containers for the local development environment but then, you can move to a scalable, PaaS cloud solution as Azure Cosmos DB by simply [changing the MongoDB connection string to point to Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account).</span></span>

![Diagram pokazujący, że mikrousługa lokalizacji w eShopOnContainers można użyć usługi Cosmos DB lub Mongo DB.](./media/nosql-database-persistence-infrastructure/eshoponcontainers-mongodb-containers.png)

<span data-ttu-id="2c5fa-159">**Rysunek 7-21**.</span><span class="sxs-lookup"><span data-stu-id="2c5fa-159">**Figure 7-21**.</span></span> <span data-ttu-id="2c5fa-160">EShopOnContainers przy użyciu kontenerów MongoDB dla dev-env lub Azure Cosmos DB dla produkcji</span><span class="sxs-lookup"><span data-stu-id="2c5fa-160">eShopOnContainers using MongoDB containers for dev-env or Azure Cosmos DB for production</span></span>

<span data-ttu-id="2c5fa-161">Produkcyjna usługa Azure Cosmos DB będzie działać w chmurze platformy Azure jako usługa PaaS i skalowalna.</span><span class="sxs-lookup"><span data-stu-id="2c5fa-161">The production Azure Cosmos DB would be running in Azure's cloud as a PaaS and scalable service.</span></span>

<span data-ttu-id="2c5fa-162">Niestandardowe kontenery .NET Core można uruchomić na lokalnym hoście platformy Docker rozwoju (który używa platformy Docker dla systemu Windows na komputerze z systemem Windows 10) lub zostać wdrożone w środowisku produkcyjnym, takich jak Kubernetes w usłudze Azure AKS lub azure service service fabric.</span><span class="sxs-lookup"><span data-stu-id="2c5fa-162">Your custom .NET Core containers can run on a local development Docker host (that is using Docker for Windows in a Windows 10 machine) or be deployed into a production environment, like Kubernetes in Azure AKS or Azure Service Fabric.</span></span> <span data-ttu-id="2c5fa-163">W tym drugim środowisku można wdrożyć tylko kontenery niestandardowe .NET Core, ale nie kontener MongoDB, ponieważ można używać usługi Azure Cosmos DB w chmurze do obsługi danych w środowisku produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="2c5fa-163">In this second environment, you would deploy only the .NET Core custom containers but not the MongoDB container since you'd be using Azure Cosmos DB in the cloud for handling the data in production.</span></span>

<span data-ttu-id="2c5fa-164">Wyraźną zaletą korzystania z interfejsu API mongodb jest, że rozwiązanie może działać w obu aparatach bazy danych, MongoDB lub Azure Cosmos DB, więc migracje do różnych środowisk powinny być łatwe.</span><span class="sxs-lookup"><span data-stu-id="2c5fa-164">A clear benefit of using the MongoDB API is that your solution could run in both database engines, MongoDB or Azure Cosmos DB, so migrations to different environments should be easy.</span></span> <span data-ttu-id="2c5fa-165">Jednak czasami warto użyć natywnego interfejsu API (czyli natywnego interfejsu API usługi Cosmos DB), aby w pełni wykorzystać możliwości określonego aparatu bazy danych.</span><span class="sxs-lookup"><span data-stu-id="2c5fa-165">However, sometimes it is worthwhile to use a native API (that is the native Cosmos DB API) in order to take full advantage of the capabilities of a specific database engine.</span></span>

<span data-ttu-id="2c5fa-166">Aby uzyskać dalsze porównanie po prostu przy użyciu MongoDB i Cosmos DB w chmurze, zobacz [korzyści z używania usługi Azure Cosmos DB na tej stronie](https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction).</span><span class="sxs-lookup"><span data-stu-id="2c5fa-166">For further comparison between simply using MongoDB versus Cosmos DB in the cloud, see the [Benefits of using Azure Cosmos DB in this page](https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction).</span></span>

### <a name="analyze-your-approach-for-production-applications-mongodb-api-vs-cosmos-db-api"></a><span data-ttu-id="2c5fa-167">Analizowanie podejścia pod kątem aplikacji produkcyjnych: interfejs API mongodb vs. Cosmos DB API</span><span class="sxs-lookup"><span data-stu-id="2c5fa-167">Analyze your approach for production applications: MongoDB API vs. Cosmos DB API</span></span>

<span data-ttu-id="2c5fa-168">W eShopOnContainers używamy interfejsu API MongoDB, ponieważ naszym priorytetem było zasadniczo mieć spójne środowisko deweloper/test przy użyciu bazy danych NoSQL, która może również współpracować z usługą Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="2c5fa-168">In eShopOnContainers, we're using MongoDB API because our priority was fundamentally to have a consistent dev/test environment using a NoSQL database that could also work with Azure Cosmos DB.</span></span>

<span data-ttu-id="2c5fa-169">Jednak jeśli planujesz używać interfejsu API mongodb do uzyskiwania dostępu do usługi Azure Cosmos DB na platformie Azure dla aplikacji produkcyjnych, należy przeanalizować różnice w możliwościach i wydajności podczas korzystania z interfejsu API mongodb, aby uzyskać dostęp do baz danych usługi Azure Cosmos DB w porównaniu z przy użyciu natywnego interfejsu API usługi Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="2c5fa-169">However, if you planning to use MongoDB API to access Azure Cosmos DB in Azure for production applications, you should analyze the differences in capabilities and performance when using MongoDB API to access Azure Cosmos DB databases compared to using the native Azure Cosmos DB API.</span></span> <span data-ttu-id="2c5fa-170">Jeśli jest podobny, możesz użyć interfejsu API MongoDB i uzyskać korzyści z obsługi dwóch aparatów bazy danych NoSQL w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="2c5fa-170">If it is similar you can use MongoDB API and you get the benefit of supporting two NoSQL database engines at the same time.</span></span>

<span data-ttu-id="2c5fa-171">Klastry MongoDB można również użyć jako produkcyjnej bazy danych w chmurze platformy Azure, również z [usługą MongoDB Azure Service.](https://www.mongodb.com/scale/mongodb-azure-service)</span><span class="sxs-lookup"><span data-stu-id="2c5fa-171">You could also use MongoDB clusters as the production database in Azure's cloud, too, with [MongoDB Azure Service](https://www.mongodb.com/scale/mongodb-azure-service).</span></span> <span data-ttu-id="2c5fa-172">Ale to nie jest usługa PaaS świadczona przez firmę Microsoft.</span><span class="sxs-lookup"><span data-stu-id="2c5fa-172">But that is not a PaaS service provided by Microsoft.</span></span> <span data-ttu-id="2c5fa-173">W takim przypadku platforma Azure jest po prostu hosting tego rozwiązania pochodzących z MongoDB.</span><span class="sxs-lookup"><span data-stu-id="2c5fa-173">In this case, Azure is just hosting that solution coming from MongoDB.</span></span>

<span data-ttu-id="2c5fa-174">Zasadniczo jest to tylko zastrzeżenie stwierdzające, że nie zawsze należy używać interfejsu API MongoDB przeciwko usłudze Azure Cosmos DB, tak jak to miało miejsce w eShopOnContainers, ponieważ był to wygodny wybór dla kontenerów systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="2c5fa-174">Basically, this is just a disclaimer stating that you shouldn't always use MongoDB API against Azure Cosmos DB, as we did in eShopOnContainers because it was a convenient choice for Linux containers.</span></span> <span data-ttu-id="2c5fa-175">Decyzja powinna być oparta na konkretnych potrzebach i testach, które należy wykonać dla aplikacji produkcyjnej.</span><span class="sxs-lookup"><span data-stu-id="2c5fa-175">The decision should be based on the specific needs and tests you need to do for your production application.</span></span>

### <a name="the-code-use-mongodb-api-in-net-core-applications"></a><span data-ttu-id="2c5fa-176">Kod: Użyj interfejsu API MongoDB w aplikacjach .NET Core</span><span class="sxs-lookup"><span data-stu-id="2c5fa-176">The code: Use MongoDB API in .NET Core applications</span></span>

<span data-ttu-id="2c5fa-177">Interfejs API mongodb dla platformy .NET jest oparty na pakietach NuGet, które należy dodać do projektów, na przykład w projekcie Locations.API pokazanym na poniższym rysunku.</span><span class="sxs-lookup"><span data-stu-id="2c5fa-177">MongoDB API for .NET is based on NuGet packages that you need to add to your projects, like in the Locations.API project shown in the following figure.</span></span>

![Zrzut ekranu przedstawiający zależności w pakietach MongoDB NuGet.](./media/nosql-database-persistence-infrastructure/mongodb-api-nuget-packages.png)

<span data-ttu-id="2c5fa-179">**Rysunek 7-22**.</span><span class="sxs-lookup"><span data-stu-id="2c5fa-179">**Figure 7-22**.</span></span> <span data-ttu-id="2c5fa-180">Odwołania do pakietów NuGet interfejsu API mongodb w projekcie .NET Core</span><span class="sxs-lookup"><span data-stu-id="2c5fa-180">MongoDB API NuGet packages references in a .NET Core project</span></span>

<span data-ttu-id="2c5fa-181">Zbadajmy kod w poniższych sekcjach.</span><span class="sxs-lookup"><span data-stu-id="2c5fa-181">Let's investigate the code in the following sections.</span></span>

#### <a name="a-model-used-by-mongodb-api"></a><span data-ttu-id="2c5fa-182">Model używany przez interfejs API MongoDB</span><span class="sxs-lookup"><span data-stu-id="2c5fa-182">A Model used by MongoDB API</span></span>

<span data-ttu-id="2c5fa-183">Najpierw należy zdefiniować model, który będzie przechowywać dane pochodzące z bazy danych w pamięci aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2c5fa-183">First, you need to define a model that will hold the data coming from the database in your application's memory space.</span></span> <span data-ttu-id="2c5fa-184">Oto przykład modelu używanego dla lokalizacji w eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="2c5fa-184">Here's an example of the model used for Locations at eShopOnContainers.</span></span>

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

<span data-ttu-id="2c5fa-185">Widać, że istnieje kilka atrybutów i typów pochodzących z pakietów MongoDB NuGet.</span><span class="sxs-lookup"><span data-stu-id="2c5fa-185">You can see there are a few attributes and types coming from the MongoDB NuGet packages.</span></span>

<span data-ttu-id="2c5fa-186">Bazy danych NoSQL są zwykle bardzo dobrze przystosowane do pracy z nierelacyjnymi danymi hierarchicznymi.</span><span class="sxs-lookup"><span data-stu-id="2c5fa-186">NoSQL databases are usually very well suited for working with non-relational hierarchical data.</span></span> <span data-ttu-id="2c5fa-187">W tym przykładzie używamy typów MongoDB specjalnie dla `GeoJson2DGeographicCoordinates`lokalizacji geograficznych, takich jak .</span><span class="sxs-lookup"><span data-stu-id="2c5fa-187">In this example, we are using MongoDB types especially made for geo-locations, like `GeoJson2DGeographicCoordinates`.</span></span>

#### <a name="retrieve-the-database-and-the-collection"></a><span data-ttu-id="2c5fa-188">Pobieranie bazy danych i kolekcji</span><span class="sxs-lookup"><span data-stu-id="2c5fa-188">Retrieve the database and the collection</span></span>

<span data-ttu-id="2c5fa-189">W eShopOnContainers utworzyliśmy niestandardowy kontekst bazy danych, w którym implementujemy kod do pobierania bazy danych i MongoCollections, jak w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="2c5fa-189">In eShopOnContainers, we have created a custom database context where we implement the code to retrieve the database and the MongoCollections, as in the following code.</span></span>

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

#### <a name="retrieve-the-data"></a><span data-ttu-id="2c5fa-190">Pobieranie danych</span><span class="sxs-lookup"><span data-stu-id="2c5fa-190">Retrieve the data</span></span>

<span data-ttu-id="2c5fa-191">W kodzie języka C#, takich jak kontrolery interfejsu API sieci Web lub implementacji repozytoriów niestandardowych, można napisać podobny kod do następujących podczas wykonywania zapytań za pośrednictwem interfejsu API mongodb.</span><span class="sxs-lookup"><span data-stu-id="2c5fa-191">In C# code, like Web API controllers or custom Repositories implementation, you can write similar code to the following when querying through the MongoDB API.</span></span> <span data-ttu-id="2c5fa-192">Należy zauważyć, że `_context` obiekt jest `LocationsContext` wystąpieniem poprzedniej klasy.</span><span class="sxs-lookup"><span data-stu-id="2c5fa-192">Note that the `_context` object is an instance of the previous `LocationsContext` class.</span></span>

```csharp
public async Task<Locations> GetAsync(int locationId)
{
    var filter = Builders<Locations>.Filter.Eq("LocationId", locationId);
    return await _context.Locations
                            .Find(filter)
                            .FirstOrDefaultAsync();
}
```

#### <a name="use-an-env-var-in-the-docker-composeoverrideyml-file-for-the-mongodb-connection-string"></a><span data-ttu-id="2c5fa-193">Użyj env-var w pliku docker-compose.override.yml dla ciągu połączenia mongodb</span><span class="sxs-lookup"><span data-stu-id="2c5fa-193">Use an env-var in the docker-compose.override.yml file for the MongoDB connection string</span></span>

<span data-ttu-id="2c5fa-194">Podczas tworzenia obiektu MongoClient, potrzebuje parametru fundamentalnego, `ConnectionString` który jest dokładnie parametr wskazujący na właściwą bazę danych.</span><span class="sxs-lookup"><span data-stu-id="2c5fa-194">When creating a MongoClient object, it needs a fundamental parameter which is precisely the `ConnectionString` parameter pointing to the right database.</span></span> <span data-ttu-id="2c5fa-195">W przypadku eShopOnContainers parametry połączenia można wskazać lokalnego kontenera platformy Docker MongoDB lub do "produkcyjnej" bazy danych usługi Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="2c5fa-195">In the case of eShopOnContainers, the connection string can point to a local MongoDB Docker container or to a "production" Azure Cosmos DB database.</span></span>  <span data-ttu-id="2c5fa-196">Ten ciąg połączenia pochodzi ze zmiennych `docker-compose.override.yml` środowiskowych zdefiniowanych w plikach używanych podczas wdrażania za pomocą docker-compose lub Visual Studio, jak w poniższym kodzie yml.</span><span class="sxs-lookup"><span data-stu-id="2c5fa-196">That connection string comes from the environment variables defined in the `docker-compose.override.yml` files used when deploying with docker-compose or Visual Studio, as in the following yml code.</span></span>

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

<span data-ttu-id="2c5fa-197">Zmienna środowiskowa jest rozpoznawana `ESHOP_AZURE_COSMOSDB` w ten sposób: `.env` Jeśli zmienna globalna `ConnectionString` jest zdefiniowana w pliku z ciągiem połączenia usługi Azure Cosmos DB, użyje jej do uzyskania dostępu do bazy danych usługi Azure Cosmos DB w chmurze.</span><span class="sxs-lookup"><span data-stu-id="2c5fa-197">The `ConnectionString` environment variable is resolved this way: If the `ESHOP_AZURE_COSMOSDB` global variable is defined in the `.env` file with the Azure Cosmos DB connection string, it will use it to access the Azure Cosmos DB database in the cloud.</span></span> <span data-ttu-id="2c5fa-198">Jeśli nie jest zdefiniowany, zajmie `mongodb://nosqldata` wartość i użyje deweloperskiego kontenera MongoDB.</span><span class="sxs-lookup"><span data-stu-id="2c5fa-198">If it’s not defined, it will take the `mongodb://nosqldata` value and use the development MongoDB container.</span></span>

<span data-ttu-id="2c5fa-199">Poniższy kod `.env` przedstawia plik z globalną zmienną środowiska parametry połączenia usługi Azure Cosmos DB, zgodnie z implementacji w eShopOnContainers:</span><span class="sxs-lookup"><span data-stu-id="2c5fa-199">The following code shows the `.env` file with the Azure Cosmos DB connection string global environment variable, as implemented in eShopOnContainers:</span></span>

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

<span data-ttu-id="2c5fa-200">Odkomentuj wiersz ESHOP_AZURE_COSMOSDB i zaktualizuj ją za pomocą ciągu połączenia usługi Azure Cosmos DB uzyskanego z portalu Azure, jak wyjaśniono w [temacie Połącz aplikację MongoDB z usługą Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account).</span><span class="sxs-lookup"><span data-stu-id="2c5fa-200">Uncomment the ESHOP_AZURE_COSMOSDB line and update it with your Azure Cosmos DB connection string obtained from the Azure portal as explained in [Connect a MongoDB application to Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account).</span></span>

<span data-ttu-id="2c5fa-201">Jeśli `ESHOP_AZURE_COSMOSDB` zmienna globalna jest pusta, co `.env` oznacza, że jest komentowana w pliku, kontener używa domyślnego ciągu połączenia MongoDB.</span><span class="sxs-lookup"><span data-stu-id="2c5fa-201">If the `ESHOP_AZURE_COSMOSDB` global variable is empty, meaning it's commented out in the `.env` file, then the container uses a default MongoDB connection string.</span></span> <span data-ttu-id="2c5fa-202">Ten ciąg połączenia wskazuje na lokalny kontener MongoDB wdrożony w `nosqldata` eShopOnContainers, który jest nazwany i został zdefiniowany w pliku docker-compose, jak pokazano w następującym kodzie .yml:</span><span class="sxs-lookup"><span data-stu-id="2c5fa-202">This connection string points to the local MongoDB container deployed in eShopOnContainers that is named `nosqldata` and was defined at the docker-compose file, as shown in the following .yml code:</span></span>

``` yml
# docker-compose.yml
version: '3.4'
services:
  # ...Other services...
  nosqldata:
    image: mongo
```

#### <a name="additional-resources"></a><span data-ttu-id="2c5fa-203">Zasoby dodatkowe</span><span class="sxs-lookup"><span data-stu-id="2c5fa-203">Additional resources</span></span>

- <span data-ttu-id="2c5fa-204">**Modelowanie danych dokumentu dla baz danych NoSQL** </span><span class="sxs-lookup"><span data-stu-id="2c5fa-204">**Modeling document data for NoSQL databases** </span></span>\
  <https://docs.microsoft.com/azure/cosmos-db/modeling-data>

- <span data-ttu-id="2c5fa-205">**Vaughn Vernon. Idealny sklep z agregatami projektów opartych na domenie?**</span><span class="sxs-lookup"><span data-stu-id="2c5fa-205">**Vaughn Vernon. The Ideal Domain-Driven Design Aggregate Store?**</span></span> \
  <https://kalele.io/blog-posts/the-ideal-domain-driven-design-aggregate-store/>

- <span data-ttu-id="2c5fa-206">**Wprowadzenie do usługi Azure Cosmos DB: INTERFEJS API dla mongodb**  </span><span class="sxs-lookup"><span data-stu-id="2c5fa-206">**Introduction to Azure Cosmos DB: API for MongoDB**  </span></span>\
  <https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction>

- <span data-ttu-id="2c5fa-207">**Usługa Azure Cosmos DB: Tworzenie aplikacji sieci Web interfejsu API witryny MongoDB za pomocą platformy .NET i portalu Azure**  </span><span class="sxs-lookup"><span data-stu-id="2c5fa-207">**Azure Cosmos DB: Build a MongoDB API web app with .NET and the Azure portal**  </span></span>\
  <https://docs.microsoft.com/azure/cosmos-db/create-mongodb-dotnet>

- <span data-ttu-id="2c5fa-208">**Użyj emulatora usługi Azure Cosmos DB do lokalnego rozwoju i testowania**  </span><span class="sxs-lookup"><span data-stu-id="2c5fa-208">**Use the Azure Cosmos DB Emulator for local development and testing**  </span></span>\
  <https://docs.microsoft.com/azure/cosmos-db/local-emulator>

- <span data-ttu-id="2c5fa-209">**Łączenie aplikacji MongoDB z usługą Azure Cosmos DB**  </span><span class="sxs-lookup"><span data-stu-id="2c5fa-209">**Connect a MongoDB application to Azure Cosmos DB**  </span></span>\
  <https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account>

- <span data-ttu-id="2c5fa-210">**Obraz platformy Dokatora emulatora bazy danych usługi Cosmos (kontener systemu Windows)**  </span><span class="sxs-lookup"><span data-stu-id="2c5fa-210">**The Cosmos DB Emulator Docker image (Windows Container)**  </span></span>\
  <https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator/>

- <span data-ttu-id="2c5fa-211">**Obraz platformy MongoDB Docker (Linux i Windows Container)**  </span><span class="sxs-lookup"><span data-stu-id="2c5fa-211">**The MongoDB Docker image (Linux and Windows Container)**  </span></span>\
  <https://hub.docker.com/_/mongo/>

- <span data-ttu-id="2c5fa-212">**Korzystanie z usługi MongoChef (Studio 3T) z usługą Azure Cosmos DB: API dla konta MongoDB**  </span><span class="sxs-lookup"><span data-stu-id="2c5fa-212">**Use MongoChef (Studio 3T) with an Azure Cosmos DB: API for MongoDB account**  </span></span>\
  <https://docs.microsoft.com/azure/cosmos-db/mongodb-mongochef>

>[!div class="step-by-step"]
><span data-ttu-id="2c5fa-213">[Poprzedni](infrastructure-persistence-layer-implemenation-entity-framework-core.md)
>[następny](microservice-application-layer-web-api-design.md)</span><span class="sxs-lookup"><span data-stu-id="2c5fa-213">[Previous](infrastructure-persistence-layer-implemenation-entity-framework-core.md)
[Next](microservice-application-layer-web-api-design.md)</span></span>
