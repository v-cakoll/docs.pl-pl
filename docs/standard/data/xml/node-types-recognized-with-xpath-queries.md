---
title: Typy węzłów rozpoznawanych w zapytaniach XPath
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1d33e22d-18e5-43f8-a466-2e3d0a8dd094
ms.openlocfilehash: cc1aa668ccf6fc7f210f48a28cf76b364459c784
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710547"
---
# <a name="node-types-recognized-with-xpath-queries"></a><span data-ttu-id="19e07-102">Typy węzłów rozpoznawanych w zapytaniach XPath</span><span class="sxs-lookup"><span data-stu-id="19e07-102">Node Types Recognized with XPath Queries</span></span>
<span data-ttu-id="19e07-103">Typy węzłów rozpoznawane w zapytaniu XPath nie są tymi samymi typami węzłów, które znajdują się w Document Object Model (DOM).</span><span class="sxs-lookup"><span data-stu-id="19e07-103">The types of nodes recognized in an XPath query are not the same node types found in the Document Object Model (DOM).</span></span>  
  
## <a name="w3c-xpath-node-types"></a><span data-ttu-id="19e07-104">Typy węzłów W3C XPath</span><span class="sxs-lookup"><span data-stu-id="19e07-104">W3C XPath Node Types</span></span>  
 <span data-ttu-id="19e07-105">Typy węzłów rozpoznawane w zapytaniu XPath nie są typami węzłów znalezionych w Document Object Model (DOM).</span><span class="sxs-lookup"><span data-stu-id="19e07-105">The types of nodes recognized in an XPath query are not the types of nodes found in the Document Object Model (DOM).</span></span> <span data-ttu-id="19e07-106">Poniżej przedstawiono typy węzłów XPath reprezentowane przez <xref:System.Xml.XPath.XPathNodeType> Wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="19e07-106">The following are the XPath node types represented by the <xref:System.Xml.XPath.XPathNodeType> enumeration.</span></span>  
  
- <xref:System.Xml.XPath.XPathNodeType.All>  
  
- <xref:System.Xml.XPath.XPathNodeType.Attribute>  
  
- <xref:System.Xml.XPath.XPathNodeType.Comment>  
  
- <xref:System.Xml.XPath.XPathNodeType.Element>  
  
- <xref:System.Xml.XPath.XPathNodeType.Namespace>  
  
- <xref:System.Xml.XPath.XPathNodeType.ProcessingInstruction>  
  
- <xref:System.Xml.XPath.XPathNodeType.Root>  
  
- <xref:System.Xml.XPath.XPathNodeType.SignificantWhitespace>  
  
- <xref:System.Xml.XPath.XPathNodeType.Text>  
  
- <xref:System.Xml.XPath.XPathNodeType.Whitespace>  
  
 <span data-ttu-id="19e07-107">Te typy węzłów są oparte na modelu danych XPath, w którym węzły pochodzą z zestawu informacji XML.</span><span class="sxs-lookup"><span data-stu-id="19e07-107">These node types are based on the XPath data model, where the nodes are derived from the XML Information Set.</span></span> <span data-ttu-id="19e07-108">Typy <xref:System.Xml.XPath.XPathNodeType.SignificantWhitespace> węzłów <xref:System.Xml.XPath.XPathNodeType.Whitespace> i są Microsoft .NET rozszerzenia struktur do typów węzła podstawowego opisanego w modelu danych XPath.</span><span class="sxs-lookup"><span data-stu-id="19e07-108">The <xref:System.Xml.XPath.XPathNodeType.SignificantWhitespace> and <xref:System.Xml.XPath.XPathNodeType.Whitespace> node types are Microsoft .NET Framework extensions to the base node types described in the XPath data model.</span></span>  
  
 <span data-ttu-id="19e07-109">Typ węzła atrybutu jest używany inaczej w modelu danych XPath, niż jest w modelu DOM.</span><span class="sxs-lookup"><span data-stu-id="19e07-109">The attribute node type is used differently in the XPath data model than it is in the DOM.</span></span> <span data-ttu-id="19e07-110">W modelu danych XPath węzeł elementu ma zestaw węzłów atrybutów związanych z nim, a węzeł elementu jest elementem nadrzędnym każdego węzła atrybutu.</span><span class="sxs-lookup"><span data-stu-id="19e07-110">In the XPath data model, the element node has a set of attribute nodes related to it and the element node is the parent of each attribute node.</span></span> <span data-ttu-id="19e07-111">Jednak w modelu DOM węzeł elementu jest właścicielem, a nie elementem nadrzędnym.</span><span class="sxs-lookup"><span data-stu-id="19e07-111">However, in the DOM, the element node is the owner and not the parent.</span></span> <span data-ttu-id="19e07-112">W obu modelach węzły atrybut i przestrzeń nazw nie są traktowane jako węzły podrzędne węzła elementu.</span><span class="sxs-lookup"><span data-stu-id="19e07-112">In both models, attribute and namespace nodes are not considered child nodes of the element node.</span></span>  
  
 <span data-ttu-id="19e07-113">Typ węzła przestrzeni nazw jest dodatkiem do modelu danych XPath i nie jest rozpoznawanym typem węzła DOM.</span><span class="sxs-lookup"><span data-stu-id="19e07-113">The namespace node type is an addition to the XPath data model and is not a recognized DOM node type.</span></span>  
  
 <span data-ttu-id="19e07-114">Aby uzyskać więcej informacji na temat nawigowania po węzłach elementów, atrybutów i przestrzeni nazw, zobacz [Nawigacja zestawu węzłów przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md) oraz [nawigowanie po atrybutach i węzłach przestrzeni nazw za pomocą obiektów XPathNavigator](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md) .</span><span class="sxs-lookup"><span data-stu-id="19e07-114">For more information about navigating element, attribute, and namespace nodes, see the [Node Set Navigation Using XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md) and [Attribute and Namespace Node Navigation Using XPathNavigator](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md) topics.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19e07-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="19e07-115">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="19e07-116">Przetwarzanie danych XML przy użyciu modelu danych XPath</span><span class="sxs-lookup"><span data-stu-id="19e07-116">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="19e07-117">Wybieranie danych XML przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="19e07-117">Select XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="19e07-118">Obliczanie wyrażeń XPath przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="19e07-118">Evaluate XPath Expressions using XPathNavigator</span></span>](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)
- [<span data-ttu-id="19e07-119">Dopasowywanie węzłów przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="19e07-119">Matching Nodes using XPathNavigator</span></span>](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)
- [<span data-ttu-id="19e07-120">Zapytania XPath i przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="19e07-120">XPath Queries and Namespaces</span></span>](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)
- [<span data-ttu-id="19e07-121">Skompilowane wyrażenia XPath</span><span class="sxs-lookup"><span data-stu-id="19e07-121">Compiled XPath Expressions</span></span>](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
