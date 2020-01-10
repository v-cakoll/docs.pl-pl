---
title: Rozpoznawanie zewnętrznych zasobów podczas przetwarzania XSLT
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 3a59d31c-0ec5-4de6-a2a9-558531c8116e
ms.openlocfilehash: 58407d5f0c6e602af15f5b19b9a19cc6379b9af7
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710287"
---
# <a name="resolving-external-resources-during-xslt-processing"></a><span data-ttu-id="29278-102">Rozpoznawanie zewnętrznych zasobów podczas przetwarzania XSLT</span><span class="sxs-lookup"><span data-stu-id="29278-102">Resolving External Resources During XSLT Processing</span></span>
<span data-ttu-id="29278-103">Podczas transformacji XSLT występuje kilka razy, gdy konieczne jest rozwiązanie zasobów zewnętrznych.</span><span class="sxs-lookup"><span data-stu-id="29278-103">There are several times during an XSLT transformation when you may need to resolve external resources.</span></span>  
  
## <a name="using-the-xmlresolver-class"></a><span data-ttu-id="29278-104">Korzystanie z klasy XmlResolver</span><span class="sxs-lookup"><span data-stu-id="29278-104">Using the XmlResolver Class</span></span>  
 <span data-ttu-id="29278-105">Klasa <xref:System.Xml.XmlResolver> jest używana do rozpoznawania zasobów zewnętrznych.</span><span class="sxs-lookup"><span data-stu-id="29278-105">The <xref:System.Xml.XmlResolver> class is used to resolve external resources.</span></span> <span data-ttu-id="29278-106">W poniższej tabeli opisano, kiedy <xref:System.Xml.XmlResolver> jest uwzględniana podczas przetwarzania XSLT.</span><span class="sxs-lookup"><span data-stu-id="29278-106">The following table describes when the <xref:System.Xml.XmlResolver> becomes involved during XSLT processing.</span></span>  
  
|<span data-ttu-id="29278-107">Zadanie XSLT</span><span class="sxs-lookup"><span data-stu-id="29278-107">XSLT task</span></span>|<span data-ttu-id="29278-108">Do czego służy element XmlResolver</span><span class="sxs-lookup"><span data-stu-id="29278-108">What the XmlResolver is used for</span></span>|  
|---------------|--------------------------------------|  
|<span data-ttu-id="29278-109">Kompiluj arkusz stylów.</span><span class="sxs-lookup"><span data-stu-id="29278-109">Compile the style sheet.</span></span>|<span data-ttu-id="29278-110">Rozpoznanie identyfikatora URI arkusza stylów.</span><span class="sxs-lookup"><span data-stu-id="29278-110">Resolve the URI of the style sheet.</span></span><br /><br /> <span data-ttu-id="29278-111">\- i -</span><span class="sxs-lookup"><span data-stu-id="29278-111">-and-</span></span><br /><br /> <span data-ttu-id="29278-112">Rozpoznaj odwołania do identyfikatorów URI w dowolnych `xsl:import` lub `xsl:include` elementów.</span><span class="sxs-lookup"><span data-stu-id="29278-112">Resolve URI references in any `xsl:import` or `xsl:include` elements.</span></span>|  
|<span data-ttu-id="29278-113">Wykonaj arkusz stylów.</span><span class="sxs-lookup"><span data-stu-id="29278-113">Execute the style sheet.</span></span>|<span data-ttu-id="29278-114">Rozpoznanie identyfikatora URI dokumentu kontekstowego.</span><span class="sxs-lookup"><span data-stu-id="29278-114">Resolve the URI of the context document.</span></span><br /><br /> <span data-ttu-id="29278-115">\- i -</span><span class="sxs-lookup"><span data-stu-id="29278-115">-and-</span></span><br /><br /> <span data-ttu-id="29278-116">Rozwiąż odwołania do identyfikatorów URI w dowolnych funkcjach `document()` XSLT.</span><span class="sxs-lookup"><span data-stu-id="29278-116">Resolve URI references in any XSLT `document()` functions.</span></span>|  
  
 <span data-ttu-id="29278-117">Metody <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> i <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> obejmują przeciążenia przyjmujące obiekt <xref:System.Xml.XmlResolver> jako jeden z argumentów.</span><span class="sxs-lookup"><span data-stu-id="29278-117">The <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> and <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> methods include overloads that take an <xref:System.Xml.XmlResolver> object as one of its arguments.</span></span> <span data-ttu-id="29278-118">Jeśli nie określono <xref:System.Xml.XmlResolver>, zostanie użyta domyślna <xref:System.Xml.XmlUrlResolver> bez poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="29278-118">If an <xref:System.Xml.XmlResolver> is not specified, a default <xref:System.Xml.XmlUrlResolver> with no credentials is used.</span></span>  
  
 <span data-ttu-id="29278-119">Na poniższej liście opisano, kiedy warto określić obiekt <xref:System.Xml.XmlResolver>:</span><span class="sxs-lookup"><span data-stu-id="29278-119">The following list describes when you may want to specify an <xref:System.Xml.XmlResolver> object:</span></span>  
  
