---
title: Dodawanie elementów, atrybutów i węzłów do drzewa XML (C#)
ms.date: 07/20/2015
ms.assetid: db911e4f-40aa-499a-9500-a9763bb6df56
ms.openlocfilehash: 87b63df1011af9594ff44bed6385f9d82dee08a2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54585880"
---
# <a name="adding-elements-attributes-and-nodes-to-an-xml-tree-c"></a>Dodawanie elementów, atrybutów i węzłów do drzewa XML (C#)
Zawartość (elementy, atrybuty, komentarzy, instrukcji przetwarzania, tekstu i CDATA) można dodać do istniejącego drzewa XML.  
  
## <a name="methods-for-adding-content"></a>Metody dodawania zawartości  
 Poniższych metod Dodaj zawartość elementu podrzędnego do <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XDocument>:  
  
|Metoda|Opis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.Add%2A>|Dodaje zawartość na końcu zawartości podrzędnych <xref:System.Xml.Linq.XContainer>.|  
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|Dodaje zawartość na początku zawartość elementu podrzędnego <xref:System.Xml.Linq.XContainer>.|  
  
 Poniższych metod Dodaj zawartość jako węzły równorzędne <xref:System.Xml.Linq.XNode>. Najbardziej typowe węzeł, do której możesz dodać zawartość element równorzędny jest <xref:System.Xml.Linq.XElement>, chociaż możesz dodać zawartość prawidłowy element równorzędny takiego jak do innych typów węzłów <xref:System.Xml.Linq.XText> lub <xref:System.Xml.Linq.XComment>.  
  
|Metoda|Opis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|Dodaje zawartość po <xref:System.Xml.Linq.XNode>.|  
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|Dodaje zawartość przed <xref:System.Xml.Linq.XNode>.|  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Poniższy przykład tworzy dwie drzew XML, a następnie modyfikuje jednego z drzewa.  
  
### <a name="code"></a>Kod  
  
```csharp  
XElement srcTree = new XElement("Root",   
    new XElement("Element1", 1),  
    new XElement("Element2", 2),  
    new XElement("Element3", 3),  
    new XElement("Element4", 4),  
    new XElement("Element5", 5)  
);  
XElement xmlTree = new XElement("Root",  
    new XElement("Child1", 1),  
    new XElement("Child2", 2),  
    new XElement("Child3", 3),  
    new XElement("Child4", 4),  
    new XElement("Child5", 5)  
);  
xmlTree.Add(new XElement("NewChild", "new content"));  
xmlTree.Add(  
    from el in srcTree.Elements()  
    where (int)el > 3  
    select el  
);  
// Even though Child9 does not exist in srcTree, the following statement will not  
// throw an exception, and nothing will be added to xmlTree.  
xmlTree.Add(srcTree.Element("Child9"));  
Console.WriteLine(xmlTree);  
```  
  
### <a name="comments"></a>Komentarze  
 Ten kod generuje następujące dane wyjściowe:  
  
```xml  
<Root>  
  <Child1>1</Child1>  
  <Child2>2</Child2>  
  <Child3>3</Child3>  
  <Child4>4</Child4>  
  <Child5>5</Child5>  
  <NewChild>new content</NewChild>  
  <Element4>4</Element4>  
  <Element5>5</Element5>  
</Root>  
```  
  
## <a name="see-also"></a>Zobacz także

- [Modyfikowanie drzew XML (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
