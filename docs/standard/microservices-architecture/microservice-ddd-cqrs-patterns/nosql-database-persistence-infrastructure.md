---
title: Przy użyciu bazy danych NoSQL jako infrastruktury trwałości
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Przy użyciu bazy danych NoSQL jako infrastruktury trwałości
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/12/2017
ms.openlocfilehash: a5fce347193921305c264df34be99063920af715
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/09/2018
ms.locfileid: "44251800"
---
# <a name="using-nosql-databases-as-a-persistence-infrastructure"></a><span data-ttu-id="17133-103">Przy użyciu bazy danych NoSQL jako infrastruktury trwałości</span><span class="sxs-lookup"><span data-stu-id="17133-103">Using NoSQL databases as a persistence infrastructure</span></span>

<span data-ttu-id="17133-104">Korzystając z bazy danych NoSQL dla warstwy danych Twojej infrastruktury, zazwyczaj nie używasz ORM, takich jak Entity Framework Core.</span><span class="sxs-lookup"><span data-stu-id="17133-104">When you use NoSQL databases for your infrastructure data tier, you typically do not use an ORM like Entity Framework Core.</span></span> <span data-ttu-id="17133-105">Zamiast tego należy użyć interfejsów API dostarczonych przez aparat NoSQL, takie jak usługi Azure Cosmos DB, bazy danych MongoDB, Cassandra, RavenDB, CouchDB lub tabele magazynu platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="17133-105">Instead you use the API provided by the NoSQL engine, such as Azure Cosmos DB, MongoDB, Cassandra, RavenDB, CouchDB, or Azure Storage Tables.</span></span>

<span data-ttu-id="17133-106">Jednak gdy używasz bazę danych NoSQL, szczególnie korzystający z dokumentów bazy danych, takich jak usługi Azure Cosmos DB, CouchDB lub RavenDB, sposób projektowania modelu za pomocą agregacji DDD przypomina częściowo jak można to zrobić w programie EF Core w odniesieniu do identyfikacji Łączny katalogów głównych klas jednostek podrzędnych i klasy obiektu wartości.</span><span class="sxs-lookup"><span data-stu-id="17133-106">However, when you use a NoSQL database, especially a document-oriented database like Azure Cosmos DB, CouchDB, or RavenDB, the way you design your model with DDD aggregates is partially similar to how you can do it in EF Core, in regards to the identification of aggregate roots, child entity classes, and value object classes.</span></span> <span data-ttu-id="17133-107">Jednak ostatecznie wybranych baz danych będzie mieć wpływ na w projekcie.</span><span class="sxs-lookup"><span data-stu-id="17133-107">But, ultimately, the database selection will impact in your design.</span></span>

<span data-ttu-id="17133-108">Korzystając z bazy danych korzystający z dokumentów, możesz zaimplementować agregacji jako pojedynczy dokument zserializowane w formacie JSON lub w innym formacie.</span><span class="sxs-lookup"><span data-stu-id="17133-108">When you use a document-oriented database, you implement an aggregate as a single document, serialized in JSON or another format.</span></span> <span data-ttu-id="17133-109">Jednak korzystanie z bazy danych jest niewidoczny z domeny modelu kodu punktu widzenia.</span><span class="sxs-lookup"><span data-stu-id="17133-109">However, the use of the database is transparent from a domain model code point of view.</span></span> <span data-ttu-id="17133-110">Podczas korzystania z bazy danych NoSQL, nadal używasz klas jednostek i klasy głównego agregacji, ale bardziej elastyczne niż przy użyciu programu EF Core, ponieważ nie ma charakteru relacyjnego trwałości.</span><span class="sxs-lookup"><span data-stu-id="17133-110">When using a NoSQL database, you still are using entity classes and aggregate root classes, but with more flexibility than when using EF Core because the persistence is not relational.</span></span>

<span data-ttu-id="17133-111">Różnica polega na w sposób utrzymują się tego modelu.</span><span class="sxs-lookup"><span data-stu-id="17133-111">The difference is in how you persist that model.</span></span> <span data-ttu-id="17133-112">Jeśli zaimplementowano modelu domeny oparte na klasach jednostki POCO niezależny od trwałości infrastruktury jego może wyglądać tak, jak można przenieść do infrastruktury trwałości różne, nawet z relacyjnych, NoSQL.</span><span class="sxs-lookup"><span data-stu-id="17133-112">If you implemented your domain model based on POCO entity classes, agnostic to the infrastructure persistence, it might look like you could move to a different persistence infrastructure, even from relational to NoSQL.</span></span> <span data-ttu-id="17133-113">Który nie powinien być cel.</span><span class="sxs-lookup"><span data-stu-id="17133-113">However, that should not be your goal.</span></span> <span data-ttu-id="17133-114">Zawsze istnieją ograniczenia w różnych bazach danych będzie umożliwiać wypychanie powiadomień możesz ponownie, dlatego nie można mieć ten sam model dla relacyjnych lub bazy danych NoSQL.</span><span class="sxs-lookup"><span data-stu-id="17133-114">There are always constraints in the different databases will push you back, so you will not be able to have the same model for relational or NoSQL databases.</span></span> <span data-ttu-id="17133-115">Zmiana stanu trwałego modele nie jest proste, ponieważ transakcje i operacji utrwalania będzie zbytnio.</span><span class="sxs-lookup"><span data-stu-id="17133-115">Changing persistence models would not be trivial, because transactions and persistence operations will be very different.</span></span>

