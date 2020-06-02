---
title: Dane wyjściowe klasy XslTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 8e149d32-4b2f-493f-9e4b-d0d93475acde
ms.openlocfilehash: 5fa8c8228382f7f326a8d2243ed0450fca31f6fb
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288696"
---
# <a name="outputs-from-an-xsltransform"></a><span data-ttu-id="d1bf1-102">Dane wyjściowe klasy XslTransform</span><span class="sxs-lookup"><span data-stu-id="d1bf1-102">Outputs from an XslTransform</span></span>
<span data-ttu-id="d1bf1-103">Ponieważ arkusze stylów mogą określić format danych wyjściowych przy użyciu `<xsl:output>` instrukcji z `method` atrybutem, w poniższej tabeli opisano, w jaki sposób format danych wyjściowych jest <xref:System.Xml.Xsl.XslTransform.Transform%2A> używany do pisania danych wyjściowych, a format danych wyjściowych jest zadeklarowany jako <xref:System.IO.Stream> lub <xref:System.IO.TextWriter> .</span><span class="sxs-lookup"><span data-stu-id="d1bf1-103">Since style sheets can determine the output format using an `<xsl:output>` statement with the `method` attribute, the following table describes what the output format is when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is used to write the output, and the output format is declared as a <xref:System.IO.Stream> or <xref:System.IO.TextWriter>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d1bf1-104"><xref:System.Xml.Xsl.XslTransform>Klasa jest przestarzała w .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="d1bf1-104">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the .NET Framework 2.0.</span></span> <span data-ttu-id="d1bf1-105">Można wykonać przekształcenia Extensible Stylesheet Language for Transformations (XSLT) przy użyciu <xref:System.Xml.Xsl.XslCompiledTransform> klasy.</span><span class="sxs-lookup"><span data-stu-id="d1bf1-105">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="d1bf1-106">Aby uzyskać więcej informacji, zobacz [Używanie klasy XslCompiledTransform](using-the-xslcompiledtransform-class.md) i [Migrowanie z klasy XslTransform](migrating-from-the-xsltransform-class.md) .</span><span class="sxs-lookup"><span data-stu-id="d1bf1-106">See [Using the XslCompiledTransform Class](using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="d1bf1-107">Ponieważ arkusze stylów mogą określić format danych wyjściowych przy użyciu `<xsl:output>` instrukcji z `method` atrybutem, w poniższej tabeli opisano, w jaki sposób format danych wyjściowych jest <xref:System.Xml.Xsl.XslTransform.Transform%2A> używany do pisania danych wyjściowych, a format danych wyjściowych jest zadeklarowany jako <xref:System.IO.Stream> lub <xref:System.IO.TextWriter> .</span><span class="sxs-lookup"><span data-stu-id="d1bf1-107">Since style sheets can determine the output format using an `<xsl:output>` statement with the `method` attribute, the following table describes what the output format is when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is used to write the output, and the output format is declared as a <xref:System.IO.Stream> or <xref:System.IO.TextWriter>.</span></span> <span data-ttu-id="d1bf1-108">W poniższej tabeli opisano, co się dzieje, gdy typ danych wyjściowych jest zadeklarowany przez <xref:System.Xml.Xsl.XslTransform.Transform%2A> metodę w połączeniu z użyciem `<xsl:output>` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="d1bf1-108">The following table describes what happens when an output type is declared by the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method in conjunction with the use of an `<xsl:output>` statement:</span></span>  
  
|<span data-ttu-id="d1bf1-109">Atrybut \<xsl:output method = ></span><span class="sxs-lookup"><span data-stu-id="d1bf1-109">\<xsl:output method = > attribute</span></span>|<span data-ttu-id="d1bf1-110">Format wyniku</span><span class="sxs-lookup"><span data-stu-id="d1bf1-110">Result format</span></span>|  
|-----------------------------------------|-------------------|  
|<span data-ttu-id="d1bf1-111">Metoda = "XML"</span><span class="sxs-lookup"><span data-stu-id="d1bf1-111">method="xml"</span></span>|<span data-ttu-id="d1bf1-112">XML</span><span class="sxs-lookup"><span data-stu-id="d1bf1-112">XML</span></span>|  
|<span data-ttu-id="d1bf1-113">Metoda = "HTML"</span><span class="sxs-lookup"><span data-stu-id="d1bf1-113">method="html"</span></span>|<span data-ttu-id="d1bf1-114">HTML</span><span class="sxs-lookup"><span data-stu-id="d1bf1-114">HTML</span></span>|  
|<span data-ttu-id="d1bf1-115">Metoda = "text"</span><span class="sxs-lookup"><span data-stu-id="d1bf1-115">method="text"</span></span>|<span data-ttu-id="d1bf1-116">Tekst</span><span class="sxs-lookup"><span data-stu-id="d1bf1-116">Text</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="d1bf1-117">Uwaga: `<xsl:output>` instrukcja jest ignorowana, jeśli dane wyjściowe <xref:System.Xml.Xsl.XslTransform.Transform%2A> metody są <xref:System.Xml.XmlReader> lub <xref:System.Xml.XmlWriter> .</span><span class="sxs-lookup"><span data-stu-id="d1bf1-117">Note: The `<xsl:output>` statement is ignored when the output of the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is an <xref:System.Xml.XmlReader> or <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="d1bf1-118">Następujące atrybuty są obsługiwane, gdy <xref:System.Xml.Xsl.XslTransform.Transform%2A> wynikiem metody jest <xref:System.IO.Stream> lub <xref:System.IO.TextWriter> :</span><span class="sxs-lookup"><span data-stu-id="d1bf1-118">The following attributes are supported when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method output is a <xref:System.IO.Stream> or <xref:System.IO.TextWriter>:</span></span>  
  
