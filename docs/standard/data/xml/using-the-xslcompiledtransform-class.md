---
title: Używanie klasy XslCompiledTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: f9b074f6-d6f4-49dd-a093-df510bf0cf7b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0537685a91db2c0e323b3f1bda24c6cadc264e34
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47112484"
---
# <a name="using-the-xslcompiledtransform-class"></a><span data-ttu-id="b8d87-102">Używanie klasy XslCompiledTransform</span><span class="sxs-lookup"><span data-stu-id="b8d87-102">Using the XslCompiledTransform Class</span></span>
<span data-ttu-id="b8d87-103"><xref:System.Xml.Xsl.XslCompiledTransform> Klasa jest procesora XSLT programu Microsoft .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b8d87-103">The <xref:System.Xml.Xsl.XslCompiledTransform> class is the Microsoft .NET Framework XSLT processor.</span></span> <span data-ttu-id="b8d87-104">Ta klasa jest używana do kompilowania arkusze stylów i wykonania przekształcenia XSLT.</span><span class="sxs-lookup"><span data-stu-id="b8d87-104">This class is used to compile style sheets and execute XSLT transformations.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b8d87-105">Mimo że ogólną wydajność <xref:System.Xml.Xsl.XslCompiledTransform> klasy jest lepsze niż <xref:System.Xml.Xsl.XslTransform> klasy <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> metody <xref:System.Xml.Xsl.XslCompiledTransform> klasy może działać więcej wolniej niż <xref:System.Xml.Xsl.XslTransform.Load%2A> metody <xref:System.Xml.Xsl.XslTransform> klasy pierwszego czasu jest wywoływana w transformacji.</span><span class="sxs-lookup"><span data-stu-id="b8d87-105">Although the overall performance of the <xref:System.Xml.Xsl.XslCompiledTransform> class is better than the <xref:System.Xml.Xsl.XslTransform> class, the <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> method of the <xref:System.Xml.Xsl.XslCompiledTransform> class might perform more slowly than the <xref:System.Xml.Xsl.XslTransform.Load%2A> method of the <xref:System.Xml.Xsl.XslTransform> class the first time it is called on a transformation.</span></span> <span data-ttu-id="b8d87-106">Jest to spowodowane plik XSLT, ale muszą być skompilowane, zanim został załadowany.</span><span class="sxs-lookup"><span data-stu-id="b8d87-106">This is because the XSLT file must be compiled before it is loaded.</span></span> <span data-ttu-id="b8d87-107">Aby uzyskać więcej informacji, zobacz następujący wpis w blogu: [XslCompiledTransform wolniej niż XslTransform?](https://blogs.msdn.microsoft.com/antosha/2006/07/16/xslcompiledtransform-slower-than-xsltransform/)</span><span class="sxs-lookup"><span data-stu-id="b8d87-107">For more information, see the following blog post: [XslCompiledTransform Slower than XslTransform?](https://blogs.msdn.microsoft.com/antosha/2006/07/16/xslcompiledtransform-slower-than-xsltransform/)</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b8d87-108">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="b8d87-108">In This Section</span></span>  
 [<span data-ttu-id="b8d87-109">Dane wejściowe klasy XslCompiledTransform</span><span class="sxs-lookup"><span data-stu-id="b8d87-109">Inputs to the XslCompiledTransform Class</span></span>](../../../../docs/standard/data/xml/inputs-to-the-xslcompiledtransform-class.md)  
 <span data-ttu-id="b8d87-110">W tym artykule opisano dostępne opcje danych wejściowych XSLT.</span><span class="sxs-lookup"><span data-stu-id="b8d87-110">Describes the available XSLT input options.</span></span>  
  
 [<span data-ttu-id="b8d87-111">Opcje danych wyjściowych klasy XslCompiledTransform</span><span class="sxs-lookup"><span data-stu-id="b8d87-111">Output Options on the XslCompiledTransform Class</span></span>](../../../../docs/standard/data/xml/output-options-on-the-xslcompiledtransform-class.md)  
 <span data-ttu-id="b8d87-112">W tym artykule opisano dostępne opcje wyjściowe XSLT.</span><span class="sxs-lookup"><span data-stu-id="b8d87-112">Describes the available XSLT output options.</span></span>  
  
 [<span data-ttu-id="b8d87-113">Rozpoznawanie zewnętrznych zasobów podczas przetwarzania XSLT</span><span class="sxs-lookup"><span data-stu-id="b8d87-113">Resolving External Resources During XSLT Processing</span></span>](../../../../docs/standard/data/xml/resolving-external-resources-during-xslt-processing.md)  
 <span data-ttu-id="b8d87-114">Omawia przy użyciu <xref:System.Xml.XmlResolver> klasy, aby rozwiązać zasobów zewnętrznych.</span><span class="sxs-lookup"><span data-stu-id="b8d87-114">Discusses using the <xref:System.Xml.XmlResolver> class to resolve external resources.</span></span>  
  
 [<span data-ttu-id="b8d87-115">Rozszerzanie arkuszy stylów XSLT</span><span class="sxs-lookup"><span data-stu-id="b8d87-115">Extending XSLT Style Sheets</span></span>](../../../../docs/standard/data/xml/extending-xslt-style-sheets.md)  
 <span data-ttu-id="b8d87-116">W tym artykule omówiono, jak XSLT rozszerzenia są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="b8d87-116">Discusses how XSLT extensions are supported.</span></span>  
  
|||  
|-|-|  
|[<span data-ttu-id="b8d87-117">Odwracalne błędy XSLT</span><span class="sxs-lookup"><span data-stu-id="b8d87-117">Recoverable XSLT Errors</span></span>](../../../../docs/standard/data/xml/recoverable-xslt-errors.md)|<span data-ttu-id="b8d87-118">Wyświetla listę zachowań uznaniowych dozwolone przez XSLT World Wide Web Consortium (W3C) 1.0 zalecenia i w tym artykule opisano, jak te zachowania są obsługiwane przez <xref:System.Xml.Xsl.XslCompiledTransform> klasy.</span><span class="sxs-lookup"><span data-stu-id="b8d87-118">Lists discretionary behaviors allowed by the World Wide Web Consortium (W3C) XSLT 1.0 recommendation and describes how these behaviors are handled by the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>|  
|[<span data-ttu-id="b8d87-119">Instrukcje: Przekształcanie fragmentu węzła</span><span class="sxs-lookup"><span data-stu-id="b8d87-119">How to: Transform a Node Fragment</span></span>](../../../../docs/standard/data/xml/how-to-transform-a-node-fragment.md)|<span data-ttu-id="b8d87-120">Opisuje sposób Przekształcanie fragmentu węzła.</span><span class="sxs-lookup"><span data-stu-id="b8d87-120">Describes how to transform a node fragment.</span></span>|  
  
## <a name="related-sections"></a><span data-ttu-id="b8d87-121">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="b8d87-121">Related Sections</span></span>  
 [<span data-ttu-id="b8d87-122">Migrowanie z klasy XslTransform</span><span class="sxs-lookup"><span data-stu-id="b8d87-122">Migrating From the XslTransform Class</span></span>](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)  
 <span data-ttu-id="b8d87-123">W tym artykule omówiono sposób migracji kodu z <xref:System.Xml.Xsl.XslTransform> klasy</span><span class="sxs-lookup"><span data-stu-id="b8d87-123">Discusses how to migrate code from the <xref:System.Xml.Xsl.XslTransform> class</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8d87-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b8d87-124">See also</span></span>

- <xref:System.Xml.Xsl.XsltSettings>  
- <xref:System.Xml.Xsl.XsltMessageEncounteredEventArgs>
