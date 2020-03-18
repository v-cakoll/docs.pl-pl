---
title: LINQ do Adnotacji XML3
ms.date: 07/20/2015
ms.assetid: 54e7b9d0-07f5-488f-9065-b6e6b870f810
ms.openlocfilehash: 5f1940be2fc126ff9e9c7a4cb37e5cc7fc95d3c3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "66689945"
---
# <a name="linq-to-xml-annotations"></a><span data-ttu-id="611d5-102">Adnotacje LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="611d5-102">LINQ to XML Annotations</span></span>

<span data-ttu-id="611d5-103">Adnotacje [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] umożliwiające skojarzenie dowolnego obiektu dowolnego dowolnego typu z dowolnym składnikiem XML w drzewie XML.</span><span class="sxs-lookup"><span data-stu-id="611d5-103">Annotations in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] enable you to associate any arbitrary object of any arbitrary type with any XML component in an XML tree.</span></span>

<span data-ttu-id="611d5-104">Aby dodać adnotację do składnika XML, takiego jak <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XAttribute>, należy wywołać <xref:System.Xml.Linq.XObject.AddAnnotation%2A> metodę.</span><span class="sxs-lookup"><span data-stu-id="611d5-104">To add an annotation to an XML component, such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute>, you call the <xref:System.Xml.Linq.XObject.AddAnnotation%2A> method.</span></span> <span data-ttu-id="611d5-105">Adnotacje można pobrać według typu.</span><span class="sxs-lookup"><span data-stu-id="611d5-105">You retrieve annotations by type.</span></span>

<span data-ttu-id="611d5-106">Należy zauważyć, że adnotacje nie są częścią zestawu informacji XML; nie są serializowane ani deserializowane.</span><span class="sxs-lookup"><span data-stu-id="611d5-106">Note that annotations are not part of the XML infoset; they are not serialized or deserialized.</span></span>

## <a name="methods"></a><span data-ttu-id="611d5-107">Metody</span><span class="sxs-lookup"><span data-stu-id="611d5-107">Methods</span></span>

<span data-ttu-id="611d5-108">Podczas pracy z adnotacjami można użyć następujących metod:</span><span class="sxs-lookup"><span data-stu-id="611d5-108">You can use the following methods when working with annotations:</span></span>

|<span data-ttu-id="611d5-109">Metoda</span><span class="sxs-lookup"><span data-stu-id="611d5-109">Method</span></span>|<span data-ttu-id="611d5-110">Opis</span><span class="sxs-lookup"><span data-stu-id="611d5-110">Description</span></span>|
|------------|-----------------|
|<xref:System.Xml.Linq.XObject.AddAnnotation%2A>|<span data-ttu-id="611d5-111">Dodaje obiekt do listy adnotacji pliku <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="611d5-111">Adds an object to the annotation list of an <xref:System.Xml.Linq.XObject>.</span></span>|
|<xref:System.Xml.Linq.XObject.Annotation%2A>|<span data-ttu-id="611d5-112">Pobiera pierwszy obiekt adnotacji określonego typu <xref:System.Xml.Linq.XObject>z pliku .</span><span class="sxs-lookup"><span data-stu-id="611d5-112">Gets the first annotation object of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|
|<xref:System.Xml.Linq.XObject.Annotations%2A>|<span data-ttu-id="611d5-113">Pobiera kolekcję adnotacji określonego typu dla <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="611d5-113">Gets a collection of annotations of the specified type for an <xref:System.Xml.Linq.XObject>.</span></span>|
|<xref:System.Xml.Linq.XObject.RemoveAnnotations%2A>|<span data-ttu-id="611d5-114">Usuwa adnotacje określonego typu z <xref:System.Xml.Linq.XObject>pliku .</span><span class="sxs-lookup"><span data-stu-id="611d5-114">Removes the annotations of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|
