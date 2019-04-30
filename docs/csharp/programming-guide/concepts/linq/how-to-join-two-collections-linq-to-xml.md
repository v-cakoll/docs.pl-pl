---
title: 'Instrukcje: Łączenie dwóch kolekcji (LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 7b817ede-911a-4cff-9dd3-639c3fc228c9
ms.openlocfilehash: fb158427afd59caea5eecdad29fa0a68686f6381
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61667967"
---
# <a name="how-to-join-two-collections-linq-to-xml-c"></a>Instrukcje: Łączenie dwóch kolekcji (LINQ to XML) (C#)
Element lub atrybut w dokumencie XML czasami mogą odwoływać się do innego elementu lub atrybutu. Na przykład [przykładowy plik XML: Klienci i zamówienia (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md) dokument XML zawiera listę klientów i listę zamówień. Każdy `Customer` element zawiera `CustomerID` atrybutu. Każdy `Order` element zawiera `CustomerID` elementu. `CustomerID` Elementu w ramach każdego zamówienia odwołuje się do `CustomerID` atrybutu w klienta.  
  
 Temat [przykładowy plik XSD: Klienci i zamówienia](../../../../csharp/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders1.md) zawiera XSD, który może służyć do sprawdzania poprawności w tym dokumencie. Używa ona `xs:key` i `xs:keyref` funkcji XSD ustalenie, czy `CustomerID` atrybutu `Customer` element jest klucz oraz do ustanawiania relacji między `CustomerID` elementu w każdym `Order` elementu i `CustomerID` atrybutu w każdym `Customer` elementu.  
  
 Za pomocą [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], korzystać z zalet tej relacji, za pomocą `join` klauzuli.  
  
 Należy zauważyć, że indeks nie jest dostępne, takich dołączenie będzie runtime niską wydajność.  
  
 Aby uzyskać szczegółowe informacje o `join`, zobacz [operacji Join (C#)](../../../../csharp/programming-guide/concepts/linq/join-operations.md).  
  
## <a name="example"></a>Przykład  
 Następujące sprzężenia przykład `Customer` elementów `Order` elementy i generuje nowy dokument XML, który zawiera `CompanyName` element zamówienia.  
  
 Przed wykonaniem kwerendy, przykład sprawdza, czy dokument jest zgodny ze schematem w [przykładowy plik XSD: Klienci i zamówienia](../../../../csharp/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders1.md). Daje to gwarancję, że klauzuli join zawsze będzie działać.  
  
 To zapytanie pobiera pierwszych wszystkie `Customer` elementów, a następnie dołącza je do `Order` elementów. Wybiera wszystkie zamówienia dla klientów korzystających z `CustomerID` większa niż "K". Go następnie projekty nową `Order` element, który zawiera informacje o kliencie w ramach każdego zamówienia.  
  
 W tym przykładzie użyto następujący dokument XML: [Przykładowy plik XML: Klienci i zamówienia (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).  
  
 W tym przykładzie użyto następujących schematu XSD: [Przykładowy plik XSD: Klienci i zamówienia](../../../../csharp/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders1.md).  
  
 Należy pamiętać, że łączenie w ten sposób nie będzie wykonywać bardzo dobrze. Sprzężenia są realizowane za pośrednictwem wyszukiwania liniowego. Brak skrótu tabele i indeksy, aby poprawić wydajność.  
  
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

- [Zaawansowane techniki zapytań (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
