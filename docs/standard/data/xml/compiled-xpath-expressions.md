---
title: Skompilowane wyrażenia XPath
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: e25dd95f-b64c-4d8b-a3a4-379e1aa0ad55
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d7bb158331c1e03b18601dc553ed8ac0e8fa7930
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "44041398"
---
# <a name="compiled-xpath-expressions"></a><span data-ttu-id="6bcf5-102">Skompilowane wyrażenia XPath</span><span class="sxs-lookup"><span data-stu-id="6bcf5-102">Compiled XPath Expressions</span></span>
<span data-ttu-id="6bcf5-103"><xref:System.Xml.XPath.XPathExpression> Obiekt reprezentuje kompilowanym zapytaniu XPath zwróciło albo statycznych <xref:System.Xml.XPath.XPathExpression.Compile%2A> metody <xref:System.Xml.XPath.XPathExpression> klasy lub <xref:System.Xml.XPath.XPathNavigator.Compile%2A> metody <xref:System.Xml.XPath.XPathNavigator> klasy.</span><span class="sxs-lookup"><span data-stu-id="6bcf5-103">An <xref:System.Xml.XPath.XPathExpression> object represents a compiled XPath query returned from either the static <xref:System.Xml.XPath.XPathExpression.Compile%2A> method of the <xref:System.Xml.XPath.XPathExpression> class or the <xref:System.Xml.XPath.XPathNavigator.Compile%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
## <a name="the-xpathexpression-class"></a><span data-ttu-id="6bcf5-104">Klasa XPathExpression</span><span class="sxs-lookup"><span data-stu-id="6bcf5-104">The XPathExpression Class</span></span>  
 <span data-ttu-id="6bcf5-105">A skompilowany zapytanie XPath, reprezentowane przez <xref:System.Xml.XPath.XPathExpression> obiekt jest przydatne, jeśli to samo zapytanie XPath jest używana w więcej niż jeden raz.</span><span class="sxs-lookup"><span data-stu-id="6bcf5-105">A compiled XPath query represented by an <xref:System.Xml.XPath.XPathExpression> object is useful if the same XPath query is being used more than once.</span></span>  
  
 <span data-ttu-id="6bcf5-106">Na przykład podczas wywoływania <xref:System.Xml.XPath.XPathNavigator.Select%2A> metoda wielokrotnie, zamiast korzystać z ciągu reprezentującego Kwerenda XPath każdorazowo, użyj <xref:System.Xml.XPath.XPathExpression.Compile%2A> metody <xref:System.Xml.XPath.XPathExpression> klasy lub <xref:System.Xml.XPath.XPathNavigator.Compile%2A> metody <xref:System.Xml.XPath.XPathNavigator> klasy do kompilowania i Zapytanie XPath w pamięci podręcznej <xref:System.Xml.XPath.XPathExpression> obiekt do ponownego użycia i wydajności.</span><span class="sxs-lookup"><span data-stu-id="6bcf5-106">For example, when calling the <xref:System.Xml.XPath.XPathNavigator.Select%2A> method multiple times, instead of using a string representing the XPath query each time, use the <xref:System.Xml.XPath.XPathExpression.Compile%2A> method of the <xref:System.Xml.XPath.XPathExpression> class or the <xref:System.Xml.XPath.XPathNavigator.Compile%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class to compile and cache the XPath query in an <xref:System.Xml.XPath.XPathExpression> object for reuse and improved performance.</span></span>  
  
 <span data-ttu-id="6bcf5-107">Po skompilowaniu <xref:System.Xml.XPath.XPathExpression> obiekt może być używany jako dane wejściowe dla następujących <xref:System.Xml.XPath.XPathNavigator> metody klasy, w zależności od typu zwróconych przez kwerendę XPath.</span><span class="sxs-lookup"><span data-stu-id="6bcf5-107">Once compiled, the <xref:System.Xml.XPath.XPathExpression> object may be used as input to the following <xref:System.Xml.XPath.XPathNavigator> class methods depending on the type returned from the XPath query.</span></span>  
  
