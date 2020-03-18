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
# <a name="use-nosql-databases-as-a-persistence-infrastructure"></a><span data-ttu-id="6a403-103">Używanie baz danych NoSQL jako infrastruktury trwałości</span><span class="sxs-lookup"><span data-stu-id="6a403-103">Use NoSQL databases as a persistence infrastructure</span></span>

<span data-ttu-id="6a403-104">Korzystając z baz danych NoSQL dla warstwy danych infrastruktury, zazwyczaj nie używasz ORM jak Entity Framework Core.</span><span class="sxs-lookup"><span data-stu-id="6a403-104">When you use NoSQL databases for your infrastructure data tier, you typically do not use an ORM like Entity Framework Core.</span></span> <span data-ttu-id="6a403-105">Zamiast tego używasz interfejsu API dostarczonego przez aparat NoSQL, takich jak Azure Cosmos DB, MongoDB, Cassandra, RavenDB, CouchDB lub Tabele magazynu Azure.</span><span class="sxs-lookup"><span data-stu-id="6a403-105">Instead you use the API provided by the NoSQL engine, such as Azure Cosmos DB, MongoDB, Cassandra, RavenDB, CouchDB, or Azure Storage Tables.</span></span>

<span data-ttu-id="6a403-106">Jednak w przypadku korzystania z bazy danych NoSQL, zwłaszcza bazy danych zorientowanych na dokumenty, takich jak Azure Cosmos DB, CouchDB lub RavenDB, sposób projektowania modelu za pomocą agregatów DDD jest częściowo podobny do sposobu, w jaki można to zrobić w EF Core, w odniesieniu do identyfikacji zagregowane katalogi główne, klasy jednostek podrzędnych i klasy obiektów wartości.</span><span class="sxs-lookup"><span data-stu-id="6a403-106">However, when you use a NoSQL database, especially a document-oriented database like Azure Cosmos DB, CouchDB, or RavenDB, the way you design your model with DDD aggregates is partially similar to how you can do it in EF Core, in regards to the identification of aggregate roots, child entity classes, and value object classes.</span></span> <span data-ttu-id="6a403-107">Ale ostatecznie wybór bazy danych wpłynie na projekt.</span><span class="sxs-lookup"><span data-stu-id="6a403-107">But, ultimately, the database selection will impact in your design.</span></span>

<span data-ttu-id="6a403-108">Korzystając z bazy danych zorientowanej na dokument, należy zaimplementować agregacji jako pojedynczy dokument, serializowany w JSON lub w innym formacie.</span><span class="sxs-lookup"><span data-stu-id="6a403-108">When you use a document-oriented database, you implement an aggregate as a single document, serialized in JSON or another format.</span></span> <span data-ttu-id="6a403-109">Jednak użycie bazy danych jest nieprzezroczyste z punktu widzenia kodu modelu domeny.</span><span class="sxs-lookup"><span data-stu-id="6a403-109">However, the use of the database is transparent from a domain model code point of view.</span></span> <span data-ttu-id="6a403-110">Korzystając z bazy danych NoSQL, nadal używasz klas jednostek i klas głównych agregacji, ale z większą elastycznością niż podczas korzystania z EF Core, ponieważ trwałość nie jest relacyjna.</span><span class="sxs-lookup"><span data-stu-id="6a403-110">When using a NoSQL database, you still are using entity classes and aggregate root classes, but with more flexibility than when using EF Core because the persistence is not relational.</span></span>

<span data-ttu-id="6a403-111">Różnica polega na tym, jak utrwalić tego modelu.</span><span class="sxs-lookup"><span data-stu-id="6a403-111">The difference is in how you persist that model.</span></span> <span data-ttu-id="6a403-112">Jeśli zaimplementowano model domeny na podstawie klas jednostek POCO, agnostyk do trwałości infrastruktury, może to wyglądać, że można przenieść do innej infrastruktury trwałości, nawet z relacyjnych do NoSQL.</span><span class="sxs-lookup"><span data-stu-id="6a403-112">If you implemented your domain model based on POCO entity classes, agnostic to the infrastructure persistence, it might look like you could move to a different persistence infrastructure, even from relational to NoSQL.</span></span> <span data-ttu-id="6a403-113">Jednak to nie powinno być twoim celem.</span><span class="sxs-lookup"><span data-stu-id="6a403-113">However, that should not be your goal.</span></span> <span data-ttu-id="6a403-114">Zawsze istnieją ograniczenia i kompromisy w różnych technologiach bazy danych, więc nie będzie można mieć tego samego modelu dla relacyjnych lub nosql baz danych.</span><span class="sxs-lookup"><span data-stu-id="6a403-114">There are always constraints and trade-offs in the different database technologies, so you will not be able to have the same model for relational or NoSQL databases.</span></span> <span data-ttu-id="6a403-115">Zmiana modeli trwałości nie jest zadaniem trywialnym, ponieważ transakcje i operacje trwałości będą bardzo różne.</span><span class="sxs-lookup"><span data-stu-id="6a403-115">Changing persistence models is not a trivial task, because transactions and persistence operations will be very different.</span></span>

