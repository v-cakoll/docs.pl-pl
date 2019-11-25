---
title: Jak filtrować nazwy elementów (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 1849fb03-f075-421f-863c-e8fb32773cdf
ms.openlocfilehash: 74efb19ef5ec77ca29145d27a8e5aa977530b68b
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141265"
---
# <a name="how-to-filter-on-element-names-linq-to-xml-c"></a><span data-ttu-id="ff81a-102">Jak filtrować nazwy elementów (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="ff81a-102">How to filter on element names (LINQ to XML) (C#)</span></span>
<span data-ttu-id="ff81a-103">Po wywołaniu jednej z metod, które zwracają <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement>, można filtrować według nazwy elementu.</span><span class="sxs-lookup"><span data-stu-id="ff81a-103">When you call one of the methods that return <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, you can filter on the element name.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ff81a-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="ff81a-104">Example</span></span>  
 <span data-ttu-id="ff81a-105">Ten przykład pobiera kolekcję elementów podrzędnych, które są filtrowane w celu zawiera tylko elementy podrzędne o określonej nazwie.</span><span class="sxs-lookup"><span data-stu-id="ff81a-105">This example retrieves a collection of descendants that is filtered to contain only descendants with the specified name.</span></span>  
  
 <span data-ttu-id="ff81a-106">W tym przykładzie zastosowano następujący dokument XML: [przykładowy plik XML: typowe zamówienie zakupu (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="ff81a-106">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
```csharp  
XElement po = XElement.Load("PurchaseOrder.xml");  
IEnumerable<XElement> items =  
    from el in po.Descendants("ProductName")  
    select el;  
foreach(XElement prdName in items)  
    Console.WriteLine(prdName.Name + ":" + (string) prdName);  
```  
  
 <span data-ttu-id="ff81a-107">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="ff81a-107">This code produces the following output:</span></span>  
  
```output  
ProductName:Lawnmower  
ProductName:Baby Monitor  
```  
  
 <span data-ttu-id="ff81a-108">Inne metody, które zwracają <xref:System.Collections.Generic.IEnumerable%601> kolekcji <xref:System.Xml.Linq.XElement>, są zgodne z tym samym wzorcem.</span><span class="sxs-lookup"><span data-stu-id="ff81a-108">The other methods that return <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement> collections follow the same pattern.</span></span> <span data-ttu-id="ff81a-109">Ich podpisy są podobne do <xref:System.Xml.Linq.XContainer.Elements%2A> i <xref:System.Xml.Linq.XContainer.Descendants%2A>.</span><span class="sxs-lookup"><span data-stu-id="ff81a-109">Their signatures are similar to <xref:System.Xml.Linq.XContainer.Elements%2A> and <xref:System.Xml.Linq.XContainer.Descendants%2A>.</span></span> <span data-ttu-id="ff81a-110">Poniżej znajduje się kompletna lista metod, które mają podobne sygnatury metod:</span><span class="sxs-lookup"><span data-stu-id="ff81a-110">The following is the complete list of methods that have similar method signatures:</span></span>  
  
- <xref:System.Xml.Linq.XNode.Ancestors%2A>  
  
- <xref:System.Xml.Linq.XContainer.Descendants%2A>  
  
- <xref:System.Xml.Linq.XContainer.Elements%2A>  
  
- <xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A>  
  
- <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>  
  
- <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>  
  
- <xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A>  
  
## <a name="example"></a><span data-ttu-id="ff81a-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="ff81a-111">Example</span></span>  
 <span data-ttu-id="ff81a-112">W poniższym przykładzie pokazano to samo zapytanie dla kodu XML, który znajduje się w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="ff81a-112">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="ff81a-113">Aby uzyskać więcej informacji, zobacz temat [przestrzenie nazw —C#omówienie (LINQ to XML) ()](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="ff81a-113">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="ff81a-114">W tym przykładzie zastosowano następujący dokument XML: [przykładowy plik XML: typowe zamówienie zakupu w przestrzeni nazw](./sample-xml-file-typical-purchase-order-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="ff81a-114">This example uses the following XML document: [Sample XML File: Typical Purchase Order in a Namespace](./sample-xml-file-typical-purchase-order-in-a-namespace.md).</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement po = XElement.Load("PurchaseOrderInNamespace.xml");  
IEnumerable<XElement> items =  
    from el in po.Descendants(aw + "ProductName")  
    select el;  
foreach (XElement prdName in items)  
    Console.WriteLine(prdName.Name + ":" + (string)prdName);  
```  
  
 <span data-ttu-id="ff81a-115">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="ff81a-115">This code produces the following output:</span></span>  
  
```output  
{http://www.adventure-works.com}ProductName:Lawnmower  
{http://www.adventure-works.com}ProductName:Baby Monitor  
```  
  
## <a name="see-also"></a><span data-ttu-id="ff81a-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ff81a-116">See also</span></span>

- [<span data-ttu-id="ff81a-117">Osie LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="ff81a-117">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
