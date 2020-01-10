---
title: Przekształcenia XSLT przy użyciu klasy XslTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 500335af-f9b5-413b-968a-e6d9a824478c
ms.openlocfilehash: 5f670fa5e83d1802496c0cc6972a7e3af7cae374
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709650"
---
# <a name="xslt-transformations-with-the-xsltransform-class"></a><span data-ttu-id="47992-102">Przekształcenia XSLT przy użyciu klasy XslTransform</span><span class="sxs-lookup"><span data-stu-id="47992-102">XSLT Transformations with the XslTransform Class</span></span>

> [!NOTE]
> <span data-ttu-id="47992-103">Klasa <xref:System.Xml.Xsl.XslTransform> jest przestarzała w .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="47992-103">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the .NET Framework 2.0.</span></span> <span data-ttu-id="47992-104">Można wykonywać przekształcenia Extensible Stylesheet Language for Transformations (XSLT) przy użyciu klasy <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="47992-104">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="47992-105">Aby uzyskać więcej informacji, zobacz [Używanie klasy XslCompiledTransform](using-the-xslcompiledtransform-class.md) i [Migrowanie z klasy XslTransform](migrating-from-the-xsltransform-class.md) .</span><span class="sxs-lookup"><span data-stu-id="47992-105">See [Using the XslCompiledTransform Class](using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](migrating-from-the-xsltransform-class.md) for more information.</span></span>

