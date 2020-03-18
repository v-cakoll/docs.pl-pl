---
title: Porównanie metody XPath i LINQ to XML
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 87d361b1-daa9-4fd4-a53a-cbfa40111ad3
ms.openlocfilehash: e9bf192a2075653802f0c5a8b4e44ff0ceacb975
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "66487529"
---
# <a name="comparison-of-xpath-and-linq-to-xml"></a><span data-ttu-id="b19ca-102">Porównanie metody XPath i LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="b19ca-102">Comparison of XPath and LINQ to XML</span></span>
<span data-ttu-id="b19ca-103">XPath i LINQ do XML oferują pewne podobne funkcje.</span><span class="sxs-lookup"><span data-stu-id="b19ca-103">XPath and LINQ to XML offer some similar functionality.</span></span> <span data-ttu-id="b19ca-104">Oba mogą służyć do wykonywania zapytań drzewa XML, zwracając takie wyniki jak zbiór elementów, zbiór atrybutów, zbiór węzłów lub wartość elementu lub atrybutu.</span><span class="sxs-lookup"><span data-stu-id="b19ca-104">Both can be used to query an XML tree, returning such results as a collection of elements, a collection of attributes, a collection of nodes, or the value of an element or attribute.</span></span> <span data-ttu-id="b19ca-105">Istnieją jednak również pewne różnice.</span><span class="sxs-lookup"><span data-stu-id="b19ca-105">However, there are also some differences.</span></span>  
  
## <a name="differences-between-xpath-and-linq-to-xml"></a><span data-ttu-id="b19ca-106">Różnice między XPath i LINQ do XML</span><span class="sxs-lookup"><span data-stu-id="b19ca-106">Differences Between XPath and LINQ to XML</span></span>  
 <span data-ttu-id="b19ca-107">XPath nie zezwala na projekcję nowych typów.</span><span class="sxs-lookup"><span data-stu-id="b19ca-107">XPath does not allow projection of new types.</span></span> <span data-ttu-id="b19ca-108">Może zwracać tylko kolekcje węzłów z drzewa, podczas gdy LINQ do XML może wykonać kwerendę i rzutować wykres obiektu lub drzewo XML w nowym kształcie.</span><span class="sxs-lookup"><span data-stu-id="b19ca-108">It can only return collections of nodes from the tree, whereas LINQ to XML can execute a query and project an object graph or an XML tree in a new shape.</span></span> <span data-ttu-id="b19ca-109">LINQ do xml zapytania obejmują znacznie więcej funkcji i są znacznie bardziej wydajne niż wyrażenia XPath.</span><span class="sxs-lookup"><span data-stu-id="b19ca-109">LINQ to XML queries encompass much more functionality and are much more powerful than XPath expressions.</span></span>  
  
 <span data-ttu-id="b19ca-110">Wyrażenia XPath istnieją w izolacji w ciągu.</span><span class="sxs-lookup"><span data-stu-id="b19ca-110">XPath expressions exist in isolation within a string.</span></span> <span data-ttu-id="b19ca-111">Kompilator Języka C# nie może pomóc w przeanalizowaniu wyrażenia XPath w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="b19ca-111">The C# compiler cannot help parse the XPath expression at compile time.</span></span> <span data-ttu-id="b19ca-112">Natomiast zapytania LINQ do XML są analizowane i kompilowane przez kompilator C#.</span><span class="sxs-lookup"><span data-stu-id="b19ca-112">By contrast, LINQ to XML queries are parsed and compiled by the C# compiler.</span></span> <span data-ttu-id="b19ca-113">Kompilator jest w stanie przechwycić wiele błędów zapytań.</span><span class="sxs-lookup"><span data-stu-id="b19ca-113">The compiler is able to catch many query errors.</span></span>  
  
 <span data-ttu-id="b19ca-114">Wyniki XPath nie są silnie typowane.</span><span class="sxs-lookup"><span data-stu-id="b19ca-114">XPath results are not strongly typed.</span></span> <span data-ttu-id="b19ca-115">W wielu okolicznościach wynik oceny wyrażenia XPath jest obiektem i to do dewelopera należy określenie właściwego typu i rzutowanie wyniku w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="b19ca-115">In a number of circumstances, the result of evaluating an XPath expression is an object, and it is up to the developer to determine the proper type and cast the result as necessary.</span></span> <span data-ttu-id="b19ca-116">Natomiast rzutowania z kwerendy LINQ do XML są silnie typowane.</span><span class="sxs-lookup"><span data-stu-id="b19ca-116">By contrast, the projections from a LINQ to XML query are strongly typed.</span></span>  
  
