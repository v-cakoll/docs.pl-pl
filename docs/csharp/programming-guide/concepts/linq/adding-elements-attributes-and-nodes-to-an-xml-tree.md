---
title: Dodawanie elementów, atrybutów i węzłów do drzewa XML (C#)
ms.date: 07/20/2015
ms.assetid: db911e4f-40aa-499a-9500-a9763bb6df56
ms.openlocfilehash: 20d8d9d9c592f5f570d7c94298dcee41763c1f1f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169578"
---
# <a name="adding-elements-attributes-and-nodes-to-an-xml-tree-c"></a>Dodawanie elementów, atrybutów i węzłów do drzewa XML (C#)
Do istniejącego drzewa XML można dodawać zawartość (elementy, atrybuty, komentarze, instrukcje przetwarzania, tekst i CDATA).  
  
## <a name="methods-for-adding-content"></a>Metody dodawania zawartości  
 Następujące metody dodają zawartość <xref:System.Xml.Linq.XElement> podrzędną <xref:System.Xml.Linq.XDocument>do:  
  
|Metoda|Opis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.Add%2A>|Dodaje zawartość na końcu zawartości podrzędnej <xref:System.Xml.Linq.XContainer>pliku .|  
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|Dodaje zawartość na początku zawartości podrzędnej pliku <xref:System.Xml.Linq.XContainer>.|  
  
 Następujące metody dodają zawartość jako węzły równorzędne pliku <xref:System.Xml.Linq.XNode>. Najczęstszym węzłem, do którego <xref:System.Xml.Linq.XElement>dodajesię zawartość równorzędnej, jest , chociaż <xref:System.Xml.Linq.XText> można <xref:System.Xml.Linq.XComment>dodać prawidłową zawartość równorzędnego do innych typów węzłów, takich jak lub .  
  
|Metoda|Opis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|Dodaje zawartość <xref:System.Xml.Linq.XNode>po pliku .|  
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|Dodaje zawartość <xref:System.Xml.Linq.XNode>przed .|  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Poniższy przykład tworzy dwa drzewa XML, a następnie modyfikuje jedno z drzew.  
  
### <a name="code"></a>Code  
  
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
  