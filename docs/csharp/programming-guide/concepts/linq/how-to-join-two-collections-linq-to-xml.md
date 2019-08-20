---
title: 'Instrukcje: Dołącz dwie kolekcje (LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 7b817ede-911a-4cff-9dd3-639c3fc228c9
ms.openlocfilehash: aa774e23cfd232709f9824826f5084fe6049ef37
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69593200"
---
# <a name="how-to-join-two-collections-linq-to-xml-c"></a>Instrukcje: Dołącz dwie kolekcje (LINQ to XML) (C#)
Element lub atrybut w dokumencie XML czasami może odwoływać się do innego elementu lub atrybutu. [Przykładowy plik XML: Dokument XML Customers and Orders](./sample-xml-file-customers-and-orders-linq-to-xml-2.md) (LINQ to XML) zawiera listę klientów i listę zamówień. Każdy `Customer` element`CustomerID` zawiera atrybut. Każdy `Order` element`CustomerID` zawiera element. Element w każdym porządku odwołuje się `CustomerID` do atrybutu w kliencie. `CustomerID`  
  
 Przykładowy plik [XSD tematu: Klienci i zamówienia](./sample-xsd-file-customers-and-orders1.md) zawierają XSD, których można użyć do zweryfikowania tego dokumentu. Używa `xs:key` `CustomerID` i `Customer` `Order` funkcji XSD, aby określić, że atrybutelementujestkluczemiabyustanowićrelacjęmiędzyelementemwkażdymelemenciea`CustomerID` `xs:keyref` atrybut w każdym `Customer`elemencie. `CustomerID`  
  
 Za pomocą programu można korzystać z tej relacji przy `join` użyciu klauzuli. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]  
  
 Należy pamiętać, że ponieważ nie ma dostępnego indeksu, takie dołączenie będzie miało niską wydajność środowiska uruchomieniowego.  
  
 Aby uzyskać bardziej szczegółowe informacje `join`na temat, zobacz [operacjeC#join ()](./join-operations.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład sprzęga `Customer` elementy `Order` do elementów i generuje nowy dokument `CompanyName` XML, który zawiera element w zamówieniach.  
  
 Przed wykonaniem zapytania, przykład sprawdza, czy dokument jest zgodny ze schematem w [przykładowym pliku XSD: Klienci i zamówienia](./sample-xsd-file-customers-and-orders1.md). Dzięki temu Klauzula join zawsze będzie działała.  
  
 To zapytanie najpierw pobiera wszystkie `Customer` elementy, a następnie łączy je `Order` z elementami. Wybiera tylko zamówienia dla klientów o `CustomerID` większej niż "K". Następnie projektuje nowy `Order` element, który zawiera informacje o kliencie w ramach poszczególnych zamówień.  
  
 W tym przykładzie zastosowano następujący dokument XML: [Przykładowy plik XML: Klienci i zamówienia (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).  
  
 W tym przykładzie zastosowano następujący schemat XSD: [Przykładowy plik XSD: Klienci i zamówienia](./sample-xsd-file-customers-and-orders1.md).  
  
 Należy pamiętać, że sprzężenie w ten sposób nie będzie działać prawidłowo. Sprzężenia są wykonywane za pośrednictwem wyszukiwania liniowego. Brak tabel lub indeksów skrótów, które mogą pomóc w wydajności.  
  
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
