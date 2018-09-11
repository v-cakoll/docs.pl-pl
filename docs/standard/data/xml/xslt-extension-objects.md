---
title: Obiekty rozszerzeń XSLT
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: a4ebdbad-087c-4cfe-acc0-17c48142f81a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 40a530190ee4b19d72399ab877cf26bad1090b9f
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44264119"
---
# <a name="xslt-extension-objects"></a><span data-ttu-id="a4c9d-102">Obiekty rozszerzeń XSLT</span><span class="sxs-lookup"><span data-stu-id="a4c9d-102">XSLT Extension Objects</span></span>
<span data-ttu-id="a4c9d-103">Obiekty rozszerzeń są używane do rozszerzania funkcji arkuszy stylów.</span><span class="sxs-lookup"><span data-stu-id="a4c9d-103">Extension objects are used to extend the functionality of style sheets.</span></span> <span data-ttu-id="a4c9d-104">Obiekty rozszerzeń są obsługiwane przez <xref:System.Xml.Xsl.XsltArgumentList> klasy.</span><span class="sxs-lookup"><span data-stu-id="a4c9d-104">Extension objects are maintained by the <xref:System.Xml.Xsl.XsltArgumentList> class.</span></span>  
  
 <span data-ttu-id="a4c9d-105">Poniżej przedstawiono zalety korzystania z obiektu rozszerzenia zamiast osadzonych skryptów:</span><span class="sxs-lookup"><span data-stu-id="a4c9d-105">The following are advantages to using an extension object rather than embedded script:</span></span>  
  
-   <span data-ttu-id="a4c9d-106">Zapewnia lepszą hermetyzacji i ponowne użycie klas.</span><span class="sxs-lookup"><span data-stu-id="a4c9d-106">Provides better encapsulation and reuse of classes.</span></span>  
  
-   <span data-ttu-id="a4c9d-107">Umożliwia arkusze stylów była mniejsza i będzie łatwiejszy w utrzymaniu.</span><span class="sxs-lookup"><span data-stu-id="a4c9d-107">Allows style sheets to be smaller and more maintainable.</span></span>  
  
 <span data-ttu-id="a4c9d-108">Obiekty rozszerzeń XSLT są dodawane do <xref:System.Xml.Xsl.XsltArgumentList> przy użyciu <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="a4c9d-108">XSLT extension objects are added to the <xref:System.Xml.Xsl.XsltArgumentList> object using the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span> <span data-ttu-id="a4c9d-109">Kwalifikowana nazwa i identyfikator URI przestrzeni nazw są skojarzone z obiektu rozszerzenia, w tym czasie.</span><span class="sxs-lookup"><span data-stu-id="a4c9d-109">A qualified name and namespace URI are associated with the extension object at that time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a4c9d-110">Zestaw uprawnień FullTrust jest wymagane do wywołania <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="a4c9d-110">The FullTrust permission set is required to call the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span> <span data-ttu-id="a4c9d-111">Aby uzyskać więcej informacji, zobacz [zabezpieczenia dostępu kodu](https://msdn.microsoft.com/library/23a20143-241d-4fe5-9d9f-3933fd594c03) i [NIB: nazwane zestawy uprawnień](https://msdn.microsoft.com/library/08250d67-c99d-4ab0-8d2b-b0e12019f6e3).</span><span class="sxs-lookup"><span data-stu-id="a4c9d-111">For more information, see [Code Access Security](https://msdn.microsoft.com/library/23a20143-241d-4fe5-9d9f-3933fd594c03) and [NIB: Named Permission Sets](https://msdn.microsoft.com/library/08250d67-c99d-4ab0-8d2b-b0e12019f6e3).</span></span>  
  
 <span data-ttu-id="a4c9d-112">Typy danych zwróciło obiekty rozszerzeń są jedną z czterech podstawowych XPath typy danych `number`, `string`, `Boolean`, i `node set`.</span><span class="sxs-lookup"><span data-stu-id="a4c9d-112">The data types returned from extension objects are one of the four basic XPath data types of `number`, `string`, `Boolean`, and `node set`.</span></span>  
  
 <span data-ttu-id="a4c9d-113">Wszystkie metody, która jest zdefiniowana za pomocą `params` — słowo kluczowe, które dopuszcza nieokreślonej liczby parametrów do przekazania, nie jest obsługiwana przez <xref:System.Xml.Xsl.XslCompiledTransform> klasy.</span><span class="sxs-lookup"><span data-stu-id="a4c9d-113">Any method that is defined with the `params` keyword, which allows an unspecified number of parameters to be passed, is not currently supported by the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="a4c9d-114">Arkuszy stylów XSLT, które wykorzystują wszelkie metody zdefiniowane przy użyciu `params` — słowo kluczowe nie będą działać poprawnie.</span><span class="sxs-lookup"><span data-stu-id="a4c9d-114">XSLT style sheets that utilize any method defined with the `params` keyword will not work correctly.</span></span> <span data-ttu-id="a4c9d-115">Aby uzyskać więcej informacji, zobacz [params](~/docs/csharp/language-reference/keywords/params.md).</span><span class="sxs-lookup"><span data-stu-id="a4c9d-115">For details, see [params](~/docs/csharp/language-reference/keywords/params.md).</span></span>  
  
### <a name="to-use-an-xslt-extension-object"></a><span data-ttu-id="a4c9d-116">Używanie obiektu rozszerzenia XSLT</span><span class="sxs-lookup"><span data-stu-id="a4c9d-116">To use an XSLT extension object</span></span>  
  
1.  <span data-ttu-id="a4c9d-117">Tworzenie <xref:System.Xml.Xsl.XsltArgumentList> obiektu i dodać za pomocą obiektu rozszerzenia <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="a4c9d-117">Create an <xref:System.Xml.Xsl.XsltArgumentList> object and add the extension object using <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span>  
  
2.  <span data-ttu-id="a4c9d-118">Wywołanie obiektu rozszerzenia z arkusza stylów.</span><span class="sxs-lookup"><span data-stu-id="a4c9d-118">Call the extension object from the style sheet.</span></span>  
  
3.  <span data-ttu-id="a4c9d-119">Przekaż <xref:System.Xml.Xsl.XsltArgumentList> obiekt <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="a4c9d-119">Pass the <xref:System.Xml.Xsl.XsltArgumentList> object to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4c9d-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a4c9d-120">See also</span></span>

- [<span data-ttu-id="a4c9d-121">Przekształcenia XSLT</span><span class="sxs-lookup"><span data-stu-id="a4c9d-121">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)  
- [<span data-ttu-id="a4c9d-122">Zagadnienia dotyczące bezpieczeństwa danych XSLT</span><span class="sxs-lookup"><span data-stu-id="a4c9d-122">XSLT Security Considerations</span></span>](../../../../docs/standard/data/xml/xslt-security-considerations.md)
