---
title: Zalecane tagi XML dla komentarzy dokumentacji (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlDocComment
helpviewer_keywords:
- tags, XML
- XML comments, recommended tags [Visual Basic]
- comments, recommended XML tags
ms.assetid: 294e0736-ff1e-498e-af83-6db71ed41a72
ms.openlocfilehash: 3b2dec4224006d35fb9add11e170b9dcbeeafcf3
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/15/2018
ms.locfileid: "45649975"
---
# <a name="recommended-xml-tags-for-documentation-comments-visual-basic"></a><span data-ttu-id="9e4ac-102">Zalecane tagi XML dla komentarzy dokumentacji (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9e4ac-102">Recommended XML Tags for Documentation Comments (Visual Basic)</span></span>
<span data-ttu-id="9e4ac-103">Kompilator Visual Basic przetwarzanie komentarzy dokumentacji w kodzie do pliku XML.</span><span class="sxs-lookup"><span data-stu-id="9e4ac-103">The Visual Basic compiler can process documentation comments in your code to an XML file.</span></span> <span data-ttu-id="9e4ac-104">Można użyć dodatkowych narzędzi do przetwarzania pliku XML do dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="9e4ac-104">You can use additional tools to process the XML file into documentation.</span></span>  
  
 <span data-ttu-id="9e4ac-105">Komentarze XML są dozwolone na kodzie konstrukcji, takich jak typy i elementy członkowskie typu.</span><span class="sxs-lookup"><span data-stu-id="9e4ac-105">XML comments are allowed on code constructs such as types and type members.</span></span> <span data-ttu-id="9e4ac-106">Dla typów częściowych tylko jedną część tego typu może mieć komentarze XML, mimo że nie ma żadnych ograniczeń na dodawanie komentarza do jego członków.</span><span class="sxs-lookup"><span data-stu-id="9e4ac-106">For partial types, only one part of the type can have XML comments, although there is no restriction on commenting its members.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9e4ac-107">Komentarze dokumentacji nie można zastosować do przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="9e4ac-107">Documentation comments cannot be applied to namespaces.</span></span> <span data-ttu-id="9e4ac-108">Przyczyną jest, że jedną przestrzeń nazw może obejmować kilka zestawów, a nie wszystkie zestawy posiadają do załadowania w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="9e4ac-108">The reason is that one namespace can span several assemblies, and not all assemblies have to be loaded at the same time.</span></span>  
  
 <span data-ttu-id="9e4ac-109">Kompilator przetworzy dowolnymi tagami, które jest prawidłowym kodem XML.</span><span class="sxs-lookup"><span data-stu-id="9e4ac-109">The compiler processes any tag that is valid XML.</span></span> <span data-ttu-id="9e4ac-110">Następujące znaczniki oferuje powszechnie używanych w dokumentacji użytkownika.</span><span class="sxs-lookup"><span data-stu-id="9e4ac-110">The following tags provide commonly used functionality in user documentation.</span></span>  
  
||||  
|---|---|---|  
|[<span data-ttu-id="9e4ac-111">\<c ></span><span class="sxs-lookup"><span data-stu-id="9e4ac-111">\<c></span></span>](../../../visual-basic/language-reference/xmldoc/c.md)|[<span data-ttu-id="9e4ac-112">\<Kod ></span><span class="sxs-lookup"><span data-stu-id="9e4ac-112">\<code></span></span>](../../../visual-basic/language-reference/xmldoc/code.md)|[<span data-ttu-id="9e4ac-113">\<przykład ></span><span class="sxs-lookup"><span data-stu-id="9e4ac-113">\<example></span></span>](../../../visual-basic/language-reference/xmldoc/example.md)|  
|<span data-ttu-id="9e4ac-114">[\<wyjątek >](../../../visual-basic/language-reference/xmldoc/exception.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="9e4ac-114">[\<exception>](../../../visual-basic/language-reference/xmldoc/exception.md) <sup>1</sup></span></span>|<span data-ttu-id="9e4ac-115">[\<obejmują >](../../../visual-basic/language-reference/xmldoc/include.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="9e4ac-115">[\<include>](../../../visual-basic/language-reference/xmldoc/include.md) <sup>1</sup></span></span>|[<span data-ttu-id="9e4ac-116">\<list></span><span class="sxs-lookup"><span data-stu-id="9e4ac-116">\<list></span></span>](../../../visual-basic/language-reference/xmldoc/list.md)|  
|[<span data-ttu-id="9e4ac-117">\<para ></span><span class="sxs-lookup"><span data-stu-id="9e4ac-117">\<para></span></span>](../../../visual-basic/language-reference/xmldoc/para.md)|<span data-ttu-id="9e4ac-118">[\<param >](../../../visual-basic/language-reference/xmldoc/param.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="9e4ac-118">[\<param>](../../../visual-basic/language-reference/xmldoc/param.md) <sup>1</sup></span></span>|[<span data-ttu-id="9e4ac-119">\<paramref ></span><span class="sxs-lookup"><span data-stu-id="9e4ac-119">\<paramref></span></span>](../../../visual-basic/language-reference/xmldoc/paramref.md)|  
|<span data-ttu-id="9e4ac-120">[\<uprawnienie >](../../../visual-basic/language-reference/xmldoc/permission.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="9e4ac-120">[\<permission>](../../../visual-basic/language-reference/xmldoc/permission.md) <sup>1</sup></span></span>|[<span data-ttu-id="9e4ac-121">\<Remarks ></span><span class="sxs-lookup"><span data-stu-id="9e4ac-121">\<remarks></span></span>](../../../visual-basic/language-reference/xmldoc/remarks.md)|[<span data-ttu-id="9e4ac-122">\<Zwraca wartość ></span><span class="sxs-lookup"><span data-stu-id="9e4ac-122">\<returns></span></span>](../../../visual-basic/language-reference/xmldoc/returns.md)|  
|<span data-ttu-id="9e4ac-123">[\<zobacz >](../../../visual-basic/language-reference/xmldoc/see.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="9e4ac-123">[\<see>](../../../visual-basic/language-reference/xmldoc/see.md) <sup>1</sup></span></span>|<span data-ttu-id="9e4ac-124">[\<SeeAlso — >](../../../visual-basic/language-reference/xmldoc/seealso.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="9e4ac-124">[\<seealso>](../../../visual-basic/language-reference/xmldoc/seealso.md) <sup>1</sup></span></span>|[<span data-ttu-id="9e4ac-125">\<Summary ></span><span class="sxs-lookup"><span data-stu-id="9e4ac-125">\<summary></span></span>](../../../visual-basic/language-reference/xmldoc/summary.md)|  
|<span data-ttu-id="9e4ac-126">[\<typeparam >](../../../visual-basic/language-reference/xmldoc/typeparam.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="9e4ac-126">[\<typeparam>](../../../visual-basic/language-reference/xmldoc/typeparam.md) <sup>1</sup></span></span>|[<span data-ttu-id="9e4ac-127">\<wartość ></span><span class="sxs-lookup"><span data-stu-id="9e4ac-127">\<value></span></span>](../../../visual-basic/language-reference/xmldoc/value.md)||  
  
 <span data-ttu-id="9e4ac-128">(<sup>1</sup> kompilator sprawdza składnię.)</span><span class="sxs-lookup"><span data-stu-id="9e4ac-128">(<sup>1</sup> The compiler verifies syntax.)</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9e4ac-129">Nawiasy są wyświetlane w tekście komentarza do dokumentacji, użyć `&lt;` i `&gt;`.</span><span class="sxs-lookup"><span data-stu-id="9e4ac-129">If you want angle brackets to appear in the text of a documentation comment, use `&lt;` and `&gt;`.</span></span> <span data-ttu-id="9e4ac-130">Na przykład ciąg `"&lt;text in angle brackets&gt;"` będą wyświetlane jako `<text in angle brackets>`.</span><span class="sxs-lookup"><span data-stu-id="9e4ac-130">For example, the string `"&lt;text in angle brackets&gt;"` will appear as `<text in angle brackets>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e4ac-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9e4ac-131">See Also</span></span>  
 [<span data-ttu-id="9e4ac-132">Dokumentowanie kodu za pomocą XML</span><span class="sxs-lookup"><span data-stu-id="9e4ac-132">Documenting Your Code with XML</span></span>](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)  
 [<span data-ttu-id="9e4ac-133">/doc</span><span class="sxs-lookup"><span data-stu-id="9e4ac-133">/doc</span></span>](../../../visual-basic/reference/command-line-compiler/doc.md)  
 [<span data-ttu-id="9e4ac-134">Instrukcje: tworzenie dokumentacji XML</span><span class="sxs-lookup"><span data-stu-id="9e4ac-134">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
