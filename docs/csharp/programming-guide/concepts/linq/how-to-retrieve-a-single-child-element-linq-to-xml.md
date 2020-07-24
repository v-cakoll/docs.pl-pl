---
title: Jak pobrać pojedynczy element podrzędny (LINQ to XML) (C#)
description: Dowiedz się, jak za pomocą LINQ to XML pobrać pojedynczy element podrzędny według nazwy. W tym przykładzie w języku C# Metoda element zwraca pierwszy określony element podrzędny.
ms.date: 07/20/2015
ms.assetid: ce37db9e-76fa-46eb-b4cc-e8f32d22ad90
ms.openlocfilehash: c3a044f30cf2e411bdff52586c7a370b626f41bc
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103273"
---
# <a name="how-to-retrieve-a-single-child-element-linq-to-xml-c"></a><span data-ttu-id="af5cb-104">Jak pobrać pojedynczy element podrzędny (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="af5cb-104">How to retrieve a single child element (LINQ to XML) (C#)</span></span>
<span data-ttu-id="af5cb-105">W tym temacie wyjaśniono, jak pobrać pojedynczy element podrzędny o nazwie elementu podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="af5cb-105">This topic explains how to retrieve a single child element, given the name of the child element.</span></span> <span data-ttu-id="af5cb-106">Gdy znana jest nazwa elementu podrzędnego i istnieje tylko jeden element o tej nazwie, może być wygodne pobranie tylko jednego elementu, a nie kolekcji.</span><span class="sxs-lookup"><span data-stu-id="af5cb-106">When you know the name of the child element and that there is only one element that has this name, it can be convenient to retrieve just one element, instead of a collection.</span></span>  
  
 <span data-ttu-id="af5cb-107"><xref:System.Xml.Linq.XContainer.Element%2A>Metoda zwraca pierwszy element podrzędny <xref:System.Xml.Linq.XElement> z określonym <xref:System.Xml.Linq.XName> .</span><span class="sxs-lookup"><span data-stu-id="af5cb-107">The <xref:System.Xml.Linq.XContainer.Element%2A> method returns the first child <xref:System.Xml.Linq.XElement> with the specified <xref:System.Xml.Linq.XName>.</span></span>  
  
 <span data-ttu-id="af5cb-108">Jeśli chcesz pobrać pojedynczy element podrzędny w Visual Basic, typowym podejściem jest użycie właściwości XML, a następnie pobranie pierwszego elementu przy użyciu notacji Array indeksator.</span><span class="sxs-lookup"><span data-stu-id="af5cb-108">If you want to retrieve a single child element in Visual Basic, a common approach is to use the XML property, and then retrieve the first element using array indexer notation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="af5cb-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="af5cb-109">Example</span></span>  
 <span data-ttu-id="af5cb-110">Poniższy przykład demonstruje użycie <xref:System.Xml.Linq.XContainer.Element%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="af5cb-110">The following example demonstrates the use of the <xref:System.Xml.Linq.XContainer.Element%2A> method.</span></span> <span data-ttu-id="af5cb-111">Ten przykład pobiera drzewo XML o nazwie `po` i odnajduje pierwszy element o nazwie `Comment` .</span><span class="sxs-lookup"><span data-stu-id="af5cb-111">This example takes the XML tree named `po` and finds the first element named `Comment`.</span></span>  
  
 <span data-ttu-id="af5cb-112">W Visual Basic przykładzie pokazano użycie notacji indeksatora Array do pobrania pojedynczego elementu.</span><span class="sxs-lookup"><span data-stu-id="af5cb-112">The Visual Basic example shows using array indexer notation to retrieve a single element.</span></span>  
  
 <span data-ttu-id="af5cb-113">W tym przykładzie zastosowano następujący dokument XML: [przykładowy plik XML: typowe zamówienie zakupu (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="af5cb-113">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
```csharp  
XElement po = XElement.Load("PurchaseOrder.xml");  
XElement e = po.Element("DeliveryNotes");  
Console.WriteLine(e);  
```  
  
 <span data-ttu-id="af5cb-114">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="af5cb-114">This example produces the following output:</span></span>  
  
```xml  
<DeliveryNotes>Please leave packages in shed by driveway.</DeliveryNotes>  
```  
  
## <a name="example"></a><span data-ttu-id="af5cb-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="af5cb-115">Example</span></span>  
 <span data-ttu-id="af5cb-116">W poniższym przykładzie przedstawiono ten sam kod dla kodu XML, który znajduje się w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="af5cb-116">The following example shows the same code for XML that is in a namespace.</span></span> <span data-ttu-id="af5cb-117">Aby uzyskać więcej informacji, zobacz temat [przestrzenie nazw — omówienie (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="af5cb-117">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="af5cb-118">W tym przykładzie zastosowano następujący dokument XML: [przykładowy plik XML: typowe zamówienie zakupu w przestrzeni nazw](./sample-xml-file-typical-purchase-order-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="af5cb-118">This example uses the following XML document: [Sample XML File: Typical Purchase Order in a Namespace](./sample-xml-file-typical-purchase-order-in-a-namespace.md).</span></span>  
  
```csharp  
XElement po = XElement.Load("PurchaseOrderInNamespace.xml");  
XNamespace aw = "http://www.adventure-works.com";  
XElement e = po.Element(aw + "DeliveryNotes");  
Console.WriteLine(e);  
```  
  
 <span data-ttu-id="af5cb-119">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="af5cb-119">This example produces the following output:</span></span>  
  
```xml  
<aw:DeliveryNotes xmlns:aw="http://www.adventure-works.com">Please leave packages in shed by driveway.</aw:DeliveryNotes>  
```  
  
## <a name="see-also"></a><span data-ttu-id="af5cb-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="af5cb-120">See also</span></span>

- [<span data-ttu-id="af5cb-121">Osie LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="af5cb-121">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
