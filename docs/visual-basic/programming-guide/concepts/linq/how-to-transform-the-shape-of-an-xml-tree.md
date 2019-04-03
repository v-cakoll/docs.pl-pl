---
title: 'Instrukcje: Przekształcanie kształtu drzewa XML (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 84b60854-48b2-452c-87f2-77d53e1d653a
ms.openlocfilehash: 067bf56b8dff994080ba78147d992b97a56867cb
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58833665"
---
# <a name="how-to-transform-the-shape-of-an-xml-tree-visual-basic"></a>Instrukcje: Przekształcanie kształtu drzewa XML (Visual Basic)
*Kształt* XML dokumentu odwołuje się do jego nazwy elementów, nazwy atrybutów i cechy jej hierarchii.  
  
 Czasami trzeba będzie zmienić kształt dokumentu XML. Na przykład trzeba wysłać istniejący dokument XML do innego systemu, który wymaga innego elementu i nazwach atrybutów. Można przejść w dokumencie, usuwanie i zmienianie nazw elementów jako wymagana, ale przy użyciu konstrukcja funkcjonalna skutkuje bardziej czytelny i łatwy w obsłudze kodu. Aby uzyskać więcej informacji na temat konstrukcja funkcjonalna zobacz [konstrukcja funkcjonalna (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-construction-linq-to-xml.md).  
  
 Pierwszy przykład zmienia struktury dokumentu XML. Przenosi złożonych elementów z jednej lokalizacji w drzewie do innego.  
  
 Drugi przykład w tym temacie tworzy dokumentu XML z innego kształtu niż dokumentu źródłowego. Zmienia wielkość liter w wyrazie nazw elementów, zmienia nazwę niektóre elementy i pozostawi pewne elementy z drzewa źródła poza przekształcone drzewa.  
  
## <a name="example"></a>Przykład  
 Poniższy kod zmienia kształt pliku XML przy użyciu wyrażeń osadzonego zapytania.  
  
 Zawiera w dokumencie źródłowym XML w tym przykładzie `Customers` pod `Root` element, który zawiera wszystkich klientów. Zawiera ona także `Orders` pod `Root` element, który zawiera wszystkie zamówienia. W tym przykładzie tworzy nowego drzewa XML, w którym zamówień dla każdego klienta są zawarte w `Orders` elemencie `Customer` elementu. Oryginalny dokument zawiera również `CustomerID` element `Order` element; spowoduje elementu, można usunąć z ponownie ukształtowane dokumentu.  
  
 W tym przykładzie użyto następujący dokument XML: [Przykładowy plik XML: Klienci i zamówienia (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).  
  
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
  
 Ten kod generuje następujące dane wyjściowe:  
  
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
  
## <a name="example"></a>Przykład  
 Ten przykład zmienia nazwę niektóre elementy i konwertuje niektóre atrybuty elementów.  
  
 Kod wywołuje `ConvertAddress`, które zwraca listę <xref:System.Xml.Linq.XElement> obiektów. Argument do metody jest zapytanie, które określa `Address` złożonego elementu gdzie `Type` atrybut ma wartość `"Shipping"`.  
  
 W tym przykładzie użyto następujący dokument XML: [Przykładowy plik XML: Typowe zamówienie zakupu (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).  
  
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
  
 Ten kod generuje następujące dane wyjściowe:  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Projekcje i przekształcenia (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
