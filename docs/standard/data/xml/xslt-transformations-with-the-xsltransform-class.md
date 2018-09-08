---
title: Przekształcenia XSLT przy użyciu klasy XslTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 500335af-f9b5-413b-968a-e6d9a824478c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 67062ab87182bcb42793cb166323020178ac1688
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44197304"
---
# <a name="xslt-transformations-with-the-xsltransform-class"></a><span data-ttu-id="9a3a1-102">Przekształcenia XSLT przy użyciu klasy XslTransform</span><span class="sxs-lookup"><span data-stu-id="9a3a1-102">XSLT Transformations with the XslTransform Class</span></span>

> [!NOTE]
> <span data-ttu-id="9a3a1-103"><xref:System.Xml.Xsl.XslTransform> Klasy jest przestarzała w [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9a3a1-103">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span> <span data-ttu-id="9a3a1-104">Można przeprowadzić rozszerzalny język arkusza stylów dla przekształceń przekształcenia (XSLT) przy użyciu <xref:System.Xml.Xsl.XslCompiledTransform> klasy.</span><span class="sxs-lookup"><span data-stu-id="9a3a1-104">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="9a3a1-105">Zobacz [używanie klasy XslCompiledTransform](using-the-xslcompiledtransform-class.md) i [Migrowanie z klasy XslTransform](migrating-from-the-xsltransform-class.md) Aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="9a3a1-105">See [Using the XslCompiledTransform Class](using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](migrating-from-the-xsltransform-class.md) for more information.</span></span>

<span data-ttu-id="9a3a1-106">Celem XSLT jest do przekształcania zawartości w dokumencie źródłowym XML do innego dokumentu, która różni się w formacie lub struktury (na przykład Przekształcanie kodu XML w kodzie HTML do użycia w witrynie sieci Web lub Przekształcanie dokumentu, który zawiera tylko b wymagane pola y aplikacji).</span><span class="sxs-lookup"><span data-stu-id="9a3a1-106">The goal of the XSLT is to transform the content of a source XML document into another document that is different in format or structure (for example, to transform XML into HTML for use on a Web site or to transform it into a document that contains only the fields required by an application).</span></span> <span data-ttu-id="9a3a1-107">Ten proces przekształcania określono przez konsorcjum World Wide Web (W3C)[XSLT w wersji 1.0 zalecenie](https://www.w3.org/TR/1999/REC-xslt-19991116).</span><span class="sxs-lookup"><span data-stu-id="9a3a1-107">This transformation process is specified by the World Wide Web Consortium (W3C)[XSLT version 1.0 recommendation](https://www.w3.org/TR/1999/REC-xslt-19991116).</span></span> <span data-ttu-id="9a3a1-108">W [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], <xref:System.Xml.Xsl.XslTransform> znaleziono w klasy <xref:System.Xml.Xsl> przestrzeni nazw jest procesora XSLT, który implementuje funkcje tej specyfikacji.</span><span class="sxs-lookup"><span data-stu-id="9a3a1-108">In the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], the <xref:System.Xml.Xsl.XslTransform> class, found in the <xref:System.Xml.Xsl> namespace, is the XSLT processor that implements the functionality of this specification.</span></span> <span data-ttu-id="9a3a1-109">Istnieje kilka małych funkcji, które nie zostały wdrożone z zaleceniem W3C specyfikacji XSLT 1.0, na liście [dane wyjściowe z klasy XslTransform](outputs-from-an-xsltransform.md).</span><span class="sxs-lookup"><span data-stu-id="9a3a1-109">There are a small number of features that have not been implemented from the W3C XSLT 1.0 recommendation, listed in [Outputs from an XslTransform](outputs-from-an-xsltransform.md).</span></span> <span data-ttu-id="9a3a1-110">Na poniższej ilustracji przedstawiono architekturę przekształcania [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9a3a1-110">The following figure shows the transformation architecture of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].</span></span>

## <a name="overview"></a><span data-ttu-id="9a3a1-111">Omówienie</span><span class="sxs-lookup"><span data-stu-id="9a3a1-111">Overview</span></span>

<span data-ttu-id="9a3a1-112">![Architektura przekształcenia XSLT](media/xslttransformationswithxsltransformclass.gif "xsltTransformationsWithXslTransformClass")</span><span class="sxs-lookup"><span data-stu-id="9a3a1-112">![XSLT Transformation Architecture](media/xslttransformationswithxsltransformclass.gif "xsltTransformationsWithXslTransformClass")</span></span>  
<span data-ttu-id="9a3a1-113">Architektura przekształcenia</span><span class="sxs-lookup"><span data-stu-id="9a3a1-113">Transformation Architecture</span></span>

<span data-ttu-id="9a3a1-114">Zalecenie XSLT używa XML Path Language (XPath), aby wybrać części dokumentu XML, gdy wyrażenie XPath jest język zapytań, używany do przechodzenia węzłów w drzewie dokumentu.</span><span class="sxs-lookup"><span data-stu-id="9a3a1-114">The XSLT recommendation uses XML Path Language (XPath) to select parts of an XML document, where XPath is a query language used to navigate nodes of a document tree.</span></span> <span data-ttu-id="9a3a1-115">Jak pokazano na diagramie, [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] implementacja XPath jest używana do wybierania części XML przechowywane w kilka klas, takie jak <xref:System.Xml.XmlDocument>, <xref:System.Xml.XmlDataDocument>i <xref:System.Xml.XPath.XPathDocument>.</span><span class="sxs-lookup"><span data-stu-id="9a3a1-115">As shown in the diagram, the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] implementation of XPath is used to select parts of XML stored in several classes, such as an <xref:System.Xml.XmlDocument>, an <xref:System.Xml.XmlDataDocument>, and an <xref:System.Xml.XPath.XPathDocument>.</span></span> <span data-ttu-id="9a3a1-116"><xref:System.Xml.XPath.XPathDocument> Jest magazynem danych zoptymalizowanych XSLT i gdy jest używane z <xref:System.Xml.Xsl.XslTransform>, zapewnia przekształcenia XSLT przy użyciu dobrą wydajność.</span><span class="sxs-lookup"><span data-stu-id="9a3a1-116">An <xref:System.Xml.XPath.XPathDocument> is an optimized XSLT data store, and when used with <xref:System.Xml.Xsl.XslTransform>, it provides XSLT transformations with good performance.</span></span>

<span data-ttu-id="9a3a1-117">Podczas pracy z poniższej listy tabel często używa klas <xref:System.Xml.Xsl.XslTransform> i XPath i ich funkcji.</span><span class="sxs-lookup"><span data-stu-id="9a3a1-117">The following table list commonly uses classes when working with <xref:System.Xml.Xsl.XslTransform> and XPath and their function.</span></span>

|<span data-ttu-id="9a3a1-118">Klasy lub interfejsu</span><span class="sxs-lookup"><span data-stu-id="9a3a1-118">Class or Interface</span></span>|<span data-ttu-id="9a3a1-119">Funkcja</span><span class="sxs-lookup"><span data-stu-id="9a3a1-119">Function</span></span>|
|------------------------|--------------|
|<xref:System.Xml.XPath.XPathNavigator>|<span data-ttu-id="9a3a1-120">To interfejs API, który udostępnia model styl kursor do nawigowania w sklepie, wraz z pomocy technicznej kwerendy XPath.</span><span class="sxs-lookup"><span data-stu-id="9a3a1-120">It is an API that provides a cursor style model for navigating over a store, along with XPath query support.</span></span> <span data-ttu-id="9a3a1-121">Nie zapewnia edytowanie podstawowego magazynu.</span><span class="sxs-lookup"><span data-stu-id="9a3a1-121">It does not provide editing of the underlying store.</span></span> <span data-ttu-id="9a3a1-122">W przypadku edytowania, użyj <xref:System.Xml.XmlDocument> klasy.</span><span class="sxs-lookup"><span data-stu-id="9a3a1-122">For editing, use the <xref:System.Xml.XmlDocument> class.</span></span>|
|<xref:System.Xml.XPath.IXPathNavigable>|<span data-ttu-id="9a3a1-123">To interfejs, który udostępnia `CreateNavigator` metody <xref:System.Xml.XPath.XPathNavigator> dla magazynu.</span><span class="sxs-lookup"><span data-stu-id="9a3a1-123">It is an interface that provides a `CreateNavigator` method to an <xref:System.Xml.XPath.XPathNavigator> for the store.</span></span>|
|<xref:System.Xml.XmlDocument>|<span data-ttu-id="9a3a1-124">Umożliwia edytowanie tego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="9a3a1-124">It enables editing of this document.</span></span> <span data-ttu-id="9a3a1-125">Implementuje <xref:System.Xml.XPath.IXPathNavigable>, dzięki czemu scenariuszy edytowanie dokumentów, których następnie wymagane są przekształcenia XSLT.</span><span class="sxs-lookup"><span data-stu-id="9a3a1-125">It implements <xref:System.Xml.XPath.IXPathNavigable>, allowing document-editing scenarios where XSLT transformations are subsequently required.</span></span> <span data-ttu-id="9a3a1-126">Aby uzyskać więcej informacji, zobacz [dane wejściowe obiektu XmlDocument klasy xsltransform](xmldocument-input-to-xsltransform.md).</span><span class="sxs-lookup"><span data-stu-id="9a3a1-126">For more information, see [XmlDocument Input to XslTransform](xmldocument-input-to-xsltransform.md).</span></span>|
|<xref:System.Xml.XmlDataDocument>|<span data-ttu-id="9a3a1-127">Jest pochodną <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="9a3a1-127">It is derived from the <xref:System.Xml.XmlDocument>.</span></span> <span data-ttu-id="9a3a1-128">Tworzy ono relacyjnej i cech XML przy użyciu <xref:System.Data.DataSet> do optymalizacji magazynowania ustrukturyzowanych danych w dokumencie XML, zgodnie z określonym mapowania na <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="9a3a1-128">It bridges the relational and XML worlds by using a <xref:System.Data.DataSet> to optimize storage of structured data within the XML document according to specified mappings on the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="9a3a1-129">Implementuje <xref:System.Xml.XPath.IXPathNavigable>, dzięki czemu scenariuszy, w którym przekształcenia XSLT mogą być wykonywane na danych relacyjnych, pobierane z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="9a3a1-129">It implements <xref:System.Xml.XPath.IXPathNavigable>, allowing scenarios where XSLT transformations can be performed over relational data retrieved from a database.</span></span> <span data-ttu-id="9a3a1-130">Aby uzyskać więcej informacji, zobacz [Integracja XML z danymi relacyjnymi i ADO.NET](xml-integration-with-relational-data-and-adonet.md).</span><span class="sxs-lookup"><span data-stu-id="9a3a1-130">For more information, see [XML Integration with Relational Data and ADO.NET](xml-integration-with-relational-data-and-adonet.md).</span></span>|
|<xref:System.Xml.XPath.XPathDocument>|<span data-ttu-id="9a3a1-131">Ta klasa jest zoptymalizowana pod kątem <xref:System.Xml.Xsl.XslTransform> przetwarzania i zapytań XPath i oferuje pamięć podręczną tylko do odczytu o wysokiej wydajności.</span><span class="sxs-lookup"><span data-stu-id="9a3a1-131">This class is optimized for <xref:System.Xml.Xsl.XslTransform> processing and XPath queries, and it provides a read-only high performance cache.</span></span> <span data-ttu-id="9a3a1-132">Implementuje <xref:System.Xml.XPath.IXPathNavigable> i jest to preferowany magazyn na potrzeby przekształceń XSLT.</span><span class="sxs-lookup"><span data-stu-id="9a3a1-132">It implements <xref:System.Xml.XPath.IXPathNavigable> and is the preferred store to use for XSLT transformations.</span></span>|
|<xref:System.Xml.XPath.XPathNodeIterator>|<span data-ttu-id="9a3a1-133">Zapewnia on nawigacji przez zestawy węzła XPath.</span><span class="sxs-lookup"><span data-stu-id="9a3a1-133">It provides navigation over XPath node sets.</span></span> <span data-ttu-id="9a3a1-134">Wszystkie metody wyboru XPath w <xref:System.Xml.XPath.XPathNavigator> zwracają <xref:System.Xml.XPath.XPathNodeIterator>.</span><span class="sxs-lookup"><span data-stu-id="9a3a1-134">All XPath selection methods on the <xref:System.Xml.XPath.XPathNavigator> return an <xref:System.Xml.XPath.XPathNodeIterator>.</span></span> <span data-ttu-id="9a3a1-135">Wiele <xref:System.Xml.XPath.XPathNodeIterator> obiekty mogą być tworzone za pośrednictwem tego samego magazynu, reprezentujący wybrany zestaw węzłów.</span><span class="sxs-lookup"><span data-stu-id="9a3a1-135">Multiple <xref:System.Xml.XPath.XPathNodeIterator> objects can be created over the same store, each representing a selected set of nodes.</span></span>|

## <a name="msxml-xslt-extensions"></a><span data-ttu-id="9a3a1-136">Rozszerzenia programu MSXML XSLT</span><span class="sxs-lookup"><span data-stu-id="9a3a1-136">MSXML XSLT Extensions</span></span>

<span data-ttu-id="9a3a1-137">`msxsl:script` i `msxsl:node-set` funkcje są tylko rozszerzenia XSLT Microsoft XML Core Services (MSXML), obsługiwane przez <xref:System.Xml.Xsl.XslTransform> klasy.</span><span class="sxs-lookup"><span data-stu-id="9a3a1-137">The `msxsl:script` and `msxsl:node-set` functions are the only Microsoft XML Core Services (MSXML) XSLT extensions supported by the <xref:System.Xml.Xsl.XslTransform> class.</span></span>

## <a name="example"></a><span data-ttu-id="9a3a1-138">Przykład</span><span class="sxs-lookup"><span data-stu-id="9a3a1-138">Example</span></span>

<span data-ttu-id="9a3a1-139">Poniższy przykład kodu ładuje arkusz stylów XSLT odczytuje plik o nazwie mojedane.XML do <xref:System.Xml.XPath.XPathDocument>i wykonuje przekształcenie danych na fikcyjnej plik o nazwie myStyleSheet.xsl, wysyłając sformatowane dane wyjściowe do konsoli.</span><span class="sxs-lookup"><span data-stu-id="9a3a1-139">The following code example loads an XSLT style sheet, reads a file called mydata.xml into an <xref:System.Xml.XPath.XPathDocument>, and performs a transformation on the data on a fictitious file called myStyleSheet.xsl, sending the formatted output to the console.</span></span>

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
        XPathDocument xpathdocument = new XPathDocument(filename);
        XmlTextWriter writer = new XmlTextWriter(Console.Out);
        writer.Formatting = Formatting.Indented;

        xslt.Transform(xpathdocument, null, writer, null);
    }
}
```

## <a name="see-also"></a><span data-ttu-id="9a3a1-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9a3a1-140">See also</span></span>

- <xref:System.Xml.Xsl.XslTransform>  
- [<span data-ttu-id="9a3a1-141">Implementowanie procesora XSLT przy użyciu klasy XslTransform</span><span class="sxs-lookup"><span data-stu-id="9a3a1-141">XslTransform Class Implements the XSLT Processor</span></span>](xsltransform-class-implements-the-xslt-processor.md)  
- [<span data-ttu-id="9a3a1-142">Implementowanie zachowań uznaniowych w klasie XslTransform</span><span class="sxs-lookup"><span data-stu-id="9a3a1-142">Implementation of Discretionary Behaviors in the XslTransform Class</span></span>](implementation-of-discretionary-behaviors-in-the-xsltransform-class.md)  
- [<span data-ttu-id="9a3a1-143">Klasa XPathNavigator w przekształceniach</span><span class="sxs-lookup"><span data-stu-id="9a3a1-143">XPathNavigator in Transformations</span></span>](xpathnavigator-in-transformations.md)  
- [<span data-ttu-id="9a3a1-144">Klasa XPathNodeIterator w przekształceniach</span><span class="sxs-lookup"><span data-stu-id="9a3a1-144">XPathNodeIterator in Transformations</span></span>](xpathnodeiterator-in-transformations.md)  
- [<span data-ttu-id="9a3a1-145">Dane wejściowe obiektu XPathDocument klasy XslTransform</span><span class="sxs-lookup"><span data-stu-id="9a3a1-145">XPathDocument Input to XslTransform</span></span>](xpathdocument-input-to-xsltransform.md)  
- [<span data-ttu-id="9a3a1-146">Dane wejściowe obiektu XmlDataDocument klasy XslTransform</span><span class="sxs-lookup"><span data-stu-id="9a3a1-146">XmlDataDocument Input to XslTransform</span></span>](xmldatadocument-input-to-xsltransform.md)  
- [<span data-ttu-id="9a3a1-147">Dane wejściowe obiektu XmlDocument klasy XslTransform</span><span class="sxs-lookup"><span data-stu-id="9a3a1-147">XmlDocument Input to XslTransform</span></span>](xmldocument-input-to-xsltransform.md)  