-   <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.XPath.XPathNavigator.Matches%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
 <span data-ttu-id="6bcf5-108">W poniższej tabeli opisano każdy z typów zwracanych W3C XPath, ich equivalencies programu Microsoft .NET Framework i co metody <xref:System.Xml.XPath.XPathExpression> obiektu może być używany z na podstawie jego typu zwracanego.</span><span class="sxs-lookup"><span data-stu-id="6bcf5-108">The following table describes each of the W3C XPath return types, their Microsoft .NET Framework equivalencies, and what methods the <xref:System.Xml.XPath.XPathExpression> object may be used with based on its return type.</span></span>  
  
|<span data-ttu-id="6bcf5-109">Typ zwracany XPath W3C</span><span class="sxs-lookup"><span data-stu-id="6bcf5-109">W3C XPath Return Type</span></span>|<span data-ttu-id="6bcf5-110">Typ równoważne programu .NET framework</span><span class="sxs-lookup"><span data-stu-id="6bcf5-110">.NET Framework Equivalent Type</span></span>|<span data-ttu-id="6bcf5-111">Opis</span><span class="sxs-lookup"><span data-stu-id="6bcf5-111">Description</span></span>|<span data-ttu-id="6bcf5-112">Metody</span><span class="sxs-lookup"><span data-stu-id="6bcf5-112">Methods</span></span>|  
|---------------------------|------------------------------------|-----------------|-------------|  
|`Node set`|<xref:System.Xml.XPath.XPathNodeIterator>|<span data-ttu-id="6bcf5-113">Nieuporządkowanej kolekcji węzłów bez duplikatów tworzone w kolejności dokumentu.</span><span class="sxs-lookup"><span data-stu-id="6bcf5-113">An unordered collection of nodes without duplicates created in document order.</span></span>|<span data-ttu-id="6bcf5-114"><xref:System.Xml.XPath.XPathNavigator.Select%2A> lub <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A></span><span class="sxs-lookup"><span data-stu-id="6bcf5-114"><xref:System.Xml.XPath.XPathNavigator.Select%2A> or <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A></span></span>|  
|`Boolean`|<xref:System.Boolean>|<span data-ttu-id="6bcf5-115">A `true` lub `false` wartość.</span><span class="sxs-lookup"><span data-stu-id="6bcf5-115">A `true` or `false` value.</span></span>|<span data-ttu-id="6bcf5-116"><xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> lub</span><span class="sxs-lookup"><span data-stu-id="6bcf5-116"><xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> or</span></span><br /><br /> <xref:System.Xml.XPath.XPathNavigator.Matches%2A>|  
|`Number`|<xref:System.Double>|<span data-ttu-id="6bcf5-117">Liczba zmiennoprzecinkowa.</span><span class="sxs-lookup"><span data-stu-id="6bcf5-117">A floating-point number.</span></span>|<xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>|  
|`String`|<xref:System.String>|<span data-ttu-id="6bcf5-118">Sekwencja znaków UCS.</span><span class="sxs-lookup"><span data-stu-id="6bcf5-118">A sequence of UCS characters.</span></span>|<xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>|  
  
> [!NOTE]
>  <span data-ttu-id="6bcf5-119"><xref:System.Xml.XPath.XPathNavigator.Matches%2A> Metoda przyjmuje jako parametr wyrażenia XPath.</span><span class="sxs-lookup"><span data-stu-id="6bcf5-119">The <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method accepts an XPath expression as its parameter.</span></span> <span data-ttu-id="6bcf5-120"><xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> Metoda zwraca <xref:System.Xml.XPath.XPathNavigator> obiektu, nie jeden z typów zwracanych W3C XPath.</span><span class="sxs-lookup"><span data-stu-id="6bcf5-120">The <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> method returns an <xref:System.Xml.XPath.XPathNavigator> object, not one of the W3C XPath return types.</span></span>  
  