<span data-ttu-id="6a403-116">Na przykład w bazie danych zorientowanych na dokument jest w porządku dla katalogu głównego agregacji mieć wiele właściwości kolekcji podrzędnej.</span><span class="sxs-lookup"><span data-stu-id="6a403-116">For example, in a document-oriented database, it is okay for an aggregate root to have multiple child collection properties.</span></span> <span data-ttu-id="6a403-117">W relacyjnej bazie danych wykonywanie zapytań dotyczących wielu właściwości kolekcji podrzędnych nie jest łatwo zoptymalizowane, ponieważ otrzymasz instrukcję UNION ALL SQL z powrotem z EF.</span><span class="sxs-lookup"><span data-stu-id="6a403-117">In a relational database, querying multiple child collection properties is not easily optimized, because you get a UNION ALL SQL statement back from EF.</span></span> <span data-ttu-id="6a403-118">Posiadanie tego samego modelu domeny dla relacyjnych baz danych lub baz danych NoSQL nie jest proste i nie należy próbować tego robić.</span><span class="sxs-lookup"><span data-stu-id="6a403-118">Having the same domain model for relational databases or NoSQL databases is not simple, and you should not try to do it.</span></span> <span data-ttu-id="6a403-119">Naprawdę trzeba zaprojektować model ze zrozumieniem, jak dane będą używane w każdej określonej bazie danych.</span><span class="sxs-lookup"><span data-stu-id="6a403-119">You really have to design your model with an understanding of how the data is going to be used in each particular database.</span></span>

<span data-ttu-id="6a403-120">Korzyścią podczas korzystania z baz danych NoSQL jest to, że jednostki są bardziej zdenormalizowane, więc nie można ustawić mapowanie tabeli.</span><span class="sxs-lookup"><span data-stu-id="6a403-120">A benefit when using NoSQL databases is that the entities are more denormalized, so you do not set a table mapping.</span></span> <span data-ttu-id="6a403-121">Model domeny może być bardziej elastyczny niż w przypadku korzystania z relacyjnej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="6a403-121">Your domain model can be more flexible than when using a relational database.</span></span>

<span data-ttu-id="6a403-122">Podczas projektowania modelu domeny na podstawie agregacji przejście do bazy danych NoSQL i zorientowanych na dokumenty może być jeszcze łatwiejsze niż przy użyciu relacyjnej bazy danych, ponieważ agregaty, które projektujesz, są podobne do dokumentów seryjnych w bazie danych zorientowanych na dokumenty.</span><span class="sxs-lookup"><span data-stu-id="6a403-122">When you design your domain model based on aggregates, moving to NoSQL and document-oriented databases might be even easier than using a relational database, because the aggregates you design are similar to serialized documents in a document-oriented database.</span></span> <span data-ttu-id="6a403-123">Następnie można dołączyć do tych "worków" wszystkie informacje, które mogą być potrzebne do tego agregacji.</span><span class="sxs-lookup"><span data-stu-id="6a403-123">Then you can include in those “bags” all the information you might need for that aggregate.</span></span>

<span data-ttu-id="6a403-124">Na przykład następujący kod JSON jest przykładową implementacją agregacji zamówienia podczas korzystania z bazy danych zorientowanej na dokument.</span><span class="sxs-lookup"><span data-stu-id="6a403-124">For instance, the following JSON code is a sample implementation of an order aggregate when using a document-oriented database.</span></span> <span data-ttu-id="6a403-125">Jest on podobny do agregacji zamówienia zaimplementowaliśmy w eShopOnContainers próbki, ale bez użycia EF Core pod spodem.</span><span class="sxs-lookup"><span data-stu-id="6a403-125">It is similar to the order aggregate we implemented in the eShopOnContainers sample, but without using EF Core underneath.</span></span>

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

## <a name="introduction-to-azure-cosmos-db-and-the-native-cosmos-db-api"></a><span data-ttu-id="6a403-126">Wprowadzenie do usługi Azure Cosmos DB i natywnego interfejsu API usługi Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="6a403-126">Introduction to Azure Cosmos DB and the native Cosmos DB API</span></span>

<span data-ttu-id="6a403-127">[Usługa Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction) to globalnie rozproszona usługa bazy danych firmy Microsoft dla aplikacji o znaczeniu krytycznym.</span><span class="sxs-lookup"><span data-stu-id="6a403-127">[Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction) is Microsoft's globally distributed database service for mission-critical applications.</span></span> <span data-ttu-id="6a403-128">Usługa Azure Cosmos DB zapewnia [kompleksową globalną dystrybucję](https://docs.microsoft.com/azure/cosmos-db/distribute-data-globally), [elastyczne skalowanie przepływności i pamięci](https://docs.microsoft.com/azure/cosmos-db/partition-data) w skali globalnej, milisekundowe opóźnienia w 99. percentylu, [pięć odpowiednio zdefiniowanych poziomów spójności](https://docs.microsoft.com/azure/cosmos-db/consistency-levels) oraz gwarantowaną wysoką dostępność, wspierane przez [wiodące w branży umowy SLA](https://azure.microsoft.com/support/legal/sla/cosmos-db/).</span><span class="sxs-lookup"><span data-stu-id="6a403-128">Azure Cosmos DB provides [turn-key global distribution](https://docs.microsoft.com/azure/cosmos-db/distribute-data-globally), [elastic scaling of throughput and storage](https://docs.microsoft.com/azure/cosmos-db/partition-data) worldwide, single-digit millisecond latencies at the 99th percentile, [five well-defined consistency levels](https://docs.microsoft.com/azure/cosmos-db/consistency-levels), and guaranteed high availability, all backed by [industry-leading SLAs](https://azure.microsoft.com/support/legal/sla/cosmos-db/).</span></span> <span data-ttu-id="6a403-129">Usługa Azure Cosmos DB [automatycznie indeksuje dane](https://www.vldb.org/pvldb/vol8/p1668-shukla.pdf) bez konieczności zarządzania schematami i indeksami.</span><span class="sxs-lookup"><span data-stu-id="6a403-129">Azure Cosmos DB [automatically indexes data](https://www.vldb.org/pvldb/vol8/p1668-shukla.pdf) without requiring you to deal with schema and index management.</span></span> <span data-ttu-id="6a403-130">To usługa wielomodelowa, obsługująca modele oparte na dokumentach, parach klucz-wartość, grafach i kolumnach.</span><span class="sxs-lookup"><span data-stu-id="6a403-130">It is multi-model and supports document, key-value, graph, and columnar data models.</span></span>

