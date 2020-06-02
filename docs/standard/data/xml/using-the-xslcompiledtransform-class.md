---
title: Używanie klasy XslCompiledTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: f9b074f6-d6f4-49dd-a093-df510bf0cf7b
ms.openlocfilehash: 8705b4c6324ce20a1f37d3ee864ab494adcdd6a5
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84281776"
---
# <a name="using-the-xslcompiledtransform-class"></a><span data-ttu-id="4734b-102">Używanie klasy XslCompiledTransform</span><span class="sxs-lookup"><span data-stu-id="4734b-102">Using the XslCompiledTransform Class</span></span>
<span data-ttu-id="4734b-103"><xref:System.Xml.Xsl.XslCompiledTransform>Klasa jest procesorem XSLT środowiska Microsoft .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4734b-103">The <xref:System.Xml.Xsl.XslCompiledTransform> class is the Microsoft .NET Framework XSLT processor.</span></span> <span data-ttu-id="4734b-104">Ta klasa jest używana do kompilowania arkuszy stylów i wykonywania transformacji XSLT.</span><span class="sxs-lookup"><span data-stu-id="4734b-104">This class is used to compile style sheets and execute XSLT transformations.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4734b-105">Chociaż ogólna wydajność <xref:System.Xml.Xsl.XslCompiledTransform> klasy jest lepsza niż <xref:System.Xml.Xsl.XslTransform> Klasa, <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> Metoda <xref:System.Xml.Xsl.XslCompiledTransform> klasy może działać wolniej niż <xref:System.Xml.Xsl.XslTransform.Load%2A> Metoda <xref:System.Xml.Xsl.XslTransform> klasy, gdy jest wywoływana po raz pierwszy.</span><span class="sxs-lookup"><span data-stu-id="4734b-105">Although the overall performance of the <xref:System.Xml.Xsl.XslCompiledTransform> class is better than the <xref:System.Xml.Xsl.XslTransform> class, the <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> method of the <xref:System.Xml.Xsl.XslCompiledTransform> class might perform more slowly than the <xref:System.Xml.Xsl.XslTransform.Load%2A> method of the <xref:System.Xml.Xsl.XslTransform> class the first time it is called on a transformation.</span></span> <span data-ttu-id="4734b-106">Jest to spowodowane tym, że plik XSLT musi być skompilowany przed załadowaniem.</span><span class="sxs-lookup"><span data-stu-id="4734b-106">This is because the XSLT file must be compiled before it is loaded.</span></span> <span data-ttu-id="4734b-107">Aby uzyskać więcej informacji, zobacz następujący wpis w blogu: [XslCompiledTransform wolniej niż XslTransform?](https://docs.microsoft.com/archive/blogs/antosha/xslcompiledtransform-slower-than-xsltransform)</span><span class="sxs-lookup"><span data-stu-id="4734b-107">For more information, see the following blog post: [XslCompiledTransform Slower than XslTransform?](https://docs.microsoft.com/archive/blogs/antosha/xslcompiledtransform-slower-than-xsltransform)</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4734b-108">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="4734b-108">In This Section</span></span>  
 [<span data-ttu-id="4734b-109">Dane wejściowe klasy XslCompiledTransform</span><span class="sxs-lookup"><span data-stu-id="4734b-109">Inputs to the XslCompiledTransform Class</span></span>](inputs-to-the-xslcompiledtransform-class.md)  
 <span data-ttu-id="4734b-110">Opisuje dostępne opcje wejściowe XSLT.</span><span class="sxs-lookup"><span data-stu-id="4734b-110">Describes the available XSLT input options.</span></span>  
  
 [<span data-ttu-id="4734b-111">Opcje danych wyjściowych klasy XslCompiledTransform</span><span class="sxs-lookup"><span data-stu-id="4734b-111">Output Options on the XslCompiledTransform Class</span></span>](output-options-on-the-xslcompiledtransform-class.md)  
 <span data-ttu-id="4734b-112">Opisuje dostępne opcje wyjściowe XSLT.</span><span class="sxs-lookup"><span data-stu-id="4734b-112">Describes the available XSLT output options.</span></span>  
  
 [<span data-ttu-id="4734b-113">Rozpoznawanie zewnętrznych zasobów podczas przetwarzania XSLT</span><span class="sxs-lookup"><span data-stu-id="4734b-113">Resolving External Resources During XSLT Processing</span></span>](resolving-external-resources-during-xslt-processing.md)  
 <span data-ttu-id="4734b-114">W tym artykule omówiono użycie <xref:System.Xml.XmlResolver> klasy do rozpoznawania zasobów zewnętrznych.</span><span class="sxs-lookup"><span data-stu-id="4734b-114">Discusses using the <xref:System.Xml.XmlResolver> class to resolve external resources.</span></span>  
  
 [<span data-ttu-id="4734b-115">Rozszerzanie arkuszy stylów XSLT</span><span class="sxs-lookup"><span data-stu-id="4734b-115">Extending XSLT Style Sheets</span></span>](extending-xslt-style-sheets.md)  
 <span data-ttu-id="4734b-116">Omawia, w jaki sposób rozszerzenia XSLT są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="4734b-116">Discusses how XSLT extensions are supported.</span></span>  
  
|||  
|-|-|  
|[<span data-ttu-id="4734b-117">Odwracalne błędy XSLT</span><span class="sxs-lookup"><span data-stu-id="4734b-117">Recoverable XSLT Errors</span></span>](recoverable-xslt-errors.md)|<span data-ttu-id="4734b-118">Wyświetla listę arbitralnych zachowań dozwolonych przez organizacja World Wide Web Consortium (W3C) 1,0 zalecenia i opisuje sposób obsługi tych zachowań przez <xref:System.Xml.Xsl.XslCompiledTransform> klasę.</span><span class="sxs-lookup"><span data-stu-id="4734b-118">Lists discretionary behaviors allowed by the World Wide Web Consortium (W3C) XSLT 1.0 recommendation and describes how these behaviors are handled by the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>|  
|[<span data-ttu-id="4734b-119">Instrukcje: Przekształcanie fragmentu węzła</span><span class="sxs-lookup"><span data-stu-id="4734b-119">How to: Transform a Node Fragment</span></span>](how-to-transform-a-node-fragment.md)|<span data-ttu-id="4734b-120">Opisuje sposób przekształcania fragmentu węzła.</span><span class="sxs-lookup"><span data-stu-id="4734b-120">Describes how to transform a node fragment.</span></span>|  
  
## <a name="related-sections"></a><span data-ttu-id="4734b-121">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="4734b-121">Related Sections</span></span>  
 [<span data-ttu-id="4734b-122">Migrowanie z klasy XslTransform</span><span class="sxs-lookup"><span data-stu-id="4734b-122">Migrating From the XslTransform Class</span></span>](migrating-from-the-xsltransform-class.md)  
 <span data-ttu-id="4734b-123">Omawia sposób migrowania kodu z <xref:System.Xml.Xsl.XslTransform> klasy</span><span class="sxs-lookup"><span data-stu-id="4734b-123">Discusses how to migrate code from the <xref:System.Xml.Xsl.XslTransform> class</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4734b-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4734b-124">See also</span></span>

- <xref:System.Xml.Xsl.XsltSettings>
- <xref:System.Xml.Xsl.XsltMessageEncounteredEventArgs>
