---
title: Dodawanie elementów, atrybutów i węzłów do drzewa XML (C#)
ms.date: 07/20/2015
ms.assetid: db911e4f-40aa-499a-9500-a9763bb6df56
ms.openlocfilehash: 20d8d9d9c592f5f570d7c94298dcee41763c1f1f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169578"
---
# <a name="adding-elements-attributes-and-nodes-to-an-xml-tree-c"></a><span data-ttu-id="beb88-102">Dodawanie elementów, atrybutów i węzłów do drzewa XML (C#)</span><span class="sxs-lookup"><span data-stu-id="beb88-102">Adding Elements, Attributes, and Nodes to an XML Tree (C#)</span></span>
<span data-ttu-id="beb88-103">Do istniejącego drzewa XML można dodawać zawartość (elementy, atrybuty, komentarze, instrukcje przetwarzania, tekst i CDATA).</span><span class="sxs-lookup"><span data-stu-id="beb88-103">You can add content (elements, attributes, comments, processing instructions, text, and CDATA) to an existing XML tree.</span></span>  
  
## <a name="methods-for-adding-content"></a><span data-ttu-id="beb88-104">Metody dodawania zawartości</span><span class="sxs-lookup"><span data-stu-id="beb88-104">Methods for Adding Content</span></span>  
 <span data-ttu-id="beb88-105">Następujące metody dodają zawartość <xref:System.Xml.Linq.XElement> podrzędną <xref:System.Xml.Linq.XDocument>do:</span><span class="sxs-lookup"><span data-stu-id="beb88-105">The following methods add child content to an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XDocument>:</span></span>  
  
|<span data-ttu-id="beb88-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="beb88-106">Method</span></span>|<span data-ttu-id="beb88-107">Opis</span><span class="sxs-lookup"><span data-stu-id="beb88-107">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.Add%2A>|<span data-ttu-id="beb88-108">Dodaje zawartość na końcu zawartości podrzędnej <xref:System.Xml.Linq.XContainer>pliku .</span><span class="sxs-lookup"><span data-stu-id="beb88-108">Adds content at the end of the child content of the <xref:System.Xml.Linq.XContainer>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|<span data-ttu-id="beb88-109">Dodaje zawartość na początku zawartości podrzędnej pliku <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="beb88-109">Adds content at the beginning of the child content of the <xref:System.Xml.Linq.XContainer>.</span></span>|  
  
 <span data-ttu-id="beb88-110">Następujące metody dodają zawartość jako węzły równorzędne pliku <xref:System.Xml.Linq.XNode>.</span><span class="sxs-lookup"><span data-stu-id="beb88-110">The following methods add content as sibling nodes of an <xref:System.Xml.Linq.XNode>.</span></span> <span data-ttu-id="beb88-111">Najczęstszym węzłem, do którego <xref:System.Xml.Linq.XElement>dodajesię zawartość równorzędnej, jest , chociaż <xref:System.Xml.Linq.XText> można <xref:System.Xml.Linq.XComment>dodać prawidłową zawartość równorzędnego do innych typów węzłów, takich jak lub .</span><span class="sxs-lookup"><span data-stu-id="beb88-111">The most common node to which you add sibling content is <xref:System.Xml.Linq.XElement>, although you can add valid sibling content to other types of nodes such as <xref:System.Xml.Linq.XText> or <xref:System.Xml.Linq.XComment>.</span></span>  
  
|<span data-ttu-id="beb88-112">Metoda</span><span class="sxs-lookup"><span data-stu-id="beb88-112">Method</span></span>|<span data-ttu-id="beb88-113">Opis</span><span class="sxs-lookup"><span data-stu-id="beb88-113">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|<span data-ttu-id="beb88-114">Dodaje zawartość <xref:System.Xml.Linq.XNode>po pliku .</span><span class="sxs-lookup"><span data-stu-id="beb88-114">Adds content after the <xref:System.Xml.Linq.XNode>.</span></span>|  
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|<span data-ttu-id="beb88-115">Dodaje zawartość <xref:System.Xml.Linq.XNode>przed .</span><span class="sxs-lookup"><span data-stu-id="beb88-115">Adds content before the <xref:System.Xml.Linq.XNode>.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="beb88-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="beb88-116">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="beb88-117">Opis</span><span class="sxs-lookup"><span data-stu-id="beb88-117">Description</span></span>  
 <span data-ttu-id="beb88-118">Poniższy przykład tworzy dwa drzewa XML, a następnie modyfikuje jedno z drzew.</span><span class="sxs-lookup"><span data-stu-id="beb88-118">The following example creates two XML trees, and then modifies one of the trees.</span></span>  
  
### <a name="code"></a><span data-ttu-id="beb88-119">Code</span><span class="sxs-lookup"><span data-stu-id="beb88-119">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="beb88-120">Komentarze</span><span class="sxs-lookup"><span data-stu-id="beb88-120">Comments</span></span>  
 <span data-ttu-id="beb88-121">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="beb88-121">This code produces the following output:</span></span>  
  
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
  