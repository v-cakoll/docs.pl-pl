---
title: Jak sprzęgać dwie kolekcje (LINQ to XML) (C#)
description: Ten przykład w języku C# łączy elementy w LINQ to XML z innymi elementami i generuje nowy dokument XML.
ms.date: 07/20/2015
ms.assetid: 7b817ede-911a-4cff-9dd3-639c3fc228c9
ms.openlocfilehash: 10792ed4907e778b41821c9b32574bd8fc0ab35f
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104994"
---
# <a name="how-to-join-two-collections-linq-to-xml-c"></a>Jak sprzęgać dwie kolekcje (LINQ to XML) (C#)

Element lub atrybut w dokumencie XML czasami może odwoływać się do innego elementu lub atrybutu. [Przykładowy plik XML: Customers i Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md) dokument XML zawiera listę klientów i listę zamówień. Każdy `Customer` element zawiera `CustomerID` atrybut. Każdy `Order` element zawiera `CustomerID` element. `CustomerID`Element w każdym porządku odwołuje się do `CustomerID` atrybutu w kliencie.

[Przykładowy plik XSD tematu: klienci i zamówienia](./sample-xsd-file-customers-and-orders1.md) zawierają XSD, których można użyć do zweryfikowania tego dokumentu. Używa `xs:key` i `xs:keyref` funkcji XSD, aby określić, że `CustomerID` atrybut `Customer` elementu jest kluczem i aby ustanowić relację między `CustomerID` elementem w każdym `Order` elemencie a `CustomerID` atrybutem w każdym `Customer` elemencie.

Za pomocą programu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] można korzystać z tej relacji przy użyciu `join` klauzuli.

Ponieważ nie ma dostępnego indeksu, takie dołączenie będzie miało niską wydajność w czasie wykonywania.

Aby uzyskać bardziej szczegółowe informacje na temat `join` , zobacz [Operacje łączenia (C#)](./join-operations.md).

## <a name="example"></a>Przykład

Poniższy przykład sprzęga `Customer` elementy do `Order` elementów i generuje nowy dokument XML, który zawiera `CompanyName` element w zamówieniach.

Przed wykonaniem zapytania, przykład sprawdza, czy dokument jest zgodny ze schematem w [przykładowym pliku XSD: klienci i zamówienia](./sample-xsd-file-customers-and-orders1.md). Dzięki temu Klauzula join zawsze będzie działała.

To zapytanie najpierw pobiera wszystkie `Customer` elementy, a następnie łączy je z `Order` elementami. Wybiera tylko zamówienia dla klientów o `CustomerID` większej niż "K". Następnie projektuje nowy `Order` element, który zawiera informacje o kliencie w ramach poszczególnych zamówień.

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

Ten kod spowoduje wygenerowanie następujących danych wyjściowych:

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
