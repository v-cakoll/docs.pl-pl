---
title: LINQ do zdarzeń XML (C#)
ms.date: 07/20/2015
ms.assetid: ce7de951-cba7-4870-9962-733eb01cd680
ms.openlocfilehash: 8e0cb4519dd0fc2bed443d9a62b9a2545d10e161
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "70253174"
---
# <a name="linq-to-xml-events-c"></a>LINQ do zdarzeń XML (C#)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]zdarzenia umożliwiają powiadamianie o zmianie drzewa XML.  
  
 Zdarzenia można dodać do wystąpienia <xref:System.Xml.Linq.XObject>dowolnego pliku . Program obsługi zdarzeń otrzyma zdarzenia dla <xref:System.Xml.Linq.XObject> modyfikacji tego i dowolnego z jego elementów podrzędnych. Na przykład można dodać program obsługi zdarzeń do katalogu głównego drzewa i obsługiwać wszystkie modyfikacje do drzewa z tego programu obsługi zdarzeń.  
  
 Przykłady [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zdarzeń można <xref:System.Xml.Linq.XObject.Changing> znaleźć <xref:System.Xml.Linq.XObject.Changed>w części I .  
  
## <a name="types-and-events"></a>Typy i wydarzenia  
 Podczas pracy ze zdarzeniami należy używać następujących typów:  
  
|Typ|Opis|  
|----------|-----------------|  
|<xref:System.Xml.Linq.XObjectChange>|Określa typ zdarzenia, gdy zdarzenie jest <xref:System.Xml.Linq.XObject>wywoływane dla pliku .|  
|<xref:System.Xml.Linq.XObjectChangeEventArgs>|Zawiera dane <xref:System.Xml.Linq.XObject.Changing> dla <xref:System.Xml.Linq.XObject.Changed> i zdarzeń.|  
  
 Podczas modyfikowania drzewa XML są wywoływane następujące zdarzenia:  
  
|Wydarzenie|Opis|  
|-----------|-----------------|  
|<xref:System.Xml.Linq.XObject.Changing>|Występuje tuż <xref:System.Xml.Linq.XObject> przed tym lub którykolwiek z jego elementów podrzędnych będzie się zmieniać.|  
|<xref:System.Xml.Linq.XObject.Changed>|Występuje, <xref:System.Xml.Linq.XObject> gdy zmienił się lub którykolwiek z jego elementów podrzędnych uległ zmianie.|  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Zdarzenia są przydatne, gdy chcesz zachować pewne informacje zagregowane w drzewie XML. Na przykład można zachować sumę faktury, która jest sumą pozycji faktury. W tym przykładzie użyto zdarzeń do utrzymania sumy `Items`wszystkich elementów podrzędnych w elemencie złożonym .  
  
### <a name="code"></a>Code  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Total", "0"),  
    new XElement("Items")  
);  
XElement total = root.Element("Total");  
XElement items = root.Element("Items");  
items.Changed += (object sender, XObjectChangeEventArgs cea) =>  
{  
    switch (cea.ObjectChange)  
    {  
        case XObjectChange.Add:  
            if (sender is XElement)  
                total.Value = ((int)total + (int)(XElement)sender).ToString();  
            if (sender is XText)  
                total.Value = ((int)total + (int)((XText)sender).Parent).ToString();  
            break;  
        case XObjectChange.Remove:  
            if (sender is XElement)  
                total.Value = ((int)total - (int)(XElement)sender).ToString();  
            if (sender is XText)  
                total.Value = ((int)total - Int32.Parse(((XText)sender).Value)).ToString();  
            break;  
    }  
    Console.WriteLine("Changed {0} {1}",  
      sender.GetType().ToString(), cea.ObjectChange.ToString());  
};  
items.SetElementValue("Item1", 25);  
items.SetElementValue("Item2", 50);  
items.SetElementValue("Item2", 75);  
items.SetElementValue("Item3", 133);  
items.SetElementValue("Item1", null);  
items.SetElementValue("Item4", 100);  
Console.WriteLine("Total:{0}", (int)total);  
Console.WriteLine(root);  
```  
  
### <a name="comments"></a>Komentarze  
 Ten kod generuje następujące dane wyjściowe:  
  
```output  
Changed System.Xml.Linq.XElement Add  
Changed System.Xml.Linq.XElement Add  
Changed System.Xml.Linq.XText Remove  
Changed System.Xml.Linq.XText Add  
Changed System.Xml.Linq.XElement Add  
Changed System.Xml.Linq.XElement Remove  
Changed System.Xml.Linq.XElement Add  
Total:308  
<Root>  
  <Total>308</Total>  
  <Items>  
    <Item2>75</Item2>  
    <Item3>133</Item3>  
    <Item4>100</Item4>  
  </Items>  
</Root>  
```  
  