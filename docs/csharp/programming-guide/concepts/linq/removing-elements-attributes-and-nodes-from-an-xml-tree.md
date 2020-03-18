---
title: Usuwanie elementów, atrybutów i węzłów z drzewa XML (C#)
ms.date: 07/20/2015
ms.assetid: 07dd06d6-1117-4077-bf98-9120cf51176e
ms.openlocfilehash: badaa6bab35367d62a73f56c5221cb7d6d4a45f7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "69591261"
---
# <a name="removing-elements-attributes-and-nodes-from-an-xml-tree-c"></a><span data-ttu-id="6a03e-102">Usuwanie elementów, atrybutów i węzłów z drzewa XML (C#)</span><span class="sxs-lookup"><span data-stu-id="6a03e-102">Removing Elements, Attributes, and Nodes from an XML Tree (C#)</span></span>

<span data-ttu-id="6a03e-103">Można zmodyfikować drzewo XML, usuwając elementy, atrybuty i inne typy węzłów.</span><span class="sxs-lookup"><span data-stu-id="6a03e-103">You can modify an XML tree, removing elements, attributes, and other types of nodes.</span></span>

<span data-ttu-id="6a03e-104">Usuwanie pojedynczego elementu lub pojedynczego atrybutu z dokumentu XML jest proste.</span><span class="sxs-lookup"><span data-stu-id="6a03e-104">Removing a single element or a single attribute from an XML document is straightforward.</span></span> <span data-ttu-id="6a03e-105">Jednak podczas usuwania kolekcji elementów lub atrybutów, należy najpierw materializować kolekcji do listy, a następnie usunąć elementy lub atrybuty z listy.</span><span class="sxs-lookup"><span data-stu-id="6a03e-105">However, when removing collections of elements or attributes, you should first materialize a collection into a list, and then delete the elements or attributes from the list.</span></span> <span data-ttu-id="6a03e-106">Najlepszym rozwiązaniem jest użycie <xref:System.Xml.Linq.Extensions.Remove%2A> metody rozszerzenia, która zrobi to za Ciebie.</span><span class="sxs-lookup"><span data-stu-id="6a03e-106">The best approach is to use the <xref:System.Xml.Linq.Extensions.Remove%2A> extension method, which will do this for you.</span></span>

<span data-ttu-id="6a03e-107">Głównym powodem tego jest to, że większość kolekcji, które można pobrać z drzewa XML są uzyskują przy użyciu odroczonego wykonania.</span><span class="sxs-lookup"><span data-stu-id="6a03e-107">The main reason for doing this is that most of the collections you retrieve from an XML tree are yielded using deferred execution.</span></span> <span data-ttu-id="6a03e-108">Jeśli najpierw nie zmaterializujesz ich na liście lub jeśli nie użyjesz metod rozszerzenia, można napotkać pewną klasę błędów.</span><span class="sxs-lookup"><span data-stu-id="6a03e-108">If you do not first materialize them into a list, or if you do not use the extension methods, it is possible to encounter a certain class of bugs.</span></span> <span data-ttu-id="6a03e-109">Aby uzyskać więcej informacji, zobacz [Mixed Declarative Code/Imperative Code Bugs (LINQ to XML) (C#)](./mixed-declarative-code-imperative-code-bugs-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="6a03e-109">For more information, see [Mixed Declarative Code/Imperative Code Bugs (LINQ to XML) (C#)](./mixed-declarative-code-imperative-code-bugs-linq-to-xml.md).</span></span>

<span data-ttu-id="6a03e-110">Następujące metody usuwają węzły i atrybuty z drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="6a03e-110">The following methods remove nodes and attributes from an XML tree.</span></span>

|<span data-ttu-id="6a03e-111">Metoda</span><span class="sxs-lookup"><span data-stu-id="6a03e-111">Method</span></span>|<span data-ttu-id="6a03e-112">Opis</span><span class="sxs-lookup"><span data-stu-id="6a03e-112">Description</span></span>|
|------------|-----------------|
|<xref:System.Xml.Linq.XAttribute.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="6a03e-113">Usuwa element <xref:System.Xml.Linq.XAttribute> nadrzędny.</span><span class="sxs-lookup"><span data-stu-id="6a03e-113">Removes an <xref:System.Xml.Linq.XAttribute> from its parent.</span></span>|
|<xref:System.Xml.Linq.XContainer.RemoveNodes%2A?displayProperty=nameWithType>|<span data-ttu-id="6a03e-114">Usuwa węzły podrzędne <xref:System.Xml.Linq.XContainer>z pliku .</span><span class="sxs-lookup"><span data-stu-id="6a03e-114">Removes the child nodes from an <xref:System.Xml.Linq.XContainer>.</span></span>|
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|<span data-ttu-id="6a03e-115">Usuwa zawartość i atrybuty <xref:System.Xml.Linq.XElement>z pliku .</span><span class="sxs-lookup"><span data-stu-id="6a03e-115">Removes content and attributes from an <xref:System.Xml.Linq.XElement>.</span></span>|
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="6a03e-116">Usuwa atrybuty pliku <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="6a03e-116">Removes the attributes of an <xref:System.Xml.Linq.XElement>.</span></span>|
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|<span data-ttu-id="6a03e-117">Jeśli przekażesz `null` wartość, a następnie usuwa atrybut.</span><span class="sxs-lookup"><span data-stu-id="6a03e-117">If you pass `null` for value, then removes the attribute.</span></span>|
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|<span data-ttu-id="6a03e-118">Jeśli przejdziesz `null` dla wartości, a następnie usuwa element podrzędny.</span><span class="sxs-lookup"><span data-stu-id="6a03e-118">If you pass `null` for value, then removes the child element.</span></span>|
|<xref:System.Xml.Linq.XNode.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="6a03e-119">Usuwa element <xref:System.Xml.Linq.XNode> nadrzędny.</span><span class="sxs-lookup"><span data-stu-id="6a03e-119">Removes an <xref:System.Xml.Linq.XNode> from its parent.</span></span>|
|<xref:System.Xml.Linq.Extensions.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="6a03e-120">Usuwa każdy atrybut lub element w kolekcji źródłowej z jego elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="6a03e-120">Removes every attribute or element in the source collection from its parent element.</span></span>|

## <a name="example"></a><span data-ttu-id="6a03e-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="6a03e-121">Example</span></span>

### <a name="description"></a><span data-ttu-id="6a03e-122">Opis</span><span class="sxs-lookup"><span data-stu-id="6a03e-122">Description</span></span>

<span data-ttu-id="6a03e-123">W tym przykładzie przedstawiono trzy podejścia do usuwania elementów.</span><span class="sxs-lookup"><span data-stu-id="6a03e-123">This example demonstrates three approaches to removing elements.</span></span> <span data-ttu-id="6a03e-124">Po pierwsze usuwa pojedynczy element.</span><span class="sxs-lookup"><span data-stu-id="6a03e-124">First, it removes a single element.</span></span> <span data-ttu-id="6a03e-125">Po drugie pobiera kolekcję elementów, materializuje je <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> za pomocą operatora i usuwa kolekcję.</span><span class="sxs-lookup"><span data-stu-id="6a03e-125">Second, it retrieves a collection of elements, materializes them using the <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> operator, and removes the collection.</span></span> <span data-ttu-id="6a03e-126">Na koniec pobiera kolekcję elementów i usuwa <xref:System.Xml.Linq.Extensions.Remove%2A> je za pomocą metody rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="6a03e-126">Finally, it retrieves a collection of elements and removes them using the <xref:System.Xml.Linq.Extensions.Remove%2A> extension method.</span></span>

<span data-ttu-id="6a03e-127">Aby uzyskać więcej <xref:System.Linq.Enumerable.ToList%2A> informacji na temat operatora, zobacz [Konwertowanie typów danych (C#)](./converting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="6a03e-127">For more information on the <xref:System.Linq.Enumerable.ToList%2A> operator, see [Converting Data Types (C#)](./converting-data-types.md).</span></span>

### <a name="code"></a><span data-ttu-id="6a03e-128">Code</span><span class="sxs-lookup"><span data-stu-id="6a03e-128">Code</span></span>

```csharp
XElement root = XElement.Parse(@"<Root>
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
</Root>");
root.Element("Child1").Element("GrandChild1").Remove();
root.Element("Child2").Elements().ToList().Remove();
root.Element("Child3").Elements().Remove();
Console.WriteLine(root);
```

### <a name="comments"></a><span data-ttu-id="6a03e-129">Komentarze</span><span class="sxs-lookup"><span data-stu-id="6a03e-129">Comments</span></span>

<span data-ttu-id="6a03e-130">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="6a03e-130">This code produces the following output:</span></span>

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

<span data-ttu-id="6a03e-131">Należy zauważyć, że pierwszy element `Child1`wnuka został usunięty z .</span><span class="sxs-lookup"><span data-stu-id="6a03e-131">Notice that the first grandchild element has been removed from `Child1`.</span></span> <span data-ttu-id="6a03e-132">Wszystkie elementy wnuków zostały `Child2` usunięte `Child3`z i z .</span><span class="sxs-lookup"><span data-stu-id="6a03e-132">All grandchildren elements have been removed from `Child2` and from `Child3`.</span></span>
