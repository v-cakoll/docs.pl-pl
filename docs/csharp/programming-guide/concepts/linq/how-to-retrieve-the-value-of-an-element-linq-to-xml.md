---
title: Jak pobrać wartość elementu (LINQ do XML) (C#)
ms.date: 07/20/2015
ms.assetid: 4228c007-07c9-4cf2-a45b-e7074c109581
ms.openlocfilehash: c4bb78e937fe0de08242923cdd7cd638abf571c7
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805832"
---
# <a name="how-to-retrieve-the-value-of-an-element-linq-to-xml-c"></a><span data-ttu-id="7192f-102">Jak pobrać wartość elementu (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="7192f-102">How to retrieve the value of an element (LINQ to XML) (C#)</span></span>

<span data-ttu-id="7192f-103">W tym artykule pokazano, jak uzyskać wartość elementów.</span><span class="sxs-lookup"><span data-stu-id="7192f-103">This article shows how to get the value of elements.</span></span> <span data-ttu-id="7192f-104">Istnieją dwa główne sposoby uzyskania wartości:</span><span class="sxs-lookup"><span data-stu-id="7192f-104">There are two main ways to get the value:</span></span>

- <span data-ttu-id="7192f-105">Rzut <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XAttribute> do żądanego typu.</span><span class="sxs-lookup"><span data-stu-id="7192f-105">Cast an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XAttribute> to the desired type.</span></span> <span data-ttu-id="7192f-106">Operator konwersji jawne następnie konwertuje zawartość elementu lub atrybutu do określonego typu i przypisuje go do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="7192f-106">The explicit conversion operator then converts the contents of the element or attribute to the specified type and assigns it to your variable.</span></span>

- <span data-ttu-id="7192f-107">Użyj <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> właściwości <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType> lub.</span><span class="sxs-lookup"><span data-stu-id="7192f-107">Use the <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> or <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType> properties.</span></span> <span data-ttu-id="7192f-108">Można również ustawić wartość przy użyciu tych właściwości.</span><span class="sxs-lookup"><span data-stu-id="7192f-108">You can also set the value using these properties.</span></span>

<span data-ttu-id="7192f-109">Z C#, odlewania jest na ogół lepsze podejście.</span><span class="sxs-lookup"><span data-stu-id="7192f-109">With C#, casting is generally the better approach.</span></span> <span data-ttu-id="7192f-110">Jeśli rzutujesz element lub atrybut na typ wartości możliwej do wartości null, kod jest prostszy do zapisania podczas pobierania wartości elementu (lub atrybutu), który może lub nie może istnieć.</span><span class="sxs-lookup"><span data-stu-id="7192f-110">If you cast the element or attribute to a nullable value type, the code is simpler to write when retrieving the value of an element (or attribute) that might or might not exist.</span></span> <span data-ttu-id="7192f-111">Ostatni [przykład](#element-might-not-exist-example) w tym artykule pokazuje, że rzutowanie jest prostsze w przypadku, gdy element może nie istnieć.</span><span class="sxs-lookup"><span data-stu-id="7192f-111">The [last example](#element-might-not-exist-example) in this article demonstrates that casting is simpler in the case where the element might not exist.</span></span> <span data-ttu-id="7192f-112">Jednak nie można ustawić zawartość elementu za pomocą rzutowania, jak można za pośrednictwem <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="7192f-112">However, you cannot set the contents of an element through casting, as you can through <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="string-cast-example"></a><span data-ttu-id="7192f-113">Przykład rzutowania ciągiem</span><span class="sxs-lookup"><span data-stu-id="7192f-113">String cast example</span></span>  
 <span data-ttu-id="7192f-114">Aby pobrać wartość elementu, przerzuć obiekt na <xref:System.Xml.Linq.XElement> żądany typ.</span><span class="sxs-lookup"><span data-stu-id="7192f-114">To retrieve the value of an element, cast the <xref:System.Xml.Linq.XElement> object to your desired type.</span></span> <span data-ttu-id="7192f-115">Element można rzutować na ciąg w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="7192f-115">You can cast an element to a string, as follows:</span></span>  
  
```csharp  
XElement e = new XElement("StringElement", "abcde");  
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + (string)e);  
```  
  
 <span data-ttu-id="7192f-116">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="7192f-116">This example produces the following output:</span></span>  
  
```output  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="integer-cast-example"></a><span data-ttu-id="7192f-117">Przykład rzutowania całkowitej</span><span class="sxs-lookup"><span data-stu-id="7192f-117">Integer cast example</span></span>  
 <span data-ttu-id="7192f-118">Można również rzutować elementy do typów innych niż ciąg.</span><span class="sxs-lookup"><span data-stu-id="7192f-118">You can also cast elements to types other than string.</span></span> <span data-ttu-id="7192f-119">Na przykład jeśli masz element, który zawiera całkowitą, można `int`go przerzucić na , jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="7192f-119">For example, if you have an element that contains an integer, you can cast it to `int`, as shown in the following code:</span></span>  
  
```csharp  
XElement e = new XElement("Age", "44");  
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + (int)e);  
```  
  
 <span data-ttu-id="7192f-120">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="7192f-120">This example produces the following output:</span></span>  
  
```output  
<Age>44</Age>  
Value of e:44  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="7192f-121">zapewnia operatory jawnego rzutu `string` `bool`dla `bool?` `int`następujących `int?` `uint`typów `uint?` `long`danych: , , , , , , `GUID`, `GUID?` `decimal` `decimal?` `DateTime` `DateTime?` `TimeSpan` `TimeSpan?` `long?` `ulong` `ulong?` `float`, , , `float?`, , `double`, `double?`, , , , , , , , , , i .</span><span class="sxs-lookup"><span data-stu-id="7192f-121">provides explicit cast operators for the following data types: `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`, and `GUID?`.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="7192f-122">zapewnia te same <xref:System.Xml.Linq.XAttribute> operatory rzutowania dla obiektów.</span><span class="sxs-lookup"><span data-stu-id="7192f-122">provides the same cast operators for <xref:System.Xml.Linq.XAttribute> objects.</span></span>  
  