<span data-ttu-id="47992-106">Celem XSLT jest przekształcenie zawartości źródłowego dokumentu XML do innego dokumentu, który jest inny w formacie lub strukturze (na przykład w celu przekształcenia XML w HTML do użycia w witrynie sieci Web lub przekształcenia go w dokument zawierający tylko pola wymagane b). t aplikacji).</span><span class="sxs-lookup"><span data-stu-id="47992-106">The goal of the XSLT is to transform the content of a source XML document into another document that is different in format or structure (for example, to transform XML into HTML for use on a Web site or to transform it into a document that contains only the fields required by an application).</span></span> <span data-ttu-id="47992-107">Ten proces transformacji jest określany przez organizacja World Wide Web Consortium (W3C) w[wersji 1,0 zalecenia](https://www.w3.org/TR/1999/REC-xslt-19991116).</span><span class="sxs-lookup"><span data-stu-id="47992-107">This transformation process is specified by the World Wide Web Consortium (W3C)[XSLT version 1.0 recommendation](https://www.w3.org/TR/1999/REC-xslt-19991116).</span></span> <span data-ttu-id="47992-108">W .NET Framework Klasa <xref:System.Xml.Xsl.XslTransform>, która znajduje się w przestrzeni nazw <xref:System.Xml.Xsl>, to procesor XSLT, który implementuje funkcje tej specyfikacji.</span><span class="sxs-lookup"><span data-stu-id="47992-108">In the .NET Framework, the <xref:System.Xml.Xsl.XslTransform> class, found in the <xref:System.Xml.Xsl> namespace, is the XSLT processor that implements the functionality of this specification.</span></span> <span data-ttu-id="47992-109">Istnieje niewielka liczba funkcji, które nie zostały zaimplementowane z rekomendacji W3C XSLT 1,0, wymienione w danych [wyjściowych z XslTransform](outputs-from-an-xsltransform.md).</span><span class="sxs-lookup"><span data-stu-id="47992-109">There are a small number of features that have not been implemented from the W3C XSLT 1.0 recommendation, listed in [Outputs from an XslTransform](outputs-from-an-xsltransform.md).</span></span> <span data-ttu-id="47992-110">Na poniższej ilustracji przedstawiono architekturę transformacji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="47992-110">The following figure shows the transformation architecture of the .NET Framework.</span></span>

## <a name="overview"></a><span data-ttu-id="47992-111">Omówienie</span><span class="sxs-lookup"><span data-stu-id="47992-111">Overview</span></span>

![Diagram przedstawiający architekturę transformacji XSLT.](./media/xslt-transformations-with-the-xsltransform-class/xslt-transformation-architecture.gif) 

<span data-ttu-id="47992-113">Zalecenie XSLT używa języka ścieżki XML (XPath) do wybierania części dokumentu XML, gdzie XPath jest językiem zapytań używanym do nawigowania po węzłach drzewa dokumentu.</span><span class="sxs-lookup"><span data-stu-id="47992-113">The XSLT recommendation uses XML Path Language (XPath) to select parts of an XML document, where XPath is a query language used to navigate nodes of a document tree.</span></span> <span data-ttu-id="47992-114">Jak pokazano na diagramie, .NET Framework implementacja XPath służy do wybierania części XML przechowywanych w kilku klasach, takich jak <xref:System.Xml.XmlDocument>, <xref:System.Xml.XmlDataDocument>i <xref:System.Xml.XPath.XPathDocument>.</span><span class="sxs-lookup"><span data-stu-id="47992-114">As shown in the diagram, the .NET Framework implementation of XPath is used to select parts of XML stored in several classes, such as an <xref:System.Xml.XmlDocument>, an <xref:System.Xml.XmlDataDocument>, and an <xref:System.Xml.XPath.XPathDocument>.</span></span> <span data-ttu-id="47992-115"><xref:System.Xml.XPath.XPathDocument> jest zoptymalizowanym magazynem danych XSLT i w przypadku korzystania z <xref:System.Xml.Xsl.XslTransform>, zapewnia przekształcenia XSLT z dobrą wydajnością.</span><span class="sxs-lookup"><span data-stu-id="47992-115">An <xref:System.Xml.XPath.XPathDocument> is an optimized XSLT data store, and when used with <xref:System.Xml.Xsl.XslTransform>, it provides XSLT transformations with good performance.</span></span>

<span data-ttu-id="47992-116">W poniższej tabeli wymieniono typowe zastosowania klas podczas pracy z <xref:System.Xml.Xsl.XslTransform> i XPath oraz ich funkcją.</span><span class="sxs-lookup"><span data-stu-id="47992-116">The following table list commonly uses classes when working with <xref:System.Xml.Xsl.XslTransform> and XPath and their function.</span></span>

|<span data-ttu-id="47992-117">Klasa lub interfejs</span><span class="sxs-lookup"><span data-stu-id="47992-117">Class or Interface</span></span>|<span data-ttu-id="47992-118">Funkcja</span><span class="sxs-lookup"><span data-stu-id="47992-118">Function</span></span>|
|------------------------|--------------|
|<xref:System.Xml.XPath.XPathNavigator>|<span data-ttu-id="47992-119">Jest to interfejs API, który udostępnia model stylu kursora na potrzeby nawigowania po sklepie oraz obsługę zapytań XPath.</span><span class="sxs-lookup"><span data-stu-id="47992-119">It is an API that provides a cursor style model for navigating over a store, along with XPath query support.</span></span> <span data-ttu-id="47992-120">Nie zapewnia on edycji bazowego magazynu.</span><span class="sxs-lookup"><span data-stu-id="47992-120">It does not provide editing of the underlying store.</span></span> <span data-ttu-id="47992-121">Aby edytować, użyj klasy <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="47992-121">For editing, use the <xref:System.Xml.XmlDocument> class.</span></span>|
|<xref:System.Xml.XPath.IXPathNavigable>|<span data-ttu-id="47992-122">Jest to interfejs, który udostępnia metodę `CreateNavigator` do <xref:System.Xml.XPath.XPathNavigator> magazynu.</span><span class="sxs-lookup"><span data-stu-id="47992-122">It is an interface that provides a `CreateNavigator` method to an <xref:System.Xml.XPath.XPathNavigator> for the store.</span></span>|
|<xref:System.Xml.XmlDocument>|<span data-ttu-id="47992-123">Umożliwia edytowanie tego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="47992-123">It enables editing of this document.</span></span> <span data-ttu-id="47992-124">Implementuje <xref:System.Xml.XPath.IXPathNavigable>, co umożliwia scenariusze edycji dokumentów, w których przekształcenia XSLT są wymagane.</span><span class="sxs-lookup"><span data-stu-id="47992-124">It implements <xref:System.Xml.XPath.IXPathNavigable>, allowing document-editing scenarios where XSLT transformations are subsequently required.</span></span> <span data-ttu-id="47992-125">Aby uzyskać więcej informacji, zobacz [XmlDocument input to XslTransform](xmldocument-input-to-xsltransform.md).</span><span class="sxs-lookup"><span data-stu-id="47992-125">For more information, see [XmlDocument Input to XslTransform](xmldocument-input-to-xsltransform.md).</span></span>|
|<xref:System.Xml.XmlDataDocument>|<span data-ttu-id="47992-126">Pochodzi ona od <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="47992-126">It is derived from the <xref:System.Xml.XmlDocument>.</span></span> <span data-ttu-id="47992-127">Mostkuje środowiska relacyjne i XML przy użyciu <xref:System.Data.DataSet> do optymalizowania magazynu danych strukturalnych w dokumencie XML zgodnie z określonymi mapowaniami w <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="47992-127">It bridges the relational and XML worlds by using a <xref:System.Data.DataSet> to optimize storage of structured data within the XML document according to specified mappings on the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="47992-128">Implementuje <xref:System.Xml.XPath.IXPathNavigable>, umożliwiając scenariusze, w których można wykonywać przekształcenia XSLT w danych relacyjnych pobieranych z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="47992-128">It implements <xref:System.Xml.XPath.IXPathNavigable>, allowing scenarios where XSLT transformations can be performed over relational data retrieved from a database.</span></span> <span data-ttu-id="47992-129">Aby uzyskać więcej informacji, zobacz temat [Integracja XML z danymi relacyjnymi i ADO.NET](xml-integration-with-relational-data-and-adonet.md).</span><span class="sxs-lookup"><span data-stu-id="47992-129">For more information, see [XML Integration with Relational Data and ADO.NET](xml-integration-with-relational-data-and-adonet.md).</span></span>|
|<xref:System.Xml.XPath.XPathDocument>|<span data-ttu-id="47992-130">Ta klasa jest zoptymalizowana pod kątem <xref:System.Xml.Xsl.XslTransform> przetwarzania i zapytań XPath i udostępnia pamięć podręczną o wysokiej wydajności tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="47992-130">This class is optimized for <xref:System.Xml.Xsl.XslTransform> processing and XPath queries, and it provides a read-only high performance cache.</span></span> <span data-ttu-id="47992-131">Implementuje <xref:System.Xml.XPath.IXPathNavigable> i jest preferowanym magazynem do użycia na potrzeby transformacji XSLT.</span><span class="sxs-lookup"><span data-stu-id="47992-131">It implements <xref:System.Xml.XPath.IXPathNavigable> and is the preferred store to use for XSLT transformations.</span></span>|
|<xref:System.Xml.XPath.XPathNodeIterator>|<span data-ttu-id="47992-132">Zapewnia nawigację nad zestawami węzłów XPath.</span><span class="sxs-lookup"><span data-stu-id="47992-132">It provides navigation over XPath node sets.</span></span> <span data-ttu-id="47992-133">Wszystkie metody wyboru XPath na <xref:System.Xml.XPath.XPathNavigator> zwracają <xref:System.Xml.XPath.XPathNodeIterator>.</span><span class="sxs-lookup"><span data-stu-id="47992-133">All XPath selection methods on the <xref:System.Xml.XPath.XPathNavigator> return an <xref:System.Xml.XPath.XPathNodeIterator>.</span></span> <span data-ttu-id="47992-134">Wiele obiektów <xref:System.Xml.XPath.XPathNodeIterator> można utworzyć w tym samym magazynie, z których każdy reprezentuje wybrany zestaw węzłów.</span><span class="sxs-lookup"><span data-stu-id="47992-134">Multiple <xref:System.Xml.XPath.XPathNodeIterator> objects can be created over the same store, each representing a selected set of nodes.</span></span>|

## <a name="msxml-xslt-extensions"></a><span data-ttu-id="47992-135">Rozszerzenia XSLT języka MSXML</span><span class="sxs-lookup"><span data-stu-id="47992-135">MSXML XSLT Extensions</span></span>

<span data-ttu-id="47992-136">`msxsl:script` i `msxsl:node-set` funkcje są jedynymi rozszerzeniami XSLT programu Microsoft XML Core Services (MSXML) obsługiwanymi przez klasę <xref:System.Xml.Xsl.XslTransform>.</span><span class="sxs-lookup"><span data-stu-id="47992-136">The `msxsl:script` and `msxsl:node-set` functions are the only Microsoft XML Core Services (MSXML) XSLT extensions supported by the <xref:System.Xml.Xsl.XslTransform> class.</span></span>

## <a name="example"></a><span data-ttu-id="47992-137">Przykład</span><span class="sxs-lookup"><span data-stu-id="47992-137">Example</span></span>

<span data-ttu-id="47992-138">Poniższy przykład kodu ładuje arkusz stylów XSLT, odczytuje plik o nazwie moje dane. XML do <xref:System.Xml.XPath.XPathDocument>i wykonuje przekształcenie danych w fikcyjnym pliku o nazwie plik. xsl, wysyłając sformatowane dane wyjściowe do konsoli.</span><span class="sxs-lookup"><span data-stu-id="47992-138">The following code example loads an XSLT style sheet, reads a file called mydata.xml into an <xref:System.Xml.XPath.XPathDocument>, and performs a transformation on the data on a fictitious file called myStyleSheet.xsl, sending the formatted output to the console.</span></span>

```vb
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

## <a name="see-also"></a><span data-ttu-id="47992-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="47992-139">See also</span></span>

- <xref:System.Xml.Xsl.XslTransform>
- [<span data-ttu-id="47992-140">Implementowanie procesora XSLT przy użyciu klasy XslTransform</span><span class="sxs-lookup"><span data-stu-id="47992-140">XslTransform Class Implements the XSLT Processor</span></span>](xsltransform-class-implements-the-xslt-processor.md)
- [<span data-ttu-id="47992-141">Implementowanie zachowań uznaniowych w klasie XslTransform</span><span class="sxs-lookup"><span data-stu-id="47992-141">Implementation of Discretionary Behaviors in the XslTransform Class</span></span>](implementation-of-discretionary-behaviors-in-the-xsltransform-class.md)
- [<span data-ttu-id="47992-142">Klasa XPathNavigator w przekształceniach</span><span class="sxs-lookup"><span data-stu-id="47992-142">XPathNavigator in Transformations</span></span>](xpathnavigator-in-transformations.md)
- [<span data-ttu-id="47992-143">Klasa XPathNodeIterator w przekształceniach</span><span class="sxs-lookup"><span data-stu-id="47992-143">XPathNodeIterator in Transformations</span></span>](xpathnodeiterator-in-transformations.md)
- [<span data-ttu-id="47992-144">Dane wejściowe obiektu XPathDocument klasy XslTransform</span><span class="sxs-lookup"><span data-stu-id="47992-144">XPathDocument Input to XslTransform</span></span>](xpathdocument-input-to-xsltransform.md)
- [<span data-ttu-id="47992-145">Dane wejściowe obiektu XmlDataDocument klasy XslTransform</span><span class="sxs-lookup"><span data-stu-id="47992-145">XmlDataDocument Input to XslTransform</span></span>](xmldatadocument-input-to-xsltransform.md)
- [<span data-ttu-id="47992-146">Dane wejściowe obiektu XmlDocument klasy XslTransform</span><span class="sxs-lookup"><span data-stu-id="47992-146">XmlDocument Input to XslTransform</span></span>](xmldocument-input-to-xsltransform.md)
