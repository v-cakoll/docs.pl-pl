---
title: Hierarchia modelu (DOM) obiektu dokumentu XML
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9d187d4f-c76e-4223-a670-cc290783ce47
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 4d2ffaa994ce3c9b02ed0937967845be1b803f6d
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="xml-document-object-model-dom-hierarchy"></a><span data-ttu-id="3dcb5-102">Hierarchia modelu (DOM) obiektu dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="3dcb5-102">XML Document Object Model (DOM) Hierarchy</span></span>
<span data-ttu-id="3dcb5-103">Na poniższej ilustracji przedstawiono hierarchii klas dla XML modelu DOM (Document Object), z sieci World Wide Web konsorcjum W3C nazwę w nawiasy okrągłe oraz nazwę klasy, gdzie jest to potrzebne.</span><span class="sxs-lookup"><span data-stu-id="3dcb5-103">The following illustration shows the class hierarchy for the XML Document Object Model (DOM), with the World Wide Web Consortium (W3C) name in parenthesis along with the class name where it is relevant.</span></span>  
  
 <span data-ttu-id="3dcb5-104">![Modelu obiektu dokumentu XML &#40; DOM &#41; Hierarchia](../../../../docs/standard/data/xml/media/dom-class-hierarchy.gif "Dom_class_hierarchy")</span><span class="sxs-lookup"><span data-stu-id="3dcb5-104">![XML Document Object Model &#40;DOM&#41; hierarchy](../../../../docs/standard/data/xml/media/dom-class-hierarchy.gif "Dom_class_hierarchy")</span></span>  
<span data-ttu-id="3dcb5-105">Hierarchia XML modelu DOM (Document Object)</span><span class="sxs-lookup"><span data-stu-id="3dcb5-105">XML Document Object Model (DOM) hierarchy</span></span>  
  
 <span data-ttu-id="3dcb5-106">Następujące klasy nie dziedziczą **XmlNode**:</span><span class="sxs-lookup"><span data-stu-id="3dcb5-106">The following classes do not inherit from the **XmlNode**:</span></span>  
  
-   <span data-ttu-id="3dcb5-107">**XmlImplementation**</span><span class="sxs-lookup"><span data-stu-id="3dcb5-107">**XmlImplementation**</span></span>  
  
-   <span data-ttu-id="3dcb5-108">**XmlNamedNodeMap**</span><span class="sxs-lookup"><span data-stu-id="3dcb5-108">**XmlNamedNodeMap**</span></span>  
  
-   <span data-ttu-id="3dcb5-109">**XmlNodeList**</span><span class="sxs-lookup"><span data-stu-id="3dcb5-109">**XmlNodeList**</span></span>  
  
-   <span data-ttu-id="3dcb5-110">**XmlNodeChangedEventArgs**</span><span class="sxs-lookup"><span data-stu-id="3dcb5-110">**XmlNodeChangedEventArgs**</span></span>  
  
 <span data-ttu-id="3dcb5-111">**XmlImplementation** klasa jest używana do tworzenia dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="3dcb5-111">The **XmlImplementation** class is used to create an XML document.</span></span> <span data-ttu-id="3dcb5-112">Aby uzyskać więcej informacji, zobacz [utworzenie dokumentu XML](../../../../docs/standard/data/xml/xml-document-creation.md).</span><span class="sxs-lookup"><span data-stu-id="3dcb5-112">For more information, see [XML Document Creation](../../../../docs/standard/data/xml/xml-document-creation.md).</span></span>  
  
 <span data-ttu-id="3dcb5-113">**XmlNamedNodeMap** klasa obsługuje nieuporządkowaną zestaw węzłów.</span><span class="sxs-lookup"><span data-stu-id="3dcb5-113">The **XmlNamedNodeMap** class handles an unordered set of nodes.</span></span> <span data-ttu-id="3dcb5-114">Aby uzyskać więcej informacji, zobacz [nieuporządkowaną pobierania węzła przez nazwę lub indeks](../../../../docs/standard/data/xml/unordered-node-retrieval-by-name-or-index.md).</span><span class="sxs-lookup"><span data-stu-id="3dcb5-114">For more information, see [Unordered Node Retrieval by Name or Index](../../../../docs/standard/data/xml/unordered-node-retrieval-by-name-or-index.md).</span></span>  
  
 <span data-ttu-id="3dcb5-115">**XmlNodeList** klasa obsługuje uporządkowaną listę węzłów.</span><span class="sxs-lookup"><span data-stu-id="3dcb5-115">The **XmlNodeList** class handles an ordered list of nodes.</span></span> <span data-ttu-id="3dcb5-116">Aby uzyskać więcej informacji, zobacz [uporządkowane pobierania węzła przez indeks](../../../../docs/standard/data/xml/ordered-node-retrieval-by-index.md).</span><span class="sxs-lookup"><span data-stu-id="3dcb5-116">For more information, see [Ordered Node Retrieval by Index](../../../../docs/standard/data/xml/ordered-node-retrieval-by-index.md).</span></span>  
  
 <span data-ttu-id="3dcb5-117">**XmlNodeChangedEventArgs** klasa obsługuje procedury obsługi zdarzeń zarejestrowane na **XmlDocument**.</span><span class="sxs-lookup"><span data-stu-id="3dcb5-117">The **XmlNodeChangedEventArgs** class handles event handlers registered on the **XmlDocument**.</span></span> <span data-ttu-id="3dcb5-118">Aby uzyskać więcej informacji, zobacz [obsługi zdarzeń w dokumencie XML przy użyciu XmlNodeChangedEventArgs](../../../../docs/standard/data/xml/event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md).</span><span class="sxs-lookup"><span data-stu-id="3dcb5-118">For more information, see [Event Handling in an XML Document using the XmlNodeChangedEventArgs](../../../../docs/standard/data/xml/event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md).</span></span>  
  
 <span data-ttu-id="3dcb5-119">**XmlLinkedNode** klasa dziedziczy **XmlNode**.</span><span class="sxs-lookup"><span data-stu-id="3dcb5-119">The **XmlLinkedNode** class inherits from **XmlNode**.</span></span> <span data-ttu-id="3dcb5-120">Jego celem jest zastąpienie dwie metody z **XmlNode**: **parametr PreviousSibling** i **NextSibling** metody.</span><span class="sxs-lookup"><span data-stu-id="3dcb5-120">Its purpose is to override two methods from **XmlNode**: the **PreviousSibling** and **NextSibling** methods.</span></span> <span data-ttu-id="3dcb5-121">Te przesłoniętej metody są dziedziczone i używane przez **XmlCharacterData**, **XmlDeclaration**, **XmlDocumentType**, **XmlElement**, **XmlEntityReference**, i **XmlProcessingInstruction**, które są klasy, które mają poprzedniego i następnego elementów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="3dcb5-121">These overridden methods are then inherited and used by **XmlCharacterData**, **XmlDeclaration**, **XmlDocumentType**, **XmlElement**, **XmlEntityReference**, and **XmlProcessingInstruction**, which are classes that have previous and next siblings.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3dcb5-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3dcb5-122">See Also</span></span>  
 [<span data-ttu-id="3dcb5-123">Model DOM (XML Document Object Model)</span><span class="sxs-lookup"><span data-stu-id="3dcb5-123">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
