---
title: 'Przykładowy plik XML: wiele zamówień zakupu (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 2d29fcaa-60df-43d4-8ccc-6cdba7c013e9
ms.openlocfilehash: d73887308c07b161887716ccf2194eeb3918ff51
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168144"
---
# <a name="sample-xml-file-multiple-purchase-orders-linq-to-xml"></a>Przykładowy plik XML: wiele zamówień zakupu (LINQ to XML)
Poniższy plik XML jest używany w [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] różnych przykładach w dokumentacji. Ten plik zawiera kilka zamówień zakupu.  
  
## <a name="purchaseordersxml"></a>Zamówienia zakupu.xml  
  
```xml  
<?xml version="1.0"?>  
<PurchaseOrders>  
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
  <PurchaseOrder PurchaseOrderNumber="99505" OrderDate="1999-10-22">  
    <Address Type="Shipping">  
      <Name>Cristian Osorio</Name>  
      <Street>456 Main Street</Street>  
      <City>Buffalo</City>  
      <State>NY</State>  
      <Zip>98112</Zip>  
      <Country>USA</Country>  
    </Address>  
    <Address Type="Billing">  
      <Name>Cristian Osorio</Name>  
      <Street>456 Main Street</Street>  
      <City>Buffalo</City>  
      <State>NY</State>  
      <Zip>98112</Zip>  
      <Country>USA</Country>  
    </Address>  
    <DeliveryNotes>Please notify me before shipping.</DeliveryNotes>  
    <Items>  
      <Item PartNumber="456-NM">  
        <ProductName>Power Supply</ProductName>  
        <Quantity>1</Quantity>  
        <USPrice>45.99</USPrice>  
      </Item>  
    </Items>  
  </PurchaseOrder>  
  <PurchaseOrder PurchaseOrderNumber="99504" OrderDate="1999-10-22">  
    <Address Type="Shipping">  
      <Name>Jessica Arnold</Name>  
      <Street>4055 Madison Ave</Street>  
      <City>Seattle</City>  
      <State>WA</State>  
      <Zip>98112</Zip>  
      <Country>USA</Country>  
    </Address>  
    <Address Type="Billing">  
      <Name>Jessica Arnold</Name>  
      <Street>4055 Madison Ave</Street>  
      <City>Buffalo</City>  
      <State>NY</State>  
      <Zip>98112</Zip>  
      <Country>USA</Country>  
    </Address>  
    <Items>  
      <Item PartNumber="898-AZ">  
        <ProductName>Computer Keyboard</ProductName>  
        <Quantity>1</Quantity>  
        <USPrice>29.99</USPrice>  
      </Item>  
      <Item PartNumber="898-AM">  
        <ProductName>Wireless Mouse</ProductName>  
        <Quantity>1</Quantity>  
        <USPrice>14.99</USPrice>  
      </Item>  
    </Items>  
  </PurchaseOrder>  
</PurchaseOrders>  
```  
