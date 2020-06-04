---
title: 'Przykładowy plik XML: typowe zamówienie zakupu (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 65321b9c-1239-45e4-af40-eb86cedf7abd
ms.openlocfilehash: ed209a9a32b909a36e511a06543de75e780ea5b3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84360712"
---
# <a name="sample-xml-file-typical-purchase-order-linq-to-xml"></a><span data-ttu-id="5d03e-102">Przykładowy plik XML: typowe zamówienie zakupu (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="5d03e-102">Sample XML File: Typical Purchase Order (LINQ to XML)</span></span>
<span data-ttu-id="5d03e-103">Następujący plik XML jest używany w różnych przykładach w [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="5d03e-103">The following XML file is used in various examples in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] documentation.</span></span> <span data-ttu-id="5d03e-104">Ten plik jest typowym porządkiem zakupu.</span><span class="sxs-lookup"><span data-stu-id="5d03e-104">This file is a typical purchase order.</span></span>  
  
## <a name="purchaseorderxml"></a><span data-ttu-id="5d03e-105">PurchaseOrder. XML</span><span class="sxs-lookup"><span data-stu-id="5d03e-105">PurchaseOrder.xml</span></span>  
  
```xml  
<?xml version="1.0"?>  
<PurchaseOrder PurchaseOrderNumber="99503" OrderDate="1999-10-20">  
  <Address Type="Shipping">  
    <Name>Ellen Adams</Name>  
    <Street>123 Maple Street</Street>  
    <City>Mill Valley</City>  
    <State>CA</State>  
    <Zip>10999</Zip>  
    <Country>USA</Country>  
  </Address>  
  <Address Type="Billing">  
    <Name>Tai Yee</Name>  
    <Street>8 Oak Avenue</Street>  
    <City>Old Town</City>  
    <State>PA</State>  
    <Zip>95819</Zip>  
    <Country>USA</Country>  
  </Address>  
  <DeliveryNotes>Please leave packages in shed by driveway.</DeliveryNotes>  
  <Items>  
    <Item PartNumber="872-AA">  
      <ProductName>Lawnmower</ProductName>  
      <Quantity>1</Quantity>  
      <USPrice>148.95</USPrice>  
      <Comment>Confirm this is electric</Comment>  
    </Item>  
    <Item PartNumber="926-AA">  
      <ProductName>Baby Monitor</ProductName>  
      <Quantity>2</Quantity>  
      <USPrice>39.98</USPrice>  
      <ShipDate>1999-05-21</ShipDate>  
    </Item>  
  </Items>  
</PurchaseOrder>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5d03e-106">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5d03e-106">See also</span></span>

- [<span data-ttu-id="5d03e-107">Przykładowe dokumenty XML (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="5d03e-107">Sample XML Documents (LINQ to XML)</span></span>](sample-xml-documents-linq-to-xml.md)
