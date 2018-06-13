---
title: Przetwarzanie danych XML w pamięci
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1bbb4d05-ead7-4bda-8ece-f86d35c57ad4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 317021318153cc87b2eab3db508a9dede9dc05e3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33569645"
---
# <a name="processing-xml-data-in-memory"></a><span data-ttu-id="5f9d8-102">Przetwarzanie danych XML w pamięci</span><span class="sxs-lookup"><span data-stu-id="5f9d8-102">Processing XML Data In-Memory</span></span>
<span data-ttu-id="5f9d8-103">Microsoft .NET Framework obejmuje trzy modele przetwarzania danych XML: <xref:System.Xml.XmlDocument> klasy <xref:System.Xml.XPath.XPathDocument> klasy, a [LINQ do XML](https://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13).</span><span class="sxs-lookup"><span data-stu-id="5f9d8-103">The Microsoft .NET Framework includes three models for processing XML data: the <xref:System.Xml.XmlDocument> class, the <xref:System.Xml.XPath.XPathDocument> class, and [LINQ to XML](https://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13).</span></span>  
  
 <span data-ttu-id="5f9d8-104"><xref:System.Xml.XmlDocument> Klasa implementuje rdzeń poziom 1 W3C dokumentu obiektu modelu (DOM) oraz modelu DOM core poziomu 2 zalecenia.</span><span class="sxs-lookup"><span data-stu-id="5f9d8-104">The <xref:System.Xml.XmlDocument> class implements the W3C document object model (DOM) level 1 core and the core DOM level 2 recommendations.</span></span> <span data-ttu-id="5f9d8-105">Model DOM jest w pamięci (pamięć podręczna) drzewa reprezentację dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="5f9d8-105">The DOM is an in-memory (cache) tree representation of an XML document.</span></span> <span data-ttu-id="5f9d8-106">Z <xref:System.Xml.XmlDocument> oraz ich powiązanymi klasami, możesz utworzyć dokumentów XML, obciążenia i uzyskać dostęp do danych, modyfikować dane i zapisać zmiany.</span><span class="sxs-lookup"><span data-stu-id="5f9d8-106">With the <xref:System.Xml.XmlDocument> and its related classes, you can construct XML documents, load and access data, modify data, and save changes.</span></span>  
  
 <span data-ttu-id="5f9d8-107"><xref:System.Xml.XPath.XPathDocument> Klasy jest magazynem danych tylko do odczytu, w pamięci, który jest oparty na modelu danych XPath.</span><span class="sxs-lookup"><span data-stu-id="5f9d8-107">The <xref:System.Xml.XPath.XPathDocument> class is a read-only, in-memory data store that is based on the XPath data model.</span></span> <span data-ttu-id="5f9d8-108"><xref:System.Xml.XPath.XPathNavigator> Klasa zapewnia kilka opcji edycji i możliwości nawigacji przy użyciu modelu kursor nad dokumentów XML zawarte w tylko do odczytu <xref:System.Xml.XPath.XPathDocument> klasy, jak również <xref:System.Xml.XmlDocument> klasy.</span><span class="sxs-lookup"><span data-stu-id="5f9d8-108">The <xref:System.Xml.XPath.XPathNavigator> class offers several editing options and navigation capabilities using a cursor model over XML documents contained in the read-only <xref:System.Xml.XPath.XPathDocument> class as well as the <xref:System.Xml.XmlDocument> class.</span></span>  
  
 <span data-ttu-id="5f9d8-109">[LINQ do XML](https://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13) jest nowy model w programie .NET Framework w wersji 3.5 przetwarzania danych XML.</span><span class="sxs-lookup"><span data-stu-id="5f9d8-109">[LINQ to XML](https://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13) is the new model in the .NET Framework version 3.5 for processing XML data.</span></span> <span data-ttu-id="5f9d8-110">Jest modelu w pamięci, która wykorzystuje [LINQ (zapytania język Language-Integrated)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d).</span><span class="sxs-lookup"><span data-stu-id="5f9d8-110">It is an in-memory model that leverages [LINQ (Language-Integrated Query)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d).</span></span> <span data-ttu-id="5f9d8-111">LINQ rozszerza składnię języka C# i Visual Basic zapewnienie nowe możliwości zapytania.</span><span class="sxs-lookup"><span data-stu-id="5f9d8-111">LINQ extends the language syntax of C# and Visual Basic to provide new query capabilities.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5f9d8-112">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="5f9d8-112">In This Section</span></span>  
 [<span data-ttu-id="5f9d8-113">Przetwarzanie danych XML przy użyciu modelu DOM</span><span class="sxs-lookup"><span data-stu-id="5f9d8-113">Process XML Data Using the DOM Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-dom-model.md)  
 <span data-ttu-id="5f9d8-114">Omówienie korzystania z <xref:System.Xml.XmlDocument>oraz ich powiązanymi klasami do przetworzenia danych XML.</span><span class="sxs-lookup"><span data-stu-id="5f9d8-114">Discusses using the <xref:System.Xml.XmlDocument>, and its related classes to process XML data.</span></span>  
  
 [<span data-ttu-id="5f9d8-115">Przetwarzanie danych XML przy użyciu modelu danych XPath</span><span class="sxs-lookup"><span data-stu-id="5f9d8-115">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 <span data-ttu-id="5f9d8-116">Omówienie korzystania z <xref:System.Xml.XPath.XPathDocument>, <xref:System.Xml.XmlDocument>, i <xref:System.Xml.XPath.XPathNavigator> klasy do przetwarzania danych XML.</span><span class="sxs-lookup"><span data-stu-id="5f9d8-116">Discusses using the <xref:System.Xml.XPath.XPathDocument>, <xref:System.Xml.XmlDocument>, and <xref:System.Xml.XPath.XPathNavigator> classes to process XML data.</span></span>  
  
 [<span data-ttu-id="5f9d8-117">Przetwarzanie danych XML przy użyciu modelu LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="5f9d8-117">Process XML Data Using LINQ to XML</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-linq-to-xml.md)  
 <span data-ttu-id="5f9d8-118">Zawiera krótki przegląd LINQ do XML i łącza do LINQ do dokumentacji XML.</span><span class="sxs-lookup"><span data-stu-id="5f9d8-118">Provides a brief overview of LINQ to XML and provides links to the LINQ to XML documentation.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="5f9d8-119">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="5f9d8-119">Related Sections</span></span>  
 [<span data-ttu-id="5f9d8-120">Dokumenty i dane XML</span><span class="sxs-lookup"><span data-stu-id="5f9d8-120">XML Documents and Data</span></span>](../../../../docs/standard/data/xml/index.md)
