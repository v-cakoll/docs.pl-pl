---
title: Nawigacja po zestawie węzłów przy użyciu klasy XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1a954b41-7173-40bc-8544-d430f209b1e5
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 58adf0251fdc7427f493e8bf9947c081bfccd2a1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698827"
---
# <a name="node-set-navigation-using-xpathnavigator"></a><span data-ttu-id="33afd-102">Nawigacja po zestawie węzłów przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="33afd-102">Node Set Navigation Using XPathNavigator</span></span>
<span data-ttu-id="33afd-103">Możesz nawigować przez węzły w <xref:System.Xml.XPath.XPathDocument> lub <xref:System.Xml.XmlDocument> obiektu przy użyciu metody nawigacji ustaw węzeł <xref:System.Xml.XPath.XPathNavigator> klasy.</span><span class="sxs-lookup"><span data-stu-id="33afd-103">You can navigate over nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using the node set navigation methods of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span> <span data-ttu-id="33afd-104">Możesz przejść za pośrednictwem wszystkich węzłów lub wybrany zestaw węzłów zwrócony przez jedną z metod wybór <xref:System.Xml.XPath.XPathNavigator> klasy.</span><span class="sxs-lookup"><span data-stu-id="33afd-104">You can navigate over all the nodes or over a selected set of nodes returned by one of the selection methods of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
## <a name="element-node-set-navigation"></a><span data-ttu-id="33afd-105">Nawigacja po zestawie węzłów — element</span><span class="sxs-lookup"><span data-stu-id="33afd-105">Element Node Set Navigation</span></span>  
 <span data-ttu-id="33afd-106"><xref:System.Xml.XPath.XPathNavigator> Klasa udostępnia kilka metod, używany do przechodzenia węzłów elementów.</span><span class="sxs-lookup"><span data-stu-id="33afd-106">The <xref:System.Xml.XPath.XPathNavigator> class provides several methods used to navigate element nodes.</span></span> <span data-ttu-id="33afd-107">W poniższej tabeli przedstawiono dostępne metody nawigacji i opis przenoszeniem; nie ma metody służące do nawigacji węzłów atrybutu i przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="33afd-107">The following table shows the navigation methods available and a description of how they move; this does not include methods used to navigate attribute and namespace nodes.</span></span>  
  
 <span data-ttu-id="33afd-108">Aby uzyskać więcej informacji na temat wybierania węzły w <xref:System.Xml.XPath.XPathNavigator> obiektu, zobacz [Wybieranie, Obliczanie i dopasowywanie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md).</span><span class="sxs-lookup"><span data-stu-id="33afd-108">For more information about selecting nodes in an <xref:System.Xml.XPath.XPathNavigator> object, see [Selecting, Evaluating and Matching XML Data using XPathNavigator](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md).</span></span> <span data-ttu-id="33afd-109">Aby uzyskać więcej informacji na temat Nawigacja węzłów atrybutu i przestrzeni nazw, zobacz [atrybut i klasy Namespace węzła nawigacji za pomocą XPathNavigator](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md).</span><span class="sxs-lookup"><span data-stu-id="33afd-109">For more information about navigating attribute and namespace nodes, see [Attribute and Namespace Node Navigation Using XPathNavigator](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md).</span></span>  
  
