---
title: 'Instrukcje: Znajdowanie wszystkich węzłów w przestrzeni nazw (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: b735d7da-5727-48a3-ab57-a16378adc32e
ms.openlocfilehash: 5ccc996aa986c97fdffb3deeea36346da726a588
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/10/2019
ms.locfileid: "72249930"
---
# <a name="how-to-find-all-nodes-in-a-namespace-visual-basic"></a><span data-ttu-id="36c20-102">Instrukcje: Znajdowanie wszystkich węzłów w przestrzeni nazw (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="36c20-102">How to: Find All Nodes in a Namespace (Visual Basic)</span></span>
<span data-ttu-id="36c20-103">Można filtrować według przestrzeni nazw każdego elementu lub atrybutu, aby znaleźć wszystkie węzły w danej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="36c20-103">You can filter on the namespace of each element or attribute to find all nodes in that particular namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="36c20-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="36c20-104">Example</span></span>  
 <span data-ttu-id="36c20-105">Poniższy przykład tworzy drzewo XML z dwoma przestrzeniami nazw.</span><span class="sxs-lookup"><span data-stu-id="36c20-105">The following example creates an XML tree with two namespaces.</span></span> <span data-ttu-id="36c20-106">Następnie wykonuje iterację w drzewie i drukuje nazwy wszystkich elementów i atrybutów w jednej z tych przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="36c20-106">It then iterates through the tree and prints the names of all the elements and attributes in one of those namespaces.</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
Imports <xmlns:fc="www.fourthcoffee.com">  
  
Module Module1  
    Sub Main()  
        Dim xmlTree As XElement = _  
            <aw:Root>  
                <fc:Child1>abc</fc:Child1>  
                <fc:Child2>def</fc:Child2>  
                <aw:Child3>ghi</aw:Child3>  
                <fc:Child4>  
                    <fc:GrandChild1>jkl</fc:GrandChild1>  
                    <aw:GrandChild2>mno</aw:GrandChild2>  
                </fc:Child4>  
            </aw:Root>  
        Console.WriteLine("Nodes in the http://www.adventure-works.com namespace")  
        Dim awElements As IEnumerable(Of XElement) = _  
            From el In xmlTree.Descendants() _  
            Where (el.Name.Namespace = GetXmlNamespace(aw)) _  
            Select el  
        For Each el As XElement In awElements  
            Console.WriteLine(el.Name.ToString())  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="36c20-107">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="36c20-107">This code produces the following output:</span></span>  
  
```console  
Nodes in the http://www.adventure-works.com namespace  
{http://www.adventure-works.com}Child3  
{http://www.adventure-works.com}GrandChild2  
```  
  
## <a name="example"></a><span data-ttu-id="36c20-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="36c20-108">Example</span></span>  
 <span data-ttu-id="36c20-109">Plik XML, do którego uzyskuje się następujące zapytanie, zawiera zamówienia zakupu w dwóch różnych przestrzeniach nazw.</span><span class="sxs-lookup"><span data-stu-id="36c20-109">The XML file accessed by the following query contains purchase orders in two different namespaces.</span></span> <span data-ttu-id="36c20-110">Zapytanie tworzy nowe drzewo zawierające tylko elementy w jednej z przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="36c20-110">The query creates a new tree with just the elements in one of the namespaces.</span></span>  
  
 <span data-ttu-id="36c20-111">W tym przykładzie zastosowano następujący dokument XML: [przykładowy plik XML: skonsolidowane zamówienia zakupu](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-consolidated-purchase-orders.md).</span><span class="sxs-lookup"><span data-stu-id="36c20-111">This example uses the following XML document: [Sample XML File: Consolidated Purchase Orders](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-consolidated-purchase-orders.md).</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim cpo As XDocument = XDocument.Load("ConsolidatedPurchaseOrders.xml")  
        Dim newTree As XElement = _  
            <Root>  
                <%= From el In cpo.Root.Elements() _  
                    Where el.Name.Namespace = GetXmlNamespace(aw) _  
                    Select el %>  
            </Root>  
        Console.WriteLine(newTree)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="36c20-112">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="36c20-112">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <aw:PurchaseOrder PONumber="11223" Date="2000-01-15" xmlns:aw="http://www.adventure-works.com">  
    <aw:ShippingAddress>  
      <aw:Name>Chris Preston</aw:Name>  
      <aw:Street>123 Main St.</aw:Street>  
      <aw:City>Seattle</aw:City>  
      <aw:State>WA</aw:State>  
      <aw:Zip>98113</aw:Zip>  
      <aw:Country>USA</aw:Country>  
    </aw:ShippingAddress>  
    <aw:BillingAddress>  
      <aw:Name>Chris Preston</aw:Name>  
      <aw:Street>123 Main St.</aw:Street>  
      <aw:City>Seattle</aw:City>  
      <aw:State>WA</aw:State>  
      <aw:Zip>98113</aw:Zip>  
      <aw:Country>USA</aw:Country>  
    </aw:BillingAddress>  
    <aw:DeliveryInstructions>Ship only complete order.</aw:DeliveryInstructions>  
    <aw:Item PartNum="LIT-01">  
      <aw:ProductID>Litware Networking Card</aw:ProductID>  
      <aw:Qty>1</aw:Qty>  
      <aw:Price>20.99</aw:Price>  
    </aw:Item>  
    <aw:Item PartNum="LIT-25">  
      <aw:ProductID>Litware 17in LCD Monitor</aw:ProductID>  
      <aw:Qty>1</aw:Qty>  
      <aw:Price>199.99</aw:Price>  
    </aw:Item>  
  </aw:PurchaseOrder>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="36c20-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="36c20-113">See also</span></span>

- [<span data-ttu-id="36c20-114">Zapytania podstawowe (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="36c20-114">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
