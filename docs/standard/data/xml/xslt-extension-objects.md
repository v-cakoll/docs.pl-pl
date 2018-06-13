---
title: Obiekty rozszerzenia XSLT
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: a4ebdbad-087c-4cfe-acc0-17c48142f81a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 69fcd4bd8426bb349c090fc52f7a1f1a262378ea
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33570582"
---
# <a name="xslt-extension-objects"></a><span data-ttu-id="e3d7c-102">Obiekty rozszerzenia XSLT</span><span class="sxs-lookup"><span data-stu-id="e3d7c-102">XSLT Extension Objects</span></span>
<span data-ttu-id="e3d7c-103">Obiekty rozszerzenia są używane do rozszerzyć funkcjonalność arkuszy stylów.</span><span class="sxs-lookup"><span data-stu-id="e3d7c-103">Extension objects are used to extend the functionality of style sheets.</span></span> <span data-ttu-id="e3d7c-104">Obiekty rozszerzenia są obsługiwane przez <xref:System.Xml.Xsl.XsltArgumentList> klasy.</span><span class="sxs-lookup"><span data-stu-id="e3d7c-104">Extension objects are maintained by the <xref:System.Xml.Xsl.XsltArgumentList> class.</span></span>  
  
 <span data-ttu-id="e3d7c-105">Poniżej przedstawiono zalety korzystania z obiektu rozszerzenia, a nie osadzony skrypt:</span><span class="sxs-lookup"><span data-stu-id="e3d7c-105">The following are advantages to using an extension object rather than embedded script:</span></span>  
  
-   <span data-ttu-id="e3d7c-106">Zapewnia lepszą hermetyzacji i ponowne użycie klasy.</span><span class="sxs-lookup"><span data-stu-id="e3d7c-106">Provides better encapsulation and reuse of classes.</span></span>  
  
-   <span data-ttu-id="e3d7c-107">Umożliwia arkusze stylów mniejsze i łatwiejsze do utrzymania.</span><span class="sxs-lookup"><span data-stu-id="e3d7c-107">Allows style sheets to be smaller and more maintainable.</span></span>  
  
 <span data-ttu-id="e3d7c-108">Obiekty rozszerzenia XSLT są dodawane do <xref:System.Xml.Xsl.XsltArgumentList> przy użyciu <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="e3d7c-108">XSLT extension objects are added to the <xref:System.Xml.Xsl.XsltArgumentList> object using the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span> <span data-ttu-id="e3d7c-109">Kwalifikowana nazwa i identyfikator URI przestrzeni nazw są skojarzone z obiektem rozszerzenia o tej godzinie.</span><span class="sxs-lookup"><span data-stu-id="e3d7c-109">A qualified name and namespace URI are associated with the extension object at that time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e3d7c-110">Zestaw uprawnień FullTrust jest wymagany do wywołania <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="e3d7c-110">The FullTrust permission set is required to call the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span> <span data-ttu-id="e3d7c-111">Aby uzyskać więcej informacji, zobacz [zabezpieczenia dostępu kodu](http://msdn.microsoft.com/library/23a20143-241d-4fe5-9d9f-3933fd594c03) i [NIB: nazwane zestawy uprawnień](https://msdn.microsoft.com/library/08250d67-c99d-4ab0-8d2b-b0e12019f6e3).</span><span class="sxs-lookup"><span data-stu-id="e3d7c-111">For more information, see [Code Access Security](http://msdn.microsoft.com/library/23a20143-241d-4fe5-9d9f-3933fd594c03) and [NIB: Named Permission Sets](https://msdn.microsoft.com/library/08250d67-c99d-4ab0-8d2b-b0e12019f6e3).</span></span>  
  
 <span data-ttu-id="e3d7c-112">Typy danych zwracane z obiektów rozszerzeń są jedną z czterech podstawowych XPath typy danych `number`, `string`, `Boolean`, i `node set`.</span><span class="sxs-lookup"><span data-stu-id="e3d7c-112">The data types returned from extension objects are one of the four basic XPath data types of `number`, `string`, `Boolean`, and `node set`.</span></span>  
  
 <span data-ttu-id="e3d7c-113">Wszystkie metody, która jest zdefiniowana z `params` — słowo kluczowe, umożliwiający nieokreślony liczba parametrów nie jest obsługiwana przez <xref:System.Xml.Xsl.XslCompiledTransform> klasy.</span><span class="sxs-lookup"><span data-stu-id="e3d7c-113">Any method that is defined with the `params` keyword, which allows an unspecified number of parameters to be passed, is not currently supported by the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="e3d7c-114">Arkusze stylów XSLT wykorzystujące dowolnej metody zdefiniowane z `params` — słowo kluczowe nie będą działać poprawnie.</span><span class="sxs-lookup"><span data-stu-id="e3d7c-114">XSLT style sheets that utilize any method defined with the `params` keyword will not work correctly.</span></span> <span data-ttu-id="e3d7c-115">Aby uzyskać więcej informacji, zobacz [params](~/docs/csharp/language-reference/keywords/params.md).</span><span class="sxs-lookup"><span data-stu-id="e3d7c-115">For details, see [params](~/docs/csharp/language-reference/keywords/params.md).</span></span>  
  
### <a name="to-use-an-xslt-extension-object"></a><span data-ttu-id="e3d7c-116">Aby użyć obiektu rozszerzenia XSLT</span><span class="sxs-lookup"><span data-stu-id="e3d7c-116">To use an XSLT extension object</span></span>  
  
1.  <span data-ttu-id="e3d7c-117">Utwórz <xref:System.Xml.Xsl.XsltArgumentList> obiektu i dodać za pomocą obiektu rozszerzenia <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="e3d7c-117">Create an <xref:System.Xml.Xsl.XsltArgumentList> object and add the extension object using <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span>  
  
2.  <span data-ttu-id="e3d7c-118">Wywołanie obiektu rozszerzenia z arkusza stylów.</span><span class="sxs-lookup"><span data-stu-id="e3d7c-118">Call the extension object from the style sheet.</span></span>  
  
3.  <span data-ttu-id="e3d7c-119">Przekaż <xref:System.Xml.Xsl.XsltArgumentList> do obiektu <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="e3d7c-119">Pass the <xref:System.Xml.Xsl.XsltArgumentList> object to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3d7c-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e3d7c-120">See Also</span></span>  
 [<span data-ttu-id="e3d7c-121">Przekształcenia XSLT</span><span class="sxs-lookup"><span data-stu-id="e3d7c-121">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)  
 [<span data-ttu-id="e3d7c-122">Zagadnienia dotyczące bezpieczeństwa danych XSLT</span><span class="sxs-lookup"><span data-stu-id="e3d7c-122">XSLT Security Considerations</span></span>](../../../../docs/standard/data/xml/xslt-security-considerations.md)
