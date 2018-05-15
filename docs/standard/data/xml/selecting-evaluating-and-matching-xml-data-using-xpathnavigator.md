---
title: Wybieranie, Evaluating i dopasowywania danych XML przy użyciu parametrem XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 46e059f8-4dc8-4185-9236-784be95228ed
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 55344de87672c09305c03c25047c2f3cc3bdab7e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="selecting-evaluating-and-matching-xml-data-using-xpathnavigator"></a><span data-ttu-id="ad206-102">Wybieranie, Evaluating i dopasowywania danych XML przy użyciu parametrem XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="ad206-102">Selecting, Evaluating and Matching XML Data using XPathNavigator</span></span>
<span data-ttu-id="ad206-103"><xref:System.Xml.XPath.XPathNavigator> Klasa dostarcza metody do wybierz węzeł w <xref:System.Xml.XPath.XPathDocument> lub <xref:System.Xml.XmlDocument> przy użyciu zapytania XPath, oceny i przejrzeć wyniki wyrażenia XPath i ustalić, czy węzeł w <xref:System.Xml.XPath.XPathDocument> lub <xref:System.Xml.XmlDocument> obiekt dopasowań podane wyrażenie XPath.</span><span class="sxs-lookup"><span data-stu-id="ad206-103">The <xref:System.Xml.XPath.XPathNavigator> class provides methods to select nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using an XPath query, evaluate and examine the results of an XPath expression, and determine if a node in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object matches a given XPath expression.</span></span> <span data-ttu-id="ad206-104">Te i inne pojęcia, które odnoszą się do zaznaczania, oceny i zgodne węzły w <xref:System.Xml.XPath.XPathDocument> lub <xref:System.Xml.XmlDocument> obiektu są opisane w poniższych tematach.</span><span class="sxs-lookup"><span data-stu-id="ad206-104">These and other concepts that relate to selecting, evaluating and matching nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object are described in the following topics.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ad206-105">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="ad206-105">In This Section</span></span>  
 [<span data-ttu-id="ad206-106">Wybieranie danych XML przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="ad206-106">Select XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="ad206-107">W tym artykule opisano zestaw <xref:System.Xml.XPath.XPathNavigator> klasy metody używane do wybierz zestaw węzłów <xref:System.Xml.XPath.XPathDocument> lub <xref:System.Xml.XmlDocument> obiekt, za pomocą wyrażenia XPath.</span><span class="sxs-lookup"><span data-stu-id="ad206-107">Describes the set of <xref:System.Xml.XPath.XPathNavigator> class methods used to select a set of nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using an XPath expression.</span></span>  
  
 [<span data-ttu-id="ad206-108">Obliczanie wyrażeń XPath przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="ad206-108">Evaluate XPath Expressions using XPathNavigator</span></span>](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)  
 <span data-ttu-id="ad206-109">W tym artykule opisano <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> metody <xref:System.Xml.XPath.XPathNavigator> klasy używane do oceny wyrażenia XPath.</span><span class="sxs-lookup"><span data-stu-id="ad206-109">Describes the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class used to evaluate an XPath expression.</span></span>  
  
 [<span data-ttu-id="ad206-110">Dopasowywanie węzłów przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="ad206-110">Matching Nodes using XPathNavigator</span></span>](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)  
 <span data-ttu-id="ad206-111">W tym artykule opisano <xref:System.Xml.XPath.XPathNavigator.Matches%2A> metody <xref:System.Xml.XPath.XPathNavigator> klasa używana do określenia, czy węzeł zgodne wyrażenie XPath.</span><span class="sxs-lookup"><span data-stu-id="ad206-111">Describes the <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class used to determine if a node matches an XPath expression.</span></span>  
  
 [<span data-ttu-id="ad206-112">Typy węzłów rozpoznawanych w zapytaniach XPath</span><span class="sxs-lookup"><span data-stu-id="ad206-112">Node Types Recognized with XPath Queries</span></span>](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)  
 <span data-ttu-id="ad206-113">W tym artykule opisano typy węzłów rozpoznane w zapytaniu XPath.</span><span class="sxs-lookup"><span data-stu-id="ad206-113">Describes the types of nodes recognized in an XPath query.</span></span>  
  
 [<span data-ttu-id="ad206-114">Zapytania XPath i przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="ad206-114">XPath Queries and Namespaces</span></span>](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)  
 <span data-ttu-id="ad206-115">Opisuje przestrzeni nazw w zapytaniu XPath.</span><span class="sxs-lookup"><span data-stu-id="ad206-115">Describes the use of namespaces in an XPath query.</span></span>  
  
 [<span data-ttu-id="ad206-116">Skompilowane wyrażenia XPath</span><span class="sxs-lookup"><span data-stu-id="ad206-116">Compiled XPath Expressions</span></span>](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)  
 <span data-ttu-id="ad206-117">W tym artykule opisano <xref:System.Xml.XPath.XPathExpression> klasa, która reprezentuje skompilowanym zapytaniu XPath.</span><span class="sxs-lookup"><span data-stu-id="ad206-117">Describes the <xref:System.Xml.XPath.XPathExpression> class that represents a compiled XPath query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad206-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ad206-118">See Also</span></span>  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [<span data-ttu-id="ad206-119">Przetwarzanie danych XML przy użyciu modelu danych XPath</span><span class="sxs-lookup"><span data-stu-id="ad206-119">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [<span data-ttu-id="ad206-120">Wczytywanie danych XML przy użyciu klas XPathDocument i XmlDocument</span><span class="sxs-lookup"><span data-stu-id="ad206-120">Reading XML Data using XPathDocument and XmlDocument</span></span>](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md)  
 [<span data-ttu-id="ad206-121">Uzyskiwanie dostępu do danych XML przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="ad206-121">Accessing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="ad206-122">Edytowanie danych XML przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="ad206-122">Editing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/editing-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="ad206-123">Weryfikacja schematu przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="ad206-123">Schema Validation using XPathNavigator</span></span>](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md)
