---
title: Jak pobrać pojedynczy element podrzędny (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: ce37db9e-76fa-46eb-b4cc-e8f32d22ad90
ms.openlocfilehash: 0e10cf230a73e6419f2d9c663766f9a24a0930af
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347473"
---
# <a name="how-to-retrieve-a-single-child-element-linq-to-xml-c"></a><span data-ttu-id="3fe36-102">Jak pobrać pojedynczy element podrzędny (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="3fe36-102">How to retrieve a single child element (LINQ to XML) (C#)</span></span>
<span data-ttu-id="3fe36-103">W tym temacie wyjaśniono, jak pobrać pojedynczy element podrzędny o nazwie elementu podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="3fe36-103">This topic explains how to retrieve a single child element, given the name of the child element.</span></span> <span data-ttu-id="3fe36-104">Gdy znana jest nazwa elementu podrzędnego i istnieje tylko jeden element o tej nazwie, może być wygodne pobranie tylko jednego elementu, a nie kolekcji.</span><span class="sxs-lookup"><span data-stu-id="3fe36-104">When you know the name of the child element and that there is only one element that has this name, it can be convenient to retrieve just one element, instead of a collection.</span></span>  
  
 <span data-ttu-id="3fe36-105">Metoda <xref:System.Xml.Linq.XContainer.Element%2A> zwraca pierwszy <xref:System.Xml.Linq.XElement> podrzędny z określonym <xref:System.Xml.Linq.XName>.</span><span class="sxs-lookup"><span data-stu-id="3fe36-105">The <xref:System.Xml.Linq.XContainer.Element%2A> method returns the first child <xref:System.Xml.Linq.XElement> with the specified <xref:System.Xml.Linq.XName>.</span></span>  
  
 <span data-ttu-id="3fe36-106">Jeśli chcesz pobrać pojedynczy element podrzędny w Visual Basic, typowym podejściem jest użycie właściwości XML, a następnie pobranie pierwszego elementu przy użyciu notacji Array indeksator.</span><span class="sxs-lookup"><span data-stu-id="3fe36-106">If you want to retrieve a single child element in Visual Basic, a common approach is to use the XML property, and then retrieve the first element using array indexer notation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3fe36-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="3fe36-107">Example</span></span>  
 <span data-ttu-id="3fe36-108">Poniższy przykład ilustruje użycie metody <xref:System.Xml.Linq.XContainer.Element%2A>.</span><span class="sxs-lookup"><span data-stu-id="3fe36-108">The following example demonstrates the use of the <xref:System.Xml.Linq.XContainer.Element%2A> method.</span></span> <span data-ttu-id="3fe36-109">Ten przykład pobiera drzewo XML o nazwie `po` i odnajduje pierwszy element o nazwie `Comment`.</span><span class="sxs-lookup"><span data-stu-id="3fe36-109">This example takes the XML tree named `po` and finds the first element named `Comment`.</span></span>  
  
 <span data-ttu-id="3fe36-110">W Visual Basic przykładzie pokazano użycie notacji indeksatora Array do pobrania pojedynczego elementu.</span><span class="sxs-lookup"><span data-stu-id="3fe36-110">The Visual Basic example shows using array indexer notation to retrieve a single element.</span></span>  
  
 <span data-ttu-id="3fe36-111">W tym przykładzie zastosowano następujący dokument XML: [przykładowy plik XML: typowe zamówienie zakupu (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="3fe36-111">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
```csharp  
XElement po = XElement.Load("PurchaseOrder.xml");  
XElement e = po.Element("DeliveryNotes");  
Console.WriteLine(e);  
```  
  
 <span data-ttu-id="3fe36-112">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="3fe36-112">This example produces the following output:</span></span>  
  
```xml  
<DeliveryNotes>Please leave packages in shed by driveway.</DeliveryNotes>  
```  
  
## <a name="example"></a><span data-ttu-id="3fe36-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="3fe36-113">Example</span></span>  
 <span data-ttu-id="3fe36-114">W poniższym przykładzie przedstawiono ten sam kod dla kodu XML, który znajduje się w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="3fe36-114">The following example shows the same code for XML that is in a namespace.</span></span> <span data-ttu-id="3fe36-115">Aby uzyskać więcej informacji, zobacz temat [przestrzenie nazw —C#omówienie (LINQ to XML) ()](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="3fe36-115">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="3fe36-116">W tym przykładzie zastosowano następujący dokument XML: [przykładowy plik XML: typowe zamówienie zakupu w przestrzeni nazw](./sample-xml-file-typical-purchase-order-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="3fe36-116">This example uses the following XML document: [Sample XML File: Typical Purchase Order in a Namespace](./sample-xml-file-typical-purchase-order-in-a-namespace.md).</span></span>  
  
```csharp  
XElement po = XElement.Load("PurchaseOrderInNamespace.xml");  
XNamespace aw = "http://www.adventure-works.com";  
XElement e = po.Element(aw + "DeliveryNotes");  
Console.WriteLine(e);  
```  
  
 <span data-ttu-id="3fe36-117">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="3fe36-117">This example produces the following output:</span></span>  
  
```xml  
<aw:DeliveryNotes xmlns:aw="http://www.adventure-works.com">Please leave packages in shed by driveway.</aw:DeliveryNotes>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3fe36-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3fe36-118">See also</span></span>

- [<span data-ttu-id="3fe36-119">Osie LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="3fe36-119">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
