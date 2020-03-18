---
title: Jak dołączyć dwie kolekcje (LINQ do XML) (C#)
ms.date: 07/20/2015
ms.assetid: 7b817ede-911a-4cff-9dd3-639c3fc228c9
ms.openlocfilehash: a5044778bbfd9529faf5fe63c72076f6a973c815
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75345859"
---
# <a name="how-to-join-two-collections-linq-to-xml-c"></a>Jak dołączyć dwie kolekcje (LINQ do XML) (C#)

Element lub atrybut w dokumencie XML może czasami odwoływać się do innego elementu lub atrybutu. Przykładowy [plik XML: Klienci i zamówienia (LINQ do XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md) Dokument XML zawiera listę klientów i listę zamówień. Każdy `Customer` element `CustomerID` zawiera atrybut. Każdy `Order` element `CustomerID` zawiera element. Element `CustomerID` w każdym zamówieniu `CustomerID` odnosi się do atrybutu w kliencie.

Przykładowy [przykładowy plik XSD w temacie: Klienci i zamówienia](./sample-xsd-file-customers-and-orders1.md) zawierają xsd, który może służyć do sprawdzania poprawności tego dokumentu. Używa `xs:key` `xs:keyref` i funkcje XSD, aby `CustomerID` ustalić, `Customer` że atrybut elementu jest kluczem i `CustomerID` ustanowić `Order` relację `CustomerID` między `Customer` elementem w każdym elemencie i atrybutu w każdym elemencie.

Z [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], można skorzystać z tej `join` relacji przy użyciu klauzuli.

Ponieważ nie ma dostępnego indeksu, takie łączenie będzie miało słabą wydajność w czasie wykonywania.

Aby uzyskać bardziej `join`szczegółowe informacje na temat , zobacz [Dołączanie operacji (C#)](./join-operations.md).

## <a name="example"></a>Przykład

Poniższy przykład łączy `Customer` elementy do `Order` elementów i generuje nowy dokument XML, który zawiera `CompanyName` element w zamówieniach.

Przed wykonaniem kwerendy, przykład sprawdza, czy dokument jest zgodny ze schematem w [przykładowym pliku XSD: Klienci i zamówienia](./sample-xsd-file-customers-and-orders1.md). Gwarantuje to, że join klauzula będzie zawsze działać.

Ta kwerenda najpierw `Customer` pobiera wszystkie elementy, a `Order` następnie łączy je z elementami. Wybiera tylko zamówienia dla klientów `CustomerID` o większej niż "K". Następnie wyświetla nowy `Order` element, który zawiera informacje o kliencie w każdym zamówieniu.

W tym przykładzie użyto następującego dokumentu XML: [Przykładowy plik XML: Klienci i zamówienia (LINQ do XML).](./sample-xml-file-customers-and-orders-linq-to-xml-2.md)

W tym przykładzie użyto następującego schematu XSD: [Przykładowy plik XSD: Klienci i zamówienia](./sample-xsd-file-customers-and-orders1.md).

Przyłączenie się w ten sposób nie będzie działać dobrze. Sprzężenia są wykonywane za pomocą wyszukiwania liniowego. Nie ma żadnych tabel mieszania lub indeksów, które pomogą w wydajności.

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

```output
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