### <a name="the-returntype-property"></a><span data-ttu-id="6bcf5-121">Właściwość ReturnType</span><span class="sxs-lookup"><span data-stu-id="6bcf5-121">The ReturnType Property</span></span>  
 <span data-ttu-id="6bcf5-122">Po XPath skompilowaniu zapytania do <xref:System.Xml.XPath.XPathExpression> obiektu, możesz użyć <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> właściwość <xref:System.Xml.XPath.XPathExpression> obiektu, aby określić zapytanie XPath zwraca.</span><span class="sxs-lookup"><span data-stu-id="6bcf5-122">After an XPath query has been compiled into an <xref:System.Xml.XPath.XPathExpression> object, you can use the <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> property of the <xref:System.Xml.XPath.XPathExpression> object to determine what the XPath query returns.</span></span>  
  
 <span data-ttu-id="6bcf5-123"><xref:System.Xml.XPath.XPathExpression.ReturnType%2A> Właściwość zwraca jedną z następujących <xref:System.Xml.XPath.XPathResultType> typów zwracanych wartości wyliczenia reprezentujący W3C XPath.</span><span class="sxs-lookup"><span data-stu-id="6bcf5-123">The <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> property returns one of the following <xref:System.Xml.XPath.XPathResultType> enumeration values representing the W3C XPath return types.</span></span>  
  
-   <xref:System.Xml.XPath.XPathResultType.Any>  
  
-   <xref:System.Xml.XPath.XPathResultType.Boolean>  
  
-   <xref:System.Xml.XPath.XPathResultType.Error>  
  
-   <xref:System.Xml.XPath.XPathResultType.Navigator>  
  
-   <xref:System.Xml.XPath.XPathResultType.NodeSet>  
  
-   <xref:System.Xml.XPath.XPathResultType.Number>  
  
-   <xref:System.Xml.XPath.XPathResultType.String>  
  
 <span data-ttu-id="6bcf5-124">W poniższym przykładzie użyto <xref:System.Xml.XPath.XPathExpression> obiekt do zwrotu numeru i węzeł z `books.xml` pliku.</span><span class="sxs-lookup"><span data-stu-id="6bcf5-124">The following example uses the <xref:System.Xml.XPath.XPathExpression> object to return a number and a node set from the `books.xml` file.</span></span> <span data-ttu-id="6bcf5-125"><xref:System.Xml.XPath.XPathExpression.ReturnType%2A> Właściwości każdego <xref:System.Xml.XPath.XPathExpression> obiektu oraz wyniki z <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> i <xref:System.Xml.XPath.XPathNavigator.Select%2A> metody są zapisywane do konsoli.</span><span class="sxs-lookup"><span data-stu-id="6bcf5-125">The <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> property of each <xref:System.Xml.XPath.XPathExpression> object as well as the results from the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> and <xref:System.Xml.XPath.XPathNavigator.Select%2A> methods are written to the console.</span></span>  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
' Returns a number.  
Dim query1 As XPathExpression = navigator.Compile("bookstore/book/price/text()*10")  
Console.WriteLine(query1.ReturnType)  
  
Dim number As Double = CType(navigator.Evaluate(query1), Double)  
Console.WriteLine(number)  
  
' Returns a node set.  
Dim query2 As XPathExpression = navigator.Compile("bookstore/book/price")  
Console.WriteLine(query2.ReturnType)  
  
Dim nodes As XPathNodeIterator = navigator.Select(query2)  
nodes.MoveNext()  
Console.WriteLine(nodes.Current.Value)  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
// Returns a number.  
XPathExpression query1 = navigator.Compile("bookstore/book/price/text()*10");  
Console.WriteLine(query1.ReturnType);  
  
Double number = (Double)navigator.Evaluate(query1);  
Console.WriteLine(number);  
  
// Returns a node set.  
XPathExpression query2 = navigator.Compile("bookstore/book/price");  
Console.WriteLine(query2.ReturnType);  
  
