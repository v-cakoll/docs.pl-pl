---
title: "Przekształcenia XSLT przy użyciu klasy XslTransform"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 500335af-f9b5-413b-968a-e6d9a824478c
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 619e37ab63735ea77d3afb0d94f284b2f310efc2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="xslt-transformations-with-the-xsltransform-class"></a><span data-ttu-id="7b1ca-102">Przekształcenia XSLT przy użyciu klasy XslTransform</span><span class="sxs-lookup"><span data-stu-id="7b1ca-102">XSLT Transformations with the XslTransform Class</span></span>
> [!NOTE]
>  <span data-ttu-id="7b1ca-103"><xref:System.Xml.Xsl.XslTransform> Klasa jest przestarzała w [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7b1ca-103">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span> <span data-ttu-id="7b1ca-104">Może wykonywać rozszerzalny język arkusza stylów dla transformacji przekształcenia XSLT () przy użyciu <xref:System.Xml.Xsl.XslCompiledTransform> klasy.</span><span class="sxs-lookup"><span data-stu-id="7b1ca-104">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="7b1ca-105">Zobacz [za pomocą klasy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) i [migracji z klasy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) Aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="7b1ca-105">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="7b1ca-106">Celem XSLT jest przekształcenie zawartości dokumentu XML źródła do innego dokumentu, która różni się w formacie lub struktury (na przykład: Przekształcanie XML w kodzie HTML do użytku w witrynie sieci Web lub przekształcać je do dokumentu, który zawiera tylko b wymagane pola Aplikacja y).</span><span class="sxs-lookup"><span data-stu-id="7b1ca-106">The goal of the XSLT is to transform the content of a source XML document into another document that is different in format or structure (for example, to transform XML into HTML for use on a Web site or to transform it into a document that contains only the fields required by an application).</span></span> <span data-ttu-id="7b1ca-107">Ten proces transformacji jest określona przez znajdujący się w www.w3.org/TR/xslt zalecenia w wersji 1.0 XSLT sieci World Wide Web konsorcjum W3C.</span><span class="sxs-lookup"><span data-stu-id="7b1ca-107">This transformation process is specified by the World Wide Web Consortium (W3C) XSLT version 1.0 recommendation located at www.w3.org/TR/xslt.</span></span> <span data-ttu-id="7b1ca-108">W [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], <xref:System.Xml.Xsl.XslTransform> znaleziono w klasy <xref:System.Xml.Xsl> przestrzeni nazw jest procesorze XSLT, która implementuje funkcje w tej specyfikacji.</span><span class="sxs-lookup"><span data-stu-id="7b1ca-108">In the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], the <xref:System.Xml.Xsl.XslTransform> class, found in the <xref:System.Xml.Xsl> namespace, is the XSLT processor that implements the functionality of this specification.</span></span> <span data-ttu-id="7b1ca-109">Mała liczba funkcji, które nie zostały wdrożone z zalecenia W3C XSLT 1.0, na liście [dane wyjściowe z XslTransform](../../../../docs/standard/data/xml/outputs-from-an-xsltransform.md).</span><span class="sxs-lookup"><span data-stu-id="7b1ca-109">There are a small number of features that have not been implemented from the W3C XSLT 1.0 recommendation, listed in [Outputs from an XslTransform](../../../../docs/standard/data/xml/outputs-from-an-xsltransform.md).</span></span> <span data-ttu-id="7b1ca-110">Na poniższej ilustracji przedstawiono architekturę przekształcania [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7b1ca-110">The following figure shows the transformation architecture of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].</span></span>  
  
## <a name="overview"></a><span data-ttu-id="7b1ca-111">Omówienie</span><span class="sxs-lookup"><span data-stu-id="7b1ca-111">Overview</span></span>  
 <span data-ttu-id="7b1ca-112">![Architektura przekształcenia XSLT](../../../../docs/standard/data/xml/media/xslttransformationswithxsltransformclass.gif "xsltTransformationsWithXslTransformClass")</span><span class="sxs-lookup"><span data-stu-id="7b1ca-112">![XSLT Transformation Architecture](../../../../docs/standard/data/xml/media/xslttransformationswithxsltransformclass.gif "xsltTransformationsWithXslTransformClass")</span></span>  
