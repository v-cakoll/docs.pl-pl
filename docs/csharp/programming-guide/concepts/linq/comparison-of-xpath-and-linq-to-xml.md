---
title: Porównanie metody XPath i LINQ to XML
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 87d361b1-daa9-4fd4-a53a-cbfa40111ad3
ms.openlocfilehash: f41aa19c89365c9236ca0b8d385ffa6fbaf6be1c
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43391739"
---
# <a name="comparison-of-xpath-and-linq-to-xml"></a><span data-ttu-id="03e5c-102">Porównanie metody XPath i LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="03e5c-102">Comparison of XPath and LINQ to XML</span></span>
<span data-ttu-id="03e5c-103">Wyrażenie XPath i LINQ to XML oferuje kilka podobne funkcje.</span><span class="sxs-lookup"><span data-stu-id="03e5c-103">XPath and LINQ to XML offer some similar functionality.</span></span> <span data-ttu-id="03e5c-104">Jednocześnie może służyć do kwerendy drzewa XML, zwracaniu takich wyników jako kolekcja elementów, Kolekcja atrybutów, kolekcja węzłów lub wartość elementu lub atrybutu.</span><span class="sxs-lookup"><span data-stu-id="03e5c-104">Both can be used to query an XML tree, returning such results as a collection of elements, a collection of attributes, a collection of nodes, or the value of an element or attribute.</span></span> <span data-ttu-id="03e5c-105">Istnieją również pewne różnice.</span><span class="sxs-lookup"><span data-stu-id="03e5c-105">However, there are also some differences.</span></span>  
  
## <a name="differences-between-xpath-and-linq-to-xml"></a><span data-ttu-id="03e5c-106">Różnice między XPath i LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="03e5c-106">Differences Between XPath and LINQ to XML</span></span>  
 <span data-ttu-id="03e5c-107">Wyrażenie XPath nie zezwala na projekcji nowych typów.</span><span class="sxs-lookup"><span data-stu-id="03e5c-107">XPath does not allow projection of new types.</span></span> <span data-ttu-id="03e5c-108">Jego może zwracać tylko kolekcje węzłów z drzewa, natomiast LINQ to XML można wykonać zapytania i projektu wykresu obiektu lub drzewa XML w nowy kształt.</span><span class="sxs-lookup"><span data-stu-id="03e5c-108">It can only return collections of nodes from the tree, whereas LINQ to XML can execute a query and project an object graph or an XML tree in a new shape.</span></span> <span data-ttu-id="03e5c-109">LINQ do XML zapytań uwzględniający znacznie więcej funkcji i są bardziej zaawansowane niż wyrażenia XPath.</span><span class="sxs-lookup"><span data-stu-id="03e5c-109">LINQ to XML queries encompass much more functionality and are much more powerful than XPath expressions.</span></span>  
  
 <span data-ttu-id="03e5c-110">Wyrażenia XPath istnieje w izolacji wewnątrz ciągu.</span><span class="sxs-lookup"><span data-stu-id="03e5c-110">XPath expressions exist in isolation within a string.</span></span> <span data-ttu-id="03e5c-111">Kompilator języka C# nie będzie mogła pomóc przeanalizować wyrażenia XPath w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="03e5c-111">The C# compiler cannot help parse the XPath expression at compile time.</span></span> <span data-ttu-id="03e5c-112">Z drugiej strony LINQ to XML zapytania są analizowane i kompilowane przez kompilator języka C#.</span><span class="sxs-lookup"><span data-stu-id="03e5c-112">By contrast, LINQ to XML queries are parsed and compiled by the C# compiler.</span></span> <span data-ttu-id="03e5c-113">Kompilator jest w stanie przechwytywania wielu błędów zapytań.</span><span class="sxs-lookup"><span data-stu-id="03e5c-113">The compiler is able to catch many query errors.</span></span>  
  
 <span data-ttu-id="03e5c-114">Wyniki XPath nie są silnie typizowane.</span><span class="sxs-lookup"><span data-stu-id="03e5c-114">XPath results are not strongly typed.</span></span> <span data-ttu-id="03e5c-115">W wielu sytuacjach wynikiem obliczenia wyrażenia XPath jest obiektem, a zależy od dla deweloperów, aby ustalić odpowiedniego typu i Rzutuj wynik metody zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="03e5c-115">In a number of circumstances, the result of evaluating an XPath expression is an object, and it is up to the developer to determine the proper type and cast the result as necessary.</span></span> <span data-ttu-id="03e5c-116">Z drugiej strony projekcje z LINQ do kwerendy XML są silnie typizowane.</span><span class="sxs-lookup"><span data-stu-id="03e5c-116">By contrast, the projections from a LINQ to XML query are strongly typed.</span></span>  
  
