---
title: 'Instrukcje: Znajdź elementy w przestrzeni nazw (XPath-LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: cae1c4ac-6cd5-46cf-9b1c-bd85bc9b7ea9
ms.openlocfilehash: d85426cf7a7073c35b51157e59687e2b3bcdcf8a
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253677"
---
# <a name="how-to-find-elements-in-a-namespace-xpath-linq-to-xml-c"></a>Instrukcje: Znajdź elementy w przestrzeni nazw (XPath-LINQ to XML) (C#)

Wyrażenia XPath mogą znajdować węzły w określonej przestrzeni nazw. Wyrażenia XPath używają prefiksów przestrzeni nazw do określania przestrzeni nazw. Aby przeanalizować wyrażenie XPath, które zawiera prefiksy przestrzeni nazw, należy przekazać obiekt do metody XPath implementującej <xref:System.Xml.IXmlNamespaceResolver>. Ten przykład używa <xref:System.Xml.XmlNamespaceManager>.

Wyrażenie XPath:

`./aw:*`

## <a name="example"></a>Przykład

Poniższy przykład odczytuje drzewo XML zawierające dwie przestrzenie nazw. Używa <xref:System.Xml.XmlReader> do odczytywania dokumentu XML. <xref:System.Xml.XmlNameTable> Następnie pobiera <xref:System.Xml.XmlReader>z i <xref:System.Xml.XmlNamespaceManager> z.<xref:System.Xml.XmlNameTable> Używa <xref:System.Xml.XmlNamespaceManager> podczas wybierania elementów.

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
