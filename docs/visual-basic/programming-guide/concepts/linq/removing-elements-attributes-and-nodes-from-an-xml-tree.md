---
title: Usuwanie elementów, atrybutów i węzłów z drzewa XML
ms.date: 07/20/2015
ms.assetid: 5cf21919-4360-4b49-b29d-58ea3164ac72
ms.openlocfilehash: f8be7fe521fb3c2662b105e34fd96fea1d1ac6e7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413413"
---
# <a name="removing-elements-attributes-and-nodes-from-an-xml-tree-visual-basic"></a><span data-ttu-id="a44e7-102">Usuwanie elementów, atrybutów i węzłów z drzewa XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a44e7-102">Removing Elements, Attributes, and Nodes from an XML Tree (Visual Basic)</span></span>
<span data-ttu-id="a44e7-103">Można modyfikować drzewo XML, usuwać elementy, atrybuty i inne typy węzłów.</span><span class="sxs-lookup"><span data-stu-id="a44e7-103">You can modify an XML tree, removing elements, attributes, and other types of nodes.</span></span>  
  
 <span data-ttu-id="a44e7-104">Usuwanie pojedynczego elementu lub pojedynczego atrybutu z dokumentu XML jest proste.</span><span class="sxs-lookup"><span data-stu-id="a44e7-104">Removing a single element or a single attribute from an XML document is straightforward.</span></span> <span data-ttu-id="a44e7-105">Jednak podczas usuwania kolekcji elementów lub atrybutów należy najpierw zmaterializowania kolekcję do listy, a następnie usunąć elementy lub atrybuty z listy.</span><span class="sxs-lookup"><span data-stu-id="a44e7-105">However, when removing collections of elements or attributes, you should first materialize a collection into a list, and then delete the elements or attributes from the list.</span></span> <span data-ttu-id="a44e7-106">Najlepszym rozwiązaniem jest użycie <xref:System.Xml.Linq.Extensions.Remove%2A> metody rozszerzającej, która pozwoli Ci to zrobić.</span><span class="sxs-lookup"><span data-stu-id="a44e7-106">The best approach is to use the <xref:System.Xml.Linq.Extensions.Remove%2A> extension method, which will do this for you.</span></span>  
  
 <span data-ttu-id="a44e7-107">Głównym powodem tego jest to, że większość kolekcji pobieranych z drzewa XML jest przeprowadzana przy użyciu odroczonego wykonania.</span><span class="sxs-lookup"><span data-stu-id="a44e7-107">The main reason for doing this is that most of the collections you retrieve from an XML tree are yielded using deferred execution.</span></span> <span data-ttu-id="a44e7-108">Jeśli nie chcesz najpierw zmaterializowania ich do listy lub jeśli nie korzystasz z metod rozszerzenia, możliwe jest napotkanie pewnej klasy błędów.</span><span class="sxs-lookup"><span data-stu-id="a44e7-108">If you do not first materialize them into a list, or if you do not use the extension methods, it is possible to encounter a certain class of bugs.</span></span> <span data-ttu-id="a44e7-109">Aby uzyskać więcej informacji, zobacz [mieszany kod deklaratywny/niezbędny kod (LINQ to XML) (Visual Basic)](mixed-declarative-code-imperative-code-bugs-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="a44e7-109">For more information, see [Mixed Declarative Code/Imperative Code Bugs (LINQ to XML) (Visual Basic)](mixed-declarative-code-imperative-code-bugs-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="a44e7-110">Poniższe metody usuwają węzły i atrybuty z drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="a44e7-110">The following methods remove nodes and attributes from an XML tree.</span></span>  
  
|<span data-ttu-id="a44e7-111">Metoda</span><span class="sxs-lookup"><span data-stu-id="a44e7-111">Method</span></span>|<span data-ttu-id="a44e7-112">Opis</span><span class="sxs-lookup"><span data-stu-id="a44e7-112">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="a44e7-113">Usuwa <xref:System.Xml.Linq.XAttribute> z elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="a44e7-113">Removes an <xref:System.Xml.Linq.XAttribute> from its parent.</span></span>|  
|<xref:System.Xml.Linq.XContainer.RemoveNodes%2A?displayProperty=nameWithType>|<span data-ttu-id="a44e7-114">Usuwa węzły podrzędne z <xref:System.Xml.Linq.XContainer> .</span><span class="sxs-lookup"><span data-stu-id="a44e7-114">Removes the child nodes from an <xref:System.Xml.Linq.XContainer>.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|<span data-ttu-id="a44e7-115">Usuwa zawartość i atrybuty z <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="a44e7-115">Removes content and attributes from an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="a44e7-116">Usuwa atrybuty <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="a44e7-116">Removes the attributes of an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|<span data-ttu-id="a44e7-117">W przypadku przekazania `null` wartości, a następnie usunięcie atrybutu.</span><span class="sxs-lookup"><span data-stu-id="a44e7-117">If you pass `null` for value, then removes the attribute.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|<span data-ttu-id="a44e7-118">Jeśli zostanie przekazany `null` do wartości, spowoduje to usunięcie elementu podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="a44e7-118">If you pass `null` for value, then removes the child element.</span></span>|  
|<xref:System.Xml.Linq.XNode.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="a44e7-119">Usuwa <xref:System.Xml.Linq.XNode> z elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="a44e7-119">Removes an <xref:System.Xml.Linq.XNode> from its parent.</span></span>|  
|<xref:System.Xml.Linq.Extensions.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="a44e7-120">Usuwa każdy atrybut lub element z kolekcji źródłowej z jego elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="a44e7-120">Removes every attribute or element in the source collection from its parent element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a44e7-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="a44e7-121">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="a44e7-122">Opis</span><span class="sxs-lookup"><span data-stu-id="a44e7-122">Description</span></span>  
 <span data-ttu-id="a44e7-123">Ten przykład ilustruje trzy podejścia do usuwania elementów.</span><span class="sxs-lookup"><span data-stu-id="a44e7-123">This example demonstrates three approaches to removing elements.</span></span> <span data-ttu-id="a44e7-124">Najpierw usuwa pojedynczy element.</span><span class="sxs-lookup"><span data-stu-id="a44e7-124">First, it removes a single element.</span></span> <span data-ttu-id="a44e7-125">Po drugie Pobiera kolekcję elementów, materializuje je przy użyciu <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> operatora i usuwa kolekcję.</span><span class="sxs-lookup"><span data-stu-id="a44e7-125">Second, it retrieves a collection of elements, materializes them using the <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> operator, and removes the collection.</span></span> <span data-ttu-id="a44e7-126">Na koniec Pobiera kolekcję elementów i usuwa je za pomocą <xref:System.Xml.Linq.Extensions.Remove%2A> metody rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="a44e7-126">Finally, it retrieves a collection of elements and removes them using the <xref:System.Xml.Linq.Extensions.Remove%2A> extension method.</span></span>  
  
 <span data-ttu-id="a44e7-127">Aby uzyskać więcej informacji na temat <xref:System.Linq.Enumerable.ToList%2A> operatora, zobacz [konwertowanie typów danych (Visual Basic)](converting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="a44e7-127">For more information on the <xref:System.Linq.Enumerable.ToList%2A> operator, see [Converting Data Types (Visual Basic)](converting-data-types.md).</span></span>  
  
### <a name="code"></a><span data-ttu-id="a44e7-128">Kod</span><span class="sxs-lookup"><span data-stu-id="a44e7-128">Code</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <Child1>  
            <GrandChild1/>  
            <GrandChild2/>  
            <GrandChild3/>  
        </Child1>  
        <Child2>  
            <GrandChild4/>  
            <GrandChild5/>  
            <GrandChild6/>  
        </Child2>  
        <Child3>  
            <GrandChild7/>  
            <GrandChild8/>  
            <GrandChild9/>  
        </Child3>  
    </Root>  
root.<Child1>.<GrandChild1>.Remove()  
root.<Child2>.Elements().ToList().Remove()  
root.<Child3>.Elements().Remove()  
Console.WriteLine(root)  
```  
  
### <a name="comments"></a><span data-ttu-id="a44e7-129">Komentarze</span><span class="sxs-lookup"><span data-stu-id="a44e7-129">Comments</span></span>  
 <span data-ttu-id="a44e7-130">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="a44e7-130">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child1>  
    <GrandChild2 />  
    <GrandChild3 />  
  </Child1>  
  <Child2 />  
  <Child3 />  
</Root>  
```  
  
 <span data-ttu-id="a44e7-131">Zwróć uwagę, że pierwszy element grandchild został usunięty z `Child1` .</span><span class="sxs-lookup"><span data-stu-id="a44e7-131">Notice that the first grandchild element has been removed from `Child1`.</span></span> <span data-ttu-id="a44e7-132">Wszystkie elementy podrzędne zostały usunięte z `Child2` i z `Child3` .</span><span class="sxs-lookup"><span data-stu-id="a44e7-132">All grandchildren elements have been removed from `Child2` and from `Child3`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a44e7-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a44e7-133">See also</span></span>

- [<span data-ttu-id="a44e7-134">Modyfikowanie drzew XML (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a44e7-134">Modifying XML Trees (LINQ to XML) (Visual Basic)</span></span>](modifying-xml-trees-linq-to-xml.md)
