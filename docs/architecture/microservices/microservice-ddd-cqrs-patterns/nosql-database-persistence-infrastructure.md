---
title: Korzystanie z baz danych NoSQL jako infrastruktury trwałości
description: Architektura mikrousług platformy .NET dla aplikacji platformy .NET w kontenerze | Informacje ogólne na temat używania baz danych NoSql, a w szczególności Azure Cosmos DB jako opcji wdrożenia utrwalania.
ms.date: 10/08/2018
ms.openlocfilehash: d96d72fe675dfa830029e4311f2cf165a305c328
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71039945"
---
# <a name="use-nosql-databases-as-a-persistence-infrastructure"></a><span data-ttu-id="4cad6-103">Korzystanie z baz danych NoSQL jako infrastruktury trwałości</span><span class="sxs-lookup"><span data-stu-id="4cad6-103">Use NoSQL databases as a persistence infrastructure</span></span>

<span data-ttu-id="4cad6-104">W przypadku korzystania z baz danych NoSQL dla warstwy dane infrastruktury zazwyczaj nie używasz ORM, takiego jak Entity Framework Core.</span><span class="sxs-lookup"><span data-stu-id="4cad6-104">When you use NoSQL databases for your infrastructure data tier, you typically do not use an ORM like Entity Framework Core.</span></span> <span data-ttu-id="4cad6-105">Zamiast tego należy użyć interfejsu API dostarczonego przez aparat NoSQL, takiego jak Azure Cosmos DB, MongoDB, Cassandra, RavenDB, CouchDB lub tabel usługi Azure Storage.</span><span class="sxs-lookup"><span data-stu-id="4cad6-105">Instead you use the API provided by the NoSQL engine, such as Azure Cosmos DB, MongoDB, Cassandra, RavenDB, CouchDB, or Azure Storage Tables.</span></span>

<span data-ttu-id="4cad6-106">Jednak w przypadku korzystania z bazy danych NoSQL, w szczególności bazy danych zorientowanej na dokumenty, takiej jak Azure Cosmos DB, CouchDB lub RavenDB, sposób projektowania modelu z użyciem wartości DDD jest częściowo podobny do tego, jak można to zrobić w EF Core, w odniesieniu do identyfikacji Agregowanie elementów głównych, klas jednostek podrzędnych i klas obiektów wartości.</span><span class="sxs-lookup"><span data-stu-id="4cad6-106">However, when you use a NoSQL database, especially a document-oriented database like Azure Cosmos DB, CouchDB, or RavenDB, the way you design your model with DDD aggregates is partially similar to how you can do it in EF Core, in regards to the identification of aggregate roots, child entity classes, and value object classes.</span></span> <span data-ttu-id="4cad6-107">Ostatecznie wybór bazy danych będzie miał wpływ na projekt.</span><span class="sxs-lookup"><span data-stu-id="4cad6-107">But, ultimately, the database selection will impact in your design.</span></span>

<span data-ttu-id="4cad6-108">W przypadku korzystania z bazy danych zorientowanej na dokumenty należy zaimplementować agregację jako pojedynczy dokument, zserializowaną w formacie JSON lub inny format.</span><span class="sxs-lookup"><span data-stu-id="4cad6-108">When you use a document-oriented database, you implement an aggregate as a single document, serialized in JSON or another format.</span></span> <span data-ttu-id="4cad6-109">Jednak użycie bazy danych jest niewidoczne z punktu widzenia kodu modelu domeny.</span><span class="sxs-lookup"><span data-stu-id="4cad6-109">However, the use of the database is transparent from a domain model code point of view.</span></span> <span data-ttu-id="4cad6-110">W przypadku korzystania z bazy danych NoSQL nadal używasz klas jednostek i agregacji klas głównych, ale z większą elastycznością niż w przypadku używania EF Core, ponieważ trwałość nie jest relacyjna.</span><span class="sxs-lookup"><span data-stu-id="4cad6-110">When using a NoSQL database, you still are using entity classes and aggregate root classes, but with more flexibility than when using EF Core because the persistence is not relational.</span></span>

<span data-ttu-id="4cad6-111">Różnica polega na tym, jak utrzymywać ten model.</span><span class="sxs-lookup"><span data-stu-id="4cad6-111">The difference is in how you persist that model.</span></span> <span data-ttu-id="4cad6-112">Jeśli model domeny został zaimplementowany na podstawie klas jednostek POCO, niezależny od do trwałości infrastruktury, może to wyglądać podobnie do innej infrastruktury trwałości, nawet od relacyjnej do NoSQL.</span><span class="sxs-lookup"><span data-stu-id="4cad6-112">If you implemented your domain model based on POCO entity classes, agnostic to the infrastructure persistence, it might look like you could move to a different persistence infrastructure, even from relational to NoSQL.</span></span> <span data-ttu-id="4cad6-113">Jednak nie powinno to być cel.</span><span class="sxs-lookup"><span data-stu-id="4cad6-113">However, that should not be your goal.</span></span> <span data-ttu-id="4cad6-114">Istnieją zawsze ograniczenia i wady dotyczące różnych technologii baz danych, dzięki czemu nie będzie można korzystać z tego samego modelu dla baz danych relacyjnych lub NoSQL.</span><span class="sxs-lookup"><span data-stu-id="4cad6-114">There are always constraints and trade-offs in the different database technologies, so you will not be able to have the same model for relational or NoSQL databases.</span></span> <span data-ttu-id="4cad6-115">Zmiana modeli trwałości nie jest zadaniem prostym, ponieważ transakcje i operacje trwałości będą bardzo różne.</span><span class="sxs-lookup"><span data-stu-id="4cad6-115">Changing persistence models is not a trivial task, because transactions and persistence operations will be very different.</span></span>

