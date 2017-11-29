---
title: "Dodawanie elementy, atrybuty i węzłów do drzewa XML (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: db911e4f-40aa-499a-9500-a9763bb6df56
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: bbe7d00dc1a0b0ad5dcc7cbbedb1f2886f6ff2de
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="adding-elements-attributes-and-nodes-to-an-xml-tree-c"></a><span data-ttu-id="f47f9-102">Dodawanie elementy, atrybuty i węzłów do drzewa XML (C#)</span><span class="sxs-lookup"><span data-stu-id="f47f9-102">Adding Elements, Attributes, and Nodes to an XML Tree (C#)</span></span>
<span data-ttu-id="f47f9-103">Zawartość (elementy, atrybuty, komentarze, przetwarzanie instrukcji, tekst i CDATA) można dodać do istniejącego drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="f47f9-103">You can add content (elements, attributes, comments, processing instructions, text, and CDATA) to an existing XML tree.</span></span>  
  
## <a name="methods-for-adding-content"></a><span data-ttu-id="f47f9-104">Metody do dodawania zawartości</span><span class="sxs-lookup"><span data-stu-id="f47f9-104">Methods for Adding Content</span></span>  
 <span data-ttu-id="f47f9-105">Następujące metody Dodaj zawartość elementu podrzędnego do <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XDocument>:</span><span class="sxs-lookup"><span data-stu-id="f47f9-105">The following methods add child content to an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XDocument>:</span></span>  
  
|<span data-ttu-id="f47f9-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="f47f9-106">Method</span></span>|<span data-ttu-id="f47f9-107">Opis</span><span class="sxs-lookup"><span data-stu-id="f47f9-107">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.Add%2A>|<span data-ttu-id="f47f9-108">Dodaje zawartość na końcu zawartości elementu podrzędnego <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="f47f9-108">Adds content at the end of the child content of the <xref:System.Xml.Linq.XContainer>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|<span data-ttu-id="f47f9-109">Dodaje zawartość na początku elementu podrzędnego zawartości <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="f47f9-109">Adds content at the beginning of the child content of the <xref:System.Xml.Linq.XContainer>.</span></span>|  
  
 <span data-ttu-id="f47f9-110">Następujące metody Dodaj zawartość jako węzły równorzędne <xref:System.Xml.Linq.XNode>.</span><span class="sxs-lookup"><span data-stu-id="f47f9-110">The following methods add content as sibling nodes of an <xref:System.Xml.Linq.XNode>.</span></span> <span data-ttu-id="f47f9-111">Najbardziej typowe węzeł, do której są dodawane element równorzędny zawartości jest <xref:System.Xml.Linq.XElement>, chociaż można dodać zawartość prawidłowy element równorzędny na inne typy węzłów takich jak <xref:System.Xml.Linq.XText> lub <xref:System.Xml.Linq.XComment>.</span><span class="sxs-lookup"><span data-stu-id="f47f9-111">The most common node to which you add sibling content is <xref:System.Xml.Linq.XElement>, although you can add valid sibling content to other types of nodes such as <xref:System.Xml.Linq.XText> or <xref:System.Xml.Linq.XComment>.</span></span>  
  
|<span data-ttu-id="f47f9-112">Metoda</span><span class="sxs-lookup"><span data-stu-id="f47f9-112">Method</span></span>|<span data-ttu-id="f47f9-113">Opis</span><span class="sxs-lookup"><span data-stu-id="f47f9-113">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|<span data-ttu-id="f47f9-114">Dodaje zawartość po <xref:System.Xml.Linq.XNode>.</span><span class="sxs-lookup"><span data-stu-id="f47f9-114">Adds content after the <xref:System.Xml.Linq.XNode>.</span></span>|  
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|<span data-ttu-id="f47f9-115">Dodaje zawartość przed <xref:System.Xml.Linq.XNode>.</span><span class="sxs-lookup"><span data-stu-id="f47f9-115">Adds content before the <xref:System.Xml.Linq.XNode>.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f47f9-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="f47f9-116">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="f47f9-117">Opis</span><span class="sxs-lookup"><span data-stu-id="f47f9-117">Description</span></span>  
 <span data-ttu-id="f47f9-118">Poniższy przykład tworzy dwa drzewa XML, a następnie modyfikuje jedną z drzewa.</span><span class="sxs-lookup"><span data-stu-id="f47f9-118">The following example creates two XML trees, and then modifies one of the trees.</span></span>  
  
### <a name="code"></a><span data-ttu-id="f47f9-119">Kod</span><span class="sxs-lookup"><span data-stu-id="f47f9-119">Code</span></span>  
  
```csharp  
XElement srcTree = new XElement("Root",   
    new XElement("Element1", 1),  
    new XElement("Element2", 2),  
    new XElement("Element3", 3),  
    new XElement("Element4", 4),  
    new XElement("Element5", 5)  
);  
XElement xmlTree = new XElement("Root",  
    new XElement("Child1", 1),  
    new XElement("Child2", 2),  
    new XElement("Child3", 3),  
    new XElement("Child4", 4),  
    new XElement("Child5", 5)  
);  
xmlTree.Add(new XElement("NewChild", "new content"));  
xmlTree.Add(  
    from el in srcTree.Elements()  
    where (int)el > 3  
    select el  
);  
// Even though Child9 does not exist in srcTree, the following statement will not  
// throw an exception, and nothing will be added to xmlTree.  
xmlTree.Add(srcTree.Element("Child9"));  
Console.WriteLine(xmlTree);  
```  
  
### <a name="comments"></a><span data-ttu-id="f47f9-120">Komentarze</span><span class="sxs-lookup"><span data-stu-id="f47f9-120">Comments</span></span>  
 <span data-ttu-id="f47f9-121">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="f47f9-121">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child1>1</Child1>  
  <Child2>2</Child2>  
  <Child3>3</Child3>  
  <Child4>4</Child4>  
  <Child5>5</Child5>  
  <NewChild>new content</NewChild>  
  <Element4>4</Element4>  
  <Element5>5</Element5>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f47f9-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f47f9-122">See Also</span></span>  
 [<span data-ttu-id="f47f9-123">Modyfikowanie drzew XML (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="f47f9-123">Modifying XML Trees (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
