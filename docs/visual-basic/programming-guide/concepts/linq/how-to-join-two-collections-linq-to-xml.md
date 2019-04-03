---
title: 'Instrukcje: Łączenie dwóch kolekcji (LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 5a5758d4-906b-4285-908d-5b930db192e6
ms.openlocfilehash: 85689fa756ab20a4dcd054b70eb3003c767936ea
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58843242"
---
# <a name="how-to-join-two-collections-linq-to-xml-visual-basic"></a>Instrukcje: Łączenie dwóch kolekcji (LINQ to XML) (Visual Basic)
Element lub atrybut w dokumencie XML czasami mogą odwoływać się do innego elementu lub atrybutu. Na przykład [przykładowy plik XML: Klienci i zamówienia (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md) dokument XML zawiera listę klientów i listę zamówień. Każdy `Customer` element zawiera `CustomerID` atrybutu. Każdy `Order` element zawiera `CustomerID` elementu. `CustomerID` Elementu w ramach każdego zamówienia odwołuje się do `CustomerID` atrybutu w klienta.  
  
 Temat [przykładowy plik XSD: Klienci i zamówienia](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md) zawiera XSD, który może służyć do sprawdzania poprawności w tym dokumencie. Używa ona `xs:key` i `xs:keyref` funkcji XSD ustalenie, czy `CustomerID` atrybutu `Customer` element jest klucz oraz do ustanawiania relacji między `CustomerID` elementu w każdym `Order` elementu i `CustomerID` atrybutu w każdym `Customer` elementu.  
  
 Za pomocą [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], korzystać z zalet tej relacji, za pomocą `Join` klauzuli.  
  
 Należy zauważyć, że indeks nie jest dostępne, takich dołączenie będzie runtime niską wydajność.  
  
 Aby uzyskać szczegółowe informacje o `Join`, zobacz [operacji Join (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/join-operations.md).  
  
## <a name="example"></a>Przykład  
 Następujące sprzężenia przykład `Customer` elementów `Order` elementy i generuje nowy dokument XML, który zawiera `CompanyName` element zamówienia.  
  
 Przed wykonaniem kwerendy, przykład sprawdza, czy dokument jest zgodny ze schematem w [przykładowy plik XSD: Klienci i zamówienia](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md). Daje to gwarancję, że klauzuli join zawsze będzie działać.  
  
 To zapytanie pobiera pierwszych wszystkie `Customer` elementów, a następnie dołącza je do `Order` elementów. Wybiera wszystkie zamówienia dla klientów korzystających z `CustomerID` większa niż "K". Go następnie projekty nową `Order` element, który zawiera informacje o kliencie w ramach każdego zamówienia.  
  
 W tym przykładzie użyto następujący dokument XML: [Przykładowy plik XML: Klienci i zamówienia (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).  
  
 W tym przykładzie użyto następujących schematu XSD: [Przykładowy plik XSD: Klienci i zamówienia](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md).  
  
 Należy pamiętać, że łączenie w ten sposób nie będzie wykonywać bardzo dobrze. Sprzężenia są realizowane za pośrednictwem wyszukiwania liniowego. Brak skrótu tabele i indeksy, aby poprawić wydajność.  
  
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
  
 Ten kod generuje następujące dane wyjściowe:  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Zaawansowane techniki zapytań (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
