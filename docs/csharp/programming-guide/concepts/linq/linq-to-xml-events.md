---
title: "LINQ do XML zdarzeń (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: ce7de951-cba7-4870-9962-733eb01cd680
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 90e868c7de8c4eb8f252a914acf4bffe2fd8a6ca
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="linq-to-xml-events-c"></a>LINQ do XML zdarzeń (C#)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]zdarzenia umożliwiają powiadomienia, gdy zostanie zmieniona drzewo XML.  
  
 Zdarzenia można dodawać do wystąpienia dowolnego <xref:System.Xml.Linq.XObject>. Program obsługi zdarzeń Zadzwonimy zdarzenia dla zmian w tym <xref:System.Xml.Linq.XObject> i wszystkie jego elementy podrzędne. Można na przykład, Dodaj program obsługi zdarzeń do katalogu głównego drzewa i obsługiwać wszystkie modyfikacje w drzewie z tej obsługi zdarzeń.  
  
 Przykłady [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zdarzenia, zobacz <xref:System.Xml.Linq.XObject.Changing> i <xref:System.Xml.Linq.XObject.Changed>.  
  
## <a name="types-and-events"></a>Typy i zdarzenia  
 Podczas pracy ze zdarzeniami, można użyć następujących typów:  
  
|Typ|Opis|  
|----------|-----------------|  
|<xref:System.Xml.Linq.XObjectChange>|Określa typ zdarzenia, gdy zdarzenie jest wywoływane dla <xref:System.Xml.Linq.XObject>.|  
|<xref:System.Xml.Linq.XObjectChangeEventArgs>|Udostępnia dane dla <xref:System.Xml.Linq.XObject.Changing> i <xref:System.Xml.Linq.XObject.Changed> zdarzenia.|  
  
 Następujące zdarzenia są generowane po zmodyfikowaniu drzewo XML:  
  
|Zdarzenie|Opis|  
|-----------|-----------------|  
|<xref:System.Xml.Linq.XObject.Changing>|Występuje bezpośrednio przed tym <xref:System.Xml.Linq.XObject> lub dowolnego z jego węzłów podrzędnych ma zmienić.|  
|<xref:System.Xml.Linq.XObject.Changed>|Występuje, gdy <xref:System.Xml.Linq.XObject> został zmieniony lub dowolną z jego elementy podrzędne zostały zmienione.|  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Zdarzenia są przydatne, jeśli chcesz zachować niektóre agregują informacje w drzewie XML. Można na przykład obsługa Suma faktury, który jest sumą pozycje, faktury. W tym przykładzie użyto zdarzeń, aby zachować Suma wszystkich elementów podrzędnych w elemencie złożonych `Items`.  
  
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
 [Zaawansowane LINQ do XML programowania (C#)](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
