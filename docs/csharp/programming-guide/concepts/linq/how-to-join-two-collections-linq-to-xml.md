---
title: Jak sprzęgać dwie kolekcje (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 7b817ede-911a-4cff-9dd3-639c3fc228c9
ms.openlocfilehash: a5044778bbfd9529faf5fe63c72076f6a973c815
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345859"
---
# <a name="how-to-join-two-collections-linq-to-xml-c"></a><span data-ttu-id="a5467-102">Jak sprzęgać dwie kolekcje (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="a5467-102">How to join two collections (LINQ to XML) (C#)</span></span>

<span data-ttu-id="a5467-103">Element lub atrybut w dokumencie XML czasami może odwoływać się do innego elementu lub atrybutu.</span><span class="sxs-lookup"><span data-stu-id="a5467-103">An element or attribute in an XML document can sometimes refer to another element or attribute.</span></span> <span data-ttu-id="a5467-104">[Przykładowy plik XML: Customers i Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md) dokument XML zawiera listę klientów i listę zamówień.</span><span class="sxs-lookup"><span data-stu-id="a5467-104">For example, the [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md) XML document contains a list of customers and a list of orders.</span></span> <span data-ttu-id="a5467-105">Każdy element `Customer` zawiera atrybut `CustomerID`.</span><span class="sxs-lookup"><span data-stu-id="a5467-105">Each `Customer` element contains a `CustomerID` attribute.</span></span> <span data-ttu-id="a5467-106">Każdy element `Order` zawiera `CustomerID` elementu.</span><span class="sxs-lookup"><span data-stu-id="a5467-106">Each `Order` element contains a `CustomerID` element.</span></span> <span data-ttu-id="a5467-107">Element `CustomerID` w każdej kolejności odwołuje się do atrybutu `CustomerID` w kliencie.</span><span class="sxs-lookup"><span data-stu-id="a5467-107">The `CustomerID` element in each order refers to the `CustomerID` attribute in a customer.</span></span>

<span data-ttu-id="a5467-108">[Przykładowy plik XSD tematu: klienci i zamówienia](./sample-xsd-file-customers-and-orders1.md) zawierają XSD, których można użyć do zweryfikowania tego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="a5467-108">The topic [Sample XSD File: Customers and Orders](./sample-xsd-file-customers-and-orders1.md) contains an XSD that can be used to validate this document.</span></span> <span data-ttu-id="a5467-109">Używa `xs:key` i `xs:keyref` funkcji XSD, aby określić, że atrybut `CustomerID` elementu `Customer` jest kluczem i aby ustanowić relację między `CustomerID` elementu w każdym `Order` elementu i atrybut `CustomerID` w każdym `Customer` elementu.</span><span class="sxs-lookup"><span data-stu-id="a5467-109">It uses the `xs:key` and `xs:keyref` features of XSD to establish that the `CustomerID` attribute of the `Customer` element is a key, and to establish a relationship between the `CustomerID` element in each `Order` element and the `CustomerID` attribute in each `Customer` element.</span></span>

<span data-ttu-id="a5467-110">Za pomocą [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]można wykorzystać tę relację przy użyciu klauzuli `join`.</span><span class="sxs-lookup"><span data-stu-id="a5467-110">With [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can take advantage of this relationship by using the `join` clause.</span></span>

<span data-ttu-id="a5467-111">Ponieważ nie ma dostępnego indeksu, takie dołączenie będzie miało niską wydajność w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="a5467-111">Because there is no index available, such joining will have poor run-time performance.</span></span>

<span data-ttu-id="a5467-112">Aby uzyskać szczegółowe informacje na temat `join`, zobacz [operacje JoinC#()](./join-operations.md).</span><span class="sxs-lookup"><span data-stu-id="a5467-112">For more detailed information about `join`, see [Join Operations (C#)](./join-operations.md).</span></span>

## <a name="example"></a><span data-ttu-id="a5467-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="a5467-113">Example</span></span>

<span data-ttu-id="a5467-114">Poniższy przykład sprzęga elementy `Customer` do elementów `Order` i generuje nowy dokument XML zawierający element `CompanyName` w zamówieniach.</span><span class="sxs-lookup"><span data-stu-id="a5467-114">The following example joins the `Customer` elements to the `Order` elements, and generates a new XML document that includes the `CompanyName` element in the orders.</span></span>

<span data-ttu-id="a5467-115">Przed wykonaniem zapytania, przykład sprawdza, czy dokument jest zgodny ze schematem w [przykładowym pliku XSD: klienci i zamówienia](./sample-xsd-file-customers-and-orders1.md).</span><span class="sxs-lookup"><span data-stu-id="a5467-115">Before executing the query, the example validates that the document complies with the schema in [Sample XSD File: Customers and Orders](./sample-xsd-file-customers-and-orders1.md).</span></span> <span data-ttu-id="a5467-116">Dzięki temu Klauzula join zawsze będzie działała.</span><span class="sxs-lookup"><span data-stu-id="a5467-116">This ensures that the join clause will always work.</span></span>

<span data-ttu-id="a5467-117">To zapytanie najpierw pobiera wszystkie elementy `Customer`, a następnie łączy je z elementami `Order`.</span><span class="sxs-lookup"><span data-stu-id="a5467-117">This query first retrieves all `Customer` elements, and then joins them to the `Order` elements.</span></span> <span data-ttu-id="a5467-118">Wybiera tylko zamówienia dla klientów o `CustomerID` większej niż "K".</span><span class="sxs-lookup"><span data-stu-id="a5467-118">It selects only the orders for customers with a `CustomerID` greater than "K".</span></span> <span data-ttu-id="a5467-119">Następnie projektuje nowy element `Order` zawierający informacje o klientach w poszczególnych zamówieniach.</span><span class="sxs-lookup"><span data-stu-id="a5467-119">It then projects a new `Order` element that contains the customer information within each order.</span></span>

<span data-ttu-id="a5467-120">W tym przykładzie zastosowano następujący dokument XML: [przykładowy plik XML: Customers i Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="a5467-120">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>

<span data-ttu-id="a5467-121">W tym przykładzie zastosowano następujący schemat XSD: [przykładowy plik XSD: klienci i zamówienia](./sample-xsd-file-customers-and-orders1.md).</span><span class="sxs-lookup"><span data-stu-id="a5467-121">This example uses the following XSD schema: [Sample XSD File: Customers and Orders](./sample-xsd-file-customers-and-orders1.md).</span></span>

<span data-ttu-id="a5467-122">Łączenie w ten sposób nie będzie działać prawidłowo.</span><span class="sxs-lookup"><span data-stu-id="a5467-122">Joining in this fashion will not perform well.</span></span> <span data-ttu-id="a5467-123">Sprzężenia są wykonywane za pośrednictwem wyszukiwania liniowego.</span><span class="sxs-lookup"><span data-stu-id="a5467-123">Joins are performed via a linear search.</span></span> <span data-ttu-id="a5467-124">Brak tabel lub indeksów skrótów, które mogą pomóc w wydajności.</span><span class="sxs-lookup"><span data-stu-id="a5467-124">There are no hash tables or indexes to help with performance.</span></span>

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

<span data-ttu-id="a5467-125">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="a5467-125">This code produces the following output:</span></span>

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
