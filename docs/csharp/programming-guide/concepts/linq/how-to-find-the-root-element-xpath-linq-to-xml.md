---
title: 'Instrukcje: Znajdź element główny (XPath-LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 4fd824e0-4d39-429b-b092-f6a5c046ee6c
ms.openlocfilehash: d53fbaf089e54d50422e39cd047ee960bc8e46c3
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253598"
---
# <a name="how-to-find-the-root-element-xpath-linq-to-xml-c"></a><span data-ttu-id="8e653-102">Instrukcje: Znajdź element główny (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="8e653-102">How to: Find the Root Element (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="8e653-103">W tym temacie pokazano, jak uzyskać element główny przy użyciu XPath [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]i.</span><span class="sxs-lookup"><span data-stu-id="8e653-103">This topic shows how to get the root element with XPath and [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="8e653-104">Wyrażenie XPath:</span><span class="sxs-lookup"><span data-stu-id="8e653-104">The XPath expression is:</span></span>  
  
 `/PurchaseOrders`  
  
## <a name="example"></a><span data-ttu-id="8e653-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="8e653-105">Example</span></span>  
 <span data-ttu-id="8e653-106">Ten przykład umożliwia znalezienie elementu głównego.</span><span class="sxs-lookup"><span data-stu-id="8e653-106">This example finds the root element.</span></span>  
  
 <span data-ttu-id="8e653-107">W tym przykładzie zastosowano następujący dokument XML: [Przykładowy plik XML: Wiele zamówień zakupu (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="8e653-107">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="8e653-108">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="8e653-108">This example produces the following output:</span></span>  
  
```output  
Results are identical  
PurchaseOrders  
```  
