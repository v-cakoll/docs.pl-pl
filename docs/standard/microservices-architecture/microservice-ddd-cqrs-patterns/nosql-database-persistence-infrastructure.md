---
title: "Przy użyciu bazy danych NoSQL jako infrastruktury trwałości"
description: "Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Przy użyciu bazy danych NoSQL jako infrastruktury trwałości"
keywords: "Docker, Mikrousług, ASP.NET, kontenera"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: e4b63511069b89cc5761ce7ed64f09e9035a56a3
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="using-nosql-databases-as-a-persistence-infrastructure"></a><span data-ttu-id="b3d96-104">Przy użyciu bazy danych NoSQL jako infrastruktury trwałości</span><span class="sxs-lookup"><span data-stu-id="b3d96-104">Using NoSQL databases as a persistence infrastructure</span></span>

<span data-ttu-id="b3d96-105">Korzystając z bazy danych NoSQL dla warstwy danych Twojej infrastruktury, należy zwykle nie należy używać ORM, takich jak Entity Framework Core.</span><span class="sxs-lookup"><span data-stu-id="b3d96-105">When you use NoSQL databases for your infrastructure data tier, you typically do not use an ORM like Entity Framework Core.</span></span> <span data-ttu-id="b3d96-106">Zamiast niej używać interfejsu API dostarczonych przez aparat NoSQL, takie jak bazy danych Azure rozwiązania Cosmos, bazy danych MongoDB, Cassandra, RavenDB, CouchDB lub tabel magazynu Azure.</span><span class="sxs-lookup"><span data-stu-id="b3d96-106">Instead you use the API provided by the NoSQL engine, such as Azure Cosmos DB, MongoDB, Cassandra, RavenDB, CouchDB, or Azure Storage Tables.</span></span>

<span data-ttu-id="b3d96-107">Jednak podczas korzystania z bazy danych NoSQL, szczególnie zorientowane na dokument bazy danych, takich jak bazy danych Azure rozwiązania Cosmos, CouchDB lub RavenDB, sposób projektowania modelu za pomocą wartości zagregowanych DDD jest częściowo podobnie jak można to zrobić w podstawowej EF w odniesieniu do identyfikacji Łączny katalogów głównych klas jednostek podrzędnych klasy i wartość obiektu.</span><span class="sxs-lookup"><span data-stu-id="b3d96-107">However, when you use a NoSQL database, especially a document-oriented database like Azure Cosmos DB, CouchDB, or RavenDB, the way you design your model with DDD aggregates is partially similar to how you can do it in EF Core, in regards to the identification of aggregate roots, child entity classes, and value object classes.</span></span> <span data-ttu-id="b3d96-108">Ale ostatecznie wpłynie wybranych baz danych w projekcie.</span><span class="sxs-lookup"><span data-stu-id="b3d96-108">But, ultimately, the database selection will impact in your design.</span></span>

<span data-ttu-id="b3d96-109">Korzystając z bazy danych zorientowane na dokumentu, można zaimplementować agregacji jako pojedynczego dokumentu zserializowane w formacie JSON lub innego formatu.</span><span class="sxs-lookup"><span data-stu-id="b3d96-109">When you use a document-oriented database, you implement an aggregate as a single document, serialized in JSON or another format.</span></span> <span data-ttu-id="b3d96-110">Jednak użycie bazy danych jest przezroczysty z domeny modelu kodu punktu widzenia.</span><span class="sxs-lookup"><span data-stu-id="b3d96-110">However, the use of the database is transparent from a domain model code point of view.</span></span> <span data-ttu-id="b3d96-111">Podczas korzystania z bazy danych NoSQL, nadal używasz klas jednostek i klasy głównym agregacji, ale większą elastyczność niż przy użyciu EF Core, ponieważ nie jest relacyjna trwałość.</span><span class="sxs-lookup"><span data-stu-id="b3d96-111">When using a NoSQL database, you still are using entity classes and aggregate root classes, but with more flexibility than when using EF Core because the persistence is not relational.</span></span>

<span data-ttu-id="b3d96-112">Różnica polega na tym w sposób utrwalić modelu.</span><span class="sxs-lookup"><span data-stu-id="b3d96-112">The difference is in how you persist that model.</span></span> <span data-ttu-id="b3d96-113">Jeśli zaimplementowano modelu domeny oparte na klasach jednostki POCO niezależny od trwałości infrastruktury może prawdopodobnie może przenieść się do infrastruktury różnych trwałości, nawet od relacyjne do NoSQL.</span><span class="sxs-lookup"><span data-stu-id="b3d96-113">If you implemented your domain model based on POCO entity classes, agnostic to the infrastructure persistence, it might look like you could move to a different persistence infrastructure, even from relational to NoSQL.</span></span> <span data-ttu-id="b3d96-114">Który nie powinien być poznasz.</span><span class="sxs-lookup"><span data-stu-id="b3d96-114">However, that should not be your goal.</span></span> <span data-ttu-id="b3d96-115">Zawsze są ograniczenia w różnych baz danych przeprowadzi wypychanie możesz ponownie, nie można mieć ten sam model dla relacyjnego lub bazy danych NoSQL.</span><span class="sxs-lookup"><span data-stu-id="b3d96-115">There are always constraints in the different databases will push you back, so you will not be able to have the same model for relational or NoSQL databases.</span></span> <span data-ttu-id="b3d96-116">Zmiana modeli trwałości nie jest prosta, ponieważ transakcje i operacji utrwalania będą bardzo różnią się.</span><span class="sxs-lookup"><span data-stu-id="b3d96-116">Changing persistence models would not be trivial, because transactions and persistence operations will be very different.</span></span>

