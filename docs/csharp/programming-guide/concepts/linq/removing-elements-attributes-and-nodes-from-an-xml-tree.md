---
title: "Usuwanie elementy, atrybuty i węzły z drzewa XML (C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 07dd06d6-1117-4077-bf98-9120cf51176e
caps.latest.revision: "4"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1745b1ce84b33a67d54f5e752da2ecf9bbfdbc17
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="removing-elements-attributes-and-nodes-from-an-xml-tree-c"></a><span data-ttu-id="a4780-102">Usuwanie elementy, atrybuty i węzły z drzewa XML (C#)</span><span class="sxs-lookup"><span data-stu-id="a4780-102">Removing Elements, Attributes, and Nodes from an XML Tree (C#)</span></span>
<span data-ttu-id="a4780-103">Drzewo XML można zmodyfikować usunięcie elementów, atrybutów i innych typów węzłów.</span><span class="sxs-lookup"><span data-stu-id="a4780-103">You can modify an XML tree, removing elements, attributes, and other types of nodes.</span></span>  
  
 <span data-ttu-id="a4780-104">Usuwanie pojedynczy element lub jeden atrybut z dokumentu XML jest prosta.</span><span class="sxs-lookup"><span data-stu-id="a4780-104">Removing a single element or a single attribute from an XML document is straightforward.</span></span> <span data-ttu-id="a4780-105">Jednak podczas usuwania kolekcji elementów lub atrybutów, należy najpierw zmaterializowania kolekcji do listy, a następnie usuń z listy elementów lub atrybutów.</span><span class="sxs-lookup"><span data-stu-id="a4780-105">However, when removing collections of elements or attributes, you should first materialize a collection into a list, and then delete the elements or attributes from the list.</span></span> <span data-ttu-id="a4780-106">Najlepszym rozwiązaniem jest użycie <xref:System.Xml.Linq.Extensions.Remove%2A> — metoda rozszerzenia, co zrobić to za Ciebie.</span><span class="sxs-lookup"><span data-stu-id="a4780-106">The best approach is to use the <xref:System.Xml.Linq.Extensions.Remove%2A> extension method, which will do this for you.</span></span>  
  
 <span data-ttu-id="a4780-107">Głównym celem tej czynności jest zwróciło większość kolekcje, które można pobrać z drzewa XML przy użyciu odroczonego wykonania.</span><span class="sxs-lookup"><span data-stu-id="a4780-107">The main reason for doing this is that most of the collections you retrieve from an XML tree are yielded using deferred execution.</span></span> <span data-ttu-id="a4780-108">Jeśli użytkownik nie najpierw zmaterializowania je do listy, lub jeśli nie używasz metody rozszerzenia, istnieje możliwość wystąpienia klasy usterek.</span><span class="sxs-lookup"><span data-stu-id="a4780-108">If you do not first materialize them into a list, or if you do not use the extension methods, it is possible to encounter a certain class of bugs.</span></span> <span data-ttu-id="a4780-109">Aby uzyskać więcej informacji, zobacz [mieszanych deklaratywne usterki kodu kodu/Imperatywne (LINQ do XML) (C#)](../../../../csharp/programming-guide/concepts/linq/mixed-declarative-code-imperative-code-bugs-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="a4780-109">For more information, see [Mixed Declarative Code/Imperative Code Bugs (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/mixed-declarative-code-imperative-code-bugs-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="a4780-110">Następujące metody usuń węzły i atrybuty z drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="a4780-110">The following methods remove nodes and attributes from an XML tree.</span></span>  
  
|<span data-ttu-id="a4780-111">Metoda</span><span class="sxs-lookup"><span data-stu-id="a4780-111">Method</span></span>|<span data-ttu-id="a4780-112">Opis</span><span class="sxs-lookup"><span data-stu-id="a4780-112">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="a4780-113">Usuwa <xref:System.Xml.Linq.XAttribute> po swoim obiekcie nadrzędnym.</span><span class="sxs-lookup"><span data-stu-id="a4780-113">Removes an <xref:System.Xml.Linq.XAttribute> from its parent.</span></span>|  
|<xref:System.Xml.Linq.XContainer.RemoveNodes%2A?displayProperty=nameWithType>|<span data-ttu-id="a4780-114">Usuwa węzłów podrzędnych z <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="a4780-114">Removes the child nodes from an <xref:System.Xml.Linq.XContainer>.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|<span data-ttu-id="a4780-115">Usuwa zawartość oraz atrybutów z <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="a4780-115">Removes content and attributes from an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="a4780-116">Usuwa atrybuty <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="a4780-116">Removes the attributes of an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|<span data-ttu-id="a4780-117">W przypadku przekazania `null` dla wartości, a następnie usuwa ten atrybut.</span><span class="sxs-lookup"><span data-stu-id="a4780-117">If you pass `null` for value, then removes the attribute.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|<span data-ttu-id="a4780-118">W przypadku przekazania `null` dla wartości, a następnie usuwa element podrzędny.</span><span class="sxs-lookup"><span data-stu-id="a4780-118">If you pass `null` for value, then removes the child element.</span></span>|  
|<xref:System.Xml.Linq.XNode.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="a4780-119">Usuwa <xref:System.Xml.Linq.XNode> po swoim obiekcie nadrzędnym.</span><span class="sxs-lookup"><span data-stu-id="a4780-119">Removes an <xref:System.Xml.Linq.XNode> from its parent.</span></span>|  
|<xref:System.Xml.Linq.Extensions.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="a4780-120">Usuwa każdy atrybut lub element w kolekcji źródłowej z jego elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="a4780-120">Removes every attribute or element in the source collection from its parent element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a4780-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="a4780-121">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="a4780-122">Opis</span><span class="sxs-lookup"><span data-stu-id="a4780-122">Description</span></span>  
 <span data-ttu-id="a4780-123">W tym przykładzie przedstawiono trzy sposoby usuwanie elementów.</span><span class="sxs-lookup"><span data-stu-id="a4780-123">This example demonstrates three approaches to removing elements.</span></span> <span data-ttu-id="a4780-124">Po pierwsze Usuwa pojedynczy element.</span><span class="sxs-lookup"><span data-stu-id="a4780-124">First, it removes a single element.</span></span> <span data-ttu-id="a4780-125">Po drugie, pobiera kolekcję elementów, zostaje je przy użyciu <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> , operator i spowoduje usunięcie kolekcji.</span><span class="sxs-lookup"><span data-stu-id="a4780-125">Second, it retrieves a collection of elements, materializes them using the <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> operator, and removes the collection.</span></span> <span data-ttu-id="a4780-126">Na koniec pobiera kolekcję elementów i usuwa je przy użyciu <xref:System.Xml.Linq.Extensions.Remove%2A> — metoda rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="a4780-126">Finally, it retrieves a collection of elements and removes them using the <xref:System.Xml.Linq.Extensions.Remove%2A> extension method.</span></span>  
  
 <span data-ttu-id="a4780-127">Aby uzyskać więcej informacji na temat <xref:System.Linq.Enumerable.ToList%2A> operatora, zobacz [konwertowanie typów danych (C#)](../../../../csharp/programming-guide/concepts/linq/converting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="a4780-127">For more information on the <xref:System.Linq.Enumerable.ToList%2A> operator, see [Converting Data Types (C#)](../../../../csharp/programming-guide/concepts/linq/converting-data-types.md).</span></span>  
  
### <a name="code"></a><span data-ttu-id="a4780-128">Kod</span><span class="sxs-lookup"><span data-stu-id="a4780-128">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="a4780-129">Komentarze</span><span class="sxs-lookup"><span data-stu-id="a4780-129">Comments</span></span>  
 <span data-ttu-id="a4780-130">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="a4780-130">This code produces the following output:</span></span>  
  
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
  
 <span data-ttu-id="a4780-131">Należy zauważyć, że pierwszy element podwójnym został usunięty z `Child1`.</span><span class="sxs-lookup"><span data-stu-id="a4780-131">Notice that the first grandchild element has been removed from `Child1`.</span></span> <span data-ttu-id="a4780-132">Wszystkie elementy podrzędne zostały usunięte z `Child2` i z `Child3`.</span><span class="sxs-lookup"><span data-stu-id="a4780-132">All grandchildren elements have been removed from `Child2` and from `Child3`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4780-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a4780-133">See Also</span></span>  
 [<span data-ttu-id="a4780-134">Modyfikowanie drzew XML (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="a4780-134">Modifying XML Trees (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
