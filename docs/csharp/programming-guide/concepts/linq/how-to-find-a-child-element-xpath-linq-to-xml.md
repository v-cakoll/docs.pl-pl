---
title: 'Instrukcje: Wyszukiwanie elementu podrzędnego (XPath-LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 4fa6182d-6196-4ed1-9c9e-82949ff89c71
ms.openlocfilehash: 4a6d18c86416f7c54df554bc2f518994446a2a84
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66485727"
---
# <a name="how-to-find-a-child-element-xpath-linq-to-xml-c"></a><span data-ttu-id="48adc-102">Instrukcje: Wyszukiwanie elementu podrzędnego (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="48adc-102">How to: Find a Child Element (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="48adc-103">W tym temacie porównano osi elementu podrzędnego XPath do [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Element%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="48adc-103">This topic compares the XPath child element axis to the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Element%2A> method.</span></span>  
  
 <span data-ttu-id="48adc-104">Wyrażenie XPath jest `DeliveryNotes`.</span><span class="sxs-lookup"><span data-stu-id="48adc-104">The XPath expression is `DeliveryNotes`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="48adc-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="48adc-105">Example</span></span>  
 <span data-ttu-id="48adc-106">W tym przykładzie wyszukuje element podrzędny `DeliveryNotes`.</span><span class="sxs-lookup"><span data-stu-id="48adc-106">This example finds the child element `DeliveryNotes`.</span></span>  
  
 <span data-ttu-id="48adc-107">W tym przykładzie użyto następujący dokument XML: [Przykładowy plik XML: Wiele zamówień zakupu (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="48adc-107">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="48adc-108">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="48adc-108">This example produces the following output:</span></span>  
  
```  
Results are identical  
<DeliveryNotes>Please leave packages in shed by driveway.</DeliveryNotes>  
```  
  