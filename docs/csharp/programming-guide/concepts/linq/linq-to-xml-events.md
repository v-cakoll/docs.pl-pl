---
title: Zdarzenia LINQ to XML (C#)
ms.date: 07/20/2015
ms.assetid: ce7de951-cba7-4870-9962-733eb01cd680
ms.openlocfilehash: 8e0cb4519dd0fc2bed443d9a62b9a2545d10e161
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253174"
---
# <a name="linq-to-xml-events-c"></a>Zdarzenia LINQ to XML (C#)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]zdarzenia umożliwiają otrzymywanie powiadomień, gdy drzewo XML zostanie zmienione.  
  
 Zdarzenia można dodać do wystąpienia dowolnego <xref:System.Xml.Linq.XObject>. Procedura obsługi zdarzeń będzie następnie otrzymywać zdarzenia dotyczące modyfikacji tego <xref:System.Xml.Linq.XObject> elementu i jego elementów podrzędnych. Na przykład można dodać program obsługi zdarzeń do elementu głównego drzewa i obsłużyć wszystkie modyfikacje drzewa z tego programu obsługi zdarzeń.  
  
 Przykłady [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zdarzeń można znaleźć w tematach <xref:System.Xml.Linq.XObject.Changed> <xref:System.Xml.Linq.XObject.Changing> i.  
  
## <a name="types-and-events"></a>Typy i zdarzenia  
 Następujące typy są używane podczas pracy ze zdarzeniami:  
  
|Typ|Opis|  
|----------|-----------------|  
|<xref:System.Xml.Linq.XObjectChange>|Określa typ zdarzenia, gdy zdarzenie jest zgłaszane dla elementu <xref:System.Xml.Linq.XObject>.|  
|<xref:System.Xml.Linq.XObjectChangeEventArgs>|Dostarcza dane dla <xref:System.Xml.Linq.XObject.Changing> zdarzeń i <xref:System.Xml.Linq.XObject.Changed> .|  
  
 Podczas modyfikowania drzewa XML są zgłaszane następujące zdarzenia:  
  
|Zdarzenie|Opis|  
|-----------|-----------------|  
|<xref:System.Xml.Linq.XObject.Changing>|Występuje tuż przed tym <xref:System.Xml.Linq.XObject> lub dowolnym z jego obiektów podrzędnych zostanie zmieniony.|  
|<xref:System.Xml.Linq.XObject.Changed>|Występuje po <xref:System.Xml.Linq.XObject> zmianie lub dowolnych jego elementów podrzędnych.|  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Zdarzenia są przydatne, gdy chcesz zachować pewne zagregowane informacje w drzewie XML. Na przykład możesz chcieć zachować sumę faktury, która jest sumą wierszy faktury. Ten przykład używa zdarzeń, aby zachować sumę wszystkich elementów podrzędnych w ramach elementu `Items`złożonego.  
  
### <a name="code"></a>Kod  
  
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
  