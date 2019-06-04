---
title: 'Przykładowy plik XML: Typowe zamówienie zakupu w {1 & gt'
ms.date: 07/20/2015
ms.assetid: 84dc3339-ea32-4ccc-9af6-ab38ddfecced
ms.openlocfilehash: f47761409a0a174317259eea9b2d3a16c9fb2396
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66487194"
---
# <a name="sample-xml-file-typical-purchase-order-in-a-namespace"></a><span data-ttu-id="8b47c-102">Przykładowy plik XML: typowe zamówienie zakupu w przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="8b47c-102">Sample XML File: Typical Purchase Order in a Namespace</span></span>
<span data-ttu-id="8b47c-103">Następujący plik XML jest używany w różne przykłady w [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="8b47c-103">The following XML file is used in various examples in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] documentation.</span></span> <span data-ttu-id="8b47c-104">Ten plik ma typowe zamówienie zakupu.</span><span class="sxs-lookup"><span data-stu-id="8b47c-104">This file is a typical purchase order.</span></span> <span data-ttu-id="8b47c-105">Kod XML jest w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="8b47c-105">The XML is in a namespace.</span></span>  
  
## <a name="purchaseorderinnamespacexml"></a><span data-ttu-id="8b47c-106">PurchaseOrderInNamespace.xml</span><span class="sxs-lookup"><span data-stu-id="8b47c-106">PurchaseOrderInNamespace.xml</span></span>  
  
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
 