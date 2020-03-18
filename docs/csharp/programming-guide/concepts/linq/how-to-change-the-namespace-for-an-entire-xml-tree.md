---
title: Jak zmienić obszar nazw dla całego drzewa XML (C#)
ms.date: 07/20/2015
ms.assetid: 1584ff3b-c77d-4241-ab62-80adfb7bfc1b
ms.openlocfilehash: 6462cbb5001682b6a464c1446f8ae6de3c5669d1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141509"
---
# <a name="how-to-change-the-namespace-for-an-entire-xml-tree-c"></a><span data-ttu-id="98308-102">Jak zmienić obszar nazw dla całego drzewa XML (C#)</span><span class="sxs-lookup"><span data-stu-id="98308-102">How to change the namespace for an entire XML tree (C#)</span></span>
<span data-ttu-id="98308-103">Czasami trzeba programowo zmienić obszar nazw dla elementu lub atrybutu.</span><span class="sxs-lookup"><span data-stu-id="98308-103">You sometimes have to programmatically change the namespace for an element or an attribute.</span></span> <span data-ttu-id="98308-104">LINQ do XML sprawia, że to proste.</span><span class="sxs-lookup"><span data-stu-id="98308-104">LINQ to XML makes this easy.</span></span> <span data-ttu-id="98308-105">Obiekt <xref:System.Xml.Linq.XElement.Name%2A?displayProperty=nameWithType> można ustawić.</span><span class="sxs-lookup"><span data-stu-id="98308-105">The <xref:System.Xml.Linq.XElement.Name%2A?displayProperty=nameWithType> property can be set.</span></span> <span data-ttu-id="98308-106">Nie <xref:System.Xml.Linq.XAttribute.Name%2A?displayProperty=nameWithType> można ustawić właściwości, ale można łatwo skopiować atrybuty do <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>, usunąć istniejące atrybuty, a następnie dodać nowe atrybuty, które znajdują się w nowym żądanym obszarze nazw.</span><span class="sxs-lookup"><span data-stu-id="98308-106">The <xref:System.Xml.Linq.XAttribute.Name%2A?displayProperty=nameWithType> property cannot be set, but you can easily copy the attributes into a <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>, remove the existing attributes, and then add new attributes that are in the new desired namespace.</span></span>  
  
 <span data-ttu-id="98308-107">Aby uzyskać więcej informacji, zobacz [Omówienie przestrzeni nazw (LINQ do XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="98308-107">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="98308-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="98308-108">Example</span></span>  
 <span data-ttu-id="98308-109">Poniższy kod tworzy dwa drzewa XML w obszarze nazw.</span><span class="sxs-lookup"><span data-stu-id="98308-109">The following code creates two XML trees in no namespace.</span></span> <span data-ttu-id="98308-110">Następnie zmienia obszar nazw każdego z drzew i łączy je w jedno drzewo.</span><span class="sxs-lookup"><span data-stu-id="98308-110">It then changes the namespace of each of the trees, and combines them into a single tree.</span></span>  
  
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
  
 <span data-ttu-id="98308-111">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="98308-111">This example produces the following output:</span></span>  
  
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
