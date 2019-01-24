---
title: 'Instrukcje: Pobieranie wartości atrybutu (LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 5f4b3790-c83f-4eb3-a889-e3587edf3ca1
ms.openlocfilehash: ab14072317bf963e87534b743e3c5a6c39ee39c8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54690725"
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-visual-basic"></a>Instrukcje: Pobieranie wartości atrybutu (LINQ to XML) (Visual Basic)
W tym temacie przedstawiono sposób uzyskania wartości atrybutów. Istnieją dwa sposoby: Można rzutować <xref:System.Xml.Linq.XAttribute> żądany typ; operator jawnej konwersji następnie konwertuje zawartość element lub atrybut do określonego typu. Alternatywnie, można użyć <xref:System.Xml.Linq.XAttribute.Value%2A> właściwości. Jednak zazwyczaj lepszym rozwiązaniem jest rzutowanie. Jeśli możesz rzutować atrybutu typu dopuszczającego wartość null, kod jest prostszy do zapisania podczas pobierania wartości atrybutu, który może być lub może nie istnieć. Aby zapoznać się z przykładami korzystania z tej techniki, zobacz [jak: Pobieranie wartości elementu (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md).  
  
## <a name="example"></a>Przykład  
 W języku Visual Basic właściwość atrybutu zintegrowane służy do pobierania wartości atrybutu.  
  
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
 W języku Visual Basic właściwość atrybutu zintegrowane służy do ustawiania wartości atrybutu. Dodatkowo Jeśli używasz właściwości atrybutu zintegrowane można ustawić wartość atrybutu, który nie istnieje atrybut zostanie utworzony.  
  
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
 Poniższy przykład pokazuje sposób pobierania wartości atrybutu którym atrybut jest w przestrzeni nazw. Aby uzyskać więcej informacji, zobacz [Praca z przestrzeniami nazw XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).  
  
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
  
```  
abcde  
```  
  
## <a name="see-also"></a>Zobacz także
- [LINQ do osi XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
