---
title: "Przetwarzanie danych XML w pamięci"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1bbb4d05-ead7-4bda-8ece-f86d35c57ad4
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ec4ccbff095071b279e07cee6a1aab3ca830423f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="processing-xml-data-in-memory"></a><span data-ttu-id="0b27d-102">Przetwarzanie danych XML w pamięci</span><span class="sxs-lookup"><span data-stu-id="0b27d-102">Processing XML Data In-Memory</span></span>
<span data-ttu-id="0b27d-103">Microsoft .NET Framework obejmuje trzy modele przetwarzania danych XML: <xref:System.Xml.XmlDocument> klasy <xref:System.Xml.XPath.XPathDocument> klasy, a [LINQ do XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13).</span><span class="sxs-lookup"><span data-stu-id="0b27d-103">The Microsoft .NET Framework includes three models for processing XML data: the <xref:System.Xml.XmlDocument> class, the <xref:System.Xml.XPath.XPathDocument> class, and [LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13).</span></span>  
  
 <span data-ttu-id="0b27d-104"><xref:System.Xml.XmlDocument> Klasa implementuje rdzeń poziom 1 W3C dokumentu obiektu modelu (DOM) oraz modelu DOM core poziomu 2 zalecenia.</span><span class="sxs-lookup"><span data-stu-id="0b27d-104">The <xref:System.Xml.XmlDocument> class implements the W3C document object model (DOM) level 1 core and the core DOM level 2 recommendations.</span></span> <span data-ttu-id="0b27d-105">Model DOM jest w pamięci (pamięć podręczna) drzewa reprezentację dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="0b27d-105">The DOM is an in-memory (cache) tree representation of an XML document.</span></span> <span data-ttu-id="0b27d-106">Z <xref:System.Xml.XmlDocument> oraz ich powiązanymi klasami, możesz utworzyć dokumentów XML, obciążenia i uzyskać dostęp do danych, modyfikować dane i zapisać zmiany.</span><span class="sxs-lookup"><span data-stu-id="0b27d-106">With the <xref:System.Xml.XmlDocument> and its related classes, you can construct XML documents, load and access data, modify data, and save changes.</span></span>  
  
 <span data-ttu-id="0b27d-107"><xref:System.Xml.XPath.XPathDocument> Klasy jest magazynem danych tylko do odczytu, w pamięci, który jest oparty na modelu danych XPath.</span><span class="sxs-lookup"><span data-stu-id="0b27d-107">The <xref:System.Xml.XPath.XPathDocument> class is a read-only, in-memory data store that is based on the XPath data model.</span></span> <span data-ttu-id="0b27d-108"><xref:System.Xml.XPath.XPathNavigator> Klasa zapewnia kilka opcji edycji i możliwości nawigacji przy użyciu modelu kursor nad dokumentów XML zawarte w tylko do odczytu <xref:System.Xml.XPath.XPathDocument> klasy, jak również <xref:System.Xml.XmlDocument> klasy.</span><span class="sxs-lookup"><span data-stu-id="0b27d-108">The <xref:System.Xml.XPath.XPathNavigator> class offers several editing options and navigation capabilities using a cursor model over XML documents contained in the read-only <xref:System.Xml.XPath.XPathDocument> class as well as the <xref:System.Xml.XmlDocument> class.</span></span>  
  
 <span data-ttu-id="0b27d-109">[LINQ do XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13) jest nowy model w programie .NET Framework w wersji 3.5 przetwarzania danych XML.</span><span class="sxs-lookup"><span data-stu-id="0b27d-109">[LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13) is the new model in the .NET Framework version 3.5 for processing XML data.</span></span> <span data-ttu-id="0b27d-110">Jest modelu w pamięci, która wykorzystuje [LINQ (zapytania język Language-Integrated)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d).</span><span class="sxs-lookup"><span data-stu-id="0b27d-110">It is an in-memory model that leverages [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d).</span></span> <span data-ttu-id="0b27d-111">LINQ rozszerza składnię języka C# i Visual Basic zapewnienie nowe możliwości zapytania.</span><span class="sxs-lookup"><span data-stu-id="0b27d-111">LINQ extends the language syntax of C# and Visual Basic to provide new query capabilities.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0b27d-112">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="0b27d-112">In This Section</span></span>  
 [<span data-ttu-id="0b27d-113">Przetwarzania danych XML przy użyciu modelu DOM</span><span class="sxs-lookup"><span data-stu-id="0b27d-113">Process XML Data Using the DOM Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-dom-model.md)  
 <span data-ttu-id="0b27d-114">Omówienie korzystania z <xref:System.Xml.XmlDocument>oraz ich powiązanymi klasami do przetworzenia danych XML.</span><span class="sxs-lookup"><span data-stu-id="0b27d-114">Discusses using the <xref:System.Xml.XmlDocument>, and its related classes to process XML data.</span></span>  
  
 [<span data-ttu-id="0b27d-115">Przetwarzania danych XML przy użyciu modelu danych XPath</span><span class="sxs-lookup"><span data-stu-id="0b27d-115">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 <span data-ttu-id="0b27d-116">Omówienie korzystania z <xref:System.Xml.XPath.XPathDocument>, <xref:System.Xml.XmlDocument>, i <xref:System.Xml.XPath.XPathNavigator> klasy do przetwarzania danych XML.</span><span class="sxs-lookup"><span data-stu-id="0b27d-116">Discusses using the <xref:System.Xml.XPath.XPathDocument>, <xref:System.Xml.XmlDocument>, and <xref:System.Xml.XPath.XPathNavigator> classes to process XML data.</span></span>  
  
 [<span data-ttu-id="0b27d-117">Dane XML procesu za pomocą LINQ do XML</span><span class="sxs-lookup"><span data-stu-id="0b27d-117">Process XML Data Using LINQ to XML</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-linq-to-xml.md)  
 <span data-ttu-id="0b27d-118">Zawiera krótki przegląd LINQ do XML i łącza do LINQ do dokumentacji XML.</span><span class="sxs-lookup"><span data-stu-id="0b27d-118">Provides a brief overview of LINQ to XML and provides links to the LINQ to XML documentation.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="0b27d-119">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="0b27d-119">Related Sections</span></span>  
 [<span data-ttu-id="0b27d-120">Dokumenty XML i dane</span><span class="sxs-lookup"><span data-stu-id="0b27d-120">XML Documents and Data</span></span>](../../../../docs/standard/data/xml/index.md)
