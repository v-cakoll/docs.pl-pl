---
title: Zdarzenia LINQ to XML (C#)
ms.date: 07/20/2015
ms.assetid: ce7de951-cba7-4870-9962-733eb01cd680
ms.openlocfilehash: 6308d81eac830e11b6d58f8e460dfa377663cd21
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43740120"
---
# <a name="linq-to-xml-events-c"></a>Zdarzenia LINQ to XML (C#)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zdarzenia umożliwiają otrzymasz powiadomienie, gdy zostanie zmieniona drzewa XML.  
  
 Można dodać zdarzenia do dowolnego wystąpienia <xref:System.Xml.Linq.XObject>. Zadzwonimy zdarzenia dla zmian do tego programu obsługi zdarzeń <xref:System.Xml.Linq.XObject> i wszystkich jego obiektów podrzędnych. Na przykład możesz dodać program obsługi zdarzeń do katalogu głównego drzewa i obsługiwać wszystkie modyfikacje w drzewie z tej obsługi zdarzeń.  
  
 Przykłady [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zdarzenia, zobacz <xref:System.Xml.Linq.XObject.Changing> i <xref:System.Xml.Linq.XObject.Changed>.  
  
## <a name="types-and-events"></a>Typy i zdarzenia  
 Podczas pracy ze zdarzeniami należy użyć następujących typów:  
  
|Typ|Opis|  
|----------|-----------------|  
|<xref:System.Xml.Linq.XObjectChange>|Określa typ zdarzenia, gdy zdarzenie jest wywoływane dla <xref:System.Xml.Linq.XObject>.|  
|<xref:System.Xml.Linq.XObjectChangeEventArgs>|Udostępnia dane dla <xref:System.Xml.Linq.XObject.Changing> i <xref:System.Xml.Linq.XObject.Changed> zdarzenia.|  
  
 Następujące zdarzenia są wywoływane, gdy modyfikowanie drzewa XML:  
  
|Zdarzenie|Opis|  
|-----------|-----------------|  
|<xref:System.Xml.Linq.XObject.Changing>|Występuje zaraz przed tym <xref:System.Xml.Linq.XObject> lub przechodzi do dowolnego z jego obiektów podrzędnych do zmiany.|  
|<xref:System.Xml.Linq.XObject.Changed>|Występuje, gdy <xref:System.Xml.Linq.XObject> został zmieniony lub dowolnego z jego elementy podrzędne zostały zmienione.|  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Zdarzenia są przydatne, gdy użytkownik chce przechowywać pewne informacje agregacji w drzewie XML. Na przykład można zachować Suma faktury, która jest sumą pozycje faktury. W tym przykładzie użyto zdarzeń do obsługi sumę wszystkich elementów podrzędnych w elemencie złożonych `Items`.  
  
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
  
```  
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
  
## <a name="see-also"></a>Zobacz też

- [Zaawansowane LINQ to XML programowania (C#)](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
