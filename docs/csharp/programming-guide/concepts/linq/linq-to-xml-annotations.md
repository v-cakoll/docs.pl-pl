---
title: LINQ do XML Annotations3
ms.date: 07/20/2015
ms.assetid: 54e7b9d0-07f5-488f-9065-b6e6b870f810
ms.openlocfilehash: 8b8e03b0174ad2bf044c21eb9a9d3391da37fb7f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33320121"
---
# <a name="linq-to-xml-annotations"></a><span data-ttu-id="60028-102">LINQ do XML adnotacji</span><span class="sxs-lookup"><span data-stu-id="60028-102">LINQ to XML Annotations</span></span>
<span data-ttu-id="60028-103">Adnotacje w [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] można skojarzyć dowolnych obiektów dowolnego typu dowolnego z dowolnym składnikiem XML w drzewie XML.</span><span class="sxs-lookup"><span data-stu-id="60028-103">Annotations in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] enable you to associate any arbitrary object of any arbitrary type with any XML component in an XML tree.</span></span>  
  
 <span data-ttu-id="60028-104">Dodawanie adnotacji do elementu XML, takich jak <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XAttribute>, należy wywołać <xref:System.Xml.Linq.XObject.AddAnnotation%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="60028-104">To add an annotation to an XML component, such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute>, you call the <xref:System.Xml.Linq.XObject.AddAnnotation%2A> method.</span></span> <span data-ttu-id="60028-105">Możesz pobrać adnotacje według typu.</span><span class="sxs-lookup"><span data-stu-id="60028-105">You retrieve annotations by type.</span></span>  
  
 <span data-ttu-id="60028-106">Należy pamiętać, że adnotacje nie są częścią XML typu infoset sprawdzonych; nie jest serializowany lub deserializowany.</span><span class="sxs-lookup"><span data-stu-id="60028-106">Note that annotations are not part of the XML infoset; they are not serialized or deserialized.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="60028-107">Metody</span><span class="sxs-lookup"><span data-stu-id="60028-107">Methods</span></span>  
 <span data-ttu-id="60028-108">Podczas pracy z adnotacjami, można użyć następujących metod:</span><span class="sxs-lookup"><span data-stu-id="60028-108">You can use the following methods when working with annotations:</span></span>  
  
|<span data-ttu-id="60028-109">Metoda</span><span class="sxs-lookup"><span data-stu-id="60028-109">Method</span></span>|<span data-ttu-id="60028-110">Opis</span><span class="sxs-lookup"><span data-stu-id="60028-110">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XObject.AddAnnotation%2A>|<span data-ttu-id="60028-111">Dodaje obiekt do listy adnotacji <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="60028-111">Adds an object to the annotation list of an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObject.Annotation%2A>|<span data-ttu-id="60028-112">Pobiera pierwszy obiekt adnotacji określonego typu z <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="60028-112">Gets the first annotation object of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObject.Annotations%2A>|<span data-ttu-id="60028-113">Pobiera kolekcję adnotacje dla określonego typu <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="60028-113">Gets a collection of annotations of the specified type for an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObject.RemoveAnnotations%2A>|<span data-ttu-id="60028-114">Usuwa adnotacje określonego typu z <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="60028-114">Removes the annotations of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="60028-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="60028-115">See Also</span></span>  
 [<span data-ttu-id="60028-116">Zaawansowane LINQ do XML programowania (C#)</span><span class="sxs-lookup"><span data-stu-id="60028-116">Advanced LINQ to XML Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
