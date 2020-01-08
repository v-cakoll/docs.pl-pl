---
title: Jak pobrać wartość elementu (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 4228c007-07c9-4cf2-a45b-e7074c109581
ms.openlocfilehash: 775e7282408910cc06b7d660d84cb6f80ef47949
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347419"
---
# <a name="how-to-retrieve-the-value-of-an-element-linq-to-xml-c"></a><span data-ttu-id="4de00-102">Jak pobrać wartość elementu (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="4de00-102">How to retrieve the value of an element (LINQ to XML) (C#)</span></span>
<span data-ttu-id="4de00-103">W tym temacie pokazano, jak uzyskać wartość elementów.</span><span class="sxs-lookup"><span data-stu-id="4de00-103">This topic shows how to get the value of elements.</span></span> <span data-ttu-id="4de00-104">Istnieją dwa podstawowe sposoby wykonania tej czynności.</span><span class="sxs-lookup"><span data-stu-id="4de00-104">There are two main ways to do this.</span></span> <span data-ttu-id="4de00-105">Jednym ze sposobów jest rzutowanie <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XAttribute> na żądany typ.</span><span class="sxs-lookup"><span data-stu-id="4de00-105">One way is to cast an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XAttribute> to the desired type.</span></span> <span data-ttu-id="4de00-106">Operator jawnej konwersji konwertuje zawartość elementu lub atrybutu do określonego typu i przypisuje go do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="4de00-106">The explicit conversion operator then converts the contents of the element or attribute to the specified type and assigns it to your variable.</span></span> <span data-ttu-id="4de00-107">Alternatywnie można użyć właściwości <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> lub właściwości <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4de00-107">Alternatively, you can use the <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> property or the <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="4de00-108">C#Jednakże Rzutowanie jest ogólnie lepszym rozwiązaniem.</span><span class="sxs-lookup"><span data-stu-id="4de00-108">With C#, however, casting is generally the better approach.</span></span> <span data-ttu-id="4de00-109">Jeśli przerzutuje element lub atrybut na typ dopuszczający wartość null, kod jest łatwiejszy do zapisu podczas pobierania wartości elementu (lub atrybutu), który może lub nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="4de00-109">If you cast the element or attribute to a nullable type, the code is simpler to write when retrieving the value of an element (or attribute) that might or might not exist.</span></span> <span data-ttu-id="4de00-110">W ostatnim przykładzie w tym temacie pokazano, jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="4de00-110">The last example in this topic demonstrates this.</span></span> <span data-ttu-id="4de00-111">Nie można jednak ustawić zawartości elementu przez rzutowanie, jak można za pomocą właściwości <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4de00-111">However, you cannot set the contents of an element through casting, as you can through <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4de00-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="4de00-112">Example</span></span>  
 <span data-ttu-id="4de00-113">Aby pobrać wartość elementu, należy po prostu rzutować obiekt <xref:System.Xml.Linq.XElement> na żądany typ.</span><span class="sxs-lookup"><span data-stu-id="4de00-113">To retrieve the value of an element, you just cast the <xref:System.Xml.Linq.XElement> object to your desired type.</span></span> <span data-ttu-id="4de00-114">Można zawsze rzutować element na ciąg w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="4de00-114">You can always cast an element to a string, as follows:</span></span>  
  
```csharp  
XElement e = new XElement("StringElement", "abcde");  
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + (string)e);  
```  
  
 <span data-ttu-id="4de00-115">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="4de00-115">This example produces the following output:</span></span>  
  
```output  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="example"></a><span data-ttu-id="4de00-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="4de00-116">Example</span></span>  
 <span data-ttu-id="4de00-117">Można również rzutować elementy do typów innych niż ciąg.</span><span class="sxs-lookup"><span data-stu-id="4de00-117">You can also cast elements to types other than string.</span></span> <span data-ttu-id="4de00-118">Na przykład jeśli masz element zawierający liczbę całkowitą, możesz rzutować go na `int`, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="4de00-118">For example, if you have an element that contains an integer, you can cast it to `int`, as shown in the following code:</span></span>  
  
```csharp  
XElement e = new XElement("Age", "44");  
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + (int)e);  
```  
  
 <span data-ttu-id="4de00-119">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="4de00-119">This example produces the following output:</span></span>  
  
```output  
<Age>44</Age>  
Value of e:44  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="4de00-120">zapewnia jawne Operatory rzutowania dla następujących typów danych: `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`i `GUID?`.</span><span class="sxs-lookup"><span data-stu-id="4de00-120">provides explicit cast operators for the following data types: `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`, and `GUID?`.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="4de00-121">zapewnia te same Operatory rzutowania dla obiektów <xref:System.Xml.Linq.XAttribute>.</span><span class="sxs-lookup"><span data-stu-id="4de00-121">provides the same cast operators for <xref:System.Xml.Linq.XAttribute> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4de00-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="4de00-122">Example</span></span>  
 <span data-ttu-id="4de00-123">Za pomocą właściwości <xref:System.Xml.Linq.XElement.Value%2A> można pobrać zawartość elementu:</span><span class="sxs-lookup"><span data-stu-id="4de00-123">You can use the <xref:System.Xml.Linq.XElement.Value%2A> property to retrieve the contents of an element:</span></span>  
  
```csharp  
XElement e = new XElement("StringElement", "abcde");   
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + e.Value);  
```  
  
 <span data-ttu-id="4de00-124">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="4de00-124">This example produces the following output:</span></span>  
  
```output  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="example"></a><span data-ttu-id="4de00-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="4de00-125">Example</span></span>  
 <span data-ttu-id="4de00-126">Czasami próbujesz pobrać wartość elementu, chociaż nie masz pewności, że istnieje.</span><span class="sxs-lookup"><span data-stu-id="4de00-126">Sometimes you try to retrieve the value of an element even though you are not sure it exists.</span></span> <span data-ttu-id="4de00-127">W tym przypadku, gdy przypiszesz element rzutowany do typu dopuszczającego wartość null (albo `string` lub jeden z typów dopuszczających wartość null w .NET Framework), jeśli element nie istnieje, przypisana zmienna jest po prostu ustawiona na `null`.</span><span class="sxs-lookup"><span data-stu-id="4de00-127">In this case, when you assign the casted element to a nullable type (either `string` or one of the nullable types in the .NET Framework), if the element does not exist the assigned variable is just set to `null`.</span></span> <span data-ttu-id="4de00-128">Poniższy kod pokazuje, że gdy element może lub nie istnieje, łatwiej jest użyć rzutowania, aby użyć właściwości <xref:System.Xml.Linq.XElement.Value%2A>.</span><span class="sxs-lookup"><span data-stu-id="4de00-128">The following code shows that when the element might or might not exist, it is easier to use casting than to use the <xref:System.Xml.Linq.XElement.Value%2A> property.</span></span>  
  
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
  
 <span data-ttu-id="4de00-129">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="4de00-129">This code produces the following output:</span></span>  
  
```output  
c1:child 1 content  
c2:2  
c3:element does not exist  
c4:element does not exist  
  
v1:child 1 content  
v2:2  
v3:element does not exist  
v4:element does not exist  
```  
  
 <span data-ttu-id="4de00-130">Ogólnie rzecz biorąc, można napisać łatwiejszy kod podczas używania rzutowania do pobrania zawartości elementów i atrybutów.</span><span class="sxs-lookup"><span data-stu-id="4de00-130">In general, you can write simpler code when using casting to retrieve the contents of elements and attributes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4de00-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4de00-131">See also</span></span>

- [<span data-ttu-id="4de00-132">Osie LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="4de00-132">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
