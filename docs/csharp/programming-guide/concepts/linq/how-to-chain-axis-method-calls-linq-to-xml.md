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
# <a name="how-to-chain-axis-method-calls-linq-to-xml-c"></a><span data-ttu-id="cf1ba-102">Jak łańcuch axis wywołania metody (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="cf1ba-102">How to chain axis method calls (LINQ to XML) (C#)</span></span>
<span data-ttu-id="cf1ba-103">Typowy wzorzec, który będzie używany w kodzie jest wywołanie metody osi, a następnie wywołać jedną z osi metody rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="cf1ba-103">A common pattern that you will use in your code is to call an axis method, then call one of the extension method axes.</span></span>  
  
 <span data-ttu-id="cf1ba-104">Istnieją dwie osie o `Elements` nazwie, która zwraca kolekcję elementów: <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> metodę i <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> metodę.</span><span class="sxs-lookup"><span data-stu-id="cf1ba-104">There are two axes with the name of `Elements` that return a collection of elements: the <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> method and the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="cf1ba-105">Można połączyć te dwie osie, aby znaleźć wszystkie elementy o określonej nazwie na danej głębokości w drzewie.</span><span class="sxs-lookup"><span data-stu-id="cf1ba-105">You can combine these two axes to find all elements of a specified name at a given depth in the tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cf1ba-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="cf1ba-106">Example</span></span>  
 <span data-ttu-id="cf1ba-107">W tym <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> przykładzie używa `Name` i `Address` znaleźć wszystkie `PurchaseOrder` elementy we wszystkich elementach we wszystkich elementach.</span><span class="sxs-lookup"><span data-stu-id="cf1ba-107">This example uses <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> and <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> to find all `Name` elements in all `Address` elements in all `PurchaseOrder` elements.</span></span>  
  
 <span data-ttu-id="cf1ba-108">W tym przykładzie użyto następującego dokumentu XML: [Przykładowy plik XML: wiele zamówień zakupu (LINQ do XML).](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md)</span><span class="sxs-lookup"><span data-stu-id="cf1ba-108">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="cf1ba-109">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="cf1ba-109">This example produces the following output:</span></span>  
  
```xml  
<Name>Ellen Adams</Name>  
<Name>Tai Yee</Name>  
<Name>Cristian Osorio</Name>  
<Name>Cristian Osorio</Name>  
<Name>Jessica Arnold</Name>  
<Name>Jessica Arnold</Name>  
```  
  
 <span data-ttu-id="cf1ba-110">Działa to, ponieważ jedna z `Elements` implementacji osi jest <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XContainer>jako metoda rozszerzenia na .</span><span class="sxs-lookup"><span data-stu-id="cf1ba-110">This works because one of the implementations of the `Elements` axis is as an extension method on <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XContainer>.</span></span> <span data-ttu-id="cf1ba-111"><xref:System.Xml.Linq.XElement>pochodzi z <xref:System.Xml.Linq.XContainer>, dzięki czemu <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> można wywołać metodę na <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> wyniki wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="cf1ba-111"><xref:System.Xml.Linq.XElement> derives from <xref:System.Xml.Linq.XContainer>, so you can call the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> method on the results of a call to the <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cf1ba-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="cf1ba-112">Example</span></span>  
 <span data-ttu-id="cf1ba-113">Czasami chcesz pobrać wszystkie elementy na głębokość określonego elementu, gdy nie może lub nie może być interwencji przodków.</span><span class="sxs-lookup"><span data-stu-id="cf1ba-113">Sometimes you want to retrieve all elements at a particular element depth when there might or might not be intervening ancestors.</span></span> <span data-ttu-id="cf1ba-114">Na przykład w poniższym dokumencie można pobrać `ConfigParameter` wszystkie elementy, które `Customer` są elementami `ConfigParameter` podrzędowymi elementu, `Root` ale nie, który jest elementem podrzędnym elementu.</span><span class="sxs-lookup"><span data-stu-id="cf1ba-114">For example, in the following document, you might want to retrieve all the `ConfigParameter` elements that are children of the `Customer` element, but not the `ConfigParameter` that is a child of the `Root` element.</span></span>  
  
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
  
 <span data-ttu-id="cf1ba-115">Aby to zrobić, można <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> użyć osi, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="cf1ba-115">To do this, you can use the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> axis, as follows:</span></span>  
  
```csharp  
XElement root = XElement.Load("Irregular.xml");  
IEnumerable<XElement> configParameters =
    root.Elements("Customer").Elements("Config").  
    Elements("ConfigParameter");  
foreach (XElement cp in configParameters)  
    Console.WriteLine(cp);  
```  
  
 <span data-ttu-id="cf1ba-116">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="cf1ba-116">This example produces the following output:</span></span>  
  
```xml  
<ConfigParameter>FirstConfigParameter</ConfigParameter>  
<ConfigParameter>SecondConfigParameter</ConfigParameter>  
```  
  
## <a name="example"></a><span data-ttu-id="cf1ba-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="cf1ba-117">Example</span></span>  
 <span data-ttu-id="cf1ba-118">W poniższym przykładzie przedstawiono tę samą technikę dla Języka XML, która znajduje się w obszarze nazw.</span><span class="sxs-lookup"><span data-stu-id="cf1ba-118">The following example shows the same technique for XML that is in a namespace.</span></span> <span data-ttu-id="cf1ba-119">Aby uzyskać więcej informacji, zobacz [Omówienie przestrzeni nazw (LINQ do XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="cf1ba-119">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="cf1ba-120">W tym przykładzie użyto następującego dokumentu XML: [Przykładowy plik XML: wiele zamówień zakupu w obszarze nazw](./sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="cf1ba-120">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders in a Namespace](./sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span></span>  
  
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
  
 <span data-ttu-id="cf1ba-121">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="cf1ba-121">This example produces the following output:</span></span>  
  
```xml  
<aw:Name xmlns:aw="http://www.adventure-works.com">Ellen Adams</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Tai Yee</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>  
```  
  
## <a name="see-also"></a><span data-ttu-id="cf1ba-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cf1ba-122">See also</span></span>

- [<span data-ttu-id="cf1ba-123">LINQ do osi XML (C#)</span><span class="sxs-lookup"><span data-stu-id="cf1ba-123">LINQ to XML Axes (C#)</span></span>](linq-to-xml-axes-overview.md)
