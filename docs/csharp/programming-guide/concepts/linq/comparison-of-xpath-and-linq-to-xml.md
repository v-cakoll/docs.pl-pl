---
title: Porównanie metody XPath i LINQ to XML
description: Dowiedz się więcej o podobieństwach i różnicach w działaniu między XPath i LINQ to XML w języku C#. Można użyć obu tych metod do wykonywania zapytań w drzewie XML.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 87d361b1-daa9-4fd4-a53a-cbfa40111ad3
ms.openlocfilehash: e2f34903b20a53dea6e5ff4858d4fadaebd9c37a
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104001"
---
# <a name="comparison-of-xpath-and-linq-to-xml"></a><span data-ttu-id="fbd53-104">Porównanie metody XPath i LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="fbd53-104">Comparison of XPath and LINQ to XML</span></span>
<span data-ttu-id="fbd53-105">Wyrażenia XPath i LINQ to XML oferują pewne podobne funkcje.</span><span class="sxs-lookup"><span data-stu-id="fbd53-105">XPath and LINQ to XML offer some similar functionality.</span></span> <span data-ttu-id="fbd53-106">Oba te funkcje mogą służyć do wykonywania zapytań w drzewie XML, zwracając takie wyniki jako kolekcja elementów, Kolekcja atrybutów, kolekcja węzłów lub wartość elementu lub atrybutu.</span><span class="sxs-lookup"><span data-stu-id="fbd53-106">Both can be used to query an XML tree, returning such results as a collection of elements, a collection of attributes, a collection of nodes, or the value of an element or attribute.</span></span> <span data-ttu-id="fbd53-107">Istnieją jednak również pewne różnice.</span><span class="sxs-lookup"><span data-stu-id="fbd53-107">However, there are also some differences.</span></span>  
  
## <a name="differences-between-xpath-and-linq-to-xml"></a><span data-ttu-id="fbd53-108">Różnice między XPath i LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="fbd53-108">Differences Between XPath and LINQ to XML</span></span>  
 <span data-ttu-id="fbd53-109">Wyrażenie XPath nie zezwala na projekcję nowych typów.</span><span class="sxs-lookup"><span data-stu-id="fbd53-109">XPath does not allow projection of new types.</span></span> <span data-ttu-id="fbd53-110">Można zwrócić kolekcje węzłów tylko z drzewa, podczas gdy LINQ to XML może wykonać zapytanie i projektować obiekt Graph lub drzewo XML w nowym kształcie.</span><span class="sxs-lookup"><span data-stu-id="fbd53-110">It can only return collections of nodes from the tree, whereas LINQ to XML can execute a query and project an object graph or an XML tree in a new shape.</span></span> <span data-ttu-id="fbd53-111">Zapytania LINQ to XML obejmują znacznie większą funkcjonalność i są znacznie bardziej wydajne niż wyrażenia XPath.</span><span class="sxs-lookup"><span data-stu-id="fbd53-111">LINQ to XML queries encompass much more functionality and are much more powerful than XPath expressions.</span></span>  
  
 <span data-ttu-id="fbd53-112">Wyrażenia XPath istnieją w izolacji w ciągu.</span><span class="sxs-lookup"><span data-stu-id="fbd53-112">XPath expressions exist in isolation within a string.</span></span> <span data-ttu-id="fbd53-113">Kompilator języka C# nie może pomóc w analizie wyrażenia XPath w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="fbd53-113">The C# compiler cannot help parse the XPath expression at compile time.</span></span> <span data-ttu-id="fbd53-114">Z kolei LINQ to XML zapytania są analizowane i kompilowane przez kompilator języka C#.</span><span class="sxs-lookup"><span data-stu-id="fbd53-114">By contrast, LINQ to XML queries are parsed and compiled by the C# compiler.</span></span> <span data-ttu-id="fbd53-115">Kompilator może przechwycić wiele błędów zapytań.</span><span class="sxs-lookup"><span data-stu-id="fbd53-115">The compiler is able to catch many query errors.</span></span>  
  
 <span data-ttu-id="fbd53-116">Wyniki XPath nie są jednoznacznie wpisane.</span><span class="sxs-lookup"><span data-stu-id="fbd53-116">XPath results are not strongly typed.</span></span> <span data-ttu-id="fbd53-117">W wielu okolicznościach wynik oceny wyrażenia XPath jest obiektem, a programista może określić właściwy typ i rzutować wynik odpowiednio do potrzeb.</span><span class="sxs-lookup"><span data-stu-id="fbd53-117">In a number of circumstances, the result of evaluating an XPath expression is an object, and it is up to the developer to determine the proper type and cast the result as necessary.</span></span> <span data-ttu-id="fbd53-118">Z kolei, projekcje z kwerendy LINQ to XML są jednoznacznie wpisane.</span><span class="sxs-lookup"><span data-stu-id="fbd53-118">By contrast, the projections from a LINQ to XML query are strongly typed.</span></span>  
  
