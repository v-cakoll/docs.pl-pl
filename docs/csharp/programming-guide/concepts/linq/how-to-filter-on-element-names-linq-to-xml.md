---
title: 'Instrukcje: Filtruj według nazw elementów (LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 1849fb03-f075-421f-863c-e8fb32773cdf
ms.openlocfilehash: 9febe3b834261326bab3e82d87c476f99d4e6b1f
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69593809"
---
# <a name="how-to-filter-on-element-names-linq-to-xml-c"></a><span data-ttu-id="d1956-102">Instrukcje: Filtruj według nazw elementów (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="d1956-102">How to: Filter on Element Names (LINQ to XML) (C#)</span></span>
<span data-ttu-id="d1956-103">Po wywołaniu jednej z metod zwracanych <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement>przez, można filtrować według nazwy elementu.</span><span class="sxs-lookup"><span data-stu-id="d1956-103">When you call one of the methods that return <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, you can filter on the element name.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d1956-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="d1956-104">Example</span></span>  
 <span data-ttu-id="d1956-105">Ten przykład pobiera kolekcję elementów podrzędnych, które są filtrowane w celu zawiera tylko elementy podrzędne o określonej nazwie.</span><span class="sxs-lookup"><span data-stu-id="d1956-105">This example retrieves a collection of descendants that is filtered to contain only descendants with the specified name.</span></span>  
  
 <span data-ttu-id="d1956-106">W tym przykładzie zastosowano następujący dokument XML: [Przykładowy plik XML: Typowe zamówienie zakupu (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="d1956-106">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
```csharp  
XElement po = XElement.Load("PurchaseOrder.xml");  
IEnumerable<XElement> items =  
    from el in po.Descendants("ProductName")  
    select el;  
foreach(XElement prdName in items)  
    Console.WriteLine(prdName.Name + ":" + (string) prdName);  
```  
  
 <span data-ttu-id="d1956-107">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="d1956-107">This code produces the following output:</span></span>  
  
```  
ProductName:Lawnmower  
ProductName:Baby Monitor  
```  
  
 <span data-ttu-id="d1956-108">Inne metody, które zwracają <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> kolekcje, są zgodne z tym samym wzorcem.</span><span class="sxs-lookup"><span data-stu-id="d1956-108">The other methods that return <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement> collections follow the same pattern.</span></span> <span data-ttu-id="d1956-109">Ich podpisy są podobne <xref:System.Xml.Linq.XContainer.Elements%2A> do <xref:System.Xml.Linq.XContainer.Descendants%2A>i.</span><span class="sxs-lookup"><span data-stu-id="d1956-109">Their signatures are similar to <xref:System.Xml.Linq.XContainer.Elements%2A> and <xref:System.Xml.Linq.XContainer.Descendants%2A>.</span></span> <span data-ttu-id="d1956-110">Poniżej znajduje się kompletna lista metod, które mają podobne sygnatury metod:</span><span class="sxs-lookup"><span data-stu-id="d1956-110">The following is the complete list of methods that have similar method signatures:</span></span>  
  
- <xref:System.Xml.Linq.XNode.Ancestors%2A>  
  
- <xref:System.Xml.Linq.XContainer.Descendants%2A>  
  
- <xref:System.Xml.Linq.XContainer.Elements%2A>  
  
- <xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A>  
  
- <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>  
  
- <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>  
  
- <xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A>  
  
## <a name="example"></a><span data-ttu-id="d1956-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="d1956-111">Example</span></span>  
 <span data-ttu-id="d1956-112">W poniższym przykładzie pokazano to samo zapytanie dla kodu XML, który znajduje się w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="d1956-112">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="d1956-113">Aby uzyskać więcej informacji, zobacz temat [przestrzenie nazw —C#omówienie (LINQ to XML) ()](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="d1956-113">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="d1956-114">W tym przykładzie zastosowano następujący dokument XML: [Przykładowy plik XML: Typowe zamówienie zakupu w przestrzeni nazw](./sample-xml-file-typical-purchase-order-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="d1956-114">This example uses the following XML document: [Sample XML File: Typical Purchase Order in a Namespace](./sample-xml-file-typical-purchase-order-in-a-namespace.md).</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement po = XElement.Load("PurchaseOrderInNamespace.xml");  
IEnumerable<XElement> items =  
    from el in po.Descendants(aw + "ProductName")  
    select el;  
foreach (XElement prdName in items)  
    Console.WriteLine(prdName.Name + ":" + (string)prdName);  
```  
  
 <span data-ttu-id="d1956-115">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="d1956-115">This code produces the following output:</span></span>  
  
```  
{http://www.adventure-works.com}ProductName:Lawnmower  
{http://www.adventure-works.com}ProductName:Baby Monitor  
```  
  
## <a name="see-also"></a><span data-ttu-id="d1956-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d1956-116">See also</span></span>

- [<span data-ttu-id="d1956-117">Osie LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="d1956-117">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
