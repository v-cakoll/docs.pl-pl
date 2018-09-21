---
title: 'Porady: pobieranie wartości elementu (LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 4228c007-07c9-4cf2-a45b-e7074c109581
ms.openlocfilehash: 7537c111e7d869f8a3e2458706864960820f9764
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/21/2018
ms.locfileid: "46529330"
---
# <a name="how-to-retrieve-the-value-of-an-element-linq-to-xml-c"></a><span data-ttu-id="f3979-102">Porady: pobieranie wartości elementu (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="f3979-102">How to: Retrieve the Value of an Element (LINQ to XML) (C#)</span></span>
<span data-ttu-id="f3979-103">W tym temacie pokazano, jak można pobrać wartość elementów.</span><span class="sxs-lookup"><span data-stu-id="f3979-103">This topic shows how to get the value of elements.</span></span> <span data-ttu-id="f3979-104">Istnieją dwa główne sposoby, aby to zrobić.</span><span class="sxs-lookup"><span data-stu-id="f3979-104">There are two main ways to do this.</span></span> <span data-ttu-id="f3979-105">Jednym ze sposobów jest rzutowanie <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XAttribute> do żądanego typu.</span><span class="sxs-lookup"><span data-stu-id="f3979-105">One way is to cast an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XAttribute> to the desired type.</span></span> <span data-ttu-id="f3979-106">Operator jawnej konwersji następnie konwertuje zawartość element lub atrybut określonego typu i przypisuje go do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="f3979-106">The explicit conversion operator then converts the contents of the element or attribute to the specified type and assigns it to your variable.</span></span> <span data-ttu-id="f3979-107">Alternatywnie, można użyć <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> właściwości lub <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="f3979-107">Alternatively, you can use the <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> property or the <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="f3979-108">Za pomocą języka C# jednak rzutowania ogólnie jest lepszym rozwiązaniem.</span><span class="sxs-lookup"><span data-stu-id="f3979-108">With C#, however, casting is generally the better approach.</span></span> <span data-ttu-id="f3979-109">Jeśli rzutowanie elementu lub atrybutu typu dopuszczającego wartość null, kod jest prostszy do zapisania podczas pobierania wartości elementu (lub atrybut), który może być lub może nie istnieć.</span><span class="sxs-lookup"><span data-stu-id="f3979-109">If you cast the element or attribute to a nullable type, the code is simpler to write when retrieving the value of an element (or attribute) that might or might not exist.</span></span> <span data-ttu-id="f3979-110">Przykład ostatniego, w tym temacie przedstawia to.</span><span class="sxs-lookup"><span data-stu-id="f3979-110">The last example in this topic demonstrates this.</span></span> <span data-ttu-id="f3979-111">Jednak nie można ustawić zawartość elementu za pośrednictwem rzutowania, jak to możliwe za pośrednictwem <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="f3979-111">However, you cannot set the contents of an element through casting, as you can through <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3979-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="f3979-112">Example</span></span>  
 <span data-ttu-id="f3979-113">Aby pobrać wartość elementu, można po prostu rzutowania <xref:System.Xml.Linq.XElement> obiektu do żądanego typu.</span><span class="sxs-lookup"><span data-stu-id="f3979-113">To retrieve the value of an element, you just cast the <xref:System.Xml.Linq.XElement> object to your desired type.</span></span> <span data-ttu-id="f3979-114">Zawsze można rzutować elementu na ciąg w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="f3979-114">You can always cast an element to a string, as follows:</span></span>  
  
```csharp  
XElement e = new XElement("StringElement", "abcde");  
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + (string)e);  
```  
  
 <span data-ttu-id="f3979-115">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="f3979-115">This example produces the following output:</span></span>  
  
