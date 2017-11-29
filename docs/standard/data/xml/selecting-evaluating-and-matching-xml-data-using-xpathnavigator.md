---
title: "Wybieranie, Evaluating i dopasowywania danych XML przy użyciu parametrem XPathNavigator"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 46e059f8-4dc8-4185-9236-784be95228ed
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 7a86fb36d367342ea0c5bc4968bdd5744bd0524e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="selecting-evaluating-and-matching-xml-data-using-xpathnavigator"></a><span data-ttu-id="b8ba0-102">Wybieranie, Evaluating i dopasowywania danych XML przy użyciu parametrem XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="b8ba0-102">Selecting, Evaluating and Matching XML Data using XPathNavigator</span></span>
<span data-ttu-id="b8ba0-103"><xref:System.Xml.XPath.XPathNavigator> Klasa dostarcza metody do wybierz węzeł w <xref:System.Xml.XPath.XPathDocument> lub <xref:System.Xml.XmlDocument> przy użyciu zapytania XPath, oceny i przejrzeć wyniki wyrażenia XPath i ustalić, czy węzeł w <xref:System.Xml.XPath.XPathDocument> lub <xref:System.Xml.XmlDocument> obiekt dopasowań podane wyrażenie XPath.</span><span class="sxs-lookup"><span data-stu-id="b8ba0-103">The <xref:System.Xml.XPath.XPathNavigator> class provides methods to select nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using an XPath query, evaluate and examine the results of an XPath expression, and determine if a node in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object matches a given XPath expression.</span></span> <span data-ttu-id="b8ba0-104">Te i inne pojęcia, które odnoszą się do zaznaczania, oceny i zgodne węzły w <xref:System.Xml.XPath.XPathDocument> lub <xref:System.Xml.XmlDocument> obiektu są opisane w poniższych tematach.</span><span class="sxs-lookup"><span data-stu-id="b8ba0-104">These and other concepts that relate to selecting, evaluating and matching nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object are described in the following topics.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b8ba0-105">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="b8ba0-105">In This Section</span></span>  
 [<span data-ttu-id="b8ba0-106">Wybierz dane XML przy użyciu parametrem XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="b8ba0-106">Select XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="b8ba0-107">W tym artykule opisano zestaw <xref:System.Xml.XPath.XPathNavigator> klasy metody używane do wybierz zestaw węzłów <xref:System.Xml.XPath.XPathDocument> lub <xref:System.Xml.XmlDocument> obiekt, za pomocą wyrażenia XPath.</span><span class="sxs-lookup"><span data-stu-id="b8ba0-107">Describes the set of <xref:System.Xml.XPath.XPathNavigator> class methods used to select a set of nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using an XPath expression.</span></span>  
  
 [<span data-ttu-id="b8ba0-108">Ocena wyrażenia XPath użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="b8ba0-108">Evaluate XPath Expressions using XPathNavigator</span></span>](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)  
 <span data-ttu-id="b8ba0-109">W tym artykule opisano <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> metody <xref:System.Xml.XPath.XPathNavigator> klasy używane do oceny wyrażenia XPath.</span><span class="sxs-lookup"><span data-stu-id="b8ba0-109">Describes the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class used to evaluate an XPath expression.</span></span>  
  
 [<span data-ttu-id="b8ba0-110">Zgodne węzły użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="b8ba0-110">Matching Nodes using XPathNavigator</span></span>](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)  
 <span data-ttu-id="b8ba0-111">W tym artykule opisano <xref:System.Xml.XPath.XPathNavigator.Matches%2A> metody <xref:System.Xml.XPath.XPathNavigator> klasa używana do określenia, czy węzeł zgodne wyrażenie XPath.</span><span class="sxs-lookup"><span data-stu-id="b8ba0-111">Describes the <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class used to determine if a node matches an XPath expression.</span></span>  
  
 [<span data-ttu-id="b8ba0-112">Typy węzłów rozpoznany z kwerendy XPath</span><span class="sxs-lookup"><span data-stu-id="b8ba0-112">Node Types Recognized with XPath Queries</span></span>](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)  
 <span data-ttu-id="b8ba0-113">W tym artykule opisano typy węzłów rozpoznane w zapytaniu XPath.</span><span class="sxs-lookup"><span data-stu-id="b8ba0-113">Describes the types of nodes recognized in an XPath query.</span></span>  
  
 [<span data-ttu-id="b8ba0-114">Kwerendy XPath i przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="b8ba0-114">XPath Queries and Namespaces</span></span>](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)  
 <span data-ttu-id="b8ba0-115">Opisuje przestrzeni nazw w zapytaniu XPath.</span><span class="sxs-lookup"><span data-stu-id="b8ba0-115">Describes the use of namespaces in an XPath query.</span></span>  
  
 [<span data-ttu-id="b8ba0-116">Wyrażenia XPath skompilowanych</span><span class="sxs-lookup"><span data-stu-id="b8ba0-116">Compiled XPath Expressions</span></span>](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)  
 <span data-ttu-id="b8ba0-117">W tym artykule opisano <xref:System.Xml.XPath.XPathExpression> klasa, która reprezentuje skompilowanym zapytaniu XPath.</span><span class="sxs-lookup"><span data-stu-id="b8ba0-117">Describes the <xref:System.Xml.XPath.XPathExpression> class that represents a compiled XPath query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8ba0-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b8ba0-118">See Also</span></span>  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [<span data-ttu-id="b8ba0-119">Przetwarzania danych XML przy użyciu modelu danych XPath</span><span class="sxs-lookup"><span data-stu-id="b8ba0-119">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [<span data-ttu-id="b8ba0-120">Odczytywanie danych XML przy użyciu XPathDocument i XmlDocument</span><span class="sxs-lookup"><span data-stu-id="b8ba0-120">Reading XML Data using XPathDocument and XmlDocument</span></span>](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md)  
 [<span data-ttu-id="b8ba0-121">Uzyskiwanie dostępu do danych XML przy użyciu parametrem XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="b8ba0-121">Accessing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="b8ba0-122">Edytowanie danych XML przy użyciu parametrem XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="b8ba0-122">Editing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/editing-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="b8ba0-123">Weryfikacja schematu za pomocą parametrem XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="b8ba0-123">Schema Validation using XPathNavigator</span></span>](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md)
