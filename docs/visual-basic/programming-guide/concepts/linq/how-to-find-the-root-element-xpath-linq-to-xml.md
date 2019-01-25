---
title: 'Instrukcje: Wyszukiwanie elementu głównego (XPath-LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 72c3aed5-9522-4454-a876-2070aad13f2e
ms.openlocfilehash: 6a08817c16bafb2ba1f91931f9718d6ef5053fb9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54687339"
---
# <a name="how-to-find-the-root-element-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="ee0f4-102">Instrukcje: Wyszukiwanie elementu głównego (XPath-LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ee0f4-102">How to: Find the Root Element (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="ee0f4-103">W tym temacie pokazano, jak uzyskać element główny za pomocą wyrażenia XPath i [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ee0f4-103">This topic shows how to get the root element with XPath and [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="ee0f4-104">Wyrażenie XPath jest:</span><span class="sxs-lookup"><span data-stu-id="ee0f4-104">The XPath expression is:</span></span>  
  
 `/PurchaseOrders`  
  
## <a name="example"></a><span data-ttu-id="ee0f4-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="ee0f4-105">Example</span></span>  
 <span data-ttu-id="ee0f4-106">W tym przykładzie wyszukuje element główny.</span><span class="sxs-lookup"><span data-stu-id="ee0f4-106">This example finds the root element.</span></span>  
  
 <span data-ttu-id="ee0f4-107">W tym przykładzie użyto następujący dokument XML: [Przykładowy plik XML: Wiele zamówień zakupu (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="ee0f4-107">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
```vb  
Dim po As XDocument = XDocument.Load("PurchaseOrders.xml")  
  
' LINQ to XML query  
Dim el1 As XElement = po.Root  
  
' XPath expression  
Dim el2 As XElement = po.XPathSelectElement("/PurchaseOrders")  
  
If el1 Is el2 Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
Console.WriteLine(el1.Name)  
```  
  
 <span data-ttu-id="ee0f4-108">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="ee0f4-108">This example produces the following output:</span></span>  
  
```  
Results are identical  
PurchaseOrders  
```  
  
## <a name="see-also"></a><span data-ttu-id="ee0f4-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ee0f4-109">See also</span></span>
- [<span data-ttu-id="ee0f4-110">LINQ to XML dla użytkowników metody XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ee0f4-110">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
