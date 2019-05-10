---
title: Przetwarzanie danych XML przy użyciu modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 56b6e9c7-ed82-4a65-a647-7be32c83bcc8
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d34d22d8329f0bc26c1e29653137211bf300d324
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647822"
---
# <a name="process-xml-data-using-the-dom-model"></a><span data-ttu-id="3d577-102">Przetwarzanie danych XML przy użyciu modelu DOM</span><span class="sxs-lookup"><span data-stu-id="3d577-102">Process XML Data Using the DOM Model</span></span>
<span data-ttu-id="3d577-103">XML Document Object Model (DOM), dane XML są traktowane jako standardowy zestaw obiektów i służy do przetwarzania danych XML w pamięci.</span><span class="sxs-lookup"><span data-stu-id="3d577-103">The XML Document Object Model (DOM) treats XML data as a standard set of objects and is used to process XML data in memory.</span></span> <span data-ttu-id="3d577-104">`System.Xml` Przestrzeń nazw zawiera reprezentację programistyczne dokumenty XML, fragmenty, węzłów lub zestaw węzłów.</span><span class="sxs-lookup"><span data-stu-id="3d577-104">The `System.Xml` namespace provides a programmatic representation of XML documents, fragments, nodes, or node-sets.</span></span> <span data-ttu-id="3d577-105">Jest on oparty na Core poziomu 1 DOM World Wide Web Consortium (W3C) i zalecenia dotyczące modelu DOM poziom 2 rdzeni.</span><span class="sxs-lookup"><span data-stu-id="3d577-105">It is based on the World Wide Web Consortium (W3C) DOM Level 1 Core and the DOM Level 2 Core recommendations.</span></span>  
  
 <span data-ttu-id="3d577-106"><xref:System.Xml.XmlDocument> Klasa reprezentuje dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="3d577-106">The <xref:System.Xml.XmlDocument> class represents an XML document.</span></span> <span data-ttu-id="3d577-107">Zawiera elementy członkowskie do pobierania i tworzenia wszystkich obiektów XML.</span><span class="sxs-lookup"><span data-stu-id="3d577-107">It includes members for retrieving and creating all other XML objects.</span></span> <span data-ttu-id="3d577-108">Za pomocą <xref:System.Xml.XmlDocument>oraz ich powiązanymi klasami można konstruowania, dokumentów XML, obciążenia i uzyskiwać dostęp do danych i modyfikować dane i zapisać zmiany.</span><span class="sxs-lookup"><span data-stu-id="3d577-108">Using the <xref:System.Xml.XmlDocument>, and its related classes, you can construct XML documents, load and access data, modify data, and save changes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3d577-109">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="3d577-109">In This Section</span></span>  
  
- [<span data-ttu-id="3d577-110">Model DOM (XML Document Object Model)</span><span class="sxs-lookup"><span data-stu-id="3d577-110">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)  
  
- [<span data-ttu-id="3d577-111">Typy węzłów XML</span><span class="sxs-lookup"><span data-stu-id="3d577-111">Types of XML Nodes</span></span>](../../../../docs/standard/data/xml/types-of-xml-nodes.md)  
  
- [<span data-ttu-id="3d577-112">Hierarchia modelu DOM (XML Document Object Model)</span><span class="sxs-lookup"><span data-stu-id="3d577-112">XML Document Object Model (DOM) Hierarchy</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom-hierarchy.md)  
  
- [<span data-ttu-id="3d577-113">Mapowanie hierarchii obiektów na dane XML</span><span class="sxs-lookup"><span data-stu-id="3d577-113">Mapping the Object Hierarchy to XML Data</span></span>](../../../../docs/standard/data/xml/mapping-the-object-hierarchy-to-xml-data.md)  
  
- [<span data-ttu-id="3d577-114">Tworzenie dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="3d577-114">XML Document Creation</span></span>](../../../../docs/standard/data/xml/xml-document-creation.md)  
  
- [<span data-ttu-id="3d577-115">Wczytywanie dokumentu XML do modelu DOM</span><span class="sxs-lookup"><span data-stu-id="3d577-115">Reading an XML Document into the DOM</span></span>](../../../../docs/standard/data/xml/reading-an-xml-document-into-the-dom.md)  
  
- [<span data-ttu-id="3d577-116">Wstawianie węzłów do dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="3d577-116">Inserting Nodes into an XML Document</span></span>](../../../../docs/standard/data/xml/inserting-nodes-into-an-xml-document.md)  
  
