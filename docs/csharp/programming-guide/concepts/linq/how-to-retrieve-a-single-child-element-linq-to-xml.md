---
title: Jak pobrać pojedynczy element podrzędny (LINQ do XML) (C#)
ms.date: 07/20/2015
ms.assetid: ce37db9e-76fa-46eb-b4cc-e8f32d22ad90
ms.openlocfilehash: 0e10cf230a73e6419f2d9c663766f9a24a0930af
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75347473"
---
# <a name="how-to-retrieve-a-single-child-element-linq-to-xml-c"></a><span data-ttu-id="b7d1b-102">Jak pobrać pojedynczy element podrzędny (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="b7d1b-102">How to retrieve a single child element (LINQ to XML) (C#)</span></span>
<span data-ttu-id="b7d1b-103">W tym temacie wyjaśniono, jak pobrać pojedynczy element podrzędny, biorąc pod uwagę nazwę elementu podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="b7d1b-103">This topic explains how to retrieve a single child element, given the name of the child element.</span></span> <span data-ttu-id="b7d1b-104">Gdy znasz nazwę elementu podrzędnego i że istnieje tylko jeden element, który ma tę nazwę, może być wygodne do pobrania tylko jeden element, zamiast kolekcji.</span><span class="sxs-lookup"><span data-stu-id="b7d1b-104">When you know the name of the child element and that there is only one element that has this name, it can be convenient to retrieve just one element, instead of a collection.</span></span>  
  
 <span data-ttu-id="b7d1b-105">Metoda <xref:System.Xml.Linq.XContainer.Element%2A> zwraca pierwsze <xref:System.Xml.Linq.XElement> dziecko z <xref:System.Xml.Linq.XName>określonym .</span><span class="sxs-lookup"><span data-stu-id="b7d1b-105">The <xref:System.Xml.Linq.XContainer.Element%2A> method returns the first child <xref:System.Xml.Linq.XElement> with the specified <xref:System.Xml.Linq.XName>.</span></span>  
  
 <span data-ttu-id="b7d1b-106">Jeśli chcesz pobrać pojedynczy element podrzędny w języku Visual Basic, typowym podejściem jest użycie właściwości XML, a następnie pobranie pierwszego elementu przy użyciu notacji indeksatora tablicy.</span><span class="sxs-lookup"><span data-stu-id="b7d1b-106">If you want to retrieve a single child element in Visual Basic, a common approach is to use the XML property, and then retrieve the first element using array indexer notation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b7d1b-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="b7d1b-107">Example</span></span>  
 <span data-ttu-id="b7d1b-108">W poniższym przykładzie przedstawiono <xref:System.Xml.Linq.XContainer.Element%2A> użycie metody.</span><span class="sxs-lookup"><span data-stu-id="b7d1b-108">The following example demonstrates the use of the <xref:System.Xml.Linq.XContainer.Element%2A> method.</span></span> <span data-ttu-id="b7d1b-109">W tym przykładzie przyjmuje `po` drzewo XML o `Comment`nazwie i znajduje pierwszy element o nazwie .</span><span class="sxs-lookup"><span data-stu-id="b7d1b-109">This example takes the XML tree named `po` and finds the first element named `Comment`.</span></span>  
  
 <span data-ttu-id="b7d1b-110">W przykładzie języka Visual Basic przedstawiono przy użyciu notacji indeksatora tablicy do pobierania pojedynczego elementu.</span><span class="sxs-lookup"><span data-stu-id="b7d1b-110">The Visual Basic example shows using array indexer notation to retrieve a single element.</span></span>  
  
 <span data-ttu-id="b7d1b-111">W tym przykładzie użyto następującego dokumentu XML: [Przykładowy plik XML: Typowe zamówienie zakupu (LINQ do XML).](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md)</span><span class="sxs-lookup"><span data-stu-id="b7d1b-111">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
```csharp  
XElement po = XElement.Load("PurchaseOrder.xml");  
XElement e = po.Element("DeliveryNotes");  
Console.WriteLine(e);  
```  
  
 <span data-ttu-id="b7d1b-112">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="b7d1b-112">This example produces the following output:</span></span>  
  
```xml  
<DeliveryNotes>Please leave packages in shed by driveway.</DeliveryNotes>  
```  
  
## <a name="example"></a><span data-ttu-id="b7d1b-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="b7d1b-113">Example</span></span>  
 <span data-ttu-id="b7d1b-114">W poniższym przykładzie przedstawiono ten sam kod dla Języka XML, który znajduje się w obszarze nazw.</span><span class="sxs-lookup"><span data-stu-id="b7d1b-114">The following example shows the same code for XML that is in a namespace.</span></span> <span data-ttu-id="b7d1b-115">Aby uzyskać więcej informacji, zobacz [Omówienie przestrzeni nazw (LINQ do XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="b7d1b-115">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="b7d1b-116">W tym przykładzie użyto następującego dokumentu XML: [Przykładowy plik XML: Typowe zamówienie zakupu w obszarze nazw](./sample-xml-file-typical-purchase-order-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="b7d1b-116">This example uses the following XML document: [Sample XML File: Typical Purchase Order in a Namespace](./sample-xml-file-typical-purchase-order-in-a-namespace.md).</span></span>  
  
```csharp  
XElement po = XElement.Load("PurchaseOrderInNamespace.xml");  
XNamespace aw = "http://www.adventure-works.com";  
XElement e = po.Element(aw + "DeliveryNotes");  
Console.WriteLine(e);  
```  
  
 <span data-ttu-id="b7d1b-117">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="b7d1b-117">This example produces the following output:</span></span>  
  
```xml  
<aw:DeliveryNotes xmlns:aw="http://www.adventure-works.com">Please leave packages in shed by driveway.</aw:DeliveryNotes>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b7d1b-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b7d1b-118">See also</span></span>

- [<span data-ttu-id="b7d1b-119">LINQ do osi XML (C#)</span><span class="sxs-lookup"><span data-stu-id="b7d1b-119">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
