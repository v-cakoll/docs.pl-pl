---
title: LINQ to XML Annotations3
ms.date: 07/20/2015
ms.assetid: 54e7b9d0-07f5-488f-9065-b6e6b870f810
ms.openlocfilehash: 19661f303ccea411ff6088005cb0198b50781d37
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66487390"
---
# <a name="linq-to-xml-annotations"></a><span data-ttu-id="46c5f-102">Adnotacje LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="46c5f-102">LINQ to XML Annotations</span></span>
<span data-ttu-id="46c5f-103">Adnotacje w [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] umożliwiają skojarzenie z dowolnych obiektów dowolnego typu za pomocą dowolnego składnika XML w drzewie XML.</span><span class="sxs-lookup"><span data-stu-id="46c5f-103">Annotations in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] enable you to associate any arbitrary object of any arbitrary type with any XML component in an XML tree.</span></span>  
  
 <span data-ttu-id="46c5f-104">Dodawanie adnotacji do elementu XML, takie jak <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XAttribute>, należy wywołać <xref:System.Xml.Linq.XObject.AddAnnotation%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="46c5f-104">To add an annotation to an XML component, such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute>, you call the <xref:System.Xml.Linq.XObject.AddAnnotation%2A> method.</span></span> <span data-ttu-id="46c5f-105">Możesz pobrać adnotacje według typu.</span><span class="sxs-lookup"><span data-stu-id="46c5f-105">You retrieve annotations by type.</span></span>  
  
 <span data-ttu-id="46c5f-106">Należy pamiętać, że adnotacji nie są częścią zestaw informacji XML; nie jest serializowany lub deserializowany.</span><span class="sxs-lookup"><span data-stu-id="46c5f-106">Note that annotations are not part of the XML infoset; they are not serialized or deserialized.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="46c5f-107">Metody</span><span class="sxs-lookup"><span data-stu-id="46c5f-107">Methods</span></span>  
 <span data-ttu-id="46c5f-108">Podczas pracy z adnotacjami, można użyć następujących metod:</span><span class="sxs-lookup"><span data-stu-id="46c5f-108">You can use the following methods when working with annotations:</span></span>  
  
|<span data-ttu-id="46c5f-109">Metoda</span><span class="sxs-lookup"><span data-stu-id="46c5f-109">Method</span></span>|<span data-ttu-id="46c5f-110">Opis</span><span class="sxs-lookup"><span data-stu-id="46c5f-110">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XObject.AddAnnotation%2A>|<span data-ttu-id="46c5f-111">Dodaje obiekt do listy adnotacji <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="46c5f-111">Adds an object to the annotation list of an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObject.Annotation%2A>|<span data-ttu-id="46c5f-112">Pobiera pierwszy obiekt adnotacji określonego typu z <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="46c5f-112">Gets the first annotation object of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObject.Annotations%2A>|<span data-ttu-id="46c5f-113">Pobiera kolekcję adnotacje określonego typu <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="46c5f-113">Gets a collection of annotations of the specified type for an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObject.RemoveAnnotations%2A>|<span data-ttu-id="46c5f-114">Usuwa adnotacje określonego typu z <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="46c5f-114">Removes the annotations of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|  
  
