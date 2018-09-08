---
title: 'Porady: Wyszukiwanie elementu głównego (XPath-LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 4fd824e0-4d39-429b-b092-f6a5c046ee6c
ms.openlocfilehash: a0197a34f2e9d1b42a71d3c8cb1a4281ba495c4f
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44130737"
---
# <a name="how-to-find-the-root-element-xpath-linq-to-xml-c"></a><span data-ttu-id="e8a62-102">Porady: Wyszukiwanie elementu głównego (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="e8a62-102">How to: Find the Root Element (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="e8a62-103">W tym temacie pokazano, jak uzyskać element główny za pomocą wyrażenia XPath i [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e8a62-103">This topic shows how to get the root element with XPath and [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="e8a62-104">Wyrażenie XPath jest:</span><span class="sxs-lookup"><span data-stu-id="e8a62-104">The XPath expression is:</span></span>  
  
 `/PurchaseOrders`  
  
## <a name="example"></a><span data-ttu-id="e8a62-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="e8a62-105">Example</span></span>  
 <span data-ttu-id="e8a62-106">W tym przykładzie wyszukuje element główny.</span><span class="sxs-lookup"><span data-stu-id="e8a62-106">This example finds the root element.</span></span>  
  
 <span data-ttu-id="e8a62-107">W tym przykładzie użyto następujący dokument XML: [przykładowy plik XML: wiele zamówień zakupu (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="e8a62-107">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
// LINQ to XML query  
XElement el1 = po.Root;  
  
// XPath expression  
XElement el2 = po.XPathSelectElement("/PurchaseOrders");  
  
if (el1 == el2)  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
Console.WriteLine(el1.Name);  
```  
  
 <span data-ttu-id="e8a62-108">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="e8a62-108">This example produces the following output:</span></span>  
  
```  
Results are identical  
PurchaseOrders  
```  
  
## <a name="see-also"></a><span data-ttu-id="e8a62-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e8a62-109">See Also</span></span>

- [<span data-ttu-id="e8a62-110">LINQ to XML dla użytkowników metody XPath (C#)</span><span class="sxs-lookup"><span data-stu-id="e8a62-110">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