## <a name="result-ordering"></a><span data-ttu-id="03e5c-117">Wynik, porządkowanie</span><span class="sxs-lookup"><span data-stu-id="03e5c-117">Result Ordering</span></span>  
 <span data-ttu-id="03e5c-118">Wyrażenie XPath 1.0 zalecenie stanów, nieuporządkowane to kolekcja, która jest wynikiem obliczenia wyrażenia XPath.</span><span class="sxs-lookup"><span data-stu-id="03e5c-118">The XPath 1.0 Recommendation states that a collection that is the result of evaluating an XPath expression is unordered.</span></span>  
  
 <span data-ttu-id="03e5c-119">Podczas iteracji przez kolekcję zwracane przez LINQ do XML XPath metody osi, węzły w kolekcji są zwracane w kolejności dokumentu.</span><span class="sxs-lookup"><span data-stu-id="03e5c-119">However, when iterating through a collection returned by a LINQ to XML XPath axis method, the nodes in the collection are returned in document order.</span></span> <span data-ttu-id="03e5c-120">Jest to możliwe nawet wtedy, gdy dostęp do osi XPath gdzie predykaty są wyrażone w kolejności odwrotnej dokumentu, takich jak `preceding` i `preceding-sibling`.</span><span class="sxs-lookup"><span data-stu-id="03e5c-120">This is the case even when accessing the XPath axes where predicates are expressed in terms of reverse document order, such as `preceding` and `preceding-sibling`.</span></span>  
  
 <span data-ttu-id="03e5c-121">Z kolei większość LINQ to XML osi zwrócić kolekcji w kolejności dokumentu, ale dwa z nich, <xref:System.Xml.Linq.XNode.Ancestors%2A> i <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>, zwracają kolekcje w kolejności odwrotnej dokumentu.</span><span class="sxs-lookup"><span data-stu-id="03e5c-121">By contrast, most of the LINQ to XML axes return collections in document order, but two of them, <xref:System.Xml.Linq.XNode.Ancestors%2A> and <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>, return collections in reverse document order.</span></span> <span data-ttu-id="03e5c-122">W poniższej tabeli wylicza osi i wskazuje kolejność kolekcji dla każdego:</span><span class="sxs-lookup"><span data-stu-id="03e5c-122">The following table enumerates the axes, and indicates collection order for each:</span></span>  
  
