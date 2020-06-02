---
title: Wybieranie, obliczanie i dopasowywanie danych XML przy użyciu klasy XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 46e059f8-4dc8-4185-9236-784be95228ed
ms.openlocfilehash: 1418e768db2f5f860ec40cf4e1351b4ec4a14a08
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84282210"
---
# <a name="selecting-evaluating-and-matching-xml-data-using-xpathnavigator"></a><span data-ttu-id="d4dc7-102">Wybieranie, obliczanie i dopasowywanie danych XML przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="d4dc7-102">Selecting, Evaluating and Matching XML Data using XPathNavigator</span></span>
<span data-ttu-id="d4dc7-103"><xref:System.Xml.XPath.XPathNavigator>Klasa dostarcza metody do wybierania węzłów w <xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XmlDocument> obiekcie lub przy użyciu kwerendy XPath, ocenia i bada wyniki wyrażenia XPath i określa, czy węzeł w <xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XmlDocument> obiekcie lub odpowiada danemu wyrażeniu XPath.</span><span class="sxs-lookup"><span data-stu-id="d4dc7-103">The <xref:System.Xml.XPath.XPathNavigator> class provides methods to select nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using an XPath query, evaluate and examine the results of an XPath expression, and determine if a node in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object matches a given XPath expression.</span></span> <span data-ttu-id="d4dc7-104">Te i inne pojęcia, które odnoszą się do wybierania, oceniania i dopasowywania węzłów w <xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XmlDocument> obiekcie lub są opisane w poniższych tematach.</span><span class="sxs-lookup"><span data-stu-id="d4dc7-104">These and other concepts that relate to selecting, evaluating and matching nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object are described in the following topics.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d4dc7-105">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="d4dc7-105">In This Section</span></span>  
 [<span data-ttu-id="d4dc7-106">Wybieranie danych XML przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="d4dc7-106">Select XML Data Using XPathNavigator</span></span>](select-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="d4dc7-107">Opisuje zestaw <xref:System.Xml.XPath.XPathNavigator> metod klasy używanych do wybierania zestawu węzłów w <xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XmlDocument> obiekcie lub przy użyciu wyrażenia XPath.</span><span class="sxs-lookup"><span data-stu-id="d4dc7-107">Describes the set of <xref:System.Xml.XPath.XPathNavigator> class methods used to select a set of nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using an XPath expression.</span></span>  
  
 [<span data-ttu-id="d4dc7-108">Obliczanie wyrażeń XPath przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="d4dc7-108">Evaluate XPath Expressions using XPathNavigator</span></span>](evaluate-xpath-expressions-using-xpathnavigator.md)  
 <span data-ttu-id="d4dc7-109">Opisuje <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> metodę <xref:System.Xml.XPath.XPathNavigator> klasy używanej do obliczania wyrażenia XPath.</span><span class="sxs-lookup"><span data-stu-id="d4dc7-109">Describes the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class used to evaluate an XPath expression.</span></span>  
  
 [<span data-ttu-id="d4dc7-110">Dopasowywanie węzłów przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="d4dc7-110">Matching Nodes using XPathNavigator</span></span>](matching-nodes-using-xpathnavigator.md)  
 <span data-ttu-id="d4dc7-111">Opisuje <xref:System.Xml.XPath.XPathNavigator.Matches%2A> metodę <xref:System.Xml.XPath.XPathNavigator> klasy służącą do określenia, czy węzeł dopasowuje wyrażenie XPath.</span><span class="sxs-lookup"><span data-stu-id="d4dc7-111">Describes the <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class used to determine if a node matches an XPath expression.</span></span>  
  
 [<span data-ttu-id="d4dc7-112">Typy węzłów rozpoznawanych w zapytaniach XPath</span><span class="sxs-lookup"><span data-stu-id="d4dc7-112">Node Types Recognized with XPath Queries</span></span>](node-types-recognized-with-xpath-queries.md)  
 <span data-ttu-id="d4dc7-113">Opisuje typy węzłów rozpoznawane w zapytaniu XPath.</span><span class="sxs-lookup"><span data-stu-id="d4dc7-113">Describes the types of nodes recognized in an XPath query.</span></span>  
  
 [<span data-ttu-id="d4dc7-114">Zapytania XPath i przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="d4dc7-114">XPath Queries and Namespaces</span></span>](xpath-queries-and-namespaces.md)  
 <span data-ttu-id="d4dc7-115">Opisuje użycie przestrzeni nazw w zapytaniu XPath.</span><span class="sxs-lookup"><span data-stu-id="d4dc7-115">Describes the use of namespaces in an XPath query.</span></span>  
  
 [<span data-ttu-id="d4dc7-116">Skompilowane wyrażenia XPath</span><span class="sxs-lookup"><span data-stu-id="d4dc7-116">Compiled XPath Expressions</span></span>](compiled-xpath-expressions.md)  
 <span data-ttu-id="d4dc7-117">Opisuje <xref:System.Xml.XPath.XPathExpression> klasę, która reprezentuje skompilowane zapytanie XPath.</span><span class="sxs-lookup"><span data-stu-id="d4dc7-117">Describes the <xref:System.Xml.XPath.XPathExpression> class that represents a compiled XPath query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4dc7-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d4dc7-118">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="d4dc7-119">Przetwarzanie danych XML przy użyciu modelu danych XPath</span><span class="sxs-lookup"><span data-stu-id="d4dc7-119">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="d4dc7-120">Wczytywanie danych XML przy użyciu klas XPathDocument i XmlDocument</span><span class="sxs-lookup"><span data-stu-id="d4dc7-120">Reading XML Data using XPathDocument and XmlDocument</span></span>](reading-xml-data-using-xpathdocument-and-xmldocument.md)
- [<span data-ttu-id="d4dc7-121">Uzyskiwanie dostępu do danych XML przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="d4dc7-121">Accessing XML Data using XPathNavigator</span></span>](accessing-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="d4dc7-122">Edytowanie danych XML przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="d4dc7-122">Editing XML Data using XPathNavigator</span></span>](editing-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="d4dc7-123">Weryfikacja schematu przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="d4dc7-123">Schema Validation using XPathNavigator</span></span>](schema-validation-using-xpathnavigator.md)
