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

Jeśli używasz C\# modelu do zaimplementowania agregacji, które mają być używane przez ekran podobny do rozwiązania Cosmos DB zestaw SDK usługi Azure, agregacji jest podobny do C\# klasy POCO używane EF podstawowych. Jest to różnica w taki sposób, aby użyć ich z warstwy aplikacji i infrastruktury, zgodnie z poniższym kodem:

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

Widać, że sposób pracy z modelem domeny może być podobny do sposobu używania jej w Twojej warstwy modelu domeny po EF infrastruktury. Do zapewnienia spójności, invariants i sprawdzanie poprawności w agregacji są nadal używać tych samych metod głównego agregacji.

Jednak gdy można utrwalić modelu do bazy danych NoSQL, kod i zmiany interfejsu API znacznie w porównaniu do kodu EF Core lub inny kod powiązany relacyjnych baz danych.

#### <a name="additional-resources"></a>Dodatkowe zasoby

-   **Modelowanie danych w usłudze DocumentDB**
    [*https://docs.microsoft.com/azure/documentdb/documentdb-modeling-data*](https://docs.microsoft.com/azure/documentdb/documentdb-modeling-data)

-   **Vaughn Vernon. Nadaje się doskonale oparte na domenie projektu agregacji sklepu? ** 
     [ *https://vaughnvernon.co/?p=942*](https://vaughnvernon.co/?p=942)

-   **Funkcja trwałość magazynu zdarzeń dla platformy .NET.** Repozytorium GitHub.
    [*https://github.com/NEventStore/NEventStore*](https://github.com/NEventStore/NEventStore)


>[!div class="step-by-step"]
[Poprzednie] (infrastructure-persistence-layer-implemenation-entity-framework-core.md) [dalej] (microservice-application-layer-web-api-design.md)
