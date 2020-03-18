---
title: Jak łańcuch axis wywołania metody (LINQ do XML) (C#)
ms.date: 07/20/2015
ms.assetid: 067e6da2-ee32-486d-803c-e611b328e39a
ms.openlocfilehash: 56fa5c9e8358883d838b68e99664240aa97f347f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169470"
---
# <a name="how-to-chain-axis-method-calls-linq-to-xml-c"></a>Jak łańcuch axis wywołania metody (LINQ do XML) (C#)
Typowy wzorzec, który będzie używany w kodzie jest wywołanie metody osi, a następnie wywołać jedną z osi metody rozszerzenia.  
  
 Istnieją dwie osie o `Elements` nazwie, która zwraca kolekcję elementów: <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> metodę i <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> metodę. Można połączyć te dwie osie, aby znaleźć wszystkie elementy o określonej nazwie na danej głębokości w drzewie.  
  
## <a name="example"></a>Przykład  
 W tym <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> przykładzie używa `Name` i `Address` znaleźć wszystkie `PurchaseOrder` elementy we wszystkich elementach we wszystkich elementach.  
  
 W tym przykładzie użyto następującego dokumentu XML: [Przykładowy plik XML: wiele zamówień zakupu (LINQ do XML).](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md)  
  
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
  
 Działa to, ponieważ jedna z `Elements` implementacji osi jest <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XContainer>jako metoda rozszerzenia na . <xref:System.Xml.Linq.XElement>pochodzi z <xref:System.Xml.Linq.XContainer>, dzięki czemu <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> można wywołać metodę na <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> wyniki wywołania metody.  
  
## <a name="example"></a>Przykład  
 Czasami chcesz pobrać wszystkie elementy na głębokość określonego elementu, gdy nie może lub nie może być interwencji przodków. Na przykład w poniższym dokumencie można pobrać `ConfigParameter` wszystkie elementy, które `Customer` są elementami `ConfigParameter` podrzędowymi elementu, `Root` ale nie, który jest elementem podrzędnym elementu.  
  
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
  
 Aby to zrobić, można <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> użyć osi, w następujący sposób:  
  
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
 W poniższym przykładzie przedstawiono tę samą technikę dla Języka XML, która znajduje się w obszarze nazw. Aby uzyskać więcej informacji, zobacz [Omówienie przestrzeni nazw (LINQ do XML) (C#)](namespaces-overview-linq-to-xml.md).  
  
 W tym przykładzie użyto następującego dokumentu XML: [Przykładowy plik XML: wiele zamówień zakupu w obszarze nazw](./sample-xml-file-multiple-purchase-orders-in-a-namespace.md).  
  
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

- [LINQ do osi XML (C#)](linq-to-xml-axes-overview.md)
