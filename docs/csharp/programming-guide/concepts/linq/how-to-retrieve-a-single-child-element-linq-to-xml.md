---
title: 'Porady: pobieranie jeden typ elementów podrzędnych (LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: ce37db9e-76fa-46eb-b4cc-e8f32d22ad90
ms.openlocfilehash: 77ccd56d1d131a740bb90ef4258ef35504f5e3cb
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44206198"
---
# <a name="how-to-retrieve-a-single-child-element-linq-to-xml-c"></a><span data-ttu-id="5c8f1-102">Porady: pobieranie jeden typ elementów podrzędnych (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="5c8f1-102">How to: Retrieve a Single Child Element (LINQ to XML) (C#)</span></span>
<span data-ttu-id="5c8f1-103">W tym temacie wyjaśniono, jak pobrać jeden typ elementów podrzędnych, biorąc pod uwagę nazwę elementu podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="5c8f1-103">This topic explains how to retrieve a single child element, given the name of the child element.</span></span> <span data-ttu-id="5c8f1-104">Znając nazwę elementu podrzędnego elementu i że istnieje tylko jeden element o tej nazwie może być wygodna można pobrać tylko jeden element, zamiast kolekcji.</span><span class="sxs-lookup"><span data-stu-id="5c8f1-104">When you know the name of the child element and that there is only one element that has this name, it can be convenient to retrieve just one element, instead of a collection.</span></span>  
  
 <span data-ttu-id="5c8f1-105"><xref:System.Xml.Linq.XContainer.Element%2A> Metoda zwraca pierwszy element podrzędny <xref:System.Xml.Linq.XElement> z określonym <xref:System.Xml.Linq.XName>.</span><span class="sxs-lookup"><span data-stu-id="5c8f1-105">The <xref:System.Xml.Linq.XContainer.Element%2A> method returns the first child <xref:System.Xml.Linq.XElement> with the specified <xref:System.Xml.Linq.XName>.</span></span>  
  
 <span data-ttu-id="5c8f1-106">Jeśli chcesz pobrać jeden typ elementów podrzędnych w języku Visual Basic, typowym podejściem jest używać właściwości XML, a następnie pobrać pierwszy element tablicy notacji indeksatora.</span><span class="sxs-lookup"><span data-stu-id="5c8f1-106">If you want to retrieve a single child element in Visual Basic, a common approach is to use the XML property, and then retrieve the first element using array indexer notation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5c8f1-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="5c8f1-107">Example</span></span>  
 <span data-ttu-id="5c8f1-108">W poniższym przykładzie pokazano użycie <xref:System.Xml.Linq.XContainer.Element%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="5c8f1-108">The following example demonstrates the use of the <xref:System.Xml.Linq.XContainer.Element%2A> method.</span></span> <span data-ttu-id="5c8f1-109">W tym przykładzie pobiera drzewa XML o nazwie `po` i znajdzie pierwszy element o nazwie `Comment`.</span><span class="sxs-lookup"><span data-stu-id="5c8f1-109">This example takes the XML tree named `po` and finds the first element named `Comment`.</span></span>  
  
 <span data-ttu-id="5c8f1-110">W języku Visual Basic przykładzie przy użyciu notacji indeksatora tablicy, aby pobrać jeden element.</span><span class="sxs-lookup"><span data-stu-id="5c8f1-110">The Visual Basic example shows using array indexer notation to retrieve a single element.</span></span>  
  
 <span data-ttu-id="5c8f1-111">W tym przykładzie użyto następujący dokument XML: [przykładowy plik XML: typowe zamówienie zakupu (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="5c8f1-111">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
```csharp  
XElement po = XElement.Load("PurchaseOrder.xml");  
XElement e = po.Element("DeliveryNotes");  
Console.WriteLine(e);  
```  
  
 <span data-ttu-id="5c8f1-112">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="5c8f1-112">This example produces the following output:</span></span>  
  
```xml  
<DeliveryNotes>Please leave packages in shed by driveway.</DeliveryNotes>  
```  
  
## <a name="example"></a><span data-ttu-id="5c8f1-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="5c8f1-113">Example</span></span>  
 <span data-ttu-id="5c8f1-114">Poniższy przykład pokazuje ten sam kod XML, który znajduje się w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="5c8f1-114">The following example shows the same code for XML that is in a namespace.</span></span> <span data-ttu-id="5c8f1-115">Aby uzyskać więcej informacji, zobacz [Praca z przestrzeniami nazw XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="5c8f1-115">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="5c8f1-116">W tym przykładzie użyto następujący dokument XML: [przykładowy plik XML: typowe zamówienie zakupu w Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="5c8f1-116">This example uses the following XML document: [Sample XML File: Typical Purchase Order in a Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md).</span></span>  
  
```csharp  
XElement po = XElement.Load("PurchaseOrderInNamespace.xml");  
XNamespace aw = "http://www.adventure-works.com";  
XElement e = po.Element(aw + "DeliveryNotes");  
Console.WriteLine(e);  
```  
  
 <span data-ttu-id="5c8f1-117">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="5c8f1-117">This example produces the following output:</span></span>  
  
```xml  
<aw:DeliveryNotes xmlns:aw="http://www.adventure-works.com">Please leave packages in shed by driveway.</aw:DeliveryNotes>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5c8f1-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5c8f1-118">See Also</span></span>

- [<span data-ttu-id="5c8f1-119">LINQ do XML osi (C#)</span><span class="sxs-lookup"><span data-stu-id="5c8f1-119">LINQ to XML Axes (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