## <a name="result-ordering"></a><span data-ttu-id="fbd53-119">Porządkowanie wyników</span><span class="sxs-lookup"><span data-stu-id="fbd53-119">Result Ordering</span></span>  
 <span data-ttu-id="fbd53-120">Zalecenie XPath 1,0 stwierdza, że kolekcja będąca wynikiem oceny wyrażenia XPath jest nieuporządkowana.</span><span class="sxs-lookup"><span data-stu-id="fbd53-120">The XPath 1.0 Recommendation states that a collection that is the result of evaluating an XPath expression is unordered.</span></span>  
  
 <span data-ttu-id="fbd53-121">Jednak podczas iteracji w kolekcji zwróconej przez LINQ to XML metodę osi XPath węzły w kolekcji są zwracane w kolejności dokumentu.</span><span class="sxs-lookup"><span data-stu-id="fbd53-121">However, when iterating through a collection returned by a LINQ to XML XPath axis method, the nodes in the collection are returned in document order.</span></span> <span data-ttu-id="fbd53-122">Jest to przypadek, nawet w przypadku uzyskiwania dostępu do osi XPath, gdzie predykaty są wyrażane w postaci odwrotnej kolejności dokumentu, takiej jak `preceding` i `preceding-sibling` .</span><span class="sxs-lookup"><span data-stu-id="fbd53-122">This is the case even when accessing the XPath axes where predicates are expressed in terms of reverse document order, such as `preceding` and `preceding-sibling`.</span></span>  
  
 <span data-ttu-id="fbd53-123">Z kolei większość osi LINQ to XML zwraca kolekcje w kolejności dokumentu, ale dwa z nich, <xref:System.Xml.Linq.XNode.Ancestors%2A> a następnie <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A> zwraca kolekcje w odwrotnej kolejności dokumentu.</span><span class="sxs-lookup"><span data-stu-id="fbd53-123">By contrast, most of the LINQ to XML axes return collections in document order, but two of them, <xref:System.Xml.Linq.XNode.Ancestors%2A> and <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>, return collections in reverse document order.</span></span> <span data-ttu-id="fbd53-124">Poniższa tabela zawiera Wyliczenie osi i wskazuje kolejność zbierania dla każdej z nich:</span><span class="sxs-lookup"><span data-stu-id="fbd53-124">The following table enumerates the axes, and indicates collection order for each:</span></span>  
  