|<span data-ttu-id="03e5c-123">LINQ do XML osi</span><span class="sxs-lookup"><span data-stu-id="03e5c-123">LINQ to XML axis</span></span>|<span data-ttu-id="03e5c-124">Szeregowanie</span><span class="sxs-lookup"><span data-stu-id="03e5c-124">Ordering</span></span>|  
|----------------------|--------------|  
|<span data-ttu-id="03e5c-125">XContainer.DescendantNodes</span><span class="sxs-lookup"><span data-stu-id="03e5c-125">XContainer.DescendantNodes</span></span>|<span data-ttu-id="03e5c-126">Kolejności dokumentu</span><span class="sxs-lookup"><span data-stu-id="03e5c-126">Document order</span></span>|  
|<span data-ttu-id="03e5c-127">XContainer.Descendants</span><span class="sxs-lookup"><span data-stu-id="03e5c-127">XContainer.Descendants</span></span>|<span data-ttu-id="03e5c-128">Kolejności dokumentu</span><span class="sxs-lookup"><span data-stu-id="03e5c-128">Document order</span></span>|  
|<span data-ttu-id="03e5c-129">XContainer.Elements</span><span class="sxs-lookup"><span data-stu-id="03e5c-129">XContainer.Elements</span></span>|<span data-ttu-id="03e5c-130">Kolejności dokumentu</span><span class="sxs-lookup"><span data-stu-id="03e5c-130">Document order</span></span>|  
|<span data-ttu-id="03e5c-131">XContainer.Nodes</span><span class="sxs-lookup"><span data-stu-id="03e5c-131">XContainer.Nodes</span></span>|<span data-ttu-id="03e5c-132">Kolejności dokumentu</span><span class="sxs-lookup"><span data-stu-id="03e5c-132">Document order</span></span>|  
|<span data-ttu-id="03e5c-133">XContainer.NodesAfterSelf</span><span class="sxs-lookup"><span data-stu-id="03e5c-133">XContainer.NodesAfterSelf</span></span>|<span data-ttu-id="03e5c-134">Kolejności dokumentu</span><span class="sxs-lookup"><span data-stu-id="03e5c-134">Document order</span></span>|  
|<span data-ttu-id="03e5c-135">XContainer.NodesBeforeSelf</span><span class="sxs-lookup"><span data-stu-id="03e5c-135">XContainer.NodesBeforeSelf</span></span>|<span data-ttu-id="03e5c-136">Kolejności dokumentu</span><span class="sxs-lookup"><span data-stu-id="03e5c-136">Document order</span></span>|  
|<span data-ttu-id="03e5c-137">XElement.AncestorsAndSelf</span><span class="sxs-lookup"><span data-stu-id="03e5c-137">XElement.AncestorsAndSelf</span></span>|<span data-ttu-id="03e5c-138">Kolejności odwrotnej dokumentu</span><span class="sxs-lookup"><span data-stu-id="03e5c-138">Reverse document order</span></span>|  
|<span data-ttu-id="03e5c-139">XElement.Attributes</span><span class="sxs-lookup"><span data-stu-id="03e5c-139">XElement.Attributes</span></span>|<span data-ttu-id="03e5c-140">Kolejności dokumentu</span><span class="sxs-lookup"><span data-stu-id="03e5c-140">Document order</span></span>|  
|<span data-ttu-id="03e5c-141">XElement.DescendantNodesAndSelf</span><span class="sxs-lookup"><span data-stu-id="03e5c-141">XElement.DescendantNodesAndSelf</span></span>|<span data-ttu-id="03e5c-142">Kolejności dokumentu</span><span class="sxs-lookup"><span data-stu-id="03e5c-142">Document order</span></span>|  
|<span data-ttu-id="03e5c-143">XElement.DescendantsAndSelf</span><span class="sxs-lookup"><span data-stu-id="03e5c-143">XElement.DescendantsAndSelf</span></span>|<span data-ttu-id="03e5c-144">Kolejności dokumentu</span><span class="sxs-lookup"><span data-stu-id="03e5c-144">Document order</span></span>|  
|<span data-ttu-id="03e5c-145">XNode.Ancestors</span><span class="sxs-lookup"><span data-stu-id="03e5c-145">XNode.Ancestors</span></span>|<span data-ttu-id="03e5c-146">Kolejności odwrotnej dokumentu</span><span class="sxs-lookup"><span data-stu-id="03e5c-146">Reverse document order</span></span>|  
|<span data-ttu-id="03e5c-147">XNode.ElementsAfterSelf</span><span class="sxs-lookup"><span data-stu-id="03e5c-147">XNode.ElementsAfterSelf</span></span>|<span data-ttu-id="03e5c-148">Kolejności dokumentu</span><span class="sxs-lookup"><span data-stu-id="03e5c-148">Document order</span></span>|  
|<span data-ttu-id="03e5c-149">XNode.ElementsBeforeSelf</span><span class="sxs-lookup"><span data-stu-id="03e5c-149">XNode.ElementsBeforeSelf</span></span>|<span data-ttu-id="03e5c-150">Kolejności dokumentu</span><span class="sxs-lookup"><span data-stu-id="03e5c-150">Document order</span></span>|  
|<span data-ttu-id="03e5c-151">XNode.NodesAfterSelf</span><span class="sxs-lookup"><span data-stu-id="03e5c-151">XNode.NodesAfterSelf</span></span>|<span data-ttu-id="03e5c-152">Kolejności dokumentu</span><span class="sxs-lookup"><span data-stu-id="03e5c-152">Document order</span></span>|  
|<span data-ttu-id="03e5c-153">XNode.NodesBeforeSelf</span><span class="sxs-lookup"><span data-stu-id="03e5c-153">XNode.NodesBeforeSelf</span></span>|<span data-ttu-id="03e5c-154">Kolejności dokumentu</span><span class="sxs-lookup"><span data-stu-id="03e5c-154">Document order</span></span>|  
  
