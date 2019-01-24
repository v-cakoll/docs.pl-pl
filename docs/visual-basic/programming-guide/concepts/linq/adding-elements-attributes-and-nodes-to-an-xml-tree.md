---
title: Dodawanie elementów, atrybutów i węzłów do drzewa XML (Visual Basic)
ms.date: 07/20/2015
ms.assetid: e243e694-c987-43aa-8b22-1e33dace582c
ms.openlocfilehash: 5b15a3a943425a7443ad0986d8d91973d0090ed3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54669344"
---
# <a name="adding-elements-attributes-and-nodes-to-an-xml-tree-visual-basic"></a>Dodawanie elementów, atrybutów i węzłów do drzewa XML (Visual Basic)
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
  
```vb  
Dim srcTree As XElement = _  
    <Root>  
        <Element1>1</Element1>  
        <Element2>2</Element2>  
        <Element3>3</Element3>  
        <Element4>4</Element4>  
        <Element5>5</Element5>  
    </Root>  
Dim xmlTree As XElement = _  
    <Root>  
        <Child1>1</Child1>  
        <Child2>2</Child2>  
        <Child3>3</Child3>  
        <Child4>4</Child4>  
        <Child5>5</Child5>  
    </Root>  
  
xmlTree.Add(<NewChild>new content</NewChild>)  
xmlTree.Add( _  
    From el In srcTree.Elements() _  
    Where CInt(el) > 3 _  
    Select el)  
  
' Even though Child9 does not exist in srcTree, the following statement  
' will not throw an exception, and nothing will be added to xmlTree.  
xmlTree.Add(srcTree.Element("Child9"))  
Console.WriteLine(xmlTree)  
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
- [Modyfikowanie drzew XML (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
