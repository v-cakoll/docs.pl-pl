---
title: LINQ to XML Annotations2
ms.date: 07/20/2015
ms.assetid: c3e8b3ff-fceb-4428-b0ca-1ed6f128aac8
ms.openlocfilehash: 917129a06483ce2001e178d744440504533d28d6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84369014"
---
# <a name="linq-to-xml-annotations"></a><span data-ttu-id="33609-102">Adnotacje LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="33609-102">LINQ to XML Annotations</span></span>
<span data-ttu-id="33609-103">Adnotacje w programie [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] umożliwiają kojarzenie dowolnego dowolnego dowolnego obiektu dowolnego dowolnego typu z dowolnym składnikiem XML w drzewie XML.</span><span class="sxs-lookup"><span data-stu-id="33609-103">Annotations in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] enable you to associate any arbitrary object of any arbitrary type with any XML component in an XML tree.</span></span>  
  
 <span data-ttu-id="33609-104">Aby dodać adnotację do składnika XML, takiego jak <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XAttribute> , należy wywołać <xref:System.Xml.Linq.XObject.AddAnnotation%2A> metodę.</span><span class="sxs-lookup"><span data-stu-id="33609-104">To add an annotation to an XML component, such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute>, you call the <xref:System.Xml.Linq.XObject.AddAnnotation%2A> method.</span></span> <span data-ttu-id="33609-105">Pobierasz adnotacje według typu.</span><span class="sxs-lookup"><span data-stu-id="33609-105">You retrieve annotations by type.</span></span>  
  
 <span data-ttu-id="33609-106">Zwróć uwagę, że adnotacje nie są częścią sprawdzonych XML; nie są one serializowane ani deserializowane.</span><span class="sxs-lookup"><span data-stu-id="33609-106">Note that annotations are not part of the XML infoset; they are not serialized or deserialized.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="33609-107">Metody</span><span class="sxs-lookup"><span data-stu-id="33609-107">Methods</span></span>  
 <span data-ttu-id="33609-108">Podczas pracy z adnotacjami można użyć następujących metod:</span><span class="sxs-lookup"><span data-stu-id="33609-108">You can use the following methods when working with annotations:</span></span>  
  
|<span data-ttu-id="33609-109">Metoda</span><span class="sxs-lookup"><span data-stu-id="33609-109">Method</span></span>|<span data-ttu-id="33609-110">Opis</span><span class="sxs-lookup"><span data-stu-id="33609-110">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XObject.AddAnnotation%2A>|<span data-ttu-id="33609-111">Dodaje obiekt do listy adnotacji elementu <xref:System.Xml.Linq.XObject> .</span><span class="sxs-lookup"><span data-stu-id="33609-111">Adds an object to the annotation list of an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObject.Annotation%2A>|<span data-ttu-id="33609-112">Pobiera pierwszy obiekt adnotacji określonego typu z <xref:System.Xml.Linq.XObject> .</span><span class="sxs-lookup"><span data-stu-id="33609-112">Gets the first annotation object of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObject.Annotations%2A>|<span data-ttu-id="33609-113">Pobiera kolekcję adnotacji określonego typu dla <xref:System.Xml.Linq.XObject> .</span><span class="sxs-lookup"><span data-stu-id="33609-113">Gets a collection of annotations of the specified type for an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObject.RemoveAnnotations%2A>|<span data-ttu-id="33609-114">Usuwa adnotacje określonego typu z <xref:System.Xml.Linq.XObject> .</span><span class="sxs-lookup"><span data-stu-id="33609-114">Removes the annotations of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="33609-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="33609-115">See also</span></span>

- [<span data-ttu-id="33609-116">Zaawansowane programowanie LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="33609-116">Advanced LINQ to XML Programming (Visual Basic)</span></span>](advanced-linq-to-xml-programming.md)