![Diagram przedstawiający globalną dystrybucję usługi Azure Cosmos DB.](./media/nosql-database-persistence-infrastructure/azure-cosmos-db-global-distribution.png)

<span data-ttu-id="6a403-132">**Rysunek 7-19**.</span><span class="sxs-lookup"><span data-stu-id="6a403-132">**Figure 7-19**.</span></span> <span data-ttu-id="6a403-133">Globalna dystrybucja usługi Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="6a403-133">Azure Cosmos DB global distribution</span></span>

<span data-ttu-id="6a403-134">Korzystając z modelu\# C do zaimplementowania agregacji do użycia przez interfejs API usługi\# Azure Cosmos DB, agregacji może być podobny do klas POCO C używane z EF Core.</span><span class="sxs-lookup"><span data-stu-id="6a403-134">When you use a C\# model to implement the aggregate to be used by the Azure Cosmos DB API, the aggregate can be similar to the C\# POCO classes used with EF Core.</span></span> <span data-ttu-id="6a403-135">Różnica polega na sposobie ich używania z warstw aplikacji i infrastruktury, jak w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="6a403-135">The difference is in the way to use them from the application and infrastructure layers, as in the following code:</span></span>

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

<span data-ttu-id="6a403-136">Można zobaczyć, że sposób pracy z modelem domeny może być podobny do sposobu, w jaki używasz go w warstwie modelu domeny, gdy infrastruktura jest EF.</span><span class="sxs-lookup"><span data-stu-id="6a403-136">You can see that the way you work with your domain model can be similar to the way you use it in your domain model layer when the infrastructure is EF.</span></span> <span data-ttu-id="6a403-137">Nadal używasz tych samych metod root agregacji, aby zapewnić spójność, invariants i sprawdzania poprawności w agregacji.</span><span class="sxs-lookup"><span data-stu-id="6a403-137">You still use the same aggregate root methods to ensure consistency, invariants, and validations within the aggregate.</span></span>

<span data-ttu-id="6a403-138">Jednak po utrwalić modelu do bazy danych NoSQL, kod i interfejs API zmieniają się dramatycznie w porównaniu do kodu EF Core lub innego kodu związanego z relacyjnych baz danych.</span><span class="sxs-lookup"><span data-stu-id="6a403-138">However, when you persist your model into the NoSQL database, the code and API change dramatically compared to EF Core code or any other code related to relational databases.</span></span>

## <a name="implement-net-code-targeting-mongodb-and-azure-cosmos-db"></a><span data-ttu-id="6a403-139">Implementowanie kodu .NET dla usługi MongoDB i usługi Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="6a403-139">Implement .NET code targeting MongoDB and Azure Cosmos DB</span></span>

### <a name="use-azure-cosmos-db-from-net-containers"></a><span data-ttu-id="6a403-140">Korzystanie z usługi Azure Cosmos DB z kontenerów platformy .NET</span><span class="sxs-lookup"><span data-stu-id="6a403-140">Use Azure Cosmos DB from .NET containers</span></span>

<span data-ttu-id="6a403-141">Dostęp do baz danych usługi Azure Cosmos DB można uzyskać z kodu .NET działającego w kontenerach, podobnie jak z dowolnej innej aplikacji .NET.</span><span class="sxs-lookup"><span data-stu-id="6a403-141">You can access Azure Cosmos DB databases from .NET code running in containers, like from any other .NET application.</span></span> <span data-ttu-id="6a403-142">Na przykład locations.API i Marketing.API mikrousług w eShopOnContainers są implementowane, dzięki czemu mogą korzystać z baz danych usługi Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="6a403-142">For instance, the Locations.API and Marketing.API microservices in eShopOnContainers are implemented so they can consume Azure Cosmos DB databases.</span></span>

