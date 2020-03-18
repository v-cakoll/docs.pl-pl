---
title: Jak znaleźć element z określonym atrybutem (C#)
ms.date: 07/20/2015
ms.assetid: b92591aa-3cfb-490e-99f6-da8de335e362
ms.openlocfilehash: 106885b8658c493caab3101e6b4ce921589076eb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141160"
---
# <a name="how-to-find-an-element-with-a-specific-attribute-c"></a><span data-ttu-id="56e1e-102">Jak znaleźć element z określonym atrybutem (C#)</span><span class="sxs-lookup"><span data-stu-id="56e1e-102">How to find an element with a specific attribute (C#)</span></span>
<span data-ttu-id="56e1e-103">W tym temacie pokazano, jak znaleźć element, który ma atrybut, który ma określoną wartość.</span><span class="sxs-lookup"><span data-stu-id="56e1e-103">This topic shows how to find an element that has an attribute that has a specific value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="56e1e-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="56e1e-104">Example</span></span>  
 <span data-ttu-id="56e1e-105">W przykładzie pokazano, `Address` jak znaleźć `Type` element, który ma atrybut o wartości "Billing".</span><span class="sxs-lookup"><span data-stu-id="56e1e-105">The example shows how to find the `Address` element that has a `Type` attribute with a value of "Billing".</span></span>  
  
 <span data-ttu-id="56e1e-106">W tym przykładzie użyto następującego dokumentu XML: [Przykładowy plik XML: Typowe zamówienie zakupu (LINQ do XML).](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md)</span><span class="sxs-lookup"><span data-stu-id="56e1e-106">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("PurchaseOrder.xml");  
IEnumerable<XElement> address =  
    from el in root.Elements("Address")  
    where (string)el.Attribute("Type") == "Billing"  
    select el;  
foreach (XElement el in address)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="56e1e-107">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="56e1e-107">This code produces the following output:</span></span>  
  
```xml  
<Address Type="Billing">  
  <Name>Tai Yee</Name>  
  <Street>8 Oak Avenue</Street>  
  <City>Old Town</City>  
  <State>PA</State>  
  <Zip>95819</Zip>  
  <Country>USA</Country>  
</Address>  
```  
  
## <a name="example"></a><span data-ttu-id="56e1e-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="56e1e-108">Example</span></span>  
 <span data-ttu-id="56e1e-109">W poniższym przykładzie przedstawiono tę samą kwerendę dla języka XML, która znajduje się w obszarze nazw.</span><span class="sxs-lookup"><span data-stu-id="56e1e-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="56e1e-110">Aby uzyskać więcej informacji, zobacz [Omówienie przestrzeni nazw (LINQ do XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="56e1e-110">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="56e1e-111">W tym przykładzie użyto następującego dokumentu XML: [Przykładowy plik XML: Typowe zamówienie zakupu w obszarze nazw](./sample-xml-file-typical-purchase-order-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="56e1e-111">This example uses the following XML document: [Sample XML File: Typical Purchase Order in a Namespace](./sample-xml-file-typical-purchase-order-in-a-namespace.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("PurchaseOrderInNamespace.xml");  
XNamespace aw = "http://www.adventure-works.com";  
IEnumerable<XElement> address =  
    from el in root.Elements(aw + "Address")  
    where (string)el.Attribute(aw + "Type") == "Billing"  
    select el;  
foreach (XElement el in address)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="56e1e-112">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="56e1e-112">This code produces the following output:</span></span>  
  
```xml  
<aw:Address aw:Type="Billing" xmlns:aw="http://www.adventure-works.com">  
  <aw:Name>Tai Yee</aw:Name>  
  <aw:Street>8 Oak Avenue</aw:Street>  
  <aw:City>Old Town</aw:City>  
  <aw:State>PA</aw:State>  
  <aw:Zip>95819</aw:Zip>  
  <aw:Country>USA</aw:Country>  
</aw:Address>  
```  
  
## <a name="see-also"></a><span data-ttu-id="56e1e-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="56e1e-113">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [<span data-ttu-id="56e1e-114">Omówienie standardowych operatorów zapytań (C#)</span><span class="sxs-lookup"><span data-stu-id="56e1e-114">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="56e1e-115">Operacje projekcji (C#)</span><span class="sxs-lookup"><span data-stu-id="56e1e-115">Projection Operations (C#)</span></span>](./projection-operations.md)