## <a name="positional-predicates"></a><span data-ttu-id="03e5c-155">Predykaty pozycyjne</span><span class="sxs-lookup"><span data-stu-id="03e5c-155">Positional Predicates</span></span>  
 <span data-ttu-id="03e5c-156">W obrębie wyrażenia XPath predykaty pozycyjne są wyrażone w kolejności dokumentu dla wielu osi, ale są wyrażone w kolejności odwrotnej dokumentu dla odwrotnej osi, które są `preceding`, `preceding-sibling`, `ancestor`, i `ancestor-or-self`.</span><span class="sxs-lookup"><span data-stu-id="03e5c-156">Within an XPath expression, positional predicates are expressed in terms of document order for many axes, but are expressed in reverse document order for reverse axes, which are `preceding`, `preceding-sibling`, `ancestor`, and `ancestor-or-self`.</span></span> <span data-ttu-id="03e5c-157">Na przykład, wyrażenie XPath `preceding-sibling::*[1]` zwraca niezwłocznie poprzednich elementów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="03e5c-157">For example, the XPath expression `preceding-sibling::*[1]` returns the immediately preceding sibling.</span></span> <span data-ttu-id="03e5c-158">Dotyczy to nawet, jeśli zestaw wynik końcowy są prezentowane w kolejności dokumentu.</span><span class="sxs-lookup"><span data-stu-id="03e5c-158">This is the case even though the final result set is presented in document order.</span></span>  
  
 <span data-ttu-id="03e5c-159">Z drugiej strony wszystkich predykaty pozycyjne w składniku LINQ to XML zawsze są wyrażone w kolejności osi.</span><span class="sxs-lookup"><span data-stu-id="03e5c-159">By contrast, all positional predicates in LINQ to XML are always expressed in terms of the order of the axis.</span></span> <span data-ttu-id="03e5c-160">Na przykład `anElement.ElementsBeforeSelf().ElementAt(0)` zwraca pierwszy element podrzędny elementu nadrzędnego zapytanie o element, a nie bezpośrednio poprzednich elementów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="03e5c-160">For example, `anElement.ElementsBeforeSelf().ElementAt(0)` returns the first child element of the parent of the queried element, not the immediate preceding sibling.</span></span> <span data-ttu-id="03e5c-161">Inny przykład: `anElement.Ancestors().ElementAt(0)` zwraca element nadrzędny.</span><span class="sxs-lookup"><span data-stu-id="03e5c-161">Another example: `anElement.Ancestors().ElementAt(0)` returns the parent element.</span></span>  
  
 <span data-ttu-id="03e5c-162">Jeśli chcesz znaleźć bezpośrednio poprzedzający element w składniku LINQ to XML, należy napisać następujące wyrażenie:</span><span class="sxs-lookup"><span data-stu-id="03e5c-162">If you wanted to find the immediately preceding element in LINQ to XML, you would write the following expression:</span></span>  
  
```csharp
ElementsBeforeSelf().Last()
```
  
```vb
ElementsBeforeSelf().Last()
```
  
## <a name="performance-differences"></a><span data-ttu-id="03e5c-163">Różnice w wydajności</span><span class="sxs-lookup"><span data-stu-id="03e5c-163">Performance Differences</span></span>  
 <span data-ttu-id="03e5c-164">Kwerendy XPath, które używają funkcji XPath w składniku LINQ to XML nie wykona oraz LINQ do XML zapytań.</span><span class="sxs-lookup"><span data-stu-id="03e5c-164">XPath queries that use the XPath functionality in LINQ to XML will not perform as well as LINQ to XML queries.</span></span>  
  
## <a name="comparison-of-composition"></a><span data-ttu-id="03e5c-165">Porównanie kompozycji</span><span class="sxs-lookup"><span data-stu-id="03e5c-165">Comparison of Composition</span></span>  
 <span data-ttu-id="03e5c-166">Skład zapytaniu składnika LINQ to XML jest nieco zbliżony do składu wyrażenie XPath, mimo że jest to bardzo różne przy użyciu składni.</span><span class="sxs-lookup"><span data-stu-id="03e5c-166">Composition of a LINQ to XML query is somewhat parallel to composition of an XPath expression, although very different in syntax.</span></span>  
  
 <span data-ttu-id="03e5c-167">Na przykład, jeśli element w zmiennej o nazwie `customers`, i chcesz znaleźć element podwójnym o nazwie `CompanyName` w ramach wszystkich elementów podrzędnych o nazwie `Customer`, należy napisać wyrażenie XPath w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="03e5c-167">For example, if you have an element in a variable named `customers`, and you want to find a grandchild element named `CompanyName` under all child elements named `Customer`, you would write an XPath expression as follows:</span></span>  
  
```csharp  
customers.XPathSelectElements("./Customer/CompanyName")
```  
  
