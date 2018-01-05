---
title: "Rozpoznawanie zewnętrznych zasobów podczas przetwarzania XSLT"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 3a59d31c-0ec5-4de6-a2a9-558531c8116e
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2bb115e14f8ff5d1065d87335d4d9021bd32ddd1
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="resolving-external-resources-during-xslt-processing"></a><span data-ttu-id="11cc1-102">Rozpoznawanie zewnętrznych zasobów podczas przetwarzania XSLT</span><span class="sxs-lookup"><span data-stu-id="11cc1-102">Resolving External Resources During XSLT Processing</span></span>
<span data-ttu-id="11cc1-103">Istnieje kilka razy podczas transformację XSLT, gdy trzeba rozwiązać zasobów zewnętrznych.</span><span class="sxs-lookup"><span data-stu-id="11cc1-103">There are several times during an XSLT transformation when you may need to resolve external resources.</span></span>  
  
## <a name="using-the-xmlresolver-class"></a><span data-ttu-id="11cc1-104">Używanie klasy element XmlResolver</span><span class="sxs-lookup"><span data-stu-id="11cc1-104">Using the XmlResolver Class</span></span>  
 <span data-ttu-id="11cc1-105"><xref:System.Xml.XmlResolver> Klasa jest używana do rozpoznawania zasobów zewnętrznych.</span><span class="sxs-lookup"><span data-stu-id="11cc1-105">The <xref:System.Xml.XmlResolver> class is used to resolve external resources.</span></span> <span data-ttu-id="11cc1-106">W poniższej tabeli opisano, kiedy <xref:System.Xml.XmlResolver> staje się zaangażowanych podczas przetwarzania XSLT.</span><span class="sxs-lookup"><span data-stu-id="11cc1-106">The following table describes when the <xref:System.Xml.XmlResolver> becomes involved during XSLT processing.</span></span>  
  
|<span data-ttu-id="11cc1-107">Zadanie XSLT</span><span class="sxs-lookup"><span data-stu-id="11cc1-107">XSLT task</span></span>|<span data-ttu-id="11cc1-108">Element XmlResolver służy do</span><span class="sxs-lookup"><span data-stu-id="11cc1-108">What the XmlResolver is used for</span></span>|  
|---------------|--------------------------------------|  
|<span data-ttu-id="11cc1-109">Kompiluj arkusza stylów.</span><span class="sxs-lookup"><span data-stu-id="11cc1-109">Compile the style sheet.</span></span>|<span data-ttu-id="11cc1-110">Rozwiąż URI arkusza stylów.</span><span class="sxs-lookup"><span data-stu-id="11cc1-110">Resolve the URI of the style sheet.</span></span><br /><br /> <span data-ttu-id="11cc1-111">- i -</span><span class="sxs-lookup"><span data-stu-id="11cc1-111">-and-</span></span><br /><br /> <span data-ttu-id="11cc1-112">Rozpoznać odwołań do identyfikatora URI w żadnym `xsl:import` lub `xsl:include` elementów.</span><span class="sxs-lookup"><span data-stu-id="11cc1-112">Resolve URI references in any `xsl:import` or `xsl:include` elements.</span></span>|  
|<span data-ttu-id="11cc1-113">Wykonanie arkusza stylów.</span><span class="sxs-lookup"><span data-stu-id="11cc1-113">Execute the style sheet.</span></span>|<span data-ttu-id="11cc1-114">Rozwiąż identyfikator URI dokumentu kontekstu.</span><span class="sxs-lookup"><span data-stu-id="11cc1-114">Resolve the URI of the context document.</span></span><br /><br /> <span data-ttu-id="11cc1-115">- i -</span><span class="sxs-lookup"><span data-stu-id="11cc1-115">-and-</span></span><br /><br /> <span data-ttu-id="11cc1-116">Rozpoznać odwołań do identyfikatora URI w dowolnym XSLT `document()` funkcji.</span><span class="sxs-lookup"><span data-stu-id="11cc1-116">Resolve URI references in any XSLT `document()` functions.</span></span>|  
  
 <span data-ttu-id="11cc1-117"><xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> i <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metod uwzględnić przeciążeń, które przyjmują <xref:System.Xml.XmlResolver> obiektu jako jego argumenty.</span><span class="sxs-lookup"><span data-stu-id="11cc1-117">The <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> and <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> methods include overloads that take an <xref:System.Xml.XmlResolver> object as one of its arguments.</span></span> <span data-ttu-id="11cc1-118">Jeśli <xref:System.Xml.XmlResolver> nie zostanie określony, domyślnie <xref:System.Xml.XmlUrlResolver> bez poświadczeń jest używany.</span><span class="sxs-lookup"><span data-stu-id="11cc1-118">If an <xref:System.Xml.XmlResolver> is not specified, a default <xref:System.Xml.XmlUrlResolver> with no credentials is used.</span></span>  
  
 <span data-ttu-id="11cc1-119">Na poniższej liście opisano, kiedy można określić <xref:System.Xml.XmlResolver> obiektu:</span><span class="sxs-lookup"><span data-stu-id="11cc1-119">The following list describes when you may want to specify an <xref:System.Xml.XmlResolver> object:</span></span>  
  
