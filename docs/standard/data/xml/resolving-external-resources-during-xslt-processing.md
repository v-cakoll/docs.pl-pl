---
title: Rozpoznawanie zewnętrznych zasobów podczas przetwarzania XSLT
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 3a59d31c-0ec5-4de6-a2a9-558531c8116e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 958699b8e3a00cfe3f8fd8ac4bb96914dcd0598c
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44185129"
---
# <a name="resolving-external-resources-during-xslt-processing"></a><span data-ttu-id="464f4-102">Rozpoznawanie zewnętrznych zasobów podczas przetwarzania XSLT</span><span class="sxs-lookup"><span data-stu-id="464f4-102">Resolving External Resources During XSLT Processing</span></span>
<span data-ttu-id="464f4-103">Istnieje kilka razy podczas transformacji XSLT, gdy trzeba rozwiązać zasobów zewnętrznych.</span><span class="sxs-lookup"><span data-stu-id="464f4-103">There are several times during an XSLT transformation when you may need to resolve external resources.</span></span>  
  
## <a name="using-the-xmlresolver-class"></a><span data-ttu-id="464f4-104">Używanie klasy element XmlResolver</span><span class="sxs-lookup"><span data-stu-id="464f4-104">Using the XmlResolver Class</span></span>  
 <span data-ttu-id="464f4-105"><xref:System.Xml.XmlResolver> Klasy jest używany do rozpoznawania zasobów zewnętrznych.</span><span class="sxs-lookup"><span data-stu-id="464f4-105">The <xref:System.Xml.XmlResolver> class is used to resolve external resources.</span></span> <span data-ttu-id="464f4-106">Poniższa tabela opisuje, kiedy <xref:System.Xml.XmlResolver> staje się zaangażowane podczas przetwarzania XSLT.</span><span class="sxs-lookup"><span data-stu-id="464f4-106">The following table describes when the <xref:System.Xml.XmlResolver> becomes involved during XSLT processing.</span></span>  
  
|<span data-ttu-id="464f4-107">Zadanie XSLT</span><span class="sxs-lookup"><span data-stu-id="464f4-107">XSLT task</span></span>|<span data-ttu-id="464f4-108">Element XmlResolver do czego służy</span><span class="sxs-lookup"><span data-stu-id="464f4-108">What the XmlResolver is used for</span></span>|  
|---------------|--------------------------------------|  
|<span data-ttu-id="464f4-109">Skompiluj arkusza stylów.</span><span class="sxs-lookup"><span data-stu-id="464f4-109">Compile the style sheet.</span></span>|<span data-ttu-id="464f4-110">Rozwiązany identyfikator URI w arkusza stylów.</span><span class="sxs-lookup"><span data-stu-id="464f4-110">Resolve the URI of the style sheet.</span></span><br /><br /> <span data-ttu-id="464f4-111">- i -</span><span class="sxs-lookup"><span data-stu-id="464f4-111">-and-</span></span><br /><br /> <span data-ttu-id="464f4-112">Rozpoznać identyfikatora URI odwołania w żadnym `xsl:import` lub `xsl:include` elementów.</span><span class="sxs-lookup"><span data-stu-id="464f4-112">Resolve URI references in any `xsl:import` or `xsl:include` elements.</span></span>|  
|<span data-ttu-id="464f4-113">Wykonaj arkusza stylów.</span><span class="sxs-lookup"><span data-stu-id="464f4-113">Execute the style sheet.</span></span>|<span data-ttu-id="464f4-114">Rozwiązany identyfikator URI dokumentu kontekstu.</span><span class="sxs-lookup"><span data-stu-id="464f4-114">Resolve the URI of the context document.</span></span><br /><br /> <span data-ttu-id="464f4-115">- i -</span><span class="sxs-lookup"><span data-stu-id="464f4-115">-and-</span></span><br /><br /> <span data-ttu-id="464f4-116">Rozwiązać odwołania do identyfikatora URI w dowolnym XSLT `document()` funkcji.</span><span class="sxs-lookup"><span data-stu-id="464f4-116">Resolve URI references in any XSLT `document()` functions.</span></span>|  
  
 <span data-ttu-id="464f4-117"><xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> i <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metody obejmują przeciążeń, które przyjmują <xref:System.Xml.XmlResolver> obiektu jako jeden z jej argumentów.</span><span class="sxs-lookup"><span data-stu-id="464f4-117">The <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> and <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> methods include overloads that take an <xref:System.Xml.XmlResolver> object as one of its arguments.</span></span> <span data-ttu-id="464f4-118">Jeśli <xref:System.Xml.XmlResolver> nie zostanie określony, domyślnie <xref:System.Xml.XmlUrlResolver> bez poświadczeń jest używany.</span><span class="sxs-lookup"><span data-stu-id="464f4-118">If an <xref:System.Xml.XmlResolver> is not specified, a default <xref:System.Xml.XmlUrlResolver> with no credentials is used.</span></span>  
  
 <span data-ttu-id="464f4-119">Na poniższej liście opisano, kiedy warto określić <xref:System.Xml.XmlResolver> obiektu:</span><span class="sxs-lookup"><span data-stu-id="464f4-119">The following list describes when you may want to specify an <xref:System.Xml.XmlResolver> object:</span></span>  
  