<span data-ttu-id="7b1ca-113">Architektura przekształcenia</span><span class="sxs-lookup"><span data-stu-id="7b1ca-113">Transformation Architecture</span></span>  
  
 <span data-ttu-id="7b1ca-114">Zalecenie XSLT używa XML Path Language (XPath), aby wybrać części dokumentu XML, gdy wyrażenie XPath jest język kwerendy służące do nawigacji węzłów w drzewie dokumentu.</span><span class="sxs-lookup"><span data-stu-id="7b1ca-114">The XSLT recommendation uses XML Path Language (XPath) to select parts of an XML document, where XPath is a query language used to navigate nodes of a document tree.</span></span> <span data-ttu-id="7b1ca-115">Jak pokazano na diagramie [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] implementacji XPath jest używana do wybierania części XML przechowywane w kilka klas, takich jak <xref:System.Xml.XmlDocument>, <xref:System.Xml.XmlDataDocument>i <xref:System.Xml.XPath.XPathDocument>.</span><span class="sxs-lookup"><span data-stu-id="7b1ca-115">As shown in the diagram, the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] implementation of XPath is used to select parts of XML stored in several classes, such as an <xref:System.Xml.XmlDocument>, an <xref:System.Xml.XmlDataDocument>, and an <xref:System.Xml.XPath.XPathDocument>.</span></span> <span data-ttu-id="7b1ca-116"><xref:System.Xml.XPath.XPathDocument> Jest zoptymalizowany XSLT magazynu danych, a w przypadku użycia z <xref:System.Xml.Xsl.XslTransform>, zapewnia przekształceń XSLT z dobrą wydajność.</span><span class="sxs-lookup"><span data-stu-id="7b1ca-116">An <xref:System.Xml.XPath.XPathDocument> is an optimized XSLT data store, and when used with <xref:System.Xml.Xsl.XslTransform>, it provides XSLT transformations with good performance.</span></span>  
  
 <span data-ttu-id="7b1ca-117">Podczas pracy z poniższej listy tabeli często używa klas <xref:System.Xml.Xsl.XslTransform> i XPath i ich funkcji.</span><span class="sxs-lookup"><span data-stu-id="7b1ca-117">The following table list commonly uses classes when working with <xref:System.Xml.Xsl.XslTransform> and XPath and their function.</span></span>  
  