<span data-ttu-id="4cad6-116">Na przykład w bazie danych zorientowanej na dokument nie jest możliwe, aby zagregowany element główny miał wiele właściwości kolekcji podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="4cad6-116">For example, in a document-oriented database, it is okay for an aggregate root to have multiple child collection properties.</span></span> <span data-ttu-id="4cad6-117">W relacyjnej bazie danych zapytania z wieloma podrzędnymi właściwościami kolekcji nie są łatwo zoptymalizowane, ponieważ z powrotem uzyskuje się instrukcję UNION ALL języka SQL od EF.</span><span class="sxs-lookup"><span data-stu-id="4cad6-117">In a relational database, querying multiple child collection properties is not easily optimized, because you get a UNION ALL SQL statement back from EF.</span></span> <span data-ttu-id="4cad6-118">Posiadanie tego samego modelu domeny dla relacyjnych baz danych lub baz danych NoSQL nie jest proste i nie należy go podejmować.</span><span class="sxs-lookup"><span data-stu-id="4cad6-118">Having the same domain model for relational databases or NoSQL databases is not simple, and you should not try to do it.</span></span> <span data-ttu-id="4cad6-119">Naprawdę musisz zaprojektować model, aby zrozumieć, w jaki sposób dane będą używane w każdej konkretnej bazie danych.</span><span class="sxs-lookup"><span data-stu-id="4cad6-119">You really have to design your model with an understanding of how the data is going to be used in each particular database.</span></span>

<span data-ttu-id="4cad6-120">Zaletą korzystania z baz danych NoSQL jest to, że jednostki są bardziej znormalizowane, dlatego nie należy ustawiać mapowania tabeli.</span><span class="sxs-lookup"><span data-stu-id="4cad6-120">A benefit when using NoSQL databases is that the entities are more denormalized, so you do not set a table mapping.</span></span> <span data-ttu-id="4cad6-121">Model domeny może być bardziej elastyczny niż w przypadku korzystania z relacyjnej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="4cad6-121">Your domain model can be more flexible than when using a relational database.</span></span>

<span data-ttu-id="4cad6-122">Podczas projektowania modelu domeny opartego na agregacjach, przeniesienie do NoSQL i baz danych zorientowane na dokumenty może być jeszcze łatwiejsze niż używanie relacyjnej bazy danych, ponieważ zagregowane wartości są podobne do serializowanych dokumentów w bazie danych zorientowanej na dokument.</span><span class="sxs-lookup"><span data-stu-id="4cad6-122">When you design your domain model based on aggregates, moving to NoSQL and document-oriented databases might be even easier than using a relational database, because the aggregates you design are similar to serialized documents in a document-oriented database.</span></span> <span data-ttu-id="4cad6-123">Następnie można dołączyć do tych "toreb" wszystkie informacje, które mogą być potrzebne dla tego agregacji.</span><span class="sxs-lookup"><span data-stu-id="4cad6-123">Then you can include in those “bags” all the information you might need for that aggregate.</span></span>

<span data-ttu-id="4cad6-124">Na przykład poniższy kod JSON to Przykładowa implementacja agregacji zamówienia przy użyciu bazy danych zorientowanej na dokument.</span><span class="sxs-lookup"><span data-stu-id="4cad6-124">For instance, the following JSON code is a sample implementation of an order aggregate when using a document-oriented database.</span></span> <span data-ttu-id="4cad6-125">Jest to podobne do kolejności agregowania wdrożonej w przykładzie eShopOnContainers, ale bez użycia EF Core poniżej.</span><span class="sxs-lookup"><span data-stu-id="4cad6-125">It is similar to the order aggregate we implemented in the eShopOnContainers sample, but without using EF Core underneath.</span></span>

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

## <a name="introduction-to-azure-cosmos-db-and-the-native-cosmos-db-api"></a><span data-ttu-id="4cad6-126">Wprowadzenie do Azure Cosmos DB i natywnego interfejsu API Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="4cad6-126">Introduction to Azure Cosmos DB and the native Cosmos DB API</span></span>