XPathNodeIterator nodes = navigator.Select(query2);  
nodes.MoveNext();  
Console.WriteLine(nodes.Current.Value);  
```  
  
 <span data-ttu-id="6bcf5-126">Przykład przyjmuje `books.xml` pliku jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="6bcf5-126">The example takes the `books.xml` file as input.</span></span>  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="higher-performance-xpath-expressions"></a><span data-ttu-id="6bcf5-127">Wyrażenia XPath w usłudze wyższej wydajności</span><span class="sxs-lookup"><span data-stu-id="6bcf5-127">Higher Performance XPath Expressions</span></span>  
 <span data-ttu-id="6bcf5-128">Lepszą wydajność należy użyć bardziej konkretny od pozostałych wyrażenia XPath w zapytaniach.</span><span class="sxs-lookup"><span data-stu-id="6bcf5-128">For better performance, use the most specific XPath expression possible in your queries.</span></span> <span data-ttu-id="6bcf5-129">Na przykład jeśli `book` węzeł jest elementem podrzędnym `bookstore` węzła i `bookstore` węzeł jest elementem najważniejsze w dokumencie XML za pomocą wyrażenia XPath `/bookstore/book` jest szybsza niż przy użyciu `//book`.</span><span class="sxs-lookup"><span data-stu-id="6bcf5-129">For example, if the `book` node is a child node of the `bookstore` node and the `bookstore` node is the top-most element in an XML document, using the XPath expression `/bookstore/book` is faster than using `//book`.</span></span> <span data-ttu-id="6bcf5-130">`//book` Wyrażenie XPath przeskanuje każdego węzła w drzewie XML, aby zidentyfikować pasujące węzły.</span><span class="sxs-lookup"><span data-stu-id="6bcf5-130">The `//book` XPath expression will scan every node in the XML tree to identify matching nodes.</span></span>  
  
 <span data-ttu-id="6bcf5-131">Ponadto, korzystając z węzła ustawić nawigacji metod dostarczonych przez <xref:System.Xml.XPath.XPathNavigator> klasy może spowodować lepszą wydajność za pośrednictwem metody dostarczone przez <xref:System.Xml.XPath.XPathNavigator> klasy w przypadkach, gdy kryteria wyboru są proste.</span><span class="sxs-lookup"><span data-stu-id="6bcf5-131">Additionally, using the node set navigation methods supplied by the <xref:System.Xml.XPath.XPathNavigator> class may result in improved performance over the selection methods supplied by the <xref:System.Xml.XPath.XPathNavigator> class in cases where your selection criteria are simple.</span></span> <span data-ttu-id="6bcf5-132">Na przykład, chcąc pierwszego elementu podrzędnego bieżącego węzła jest szybsze użyj <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A> metoda niż korzystać `child::*[1]` wyrażenie XPath i <xref:System.Xml.XPath.XPathNavigator.Select%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="6bcf5-132">For example, if you need to select the first child of the current node, it is faster to use the <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A> method than to use the `child::*[1]` XPath expression and the <xref:System.Xml.XPath.XPathNavigator.Select%2A> method.</span></span>  
  
 <span data-ttu-id="6bcf5-133">Aby uzyskać więcej informacji na temat węzła zestawu metod nawigacji <xref:System.Xml.XPath.XPathNavigator> klasy, zobacz [węzła zestawu nawigacji przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md).</span><span class="sxs-lookup"><span data-stu-id="6bcf5-133">For more information about the node set navigation methods of the <xref:System.Xml.XPath.XPathNavigator> class, see [Node Set Navigation Using XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bcf5-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6bcf5-134">See also</span></span>

- <xref:System.Xml.XmlDocument>  
- <xref:System.Xml.XPath.XPathDocument>  
- <xref:System.Xml.XPath.XPathNavigator>  
- [<span data-ttu-id="6bcf5-135">Przetwarzanie danych XML przy użyciu modelu danych XPath</span><span class="sxs-lookup"><span data-stu-id="6bcf5-135">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
- [<span data-ttu-id="6bcf5-136">Wybieranie danych XML przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="6bcf5-136">Select XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)  
- [<span data-ttu-id="6bcf5-137">Obliczanie wyrażeń XPath przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="6bcf5-137">Evaluate XPath Expressions using XPathNavigator</span></span>](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)  
- [<span data-ttu-id="6bcf5-138">Dopasowywanie węzłów przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="6bcf5-138">Matching Nodes using XPathNavigator</span></span>](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)  
- [<span data-ttu-id="6bcf5-139">Typy węzłów rozpoznawanych w zapytaniach XPath</span><span class="sxs-lookup"><span data-stu-id="6bcf5-139">Node Types Recognized with XPath Queries</span></span>](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)  
- [<span data-ttu-id="6bcf5-140">Zapytania XPath i przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="6bcf5-140">XPath Queries and Namespaces</span></span>](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)
