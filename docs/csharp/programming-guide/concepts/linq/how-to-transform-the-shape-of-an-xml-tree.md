---
title: Jak przekształcić kształt drzewa XML (C#)
ms.date: 07/20/2015
ms.assetid: 93c5d426-dea2-4709-a991-60204de42e8f
ms.openlocfilehash: 91f91ed6fea5371fae2ce67a413f4825f37af6c3
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347303"
---
# <a name="how-to-transform-the-shape-of-an-xml-tree-c"></a>Jak przekształcić kształt drzewa XML (C#)
*Kształt* dokumentu XML odwołuje się do jego nazw elementów, nazw atrybutów i cech hierarchii.  
  
 Czasami trzeba będzie zmienić kształt dokumentu XML. Na przykład może być konieczne wysłanie istniejącego dokumentu XML do innego systemu, który wymaga innych nazw elementów i atrybutów. Możesz przejść przez dokument, usunąć i zmienić nazwy elementów zgodnie z potrzebami, ale użycie konstrukcji funkcjonalnej skutkuje bardziej czytelnym i możliwym do utrzymania kodem. Aby uzyskać więcej informacji na temat konstrukcji funkcjonalnej, zobacz [konstrukcja funkcjonalnaC#(LINQ to XML) ()](./functional-construction-linq-to-xml.md).  
  
 Pierwszy przykład zmienia organizację dokumentu XML. Przenosi elementy złożone z jednej lokalizacji w drzewie do innej.  
  
 Drugi przykład w tym temacie tworzy dokument XML o innym kształcie niż dokument źródłowy. Zmiany wielkości liter w nazwach elementów, zmiana nazwy niektórych elementów i pozostawienie niektórych elementów z drzewa źródłowego z przekształconego drzewa.  
  
## <a name="example"></a>Przykład  
 Poniższy kod zmienia kształt pliku XML przy użyciu osadzonych wyrażeń zapytań.  
  
 Źródłowy dokument XML w tym przykładzie zawiera element `Customers` w elemencie `Root`, który zawiera wszystkich klientów. Zawiera również element `Orders` w elemencie `Root`, który zawiera wszystkie zamówienia. Ten przykład tworzy nowe drzewo XML, w którym zamówienia dla każdego klienta znajdują się w `Orders` elementu w ramach elementu `Customer`. Oryginalny dokument zawiera również element `CustomerID` w elemencie `Order`; Ten element zostanie usunięty z dokumentu, który można zmienić.  
  
 W tym przykładzie zastosowano następujący dokument XML: [przykładowy plik XML: Customers i Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).  
  
```csharp  
XElement co = XElement.Load("CustomersOrders.xml");  
XElement newCustOrd =  
    new XElement("Root",  
        from cust in co.Element("Customers").Elements("Customer")  
        select new XElement("Customer",  
            cust.Attributes(),  
            cust.Elements(),  
            new XElement("Orders",  
                from ord in co.Element("Orders").Elements("Order")  
                where (string)ord.Element("CustomerID") == (string)cust.Attribute("CustomerID")  
                select new XElement("Order",  
                    ord.Attributes(),  
                    ord.Element("EmployeeID"),  
                    ord.Element("OrderDate"),  
                    ord.Element("RequiredDate"),  
                    ord.Element("ShipInfo")  
                )  
            )  
        )  
    );  
Console.WriteLine(newCustOrd);  
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
  
 W tym przykładzie zastosowano następujący dokument XML: [przykładowy plik XML: typowe zamówienie zakupu (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).  
  
```csharp  
static IEnumerable<XElement> ConvertAddress(XElement add)  
{  
    List<XElement> fragment = new List<XElement>() {  
        new XElement("NAME", (string)add.Element("Name")),  
        new XElement("STREET", (string)add.Element("Street")),  
        new XElement("CITY", (string)add.Element("City")),  
        new XElement("ST", (string)add.Element("State")),  
        new XElement("POSTALCODE", (string)add.Element("Zip")),  
        new XElement("COUNTRY", (string)add.Element("Country"))  
    };  
    return fragment;  
}  
  
static void Main(string[] args)  
{  
    XElement po = XElement.Load("PurchaseOrder.xml");  
    XElement newPo = new XElement("PO",  
        new XElement("ID", (string)po.Attribute("PurchaseOrderNumber")),  
        new XElement("DATE", (DateTime)po.Attribute("OrderDate")),  
        ConvertAddress(  
            (from el in po.Elements("Address")  
            where (string)el.Attribute("Type") == "Shipping"  
            select el)  
            .First()  
        )  
    );  
    Console.WriteLine(newPo);  
}  
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