-   <span data-ttu-id="464f4-120">Jeśli proces XSLT musi uzyskać dostęp do zasobów sieciowych, która wymaga uwierzytelnienia, można użyć <xref:System.Xml.XmlResolver> niezbędne poświadczenia.</span><span class="sxs-lookup"><span data-stu-id="464f4-120">If the XSLT process needs to access a network resource that requires authentication, you can use an <xref:System.Xml.XmlResolver> with the necessary credentials.</span></span>  
  
-   <span data-ttu-id="464f4-121">Jeśli chcesz ograniczyć zasoby, które proces XSLT można uzyskać dostępu, możesz użyć <xref:System.Xml.XmlSecureResolver> with odpowiednie uprawnienie jest ustawiona.</span><span class="sxs-lookup"><span data-stu-id="464f4-121">If you want to restrict the resources that the XSLT process can access, you can use an <xref:System.Xml.XmlSecureResolver> with the correct permission set.</span></span> <span data-ttu-id="464f4-122">Użyj <xref:System.Xml.XmlSecureResolver> klasy, jeśli trzeba otworzyć zasób, które nie mają kontroli nad lub które nie jest zaufany.</span><span class="sxs-lookup"><span data-stu-id="464f4-122">Use the <xref:System.Xml.XmlSecureResolver> class if you need to open a resource that you do not control, or that is untrusted.</span></span>  
  
-   <span data-ttu-id="464f4-123">Jeśli chcesz dostosować zachowanie, możesz zaimplementować własną <xref:System.Xml.XmlResolver> klasy i używane w celu rozwiązania zasobów.</span><span class="sxs-lookup"><span data-stu-id="464f4-123">If you want to customize behavior, you can implement your own <xref:System.Xml.XmlResolver> class and use it to resolve resources.</span></span>  
  
-   <span data-ttu-id="464f4-124">Jeśli chcesz upewnić się, że są dostępne nie zasoby zewnętrzne, można określić `null` dla <xref:System.Xml.XmlResolver> argumentu.</span><span class="sxs-lookup"><span data-stu-id="464f4-124">If you want to ensure that no external resources are accessed, you can specify `null` for the <xref:System.Xml.XmlResolver> argument.</span></span>  
  
## <a name="example"></a><span data-ttu-id="464f4-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="464f4-125">Example</span></span>  
 <span data-ttu-id="464f4-126">Poniższy przykład kompiluje arkusza stylów, który jest przechowywany w zasobie sieciowym.</span><span class="sxs-lookup"><span data-stu-id="464f4-126">The following example compiles a style sheet that is stored on a network resource.</span></span> <span data-ttu-id="464f4-127"><xref:System.Xml.XmlUrlResolver> Obiekt Określa poświadczenia niezbędne do uzyskania dostępu arkusza stylów.</span><span class="sxs-lookup"><span data-stu-id="464f4-127">An <xref:System.Xml.XmlUrlResolver> object specifies the credentials necessary to access the style sheet.</span></span>  
  
 [!code-csharp[XslCompiledTransform.Load#11](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Load/CS/Xslt_Load_v2.cs#11)]
 [!code-vb[XslCompiledTransform.Load#11](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Load/VB/Xslt_Load_v2.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="464f4-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="464f4-128">See also</span></span>

- <xref:System.Xml.Xsl.XslCompiledTransform>  
- <xref:System.Xml.Xsl.XsltSettings>  
- [<span data-ttu-id="464f4-129">Przekształcenia XSLT</span><span class="sxs-lookup"><span data-stu-id="464f4-129">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)