- <span data-ttu-id="29278-120">Jeśli proces XSLT musi uzyskać dostęp do zasobu sieciowego, który wymaga uwierzytelnienia, można użyć <xref:System.Xml.XmlResolver> z niezbędnymi poświadczeniami.</span><span class="sxs-lookup"><span data-stu-id="29278-120">If the XSLT process needs to access a network resource that requires authentication, you can use an <xref:System.Xml.XmlResolver> with the necessary credentials.</span></span>  
  
- <span data-ttu-id="29278-121">Jeśli chcesz ograniczyć zasoby, do których proces XSLT może uzyskać dostęp, możesz użyć <xref:System.Xml.XmlSecureResolver> z prawidłowym zestawem uprawnień.</span><span class="sxs-lookup"><span data-stu-id="29278-121">If you want to restrict the resources that the XSLT process can access, you can use an <xref:System.Xml.XmlSecureResolver> with the correct permission set.</span></span> <span data-ttu-id="29278-122">Użyj klasy <xref:System.Xml.XmlSecureResolver>, jeśli konieczne jest otwarcie zasobu, który nie jest kontrolowany lub że nie jest zaufany.</span><span class="sxs-lookup"><span data-stu-id="29278-122">Use the <xref:System.Xml.XmlSecureResolver> class if you need to open a resource that you do not control, or that is untrusted.</span></span>  
  
- <span data-ttu-id="29278-123">Aby dostosować zachowanie, można zaimplementować własną klasę <xref:System.Xml.XmlResolver> i używać jej do rozwiązywania zasobów.</span><span class="sxs-lookup"><span data-stu-id="29278-123">If you want to customize behavior, you can implement your own <xref:System.Xml.XmlResolver> class and use it to resolve resources.</span></span>  
  
- <span data-ttu-id="29278-124">Jeśli chcesz się upewnić, że nie ma dostępu do zasobów zewnętrznych, możesz określić `null` dla argumentu <xref:System.Xml.XmlResolver>.</span><span class="sxs-lookup"><span data-stu-id="29278-124">If you want to ensure that no external resources are accessed, you can specify `null` for the <xref:System.Xml.XmlResolver> argument.</span></span>  
  
## <a name="example"></a><span data-ttu-id="29278-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="29278-125">Example</span></span>  
 <span data-ttu-id="29278-126">Poniższy przykład kompiluje arkusz stylów, który jest przechowywany w zasobów sieciowych.</span><span class="sxs-lookup"><span data-stu-id="29278-126">The following example compiles a style sheet that is stored on a network resource.</span></span> <span data-ttu-id="29278-127">Obiekt <xref:System.Xml.XmlUrlResolver> określa poświadczenia niezbędne do uzyskania dostępu do arkusza stylów.</span><span class="sxs-lookup"><span data-stu-id="29278-127">An <xref:System.Xml.XmlUrlResolver> object specifies the credentials necessary to access the style sheet.</span></span>  
  
 [!code-csharp[XslCompiledTransform.Load#11](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Load/CS/Xslt_Load_v2.cs#11)]
 [!code-vb[XslCompiledTransform.Load#11](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Load/VB/Xslt_Load_v2.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="29278-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="29278-128">See also</span></span>

- <xref:System.Xml.Xsl.XslCompiledTransform>
- <xref:System.Xml.Xsl.XsltSettings>
- [<span data-ttu-id="29278-129">Przekształcenia XSLT</span><span class="sxs-lookup"><span data-stu-id="29278-129">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)
