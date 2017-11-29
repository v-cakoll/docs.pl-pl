---
title: "Porady: Pobieranie elementu podrzędnego pojedynczego (LINQ do XML) (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: ce37db9e-76fa-46eb-b4cc-e8f32d22ad90
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 722a6b6630fd08a328a26dcef4d72a8cdd817924
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-retrieve-a-single-child-element-linq-to-xml-c"></a><span data-ttu-id="1ed24-102">Porady: Pobieranie elementu podrzędnego pojedynczego (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="1ed24-102">How to: Retrieve a Single Child Element (LINQ to XML) (C#)</span></span>
<span data-ttu-id="1ed24-103">W tym temacie wyjaśniono, jak pobrać element pojedynczy element potomny, nazwę elementu podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="1ed24-103">This topic explains how to retrieve a single child element, given the name of the child element.</span></span> <span data-ttu-id="1ed24-104">Jeśli znasz nazwę elementu podrzędnego elementu i że istnieje tylko jeden element o tej nazwie, może być wygodną można pobrać tylko jeden element, zamiast kolekcji.</span><span class="sxs-lookup"><span data-stu-id="1ed24-104">When you know the name of the child element and that there is only one element that has this name, it can be convenient to retrieve just one element, instead of a collection.</span></span>  
  
 <span data-ttu-id="1ed24-105"><xref:System.Xml.Linq.XContainer.Element%2A> Metoda zwraca pierwszy element podrzędny <xref:System.Xml.Linq.XElement> z określonym <xref:System.Xml.Linq.XName>.</span><span class="sxs-lookup"><span data-stu-id="1ed24-105">The <xref:System.Xml.Linq.XContainer.Element%2A> method returns the first child <xref:System.Xml.Linq.XElement> with the specified <xref:System.Xml.Linq.XName>.</span></span>  
  
 <span data-ttu-id="1ed24-106">Jeśli chcesz pobrać pojedynczym elemencie podrzędnym w języku Visual Basic, typowym podejściem jest przy użyciu właściwości XML, a następnie pobrać pierwszy element tablicy notacji indeksatora.</span><span class="sxs-lookup"><span data-stu-id="1ed24-106">If you want to retrieve a single child element in Visual Basic, a common approach is to use the XML property, and then retrieve the first element using array indexer notation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1ed24-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="1ed24-107">Example</span></span>  
 <span data-ttu-id="1ed24-108">W poniższym przykładzie pokazano użycie <xref:System.Xml.Linq.XContainer.Element%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="1ed24-108">The following example demonstrates the use of the <xref:System.Xml.Linq.XContainer.Element%2A> method.</span></span> <span data-ttu-id="1ed24-109">W tym przykładzie przyjmuje drzewa XML o nazwie `po` i klient znajdzie pierwszy element o nazwie `Comment`.</span><span class="sxs-lookup"><span data-stu-id="1ed24-109">This example takes the XML tree named `po` and finds the first element named `Comment`.</span></span>  
  
 <span data-ttu-id="1ed24-110">W języku Visual Basic przykładzie przy użyciu notacji indeksatora tablicy można pobrać pojedynczy element.</span><span class="sxs-lookup"><span data-stu-id="1ed24-110">The Visual Basic example shows using array indexer notation to retrieve a single element.</span></span>  
  
 <span data-ttu-id="1ed24-111">W tym przykładzie użyto następujących dokumentu XML: [przykładowego pliku XML: typowe zamówienia zakupu (LINQ do XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="1ed24-111">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
```csharp  
XElement po = XElement.Load("PurchaseOrder.xml");  
XElement e = po.Element("DeliveryNotes");  
Console.WriteLine(e);  
```  
  
 <span data-ttu-id="1ed24-112">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="1ed24-112">This example produces the following output:</span></span>  
  
```xml  
<DeliveryNotes>Please leave packages in shed by driveway.</DeliveryNotes>  
```  
  
## <a name="example"></a><span data-ttu-id="1ed24-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="1ed24-113">Example</span></span>  
 <span data-ttu-id="1ed24-114">Poniższy przykład przedstawia ten sam kod XML, który znajduje się w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="1ed24-114">The following example shows the same code for XML that is in a namespace.</span></span> <span data-ttu-id="1ed24-115">Aby uzyskać więcej informacji, zobacz [Praca z przestrzeni nazw XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="1ed24-115">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="1ed24-116">W tym przykładzie użyto następujących dokumentu XML: [przykładowego pliku XML: typowe zamówienia zakupu w Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="1ed24-116">This example uses the following XML document: [Sample XML File: Typical Purchase Order in a Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md).</span></span>  
  
```csharp  
XElement po = XElement.Load("PurchaseOrderInNamespace.xml");  
XNamespace aw = "http://www.adventure-works.com";  
XElement e = po.Element(aw + "DeliveryNotes");  
Console.WriteLine(e);  
```  
  
 <span data-ttu-id="1ed24-117">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="1ed24-117">This example produces the following output:</span></span>  
  
```xml  
<aw:DeliveryNotes xmlns:aw="http://www.adventure-works.com">Please leave packages in shed by driveway.</aw:DeliveryNotes>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1ed24-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1ed24-118">See Also</span></span>  
 [<span data-ttu-id="1ed24-119">LINQ do osi XML (C#)</span><span class="sxs-lookup"><span data-stu-id="1ed24-119">LINQ to XML Axes (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
