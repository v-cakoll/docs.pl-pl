---
title: "Porady: Przekształcanie kształtu drzewo XML (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 84b60854-48b2-452c-87f2-77d53e1d653a
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: cad7e5fc53b59593cf0c367d65d5bd44564bb1c7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-transform-the-shape-of-an-xml-tree-visual-basic"></a>Porady: Przekształcanie kształtu drzewo XML (Visual Basic)
*Kształtu* XML dokumentu odwołuje się do nazwy elementu, nazw atrybutów i cechy jej hierarchii.  
  
 Czasami trzeba będzie zmienić kształt dokumentu XML. Może być konieczne na przykład wysłać istniejący dokument XML do innego systemu, który wymaga innego elementu i nazwach atrybutów. W dokumencie, można przejść, usuwanie i zmiana nazwy elementów jako wymagana, ale przy użyciu konstrukcji funkcjonalności wyniki w bardziej czytelnym i łatwy w obsłudze kodu. Aby uzyskać więcej informacji na temat konstrukcji funkcjonalności, zobacz [funkcjonalności konstrukcji (LINQ do XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-construction-linq-to-xml.md).  
  
 Pierwszym przykładzie zmienia organizacji dokumentu XML. Powoduje przeniesienie złożonych elementów z jednej lokalizacji w drzewie do innego.  
  
 Drugi przykład w tym temacie tworzy dokument XML z kształtem innego niż dokumentu źródłowego. Go zmiany wielkości liter nazwy elementów, zmienia nazwę niektóre elementy i pozostawia niektóre elementy z drzewa źródła poza przekształcone drzewa.  
  
## <a name="example"></a>Przykład  
 Poniższy kod zmienia kształt plik XML przy użyciu wyrażenia osadzonego zapytania.  
  
 Dokument XML źródła, w tym przykładzie zawiera `Customers` elementu w obszarze `Root` element, który zawiera wszystkich klientów. Zawiera także `Orders` elementu w obszarze `Root` element, który zawiera wszystkie zamówienia. Nowe drzewo XML, w którym zamówień dla każdego klienta są zawarte w tym przykładzie jest tworzony `Orders` w elemencie `Customer` elementu. Zawiera także oryginalnego dokumentu `CustomerID` element `Order` elementu; spowoduje to element można usunąć z ponownie kształcie dokumentu.  
  
 W tym przykładzie użyto następujących dokumentu XML: [przykładowego pliku XML: Klienci i zamówienia (LINQ do XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).  
  
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
 W tym przykładzie zmienia nazwę niektóre elementy i konwertuje niektóre atrybuty elementów.  
  
 Kod wywołuje `ConvertAddress`, które zwraca listę <xref:System.Xml.Linq.XElement> obiektów. Argument do metody jest kwerendę, która określa `Address` złożonego elementu gdzie `Type` atrybut ma wartość `"Shipping"`.  
  
 W tym przykładzie użyto następujących dokumentu XML: [przykładowego pliku XML: typowe zamówienia zakupu (LINQ do XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Projekcje i przekształcenia (LINQ do XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