|<span data-ttu-id="33afd-110">Metoda</span><span class="sxs-lookup"><span data-stu-id="33afd-110">Method</span></span>|<span data-ttu-id="33afd-111">Opis</span><span class="sxs-lookup"><span data-stu-id="33afd-111">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>|<span data-ttu-id="33afd-112">Przenosi <xref:System.Xml.XPath.XPathNavigator> do tej samej pozycji <xref:System.Xml.XPath.XPathNavigator> określony.</span><span class="sxs-lookup"><span data-stu-id="33afd-112">Moves the <xref:System.Xml.XPath.XPathNavigator> to the same position of the <xref:System.Xml.XPath.XPathNavigator> specified.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>|<span data-ttu-id="33afd-113">Przenosi <xref:System.Xml.XPath.XPathNavigator> do węzła podrzędnego bieżącego węzła.</span><span class="sxs-lookup"><span data-stu-id="33afd-113">Moves the <xref:System.Xml.XPath.XPathNavigator> to a child node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>|<span data-ttu-id="33afd-114">Przenosi <xref:System.Xml.XPath.XPathNavigator> do pierwszego węzła równorzędnego bieżącego węzła.</span><span class="sxs-lookup"><span data-stu-id="33afd-114">Moves the <xref:System.Xml.XPath.XPathNavigator> to the first sibling node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>|<span data-ttu-id="33afd-115">Przenosi <xref:System.Xml.XPath.XPathNavigator> do pierwszego węzła podrzędnego bieżącego węzła.</span><span class="sxs-lookup"><span data-stu-id="33afd-115">Moves the <xref:System.Xml.XPath.XPathNavigator> to the first child node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFollowing%2A>|<span data-ttu-id="33afd-116">Przenosi <xref:System.Xml.XPath.XPathNavigator> do określonego elementu w kolejności dokumentu.</span><span class="sxs-lookup"><span data-stu-id="33afd-116">Moves the <xref:System.Xml.XPath.XPathNavigator> to the specified element in document order.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>|<span data-ttu-id="33afd-117">Przenosi <xref:System.Xml.XPath.XPathNavigator> do węzła, który ma atrybut typu `ID` z wartością, która odpowiada danym <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="33afd-117">Moves the <xref:System.Xml.XPath.XPathNavigator> to the node that has an attribute of type `ID` with a value that matches the given <xref:System.String>.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A>|<span data-ttu-id="33afd-118">Przenosi <xref:System.Xml.XPath.XPathNavigator> do kolejnego węzła równorzędnego bieżącego węzła.</span><span class="sxs-lookup"><span data-stu-id="33afd-118">Moves the <xref:System.Xml.XPath.XPathNavigator> to the next sibling node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>|<span data-ttu-id="33afd-119">Przenosi <xref:System.Xml.XPath.XPathNavigator> do węzła nadrzędnego bieżącego węzła.</span><span class="sxs-lookup"><span data-stu-id="33afd-119">Moves the <xref:System.Xml.XPath.XPathNavigator> to the parent node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A>|<span data-ttu-id="33afd-120">Przenosi <xref:System.Xml.XPath.XPathNavigator> do poprzedniego węzła równorzędnego bieżącego węzła.</span><span class="sxs-lookup"><span data-stu-id="33afd-120">Moves the <xref:System.Xml.XPath.XPathNavigator> to the previous sibling node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToRoot%2A>|<span data-ttu-id="33afd-121">Przenosi <xref:System.Xml.XPath.XPathNavigator> do węzła głównego dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="33afd-121">Moves the <xref:System.Xml.XPath.XPathNavigator> to the root node of the XML document.</span></span>|  
  
## <a name="comments-and-processing-instruction-node-navigation"></a><span data-ttu-id="33afd-122">Komentarze i nawigacja węzłów instrukcji przetwarzania</span><span class="sxs-lookup"><span data-stu-id="33afd-122">Comments and Processing Instruction Node Navigation</span></span>  
 <span data-ttu-id="33afd-123">Następujące <xref:System.Xml.XPath.XPathNavigator> metod klasy są prawidłowe w przypadku przenoszenia do komentarze lub przetwarzania instrukcji z innych węzłów w dokumencie XML.</span><span class="sxs-lookup"><span data-stu-id="33afd-123">The following <xref:System.Xml.XPath.XPathNavigator> class methods are valid for moving to comments or processing instructions from other nodes in an XML document.</span></span>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>  
  
## <a name="see-also"></a><span data-ttu-id="33afd-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="33afd-124">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="33afd-125">Przetwarzanie danych XML przy użyciu modelu danych XPath</span><span class="sxs-lookup"><span data-stu-id="33afd-125">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="33afd-126">Nawigacja po atrybutach i przestrzeni nazw węzła przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="33afd-126">Attribute and Namespace Node Navigation Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md)
- [<span data-ttu-id="33afd-127">Wyodrębnianie danych XML przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="33afd-127">Extract XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/extract-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="33afd-128">Uzyskiwanie dostępu do silnie typizowanych danych XML przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="33afd-128">Accessing Strongly Typed XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
