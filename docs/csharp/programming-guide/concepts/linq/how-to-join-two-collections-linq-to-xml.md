---
title: Jak sprzęgać dwie kolekcje (LINQ to XML) (C#)
description: Ten przykład w języku C# łączy elementy w LINQ to XML z innymi elementami i generuje nowy dokument XML.
ms.date: 07/20/2015
ms.assetid: 7b817ede-911a-4cff-9dd3-639c3fc228c9
ms.openlocfilehash: 10792ed4907e778b41821c9b32574bd8fc0ab35f
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104994"
---
# <a name="how-to-join-two-collections-linq-to-xml-c"></a><span data-ttu-id="f8543-103">Jak sprzęgać dwie kolekcje (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="f8543-103">How to join two collections (LINQ to XML) (C#)</span></span>

<span data-ttu-id="f8543-104">Element lub atrybut w dokumencie XML czasami może odwoływać się do innego elementu lub atrybutu.</span><span class="sxs-lookup"><span data-stu-id="f8543-104">An element or attribute in an XML document can sometimes refer to another element or attribute.</span></span> <span data-ttu-id="f8543-105">[Przykładowy plik XML: Customers i Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md) dokument XML zawiera listę klientów i listę zamówień.</span><span class="sxs-lookup"><span data-stu-id="f8543-105">For example, the [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md) XML document contains a list of customers and a list of orders.</span></span> <span data-ttu-id="f8543-106">Każdy `Customer` element zawiera `CustomerID` atrybut.</span><span class="sxs-lookup"><span data-stu-id="f8543-106">Each `Customer` element contains a `CustomerID` attribute.</span></span> <span data-ttu-id="f8543-107">Każdy `Order` element zawiera `CustomerID` element.</span><span class="sxs-lookup"><span data-stu-id="f8543-107">Each `Order` element contains a `CustomerID` element.</span></span> <span data-ttu-id="f8543-108">`CustomerID`Element w każdym porządku odwołuje się do `CustomerID` atrybutu w kliencie.</span><span class="sxs-lookup"><span data-stu-id="f8543-108">The `CustomerID` element in each order refers to the `CustomerID` attribute in a customer.</span></span>

<span data-ttu-id="f8543-109">[Przykładowy plik XSD tematu: klienci i zamówienia](./sample-xsd-file-customers-and-orders1.md) zawierają XSD, których można użyć do zweryfikowania tego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="f8543-109">The topic [Sample XSD File: Customers and Orders](./sample-xsd-file-customers-and-orders1.md) contains an XSD that can be used to validate this document.</span></span> <span data-ttu-id="f8543-110">Używa `xs:key` i `xs:keyref` funkcji XSD, aby określić, że `CustomerID` atrybut `Customer` elementu jest kluczem i aby ustanowić relację między `CustomerID` elementem w każdym `Order` elemencie a `CustomerID` atrybutem w każdym `Customer` elemencie.</span><span class="sxs-lookup"><span data-stu-id="f8543-110">It uses the `xs:key` and `xs:keyref` features of XSD to establish that the `CustomerID` attribute of the `Customer` element is a key, and to establish a relationship between the `CustomerID` element in each `Order` element and the `CustomerID` attribute in each `Customer` element.</span></span>

<span data-ttu-id="f8543-111">Za pomocą programu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] można korzystać z tej relacji przy użyciu `join` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="f8543-111">With [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can take advantage of this relationship by using the `join` clause.</span></span>

<span data-ttu-id="f8543-112">Ponieważ nie ma dostępnego indeksu, takie dołączenie będzie miało niską wydajność w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="f8543-112">Because there is no index available, such joining will have poor run-time performance.</span></span>

<span data-ttu-id="f8543-113">Aby uzyskać bardziej szczegółowe informacje na temat `join` , zobacz [Operacje łączenia (C#)](./join-operations.md).</span><span class="sxs-lookup"><span data-stu-id="f8543-113">For more detailed information about `join`, see [Join Operations (C#)](./join-operations.md).</span></span>

## <a name="example"></a><span data-ttu-id="f8543-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="f8543-114">Example</span></span>

<span data-ttu-id="f8543-115">Poniższy przykład sprzęga `Customer` elementy do `Order` elementów i generuje nowy dokument XML, który zawiera `CompanyName` element w zamówieniach.</span><span class="sxs-lookup"><span data-stu-id="f8543-115">The following example joins the `Customer` elements to the `Order` elements, and generates a new XML document that includes the `CompanyName` element in the orders.</span></span>

<span data-ttu-id="f8543-116">Przed wykonaniem zapytania, przykład sprawdza, czy dokument jest zgodny ze schematem w [przykładowym pliku XSD: klienci i zamówienia](./sample-xsd-file-customers-and-orders1.md).</span><span class="sxs-lookup"><span data-stu-id="f8543-116">Before executing the query, the example validates that the document complies with the schema in [Sample XSD File: Customers and Orders](./sample-xsd-file-customers-and-orders1.md).</span></span> <span data-ttu-id="f8543-117">Dzięki temu Klauzula join zawsze będzie działała.</span><span class="sxs-lookup"><span data-stu-id="f8543-117">This ensures that the join clause will always work.</span></span>

<span data-ttu-id="f8543-118">To zapytanie najpierw pobiera wszystkie `Customer` elementy, a następnie łączy je z `Order` elementami.</span><span class="sxs-lookup"><span data-stu-id="f8543-118">This query first retrieves all `Customer` elements, and then joins them to the `Order` elements.</span></span> <span data-ttu-id="f8543-119">Wybiera tylko zamówienia dla klientów o `CustomerID` większej niż "K".</span><span class="sxs-lookup"><span data-stu-id="f8543-119">It selects only the orders for customers with a `CustomerID` greater than "K".</span></span> <span data-ttu-id="f8543-120">Następnie projektuje nowy `Order` element, który zawiera informacje o kliencie w ramach poszczególnych zamówień.</span><span class="sxs-lookup"><span data-stu-id="f8543-120">It then projects a new `Order` element that contains the customer information within each order.</span></span>

<span data-ttu-id="f8543-121">W tym przykładzie zastosowano następujący dokument XML: [przykładowy plik XML: Customers i Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="f8543-121">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>

<span data-ttu-id="f8543-122">W tym przykładzie zastosowano następujący schemat XSD: [przykładowy plik XSD: klienci i zamówienia](./sample-xsd-file-customers-and-orders1.md).</span><span class="sxs-lookup"><span data-stu-id="f8543-122">This example uses the following XSD schema: [Sample XSD File: Customers and Orders](./sample-xsd-file-customers-and-orders1.md).</span></span>

<span data-ttu-id="f8543-123">Łączenie w ten sposób nie będzie działać prawidłowo.</span><span class="sxs-lookup"><span data-stu-id="f8543-123">Joining in this fashion will not perform well.</span></span> <span data-ttu-id="f8543-124">Sprzężenia są wykonywane za pośrednictwem wyszukiwania liniowego.</span><span class="sxs-lookup"><span data-stu-id="f8543-124">Joins are performed via a linear search.</span></span> <span data-ttu-id="f8543-125">Brak tabel lub indeksów skrótów, które mogą pomóc w wydajności.</span><span class="sxs-lookup"><span data-stu-id="f8543-125">There are no hash tables or indexes to help with performance.</span></span>

```csharp
XmlSchemaSet schemas = new XmlSchemaSet();
schemas.Add("", "CustomersOrders.xsd");

Console.Write("Attempting to validate, ");
XDocument custOrdDoc = XDocument.Load("CustomersOrders.xml");

bool errors = false;
custOrdDoc.Validate(schemas, (o, e) =>
                     {
                         Console.WriteLine("{0}", e.Message);
                         errors = true;
                     });
Console.WriteLine("custOrdDoc {0}", errors ? "did not validate" : "validated");

if (!errors)
{
    // Join customers and orders, and create a new XML document with
    // a different shape.

    // The new document contains orders only for customers with a
    // CustomerID > 'K'
    XElement custOrd = custOrdDoc.Element("Root");
    XElement newCustOrd = new XElement("Root",
        from c in custOrd.Element("Customers").Elements("Customer")
        join o in custOrd.Element("Orders").Elements("Order")
                   on (string)c.Attribute("CustomerID") equals
                      (string)o.Element("CustomerID")
        where ((string)c.Attribute("CustomerID")).CompareTo("K") > 0
        select new XElement("Order",
            new XElement("CustomerID", (string)c.Attribute("CustomerID")),
            new XElement("CompanyName", (string)c.Element("CompanyName")),
            new XElement("ContactName", (string)c.Element("ContactName")),
            new XElement("EmployeeID", (string)o.Element("EmployeeID")),
            new XElement("OrderDate", (DateTime)o.Element("OrderDate"))
        )
    );
    Console.WriteLine(newCustOrd);
}
```

<span data-ttu-id="f8543-126">Ten kod spowoduje wygenerowanie następujących danych wyjściowych:</span><span class="sxs-lookup"><span data-stu-id="f8543-126">This code produces the following output:</span></span>

```output
Attempting to validate, custOrdDoc validated
<Root>
  <Order>
    <CustomerID>LAZYK</CustomerID>
    <CompanyName>Lazy K Kountry Store</CompanyName>
    <ContactName>John Steel</ContactName>
    <EmployeeID>1</EmployeeID>
    <OrderDate>1997-03-21T00:00:00</OrderDate>
  </Order>
  <Order>
    <CustomerID>LAZYK</CustomerID>
    <CompanyName>Lazy K Kountry Store</CompanyName>
    <ContactName>John Steel</ContactName>
    <EmployeeID>8</EmployeeID>
    <OrderDate>1997-05-22T00:00:00</OrderDate>
  </Order>
  <Order>
    <CustomerID>LETSS</CustomerID>
    <CompanyName>Let's Stop N Shop</CompanyName>
    <ContactName>Jaime Yorres</ContactName>
    <EmployeeID>1</EmployeeID>
    <OrderDate>1997-06-25T00:00:00</OrderDate>
  </Order>
  <Order>
    <CustomerID>LETSS</CustomerID>
    <CompanyName>Let's Stop N Shop</CompanyName>
    <ContactName>Jaime Yorres</ContactName>
    <EmployeeID>8</EmployeeID>
    <OrderDate>1997-10-27T00:00:00</OrderDate>
  </Order>
  <Order>
    <CustomerID>LETSS</CustomerID>
    <CompanyName>Let's Stop N Shop</CompanyName>
    <ContactName>Jaime Yorres</ContactName>
    <EmployeeID>6</EmployeeID>
    <OrderDate>1997-11-10T00:00:00</OrderDate>
  </Order>
  <Order>
    <CustomerID>LETSS</CustomerID>
    <CompanyName>Let's Stop N Shop</CompanyName>
    <ContactName>Jaime Yorres</ContactName>
    <EmployeeID>4</EmployeeID>
    <OrderDate>1998-02-12T00:00:00</OrderDate>
  </Order>
</Root>
```
