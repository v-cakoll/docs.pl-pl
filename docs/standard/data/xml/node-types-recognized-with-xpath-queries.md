---
title: Typy węzłów rozpoznawanych w zapytaniach XPath
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1d33e22d-18e5-43f8-a466-2e3d0a8dd094
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 19aeab232f366818291bd682ab9c063a75be6687
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61936750"
---
# <a name="node-types-recognized-with-xpath-queries"></a><span data-ttu-id="c04f9-102">Typy węzłów rozpoznawanych w zapytaniach XPath</span><span class="sxs-lookup"><span data-stu-id="c04f9-102">Node Types Recognized with XPath Queries</span></span>
<span data-ttu-id="c04f9-103">Typy węzłów rozpoznawane w zapytaniu XPath nie są te same typy węzłów można odnaleźć w modelu DOM (Document Object).</span><span class="sxs-lookup"><span data-stu-id="c04f9-103">The types of nodes recognized in an XPath query are not the same node types found in the Document Object Model (DOM).</span></span>  
  
## <a name="w3c-xpath-node-types"></a><span data-ttu-id="c04f9-104">Typy węzłów XPath W3C</span><span class="sxs-lookup"><span data-stu-id="c04f9-104">W3C XPath Node Types</span></span>  
 <span data-ttu-id="c04f9-105">Typy węzłów rozpoznawane w zapytaniu XPath nie są typy węzłów, o których odnaleźć w modelu DOM (Document Object).</span><span class="sxs-lookup"><span data-stu-id="c04f9-105">The types of nodes recognized in an XPath query are not the types of nodes found in the Document Object Model (DOM).</span></span> <span data-ttu-id="c04f9-106">Poniżej przedstawiono typy węzłów XPath, które są reprezentowane przez <xref:System.Xml.XPath.XPathNodeType> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="c04f9-106">The following are the XPath node types represented by the <xref:System.Xml.XPath.XPathNodeType> enumeration.</span></span>  
  
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
  
 <span data-ttu-id="c04f9-107">Te typy węzłów są oparte na modelu danych XPath, gdzie węzły są uzyskiwane z ustawić informacji XML.</span><span class="sxs-lookup"><span data-stu-id="c04f9-107">These node types are based on the XPath data model, where the nodes are derived from the XML Information Set.</span></span> <span data-ttu-id="c04f9-108"><xref:System.Xml.XPath.XPathNodeType.SignificantWhitespace> i <xref:System.Xml.XPath.XPathNodeType.Whitespace> typy węzłów są rozszerzeniami Microsoft .NET Framework do typów węzeł podstawowy opisane w modelu danych XPath.</span><span class="sxs-lookup"><span data-stu-id="c04f9-108">The <xref:System.Xml.XPath.XPathNodeType.SignificantWhitespace> and <xref:System.Xml.XPath.XPathNodeType.Whitespace> node types are Microsoft .NET Framework extensions to the base node types described in the XPath data model.</span></span>  
  
 <span data-ttu-id="c04f9-109">Typ węzła atrybutu jest używana inaczej w modelu danych XPath niż w modelu DOM.</span><span class="sxs-lookup"><span data-stu-id="c04f9-109">The attribute node type is used differently in the XPath data model than it is in the DOM.</span></span> <span data-ttu-id="c04f9-110">W modelu danych XPath węzeł elementu zawiera zestaw węzłów atrybutu odnoszących się do niego, a węzeł elementu jest elementem nadrzędnym każdego węzła atrybutu.</span><span class="sxs-lookup"><span data-stu-id="c04f9-110">In the XPath data model, the element node has a set of attribute nodes related to it and the element node is the parent of each attribute node.</span></span> <span data-ttu-id="c04f9-111">Jednak w modelu DOM, węzeł elementu jest właścicielem i nie nadrzędnym.</span><span class="sxs-lookup"><span data-stu-id="c04f9-111">However, in the DOM, the element node is the owner and not the parent.</span></span> <span data-ttu-id="c04f9-112">W obu modelach węzłów atrybutu i przestrzeni nazw nie są uważane za węzły podrzędne węzła elementu.</span><span class="sxs-lookup"><span data-stu-id="c04f9-112">In both models, attribute and namespace nodes are not considered child nodes of the element node.</span></span>  
  
 <span data-ttu-id="c04f9-113">Typ węzła obszaru nazw jest dodatkiem do modelu danych XPath i nie jest rozpoznawanym typem węzeł modelu DOM.</span><span class="sxs-lookup"><span data-stu-id="c04f9-113">The namespace node type is an addition to the XPath data model and is not a recognized DOM node type.</span></span>  
  
 <span data-ttu-id="c04f9-114">Aby uzyskać więcej informacji o nawigacji elementu, atrybutu i węzły przestrzeni nazw, zobacz [węzła zestawu nawigacji przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md) i [atrybut i klasy Namespace węzła nawigacji za pomocą XPathNavigator](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md) tematy.</span><span class="sxs-lookup"><span data-stu-id="c04f9-114">For more information about navigating element, attribute, and namespace nodes, see the [Node Set Navigation Using XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md) and [Attribute and Namespace Node Navigation Using XPathNavigator](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md) topics.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c04f9-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c04f9-115">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="c04f9-116">Przetwarzanie danych XML przy użyciu modelu danych XPath</span><span class="sxs-lookup"><span data-stu-id="c04f9-116">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="c04f9-117">Wybieranie danych XML przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="c04f9-117">Select XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="c04f9-118">Obliczanie wyrażeń XPath przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="c04f9-118">Evaluate XPath Expressions using XPathNavigator</span></span>](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)
- [<span data-ttu-id="c04f9-119">Dopasowywanie węzłów przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="c04f9-119">Matching Nodes using XPathNavigator</span></span>](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)
- [<span data-ttu-id="c04f9-120">Zapytania XPath i przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="c04f9-120">XPath Queries and Namespaces</span></span>](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)
- [<span data-ttu-id="c04f9-121">Skompilowane wyrażenia XPath</span><span class="sxs-lookup"><span data-stu-id="c04f9-121">Compiled XPath Expressions</span></span>](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
