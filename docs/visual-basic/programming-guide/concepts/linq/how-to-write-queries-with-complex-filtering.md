---
title: 'Instrukcje: Pisanie zapytań z użyciem filtrowania złożonego'
ms.date: 07/20/2015
ms.assetid: bf286ffc-7990-4b00-a4eb-ee3d70129950
ms.openlocfilehash: 28e84b7785948e9d50c08438494b89c906ab8505
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344455"
---
# <a name="how-to-write-queries-with-complex-filtering-visual-basic"></a><span data-ttu-id="b0f82-102">Instrukcje: Pisanie zapytań ze złożonym filtrowaniem (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b0f82-102">How to: Write Queries with Complex Filtering (Visual Basic)</span></span>
<span data-ttu-id="b0f82-103">Czasami chcesz pisać zapytania LINQ to XML ze złożonymi filtrami.</span><span class="sxs-lookup"><span data-stu-id="b0f82-103">Sometimes you want to write LINQ to XML queries with complex filters.</span></span> <span data-ttu-id="b0f82-104">Na przykład może być konieczne znalezienie wszystkich elementów, które mają element podrzędny o określonej nazwie i wartości.</span><span class="sxs-lookup"><span data-stu-id="b0f82-104">For example, you might have to find all elements that have a child element with a particular name and value.</span></span> <span data-ttu-id="b0f82-105">Ten temat zawiera przykład tworzenia zapytania z skomplikowanym filtrowaniem.</span><span class="sxs-lookup"><span data-stu-id="b0f82-105">This topic gives an example of writing a query with complex filtering.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b0f82-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="b0f82-106">Example</span></span>  
 <span data-ttu-id="b0f82-107">Ten przykład pokazuje, jak znaleźć wszystkie `PurchaseOrder` elementy mające element podrzędny `Address`, który ma atrybut `Type` równy "wysyłce" i podrzędny element `State` równy "NY".</span><span class="sxs-lookup"><span data-stu-id="b0f82-107">This example shows how to find all `PurchaseOrder` elements that have a child `Address` element that has a `Type` attribute equal to "Shipping" and a child `State` element equal to "NY".</span></span> <span data-ttu-id="b0f82-108">Używa zagnieżdżonego zapytania w klauzuli `Where`, a operator `Any` zwraca `True`, jeśli kolekcja zawiera jakiekolwiek elementy.</span><span class="sxs-lookup"><span data-stu-id="b0f82-108">It uses a nested query in the `Where` clause, and the `Any` operator returns `True` if the collection has any elements in it.</span></span>  
  
 <span data-ttu-id="b0f82-109">W tym przykładzie zastosowano następujący dokument XML: [przykładowy plik XML: wiele zamówień zakupu (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="b0f82-109">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="b0f82-110">Aby uzyskać więcej informacji na temat operatora `Any`, zobacz [Kwantyfikatory operacji (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md).</span><span class="sxs-lookup"><span data-stu-id="b0f82-110">For more information about the `Any` operator, see [Quantifier Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md).</span></span>  
  
```vb  
Dim root As XElement = XElement.Load("PurchaseOrders.xml")  
Dim purchaseOrders As IEnumerable(Of XElement) = _  
    From el In root.<PurchaseOrder> _  
    Where _  
        (From add In el.<Address> _  
        Where _  
             add.@Type = "Shipping" And _  
             add.<State>.Value = "NY" _  
        Select add) _  
    .Any() _  
    Select el  
For Each el As XElement In purchaseOrders  
    Console.WriteLine(el.@PurchaseOrderNumber)  
Next  
```  
  
 <span data-ttu-id="b0f82-111">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="b0f82-111">This code produces the following output:</span></span>  
  
```console  
99505  
```  
  
## <a name="example"></a><span data-ttu-id="b0f82-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="b0f82-112">Example</span></span>  
 <span data-ttu-id="b0f82-113">W poniższym przykładzie pokazano to samo zapytanie dla kodu XML, który znajduje się w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="b0f82-113">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="b0f82-114">Aby uzyskać więcej informacji, zobacz temat [przestrzenie nazw — omówienie (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="b0f82-114">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="b0f82-115">W tym przykładzie zastosowano następujący dokument XML: [przykładowy plik XML: wiele zamówień zakupu w przestrzeni nazw](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="b0f82-115">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders in a Namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span></span>  
  
```vb  
Imports <xmlns:aw='http://www.adventure-works.com'>  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = XElement.Load("PurchaseOrdersInNamespace.xml")  
        Dim purchaseOrders As IEnumerable(Of XElement) = _  
            From el In root.<aw:PurchaseOrder> _  
            Where _  
                (From add In el.<aw:Address> _  
                Where _  
                     add.@aw:Type = "Shipping" And _  
                     add.<aw:State>.Value = "NY" _  
                Select add) _  
            .Any() _  
            Select el  
        For Each el As XElement In purchaseOrders  
            Console.WriteLine(el.@aw:PurchaseOrderNumber)  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="b0f82-116">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="b0f82-116">This code produces the following output:</span></span>  
  
```console  
99505  
```  
  
## <a name="see-also"></a><span data-ttu-id="b0f82-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b0f82-117">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [<span data-ttu-id="b0f82-118">Zapytania podstawowe (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b0f82-118">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
- [<span data-ttu-id="b0f82-119">Właściwości osi elementu podrzędnego XML</span><span class="sxs-lookup"><span data-stu-id="b0f82-119">XML Child Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)
- [<span data-ttu-id="b0f82-120">Właściwości osi atrybutu XML</span><span class="sxs-lookup"><span data-stu-id="b0f82-120">XML Attribute Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)
- [<span data-ttu-id="b0f82-121">Właściwość wartości XML</span><span class="sxs-lookup"><span data-stu-id="b0f82-121">XML Value Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
- [<span data-ttu-id="b0f82-122">Operacje projekcji (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b0f82-122">Projection Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projection-operations.md)
- [<span data-ttu-id="b0f82-123">Operacje kwantyfikatora (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b0f82-123">Quantifier Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md)