<span data-ttu-id="17133-116">Na przykład korzystający z dokumentów bazy danych jest akceptowalne dla agregacji głównego mieć wielu właściwości kolekcji podrzędnej.</span><span class="sxs-lookup"><span data-stu-id="17133-116">For example, in a document-oriented database, it is okay for an aggregate root to have multiple child collection properties.</span></span> <span data-ttu-id="17133-117">W relacyjnej bazie danych wykonywania zapytania o wiele właściwości kolekcji podrzędnej jest często są bardzo, ponieważ wrócisz instrukcję SQL wszystkie związek z programów EF.</span><span class="sxs-lookup"><span data-stu-id="17133-117">In a relational database, querying multiple child collection properties is awful, because you get a UNION ALL SQL statement back from EF.</span></span> <span data-ttu-id="17133-118">O tym samym modelu domeny dla relacyjnych baz danych lub bazy danych NoSQL nie jest proste i nie należy spróbować.</span><span class="sxs-lookup"><span data-stu-id="17133-118">Having the same domain model for relational databases or NoSQL databases is not simple, and you should not try it.</span></span> <span data-ttu-id="17133-119">Masz naprawdę projektowania modelu za pomocą zrozumienia sposobu dane będzie można używać w każdej określonej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="17133-119">You really have to design your model with an understanding of how the data is going to be used in each particular database.</span></span>

<span data-ttu-id="17133-120">Korzyści, w przypadku korzystania z bazy danych NoSQL jest czy jednostki są bardziej nieznormalizowany, więc nie należy ustawiać Mapowanie tabeli.</span><span class="sxs-lookup"><span data-stu-id="17133-120">A benefit when using NoSQL databases is that the entities are more denormalized, so you do not set a table mapping.</span></span> <span data-ttu-id="17133-121">Model domeny może być bardziej elastyczne niż przy użyciu relacyjnej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="17133-121">Your domain model can be more flexible than when using a relational database.</span></span>

<span data-ttu-id="17133-122">Podczas projektowania modelu domeny na podstawie na agregacji, przenoszenie, NoSQL i korzystający z dokumentów bazy danych może być jeszcze łatwiejsze niż przy użyciu relacyjnej bazy danych, ponieważ agregacje, których można projektować są podobne do serializacji dokumenty w bazie danych korzystający z dokumentów.</span><span class="sxs-lookup"><span data-stu-id="17133-122">When you design your domain model based on aggregates, moving to NoSQL and document-oriented databases might be even easier than using a relational database, because the aggregates you design are similar to serialized documents in a document-oriented database.</span></span> <span data-ttu-id="17133-123">Następnie można uwzględnić w tych "zbiory" wszystkie informacje potrzebne do tej agregacji.</span><span class="sxs-lookup"><span data-stu-id="17133-123">Then you can include in those “bags” all the information you might need for that aggregate.</span></span>

<span data-ttu-id="17133-124">Na przykład poniższy kod JSON jest przykład implementacji agregacji zamówienie, podczas korzystania z bazy danych korzystający z dokumentów.</span><span class="sxs-lookup"><span data-stu-id="17133-124">For instance, the following JSON code is a sample implementation of an order aggregate when using a document-oriented database.</span></span> <span data-ttu-id="17133-125">Jest on podobny do agregacji kolejności wprowadziliśmy w ramach aplikacji eShopOnContainers przykładu, ale bez korzystania z programu EF Core poniżej.</span><span class="sxs-lookup"><span data-stu-id="17133-125">It is similar to the order aggregate we implemented in the eShopOnContainers sample, but without using EF Core underneath.</span></span>

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

## <a name="introduction-to-azure-cosmos-db-and-the-native-cosmos-db-api"></a><span data-ttu-id="17133-126">Wprowadzenie do usługi Azure Cosmos DB i natywnego interfejsu API Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="17133-126">Introduction to Azure Cosmos DB and the native Cosmos DB API</span></span>

