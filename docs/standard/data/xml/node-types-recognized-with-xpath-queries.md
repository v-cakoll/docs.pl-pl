---
title: Typy węzłów rozpoznany z kwerendy XPath
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1d33e22d-18e5-43f8-a466-2e3d0a8dd094
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 005c5f4981a7ab1889678e391a6df6e0b7b43f71
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33569382"
---
# <a name="node-types-recognized-with-xpath-queries"></a><span data-ttu-id="162e5-102">Typy węzłów rozpoznany z kwerendy XPath</span><span class="sxs-lookup"><span data-stu-id="162e5-102">Node Types Recognized with XPath Queries</span></span>
<span data-ttu-id="162e5-103">Typy węzłów rozpoznane w zapytaniu XPath nie są tego samego typy węzłów można odnaleźć w modelu DOM (Document Object).</span><span class="sxs-lookup"><span data-stu-id="162e5-103">The types of nodes recognized in an XPath query are not the same node types found in the Document Object Model (DOM).</span></span>  
  
## <a name="w3c-xpath-node-types"></a><span data-ttu-id="162e5-104">Typy węzłów XPath W3C</span><span class="sxs-lookup"><span data-stu-id="162e5-104">W3C XPath Node Types</span></span>  
 <span data-ttu-id="162e5-105">Typy węzłów rozpoznane w zapytaniu XPath nie są typy węzłów można odnaleźć w modelu DOM (Document Object).</span><span class="sxs-lookup"><span data-stu-id="162e5-105">The types of nodes recognized in an XPath query are not the types of nodes found in the Document Object Model (DOM).</span></span> <span data-ttu-id="162e5-106">Poniżej przedstawiono typy węzłów XPath reprezentowany przez <xref:System.Xml.XPath.XPathNodeType> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="162e5-106">The following are the XPath node types represented by the <xref:System.Xml.XPath.XPathNodeType> enumeration.</span></span>  
  
-   <xref:System.Xml.XPath.XPathNodeType.All>  
  
-   <xref:System.Xml.XPath.XPathNodeType.Attribute>  
  
-   <xref:System.Xml.XPath.XPathNodeType.Comment>  
  
-   <xref:System.Xml.XPath.XPathNodeType.Element>  
  
-   <xref:System.Xml.XPath.XPathNodeType.Namespace>  
  
-   <xref:System.Xml.XPath.XPathNodeType.ProcessingInstruction>  
  
-   <xref:System.Xml.XPath.XPathNodeType.Root>  
  
-   <xref:System.Xml.XPath.XPathNodeType.SignificantWhitespace>  
  
-   <xref:System.Xml.XPath.XPathNodeType.Text>  
  
-   <xref:System.Xml.XPath.XPathNodeType.Whitespace>  
  
 <span data-ttu-id="162e5-107">Te typy węzłów są oparte na XPath modelu danych, gdzie węzły są uzyskiwane z zestawu XML informacji.</span><span class="sxs-lookup"><span data-stu-id="162e5-107">These node types are based on the XPath data model, where the nodes are derived from the XML Information Set.</span></span> <span data-ttu-id="162e5-108"><xref:System.Xml.XPath.XPathNodeType.SignificantWhitespace> i <xref:System.Xml.XPath.XPathNodeType.Whitespace> węzła typy rozszerzeń programu Microsoft .NET Framework do typów węzeł podstawowy opisanego w modelu danych XPath.</span><span class="sxs-lookup"><span data-stu-id="162e5-108">The <xref:System.Xml.XPath.XPathNodeType.SignificantWhitespace> and <xref:System.Xml.XPath.XPathNodeType.Whitespace> node types are Microsoft .NET Framework extensions to the base node types described in the XPath data model.</span></span>  
  
 <span data-ttu-id="162e5-109">Typ węzła atrybutu służy inaczej w modelu danych XPath nie znajduje się w modelu DOM.</span><span class="sxs-lookup"><span data-stu-id="162e5-109">The attribute node type is used differently in the XPath data model than it is in the DOM.</span></span> <span data-ttu-id="162e5-110">W modelu danych XPath węzeł elementu ma zestaw związane z jego węzłów atrybutu i węzeł element jest elementem nadrzędnym każdego węzła atrybutu.</span><span class="sxs-lookup"><span data-stu-id="162e5-110">In the XPath data model, the element node has a set of attribute nodes related to it and the element node is the parent of each attribute node.</span></span> <span data-ttu-id="162e5-111">Jednak w modelu DOM, węzeł elementu jest właścicielem i nie nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="162e5-111">However, in the DOM, the element node is the owner and not the parent.</span></span> <span data-ttu-id="162e5-112">W obu modelach węzłów atrybutu i przestrzeni nazw nie są uznawane za węzłów podrzędnych węzła elementu.</span><span class="sxs-lookup"><span data-stu-id="162e5-112">In both models, attribute and namespace nodes are not considered child nodes of the element node.</span></span>  
  
 <span data-ttu-id="162e5-113">Typ węzła przestrzeni nazw jest dodanie do modelu danych XPath i nie jest rozpoznanym typem węzeł modelu DOM.</span><span class="sxs-lookup"><span data-stu-id="162e5-113">The namespace node type is an addition to the XPath data model and is not a recognized DOM node type.</span></span>  
  
 <span data-ttu-id="162e5-114">Aby uzyskać więcej informacji na temat nawigacji elementu, atrybutu i przestrzeni nazw węzłów, zobacz [węzła ustawić nawigacji przy użyciu Element XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md) i [atrybut i element Namespace węzła nawigacji przy użyciu XPathNavigator](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md) tematy.</span><span class="sxs-lookup"><span data-stu-id="162e5-114">For more information about navigating element, attribute, and namespace nodes, see the [Node Set Navigation Using XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md) and [Attribute and Namespace Node Navigation Using XPathNavigator](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md) topics.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="162e5-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="162e5-115">See Also</span></span>  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [<span data-ttu-id="162e5-116">Przetwarzanie danych XML przy użyciu modelu danych XPath</span><span class="sxs-lookup"><span data-stu-id="162e5-116">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [<span data-ttu-id="162e5-117">Wybieranie danych XML przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="162e5-117">Select XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="162e5-118">Obliczanie wyrażeń XPath przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="162e5-118">Evaluate XPath Expressions using XPathNavigator</span></span>](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)  
 [<span data-ttu-id="162e5-119">Dopasowywanie węzłów przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="162e5-119">Matching Nodes using XPathNavigator</span></span>](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)  
 [<span data-ttu-id="162e5-120">Zapytania XPath i przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="162e5-120">XPath Queries and Namespaces</span></span>](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)  
 [<span data-ttu-id="162e5-121">Skompilowane wyrażenia XPath</span><span class="sxs-lookup"><span data-stu-id="162e5-121">Compiled XPath Expressions</span></span>](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
