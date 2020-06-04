---
title: 'Instrukcje: pobieranie wartości elementu (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 76b9b2a5-b3ba-49da-ba74-82100e1bd21c
ms.openlocfilehash: b8ff44416f0fbb590119af7e11714e449185d977
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397794"
---
# <a name="how-to-retrieve-the-value-of-an-element-linq-to-xml-visual-basic"></a>Instrukcje: pobieranie wartości elementu (LINQ to XML) (Visual Basic)
W tym temacie pokazano, jak uzyskać wartość elementów. Istnieją dwa podstawowe sposoby wykonania tej czynności. Jednym ze sposobów jest rzutowanie <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XAttribute> na żądany typ. Operator jawnej konwersji konwertuje zawartość elementu lub atrybutu do określonego typu i przypisuje go do zmiennej. Alternatywnie można użyć <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> właściwości lub <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType> właściwości.  
  
 W przypadku Visual Basic najlepszym podejściem jest użycie <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> właściwości.  
  
## <a name="example"></a>Przykład  
 Aby pobrać wartość elementu, wystarczy przerzutować <xref:System.Xml.Linq.XElement> obiekt na żądany typ. Można zawsze rzutować element na ciąg w następujący sposób:  
  
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
 Można również rzutować elementy do typów innych niż ciąg. Na przykład jeśli masz element zawierający liczbę całkowitą, możesz go rzutować na `int` , jak pokazano w poniższym kodzie:  
  
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
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]zapewnia jawne Operatory rzutowania dla następujących typów danych:,,,,,,,,,, `string` `bool` `bool?` `int` `int?` `uint` `uint?` `long` `long?` `ulong` `ulong?` , `float` , `float?` , `double` ,,,,,, `double?` `decimal` `decimal?` `DateTime` `DateTime?` `TimeSpan` , `TimeSpan?` ,, `GUID` i `GUID?` .  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]zapewnia te same Operatory rzutowania dla <xref:System.Xml.Linq.XAttribute> obiektów.  
  
## <a name="example"></a>Przykład  
 Możesz użyć właściwości, <xref:System.Xml.Linq.XElement.Value%2A> Aby pobrać zawartość elementu:  
  
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
 Czasami próbujesz pobrać wartość elementu, chociaż nie masz pewności, że istnieje. W tym przypadku, gdy przypiszesz element rzutowany do typu dopuszczającego wartość null ( `string` lub jeden z typów wartości null w .NET Framework), jeśli element nie istnieje, przypisana zmienna jest ustawiona na `Nothing` . Poniższy kod pokazuje, że gdy element może lub nie istnieje, łatwiej jest użyć rzutowania niż w celu użycia <xref:System.Xml.Linq.XElement.Value%2A> właściwości.  
  
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
  
## <a name="see-also"></a>Zobacz też

- [Osie LINQ to XML (Visual Basic)](linq-to-xml-axes.md)
