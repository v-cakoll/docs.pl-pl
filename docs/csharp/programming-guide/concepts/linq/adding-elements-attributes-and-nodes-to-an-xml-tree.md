---
title: Dodawanie elementów, atrybutów i węzłów do drzewa XML (C#)
description: Dowiedz się więcej o metodach dodawania zawartości, takich jak elementy, atrybuty, komentarze, instrukcje przetwarzania i tekst do istniejącego drzewa XML.
ms.date: 07/20/2015
ms.assetid: db911e4f-40aa-499a-9500-a9763bb6df56
ms.openlocfilehash: 78a84401494e2d4280799632fa42dc95574e3e10
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105548"
---
# <a name="adding-elements-attributes-and-nodes-to-an-xml-tree-c"></a>Dodawanie elementów, atrybutów i węzłów do drzewa XML (C#)
Możesz dodać zawartość (elementy, atrybuty, komentarze, instrukcje przetwarzania, tekst i CDATA) do istniejącego drzewa XML.  
  
## <a name="methods-for-adding-content"></a>Metody dodawania zawartości  
 Następujące metody dodają zawartość podrzędną do elementu <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XDocument> :  
  
|Metoda|Opis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.Add%2A>|Dodaje zawartość na końcu zawartości podrzędnej <xref:System.Xml.Linq.XContainer> .|  
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|Dodaje zawartość na początku zawartości podrzędnej <xref:System.Xml.Linq.XContainer> .|  
  
 Poniższe metody dodają zawartość jako węzły równorzędne <xref:System.Xml.Linq.XNode> . Najbardziej typowym węzłem, do którego dodawana jest zawartość elementu równorzędnego <xref:System.Xml.Linq.XElement> , jest, chociaż można dodać prawidłową zawartość równorzędną do innych typów węzłów, takich jak <xref:System.Xml.Linq.XText> lub <xref:System.Xml.Linq.XComment> .  
  
|Metoda|Opis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|Dodaje zawartość po <xref:System.Xml.Linq.XNode> .|  
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|Dodaje zawartość przed <xref:System.Xml.Linq.XNode> .|  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Poniższy przykład tworzy dwa drzewa XML, a następnie modyfikuje jedno z drzew.  
  
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
 Ten kod spowoduje wygenerowanie następujących danych wyjściowych:  
  
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
  