- <span data-ttu-id="d1bf1-119">Kody</span><span class="sxs-lookup"><span data-stu-id="d1bf1-119">encoding\*</span></span>  
  
- <span data-ttu-id="d1bf1-120">Pomiń deklarację XML</span><span class="sxs-lookup"><span data-stu-id="d1bf1-120">omit-xml-declaration</span></span>  
  
- <span data-ttu-id="d1bf1-121">niezależne</span><span class="sxs-lookup"><span data-stu-id="d1bf1-121">standalone</span></span>  
  
- <span data-ttu-id="d1bf1-122">DOCTYPE — publiczny</span><span class="sxs-lookup"><span data-stu-id="d1bf1-122">doctype-public</span></span>  
  
- <span data-ttu-id="d1bf1-123">DOCTYPE — system</span><span class="sxs-lookup"><span data-stu-id="d1bf1-123">doctype-system</span></span>  
  
- <span data-ttu-id="d1bf1-124">CDATA-elementy sekcji</span><span class="sxs-lookup"><span data-stu-id="d1bf1-124">cdata-section-elements</span></span>  
  
- <span data-ttu-id="d1bf1-125">wyświetlane</span><span class="sxs-lookup"><span data-stu-id="d1bf1-125">indent</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="d1bf1-126">\*Atrybut Encoding jest ignorowany, gdy <xref:System.Xml.Xsl.XslTransform.Transform%2A> Metoda wysyła dane wyjściowe do <xref:System.IO.TextWriter> .</span><span class="sxs-lookup"><span data-stu-id="d1bf1-126">\*The encoding attribute is ignored when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is sending its output to a <xref:System.IO.TextWriter>.</span></span> <span data-ttu-id="d1bf1-127">Właściwość Encoding w <xref:System.IO.TextWriter> jest używana w zamian.</span><span class="sxs-lookup"><span data-stu-id="d1bf1-127">The encoding property on the <xref:System.IO.TextWriter> is used instead.</span></span>
  
 <span data-ttu-id="d1bf1-128">Następujący atrybut jest ignorowany, gdy <xref:System.Xml.Xsl.XslTransform.Transform%2A> wyjście metody jest <xref:System.IO.Stream> :</span><span class="sxs-lookup"><span data-stu-id="d1bf1-128">The following attribute is ignored when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method output is a <xref:System.IO.Stream>:</span></span>  
  
- <span data-ttu-id="d1bf1-129">Wersja: wersja jest zawsze 1,0</span><span class="sxs-lookup"><span data-stu-id="d1bf1-129">version: the version is always 1.0</span></span>  
  
- <span data-ttu-id="d1bf1-130">Typ nośnika: typ nośnika</span><span class="sxs-lookup"><span data-stu-id="d1bf1-130">media-type: the media-type</span></span>  
  
## <a name="escaping-special-characters"></a><span data-ttu-id="d1bf1-131">Znaki specjalne ucieczki</span><span class="sxs-lookup"><span data-stu-id="d1bf1-131">Escaping Special Characters</span></span>  
 <span data-ttu-id="d1bf1-132">`<xsl:text disable-output-escaping>`Tag służy do wskazywania, czy znaki specjalne muszą być wyprowadzane do formularza XML (na przykład przy użyciu `<&lt>` zamiast `"<"` symbolu) lub pozostawione w stanie obecne.</span><span class="sxs-lookup"><span data-stu-id="d1bf1-132">The `<xsl:text disable-output-escaping>` tag is used to indicate whether or not special characters need to be escaped into an XML form (for example, using `<&lt>` in place of the `"<"` symbol) or left in the present condition.</span></span> <span data-ttu-id="d1bf1-133">`disable-output-escaping`Atrybut jest ignorowany podczas przekształcania do <xref:System.Xml.XmlReader> <xref:System.Xml.XmlWriter> obiektu lub i nie ma wpływu na znaki specjalne.</span><span class="sxs-lookup"><span data-stu-id="d1bf1-133">The `disable-output-escaping` attribute is ignored when transforming to an <xref:System.Xml.XmlReader> or <xref:System.Xml.XmlWriter> object and has no effect on special characters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1bf1-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d1bf1-134">See also</span></span>

- [<span data-ttu-id="d1bf1-135">Implementowanie procesora XSLT przy użyciu klasy XslTransform</span><span class="sxs-lookup"><span data-stu-id="d1bf1-135">XslTransform Class Implements the XSLT Processor</span></span>](xsltransform-class-implements-the-xslt-processor.md)
