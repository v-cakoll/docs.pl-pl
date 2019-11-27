---
title: 'Instrukcje: dołączanie dwóch kolekcji (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 5a5758d4-906b-4285-908d-5b930db192e6
ms.openlocfilehash: 404a43f52fce141b515da389090c81c57186f2e2
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344533"
---
# <a name="how-to-join-two-collections-linq-to-xml-visual-basic"></a>Instrukcje: sprzęganie dwóch kolekcji (LINQ to XML) (Visual Basic)
Element lub atrybut w dokumencie XML czasami może odwoływać się do innego elementu lub atrybutu. [Przykładowy plik XML: Customers i Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md) dokument XML zawiera listę klientów i listę zamówień. Każdy element `Customer` zawiera atrybut `CustomerID`. Każdy element `Order` zawiera `CustomerID` elementu. Element `CustomerID` w każdej kolejności odwołuje się do atrybutu `CustomerID` w kliencie.  
  
 [Przykładowy plik XSD tematu: klienci i zamówienia](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md) zawierają XSD, których można użyć do zweryfikowania tego dokumentu. Używa `xs:key` i `xs:keyref` funkcji XSD, aby określić, że atrybut `CustomerID` elementu `Customer` jest kluczem i aby ustanowić relację między `CustomerID` elementu w każdym `Order` elementu i atrybut `CustomerID` w każdym `Customer` elementu.  
  
 Za pomocą [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]można wykorzystać tę relację przy użyciu klauzuli `Join`.  
  
 Należy pamiętać, że ponieważ nie ma dostępnego indeksu, takie dołączenie będzie miało niską wydajność środowiska uruchomieniowego.  
  
 Aby uzyskać szczegółowe informacje na temat `Join`, zobacz [operacje join (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/join-operations.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład sprzęga elementy `Customer` do elementów `Order` i generuje nowy dokument XML zawierający element `CompanyName` w zamówieniach.  
  
 Przed wykonaniem zapytania, przykład sprawdza, czy dokument jest zgodny ze schematem w [przykładowym pliku XSD: klienci i zamówienia](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md). Dzięki temu Klauzula join zawsze będzie działała.  
  
 To zapytanie najpierw pobiera wszystkie elementy `Customer`, a następnie łączy je z elementami `Order`. Wybiera tylko zamówienia dla klientów o `CustomerID` większej niż "K". Następnie projektuje nowy element `Order` zawierający informacje o klientach w poszczególnych zamówieniach.  
  
 W tym przykładzie zastosowano następujący dokument XML: [przykładowy plik XML: Customers i Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).  
  
 W tym przykładzie zastosowano następujący schemat XSD: [przykładowy plik XSD: klienci i zamówienia](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md).  
  
 Należy pamiętać, że sprzężenie w ten sposób nie będzie działać prawidłowo. Sprzężenia są wykonywane za pośrednictwem wyszukiwania liniowego. Brak tabel lub indeksów skrótów, które mogą pomóc w wydajności.  
  
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
  
```console
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
