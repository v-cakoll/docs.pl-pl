---
title: Zalecane tagi XML dla komentarzy do dokumentacji
ms.date: 07/20/2015
f1_keywords:
- vb.XmlDocComment
helpviewer_keywords:
- tags, XML
- XML comments, recommended tags [Visual Basic]
- comments, recommended XML tags
ms.assetid: 294e0736-ff1e-498e-af83-6db71ed41a72
ms.openlocfilehash: 093c967557b899c8661fdec348d421996e948b94
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352332"
---
# <a name="recommended-xml-tags-for-documentation-comments-visual-basic"></a><span data-ttu-id="3006c-102">Zalecane tagi XML dla komentarzy dokumentacji (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3006c-102">Recommended XML Tags for Documentation Comments (Visual Basic)</span></span>
<span data-ttu-id="3006c-103">Kompilator Visual Basic może przetwarzać komentarze dokumentacji w kodzie do pliku XML.</span><span class="sxs-lookup"><span data-stu-id="3006c-103">The Visual Basic compiler can process documentation comments in your code to an XML file.</span></span> <span data-ttu-id="3006c-104">Możesz użyć dodatkowych narzędzi do przetworzenia pliku XML w dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="3006c-104">You can use additional tools to process the XML file into documentation.</span></span>  
  
 <span data-ttu-id="3006c-105">Komentarze XML są dozwolone w konstrukcjach kodu, takich jak typy i elementy członkowskie typu.</span><span class="sxs-lookup"><span data-stu-id="3006c-105">XML comments are allowed on code constructs such as types and type members.</span></span> <span data-ttu-id="3006c-106">W przypadku typów częściowych tylko jedna część typu może zawierać komentarze XML, chociaż nie ma żadnych ograniczeń dotyczących komentowania jej elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="3006c-106">For partial types, only one part of the type can have XML comments, although there is no restriction on commenting its members.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3006c-107">Komentarzy do dokumentacji nie można stosować do przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="3006c-107">Documentation comments cannot be applied to namespaces.</span></span> <span data-ttu-id="3006c-108">Przyczyną jest to, że jedna przestrzeń nazw może obejmować kilka zestawów, a nie wszystkie zestawy muszą być ładowane w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="3006c-108">The reason is that one namespace can span several assemblies, and not all assemblies have to be loaded at the same time.</span></span>  
  
 <span data-ttu-id="3006c-109">Kompilator przetwarza dowolny tag, który jest prawidłowym kodem XML.</span><span class="sxs-lookup"><span data-stu-id="3006c-109">The compiler processes any tag that is valid XML.</span></span> <span data-ttu-id="3006c-110">Poniższe Tagi zapewniają powszechnie używane funkcje w dokumentacji użytkownika.</span><span class="sxs-lookup"><span data-stu-id="3006c-110">The following tags provide commonly used functionality in user documentation.</span></span>  
  
