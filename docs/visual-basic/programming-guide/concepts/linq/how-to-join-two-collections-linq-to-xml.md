---
title: 'Porady: Dołącz dwie kolekcje (LINQ do XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 5a5758d4-906b-4285-908d-5b930db192e6
ms.openlocfilehash: 3ceb9cf7dfdd1d18a07e93d15624fd8fac045d07
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-join-two-collections-linq-to-xml-visual-basic"></a><span data-ttu-id="dd10a-102">Porady: Dołącz dwie kolekcje (LINQ do XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dd10a-102">How to: Join Two Collections (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="dd10a-103">Element lub atrybut w dokumencie XML czasami mogą odwoływać się do innego elementu lub atrybutu.</span><span class="sxs-lookup"><span data-stu-id="dd10a-103">An element or attribute in an XML document can sometimes refer to another element or attribute.</span></span> <span data-ttu-id="dd10a-104">Na przykład [przykładowego pliku XML: Klienci i zamówienia (LINQ do XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md) dokument XML zawiera listę klientów i listę zleceń.</span><span class="sxs-lookup"><span data-stu-id="dd10a-104">For example, the [Sample XML File: Customers and Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md) XML document contains a list of customers and a list of orders.</span></span> <span data-ttu-id="dd10a-105">Każdy `Customer` zawiera element `CustomerID` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="dd10a-105">Each `Customer` element contains a `CustomerID` attribute.</span></span> <span data-ttu-id="dd10a-106">Każdy `Order` zawiera element `CustomerID` elementu.</span><span class="sxs-lookup"><span data-stu-id="dd10a-106">Each `Order` element contains a `CustomerID` element.</span></span> <span data-ttu-id="dd10a-107">`CustomerID` Elementu w każdej kolejności odwołuje się do `CustomerID` atrybutu w klienta.</span><span class="sxs-lookup"><span data-stu-id="dd10a-107">The `CustomerID` element in each order refers to the `CustomerID` attribute in a customer.</span></span>  
  
 <span data-ttu-id="dd10a-108">Temat [przykładowy plik XSD: Klienci i zamówienia](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md) zawiera XSD, który może służyć do sprawdzania poprawności tego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="dd10a-108">The topic [Sample XSD File: Customers and Orders](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md) contains an XSD that can be used to validate this document.</span></span> <span data-ttu-id="dd10a-109">Używa `xs:key` i `xs:keyref` funkcje XSD ustalenie, czy `CustomerID` atrybutu `Customer` element jest klucz oraz do ustanawiania relacji między `CustomerID` elementu w każdym `Order` element i `CustomerID` atrybutu w każdym `Customer` elementu.</span><span class="sxs-lookup"><span data-stu-id="dd10a-109">It uses the `xs:key` and `xs:keyref` features of XSD to establish that the `CustomerID` attribute of the `Customer` element is a key, and to establish a relationship between the `CustomerID` element in each `Order` element and the `CustomerID` attribute in each `Customer` element.</span></span>  
  
 <span data-ttu-id="dd10a-110">Z [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], będzie można korzystać tej relacji przy użyciu `Join` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="dd10a-110">With [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can take advantage of this relationship by using the `Join` clause.</span></span>  
  
 <span data-ttu-id="dd10a-111">Należy zauważyć, że ponieważ bez indeksu nie jest dostępny, takie łączenie będzie runtime niską wydajność.</span><span class="sxs-lookup"><span data-stu-id="dd10a-111">Note that because there is no index available, such joining will have poor runtime performance.</span></span>  
  
 <span data-ttu-id="dd10a-112">Aby uzyskać szczegółowe informacje o `Join`, zobacz [operacji Join (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/join-operations.md).</span><span class="sxs-lookup"><span data-stu-id="dd10a-112">For more detailed information about `Join`, see [Join Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/join-operations.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="dd10a-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="dd10a-113">Example</span></span>  
 <span data-ttu-id="dd10a-114">Następujące sprzężenia przykład `Customer` elementy `Order` elementów i generuje nowy dokument XML, który zawiera `CompanyName` element zamówienia.</span><span class="sxs-lookup"><span data-stu-id="dd10a-114">The following example joins the `Customer` elements to the `Order` elements, and generates a new XML document that includes the `CompanyName` element in the orders.</span></span>  
  
 <span data-ttu-id="dd10a-115">Przed wykonaniem kwerendy, przykładzie sprawdza, czy dokument jest zgodny ze schematem w [przykładowy plik XSD: Klienci i zamówienia](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md).</span><span class="sxs-lookup"><span data-stu-id="dd10a-115">Before executing the query, the example validates that the document complies with the schema in [Sample XSD File: Customers and Orders](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md).</span></span> <span data-ttu-id="dd10a-116">Daje to pewność, że zawsze będzie działać w klauzuli join.</span><span class="sxs-lookup"><span data-stu-id="dd10a-116">This ensures that the join clause will always work.</span></span>  
  
 <span data-ttu-id="dd10a-117">To zapytanie najpierw pobiera wszystkie `Customer` elementy, a następnie łączy do `Order` elementów.</span><span class="sxs-lookup"><span data-stu-id="dd10a-117">This query first retrieves all `Customer` elements, and then joins them to the `Order` elements.</span></span> <span data-ttu-id="dd10a-118">Jest ona wybierana tylko zleceń dla klientów z `CustomerID` większa niż "K".</span><span class="sxs-lookup"><span data-stu-id="dd10a-118">It selects only the orders for customers with a `CustomerID` greater than "K".</span></span> <span data-ttu-id="dd10a-119">Go następnie projektów nowy `Order` element, który zawiera informacje o kliencie w ramach każdego zamówienia.</span><span class="sxs-lookup"><span data-stu-id="dd10a-119">It then projects a new `Order` element that contains the customer information within each order.</span></span>  
  
 <span data-ttu-id="dd10a-120">W tym przykładzie użyto następujących dokumentu XML: [przykładowego pliku XML: Klienci i zamówienia (LINQ do XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="dd10a-120">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="dd10a-121">W tym przykładzie użyto następujących schematu XSD: [przykładowy plik XSD: Klienci i zamówienia](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md).</span><span class="sxs-lookup"><span data-stu-id="dd10a-121">This example uses the following XSD schema: [Sample XSD File: Customers and Orders](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md).</span></span>  
  
 <span data-ttu-id="dd10a-122">Należy pamiętać, że łączenie w ten sposób nie będzie wykonywać bardzo dobrze.</span><span class="sxs-lookup"><span data-stu-id="dd10a-122">Note that joining in this fashion will not perform very well.</span></span> <span data-ttu-id="dd10a-123">Sprzężenia są realizowane za pomocą wyszukiwania liniowego.</span><span class="sxs-lookup"><span data-stu-id="dd10a-123">Joins are performed via a linear search.</span></span> <span data-ttu-id="dd10a-124">Nie ma żadnych tabel skrótu lub indeksy ułatwiające wydajności.</span><span class="sxs-lookup"><span data-stu-id="dd10a-124">There are no hash tables or indexes to help with performance.</span></span>  
  
```vb  
Public Class Program  
    Public Shared errors As Boolean = False  
  
    Public Shared Function LamValidEvent(ByVal o As Object, _  
                 ByVal e As ValidationEventArgs) As Boolean  
        Console.WriteLine("{0}", e.Message)  
        errors = True  
    End Function  
  
    Shared Sub Main()  
        Dim schemas As New XmlSchemaSet()  
        schemas.Add("", "CustomersOrders.xsd")  
  
        Console.Write("Attempting to validate, ")  
        Dim custOrdDoc As XDocument = XDocument.Load("CustomersOrders.xml")  
  
        custOrdDoc.Validate(schemas, Function(o, e) LamValidEvent(0, e))  
        If errors Then  
            Console.WriteLine("custOrdDoc did not validate")  
        Else  
            Console.WriteLine("custOrdDoc validated")  
        End If  
  
        If Not errors Then  
            'Join customers and orders, and create a new XML document with  
            ' a different shape.  
            'The new document contains orders only for customers with a  
            ' CustomerID > 'K'.  
            Dim custOrd As XElement = custOrdDoc.<Root>.FirstOrDefault  
            Dim newCustOrd As XElement = _  
                <Root>  
                    <%= From c In custOrd.<Customers>.<Customer> _  
                        Join o In custOrd.<Orders>.<Order> _  
                        On c.@CustomerID Equals o.<CustomerID>.Value _  
                        Where c.@CustomerID.CompareTo("K") > 0 _  
                        Select _  
                        <Order>  
                            <CustomerID><%= c.@CustomerID %></CustomerID>  
                            <%= c.<CompanyName> %>  
                            <%= c.<ContactName> %>  
                            <%= o.<EmployeeID> %>  
                            <%= o.<OrderDate> %>  
                        </Order> _  
                    %>  
                </Root>  
            Console.WriteLine(newCustOrd)  
        End If  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="dd10a-125">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="dd10a-125">This code produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="dd10a-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dd10a-126">See Also</span></span>  
 [<span data-ttu-id="dd10a-127">Zaawansowane techniki zapytania (LINQ do XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dd10a-127">Advanced Query Techniques (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
