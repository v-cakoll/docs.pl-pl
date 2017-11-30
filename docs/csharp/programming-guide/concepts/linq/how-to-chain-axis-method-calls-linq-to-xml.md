---
title: "Porady: łańcucha wywołań metody osi (LINQ do XML) (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 067e6da2-ee32-486d-803c-e611b328e39a
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7cf5cb445dc64dfa5f4734ae58e6e921a5a92148
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-chain-axis-method-calls-linq-to-xml-c"></a>Porady: łańcucha wywołań metody osi (LINQ do XML) (C#)
Typowe wzorzec, który będzie używany w kodzie jest wywołanie metody osi, a następnie wywołania jednej osi — metoda rozszerzenia.  
  
 Istnieją dwie osie o nazwie `Elements` kolekcję elementów, które zwracają: <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> — metoda i <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> metody. Można połączyć tych dwóch osiach można znaleźć wszystkie elementy o określonej nazwie w danym Głębokość drzewa.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> i <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> Aby znaleźć wszystkie `Name` elementy we wszystkich `Address` elementy we wszystkich `PurchaseOrder` elementów.  
  
 W tym przykładzie użyto następujących dokumentu XML: [przykładowego pliku XML: wiele zakupów (LINQ do XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).  
  
```csharp  
XElement purchaseOrders = XElement.Load("PurchaseOrders.xml");  
IEnumerable<XElement> names =  
    from el in purchaseOrders  
        .Elements("PurchaseOrder")  
        .Elements("Address")  
        .Elements("Name")  
    select el;  
foreach (XElement e in names)  
    Console.WriteLine(e);  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<Name>Ellen Adams</Name>  
<Name>Tai Yee</Name>  
<Name>Cristian Osorio</Name>  
<Name>Cristian Osorio</Name>  
<Name>Jessica Arnold</Name>  
<Name>Jessica Arnold</Name>  
```  
  
 To działa, ponieważ jeden z implementacje `Elements` osi jest metodą rozszerzenia na <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XContainer>. <xref:System.Xml.Linq.XElement>pochodzi z <xref:System.Xml.Linq.XContainer>, dlatego można wywoływać <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> metody na wyniki wywołania <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> metody.  
  
## <a name="example"></a>Przykład  
 Czasami chcesz pobrać wszystkie elementy na głębokości dany element podczas może lub nie może być pośredniczące obiektów nadrzędnych. Na przykład w następującym dokumencie można pobrać wszystkie `ConfigParameter` elementy, które są elementami podrzędnymi `Customer` elementu, ale nie `ConfigParameter` będący elementem podrzędnym `Root` elementu.  
  
```xml  
<Root>  
  <ConfigParameter>RootConfigParameter</ConfigParameter>  
  <Customer>  
    <Name>Frank</Name>  
    <Config>  
      <ConfigParameter>FirstConfigParameter</ConfigParameter>  
    </Config>  
  </Customer>  
  <Customer>  
    <Name>Bob</Name>  
    <!--This customer doesn't have a Config element-->  
  </Customer>  
  <Customer>  
    <Name>Bill</Name>  
    <Config>  
      <ConfigParameter>SecondConfigParameter</ConfigParameter>  
    </Config>  
  </Customer>  
</Root>  
```  
  
 Aby to zrobić, można użyć <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> osi w następujący sposób:  
  
```csharp  
XElement root = XElement.Load("Irregular.xml");  
IEnumerable<XElement> configParameters =   
    root.Elements("Customer").Elements("Config").  
    Elements("ConfigParameter");  
foreach (XElement cp in configParameters)  
    Console.WriteLine(cp);  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<ConfigParameter>FirstConfigParameter</ConfigParameter>  
<ConfigParameter>SecondConfigParameter</ConfigParameter>  
```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono tę samą metodę dla formatu XML, który znajduje się w przestrzeni nazw. Aby uzyskać więcej informacji, zobacz [Praca z przestrzeni nazw XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).  
  
 W tym przykładzie użyto następujących dokumentu XML: [przykładowego pliku XML: wiele zakupów w Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md).  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement purchaseOrders = XElement.Load("PurchaseOrdersInNamespace.xml");  
IEnumerable<XElement> names =  
    from el in purchaseOrders  
        .Elements(aw + "PurchaseOrder")  
        .Elements(aw + "Address")  
        .Elements(aw + "Name")  
    select el;  
foreach (XElement e in names)  
    Console.WriteLine(e);  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<aw:Name xmlns:aw="http://www.adventure-works.com">Ellen Adams</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Tai Yee</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [LINQ do osi XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
