---
title: Jak dołączyć dwie kolekcje (LINQ do XML) (C#)
ms.date: 07/20/2015
ms.assetid: 7b817ede-911a-4cff-9dd3-639c3fc228c9
ms.openlocfilehash: a5044778bbfd9529faf5fe63c72076f6a973c815
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75345859"
---
# <a name="how-to-join-two-collections-linq-to-xml-c"></a><span data-ttu-id="fc923-102">Jak dołączyć dwie kolekcje (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="fc923-102">How to join two collections (LINQ to XML) (C#)</span></span>

<span data-ttu-id="fc923-103">Element lub atrybut w dokumencie XML może czasami odwoływać się do innego elementu lub atrybutu.</span><span class="sxs-lookup"><span data-stu-id="fc923-103">An element or attribute in an XML document can sometimes refer to another element or attribute.</span></span> <span data-ttu-id="fc923-104">Przykładowy [plik XML: Klienci i zamówienia (LINQ do XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md) Dokument XML zawiera listę klientów i listę zamówień.</span><span class="sxs-lookup"><span data-stu-id="fc923-104">For example, the [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md) XML document contains a list of customers and a list of orders.</span></span> <span data-ttu-id="fc923-105">Każdy `Customer` element `CustomerID` zawiera atrybut.</span><span class="sxs-lookup"><span data-stu-id="fc923-105">Each `Customer` element contains a `CustomerID` attribute.</span></span> <span data-ttu-id="fc923-106">Każdy `Order` element `CustomerID` zawiera element.</span><span class="sxs-lookup"><span data-stu-id="fc923-106">Each `Order` element contains a `CustomerID` element.</span></span> <span data-ttu-id="fc923-107">Element `CustomerID` w każdym zamówieniu `CustomerID` odnosi się do atrybutu w kliencie.</span><span class="sxs-lookup"><span data-stu-id="fc923-107">The `CustomerID` element in each order refers to the `CustomerID` attribute in a customer.</span></span>

<span data-ttu-id="fc923-108">Przykładowy [przykładowy plik XSD w temacie: Klienci i zamówienia](./sample-xsd-file-customers-and-orders1.md) zawierają xsd, który może służyć do sprawdzania poprawności tego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="fc923-108">The topic [Sample XSD File: Customers and Orders](./sample-xsd-file-customers-and-orders1.md) contains an XSD that can be used to validate this document.</span></span> <span data-ttu-id="fc923-109">Używa `xs:key` `xs:keyref` i funkcje XSD, aby `CustomerID` ustalić, `Customer` że atrybut elementu jest kluczem i `CustomerID` ustanowić `Order` relację `CustomerID` między `Customer` elementem w każdym elemencie i atrybutu w każdym elemencie.</span><span class="sxs-lookup"><span data-stu-id="fc923-109">It uses the `xs:key` and `xs:keyref` features of XSD to establish that the `CustomerID` attribute of the `Customer` element is a key, and to establish a relationship between the `CustomerID` element in each `Order` element and the `CustomerID` attribute in each `Customer` element.</span></span>

<span data-ttu-id="fc923-110">Z [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], można skorzystać z tej `join` relacji przy użyciu klauzuli.</span><span class="sxs-lookup"><span data-stu-id="fc923-110">With [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can take advantage of this relationship by using the `join` clause.</span></span>

<span data-ttu-id="fc923-111">Ponieważ nie ma dostępnego indeksu, takie łączenie będzie miało słabą wydajność w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="fc923-111">Because there is no index available, such joining will have poor run-time performance.</span></span>

<span data-ttu-id="fc923-112">Aby uzyskać bardziej `join`szczegółowe informacje na temat , zobacz [Dołączanie operacji (C#)](./join-operations.md).</span><span class="sxs-lookup"><span data-stu-id="fc923-112">For more detailed information about `join`, see [Join Operations (C#)](./join-operations.md).</span></span>

## <a name="example"></a><span data-ttu-id="fc923-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="fc923-113">Example</span></span>

<span data-ttu-id="fc923-114">Poniższy przykład łączy `Customer` elementy do `Order` elementów i generuje nowy dokument XML, który zawiera `CompanyName` element w zamówieniach.</span><span class="sxs-lookup"><span data-stu-id="fc923-114">The following example joins the `Customer` elements to the `Order` elements, and generates a new XML document that includes the `CompanyName` element in the orders.</span></span>

<span data-ttu-id="fc923-115">Przed wykonaniem kwerendy, przykład sprawdza, czy dokument jest zgodny ze schematem w [przykładowym pliku XSD: Klienci i zamówienia](./sample-xsd-file-customers-and-orders1.md).</span><span class="sxs-lookup"><span data-stu-id="fc923-115">Before executing the query, the example validates that the document complies with the schema in [Sample XSD File: Customers and Orders](./sample-xsd-file-customers-and-orders1.md).</span></span> <span data-ttu-id="fc923-116">Gwarantuje to, że join klauzula będzie zawsze działać.</span><span class="sxs-lookup"><span data-stu-id="fc923-116">This ensures that the join clause will always work.</span></span>

<span data-ttu-id="fc923-117">Ta kwerenda najpierw `Customer` pobiera wszystkie elementy, a `Order` następnie łączy je z elementami.</span><span class="sxs-lookup"><span data-stu-id="fc923-117">This query first retrieves all `Customer` elements, and then joins them to the `Order` elements.</span></span> <span data-ttu-id="fc923-118">Wybiera tylko zamówienia dla klientów `CustomerID` o większej niż "K".</span><span class="sxs-lookup"><span data-stu-id="fc923-118">It selects only the orders for customers with a `CustomerID` greater than "K".</span></span> <span data-ttu-id="fc923-119">Następnie wyświetla nowy `Order` element, który zawiera informacje o kliencie w każdym zamówieniu.</span><span class="sxs-lookup"><span data-stu-id="fc923-119">It then projects a new `Order` element that contains the customer information within each order.</span></span>

<span data-ttu-id="fc923-120">W tym przykładzie użyto następującego dokumentu XML: [Przykładowy plik XML: Klienci i zamówienia (LINQ do XML).](./sample-xml-file-customers-and-orders-linq-to-xml-2.md)</span><span class="sxs-lookup"><span data-stu-id="fc923-120">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>

<span data-ttu-id="fc923-121">W tym przykładzie użyto następującego schematu XSD: [Przykładowy plik XSD: Klienci i zamówienia](./sample-xsd-file-customers-and-orders1.md).</span><span class="sxs-lookup"><span data-stu-id="fc923-121">This example uses the following XSD schema: [Sample XSD File: Customers and Orders](./sample-xsd-file-customers-and-orders1.md).</span></span>

<span data-ttu-id="fc923-122">Przyłączenie się w ten sposób nie będzie działać dobrze.</span><span class="sxs-lookup"><span data-stu-id="fc923-122">Joining in this fashion will not perform well.</span></span> <span data-ttu-id="fc923-123">Sprzężenia są wykonywane za pomocą wyszukiwania liniowego.</span><span class="sxs-lookup"><span data-stu-id="fc923-123">Joins are performed via a linear search.</span></span> <span data-ttu-id="fc923-124">Nie ma żadnych tabel mieszania lub indeksów, które pomogą w wydajności.</span><span class="sxs-lookup"><span data-stu-id="fc923-124">There are no hash tables or indexes to help with performance.</span></span>

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

<span data-ttu-id="fc923-125">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="fc923-125">This code produces the following output:</span></span>

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
