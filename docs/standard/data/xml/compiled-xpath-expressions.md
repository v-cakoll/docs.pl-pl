---
title: Skompilowane wyrażenia XPath
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: e25dd95f-b64c-4d8b-a3a4-379e1aa0ad55
ms.openlocfilehash: b4675765849299050eb6cddeaaa497bc6cdc620a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711106"
---
# <a name="compiled-xpath-expressions"></a><span data-ttu-id="6d3e4-102">Skompilowane wyrażenia XPath</span><span class="sxs-lookup"><span data-stu-id="6d3e4-102">Compiled XPath Expressions</span></span>
<span data-ttu-id="6d3e4-103">Obiekt <xref:System.Xml.XPath.XPathExpression> reprezentuje skompilowane zapytanie XPath zwrócone z metody static <xref:System.Xml.XPath.XPathExpression.Compile%2A> klasy <xref:System.Xml.XPath.XPathExpression> lub <xref:System.Xml.XPath.XPathNavigator.Compile%2A> metody klasy <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="6d3e4-103">An <xref:System.Xml.XPath.XPathExpression> object represents a compiled XPath query returned from either the static <xref:System.Xml.XPath.XPathExpression.Compile%2A> method of the <xref:System.Xml.XPath.XPathExpression> class or the <xref:System.Xml.XPath.XPathNavigator.Compile%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
## <a name="the-xpathexpression-class"></a><span data-ttu-id="6d3e4-104">Klasa XPathExpression</span><span class="sxs-lookup"><span data-stu-id="6d3e4-104">The XPathExpression Class</span></span>  
 <span data-ttu-id="6d3e4-105">Skompilowane zapytanie XPath reprezentowane przez obiekt <xref:System.Xml.XPath.XPathExpression> jest przydatne, jeśli ta sama kwerenda XPath jest używana więcej niż raz.</span><span class="sxs-lookup"><span data-stu-id="6d3e4-105">A compiled XPath query represented by an <xref:System.Xml.XPath.XPathExpression> object is useful if the same XPath query is being used more than once.</span></span>  
  
 <span data-ttu-id="6d3e4-106">Na przykład w przypadku wywołania metody <xref:System.Xml.XPath.XPathNavigator.Select%2A> wiele razy zamiast używania ciągu reprezentującego kwerendę XPath za każdym razem użyj metody <xref:System.Xml.XPath.XPathExpression.Compile%2A> klasy <xref:System.Xml.XPath.XPathExpression> lub metody <xref:System.Xml.XPath.XPathNavigator.Compile%2A> klasy <xref:System.Xml.XPath.XPathNavigator> do kompilowania i buforowania zapytania XPath w obiekcie <xref:System.Xml.XPath.XPathExpression>, aby ponownie wykorzystać i zwiększyć wydajność.</span><span class="sxs-lookup"><span data-stu-id="6d3e4-106">For example, when calling the <xref:System.Xml.XPath.XPathNavigator.Select%2A> method multiple times, instead of using a string representing the XPath query each time, use the <xref:System.Xml.XPath.XPathExpression.Compile%2A> method of the <xref:System.Xml.XPath.XPathExpression> class or the <xref:System.Xml.XPath.XPathNavigator.Compile%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class to compile and cache the XPath query in an <xref:System.Xml.XPath.XPathExpression> object for reuse and improved performance.</span></span>  
  
 <span data-ttu-id="6d3e4-107">Po skompilowaniu obiekt <xref:System.Xml.XPath.XPathExpression> może być używany jako dane wejściowe do poniższych metod klasy <xref:System.Xml.XPath.XPathNavigator> w zależności od typu zwracanego z kwerendy XPath.</span><span class="sxs-lookup"><span data-stu-id="6d3e4-107">Once compiled, the <xref:System.Xml.XPath.XPathExpression> object may be used as input to the following <xref:System.Xml.XPath.XPathNavigator> class methods depending on the type returned from the XPath query.</span></span>  
  
- <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.XPath.XPathNavigator.Matches%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
 <span data-ttu-id="6d3e4-108">W poniższej tabeli opisano wszystkie typy zwracane w formacie W3C XPath, ich Microsoft .NET Framework equivalencies i metody, z których może korzystać obiekt <xref:System.Xml.XPath.XPathExpression>, w zależności od typu zwracanego.</span><span class="sxs-lookup"><span data-stu-id="6d3e4-108">The following table describes each of the W3C XPath return types, their Microsoft .NET Framework equivalencies, and what methods the <xref:System.Xml.XPath.XPathExpression> object may be used with based on its return type.</span></span>  
  
