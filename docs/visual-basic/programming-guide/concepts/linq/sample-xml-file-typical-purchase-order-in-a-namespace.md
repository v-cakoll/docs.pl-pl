---
title: 'Przykładowy plik XML: Typowe zamówienie w Namespace3'
ms.date: 07/20/2015
ms.assetid: 38260901-c9f9-4240-9cbf-652c8b05021d
ms.openlocfilehash: 94aa8d39b351a55183b7164bd4ceca875742f17d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="sample-xml-file-typical-purchase-order-in-a-namespace"></a><span data-ttu-id="be1de-102">Przykładowy plik XML: Typowe zamówienie w Namespace</span><span class="sxs-lookup"><span data-stu-id="be1de-102">Sample XML File: Typical Purchase Order in a Namespace</span></span>
<span data-ttu-id="be1de-103">Następujący plik XML jest używany w różnych przykłady w [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="be1de-103">The following XML file is used in various examples in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] documentation.</span></span> <span data-ttu-id="be1de-104">Ten plik jest typowy zakupu.</span><span class="sxs-lookup"><span data-stu-id="be1de-104">This file is a typical purchase order.</span></span> <span data-ttu-id="be1de-105">Plik XML jest w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="be1de-105">The XML is in a namespace.</span></span>  
  
## <a name="purchaseorderinnamespacexml"></a><span data-ttu-id="be1de-106">PurchaseOrderInNamespace.xml</span><span class="sxs-lookup"><span data-stu-id="be1de-106">PurchaseOrderInNamespace.xml</span></span>  
  
```xml  
<?xml version="1.0"?>  
<aw:PurchaseOrder  
    aw:PurchaseOrderNumber="99503"  
    aw:OrderDate="1999-10-20"  
    xmlns:aw="http://www.adventure-works.com">  
  <aw:Address aw:Type="Shipping">  
    <aw:Name>Ellen Adams</aw:Name>  
    <aw:Street>123 Maple Street</aw:Street>  
    <aw:City>Mill Valley</aw:City>  
    <aw:State>CA</aw:State>  
    <aw:Zip>10999</aw:Zip>  
    <aw:Country>USA</aw:Country>  
  </aw:Address>  
  <aw:Address aw:Type="Billing">  
    <aw:Name>Tai Yee</aw:Name>  
    <aw:Street>8 Oak Avenue</aw:Street>  
    <aw:City>Old Town</aw:City>  
    <aw:State>PA</aw:State>  
    <aw:Zip>95819</aw:Zip>  
    <aw:Country>USA</aw:Country>  
  </aw:Address>  
  <aw:DeliveryNotes>Please leave packages in shed by driveway.</aw:DeliveryNotes>  
  <aw:Items>  
    <aw:Item aw:PartNumber="872-AA">  
      <aw:ProductName>Lawnmower</aw:ProductName>  
      <aw:Quantity>1</aw:Quantity>  
      <aw:USPrice>148.95</aw:USPrice>  
      <aw:Comment>Confirm this is electric</aw:Comment>  
    </aw:Item>  
    <aw:Item aw:PartNumber="926-AA">  
      <aw:ProductName>Baby Monitor</aw:ProductName>  
      <aw:Quantity>2</aw:Quantity>  
      <aw:USPrice>39.98</aw:USPrice>  
      <aw:ShipDate>1999-05-21</aw:ShipDate>  
    </aw:Item>  
  </aw:Items>  
</aw:PurchaseOrder>  
```  
  
## <a name="see-also"></a><span data-ttu-id="be1de-107">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="be1de-107">See Also</span></span>  
 [<span data-ttu-id="be1de-108">Przykładowe dokumenty XML (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="be1de-108">Sample XML Documents (LINQ to XML)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-documents-linq-to-xml.md)