## <a name="value-property-example"></a><span data-ttu-id="7192f-123">Przykład właściwości wartość</span><span class="sxs-lookup"><span data-stu-id="7192f-123">Value property example</span></span>  
 <span data-ttu-id="7192f-124">Można użyć <xref:System.Xml.Linq.XElement.Value%2A> właściwości, aby pobrać zawartość elementu:</span><span class="sxs-lookup"><span data-stu-id="7192f-124">You can use the <xref:System.Xml.Linq.XElement.Value%2A> property to retrieve the contents of an element:</span></span>  
  
```csharp  
XElement e = new XElement("StringElement", "abcde");
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + e.Value);  
```  
  
 <span data-ttu-id="7192f-125">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="7192f-125">This example produces the following output:</span></span>  
  
```output  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="element-might-not-exist-example"></a><span data-ttu-id="7192f-126">Element może nie istnieć przykład</span><span class="sxs-lookup"><span data-stu-id="7192f-126">Element might not exist example</span></span>
 <span data-ttu-id="7192f-127">Czasami spróbuj odzyskać wartość elementu, nawet jeśli nie masz pewności, czy istnieje.</span><span class="sxs-lookup"><span data-stu-id="7192f-127">Sometimes you try to retrieve the value of an element even though you're not sure if it exists.</span></span> <span data-ttu-id="7192f-128">W takim przypadku po przypisaniu elementu rzutowanego do typu odwołania możliwego do wartości null lub typu wartości `null`nullable, jeśli element nie istnieje, przypisana zmienna jest ustawiona na .</span><span class="sxs-lookup"><span data-stu-id="7192f-128">In this case, when you assign the casted element to a nullable reference type or nullable value type, if the element does not exist, the assigned variable is set to `null`.</span></span> <span data-ttu-id="7192f-129">Poniższy kod pokazuje, że gdy element może lub nie może istnieć, <xref:System.Xml.Linq.XElement.Value%2A> jest łatwiejsze w użyciu rzutowania niż do korzystania z właściwości.</span><span class="sxs-lookup"><span data-stu-id="7192f-129">The following code shows that when the element might or might not exist, it is easier to use casting than to use the <xref:System.Xml.Linq.XElement.Value%2A> property.</span></span>  
  
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
  
 <span data-ttu-id="7192f-130">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="7192f-130">This code produces the following output:</span></span>  
  
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
  
 <span data-ttu-id="7192f-131">Ogólnie rzecz biorąc można napisać prostszy kod podczas korzystania z rzutowania do pobierania zawartości elementów i atrybutów.</span><span class="sxs-lookup"><span data-stu-id="7192f-131">In general, you can write simpler code when using casting to retrieve the contents of elements and attributes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7192f-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7192f-132">See also</span></span>

- [<span data-ttu-id="7192f-133">Osie LINQ do XML (C#)</span><span class="sxs-lookup"><span data-stu-id="7192f-133">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
