---
title: Dane wyjściowe z klasy XslTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 8e149d32-4b2f-493f-9e4b-d0d93475acde
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3b299f09f3dc47b5d136284d4d1d285f2e5aad5f
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/15/2018
ms.locfileid: "45641329"
---
# <a name="outputs-from-an-xsltransform"></a><span data-ttu-id="964ee-102">Dane wyjściowe z klasy XslTransform</span><span class="sxs-lookup"><span data-stu-id="964ee-102">Outputs from an XslTransform</span></span>
<span data-ttu-id="964ee-103">Ponieważ arkusze stylów można określić przy użyciu formatu danych wyjściowych `<xsl:output>` instrukcję, określając `method` atrybutu w poniższej tabeli opisano format danych wyjściowych jest, gdy <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda służy do zapisywania danych wyjściowych i format danych wyjściowych zadeklarowany jako <xref:System.IO.Stream> lub <xref:System.IO.TextWriter>.</span><span class="sxs-lookup"><span data-stu-id="964ee-103">Since style sheets can determine the output format using an `<xsl:output>` statement with the `method` attribute, the following table describes what the output format is when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is used to write the output, and the output format is declared as a <xref:System.IO.Stream> or <xref:System.IO.TextWriter>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="964ee-104"><xref:System.Xml.Xsl.XslTransform> Klasy jest przestarzała w [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="964ee-104">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span> <span data-ttu-id="964ee-105">Można przeprowadzić rozszerzalny język arkusza stylów dla przekształceń przekształcenia (XSLT) przy użyciu <xref:System.Xml.Xsl.XslCompiledTransform> klasy.</span><span class="sxs-lookup"><span data-stu-id="964ee-105">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="964ee-106">Zobacz [używanie klasy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) i [Migrowanie z klasy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) Aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="964ee-106">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="964ee-107">Ponieważ arkusze stylów można określić przy użyciu formatu danych wyjściowych `<xsl:output>` instrukcję, określając `method` atrybutu w poniższej tabeli opisano format danych wyjściowych jest, gdy <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda służy do zapisywania danych wyjściowych i format danych wyjściowych zadeklarowany jako <xref:System.IO.Stream> lub <xref:System.IO.TextWriter>.</span><span class="sxs-lookup"><span data-stu-id="964ee-107">Since style sheets can determine the output format using an `<xsl:output>` statement with the `method` attribute, the following table describes what the output format is when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is used to write the output, and the output format is declared as a <xref:System.IO.Stream> or <xref:System.IO.TextWriter>.</span></span> <span data-ttu-id="964ee-108">W poniższej tabeli opisano, co się stanie, gdy typ danych wyjściowych jest deklarowana przez <xref:System.Xml.Xsl.XslTransform.Transform%2A> metody w połączeniu z użyciem `<xsl:output>` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="964ee-108">The following table describes what happens when an output type is declared by the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method in conjunction with the use of an `<xsl:output>` statement:</span></span>  
  
|<span data-ttu-id="964ee-109">\<Metoda: output = > atrybut</span><span class="sxs-lookup"><span data-stu-id="964ee-109">\<xsl:output method = > attribute</span></span>|<span data-ttu-id="964ee-110">Format wyników</span><span class="sxs-lookup"><span data-stu-id="964ee-110">Result format</span></span>|  
|-----------------------------------------|-------------------|  
|<span data-ttu-id="964ee-111">method="xml"</span><span class="sxs-lookup"><span data-stu-id="964ee-111">method="xml"</span></span>|<span data-ttu-id="964ee-112">XML</span><span class="sxs-lookup"><span data-stu-id="964ee-112">XML</span></span>|  
|<span data-ttu-id="964ee-113">method="html"</span><span class="sxs-lookup"><span data-stu-id="964ee-113">method="html"</span></span>|<span data-ttu-id="964ee-114">HTML</span><span class="sxs-lookup"><span data-stu-id="964ee-114">HTML</span></span>|  
|<span data-ttu-id="964ee-115">method="text"</span><span class="sxs-lookup"><span data-stu-id="964ee-115">method="text"</span></span>|<span data-ttu-id="964ee-116">Tekst</span><span class="sxs-lookup"><span data-stu-id="964ee-116">Text</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="964ee-117">Uwaga: `<xsl:output>` instrukcji jest ignorowana, gdy dane wyjściowe <xref:System.Xml.Xsl.XslTransform.Transform%2A> metodą jest <xref:System.Xml.XmlReader> lub <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="964ee-117">Note: The `<xsl:output>` statement is ignored when the output of the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is an <xref:System.Xml.XmlReader> or <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="964ee-118">Następujące atrybuty są obsługiwane podczas <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda danych wyjściowych jest <xref:System.IO.Stream> lub <xref:System.IO.TextWriter>:</span><span class="sxs-lookup"><span data-stu-id="964ee-118">The following attributes are supported when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method output is a <xref:System.IO.Stream> or <xref:System.IO.TextWriter>:</span></span>  
  
-   <span data-ttu-id="964ee-119">encoding\*</span><span class="sxs-lookup"><span data-stu-id="964ee-119">encoding\*</span></span>  
  
-   <span data-ttu-id="964ee-120">Pomiń xml deklaracji</span><span class="sxs-lookup"><span data-stu-id="964ee-120">omit-xml-declaration</span></span>  
  
-   <span data-ttu-id="964ee-121">niezależne</span><span class="sxs-lookup"><span data-stu-id="964ee-121">standalone</span></span>  
  
-   <span data-ttu-id="964ee-122">publiczna doctype</span><span class="sxs-lookup"><span data-stu-id="964ee-122">doctype-public</span></span>  
  
-   <span data-ttu-id="964ee-123">DOCTYPE system</span><span class="sxs-lookup"><span data-stu-id="964ee-123">doctype-system</span></span>  
  
-   <span data-ttu-id="964ee-124">elementy w przypadku sekcja CDATA</span><span class="sxs-lookup"><span data-stu-id="964ee-124">cdata-section-elements</span></span>  
  
-   <span data-ttu-id="964ee-125">wcięcie</span><span class="sxs-lookup"><span data-stu-id="964ee-125">indent</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="964ee-126">\* kodowania. atrybut jest ignorowany podczas <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda wysyła dane wyjściowe do <xref:System.IO.TextWriter>.</span><span class="sxs-lookup"><span data-stu-id="964ee-126">\*the encoding attribute is ignored when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is sending its output to a <xref:System.IO.TextWriter>.</span></span> <span data-ttu-id="964ee-127">Właściwość kodowania <xref:System.IO.TextWriter> zamian jest używana.</span><span class="sxs-lookup"><span data-stu-id="964ee-127">The encoding property on the <xref:System.IO.TextWriter> is used instead.</span></span>  
  
 <span data-ttu-id="964ee-128">Następujący atrybut jest ignorowany podczas <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda danych wyjściowych jest <xref:System.IO.Stream>:</span><span class="sxs-lookup"><span data-stu-id="964ee-128">The following attribute is ignored when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method output is a <xref:System.IO.Stream>:</span></span>  
  
-   <span data-ttu-id="964ee-129">Wersja: wersja jest zawsze 1.0</span><span class="sxs-lookup"><span data-stu-id="964ee-129">version: the version is always 1.0</span></span>  
  
-   <span data-ttu-id="964ee-130">Typ nośnika: typ nośnika</span><span class="sxs-lookup"><span data-stu-id="964ee-130">media-type: the media-type</span></span>  
  
## <a name="escaping-special-characters"></a><span data-ttu-id="964ee-131">Znaki specjalne wyjścia</span><span class="sxs-lookup"><span data-stu-id="964ee-131">Escaping Special Characters</span></span>  
 <span data-ttu-id="964ee-132">`<xsl:text disable-output-escaping>` Tag jest używany do wskazania, czy znaki specjalne, należy wstawić do postaci XML (na przykład za pomocą `<&lt>` zamiast `"<"` symbol) lub po lewej stronie w obecnym stanie.</span><span class="sxs-lookup"><span data-stu-id="964ee-132">The `<xsl:text disable-output-escaping>` tag is used to indicate whether or not special characters need to be escaped into an XML form (for example, using `<&lt>` in place of the `"<"` symbol) or left in the present condition.</span></span> <span data-ttu-id="964ee-133">`disable-output-escaping` Atrybut jest ignorowany podczas przekształcania w <xref:System.Xml.XmlReader> lub <xref:System.Xml.XmlWriter> obiektu i nie ma wpływu na znaki specjalne.</span><span class="sxs-lookup"><span data-stu-id="964ee-133">The `disable-output-escaping` attribute is ignored when transforming to an <xref:System.Xml.XmlReader> or <xref:System.Xml.XmlWriter> object and has no effect on special characters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="964ee-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="964ee-134">See also</span></span>

- [<span data-ttu-id="964ee-135">Implementowanie procesora XSLT przy użyciu klasy XslTransform</span><span class="sxs-lookup"><span data-stu-id="964ee-135">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
