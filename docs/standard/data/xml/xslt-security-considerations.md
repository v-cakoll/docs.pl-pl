---
title: "Zagadnienia dotyczące zabezpieczeń XSLT"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fea695be-617c-4977-9567-140e820436fc
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 7388bbc388dd46a30486a2300150bc9d1566593e
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="xslt-security-considerations"></a><span data-ttu-id="ddea4-102">Zagadnienia dotyczące zabezpieczeń XSLT</span><span class="sxs-lookup"><span data-stu-id="ddea4-102">XSLT Security Considerations</span></span>
<span data-ttu-id="ddea4-103">Język XSLT zawiera bogaty zestaw funkcji, które zapewniają dużą możliwościach i elastyczności.</span><span class="sxs-lookup"><span data-stu-id="ddea4-103">The XSLT language has a rich set of features that give you a great deal of power and flexibility.</span></span> <span data-ttu-id="ddea4-104">Zawiera wiele funkcji, które jest to przydatne, mogą być również wykorzystywane przez zewnętrznych źródeł.</span><span class="sxs-lookup"><span data-stu-id="ddea4-104">It includes many features that, while useful, could also be exploited by outside sources.</span></span> <span data-ttu-id="ddea4-105">Aby można było używać bezpiecznie XSLT, muszą zrozumieć typy problemy z zabezpieczeniami, które użytkowania XSLT i podstawowe strategie, których można użyć, aby ograniczyć te zagrożenia.</span><span class="sxs-lookup"><span data-stu-id="ddea4-105">In order to use XSLT safely, you must understand the types of security issues that arise when using XSLT, and the basic strategies that you can employ to mitigate these risks.</span></span>  
  
## <a name="xslt-extensions"></a><span data-ttu-id="ddea4-106">Rozszerzenia XSLT</span><span class="sxs-lookup"><span data-stu-id="ddea4-106">XSLT Extensions</span></span>  
 <span data-ttu-id="ddea4-107">Dwa popularne rozszerzenia XSLT są obiektami skryptów i rozszerzenia arkusza stylów.</span><span class="sxs-lookup"><span data-stu-id="ddea4-107">Two popular XSLT extensions are style sheet scripting and extension objects.</span></span> <span data-ttu-id="ddea4-108">Te rozszerzenia umożliwiają procesorze XSLT do wykonywania kodu.</span><span class="sxs-lookup"><span data-stu-id="ddea4-108">These extensions allow the XSLT processor to execute code.</span></span>  
  
-   <span data-ttu-id="ddea4-109">Obiekty rozszerzenia dodać możliwości programowania do transformacji XSL.</span><span class="sxs-lookup"><span data-stu-id="ddea4-109">Extension objects add programming capabilities to XSL transformations.</span></span>  
  
-   <span data-ttu-id="ddea4-110">Skrypty można ją osadzić w arkuszu stylów przy użyciu `msxsl:script` elementu rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="ddea4-110">Scripts can be embedded in the style sheet using the `msxsl:script` extension element.</span></span>  
  
### <a name="extension-objects"></a><span data-ttu-id="ddea4-111">Rozszerzenia obiektów</span><span class="sxs-lookup"><span data-stu-id="ddea4-111">Extension Objects</span></span>  
 <span data-ttu-id="ddea4-112">Obiekty rozszerzenia są dodawane przy użyciu <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="ddea4-112">Extension objects are added using the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span> <span data-ttu-id="ddea4-113">Zestaw uprawnień FullTrust jest wymagany do obsługi obiektów rozszerzeń.</span><span class="sxs-lookup"><span data-stu-id="ddea4-113">The FullTrust permission set is required to support extension objects.</span></span> <span data-ttu-id="ddea4-114">Dzięki temu, że podwyższenie poziomu uprawnień nie odbywa się podczas wykonywania kodu obiektu rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="ddea4-114">This ensures that elevation of permissions does not happen when extension object code is executed.</span></span> <span data-ttu-id="ddea4-115">Próba wywołania <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> metody bez powoduje uprawnień FullTrust został zgłoszony wyjątek zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="ddea4-115">Attempting to call the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method without FullTrust permissions results in a security exception being thrown.</span></span>  
  
