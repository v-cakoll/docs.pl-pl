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
# <a name="how-to-chain-axis-method-calls-linq-to-xml-c"></a><span data-ttu-id="9c2a4-102">Porady: łańcucha wywołań metody osi (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="9c2a4-102">How to: Chain Axis Method Calls (LINQ to XML) (C#)</span></span>
<span data-ttu-id="9c2a4-103">Typowe wzorzec, który będzie używany w kodzie jest wywołanie metody osi, a następnie wywołania jednej osi — metoda rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="9c2a4-103">A common pattern that you will use in your code is to call an axis method, then call one of the extension method axes.</span></span>  
  
 <span data-ttu-id="9c2a4-104">Istnieją dwie osie o nazwie `Elements` kolekcję elementów, które zwracają: <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> — metoda i <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="9c2a4-104">There are two axes with the name of `Elements` that return a collection of elements: the <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> method and the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="9c2a4-105">Można połączyć tych dwóch osiach można znaleźć wszystkie elementy o określonej nazwie w danym Głębokość drzewa.</span><span class="sxs-lookup"><span data-stu-id="9c2a4-105">You can combine these two axes to find all elements of a specified name at a given depth in the tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9c2a4-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="9c2a4-106">Example</span></span>  
 <span data-ttu-id="9c2a4-107">W tym przykładzie użyto <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> i <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> Aby znaleźć wszystkie `Name` elementy we wszystkich `Address` elementy we wszystkich `PurchaseOrder` elementów.</span><span class="sxs-lookup"><span data-stu-id="9c2a4-107">This example uses <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> and <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> to find all `Name` elements in all `Address` elements in all `PurchaseOrder` elements.</span></span>  
  
 <span data-ttu-id="9c2a4-108">W tym przykładzie użyto następujących dokumentu XML: [przykładowego pliku XML: wiele zakupów (LINQ do XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="9c2a4-108">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="9c2a4-109">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="9c2a4-109">This example produces the following output:</span></span>  
  
```xml  
<Name>Ellen Adams</Name>  
<Name>Tai Yee</Name>  
<Name>Cristian Osorio</Name>  
<Name>Cristian Osorio</Name>  
<Name>Jessica Arnold</Name>  
<Name>Jessica Arnold</Name>  
```  
  
 <span data-ttu-id="9c2a4-110">To działa, ponieważ jeden z implementacje `Elements` osi jest metodą rozszerzenia na <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="9c2a4-110">This works because one of the implementations of the `Elements` axis is as an extension method on <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XContainer>.</span></span> <span data-ttu-id="9c2a4-111"><xref:System.Xml.Linq.XElement>pochodzi z <xref:System.Xml.Linq.XContainer>, dlatego można wywoływać <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> metody na wyniki wywołania <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="9c2a4-111"><xref:System.Xml.Linq.XElement> derives from <xref:System.Xml.Linq.XContainer>, so you can call the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> method on the results of a call to the <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9c2a4-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="9c2a4-112">Example</span></span>  
 <span data-ttu-id="9c2a4-113">Czasami chcesz pobrać wszystkie elementy na głębokości dany element podczas może lub nie może być pośredniczące obiektów nadrzędnych.</span><span class="sxs-lookup"><span data-stu-id="9c2a4-113">Sometimes you want to retrieve all elements at a particular element depth when there might or might not be intervening ancestors.</span></span> <span data-ttu-id="9c2a4-114">Na przykład w następującym dokumencie można pobrać wszystkie `ConfigParameter` elementy, które są elementami podrzędnymi `Customer` elementu, ale nie `ConfigParameter` będący elementem podrzędnym `Root` elementu.</span><span class="sxs-lookup"><span data-stu-id="9c2a4-114">For example, in the following document, you might want to retrieve all the `ConfigParameter` elements that are children of the `Customer` element, but not the `ConfigParameter` that is a child of the `Root` element.</span></span>  
  
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
  
 <span data-ttu-id="9c2a4-115">Aby to zrobić, można użyć <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> osi w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="9c2a4-115">To do this, you can use the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> axis, as follows:</span></span>  
  
```csharp  
XElement root = XElement.Load("Irregular.xml");  
IEnumerable<XElement> configParameters =   
    root.Elements("Customer").Elements("Config").  
    Elements("ConfigParameter");  
foreach (XElement cp in configParameters)  
    Console.WriteLine(cp);  
```  
  
 <span data-ttu-id="9c2a4-116">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="9c2a4-116">This example produces the following output:</span></span>  
  
```xml  
<ConfigParameter>FirstConfigParameter</ConfigParameter>  
<ConfigParameter>SecondConfigParameter</ConfigParameter>  
```  
  
## <a name="example"></a><span data-ttu-id="9c2a4-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="9c2a4-117">Example</span></span>  
 <span data-ttu-id="9c2a4-118">W poniższym przykładzie przedstawiono tę samą metodę dla formatu XML, który znajduje się w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="9c2a4-118">The following example shows the same technique for XML that is in a namespace.</span></span> <span data-ttu-id="9c2a4-119">Aby uzyskać więcej informacji, zobacz [Praca z przestrzeni nazw XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="9c2a4-119">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="9c2a4-120">W tym przykładzie użyto następujących dokumentu XML: [przykładowego pliku XML: wiele zakupów w Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="9c2a4-120">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders in a Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span></span>  
  
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
  
 <span data-ttu-id="9c2a4-121">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="9c2a4-121">This example produces the following output:</span></span>  
  
```xml  
<aw:Name xmlns:aw="http://www.adventure-works.com">Ellen Adams</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Tai Yee</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9c2a4-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9c2a4-122">See Also</span></span>  
 [<span data-ttu-id="9c2a4-123">LINQ do osi XML (C#)</span><span class="sxs-lookup"><span data-stu-id="9c2a4-123">LINQ to XML Axes (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
