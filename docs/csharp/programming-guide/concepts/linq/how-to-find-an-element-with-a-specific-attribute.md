---
title: "Porady: znajdowanie Element z określonym atrybutem (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: b92591aa-3cfb-490e-99f6-da8de335e362
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4fc7fd7986b79109038bb4f653131d5256c14f04
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-find-an-element-with-a-specific-attribute-c"></a><span data-ttu-id="ca487-102">Porady: znajdowanie Element z określonym atrybutem (C#)</span><span class="sxs-lookup"><span data-stu-id="ca487-102">How to: Find an Element with a Specific Attribute (C#)</span></span>
<span data-ttu-id="ca487-103">W tym temacie pokazano, jak można znaleźć elementu, który ma atrybut o określonej wartości.</span><span class="sxs-lookup"><span data-stu-id="ca487-103">This topic shows how to find an element that has an attribute that has a specific value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ca487-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="ca487-104">Example</span></span>  
 <span data-ttu-id="ca487-105">W przykładzie pokazano, jak znaleźć `Address` element, który ma `Type` atrybutu o wartości "Billing".</span><span class="sxs-lookup"><span data-stu-id="ca487-105">The example shows how to find the `Address` element that has a `Type` attribute with a value of "Billing".</span></span>  
  
 <span data-ttu-id="ca487-106">W tym przykładzie użyto następujących dokumentu XML: [przykładowego pliku XML: typowe zamówienia zakupu (LINQ do XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="ca487-106">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("PurchaseOrder.xml");  
IEnumerable<XElement> address =  
    from el in root.Elements("Address")  
    where (string)el.Attribute("Type") == "Billing"  
    select el;  
foreach (XElement el in address)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="ca487-107">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="ca487-107">This code produces the following output:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="ca487-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="ca487-108">Example</span></span>  
 <span data-ttu-id="ca487-109">W poniższym przykładzie pokazano tego samego zapytania w formacie XML, który znajduje się w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="ca487-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="ca487-110">Aby uzyskać więcej informacji, zobacz [Praca z przestrzeni nazw XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="ca487-110">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="ca487-111">W tym przykładzie użyto następujących dokumentu XML: [przykładowego pliku XML: typowe zamówienia zakupu w Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="ca487-111">This example uses the following XML document: [Sample XML File: Typical Purchase Order in a Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md).</span></span>  
  
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
  
 <span data-ttu-id="ca487-112">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="ca487-112">This code produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ca487-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ca487-113">See Also</span></span>  
 <xref:System.Xml.Linq.XElement.Attribute%2A>  
 <xref:System.Xml.Linq.XContainer.Elements%2A>  
 [<span data-ttu-id="ca487-114">Podstawowe zapytania (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="ca487-114">Basic Queries (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)  
 [<span data-ttu-id="ca487-115">Operatory standardowe zapytań — omówienie (C#)</span><span class="sxs-lookup"><span data-stu-id="ca487-115">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="ca487-116">Operacje rzutowania (C#)</span><span class="sxs-lookup"><span data-stu-id="ca487-116">Projection Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projection-operations.md)
