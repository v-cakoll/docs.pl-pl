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
ms.openlocfilehash: 7830db136e9b900458496b36df5bc37f76661129
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523966"
---
# <a name="recommended-xml-tags-for-documentation-comments-visual-basic"></a><span data-ttu-id="dc6aa-102">Zalecane tagi XML dla komentarzy dokumentacji (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dc6aa-102">Recommended XML Tags for Documentation Comments (Visual Basic)</span></span>
<span data-ttu-id="dc6aa-103">Kompilator Visual Basic może przetwarzać komentarze dokumentacji w kodzie do pliku XML.</span><span class="sxs-lookup"><span data-stu-id="dc6aa-103">The Visual Basic compiler can process documentation comments in your code to an XML file.</span></span> <span data-ttu-id="dc6aa-104">Możesz użyć dodatkowych narzędzi do przetworzenia pliku XML w dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="dc6aa-104">You can use additional tools to process the XML file into documentation.</span></span>  
  
 <span data-ttu-id="dc6aa-105">Komentarze XML są dozwolone w konstrukcjach kodu, takich jak typy i elementy członkowskie typu.</span><span class="sxs-lookup"><span data-stu-id="dc6aa-105">XML comments are allowed on code constructs such as types and type members.</span></span> <span data-ttu-id="dc6aa-106">W przypadku typów częściowych tylko jedna część typu może zawierać komentarze XML, chociaż nie ma żadnych ograniczeń dotyczących komentowania jej elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="dc6aa-106">For partial types, only one part of the type can have XML comments, although there is no restriction on commenting its members.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dc6aa-107">Komentarzy do dokumentacji nie można stosować do przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="dc6aa-107">Documentation comments cannot be applied to namespaces.</span></span> <span data-ttu-id="dc6aa-108">Przyczyną jest to, że jedna przestrzeń nazw może obejmować kilka zestawów, a nie wszystkie zestawy muszą być ładowane w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="dc6aa-108">The reason is that one namespace can span several assemblies, and not all assemblies have to be loaded at the same time.</span></span>  
  
 <span data-ttu-id="dc6aa-109">Kompilator przetwarza dowolny tag, który jest prawidłowym kodem XML.</span><span class="sxs-lookup"><span data-stu-id="dc6aa-109">The compiler processes any tag that is valid XML.</span></span> <span data-ttu-id="dc6aa-110">Poniższe Tagi zapewniają powszechnie używane funkcje w dokumentacji użytkownika.</span><span class="sxs-lookup"><span data-stu-id="dc6aa-110">The following tags provide commonly used functionality in user documentation.</span></span>  
  