|<span data-ttu-id="fbd53-125">Oś LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="fbd53-125">LINQ to XML axis</span></span>|<span data-ttu-id="fbd53-126">Szeregowanie</span><span class="sxs-lookup"><span data-stu-id="fbd53-126">Ordering</span></span>|  
|----------------------|--------------|  
|<span data-ttu-id="fbd53-127">XContainer.DescendantNodes</span><span class="sxs-lookup"><span data-stu-id="fbd53-127">XContainer.DescendantNodes</span></span>|<span data-ttu-id="fbd53-128">Kolejność dokumentów</span><span class="sxs-lookup"><span data-stu-id="fbd53-128">Document order</span></span>|  
|<span data-ttu-id="fbd53-129">XContainer. Descendants</span><span class="sxs-lookup"><span data-stu-id="fbd53-129">XContainer.Descendants</span></span>|<span data-ttu-id="fbd53-130">Kolejność dokumentów</span><span class="sxs-lookup"><span data-stu-id="fbd53-130">Document order</span></span>|  
|<span data-ttu-id="fbd53-131">XContainer. elementy</span><span class="sxs-lookup"><span data-stu-id="fbd53-131">XContainer.Elements</span></span>|<span data-ttu-id="fbd53-132">Kolejność dokumentów</span><span class="sxs-lookup"><span data-stu-id="fbd53-132">Document order</span></span>|  
|<span data-ttu-id="fbd53-133">XContainer. węzły</span><span class="sxs-lookup"><span data-stu-id="fbd53-133">XContainer.Nodes</span></span>|<span data-ttu-id="fbd53-134">Kolejność dokumentów</span><span class="sxs-lookup"><span data-stu-id="fbd53-134">Document order</span></span>|  
|<span data-ttu-id="fbd53-135">XContainer.NodesAfterSelf</span><span class="sxs-lookup"><span data-stu-id="fbd53-135">XContainer.NodesAfterSelf</span></span>|<span data-ttu-id="fbd53-136">Kolejność dokumentów</span><span class="sxs-lookup"><span data-stu-id="fbd53-136">Document order</span></span>|  
|<span data-ttu-id="fbd53-137">XContainer.NodesBeforeSelf</span><span class="sxs-lookup"><span data-stu-id="fbd53-137">XContainer.NodesBeforeSelf</span></span>|<span data-ttu-id="fbd53-138">Kolejność dokumentów</span><span class="sxs-lookup"><span data-stu-id="fbd53-138">Document order</span></span>|  
|<span data-ttu-id="fbd53-139">XElement. AncestorsAndSelf</span><span class="sxs-lookup"><span data-stu-id="fbd53-139">XElement.AncestorsAndSelf</span></span>|<span data-ttu-id="fbd53-140">Zamówienie odwrócenia dokumentu</span><span class="sxs-lookup"><span data-stu-id="fbd53-140">Reverse document order</span></span>|  
|<span data-ttu-id="fbd53-141">XElement. Attributes</span><span class="sxs-lookup"><span data-stu-id="fbd53-141">XElement.Attributes</span></span>|<span data-ttu-id="fbd53-142">Kolejność dokumentów</span><span class="sxs-lookup"><span data-stu-id="fbd53-142">Document order</span></span>|  
|<span data-ttu-id="fbd53-143">XElement. DescendantNodesAndSelf</span><span class="sxs-lookup"><span data-stu-id="fbd53-143">XElement.DescendantNodesAndSelf</span></span>|<span data-ttu-id="fbd53-144">Kolejność dokumentów</span><span class="sxs-lookup"><span data-stu-id="fbd53-144">Document order</span></span>|  
|<span data-ttu-id="fbd53-145">XElement. DescendantsAndSelf</span><span class="sxs-lookup"><span data-stu-id="fbd53-145">XElement.DescendantsAndSelf</span></span>|<span data-ttu-id="fbd53-146">Kolejność dokumentów</span><span class="sxs-lookup"><span data-stu-id="fbd53-146">Document order</span></span>|  
|<span data-ttu-id="fbd53-147">XNode. przodków</span><span class="sxs-lookup"><span data-stu-id="fbd53-147">XNode.Ancestors</span></span>|<span data-ttu-id="fbd53-148">Zamówienie odwrócenia dokumentu</span><span class="sxs-lookup"><span data-stu-id="fbd53-148">Reverse document order</span></span>|  
|<span data-ttu-id="fbd53-149">XNode.ElementsAfterSelf</span><span class="sxs-lookup"><span data-stu-id="fbd53-149">XNode.ElementsAfterSelf</span></span>|<span data-ttu-id="fbd53-150">Kolejność dokumentów</span><span class="sxs-lookup"><span data-stu-id="fbd53-150">Document order</span></span>|  
|<span data-ttu-id="fbd53-151">XNode.ElementsBeforeSelf</span><span class="sxs-lookup"><span data-stu-id="fbd53-151">XNode.ElementsBeforeSelf</span></span>|<span data-ttu-id="fbd53-152">Kolejność dokumentów</span><span class="sxs-lookup"><span data-stu-id="fbd53-152">Document order</span></span>|  
|<span data-ttu-id="fbd53-153">XNode.NodesAfterSelf</span><span class="sxs-lookup"><span data-stu-id="fbd53-153">XNode.NodesAfterSelf</span></span>|<span data-ttu-id="fbd53-154">Kolejność dokumentów</span><span class="sxs-lookup"><span data-stu-id="fbd53-154">Document order</span></span>|  
|<span data-ttu-id="fbd53-155">XNode.NodesBeforeSelf</span><span class="sxs-lookup"><span data-stu-id="fbd53-155">XNode.NodesBeforeSelf</span></span>|<span data-ttu-id="fbd53-156">Kolejność dokumentów</span><span class="sxs-lookup"><span data-stu-id="fbd53-156">Document order</span></span>|  
  
