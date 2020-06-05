---
title: 'Instrukcje: pobieranie pojedynczego elementu podrzędnego (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 0033e258-d9c4-4569-86f6-79b7c06d1204
ms.openlocfilehash: ab28ddd960374b22f44ac0c8fc7bddfe0608b8c5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397846"
---
# <a name="how-to-retrieve-a-single-child-element-linq-to-xml-visual-basic"></a><span data-ttu-id="7c344-102">Instrukcje: Pobieranie pojedynczego elementu podrzędnego (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7c344-102">How to: Retrieve a Single Child Element (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="7c344-103">W tym temacie wyjaśniono, jak pobrać pojedynczy element podrzędny o nazwie elementu podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="7c344-103">This topic explains how to retrieve a single child element, given the name of the child element.</span></span> <span data-ttu-id="7c344-104">Gdy znana jest nazwa elementu podrzędnego i istnieje tylko jeden element o tej nazwie, może być wygodne pobranie tylko jednego elementu, a nie kolekcji.</span><span class="sxs-lookup"><span data-stu-id="7c344-104">When you know the name of the child element and that there is only one element that has this name, it can be convenient to retrieve just one element, instead of a collection.</span></span>  
  
 <span data-ttu-id="7c344-105"><xref:System.Xml.Linq.XContainer.Element%2A>Metoda zwraca pierwszy element podrzędny <xref:System.Xml.Linq.XElement> z określonym <xref:System.Xml.Linq.XName> .</span><span class="sxs-lookup"><span data-stu-id="7c344-105">The <xref:System.Xml.Linq.XContainer.Element%2A> method returns the first child <xref:System.Xml.Linq.XElement> with the specified <xref:System.Xml.Linq.XName>.</span></span>  
  
 <span data-ttu-id="7c344-106">Jeśli chcesz pobrać pojedynczy element podrzędny w Visual Basic, typowym podejściem jest użycie właściwości XML, a następnie pobranie pierwszego elementu przy użyciu notacji Array indeksator.</span><span class="sxs-lookup"><span data-stu-id="7c344-106">If you want to retrieve a single child element in Visual Basic, a common approach is to use the XML property, and then retrieve the first element using array indexer notation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7c344-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="7c344-107">Example</span></span>  
 <span data-ttu-id="7c344-108">Poniższy przykład demonstruje użycie <xref:System.Xml.Linq.XContainer.Element%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="7c344-108">The following example demonstrates the use of the <xref:System.Xml.Linq.XContainer.Element%2A> method.</span></span> <span data-ttu-id="7c344-109">Ten przykład pobiera drzewo XML o nazwie `po` i odnajduje pierwszy element o nazwie `Comment` .</span><span class="sxs-lookup"><span data-stu-id="7c344-109">This example takes the XML tree named `po` and finds the first element named `Comment`.</span></span>  
  
 <span data-ttu-id="7c344-110">W Visual Basic przykładzie pokazano użycie notacji indeksatora Array do pobrania pojedynczego elementu.</span><span class="sxs-lookup"><span data-stu-id="7c344-110">The Visual Basic example shows using array indexer notation to retrieve a single element.</span></span>  
  
 <span data-ttu-id="7c344-111">W tym przykładzie zastosowano następujący dokument XML: [przykładowy plik XML: typowe zamówienie zakupu (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="7c344-111">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml.md).</span></span>  
  
```vb  
Dim po As XElement = XElement.Load("PurchaseOrder.xml")  
Dim e As XElement = po.<DeliveryNotes>(0)  
Console.WriteLine(e)  
```  
  
 <span data-ttu-id="7c344-112">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="7c344-112">This example produces the following output:</span></span>  
  
```xml  
<DeliveryNotes>Please leave packages in shed by driveway.</DeliveryNotes>  
```  
  
## <a name="example"></a><span data-ttu-id="7c344-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="7c344-113">Example</span></span>  
 <span data-ttu-id="7c344-114">W poniższym przykładzie przedstawiono ten sam kod dla kodu XML, który znajduje się w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="7c344-114">The following example shows the same code for XML that is in a namespace.</span></span> <span data-ttu-id="7c344-115">Aby uzyskać więcej informacji, zobacz temat [przestrzenie nazw — omówienie (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="7c344-115">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="7c344-116">W tym przykładzie zastosowano następujący dokument XML: [przykładowy plik XML: typowe zamówienie zakupu w przestrzeni nazw](sample-xml-file-typical-purchase-order-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="7c344-116">This example uses the following XML document: [Sample XML File: Typical Purchase Order in a Namespace](sample-xml-file-typical-purchase-order-in-a-namespace.md).</span></span>  
  
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
  
 <span data-ttu-id="7c344-117">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="7c344-117">This example produces the following output:</span></span>  
  
```xml  
<aw:DeliveryNotes xmlns:aw="http://www.adventure-works.com">Please leave packages in shed by driveway.</aw:DeliveryNotes>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7c344-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7c344-118">See also</span></span>

- [<span data-ttu-id="7c344-119">Osie LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7c344-119">LINQ to XML Axes (Visual Basic)</span></span>](linq-to-xml-axes.md)
