---
title: "Porady: znajdowanie elementów w Namespace (XPath-LINQ do XML) (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: cae1c4ac-6cd5-46cf-9b1c-bd85bc9b7ea9
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f1804731a39eebce74a38a4e8b296747e535c0b8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-find-elements-in-a-namespace-xpath-linq-to-xml-c"></a>Porady: znajdowanie elementów w Namespace (XPath-LINQ do XML) (C#)
Wyrażenia XPath można znaleźć węzłów w określonej przestrzeni nazw. Wyrażenia XPath Użyj prefiksy przestrzeni nazw dla określenie obszarów nazw. Aby analizować wyrażenie XPath, który zawiera prefiksy przestrzeni nazw, trzeba przekazać do metody XPath, które implementuje obiektu <xref:System.Xml.IXmlNamespaceResolver>. W tym przykładzie użyto <xref:System.Xml.XmlNamespaceManager>.  
  
 Wyrażenie XPath jest:  
  
 `./aw:*`  
  
## <a name="example"></a>Przykład  
 Poniższy przykład odczytuje drzewo XML, który zawiera dwie przestrzenie nazw. Używa <xref:System.Xml.XmlReader> dokumentu XML. Następnie pobiera <xref:System.Xml.XmlNameTable> z <xref:System.Xml.XmlReader>i <xref:System.Xml.XmlNamespaceManager> z <xref:System.Xml.XmlNameTable>. Używa <xref:System.Xml.XmlNamespaceManager> podczas wybierania elementów.  
  
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
  
```  
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
  
## <a name="see-also"></a>Zobacz też  
 [LINQ do XML dla użytkowników XPath (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
