---
title: 'Porady: pobieranie wartości elementu (LINQ do XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 76b9b2a5-b3ba-49da-ba74-82100e1bd21c
ms.openlocfilehash: ff2a1712a79bdedd74fe51391f01dd900ae585e6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-retrieve-the-value-of-an-element-linq-to-xml-visual-basic"></a><span data-ttu-id="ba6c1-102">Porady: pobieranie wartości elementu (LINQ do XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ba6c1-102">How to: Retrieve the Value of an Element (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="ba6c1-103">W tym temacie pokazano, jak pobrać wartość elementów.</span><span class="sxs-lookup"><span data-stu-id="ba6c1-103">This topic shows how to get the value of elements.</span></span> <span data-ttu-id="ba6c1-104">Istnieją dwa sposoby, w tym celu.</span><span class="sxs-lookup"><span data-stu-id="ba6c1-104">There are two main ways to do this.</span></span> <span data-ttu-id="ba6c1-105">Jednym ze sposobów jest można rzutować <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XAttribute> do odpowiedniego typu.</span><span class="sxs-lookup"><span data-stu-id="ba6c1-105">One way is to cast an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XAttribute> to the desired type.</span></span> <span data-ttu-id="ba6c1-106">Operator jawnej konwersji następnie konwertuje zawartość elementu lub atrybutu na określony typ i przypisuje go do zmiennej użytkownika.</span><span class="sxs-lookup"><span data-stu-id="ba6c1-106">The explicit conversion operator then converts the contents of the element or attribute to the specified type and assigns it to your variable.</span></span> <span data-ttu-id="ba6c1-107">Alternatywnie można użyć <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> właściwości lub <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="ba6c1-107">Alternatively, you can use the <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> property or the <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="ba6c1-108">Za pomocą Visual Basic, najlepszym rozwiązaniem jest użycie <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="ba6c1-108">With Visual Basic, the best approach is to use the <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ba6c1-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="ba6c1-109">Example</span></span>  
 <span data-ttu-id="ba6c1-110">Do pobierania wartości elementu, należy po prostu rzutowania <xref:System.Xml.Linq.XElement> obiektu do żądanego typu.</span><span class="sxs-lookup"><span data-stu-id="ba6c1-110">To retrieve the value of an element, you just cast the <xref:System.Xml.Linq.XElement> object to your desired type.</span></span> <span data-ttu-id="ba6c1-111">Zawsze można rzutować elementu na ciąg w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="ba6c1-111">You can always cast an element to a string, as follows:</span></span>  
  
```vb  
Dim e As XElement = <StringElement>abcde</StringElement>  
Console.WriteLine(e)  
Console.WriteLine("Value of e:" & e.Value)  
```  
  
 <span data-ttu-id="ba6c1-112">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="ba6c1-112">This example produces the following output:</span></span>  
  
```xml  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="example"></a><span data-ttu-id="ba6c1-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="ba6c1-113">Example</span></span>  
 <span data-ttu-id="ba6c1-114">Można również rzutować elementów typu innego niż ciąg.</span><span class="sxs-lookup"><span data-stu-id="ba6c1-114">You can also cast elements to types other than string.</span></span> <span data-ttu-id="ba6c1-115">Na przykład, jeśli element, który zawiera całkowitą, można rzutować na `int`, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="ba6c1-115">For example, if you have an element that contains an integer, you can cast it to `int`, as shown in the following code:</span></span>  
  
```vb  
Dim e As XElement = <Age>44</Age>  
Console.WriteLine(e)  
Console.WriteLine("Value of e:" & CInt(e))  
```  
  
 <span data-ttu-id="ba6c1-116">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="ba6c1-116">This example produces the following output:</span></span>  
  
```xml  
<Age>44</Age>  
Value of e:44  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="ba6c1-117"> zawiera operatory jawnego rzutowania dla następujących typów danych: `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?` , `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`, i `GUID?`.</span><span class="sxs-lookup"><span data-stu-id="ba6c1-117"> provides explicit cast operators for the following data types: `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`, and `GUID?`.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="ba6c1-118"> udostępnia tego samego operatory rzutowania dla <xref:System.Xml.Linq.XAttribute> obiektów.</span><span class="sxs-lookup"><span data-stu-id="ba6c1-118"> provides the same cast operators for <xref:System.Xml.Linq.XAttribute> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ba6c1-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="ba6c1-119">Example</span></span>  
 <span data-ttu-id="ba6c1-120">Można użyć <xref:System.Xml.Linq.XElement.Value%2A> właściwość, aby pobrać zawartość elementu:</span><span class="sxs-lookup"><span data-stu-id="ba6c1-120">You can use the <xref:System.Xml.Linq.XElement.Value%2A> property to retrieve the contents of an element:</span></span>  
  
```vb  
Dim e As XElement = <StringElement>abcde</StringElement>  
Console.WriteLine(e)  
Console.WriteLine("Value of e:" & e.Value)  
```  
  
 <span data-ttu-id="ba6c1-121">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="ba6c1-121">This example produces the following output:</span></span>  
  
```xml  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="example"></a><span data-ttu-id="ba6c1-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="ba6c1-122">Example</span></span>  
 <span data-ttu-id="ba6c1-123">Czasami użytkownik próbuje pobrać wartość elementu, nawet jeśli nie ma pewności, że istnieje.</span><span class="sxs-lookup"><span data-stu-id="ba6c1-123">Sometimes you try to retrieve the value of an element even though you are not sure it exists.</span></span> <span data-ttu-id="ba6c1-124">W takim przypadku po przypisaniu rzutować elementu do typu dopuszczającego wartości null (albo `string` lub jeden z typów wartości null w [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]), jeśli element nie istnieje przypisane tylko ustawiono zmienną `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="ba6c1-124">In this case, when you assign the casted element to a nullable type (either `string` or one of the nullable types in the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]), if the element does not exist the assigned variable is just set to `Nothing`.</span></span> <span data-ttu-id="ba6c1-125">Poniższy kod pokazuje, że element może lub nie istnieje, jest łatwiejsze w rzutowanie niż korzystać <xref:System.Xml.Linq.XElement.Value%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="ba6c1-125">The following code shows that when the element might or might not exist, it is easier to use casting than to use the <xref:System.Xml.Linq.XElement.Value%2A> property.</span></span>  
  
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
  
 <span data-ttu-id="ba6c1-126">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="ba6c1-126">This code produces the following output:</span></span>  
  
```  
c1:child 1 content  
c2:2  
c3:element does not exist  
c4:element does not exist  
  
v1:child 1 content  
v2:2  
v3:element does not exist  
v4:element does not exist  
```  
  
 <span data-ttu-id="ba6c1-127">Ogólnie rzecz biorąc można napisać kod prostszy, używając rzutowanie Aby pobrać zawartość elementów i atrybutów.</span><span class="sxs-lookup"><span data-stu-id="ba6c1-127">In general, you can write simpler code when using casting to retrieve the contents of elements and attributes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba6c1-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ba6c1-128">See Also</span></span>  
 [<span data-ttu-id="ba6c1-129">LINQ do osi XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ba6c1-129">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
