---
title: "Porady: znajdowanie elementu podrzędnego (XPath-LINQ do XML) (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: adb46c98-a650-42e2-b62d-835920fe8421
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0929807c2f915be64f553be7a3aa669db6981f70
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-find-a-child-element-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="4cf6e-102">Porady: znajdowanie elementu podrzędnego (XPath-LINQ do XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4cf6e-102">How to: Find a Child Element (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="4cf6e-103">W tym temacie porównuje osi elementu podrzędnego XPath do [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Element%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="4cf6e-103">This topic compares the XPath child element axis to the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Element%2A> method.</span></span>  
  
 <span data-ttu-id="4cf6e-104">Wyrażenie XPath jest `DeliveryNotes`.</span><span class="sxs-lookup"><span data-stu-id="4cf6e-104">The XPath expression is `DeliveryNotes`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4cf6e-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="4cf6e-105">Example</span></span>  
 <span data-ttu-id="4cf6e-106">W tym przykładzie znajduje element podrzędny `DeliveryNotes`.</span><span class="sxs-lookup"><span data-stu-id="4cf6e-106">This example finds the child element `DeliveryNotes`.</span></span>  
  
 <span data-ttu-id="4cf6e-107">W tym przykładzie użyto następujących dokumentu XML: [przykładowego pliku XML: wiele zakupów (LINQ do XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="4cf6e-107">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
```vb  
Dim cpo As XDocument = XDocument.Load("PurchaseOrders.xml")  
Dim po As XElement = cpo.Root.<PurchaseOrder>.FirstOrDefault  
  
'LINQ to XML query  
Dim el1 As XElement = po.<DeliveryNotes>.FirstOrDefault  
  
' XPath expression  
Dim el2 As XElement = po.XPathSelectElement("DeliveryNotes")  
' same as "child::DeliveryNotes"  
' same as "./DeliveryNotes"  
  
If el1 Is el2 Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
Console.WriteLine(el1)  
```  
  
 <span data-ttu-id="4cf6e-108">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="4cf6e-108">This example produces the following output:</span></span>  
  
```  
Results are identical  
<DeliveryNotes>Please leave packages in shed by driveway.</DeliveryNotes>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4cf6e-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4cf6e-109">See Also</span></span>  
 [<span data-ttu-id="4cf6e-110">LINQ do XML dla wyrażenia XPath użytkowników (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4cf6e-110">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
