---
title: "Węzeł nawigacji zestawu użyciu klasy XPathNavigator"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1a954b41-7173-40bc-8544-d430f209b1e5
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9ac0135227599d6a72813bcf57b209705545da66
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="node-set-navigation-using-xpathnavigator"></a><span data-ttu-id="f5140-102">Węzeł nawigacji zestawu użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="f5140-102">Node Set Navigation Using XPathNavigator</span></span>
<span data-ttu-id="f5140-103">Można nawigować przez węzły w <xref:System.Xml.XPath.XPathDocument> lub <xref:System.Xml.XmlDocument> obiekt przy użyciu zestawu węzłów nawigacji metody <xref:System.Xml.XPath.XPathNavigator> klasy.</span><span class="sxs-lookup"><span data-stu-id="f5140-103">You can navigate over nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using the node set navigation methods of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span> <span data-ttu-id="f5140-104">Można przejść na wszystkich węzłach lub wybrany zestaw zwrócony przez jedną z metod wybór węzłów <xref:System.Xml.XPath.XPathNavigator> klasy.</span><span class="sxs-lookup"><span data-stu-id="f5140-104">You can navigate over all the nodes or over a selected set of nodes returned by one of the selection methods of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
## <a name="element-node-set-navigation"></a><span data-ttu-id="f5140-105">Element węzła zestawu nawigacji</span><span class="sxs-lookup"><span data-stu-id="f5140-105">Element Node Set Navigation</span></span>  
 <span data-ttu-id="f5140-106"><xref:System.Xml.XPath.XPathNavigator> Klasa udostępnia kilka metod służące do nawigacji węzłów elementów.</span><span class="sxs-lookup"><span data-stu-id="f5140-106">The <xref:System.Xml.XPath.XPathNavigator> class provides several methods used to navigate element nodes.</span></span> <span data-ttu-id="f5140-107">W poniższej tabeli przedstawiono dostępne metody nawigacji oraz opis przenoszeniem; nie ma metody używane do przechodzenia węzłów atrybutu i przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="f5140-107">The following table shows the navigation methods available and a description of how they move; this does not include methods used to navigate attribute and namespace nodes.</span></span>  
  
 <span data-ttu-id="f5140-108">Aby uzyskać więcej informacji o wybieraniu węzłów w <xref:System.Xml.XPath.XPathNavigator> obiektów, zobacz [wybranie opcji, Evaluating i dopasowywania danych XML przy użyciu Element XPathNavigator](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md).</span><span class="sxs-lookup"><span data-stu-id="f5140-108">For more information about selecting nodes in an <xref:System.Xml.XPath.XPathNavigator> object, see [Selecting, Evaluating and Matching XML Data using XPathNavigator](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md).</span></span> <span data-ttu-id="f5140-109">Aby uzyskać więcej informacji na temat Nawigacja węzłów atrybutu i przestrzeni nazw, zobacz [atrybut i element Namespace węzła nawigacji przy użyciu XPathNavigator](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md).</span><span class="sxs-lookup"><span data-stu-id="f5140-109">For more information about navigating attribute and namespace nodes, see [Attribute and Namespace Node Navigation Using XPathNavigator](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md).</span></span>  
  
