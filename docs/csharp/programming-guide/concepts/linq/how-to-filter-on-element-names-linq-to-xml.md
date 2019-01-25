---
title: 'Instrukcje: Filtrowanie nazw elementów (LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 1849fb03-f075-421f-863c-e8fb32773cdf
ms.openlocfilehash: 586c371fdd014eee6eb21563214d9e26a0e264fe
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54540783"
---
# <a name="how-to-filter-on-element-names-linq-to-xml-c"></a><span data-ttu-id="85c62-102">Instrukcje: Filtrowanie nazw elementów (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="85c62-102">How to: Filter on Element Names (LINQ to XML) (C#)</span></span>
<span data-ttu-id="85c62-103">Wywołanie jednej z metod, które zwracają <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement>, możesz przefiltrować listę według nazwy elementu.</span><span class="sxs-lookup"><span data-stu-id="85c62-103">When you call one of the methods that return <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, you can filter on the element name.</span></span>  
  
## <a name="example"></a><span data-ttu-id="85c62-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="85c62-104">Example</span></span>  
 <span data-ttu-id="85c62-105">W tym przykładzie pobiera kolekcję elementów podrzędnych, która jest filtrowana w celu uwzględnienia tylko elementów potomnych o określonej nazwie.</span><span class="sxs-lookup"><span data-stu-id="85c62-105">This example retrieves a collection of descendants that is filtered to contain only descendants with the specified name.</span></span>  
  
 <span data-ttu-id="85c62-106">W tym przykładzie użyto następujący dokument XML: [Przykładowy plik XML: Typowe zamówienie zakupu (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="85c62-106">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
```csharp  
XElement po = XElement.Load("PurchaseOrder.xml");  
IEnumerable<XElement> items =  
    from el in po.Descendants("ProductName")  
    select el;  
foreach(XElement prdName in items)  
    Console.WriteLine(prdName.Name + ":" + (string) prdName);  
```  
  
 <span data-ttu-id="85c62-107">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="85c62-107">This code produces the following output:</span></span>  
  
```  
ProductName:Lawnmower  
ProductName:Baby Monitor  
```  
  
 <span data-ttu-id="85c62-108">Metody, które zwracają <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> kolekcje postępuj zgodnie z tym samym wzorcem.</span><span class="sxs-lookup"><span data-stu-id="85c62-108">The other methods that return <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement> collections follow the same pattern.</span></span> <span data-ttu-id="85c62-109">Ich podpisy są podobne do <xref:System.Xml.Linq.XContainer.Elements%2A> i <xref:System.Xml.Linq.XContainer.Descendants%2A>.</span><span class="sxs-lookup"><span data-stu-id="85c62-109">Their signatures are similar to <xref:System.Xml.Linq.XContainer.Elements%2A> and <xref:System.Xml.Linq.XContainer.Descendants%2A>.</span></span> <span data-ttu-id="85c62-110">Oto Pełna lista metod, które mają podobne podpisy metod:</span><span class="sxs-lookup"><span data-stu-id="85c62-110">The following is the complete list of methods that have similar method signatures:</span></span>  
  
-   <xref:System.Xml.Linq.XNode.Ancestors%2A>  
  
-   <xref:System.Xml.Linq.XContainer.Descendants%2A>  
  
-   <xref:System.Xml.Linq.XContainer.Elements%2A>  
  
-   <xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A>  
  
-   <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>  
  
-   <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>  
  
-   <xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A>  
  
## <a name="example"></a><span data-ttu-id="85c62-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="85c62-111">Example</span></span>  
 <span data-ttu-id="85c62-112">Poniższy przykład pokazuje tego samego zapytania w formacie XML, który znajduje się w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="85c62-112">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="85c62-113">Aby uzyskać więcej informacji, zobacz [Praca z przestrzeniami nazw XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="85c62-113">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="85c62-114">W tym przykładzie użyto następujący dokument XML: [Przykładowy plik XML: Typowe zamówienie zakupu w Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="85c62-114">This example uses the following XML document: [Sample XML File: Typical Purchase Order in a Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md).</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement po = XElement.Load("PurchaseOrderInNamespace.xml");  
IEnumerable<XElement> items =  
    from el in po.Descendants(aw + "ProductName")  
    select el;  
foreach (XElement prdName in items)  
    Console.WriteLine(prdName.Name + ":" + (string)prdName);  
```  
  
 <span data-ttu-id="85c62-115">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="85c62-115">This code produces the following output:</span></span>  
  
```  
{http://www.adventure-works.com}ProductName:Lawnmower  
{http://www.adventure-works.com}ProductName:Baby Monitor  
```  
  
## <a name="see-also"></a><span data-ttu-id="85c62-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="85c62-116">See also</span></span>

- [<span data-ttu-id="85c62-117">LINQ do XML osi (C#)</span><span class="sxs-lookup"><span data-stu-id="85c62-117">LINQ to XML Axes (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