## <a name="positional-predicates"></a><span data-ttu-id="fbd53-157">Predykaty pozycyjne</span><span class="sxs-lookup"><span data-stu-id="fbd53-157">Positional Predicates</span></span>  
 <span data-ttu-id="fbd53-158">W wyrażeniu XPath predykaty pozycyjne są wyrażane w zakresie kolejności dokumentu dla wielu osi, ale są wyrażane w kolejności odwrotnego dokumentu dla odwróconych osi, które są `preceding` ,, `preceding-sibling` `ancestor` , i `ancestor-or-self` .</span><span class="sxs-lookup"><span data-stu-id="fbd53-158">Within an XPath expression, positional predicates are expressed in terms of document order for many axes, but are expressed in reverse document order for reverse axes, which are `preceding`, `preceding-sibling`, `ancestor`, and `ancestor-or-self`.</span></span> <span data-ttu-id="fbd53-159">Na przykład wyrażenie XPath `preceding-sibling::*[1]` zwraca bezpośrednio poprzedni element równorzędny.</span><span class="sxs-lookup"><span data-stu-id="fbd53-159">For example, the XPath expression `preceding-sibling::*[1]` returns the immediately preceding sibling.</span></span> <span data-ttu-id="fbd53-160">Dzieje się tak, mimo że końcowy zestaw wyników jest przedstawiony w kolejności dokumentu.</span><span class="sxs-lookup"><span data-stu-id="fbd53-160">This is the case even though the final result set is presented in document order.</span></span>  
  
 <span data-ttu-id="fbd53-161">Z kolei wszystkie predykaty pozycyjne w LINQ to XML są zawsze wyrażane w warunkach kolejności osi.</span><span class="sxs-lookup"><span data-stu-id="fbd53-161">By contrast, all positional predicates in LINQ to XML are always expressed in terms of the order of the axis.</span></span> <span data-ttu-id="fbd53-162">Na przykład `anElement.ElementsBeforeSelf().ElementAt(0)` zwraca pierwszy element podrzędny obiektu nadrzędnego z zapytania elementu, a nie bezpośrednio poprzedzającego element równorzędny.</span><span class="sxs-lookup"><span data-stu-id="fbd53-162">For example, `anElement.ElementsBeforeSelf().ElementAt(0)` returns the first child element of the parent of the queried element, not the immediate preceding sibling.</span></span> <span data-ttu-id="fbd53-163">Inny przykład: `anElement.Ancestors().ElementAt(0)` zwraca element nadrzędny.</span><span class="sxs-lookup"><span data-stu-id="fbd53-163">Another example: `anElement.Ancestors().ElementAt(0)` returns the parent element.</span></span>  
  
 <span data-ttu-id="fbd53-164">Aby znaleźć bezpośrednio poprzedzający element w LINQ to XML, należy napisać następujące wyrażenie:</span><span class="sxs-lookup"><span data-stu-id="fbd53-164">If you wanted to find the immediately preceding element in LINQ to XML, you would write the following expression:</span></span>  
  
```csharp
ElementsBeforeSelf().Last()
```
  
```vb
ElementsBeforeSelf().Last()
```
  
## <a name="performance-differences"></a><span data-ttu-id="fbd53-165">Różnice w wydajności</span><span class="sxs-lookup"><span data-stu-id="fbd53-165">Performance Differences</span></span>  
 <span data-ttu-id="fbd53-166">Zapytania XPath korzystające z funkcji XPath w LINQ to XML nie będą wykonywać ani LINQ to XML zapytań.</span><span class="sxs-lookup"><span data-stu-id="fbd53-166">XPath queries that use the XPath functionality in LINQ to XML will not perform as well as LINQ to XML queries.</span></span>  
  
## <a name="comparison-of-composition"></a><span data-ttu-id="fbd53-167">Porównanie kompozycji</span><span class="sxs-lookup"><span data-stu-id="fbd53-167">Comparison of Composition</span></span>  
 <span data-ttu-id="fbd53-168">Kompozycja LINQ to XMLego zapytania jest nieco równoległa do kompozycji wyrażenia XPath, chociaż różni się w składni.</span><span class="sxs-lookup"><span data-stu-id="fbd53-168">Composition of a LINQ to XML query is somewhat parallel to composition of an XPath expression, although very different in syntax.</span></span>  
  
 <span data-ttu-id="fbd53-169">Na przykład jeśli masz element w zmiennej o nazwie `customers` i chcesz znaleźć element grandchild o nazwie `CompanyName` pod wszystkimi elementami podrzędnymi o nazwie `Customer` , Zapisz wyrażenie XPath w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="fbd53-169">For example, if you have an element in a variable named `customers`, and you want to find a grandchild element named `CompanyName` under all child elements named `Customer`, you would write an XPath expression as follows:</span></span>  
  