<span data-ttu-id="4cad6-127">[Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction) to usługa dystrybuowana globalnie bazy danych firmy Microsoft dla aplikacji o znaczeniu strategicznym.</span><span class="sxs-lookup"><span data-stu-id="4cad6-127">[Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction) is Microsoft's globally distributed database service for mission-critical applications.</span></span> <span data-ttu-id="4cad6-128">Azure Cosmos DB zapewnia [globalną dystrybucję](https://docs.microsoft.com/azure/cosmos-db/distribute-data-globally), [elastyczne skalowanie przepływności i magazynu](https://docs.microsoft.com/azure/cosmos-db/partition-data) na całym świecie, opóźnienia o pojedynczej liczbie milisekund w 99 percentylu, [pięć dobrze zdefiniowanych poziomów spójności](https://docs.microsoft.com/azure/cosmos-db/consistency-levels)i gwarantowane wysokie dostępność — wszystko to [umowy SLA wiodące w branży](https://azure.microsoft.com/support/legal/sla/cosmos-db/).</span><span class="sxs-lookup"><span data-stu-id="4cad6-128">Azure Cosmos DB provides [turn-key global distribution](https://docs.microsoft.com/azure/cosmos-db/distribute-data-globally), [elastic scaling of throughput and storage](https://docs.microsoft.com/azure/cosmos-db/partition-data) worldwide, single-digit millisecond latencies at the 99th percentile, [five well-defined consistency levels](https://docs.microsoft.com/azure/cosmos-db/consistency-levels), and guaranteed high availability, all backed by [industry-leading SLAs](https://azure.microsoft.com/support/legal/sla/cosmos-db/).</span></span> <span data-ttu-id="4cad6-129">Azure Cosmos DB [automatycznie indeksuje dane](https://www.vldb.org/pvldb/vol8/p1668-shukla.pdf) bez konieczności postępowania z zarządzaniem schematami i indeksami.</span><span class="sxs-lookup"><span data-stu-id="4cad6-129">Azure Cosmos DB [automatically indexes data](https://www.vldb.org/pvldb/vol8/p1668-shukla.pdf) without requiring you to deal with schema and index management.</span></span> <span data-ttu-id="4cad6-130">Jest to wiele modeli i obsługuje modele danych Document, key-value, Graph i kolumnowy.</span><span class="sxs-lookup"><span data-stu-id="4cad6-130">It is multi-model and supports document, key-value, graph, and columnar data models.</span></span>

![<span data-ttu-id="4cad6-131">Azure Cosmos DB to globalnie dystrybuowana, gwarantowana baza danych o małym opóźnieniu, do której można uzyskać dostęp za pomocą czterech protokołów interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="4cad6-131">Azure Cosmos DB is a globally distributed guaranteed low-latency database that can be accessed with four API protocols.</span></span> ](./media/image19.1.png)

<span data-ttu-id="4cad6-132">**Rysunek 7-19**.</span><span class="sxs-lookup"><span data-stu-id="4cad6-132">**Figure 7-19**.</span></span> <span data-ttu-id="4cad6-133">Azure Cosmos DB dystrybucji globalnej</span><span class="sxs-lookup"><span data-stu-id="4cad6-133">Azure Cosmos DB global distribution</span></span>

<span data-ttu-id="4cad6-134">W przypadku używania modelu języka\# C do implementowania agregacji, która ma być używana przez interfejs API Azure Cosmos DB, agregacja może być podobna\# do klas C poco używanych z EF Core.</span><span class="sxs-lookup"><span data-stu-id="4cad6-134">When you use a C\# model to implement the aggregate to be used by the Azure Cosmos DB API, the aggregate can be similar to the C\# POCO classes used with EF Core.</span></span> <span data-ttu-id="4cad6-135">Różnica polega na sposobie korzystania z nich z warstw aplikacji i infrastruktury, jak w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="4cad6-135">The difference is in the way to use them from the application and infrastructure layers, as in the following code:</span></span>

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

<span data-ttu-id="4cad6-136">Możesz zobaczyć, że sposób pracy z modelem domeny może być podobny do sposobu korzystania z niego w warstwie modelu domeny, gdy infrastruktura jest Dr.</span><span class="sxs-lookup"><span data-stu-id="4cad6-136">You can see that the way you work with your domain model can be similar to the way you use it in your domain model layer when the infrastructure is EF.</span></span> <span data-ttu-id="4cad6-137">Nadal używasz tych samych agregacji metod głównych w celu zapewnienia spójności, nieodmian i walidacji w ramach agregacji.</span><span class="sxs-lookup"><span data-stu-id="4cad6-137">You still use the same aggregate root methods to ensure consistency, invariants, and validations within the aggregate.</span></span>

<span data-ttu-id="4cad6-138">Jednak w przypadku utrwalania modelu w bazie danych NoSQL zmiana kodu i interfejsu API znacznie porównana z kodem EF Core lub innym kodem związanym z relacyjnymi bazami danych.</span><span class="sxs-lookup"><span data-stu-id="4cad6-138">However, when you persist your model into the NoSQL database, the code and API change dramatically compared to EF Core code or any other code related to relational databases.</span></span>

## <a name="implement-net-code-targeting-mongodb-and-azure-cosmos-db"></a><span data-ttu-id="4cad6-139">Implementowanie kodu platformy .NET dla MongoDB i Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="4cad6-139">Implement .NET code targeting MongoDB and Azure Cosmos DB</span></span>

### <a name="use-azure-cosmos-db-from-net-containers"></a><span data-ttu-id="4cad6-140">Używanie Azure Cosmos DB z kontenerów platformy .NET</span><span class="sxs-lookup"><span data-stu-id="4cad6-140">Use Azure Cosmos DB from .NET containers</span></span>

<span data-ttu-id="4cad6-141">Dostęp do Azure Cosmos DB baz danych można uzyskać z kodu platformy .NET działającego w kontenerach, podobnie jak w przypadku dowolnej innej aplikacji platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="4cad6-141">You can access Azure Cosmos DB databases from .NET code running in containers, like from any other .NET application.</span></span> <span data-ttu-id="4cad6-142">Na przykład w programie eShopOnContainers są implementowane mikrousługi lokalizacji. API i marketingu. API, dzięki czemu mogą korzystać z Azure Cosmos DB baz danych.</span><span class="sxs-lookup"><span data-stu-id="4cad6-142">For instance, the Locations.API and Marketing.API microservices in eShopOnContainers are implemented so they can consume Azure Cosmos DB databases.</span></span>