-   <span data-ttu-id="11cc1-120">Jeśli proces XSLT wymaga dostępu do zasobu sieciowego, która wymaga uwierzytelnienia, można użyć <xref:System.Xml.XmlResolver> niezbędne poświadczenia.</span><span class="sxs-lookup"><span data-stu-id="11cc1-120">If the XSLT process needs to access a network resource that requires authentication, you can use an <xref:System.Xml.XmlResolver> with the necessary credentials.</span></span>  
  
-   <span data-ttu-id="11cc1-121">Jeśli chcesz ograniczyć zasoby, do których dostęp procesu XSLT, możesz użyć <xref:System.Xml.XmlSecureResolver> ustawienie odpowiednie uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="11cc1-121">If you want to restrict the resources that the XSLT process can access, you can use an <xref:System.Xml.XmlSecureResolver> with the correct permission set.</span></span> <span data-ttu-id="11cc1-122">Użyj <xref:System.Xml.XmlSecureResolver> klasy, jeśli trzeba otworzyć zasobu, która kontroluje, lub niezaufanych.</span><span class="sxs-lookup"><span data-stu-id="11cc1-122">Use the <xref:System.Xml.XmlSecureResolver> class if you need to open a resource that you do not control, or that is untrusted.</span></span>  
  
-   <span data-ttu-id="11cc1-123">Jeśli chcesz dostosować zachowanie, można zaimplementować własne <xref:System.Xml.XmlResolver> klasy i użyć go do rozwiązania zasobów.</span><span class="sxs-lookup"><span data-stu-id="11cc1-123">If you want to customize behavior, you can implement your own <xref:System.Xml.XmlResolver> class and use it to resolve resources.</span></span>  
  
-   <span data-ttu-id="11cc1-124">Jeśli chcesz upewnić się, że nie zewnętrzne zasoby są dostępne, można określić `null` dla <xref:System.Xml.XmlResolver> argumentu.</span><span class="sxs-lookup"><span data-stu-id="11cc1-124">If you want to ensure that no external resources are accessed, you can specify `null` for the <xref:System.Xml.XmlResolver> argument.</span></span>  
  
## <a name="example"></a><span data-ttu-id="11cc1-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="11cc1-125">Example</span></span>  
 <span data-ttu-id="11cc1-126">Poniższy przykład tworzy arkusz stylów, który jest przechowywany w zasobie sieciowym.</span><span class="sxs-lookup"><span data-stu-id="11cc1-126">The following example compiles a style sheet that is stored on a network resource.</span></span> <span data-ttu-id="11cc1-127"><xref:System.Xml.XmlUrlResolver> Obiektu Określa poświadczenia niezbędne do uzyskania dostępu arkusza stylów.</span><span class="sxs-lookup"><span data-stu-id="11cc1-127">An <xref:System.Xml.XmlUrlResolver> object specifies the credentials necessary to access the style sheet.</span></span>  
  
 [!code-csharp[XslCompiledTransform.Load#11](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Load/CS/Xslt_Load_v2.cs#11)]
 [!code-vb[XslCompiledTransform.Load#11](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Load/VB/Xslt_Load_v2.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="11cc1-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="11cc1-128">See Also</span></span>  
 <xref:System.Xml.Xsl.XslCompiledTransform>  
 <xref:System.Xml.Xsl.XsltSettings>  
 [<span data-ttu-id="11cc1-129">Przekształcenia XSLT</span><span class="sxs-lookup"><span data-stu-id="11cc1-129">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)
