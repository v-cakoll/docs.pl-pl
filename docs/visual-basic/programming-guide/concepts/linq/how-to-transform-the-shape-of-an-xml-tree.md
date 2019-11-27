---
title: 'Instrukcje: Przekształcanie kształtu drzewa XML'
ms.date: 07/20/2015
ms.assetid: 84b60854-48b2-452c-87f2-77d53e1d653a
ms.openlocfilehash: 67ffd5f50572c0deba75c664ffd0e12ecfabf730
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74332419"
---
# <a name="how-to-transform-the-shape-of-an-xml-tree-visual-basic"></a>Instrukcje: Przekształcanie kształtu drzewa XML (Visual Basic)
*Kształt* dokumentu XML odwołuje się do jego nazw elementów, nazw atrybutów i cech hierarchii.  
  
 Czasami trzeba będzie zmienić kształt dokumentu XML. Na przykład może być konieczne wysłanie istniejącego dokumentu XML do innego systemu, który wymaga innych nazw elementów i atrybutów. Możesz przejść przez dokument, usunąć i zmienić nazwy elementów zgodnie z potrzebami, ale użycie konstrukcji funkcjonalnej skutkuje bardziej czytelnym i możliwym do utrzymania kodem. Aby uzyskać więcej informacji na temat konstrukcji funkcjonalnej, zobacz [konstrukcja funkcjonalna (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-construction-linq-to-xml.md).  
  
 Pierwszy przykład zmienia organizację dokumentu XML. Przenosi elementy złożone z jednej lokalizacji w drzewie do innej.  
  
 Drugi przykład w tym temacie tworzy dokument XML o innym kształcie niż dokument źródłowy. Zmiany wielkości liter w nazwach elementów, zmiana nazwy niektórych elementów i pozostawienie niektórych elementów z drzewa źródłowego z przekształconego drzewa.  
  
## <a name="example"></a>Przykład  
 Poniższy kod zmienia kształt pliku XML przy użyciu osadzonych wyrażeń zapytań.  
  
 Źródłowy dokument XML w tym przykładzie zawiera element `Customers` w elemencie `Root`, który zawiera wszystkich klientów. Zawiera również element `Orders` w elemencie `Root`, który zawiera wszystkie zamówienia. Ten przykład tworzy nowe drzewo XML, w którym zamówienia dla każdego klienta znajdują się w `Orders` elementu w ramach elementu `Customer`. Oryginalny dokument zawiera również element `CustomerID` w elemencie `Order`; Ten element zostanie usunięty z dokumentu, który można zmienić.  
  
 W tym przykładzie zastosowano następujący dokument XML: [przykładowy plik XML: Customers i Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).  
  
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
 Ten przykład zmienia nazwę niektórych elementów i konwertuje niektóre atrybuty do elementów.  
  
 Kod wywołuje `ConvertAddress`, który zwraca listę obiektów <xref:System.Xml.Linq.XElement>. Argument metody jest zapytanie, które określa `Address` element złożony, gdzie atrybut `Type` ma wartość `"Shipping"`.  
  
 W tym przykładzie zastosowano następujący dokument XML: [przykładowy plik XML: typowe zamówienie zakupu (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).  
  
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