<span data-ttu-id="b3d96-117">Na przykład w bazie danych zorientowane na dokument jest poprawny dla elementu głównego agregacji ma wiele właściwości kolekcji podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="b3d96-117">For example, in a document-oriented database, it is okay for an aggregate root to have multiple child collection properties.</span></span> <span data-ttu-id="b3d96-118">Relacyjnej bazy danych zapytań wiele właściwości kolekcji podrzędnych jest awful, ponieważ wracając instrukcję SQL wszystkie związek z EF.</span><span class="sxs-lookup"><span data-stu-id="b3d96-118">In a relational database, querying multiple child collection properties is awful, because you get a UNION ALL SQL statement back from EF.</span></span> <span data-ttu-id="b3d96-119">O tym samym modelu domeny relacyjnych baz danych lub bazy danych NoSQL nie jest proste, a nie należy dążyć.</span><span class="sxs-lookup"><span data-stu-id="b3d96-119">Having the same domain model for relational databases or NoSQL databases is not simple, and you should not try it.</span></span> <span data-ttu-id="b3d96-120">Masz naprawdę projektowania modelu za pomocą zrozumienia sposobu danych będzie można używać w każdej określonej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="b3d96-120">You really have to design your model with an understanding of how the data is going to be used in each particular database.</span></span>

<span data-ttu-id="b3d96-121">Korzyści, w przypadku korzystania z bazy danych NoSQL to jednostek więcej nieznormalizowany, dlatego nie należy ustawiać mapowania tabeli.</span><span class="sxs-lookup"><span data-stu-id="b3d96-121">A benefit when using NoSQL databases is that the entities are more denormalized, so you do not set a table mapping.</span></span> <span data-ttu-id="b3d96-122">Model domeny może być bardziej elastyczne niż przy użyciu relacyjnej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="b3d96-122">Your domain model can be more flexible than when using a relational database.</span></span>

<span data-ttu-id="b3d96-123">Podczas projektowania modelu domeny wartościami zagregowanymi, w oparciu przechodzenia do NoSQL i zorientowane na dokument baz danych może być łatwiejsze niż przy użyciu relacyjnej bazy danych, ponieważ agregacje, którą można zaprojektować są podobne do serializacji dokumenty w bazie danych zorientowane na dokument.</span><span class="sxs-lookup"><span data-stu-id="b3d96-123">When you design your domain model based on aggregates, moving to NoSQL and document-oriented databases might be even easier than using a relational database, because the aggregates you design are similar to serialized documents in a document-oriented database.</span></span> <span data-ttu-id="b3d96-124">Następnie można uwzględnić w tych "torbach" wszystkich informacji potrzebnych do tej agregacji.</span><span class="sxs-lookup"><span data-stu-id="b3d96-124">Then you can include in those “bags” all the information you might need for that aggregate.</span></span>

<span data-ttu-id="b3d96-125">Na przykład następujący kod JSON jest przykładowa implementacja agregacji kolejności podczas korzystania z bazy danych zorientowane na dokument.</span><span class="sxs-lookup"><span data-stu-id="b3d96-125">For instance, the following JSON code is a sample implementation of an order aggregate when using a document-oriented database.</span></span> <span data-ttu-id="b3d96-126">Jest on podobny do agregacji kolejności zaimplementowano w przykładowym eShopOnContainers, ale bez użycia rdzeni EF poniżej.</span><span class="sxs-lookup"><span data-stu-id="b3d96-126">It is similar to the order aggregate we implemented in the eShopOnContainers sample, but without using EF Core underneath.</span></span>

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

<span data-ttu-id="b3d96-127">Jeśli używasz C\# modelu do zaimplementowania agregacji, które mają być używane przez ekran podobny do rozwiązania Cosmos DB zestaw SDK usługi Azure, agregacji jest podobny do C\# klasy POCO używane EF podstawowych.</span><span class="sxs-lookup"><span data-stu-id="b3d96-127">When you use a C\# model to implement the aggregate to be used by something like the Azure Cosmos DB SDK, the aggregate is similar to the C\# POCO classes used with EF Core.</span></span> <span data-ttu-id="b3d96-128">Jest to różnica w taki sposób, aby użyć ich z warstwy aplikacji i infrastruktury, zgodnie z poniższym kodem:</span><span class="sxs-lookup"><span data-stu-id="b3d96-128">The difference is in the way to use them from the application and infrastructure layers, as in the following code:</span></span>

