---
title: LINQ to XML Annotations3
ms.date: 07/20/2015
ms.assetid: 54e7b9d0-07f5-488f-9065-b6e6b870f810
ms.openlocfilehash: 13dd72a9016dea8c5b4389580f912625028e51ae
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43530367"
---
# <a name="linq-to-xml-annotations"></a><span data-ttu-id="3965f-102">Adnotacje LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="3965f-102">LINQ to XML Annotations</span></span>
<span data-ttu-id="3965f-103">Adnotacje w [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] umożliwiają skojarzenie z dowolnych obiektów dowolnego typu za pomocą dowolnego składnika XML w drzewie XML.</span><span class="sxs-lookup"><span data-stu-id="3965f-103">Annotations in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] enable you to associate any arbitrary object of any arbitrary type with any XML component in an XML tree.</span></span>  
  
 <span data-ttu-id="3965f-104">Dodawanie adnotacji do elementu XML, takie jak <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XAttribute>, należy wywołać <xref:System.Xml.Linq.XObject.AddAnnotation%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="3965f-104">To add an annotation to an XML component, such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute>, you call the <xref:System.Xml.Linq.XObject.AddAnnotation%2A> method.</span></span> <span data-ttu-id="3965f-105">Możesz pobrać adnotacje według typu.</span><span class="sxs-lookup"><span data-stu-id="3965f-105">You retrieve annotations by type.</span></span>  
  
 <span data-ttu-id="3965f-106">Należy pamiętać, że adnotacji nie są częścią zestaw informacji XML; nie jest serializowany lub deserializowany.</span><span class="sxs-lookup"><span data-stu-id="3965f-106">Note that annotations are not part of the XML infoset; they are not serialized or deserialized.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3965f-107">Metody</span><span class="sxs-lookup"><span data-stu-id="3965f-107">Methods</span></span>  
 <span data-ttu-id="3965f-108">Podczas pracy z adnotacjami, można użyć następujących metod:</span><span class="sxs-lookup"><span data-stu-id="3965f-108">You can use the following methods when working with annotations:</span></span>  
  
|<span data-ttu-id="3965f-109">Metoda</span><span class="sxs-lookup"><span data-stu-id="3965f-109">Method</span></span>|<span data-ttu-id="3965f-110">Opis</span><span class="sxs-lookup"><span data-stu-id="3965f-110">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XObject.AddAnnotation%2A>|<span data-ttu-id="3965f-111">Dodaje obiekt do listy adnotacji <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="3965f-111">Adds an object to the annotation list of an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObject.Annotation%2A>|<span data-ttu-id="3965f-112">Pobiera pierwszy obiekt adnotacji określonego typu z <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="3965f-112">Gets the first annotation object of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObject.Annotations%2A>|<span data-ttu-id="3965f-113">Pobiera kolekcję adnotacje określonego typu <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="3965f-113">Gets a collection of annotations of the specified type for an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObject.RemoveAnnotations%2A>|<span data-ttu-id="3965f-114">Usuwa adnotacje określonego typu z <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="3965f-114">Removes the annotations of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3965f-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3965f-115">See Also</span></span>

- [<span data-ttu-id="3965f-116">Zaawansowane LINQ to XML programowania (C#)</span><span class="sxs-lookup"><span data-stu-id="3965f-116">Advanced LINQ to XML Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