```csharp  
customers.XPathSelectElements("./Customer/CompanyName")
```  
  
```vb
customers.XPathSelectElements("./Customer/CompanyName")
```

 <span data-ttu-id="fbd53-170">Odpowiednik kwerendy LINQ to XML jest:</span><span class="sxs-lookup"><span data-stu-id="fbd53-170">The equivalent LINQ to XML query is:</span></span>  
  
```csharp  
customers.Elements("Customer").Elements("CompanyName")
```  
  
```vb
customers.Elements("Customer").Elements("CompanyName")
```  

 <span data-ttu-id="fbd53-171">Istnieją podobne równoległości dla każdej z osi XPath.</span><span class="sxs-lookup"><span data-stu-id="fbd53-171">There are similar parallels for each of the XPath axes.</span></span>  
  
|<span data-ttu-id="fbd53-172">Oś XPath</span><span class="sxs-lookup"><span data-stu-id="fbd53-172">XPath axis</span></span>|<span data-ttu-id="fbd53-173">Oś LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="fbd53-173">LINQ to XML axis</span></span>|  
|----------------|----------------------|  
|<span data-ttu-id="fbd53-174">element podrzędny (oś domyślna)</span><span class="sxs-lookup"><span data-stu-id="fbd53-174">child (the default axis)</span></span>|<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="fbd53-175">Nadrzędne (..)</span><span class="sxs-lookup"><span data-stu-id="fbd53-175">Parent (..)</span></span>|<xref:System.Xml.Linq.XObject.Parent%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="fbd53-176">oś atrybutów (@)</span><span class="sxs-lookup"><span data-stu-id="fbd53-176">attribute axis (@)</span></span>|<xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="fbd53-177">lub</span><span class="sxs-lookup"><span data-stu-id="fbd53-177">or</span></span><br /><br /> <xref:System.Xml.Linq.XElement.Attributes%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="fbd53-178">oś nadrzędna</span><span class="sxs-lookup"><span data-stu-id="fbd53-178">ancestor axis</span></span>|<xref:System.Xml.Linq.XNode.Ancestors%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="fbd53-179">obiekt nadrzędny lub samosamej osi</span><span class="sxs-lookup"><span data-stu-id="fbd53-179">ancestor-or-self axis</span></span>|<xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="fbd53-180">oś elementu podrzędnego (//)</span><span class="sxs-lookup"><span data-stu-id="fbd53-180">descendant axis (//)</span></span>|<xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="fbd53-181">lub</span><span class="sxs-lookup"><span data-stu-id="fbd53-181">or</span></span><br /><br /> <xref:System.Xml.Linq.XContainer.DescendantNodes%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="fbd53-182">elementy podrzędne lub samodzielne</span><span class="sxs-lookup"><span data-stu-id="fbd53-182">descendant-or-self</span></span>|<xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="fbd53-183">lub</span><span class="sxs-lookup"><span data-stu-id="fbd53-183">or</span></span><br /><br /> <xref:System.Xml.Linq.XElement.DescendantNodesAndSelf%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="fbd53-184">poniżej — element równorzędny</span><span class="sxs-lookup"><span data-stu-id="fbd53-184">following-sibling</span></span>|<xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="fbd53-185">lub</span><span class="sxs-lookup"><span data-stu-id="fbd53-185">or</span></span><br /><br /> <xref:System.Xml.Linq.XNode.NodesAfterSelf%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="fbd53-186">Poprzedni element równorzędny</span><span class="sxs-lookup"><span data-stu-id="fbd53-186">preceding-sibling</span></span>|<xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="fbd53-187">lub</span><span class="sxs-lookup"><span data-stu-id="fbd53-187">or</span></span><br /><br /> <xref:System.Xml.Linq.XNode.NodesBeforeSelf%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="fbd53-188">dodaje</span><span class="sxs-lookup"><span data-stu-id="fbd53-188">following</span></span>|<span data-ttu-id="fbd53-189">Brak bezpośredniego odpowiednika.</span><span class="sxs-lookup"><span data-stu-id="fbd53-189">No direct equivalent.</span></span>|  
|<span data-ttu-id="fbd53-190">licencyjn</span><span class="sxs-lookup"><span data-stu-id="fbd53-190">preceding</span></span>|<span data-ttu-id="fbd53-191">Brak bezpośredniego odpowiednika.</span><span class="sxs-lookup"><span data-stu-id="fbd53-191">No direct equivalent.</span></span>|  
  