### <a name="style-sheet-scripts"></a><span data-ttu-id="ddea4-116">Skrypty arkusza stylów</span><span class="sxs-lookup"><span data-stu-id="ddea4-116">Style Sheet Scripts</span></span>  
 <span data-ttu-id="ddea4-117">Skrypty mogą być osadzone w arkuszu stylów przy użyciu `msxsl:script` elementu rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="ddea4-117">Scripts can be embedded in a style sheet using the `msxsl:script` extension element.</span></span> <span data-ttu-id="ddea4-118">Obsługa skryptów jest funkcją opcjonalną na <xref:System.Xml.Xsl.XslCompiledTransform> klasy, która jest domyślnie wyłączona.</span><span class="sxs-lookup"><span data-stu-id="ddea4-118">Script support is an optional feature on the <xref:System.Xml.Xsl.XslCompiledTransform> class that is disabled by default.</span></span> <span data-ttu-id="ddea4-119">Może być włączona obsługa skryptów przez ustawienie <xref:System.Xml.Xsl.XsltSettings.EnableScript%2A?displayProperty=nameWithType> właściwości `true` i przekazywanie <xref:System.Xml.Xsl.XsltSettings> do obiektu <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="ddea4-119">Scripting can be enabled by setting the <xref:System.Xml.Xsl.XsltSettings.EnableScript%2A?displayProperty=nameWithType> property to `true` and passing the <xref:System.Xml.Xsl.XsltSettings> object to the <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> method.</span></span>  
  
#### <a name="guidelines"></a><span data-ttu-id="ddea4-120">Wytyczne dotyczące</span><span class="sxs-lookup"><span data-stu-id="ddea4-120">Guidelines</span></span>  
 <span data-ttu-id="ddea4-121">Włącz wykonywanie skryptów, tylko gdy arkusz stylów pochodzi z zaufanego źródła.</span><span class="sxs-lookup"><span data-stu-id="ddea4-121">Enable scripting only when the style sheet comes from a trusted source.</span></span> <span data-ttu-id="ddea4-122">Jeśli nie można zweryfikować źródła arkusza stylów lub arkusz stylów nie pochodzi z zaufanego źródła, Przekaż `null` argumentu ustawienia XSLT.</span><span class="sxs-lookup"><span data-stu-id="ddea4-122">If you cannot verify the source of the style sheet, or if the style sheet does not come from a trusted source, pass in `null` for the XSLT settings argument.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="ddea4-123">Zasoby zewnętrzne</span><span class="sxs-lookup"><span data-stu-id="ddea4-123">External Resources</span></span>  
 <span data-ttu-id="ddea4-124">Język XSLT zawiera funkcje, takie jak `xsl:import`, `xsl:include`, lub `document()` funkcja, gdy procesor musi rozpoznać odwołań do identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="ddea4-124">The XSLT language has features such as `xsl:import`, `xsl:include`, or the `document()` function, where the processor needs to resolve URI references.</span></span> <span data-ttu-id="ddea4-125"><xref:System.Xml.XmlResolver> Klasa jest używana do rozpoznawania zasobów zewnętrznych.</span><span class="sxs-lookup"><span data-stu-id="ddea4-125">The <xref:System.Xml.XmlResolver> class is used to resolve external resources.</span></span> <span data-ttu-id="ddea4-126">Zasoby zewnętrzne mogą muszą zostać rozwiązane w dwóch następujących przypadków:</span><span class="sxs-lookup"><span data-stu-id="ddea4-126">External resources may need to be resolved in the following two cases:</span></span>  
  
-   <span data-ttu-id="ddea4-127">W przypadku kompilowania kodu arkusz stylów <xref:System.Xml.XmlResolver> służy do `xsl:import` i `xsl:include` rozpoznawania.</span><span class="sxs-lookup"><span data-stu-id="ddea4-127">When compiling a style sheet, the <xref:System.Xml.XmlResolver> is used for `xsl:import` and `xsl:include` resolution.</span></span>  
  
-   <span data-ttu-id="ddea4-128">Podczas wykonywania transformacji, <xref:System.Xml.XmlResolver> jest używany do rozpoznawania `document()` funkcji.</span><span class="sxs-lookup"><span data-stu-id="ddea4-128">When executing the transformation, the <xref:System.Xml.XmlResolver> is used to resolve the `document()` function.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ddea4-129">`document()` Funkcja jest domyślnie wyłączony na <xref:System.Xml.Xsl.XslCompiledTransform> klasy.</span><span class="sxs-lookup"><span data-stu-id="ddea4-129">The `document()` function is disabled by default on the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="ddea4-130">Ta funkcja może być włączona <xref:System.Xml.Xsl.XsltSettings.EnableDocumentFunction%2A?displayProperty=nameWithType> właściwości `true` i przekazywanie <xref:System.Xml.Xsl.XsltSettings> do obiektu <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="ddea4-130">This feature can be enabled by setting the <xref:System.Xml.Xsl.XsltSettings.EnableDocumentFunction%2A?displayProperty=nameWithType> property to `true` and passing the <xref:System.Xml.Xsl.XsltSettings> object to the <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> method.</span></span>  
  
 <span data-ttu-id="ddea4-131"><xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> i <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metody każdego obejmują przeciążenia, które akceptują <xref:System.Xml.XmlResolver> jako jeden z jego argumentów.</span><span class="sxs-lookup"><span data-stu-id="ddea4-131">The <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> and <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> methods each include overloads that accept an <xref:System.Xml.XmlResolver> as one of its arguments.</span></span> <span data-ttu-id="ddea4-132">Jeśli <xref:System.Xml.XmlResolver> nie zostanie określony, domyślnie <xref:System.Xml.XmlUrlResolver> bez poświadczeń jest używany.</span><span class="sxs-lookup"><span data-stu-id="ddea4-132">If an <xref:System.Xml.XmlResolver> is not specified, a default <xref:System.Xml.XmlUrlResolver> with no credentials is used.</span></span>  
  