||||  
|---|---|---|  
|[<span data-ttu-id="3006c-111">\<c ></span><span class="sxs-lookup"><span data-stu-id="3006c-111">\<c></span></span>](../../../visual-basic/language-reference/xmldoc/c.md)|[<span data-ttu-id="3006c-112">> kodu \<</span><span class="sxs-lookup"><span data-stu-id="3006c-112">\<code></span></span>](../../../visual-basic/language-reference/xmldoc/code.md)|[<span data-ttu-id="3006c-113">przykład \<></span><span class="sxs-lookup"><span data-stu-id="3006c-113">\<example></span></span>](../../../visual-basic/language-reference/xmldoc/example.md)|  
|<span data-ttu-id="3006c-114">[\<wyjątek >](../../../visual-basic/language-reference/xmldoc/exception.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="3006c-114">[\<exception>](../../../visual-basic/language-reference/xmldoc/exception.md) <sup>1</sup></span></span>|<span data-ttu-id="3006c-115">[\<uwzględnij >](../../../visual-basic/language-reference/xmldoc/include.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="3006c-115">[\<include>](../../../visual-basic/language-reference/xmldoc/include.md) <sup>1</sup></span></span>|[<span data-ttu-id="3006c-116">> Lista \<</span><span class="sxs-lookup"><span data-stu-id="3006c-116">\<list></span></span>](../../../visual-basic/language-reference/xmldoc/list.md)|  
|[<span data-ttu-id="3006c-117">\<para ></span><span class="sxs-lookup"><span data-stu-id="3006c-117">\<para></span></span>](../../../visual-basic/language-reference/xmldoc/para.md)|<span data-ttu-id="3006c-118">[\<param >](../../../visual-basic/language-reference/xmldoc/param.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="3006c-118">[\<param>](../../../visual-basic/language-reference/xmldoc/param.md) <sup>1</sup></span></span>|[<span data-ttu-id="3006c-119">\<paramref ></span><span class="sxs-lookup"><span data-stu-id="3006c-119">\<paramref></span></span>](../../../visual-basic/language-reference/xmldoc/paramref.md)|  
|<span data-ttu-id="3006c-120">[> uprawnień\<](../../../visual-basic/language-reference/xmldoc/permission.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="3006c-120">[\<permission>](../../../visual-basic/language-reference/xmldoc/permission.md) <sup>1</sup></span></span>|[<span data-ttu-id="3006c-121">\<uwagi ></span><span class="sxs-lookup"><span data-stu-id="3006c-121">\<remarks></span></span>](../../../visual-basic/language-reference/xmldoc/remarks.md)|[<span data-ttu-id="3006c-122">\<returns></span><span class="sxs-lookup"><span data-stu-id="3006c-122">\<returns></span></span>](../../../visual-basic/language-reference/xmldoc/returns.md)|  
|<span data-ttu-id="3006c-123">[\<zobacz >](../../../visual-basic/language-reference/xmldoc/see.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="3006c-123">[\<see>](../../../visual-basic/language-reference/xmldoc/see.md) <sup>1</sup></span></span>|<span data-ttu-id="3006c-124">[\<seealso — >](../../../visual-basic/language-reference/xmldoc/seealso.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="3006c-124">[\<seealso>](../../../visual-basic/language-reference/xmldoc/seealso.md) <sup>1</sup></span></span>|[<span data-ttu-id="3006c-125">\<summary></span><span class="sxs-lookup"><span data-stu-id="3006c-125">\<summary></span></span>](../../../visual-basic/language-reference/xmldoc/summary.md)|  
|<span data-ttu-id="3006c-126">[\<typeparam >](../../../visual-basic/language-reference/xmldoc/typeparam.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="3006c-126">[\<typeparam>](../../../visual-basic/language-reference/xmldoc/typeparam.md) <sup>1</sup></span></span>|[<span data-ttu-id="3006c-127">\<value></span><span class="sxs-lookup"><span data-stu-id="3006c-127">\<value></span></span>](../../../visual-basic/language-reference/xmldoc/value.md)||  
  
 <span data-ttu-id="3006c-128">(<sup>1</sup> kompilator weryfikuje składnię).</span><span class="sxs-lookup"><span data-stu-id="3006c-128">(<sup>1</sup> The compiler verifies syntax.)</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3006c-129">Jeśli chcesz, aby nawiasy kątowe pojawiały się w tekście komentarza do dokumentacji, użyj `&lt;` i `&gt;`.</span><span class="sxs-lookup"><span data-stu-id="3006c-129">If you want angle brackets to appear in the text of a documentation comment, use `&lt;` and `&gt;`.</span></span> <span data-ttu-id="3006c-130">Na przykład ciąg `"&lt;text in angle brackets&gt;"` będzie wyświetlany jako `<text in angle brackets>`.</span><span class="sxs-lookup"><span data-stu-id="3006c-130">For example, the string `"&lt;text in angle brackets&gt;"` will appear as `<text in angle brackets>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3006c-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3006c-131">See also</span></span>

- [<span data-ttu-id="3006c-132">Dokumentowanie kodu za pomocą XML</span><span class="sxs-lookup"><span data-stu-id="3006c-132">Documenting Your Code with XML</span></span>](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
- [<span data-ttu-id="3006c-133">-doc</span><span class="sxs-lookup"><span data-stu-id="3006c-133">-doc</span></span>](../../../visual-basic/reference/command-line-compiler/doc.md)
- [<span data-ttu-id="3006c-134">Instrukcje: tworzenie dokumentacji XML</span><span class="sxs-lookup"><span data-stu-id="3006c-134">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