|<span data-ttu-id="7b1ca-118">Klasy lub interfejsu</span><span class="sxs-lookup"><span data-stu-id="7b1ca-118">Class or Interface</span></span>|<span data-ttu-id="7b1ca-119">Funkcja</span><span class="sxs-lookup"><span data-stu-id="7b1ca-119">Function</span></span>|  
|------------------------|--------------|  
|<xref:System.Xml.XPath.XPathNavigator>|<span data-ttu-id="7b1ca-120">To interfejs API, który udostępnia model styl kursora nawigacji w sklepie, wraz z możliwością kwerendy XPath.</span><span class="sxs-lookup"><span data-stu-id="7b1ca-120">It is an API that provides a cursor style model for navigating over a store, along with XPath query support.</span></span> <span data-ttu-id="7b1ca-121">Nie zapewnia edytowanie odpowiedni magazyn.</span><span class="sxs-lookup"><span data-stu-id="7b1ca-121">It does not provide editing of the underlying store.</span></span> <span data-ttu-id="7b1ca-122">Do edycji, użyj <xref:System.Xml.XmlDocument> klasy.</span><span class="sxs-lookup"><span data-stu-id="7b1ca-122">For editing, use the <xref:System.Xml.XmlDocument> class.</span></span>|  
|<xref:System.Xml.XPath.IXPathNavigable>|<span data-ttu-id="7b1ca-123">Jest to interfejs zapewniający `CreateNavigator` metody <xref:System.Xml.XPath.XPathNavigator> magazynu.</span><span class="sxs-lookup"><span data-stu-id="7b1ca-123">It is an interface that provides a `CreateNavigator` method to an <xref:System.Xml.XPath.XPathNavigator> for the store.</span></span>|  
|<xref:System.Xml.XmlDocument>|<span data-ttu-id="7b1ca-124">Umożliwia edytowanie tego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="7b1ca-124">It enables editing of this document.</span></span> <span data-ttu-id="7b1ca-125">Implementuje <xref:System.Xml.XPath.IXPathNavigable>, umożliwiając scenariusze edycji dokumentu, gdzie są następnie wymagane przekształcenia XSLT.</span><span class="sxs-lookup"><span data-stu-id="7b1ca-125">It implements <xref:System.Xml.XPath.IXPathNavigable>, allowing document-editing scenarios where XSLT transformations are subsequently required.</span></span> <span data-ttu-id="7b1ca-126">Aby uzyskać więcej informacji, zobacz [dane wejściowe XmlDocument XslTransform](../../../../docs/standard/data/xml/xmldocument-input-to-xsltransform.md).</span><span class="sxs-lookup"><span data-stu-id="7b1ca-126">For more information, see [XmlDocument Input to XslTransform](../../../../docs/standard/data/xml/xmldocument-input-to-xsltransform.md).</span></span>|  
|<xref:System.Xml.XmlDataDocument>|<span data-ttu-id="7b1ca-127">Jest pochodną <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="7b1ca-127">It is derived from the <xref:System.Xml.XmlDocument>.</span></span> <span data-ttu-id="7b1ca-128">Tworzy ono relacyjnych i względem XML przy użyciu <xref:System.Data.DataSet> w celu zoptymalizowania magazynu danych strukturalnych w dokumencie XML zgodnie z określonym mapowania na <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="7b1ca-128">It bridges the relational and XML worlds by using a <xref:System.Data.DataSet> to optimize storage of structured data within the XML document according to specified mappings on the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="7b1ca-129">Implementuje <xref:System.Xml.XPath.IXPathNavigable>, dzięki czemu scenariuszy, w którym przekształcenia XSLT mogą być wykonywane za pośrednictwem relacyjne dane pobrane z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="7b1ca-129">It implements <xref:System.Xml.XPath.IXPathNavigable>, allowing scenarios where XSLT transformations can be performed over relational data retrieved from a database.</span></span> <span data-ttu-id="7b1ca-130">Aby uzyskać więcej informacji, zobacz [XML integracji z danych relacyjnych i ADO.NET](../../../../docs/standard/data/xml/xml-integration-with-relational-data-and-adonet.md).</span><span class="sxs-lookup"><span data-stu-id="7b1ca-130">For more information, see [XML Integration with Relational Data and ADO.NET](../../../../docs/standard/data/xml/xml-integration-with-relational-data-and-adonet.md).</span></span>|  
|<xref:System.Xml.XPath.XPathDocument>|<span data-ttu-id="7b1ca-131">Ta klasa jest zoptymalizowana pod kątem <xref:System.Xml.Xsl.XslTransform> przetwarzania i kwerendy XPath i udostępnia pamięć podręczną tylko do odczytu o wysokiej wydajności.</span><span class="sxs-lookup"><span data-stu-id="7b1ca-131">This class is optimized for <xref:System.Xml.Xsl.XslTransform> processing and XPath queries, and it provides a read-only high performance cache.</span></span> <span data-ttu-id="7b1ca-132">Implementuje <xref:System.Xml.XPath.IXPathNavigable> i preferowany magazynu do użycia na potrzeby przekształcenia XSLT.</span><span class="sxs-lookup"><span data-stu-id="7b1ca-132">It implements <xref:System.Xml.XPath.IXPathNavigable> and is the preferred store to use for XSLT transformations.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeIterator>|<span data-ttu-id="7b1ca-133">Zapewnia on nawigacji przez zestaw węzłów XPath.</span><span class="sxs-lookup"><span data-stu-id="7b1ca-133">It provides navigation over XPath node sets.</span></span> <span data-ttu-id="7b1ca-134">Wszystkie metody wyboru XPath na <xref:System.Xml.XPath.XPathNavigator> zwracać <xref:System.Xml.XPath.XPathNodeIterator>.</span><span class="sxs-lookup"><span data-stu-id="7b1ca-134">All XPath selection methods on the <xref:System.Xml.XPath.XPathNavigator> return an <xref:System.Xml.XPath.XPathNodeIterator>.</span></span> <span data-ttu-id="7b1ca-135">Wiele <xref:System.Xml.XPath.XPathNodeIterator> obiekty mogą być tworzone w tym samym magazynie reprezentujący wybranego zestawu węzłów.</span><span class="sxs-lookup"><span data-stu-id="7b1ca-135">Multiple <xref:System.Xml.XPath.XPathNodeIterator> objects can be created over the same store, each representing a selected set of nodes.</span></span>|  
  
