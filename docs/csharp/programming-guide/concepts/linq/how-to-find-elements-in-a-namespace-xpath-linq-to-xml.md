---
title: Jak znaleźć elementy w przestrzeni nazw (XPath-LINQ do XML) (C#)
ms.date: 07/20/2015
ms.assetid: cae1c4ac-6cd5-46cf-9b1c-bd85bc9b7ea9
ms.openlocfilehash: da9d819be5234a2429b6eab276f89bd0d877d4a7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141065"
---
# <a name="how-to-find-elements-in-a-namespace-xpath-linq-to-xml-c"></a>Jak znaleźć elementy w przestrzeni nazw (XPath-LINQ do XML) (C#)

Wyrażenia XPath mogą znajdować węzły w określonym obszarze nazw. Wyrażenia XPath używają prefiksów obszaru nazw do określania przestrzeni nazw. Aby przeanalizować wyrażenie XPath zawierające prefiksy obszaru nazw, należy przekazać obiekt do <xref:System.Xml.IXmlNamespaceResolver>metod XPath, które implementują . W tym <xref:System.Xml.XmlNamespaceManager>przykładzie użyto .

Wyrażenie XPath jest następujące:

`./aw:*`

## <a name="example"></a>Przykład

Poniższy przykład odczytuje drzewo XML, który zawiera dwa obszary nazw. Używa <xref:System.Xml.XmlReader> do odczytu dokumentu XML. Następnie dostaje <xref:System.Xml.XmlNameTable> z <xref:System.Xml.XmlReader>, i <xref:System.Xml.XmlNamespaceManager> z <xref:System.Xml.XmlNameTable>. Używa podczas <xref:System.Xml.XmlNamespaceManager> wybierania elementów.

```csharp
XmlReader reader = XmlReader.Create("ConsolidatedPurchaseOrders.xml");
XElement root = XElement.Load(reader);
XmlNameTable nameTable = reader.NameTable;
XmlNamespaceManager namespaceManager = new XmlNamespaceManager(nameTable);
namespaceManager.AddNamespace("aw", "http://www.adventure-works.com");
IEnumerable<XElement> list1 = root.XPathSelectElements("./aw:*", namespaceManager);
IEnumerable<XElement> list2 =
    from el in root.Elements()
    where el.Name.Namespace == "http://www.adventure-works.com"
    select el;
if (list1.Count() == list2.Count() &&
        list1.Intersect(list2).Count() == list1.Count())
    Console.WriteLine("Results are identical");
else
    Console.WriteLine("Results differ");
foreach (XElement el in list2)
    Console.WriteLine(el);
```

Ten przykład generuje następujące wyniki:

```output
Results are identical
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
```
