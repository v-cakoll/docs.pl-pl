---
title: 'Porady: Dołącz dwie kolekcje (LINQ do XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 7b817ede-911a-4cff-9dd3-639c3fc228c9
ms.openlocfilehash: d4e7c73262cce234dc8373d42b2a8cb366316622
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33324827"
---
# <a name="how-to-join-two-collections-linq-to-xml-c"></a>Porady: Dołącz dwie kolekcje (LINQ do XML) (C#)
Element lub atrybut w dokumencie XML czasami mogą odwoływać się do innego elementu lub atrybutu. Na przykład [przykładowego pliku XML: Klienci i zamówienia (LINQ do XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md) dokument XML zawiera listę klientów i listę zleceń. Każdy `Customer` zawiera element `CustomerID` atrybutu. Każdy `Order` zawiera element `CustomerID` elementu. `CustomerID` Elementu w każdej kolejności odwołuje się do `CustomerID` atrybutu w klienta.  
  
 Temat [przykładowy plik XSD: Klienci i zamówienia](../../../../csharp/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders1.md) zawiera XSD, który może służyć do sprawdzania poprawności tego dokumentu. Używa `xs:key` i `xs:keyref` funkcje XSD ustalenie, czy `CustomerID` atrybutu `Customer` element jest klucz oraz do ustanawiania relacji między `CustomerID` elementu w każdym `Order` element i `CustomerID` atrybutu w każdym `Customer` elementu.  
  
 Z [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], będzie można korzystać tej relacji przy użyciu `join` klauzuli.  
  
 Należy zauważyć, że ponieważ bez indeksu nie jest dostępny, takie łączenie będzie runtime niską wydajność.  
  
 Aby uzyskać szczegółowe informacje o `join`, zobacz [operacji Join (C#)](../../../../csharp/programming-guide/concepts/linq/join-operations.md).  
  
## <a name="example"></a>Przykład  
 Następujące sprzężenia przykład `Customer` elementy `Order` elementów i generuje nowy dokument XML, który zawiera `CompanyName` element zamówienia.  
  
 Przed wykonaniem kwerendy, przykładzie sprawdza, czy dokument jest zgodny ze schematem w [przykładowy plik XSD: Klienci i zamówienia](../../../../csharp/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders1.md). Daje to pewność, że zawsze będzie działać w klauzuli join.  
  
 To zapytanie najpierw pobiera wszystkie `Customer` elementy, a następnie łączy do `Order` elementów. Jest ona wybierana tylko zleceń dla klientów z `CustomerID` większa niż "K". Go następnie projektów nowy `Order` element, który zawiera informacje o kliencie w ramach każdego zamówienia.  
  
 W tym przykładzie użyto następujących dokumentu XML: [przykładowego pliku XML: Klienci i zamówienia (LINQ do XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).  
  
 W tym przykładzie użyto następujących schematu XSD: [przykładowy plik XSD: Klienci i zamówienia](../../../../csharp/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders1.md).  
  
 Należy pamiętać, że łączenie w ten sposób nie będzie wykonywać bardzo dobrze. Sprzężenia są realizowane za pomocą wyszukiwania liniowego. Nie ma żadnych tabel skrótu lub indeksy ułatwiające wydajności.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Zaawansowane techniki zapytania (LINQ do XML) (C#)](../../../../csharp/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
