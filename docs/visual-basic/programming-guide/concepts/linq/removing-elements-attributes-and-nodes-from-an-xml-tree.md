---
title: Usuwanie elementów, atrybutów i węzłów z drzewa XML
ms.date: 07/20/2015
ms.assetid: 5cf21919-4360-4b49-b29d-58ea3164ac72
ms.openlocfilehash: 4cce1eff469c1f737e18b88cce30155547d9f11b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348952"
---
# <a name="removing-elements-attributes-and-nodes-from-an-xml-tree-visual-basic"></a>Usuwanie elementów, atrybutów i węzłów z drzewa XML (Visual Basic)
Można modyfikować drzewo XML, usuwać elementy, atrybuty i inne typy węzłów.  
  
 Usuwanie pojedynczego elementu lub pojedynczego atrybutu z dokumentu XML jest proste. Jednak podczas usuwania kolekcji elementów lub atrybutów należy najpierw zmaterializowania kolekcję do listy, a następnie usunąć elementy lub atrybuty z listy. Najlepszym rozwiązaniem jest użycie metody rozszerzenia <xref:System.Xml.Linq.Extensions.Remove%2A>, która pozwoli Ci to robić.  
  
 Głównym powodem tego jest to, że większość kolekcji pobieranych z drzewa XML jest przeprowadzana przy użyciu odroczonego wykonania. Jeśli nie chcesz najpierw zmaterializowania ich do listy lub jeśli nie korzystasz z metod rozszerzenia, możliwe jest napotkanie pewnej klasy błędów. Aby uzyskać więcej informacji, zobacz [mieszany kod deklaratywny/niezbędny kod (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/mixed-declarative-code-imperative-code-bugs-linq-to-xml.md).  
  
 Poniższe metody usuwają węzły i atrybuty z drzewa XML.  
  
|Metoda|Opis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Remove%2A?displayProperty=nameWithType>|Usuwa <xref:System.Xml.Linq.XAttribute> z jego elementu nadrzędnego.|  
|<xref:System.Xml.Linq.XContainer.RemoveNodes%2A?displayProperty=nameWithType>|Usuwa węzły podrzędne z <xref:System.Xml.Linq.XContainer>.|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|Usuwa zawartość i atrybuty z <xref:System.Xml.Linq.XElement>.|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|Usuwa atrybuty <xref:System.Xml.Linq.XElement>.|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|W przypadku przekazania `null` dla wartości, a następnie usunięcia atrybutu.|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|Jeśli przejdziesz `null` do wartości, spowoduje to usunięcie elementu podrzędnego.|  
|<xref:System.Xml.Linq.XNode.Remove%2A?displayProperty=nameWithType>|Usuwa <xref:System.Xml.Linq.XNode> z jego elementu nadrzędnego.|  
|<xref:System.Xml.Linq.Extensions.Remove%2A?displayProperty=nameWithType>|Usuwa każdy atrybut lub element z kolekcji źródłowej z jego elementu nadrzędnego.|  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Ten przykład ilustruje trzy podejścia do usuwania elementów. Najpierw usuwa pojedynczy element. Po drugie Pobiera kolekcję elementów, materializuje je przy użyciu operatora <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> i usuwa kolekcję. Na koniec Pobiera kolekcję elementów i usuwa je przy użyciu metody rozszerzenia <xref:System.Xml.Linq.Extensions.Remove%2A>.  
  
 Aby uzyskać więcej informacji na temat operatora <xref:System.Linq.Enumerable.ToList%2A>, zobacz [konwertowanie typów danych (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/converting-data-types.md).  
  
### <a name="code"></a>Kod  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <Child1>  
            <GrandChild1/>  
            <GrandChild2/>  
            <GrandChild3/>  
        </Child1>  
        <Child2>  
            <GrandChild4/>  
            <GrandChild5/>  
            <GrandChild6/>  
        </Child2>  
        <Child3>  
            <GrandChild7/>  
            <GrandChild8/>  
            <GrandChild9/>  
        </Child3>  
    </Root>  
root.<Child1>.<GrandChild1>.Remove()  
root.<Child2>.Elements().ToList().Remove()  
root.<Child3>.Elements().Remove()  
Console.WriteLine(root)  
```  
  
### <a name="comments"></a>Komentarze  
 Ten kod generuje następujące dane wyjściowe:  
  
```xml  
<Root>  
  <Child1>  
    <GrandChild2 />  
    <GrandChild3 />  
  </Child1>  
  <Child2 />  
  <Child3 />  
</Root>  
```  
  
 Zwróć uwagę, że pierwszy element grandchild został usunięty z `Child1`. Wszystkie elementy podrzędne zostały usunięte z `Child2` i z `Child3`.  
  
## <a name="see-also"></a>Zobacz także

- [Modyfikowanie drzew XML (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