## <a name="result-ordering"></a><span data-ttu-id="b19ca-117">Kolejność wyników</span><span class="sxs-lookup"><span data-stu-id="b19ca-117">Result Ordering</span></span>  
 <span data-ttu-id="b19ca-118">Zalecenie XPath 1.0 stwierdza, że kolekcja, która jest wynikiem oceny wyrażenia XPath jest nieuporządkowana.</span><span class="sxs-lookup"><span data-stu-id="b19ca-118">The XPath 1.0 Recommendation states that a collection that is the result of evaluating an XPath expression is unordered.</span></span>  
  
 <span data-ttu-id="b19ca-119">Jednak podczas iteracji za pośrednictwem kolekcji zwracanej przez LINQ do XML XPath metody osi, węzły w kolekcji są zwracane w kolejności dokumentu.</span><span class="sxs-lookup"><span data-stu-id="b19ca-119">However, when iterating through a collection returned by a LINQ to XML XPath axis method, the nodes in the collection are returned in document order.</span></span> <span data-ttu-id="b19ca-120">Dzieje się tak nawet podczas uzyskiwania dostępu do osi XPath, gdzie predykaty `preceding` są `preceding-sibling`wyrażone w kategoriach odwrotnej kolejności dokumentów, takich jak i .</span><span class="sxs-lookup"><span data-stu-id="b19ca-120">This is the case even when accessing the XPath axes where predicates are expressed in terms of reverse document order, such as `preceding` and `preceding-sibling`.</span></span>  
  
 <span data-ttu-id="b19ca-121">Natomiast większość osi LINQ do XML zwraca kolekcje w kolejności dokumentu, ale dwie z nich, <xref:System.Xml.Linq.XNode.Ancestors%2A> a <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>kolekcje zwracają w odwrotnej kolejności dokumentu.</span><span class="sxs-lookup"><span data-stu-id="b19ca-121">By contrast, most of the LINQ to XML axes return collections in document order, but two of them, <xref:System.Xml.Linq.XNode.Ancestors%2A> and <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>, return collections in reverse document order.</span></span> <span data-ttu-id="b19ca-122">W poniższej tabeli wylicza się osie i wskazuje kolejność zbierania dla każdego z nich:</span><span class="sxs-lookup"><span data-stu-id="b19ca-122">The following table enumerates the axes, and indicates collection order for each:</span></span>  
  