<span data-ttu-id="4cad6-143">Istnieje jednak ograniczenie Azure Cosmos DB z punktu widzenia środowiska projektowania platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="4cad6-143">However, there’s a limitation in Azure Cosmos DB from a Docker development environment point of view.</span></span> <span data-ttu-id="4cad6-144">Nawet wtedy, gdy [Azure Cosmos DB emulatora](https://docs.microsoft.com/azure/cosmos-db/local-emulator) lokalnego można uruchomić na lokalnym komputerze deweloperskim (na przykład na komputerze), od momentu do późnego 2017, tylko system Windows, a nie Linux.</span><span class="sxs-lookup"><span data-stu-id="4cad6-144">Even when there’s a on-premises [Azure Cosmos DB Emulator](https://docs.microsoft.com/azure/cosmos-db/local-emulator) able to run in a local development machine (like a PC), as of late 2017, it just supports Windows, not Linux.</span></span> 

<span data-ttu-id="4cad6-145">Istnieje również możliwość uruchomienia tego emulatora na platformie Docker, ale tylko w kontenerach systemu Windows, a nie w przypadku kontenerów z systemem Linux.</span><span class="sxs-lookup"><span data-stu-id="4cad6-145">There is also the possibility to run this emulator on Docker, but just on Windows Containers, not with Linux Containers.</span></span> <span data-ttu-id="4cad6-146">Jest to wstępna niepełnosprawność środowiska programistycznego, jeśli aplikacja jest wdrażana jako kontenery systemu Linux, ponieważ obecnie nie można wdrażać kontenerów systemów Linux i Windows na Docker for Windows w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="4cad6-146">That is an initial handicap for the development environment if your application is deployed as Linux containers, since, currently, you cannot deploy Linux and Windows Containers on Docker for Windows at the same time.</span></span> <span data-ttu-id="4cad6-147">Wszystkie wdrażane kontenery muszą być przeznaczone dla systemu Linux lub Windows.</span><span class="sxs-lookup"><span data-stu-id="4cad6-147">Either all containers being deployed have to be for Linux or for Windows.</span></span>

<span data-ttu-id="4cad6-148">Idealnym i bardziej prostym wdrożeniem rozwiązania deweloperskiego/testowego jest możliwość wdrażania systemów baz danych jako kontenerów wraz z niestandardowymi kontenerami, dzięki czemu środowiska deweloperskie/testowe są zawsze spójne.</span><span class="sxs-lookup"><span data-stu-id="4cad6-148">The ideal and more straightforward deployment for a dev/test solution is to be able to deploy your database systems as containers along with your custom containers so your dev/test environments are always consistent.</span></span>

### <a name="use-mongodb-api-for-local-devtest-linuxwindows-containers-plus-azure-cosmos-db"></a><span data-ttu-id="4cad6-149">Korzystanie z interfejsu API MongoDB na potrzeby lokalnego tworzenia i testowania kontenerów systemu Linux/Windows oraz Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="4cad6-149">Use MongoDB API for local dev/test Linux/Windows containers plus Azure Cosmos DB</span></span>

<span data-ttu-id="4cad6-150">Bazy danych Cosmos DB obsługują interfejs API MongoDB dla platformy .NET oraz natywny protokół MongoDB.</span><span class="sxs-lookup"><span data-stu-id="4cad6-150">Cosmos DB databases support MongoDB API for .NET as well as the native MongoDB wire protocol.</span></span> <span data-ttu-id="4cad6-151">Oznacza to, że korzystając z istniejących sterowników, aplikacja zapisywana dla MongoDB może teraz komunikować się z Cosmos DB i używać Cosmos DB baz danych zamiast baz danych MongoDB, jak pokazano na rysunku 7-20.</span><span class="sxs-lookup"><span data-stu-id="4cad6-151">This means that by using existing drivers, your application written for MongoDB can now communicate with Cosmos DB and use Cosmos DB databases instead of MongoDB databases, as shown in Figure 7-20.</span></span>

![Cosmos DB obsługuje interfejs API MongoDB dla protokołów .NET i MongoDB, można łatwo przełączać od MongoDb do Cosmos DB.](./media/image19.2.png)

<span data-ttu-id="4cad6-153">**Rysunek 7-20**.</span><span class="sxs-lookup"><span data-stu-id="4cad6-153">**Figure 7-20**.</span></span> <span data-ttu-id="4cad6-154">Używanie interfejsu API MongoDB i protokołu do uzyskiwania dostępu Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="4cad6-154">Using MongoDB API and protocol to access Azure Cosmos DB</span></span>

<span data-ttu-id="4cad6-155">Jest to bardzo wygodne podejście do weryfikacji koncepcji w środowiskach platformy Docker z kontenerami systemu Linux, ponieważ [obraz platformy](https://hub.docker.com/r/_/mongo/) Docker MongoDB jest obrazem wielodostępnym, który obsługuje kontenery platformy Docker Linux i kontenery platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="4cad6-155">This is a very convenient approach for proof of concepts in Docker environments with Linux containers because the [MongoDB Docker image](https://hub.docker.com/r/_/mongo/) is a multi-arch image that supports Docker Linux containers and Docker Windows containers.</span></span>

<span data-ttu-id="4cad6-156">Jak pokazano na poniższej ilustracji, za pomocą interfejsu API MongoDB, eShopOnContainers obsługuje kontenery systemu Linux i Windows dla lokalnego środowiska programistycznego, ale można przenieść do skalowalnego rozwiązania w chmurze PaaS jako Azure Cosmos DB, po prostu [zmieniając MongoDB parametry połączenia w celu wskazywania Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account).</span><span class="sxs-lookup"><span data-stu-id="4cad6-156">As shown in the following image, by using the MongoDB API, eShopOnContainers supports MongoDB Linux and Windows containers for the local development environment but then, you can move to a scalable, PaaS cloud solution as Azure Cosmos DB by simply [changing the MongoDB connection string to point to Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account).</span></span>

![Mikrousługa lokalizacji w eShopOnContainers jest implementowana przy użyciu MongoDB, ale można ją przełączyć do Cosmos DB przez zmianę parametrów połączenia.](./media/image20-bis.png)

<span data-ttu-id="4cad6-158">**Rysunek 7-21**.</span><span class="sxs-lookup"><span data-stu-id="4cad6-158">**Figure 7-21**.</span></span> <span data-ttu-id="4cad6-159">eShopOnContainers przy użyciu kontenerów MongoDB do celów deweloperskich lub Azure Cosmos DB produkcyjnych</span><span class="sxs-lookup"><span data-stu-id="4cad6-159">eShopOnContainers using MongoDB containers for dev-env or Azure Cosmos DB for production</span></span>

<span data-ttu-id="4cad6-160">Azure Cosmos DB produkcyjne będzie działać w chmurze platformy Azure jako usługa PaaS i skalowalna.</span><span class="sxs-lookup"><span data-stu-id="4cad6-160">The production Azure Cosmos DB would be running in Azure’s cloud as a PaaS and scalable service.</span></span>

<span data-ttu-id="4cad6-161">Niestandardowe kontenery programu .NET Core można uruchamiać na lokalnym hoście platformy Docker (używanym Docker for Windows na komputerze z systemem Windows 10) lub wdrożyć w środowisku produkcyjnym, takim jak Kubernetes na platformie Azure AKS lub platformie Azure Service Fabric.</span><span class="sxs-lookup"><span data-stu-id="4cad6-161">Your custom .NET Core containers can run on a local development Docker host (that is using Docker for Windows in a Windows 10 machine) or be deployed into a production environment, like Kubernetes in Azure AKS or Azure Service Fabric.</span></span> <span data-ttu-id="4cad6-162">W tym drugim środowisku wdrożono tylko kontenery niestandardowe platformy .NET Core, ale nie kontener MongoDB, ponieważ do obsługi danych w środowisku produkcyjnym jest używany Azure Cosmos DB w chmurze.</span><span class="sxs-lookup"><span data-stu-id="4cad6-162">In this second environment, you would deploy only the .NET Core custom containers but not the MongoDB container since you’d be using Azure Cosmos DB in the cloud for handling the data in production.</span></span>

<span data-ttu-id="4cad6-163">Oczywistą zaletą korzystania z interfejsu API MongoDB jest to, że rozwiązanie może działać zarówno w aparatach baz danych, MongoDB, jak i Azure Cosmos DB, dzięki czemu migracja do różnych środowisk powinna być łatwa.</span><span class="sxs-lookup"><span data-stu-id="4cad6-163">A clear benefit of using the MongoDB API is that your solution could run in both database engines, MongoDB or Azure Cosmos DB, so migrations to different environments should be easy.</span></span> <span data-ttu-id="4cad6-164">Jednak czasami jest wartościowa użycie natywnego interfejsu API (jest to natywny interfejs API Cosmos DB) w celu pełnego wykorzystania możliwości określonego aparatu bazy danych.</span><span class="sxs-lookup"><span data-stu-id="4cad6-164">However, sometimes it is worthwhile to use a native API (that is the native Cosmos DB API) in order to take full advantage of the capabilities of a specific database engine.</span></span>

<span data-ttu-id="4cad6-165">Aby uzyskać dalsze porównanie między zwykłym użyciem MongoDB a Cosmos DB w chmurze, zobacz [zalety korzystania z Azure Cosmos DB na tej stronie](https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction).</span><span class="sxs-lookup"><span data-stu-id="4cad6-165">For further comparison between simply using MongoDB versus Cosmos DB in the cloud, see the [Benefits of using Azure Cosmos DB in this page](https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction).</span></span> 

### <a name="analyze-your-approach-for-production-applications-mongodb-api-vs-cosmos-db-api"></a><span data-ttu-id="4cad6-166">Analizuj podejście do aplikacji produkcyjnych: Interfejs API MongoDB a Interfejs API Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="4cad6-166">Analyze your approach for production applications: MongoDB API vs. Cosmos DB API</span></span>

<span data-ttu-id="4cad6-167">W eShopOnContainers korzystamy z interfejsu API MongoDB, ponieważ naszym priorytetem było podstawowe środowisko deweloperskie/testowe przy użyciu bazy danych NoSQL, która może również współejść z Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="4cad6-167">In eShopOnContainers, we’re using MongoDB API because our priority was fundamentally to have a consistent dev/test environment using a NoSQL database that could also work with Azure Cosmos DB.</span></span>

<span data-ttu-id="4cad6-168">Jeśli jednak planujesz używać interfejsu API MongoDB do uzyskiwania dostępu do Azure Cosmos DB na platformie Azure dla aplikacji produkcyjnych, należy przeanalizować różnice w zakresie możliwości i wydajności podczas korzystania z interfejsu API MongoDB w celu uzyskania dostępu do Azure Cosmos DB baz danych w porównaniu z użyciem natywnego Interfejs API Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="4cad6-168">However, if you planning to use MongoDB API to access Azure Cosmos DB in Azure for production applications, you should analyze the differences in capabilities and performance when using MongoDB API to access Azure Cosmos DB databases compared to using the native Azure Cosmos DB API.</span></span> <span data-ttu-id="4cad6-169">Jeśli jest podobna, można użyć interfejsu API MongoDB i uzyskać korzyści z obsługi dwóch aparatów bazy danych NoSQL w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="4cad6-169">If it is similar you can use MongoDB API and you get the benefit of supporting two NoSQL database engines at the same time.</span></span>

<span data-ttu-id="4cad6-170">Klastry MongoDB można również używać jako produkcyjnej bazy danych w chmurze platformy Azure, za pomocą [usługi MongoDB platformy Azure](https://www.mongodb.com/scale/mongodb-azure-service).</span><span class="sxs-lookup"><span data-stu-id="4cad6-170">You could also use MongoDB clusters as the production database in Azure’s cloud, too, with [MongoDB Azure Service](https://www.mongodb.com/scale/mongodb-azure-service).</span></span> <span data-ttu-id="4cad6-171">Ale nie jest to usługa PaaS świadczona przez firmę Microsoft.</span><span class="sxs-lookup"><span data-stu-id="4cad6-171">But that is not a PaaS service provided by Microsoft.</span></span> <span data-ttu-id="4cad6-172">W takim przypadku platforma Azure obsługuje tylko to rozwiązanie pochodzące z MongoDB.</span><span class="sxs-lookup"><span data-stu-id="4cad6-172">In this case, Azure is just hosting that solution coming from MongoDB.</span></span>

<span data-ttu-id="4cad6-173">Zasadniczo jest to tylko oświadczenie stwierdzające, że nie należy zawsze używać interfejsu API MongoDB w odniesieniu do Azure Cosmos DB, tak jak w eShopOnContainers, ponieważ było to wygodne rozwiązanie dla kontenerów systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="4cad6-173">Basically, this is just a disclaimer stating that you shouldn’t always use MongoDB API against Azure Cosmos DB, as we did in eShopOnContainers because it was a convenient choice for Linux containers.</span></span> <span data-ttu-id="4cad6-174">Decyzja powinna być oparta na określonych wymaganiach i testach, które należy wykonać w przypadku aplikacji produkcyjnej.</span><span class="sxs-lookup"><span data-stu-id="4cad6-174">The decision should be based on the specific needs and tests you need to do for your production application.</span></span>

### <a name="the-code-use-mongodb-api-in-net-core-applications"></a><span data-ttu-id="4cad6-175">Kod: Korzystanie z interfejsu API MongoDB w aplikacjach .NET Core</span><span class="sxs-lookup"><span data-stu-id="4cad6-175">The code: Use MongoDB API in .NET Core applications</span></span>

<span data-ttu-id="4cad6-176">Interfejs API MongoDB dla platformy .NET jest oparty na pakietach NuGet, które należy dodać do projektów, takich jak w projekcie Locations. API pokazane na poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="4cad6-176">MongoDB API for .NET is based on NuGet packages that you need to add to your projects, like in the Locations.API project shown in the following figure.</span></span>

![Widok Eksplorator rozwiązań pokazujący zależności w pakietach NuGet MongoDB.](./media/image21-bis.png)

<span data-ttu-id="4cad6-178">**Rysunek 7-22**.</span><span class="sxs-lookup"><span data-stu-id="4cad6-178">**Figure 7-22**.</span></span> <span data-ttu-id="4cad6-179">Pakiety NuGet interfejsu API MongoDB w projekcie .NET Core</span><span class="sxs-lookup"><span data-stu-id="4cad6-179">MongoDB API NuGet packages references in a .NET Core project</span></span>

<span data-ttu-id="4cad6-180">Zbadamy kod w poniższych sekcjach.</span><span class="sxs-lookup"><span data-stu-id="4cad6-180">Let's investigate the code in the following sections.</span></span>

#### <a name="a-model-used-by-mongodb-api"></a><span data-ttu-id="4cad6-181">Model używany przez interfejs API MongoDB</span><span class="sxs-lookup"><span data-stu-id="4cad6-181">A Model used by MongoDB API</span></span>

<span data-ttu-id="4cad6-182">Najpierw należy zdefiniować model, który będzie przechowywać dane pochodzące z bazy danych w przestrzeni pamięci aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4cad6-182">First, you need to define a model that will hold the data coming from the database in your application’s memory space.</span></span> <span data-ttu-id="4cad6-183">Poniżej przedstawiono przykładowy model używany do lokalizacji w eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="4cad6-183">Here’s an example of the model used for Locations at eShopOnContainers.</span></span>

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

<span data-ttu-id="4cad6-184">Można zobaczyć kilka atrybutów i typów pochodzących z pakietów NuGet MongoDB.</span><span class="sxs-lookup"><span data-stu-id="4cad6-184">You can see there are a few attributes and types coming from the MongoDB NuGet packages.</span></span>

<span data-ttu-id="4cad6-185">Bazy danych NoSQL są zwykle bardzo dobrze dopasowane do pracy z nierelacyjnymi danymi hierarchicznymi.</span><span class="sxs-lookup"><span data-stu-id="4cad6-185">NoSQL databases are usually very well suited for working with non-relational hierarchical data.</span></span> <span data-ttu-id="4cad6-186">W tym przykładzie używamy typów MongoDB, szczególnie dla lokalizacji geograficznych, takich jak `GeoJson2DGeographicCoordinates`.</span><span class="sxs-lookup"><span data-stu-id="4cad6-186">In this example, we are using MongoDB types especially made for geo-locations, like `GeoJson2DGeographicCoordinates`.</span></span>

#### <a name="retrieve-the-database-and-the-collection"></a><span data-ttu-id="4cad6-187">Pobieranie bazy danych i kolekcji</span><span class="sxs-lookup"><span data-stu-id="4cad6-187">Retrieve the database and the collection</span></span>

<span data-ttu-id="4cad6-188">W eShopOnContainers został utworzony niestandardowy kontekst bazy danych, w którym implementujemy kod w celu pobrania bazy danych i MongoCollections, jak w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="4cad6-188">In eShopOnContainers, we have created a custom database context where we implement the code to retrieve the database and the MongoCollections, as in the following code.</span></span>

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

#### <a name="retrieve-the-data"></a><span data-ttu-id="4cad6-189">Pobieranie danych</span><span class="sxs-lookup"><span data-stu-id="4cad6-189">Retrieve the data</span></span>

<span data-ttu-id="4cad6-190">W C# kodzie, takim jak kontrolery interfejsu API sieci Web lub implementacji niestandardowych repozytoriów, można napisać podobny kod do poniższego zapytania przy użyciu interfejsu API MongoDB.</span><span class="sxs-lookup"><span data-stu-id="4cad6-190">In C# code, like Web API controllers or custom Repositories implementation, you can write similar code to the following when querying through the MongoDB API.</span></span> <span data-ttu-id="4cad6-191">Należy zauważyć, `_context` że obiekt jest wystąpieniem poprzedniej `LocationsContext` klasy.</span><span class="sxs-lookup"><span data-stu-id="4cad6-191">Note that the `_context` object is an instance of the previous `LocationsContext` class.</span></span>

```csharp
public async Task<Locations> GetAsync(int locationId)
{
    var filter = Builders<Locations>.Filter.Eq("LocationId", locationId);
    return await _context.Locations
                            .Find(filter)
                            .FirstOrDefaultAsync();
}
```

#### <a name="use-an-env-var-in-the-docker-composeoverrideyml-file-for-the-mongodb-connection-string"></a><span data-ttu-id="4cad6-192">Użyj funkcji ENV-var w pliku Docker-Compose. override. yml dla parametrów połączenia MongoDB</span><span class="sxs-lookup"><span data-stu-id="4cad6-192">Use an env-var in the docker-compose.override.yml file for the MongoDB connection string</span></span>

<span data-ttu-id="4cad6-193">Podczas tworzenia obiektu MongoClient musi on mieć podstawowy parametr, który jest precyzyjnym `ConnectionString` parametrem wskazującym odpowiednią bazę danych.</span><span class="sxs-lookup"><span data-stu-id="4cad6-193">When creating a MongoClient object, it needs a fundamental parameter which is precisely the `ConnectionString` parameter pointing to the right database.</span></span> <span data-ttu-id="4cad6-194">W przypadku eShopOnContainers parametry połączenia mogą wskazywać lokalny kontener platformy Docker MongoDB lub do bazy danych Azure Cosmos DB produkcyjnych.</span><span class="sxs-lookup"><span data-stu-id="4cad6-194">In the case of eShopOnContainers, the connection string can point to a local MongoDB Docker container or to a “production” Azure Cosmos DB database.</span></span>  <span data-ttu-id="4cad6-195">Te parametry połączenia pochodzą ze zmiennych środowiskowych zdefiniowanych w `docker-compose.override.yml` plikach używanych podczas wdrażania przy użyciu platformy Docker-redagowanie lub programu Visual Studio, jak w poniższym kodzie YML.</span><span class="sxs-lookup"><span data-stu-id="4cad6-195">That connection string comes from the environment variables defined in the `docker-compose.override.yml` files used when deploying with docker-compose or Visual Studio, as in the following yml code.</span></span>

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

<span data-ttu-id="4cad6-196">Zmienna `ConnectionString` środowiskowa jest rozpoznawana w następujący sposób: `.env` Jeśli zmienna `ESHOP_AZURE_COSMOSDB` globalna jest zdefiniowana w pliku z parametrami połączenia Azure Cosmos DB, będzie ona używać go do uzyskiwania dostępu do bazy danych Azure Cosmos DB w chmurze.</span><span class="sxs-lookup"><span data-stu-id="4cad6-196">The `ConnectionString` environment variable is resolved this way: If the `ESHOP_AZURE_COSMOSDB` global variable is defined in the `.env` file with the Azure Cosmos DB connection string, it will use it to access the Azure Cosmos DB database in the cloud.</span></span> <span data-ttu-id="4cad6-197">Jeśli ta `mongodb://nosql.data` wartość nie jest zdefiniowana, zostanie ona przestosowana i będzie używać kontenera MongoDB Development.</span><span class="sxs-lookup"><span data-stu-id="4cad6-197">If it’s not defined, it will take the `mongodb://nosql.data` value and use the development mongodb container.</span></span>

<span data-ttu-id="4cad6-198">Poniższy kod przedstawia `.env` plik Azure Cosmos DB z eShopOnContainersą globalną zmienną środowiskową parametrów połączenia, zgodnie z zaimplementowaną w programie:</span><span class="sxs-lookup"><span data-stu-id="4cad6-198">The following code shows the `.env` file with the Azure Cosmos DB connection string global environment variable, as implemented in eShopOnContainers:</span></span>

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

<span data-ttu-id="4cad6-199">Należy usunąć komentarz z wiersza ESHOP_AZURE_COSMOSDB i zaktualizować go przy użyciu parametrów połączenia Azure Cosmos DB uzyskanych z Azure Portal, jak wyjaśniono w temacie [łączenie aplikacji MongoDB do Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account).</span><span class="sxs-lookup"><span data-stu-id="4cad6-199">You should uncomment the ESHOP_AZURE_COSMOSDB line and update it with your Azure Cosmos DB connection string obtained from the Azure portal as explained in [Connect a MongoDB application to Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account).</span></span>

<span data-ttu-id="4cad6-200">Jeśli zmienna `.env` globalna jest pusta, co oznacza, że jest oznaczona jako komentarz do pliku, kontener używa domyślnych parametrów połączenia MongoDB wskazujących lokalny kontener MongoDB wdrożony w eShopOnContainers o nazwie `ESHOP_AZURE_COSMOSDB` `nosql.data`i został zdefiniowany w pliku Docker-Zredaguj, jak pokazano w poniższym kodzie. yml.</span><span class="sxs-lookup"><span data-stu-id="4cad6-200">If the `ESHOP_AZURE_COSMOSDB` global variable is empty, meaning that it is commented out in the `.env` file, then the container uses a default MongoDB connection string pointing to the local MongoDB container deployed in eShopOnContainers which is named `nosql.data` and was defined at the docker-compose file, as shown in the following .yml code.</span></span> 

``` yml
# docker-compose.yml
version: '3.4'
services:
  # ...Other services...
  nosql.data:
    image: mongo
```

#### <a name="additional-resources"></a><span data-ttu-id="4cad6-201">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="4cad6-201">Additional resources</span></span>

- <span data-ttu-id="4cad6-202">**Modelowanie danych dokumentu dla baz danych NoSQL** </span><span class="sxs-lookup"><span data-stu-id="4cad6-202">**Modeling document data for NoSQL databases** </span></span>\
  <https://docs.microsoft.com/azure/cosmos-db/modeling-data>

- <span data-ttu-id="4cad6-203">**Vaughn Vernon. Idealny magazyn agregacji projektu opartego na domenie?**</span><span class="sxs-lookup"><span data-stu-id="4cad6-203">**Vaughn Vernon. The Ideal Domain-Driven Design Aggregate Store?**</span></span> \
  <https://kalele.io/blog-posts/the-ideal-domain-driven-design-aggregate-store/>

- <span data-ttu-id="4cad6-204">**Wprowadzenie do Azure Cosmos DB: Interfejs API dla usługi MongoDB**  </span><span class="sxs-lookup"><span data-stu-id="4cad6-204">**Introduction to Azure Cosmos DB: API for MongoDB**  </span></span>\
  <https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction>

- <span data-ttu-id="4cad6-205">**Azure Cosmos DB: Tworzenie aplikacji sieci Web interfejsu API MongoDB za pomocą platformy .NET i Azure Portal**  </span><span class="sxs-lookup"><span data-stu-id="4cad6-205">**Azure Cosmos DB: Build a MongoDB API web app with .NET and the Azure portal**  </span></span>\
  <https://docs.microsoft.com/azure/cosmos-db/create-mongodb-dotnet>

- <span data-ttu-id="4cad6-206">**Korzystanie z emulatora Azure Cosmos DB na potrzeby lokalnego tworzenia i testowania**  </span><span class="sxs-lookup"><span data-stu-id="4cad6-206">**Use the Azure Cosmos DB Emulator for local development and testing**  </span></span>\
  <https://docs.microsoft.com/azure/cosmos-db/local-emulator>

- <span data-ttu-id="4cad6-207">**Łączenie aplikacji MongoDB z usługą Azure Cosmos DB**  </span><span class="sxs-lookup"><span data-stu-id="4cad6-207">**Connect a MongoDB application to Azure Cosmos DB**  </span></span>\
  <https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account>

- <span data-ttu-id="4cad6-208">**Obraz Cosmos DB Docker emulatora (kontener systemu Windows)**   </span><span class="sxs-lookup"><span data-stu-id="4cad6-208">**The Cosmos DB Emulator Docker image (Windows Container)**  </span></span>\
  <https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator/>

- <span data-ttu-id="4cad6-209">**Obraz platformy Docker MongoDB (kontener Linux i Windows)**   </span><span class="sxs-lookup"><span data-stu-id="4cad6-209">**The MongoDB Docker image (Linux and Windows Container)**  </span></span>\
  <https://hub.docker.com/_/mongo/>

- <span data-ttu-id="4cad6-210">**Użyj korzystanie programu mongochef (Studio 3T) z Azure Cosmos DB: Interfejs API dla konta MongoDB**  </span><span class="sxs-lookup"><span data-stu-id="4cad6-210">**Use MongoChef (Studio 3T) with an Azure Cosmos DB: API for MongoDB account**  </span></span>\
  <https://docs.microsoft.com/azure/cosmos-db/mongodb-mongochef>

>[!div class="step-by-step"]
><span data-ttu-id="4cad6-211">[Poprzedni](infrastructure-persistence-layer-implemenation-entity-framework-core.md)Następny
>[](microservice-application-layer-web-api-design.md)</span><span class="sxs-lookup"><span data-stu-id="4cad6-211">[Previous](infrastructure-persistence-layer-implemenation-entity-framework-core.md)
[Next](microservice-application-layer-web-api-design.md)</span></span>
