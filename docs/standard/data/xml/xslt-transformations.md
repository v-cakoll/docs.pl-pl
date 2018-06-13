---
title: Przekształcenia XSLT
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 202f8820-224c-494f-b61e-cd127eac6e03
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 922de11567af9409265ee18bfa6a2637951c57c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33571004"
---
# <a name="xslt-transformations"></a><span data-ttu-id="d03f1-102">Przekształcenia XSLT</span><span class="sxs-lookup"><span data-stu-id="d03f1-102">XSLT Transformations</span></span>
<span data-ttu-id="d03f1-103">Extensible Stylesheet Language Transformation (XSLT) pozwala na przekształcanie zawartości dokumentu XML źródła do innego dokumentu, która różni się w formacie lub struktury.</span><span class="sxs-lookup"><span data-stu-id="d03f1-103">The Extensible Stylesheet Language Transformation (XSLT) lets you transform the content of a source XML document into another document that is different in format or structure.</span></span> <span data-ttu-id="d03f1-104">Na przykład można użyć XSLT do transformacji XML w kodzie HTML do użytku w witrynie sieci Web lub aby przekształcić go do dokumentu, który zawiera tylko te pola, które są wymagane przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="d03f1-104">For example, you can use XSLT to transform XML into HTML for use on a Web site or to transform it into a document that contains only the fields required by an application.</span></span> <span data-ttu-id="d03f1-105">Ten proces transformacji jest określona przez [zalecenie W3C transformacji XSL (XSLT) w wersji 1.0](https://www.w3.org/TR/xslt-10/).</span><span class="sxs-lookup"><span data-stu-id="d03f1-105">This transformation process is specified by the [W3C XSL Transformations (XSLT) Version 1.0 recommendation](https://www.w3.org/TR/xslt-10/).</span></span>  
  
 <span data-ttu-id="d03f1-106"><xref:System.Xml.Xsl.XslCompiledTransform> Klasa jest procesorze XSLT w .NET.</span><span class="sxs-lookup"><span data-stu-id="d03f1-106">The <xref:System.Xml.Xsl.XslCompiledTransform> class is the XSLT processor in .NET.</span></span> <span data-ttu-id="d03f1-107"><xref:System.Xml.Xsl.XslCompiledTransform> Klasy obsługuje [zalecenie W3C XSLT 1.0](https://www.w3.org/TR/xslt-10/).</span><span class="sxs-lookup"><span data-stu-id="d03f1-107">The <xref:System.Xml.Xsl.XslCompiledTransform> class supports the [W3C XSLT 1.0 recommendation](https://www.w3.org/TR/xslt-10/).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d03f1-108"><xref:System.Xml.Xsl.XslTransform> Klasa jest przestarzałe w programie .NET Framework w wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="d03f1-108">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in .NET Framework version 2.0.</span></span> <span data-ttu-id="d03f1-109"><xref:System.Xml.Xsl.XslCompiledTransform> Klasa jest implementacją nowego aparatu XSLT.</span><span class="sxs-lookup"><span data-stu-id="d03f1-109">The <xref:System.Xml.Xsl.XslCompiledTransform> class is a new implementation of the XSLT engine.</span></span> <span data-ttu-id="d03f1-110">Zawiera ulepszenia wydajności i nowe funkcje zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="d03f1-110">It includes performance improvements and new security features.</span></span> <span data-ttu-id="d03f1-111">Zalecaną praktyką jest utworzenie aplikacji XSLT przy użyciu <xref:System.Xml.Xsl.XslCompiledTransform> klasy.</span><span class="sxs-lookup"><span data-stu-id="d03f1-111">The recommended practice is to create XSLT applications using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d03f1-112">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="d03f1-112">In This Section</span></span>  
 [<span data-ttu-id="d03f1-113">Używanie klasy XslCompiledTransform</span><span class="sxs-lookup"><span data-stu-id="d03f1-113">Using the XslCompiledTransform Class</span></span>](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)  
 <span data-ttu-id="d03f1-114">Zawiera informacje na temat używania <xref:System.Xml.Xsl.XslCompiledTransform> klasy.</span><span class="sxs-lookup"><span data-stu-id="d03f1-114">Provides information on using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
 [<span data-ttu-id="d03f1-115">Migrowanie z klasy XslTransform</span><span class="sxs-lookup"><span data-stu-id="d03f1-115">Migrating From the XslTransform Class</span></span>](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)  
 <span data-ttu-id="d03f1-116">W tym artykule omówiono sposób migracji kod z <xref:System.Xml.Xsl.XslTransform> klasy.</span><span class="sxs-lookup"><span data-stu-id="d03f1-116">Discusses how to migrate code from the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
 [<span data-ttu-id="d03f1-117">Kompilator XSLT (xsltc.exe)</span><span class="sxs-lookup"><span data-stu-id="d03f1-117">XSLT Compiler (xsltc.exe)</span></span>](../../../../docs/standard/data/xml/xslt-compiler-xsltc-exe.md)  
 <span data-ttu-id="d03f1-118">Zawiera informacje na temat używania kompilatora XSLT.</span><span class="sxs-lookup"><span data-stu-id="d03f1-118">Provides information on using the XSLT compiler.</span></span>  
  
 [<span data-ttu-id="d03f1-119">Przekształcenia XSLT przy użyciu klasy XslTransform</span><span class="sxs-lookup"><span data-stu-id="d03f1-119">XSLT Transformations with the XslTransform Class</span></span>](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
 <span data-ttu-id="d03f1-120">Zawiera informacje na temat używania <xref:System.Xml.Xsl.XslTransform> klasy.</span><span class="sxs-lookup"><span data-stu-id="d03f1-120">Provides information on using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="d03f1-121">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="d03f1-121">Reference</span></span>  
 <xref:System.Xml.Xsl.XslCompiledTransform>  
 <xref:System.Xml.Xsl.XsltArgumentList>  
 <xref:System.Xml.Xsl.XsltSettings>  
  
## <a name="related-sections"></a><span data-ttu-id="d03f1-122">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="d03f1-122">Related Sections</span></span>  
 [<span data-ttu-id="d03f1-123">Dokumenty i dane XML</span><span class="sxs-lookup"><span data-stu-id="d03f1-123">XML Documents and Data</span></span>](../../../../docs/standard/data/xml/index.md)
