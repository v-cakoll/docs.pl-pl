---
title: 'Instrukcje: pobieranie wartości elementu (LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 76b9b2a5-b3ba-49da-ba74-82100e1bd21c
ms.openlocfilehash: cbeda0b7f4b1c1161b14c0ecf8c0971139405a75
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320423"
---
# <a name="how-to-retrieve-the-value-of-an-element-linq-to-xml-visual-basic"></a>Instrukcje: pobieranie wartości elementu (LINQ to XML) (Visual Basic)
W tym temacie pokazano, jak uzyskać wartość elementów. Istnieją dwa podstawowe sposoby wykonania tej czynności. Jednym ze sposobów jest rzutowanie <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XAttribute> na żądany typ. Operator jawnej konwersji konwertuje zawartość elementu lub atrybutu do określonego typu i przypisuje go do zmiennej. Alternatywnie można użyć właściwości <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> lub właściwości <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType>.  
  
 W przypadku Visual Basic najlepszym podejściem jest użycie właściwości <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType>.  
  
## <a name="example"></a>Przykład  
 Aby pobrać wartość elementu, należy po prostu rzutować obiekt <xref:System.Xml.Linq.XElement> na żądany typ. Można zawsze rzutować element na ciąg w następujący sposób:  
  
```vb  
Dim e As XElement = <StringElement>abcde</StringElement>  
Console.WriteLine(e)  
Console.WriteLine("Value of e:" & e.Value)  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="example"></a>Przykład  
 Można również rzutować elementy do typów innych niż ciąg. Na przykład jeśli masz element zawierający liczbę całkowitą, możesz rzutować go na `int`, jak pokazano w poniższym kodzie:  
  
```vb  
Dim e As XElement = <Age>44</Age>  
Console.WriteLine(e)  
Console.WriteLine("Value of e:" & CInt(e))  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<Age>44</Age>  
Value of e:44  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zapewnia jawne Operatory rzutowania dla następujących typów danych: `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 0, 1, 2 i 3.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zapewnia te same Operatory rzutowania dla obiektów <xref:System.Xml.Linq.XAttribute>.  
  
## <a name="example"></a>Przykład  
 Aby pobrać zawartość elementu, można użyć właściwości <xref:System.Xml.Linq.XElement.Value%2A>:  
  
```vb  
Dim e As XElement = <StringElement>abcde</StringElement>  
Console.WriteLine(e)  
Console.WriteLine("Value of e:" & e.Value)  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="example"></a>Przykład  
 Czasami próbujesz pobrać wartość elementu, chociaż nie masz pewności, że istnieje. W tym przypadku, gdy przypiszesz element rzutowany do typu dopuszczającego wartość null (`string` lub jeden z typów dopuszczających wartość null w .NET Framework), jeśli element nie istnieje, przypisana zmienna jest po prostu ustawiona na `Nothing`. Poniższy kod pokazuje, że gdy element może lub nie istnieje, łatwiej jest użyć rzutowania, aby użyć właściwości <xref:System.Xml.Linq.XElement.Value%2A>.  
  
```vb  
Dim root As XElement = <Root>  
                           <Child1>child 1 content</Child1>  
                           <Child2>2</Child2>  
                       </Root>  
  
' The following assignments show why it is easier to use  
' casting when the element might or might not exist.  
  
Dim c1 As String = CStr(root.Element("Child1"))  
Console.WriteLine("c1:{0}", IIf(c1 Is Nothing, "element does not exist", c1))  
  
Dim c2 As Nullable(Of Integer) = CType(root.Element("Child2"), Nullable(Of Integer))  
Console.WriteLine("c2:{0}", IIf(Not (c2.HasValue), "element does not exist", c2.ToString()))  
  
Dim c3 As String = CStr(root.Element("Child3"))  
Console.WriteLine("c3:{0}", IIf(c3 Is Nothing, "element does not exist", c3))  
  
Dim c4 As Nullable(Of Integer) = CType(root.Element("Child4"), Nullable(Of Integer))  
Console.WriteLine("c4:{0}", IIf(Not (c4.HasValue), "element does not exist", c4.ToString()))  
  
Console.WriteLine()  
  
' The following assignments show the required code when using  
' the Value property when the attribute might or might not exist.  
' Notice that this is more difficult than the casting approach.  
  
Dim e1 As XElement = root.Element("Child1")  
Dim v1 As String  
If (e1 Is Nothing) Then  
    v1 = Nothing  
Else  
    v1 = e1.Value  
End If  
Console.WriteLine("v1:{0}", IIf(v1 Is Nothing, "element does not exist", v1))  
  
Dim e2 As XElement = root.Element("Child2")  
Dim v2 As Nullable(Of Integer)  
If (e2 Is Nothing) Then  
    v2 = Nothing  
Else  
    v2 = e2.Value  
End If  
Console.WriteLine("v2:{0}", IIf(Not (v2.HasValue), "element does not exist", v2))  
  
Dim e3 As XElement = root.Element("Child3")  
Dim v3 As String  
If (e3 Is Nothing) Then  
    v3 = Nothing  
Else  
    v3 = e3.Value  
End If  
Console.WriteLine("v3:{0}", IIf(v3 Is Nothing, "element does not exist", v3))  
  
Dim e4 As XElement = root.Element("Child4")  
Dim v4 As Nullable(Of Integer)  
If (e4 Is Nothing) Then  
    v4 = Nothing  
Else  
    v4 = e4.Value  
End If  
Console.WriteLine("v4:{0}", IIf(Not (v4.HasValue), "element does not exist", v4))  
```  
  
 Ten kod generuje następujące dane wyjściowe:  
  
```console  
c1:child 1 content  
c2:2  
c3:element does not exist  
c4:element does not exist  
  
v1:child 1 content  
v2:2  
v3:element does not exist  
v4:element does not exist  
```  
  
 Ogólnie rzecz biorąc, można napisać łatwiejszy kod podczas używania rzutowania do pobrania zawartości elementów i atrybutów.  
  
## <a name="see-also"></a>Zobacz także

- [Osie LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
