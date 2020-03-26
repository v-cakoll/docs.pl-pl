---
title: 'Jak: Pobieranie wartości atrybutu (LINQ do XML)'
ms.date: 07/20/2015
ms.assetid: 5f4b3790-c83f-4eb3-a889-e3587edf3ca1
ms.openlocfilehash: 6593639dcdc234ddda808cfdb5e85ebe1a771b62
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2020
ms.locfileid: "80248950"
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-visual-basic"></a>Jak: Pobieranie wartości atrybutu (LINQ do XML) (Visual Basic)
W tym temacie pokazano, jak uzyskać wartość atrybutów. Istnieją dwa główne sposoby: <xref:System.Xml.Linq.XAttribute> można rzucić do żądanego typu; operator konwersji jawne następnie konwertuje zawartość elementu lub atrybutu do określonego typu. Goście mogą również skorzystać <xref:System.Xml.Linq.XAttribute.Value%2A> z obiektu. Jednak odlewanie jest na ogół lepszym podejściem. Jeśli rzutujesz atrybut na typ wartości możliwej do wartości null, kod jest prostszy do zapisania podczas pobierania wartości atrybutu, który może lub nie może istnieć. Aby zapoznać się z przykładami tej techniki, zobacz [Jak: Pobieranie wartości elementu (LINQ do XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md).  
  
## <a name="example"></a>Przykład  
 W języku Visual Basic można użyć właściwości atrybutu zintegrowanego, aby pobrać wartość atrybutu.  
  
```vb  
Dim root As XElement = <Root Attr="abcde"/>  
Console.WriteLine(root)  
Dim str As String = root.@Attr  
Console.WriteLine(str)  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<Root Attr="abcde" />  
abcde  
```  
  
## <a name="example"></a>Przykład  
 W języku Visual Basic można użyć właściwości atrybutu zintegrowanego, aby ustawić wartość atrybutu. Ponadto jeśli używasz właściwości atrybutu zintegrowanego, aby ustawić wartość atrybutu, który nie istnieje, zostanie utworzony atrybut.  
  
```vb  
Dim root As XElement = <Root Att1="content"/>  
root.@Att1 = "new content"  
root.@Att2 = "new attribute"  
Console.WriteLine(root)  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<Root Att1="new content" Att2="new attribute" />  
```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak pobrać wartość atrybutu, w którym atrybut znajduje się w obszarze nazw. Aby uzyskać więcej informacji, zobacz [Omówienie obszarów nazw (LINQ do XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <aw:Root aw:Attr="abcde"/>  
        Dim str As String = root.@aw:Attr  
        Console.WriteLine(str)  
    End Sub  
End Module  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```console  
abcde  
```  
  
## <a name="see-also"></a>Zobacz też

- [Osie LINQ do XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
