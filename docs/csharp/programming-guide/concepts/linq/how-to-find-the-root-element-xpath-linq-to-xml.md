---
title: 'Porady: znajdowanie elementem głównym (XPath-LINQ do XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 4fd824e0-4d39-429b-b092-f6a5c046ee6c
ms.openlocfilehash: a7c15c8eb688f70b2d1633fc5c094b02cc97031c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-find-the-root-element-xpath-linq-to-xml-c"></a><span data-ttu-id="5bc39-102">Porady: znajdowanie elementem głównym (XPath-LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="5bc39-102">How to: Find the Root Element (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="5bc39-103">W tym temacie pokazano, jak uzyskać elementu głównego z XPath i [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5bc39-103">This topic shows how to get the root element with XPath and [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="5bc39-104">Wyrażenie XPath jest:</span><span class="sxs-lookup"><span data-stu-id="5bc39-104">The XPath expression is:</span></span>  
  
 `/PurchaseOrders`  
  
## <a name="example"></a><span data-ttu-id="5bc39-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="5bc39-105">Example</span></span>  
 <span data-ttu-id="5bc39-106">W tym przykładzie znajduje elementu głównego.</span><span class="sxs-lookup"><span data-stu-id="5bc39-106">This example finds the root element.</span></span>  
  
 <span data-ttu-id="5bc39-107">W tym przykładzie użyto następujących dokumentu XML: [przykładowego pliku XML: wiele zakupów (LINQ do XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="5bc39-107">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="5bc39-108">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="5bc39-108">This example produces the following output:</span></span>  
  
```  
Results are identical  
PurchaseOrders  
```  
  
## <a name="see-also"></a><span data-ttu-id="5bc39-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5bc39-109">See Also</span></span>  
 [<span data-ttu-id="5bc39-110">LINQ do XML dla użytkowników XPath (C#)</span><span class="sxs-lookup"><span data-stu-id="5bc39-110">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
