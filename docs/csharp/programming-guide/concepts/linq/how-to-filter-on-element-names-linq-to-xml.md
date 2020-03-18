---
title: Jak filtrować nazwy elementów (LINQ do XML) (C#)
ms.date: 07/20/2015
ms.assetid: 1849fb03-f075-421f-863c-e8fb32773cdf
ms.openlocfilehash: 74efb19ef5ec77ca29145d27a8e5aa977530b68b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141265"
---
# <a name="how-to-filter-on-element-names-linq-to-xml-c"></a><span data-ttu-id="62028-102">Jak filtrować nazwy elementów (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="62028-102">How to filter on element names (LINQ to XML) (C#)</span></span>
<span data-ttu-id="62028-103">Po wywołaniu jednej z metod, które zwracają <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement>, można filtrować na nazwę elementu.</span><span class="sxs-lookup"><span data-stu-id="62028-103">When you call one of the methods that return <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, you can filter on the element name.</span></span>  
  
## <a name="example"></a><span data-ttu-id="62028-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="62028-104">Example</span></span>  
 <span data-ttu-id="62028-105">W tym przykładzie pobiera kolekcję elementów podrzędnych, który jest filtrowany, aby zawierać tylko elementy podrzędne o określonej nazwie.</span><span class="sxs-lookup"><span data-stu-id="62028-105">This example retrieves a collection of descendants that is filtered to contain only descendants with the specified name.</span></span>  
  
 <span data-ttu-id="62028-106">W tym przykładzie użyto następującego dokumentu XML: [Przykładowy plik XML: Typowe zamówienie zakupu (LINQ do XML).](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md)</span><span class="sxs-lookup"><span data-stu-id="62028-106">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
```csharp  
XElement po = XElement.Load("PurchaseOrder.xml");  
IEnumerable<XElement> items =  
    from el in po.Descendants("ProductName")  
    select el;  
foreach(XElement prdName in items)  
    Console.WriteLine(prdName.Name + ":" + (string) prdName);  
```  
  
 <span data-ttu-id="62028-107">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="62028-107">This code produces the following output:</span></span>  
  
```output  
ProductName:Lawnmower  
ProductName:Baby Monitor  
```  
  
 <span data-ttu-id="62028-108">Inne metody, które <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> zwracają kolekcje postępują zgodnie z tym samym wzorcem.</span><span class="sxs-lookup"><span data-stu-id="62028-108">The other methods that return <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement> collections follow the same pattern.</span></span> <span data-ttu-id="62028-109">Ich podpisy są <xref:System.Xml.Linq.XContainer.Elements%2A> <xref:System.Xml.Linq.XContainer.Descendants%2A>podobne i .</span><span class="sxs-lookup"><span data-stu-id="62028-109">Their signatures are similar to <xref:System.Xml.Linq.XContainer.Elements%2A> and <xref:System.Xml.Linq.XContainer.Descendants%2A>.</span></span> <span data-ttu-id="62028-110">Poniżej znajduje się pełna lista metod, które mają podobne podpisy metod:</span><span class="sxs-lookup"><span data-stu-id="62028-110">The following is the complete list of methods that have similar method signatures:</span></span>  
  
- <xref:System.Xml.Linq.XNode.Ancestors%2A>  
  
- <xref:System.Xml.Linq.XContainer.Descendants%2A>  
  
- <xref:System.Xml.Linq.XContainer.Elements%2A>  
  
- <xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A>  
  
- <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>  
  
- <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>  
  
- <xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A>  
  
## <a name="example"></a><span data-ttu-id="62028-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="62028-111">Example</span></span>  
 <span data-ttu-id="62028-112">W poniższym przykładzie przedstawiono tę samą kwerendę dla języka XML, która znajduje się w obszarze nazw.</span><span class="sxs-lookup"><span data-stu-id="62028-112">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="62028-113">Aby uzyskać więcej informacji, zobacz [Omówienie przestrzeni nazw (LINQ do XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="62028-113">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="62028-114">W tym przykładzie użyto następującego dokumentu XML: [Przykładowy plik XML: Typowe zamówienie zakupu w obszarze nazw](./sample-xml-file-typical-purchase-order-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="62028-114">This example uses the following XML document: [Sample XML File: Typical Purchase Order in a Namespace](./sample-xml-file-typical-purchase-order-in-a-namespace.md).</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement po = XElement.Load("PurchaseOrderInNamespace.xml");  
IEnumerable<XElement> items =  
    from el in po.Descendants(aw + "ProductName")  
    select el;  
foreach (XElement prdName in items)  
    Console.WriteLine(prdName.Name + ":" + (string)prdName);  
```  
  
 <span data-ttu-id="62028-115">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="62028-115">This code produces the following output:</span></span>  
  
```output  
{http://www.adventure-works.com}ProductName:Lawnmower  
{http://www.adventure-works.com}ProductName:Baby Monitor  
```  
  
## <a name="see-also"></a><span data-ttu-id="62028-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="62028-116">See also</span></span>

- [<span data-ttu-id="62028-117">LINQ do osi XML (C#)</span><span class="sxs-lookup"><span data-stu-id="62028-117">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
