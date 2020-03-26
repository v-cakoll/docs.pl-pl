---
title: 'Jak: Pobieranie wartości elementu (LINQ do XML)'
ms.date: 07/20/2015
ms.assetid: 76b9b2a5-b3ba-49da-ba74-82100e1bd21c
ms.openlocfilehash: b1a61091dc59b403c5d967609e8870492c24347f
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2020
ms.locfileid: "80248937"
---
# <a name="how-to-retrieve-the-value-of-an-element-linq-to-xml-visual-basic"></a>Jak: Pobieranie wartości elementu (LINQ do XML) (Visual Basic)
W tym temacie pokazano, jak uzyskać wartość elementów. Istnieją dwa główne sposoby, aby to zrobić. Jednym ze sposobów <xref:System.Xml.Linq.XElement> jest <xref:System.Xml.Linq.XAttribute> rzucenie lub do żądanego typu. Operator konwersji jawne następnie konwertuje zawartość elementu lub atrybutu do określonego typu i przypisuje go do zmiennej. Goście mogą również skorzystać <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> z <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType> obiektu lub obiektu.  
  
 W języku Visual Basic najlepszym rozwiązaniem <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> jest użycie właściwości.  
  
## <a name="example"></a>Przykład  
 Aby pobrać wartość elementu, wystarczy rzutować <xref:System.Xml.Linq.XElement> obiekt do żądanego typu. Zawsze można rzutować element do ciągu, w następujący sposób:  
  
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
 Można również rzutować elementy do typów innych niż ciąg. Na przykład jeśli masz element, który zawiera całkowitą, można `int`go przerzucić na , jak pokazano w poniższym kodzie:  
  
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
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]zapewnia operatory jawnego rzutu `string` `bool`dla `bool?` `int`następujących `int?` `uint`typów `uint?` `long`danych: , , , , , , `GUID`, `GUID?` `decimal` `decimal?` `DateTime` `DateTime?` `TimeSpan` `TimeSpan?` `long?` `ulong` `ulong?` `float`, , , `float?`, , `double`, `double?`, , , , , , , , , , i .  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]zapewnia te same <xref:System.Xml.Linq.XAttribute> operatory rzutowania dla obiektów.  
  
## <a name="example"></a>Przykład  
 Można użyć <xref:System.Xml.Linq.XElement.Value%2A> właściwości, aby pobrać zawartość elementu:  
  
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
 Czasami spróbuj pobrać wartość elementu, nawet jeśli nie masz pewności, że istnieje. W takim przypadku po przypisaniu elementu rzutowanego do typu `string` możliwego do wartości null (jednego lub jednego z typów wartości nullable w `Nothing`.NET Framework), jeśli element nie istnieje, przypisana zmienna jest po prostu ustawiona na . Poniższy kod pokazuje, że gdy element może lub nie może istnieć, <xref:System.Xml.Linq.XElement.Value%2A> jest łatwiejsze w użyciu rzutowania niż do korzystania z właściwości.  
  
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
  
 Ogólnie rzecz biorąc można napisać prostszy kod podczas korzystania z rzutowania do pobierania zawartości elementów i atrybutów.  
  
## <a name="see-also"></a>Zobacz też

- [Osie LINQ do XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
