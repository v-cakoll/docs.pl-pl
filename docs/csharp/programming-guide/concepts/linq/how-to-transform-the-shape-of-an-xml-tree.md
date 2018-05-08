---
title: 'Porady: Przekształcanie kształtu drzewo XML (C#)'
ms.date: 07/20/2015
ms.assetid: 93c5d426-dea2-4709-a991-60204de42e8f
ms.openlocfilehash: 2c1f5728781a89caa813c2e3cbd822ae711a77e4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-transform-the-shape-of-an-xml-tree-c"></a>Porady: Przekształcanie kształtu drzewo XML (C#)
*Kształtu* XML dokumentu odwołuje się do nazwy elementu, nazw atrybutów i cechy jej hierarchii.  
  
 Czasami trzeba będzie zmienić kształt dokumentu XML. Może być konieczne na przykład wysłać istniejący dokument XML do innego systemu, który wymaga innego elementu i nazwach atrybutów. W dokumencie, można przejść, usuwanie i zmiana nazwy elementów jako wymagana, ale przy użyciu konstrukcji funkcjonalności wyniki w bardziej czytelnym i łatwy w obsłudze kodu. Aby uzyskać więcej informacji na temat konstrukcji funkcjonalności, zobacz [funkcjonalności konstrukcji (LINQ do XML) (C#)](../../../../csharp/programming-guide/concepts/linq/functional-construction-linq-to-xml.md).  
  
 Pierwszym przykładzie zmienia organizacji dokumentu XML. Powoduje przeniesienie złożonych elementów z jednej lokalizacji w drzewie do innego.  
  
 Drugi przykład w tym temacie tworzy dokument XML z kształtem innego niż dokumentu źródłowego. Go zmiany wielkości liter nazwy elementów, zmienia nazwę niektóre elementy i pozostawia niektóre elementy z drzewa źródła poza przekształcone drzewa.  
  
## <a name="example"></a>Przykład  
 Poniższy kod zmienia kształt plik XML przy użyciu wyrażenia osadzonego zapytania.  
  
 Dokument XML źródła, w tym przykładzie zawiera `Customers` elementu w obszarze `Root` element, który zawiera wszystkich klientów. Zawiera także `Orders` elementu w obszarze `Root` element, który zawiera wszystkie zamówienia. Nowe drzewo XML, w którym zamówień dla każdego klienta są zawarte w tym przykładzie jest tworzony `Orders` w elemencie `Customer` elementu. Zawiera także oryginalnego dokumentu `CustomerID` element `Order` elementu; spowoduje to element można usunąć z ponownie kształcie dokumentu.  
  
 W tym przykładzie użyto następujących dokumentu XML: [przykładowego pliku XML: Klienci i zamówienia (LINQ do XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).  
  
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
 W tym przykładzie zmienia nazwę niektóre elementy i konwertuje niektóre atrybuty elementów.  
  
 Kod wywołuje `ConvertAddress`, które zwraca listę <xref:System.Xml.Linq.XElement> obiektów. Argument do metody jest kwerendę, która określa `Address` złożonego elementu gdzie `Type` atrybut ma wartość `"Shipping"`.  
  
 W tym przykładzie użyto następujących dokumentu XML: [przykładowego pliku XML: typowe zamówienia zakupu (LINQ do XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Projekcje i przekształcenia (LINQ do XML) (C#)](../../../../csharp/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
