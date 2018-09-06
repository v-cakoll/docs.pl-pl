---
title: Obiekty rozszerzeń XSLT
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: a4ebdbad-087c-4cfe-acc0-17c48142f81a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6f958af5859804cdeb382adab2f3772c42ac5b16
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43724373"
---
# <a name="xslt-extension-objects"></a><span data-ttu-id="5b994-102">Obiekty rozszerzeń XSLT</span><span class="sxs-lookup"><span data-stu-id="5b994-102">XSLT Extension Objects</span></span>
<span data-ttu-id="5b994-103">Obiekty rozszerzeń są używane do rozszerzania funkcji arkuszy stylów.</span><span class="sxs-lookup"><span data-stu-id="5b994-103">Extension objects are used to extend the functionality of style sheets.</span></span> <span data-ttu-id="5b994-104">Obiekty rozszerzeń są obsługiwane przez <xref:System.Xml.Xsl.XsltArgumentList> klasy.</span><span class="sxs-lookup"><span data-stu-id="5b994-104">Extension objects are maintained by the <xref:System.Xml.Xsl.XsltArgumentList> class.</span></span>  
  
 <span data-ttu-id="5b994-105">Poniżej przedstawiono zalety korzystania z obiektu rozszerzenia zamiast osadzonych skryptów:</span><span class="sxs-lookup"><span data-stu-id="5b994-105">The following are advantages to using an extension object rather than embedded script:</span></span>  
  
-   <span data-ttu-id="5b994-106">Zapewnia lepszą hermetyzacji i ponowne użycie klas.</span><span class="sxs-lookup"><span data-stu-id="5b994-106">Provides better encapsulation and reuse of classes.</span></span>  
  
-   <span data-ttu-id="5b994-107">Umożliwia arkusze stylów była mniejsza i będzie łatwiejszy w utrzymaniu.</span><span class="sxs-lookup"><span data-stu-id="5b994-107">Allows style sheets to be smaller and more maintainable.</span></span>  
  
 <span data-ttu-id="5b994-108">Obiekty rozszerzeń XSLT są dodawane do <xref:System.Xml.Xsl.XsltArgumentList> przy użyciu <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="5b994-108">XSLT extension objects are added to the <xref:System.Xml.Xsl.XsltArgumentList> object using the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span> <span data-ttu-id="5b994-109">Kwalifikowana nazwa i identyfikator URI przestrzeni nazw są skojarzone z obiektu rozszerzenia, w tym czasie.</span><span class="sxs-lookup"><span data-stu-id="5b994-109">A qualified name and namespace URI are associated with the extension object at that time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5b994-110">Zestaw uprawnień FullTrust jest wymagane do wywołania <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="5b994-110">The FullTrust permission set is required to call the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span> <span data-ttu-id="5b994-111">Aby uzyskać więcej informacji, zobacz [zabezpieczenia dostępu kodu](https://msdn.microsoft.com/library/23a20143-241d-4fe5-9d9f-3933fd594c03) i [NIB: nazwane zestawy uprawnień](https://msdn.microsoft.com/library/08250d67-c99d-4ab0-8d2b-b0e12019f6e3).</span><span class="sxs-lookup"><span data-stu-id="5b994-111">For more information, see [Code Access Security](https://msdn.microsoft.com/library/23a20143-241d-4fe5-9d9f-3933fd594c03) and [NIB: Named Permission Sets](https://msdn.microsoft.com/library/08250d67-c99d-4ab0-8d2b-b0e12019f6e3).</span></span>  
  
 <span data-ttu-id="5b994-112">Typy danych zwróciło obiekty rozszerzeń są jedną z czterech podstawowych XPath typy danych `number`, `string`, `Boolean`, i `node set`.</span><span class="sxs-lookup"><span data-stu-id="5b994-112">The data types returned from extension objects are one of the four basic XPath data types of `number`, `string`, `Boolean`, and `node set`.</span></span>  
  
 <span data-ttu-id="5b994-113">Wszystkie metody, która jest zdefiniowana za pomocą `params` — słowo kluczowe, które dopuszcza nieokreślonej liczby parametrów do przekazania, nie jest obsługiwana przez <xref:System.Xml.Xsl.XslCompiledTransform> klasy.</span><span class="sxs-lookup"><span data-stu-id="5b994-113">Any method that is defined with the `params` keyword, which allows an unspecified number of parameters to be passed, is not currently supported by the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="5b994-114">Arkuszy stylów XSLT, które wykorzystują wszelkie metody zdefiniowane przy użyciu `params` — słowo kluczowe nie będą działać poprawnie.</span><span class="sxs-lookup"><span data-stu-id="5b994-114">XSLT style sheets that utilize any method defined with the `params` keyword will not work correctly.</span></span> <span data-ttu-id="5b994-115">Aby uzyskać więcej informacji, zobacz [params](~/docs/csharp/language-reference/keywords/params.md).</span><span class="sxs-lookup"><span data-stu-id="5b994-115">For details, see [params](~/docs/csharp/language-reference/keywords/params.md).</span></span>  
  
### <a name="to-use-an-xslt-extension-object"></a><span data-ttu-id="5b994-116">Używanie obiektu rozszerzenia XSLT</span><span class="sxs-lookup"><span data-stu-id="5b994-116">To use an XSLT extension object</span></span>  
  
1.  <span data-ttu-id="5b994-117">Tworzenie <xref:System.Xml.Xsl.XsltArgumentList> obiektu i dodać za pomocą obiektu rozszerzenia <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="5b994-117">Create an <xref:System.Xml.Xsl.XsltArgumentList> object and add the extension object using <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span>  
  
2.  <span data-ttu-id="5b994-118">Wywołanie obiektu rozszerzenia z arkusza stylów.</span><span class="sxs-lookup"><span data-stu-id="5b994-118">Call the extension object from the style sheet.</span></span>  
  
3.  <span data-ttu-id="5b994-119">Przekaż <xref:System.Xml.Xsl.XsltArgumentList> obiekt <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="5b994-119">Pass the <xref:System.Xml.Xsl.XsltArgumentList> object to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b994-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5b994-120">See Also</span></span>  
 [<span data-ttu-id="5b994-121">Przekształcenia XSLT</span><span class="sxs-lookup"><span data-stu-id="5b994-121">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)  
 [<span data-ttu-id="5b994-122">Zagadnienia dotyczące bezpieczeństwa danych XSLT</span><span class="sxs-lookup"><span data-stu-id="5b994-122">XSLT Security Considerations</span></span>](../../../../docs/standard/data/xml/xslt-security-considerations.md)
