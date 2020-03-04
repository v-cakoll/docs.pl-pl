---
title: Dane wyjściowe klasy XslTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 8e149d32-4b2f-493f-9e4b-d0d93475acde
ms.openlocfilehash: 93cbf7807630a605e17e7f513055c052aad0d08e
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159640"
---
# <a name="outputs-from-an-xsltransform"></a><span data-ttu-id="45f81-102">Dane wyjściowe klasy XslTransform</span><span class="sxs-lookup"><span data-stu-id="45f81-102">Outputs from an XslTransform</span></span>
<span data-ttu-id="45f81-103">Ponieważ arkusze stylów mogą określić format danych wyjściowych przy użyciu instrukcji `<xsl:output>` z atrybutem `method`, w poniższej tabeli opisano, w jaki sposób format danych wyjściowych <xref:System.Xml.Xsl.XslTransform.Transform%2A> jest używany do zapisywania danych wyjściowych, a format danych wyjściowych jest zadeklarowany jako <xref:System.IO.Stream> lub <xref:System.IO.TextWriter>.</span><span class="sxs-lookup"><span data-stu-id="45f81-103">Since style sheets can determine the output format using an `<xsl:output>` statement with the `method` attribute, the following table describes what the output format is when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is used to write the output, and the output format is declared as a <xref:System.IO.Stream> or <xref:System.IO.TextWriter>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="45f81-104">Klasa <xref:System.Xml.Xsl.XslTransform> jest przestarzała w .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="45f81-104">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the .NET Framework 2.0.</span></span> <span data-ttu-id="45f81-105">Można wykonywać przekształcenia Extensible Stylesheet Language for Transformations (XSLT) przy użyciu klasy <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="45f81-105">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="45f81-106">Aby uzyskać więcej informacji, zobacz [Używanie klasy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) i [Migrowanie z klasy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) .</span><span class="sxs-lookup"><span data-stu-id="45f81-106">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="45f81-107">Ponieważ arkusze stylów mogą określić format danych wyjściowych przy użyciu instrukcji `<xsl:output>` z atrybutem `method`, w poniższej tabeli opisano, w jaki sposób format danych wyjściowych <xref:System.Xml.Xsl.XslTransform.Transform%2A> jest używany do zapisywania danych wyjściowych, a format danych wyjściowych jest zadeklarowany jako <xref:System.IO.Stream> lub <xref:System.IO.TextWriter>.</span><span class="sxs-lookup"><span data-stu-id="45f81-107">Since style sheets can determine the output format using an `<xsl:output>` statement with the `method` attribute, the following table describes what the output format is when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is used to write the output, and the output format is declared as a <xref:System.IO.Stream> or <xref:System.IO.TextWriter>.</span></span> <span data-ttu-id="45f81-108">W poniższej tabeli opisano, co się dzieje, gdy typ danych wyjściowych jest zadeklarowany przez metodę <xref:System.Xml.Xsl.XslTransform.Transform%2A> w połączeniu z użyciem instrukcji `<xsl:output>`:</span><span class="sxs-lookup"><span data-stu-id="45f81-108">The following table describes what happens when an output type is declared by the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method in conjunction with the use of an `<xsl:output>` statement:</span></span>  
  
|<span data-ttu-id="45f81-109">\<xsl: output — Metoda = atrybut ></span><span class="sxs-lookup"><span data-stu-id="45f81-109">\<xsl:output method = > attribute</span></span>|<span data-ttu-id="45f81-110">Format wyniku</span><span class="sxs-lookup"><span data-stu-id="45f81-110">Result format</span></span>|  
|-----------------------------------------|-------------------|  
|<span data-ttu-id="45f81-111">method="xml"</span><span class="sxs-lookup"><span data-stu-id="45f81-111">method="xml"</span></span>|<span data-ttu-id="45f81-112">{1&gt;XML&lt;1}</span><span class="sxs-lookup"><span data-stu-id="45f81-112">XML</span></span>|  
|<span data-ttu-id="45f81-113">method="html"</span><span class="sxs-lookup"><span data-stu-id="45f81-113">method="html"</span></span>|<span data-ttu-id="45f81-114">HTML</span><span class="sxs-lookup"><span data-stu-id="45f81-114">HTML</span></span>|  
|<span data-ttu-id="45f81-115">method="text"</span><span class="sxs-lookup"><span data-stu-id="45f81-115">method="text"</span></span>|<span data-ttu-id="45f81-116">Tekst</span><span class="sxs-lookup"><span data-stu-id="45f81-116">Text</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="45f81-117">Uwaga: Instrukcja `<xsl:output>` jest ignorowana, gdy dane wyjściowe metody <xref:System.Xml.Xsl.XslTransform.Transform%2A> są <xref:System.Xml.XmlReader> lub <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="45f81-117">Note: The `<xsl:output>` statement is ignored when the output of the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is an <xref:System.Xml.XmlReader> or <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="45f81-118">Następujące atrybuty są obsługiwane, gdy dane wyjściowe metody <xref:System.Xml.Xsl.XslTransform.Transform%2A> są <xref:System.IO.Stream> lub <xref:System.IO.TextWriter>:</span><span class="sxs-lookup"><span data-stu-id="45f81-118">The following attributes are supported when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method output is a <xref:System.IO.Stream> or <xref:System.IO.TextWriter>:</span></span>  
  
