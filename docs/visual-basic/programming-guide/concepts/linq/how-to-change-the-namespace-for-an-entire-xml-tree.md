---
title: 'Instrukcje: zmienianie przestrzeni nazw dla całego drzewa XML'
ms.date: 07/20/2015
ms.assetid: 1837324b-5cb5-4fa8-95b9-3071efa0f913
ms.openlocfilehash: 11938b575ed5133d930e585dbe4d744e3168cced
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84374982"
---
# <a name="how-to-change-the-namespace-for-an-entire-xml-tree-visual-basic"></a>Instrukcje: zmienianie przestrzeni nazw dla całego drzewa XML (Visual Basic)
Czasami trzeba programistycznie zmienić przestrzeń nazw dla elementu lub atrybutu. Ułatwia to LINQ to XML. <xref:System.Xml.Linq.XElement.Name%2A?displayProperty=nameWithType>Właściwość może być ustawiona. <xref:System.Xml.Linq.XAttribute.Name%2A?displayProperty=nameWithType>Nie można ustawić właściwości, ale można łatwo skopiować atrybuty do <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> , usunąć istniejące atrybuty, a następnie dodać nowe atrybuty, które znajdują się w nowym żądanym obszarze nazw.  
  
 Aby uzyskać więcej informacji, zobacz temat [przestrzenie nazw — omówienie (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).  
  
## <a name="example"></a>Przykład  
 Poniższy kod tworzy dwa drzewa XML w obszarze brak przestrzeni nazw. Następnie zmienia przestrzeń nazw każdego drzewa i łączy je w jedno drzewo.  
  
```vb  
Dim tree1 As XElement = _  
    <Data>  
        <Child MyAttr="content">content</Child>  
    </Data>  
Dim tree2 As XElement = _  
    <Data>  
        <Child MyAttr="content">content</Child>  
    </Data>  
Dim aw As XNamespace = "http://www.adventure-works.com"  
Dim ad As XNamespace = "http://www.adatum.com"  
' change the namespace of every element and attribute in the first tree  
For Each el As XElement In tree1.DescendantsAndSelf  
    el.Name = aw.GetName(el.Name.LocalName)  
    Dim atList As List(Of XAttribute) = el.Attributes().ToList()  
    el.Attributes().Remove()  
    For Each at As XAttribute In atList  
        el.Add(New XAttribute(aw.GetName(at.Name.LocalName), at.Value))  
    Next  
Next  
' change the namespace of every element and attribute in the second tree  
For Each el As XElement In tree2.DescendantsAndSelf()  
    el.Name = ad.GetName(el.Name.LocalName)  
    Dim atList As List(Of XAttribute) = el.Attributes().ToList()  
    el.Attributes().Remove()  
    For Each at As XAttribute In atList  
        el.Add(New XAttribute(ad.GetName(at.Name.LocalName), at.Value))  
    Next  
Next  
' add attribute namespaces so that the tree will be serialized with  
' the aw and ad namespace prefixes  
tree1.Add( _  
    New XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com") _  
)  
tree2.Add( _  
    New XAttribute(XNamespace.Xmlns + "ad", "http://www.adatum.com") _  
)  
' create a new composite tree  
Dim root As XElement = _  
    <Root>  
        <%= tree1 %>  
        <%= tree2 %>  
    </Root>  
Console.WriteLine(root)  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<Root>  
  <aw:Data xmlns:aw="http://www.adventure-works.com">  
    <aw:Child aw:MyAttr="content">content</aw:Child>  
  </aw:Data>  
  <ad:Data xmlns:ad="http://www.adatum.com">  
    <ad:Child ad:MyAttr="content">content</ad:Child>  
  </ad:Data>  
</Root>  
```  
  
## <a name="see-also"></a>Zobacz też

- [Modyfikowanie drzew XML (LINQ to XML) (Visual Basic)](modifying-xml-trees-linq-to-xml.md)
