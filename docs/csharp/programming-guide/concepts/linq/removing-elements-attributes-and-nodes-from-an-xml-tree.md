---
title: Usuwanie elementów, atrybutów i węzłów z drzewa XML (C#)
ms.date: 07/20/2015
ms.assetid: 07dd06d6-1117-4077-bf98-9120cf51176e
ms.openlocfilehash: 9ce63ce6a4ef75dedc788efca11e8dd2bdb471eb
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46320477"
---
# <a name="removing-elements-attributes-and-nodes-from-an-xml-tree-c"></a><span data-ttu-id="60c73-102">Usuwanie elementów, atrybutów i węzłów z drzewa XML (C#)</span><span class="sxs-lookup"><span data-stu-id="60c73-102">Removing Elements, Attributes, and Nodes from an XML Tree (C#)</span></span>
<span data-ttu-id="60c73-103">Możesz zmodyfikować drzewa XML, usunięcie elementów, atrybutów i innych typów węzłów.</span><span class="sxs-lookup"><span data-stu-id="60c73-103">You can modify an XML tree, removing elements, attributes, and other types of nodes.</span></span>  
  
 <span data-ttu-id="60c73-104">Usuwanie dokumentu XML pojedynczy element lub jeden atrybut jest bardzo proste.</span><span class="sxs-lookup"><span data-stu-id="60c73-104">Removing a single element or a single attribute from an XML document is straightforward.</span></span> <span data-ttu-id="60c73-105">Jednak podczas usuwania kolekcji elementów lub atrybutów, należy najpierw zmaterializowania kolekcji do listy, a następnie usuń z listy elementów lub atrybutów.</span><span class="sxs-lookup"><span data-stu-id="60c73-105">However, when removing collections of elements or attributes, you should first materialize a collection into a list, and then delete the elements or attributes from the list.</span></span> <span data-ttu-id="60c73-106">Najlepszym rozwiązaniem jest użycie <xref:System.Xml.Linq.Extensions.Remove%2A> metodę rozszerzenia, które wykona to dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="60c73-106">The best approach is to use the <xref:System.Xml.Linq.Extensions.Remove%2A> extension method, which will do this for you.</span></span>  
  
 <span data-ttu-id="60c73-107">Głównym powodem w ten sposób jest uzyskane większość kolekcje, które możesz pobrać z drzewa XML za pomocą odroczonego wykonania.</span><span class="sxs-lookup"><span data-stu-id="60c73-107">The main reason for doing this is that most of the collections you retrieve from an XML tree are yielded using deferred execution.</span></span> <span data-ttu-id="60c73-108">Jeśli użytkownik nie najpierw zmaterializowania je do listy lub jeśli nie używasz metody rozszerzenia, jest możliwość napotkania klasę usterek.</span><span class="sxs-lookup"><span data-stu-id="60c73-108">If you do not first materialize them into a list, or if you do not use the extension methods, it is possible to encounter a certain class of bugs.</span></span> <span data-ttu-id="60c73-109">Aby uzyskać więcej informacji, zobacz [mieszane deklaratywne usterki kodu kodu/Imperatywne (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/mixed-declarative-code-imperative-code-bugs-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="60c73-109">For more information, see [Mixed Declarative Code/Imperative Code Bugs (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/mixed-declarative-code-imperative-code-bugs-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="60c73-110">Następujące metody usuń węzły i atrybuty z drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="60c73-110">The following methods remove nodes and attributes from an XML tree.</span></span>  
  
|<span data-ttu-id="60c73-111">Metoda</span><span class="sxs-lookup"><span data-stu-id="60c73-111">Method</span></span>|<span data-ttu-id="60c73-112">Opis</span><span class="sxs-lookup"><span data-stu-id="60c73-112">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="60c73-113">Usuwa <xref:System.Xml.Linq.XAttribute> od jego elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="60c73-113">Removes an <xref:System.Xml.Linq.XAttribute> from its parent.</span></span>|  
|<xref:System.Xml.Linq.XContainer.RemoveNodes%2A?displayProperty=nameWithType>|<span data-ttu-id="60c73-114">Usuwa węzły podrzędne z <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="60c73-114">Removes the child nodes from an <xref:System.Xml.Linq.XContainer>.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|<span data-ttu-id="60c73-115">Usuwa zawartość i atrybutów z <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="60c73-115">Removes content and attributes from an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="60c73-116">Usuwa atrybuty <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="60c73-116">Removes the attributes of an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|<span data-ttu-id="60c73-117">W przypadku przekazania `null` wartości, a następnie usuwa atrybut.</span><span class="sxs-lookup"><span data-stu-id="60c73-117">If you pass `null` for value, then removes the attribute.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|<span data-ttu-id="60c73-118">W przypadku przekazania `null` wartości, a następnie usuwa element podrzędny.</span><span class="sxs-lookup"><span data-stu-id="60c73-118">If you pass `null` for value, then removes the child element.</span></span>|  
|<xref:System.Xml.Linq.XNode.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="60c73-119">Usuwa <xref:System.Xml.Linq.XNode> od jego elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="60c73-119">Removes an <xref:System.Xml.Linq.XNode> from its parent.</span></span>|  
|<xref:System.Xml.Linq.Extensions.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="60c73-120">Usuwa każdego atrybutu lub elementu w kolekcji źródłowej, z jego elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="60c73-120">Removes every attribute or element in the source collection from its parent element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="60c73-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="60c73-121">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="60c73-122">Opis</span><span class="sxs-lookup"><span data-stu-id="60c73-122">Description</span></span>  
 <span data-ttu-id="60c73-123">W tym przykładzie przedstawiono trzy sposoby usuwania elementów.</span><span class="sxs-lookup"><span data-stu-id="60c73-123">This example demonstrates three approaches to removing elements.</span></span> <span data-ttu-id="60c73-124">Po pierwsze Usuwa pojedynczy element.</span><span class="sxs-lookup"><span data-stu-id="60c73-124">First, it removes a single element.</span></span> <span data-ttu-id="60c73-125">Po drugie, pobiera kolekcję elementów, materializuje je przy użyciu <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> operatora i usuwa kolekcji.</span><span class="sxs-lookup"><span data-stu-id="60c73-125">Second, it retrieves a collection of elements, materializes them using the <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> operator, and removes the collection.</span></span> <span data-ttu-id="60c73-126">Na koniec pobiera kolekcję elementów i usuwa je przy użyciu <xref:System.Xml.Linq.Extensions.Remove%2A> — metoda rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="60c73-126">Finally, it retrieves a collection of elements and removes them using the <xref:System.Xml.Linq.Extensions.Remove%2A> extension method.</span></span>  
  
 <span data-ttu-id="60c73-127">Aby uzyskać więcej informacji na temat <xref:System.Linq.Enumerable.ToList%2A> operatora, zobacz [konwertowanie typów danych (C#)](../../../../csharp/programming-guide/concepts/linq/converting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="60c73-127">For more information on the <xref:System.Linq.Enumerable.ToList%2A> operator, see [Converting Data Types (C#)](../../../../csharp/programming-guide/concepts/linq/converting-data-types.md).</span></span>  
  
### <a name="code"></a><span data-ttu-id="60c73-128">Kod</span><span class="sxs-lookup"><span data-stu-id="60c73-128">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="60c73-129">Komentarze</span><span class="sxs-lookup"><span data-stu-id="60c73-129">Comments</span></span>  
 <span data-ttu-id="60c73-130">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="60c73-130">This code produces the following output:</span></span>  
  
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
  
 <span data-ttu-id="60c73-131">Należy zauważyć, że pierwszy element podwójnym została usunięta z `Child1`.</span><span class="sxs-lookup"><span data-stu-id="60c73-131">Notice that the first grandchild element has been removed from `Child1`.</span></span> <span data-ttu-id="60c73-132">Wszystkie elementy podrzędne zostały usunięte z `Child2` i `Child3`.</span><span class="sxs-lookup"><span data-stu-id="60c73-132">All grandchildren elements have been removed from `Child2` and from `Child3`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60c73-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="60c73-133">See Also</span></span>

- [<span data-ttu-id="60c73-134">Modyfikowanie drzew XML (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="60c73-134">Modifying XML Trees (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
