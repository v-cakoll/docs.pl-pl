---
title: Jak przekształcić kształt drzewa XML (C#)
ms.date: 07/20/2015
ms.assetid: 93c5d426-dea2-4709-a991-60204de42e8f
ms.openlocfilehash: 91f91ed6fea5371fae2ce67a413f4825f37af6c3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75347303"
---
# <a name="how-to-transform-the-shape-of-an-xml-tree-c"></a>Jak przekształcić kształt drzewa XML (C#)
*Kształt* dokumentu XML odnosi się do jego nazw elementów, nazw atrybutów i cech jego hierarchii.  
  
 Czasami trzeba będzie zmienić kształt dokumentu XML. Na przykład może być trzeba wysłać istniejący dokument XML do innego systemu, który wymaga różnych nazw elementów i atrybutów. Można przejść przez dokument, usuwanie i zmienianie nazw elementów zgodnie z wymaganiami, ale przy użyciu funkcjonalnych wyników budowy w bardziej czytelny i konserwacji kodu. Aby uzyskać więcej informacji na temat konstrukcji funkcjonalnej, zobacz [Functional Construction (LINQ to XML) (C#).](./functional-construction-linq-to-xml.md)  
  
 Pierwszy przykład zmienia organizację dokumentu XML. Przenosi złożone elementy z jednego miejsca w drzewie do drugiego.  
  
 Drugi przykład w tym temacie tworzy dokument XML o innym kształcie niż dokument źródłowy. Zmienia obudowę nazw elementów, zmienia nazwy niektórych elementów i pozostawia niektóre elementy z drzewa źródłowego z przekształconego drzewa.  
  
## <a name="example"></a>Przykład  
 Poniższy kod zmienia kształt pliku XML przy użyciu osadzonych wyrażeń kwerend.  
  
 Źródłowy dokument XML w `Customers` tym `Root` przykładzie zawiera element pod elementem, który zawiera wszystkich klientów. Zawiera również `Orders` element pod `Root` elementem, który zawiera wszystkie zamówienia. W tym przykładzie tworzy nowe drzewo XML, w którym `Orders` zamówienia dla `Customer` każdego klienta są zawarte w elemencie w elemencie. Oryginalny dokument zawiera `CustomerID` również element `Order` w elemencie; ten element zostanie usunięty z dokumentu o zmienionej kształcie.  
  
 W tym przykładzie użyto następującego dokumentu XML: [Przykładowy plik XML: Klienci i zamówienia (LINQ do XML).](./sample-xml-file-customers-and-orders-linq-to-xml-2.md)  
  
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
 W tym przykładzie zmienia nazwy niektórych elementów i konwertuje niektóre atrybuty do elementów.  
  
 Kod wywołuje `ConvertAddress`, który zwraca <xref:System.Xml.Linq.XElement> listę obiektów. Argument metody jest kwerendą, która `Address` określa złożony `Type` element, w `"Shipping"`którym atrybut ma wartość .  
  
 W tym przykładzie użyto następującego dokumentu XML: [Przykładowy plik XML: Typowe zamówienie zakupu (LINQ do XML).](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md)  
  
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
