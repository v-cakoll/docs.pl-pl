---
title: Dodawanie elementów, atrybutów i węzłów do drzewa XML (C#)
description: Dowiedz się więcej o metodach dodawania zawartości, takich jak elementy, atrybuty, komentarze, instrukcje przetwarzania i tekst do istniejącego drzewa XML.
ms.date: 07/20/2015
ms.assetid: db911e4f-40aa-499a-9500-a9763bb6df56
ms.openlocfilehash: 78a84401494e2d4280799632fa42dc95574e3e10
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105548"
---
# <a name="adding-elements-attributes-and-nodes-to-an-xml-tree-c"></a><span data-ttu-id="1158c-103">Dodawanie elementów, atrybutów i węzłów do drzewa XML (C#)</span><span class="sxs-lookup"><span data-stu-id="1158c-103">Adding Elements, Attributes, and Nodes to an XML Tree (C#)</span></span>
<span data-ttu-id="1158c-104">Możesz dodać zawartość (elementy, atrybuty, komentarze, instrukcje przetwarzania, tekst i CDATA) do istniejącego drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="1158c-104">You can add content (elements, attributes, comments, processing instructions, text, and CDATA) to an existing XML tree.</span></span>  
  
## <a name="methods-for-adding-content"></a><span data-ttu-id="1158c-105">Metody dodawania zawartości</span><span class="sxs-lookup"><span data-stu-id="1158c-105">Methods for Adding Content</span></span>  
 <span data-ttu-id="1158c-106">Następujące metody dodają zawartość podrzędną do elementu <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XDocument> :</span><span class="sxs-lookup"><span data-stu-id="1158c-106">The following methods add child content to an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XDocument>:</span></span>  
  
|<span data-ttu-id="1158c-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="1158c-107">Method</span></span>|<span data-ttu-id="1158c-108">Opis</span><span class="sxs-lookup"><span data-stu-id="1158c-108">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.Add%2A>|<span data-ttu-id="1158c-109">Dodaje zawartość na końcu zawartości podrzędnej <xref:System.Xml.Linq.XContainer> .</span><span class="sxs-lookup"><span data-stu-id="1158c-109">Adds content at the end of the child content of the <xref:System.Xml.Linq.XContainer>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|<span data-ttu-id="1158c-110">Dodaje zawartość na początku zawartości podrzędnej <xref:System.Xml.Linq.XContainer> .</span><span class="sxs-lookup"><span data-stu-id="1158c-110">Adds content at the beginning of the child content of the <xref:System.Xml.Linq.XContainer>.</span></span>|  
  
 <span data-ttu-id="1158c-111">Poniższe metody dodają zawartość jako węzły równorzędne <xref:System.Xml.Linq.XNode> .</span><span class="sxs-lookup"><span data-stu-id="1158c-111">The following methods add content as sibling nodes of an <xref:System.Xml.Linq.XNode>.</span></span> <span data-ttu-id="1158c-112">Najbardziej typowym węzłem, do którego dodawana jest zawartość elementu równorzędnego <xref:System.Xml.Linq.XElement> , jest, chociaż można dodać prawidłową zawartość równorzędną do innych typów węzłów, takich jak <xref:System.Xml.Linq.XText> lub <xref:System.Xml.Linq.XComment> .</span><span class="sxs-lookup"><span data-stu-id="1158c-112">The most common node to which you add sibling content is <xref:System.Xml.Linq.XElement>, although you can add valid sibling content to other types of nodes such as <xref:System.Xml.Linq.XText> or <xref:System.Xml.Linq.XComment>.</span></span>  
  
|<span data-ttu-id="1158c-113">Metoda</span><span class="sxs-lookup"><span data-stu-id="1158c-113">Method</span></span>|<span data-ttu-id="1158c-114">Opis</span><span class="sxs-lookup"><span data-stu-id="1158c-114">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|<span data-ttu-id="1158c-115">Dodaje zawartość po <xref:System.Xml.Linq.XNode> .</span><span class="sxs-lookup"><span data-stu-id="1158c-115">Adds content after the <xref:System.Xml.Linq.XNode>.</span></span>|  
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|<span data-ttu-id="1158c-116">Dodaje zawartość przed <xref:System.Xml.Linq.XNode> .</span><span class="sxs-lookup"><span data-stu-id="1158c-116">Adds content before the <xref:System.Xml.Linq.XNode>.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1158c-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="1158c-117">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="1158c-118">Opis</span><span class="sxs-lookup"><span data-stu-id="1158c-118">Description</span></span>  
 <span data-ttu-id="1158c-119">Poniższy przykład tworzy dwa drzewa XML, a następnie modyfikuje jedno z drzew.</span><span class="sxs-lookup"><span data-stu-id="1158c-119">The following example creates two XML trees, and then modifies one of the trees.</span></span>  
  
### <a name="code"></a><span data-ttu-id="1158c-120">Kod</span><span class="sxs-lookup"><span data-stu-id="1158c-120">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="1158c-121">Komentarze</span><span class="sxs-lookup"><span data-stu-id="1158c-121">Comments</span></span>  
 <span data-ttu-id="1158c-122">Ten kod spowoduje wygenerowanie następujących danych wyjściowych:</span><span class="sxs-lookup"><span data-stu-id="1158c-122">This code produces the following output:</span></span>  
  
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
  