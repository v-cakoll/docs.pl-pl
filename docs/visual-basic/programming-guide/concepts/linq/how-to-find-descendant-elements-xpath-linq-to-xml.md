---
title: 'Instrukcje: wyszukiwanie elementów potomnych (XPath-LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: e7e2dc9e-bda9-420d-a5b1-4fabf1cca46b
ms.openlocfilehash: ee67a54116a7d91f6cf6af179d6398a4dcece9c4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84405238"
---
# <a name="how-to-find-descendant-elements-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="54a8b-102">Instrukcje: Znajdowanie elementów potomnych (XPath-LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="54a8b-102">How to: Find Descendant Elements (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="54a8b-103">W tym temacie pokazano, jak uzyskać elementy podrzędne o określonej nazwie.</span><span class="sxs-lookup"><span data-stu-id="54a8b-103">This topic shows how to get the descendant elements with a particular name.</span></span>  
  
 <span data-ttu-id="54a8b-104">Wyrażenie XPath ma wartość `//Name` .</span><span class="sxs-lookup"><span data-stu-id="54a8b-104">The XPath expression is `//Name`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="54a8b-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="54a8b-105">Example</span></span>  
 <span data-ttu-id="54a8b-106">Ten przykład umożliwia znalezienie wszystkich elementów podrzędnych o nazwie `Name` .</span><span class="sxs-lookup"><span data-stu-id="54a8b-106">This example finds all descendants named `Name`.</span></span>  
  
 <span data-ttu-id="54a8b-107">W tym przykładzie zastosowano następujący dokument XML: [przykładowy plik XML: wiele zamówień zakupu (LINQ to XML)](sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="54a8b-107">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
```vb  
      Dim po As XDocument = XDocument.Load("PurchaseOrders.xml")  
  
' LINQ to XML query  
Dim list1 As IEnumerable(Of XElement) = po...<Name>  
  
' XPath expression  
Dim list2 As IEnumerable(Of XElement) = po.XPathSelectElements("//Name")  
  
If (list1.Count() = list2.Count() And _  
        list1.Intersect(list2).Count() = list1.Count()) Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
For Each el As XElement In list1  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="54a8b-108">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="54a8b-108">This example produces the following output:</span></span>  
  
```console
Results are identical  
<Name>Ellen Adams</Name>  
<Name>Tai Yee</Name>  
<Name>Cristian Osorio</Name>  
<Name>Cristian Osorio</Name>  
<Name>Jessica Arnold</Name>  
<Name>Jessica Arnold</Name>  
```  
  
## <a name="see-also"></a><span data-ttu-id="54a8b-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="54a8b-109">See also</span></span>

- [<span data-ttu-id="54a8b-110">LINQ to XML dla użytkowników XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="54a8b-110">LINQ to XML for XPath Users (Visual Basic)</span></span>](linq-to-xml-for-xpath-users.md)