#### <a name="guidelines"></a><span data-ttu-id="ddea4-133">Wytyczne dotyczące</span><span class="sxs-lookup"><span data-stu-id="ddea4-133">Guidelines</span></span>  
 <span data-ttu-id="ddea4-134">Włącz `document()` działa tylko wtedy, gdy arkusz stylów pochodzi z zaufanego źródła.</span><span class="sxs-lookup"><span data-stu-id="ddea4-134">Enable the `document()` function only when the style sheet comes from a trusted source.</span></span>  
  
 <span data-ttu-id="ddea4-135">Na poniższej liście opisano, kiedy można określić <xref:System.Xml.XmlResolver> obiektu:</span><span class="sxs-lookup"><span data-stu-id="ddea4-135">The following list describes when you may want to specify an <xref:System.Xml.XmlResolver> object:</span></span>  
  
-   <span data-ttu-id="ddea4-136">Jeśli proces XSLT wymaga dostępu do zasobu sieciowego, która wymaga uwierzytelnienia, można użyć <xref:System.Xml.XmlResolver> niezbędne poświadczenia.</span><span class="sxs-lookup"><span data-stu-id="ddea4-136">If the XSLT process needs to access a network resource that requires authentication, you can use an <xref:System.Xml.XmlResolver> with the necessary credentials.</span></span>  
  
-   <span data-ttu-id="ddea4-137">Jeśli chcesz ograniczyć zasoby, do których dostęp procesu XSLT, możesz użyć <xref:System.Xml.XmlSecureResolver> ustawienie odpowiednie uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="ddea4-137">If you want to restrict the resources that the XSLT process can access, you can use an <xref:System.Xml.XmlSecureResolver> with the correct permission set.</span></span> <span data-ttu-id="ddea4-138">Użyj <xref:System.Xml.XmlSecureResolver> klasy, jeśli trzeba otworzyć zasobu, która kontroluje, lub niezaufanych.</span><span class="sxs-lookup"><span data-stu-id="ddea4-138">Use the <xref:System.Xml.XmlSecureResolver> class if you need to open a resource that you do not control, or that is untrusted.</span></span>  
  
-   <span data-ttu-id="ddea4-139">Jeśli chcesz dostosować zachowanie, można zaimplementować własne <xref:System.Xml.XmlResolver> klasy i użyć go do rozwiązania zasobów.</span><span class="sxs-lookup"><span data-stu-id="ddea4-139">If you want to customize behavior, you can implement your own <xref:System.Xml.XmlResolver> class and use it to resolve resources.</span></span>  
  
-   <span data-ttu-id="ddea4-140">Jeśli chcesz upewnić się, że nie zewnętrzne zasoby są dostępne, można określić `null` dla <xref:System.Xml.XmlResolver> argumentu.</span><span class="sxs-lookup"><span data-stu-id="ddea4-140">If you want to ensure that no external resources are accessed, you can specify `null` for the <xref:System.Xml.XmlResolver> argument.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddea4-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ddea4-141">See Also</span></span>  
 [<span data-ttu-id="ddea4-142">Przekształcenia XSLT</span><span class="sxs-lookup"><span data-stu-id="ddea4-142">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)  
 [<span data-ttu-id="ddea4-143">Rozpoznawanie zewnętrznych zasobów podczas przetwarzania XSLT</span><span class="sxs-lookup"><span data-stu-id="ddea4-143">Resolving External Resources During XSLT Processing</span></span>](../../../../docs/standard/data/xml/resolving-external-resources-during-xslt-processing.md)  
 [<span data-ttu-id="ddea4-144">Zabezpieczenia dostępu kodu</span><span class="sxs-lookup"><span data-stu-id="ddea4-144">Code Access Security</span></span>](http://msdn.microsoft.com/library/23a20143-241d-4fe5-9d9f-3933fd594c03)