<span data-ttu-id="17133-127">[Usługa Azure Cosmos DB](https://docs.microsoft.com/en-us/azure/cosmos-db/introduction) to usługa globalnie rozproszona baza danych firmy Microsoft dla aplikacji o kluczowym znaczeniu.</span><span class="sxs-lookup"><span data-stu-id="17133-127">[Azure Cosmos DB](https://docs.microsoft.com/en-us/azure/cosmos-db/introduction) is Microsoft's globally distributed database service for mission-critical applications.</span></span> <span data-ttu-id="17133-128">Usługa Azure Cosmos DB zapewnia [kompleksowa dystrybucja globalna](https://docs.microsoft.com/en-us/azure/cosmos-db/distribute-data-globally), [elastyczne skalowanie przepływności i przestrzeni dyskowej](https://docs.microsoft.com/en-us/azure/cosmos-db/partition-data) na całym świecie, oznaczona jedną cyfrą milisekundowe opóźnienie w 99. percentylu, [pięć dobrze zdefiniowanych poziomów spójności](https://docs.microsoft.com/en-us/azure/cosmos-db/consistency-levels)oraz gwarantowaną wysoką dostępność, wspierane przez [wiodące w branży umowy SLA](https://azure.microsoft.com/support/legal/sla/cosmos-db/).</span><span class="sxs-lookup"><span data-stu-id="17133-128">Azure Cosmos DB provides [turn-key global distribution](https://docs.microsoft.com/en-us/azure/cosmos-db/distribute-data-globally), [elastic scaling of throughput and storage](https://docs.microsoft.com/en-us/azure/cosmos-db/partition-data) worldwide, single-digit millisecond latencies at the 99th percentile, [five well-defined consistency levels](https://docs.microsoft.com/en-us/azure/cosmos-db/consistency-levels), and guaranteed high availability, all backed by [industry-leading SLAs](https://azure.microsoft.com/support/legal/sla/cosmos-db/).</span></span> <span data-ttu-id="17133-129">Usługa Azure Cosmos DB [automatycznie indeksuje dane](http://www.vldb.org/pvldb/vol8/p1668-shukla.pdf) bez konieczności zarządzania schematami i indeksami.</span><span class="sxs-lookup"><span data-stu-id="17133-129">Azure Cosmos DB [automatically indexes data](http://www.vldb.org/pvldb/vol8/p1668-shukla.pdf) without requiring you to deal with schema and index management.</span></span> <span data-ttu-id="17133-130">Jest wiele modeli i obsługuje dokumentów, pary klucz wartość, wykres i modele dokumentowe.</span><span class="sxs-lookup"><span data-stu-id="17133-130">It is multi-model and supports document, key-value, graph, and columnar data models.</span></span>

<span data-ttu-id="17133-131">![](./media/image19.1.png) Rysunek 9-19.</span><span class="sxs-lookup"><span data-stu-id="17133-131">![](./media/image19.1.png) Figure 9-19.</span></span> <span data-ttu-id="17133-132">Dystrybucję globalną usługi Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="17133-132">Azure Cosmos DB global distribution</span></span>

<span data-ttu-id="17133-133">Kiedy używasz C\# modelu implementacji agregacji, który będzie używany przez usługi Azure Cosmos DB interfejsu API, agregacja może mieć postać podobną do C\# klasy POCO używane z programem EF Core.</span><span class="sxs-lookup"><span data-stu-id="17133-133">When you use a C\# model to implement the aggregate to be used by the Azure Cosmos DB API, the aggregate can be similar to the C\# POCO classes used with EF Core.</span></span> <span data-ttu-id="17133-134">Różnica polega na w taki sposób, aby ich używać z warstw aplikacji i infrastruktury, zgodnie z poniższym kodem:</span><span class="sxs-lookup"><span data-stu-id="17133-134">The difference is in the way to use them from the application and infrastructure layers, as in the following code:</span></span>

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

<span data-ttu-id="17133-135">Widać, że sposób pracy z modelu domeny może być w podobny sposób, możesz użyć go w warstwie modelu domeny podczas infrastruktury jest EF.</span><span class="sxs-lookup"><span data-stu-id="17133-135">You can see that the way you work with your domain model can be similar to the way you use it in your domain model layer when the infrastructure is EF.</span></span> <span data-ttu-id="17133-136">Zapewnienie spójności, invariants i sprawdzania poprawności w agregacji są nadal używać tych samych metod głównego agregacji.</span><span class="sxs-lookup"><span data-stu-id="17133-136">You still use the same aggregate root methods to ensure consistency, invariants, and validations within the aggregate.</span></span>

<span data-ttu-id="17133-137">Jednak gdy można utrwalić modelu w bazie danych NoSQL, kod i zmiany interfejsu API, które znacznie w porównaniu do kod programem EF Core lub innego kodu, związane z relacyjnych baz danych.</span><span class="sxs-lookup"><span data-stu-id="17133-137">However, when you persist your model into the NoSQL database, the code and API change dramatically compared to EF Core code or any other code related to relational databases.</span></span>

## <a name="implementing-net-code-targeting-mongodb-and-azure-cosmos-db"></a><span data-ttu-id="17133-138">Wdrażanie kodu platformy .NET dla bazy danych MongoDB i usługi Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="17133-138">Implementing .NET code targeting MongoDB and Azure Cosmos DB</span></span>

### <a name="using-azure-cosmos-db-from-net-containers"></a><span data-ttu-id="17133-139">Za pomocą usługi Azure Cosmos DB z kontenerami .NET</span><span class="sxs-lookup"><span data-stu-id="17133-139">Using Azure Cosmos DB from .NET containers</span></span>

<span data-ttu-id="17133-140">Możesz uzyskać dostęp baz danych Azure Cosmos DB z kodu .NET działających w kontenerach, takich jak z dowolnej aplikacji platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="17133-140">You can access Azure Cosmos DB databases from .NET code running in containers, like from any other .NET application.</span></span> <span data-ttu-id="17133-141">Na przykład Locations.API i Marketing.API mikrousług w ramach aplikacji eShopOnContainers są implementowane, dzięki czemu mogą one wykorzystywać baz danych Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="17133-141">For instance, the Locations.API and Marketing.API microservices in eShopOnContainers are implemented so they can consume Azure Cosmos DB databases.</span></span>

<span data-ttu-id="17133-142">Jednak jest to ograniczenie w usłudze Azure Cosmos DB z platformy Docker rozwoju środowiska punktu widzenia.</span><span class="sxs-lookup"><span data-stu-id="17133-142">However, there’s a limitation in Azure Cosmos DB from a Docker development environment point of view.</span></span> <span data-ttu-id="17133-143">Nawet w przypadku lokalnych [emulatora usługi Azure Cosmos DB](https://docs.microsoft.com/en-us/azure/cosmos-db/local-emulator) można uruchamiać w lokalnym komputerem deweloperskim (np. komputer), jako późnego 2017 po prostu obsługuje on Windows i Linux nie.</span><span class="sxs-lookup"><span data-stu-id="17133-143">Even when there’s a on-premises [Azure Cosmos DB Emulator](https://docs.microsoft.com/en-us/azure/cosmos-db/local-emulator) able to run in a local development machine (like a PC), as of late 2017, it just supports Windows, not Linux.</span></span> 

<span data-ttu-id="17133-144">Istnieje również możliwość uruchomienia tego emulatora na platformy Docker, ale tylko na kontenery Windows z użyciem not kontenerów systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="17133-144">There is also the possibility to run this emulator on Docker, but just on Windows Containers with the , not Linux Containers.</span></span> <span data-ttu-id="17133-145">Jeśli aplikacja jest wdrażana jako kontenerów systemu Linux, ponieważ obecnie jest początkowa przeszkoda dla środowiska programistycznego, nie można wdrożyć systemu Linux i kontenerów Windows w Docker for Windows, które znajdują się w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="17133-145">That is an initial handicap for the development environment if your application is deployed as Linux containers, since, currently, you cannot deploy Linux and Windows Containers on Docker for Windows at the same time.</span></span> <span data-ttu-id="17133-146">Albo wszystkie kontenery wdrażane trzeba dla systemu Linux lub Windows.</span><span class="sxs-lookup"><span data-stu-id="17133-146">Either all containers being deployed have to be for Linux or for Windows.</span></span>  

<span data-ttu-id="17133-147">Idealnym rozwiązaniem i bardziej bezpośredni wdrożenie rozwiązania i testowania aplikacji jest mogli wdrażać swoje systemy baz danych jako kontenery wraz z kontenerów niestandardowych, więc swoje środowiska deweloperskie i testowe zawsze są spójne.</span><span class="sxs-lookup"><span data-stu-id="17133-147">The ideal and more straightforward deployment for a dev/test solution is to be able to deploy your database systems as containers along with your custom containers so your dev/test environments are always consistent.</span></span>

### <a name="use-mongodb-api-for-local-devtest-linuxwindows-containers-plus-azure-cosmos-db"></a><span data-ttu-id="17133-148">Użyj interfejsu API usługi MongoDB dla kontenerów systemu Linux/Windows lokalnego i testowania oraz usługi Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="17133-148">Use MongoDB API for local dev/test Linux/Windows containers plus Azure Cosmos DB</span></span>

<span data-ttu-id="17133-149">Cosmos DB w bazach danych obsługują interfejsu API usługi MongoDB dla platformy .NET, a także natywny protokół przewodowy MongoDB.</span><span class="sxs-lookup"><span data-stu-id="17133-149">Cosmos DB databases support MongoDB API for .NET as well as the native MongoDB wire protocol.</span></span> <span data-ttu-id="17133-150">Oznacza to, że przy użyciu istniejących sterowników aplikacji napisanych dla usługi MongoDB może teraz komunikować się z usługą Cosmos DB i używać baz danych Cosmos DB zamiast bazy danych MongoDB, jak pokazano w rysunek 9-20.</span><span class="sxs-lookup"><span data-stu-id="17133-150">This means that by using existing drivers, your application written for MongoDB can now communicate with Cosmos DB and use Cosmos DB databases instead of MongoDB databases, as shown in Figure 9-20.</span></span>

<span data-ttu-id="17133-151">![](./media/image19.2.png) Rysunek 9-20.</span><span class="sxs-lookup"><span data-stu-id="17133-151">![](./media/image19.2.png) Figure 9-20.</span></span> <span data-ttu-id="17133-152">Dostęp do usługi Azure Cosmos DB przy użyciu interfejsu API usługi MongoDB i protokół</span><span class="sxs-lookup"><span data-stu-id="17133-152">Using MongoDB API and protocol to access Azure Cosmos DB</span></span>

<span data-ttu-id="17133-153">Jest to wygodna metoda weryfikację koncepcji w środowiskach platformy Docker z kontenerami systemu Linux, ponieważ [obrazu platformy Docker z bazy danych MongoDB](https://hub.docker.com/r/_/mongo/) jest obrazem wielu architektury, który obsługuje kontenery platformy Docker w systemie Linux i kontenerów platformy Docker, Windows.</span><span class="sxs-lookup"><span data-stu-id="17133-153">This is a very convenient approach for proof of concepts in Docker environments with Linux containers because the [MongoDB Docker image](https://hub.docker.com/r/_/mongo/) is a multi-arch image that supports Docker Linux containers and Docker Windows containers.</span></span>

<span data-ttu-id="17133-154">Jak pokazano na ilustracji 9-21 za pomocą interfejsu API usługi MongoDB, ramach aplikacji eShopOnContainers obsługuje bazy danych MongoDB, Linux i Windows kontenery dla lokalnego środowiska deweloperskiego, ale następnie można przenieść do skalowalnych, PaaS rozwiązania w chmurze jako usługi Azure Cosmos DB, po prostu [zmiana Parametry połączenia bazy danych MongoDB, aby wskazywała usługę Azure Cosmos DB](https://docs.microsoft.com/en-us/azure/cosmos-db/connect-mongodb-account).</span><span class="sxs-lookup"><span data-stu-id="17133-154">As shown in the image 9-21, by using the MongoDB API, eShopOnContainers supports MongoDB Linux and Windows containers for the local development environment but then, you can move to a scalable, PaaS cloud solution as Azure Cosmos DB by simply [changing the MongoDB connection string to point to Azure Cosmos DB](https://docs.microsoft.com/en-us/azure/cosmos-db/connect-mongodb-account).</span></span> 

<span data-ttu-id="17133-155">![](./media/image20-bis.png) Rysunek 9-21.</span><span class="sxs-lookup"><span data-stu-id="17133-155">![](./media/image20-bis.png) Figure 9-21.</span></span> <span data-ttu-id="17133-156">przy użyciu bazy danych MongoDB kontenery Środowisko deweloperskie i usługi Azure Cosmos DB dla środowiska produkcyjnego w ramach aplikacji eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="17133-156">eShopOnContainers using MongoDB containers for dev-env or Azure Cosmos DB for production</span></span>

<span data-ttu-id="17133-157">Azure Cosmos DB w środowisku produkcyjnym będzie działać w chmurze platformy Azure PaaS i skalowalna usługa.</span><span class="sxs-lookup"><span data-stu-id="17133-157">The production Azure Cosmos DB would be running in Azure’s cloud as a PaaS and scalable service.</span></span>

<span data-ttu-id="17133-158">Niestandardowe kontenerów platformy .NET Core można uruchomić na rozwoju lokalnego hosta platformy Docker, (który jest przy użyciu platformy Docker for Windows na maszynie z systemem Windows 10), lub można wdrożyć w środowisku produkcyjnym, takich jak Kubernetes w usłudze AKS Azure lub usługi Azure Service Fabric.</span><span class="sxs-lookup"><span data-stu-id="17133-158">Your custom .NET Core containers can run on a local development Docker host (that is using Docker for Windows in a Windows 10 machine) or be deployed into a production environment, like Kubernetes in Azure AKS or Azure Service Fabric.</span></span> <span data-ttu-id="17133-159">W tym środowisku drugi będzie wdrożyć tylko kontenerów niestandardowych platformy .NET Core, ale nie w kontenerze bazy danych MongoDB, ponieważ jak się przy użyciu usługi Azure Cosmos DB w chmurze do obsługi danych w środowisku produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="17133-159">In this second environment, you would deploy only the .NET Core custom containers but not the MongoDB container since you’d be using Azure Cosmos DB in the cloud for handling the data in production.</span></span>

<span data-ttu-id="17133-160">Wyczyść korzyść wynikająca z użycia interfejsu API usługi MongoDB jest, że rozwiązania może działać w obu baz danych, bazy danych MongoDB lub Azure Cosmos DB, dzięki migracji do różnych środowisk powinno być łatwe.</span><span class="sxs-lookup"><span data-stu-id="17133-160">A clear benefit of using the MongoDB API is that your solution could run in both database engines, MongoDB or Azure Cosmos DB, so migrations to different environments should be easy.</span></span> <span data-ttu-id="17133-161">Jednak czasami warto używać natywnych interfejsów API (czyli natywnego interfejsu API Cosmos DB), aby w pełni korzystać z możliwości aparatu konkretnej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="17133-161">However, sometimes it is worthwhile to use a native API (that is the native Cosmos DB API) in order to take full advantage of the capabilities of a specific database engine.</span></span>

<span data-ttu-id="17133-162">Aby uzyskać dalsze porównania po prostu przy użyciu bazy danych MongoDB i Cosmos DB w chmurze, zobacz [korzyści z używania usługi Azure Cosmos DB na tej stronie](https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb-introduction).</span><span class="sxs-lookup"><span data-stu-id="17133-162">For further comparison between simply using MongoDB versus Cosmos DB in the cloud, see the [Benefits of using Azure Cosmos DB in this page](https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb-introduction).</span></span> 


### <a name="analyze-your-approach-for-production-applications-mongodb-api-vs-cosmos-db-api"></a><span data-ttu-id="17133-163">Analizuj swoje podejście przez aplikacje produkcyjne: vs interfejsu API usługi MongoDB. Interfejs API usługi cosmos DB</span><span class="sxs-lookup"><span data-stu-id="17133-163">Analyze your approach for production applications: MongoDB API vs. Cosmos DB API</span></span>

<span data-ttu-id="17133-164">W ramach aplikacji eShopOnContainers, firma Microsoft korzysta z interfejsu API usługi MongoDB ponieważ priorytetu było całkowicie w środowisku spójne tworzenie i testowanie przy użyciu bazy danych NoSQL, która może również działać z usługą Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="17133-164">In eShopOnContainers, we’re using MongoDB API because our priority was fundamentally to have a consistent dev/test environment using a NoSQL database that could also work with Azure Cosmos DB.</span></span>

<span data-ttu-id="17133-165">Jednakże jeśli planujesz uzyskiwanie dostępu do usługi Azure Cosmos DB na platformie Azure dla aplikacji produkcyjnych za pomocą interfejsu API bazy danych MongoDB, możesz powinieneś przeanalizować, różnice w możliwości i wydajność podczas dostępu do baz danych Azure Cosmos DB w porównaniu do przy użyciu natywnych przy użyciu interfejsu API usługi MongoDB Interfejs API usługi Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="17133-165">However, if you planning to use MongoDB API to access Azure Cosmos DB in Azure for production applications, you should analyze the differences in capabilities and performance when using MongoDB API to access Azure Cosmos DB databases compared to using the native Azure Cosmos DB API.</span></span> <span data-ttu-id="17133-166">Jeśli jest on podobny można użyć interfejsu API usługi MongoDB i skorzystać z zalet obsługi dwóch baz danych NoSQL, w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="17133-166">If it is similar you can use MongoDB API, and you get the benefit of supporting two NoSQL database engines at the same time.</span></span> 

<span data-ttu-id="17133-167">Można także użyć klastry bazy danych MongoDB jako produkcyjnej bazy danych w chmurze platformy Azure, za pomocą [bazy danych MongoDB usługi Azure Service](https://www.mongodb.com/scale/mongodb-azure-service).</span><span class="sxs-lookup"><span data-stu-id="17133-167">You could also use MongoDB clusters as the production database in Azure’s cloud, too, with [MongoDB Azure Service](https://www.mongodb.com/scale/mongodb-azure-service).</span></span> <span data-ttu-id="17133-168">Ale nie jest obsługiwane przez firmę Microsoft usługa PaaS.</span><span class="sxs-lookup"><span data-stu-id="17133-168">But that is not a PaaS service provided by Microsoft.</span></span> <span data-ttu-id="17133-169">W tym przypadku hostingu platformy Azure jest po prostu rozwiązanie pochodzące z bazy danych MongoDB.</span><span class="sxs-lookup"><span data-stu-id="17133-169">In this case, Azure is just hosting that solution coming from MongoDB.</span></span>

<span data-ttu-id="17133-170">Zasadniczo jest to po prostu zastrzeżenie, podając nie należy zawsze używać interfejsu API usługi MongoDB względem usługi Azure Cosmos DB, ile My mieliśmy, w ramach aplikacji eShopOnContainers, ponieważ jest to wygodne wybór dla kontenerów systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="17133-170">Basically, this is just a disclaimer stating that you shouldn’t always use MongoDB API against Azure Cosmos DB, as we did in eShopOnContainers because it was a convenient choice for Linux containers.</span></span> <span data-ttu-id="17133-171">Decyzja powinna być oparta na konkretnych potrzeb i testy, które należy wykonać dla aplikacji produkcyjnych.</span><span class="sxs-lookup"><span data-stu-id="17133-171">The decision should be based on the specific needs and tests you need to do for your production application.</span></span>  

### <a name="the-code-using-mongodb-api-in-net-core-applications"></a><span data-ttu-id="17133-172">Ten kod: przy użyciu interfejsu API usługi MongoDB w aplikacjach platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="17133-172">The code: Using MongoDB API in .NET Core applications</span></span>

<span data-ttu-id="17133-173">Interfejsu API usługi MongoDB dla platformy .NET jest oparty na pakietach NuGet, należy dodać do swoich projektów, takich jak Locations.API wyświetlane w rysunek 9-22.</span><span class="sxs-lookup"><span data-stu-id="17133-173">MongoDB API for .NET is based on NuGet packages that you need to add to your projects, like the Locations.API shown in Figure 9-22.</span></span>

<span data-ttu-id="17133-174">![](./media/image21-bis.png) Rysunek 9-22.</span><span class="sxs-lookup"><span data-stu-id="17133-174">![](./media/image21-bis.png) Figure 9-22.</span></span> <span data-ttu-id="17133-175">NuGet interfejsu API usługi MongoDB pakietów odwołań w projekcie platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="17133-175">MongoDB API NuGet packages references in a .NET Core project</span></span>

<span data-ttu-id="17133-176">Teraz Zbadaj kod w poniższych sekcjach.</span><span class="sxs-lookup"><span data-stu-id="17133-176">Let's investigate the code in the following sections.</span></span>

#### <a name="a-model-used-by-mongodb-api"></a><span data-ttu-id="17133-177">Model używany przez interfejs API usługi MongoDB</span><span class="sxs-lookup"><span data-stu-id="17133-177">A Model used by MongoDB API</span></span>

<span data-ttu-id="17133-178">Najpierw należy zdefiniować model, w którym będą przechowywane dane pochodzące z bazy danych w obszarze pamięci aplikacji.</span><span class="sxs-lookup"><span data-stu-id="17133-178">First, you need to define a model that will hold the data coming from the database in your application’s memory space.</span></span> <span data-ttu-id="17133-179">Oto przykład model, używane dla lokalizacji, w ramach aplikacji eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="17133-179">Here’s an example of the model used for Locations at eShopOnContainers.</span></span>

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

<span data-ttu-id="17133-180">Widać, że nie ma kilka atrybutów i typy pochodzące z pakietów NuGet bazy danych MongoDB.</span><span class="sxs-lookup"><span data-stu-id="17133-180">You can see there are a few attributes and types coming from the MongoDB NuGet packages.</span></span>

<span data-ttu-id="17133-181">Bazy danych NoSQL są zazwyczaj bardzo dobrze nadaje się do pracy z danymi hierarchicznymi nierelacyjnych.</span><span class="sxs-lookup"><span data-stu-id="17133-181">NoSQL databases are usually very well suited for working with non-relational hierarchical data.</span></span> <span data-ttu-id="17133-182">W tym przykładzie używamy typów bazy danych MongoDB, szczególnie wprowadzone dla lokalizacji geograficznej, takich jak `GeoJson2DGeographicCoordinates`.</span><span class="sxs-lookup"><span data-stu-id="17133-182">In this example, we are using MongoDB types especially made for geo-locations, like `GeoJson2DGeographicCoordinates`.</span></span>

#### <a name="retrieve-the-database-and-the-collection"></a><span data-ttu-id="17133-183">Pobieranie bazy danych i kolekcji</span><span class="sxs-lookup"><span data-stu-id="17133-183">Retrieve the database and the collection</span></span>

<span data-ttu-id="17133-184">W ramach aplikacji eShopOnContainers utworzyliśmy kontekstu niestandardowej bazy danych, gdzie wdrażamy kod, aby pobrać bazy danych i MongoCollections, tak jak w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="17133-184">In eShopOnContainers, we have created a custom database context where we implement the code to retrieve the database and the MongoCollections, as in the following code.</span></span>

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

#### <a name="retrieve-the-data"></a><span data-ttu-id="17133-185">Pobieranie danych</span><span class="sxs-lookup"><span data-stu-id="17133-185">Retrieve the data</span></span>

<span data-ttu-id="17133-186">W kodzie języka C#, takie jak kontrolerów internetowych interfejsów API lub implementację niestandardową repozytoriów można napisać kod podobny do następującego podczas wykonywania zapytania za pomocą interfejsu API usługi MongoDB.</span><span class="sxs-lookup"><span data-stu-id="17133-186">In C# code, like Web API controllers or custom Repositories implementation, you can write similar code to the following when querying through the MongoDB API.</span></span> <span data-ttu-id="17133-187">Należy pamiętać, że `_context` obiekt jest wystąpieniem poprzedniego `LocationsContext` klasy.</span><span class="sxs-lookup"><span data-stu-id="17133-187">Note that the `_context` object is an instance of the previous `LocationsContext` class.</span></span>

```csharp
public async Task<Locations> GetAsync(int locationId)
{
    var filter = Builders<Locations>.Filter.Eq("LocationId", locationId);
    return await _context.Locations
                            .Find(filter)
                            .FirstOrDefaultAsync();
}
```

#### <a name="use-an-env-var-in-the-docker-composeoverrideyml-file-for-the-mongodb-connection-string"></a><span data-ttu-id="17133-188">Użyj env-var w pliku docker-compose.override.yml dla parametrów połączenia bazy danych MongoDB</span><span class="sxs-lookup"><span data-stu-id="17133-188">Use an env-var in the docker-compose.override.yml file for the MongoDB connection string</span></span>

<span data-ttu-id="17133-189">Podczas tworzenia obiektu klucza MongoClient, potrzebuje podstawowych parametr, który dokładnie `ConnectionString` parametrem odpowiednią bazę danych.</span><span class="sxs-lookup"><span data-stu-id="17133-189">When creating a MongoClient object, it needs a fundamental parameter which is precisely the `ConnectionString` parameter pointing to the right database.</span></span> <span data-ttu-id="17133-190">W przypadku ramach aplikacji eShopOnContainers parametry połączenia mogą wskazać, lokalny kontener platformy Docker z bazy danych MongoDB lub z bazą danych Azure Cosmos DB "produkcyjne".</span><span class="sxs-lookup"><span data-stu-id="17133-190">In the case of eShopOnContainers, the connection string can point to a local MongoDB Docker container or to a “production” Azure Cosmos DB database.</span></span>  <span data-ttu-id="17133-191">Te parametry połączenia pochodzą ze zmiennych środowiskowych zdefiniowanych w `docker-compose.override.yml` pliki używane podczas wdrażania za pomocą docker-compose lub Visual Studio, tak jak w poniższym kodzie yml.</span><span class="sxs-lookup"><span data-stu-id="17133-191">That connection string comes from the environment variables defined in the `docker-compose.override.yml` files used when deploying with docker-compose or Visual Studio, as in the following yml code.</span></span>

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

<span data-ttu-id="17133-192">`ConnectionString` Zmiennej środowiskowej zostanie rozwiązany w ten sposób: Jeśli `ESHOP_AZURE_COSMOSDB` zmienna globalna jest zdefiniowany w `.env` pliku przy użyciu parametrów połączenia usługi Azure Cosmos DB, użyje on dostępu do bazy danych Azure Cosmos DB w chmurze.</span><span class="sxs-lookup"><span data-stu-id="17133-192">The `ConnectionString` environment variable is resolved this way: If the `ESHOP_AZURE_COSMOSDB` global variable is defined in the `.env` file with the Azure Cosmos DB connection string, it will use it to access the Azure Cosmos DB database in the cloud.</span></span> 

<span data-ttu-id="17133-193">Poniższy kod przedstawia `.env` plików za pomocą usługi Azure Cosmos DB globalnego zmienna środowiskowa parametrów połączenia, zgodnie z implementacją w ramach aplikacji eShopOnContainers:</span><span class="sxs-lookup"><span data-stu-id="17133-193">The following code shows the `.env` file with the Azure Cosmos DB connection string global environment variable, as implemented in eShopOnContainers:</span></span>

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

<span data-ttu-id="17133-194">Powinien usuń znaczniki komentarza wierszu ESHOP_AZURE_COSMOSDB i aktualizacji za pomocą usługi Azure Cosmos DB parametry połączenia uzyskane w witrynie Azure portal jako wyjaśnione w [połączyć aplikację MongoDB w usłudze Azure Cosmos DB](https://docs.microsoft.com/en-us/azure/cosmos-db/connect-mongodb-account).</span><span class="sxs-lookup"><span data-stu-id="17133-194">You should uncomment the ESHOP_AZURE_COSMOSDB line and update it with your Azure Cosmos DB connection string obtained from the Azure portal as explained in [Connect a MongoDB application to Azure Cosmos DB](https://docs.microsoft.com/en-us/azure/cosmos-db/connect-mongodb-account).</span></span>

<span data-ttu-id="17133-195">Jeśli `ESHOP_AZURE_COSMOSDB` zmienna globalna jest pusta, co oznacza, że zostanie ona opatrzona komentarzem na zewnątrz w `.env` pliku, kontener używa domyślne parametry połączenia bazy danych MongoDB wskazujący lokalny kontener bazy danych MongoDB, wdrożonych w ramach aplikacji eShopOnContainers, który nosi nazwę `nosql.data`, jak pokazano w poniższym kodzie yml.</span><span class="sxs-lookup"><span data-stu-id="17133-195">If the `ESHOP_AZURE_COSMOSDB` global variable is empty, meaning that it is commented out in the `.env` file, then the container uses a default MongoDB connection string pointing to the local MongoDB container deployed in eShopOnContainers which is named `nosql.data`, as shown in the following .yml code.</span></span> 

#### <a name="additional-resources"></a><span data-ttu-id="17133-196">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="17133-196">Additional resources</span></span>

-   <span data-ttu-id="17133-197">**Modelowanie danych dokumentu dla baz danych NoSQL**
    [*https://docs.microsoft.com/en-us/azure/cosmos-db/modeling-data*](https://docs.microsoft.com/en-us/azure/cosmos-db/modeling-data)</span><span class="sxs-lookup"><span data-stu-id="17133-197">**Modeling document data for NoSQL databases**
[*https://docs.microsoft.com/en-us/azure/cosmos-db/modeling-data*](https://docs.microsoft.com/en-us/azure/cosmos-db/modeling-data)</span></span>

-   <span data-ttu-id="17133-198">**Vaughn Vernon. Idealne rozwiązanie oparte na domenie projektu agregacji Store?**
    [*https://vaughnvernon.co/?p=942*](https://vaughnvernon.co/?p=942)</span><span class="sxs-lookup"><span data-stu-id="17133-198">**Vaughn Vernon. The Ideal Domain-Driven Design Aggregate Store?**
[*https://vaughnvernon.co/?p=942*](https://vaughnvernon.co/?p=942)</span></span>

-   <span data-ttu-id="17133-199">**Wprowadzenie do usługi Azure Cosmos DB: interfejs API systemu MongoDB** 
    [*https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb-introduction*](https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb-introduction)</span><span class="sxs-lookup"><span data-stu-id="17133-199">**Introduction to Azure Cosmos DB: API for MongoDB** 
[*https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb-introduction*](https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb-introduction)</span></span>

-   <span data-ttu-id="17133-200">**Azure Cosmos DB: Tworzenie aplikacji internetowej interfejsu API usługi MongoDB przy użyciu platformy .NET i witryny Azure portal** 
    [\*https://docs.microsoft.com/en-us/azure/cosmos-db/create-mongodb-dotnet \*](https://docs.microsoft.com/en-us/azure/cosmos-db/create-mongodb-dotnet )</span><span class="sxs-lookup"><span data-stu-id="17133-200">**Azure Cosmos DB: Build a MongoDB API web app with .NET and the Azure portal** 
[\*https://docs.microsoft.com/en-us/azure/cosmos-db/create-mongodb-dotnet \*](https://docs.microsoft.com/en-us/azure/cosmos-db/create-mongodb-dotnet )</span></span>

-   <span data-ttu-id="17133-201">**Korzystanie z emulatora usługi Azure Cosmos DB do lokalnego tworzenia i testowania** 
    [*https://docs.microsoft.com/en-us/azure/cosmos-db/local-emulator*](https://docs.microsoft.com/en-us/azure/cosmos-db/local-emulator)</span><span class="sxs-lookup"><span data-stu-id="17133-201">**Use the Azure Cosmos DB Emulator for local development and testing** 
[*https://docs.microsoft.com/en-us/azure/cosmos-db/local-emulator*](https://docs.microsoft.com/en-us/azure/cosmos-db/local-emulator)</span></span>

-   <span data-ttu-id="17133-202">**Łączenie aplikacji bazy danych MongoDB w usłudze Azure Cosmos DB** 
    [*https://docs.microsoft.com/en-us/azure/cosmos-db/connect-mongodb-account*](https://docs.microsoft.com/en-us/azure/cosmos-db/connect-mongodb-account)</span><span class="sxs-lookup"><span data-stu-id="17133-202">**Connect a MongoDB application to Azure Cosmos DB** 
[*https://docs.microsoft.com/en-us/azure/cosmos-db/connect-mongodb-account*](https://docs.microsoft.com/en-us/azure/cosmos-db/connect-mongodb-account)</span></span>

-   <span data-ttu-id="17133-203">**Obraz Cosmos DB Emulator Docker (kontener Windows)** 
    [*https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator/*](https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator/)</span><span class="sxs-lookup"><span data-stu-id="17133-203">**The Cosmos DB Emulator Docker image (Windows Container)** 
[*https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator/*](https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator/)</span></span>

-   <span data-ttu-id="17133-204">**Obraz platformy Docker z bazy danych MongoDB (Linux i kontenerów Windows)** 
    [*https://hub.docker.com/r/_/mongo/*](https://hub.docker.com/r/_/mongo/)</span><span class="sxs-lookup"><span data-stu-id="17133-204">**The MongoDB Docker image (Linux and Windows Container)** 
[*https://hub.docker.com/r/_/mongo/*](https://hub.docker.com/r/_/mongo/)</span></span>

-   <span data-ttu-id="17133-205">**Korzystanie z programu MongoChef (z programu z programu Studio 3T) za pomocą usługi Azure Cosmos DB: interfejs API dla konta bazy danych MongoDB** 
    [*https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb-mongochef*](https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb-mongochef)</span><span class="sxs-lookup"><span data-stu-id="17133-205">**Use MongoChef (Studio 3T) with an Azure Cosmos DB: API for MongoDB account** 
[*https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb-mongochef*](https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb-mongochef)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="17133-206">[Poprzednie](infrastructure-persistence-layer-implemenation-entity-framework-core.md)
[dalej](microservice-application-layer-web-api-design.md)</span><span class="sxs-lookup"><span data-stu-id="17133-206">[Previous](infrastructure-persistence-layer-implemenation-entity-framework-core.md)
[Next](microservice-application-layer-web-api-design.md)</span></span>