|<span data-ttu-id="b19ca-123">LINQ do osi XML</span><span class="sxs-lookup"><span data-stu-id="b19ca-123">LINQ to XML axis</span></span>|<span data-ttu-id="b19ca-124">Szeregowanie</span><span class="sxs-lookup"><span data-stu-id="b19ca-124">Ordering</span></span>|  
|----------------------|--------------|  
|<span data-ttu-id="b19ca-125">Węzły XContainer.Descendant</span><span class="sxs-lookup"><span data-stu-id="b19ca-125">XContainer.DescendantNodes</span></span>|<span data-ttu-id="b19ca-126">Kolejność dokumentów</span><span class="sxs-lookup"><span data-stu-id="b19ca-126">Document order</span></span>|  
|<span data-ttu-id="b19ca-127">XContainer.Descendants (Podrzędne).</span><span class="sxs-lookup"><span data-stu-id="b19ca-127">XContainer.Descendants</span></span>|<span data-ttu-id="b19ca-128">Kolejność dokumentów</span><span class="sxs-lookup"><span data-stu-id="b19ca-128">Document order</span></span>|  
|<span data-ttu-id="b19ca-129">XContainer.Elements (Elementy XContainer.Elements)</span><span class="sxs-lookup"><span data-stu-id="b19ca-129">XContainer.Elements</span></span>|<span data-ttu-id="b19ca-130">Kolejność dokumentów</span><span class="sxs-lookup"><span data-stu-id="b19ca-130">Document order</span></span>|  
|<span data-ttu-id="b19ca-131">XContainer.Węzły</span><span class="sxs-lookup"><span data-stu-id="b19ca-131">XContainer.Nodes</span></span>|<span data-ttu-id="b19ca-132">Kolejność dokumentów</span><span class="sxs-lookup"><span data-stu-id="b19ca-132">Document order</span></span>|  
|<span data-ttu-id="b19ca-133">XContainer.NodesAfterSelf</span><span class="sxs-lookup"><span data-stu-id="b19ca-133">XContainer.NodesAfterSelf</span></span>|<span data-ttu-id="b19ca-134">Kolejność dokumentów</span><span class="sxs-lookup"><span data-stu-id="b19ca-134">Document order</span></span>|  
|<span data-ttu-id="b19ca-135">XContainer.NodesPrzedsiebie</span><span class="sxs-lookup"><span data-stu-id="b19ca-135">XContainer.NodesBeforeSelf</span></span>|<span data-ttu-id="b19ca-136">Kolejność dokumentów</span><span class="sxs-lookup"><span data-stu-id="b19ca-136">Document order</span></span>|  
|<span data-ttu-id="b19ca-137">XElement.AncestorsISelf</span><span class="sxs-lookup"><span data-stu-id="b19ca-137">XElement.AncestorsAndSelf</span></span>|<span data-ttu-id="b19ca-138">Odwróć kolejność dokumentów</span><span class="sxs-lookup"><span data-stu-id="b19ca-138">Reverse document order</span></span>|  
|<span data-ttu-id="b19ca-139">XElement.Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b19ca-139">XElement.Attributes</span></span>|<span data-ttu-id="b19ca-140">Kolejność dokumentów</span><span class="sxs-lookup"><span data-stu-id="b19ca-140">Document order</span></span>|  
|<span data-ttu-id="b19ca-141">XElement.DescendantNodesAndSelf</span><span class="sxs-lookup"><span data-stu-id="b19ca-141">XElement.DescendantNodesAndSelf</span></span>|<span data-ttu-id="b19ca-142">Kolejność dokumentów</span><span class="sxs-lookup"><span data-stu-id="b19ca-142">Document order</span></span>|  
|<span data-ttu-id="b19ca-143">XElement.DescendantsAndSelf</span><span class="sxs-lookup"><span data-stu-id="b19ca-143">XElement.DescendantsAndSelf</span></span>|<span data-ttu-id="b19ca-144">Kolejność dokumentów</span><span class="sxs-lookup"><span data-stu-id="b19ca-144">Document order</span></span>|  
|<span data-ttu-id="b19ca-145">XNode.Przodkowie</span><span class="sxs-lookup"><span data-stu-id="b19ca-145">XNode.Ancestors</span></span>|<span data-ttu-id="b19ca-146">Odwróć kolejność dokumentów</span><span class="sxs-lookup"><span data-stu-id="b19ca-146">Reverse document order</span></span>|  
|<span data-ttu-id="b19ca-147">XNode.ElementsAfterSelf</span><span class="sxs-lookup"><span data-stu-id="b19ca-147">XNode.ElementsAfterSelf</span></span>|<span data-ttu-id="b19ca-148">Kolejność dokumentów</span><span class="sxs-lookup"><span data-stu-id="b19ca-148">Document order</span></span>|  
|<span data-ttu-id="b19ca-149">XNode.ElementsBeforeSelf</span><span class="sxs-lookup"><span data-stu-id="b19ca-149">XNode.ElementsBeforeSelf</span></span>|<span data-ttu-id="b19ca-150">Kolejność dokumentów</span><span class="sxs-lookup"><span data-stu-id="b19ca-150">Document order</span></span>|  
|<span data-ttu-id="b19ca-151">XNode.NodesAfterSelf</span><span class="sxs-lookup"><span data-stu-id="b19ca-151">XNode.NodesAfterSelf</span></span>|<span data-ttu-id="b19ca-152">Kolejność dokumentów</span><span class="sxs-lookup"><span data-stu-id="b19ca-152">Document order</span></span>|  
|<span data-ttu-id="b19ca-153">XNode.NodesBeforeSelf</span><span class="sxs-lookup"><span data-stu-id="b19ca-153">XNode.NodesBeforeSelf</span></span>|<span data-ttu-id="b19ca-154">Kolejność dokumentów</span><span class="sxs-lookup"><span data-stu-id="b19ca-154">Document order</span></span>|  
  
