---
title: Sposób łańcucha wywołań metod osi (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 067e6da2-ee32-486d-803c-e611b328e39a
ms.openlocfilehash: ccfbf516a7fddbef357bfb0072288e250768616b
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141436"
---
# <a name="how-to-chain-axis-method-calls-linq-to-xml-c"></a><span data-ttu-id="7a15a-102">Sposób łańcucha wywołań metod osi (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="7a15a-102">How to chain axis method calls (LINQ to XML) (C#)</span></span>
<span data-ttu-id="7a15a-103">Typowym wzorcem, który będzie używany w kodzie, jest wywołanie metody osi, a następnie wywołanie jednej z osi metody rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="7a15a-103">A common pattern that you will use in your code is to call an axis method, then call one of the extension method axes.</span></span>  
  
 <span data-ttu-id="7a15a-104">Istnieją dwie osie o nazwie `Elements`, która zwraca kolekcję elementów: metodę <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> i metodę <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7a15a-104">There are two axes with the name of `Elements` that return a collection of elements: the <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> method and the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="7a15a-105">Można połączyć te dwie osie, aby znaleźć wszystkie elementy określonej nazwy na danej głębokości drzewa.</span><span class="sxs-lookup"><span data-stu-id="7a15a-105">You can combine these two axes to find all elements of a specified name at a given depth in the tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7a15a-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="7a15a-106">Example</span></span>  
 <span data-ttu-id="7a15a-107">W tym przykładzie używa <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> i <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> do znajdowania wszystkich `Name` elementów we wszystkich elementach `Address` we wszystkich elementów `PurchaseOrder`.</span><span class="sxs-lookup"><span data-stu-id="7a15a-107">This example uses <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> and <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> to find all `Name` elements in all `Address` elements in all `PurchaseOrder` elements.</span></span>  
  
 <span data-ttu-id="7a15a-108">W tym przykładzie zastosowano następujący dokument XML: [przykładowy plik XML: wiele zamówień zakupu (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="7a15a-108">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="7a15a-109">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="7a15a-109">This example produces the following output:</span></span>  
  
```xml  
<Name>Ellen Adams</Name>  
<Name>Tai Yee</Name>  
<Name>Cristian Osorio</Name>  
<Name>Cristian Osorio</Name>  
<Name>Jessica Arnold</Name>  
<Name>Jessica Arnold</Name>  
```  
  
 <span data-ttu-id="7a15a-110">To działa, ponieważ jedna z implementacji osi `Elements` jest metodą rozszerzającą <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="7a15a-110">This works because one of the implementations of the `Elements` axis is as an extension method on <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XContainer>.</span></span> <span data-ttu-id="7a15a-111"><xref:System.Xml.Linq.XElement> pochodzi od <xref:System.Xml.Linq.XContainer>, więc można wywołać metodę <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> na wynikach wywołania metody <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7a15a-111"><xref:System.Xml.Linq.XElement> derives from <xref:System.Xml.Linq.XContainer>, so you can call the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> method on the results of a call to the <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7a15a-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="7a15a-112">Example</span></span>  
 <span data-ttu-id="7a15a-113">Czasami chcesz pobrać wszystkie elementy z konkretnej głębokości elementu, jeśli istnieją lub mogą nie powodować interwencji elementów nadrzędnych.</span><span class="sxs-lookup"><span data-stu-id="7a15a-113">Sometimes you want to retrieve all elements at a particular element depth when there might or might not be intervening ancestors.</span></span> <span data-ttu-id="7a15a-114">Na przykład w poniższym dokumencie można pobrać wszystkie elementy `ConfigParameter`, które są elementami podrzędnymi elementu `Customer`, ale nie `ConfigParameter`, który jest elementem podrzędnym elementu `Root`.</span><span class="sxs-lookup"><span data-stu-id="7a15a-114">For example, in the following document, you might want to retrieve all the `ConfigParameter` elements that are children of the `Customer` element, but not the `ConfigParameter` that is a child of the `Root` element.</span></span>  
  
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
  
 <span data-ttu-id="7a15a-115">W tym celu można użyć osi <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="7a15a-115">To do this, you can use the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> axis, as follows:</span></span>  
  
```csharp  
XElement root = XElement.Load("Irregular.xml");  
IEnumerable<XElement> configParameters =   
    root.Elements("Customer").Elements("Config").  
    Elements("ConfigParameter");  
foreach (XElement cp in configParameters)  
    Console.WriteLine(cp);  
```  
  
 <span data-ttu-id="7a15a-116">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="7a15a-116">This example produces the following output:</span></span>  
  
```xml  
<ConfigParameter>FirstConfigParameter</ConfigParameter>  
<ConfigParameter>SecondConfigParameter</ConfigParameter>  
```  
  
## <a name="example"></a><span data-ttu-id="7a15a-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="7a15a-117">Example</span></span>  
 <span data-ttu-id="7a15a-118">Poniższy przykład pokazuje tę samą technikę dla XML, która znajduje się w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="7a15a-118">The following example shows the same technique for XML that is in a namespace.</span></span> <span data-ttu-id="7a15a-119">Aby uzyskać więcej informacji, zobacz temat [przestrzenie nazw —C#omówienie (LINQ to XML) ()](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="7a15a-119">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="7a15a-120">W tym przykładzie zastosowano następujący dokument XML: [przykładowy plik XML: wiele zamówień zakupu w przestrzeni nazw](./sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="7a15a-120">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders in a Namespace](./sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span></span>  
  
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
  
 <span data-ttu-id="7a15a-121">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="7a15a-121">This example produces the following output:</span></span>  
  
```xml  
<aw:Name xmlns:aw="http://www.adventure-works.com">Ellen Adams</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Tai Yee</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7a15a-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7a15a-122">See also</span></span>

- [<span data-ttu-id="7a15a-123">Osie LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="7a15a-123">LINQ to XML Axes (C#)</span></span>](linq-to-xml-axes-overview.md)
