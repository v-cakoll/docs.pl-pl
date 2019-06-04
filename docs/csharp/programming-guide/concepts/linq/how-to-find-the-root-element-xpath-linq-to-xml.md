---
title: 'Instrukcje: Wyszukiwanie elementu głównego (XPath-LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 4fd824e0-4d39-429b-b092-f6a5c046ee6c
ms.openlocfilehash: 59696e6f3487bbb09135ba413a173c32dffa0c9b
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66485414"
---
# <a name="how-to-find-the-root-element-xpath-linq-to-xml-c"></a><span data-ttu-id="9d6ec-102">Instrukcje: Wyszukiwanie elementu głównego (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="9d6ec-102">How to: Find the Root Element (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="9d6ec-103">W tym temacie pokazano, jak uzyskać element główny za pomocą wyrażenia XPath i [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9d6ec-103">This topic shows how to get the root element with XPath and [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="9d6ec-104">Wyrażenie XPath jest:</span><span class="sxs-lookup"><span data-stu-id="9d6ec-104">The XPath expression is:</span></span>  
  
 `/PurchaseOrders`  
  
## <a name="example"></a><span data-ttu-id="9d6ec-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="9d6ec-105">Example</span></span>  
 <span data-ttu-id="9d6ec-106">W tym przykładzie wyszukuje element główny.</span><span class="sxs-lookup"><span data-stu-id="9d6ec-106">This example finds the root element.</span></span>  
  
 <span data-ttu-id="9d6ec-107">W tym przykładzie użyto następujący dokument XML: [Przykładowy plik XML: Wiele zamówień zakupu (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="9d6ec-107">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="9d6ec-108">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="9d6ec-108">This example produces the following output:</span></span>  
  
```  
Results are identical  
PurchaseOrders  
```  