## <a name="positional-predicates"></a><span data-ttu-id="b19ca-155">Predykaty pozycyjne</span><span class="sxs-lookup"><span data-stu-id="b19ca-155">Positional Predicates</span></span>  
 <span data-ttu-id="b19ca-156">W wyrażeniu XPath predykaty pozycyjne są wyrażane w kolejności dokumentów dla wielu osi, ale są `preceding`wyrażone w odwrotnej kolejności dokumentu dla osi odwróconych, które są , `preceding-sibling`, `ancestor`, i `ancestor-or-self`.</span><span class="sxs-lookup"><span data-stu-id="b19ca-156">Within an XPath expression, positional predicates are expressed in terms of document order for many axes, but are expressed in reverse document order for reverse axes, which are `preceding`, `preceding-sibling`, `ancestor`, and `ancestor-or-self`.</span></span> <span data-ttu-id="b19ca-157">Na przykład wyrażenie `preceding-sibling::*[1]` XPath zwraca bezpośrednio poprzedzających elementu równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="b19ca-157">For example, the XPath expression `preceding-sibling::*[1]` returns the immediately preceding sibling.</span></span> <span data-ttu-id="b19ca-158">Dzieje się tak, mimo że ostateczny zestaw wyników jest prezentowany w kolejności dokumentu.</span><span class="sxs-lookup"><span data-stu-id="b19ca-158">This is the case even though the final result set is presented in document order.</span></span>  
  
 <span data-ttu-id="b19ca-159">Natomiast wszystkie predykaty pozycyjne w LINQ do XML są zawsze wyrażone w kolejności osi.</span><span class="sxs-lookup"><span data-stu-id="b19ca-159">By contrast, all positional predicates in LINQ to XML are always expressed in terms of the order of the axis.</span></span> <span data-ttu-id="b19ca-160">Na przykład `anElement.ElementsBeforeSelf().ElementAt(0)` zwraca pierwszy element podrzędny elementu nadrzędnego elementu, którego dotyczy kwerenda, a nie bezpośrednio poprzedzających elementu równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="b19ca-160">For example, `anElement.ElementsBeforeSelf().ElementAt(0)` returns the first child element of the parent of the queried element, not the immediate preceding sibling.</span></span> <span data-ttu-id="b19ca-161">Inny przykład: `anElement.Ancestors().ElementAt(0)` zwraca element nadrzędny.</span><span class="sxs-lookup"><span data-stu-id="b19ca-161">Another example: `anElement.Ancestors().ElementAt(0)` returns the parent element.</span></span>  
  
 <span data-ttu-id="b19ca-162">Jeśli chcesz znaleźć bezpośrednio poprzedzający element w LINQ do XML, należy napisać następujące wyrażenie:</span><span class="sxs-lookup"><span data-stu-id="b19ca-162">If you wanted to find the immediately preceding element in LINQ to XML, you would write the following expression:</span></span>  
  
```csharp
ElementsBeforeSelf().Last()
```
  
```vb
ElementsBeforeSelf().Last()
```
  
## <a name="performance-differences"></a><span data-ttu-id="b19ca-163">Różnice w wydajności</span><span class="sxs-lookup"><span data-stu-id="b19ca-163">Performance Differences</span></span>  
 <span data-ttu-id="b19ca-164">Kwerendy XPath, które używają funkcji XPath w LINQ do XML nie będzie działać, jak również LINQ do xml kwerend.</span><span class="sxs-lookup"><span data-stu-id="b19ca-164">XPath queries that use the XPath functionality in LINQ to XML will not perform as well as LINQ to XML queries.</span></span>  
  
## <a name="comparison-of-composition"></a><span data-ttu-id="b19ca-165">Porównanie składu</span><span class="sxs-lookup"><span data-stu-id="b19ca-165">Comparison of Composition</span></span>  
 <span data-ttu-id="b19ca-166">Skład kwerendy LINQ do XML jest nieco równoległy do kompozycji wyrażenia XPath, chociaż bardzo różni się składnią.</span><span class="sxs-lookup"><span data-stu-id="b19ca-166">Composition of a LINQ to XML query is somewhat parallel to composition of an XPath expression, although very different in syntax.</span></span>  
  
 <span data-ttu-id="b19ca-167">Na przykład jeśli masz element w `customers`zmiennej o nazwie i chcesz `CompanyName` znaleźć element wnuka o nazwie pod wszystkimi elementami podrzędnych o nazwie, `Customer`należy napisać wyrażenie XPath w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="b19ca-167">For example, if you have an element in a variable named `customers`, and you want to find a grandchild element named `CompanyName` under all child elements named `Customer`, you would write an XPath expression as follows:</span></span>  
  
```csharp  
customers.XPathSelectElements("./Customer/CompanyName")
```  
  