- <span data-ttu-id="45f81-119">encoding\*</span><span class="sxs-lookup"><span data-stu-id="45f81-119">encoding\*</span></span>  
  
- <span data-ttu-id="45f81-120">Pomiń deklarację XML</span><span class="sxs-lookup"><span data-stu-id="45f81-120">omit-xml-declaration</span></span>  
  
- <span data-ttu-id="45f81-121">autonomiczne</span><span class="sxs-lookup"><span data-stu-id="45f81-121">standalone</span></span>  
  
- <span data-ttu-id="45f81-122">DOCTYPE — publiczny</span><span class="sxs-lookup"><span data-stu-id="45f81-122">doctype-public</span></span>  
  
- <span data-ttu-id="45f81-123">DOCTYPE — system</span><span class="sxs-lookup"><span data-stu-id="45f81-123">doctype-system</span></span>  
  
- <span data-ttu-id="45f81-124">CDATA-elementy sekcji</span><span class="sxs-lookup"><span data-stu-id="45f81-124">cdata-section-elements</span></span>  
  
- <span data-ttu-id="45f81-125">wyświetlane</span><span class="sxs-lookup"><span data-stu-id="45f81-125">indent</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="45f81-126">\*atrybut kodowania jest ignorowany, gdy metoda <xref:System.Xml.Xsl.XslTransform.Transform%2A> wysyła dane wyjściowe do <xref:System.IO.TextWriter>.</span><span class="sxs-lookup"><span data-stu-id="45f81-126">\*The encoding attribute is ignored when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is sending its output to a <xref:System.IO.TextWriter>.</span></span> <span data-ttu-id="45f81-127">Zamiast tego zostanie użyta Właściwość Encoding w <xref:System.IO.TextWriter>.</span><span class="sxs-lookup"><span data-stu-id="45f81-127">The encoding property on the <xref:System.IO.TextWriter> is used instead.</span></span>
  
 <span data-ttu-id="45f81-128">Następujący atrybut jest ignorowany, gdy dane wyjściowe metody <xref:System.Xml.Xsl.XslTransform.Transform%2A> są <xref:System.IO.Stream>:</span><span class="sxs-lookup"><span data-stu-id="45f81-128">The following attribute is ignored when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method output is a <xref:System.IO.Stream>:</span></span>  
  
- <span data-ttu-id="45f81-129">Wersja: wersja jest zawsze 1,0</span><span class="sxs-lookup"><span data-stu-id="45f81-129">version: the version is always 1.0</span></span>  
  
- <span data-ttu-id="45f81-130">Typ nośnika: typ nośnika</span><span class="sxs-lookup"><span data-stu-id="45f81-130">media-type: the media-type</span></span>  
  
## <a name="escaping-special-characters"></a><span data-ttu-id="45f81-131">Znaki specjalne ucieczki</span><span class="sxs-lookup"><span data-stu-id="45f81-131">Escaping Special Characters</span></span>  
 <span data-ttu-id="45f81-132">Tag `<xsl:text disable-output-escaping>` służy do wskazywania, czy znaki specjalne muszą być wyprowadzane do formularza XML (na przykład przy użyciu `<&lt>` zamiast symbolu `"<"`) lub pozostawione w stanie obecne.</span><span class="sxs-lookup"><span data-stu-id="45f81-132">The `<xsl:text disable-output-escaping>` tag is used to indicate whether or not special characters need to be escaped into an XML form (for example, using `<&lt>` in place of the `"<"` symbol) or left in the present condition.</span></span> <span data-ttu-id="45f81-133">Atrybut `disable-output-escaping` jest ignorowany podczas przekształcania do obiektu <xref:System.Xml.XmlReader> lub <xref:System.Xml.XmlWriter> i nie ma wpływu na znaki specjalne.</span><span class="sxs-lookup"><span data-stu-id="45f81-133">The `disable-output-escaping` attribute is ignored when transforming to an <xref:System.Xml.XmlReader> or <xref:System.Xml.XmlWriter> object and has no effect on special characters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45f81-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="45f81-134">See also</span></span>

- [<span data-ttu-id="45f81-135">Implementowanie procesora XSLT przy użyciu klasy XslTransform</span><span class="sxs-lookup"><span data-stu-id="45f81-135">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
