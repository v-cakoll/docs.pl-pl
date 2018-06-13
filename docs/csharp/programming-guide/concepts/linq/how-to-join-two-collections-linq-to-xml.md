---
title: 'Porady: Dołącz dwie kolekcje (LINQ do XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 7b817ede-911a-4cff-9dd3-639c3fc228c9
ms.openlocfilehash: d4e7c73262cce234dc8373d42b2a8cb366316622
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33324827"
---
# <a name="how-to-join-two-collections-linq-to-xml-c"></a><span data-ttu-id="0612b-102">Porady: Dołącz dwie kolekcje (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="0612b-102">How to: Join Two Collections (LINQ to XML) (C#)</span></span>
<span data-ttu-id="0612b-103">Element lub atrybut w dokumencie XML czasami mogą odwoływać się do innego elementu lub atrybutu.</span><span class="sxs-lookup"><span data-stu-id="0612b-103">An element or attribute in an XML document can sometimes refer to another element or attribute.</span></span> <span data-ttu-id="0612b-104">Na przykład [przykładowego pliku XML: Klienci i zamówienia (LINQ do XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md) dokument XML zawiera listę klientów i listę zleceń.</span><span class="sxs-lookup"><span data-stu-id="0612b-104">For example, the [Sample XML File: Customers and Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md) XML document contains a list of customers and a list of orders.</span></span> <span data-ttu-id="0612b-105">Każdy `Customer` zawiera element `CustomerID` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="0612b-105">Each `Customer` element contains a `CustomerID` attribute.</span></span> <span data-ttu-id="0612b-106">Każdy `Order` zawiera element `CustomerID` elementu.</span><span class="sxs-lookup"><span data-stu-id="0612b-106">Each `Order` element contains a `CustomerID` element.</span></span> <span data-ttu-id="0612b-107">`CustomerID` Elementu w każdej kolejności odwołuje się do `CustomerID` atrybutu w klienta.</span><span class="sxs-lookup"><span data-stu-id="0612b-107">The `CustomerID` element in each order refers to the `CustomerID` attribute in a customer.</span></span>  
  
 <span data-ttu-id="0612b-108">Temat [przykładowy plik XSD: Klienci i zamówienia](../../../../csharp/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders1.md) zawiera XSD, który może służyć do sprawdzania poprawności tego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="0612b-108">The topic [Sample XSD File: Customers and Orders](../../../../csharp/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders1.md) contains an XSD that can be used to validate this document.</span></span> <span data-ttu-id="0612b-109">Używa `xs:key` i `xs:keyref` funkcje XSD ustalenie, czy `CustomerID` atrybutu `Customer` element jest klucz oraz do ustanawiania relacji między `CustomerID` elementu w każdym `Order` element i `CustomerID` atrybutu w każdym `Customer` elementu.</span><span class="sxs-lookup"><span data-stu-id="0612b-109">It uses the `xs:key` and `xs:keyref` features of XSD to establish that the `CustomerID` attribute of the `Customer` element is a key, and to establish a relationship between the `CustomerID` element in each `Order` element and the `CustomerID` attribute in each `Customer` element.</span></span>  
  
 <span data-ttu-id="0612b-110">Z [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], będzie można korzystać tej relacji przy użyciu `join` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="0612b-110">With [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can take advantage of this relationship by using the `join` clause.</span></span>  
  
 <span data-ttu-id="0612b-111">Należy zauważyć, że ponieważ bez indeksu nie jest dostępny, takie łączenie będzie runtime niską wydajność.</span><span class="sxs-lookup"><span data-stu-id="0612b-111">Note that because there is no index available, such joining will have poor runtime performance.</span></span>  
  
 <span data-ttu-id="0612b-112">Aby uzyskać szczegółowe informacje o `join`, zobacz [operacji Join (C#)](../../../../csharp/programming-guide/concepts/linq/join-operations.md).</span><span class="sxs-lookup"><span data-stu-id="0612b-112">For more detailed information about `join`, see [Join Operations (C#)](../../../../csharp/programming-guide/concepts/linq/join-operations.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0612b-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="0612b-113">Example</span></span>  
 <span data-ttu-id="0612b-114">Następujące sprzężenia przykład `Customer` elementy `Order` elementów i generuje nowy dokument XML, który zawiera `CompanyName` element zamówienia.</span><span class="sxs-lookup"><span data-stu-id="0612b-114">The following example joins the `Customer` elements to the `Order` elements, and generates a new XML document that includes the `CompanyName` element in the orders.</span></span>  
  
 <span data-ttu-id="0612b-115">Przed wykonaniem kwerendy, przykładzie sprawdza, czy dokument jest zgodny ze schematem w [przykładowy plik XSD: Klienci i zamówienia](../../../../csharp/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders1.md).</span><span class="sxs-lookup"><span data-stu-id="0612b-115">Before executing the query, the example validates that the document complies with the schema in [Sample XSD File: Customers and Orders](../../../../csharp/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders1.md).</span></span> <span data-ttu-id="0612b-116">Daje to pewność, że zawsze będzie działać w klauzuli join.</span><span class="sxs-lookup"><span data-stu-id="0612b-116">This ensures that the join clause will always work.</span></span>  
  
 <span data-ttu-id="0612b-117">To zapytanie najpierw pobiera wszystkie `Customer` elementy, a następnie łączy do `Order` elementów.</span><span class="sxs-lookup"><span data-stu-id="0612b-117">This query first retrieves all `Customer` elements, and then joins them to the `Order` elements.</span></span> <span data-ttu-id="0612b-118">Jest ona wybierana tylko zleceń dla klientów z `CustomerID` większa niż "K".</span><span class="sxs-lookup"><span data-stu-id="0612b-118">It selects only the orders for customers with a `CustomerID` greater than "K".</span></span> <span data-ttu-id="0612b-119">Go następnie projektów nowy `Order` element, który zawiera informacje o kliencie w ramach każdego zamówienia.</span><span class="sxs-lookup"><span data-stu-id="0612b-119">It then projects a new `Order` element that contains the customer information within each order.</span></span>  
  
 <span data-ttu-id="0612b-120">W tym przykładzie użyto następujących dokumentu XML: [przykładowego pliku XML: Klienci i zamówienia (LINQ do XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="0612b-120">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
 <span data-ttu-id="0612b-121">W tym przykładzie użyto następujących schematu XSD: [przykładowy plik XSD: Klienci i zamówienia](../../../../csharp/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders1.md).</span><span class="sxs-lookup"><span data-stu-id="0612b-121">This example uses the following XSD schema: [Sample XSD File: Customers and Orders](../../../../csharp/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders1.md).</span></span>  
  
 <span data-ttu-id="0612b-122">Należy pamiętać, że łączenie w ten sposób nie będzie wykonywać bardzo dobrze.</span><span class="sxs-lookup"><span data-stu-id="0612b-122">Note that joining in this fashion will not perform very well.</span></span> <span data-ttu-id="0612b-123">Sprzężenia są realizowane za pomocą wyszukiwania liniowego.</span><span class="sxs-lookup"><span data-stu-id="0612b-123">Joins are performed via a linear search.</span></span> <span data-ttu-id="0612b-124">Nie ma żadnych tabel skrótu lub indeksy ułatwiające wydajności.</span><span class="sxs-lookup"><span data-stu-id="0612b-124">There are no hash tables or indexes to help with performance.</span></span>  
  
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
  
 <span data-ttu-id="0612b-125">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="0612b-125">This code produces the following output:</span></span>  
  
```  
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
  
## <a name="see-also"></a><span data-ttu-id="0612b-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0612b-126">See Also</span></span>  
 [<span data-ttu-id="0612b-127">Zaawansowane techniki zapytania (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="0612b-127">Advanced Query Techniques (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
