---
title: 'Porady: Pobieranie elementu podrzędnego pojedynczego (LINQ do XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 0033e258-d9c4-4569-86f6-79b7c06d1204
ms.openlocfilehash: 9f2b767dcfa68b732eb3f9d0552ec7404658d591
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33643242"
---
# <a name="how-to-retrieve-a-single-child-element-linq-to-xml-visual-basic"></a><span data-ttu-id="ddf3a-102">Porady: Pobieranie elementu podrzędnego pojedynczego (LINQ do XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ddf3a-102">How to: Retrieve a Single Child Element (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="ddf3a-103">W tym temacie wyjaśniono, jak pobrać element pojedynczy element potomny, nazwę elementu podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="ddf3a-103">This topic explains how to retrieve a single child element, given the name of the child element.</span></span> <span data-ttu-id="ddf3a-104">Jeśli znasz nazwę elementu podrzędnego elementu i że istnieje tylko jeden element o tej nazwie, może być wygodną można pobrać tylko jeden element, zamiast kolekcji.</span><span class="sxs-lookup"><span data-stu-id="ddf3a-104">When you know the name of the child element and that there is only one element that has this name, it can be convenient to retrieve just one element, instead of a collection.</span></span>  
  
 <span data-ttu-id="ddf3a-105"><xref:System.Xml.Linq.XContainer.Element%2A> Metoda zwraca pierwszy element podrzędny <xref:System.Xml.Linq.XElement> z określonym <xref:System.Xml.Linq.XName>.</span><span class="sxs-lookup"><span data-stu-id="ddf3a-105">The <xref:System.Xml.Linq.XContainer.Element%2A> method returns the first child <xref:System.Xml.Linq.XElement> with the specified <xref:System.Xml.Linq.XName>.</span></span>  
  
 <span data-ttu-id="ddf3a-106">Jeśli chcesz pobrać pojedynczym elemencie podrzędnym w języku Visual Basic, typowym podejściem jest przy użyciu właściwości XML, a następnie pobrać pierwszy element tablicy notacji indeksatora.</span><span class="sxs-lookup"><span data-stu-id="ddf3a-106">If you want to retrieve a single child element in Visual Basic, a common approach is to use the XML property, and then retrieve the first element using array indexer notation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ddf3a-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="ddf3a-107">Example</span></span>  
 <span data-ttu-id="ddf3a-108">W poniższym przykładzie pokazano użycie <xref:System.Xml.Linq.XContainer.Element%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="ddf3a-108">The following example demonstrates the use of the <xref:System.Xml.Linq.XContainer.Element%2A> method.</span></span> <span data-ttu-id="ddf3a-109">W tym przykładzie przyjmuje drzewa XML o nazwie `po` i klient znajdzie pierwszy element o nazwie `Comment`.</span><span class="sxs-lookup"><span data-stu-id="ddf3a-109">This example takes the XML tree named `po` and finds the first element named `Comment`.</span></span>  
  
 <span data-ttu-id="ddf3a-110">W języku Visual Basic przykładzie przy użyciu notacji indeksatora tablicy można pobrać pojedynczy element.</span><span class="sxs-lookup"><span data-stu-id="ddf3a-110">The Visual Basic example shows using array indexer notation to retrieve a single element.</span></span>  
  
 <span data-ttu-id="ddf3a-111">W tym przykładzie użyto następujących dokumentu XML: [przykładowego pliku XML: typowe zamówienia zakupu (LINQ do XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="ddf3a-111">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).</span></span>  
  
```vb  
Dim po As XElement = XElement.Load("PurchaseOrder.xml")  
Dim e As XElement = po.<DeliveryNotes>(0)  
Console.WriteLine(e)  
```  
  
 <span data-ttu-id="ddf3a-112">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="ddf3a-112">This example produces the following output:</span></span>  
  
```xml  
<DeliveryNotes>Please leave packages in shed by driveway.</DeliveryNotes>  
```  
  
## <a name="example"></a><span data-ttu-id="ddf3a-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="ddf3a-113">Example</span></span>  
 <span data-ttu-id="ddf3a-114">Poniższy przykład przedstawia ten sam kod XML, który znajduje się w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="ddf3a-114">The following example shows the same code for XML that is in a namespace.</span></span> <span data-ttu-id="ddf3a-115">Aby uzyskać więcej informacji, zobacz [Praca z przestrzeni nazw XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="ddf3a-115">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="ddf3a-116">W tym przykładzie użyto następujących dokumentu XML: [przykładowego pliku XML: typowe zamówienia zakupu w Namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="ddf3a-116">This example uses the following XML document: [Sample XML File: Typical Purchase Order in a Namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md).</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim po As XElement = XElement.Load("PurchaseOrderInNamespace.xml")  
        Dim e As XElement = po.<aw:DeliveryNotes>(0)  
        Console.WriteLine(e)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="ddf3a-117">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="ddf3a-117">This example produces the following output:</span></span>  
  
```xml  
<aw:DeliveryNotes xmlns:aw="http://www.adventure-works.com">Please leave packages in shed by driveway.</aw:DeliveryNotes>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ddf3a-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ddf3a-118">See Also</span></span>  
 [<span data-ttu-id="ddf3a-119">LINQ do osi XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ddf3a-119">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