```csharp
// C# EXAMPLE OF AN ORDER AGGREGATE BEING PERSISTED WITH DOCUMENTDB API
// *** Domain Model Code ***
// Aggregate: Create an Order object with its child entities and/or value objects.
// Then, use AggregateRoot’s methods to add the nested objects so invariants and
// logic is consistent across the nested properties (value objects and entities).
// This can be saved as JSON as is without converting into rows/columns.
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

OrderItem orderItem2 = new OrderItem
{
    Id = 20170012,
    ProductId = "123457",
    ProductName = ".NET Mug",
    UnitPrice = 15,
    Units = 1,
    Discount = 0;
};

//Using methods with domain logic within the entity. No anemic-domain model
orderAggregate.AddOrderItem(orderItem1);
orderAggregate.AddOrderItem(orderItem2);

// *** End of Domain Model Code ***
//...
// *** Infrastructure Code using Cosmos DB Client API ***
Uri collectionUri = UriFactory.CreateDocumentCollectionUri(databaseName,
    collectionName);

await client.CreateDocumentAsync(collectionUri, order);

// As your app evolves, let's say your object has a new schema. You can insert
// OrderV2 objects without any changes to the database tier.
Order2 newOrder = GetOrderV2Sample("IdForSalesOrder2");
await client.CreateDocumentAsync(collectionUri, newOrder);
```

<span data-ttu-id="b3d96-129">Widać, że sposób pracy z modelem domeny może być podobny do sposobu używania jej w Twojej warstwy modelu domeny po EF infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="b3d96-129">You can see that the way you work with your domain model can be similar to the way you use it in your domain model layer when the infrastructure is EF.</span></span> <span data-ttu-id="b3d96-130">Do zapewnienia spójności, invariants i sprawdzanie poprawności w agregacji są nadal używać tych samych metod głównego agregacji.</span><span class="sxs-lookup"><span data-stu-id="b3d96-130">You still use the same aggregate root methods to ensure consistency, invariants, and validations within the aggregate.</span></span>

<span data-ttu-id="b3d96-131">Jednak gdy można utrwalić modelu do bazy danych NoSQL, kod i zmiany interfejsu API znacznie w porównaniu do kodu EF Core lub inny kod powiązany relacyjnych baz danych.</span><span class="sxs-lookup"><span data-stu-id="b3d96-131">However, when you persist your model into the NoSQL database, the code and API change dramatically compared to EF Core code or any other code related to relational databases.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="b3d96-132">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="b3d96-132">Additional resources</span></span>

-   <span data-ttu-id="b3d96-133">**Modelowanie danych w usłudze DocumentDB**
    [*https://docs.microsoft.com/azure/documentdb/documentdb-modeling-data*](https://docs.microsoft.com/azure/documentdb/documentdb-modeling-data)</span><span class="sxs-lookup"><span data-stu-id="b3d96-133">**Modeling data in DocumentDB**
[*https://docs.microsoft.com/azure/documentdb/documentdb-modeling-data*](https://docs.microsoft.com/azure/documentdb/documentdb-modeling-data)</span></span>

-   <span data-ttu-id="b3d96-134">**Vaughn Vernon. Nadaje się doskonale oparte na domenie projektu agregacji sklepu? ** 
     [ *https://vaughnvernon.co/?p=942*](https://vaughnvernon.co/?p=942)</span><span class="sxs-lookup"><span data-stu-id="b3d96-134">**Vaughn Vernon. The Ideal Domain-Driven Design Aggregate Store?**
[*https://vaughnvernon.co/?p=942*](https://vaughnvernon.co/?p=942)</span></span>

-   <span data-ttu-id="b3d96-135">**Funkcja trwałość magazynu zdarzeń dla platformy .NET.**</span><span class="sxs-lookup"><span data-stu-id="b3d96-135">**A persistence agnostic Event Store for .NET.**</span></span> <span data-ttu-id="b3d96-136">Repozytorium GitHub.</span><span class="sxs-lookup"><span data-stu-id="b3d96-136">GitHub repo.</span></span>
    [<span data-ttu-id="b3d96-137">*https://github.com/NEventStore/NEventStore*</span><span class="sxs-lookup"><span data-stu-id="b3d96-137">*https://github.com/NEventStore/NEventStore*</span></span>](https://github.com/NEventStore/NEventStore)


>[!div class="step-by-step"]
<span data-ttu-id="b3d96-138">[Poprzednie] (infrastructure-persistence-layer-implemenation-entity-framework-core.md) [dalej] (microservice-application-layer-web-api-design.md)</span><span class="sxs-lookup"><span data-stu-id="b3d96-138">[Previous] (infrastructure-persistence-layer-implemenation-entity-framework-core.md) [Next] (microservice-application-layer-web-api-design.md)</span></span>
