---
title: 'Porady: Przekształcanie kształtu drzewo XML (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 84b60854-48b2-452c-87f2-77d53e1d653a
ms.openlocfilehash: c1221fb3ad4017d7367493a3c6abef23b8c6b55b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33643942"
---
# <a name="how-to-transform-the-shape-of-an-xml-tree-visual-basic"></a><span data-ttu-id="bd6fe-102">Porady: Przekształcanie kształtu drzewo XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bd6fe-102">How to: Transform the Shape of an XML Tree (Visual Basic)</span></span>
<span data-ttu-id="bd6fe-103">*Kształtu* XML dokumentu odwołuje się do nazwy elementu, nazw atrybutów i cechy jej hierarchii.</span><span class="sxs-lookup"><span data-stu-id="bd6fe-103">The *shape* of an XML document refers to its element names, attribute names, and the characteristics of its hierarchy.</span></span>  
  
 <span data-ttu-id="bd6fe-104">Czasami trzeba będzie zmienić kształt dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="bd6fe-104">Sometimes you will have to change the shape of an XML document.</span></span> <span data-ttu-id="bd6fe-105">Może być konieczne na przykład wysłać istniejący dokument XML do innego systemu, który wymaga innego elementu i nazwach atrybutów.</span><span class="sxs-lookup"><span data-stu-id="bd6fe-105">For example, you might have to send an existing XML document to another system that requires different element and attribute names.</span></span> <span data-ttu-id="bd6fe-106">W dokumencie, można przejść, usuwanie i zmiana nazwy elementów jako wymagana, ale przy użyciu konstrukcji funkcjonalności wyniki w bardziej czytelnym i łatwy w obsłudze kodu.</span><span class="sxs-lookup"><span data-stu-id="bd6fe-106">You could go through the document, deleting and renaming elements as required, but using functional construction results in more readable and maintainable code.</span></span> <span data-ttu-id="bd6fe-107">Aby uzyskać więcej informacji na temat konstrukcji funkcjonalności, zobacz [funkcjonalności konstrukcji (LINQ do XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-construction-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="bd6fe-107">For more information about functional construction, see [Functional Construction (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-construction-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="bd6fe-108">Pierwszym przykładzie zmienia organizacji dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="bd6fe-108">The first example changes the organization of the XML document.</span></span> <span data-ttu-id="bd6fe-109">Powoduje przeniesienie złożonych elementów z jednej lokalizacji w drzewie do innego.</span><span class="sxs-lookup"><span data-stu-id="bd6fe-109">It moves complex elements from one location in the tree to another.</span></span>  
  
 <span data-ttu-id="bd6fe-110">Drugi przykład w tym temacie tworzy dokument XML z kształtem innego niż dokumentu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="bd6fe-110">The second example in this topic creates an XML document with a different shape than the source document.</span></span> <span data-ttu-id="bd6fe-111">Go zmiany wielkości liter nazwy elementów, zmienia nazwę niektóre elementy i pozostawia niektóre elementy z drzewa źródła poza przekształcone drzewa.</span><span class="sxs-lookup"><span data-stu-id="bd6fe-111">It changes the casing of the element names, renames some elements, and leaves some elements from the source tree out of the transformed tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bd6fe-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="bd6fe-112">Example</span></span>  
 <span data-ttu-id="bd6fe-113">Poniższy kod zmienia kształt plik XML przy użyciu wyrażenia osadzonego zapytania.</span><span class="sxs-lookup"><span data-stu-id="bd6fe-113">The following code changes the shape of an XML file using embedded query expressions.</span></span>  
  
 <span data-ttu-id="bd6fe-114">Dokument XML źródła, w tym przykładzie zawiera `Customers` elementu w obszarze `Root` element, który zawiera wszystkich klientów.</span><span class="sxs-lookup"><span data-stu-id="bd6fe-114">The source XML document in this example contains a `Customers` element under the `Root` element that contains all customers.</span></span> <span data-ttu-id="bd6fe-115">Zawiera także `Orders` elementu w obszarze `Root` element, który zawiera wszystkie zamówienia.</span><span class="sxs-lookup"><span data-stu-id="bd6fe-115">It also contains an `Orders` element under the `Root` element that contains all orders.</span></span> <span data-ttu-id="bd6fe-116">Nowe drzewo XML, w którym zamówień dla każdego klienta są zawarte w tym przykładzie jest tworzony `Orders` w elemencie `Customer` elementu.</span><span class="sxs-lookup"><span data-stu-id="bd6fe-116">This example creates a new XML tree in which the orders for each customer are contained in an `Orders` element within the `Customer` element.</span></span> <span data-ttu-id="bd6fe-117">Zawiera także oryginalnego dokumentu `CustomerID` element `Order` elementu; spowoduje to element można usunąć z ponownie kształcie dokumentu.</span><span class="sxs-lookup"><span data-stu-id="bd6fe-117">The original document also contains a `CustomerID` element in the `Order` element; this element will be removed from the re-shaped document.</span></span>  
  
 <span data-ttu-id="bd6fe-118">W tym przykładzie użyto następujących dokumentu XML: [przykładowego pliku XML: Klienci i zamówienia (LINQ do XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="bd6fe-118">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="bd6fe-119">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="bd6fe-119">This code produces the following output:</span></span>  
  
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
. . .  
```  
  
## <a name="example"></a><span data-ttu-id="bd6fe-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="bd6fe-120">Example</span></span>  
 <span data-ttu-id="bd6fe-121">W tym przykładzie zmienia nazwę niektóre elementy i konwertuje niektóre atrybuty elementów.</span><span class="sxs-lookup"><span data-stu-id="bd6fe-121">This example renames some elements and converts some attributes to elements.</span></span>  
  
 <span data-ttu-id="bd6fe-122">Kod wywołuje `ConvertAddress`, które zwraca listę <xref:System.Xml.Linq.XElement> obiektów.</span><span class="sxs-lookup"><span data-stu-id="bd6fe-122">The code calls `ConvertAddress`, which returns a list of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="bd6fe-123">Argument do metody jest kwerendę, która określa `Address` złożonego elementu gdzie `Type` atrybut ma wartość `"Shipping"`.</span><span class="sxs-lookup"><span data-stu-id="bd6fe-123">The argument to the method is a query that determines the `Address` complex element where the `Type` attribute has a value of `"Shipping"`.</span></span>  
  
 <span data-ttu-id="bd6fe-124">W tym przykładzie użyto następujących dokumentu XML: [przykładowego pliku XML: typowe zamówienia zakupu (LINQ do XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="bd6fe-124">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="bd6fe-125">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="bd6fe-125">This code produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bd6fe-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bd6fe-126">See Also</span></span>  
 [<span data-ttu-id="bd6fe-127">Projekcje i przekształcenia (LINQ do XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bd6fe-127">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
