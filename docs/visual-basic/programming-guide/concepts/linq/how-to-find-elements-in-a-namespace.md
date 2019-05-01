---
title: 'Instrukcje: Znajdowanie elementów w Namespace (XPath-LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: c7cb3b77-3424-4b54-9efa-4dc715948e41
ms.openlocfilehash: f48ae0a03d625a3510b2280aa6361e2a731e5afe
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61780474"
---
# <a name="how-to-find-elements-in-a-namespace-xpath-linq-to-xml-visual-basic"></a>Instrukcje: Znajdowanie elementów w Namespace (XPath-LINQ to XML) (Visual Basic)
Wyrażenia XPath można znaleźć węzły w określonej przestrzeni nazw. Wyrażenia XPath używać prefiksów przestrzeni nazw do określania przestrzeni nazw. Aby analizować wyrażenie XPath, który zawiera prefiksy przestrzeni nazw, należy przekazać obiekt do metody XPath, które implementuje <xref:System.Xml.IXmlNamespaceResolver>. W tym przykładzie użyto <xref:System.Xml.XmlNamespaceManager>.  
  
 Wyrażenie XPath jest:  
  
 `./aw:*`  
  
## <a name="example"></a>Przykład  
 Poniższy przykład odczytuje drzewa XML, który zawiera dwie przestrzeni nazw. Używa ona <xref:System.Xml.XmlReader> do odczytu dokumentu XML. Następnie pobiera <xref:System.Xml.XmlNameTable> z <xref:System.Xml.XmlReader>i <xref:System.Xml.XmlNamespaceManager> z <xref:System.Xml.XmlNameTable>. Używa ona <xref:System.Xml.XmlNamespaceManager> podczas wybierania elementów.  
  
```vb  
Dim reader As XmlReader = _  
        XmlReader.Create("ConsolidatedPurchaseOrders.xml")  
Dim root As XElement = XElement.Load(reader)  
Dim nameTable As XmlNameTable = reader.NameTable  
Dim namespaceManager As XmlNamespaceManager = New XmlNamespaceManager(nameTable)  
namespaceManager.AddNamespace("aw", "http://www.adventure-works.com")  
  
Dim list1 As IEnumerable(Of XElement) = _  
        root.XPathSelectElements("./aw:*", namespaceManager)  
Dim list2 As IEnumerable(Of XElement) = _  
    From el In root.Elements() _  
    Where el.Name.Namespace = "http://www.adventure-works.com" _  
    Select el  
  
If list1.Count() = list2.Count() And _  
        list1.Intersect(list2).Count() = list1.Count() Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
For Each el As XElement In list2  
    Console.WriteLine(el)  
Next  
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
  
## <a name="see-also"></a>Zobacz także

- [LINQ to XML dla użytkowników metody XPath (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