|<span data-ttu-id="f5140-110">Metoda</span><span class="sxs-lookup"><span data-stu-id="f5140-110">Method</span></span>|<span data-ttu-id="f5140-111">Opis</span><span class="sxs-lookup"><span data-stu-id="f5140-111">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>|<span data-ttu-id="f5140-112">Przenosi <xref:System.Xml.XPath.XPathNavigator> do tej samej pozycji <xref:System.Xml.XPath.XPathNavigator> określony.</span><span class="sxs-lookup"><span data-stu-id="f5140-112">Moves the <xref:System.Xml.XPath.XPathNavigator> to the same position of the <xref:System.Xml.XPath.XPathNavigator> specified.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>|<span data-ttu-id="f5140-113">Przenosi <xref:System.Xml.XPath.XPathNavigator> do elementem podrzędnym bieżącego węzła.</span><span class="sxs-lookup"><span data-stu-id="f5140-113">Moves the <xref:System.Xml.XPath.XPathNavigator> to a child node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>|<span data-ttu-id="f5140-114">Przenosi <xref:System.Xml.XPath.XPathNavigator> pierwszy węzeł równorzędny bieżącego węzła.</span><span class="sxs-lookup"><span data-stu-id="f5140-114">Moves the <xref:System.Xml.XPath.XPathNavigator> to the first sibling node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>|<span data-ttu-id="f5140-115">Przenosi <xref:System.Xml.XPath.XPathNavigator> do pierwszego podrzędnym bieżącego węzła.</span><span class="sxs-lookup"><span data-stu-id="f5140-115">Moves the <xref:System.Xml.XPath.XPathNavigator> to the first child node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFollowing%2A>|<span data-ttu-id="f5140-116">Przenosi <xref:System.Xml.XPath.XPathNavigator> do określonego elementu w kolejności dokumentu.</span><span class="sxs-lookup"><span data-stu-id="f5140-116">Moves the <xref:System.Xml.XPath.XPathNavigator> to the specified element in document order.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>|<span data-ttu-id="f5140-117">Przenosi <xref:System.Xml.XPath.XPathNavigator> do węzła, który ma atrybut typu `ID` z wartością, która odpowiada danym <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="f5140-117">Moves the <xref:System.Xml.XPath.XPathNavigator> to the node that has an attribute of type `ID` with a value that matches the given <xref:System.String>.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A>|<span data-ttu-id="f5140-118">Przenosi <xref:System.Xml.XPath.XPathNavigator> do następnego węzła tego samego poziomu bieżącego węzła.</span><span class="sxs-lookup"><span data-stu-id="f5140-118">Moves the <xref:System.Xml.XPath.XPathNavigator> to the next sibling node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>|<span data-ttu-id="f5140-119">Przenosi <xref:System.Xml.XPath.XPathNavigator> do węzła nadrzędnego bieżącego węzła.</span><span class="sxs-lookup"><span data-stu-id="f5140-119">Moves the <xref:System.Xml.XPath.XPathNavigator> to the parent node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A>|<span data-ttu-id="f5140-120">Przenosi <xref:System.Xml.XPath.XPathNavigator> do poprzedniego węzła tego samego poziomu bieżącego węzła.</span><span class="sxs-lookup"><span data-stu-id="f5140-120">Moves the <xref:System.Xml.XPath.XPathNavigator> to the previous sibling node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToRoot%2A>|<span data-ttu-id="f5140-121">Przenosi <xref:System.Xml.XPath.XPathNavigator> do węzła głównego dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="f5140-121">Moves the <xref:System.Xml.XPath.XPathNavigator> to the root node of the XML document.</span></span>|  
  
## <a name="comments-and-processing-instruction-node-navigation"></a><span data-ttu-id="f5140-122">Komentarze i przetwarzania instrukcji węzła nawigacji</span><span class="sxs-lookup"><span data-stu-id="f5140-122">Comments and Processing Instruction Node Navigation</span></span>  
 <span data-ttu-id="f5140-123">Następujące <xref:System.Xml.XPath.XPathNavigator> metod klasy są prawidłowe w przypadku przenoszenia do komentarzy lub przetwarzania instrukcji inne węzły w dokumencie XML.</span><span class="sxs-lookup"><span data-stu-id="f5140-123">The following <xref:System.Xml.XPath.XPathNavigator> class methods are valid for moving to comments or processing instructions from other nodes in an XML document.</span></span>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>  
  
## <a name="see-also"></a><span data-ttu-id="f5140-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f5140-124">See Also</span></span>  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [<span data-ttu-id="f5140-125">Przetwarzania danych XML przy użyciu modelu danych XPath</span><span class="sxs-lookup"><span data-stu-id="f5140-125">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [<span data-ttu-id="f5140-126">Atrybut i Namespace węzła nawigacji użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="f5140-126">Attribute and Namespace Node Navigation Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md)  
 [<span data-ttu-id="f5140-127">Wyodrębnianie danych XML przy użyciu parametrem XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="f5140-127">Extract XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/extract-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="f5140-128">Uzyskiwanie dostępu do silnie typu danych XML przy użyciu parametrem XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="f5140-128">Accessing Strongly Typed XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