```  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="example"></a><span data-ttu-id="f3979-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="f3979-116">Example</span></span>  
 <span data-ttu-id="f3979-117">Można również rzutowania elementów do typów innych niż ciąg.</span><span class="sxs-lookup"><span data-stu-id="f3979-117">You can also cast elements to types other than string.</span></span> <span data-ttu-id="f3979-118">Na przykład, jeśli element, który zawiera liczbę całkowitą, można go rzutować do `int`, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="f3979-118">For example, if you have an element that contains an integer, you can cast it to `int`, as shown in the following code:</span></span>  
  
```csharp  
XElement e = new XElement("Age", "44");  
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + (int)e);  
```  
  
 <span data-ttu-id="f3979-119">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="f3979-119">This example produces the following output:</span></span>  
  
```  
<Age>44</Age>  
Value of e:44  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="f3979-120"> zawiera operatory jawnego rzutowania dla następujących typów danych: `string\`, `bool\`, `bool?\`, `int\`, `int?\`, `uint\`, `uint?\`, `long\`, `long?\`, `ulong\`, `ulong?` , `float\`, `float?\`, `double\`, `double?\`, `decimal\`, `decimal?\`, `DateTime\`, `DateTime?\`, `TimeSpan\`, `TimeSpan?\`, `GUID\`, i `GUID?\`.</span><span class="sxs-lookup"><span data-stu-id="f3979-120"> provides explicit cast operators for the following data types: `string\`, `bool\`, `bool?\`, `int\`, `int?\`, `uint\`, `uint?\`, `long\`, `long?\`, `ulong\`, `ulong?\`, `float\`, `float?\`, `double\`, `double?\`, `decimal\`, `decimal?\`, `DateTime\`, `DateTime?\`, `TimeSpan\`, `TimeSpan?\`, `GUID\`, and `GUID?\`.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="f3979-121"> zawiera ten sam operatorów rzutowania na potrzeby <xref:System.Xml.Linq.XAttribute> obiektów.</span><span class="sxs-lookup"><span data-stu-id="f3979-121"> provides the same cast operators for <xref:System.Xml.Linq.XAttribute> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3979-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="f3979-122">Example</span></span>  
 <span data-ttu-id="f3979-123">Możesz użyć <xref:System.Xml.Linq.XElement.Value%2A> właściwości, aby pobrać zawartość elementu:</span><span class="sxs-lookup"><span data-stu-id="f3979-123">You can use the <xref:System.Xml.Linq.XElement.Value%2A> property to retrieve the contents of an element:</span></span>  
  
```csharp  
XElement e = new XElement("StringElement", "abcde");   
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + e.Value);  
```  
  
 <span data-ttu-id="f3979-124">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="f3979-124">This example produces the following output:</span></span>  
  
```  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="example"></a><span data-ttu-id="f3979-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="f3979-125">Example</span></span>  
 <span data-ttu-id="f3979-126">Czasami użytkownik próbuje pobrać wartość elementu, nawet jeśli nie ma pewności, że istnieje.</span><span class="sxs-lookup"><span data-stu-id="f3979-126">Sometimes you try to retrieve the value of an element even though you are not sure it exists.</span></span> <span data-ttu-id="f3979-127">W tym przypadku przypisana element rzutować na typ dopuszczający wartość null (albo `string` lub jednego z typy dopuszczające wartości null w [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]), jeśli element nie ma przypisanych właśnie ustawiono zmienną `null`.</span><span class="sxs-lookup"><span data-stu-id="f3979-127">In this case, when you assign the casted element to a nullable type (either `string` or one of the nullable types in the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]), if the element does not exist the assigned variable is just set to `null`.</span></span> <span data-ttu-id="f3979-128">Poniższy kod pokazuje, że gdy elementu może lub nie istnieje, jest łatwiejszy w obsłudze rzutowania niż korzystać <xref:System.Xml.Linq.XElement.Value%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="f3979-128">The following code shows that when the element might or might not exist, it is easier to use casting than to use the <xref:System.Xml.Linq.XElement.Value%2A> property.</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Child1", "child 1 content"),  
    new XElement("Child2", "2")  
);  
  
// The following assignments show why it is easier to use  
// casting when the element might or might not exist.  
  
string c1 = (string)root.Element("Child1");  
Console.WriteLine("c1:{0}", c1 == null ? "element does not exist" : c1);  
  
int? c2 = (int?)root.Element("Child2");  
Console.WriteLine("c2:{0}", c2 == null ? "element does not exist" : c2.ToString());  
  
string c3 = (string)root.Element("Child3");  
Console.WriteLine("c3:{0}", c3 == null ? "element does not exist" : c3);  
  
int? c4 = (int?)root.Element("Child4");  
Console.WriteLine("c4:{0}", c4 == null ? "element does not exist" : c4.ToString());  
  
Console.WriteLine();  
  
// The following assignments show the required code when using  
// the Value property when the element might or might not exist.  
// Notice that this is more difficult than the casting approach.  
  
XElement e1 = root.Element("Child1");  
string v1;  
if (e1 == null)  
    v1 = null;  
else  
    v1 = e1.Value;  
Console.WriteLine("v1:{0}", v1 == null ? "element does not exist" : v1);  
  
XElement e2 = root.Element("Child2");  
int? v2;  
if (e2 == null)  
    v2 = null;  
else  
    v2 = Int32.Parse(e2.Value);  
Console.WriteLine("v2:{0}", v2 == null ? "element does not exist" : v2.ToString());  
  
XElement e3 = root.Element("Child3");  
string v3;  
if (e3 == null)  
    v3 = null;  
else  
    v3 = e3.Value;  
Console.WriteLine("v3:{0}", v3 == null ? "element does not exist" : v3);  
  
XElement e4 = root.Element("Child4");  
int? v4;  
if (e4 == null)  
    v4 = null;  
else  
    v4 = Int32.Parse(e4.Value);  
Console.WriteLine("v4:{0}", v4 == null ? "element does not exist" : v4.ToString());  
```  
  
 <span data-ttu-id="f3979-129">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="f3979-129">This code produces the following output:</span></span>  
  
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
  
 <span data-ttu-id="f3979-130">Ogólnie rzecz biorąc można napisać kod prostsze, gdy za pomocą rzutowania, aby pobrać zawartość elementów i atrybutów.</span><span class="sxs-lookup"><span data-stu-id="f3979-130">In general, you can write simpler code when using casting to retrieve the contents of elements and attributes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3979-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f3979-131">See Also</span></span>

- [<span data-ttu-id="f3979-132">LINQ do XML osi (C#)</span><span class="sxs-lookup"><span data-stu-id="f3979-132">LINQ to XML Axes (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
