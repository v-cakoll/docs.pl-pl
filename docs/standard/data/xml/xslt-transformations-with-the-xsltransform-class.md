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
ms.openlocfilehash: ee35ce1016d9e0a825254fad4b08d4b94da16943
ms.sourcegitcommit: a8d3504f0eae1a40bda2b06bd441ba01f1631ef0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/18/2019
ms.locfileid: "67170953"
---
# <a name="xslt-transformations-with-the-xsltransform-class"></a><span data-ttu-id="5dbe9-102">Przekształcenia XSLT przy użyciu klasy XslTransform</span><span class="sxs-lookup"><span data-stu-id="5dbe9-102">XSLT Transformations with the XslTransform Class</span></span>

> [!NOTE]
> <span data-ttu-id="5dbe9-103"><xref:System.Xml.Xsl.XslTransform> Klasa jest przestarzała w programie .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="5dbe9-103">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the .NET Framework 2.0.</span></span> <span data-ttu-id="5dbe9-104">Można przeprowadzić rozszerzalny język arkusza stylów dla przekształceń przekształcenia (XSLT) przy użyciu <xref:System.Xml.Xsl.XslCompiledTransform> klasy.</span><span class="sxs-lookup"><span data-stu-id="5dbe9-104">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="5dbe9-105">Zobacz [używanie klasy XslCompiledTransform](using-the-xslcompiledtransform-class.md) i [Migrowanie z klasy XslTransform](migrating-from-the-xsltransform-class.md) Aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="5dbe9-105">See [Using the XslCompiledTransform Class](using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](migrating-from-the-xsltransform-class.md) for more information.</span></span>