||||  
|---|---|---|  
|[<span data-ttu-id="dc6aa-111">\<c ></span><span class="sxs-lookup"><span data-stu-id="dc6aa-111">\<c></span></span>](../../../visual-basic/language-reference/xmldoc/c.md)|[<span data-ttu-id="dc6aa-112">\<code ></span><span class="sxs-lookup"><span data-stu-id="dc6aa-112">\<code></span></span>](../../../visual-basic/language-reference/xmldoc/code.md)|[<span data-ttu-id="dc6aa-113">\<example ></span><span class="sxs-lookup"><span data-stu-id="dc6aa-113">\<example></span></span>](../../../visual-basic/language-reference/xmldoc/example.md)|  
|<span data-ttu-id="dc6aa-114">[\<exception >](../../../visual-basic/language-reference/xmldoc/exception.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="dc6aa-114">[\<exception>](../../../visual-basic/language-reference/xmldoc/exception.md) <sup>1</sup></span></span>|<span data-ttu-id="dc6aa-115">[\<include >](../../../visual-basic/language-reference/xmldoc/include.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="dc6aa-115">[\<include>](../../../visual-basic/language-reference/xmldoc/include.md) <sup>1</sup></span></span>|[<span data-ttu-id="dc6aa-116">\<list ></span><span class="sxs-lookup"><span data-stu-id="dc6aa-116">\<list></span></span>](../../../visual-basic/language-reference/xmldoc/list.md)|  
|[<span data-ttu-id="dc6aa-117">\<para ></span><span class="sxs-lookup"><span data-stu-id="dc6aa-117">\<para></span></span>](../../../visual-basic/language-reference/xmldoc/para.md)|<span data-ttu-id="dc6aa-118">[\<param >](../../../visual-basic/language-reference/xmldoc/param.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="dc6aa-118">[\<param>](../../../visual-basic/language-reference/xmldoc/param.md) <sup>1</sup></span></span>|[<span data-ttu-id="dc6aa-119">\<paramref ></span><span class="sxs-lookup"><span data-stu-id="dc6aa-119">\<paramref></span></span>](../../../visual-basic/language-reference/xmldoc/paramref.md)|  
|<span data-ttu-id="dc6aa-120">[\<permission >](../../../visual-basic/language-reference/xmldoc/permission.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="dc6aa-120">[\<permission>](../../../visual-basic/language-reference/xmldoc/permission.md) <sup>1</sup></span></span>|[<span data-ttu-id="dc6aa-121">\<remarks ></span><span class="sxs-lookup"><span data-stu-id="dc6aa-121">\<remarks></span></span>](../../../visual-basic/language-reference/xmldoc/remarks.md)|[<span data-ttu-id="dc6aa-122">\<returns></span><span class="sxs-lookup"><span data-stu-id="dc6aa-122">\<returns></span></span>](../../../visual-basic/language-reference/xmldoc/returns.md)|  
|<span data-ttu-id="dc6aa-123">[\<see >](../../../visual-basic/language-reference/xmldoc/see.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="dc6aa-123">[\<see>](../../../visual-basic/language-reference/xmldoc/see.md) <sup>1</sup></span></span>|<span data-ttu-id="dc6aa-124">[\<seealso >](../../../visual-basic/language-reference/xmldoc/seealso.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="dc6aa-124">[\<seealso>](../../../visual-basic/language-reference/xmldoc/seealso.md) <sup>1</sup></span></span>|[<span data-ttu-id="dc6aa-125">\<summary></span><span class="sxs-lookup"><span data-stu-id="dc6aa-125">\<summary></span></span>](../../../visual-basic/language-reference/xmldoc/summary.md)|  
|<span data-ttu-id="dc6aa-126">[\<typeparam >](../../../visual-basic/language-reference/xmldoc/typeparam.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="dc6aa-126">[\<typeparam>](../../../visual-basic/language-reference/xmldoc/typeparam.md) <sup>1</sup></span></span>|[<span data-ttu-id="dc6aa-127">\<value></span><span class="sxs-lookup"><span data-stu-id="dc6aa-127">\<value></span></span>](../../../visual-basic/language-reference/xmldoc/value.md)||  
  
 <span data-ttu-id="dc6aa-128">(<sup>1</sup> kompilator weryfikuje składnię).</span><span class="sxs-lookup"><span data-stu-id="dc6aa-128">(<sup>1</sup> The compiler verifies syntax.)</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dc6aa-129">Jeśli chcesz, aby nawiasy kątowe pojawiały się w tekście komentarza do dokumentacji, użyj `&lt;` i `&gt;`.</span><span class="sxs-lookup"><span data-stu-id="dc6aa-129">If you want angle brackets to appear in the text of a documentation comment, use `&lt;` and `&gt;`.</span></span> <span data-ttu-id="dc6aa-130">Na przykład ciąg `"&lt;text in angle brackets&gt;"` będzie wyświetlany jako `<text in angle brackets>`.</span><span class="sxs-lookup"><span data-stu-id="dc6aa-130">For example, the string `"&lt;text in angle brackets&gt;"` will appear as `<text in angle brackets>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc6aa-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dc6aa-131">See also</span></span>

- [<span data-ttu-id="dc6aa-132">Dokumentowanie kodu za pomocą XML</span><span class="sxs-lookup"><span data-stu-id="dc6aa-132">Documenting Your Code with XML</span></span>](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
- [<span data-ttu-id="dc6aa-133">-doc</span><span class="sxs-lookup"><span data-stu-id="dc6aa-133">-doc</span></span>](../../../visual-basic/reference/command-line-compiler/doc.md)
- [<span data-ttu-id="dc6aa-134">Instrukcje: tworzenie dokumentacji XML</span><span class="sxs-lookup"><span data-stu-id="dc6aa-134">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
