---
title: 'Porady: łączenie dwóch kolekcji (LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 7b817ede-911a-4cff-9dd3-639c3fc228c9
ms.openlocfilehash: 00db2decfb8595c32e86f76c8aa139d91e75d112
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43513533"
---
# <a name="how-to-join-two-collections-linq-to-xml-c"></a><span data-ttu-id="a43e6-102">Porady: łączenie dwóch kolekcji (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="a43e6-102">How to: Join Two Collections (LINQ to XML) (C#)</span></span>
<span data-ttu-id="a43e6-103">Element lub atrybut w dokumencie XML czasami mogą odwoływać się do innego elementu lub atrybutu.</span><span class="sxs-lookup"><span data-stu-id="a43e6-103">An element or attribute in an XML document can sometimes refer to another element or attribute.</span></span> <span data-ttu-id="a43e6-104">Na przykład [przykładowy plik XML: Klienci i zamówienia (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md) dokument XML zawiera listę klientów i listę zamówień.</span><span class="sxs-lookup"><span data-stu-id="a43e6-104">For example, the [Sample XML File: Customers and Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md) XML document contains a list of customers and a list of orders.</span></span> <span data-ttu-id="a43e6-105">Każdy `Customer` element zawiera `CustomerID` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="a43e6-105">Each `Customer` element contains a `CustomerID` attribute.</span></span> <span data-ttu-id="a43e6-106">Każdy `Order` element zawiera `CustomerID` elementu.</span><span class="sxs-lookup"><span data-stu-id="a43e6-106">Each `Order` element contains a `CustomerID` element.</span></span> <span data-ttu-id="a43e6-107">`CustomerID` Elementu w ramach każdego zamówienia odwołuje się do `CustomerID` atrybutu w klienta.</span><span class="sxs-lookup"><span data-stu-id="a43e6-107">The `CustomerID` element in each order refers to the `CustomerID` attribute in a customer.</span></span>  
  
 <span data-ttu-id="a43e6-108">Temat [przykładowy plik XSD: Klienci i zamówienia](../../../../csharp/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders1.md) zawiera XSD, który może służyć do sprawdzania poprawności w tym dokumencie.</span><span class="sxs-lookup"><span data-stu-id="a43e6-108">The topic [Sample XSD File: Customers and Orders](../../../../csharp/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders1.md) contains an XSD that can be used to validate this document.</span></span> <span data-ttu-id="a43e6-109">Używa ona `xs:key` i `xs:keyref` funkcji XSD ustalenie, czy `CustomerID` atrybutu `Customer` element jest klucz oraz do ustanawiania relacji między `CustomerID` elementu w każdym `Order` elementu i `CustomerID` atrybutu w każdym `Customer` elementu.</span><span class="sxs-lookup"><span data-stu-id="a43e6-109">It uses the `xs:key` and `xs:keyref` features of XSD to establish that the `CustomerID` attribute of the `Customer` element is a key, and to establish a relationship between the `CustomerID` element in each `Order` element and the `CustomerID` attribute in each `Customer` element.</span></span>  
  
 <span data-ttu-id="a43e6-110">Za pomocą [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], korzystać z zalet tej relacji, za pomocą `join` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="a43e6-110">With [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can take advantage of this relationship by using the `join` clause.</span></span>  
  
 <span data-ttu-id="a43e6-111">Należy zauważyć, że indeks nie jest dostępne, takich dołączenie będzie runtime niską wydajność.</span><span class="sxs-lookup"><span data-stu-id="a43e6-111">Note that because there is no index available, such joining will have poor runtime performance.</span></span>  
  
 <span data-ttu-id="a43e6-112">Aby uzyskać szczegółowe informacje o `join`, zobacz [operacji Join (C#)](../../../../csharp/programming-guide/concepts/linq/join-operations.md).</span><span class="sxs-lookup"><span data-stu-id="a43e6-112">For more detailed information about `join`, see [Join Operations (C#)](../../../../csharp/programming-guide/concepts/linq/join-operations.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a43e6-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="a43e6-113">Example</span></span>  
 <span data-ttu-id="a43e6-114">Następujące sprzężenia przykład `Customer` elementów `Order` elementy i generuje nowy dokument XML, który zawiera `CompanyName` element zamówienia.</span><span class="sxs-lookup"><span data-stu-id="a43e6-114">The following example joins the `Customer` elements to the `Order` elements, and generates a new XML document that includes the `CompanyName` element in the orders.</span></span>  
  
 <span data-ttu-id="a43e6-115">Przed wykonaniem kwerendy, przykład sprawdza, czy dokument jest zgodny ze schematem w [przykładowy plik XSD: Klienci i zamówienia](../../../../csharp/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders1.md).</span><span class="sxs-lookup"><span data-stu-id="a43e6-115">Before executing the query, the example validates that the document complies with the schema in [Sample XSD File: Customers and Orders](../../../../csharp/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders1.md).</span></span> <span data-ttu-id="a43e6-116">Daje to gwarancję, że klauzuli join zawsze będzie działać.</span><span class="sxs-lookup"><span data-stu-id="a43e6-116">This ensures that the join clause will always work.</span></span>  
  
 <span data-ttu-id="a43e6-117">To zapytanie pobiera pierwszych wszystkie `Customer` elementów, a następnie dołącza je do `Order` elementów.</span><span class="sxs-lookup"><span data-stu-id="a43e6-117">This query first retrieves all `Customer` elements, and then joins them to the `Order` elements.</span></span> <span data-ttu-id="a43e6-118">Wybiera wszystkie zamówienia dla klientów korzystających z `CustomerID` większa niż "K".</span><span class="sxs-lookup"><span data-stu-id="a43e6-118">It selects only the orders for customers with a `CustomerID` greater than "K".</span></span> <span data-ttu-id="a43e6-119">Go następnie projekty nową `Order` element, który zawiera informacje o kliencie w ramach każdego zamówienia.</span><span class="sxs-lookup"><span data-stu-id="a43e6-119">It then projects a new `Order` element that contains the customer information within each order.</span></span>  
  
 <span data-ttu-id="a43e6-120">W tym przykładzie użyto następujący dokument XML: [przykładowy plik XML: Klienci i zamówienia (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="a43e6-120">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
 <span data-ttu-id="a43e6-121">W tym przykładzie użyto następujących schematu XSD: [przykładowy plik XSD: Klienci i zamówienia](../../../../csharp/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders1.md).</span><span class="sxs-lookup"><span data-stu-id="a43e6-121">This example uses the following XSD schema: [Sample XSD File: Customers and Orders](../../../../csharp/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders1.md).</span></span>  
  
 <span data-ttu-id="a43e6-122">Należy pamiętać, że łączenie w ten sposób nie będzie wykonywać bardzo dobrze.</span><span class="sxs-lookup"><span data-stu-id="a43e6-122">Note that joining in this fashion will not perform very well.</span></span> <span data-ttu-id="a43e6-123">Sprzężenia są realizowane za pośrednictwem wyszukiwania liniowego.</span><span class="sxs-lookup"><span data-stu-id="a43e6-123">Joins are performed via a linear search.</span></span> <span data-ttu-id="a43e6-124">Brak skrótu tabele i indeksy, aby poprawić wydajność.</span><span class="sxs-lookup"><span data-stu-id="a43e6-124">There are no hash tables or indexes to help with performance.</span></span>  
  
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
  
 <span data-ttu-id="a43e6-125">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="a43e6-125">This code produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a43e6-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a43e6-126">See Also</span></span>

- [<span data-ttu-id="a43e6-127">Zaawansowane techniki zapytań (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="a43e6-127">Advanced Query Techniques (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
