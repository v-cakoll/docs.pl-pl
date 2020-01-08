---
title: Jak sprzęgać dwie kolekcje (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 7b817ede-911a-4cff-9dd3-639c3fc228c9
ms.openlocfilehash: a5044778bbfd9529faf5fe63c72076f6a973c815
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345859"
---
# <a name="how-to-join-two-collections-linq-to-xml-c"></a>Jak sprzęgać dwie kolekcje (LINQ to XML) (C#)

Element lub atrybut w dokumencie XML czasami może odwoływać się do innego elementu lub atrybutu. [Przykładowy plik XML: Customers i Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md) dokument XML zawiera listę klientów i listę zamówień. Każdy element `Customer` zawiera atrybut `CustomerID`. Każdy element `Order` zawiera `CustomerID` elementu. Element `CustomerID` w każdej kolejności odwołuje się do atrybutu `CustomerID` w kliencie.

[Przykładowy plik XSD tematu: klienci i zamówienia](./sample-xsd-file-customers-and-orders1.md) zawierają XSD, których można użyć do zweryfikowania tego dokumentu. Używa `xs:key` i `xs:keyref` funkcji XSD, aby określić, że atrybut `CustomerID` elementu `Customer` jest kluczem i aby ustanowić relację między `CustomerID` elementu w każdym `Order` elementu i atrybut `CustomerID` w każdym `Customer` elementu.

Za pomocą [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]można wykorzystać tę relację przy użyciu klauzuli `join`.

Ponieważ nie ma dostępnego indeksu, takie dołączenie będzie miało niską wydajność w czasie wykonywania.

Aby uzyskać szczegółowe informacje na temat `join`, zobacz [operacje JoinC#()](./join-operations.md).

## <a name="example"></a>Przykład

Poniższy przykład sprzęga elementy `Customer` do elementów `Order` i generuje nowy dokument XML zawierający element `CompanyName` w zamówieniach.

Przed wykonaniem zapytania, przykład sprawdza, czy dokument jest zgodny ze schematem w [przykładowym pliku XSD: klienci i zamówienia](./sample-xsd-file-customers-and-orders1.md). Dzięki temu Klauzula join zawsze będzie działała.

To zapytanie najpierw pobiera wszystkie elementy `Customer`, a następnie łączy je z elementami `Order`. Wybiera tylko zamówienia dla klientów o `CustomerID` większej niż "K". Następnie projektuje nowy element `Order` zawierający informacje o klientach w poszczególnych zamówieniach.

W tym przykładzie zastosowano następujący dokument XML: [przykładowy plik XML: Customers i Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).

W tym przykładzie zastosowano następujący schemat XSD: [przykładowy plik XSD: klienci i zamówienia](./sample-xsd-file-customers-and-orders1.md).

Łączenie w ten sposób nie będzie działać prawidłowo. Sprzężenia są wykonywane za pośrednictwem wyszukiwania liniowego. Brak tabel lub indeksów skrótów, które mogą pomóc w wydajności.

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
