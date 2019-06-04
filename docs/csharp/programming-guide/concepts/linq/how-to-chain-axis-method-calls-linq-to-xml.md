---
title: 'Instrukcje: Połączyć w łańcuch wywołań metody osi (LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 067e6da2-ee32-486d-803c-e611b328e39a
ms.openlocfilehash: 39113c1b96ea7376d61c606aaa5f79715dbe3cab
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66485924"
---
# <a name="how-to-chain-axis-method-calls-linq-to-xml-c"></a>Instrukcje: Połączyć w łańcuch wywołań metody osi (LINQ to XML) (C#)
Typowy wzorzec, który będzie używany w kodzie jest wywołanie metody osi, a następnie wywołania jednej osi metody rozszerzenia.  
  
 Istnieją dwie osie o nazwie `Elements` zwracanych kolekcję elementów: <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> metody i <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> metody. Można połączyć te dwie osie, aby znaleźć wszystkie elementy o określonej nazwie na danym poziomie drzewa.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> i <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> Aby znaleźć wszystkie `Name` elementów we wszystkich `Address` elementów we wszystkich `PurchaseOrder` elementów.  
  
 W tym przykładzie użyto następujący dokument XML: [Przykładowy plik XML: Wiele zamówień zakupu (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).  
  
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
  
 To działa, ponieważ jeden z implementacji `Elements` osi jest jako metodę rozszerzenia w <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XContainer>. <xref:System.Xml.Linq.XElement> pochodzi od klasy <xref:System.Xml.Linq.XContainer>, dzięki czemu można wywoływać <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> metody na wynikach wywołania <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> metody.  
  
## <a name="example"></a>Przykład  
 Czasami chcesz pobrać wszystkie elementy na głębokości konkretnego elementu podczas może być lub może nie być pośredniczące elementów nadrzędnych. Na przykład w dokumencie, możesz chcieć pobrać wszystkie `ConfigParameter` elementy, które są elementami podrzędnymi `Customer` elementu, ale nie `ConfigParameter` czyli element podrzędny `Root` elementu.  
  
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
 Poniższy przykład pokazuje tę samą technikę, XML, który znajduje się w przestrzeni nazw. Aby uzyskać więcej informacji, zobacz [Praca z przestrzeniami nazw XML (C#)](../../../../csharp/programming-guide/concepts/linq/namespaces-overview-linq-to-xml.md).  
  
 W tym przykładzie użyto następujący dokument XML: [Przykładowy plik XML: Wiele zamówień zakupu w Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md).  
  
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
  
## <a name="see-also"></a>Zobacz także

- [LINQ do XML osi (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