```vb
customers.XPathSelectElements("./Customer/CompanyName")
```

 <span data-ttu-id="03e5c-168">Jest równoważne zapytaniu składnika LINQ to XML:</span><span class="sxs-lookup"><span data-stu-id="03e5c-168">The equivalent LINQ to XML query is:</span></span>  
  
```csharp  
customers.Elements("Customer").Elements("CompanyName")
```  
  
```vb
customers.Elements("Customer").Elements("CompanyName")
```  

 <span data-ttu-id="03e5c-169">Istnieją podobne równoleżników dla każdej z osi XPath.</span><span class="sxs-lookup"><span data-stu-id="03e5c-169">There are similar parallels for each of the XPath axes.</span></span>  
  
|<span data-ttu-id="03e5c-170">Wyrażenie XPath osi</span><span class="sxs-lookup"><span data-stu-id="03e5c-170">XPath axis</span></span>|<span data-ttu-id="03e5c-171">LINQ do XML osi</span><span class="sxs-lookup"><span data-stu-id="03e5c-171">LINQ to XML axis</span></span>|  
|----------------|----------------------|  
|<span data-ttu-id="03e5c-172">podrzędne (oś domyślny)</span><span class="sxs-lookup"><span data-stu-id="03e5c-172">child (the default axis)</span></span>|<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="03e5c-173">Nadrzędny (.)</span><span class="sxs-lookup"><span data-stu-id="03e5c-173">Parent (..)</span></span>|<xref:System.Xml.Linq.XObject.Parent%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="03e5c-174">osi atrybutu (@)</span><span class="sxs-lookup"><span data-stu-id="03e5c-174">attribute axis (@)</span></span>|<xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="03e5c-175">lub</span><span class="sxs-lookup"><span data-stu-id="03e5c-175">or</span></span><br /><br /> <xref:System.Xml.Linq.XElement.Attributes%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="03e5c-176">osi nadrzędnym</span><span class="sxs-lookup"><span data-stu-id="03e5c-176">ancestor axis</span></span>|<xref:System.Xml.Linq.XNode.Ancestors%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="03e5c-177">osi nadrzędnym lub self</span><span class="sxs-lookup"><span data-stu-id="03e5c-177">ancestor-or-self axis</span></span>|<xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="03e5c-178">osi elementu podrzędnego (/ /)</span><span class="sxs-lookup"><span data-stu-id="03e5c-178">descendant axis (//)</span></span>|<xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="03e5c-179">lub</span><span class="sxs-lookup"><span data-stu-id="03e5c-179">or</span></span><br /><br /> <xref:System.Xml.Linq.XContainer.DescendantNodes%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="03e5c-180">descendant-or-self</span><span class="sxs-lookup"><span data-stu-id="03e5c-180">descendant-or-self</span></span>|<xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="03e5c-181">lub</span><span class="sxs-lookup"><span data-stu-id="03e5c-181">or</span></span><br /><br /> <xref:System.Xml.Linq.XElement.DescendantNodesAndSelf%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="03e5c-182">następujący element równorzędny</span><span class="sxs-lookup"><span data-stu-id="03e5c-182">following-sibling</span></span>|<xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="03e5c-183">lub</span><span class="sxs-lookup"><span data-stu-id="03e5c-183">or</span></span><br /><br /> <xref:System.Xml.Linq.XNode.NodesAfterSelf%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="03e5c-184">Poprzedni element równorzędny</span><span class="sxs-lookup"><span data-stu-id="03e5c-184">preceding-sibling</span></span>|<xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="03e5c-185">lub</span><span class="sxs-lookup"><span data-stu-id="03e5c-185">or</span></span><br /><br /> <xref:System.Xml.Linq.XNode.NodesBeforeSelf%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="03e5c-186">następujące</span><span class="sxs-lookup"><span data-stu-id="03e5c-186">following</span></span>|<span data-ttu-id="03e5c-187">Bezpośredniego odpowiednika.</span><span class="sxs-lookup"><span data-stu-id="03e5c-187">No direct equivalent.</span></span>|  
|<span data-ttu-id="03e5c-188">poprzedza</span><span class="sxs-lookup"><span data-stu-id="03e5c-188">preceding</span></span>|<span data-ttu-id="03e5c-189">Bezpośredniego odpowiednika.</span><span class="sxs-lookup"><span data-stu-id="03e5c-189">No direct equivalent.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="03e5c-190">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="03e5c-190">See Also</span></span>  
 [<span data-ttu-id="03e5c-191">LINQ to XML dla użytkowników metody XPath (C#)</span><span class="sxs-lookup"><span data-stu-id="03e5c-191">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