<span data-ttu-id="5dbe9-106">Celem XSLT jest do przekształcania zawartości w dokumencie źródłowym XML do innego dokumentu, która różni się w formacie lub struktury (na przykład Przekształcanie kodu XML w kodzie HTML do użycia w witrynie sieci Web lub Przekształcanie dokumentu, który zawiera tylko b wymagane pola y aplikacji).</span><span class="sxs-lookup"><span data-stu-id="5dbe9-106">The goal of the XSLT is to transform the content of a source XML document into another document that is different in format or structure (for example, to transform XML into HTML for use on a Web site or to transform it into a document that contains only the fields required by an application).</span></span> <span data-ttu-id="5dbe9-107">Ten proces przekształcania określono przez konsorcjum World Wide Web (W3C)[XSLT w wersji 1.0 zalecenie](https://www.w3.org/TR/1999/REC-xslt-19991116).</span><span class="sxs-lookup"><span data-stu-id="5dbe9-107">This transformation process is specified by the World Wide Web Consortium (W3C)[XSLT version 1.0 recommendation](https://www.w3.org/TR/1999/REC-xslt-19991116).</span></span> <span data-ttu-id="5dbe9-108">W .NET Framework <xref:System.Xml.Xsl.XslTransform> znaleziono w klasy <xref:System.Xml.Xsl> przestrzeni nazw jest procesora XSLT, który implementuje funkcje tej specyfikacji.</span><span class="sxs-lookup"><span data-stu-id="5dbe9-108">In the .NET Framework, the <xref:System.Xml.Xsl.XslTransform> class, found in the <xref:System.Xml.Xsl> namespace, is the XSLT processor that implements the functionality of this specification.</span></span> <span data-ttu-id="5dbe9-109">Istnieje kilka małych funkcji, które nie zostały wdrożone z zaleceniem W3C specyfikacji XSLT 1.0, na liście [dane wyjściowe z klasy XslTransform](outputs-from-an-xsltransform.md).</span><span class="sxs-lookup"><span data-stu-id="5dbe9-109">There are a small number of features that have not been implemented from the W3C XSLT 1.0 recommendation, listed in [Outputs from an XslTransform](outputs-from-an-xsltransform.md).</span></span> <span data-ttu-id="5dbe9-110">Na poniższej ilustracji przedstawiono architekturę przekształcania programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5dbe9-110">The following figure shows the transformation architecture of the .NET Framework.</span></span>

## <a name="overview"></a><span data-ttu-id="5dbe9-111">Omówienie</span><span class="sxs-lookup"><span data-stu-id="5dbe9-111">Overview</span></span>

![Diagram przedstawiający architekturę transformację XSLT.](./media/xslt-transformations-with-the-xsltransform-class/xslt-transformation-architecture.gif) 

<span data-ttu-id="5dbe9-113">Zalecenie XSLT używa XML Path Language (XPath), aby wybrać części dokumentu XML, gdy wyrażenie XPath jest język zapytań, używany do przechodzenia węzłów w drzewie dokumentu.</span><span class="sxs-lookup"><span data-stu-id="5dbe9-113">The XSLT recommendation uses XML Path Language (XPath) to select parts of an XML document, where XPath is a query language used to navigate nodes of a document tree.</span></span> <span data-ttu-id="5dbe9-114">Jak pokazano na diagramie, wdrożenia programu .NET Framework, XPath jest używany do wybierania części XML przechowywane w kilka klas, takie jak <xref:System.Xml.XmlDocument>, <xref:System.Xml.XmlDataDocument>i <xref:System.Xml.XPath.XPathDocument>.</span><span class="sxs-lookup"><span data-stu-id="5dbe9-114">As shown in the diagram, the .NET Framework implementation of XPath is used to select parts of XML stored in several classes, such as an <xref:System.Xml.XmlDocument>, an <xref:System.Xml.XmlDataDocument>, and an <xref:System.Xml.XPath.XPathDocument>.</span></span> <span data-ttu-id="5dbe9-115"><xref:System.Xml.XPath.XPathDocument> Jest magazynem danych zoptymalizowanych XSLT i gdy jest używane z <xref:System.Xml.Xsl.XslTransform>, zapewnia przekształcenia XSLT przy użyciu dobrą wydajność.</span><span class="sxs-lookup"><span data-stu-id="5dbe9-115">An <xref:System.Xml.XPath.XPathDocument> is an optimized XSLT data store, and when used with <xref:System.Xml.Xsl.XslTransform>, it provides XSLT transformations with good performance.</span></span>

<span data-ttu-id="5dbe9-116">Podczas pracy z poniższej listy tabel często używa klas <xref:System.Xml.Xsl.XslTransform> i XPath i ich funkcji.</span><span class="sxs-lookup"><span data-stu-id="5dbe9-116">The following table list commonly uses classes when working with <xref:System.Xml.Xsl.XslTransform> and XPath and their function.</span></span>

|<span data-ttu-id="5dbe9-117">Klasy lub interfejsu</span><span class="sxs-lookup"><span data-stu-id="5dbe9-117">Class or Interface</span></span>|<span data-ttu-id="5dbe9-118">Funkcja</span><span class="sxs-lookup"><span data-stu-id="5dbe9-118">Function</span></span>|
|------------------------|--------------|
|<xref:System.Xml.XPath.XPathNavigator>|<span data-ttu-id="5dbe9-119">To interfejs API, który udostępnia model styl kursor do nawigowania w sklepie, wraz z pomocy technicznej kwerendy XPath.</span><span class="sxs-lookup"><span data-stu-id="5dbe9-119">It is an API that provides a cursor style model for navigating over a store, along with XPath query support.</span></span> <span data-ttu-id="5dbe9-120">Nie zapewnia edytowanie podstawowego magazynu.</span><span class="sxs-lookup"><span data-stu-id="5dbe9-120">It does not provide editing of the underlying store.</span></span> <span data-ttu-id="5dbe9-121">W przypadku edytowania, użyj <xref:System.Xml.XmlDocument> klasy.</span><span class="sxs-lookup"><span data-stu-id="5dbe9-121">For editing, use the <xref:System.Xml.XmlDocument> class.</span></span>|
|<xref:System.Xml.XPath.IXPathNavigable>|<span data-ttu-id="5dbe9-122">To interfejs, który udostępnia `CreateNavigator` metody <xref:System.Xml.XPath.XPathNavigator> dla magazynu.</span><span class="sxs-lookup"><span data-stu-id="5dbe9-122">It is an interface that provides a `CreateNavigator` method to an <xref:System.Xml.XPath.XPathNavigator> for the store.</span></span>|
|<xref:System.Xml.XmlDocument>|<span data-ttu-id="5dbe9-123">Umożliwia edytowanie tego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="5dbe9-123">It enables editing of this document.</span></span> <span data-ttu-id="5dbe9-124">Implementuje <xref:System.Xml.XPath.IXPathNavigable>, dzięki czemu scenariuszy edytowanie dokumentów, których następnie wymagane są przekształcenia XSLT.</span><span class="sxs-lookup"><span data-stu-id="5dbe9-124">It implements <xref:System.Xml.XPath.IXPathNavigable>, allowing document-editing scenarios where XSLT transformations are subsequently required.</span></span> <span data-ttu-id="5dbe9-125">Aby uzyskać więcej informacji, zobacz [dane wejściowe obiektu XmlDocument klasy xsltransform](xmldocument-input-to-xsltransform.md).</span><span class="sxs-lookup"><span data-stu-id="5dbe9-125">For more information, see [XmlDocument Input to XslTransform](xmldocument-input-to-xsltransform.md).</span></span>|
|<xref:System.Xml.XmlDataDocument>|<span data-ttu-id="5dbe9-126">Jest pochodną <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="5dbe9-126">It is derived from the <xref:System.Xml.XmlDocument>.</span></span> <span data-ttu-id="5dbe9-127">Tworzy ono relacyjnej i cech XML przy użyciu <xref:System.Data.DataSet> do optymalizacji magazynowania ustrukturyzowanych danych w dokumencie XML, zgodnie z określonym mapowania na <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="5dbe9-127">It bridges the relational and XML worlds by using a <xref:System.Data.DataSet> to optimize storage of structured data within the XML document according to specified mappings on the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="5dbe9-128">Implementuje <xref:System.Xml.XPath.IXPathNavigable>, dzięki czemu scenariuszy, w którym przekształcenia XSLT mogą być wykonywane na danych relacyjnych, pobierane z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="5dbe9-128">It implements <xref:System.Xml.XPath.IXPathNavigable>, allowing scenarios where XSLT transformations can be performed over relational data retrieved from a database.</span></span> <span data-ttu-id="5dbe9-129">Aby uzyskać więcej informacji, zobacz [Integracja XML z danymi relacyjnymi i ADO.NET](xml-integration-with-relational-data-and-adonet.md).</span><span class="sxs-lookup"><span data-stu-id="5dbe9-129">For more information, see [XML Integration with Relational Data and ADO.NET](xml-integration-with-relational-data-and-adonet.md).</span></span>|
|<xref:System.Xml.XPath.XPathDocument>|<span data-ttu-id="5dbe9-130">Ta klasa jest zoptymalizowana pod kątem <xref:System.Xml.Xsl.XslTransform> przetwarzania i zapytań XPath i oferuje pamięć podręczną tylko do odczytu o wysokiej wydajności.</span><span class="sxs-lookup"><span data-stu-id="5dbe9-130">This class is optimized for <xref:System.Xml.Xsl.XslTransform> processing and XPath queries, and it provides a read-only high performance cache.</span></span> <span data-ttu-id="5dbe9-131">Implementuje <xref:System.Xml.XPath.IXPathNavigable> i jest to preferowany magazyn na potrzeby przekształceń XSLT.</span><span class="sxs-lookup"><span data-stu-id="5dbe9-131">It implements <xref:System.Xml.XPath.IXPathNavigable> and is the preferred store to use for XSLT transformations.</span></span>|
|<xref:System.Xml.XPath.XPathNodeIterator>|<span data-ttu-id="5dbe9-132">Zapewnia on nawigacji przez zestawy węzła XPath.</span><span class="sxs-lookup"><span data-stu-id="5dbe9-132">It provides navigation over XPath node sets.</span></span> <span data-ttu-id="5dbe9-133">Wszystkie metody wyboru XPath w <xref:System.Xml.XPath.XPathNavigator> zwracają <xref:System.Xml.XPath.XPathNodeIterator>.</span><span class="sxs-lookup"><span data-stu-id="5dbe9-133">All XPath selection methods on the <xref:System.Xml.XPath.XPathNavigator> return an <xref:System.Xml.XPath.XPathNodeIterator>.</span></span> <span data-ttu-id="5dbe9-134">Wiele <xref:System.Xml.XPath.XPathNodeIterator> obiekty mogą być tworzone za pośrednictwem tego samego magazynu, reprezentujący wybrany zestaw węzłów.</span><span class="sxs-lookup"><span data-stu-id="5dbe9-134">Multiple <xref:System.Xml.XPath.XPathNodeIterator> objects can be created over the same store, each representing a selected set of nodes.</span></span>|

## <a name="msxml-xslt-extensions"></a><span data-ttu-id="5dbe9-135">Rozszerzenia programu MSXML XSLT</span><span class="sxs-lookup"><span data-stu-id="5dbe9-135">MSXML XSLT Extensions</span></span>

<span data-ttu-id="5dbe9-136">`msxsl:script` i `msxsl:node-set` funkcje są tylko rozszerzenia XSLT Microsoft XML Core Services (MSXML), obsługiwane przez <xref:System.Xml.Xsl.XslTransform> klasy.</span><span class="sxs-lookup"><span data-stu-id="5dbe9-136">The `msxsl:script` and `msxsl:node-set` functions are the only Microsoft XML Core Services (MSXML) XSLT extensions supported by the <xref:System.Xml.Xsl.XslTransform> class.</span></span>

## <a name="example"></a><span data-ttu-id="5dbe9-137">Przykład</span><span class="sxs-lookup"><span data-stu-id="5dbe9-137">Example</span></span>

<span data-ttu-id="5dbe9-138">Poniższy przykład kodu ładuje arkusz stylów XSLT odczytuje plik o nazwie mojedane.XML do <xref:System.Xml.XPath.XPathDocument>i wykonuje przekształcenie danych na fikcyjnej plik o nazwie myStyleSheet.xsl, wysyłając sformatowane dane wyjściowe do konsoli.</span><span class="sxs-lookup"><span data-stu-id="5dbe9-138">The following code example loads an XSLT style sheet, reads a file called mydata.xml into an <xref:System.Xml.XPath.XPathDocument>, and performs a transformation on the data on a fictitious file called myStyleSheet.xsl, sending the formatted output to the console.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="5dbe9-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5dbe9-139">See also</span></span>

- <xref:System.Xml.Xsl.XslTransform>
- [<span data-ttu-id="5dbe9-140">Implementowanie procesora XSLT przy użyciu klasy XslTransform</span><span class="sxs-lookup"><span data-stu-id="5dbe9-140">XslTransform Class Implements the XSLT Processor</span></span>](xsltransform-class-implements-the-xslt-processor.md)
- [<span data-ttu-id="5dbe9-141">Implementowanie zachowań uznaniowych w klasie XslTransform</span><span class="sxs-lookup"><span data-stu-id="5dbe9-141">Implementation of Discretionary Behaviors in the XslTransform Class</span></span>](implementation-of-discretionary-behaviors-in-the-xsltransform-class.md)
- [<span data-ttu-id="5dbe9-142">Klasa XPathNavigator w przekształceniach</span><span class="sxs-lookup"><span data-stu-id="5dbe9-142">XPathNavigator in Transformations</span></span>](xpathnavigator-in-transformations.md)
- [<span data-ttu-id="5dbe9-143">Klasa XPathNodeIterator w przekształceniach</span><span class="sxs-lookup"><span data-stu-id="5dbe9-143">XPathNodeIterator in Transformations</span></span>](xpathnodeiterator-in-transformations.md)
- [<span data-ttu-id="5dbe9-144">Dane wejściowe obiektu XPathDocument klasy XslTransform</span><span class="sxs-lookup"><span data-stu-id="5dbe9-144">XPathDocument Input to XslTransform</span></span>](xpathdocument-input-to-xsltransform.md)
- [<span data-ttu-id="5dbe9-145">Dane wejściowe obiektu XmlDataDocument klasy XslTransform</span><span class="sxs-lookup"><span data-stu-id="5dbe9-145">XmlDataDocument Input to XslTransform</span></span>](xmldatadocument-input-to-xsltransform.md)
- [<span data-ttu-id="5dbe9-146">Dane wejściowe obiektu XmlDocument klasy XslTransform</span><span class="sxs-lookup"><span data-stu-id="5dbe9-146">XmlDocument Input to XslTransform</span></span>](xmldocument-input-to-xsltransform.md)
