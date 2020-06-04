---
title: 'Instrukcje: wyszukiwanie listy elementów podrzędnych (XPath-LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 2868abfd-9f7b-412a-9cb5-f643f0fed146
ms.openlocfilehash: d03b89f93fede3abd2d482c01979e93876d60c0b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410776"
---
# <a name="how-to-find-a-list-of-child-elements-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="69e0b-102">Instrukcje: Znajdowanie listy elementów podrzędnych (XPath-LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="69e0b-102">How to: Find a List of Child Elements (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="69e0b-103">W tym temacie porównano oś elementów podrzędnych XPath z [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Elements%2A> osią.</span><span class="sxs-lookup"><span data-stu-id="69e0b-103">This topic compares the XPath child elements axis to the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Elements%2A> axis.</span></span>  
  
 <span data-ttu-id="69e0b-104">Wyrażenie XPath:`./*`</span><span class="sxs-lookup"><span data-stu-id="69e0b-104">The XPath expression is: `./*`</span></span>  
  
## <a name="example"></a><span data-ttu-id="69e0b-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="69e0b-105">Example</span></span>  
 <span data-ttu-id="69e0b-106">Ten przykład umożliwia znalezienie wszystkich elementów podrzędnych `Address` elementu.</span><span class="sxs-lookup"><span data-stu-id="69e0b-106">This example finds all of the child elements of the `Address` element.</span></span>  
  
 <span data-ttu-id="69e0b-107">W tym przykładzie zastosowano następujący dokument XML: [przykładowy plik XML: wiele zamówień zakupu (LINQ to XML)](sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="69e0b-107">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
```vb  
Dim cpo As XDocument = XDocument.Load("PurchaseOrders.xml")  
Dim po As XElement = cpo.Root.<PurchaseOrder>.<Address>.FirstOrDefault  
  
' LINQ to XML query  
Dim list1 As IEnumerable(Of XElement) = po.Elements()  
  
' XPath expression  
Dim list2 As IEnumerable(Of XElement) = po.XPathSelectElements("./*")  
  
If (list1.Count() = list2.Count()) AndAlso _  
    (list1.Intersect(list2).Count() = list1.Count()) Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
For Each el As XElement In list1  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="69e0b-108">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="69e0b-108">This example produces the following output:</span></span>  
  
```console
Results are identical  
<Name>Ellen Adams</Name>  
<Street>123 Maple Street</Street>  
<City>Mill Valley</City>  
<State>CA</State>  
<Zip>10999</Zip>  
<Country>USA</Country>  
```  
  
## <a name="see-also"></a><span data-ttu-id="69e0b-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="69e0b-109">See also</span></span>

- [<span data-ttu-id="69e0b-110">LINQ to XML dla użytkowników XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="69e0b-110">LINQ to XML for XPath Users (Visual Basic)</span></span>](linq-to-xml-for-xpath-users.md)
