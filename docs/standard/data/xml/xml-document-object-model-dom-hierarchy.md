---
title: Hierarchia Model (DOM) obiektu dokumentu XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 9d187d4f-c76e-4223-a670-cc290783ce47
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ef2b5b200f95cdfac9b08a33c328c1dfb797e59e
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45749704"
---
# <a name="xml-document-object-model-dom-hierarchy"></a><span data-ttu-id="72f1d-102">Hierarchia Model (DOM) obiektu dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="72f1d-102">XML Document Object Model (DOM) Hierarchy</span></span>
<span data-ttu-id="72f1d-103">Na poniższej ilustracji przedstawiono hierarchii klas dla XML Document Object Model (DOM), za pomocą sieci World Wide Web Consortium (W3C) nadaj nazwę w nawiasach wraz z nazwą klasy, gdzie jest to stosowne.</span><span class="sxs-lookup"><span data-stu-id="72f1d-103">The following illustration shows the class hierarchy for the XML Document Object Model (DOM), with the World Wide Web Consortium (W3C) name in parenthesis along with the class name where it is relevant.</span></span>  
  
 <span data-ttu-id="72f1d-104">![Model obiektu dokumentu XML &#40;DOM&#41; hierarchii](../../../../docs/standard/data/xml/media/dom-class-hierarchy.gif "Dom_class_hierarchy")</span><span class="sxs-lookup"><span data-stu-id="72f1d-104">![XML Document Object Model &#40;DOM&#41; hierarchy](../../../../docs/standard/data/xml/media/dom-class-hierarchy.gif "Dom_class_hierarchy")</span></span>  
<span data-ttu-id="72f1d-105">Hierarchia XML modelu DOM (Document Object)</span><span class="sxs-lookup"><span data-stu-id="72f1d-105">XML Document Object Model (DOM) hierarchy</span></span>  
  
 <span data-ttu-id="72f1d-106">Następujące klasy nie dziedziczą **XmlNode**:</span><span class="sxs-lookup"><span data-stu-id="72f1d-106">The following classes do not inherit from the **XmlNode**:</span></span>  
  
-   <span data-ttu-id="72f1d-107">**XmlImplementation**</span><span class="sxs-lookup"><span data-stu-id="72f1d-107">**XmlImplementation**</span></span>  
  
-   <span data-ttu-id="72f1d-108">**XmlNamedNodeMap**</span><span class="sxs-lookup"><span data-stu-id="72f1d-108">**XmlNamedNodeMap**</span></span>  
  
-   <span data-ttu-id="72f1d-109">**XmlNodeList**</span><span class="sxs-lookup"><span data-stu-id="72f1d-109">**XmlNodeList**</span></span>  
  
-   <span data-ttu-id="72f1d-110">**Klasy XmlNodeChangedEventArgs**</span><span class="sxs-lookup"><span data-stu-id="72f1d-110">**XmlNodeChangedEventArgs**</span></span>  
  
 <span data-ttu-id="72f1d-111">**XmlImplementation** klasa jest używana w celu utworzenia dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="72f1d-111">The **XmlImplementation** class is used to create an XML document.</span></span> <span data-ttu-id="72f1d-112">Aby uzyskać więcej informacji, zobacz [Tworzenie dokumentu XML](../../../../docs/standard/data/xml/xml-document-creation.md).</span><span class="sxs-lookup"><span data-stu-id="72f1d-112">For more information, see [XML Document Creation](../../../../docs/standard/data/xml/xml-document-creation.md).</span></span>  
  
 <span data-ttu-id="72f1d-113">**XmlNamedNodeMap** klasa obsługuje nieuporządkowaną zestaw węzłów.</span><span class="sxs-lookup"><span data-stu-id="72f1d-113">The **XmlNamedNodeMap** class handles an unordered set of nodes.</span></span> <span data-ttu-id="72f1d-114">Aby uzyskać więcej informacji, zobacz [nieuporządkowaną pobierania węzła przez nazwę lub indeks](../../../../docs/standard/data/xml/unordered-node-retrieval-by-name-or-index.md).</span><span class="sxs-lookup"><span data-stu-id="72f1d-114">For more information, see [Unordered Node Retrieval by Name or Index](../../../../docs/standard/data/xml/unordered-node-retrieval-by-name-or-index.md).</span></span>  
  
 <span data-ttu-id="72f1d-115">**XmlNodeList** klasa obsługuje uporządkowane listy węzłów.</span><span class="sxs-lookup"><span data-stu-id="72f1d-115">The **XmlNodeList** class handles an ordered list of nodes.</span></span> <span data-ttu-id="72f1d-116">Aby uzyskać więcej informacji, zobacz [uporządkowane pobierania węzła za pomocą indeksu](../../../../docs/standard/data/xml/ordered-node-retrieval-by-index.md).</span><span class="sxs-lookup"><span data-stu-id="72f1d-116">For more information, see [Ordered Node Retrieval by Index](../../../../docs/standard/data/xml/ordered-node-retrieval-by-index.md).</span></span>  
  
 <span data-ttu-id="72f1d-117">**Klasy XmlNodeChangedEventArgs** klasa obsługuje programy obsługi zdarzeń zarejestrowane na **XmlDocument**.</span><span class="sxs-lookup"><span data-stu-id="72f1d-117">The **XmlNodeChangedEventArgs** class handles event handlers registered on the **XmlDocument**.</span></span> <span data-ttu-id="72f1d-118">Aby uzyskać więcej informacji, zobacz [zdarzenie obsługi w dokumencie XML przy użyciu klasy XmlNodeChangedEventArgs](../../../../docs/standard/data/xml/event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md).</span><span class="sxs-lookup"><span data-stu-id="72f1d-118">For more information, see [Event Handling in an XML Document using the XmlNodeChangedEventArgs](../../../../docs/standard/data/xml/event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md).</span></span>  
  
 <span data-ttu-id="72f1d-119">**XmlLinkedNode** klasa dziedziczy **XmlNode**.</span><span class="sxs-lookup"><span data-stu-id="72f1d-119">The **XmlLinkedNode** class inherits from **XmlNode**.</span></span> <span data-ttu-id="72f1d-120">Jego celem jest zastąpienie dwie metody z **XmlNode**: **PreviousSibling** i **NextSibling** metody.</span><span class="sxs-lookup"><span data-stu-id="72f1d-120">Its purpose is to override two methods from **XmlNode**: the **PreviousSibling** and **NextSibling** methods.</span></span> <span data-ttu-id="72f1d-121">Te przesłonięte metody są dziedziczone i używane przez **XmlCharacterData**, **XmlDeclaration**, **XmlDocumentType**, **XmlElement**, **XmlEntityReference**, i **XmlProcessingInstruction**, służą do klas, które mają elementy równorzędne poprzedni i dalej.</span><span class="sxs-lookup"><span data-stu-id="72f1d-121">These overridden methods are then inherited and used by **XmlCharacterData**, **XmlDeclaration**, **XmlDocumentType**, **XmlElement**, **XmlEntityReference**, and **XmlProcessingInstruction**, which are classes that have previous and next siblings.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72f1d-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="72f1d-122">See also</span></span>

- [<span data-ttu-id="72f1d-123">Model DOM (XML Document Object Model)</span><span class="sxs-lookup"><span data-stu-id="72f1d-123">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
