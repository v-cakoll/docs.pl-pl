---
title: 'Porady: znajdowanie elementu podrzędnego (XPath-LINQ do XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 4fa6182d-6196-4ed1-9c9e-82949ff89c71
ms.openlocfilehash: 769b0fd2a3c0e2de64342550f8adb52ef177ad96
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-find-a-child-element-xpath-linq-to-xml-c"></a><span data-ttu-id="2e9ea-102">Porady: znajdowanie elementu podrzędnego (XPath-LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="2e9ea-102">How to: Find a Child Element (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="2e9ea-103">W tym temacie porównuje osi elementu podrzędnego XPath do [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Element%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="2e9ea-103">This topic compares the XPath child element axis to the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Element%2A> method.</span></span>  
  
 <span data-ttu-id="2e9ea-104">Wyrażenie XPath jest `DeliveryNotes`.</span><span class="sxs-lookup"><span data-stu-id="2e9ea-104">The XPath expression is `DeliveryNotes`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2e9ea-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="2e9ea-105">Example</span></span>  
 <span data-ttu-id="2e9ea-106">W tym przykładzie znajduje element podrzędny `DeliveryNotes`.</span><span class="sxs-lookup"><span data-stu-id="2e9ea-106">This example finds the child element `DeliveryNotes`.</span></span>  
  
 <span data-ttu-id="2e9ea-107">W tym przykładzie użyto następujących dokumentu XML: [przykładowego pliku XML: wiele zakupów (LINQ do XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="2e9ea-107">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
```csharp  
XDocument cpo = XDocument.Load("PurchaseOrders.xml");  
XElement po = cpo.Root.Element("PurchaseOrder");  
  
// LINQ to XML query  
XElement el1 = po.Element("DeliveryNotes");  
  
// XPath expression  
XElement el2 = po.XPathSelectElement("DeliveryNotes");  
// same as "child::DeliveryNotes"  
// same as "./DeliveryNotes"  
  
if (el1 == el2)  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
Console.WriteLine(el1);  
```  
  
 <span data-ttu-id="2e9ea-108">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="2e9ea-108">This example produces the following output:</span></span>  
  
```  
Results are identical  
<DeliveryNotes>Please leave packages in shed by driveway.</DeliveryNotes>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2e9ea-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2e9ea-109">See Also</span></span>  
 [<span data-ttu-id="2e9ea-110">LINQ do XML dla użytkowników XPath (C#)</span><span class="sxs-lookup"><span data-stu-id="2e9ea-110">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