## <a name="msxml-xslt-extensions"></a><span data-ttu-id="7b1ca-136">Rozszerzenia programu MSXML XSLT</span><span class="sxs-lookup"><span data-stu-id="7b1ca-136">MSXML XSLT Extensions</span></span>  
 <span data-ttu-id="7b1ca-137">`msxsl:script` i `msxsl:node-set` funkcje są tylko rozszerzenia XSLT Microsoft XML Core Services (MSXML) obsługiwany przez <xref:System.Xml.Xsl.XslTransform> klasy.</span><span class="sxs-lookup"><span data-stu-id="7b1ca-137">The `msxsl:script` and `msxsl:node-set` functions are the only Microsoft XML Core Services (MSXML) XSLT extensions supported by the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7b1ca-138">Przykład</span><span class="sxs-lookup"><span data-stu-id="7b1ca-138">Example</span></span>  
 <span data-ttu-id="7b1ca-139">Poniższy przykład kodu ładuje arkusz stylów XSLT odczytuje plik o nazwie mojedane.XML do <xref:System.Xml.XPath.XPathDocument>i wykonuje transformację danych w fikcyjnej plik o nazwie myStyleSheet.xsl wysyłania sformatowane dane wyjściowe do konsoli.</span><span class="sxs-lookup"><span data-stu-id="7b1ca-139">The following code example loads an XSLT style sheet, reads a file called mydata.xml into an <xref:System.Xml.XPath.XPathDocument>, and performs a transformation on the data on a fictitious file called myStyleSheet.xsl, sending the formatted output to the console.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports System.Xml.XPath  
Imports System.Xml.Xsl  
  
Public Class Sample  
    Private filename As [String] = "mydata.xml"  
    Private stylesheet As [String] = "myStyleSheet.xsl"  
  
    Public Shared Sub Main()  
        Dim xslt As New XslTransform()  
        xslt.Load(stylesheet)  
        Dim xpathdocument As New XPathDocument(filename)  
        Dim writer As New XmlTextWriter(Console.Out)  
        writer.Formatting = Formatting.Indented  
  
        xslt.Transform(xpathdocument, Nothing, writer, Nothing)  
    End Sub 'Main  
End Class 'Sample  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
using System.Xml.XPath;  
using System.Xml.Xsl;  
  
public class Sample   
{  
    private const String filename = "mydata.xml";  
    private const String stylesheet = "myStyleSheet.xsl";  
  
    public static void Main()   
    {  
    XslTransform xslt = new XslTransform();  
    xslt.Load(stylesheet);  
    XPathDocument xpathdocument = new  
    XPathDocument(filename);  
    XmlTextWriter writer = new XmlTextWriter(Console.Out);  
    writer.Formatting=Formatting.Indented;  
  
    xslt.Transform(xpathdocument, null, writer, null);      
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="7b1ca-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7b1ca-140">See Also</span></span>  
 <xref:System.Xml.Xsl.XslTransform>  
 [<span data-ttu-id="7b1ca-141">Klasa XslTransform implementuje procesorze XSLT</span><span class="sxs-lookup"><span data-stu-id="7b1ca-141">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)  
 [<span data-ttu-id="7b1ca-142">Implementacja DACL zachowania w klasie XslTransform</span><span class="sxs-lookup"><span data-stu-id="7b1ca-142">Implementation of Discretionary Behaviors in the XslTransform Class</span></span>](../../../../docs/standard/data/xml/implementation-of-discretionary-behaviors-in-the-xsltransform-class.md)  
 [<span data-ttu-id="7b1ca-143">Element XPathNavigator w przekształcenia</span><span class="sxs-lookup"><span data-stu-id="7b1ca-143">XPathNavigator in Transformations</span></span>](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)  
 [<span data-ttu-id="7b1ca-144">Element XPathNodeIterator w przekształcenia</span><span class="sxs-lookup"><span data-stu-id="7b1ca-144">XPathNodeIterator in Transformations</span></span>](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)  
 [<span data-ttu-id="7b1ca-145">Dane wejściowe XPathDocument XslTransform</span><span class="sxs-lookup"><span data-stu-id="7b1ca-145">XPathDocument Input to XslTransform</span></span>](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)  
 [<span data-ttu-id="7b1ca-146">Dane wejściowe dokumentu XmlDataDocument XslTransform</span><span class="sxs-lookup"><span data-stu-id="7b1ca-146">XmlDataDocument Input to XslTransform</span></span>](../../../../docs/standard/data/xml/xmldatadocument-input-to-xsltransform.md)  
 [<span data-ttu-id="7b1ca-147">Dane wejściowe XmlDocument XslTransform</span><span class="sxs-lookup"><span data-stu-id="7b1ca-147">XmlDocument Input to XslTransform</span></span>](../../../../docs/standard/data/xml/xmldocument-input-to-xsltransform.md)
