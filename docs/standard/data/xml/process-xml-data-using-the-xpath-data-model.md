---
title: "Przetwarzania danych XML przy użyciu modelu danych XPath"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 536c6fce-1453-4654-9c72-bca54d47e081
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3d2c8db03d494be13a93df06a359e4e4294c22a2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="process-xml-data-using-the-xpath-data-model"></a><span data-ttu-id="85652-102">Przetwarzania danych XML przy użyciu modelu danych XPath</span><span class="sxs-lookup"><span data-stu-id="85652-102">Process XML Data Using the XPath Data Model</span></span>
<span data-ttu-id="85652-103"><xref:System.Xml?displayProperty=nameWithType> Przestrzeń nazw zapewnia programowy reprezentację dokumenty XML, fragmenty, węzły lub zestaw węzłów w pamięci, za pomocą <xref:System.Xml.XmlDocument> lub <xref:System.Xml.XPath.XPathDocument> klasy.</span><span class="sxs-lookup"><span data-stu-id="85652-103">The <xref:System.Xml?displayProperty=nameWithType> namespace provides a programmatic representation of XML documents, fragments, nodes, or node-sets in-memory, using the <xref:System.Xml.XmlDocument> or <xref:System.Xml.XPath.XPathDocument> classes.</span></span>  
  
 <span data-ttu-id="85652-104"><xref:System.Xml.XPath.XPathDocument> Klasa udostępnia reprezentację dokumentu XML za pomocą wyrażenia XPath modelu danych, szybka i tylko do odczytu w pamięci.</span><span class="sxs-lookup"><span data-stu-id="85652-104">The <xref:System.Xml.XPath.XPathDocument> class provides a fast, read-only, in-memory representation of an XML document using the XPath data model.</span></span> <span data-ttu-id="85652-105"><xref:System.Xml.XmlDocument> Klasa udostępnia można edytować w pamięci reprezentację w postaci dokumentu XML wykonania W3C modelu DOM (Document Object) poziom 1 Core i Core DOM poziomu 2.</span><span class="sxs-lookup"><span data-stu-id="85652-105">The <xref:System.Xml.XmlDocument> class provides an editable in-memory representation of an XML document implementing W3C Document Object Model (DOM) Level 1 Core and Core DOM Level 2.</span></span> <span data-ttu-id="85652-106">Zarówno klasy implementować <xref:System.Xml.XPath.IXPathNavigable> interfejsu i zwracać <xref:System.Xml.XPath.XPathNavigator> obiekt używany do wybierz oceny, przejdź, a w niektórych przypadkach edytowanie danych XML.</span><span class="sxs-lookup"><span data-stu-id="85652-106">Both classes implement the <xref:System.Xml.XPath.IXPathNavigable> interface and return an <xref:System.Xml.XPath.XPathNavigator> object used to select, evaluate, navigate, and in some cases, edit the underlying XML data.</span></span>  
  
 <span data-ttu-id="85652-107">W poniższych sekcjach opisano funkcje <xref:System.Xml.XPath.XPathNavigator> klasy oparte na klasie zwraca go.</span><span class="sxs-lookup"><span data-stu-id="85652-107">The following sections describe the functionality of the <xref:System.Xml.XPath.XPathNavigator> class based on the class that returns it.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="85652-108">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="85652-108">In This Section</span></span>  
 [<span data-ttu-id="85652-109">Odczytywanie danych XML przy użyciu XPathDocument i XmlDocument</span><span class="sxs-lookup"><span data-stu-id="85652-109">Reading XML Data using XPathDocument and XmlDocument</span></span>](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md)  
 <span data-ttu-id="85652-110">Opisuje sposób tworzenia tylko do odczytu <xref:System.Xml.XPath.XPathDocument> obiektu klasy do odczytu dokumentu XML oraz sposobu tworzenia, edycji <xref:System.Xml.XmlDocument> obiektu klasy do odczytu i edycji dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="85652-110">Describes how to create a read-only <xref:System.Xml.XPath.XPathDocument> class object to read an XML document and how to create an editable <xref:System.Xml.XmlDocument> class object to read and edit an XML document.</span></span> <span data-ttu-id="85652-111">W tym temacie opisano sposób zwracany <xref:System.Xml.XPath.XPathNavigator> obiektu z każdej klasy do nawigowania i edytować dokument XML.</span><span class="sxs-lookup"><span data-stu-id="85652-111">This topic also describes how return an <xref:System.Xml.XPath.XPathNavigator> object from each class to navigate and edit an XML document.</span></span>  
  
 [<span data-ttu-id="85652-112">Wybieranie, Evaluating i dopasowywania danych XML przy użyciu parametrem XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="85652-112">Selecting, Evaluating and Matching XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="85652-113">Opisuje metody <xref:System.Xml.XPath.XPathNavigator> klasa używana do wybierania węzłów w <xref:System.Xml.XPath.XPathDocument> lub <xref:System.Xml.XmlDocument> przy użyciu zapytania XPath, oceny i przejrzeć wyniki wyrażenia XPath i ustalić, czy węzeł w dokumencie XML zgodne danego języka XPath wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="85652-113">Describes the methods of the <xref:System.Xml.XPath.XPathNavigator> class used to select nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using an XPath query, evaluate and examine the results of an XPath expression, and determine if a node in an XML document matches a given XPath expression.</span></span>  
  
 [<span data-ttu-id="85652-114">Uzyskiwanie dostępu do danych XML przy użyciu parametrem XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="85652-114">Accessing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="85652-115">Opisuje metody <xref:System.Xml.XPath.XPathNavigator> klasa używana do nawigowania węzłów, wyodrębnić dane XML i dostępu jednoznacznie danych XML w <xref:System.Xml.XPath.XPathDocument> lub <xref:System.Xml.XmlDocument> obiektu.</span><span class="sxs-lookup"><span data-stu-id="85652-115">Describes the methods of the <xref:System.Xml.XPath.XPathNavigator> class used to navigate nodes, extract XML data and access strongly typed XML data in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object.</span></span>  
  
 [<span data-ttu-id="85652-116">Edytowanie danych XML przy użyciu parametrem XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="85652-116">Editing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/editing-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="85652-117">Opisuje metody <xref:System.Xml.XPath.XPathNavigator> klasa służy do wstawiania, modyfikowania i usuwania węzłów i wartości z dokumentu XML zawartych w <xref:System.Xml.XmlDocument> obiektu.</span><span class="sxs-lookup"><span data-stu-id="85652-117">Describes the methods of the <xref:System.Xml.XPath.XPathNavigator> class used to insert, modify and remove nodes and values from an XML document contained in an <xref:System.Xml.XmlDocument> object.</span></span>  
  
 [<span data-ttu-id="85652-118">Weryfikacja schematu za pomocą parametrem XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="85652-118">Schema Validation using XPathNavigator</span></span>](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md)  
 <span data-ttu-id="85652-119">Zawiera opis sposobów sprawdzania poprawności zawartości XML zawartych w <xref:System.Xml.XPath.XPathDocument> lub <xref:System.Xml.XmlDocument> obiektu.</span><span class="sxs-lookup"><span data-stu-id="85652-119">Describes the ways to validate the XML content contained in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85652-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="85652-120">See Also</span></span>  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [<span data-ttu-id="85652-121">Przetwarzania danych XML przy użyciu modelu DOM</span><span class="sxs-lookup"><span data-stu-id="85652-121">Process XML Data Using the DOM Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-dom-model.md)
