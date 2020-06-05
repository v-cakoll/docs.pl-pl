---
title: 'Instrukcje: przekształcanie kształtu drzewa XML'
ms.date: 07/20/2015
ms.assetid: 84b60854-48b2-452c-87f2-77d53e1d653a
ms.openlocfilehash: 90fa23df09972eb76154dc47ce0a025e85a12ea3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397664"
---
# <a name="how-to-transform-the-shape-of-an-xml-tree-visual-basic"></a><span data-ttu-id="e36e0-102">Instrukcje: Przekształcanie kształtu drzewa XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e36e0-102">How to: Transform the Shape of an XML Tree (Visual Basic)</span></span>
<span data-ttu-id="e36e0-103">*Kształt* dokumentu XML odwołuje się do jego nazw elementów, nazw atrybutów i cech hierarchii.</span><span class="sxs-lookup"><span data-stu-id="e36e0-103">The *shape* of an XML document refers to its element names, attribute names, and the characteristics of its hierarchy.</span></span>  
  
 <span data-ttu-id="e36e0-104">Czasami trzeba będzie zmienić kształt dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="e36e0-104">Sometimes you will have to change the shape of an XML document.</span></span> <span data-ttu-id="e36e0-105">Na przykład może być konieczne wysłanie istniejącego dokumentu XML do innego systemu, który wymaga innych nazw elementów i atrybutów.</span><span class="sxs-lookup"><span data-stu-id="e36e0-105">For example, you might have to send an existing XML document to another system that requires different element and attribute names.</span></span> <span data-ttu-id="e36e0-106">Możesz przejść przez dokument, usunąć i zmienić nazwy elementów zgodnie z potrzebami, ale użycie konstrukcji funkcjonalnej skutkuje bardziej czytelnym i możliwym do utrzymania kodem.</span><span class="sxs-lookup"><span data-stu-id="e36e0-106">You could go through the document, deleting and renaming elements as required, but using functional construction results in more readable and maintainable code.</span></span> <span data-ttu-id="e36e0-107">Aby uzyskać więcej informacji na temat konstrukcji funkcjonalnej, zobacz [konstrukcja funkcjonalna (LINQ to XML) (Visual Basic)](functional-construction-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="e36e0-107">For more information about functional construction, see [Functional Construction (LINQ to XML) (Visual Basic)](functional-construction-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="e36e0-108">Pierwszy przykład zmienia organizację dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="e36e0-108">The first example changes the organization of the XML document.</span></span> <span data-ttu-id="e36e0-109">Przenosi elementy złożone z jednej lokalizacji w drzewie do innej.</span><span class="sxs-lookup"><span data-stu-id="e36e0-109">It moves complex elements from one location in the tree to another.</span></span>  
  
 <span data-ttu-id="e36e0-110">Drugi przykład w tym temacie tworzy dokument XML o innym kształcie niż dokument źródłowy.</span><span class="sxs-lookup"><span data-stu-id="e36e0-110">The second example in this topic creates an XML document with a different shape than the source document.</span></span> <span data-ttu-id="e36e0-111">Zmiany wielkości liter w nazwach elementów, zmiana nazwy niektórych elementów i pozostawienie niektórych elementów z drzewa źródłowego z przekształconego drzewa.</span><span class="sxs-lookup"><span data-stu-id="e36e0-111">It changes the casing of the element names, renames some elements, and leaves some elements from the source tree out of the transformed tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e36e0-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="e36e0-112">Example</span></span>  
 <span data-ttu-id="e36e0-113">Poniższy kod zmienia kształt pliku XML przy użyciu osadzonych wyrażeń zapytań.</span><span class="sxs-lookup"><span data-stu-id="e36e0-113">The following code changes the shape of an XML file using embedded query expressions.</span></span>  
  
 <span data-ttu-id="e36e0-114">Źródłowy dokument XML w tym przykładzie zawiera `Customers` element w obszarze `Root` elementu, który zawiera wszystkich klientów.</span><span class="sxs-lookup"><span data-stu-id="e36e0-114">The source XML document in this example contains a `Customers` element under the `Root` element that contains all customers.</span></span> <span data-ttu-id="e36e0-115">Zawiera również `Orders` element w obszarze `Root` elementu, który zawiera wszystkie zamówienia.</span><span class="sxs-lookup"><span data-stu-id="e36e0-115">It also contains an `Orders` element under the `Root` element that contains all orders.</span></span> <span data-ttu-id="e36e0-116">Ten przykład tworzy nowe drzewo XML, w którym zamówienia dla każdego klienta są zawarte w elemencie w `Orders` `Customer` elemencie.</span><span class="sxs-lookup"><span data-stu-id="e36e0-116">This example creates a new XML tree in which the orders for each customer are contained in an `Orders` element within the `Customer` element.</span></span> <span data-ttu-id="e36e0-117">Oryginalny dokument zawiera również `CustomerID` element w `Order` elemencie; ten element zostanie usunięty z dokumentu, który można zmienić.</span><span class="sxs-lookup"><span data-stu-id="e36e0-117">The original document also contains a `CustomerID` element in the `Order` element; this element will be removed from the re-shaped document.</span></span>  
  
 <span data-ttu-id="e36e0-118">W tym przykładzie zastosowano następujący dokument XML: [przykładowy plik XML: Customers i Orders (LINQ to XML)](sample-xml-file-customers-and-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="e36e0-118">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](sample-xml-file-customers-and-orders-linq-to-xml.md).</span></span>  
  
```vb  
Dim co As XElement = XElement.Load("CustomersOrders.xml")  
Dim newCustOrd = _  
    <Root>  
        <%= From cust In co.<Customers>.<Customer> _  
            Select _  
            <Customer>  
                <%= cust.Attributes() %>  
                <%= cust.Elements() %>  
                <Orders>  
                    <%= From ord In co.<Orders>.<Order> _  
                        Where ord.<CustomerID>.Value = cust.@CustomerID _  
                        Select _  
                        <Order>  
                            <%= ord.Attributes() %>  
                            <%= ord.<EmployeeID> %>  
                            <%= ord.<OrderDate> %>  
                            <%= ord.<RequiredDate> %>  
                            <%= ord.<ShipInfo> %>  
                        </Order> _  
                    %>  
                </Orders>  
            </Customer> _  
        %>  
    </Root>  
Console.WriteLine(newCustOrd)  
```  
  
 <span data-ttu-id="e36e0-119">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="e36e0-119">This code produces the following output:</span></span>  
  
```xml  
<Root>  
<Customer CustomerID="GREAL">  
  <CompanyName>Great Lakes Food Market</CompanyName>  
  <ContactName>Howard Snyder</ContactName>  
  <ContactTitle>Marketing Manager</ContactTitle>  
  <Phone>(503) 555-7555</Phone>  
  <FullAddress>  
    <Address>2732 Baker Blvd.</Address>  
    <City>Eugene</City>  
    <Region>OR</Region>  
    <PostalCode>97403</PostalCode>  
    <Country>USA</Country>  
  </FullAddress>  
  <Orders />  
</Customer>  
<Customer CustomerID="HUNGC">  
  <CompanyName>Hungry Coyote Import Store</CompanyName>  
  <ContactName>Yoshi Latimer</ContactName>  
  <ContactTitle>Sales Representative</ContactTitle>  
  <Phone>(503) 555-6874</Phone>  
  <Fax>(503) 555-2376</Fax>  
  <FullAddress>  
    <Address>City Center Plaza 516 Main St.</Address>  
    <City>Elgin</City>  
    <Region>OR</Region>  
    <PostalCode>97827</PostalCode>  
    <Country>USA</Country>  
  </FullAddress>  
  <Orders />  
</Customer>  
...
</Root>
```  
  
## <a name="example"></a><span data-ttu-id="e36e0-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="e36e0-120">Example</span></span>  
 <span data-ttu-id="e36e0-121">Ten przykład zmienia nazwę niektórych elementów i konwertuje niektóre atrybuty do elementów.</span><span class="sxs-lookup"><span data-stu-id="e36e0-121">This example renames some elements and converts some attributes to elements.</span></span>  
  
 <span data-ttu-id="e36e0-122">Kod wywołuje metodę `ConvertAddress` , która zwraca listę <xref:System.Xml.Linq.XElement> obiektów.</span><span class="sxs-lookup"><span data-stu-id="e36e0-122">The code calls `ConvertAddress`, which returns a list of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="e36e0-123">Argument metody jest zapytanie, które określa `Address` element złożony, gdzie `Type` atrybut ma wartość `"Shipping"` .</span><span class="sxs-lookup"><span data-stu-id="e36e0-123">The argument to the method is a query that determines the `Address` complex element where the `Type` attribute has a value of `"Shipping"`.</span></span>  
  
 <span data-ttu-id="e36e0-124">W tym przykładzie zastosowano następujący dokument XML: [przykładowy plik XML: typowe zamówienie zakupu (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="e36e0-124">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml.md).</span></span>  
  
```vb  
Function ConvertAddress(ByVal add As XElement) As IEnumerable(Of XElement)  
    Dim fragment = New List(Of XElement)  
    fragment.Add(<NAME><%= add.<Name>.Value %></NAME>)  
    fragment.Add(<STREET><%= add.<Street>.Value %></STREET>)  
    fragment.Add(<CITY><%= add.<City>.Value %></CITY>)  
    fragment.Add(<ST><%= add.<State>.Value %></ST>)  
    fragment.Add(<POSTALCODE><%= add.<Zip>.Value %></POSTALCODE>)  
    fragment.Add(<COUNTRY><%= add.<Country>.Value %></COUNTRY>)  
    Return fragment  
End Function  
  
Sub Main()  
    Dim po As XElement = XElement.Load("PurchaseOrder.xml")  
    Dim newPo As XElement = _  
        <PO>  
            <ID><%= po.@PurchaseOrderNumber %></ID>  
            <DATE><%= CDate(po.@OrderDate) %></DATE>  
            <%= _  
                ConvertAddress( _  
                (From el In po.<Address> _  
                Where el.@Type = "Shipping" _  
                Select el) _  
                .First() _  
                ) _  
            %>  
        </PO>  
    Console.WriteLine(newPo)  
End Sub  
```  
  
 <span data-ttu-id="e36e0-125">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="e36e0-125">This code produces the following output:</span></span>  
  
```xml  
<PO>  
  <ID>99503</ID>  
  <DATE>1999-10-20T00:00:00</DATE>  
  <NAME>Ellen Adams</NAME>  
  <STREET>123 Maple Street</STREET>  
  <CITY>Mill Valley</CITY>  
  <ST>CA</ST>  
  <POSTALCODE>10999</POSTALCODE>  
  <COUNTRY>USA</COUNTRY>  
</PO>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e36e0-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e36e0-126">See also</span></span>

- [<span data-ttu-id="e36e0-127">Projekcje i przekształcenia (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e36e0-127">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](projections-and-transformations-linq-to-xml.md)
