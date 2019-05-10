---
title: Hierarchia modelu DOM (XML Document Object Model)
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 9d187d4f-c76e-4223-a670-cc290783ce47
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 79078b16f0d56c40a3dcfeabaaed9b5cbb7753a0
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64589846"
---
# <a name="xml-document-object-model-dom-hierarchy"></a><span data-ttu-id="daf18-102">Hierarchia modelu DOM (XML Document Object Model)</span><span class="sxs-lookup"><span data-stu-id="daf18-102">XML Document Object Model (DOM) Hierarchy</span></span>
<span data-ttu-id="daf18-103">Na poniższej ilustracji przedstawiono hierarchii klas dla XML Document Object Model (DOM), za pomocą sieci World Wide Web Consortium (W3C) nadaj nazwę w nawiasach wraz z nazwą klasy, gdzie jest to stosowne.</span><span class="sxs-lookup"><span data-stu-id="daf18-103">The following illustration shows the class hierarchy for the XML Document Object Model (DOM), with the World Wide Web Consortium (W3C) name in parenthesis along with the class name where it is relevant.</span></span>  
  
 <span data-ttu-id="daf18-104">![XML Document Object Model &#40;DOM&#41; hierarchy](../../../../docs/standard/data/xml/media/dom-class-hierarchy.gif "Dom_class_hierarchy")</span><span class="sxs-lookup"><span data-stu-id="daf18-104">![XML Document Object Model &#40;DOM&#41; hierarchy](../../../../docs/standard/data/xml/media/dom-class-hierarchy.gif "Dom_class_hierarchy")</span></span>  
<span data-ttu-id="daf18-105">Hierarchia XML modelu DOM (Document Object)</span><span class="sxs-lookup"><span data-stu-id="daf18-105">XML Document Object Model (DOM) hierarchy</span></span>  
  
 <span data-ttu-id="daf18-106">Następujące klasy nie dziedziczą **XmlNode**:</span><span class="sxs-lookup"><span data-stu-id="daf18-106">The following classes do not inherit from the **XmlNode**:</span></span>  
  
- <span data-ttu-id="daf18-107">**XmlImplementation**</span><span class="sxs-lookup"><span data-stu-id="daf18-107">**XmlImplementation**</span></span>  
  
- <span data-ttu-id="daf18-108">**XmlNamedNodeMap**</span><span class="sxs-lookup"><span data-stu-id="daf18-108">**XmlNamedNodeMap**</span></span>  
  
- <span data-ttu-id="daf18-109">**XmlNodeList**</span><span class="sxs-lookup"><span data-stu-id="daf18-109">**XmlNodeList**</span></span>  
  
- <span data-ttu-id="daf18-110">**XmlNodeChangedEventArgs**</span><span class="sxs-lookup"><span data-stu-id="daf18-110">**XmlNodeChangedEventArgs**</span></span>  
  
 <span data-ttu-id="daf18-111">**XmlImplementation** klasa jest używana w celu utworzenia dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="daf18-111">The **XmlImplementation** class is used to create an XML document.</span></span> <span data-ttu-id="daf18-112">Aby uzyskać więcej informacji, zobacz [Tworzenie dokumentu XML](../../../../docs/standard/data/xml/xml-document-creation.md).</span><span class="sxs-lookup"><span data-stu-id="daf18-112">For more information, see [XML Document Creation](../../../../docs/standard/data/xml/xml-document-creation.md).</span></span>  
  
 <span data-ttu-id="daf18-113">**XmlNamedNodeMap** klasa obsługuje nieuporządkowaną zestaw węzłów.</span><span class="sxs-lookup"><span data-stu-id="daf18-113">The **XmlNamedNodeMap** class handles an unordered set of nodes.</span></span> <span data-ttu-id="daf18-114">Aby uzyskać więcej informacji, zobacz [nieuporządkowaną pobierania węzła przez nazwę lub indeks](../../../../docs/standard/data/xml/unordered-node-retrieval-by-name-or-index.md).</span><span class="sxs-lookup"><span data-stu-id="daf18-114">For more information, see [Unordered Node Retrieval by Name or Index](../../../../docs/standard/data/xml/unordered-node-retrieval-by-name-or-index.md).</span></span>  
  
 <span data-ttu-id="daf18-115">**XmlNodeList** klasa obsługuje uporządkowane listy węzłów.</span><span class="sxs-lookup"><span data-stu-id="daf18-115">The **XmlNodeList** class handles an ordered list of nodes.</span></span> <span data-ttu-id="daf18-116">Aby uzyskać więcej informacji, zobacz [uporządkowane pobierania węzła za pomocą indeksu](../../../../docs/standard/data/xml/ordered-node-retrieval-by-index.md).</span><span class="sxs-lookup"><span data-stu-id="daf18-116">For more information, see [Ordered Node Retrieval by Index](../../../../docs/standard/data/xml/ordered-node-retrieval-by-index.md).</span></span>  
  
 <span data-ttu-id="daf18-117">**Klasy XmlNodeChangedEventArgs** klasa obsługuje programy obsługi zdarzeń zarejestrowane na **XmlDocument**.</span><span class="sxs-lookup"><span data-stu-id="daf18-117">The **XmlNodeChangedEventArgs** class handles event handlers registered on the **XmlDocument**.</span></span> <span data-ttu-id="daf18-118">Aby uzyskać więcej informacji, zobacz [zdarzenie obsługi w dokumencie XML przy użyciu klasy XmlNodeChangedEventArgs](../../../../docs/standard/data/xml/event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md).</span><span class="sxs-lookup"><span data-stu-id="daf18-118">For more information, see [Event Handling in an XML Document using the XmlNodeChangedEventArgs](../../../../docs/standard/data/xml/event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md).</span></span>  
  
 <span data-ttu-id="daf18-119">**XmlLinkedNode** klasa dziedziczy **XmlNode**.</span><span class="sxs-lookup"><span data-stu-id="daf18-119">The **XmlLinkedNode** class inherits from **XmlNode**.</span></span> <span data-ttu-id="daf18-120">Jego celem jest zastąpienie dwie metody z **XmlNode**: **PreviousSibling** i **NextSibling** metody.</span><span class="sxs-lookup"><span data-stu-id="daf18-120">Its purpose is to override two methods from **XmlNode**: the **PreviousSibling** and **NextSibling** methods.</span></span> <span data-ttu-id="daf18-121">Te przesłonięte metody są dziedziczone i używane przez **XmlCharacterData**, **XmlDeclaration**, **XmlDocumentType**, **XmlElement**, **XmlEntityReference**, i **XmlProcessingInstruction**, służą do klas, które mają elementy równorzędne poprzedni i dalej.</span><span class="sxs-lookup"><span data-stu-id="daf18-121">These overridden methods are then inherited and used by **XmlCharacterData**, **XmlDeclaration**, **XmlDocumentType**, **XmlElement**, **XmlEntityReference**, and **XmlProcessingInstruction**, which are classes that have previous and next siblings.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="daf18-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="daf18-122">See also</span></span>

- [<span data-ttu-id="daf18-123">Model DOM (XML Document Object Model)</span><span class="sxs-lookup"><span data-stu-id="daf18-123">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
