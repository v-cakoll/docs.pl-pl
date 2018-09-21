---
title: Wybieranie, Obliczanie i dopasowywanie danych XML przy użyciu klasy XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 46e059f8-4dc8-4185-9236-784be95228ed
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2544070bb7ea891a804edd559a5d58e08b071771
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/20/2018
ms.locfileid: "46490390"
---
# <a name="selecting-evaluating-and-matching-xml-data-using-xpathnavigator"></a><span data-ttu-id="0e3ca-102">Wybieranie, Obliczanie i dopasowywanie danych XML przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="0e3ca-102">Selecting, Evaluating and Matching XML Data using XPathNavigator</span></span>
<span data-ttu-id="0e3ca-103"><xref:System.Xml.XPath.XPathNavigator> Klasa dostarcza metody do wybierania węzłów w <xref:System.Xml.XPath.XPathDocument> lub <xref:System.Xml.XmlDocument> przy użyciu zapytania XPath, oceny i sprawdź wyniki wyrażenia XPath i określić, czy węzeł w <xref:System.Xml.XPath.XPathDocument> lub <xref:System.Xml.XmlDocument> obiektu pasuje podane wyrażenie XPath.</span><span class="sxs-lookup"><span data-stu-id="0e3ca-103">The <xref:System.Xml.XPath.XPathNavigator> class provides methods to select nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using an XPath query, evaluate and examine the results of an XPath expression, and determine if a node in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object matches a given XPath expression.</span></span> <span data-ttu-id="0e3ca-104">Te i inne pojęcia, które odnoszą się do zaznaczania, oceniania i zgodne węzły w <xref:System.Xml.XPath.XPathDocument> lub <xref:System.Xml.XmlDocument> obiektu są opisane w poniższych tematach.</span><span class="sxs-lookup"><span data-stu-id="0e3ca-104">These and other concepts that relate to selecting, evaluating and matching nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object are described in the following topics.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0e3ca-105">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="0e3ca-105">In This Section</span></span>  
 [<span data-ttu-id="0e3ca-106">Wybieranie danych XML przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="0e3ca-106">Select XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="0e3ca-107">Opisuje zestaw <xref:System.Xml.XPath.XPathNavigator> używany do wybierania zestaw węzłów w metody klasy <xref:System.Xml.XPath.XPathDocument> lub <xref:System.Xml.XmlDocument> obiekt, za pomocą wyrażenia XPath.</span><span class="sxs-lookup"><span data-stu-id="0e3ca-107">Describes the set of <xref:System.Xml.XPath.XPathNavigator> class methods used to select a set of nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using an XPath expression.</span></span>  
  
 [<span data-ttu-id="0e3ca-108">Obliczanie wyrażeń XPath przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="0e3ca-108">Evaluate XPath Expressions using XPathNavigator</span></span>](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)  
 <span data-ttu-id="0e3ca-109">W tym artykule opisano <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> metody <xref:System.Xml.XPath.XPathNavigator> klasa używana do oceny wyrażenia XPath.</span><span class="sxs-lookup"><span data-stu-id="0e3ca-109">Describes the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class used to evaluate an XPath expression.</span></span>  
  
 [<span data-ttu-id="0e3ca-110">Dopasowywanie węzłów przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="0e3ca-110">Matching Nodes using XPathNavigator</span></span>](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)  
 <span data-ttu-id="0e3ca-111">W tym artykule opisano <xref:System.Xml.XPath.XPathNavigator.Matches%2A> metody <xref:System.Xml.XPath.XPathNavigator> klasa używana do określenia, czy węzeł odpowiada wyrażenie XPath.</span><span class="sxs-lookup"><span data-stu-id="0e3ca-111">Describes the <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class used to determine if a node matches an XPath expression.</span></span>  
  
 [<span data-ttu-id="0e3ca-112">Typy węzłów rozpoznawanych w zapytaniach XPath</span><span class="sxs-lookup"><span data-stu-id="0e3ca-112">Node Types Recognized with XPath Queries</span></span>](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)  
 <span data-ttu-id="0e3ca-113">Opisuje typy węzłów rozpoznawane w zapytaniu XPath.</span><span class="sxs-lookup"><span data-stu-id="0e3ca-113">Describes the types of nodes recognized in an XPath query.</span></span>  
  
 [<span data-ttu-id="0e3ca-114">Zapytania XPath i przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="0e3ca-114">XPath Queries and Namespaces</span></span>](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)  
 <span data-ttu-id="0e3ca-115">W tym artykule opisano korzystanie z przestrzeni nazw w zapytaniu XPath.</span><span class="sxs-lookup"><span data-stu-id="0e3ca-115">Describes the use of namespaces in an XPath query.</span></span>  
  
 [<span data-ttu-id="0e3ca-116">Skompilowane wyrażenia XPath</span><span class="sxs-lookup"><span data-stu-id="0e3ca-116">Compiled XPath Expressions</span></span>](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)  
 <span data-ttu-id="0e3ca-117">W tym artykule opisano <xref:System.Xml.XPath.XPathExpression> klasa, która reprezentuje kompilowanym zapytaniu XPath.</span><span class="sxs-lookup"><span data-stu-id="0e3ca-117">Describes the <xref:System.Xml.XPath.XPathExpression> class that represents a compiled XPath query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e3ca-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0e3ca-118">See also</span></span>

- <xref:System.Xml.XmlDocument>  
- <xref:System.Xml.XPath.XPathDocument>  
- <xref:System.Xml.XPath.XPathNavigator>  
- [<span data-ttu-id="0e3ca-119">Przetwarzanie danych XML przy użyciu modelu danych XPath</span><span class="sxs-lookup"><span data-stu-id="0e3ca-119">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
- [<span data-ttu-id="0e3ca-120">Wczytywanie danych XML przy użyciu klas XPathDocument i XmlDocument</span><span class="sxs-lookup"><span data-stu-id="0e3ca-120">Reading XML Data using XPathDocument and XmlDocument</span></span>](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md)  
- [<span data-ttu-id="0e3ca-121">Uzyskiwanie dostępu do danych XML przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="0e3ca-121">Accessing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)  
- [<span data-ttu-id="0e3ca-122">Edytowanie danych XML przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="0e3ca-122">Editing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/editing-xml-data-using-xpathnavigator.md)  
- [<span data-ttu-id="0e3ca-123">Weryfikacja schematu przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="0e3ca-123">Schema Validation using XPathNavigator</span></span>](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md)
