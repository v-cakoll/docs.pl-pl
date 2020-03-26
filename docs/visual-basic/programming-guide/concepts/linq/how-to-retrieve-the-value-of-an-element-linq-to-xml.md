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
# <a name="how-to-retrieve-the-value-of-an-element-linq-to-xml-visual-basic"></a><span data-ttu-id="83f96-102">Jak: Pobieranie wartości elementu (LINQ do XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="83f96-102">How to: Retrieve the Value of an Element (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="83f96-103">W tym temacie pokazano, jak uzyskać wartość elementów.</span><span class="sxs-lookup"><span data-stu-id="83f96-103">This topic shows how to get the value of elements.</span></span> <span data-ttu-id="83f96-104">Istnieją dwa główne sposoby, aby to zrobić.</span><span class="sxs-lookup"><span data-stu-id="83f96-104">There are two main ways to do this.</span></span> <span data-ttu-id="83f96-105">Jednym ze sposobów <xref:System.Xml.Linq.XElement> jest <xref:System.Xml.Linq.XAttribute> rzucenie lub do żądanego typu.</span><span class="sxs-lookup"><span data-stu-id="83f96-105">One way is to cast an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XAttribute> to the desired type.</span></span> <span data-ttu-id="83f96-106">Operator konwersji jawne następnie konwertuje zawartość elementu lub atrybutu do określonego typu i przypisuje go do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="83f96-106">The explicit conversion operator then converts the contents of the element or attribute to the specified type and assigns it to your variable.</span></span> <span data-ttu-id="83f96-107">Goście mogą również skorzystać <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> z <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType> obiektu lub obiektu.</span><span class="sxs-lookup"><span data-stu-id="83f96-107">Alternatively, you can use the <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> property or the <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="83f96-108">W języku Visual Basic najlepszym rozwiązaniem <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> jest użycie właściwości.</span><span class="sxs-lookup"><span data-stu-id="83f96-108">With Visual Basic, the best approach is to use the <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="83f96-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="83f96-109">Example</span></span>  
 <span data-ttu-id="83f96-110">Aby pobrać wartość elementu, wystarczy rzutować <xref:System.Xml.Linq.XElement> obiekt do żądanego typu.</span><span class="sxs-lookup"><span data-stu-id="83f96-110">To retrieve the value of an element, you just cast the <xref:System.Xml.Linq.XElement> object to your desired type.</span></span> <span data-ttu-id="83f96-111">Zawsze można rzutować element do ciągu, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="83f96-111">You can always cast an element to a string, as follows:</span></span>  
  
```vb  
Dim e As XElement = <StringElement>abcde</StringElement>  
Console.WriteLine(e)  
Console.WriteLine("Value of e:" & e.Value)  
```  
  
 <span data-ttu-id="83f96-112">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="83f96-112">This example produces the following output:</span></span>  
  
```xml  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="example"></a><span data-ttu-id="83f96-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="83f96-113">Example</span></span>  
 <span data-ttu-id="83f96-114">Można również rzutować elementy do typów innych niż ciąg.</span><span class="sxs-lookup"><span data-stu-id="83f96-114">You can also cast elements to types other than string.</span></span> <span data-ttu-id="83f96-115">Na przykład jeśli masz element, który zawiera całkowitą, można `int`go przerzucić na , jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="83f96-115">For example, if you have an element that contains an integer, you can cast it to `int`, as shown in the following code:</span></span>  
  
```vb  
Dim e As XElement = <Age>44</Age>  
Console.WriteLine(e)  
Console.WriteLine("Value of e:" & CInt(e))  
```  
  
 <span data-ttu-id="83f96-116">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="83f96-116">This example produces the following output:</span></span>  
  
```xml  
<Age>44</Age>  
Value of e:44  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="83f96-117">zapewnia operatory jawnego rzutu `string` `bool`dla `bool?` `int`następujących `int?` `uint`typów `uint?` `long`danych: , , , , , , `GUID`, `GUID?` `decimal` `decimal?` `DateTime` `DateTime?` `TimeSpan` `TimeSpan?` `long?` `ulong` `ulong?` `float`, , , `float?`, , `double`, `double?`, , , , , , , , , , i .</span><span class="sxs-lookup"><span data-stu-id="83f96-117">provides explicit cast operators for the following data types: `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`, and `GUID?`.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="83f96-118">zapewnia te same <xref:System.Xml.Linq.XAttribute> operatory rzutowania dla obiektów.</span><span class="sxs-lookup"><span data-stu-id="83f96-118">provides the same cast operators for <xref:System.Xml.Linq.XAttribute> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="83f96-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="83f96-119">Example</span></span>  
 <span data-ttu-id="83f96-120">Można użyć <xref:System.Xml.Linq.XElement.Value%2A> właściwości, aby pobrać zawartość elementu:</span><span class="sxs-lookup"><span data-stu-id="83f96-120">You can use the <xref:System.Xml.Linq.XElement.Value%2A> property to retrieve the contents of an element:</span></span>  
  
```vb  
Dim e As XElement = <StringElement>abcde</StringElement>  
Console.WriteLine(e)  
Console.WriteLine("Value of e:" & e.Value)  
```  
  
 <span data-ttu-id="83f96-121">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="83f96-121">This example produces the following output:</span></span>  
  
```xml  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="example"></a><span data-ttu-id="83f96-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="83f96-122">Example</span></span>  
 <span data-ttu-id="83f96-123">Czasami spróbuj pobrać wartość elementu, nawet jeśli nie masz pewności, że istnieje.</span><span class="sxs-lookup"><span data-stu-id="83f96-123">Sometimes you try to retrieve the value of an element even though you are not sure it exists.</span></span> <span data-ttu-id="83f96-124">W takim przypadku po przypisaniu elementu rzutowanego do typu `string` możliwego do wartości null (jednego lub jednego z typów wartości nullable w `Nothing`.NET Framework), jeśli element nie istnieje, przypisana zmienna jest po prostu ustawiona na .</span><span class="sxs-lookup"><span data-stu-id="83f96-124">In this case, when you assign the casted element to a nullable type (either `string` or one of the nullable value types in the .NET Framework), if the element does not exist the assigned variable is just set to `Nothing`.</span></span> <span data-ttu-id="83f96-125">Poniższy kod pokazuje, że gdy element może lub nie może istnieć, <xref:System.Xml.Linq.XElement.Value%2A> jest łatwiejsze w użyciu rzutowania niż do korzystania z właściwości.</span><span class="sxs-lookup"><span data-stu-id="83f96-125">The following code shows that when the element might or might not exist, it is easier to use casting than to use the <xref:System.Xml.Linq.XElement.Value%2A> property.</span></span>  
  
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
  
 <span data-ttu-id="83f96-126">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="83f96-126">This code produces the following output:</span></span>  
  
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
  
 <span data-ttu-id="83f96-127">Ogólnie rzecz biorąc można napisać prostszy kod podczas korzystania z rzutowania do pobierania zawartości elementów i atrybutów.</span><span class="sxs-lookup"><span data-stu-id="83f96-127">In general, you can write simpler code when using casting to retrieve the contents of elements and attributes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83f96-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="83f96-128">See also</span></span>

- [<span data-ttu-id="83f96-129">Osie LINQ do XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="83f96-129">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
