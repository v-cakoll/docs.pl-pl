---
title: 'Porady: łańcucha wywołań metody osi (LINQ do XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: e4e22942-39bd-460f-b3c0-9f09e53d3aa9
ms.openlocfilehash: b90cd757429639483f11427e2747c7dd3db9e07b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-chain-axis-method-calls-linq-to-xml-visual-basic"></a><span data-ttu-id="2337a-102">Porady: łańcucha wywołań metody osi (LINQ do XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2337a-102">How to: Chain Axis Method Calls (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="2337a-103">Typowe wzorzec, który będzie używany w kodzie jest wywołanie metody osi, a następnie wywołania jednej osi — metoda rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="2337a-103">A common pattern that you will use in your code is to call an axis method, then call one of the extension method axes.</span></span>  
  
 <span data-ttu-id="2337a-104">Istnieją dwie osie o nazwie `Elements` kolekcję elementów, które zwracają: <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> — metoda i <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="2337a-104">There are two axes with the name of `Elements` that return a collection of elements: the <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> method and the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="2337a-105">Można połączyć tych dwóch osiach można znaleźć wszystkie elementy o określonej nazwie w danym Głębokość drzewa.</span><span class="sxs-lookup"><span data-stu-id="2337a-105">You can combine these two axes to find all elements of a specified name at a given depth in the tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2337a-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="2337a-106">Example</span></span>  
 <span data-ttu-id="2337a-107">W tym przykładzie użyto <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> i <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> Aby znaleźć wszystkie `Name` elementy we wszystkich `Address` elementy we wszystkich `PurchaseOrder` elementów.</span><span class="sxs-lookup"><span data-stu-id="2337a-107">This example uses <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> and <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> to find all `Name` elements in all `Address` elements in all `PurchaseOrder` elements.</span></span>  
  
 <span data-ttu-id="2337a-108">W tym przykładzie użyto następujących dokumentu XML: [przykładowego pliku XML: wiele zakupów (LINQ do XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="2337a-108">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
```vb  
Dim purchaseOrders As XElement = XElement.Load("PurchaseOrders.xml")  
Dim names As IEnumerable(Of XElement) = _  
    From el In purchaseOrders.<PurchaseOrder>.<Address>.<Name> _  
    Select el  
For Each e As XElement In names  
    Console.WriteLine(e)  
Next  
```  
  
 <span data-ttu-id="2337a-109">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="2337a-109">This example produces the following output:</span></span>  
  
```xml  
<Name>Ellen Adams</Name>  
<Name>Tai Yee</Name>  
<Name>Cristian Osorio</Name>  
<Name>Cristian Osorio</Name>  
<Name>Jessica Arnold</Name>  
<Name>Jessica Arnold</Name>  
```  
  
 <span data-ttu-id="2337a-110">To działa, ponieważ jeden z implementacje `Elements` osi jest metodą rozszerzenia na <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="2337a-110">This works because one of the implementations of the `Elements` axis is as an extension method on <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XContainer>.</span></span> <span data-ttu-id="2337a-111"><xref:System.Xml.Linq.XElement> pochodzi z <xref:System.Xml.Linq.XContainer>, dlatego można wywoływać <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> metody na wyniki wywołania <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="2337a-111"><xref:System.Xml.Linq.XElement> derives from <xref:System.Xml.Linq.XContainer>, so you can call the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> method on the results of a call to the <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2337a-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="2337a-112">Example</span></span>  
 <span data-ttu-id="2337a-113">Czasami chcesz pobrać wszystkie elementy na głębokości dany element podczas może lub nie może być pośredniczące obiektów nadrzędnych.</span><span class="sxs-lookup"><span data-stu-id="2337a-113">Sometimes you want to retrieve all elements at a particular element depth when there might or might not be intervening ancestors.</span></span> <span data-ttu-id="2337a-114">Na przykład w następującym dokumencie można pobrać wszystkie `ConfigParameter` elementy, które są elementami podrzędnymi `Customer` elementu, ale nie `ConfigParameter` będący elementem podrzędnym `Root` elementu.</span><span class="sxs-lookup"><span data-stu-id="2337a-114">For example, in the following document, you might want to retrieve all the `ConfigParameter` elements that are children of the `Customer` element, but not the `ConfigParameter` that is a child of the `Root` element.</span></span>  
  
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
  
 <span data-ttu-id="2337a-115">Aby to zrobić, można użyć <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> osi w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="2337a-115">To do this, you can use the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> axis, as follows:</span></span>  
  
```vb  
Dim root As XElement = XElement.Load("Irregular.xml")  
Dim configParameters As IEnumerable(Of XElement) = _  
    root.<Customer>.<Config>.<ConfigParameter>  
For Each cp As XElement In configParameters  
    Console.WriteLine(cp)  
Next  
```  
  
 <span data-ttu-id="2337a-116">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="2337a-116">This example produces the following output:</span></span>  
  
```xml  
<ConfigParameter>FirstConfigParameter</ConfigParameter>  
<ConfigParameter>SecondConfigParameter</ConfigParameter>  
```  
  
## <a name="example"></a><span data-ttu-id="2337a-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="2337a-117">Example</span></span>  
 <span data-ttu-id="2337a-118">W poniższym przykładzie przedstawiono tę samą metodę dla formatu XML, który znajduje się w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="2337a-118">The following example shows the same technique for XML that is in a namespace.</span></span> <span data-ttu-id="2337a-119">Aby uzyskać więcej informacji, zobacz [Praca z przestrzeni nazw XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="2337a-119">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="2337a-120">W tym przykładzie użyto następujących dokumentu XML: [przykładowego pliku XML: wiele zakupów w Namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="2337a-120">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders in a Namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim purchaseOrders As XElement = XElement.Load("PurchaseOrdersInNamespace.xml")  
        Dim names As IEnumerable(Of XElement) = _  
            From el In purchaseOrders.<aw:PurchaseOrder>.<aw:Address>.<aw:Name> _  
            Select el  
        For Each e As XElement In names  
            Console.WriteLine(e)  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="2337a-121">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="2337a-121">This example produces the following output:</span></span>  
  
```xml  
<aw:Name xmlns:aw="http://www.adventure-works.com">Ellen Adams</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Tai Yee</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2337a-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2337a-122">See Also</span></span>  
 [<span data-ttu-id="2337a-123">LINQ do osi XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2337a-123">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