|<span data-ttu-id="6d3e4-109">Typ zwracany XPath W3C</span><span class="sxs-lookup"><span data-stu-id="6d3e4-109">W3C XPath Return Type</span></span>|<span data-ttu-id="6d3e4-110">Typ odpowiedni .NET Framework</span><span class="sxs-lookup"><span data-stu-id="6d3e4-110">.NET Framework Equivalent Type</span></span>|<span data-ttu-id="6d3e4-111">Opis</span><span class="sxs-lookup"><span data-stu-id="6d3e4-111">Description</span></span>|<span data-ttu-id="6d3e4-112">Metody</span><span class="sxs-lookup"><span data-stu-id="6d3e4-112">Methods</span></span>|  
|---------------------------|------------------------------------|-----------------|-------------|  
|`Node set`|<xref:System.Xml.XPath.XPathNodeIterator>|<span data-ttu-id="6d3e4-113">Nieuporządkowana kolekcja węzłów bez duplikatów utworzonych w kolejności dokumentu.</span><span class="sxs-lookup"><span data-stu-id="6d3e4-113">An unordered collection of nodes without duplicates created in document order.</span></span>|<span data-ttu-id="6d3e4-114"><xref:System.Xml.XPath.XPathNavigator.Select%2A> lub <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A></span><span class="sxs-lookup"><span data-stu-id="6d3e4-114"><xref:System.Xml.XPath.XPathNavigator.Select%2A> or <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A></span></span>|  
|`Boolean`|<xref:System.Boolean>|<span data-ttu-id="6d3e4-115">Wartość `true` lub `false`.</span><span class="sxs-lookup"><span data-stu-id="6d3e4-115">A `true` or `false` value.</span></span>|<span data-ttu-id="6d3e4-116"><xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> lub</span><span class="sxs-lookup"><span data-stu-id="6d3e4-116"><xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> or</span></span><br /><br /> <xref:System.Xml.XPath.XPathNavigator.Matches%2A>|  
|`Number`|<xref:System.Double>|<span data-ttu-id="6d3e4-117">Liczba zmiennoprzecinkowa.</span><span class="sxs-lookup"><span data-stu-id="6d3e4-117">A floating-point number.</span></span>|<xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>|  
|`String`|<xref:System.String>|<span data-ttu-id="6d3e4-118">Sekwencja znaków UCS.</span><span class="sxs-lookup"><span data-stu-id="6d3e4-118">A sequence of UCS characters.</span></span>|<xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>|  
  
> [!NOTE]
> <span data-ttu-id="6d3e4-119">Metoda <xref:System.Xml.XPath.XPathNavigator.Matches%2A> akceptuje wyrażenie XPath jako parametr.</span><span class="sxs-lookup"><span data-stu-id="6d3e4-119">The <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method accepts an XPath expression as its parameter.</span></span> <span data-ttu-id="6d3e4-120">Metoda <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> zwraca obiekt <xref:System.Xml.XPath.XPathNavigator>, a nie jeden z typów zwracanych w formacie xmlxpath.</span><span class="sxs-lookup"><span data-stu-id="6d3e4-120">The <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> method returns an <xref:System.Xml.XPath.XPathNavigator> object, not one of the W3C XPath return types.</span></span>  
  
### <a name="the-returntype-property"></a><span data-ttu-id="6d3e4-121">Właściwość ReturnType</span><span class="sxs-lookup"><span data-stu-id="6d3e4-121">The ReturnType Property</span></span>  
 <span data-ttu-id="6d3e4-122">Po skompilowaniu zapytania XPath do obiektu <xref:System.Xml.XPath.XPathExpression> można użyć właściwości <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> obiektu <xref:System.Xml.XPath.XPathExpression>, aby określić, co zwraca zapytanie XPath.</span><span class="sxs-lookup"><span data-stu-id="6d3e4-122">After an XPath query has been compiled into an <xref:System.Xml.XPath.XPathExpression> object, you can use the <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> property of the <xref:System.Xml.XPath.XPathExpression> object to determine what the XPath query returns.</span></span>  
  
 <span data-ttu-id="6d3e4-123">Właściwość <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> zwraca jedną z następujących <xref:System.Xml.XPath.XPathResultType> wartości wyliczenia reprezentujących typy zwracane w formacie W3C XPath.</span><span class="sxs-lookup"><span data-stu-id="6d3e4-123">The <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> property returns one of the following <xref:System.Xml.XPath.XPathResultType> enumeration values representing the W3C XPath return types.</span></span>  
  
- <xref:System.Xml.XPath.XPathResultType.Any>  
  
- <xref:System.Xml.XPath.XPathResultType.Boolean>  
  
- <xref:System.Xml.XPath.XPathResultType.Error>  
  
- <xref:System.Xml.XPath.XPathResultType.Navigator>  
  
- <xref:System.Xml.XPath.XPathResultType.NodeSet>  
  
- <xref:System.Xml.XPath.XPathResultType.Number>  
  
