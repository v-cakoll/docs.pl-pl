---
title: Jak zmienić przestrzeń nazw dla całego drzewa XML (C#)
description: Dowiedz się, jak programowo zmienić przestrzeń nazw dla elementu lub atrybutu w LINQ to XML w języku C#.
ms.date: 07/20/2015
ms.assetid: 1584ff3b-c77d-4241-ab62-80adfb7bfc1b
ms.openlocfilehash: 0bf4c9d8f3cf569f14b654dfd0c4291a7eb647df
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105365"
---
# <a name="how-to-change-the-namespace-for-an-entire-xml-tree-c"></a><span data-ttu-id="0349c-103">Jak zmienić przestrzeń nazw dla całego drzewa XML (C#)</span><span class="sxs-lookup"><span data-stu-id="0349c-103">How to change the namespace for an entire XML tree (C#)</span></span>
<span data-ttu-id="0349c-104">Czasami trzeba programistycznie zmienić przestrzeń nazw dla elementu lub atrybutu.</span><span class="sxs-lookup"><span data-stu-id="0349c-104">You sometimes have to programmatically change the namespace for an element or an attribute.</span></span> <span data-ttu-id="0349c-105">Ułatwia to LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="0349c-105">LINQ to XML makes this easy.</span></span> <span data-ttu-id="0349c-106"><xref:System.Xml.Linq.XElement.Name%2A?displayProperty=nameWithType>Właściwość może być ustawiona.</span><span class="sxs-lookup"><span data-stu-id="0349c-106">The <xref:System.Xml.Linq.XElement.Name%2A?displayProperty=nameWithType> property can be set.</span></span> <span data-ttu-id="0349c-107"><xref:System.Xml.Linq.XAttribute.Name%2A?displayProperty=nameWithType>Nie można ustawić właściwości, ale można łatwo skopiować atrybuty do <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> , usunąć istniejące atrybuty, a następnie dodać nowe atrybuty, które znajdują się w nowym żądanym obszarze nazw.</span><span class="sxs-lookup"><span data-stu-id="0349c-107">The <xref:System.Xml.Linq.XAttribute.Name%2A?displayProperty=nameWithType> property cannot be set, but you can easily copy the attributes into a <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>, remove the existing attributes, and then add new attributes that are in the new desired namespace.</span></span>  
  
 <span data-ttu-id="0349c-108">Aby uzyskać więcej informacji, zobacz temat [przestrzenie nazw — omówienie (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="0349c-108">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0349c-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="0349c-109">Example</span></span>  
 <span data-ttu-id="0349c-110">Poniższy kod tworzy dwa drzewa XML w obszarze brak przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="0349c-110">The following code creates two XML trees in no namespace.</span></span> <span data-ttu-id="0349c-111">Następnie zmienia przestrzeń nazw każdego drzewa i łączy je w jedno drzewo.</span><span class="sxs-lookup"><span data-stu-id="0349c-111">It then changes the namespace of each of the trees, and combines them into a single tree.</span></span>  
  
```csharp  
XElement tree1 = new XElement("Data",  
    new XElement("Child", "content",  
        new XAttribute("MyAttr", "content")  
    )  
);  
XElement tree2 = new XElement("Data",  
    new XElement("Child", "content",  
        new XAttribute("MyAttr", "content")  
    )  
);  
XNamespace aw = "http://www.adventure-works.com";  
XNamespace ad = "http://www.adatum.com";  
// change the namespace of every element and attribute in the first tree  
foreach (XElement el in tree1.DescendantsAndSelf())  
{  
    el.Name = aw.GetName(el.Name.LocalName);  
    List<XAttribute> atList = el.Attributes().ToList();  
    el.Attributes().Remove();  
    foreach (XAttribute at in atList)  
        el.Add(new XAttribute(aw.GetName(at.Name.LocalName), at.Value));  
}  
// change the namespace of every element and attribute in the second tree  
foreach (XElement el in tree2.DescendantsAndSelf())  
{  
    el.Name = ad.GetName(el.Name.LocalName);  
    List<XAttribute> atList = el.Attributes().ToList();  
    el.Attributes().Remove();  
    foreach (XAttribute at in atList)  
        el.Add(new XAttribute(ad.GetName(at.Name.LocalName), at.Value));  
}  
// add attribute namespaces so that the tree will be serialized with  
// the aw and ad namespace prefixes  
tree1.Add(  
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com")  
);  
tree2.Add(  
    new XAttribute(XNamespace.Xmlns + "ad", "http://www.adatum.com")  
);  
// create a new composite tree  
XElement root = new XElement("Root",  
    tree1,  
    tree2  
);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="0349c-112">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="0349c-112">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <aw:Data xmlns:aw="http://www.adventure-works.com">  
    <aw:Child aw:MyAttr="content">content</aw:Child>  
  </aw:Data>  
  <ad:Data xmlns:ad="http://www.adatum.com">  
    <ad:Child ad:MyAttr="content">content</ad:Child>  
  </ad:Data>  
</Root>  
```  
