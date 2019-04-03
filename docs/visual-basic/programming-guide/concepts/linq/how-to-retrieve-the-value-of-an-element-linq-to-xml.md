---
title: 'Instrukcje: Pobieranie wartości elementu (LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 76b9b2a5-b3ba-49da-ba74-82100e1bd21c
ms.openlocfilehash: 490e98134497836e0751e48949d4dceda41bcbf3
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58814084"
---
# <a name="how-to-retrieve-the-value-of-an-element-linq-to-xml-visual-basic"></a><span data-ttu-id="e2e29-102">Instrukcje: Pobieranie wartości elementu (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e2e29-102">How to: Retrieve the Value of an Element (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="e2e29-103">W tym temacie pokazano, jak można pobrać wartość elementów.</span><span class="sxs-lookup"><span data-stu-id="e2e29-103">This topic shows how to get the value of elements.</span></span> <span data-ttu-id="e2e29-104">Istnieją dwa główne sposoby, aby to zrobić.</span><span class="sxs-lookup"><span data-stu-id="e2e29-104">There are two main ways to do this.</span></span> <span data-ttu-id="e2e29-105">Jednym ze sposobów jest rzutowanie <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XAttribute> do żądanego typu.</span><span class="sxs-lookup"><span data-stu-id="e2e29-105">One way is to cast an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XAttribute> to the desired type.</span></span> <span data-ttu-id="e2e29-106">Operator jawnej konwersji następnie konwertuje zawartość element lub atrybut określonego typu i przypisuje go do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="e2e29-106">The explicit conversion operator then converts the contents of the element or attribute to the specified type and assigns it to your variable.</span></span> <span data-ttu-id="e2e29-107">Alternatywnie, można użyć <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> właściwości lub <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="e2e29-107">Alternatively, you can use the <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> property or the <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="e2e29-108">Za pomocą Visual Basic, najlepszym rozwiązaniem jest użycie <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="e2e29-108">With Visual Basic, the best approach is to use the <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e2e29-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="e2e29-109">Example</span></span>  
 <span data-ttu-id="e2e29-110">Aby pobrać wartość elementu, można po prostu rzutowania <xref:System.Xml.Linq.XElement> obiektu do żądanego typu.</span><span class="sxs-lookup"><span data-stu-id="e2e29-110">To retrieve the value of an element, you just cast the <xref:System.Xml.Linq.XElement> object to your desired type.</span></span> <span data-ttu-id="e2e29-111">Zawsze można rzutować elementu na ciąg w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="e2e29-111">You can always cast an element to a string, as follows:</span></span>  
  
```vb  
Dim e As XElement = <StringElement>abcde</StringElement>  
Console.WriteLine(e)  
Console.WriteLine("Value of e:" & e.Value)  
```  
  
 <span data-ttu-id="e2e29-112">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="e2e29-112">This example produces the following output:</span></span>  
  
```xml  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="example"></a><span data-ttu-id="e2e29-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="e2e29-113">Example</span></span>  
 <span data-ttu-id="e2e29-114">Można również rzutowania elementów do typów innych niż ciąg.</span><span class="sxs-lookup"><span data-stu-id="e2e29-114">You can also cast elements to types other than string.</span></span> <span data-ttu-id="e2e29-115">Na przykład, jeśli element, który zawiera liczbę całkowitą, można go rzutować do `int`, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="e2e29-115">For example, if you have an element that contains an integer, you can cast it to `int`, as shown in the following code:</span></span>  
  
```vb  
Dim e As XElement = <Age>44</Age>  
Console.WriteLine(e)  
Console.WriteLine("Value of e:" & CInt(e))  
```  
  
 <span data-ttu-id="e2e29-116">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="e2e29-116">This example produces the following output:</span></span>  
  
```xml  
<Age>44</Age>  
Value of e:44  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="e2e29-117">zawiera operatory jawnego rzutowania dla następujących typów danych: `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?` , `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`, i `GUID?`.</span><span class="sxs-lookup"><span data-stu-id="e2e29-117">provides explicit cast operators for the following data types: `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`, and `GUID?`.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="e2e29-118">zawiera ten sam operatorów rzutowania na potrzeby <xref:System.Xml.Linq.XAttribute> obiektów.</span><span class="sxs-lookup"><span data-stu-id="e2e29-118">provides the same cast operators for <xref:System.Xml.Linq.XAttribute> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e2e29-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="e2e29-119">Example</span></span>  
 <span data-ttu-id="e2e29-120">Możesz użyć <xref:System.Xml.Linq.XElement.Value%2A> właściwości, aby pobrać zawartość elementu:</span><span class="sxs-lookup"><span data-stu-id="e2e29-120">You can use the <xref:System.Xml.Linq.XElement.Value%2A> property to retrieve the contents of an element:</span></span>  
  
```vb  
Dim e As XElement = <StringElement>abcde</StringElement>  
Console.WriteLine(e)  
Console.WriteLine("Value of e:" & e.Value)  
```  
  
 <span data-ttu-id="e2e29-121">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="e2e29-121">This example produces the following output:</span></span>  
  
```xml  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="example"></a><span data-ttu-id="e2e29-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="e2e29-122">Example</span></span>  
 <span data-ttu-id="e2e29-123">Czasami użytkownik próbuje pobrać wartość elementu, nawet jeśli nie ma pewności, że istnieje.</span><span class="sxs-lookup"><span data-stu-id="e2e29-123">Sometimes you try to retrieve the value of an element even though you are not sure it exists.</span></span> <span data-ttu-id="e2e29-124">W tym przypadku przypisana element rzutować na typ dopuszczający wartość null (albo `string` lub jednego z typy dopuszczające wartości null w [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]), jeśli element nie ma przypisanych właśnie ustawiono zmienną `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="e2e29-124">In this case, when you assign the casted element to a nullable type (either `string` or one of the nullable types in the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]), if the element does not exist the assigned variable is just set to `Nothing`.</span></span> <span data-ttu-id="e2e29-125">Poniższy kod pokazuje, że gdy elementu może lub nie istnieje, jest łatwiejszy w obsłudze rzutowania niż korzystać <xref:System.Xml.Linq.XElement.Value%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="e2e29-125">The following code shows that when the element might or might not exist, it is easier to use casting than to use the <xref:System.Xml.Linq.XElement.Value%2A> property.</span></span>  
  
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
  
 <span data-ttu-id="e2e29-126">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="e2e29-126">This code produces the following output:</span></span>  
  
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
  
 <span data-ttu-id="e2e29-127">Ogólnie rzecz biorąc można napisać kod prostsze, gdy za pomocą rzutowania, aby pobrać zawartość elementów i atrybutów.</span><span class="sxs-lookup"><span data-stu-id="e2e29-127">In general, you can write simpler code when using casting to retrieve the contents of elements and attributes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2e29-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e2e29-128">See also</span></span>

- [<span data-ttu-id="e2e29-129">LINQ do osi XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e2e29-129">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