- [<span data-ttu-id="3d577-117">Usuwanie węzłów, zawartości i wartości z dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="3d577-117">Removing Nodes, Content, and Values from an XML Document</span></span>](../../../../docs/standard/data/xml/removing-nodes-content-and-values-from-an-xml-document.md)  
  
- [<span data-ttu-id="3d577-118">Modyfikowanie węzłów, zawartości i wartości w dokumencie XML</span><span class="sxs-lookup"><span data-stu-id="3d577-118">Modifying Nodes, Content, and Values in an XML Document</span></span>](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md)  
  
- [<span data-ttu-id="3d577-119">Weryfikowanie dokumentu XML w modelu DOM</span><span class="sxs-lookup"><span data-stu-id="3d577-119">Validating an XML Document in the DOM</span></span>](../../../../docs/standard/data/xml/validating-an-xml-document-in-the-dom.md)  
  
- [<span data-ttu-id="3d577-120">Zapisywanie dokumentu</span><span class="sxs-lookup"><span data-stu-id="3d577-120">Saving and Writing a Document</span></span>](../../../../docs/standard/data/xml/saving-and-writing-a-document.md)  
  
- [<span data-ttu-id="3d577-121">Wybieranie węzłów za pomocą nawigacji XPath</span><span class="sxs-lookup"><span data-stu-id="3d577-121">Select Nodes Using XPath Navigation</span></span>](../../../../docs/standard/data/xml/select-nodes-using-xpath-navigation.md)  
  
- [<span data-ttu-id="3d577-122">Rozpoznawanie zasobów zewnętrznych</span><span class="sxs-lookup"><span data-stu-id="3d577-122">Resolving External Resources</span></span>](../../../../docs/standard/data/xml/resolving-external-resources.md)  
  
- [<span data-ttu-id="3d577-123">Porównywanie obiektów przy użyciu tabeli XmlNameTable</span><span class="sxs-lookup"><span data-stu-id="3d577-123">Object Comparison Using XmlNameTable</span></span>](../../../../docs/standard/data/xml/object-comparison-using-xmlnametable.md)  
  
- [<span data-ttu-id="3d577-124">Kolekcje węzłów: NamedNodeMaps i NodeLists</span><span class="sxs-lookup"><span data-stu-id="3d577-124">Node Collections in NamedNodeMaps and NodeLists</span></span>](../../../../docs/standard/data/xml/node-collections-in-namednodemaps-and-nodelists.md)  
  
- [<span data-ttu-id="3d577-125">Aktualizacja dynamiczna obiektów NodeLists i NamedNodeMaps</span><span class="sxs-lookup"><span data-stu-id="3d577-125">Dynamic Updates to NodeLists and NamedNodeMaps</span></span>](../../../../docs/standard/data/xml/dynamic-updates-to-nodelists-and-namednodemaps.md)  
  
- [<span data-ttu-id="3d577-126">Obsługa przestrzeni nazw w modelu DOM</span><span class="sxs-lookup"><span data-stu-id="3d577-126">Namespace Support in the DOM</span></span>](../../../../docs/standard/data/xml/namespace-support-in-the-dom.md)  
  
- [<span data-ttu-id="3d577-127">Obsługa zdarzeń w dokumencie XML przy użyciu klasy XmlNodeChangedEventArgs</span><span class="sxs-lookup"><span data-stu-id="3d577-127">Event Handling in an XML Document Using the XmlNodeChangedEventArgs</span></span>](../../../../docs/standard/data/xml/event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md)  
  
- [<span data-ttu-id="3d577-128">Rozszerzanie modelu DOM</span><span class="sxs-lookup"><span data-stu-id="3d577-128">Extending the DOM</span></span>](../../../../docs/standard/data/xml/extending-the-dom.md)  
  
## <a name="related-sections"></a><span data-ttu-id="3d577-129">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="3d577-129">Related Sections</span></span>  
 [<span data-ttu-id="3d577-130">Przetwarzanie danych XML przy użyciu modelu danych XPath</span><span class="sxs-lookup"><span data-stu-id="3d577-130">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 <span data-ttu-id="3d577-131">Omawia przy użyciu przetwarzania XML <xref:System.Xml.XPath.XPathNavigator> klasy.</span><span class="sxs-lookup"><span data-stu-id="3d577-131">Discusses XML processing using the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>
