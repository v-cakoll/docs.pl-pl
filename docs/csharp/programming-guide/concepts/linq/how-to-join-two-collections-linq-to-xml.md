---
title: 'Instrukcje: Dołącz dwie kolekcje (LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 7b817ede-911a-4cff-9dd3-639c3fc228c9
ms.openlocfilehash: 82083a24da9a5356a8ff8e8430b61bb5d41f7c72
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253577"
---
# <a name="how-to-join-two-collections-linq-to-xml-c"></a><span data-ttu-id="30cbb-102">Instrukcje: Dołącz dwie kolekcje (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="30cbb-102">How to: Join Two Collections (LINQ to XML) (C#)</span></span>
<span data-ttu-id="30cbb-103">Element lub atrybut w dokumencie XML czasami może odwoływać się do innego elementu lub atrybutu.</span><span class="sxs-lookup"><span data-stu-id="30cbb-103">An element or attribute in an XML document can sometimes refer to another element or attribute.</span></span> <span data-ttu-id="30cbb-104">[Przykładowy plik XML: Dokument XML Customers and Orders](./sample-xml-file-customers-and-orders-linq-to-xml-2.md) (LINQ to XML) zawiera listę klientów i listę zamówień.</span><span class="sxs-lookup"><span data-stu-id="30cbb-104">For example, the [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md) XML document contains a list of customers and a list of orders.</span></span> <span data-ttu-id="30cbb-105">Każdy `Customer` element`CustomerID` zawiera atrybut.</span><span class="sxs-lookup"><span data-stu-id="30cbb-105">Each `Customer` element contains a `CustomerID` attribute.</span></span> <span data-ttu-id="30cbb-106">Każdy `Order` element`CustomerID` zawiera element.</span><span class="sxs-lookup"><span data-stu-id="30cbb-106">Each `Order` element contains a `CustomerID` element.</span></span> <span data-ttu-id="30cbb-107">Element w każdym porządku odwołuje się `CustomerID` do atrybutu w kliencie. `CustomerID`</span><span class="sxs-lookup"><span data-stu-id="30cbb-107">The `CustomerID` element in each order refers to the `CustomerID` attribute in a customer.</span></span>  
  
 <span data-ttu-id="30cbb-108">Przykładowy plik [XSD tematu: Klienci i zamówienia](./sample-xsd-file-customers-and-orders1.md) zawierają XSD, których można użyć do zweryfikowania tego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="30cbb-108">The topic [Sample XSD File: Customers and Orders](./sample-xsd-file-customers-and-orders1.md) contains an XSD that can be used to validate this document.</span></span> <span data-ttu-id="30cbb-109">Używa `xs:key` `CustomerID` i `Customer` `Order` funkcji XSD, aby określić, że atrybutelementujestkluczemiabyustanowićrelacjęmiędzyelementemwkażdymelemenciea`CustomerID` `xs:keyref` atrybut w każdym `Customer`elemencie. `CustomerID`</span><span class="sxs-lookup"><span data-stu-id="30cbb-109">It uses the `xs:key` and `xs:keyref` features of XSD to establish that the `CustomerID` attribute of the `Customer` element is a key, and to establish a relationship between the `CustomerID` element in each `Order` element and the `CustomerID` attribute in each `Customer` element.</span></span>  
  
 <span data-ttu-id="30cbb-110">Za pomocą programu można korzystać z tej relacji przy `join` użyciu klauzuli. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30cbb-110">With [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can take advantage of this relationship by using the `join` clause.</span></span>  
  
 <span data-ttu-id="30cbb-111">Należy pamiętać, że ponieważ nie ma dostępnego indeksu, takie dołączenie będzie miało niską wydajność środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="30cbb-111">Note that because there is no index available, such joining will have poor runtime performance.</span></span>  
  
 <span data-ttu-id="30cbb-112">Aby uzyskać bardziej szczegółowe informacje `join`na temat, zobacz [operacjeC#join ()](./join-operations.md).</span><span class="sxs-lookup"><span data-stu-id="30cbb-112">For more detailed information about `join`, see [Join Operations (C#)](./join-operations.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="30cbb-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="30cbb-113">Example</span></span>  
 <span data-ttu-id="30cbb-114">Poniższy przykład sprzęga `Customer` elementy `Order` do elementów i generuje nowy dokument `CompanyName` XML, który zawiera element w zamówieniach.</span><span class="sxs-lookup"><span data-stu-id="30cbb-114">The following example joins the `Customer` elements to the `Order` elements, and generates a new XML document that includes the `CompanyName` element in the orders.</span></span>  
  
 <span data-ttu-id="30cbb-115">Przed wykonaniem zapytania, przykład sprawdza, czy dokument jest zgodny ze schematem w [przykładowym pliku XSD: Klienci i zamówienia](./sample-xsd-file-customers-and-orders1.md).</span><span class="sxs-lookup"><span data-stu-id="30cbb-115">Before executing the query, the example validates that the document complies with the schema in [Sample XSD File: Customers and Orders](./sample-xsd-file-customers-and-orders1.md).</span></span> <span data-ttu-id="30cbb-116">Dzięki temu Klauzula join zawsze będzie działała.</span><span class="sxs-lookup"><span data-stu-id="30cbb-116">This ensures that the join clause will always work.</span></span>  
  
 <span data-ttu-id="30cbb-117">To zapytanie najpierw pobiera wszystkie `Customer` elementy, a następnie łączy je `Order` z elementami.</span><span class="sxs-lookup"><span data-stu-id="30cbb-117">This query first retrieves all `Customer` elements, and then joins them to the `Order` elements.</span></span> <span data-ttu-id="30cbb-118">Wybiera tylko zamówienia dla klientów o `CustomerID` większej niż "K".</span><span class="sxs-lookup"><span data-stu-id="30cbb-118">It selects only the orders for customers with a `CustomerID` greater than "K".</span></span> <span data-ttu-id="30cbb-119">Następnie projektuje nowy `Order` element, który zawiera informacje o kliencie w ramach poszczególnych zamówień.</span><span class="sxs-lookup"><span data-stu-id="30cbb-119">It then projects a new `Order` element that contains the customer information within each order.</span></span>  
  
 <span data-ttu-id="30cbb-120">W tym przykładzie zastosowano następujący dokument XML: [Przykładowy plik XML: Klienci i zamówienia (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="30cbb-120">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
 <span data-ttu-id="30cbb-121">W tym przykładzie zastosowano następujący schemat XSD: [Przykładowy plik XSD: Klienci i zamówienia](./sample-xsd-file-customers-and-orders1.md).</span><span class="sxs-lookup"><span data-stu-id="30cbb-121">This example uses the following XSD schema: [Sample XSD File: Customers and Orders](./sample-xsd-file-customers-and-orders1.md).</span></span>  
  
 <span data-ttu-id="30cbb-122">Należy pamiętać, że sprzężenie w ten sposób nie będzie działać prawidłowo.</span><span class="sxs-lookup"><span data-stu-id="30cbb-122">Note that joining in this fashion will not perform very well.</span></span> <span data-ttu-id="30cbb-123">Sprzężenia są wykonywane za pośrednictwem wyszukiwania liniowego.</span><span class="sxs-lookup"><span data-stu-id="30cbb-123">Joins are performed via a linear search.</span></span> <span data-ttu-id="30cbb-124">Brak tabel lub indeksów skrótów, które mogą pomóc w wydajności.</span><span class="sxs-lookup"><span data-stu-id="30cbb-124">There are no hash tables or indexes to help with performance.</span></span>  
  
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
  
 <span data-ttu-id="30cbb-125">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="30cbb-125">This code produces the following output:</span></span>  
  
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