<span data-ttu-id="6a403-143">Istnieje jednak ograniczenie w usłudze Azure Cosmos DB z punktu widzenia środowiska programistycznego platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="6a403-143">However, there’s a limitation in Azure Cosmos DB from a Docker development environment point of view.</span></span> <span data-ttu-id="6a403-144">Mimo że istnieje lokalny [emulator usługi Azure Cosmos DB,](https://docs.microsoft.com/azure/cosmos-db/local-emulator) który można uruchomić na komputerze deweloperskim, obsługuje tylko system Windows.</span><span class="sxs-lookup"><span data-stu-id="6a403-144">Even though there’s an on-premises [Azure Cosmos DB Emulator](https://docs.microsoft.com/azure/cosmos-db/local-emulator) that can run in a local development machine, it only supports Windows.</span></span> <span data-ttu-id="6a403-145">Systemy Linux i macOS nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="6a403-145">Linux and macOS aren't supported.</span></span>

<span data-ttu-id="6a403-146">Istnieje również możliwość uruchomienia tego emulatora na platformie Docker, ale tylko w kontenerach systemu Windows, a nie z kontenerami systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="6a403-146">There's also the possibility to run this emulator on Docker, but just on Windows Containers, not with Linux Containers.</span></span> <span data-ttu-id="6a403-147">Jest to początkowe utrudnienie dla środowiska programistycznego, jeśli aplikacja jest wdrażana jako kontenery systemu Linux, ponieważ obecnie nie można wdrożyć kontenerów systemu Linux i Windows na platformie Docker dla systemu Windows w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="6a403-147">That's an initial handicap for the development environment if your application is deployed as Linux containers, since, currently, you can't deploy Linux and Windows Containers on Docker for Windows at the same time.</span></span> <span data-ttu-id="6a403-148">Wszystkie kontenery wdrażane muszą być dla systemu Linux lub windows.</span><span class="sxs-lookup"><span data-stu-id="6a403-148">Either all containers being deployed have to be for Linux or for Windows.</span></span>

<span data-ttu-id="6a403-149">Idealne i bardziej proste wdrożenie dla rozwiązania dewelopera/testu jest możliwość wdrażania systemów baz danych jako kontenerów wraz z kontenerów niestandardowych, dzięki czemu środowiska deweloperów/testów są zawsze spójne.</span><span class="sxs-lookup"><span data-stu-id="6a403-149">The ideal and more straightforward deployment for a dev/test solution is to be able to deploy your database systems as containers along with your custom containers so your dev/test environments are always consistent.</span></span>

### <a name="use-mongodb-api-for-local-devtest-linuxwindows-containers-plus-azure-cosmos-db"></a><span data-ttu-id="6a403-150">Użyj interfejsu API MongoDB dla lokalnych kontenerów deweloperskich/testowych systemu Linux/Windows oraz usługi Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="6a403-150">Use MongoDB API for local dev/test Linux/Windows containers plus Azure Cosmos DB</span></span>

<span data-ttu-id="6a403-151">Bazy danych usługi Cosmos DB obsługują interfejs API MongoDB dla .NET, a także natywny protokół przewodowy MongoDB.</span><span class="sxs-lookup"><span data-stu-id="6a403-151">Cosmos DB databases support MongoDB API for .NET as well as the native MongoDB wire protocol.</span></span> <span data-ttu-id="6a403-152">Oznacza to, że przy użyciu istniejących sterowników, aplikacja napisana dla MongoDB może teraz komunikować się z usługą Cosmos DB i używać baz danych usługi Cosmos DB zamiast baz danych MongoDB, jak pokazano na rysunku 7-20.</span><span class="sxs-lookup"><span data-stu-id="6a403-152">This means that by using existing drivers, your application written for MongoDB can now communicate with Cosmos DB and use Cosmos DB databases instead of MongoDB databases, as shown in Figure 7-20.</span></span>

![Diagram pokazujący, że usługa Cosmos DB obsługuje protokół drutu .NET i MongoDB.](./media/nosql-database-persistence-infrastructure/mongodb-api-wire-protocol.png)

<span data-ttu-id="6a403-154">**Rysunek 7-20**.</span><span class="sxs-lookup"><span data-stu-id="6a403-154">**Figure 7-20**.</span></span> <span data-ttu-id="6a403-155">Korzystanie z interfejsu API i protokołu MongoDB w celu uzyskania dostępu do usługi Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="6a403-155">Using MongoDB API and protocol to access Azure Cosmos DB</span></span>

<span data-ttu-id="6a403-156">Jest to bardzo wygodne podejście do sprawdzania pojęć w środowiskach platformy Docker z kontenerami systemu Linux, ponieważ [obraz docker MongoDB](https://hub.docker.com/r/_/mongo/) jest obrazem wielołukowym obsługującym kontenery docker Linux i kontenery systemu Windows platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="6a403-156">This is a very convenient approach for proof of concepts in Docker environments with Linux containers because the [MongoDB Docker image](https://hub.docker.com/r/_/mongo/) is a multi-arch image that supports Docker Linux containers and Docker Windows containers.</span></span>

<span data-ttu-id="6a403-157">Jak pokazano na poniższej ilustracji, przy użyciu interfejsu API MongoDB, eShopOnContainers obsługuje kontenery MongoDB Linux i Windows dla lokalnego środowiska programistycznego, ale następnie można przejść do skalowalne, paas rozwiązanie w chmurze jako usługi Azure Cosmos DB, po prostu [zmieniając ciąg połączenia MongoDB do punktu usługi Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account).</span><span class="sxs-lookup"><span data-stu-id="6a403-157">As shown in the following image, by using the MongoDB API, eShopOnContainers supports MongoDB Linux and Windows containers for the local development environment but then, you can move to a scalable, PaaS cloud solution as Azure Cosmos DB by simply [changing the MongoDB connection string to point to Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account).</span></span>

![Diagram pokazujący, że mikrousługi lokalizacji w eShopOnContainers można użyć usługi Cosmos DB lub Mongo DB.](./media/nosql-database-persistence-infrastructure/eshoponcontainers-mongodb-containers.png)

<span data-ttu-id="6a403-159">**Rysunek 7-21**.</span><span class="sxs-lookup"><span data-stu-id="6a403-159">**Figure 7-21**.</span></span> <span data-ttu-id="6a403-160">eShopOnContainers przy użyciu kontenerów MongoDB dla dev-env lub usługi Azure Cosmos DB dla produkcji</span><span class="sxs-lookup"><span data-stu-id="6a403-160">eShopOnContainers using MongoDB containers for dev-env or Azure Cosmos DB for production</span></span>

<span data-ttu-id="6a403-161">Produkcyjne usługi Azure Cosmos DB będzie działać w chmurze platformy Azure jako PaaS i skalowalne usługi.</span><span class="sxs-lookup"><span data-stu-id="6a403-161">The production Azure Cosmos DB would be running in Azure’s cloud as a PaaS and scalable service.</span></span>

<span data-ttu-id="6a403-162">Niestandardowe kontenery .NET Core można uruchomić na lokalnym hoście platformy Docker rozwoju (który używa platformy Docker dla systemu Windows na komputerze z systemem Windows 10) lub być wdrożone w środowisku produkcyjnym, takich jak Kubernetes w usłudze Azure AKS lub sieci szkieletowej usług Azure.</span><span class="sxs-lookup"><span data-stu-id="6a403-162">Your custom .NET Core containers can run on a local development Docker host (that is using Docker for Windows in a Windows 10 machine) or be deployed into a production environment, like Kubernetes in Azure AKS or Azure Service Fabric.</span></span> <span data-ttu-id="6a403-163">W tym drugim środowisku można wdrożyć tylko kontenery niestandardowe .NET Core, ale nie kontener Akcjonord y dostępu do usługi MongoDB, ponieważ chcesz używać usługi Azure Cosmos DB w chmurze do obsługi danych w środowisku produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="6a403-163">In this second environment, you would deploy only the .NET Core custom containers but not the MongoDB container since you’d be using Azure Cosmos DB in the cloud for handling the data in production.</span></span>

<span data-ttu-id="6a403-164">Wyraźną zaletą korzystania z interfejsu API MongoDB jest to, że rozwiązanie może działać w obu aparatach baz danych, MongoDB lub usłudze Azure Cosmos DB, więc migracje do różnych środowisk powinny być łatwe.</span><span class="sxs-lookup"><span data-stu-id="6a403-164">A clear benefit of using the MongoDB API is that your solution could run in both database engines, MongoDB or Azure Cosmos DB, so migrations to different environments should be easy.</span></span> <span data-ttu-id="6a403-165">Jednak czasami warto użyć natywnego interfejsu API (który jest macierzystym interfejsem API usługi Cosmos DB), aby w pełni wykorzystać możliwości określonego aparatu bazy danych.</span><span class="sxs-lookup"><span data-stu-id="6a403-165">However, sometimes it is worthwhile to use a native API (that is the native Cosmos DB API) in order to take full advantage of the capabilities of a specific database engine.</span></span>

<span data-ttu-id="6a403-166">Aby uzyskać dalsze porównanie między po prostu przy użyciu usługi MongoDB i usługi Cosmos DB w chmurze, zobacz [korzyści z korzystania z usługi Azure Cosmos DB na tej stronie](https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction).</span><span class="sxs-lookup"><span data-stu-id="6a403-166">For further comparison between simply using MongoDB versus Cosmos DB in the cloud, see the [Benefits of using Azure Cosmos DB in this page](https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction).</span></span>

### <a name="analyze-your-approach-for-production-applications-mongodb-api-vs-cosmos-db-api"></a><span data-ttu-id="6a403-167">Analizuj swoje podejście do zastosowań produkcyjnych: Interfejs API MongoDB w porównaniu z interfejsem API usługi Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="6a403-167">Analyze your approach for production applications: MongoDB API vs. Cosmos DB API</span></span>

<span data-ttu-id="6a403-168">W eShopOnContainers używamy interfejsu API MongoDB, ponieważ naszym priorytetem było zasadniczo mieć spójne środowisko deweloperów/testów przy użyciu bazy danych NoSQL, która może również współpracować z usługi Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="6a403-168">In eShopOnContainers, we’re using MongoDB API because our priority was fundamentally to have a consistent dev/test environment using a NoSQL database that could also work with Azure Cosmos DB.</span></span>

<span data-ttu-id="6a403-169">Jeśli jednak planujesz użyć interfejsu API MongoDB do uzyskiwania dostępu do usługi Azure Cosmos DB na platformie Azure dla aplikacji produkcyjnych, należy przeanalizować różnice w możliwościach i wydajności podczas korzystania z interfejsu API MongoDB w celu uzyskania dostępu do baz danych usługi Azure Cosmos DB w porównaniu z użyciem natywnych Interfejs API usługi Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="6a403-169">However, if you planning to use MongoDB API to access Azure Cosmos DB in Azure for production applications, you should analyze the differences in capabilities and performance when using MongoDB API to access Azure Cosmos DB databases compared to using the native Azure Cosmos DB API.</span></span> <span data-ttu-id="6a403-170">Jeśli jest podobny, możesz użyć interfejsu API MongoDB i możesz korzystać z obsługi dwóch aparatów baz danych NoSQL w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="6a403-170">If it is similar you can use MongoDB API and you get the benefit of supporting two NoSQL database engines at the same time.</span></span>

<span data-ttu-id="6a403-171">Można również użyć klastrów MongoDB jako produkcyjnej bazy danych w chmurze platformy Azure, zbyt, z [MongoDB Usługi Azure](https://www.mongodb.com/scale/mongodb-azure-service).</span><span class="sxs-lookup"><span data-stu-id="6a403-171">You could also use MongoDB clusters as the production database in Azure’s cloud, too, with [MongoDB Azure Service](https://www.mongodb.com/scale/mongodb-azure-service).</span></span> <span data-ttu-id="6a403-172">Ale to nie jest usługa PaaS świadczona przez Firmę Microsoft.</span><span class="sxs-lookup"><span data-stu-id="6a403-172">But that is not a PaaS service provided by Microsoft.</span></span> <span data-ttu-id="6a403-173">W takim przypadku platforma Azure jest tylko hosting tego rozwiązania pochodzącego z MongoDB.</span><span class="sxs-lookup"><span data-stu-id="6a403-173">In this case, Azure is just hosting that solution coming from MongoDB.</span></span>

<span data-ttu-id="6a403-174">Zasadniczo jest to tylko zastrzeżenie stwierdzające, że nie zawsze należy używać interfejsu API MongoDB w usłudze Azure Cosmos DB, tak jak to miało miejsce w eShopOnContainers, ponieważ był to wygodny wybór dla kontenerów systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="6a403-174">Basically, this is just a disclaimer stating that you shouldn’t always use MongoDB API against Azure Cosmos DB, as we did in eShopOnContainers because it was a convenient choice for Linux containers.</span></span> <span data-ttu-id="6a403-175">Decyzja powinna być oparta na konkretnych potrzebach i testach, które należy wykonać dla aplikacji produkcyjnej.</span><span class="sxs-lookup"><span data-stu-id="6a403-175">The decision should be based on the specific needs and tests you need to do for your production application.</span></span>

### <a name="the-code-use-mongodb-api-in-net-core-applications"></a><span data-ttu-id="6a403-176">Kod: Użyj interfejsu API MongoDB w aplikacjach .NET Core</span><span class="sxs-lookup"><span data-stu-id="6a403-176">The code: Use MongoDB API in .NET Core applications</span></span>

<span data-ttu-id="6a403-177">Interfejs API MongoDB dla .NET jest oparty na pakietach NuGet, które należy dodać do projektów, takich jak w projekcie Locations.API pokazanym na poniższej stronie.</span><span class="sxs-lookup"><span data-stu-id="6a403-177">MongoDB API for .NET is based on NuGet packages that you need to add to your projects, like in the Locations.API project shown in the following figure.</span></span>

![Zrzut ekranu przedstawiający zależności w pakietach NuGet MongoDB.](./media/nosql-database-persistence-infrastructure/mongodb-api-nuget-packages.png)

<span data-ttu-id="6a403-179">**Rysunek 7-22**.</span><span class="sxs-lookup"><span data-stu-id="6a403-179">**Figure 7-22**.</span></span> <span data-ttu-id="6a403-180">Odwołania pakietów MongoDB API NuGet w projekcie .NET Core</span><span class="sxs-lookup"><span data-stu-id="6a403-180">MongoDB API NuGet packages references in a .NET Core project</span></span>

<span data-ttu-id="6a403-181">Zbadajmy kod w poniższych sekcjach.</span><span class="sxs-lookup"><span data-stu-id="6a403-181">Let's investigate the code in the following sections.</span></span>

#### <a name="a-model-used-by-mongodb-api"></a><span data-ttu-id="6a403-182">Model używany przez Interfejs API MongoDB</span><span class="sxs-lookup"><span data-stu-id="6a403-182">A Model used by MongoDB API</span></span>

<span data-ttu-id="6a403-183">Najpierw należy zdefiniować model, który będzie przechowywać dane pochodzące z bazy danych w przestrzeni pamięci aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6a403-183">First, you need to define a model that will hold the data coming from the database in your application’s memory space.</span></span> <span data-ttu-id="6a403-184">Oto przykład modelu używanego dla lokalizacji w eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="6a403-184">Here’s an example of the model used for Locations at eShopOnContainers.</span></span>

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

<span data-ttu-id="6a403-185">Możesz zobaczyć, że istnieje kilka atrybutów i typów pochodzących z pakietów NuGet MongoDB.</span><span class="sxs-lookup"><span data-stu-id="6a403-185">You can see there are a few attributes and types coming from the MongoDB NuGet packages.</span></span>

<span data-ttu-id="6a403-186">Bazy danych NoSQL są zwykle bardzo dobrze przystosowane do pracy z nierelacyjnymi danymi hierarchicznymi.</span><span class="sxs-lookup"><span data-stu-id="6a403-186">NoSQL databases are usually very well suited for working with non-relational hierarchical data.</span></span> <span data-ttu-id="6a403-187">W tym przykładzie używamy typów MongoDB specjalnie dla lokalizacji `GeoJson2DGeographicCoordinates`geograficznych, takich jak .</span><span class="sxs-lookup"><span data-stu-id="6a403-187">In this example, we are using MongoDB types especially made for geo-locations, like `GeoJson2DGeographicCoordinates`.</span></span>

#### <a name="retrieve-the-database-and-the-collection"></a><span data-ttu-id="6a403-188">Pobieranie bazy danych i kolekcji</span><span class="sxs-lookup"><span data-stu-id="6a403-188">Retrieve the database and the collection</span></span>

<span data-ttu-id="6a403-189">W eShopOnContainers utworzyliśmy kontekst niestandardowej bazy danych, w którym implementujemy kod do pobierania bazy danych i MongoCollections, jak w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="6a403-189">In eShopOnContainers, we have created a custom database context where we implement the code to retrieve the database and the MongoCollections, as in the following code.</span></span>

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

#### <a name="retrieve-the-data"></a><span data-ttu-id="6a403-190">Pobieranie danych</span><span class="sxs-lookup"><span data-stu-id="6a403-190">Retrieve the data</span></span>

<span data-ttu-id="6a403-191">W kodzie Języka C#, takich jak kontrolery interfejsu API sieci Web lub implementacja niestandardowych repozytoriów, można napisać podobny kod do następującego podczas wykonywania zapytań za pośrednictwem interfejsu API MongoDB.</span><span class="sxs-lookup"><span data-stu-id="6a403-191">In C# code, like Web API controllers or custom Repositories implementation, you can write similar code to the following when querying through the MongoDB API.</span></span> <span data-ttu-id="6a403-192">Należy zauważyć, że `_context` obiekt jest `LocationsContext` wystąpieniem poprzedniej klasy.</span><span class="sxs-lookup"><span data-stu-id="6a403-192">Note that the `_context` object is an instance of the previous `LocationsContext` class.</span></span>

```csharp
public async Task<Locations> GetAsync(int locationId)
{
    var filter = Builders<Locations>.Filter.Eq("LocationId", locationId);
    return await _context.Locations
                            .Find(filter)
                            .FirstOrDefaultAsync();
}
```

#### <a name="use-an-env-var-in-the-docker-composeoverrideyml-file-for-the-mongodb-connection-string"></a><span data-ttu-id="6a403-193">Użyj pliku env-var w pliku docker-compose.override.yml dla ciągu połączenia MongoDB</span><span class="sxs-lookup"><span data-stu-id="6a403-193">Use an env-var in the docker-compose.override.yml file for the MongoDB connection string</span></span>

<span data-ttu-id="6a403-194">Podczas tworzenia MongoClient obiektu, potrzebuje parametru podstawowego, który jest właśnie `ConnectionString` parametr wskazujący na prawej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="6a403-194">When creating a MongoClient object, it needs a fundamental parameter which is precisely the `ConnectionString` parameter pointing to the right database.</span></span> <span data-ttu-id="6a403-195">W przypadku eShopOnContainers parametry połączenia można wskazać lokalnego kontenera platformy Docker MongoDB lub "produkcyjnej" bazy danych usługi Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="6a403-195">In the case of eShopOnContainers, the connection string can point to a local MongoDB Docker container or to a “production” Azure Cosmos DB database.</span></span>  <span data-ttu-id="6a403-196">Ten ciąg połączenia pochodzi ze zmiennych `docker-compose.override.yml` środowiskowych zdefiniowanych w plikach używanych podczas wdrażania z docker-compose lub Visual Studio, jak w poniższym kodzie yml.</span><span class="sxs-lookup"><span data-stu-id="6a403-196">That connection string comes from the environment variables defined in the `docker-compose.override.yml` files used when deploying with docker-compose or Visual Studio, as in the following yml code.</span></span>

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

<span data-ttu-id="6a403-197">Zmienna środowiskowa `ConnectionString` jest rozpoznawana w ten sposób: Jeśli zmienna `ESHOP_AZURE_COSMOSDB` globalna jest zdefiniowana w `.env` pliku z parametryą połączenia usługi Azure Cosmos DB, użyje jej do uzyskania dostępu do bazy danych usługi Azure Cosmos DB w chmurze.</span><span class="sxs-lookup"><span data-stu-id="6a403-197">The `ConnectionString` environment variable is resolved this way: If the `ESHOP_AZURE_COSMOSDB` global variable is defined in the `.env` file with the Azure Cosmos DB connection string, it will use it to access the Azure Cosmos DB database in the cloud.</span></span> <span data-ttu-id="6a403-198">Jeśli nie jest zdefiniowany, zajmie `mongodb://nosqldata` wartość i użyć kontenera MongoDB rozwoju.</span><span class="sxs-lookup"><span data-stu-id="6a403-198">If it’s not defined, it will take the `mongodb://nosqldata` value and use the development MongoDB container.</span></span>

<span data-ttu-id="6a403-199">Poniższy kod przedstawia `.env` plik z globalną zmienną środowiskową ciągu połączenia usługi Azure Cosmos DB, zaimplementowany w eShopOnContainers:</span><span class="sxs-lookup"><span data-stu-id="6a403-199">The following code shows the `.env` file with the Azure Cosmos DB connection string global environment variable, as implemented in eShopOnContainers:</span></span>

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

<span data-ttu-id="6a403-200">Odkomentuj wiersz ESHOP_AZURE_COSMOSDB i zaktualizuj go za pomocą ciągu połączenia usługi Azure Cosmos DB uzyskanego z witryny Azure portal, jak [wyjaśniono w połącz aplikację MongoDB z usługą Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account).</span><span class="sxs-lookup"><span data-stu-id="6a403-200">Uncomment the ESHOP_AZURE_COSMOSDB line and update it with your Azure Cosmos DB connection string obtained from the Azure portal as explained in [Connect a MongoDB application to Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account).</span></span>

<span data-ttu-id="6a403-201">Jeśli `ESHOP_AZURE_COSMOSDB` zmienna globalna jest pusta, co `.env` oznacza, że jest komentowana w pliku, kontener używa domyślnego ciągu połączenia MongoDB.</span><span class="sxs-lookup"><span data-stu-id="6a403-201">If the `ESHOP_AZURE_COSMOSDB` global variable is empty, meaning it's commented out in the `.env` file, then the container uses a default MongoDB connection string.</span></span> <span data-ttu-id="6a403-202">Ten ciąg połączeń wskazuje lokalny kontener MongoDB wdrożony w eShopOnContainers, który został nazwany `nosqldata` i został zdefiniowany w pliku docker-compose, jak pokazano w następującym kodzie .yml:</span><span class="sxs-lookup"><span data-stu-id="6a403-202">This connection string points to the local MongoDB container deployed in eShopOnContainers that is named `nosqldata` and was defined at the docker-compose file, as shown in the following .yml code:</span></span>

``` yml
# docker-compose.yml
version: '3.4'
services:
  # ...Other services...
  nosqldata:
    image: mongo
```

#### <a name="additional-resources"></a><span data-ttu-id="6a403-203">Zasoby dodatkowe</span><span class="sxs-lookup"><span data-stu-id="6a403-203">Additional resources</span></span>

- <span data-ttu-id="6a403-204">**Modelowanie danych dokumentu dla baz danych NoSQL** </span><span class="sxs-lookup"><span data-stu-id="6a403-204">**Modeling document data for NoSQL databases** </span></span>\
  <https://docs.microsoft.com/azure/cosmos-db/modeling-data>

- <span data-ttu-id="6a403-205">**Vaughn Vernon. Idealny magazyn agregacji projektowej oparty na domenie?**</span><span class="sxs-lookup"><span data-stu-id="6a403-205">**Vaughn Vernon. The Ideal Domain-Driven Design Aggregate Store?**</span></span> \
  <https://kalele.io/blog-posts/the-ideal-domain-driven-design-aggregate-store/>

- <span data-ttu-id="6a403-206">**Wprowadzenie do usługi Azure Cosmos DB: interfejs API dla usługi MongoDB**  </span><span class="sxs-lookup"><span data-stu-id="6a403-206">**Introduction to Azure Cosmos DB: API for MongoDB**  </span></span>\
  <https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction>

- <span data-ttu-id="6a403-207">**Usługa Azure Cosmos DB: tworzenie aplikacji sieci Web interfejsu API MongoDB przy platformie .NET i witrynie Azure portal**  </span><span class="sxs-lookup"><span data-stu-id="6a403-207">**Azure Cosmos DB: Build a MongoDB API web app with .NET and the Azure portal**  </span></span>\
  <https://docs.microsoft.com/azure/cosmos-db/create-mongodb-dotnet>

- <span data-ttu-id="6a403-208">**Użyj emulatora usługi Azure Cosmos DB do lokalnego programowania i testowania**  </span><span class="sxs-lookup"><span data-stu-id="6a403-208">**Use the Azure Cosmos DB Emulator for local development and testing**  </span></span>\
  <https://docs.microsoft.com/azure/cosmos-db/local-emulator>

- <span data-ttu-id="6a403-209">**Łączenie aplikacji MongoDB z usługą Azure Cosmos DB**  </span><span class="sxs-lookup"><span data-stu-id="6a403-209">**Connect a MongoDB application to Azure Cosmos DB**  </span></span>\
  <https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account>

- <span data-ttu-id="6a403-210">**Obraz platformy Docker emulatora usługi Cosmos DB (kontener systemu Windows)**  </span><span class="sxs-lookup"><span data-stu-id="6a403-210">**The Cosmos DB Emulator Docker image (Windows Container)**  </span></span>\
  <https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator/>

- <span data-ttu-id="6a403-211">**Obraz platformy Docker MongoDB (kontener Linux i Windows)**  </span><span class="sxs-lookup"><span data-stu-id="6a403-211">**The MongoDB Docker image (Linux and Windows Container)**  </span></span>\
  <https://hub.docker.com/_/mongo/>

- <span data-ttu-id="6a403-212">**Korzystanie z usługi MongoChef (Studio 3T) z kontem usługi Azure Cosmos DB: API dla konta MongoDB**  </span><span class="sxs-lookup"><span data-stu-id="6a403-212">**Use MongoChef (Studio 3T) with an Azure Cosmos DB: API for MongoDB account**  </span></span>\
  <https://docs.microsoft.com/azure/cosmos-db/mongodb-mongochef>

>[!div class="step-by-step"]
><span data-ttu-id="6a403-213">[Poprzedni](infrastructure-persistence-layer-implemenation-entity-framework-core.md)
>[następny](microservice-application-layer-web-api-design.md)</span><span class="sxs-lookup"><span data-stu-id="6a403-213">[Previous](infrastructure-persistence-layer-implemenation-entity-framework-core.md)
[Next](microservice-application-layer-web-api-design.md)</span></span>