```vb
customers.XPathSelectElements("./Customer/CompanyName")
```

 <span data-ttu-id="b19ca-168">Równoważne LINQ do kwerendy XML jest:</span><span class="sxs-lookup"><span data-stu-id="b19ca-168">The equivalent LINQ to XML query is:</span></span>  
  
```csharp  
customers.Elements("Customer").Elements("CompanyName")
```  
  
```vb
customers.Elements("Customer").Elements("CompanyName")
```  

 <span data-ttu-id="b19ca-169">Istnieją podobne podobieństwa dla każdej z osi XPath.</span><span class="sxs-lookup"><span data-stu-id="b19ca-169">There are similar parallels for each of the XPath axes.</span></span>  
  
|<span data-ttu-id="b19ca-170">Oś XPath</span><span class="sxs-lookup"><span data-stu-id="b19ca-170">XPath axis</span></span>|<span data-ttu-id="b19ca-171">LINQ do osi XML</span><span class="sxs-lookup"><span data-stu-id="b19ca-171">LINQ to XML axis</span></span>|  
|----------------|----------------------|  
|<span data-ttu-id="b19ca-172">podrzędny (oś domyślna)</span><span class="sxs-lookup"><span data-stu-id="b19ca-172">child (the default axis)</span></span>|<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="b19ca-173">Element nadrzędny (..)</span><span class="sxs-lookup"><span data-stu-id="b19ca-173">Parent (..)</span></span>|<xref:System.Xml.Linq.XObject.Parent%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="b19ca-174">oś atrybutu (@)</span><span class="sxs-lookup"><span data-stu-id="b19ca-174">attribute axis (@)</span></span>|<xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="b19ca-175">lub</span><span class="sxs-lookup"><span data-stu-id="b19ca-175">or</span></span><br /><br /> <xref:System.Xml.Linq.XElement.Attributes%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="b19ca-176">oś przodka</span><span class="sxs-lookup"><span data-stu-id="b19ca-176">ancestor axis</span></span>|<xref:System.Xml.Linq.XNode.Ancestors%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="b19ca-177">oś przodka lub samo-siebie</span><span class="sxs-lookup"><span data-stu-id="b19ca-177">ancestor-or-self axis</span></span>|<xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="b19ca-178">oś podrzędna (//)</span><span class="sxs-lookup"><span data-stu-id="b19ca-178">descendant axis (//)</span></span>|<xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="b19ca-179">lub</span><span class="sxs-lookup"><span data-stu-id="b19ca-179">or</span></span><br /><br /> <xref:System.Xml.Linq.XContainer.DescendantNodes%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="b19ca-180">pojechania lub-ja</span><span class="sxs-lookup"><span data-stu-id="b19ca-180">descendant-or-self</span></span>|<xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="b19ca-181">lub</span><span class="sxs-lookup"><span data-stu-id="b19ca-181">or</span></span><br /><br /> <xref:System.Xml.Linq.XElement.DescendantNodesAndSelf%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="b19ca-182">kolejne rodzeństwo</span><span class="sxs-lookup"><span data-stu-id="b19ca-182">following-sibling</span></span>|<xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="b19ca-183">lub</span><span class="sxs-lookup"><span data-stu-id="b19ca-183">or</span></span><br /><br /> <xref:System.Xml.Linq.XNode.NodesAfterSelf%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="b19ca-184">poprzednia rodzeństwo</span><span class="sxs-lookup"><span data-stu-id="b19ca-184">preceding-sibling</span></span>|<xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="b19ca-185">lub</span><span class="sxs-lookup"><span data-stu-id="b19ca-185">or</span></span><br /><br /> <xref:System.Xml.Linq.XNode.NodesBeforeSelf%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="b19ca-186">Następujące</span><span class="sxs-lookup"><span data-stu-id="b19ca-186">following</span></span>|<span data-ttu-id="b19ca-187">Brak bezpośredniego odpowiednika.</span><span class="sxs-lookup"><span data-stu-id="b19ca-187">No direct equivalent.</span></span>|  
|<span data-ttu-id="b19ca-188">Poprzednim</span><span class="sxs-lookup"><span data-stu-id="b19ca-188">preceding</span></span>|<span data-ttu-id="b19ca-189">Brak bezpośredniego odpowiednika.</span><span class="sxs-lookup"><span data-stu-id="b19ca-189">No direct equivalent.</span></span>|  
  