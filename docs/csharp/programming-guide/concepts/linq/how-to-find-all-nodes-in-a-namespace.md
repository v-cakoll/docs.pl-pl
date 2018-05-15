---
title: 'Porady: znajdowanie wszystkich węzłów w Namespace (C#)'
ms.date: 07/20/2015
ms.assetid: 3a38b913-a53e-4d0e-a19d-8782bffd3364
ms.openlocfilehash: b22acdd7c2d64316e802c4dd01876a61141c8979
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-find-all-nodes-in-a-namespace-c"></a><span data-ttu-id="019d7-102">Porady: znajdowanie wszystkich węzłów w Namespace (C#)</span><span class="sxs-lookup"><span data-stu-id="019d7-102">How to: Find All Nodes in a Namespace (C#)</span></span>
<span data-ttu-id="019d7-103">Można filtrować według nazw każdego elementu lub atrybutu, aby znaleźć wszystkie węzły w tego określonego obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="019d7-103">You can filter on the namespace of each element or attribute to find all nodes in that particular namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="019d7-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="019d7-104">Example</span></span>  
 <span data-ttu-id="019d7-105">Poniższy przykład tworzy drzewo XML z dwoma obszarami nazw.</span><span class="sxs-lookup"><span data-stu-id="019d7-105">The following example creates an XML tree with two namespaces.</span></span> <span data-ttu-id="019d7-106">Następnie iteruje drzewa i wyświetla nazwy wszystkich elementów i atrybutów w jednym z tych obszarów nazw.</span><span class="sxs-lookup"><span data-stu-id="019d7-106">It then iterates through the tree and prints the names of all the elements and attributes in one of those namespaces.</span></span>  
  
```csharp  
string markup = @"<aw:Root xmlns:aw='http://www.adventure-works.com' xmlns:fc='www.fourthcoffee.com'>  
  <fc:Child1>abc</fc:Child1>  
  <fc:Child2>def</fc:Child2>  
  <aw:Child3>ghi</aw:Child3>  
  <fc:Child4>  
    <fc:GrandChild1>jkl</fc:GrandChild1>  
    <aw:GrandChild2>mno</aw:GrandChild2>  
  </fc:Child4>  
</aw:Root>";  
XElement xmlTree = XElement.Parse(markup);  
Console.WriteLine("Nodes in the http://www.adventure-works.com namespace");  
IEnumerable<XElement> awElements =  
    from el in xmlTree.Descendants()  
    where el.Name.Namespace == "http://www.adventure-works.com"  
    select el;  
foreach (XElement el in awElements)  
    Console.WriteLine(el.Name.ToString());  
```  
  
 <span data-ttu-id="019d7-107">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="019d7-107">This code produces the following output:</span></span>  
  
```  
Nodes in the http://www.adventure-works.com namespace  
{http://www.adventure-works.com}Child3  
{http://www.adventure-works.com}GrandChild2  
```  
  
## <a name="example"></a><span data-ttu-id="019d7-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="019d7-108">Example</span></span>  
 <span data-ttu-id="019d7-109">Plik XML używane przez następujące zapytanie zawiera zakupów w dwóch różnych przestrzeniach nazw.</span><span class="sxs-lookup"><span data-stu-id="019d7-109">The XML file accessed by the following query contains purchase orders in two different namespaces.</span></span> <span data-ttu-id="019d7-110">Zapytanie tworzy nowe drzewo tylko elementy w jednej z przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="019d7-110">The query creates a new tree with just the elements in one of the namespaces.</span></span>  
  
 <span data-ttu-id="019d7-111">W tym przykładzie użyto następujących dokumentu XML: [przykładowego pliku XML: skonsolidowane zakupów](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-consolidated-purchase-orders.md).</span><span class="sxs-lookup"><span data-stu-id="019d7-111">This example uses the following XML document: [Sample XML File: Consolidated Purchase Orders](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-consolidated-purchase-orders.md).</span></span>  
  
```csharp  
XDocument cpo = XDocument.Load("ConsolidatedPurchaseOrders.xml");  
XNamespace aw = "http://www.adventure-works.com";  
XElement newTree = new XElement("Root",  
    from el in cpo.Root.Elements()  
    where el.Name.Namespace == aw  
    select el  
);  
Console.WriteLine(newTree);  
```  
  
 <span data-ttu-id="019d7-112">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="019d7-112">This code produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="019d7-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="019d7-113">See Also</span></span>  
 [<span data-ttu-id="019d7-114">Podstawowe zapytania (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="019d7-114">Basic Queries (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