- <xref:System.Xml.XPath.XPathResultType.String>  
  
 <span data-ttu-id="6d3e4-124">Poniższy przykład używa obiektu <xref:System.Xml.XPath.XPathExpression>, aby zwrócić numer i zestaw węzłów z pliku `books.xml`.</span><span class="sxs-lookup"><span data-stu-id="6d3e4-124">The following example uses the <xref:System.Xml.XPath.XPathExpression> object to return a number and a node set from the `books.xml` file.</span></span> <span data-ttu-id="6d3e4-125">Właściwość <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> każdego obiektu <xref:System.Xml.XPath.XPathExpression>, a także wyniki <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> i <xref:System.Xml.XPath.XPathNavigator.Select%2A> metody są zapisywane w konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="6d3e4-125">The <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> property of each <xref:System.Xml.XPath.XPathExpression> object as well as the results from the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> and <xref:System.Xml.XPath.XPathNavigator.Select%2A> methods are written to the console.</span></span>  
  
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
  
 <span data-ttu-id="6d3e4-126">Przykład pobiera `books.xml` plik jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="6d3e4-126">The example takes the `books.xml` file as input.</span></span>  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="higher-performance-xpath-expressions"></a><span data-ttu-id="6d3e4-127">Wyrażenia XPath o wyższej wydajności</span><span class="sxs-lookup"><span data-stu-id="6d3e4-127">Higher Performance XPath Expressions</span></span>  
 <span data-ttu-id="6d3e4-128">Aby uzyskać lepszą wydajność, użyj najbardziej określonego wyrażenia XPath możliwego w zapytaniach.</span><span class="sxs-lookup"><span data-stu-id="6d3e4-128">For better performance, use the most specific XPath expression possible in your queries.</span></span> <span data-ttu-id="6d3e4-129">Na przykład, jeśli węzeł `book` jest węzłem podrzędnym węzła `bookstore`, a węzeł `bookstore` jest elementem najwyższego poziomu w dokumencie XML, użycie wyrażenia XPath `/bookstore/book` jest szybsze niż użycie `//book`.</span><span class="sxs-lookup"><span data-stu-id="6d3e4-129">For example, if the `book` node is a child node of the `bookstore` node and the `bookstore` node is the top-most element in an XML document, using the XPath expression `/bookstore/book` is faster than using `//book`.</span></span> <span data-ttu-id="6d3e4-130">`//book` wyrażenie XPath skanuje każdy węzeł w drzewie XML, aby zidentyfikować pasujące węzły.</span><span class="sxs-lookup"><span data-stu-id="6d3e4-130">The `//book` XPath expression will scan every node in the XML tree to identify matching nodes.</span></span>  
  
 <span data-ttu-id="6d3e4-131">Ponadto przy użyciu metod nawigacji zestawu węzłów dostarczonych przez klasę <xref:System.Xml.XPath.XPathNavigator> może spowodować zwiększenie wydajności na podstawie metod wyboru dostarczonych przez klasę <xref:System.Xml.XPath.XPathNavigator> w przypadkach, gdy kryteria wyboru są proste.</span><span class="sxs-lookup"><span data-stu-id="6d3e4-131">Additionally, using the node set navigation methods supplied by the <xref:System.Xml.XPath.XPathNavigator> class may result in improved performance over the selection methods supplied by the <xref:System.Xml.XPath.XPathNavigator> class in cases where your selection criteria are simple.</span></span> <span data-ttu-id="6d3e4-132">Na przykład, jeśli trzeba wybrać pierwszy element podrzędny bieżącego węzła, można użyć metody <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>ej, aby użyć `child::*[1]` wyrażenia XPath i metody <xref:System.Xml.XPath.XPathNavigator.Select%2A>.</span><span class="sxs-lookup"><span data-stu-id="6d3e4-132">For example, if you need to select the first child of the current node, it is faster to use the <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A> method than to use the `child::*[1]` XPath expression and the <xref:System.Xml.XPath.XPathNavigator.Select%2A> method.</span></span>  
  
 <span data-ttu-id="6d3e4-133">Aby uzyskać więcej informacji na temat metod nawigacji zestawu węzłów klasy <xref:System.Xml.XPath.XPathNavigator>, zobacz [Nawigacja zestawu węzłów za pomocą elementu XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md).</span><span class="sxs-lookup"><span data-stu-id="6d3e4-133">For more information about the node set navigation methods of the <xref:System.Xml.XPath.XPathNavigator> class, see [Node Set Navigation Using XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d3e4-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6d3e4-134">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="6d3e4-135">Przetwarzanie danych XML przy użyciu modelu danych XPath</span><span class="sxs-lookup"><span data-stu-id="6d3e4-135">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="6d3e4-136">Wybieranie danych XML przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="6d3e4-136">Select XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="6d3e4-137">Obliczanie wyrażeń XPath przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="6d3e4-137">Evaluate XPath Expressions using XPathNavigator</span></span>](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)
- [<span data-ttu-id="6d3e4-138">Dopasowywanie węzłów przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="6d3e4-138">Matching Nodes using XPathNavigator</span></span>](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)
- [<span data-ttu-id="6d3e4-139">Typy węzłów rozpoznawanych w zapytaniach XPath</span><span class="sxs-lookup"><span data-stu-id="6d3e4-139">Node Types Recognized with XPath Queries</span></span>](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)
- [<span data-ttu-id="6d3e4-140">Zapytania XPath i przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="6d3e4-140">XPath Queries and Namespaces</span></span>](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)
