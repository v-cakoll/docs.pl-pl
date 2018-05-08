---
title: Usuwanie elementy, atrybuty i węzły z drzewa XML (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 5cf21919-4360-4b49-b29d-58ea3164ac72
ms.openlocfilehash: dbc5cfd7bf6e1f1b77dd14a6771c387fac29d062
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="removing-elements-attributes-and-nodes-from-an-xml-tree-visual-basic"></a>Usuwanie elementy, atrybuty i węzły z drzewa XML (Visual Basic)
Drzewo XML można zmodyfikować usunięcie elementów, atrybutów i innych typów węzłów.  
  
 Usuwanie pojedynczy element lub jeden atrybut z dokumentu XML jest prosta. Jednak podczas usuwania kolekcji elementów lub atrybutów, należy najpierw zmaterializowania kolekcji do listy, a następnie usuń z listy elementów lub atrybutów. Najlepszym rozwiązaniem jest użycie <xref:System.Xml.Linq.Extensions.Remove%2A> — metoda rozszerzenia, co zrobić to za Ciebie.  
  
 Głównym celem tej czynności jest zwróciło większość kolekcje, które można pobrać z drzewa XML przy użyciu odroczonego wykonania. Jeśli użytkownik nie najpierw zmaterializowania je do listy, lub jeśli nie używasz metody rozszerzenia, istnieje możliwość wystąpienia klasy usterek. Aby uzyskać więcej informacji, zobacz [mieszanych deklaratywne usterki kodu kodu/Imperatywne (LINQ do XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/mixed-declarative-code-imperative-code-bugs-linq-to-xml.md).  
  
 Następujące metody usuń węzły i atrybuty z drzewa XML.  
  
|Metoda|Opis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Remove%2A?displayProperty=nameWithType>|Usuwa <xref:System.Xml.Linq.XAttribute> po swoim obiekcie nadrzędnym.|  
|<xref:System.Xml.Linq.XContainer.RemoveNodes%2A?displayProperty=nameWithType>|Usuwa węzłów podrzędnych z <xref:System.Xml.Linq.XContainer>.|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|Usuwa zawartość oraz atrybutów z <xref:System.Xml.Linq.XElement>.|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|Usuwa atrybuty <xref:System.Xml.Linq.XElement>.|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|W przypadku przekazania `null` dla wartości, a następnie usuwa ten atrybut.|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|W przypadku przekazania `null` dla wartości, a następnie usuwa element podrzędny.|  
|<xref:System.Xml.Linq.XNode.Remove%2A?displayProperty=nameWithType>|Usuwa <xref:System.Xml.Linq.XNode> po swoim obiekcie nadrzędnym.|  
|<xref:System.Xml.Linq.Extensions.Remove%2A?displayProperty=nameWithType>|Usuwa każdy atrybut lub element w kolekcji źródłowej z jego elementu nadrzędnego.|  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 W tym przykładzie przedstawiono trzy sposoby usuwanie elementów. Po pierwsze Usuwa pojedynczy element. Po drugie, pobiera kolekcję elementów, zostaje je przy użyciu <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> , operator i spowoduje usunięcie kolekcji. Na koniec pobiera kolekcję elementów i usuwa je przy użyciu <xref:System.Xml.Linq.Extensions.Remove%2A> — metoda rozszerzenia.  
  
 Aby uzyskać więcej informacji na temat <xref:System.Linq.Enumerable.ToList%2A> operatora, zobacz [konwertowanie typów danych (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/converting-data-types.md).  
  
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
  
 Należy zauważyć, że pierwszy element podwójnym został usunięty z `Child1`. Wszystkie elementy podrzędne zostały usunięte z `Child2` i z `Child3`.  
  
## <a name="see-also"></a>Zobacz też  
 [Modyfikowanie drzew XML (LINQ do XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
