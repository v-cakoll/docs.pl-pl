---
title: Zalecane tagi XML dla komentarzy dokumentacji (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlDocComment
helpviewer_keywords:
- tags, XML
- XML comments, recommended tags [Visual Basic]
- comments, recommended XML tags
ms.assetid: 294e0736-ff1e-498e-af83-6db71ed41a72
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 54712deb8bb2a5ed1e7b1f5fb8aa073dcdaf76d6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="recommended-xml-tags-for-documentation-comments-visual-basic"></a><span data-ttu-id="8fc6a-102">Zalecane tagi XML dla komentarzy dokumentacji (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8fc6a-102">Recommended XML Tags for Documentation Comments (Visual Basic)</span></span>
<span data-ttu-id="8fc6a-103">[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Kompilatora może przetwarzać komentarze do dokumentacji w kodzie do pliku XML.</span><span class="sxs-lookup"><span data-stu-id="8fc6a-103">The [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler can process documentation comments in your code to an XML file.</span></span> <span data-ttu-id="8fc6a-104">Dodatkowe narzędzia służy do przetwarzania pliku XML do dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="8fc6a-104">You can use additional tools to process the XML file into documentation.</span></span>  
  
 <span data-ttu-id="8fc6a-105">Komentarze XML są dozwolone w konstrukcji kodu, takie jak typy i elementy członkowskie typu.</span><span class="sxs-lookup"><span data-stu-id="8fc6a-105">XML comments are allowed on code constructs such as types and type members.</span></span> <span data-ttu-id="8fc6a-106">Dla typów częściowych tylko jedną część typu może mieć komentarze XML, mimo że nie ma ograniczenia komentowania jej elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="8fc6a-106">For partial types, only one part of the type can have XML comments, although there is no restriction on commenting its members.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8fc6a-107">Komentarze dokumentacji nie można zastosować do przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="8fc6a-107">Documentation comments cannot be applied to namespaces.</span></span> <span data-ttu-id="8fc6a-108">Dzieje się tak że jednej przestrzeni nazw może obejmować kilka zestawów, a nie wszystkie zestawy muszą być załadowany w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="8fc6a-108">The reason is that one namespace can span several assemblies, and not all assemblies have to be loaded at the same time.</span></span>  
  
 <span data-ttu-id="8fc6a-109">Kompilator przetwarza wszystkie tag, który jest prawidłowym kodem XML.</span><span class="sxs-lookup"><span data-stu-id="8fc6a-109">The compiler processes any tag that is valid XML.</span></span> <span data-ttu-id="8fc6a-110">Następujące tagi zawierają często używane funkcje w dokumentacji użytkownika.</span><span class="sxs-lookup"><span data-stu-id="8fc6a-110">The following tags provide commonly used functionality in user documentation.</span></span>  
  
||||  
|---|---|---|  
|[<span data-ttu-id="8fc6a-111">\<c ></span><span class="sxs-lookup"><span data-stu-id="8fc6a-111">\<c></span></span>](../../../visual-basic/language-reference/xmldoc/c.md)|[<span data-ttu-id="8fc6a-112">\<Kod ></span><span class="sxs-lookup"><span data-stu-id="8fc6a-112">\<code></span></span>](../../../visual-basic/language-reference/xmldoc/code.md)|[<span data-ttu-id="8fc6a-113">\<przykład ></span><span class="sxs-lookup"><span data-stu-id="8fc6a-113">\<example></span></span>](../../../visual-basic/language-reference/xmldoc/example.md)|  
|<span data-ttu-id="8fc6a-114">[\<wyjątek >](../../../visual-basic/language-reference/xmldoc/exception.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="8fc6a-114">[\<exception>](../../../visual-basic/language-reference/xmldoc/exception.md) <sup>1</sup></span></span>|<span data-ttu-id="8fc6a-115">[\<obejmują >](../../../visual-basic/language-reference/xmldoc/include.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="8fc6a-115">[\<include>](../../../visual-basic/language-reference/xmldoc/include.md) <sup>1</sup></span></span>|[<span data-ttu-id="8fc6a-116">\<listy ></span><span class="sxs-lookup"><span data-stu-id="8fc6a-116">\<list></span></span>](../../../visual-basic/language-reference/xmldoc/list.md)|  
|[<span data-ttu-id="8fc6a-117">\<para ></span><span class="sxs-lookup"><span data-stu-id="8fc6a-117">\<para></span></span>](../../../visual-basic/language-reference/xmldoc/para.md)|<span data-ttu-id="8fc6a-118">[\<param >](../../../visual-basic/language-reference/xmldoc/param.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="8fc6a-118">[\<param>](../../../visual-basic/language-reference/xmldoc/param.md) <sup>1</sup></span></span>|[<span data-ttu-id="8fc6a-119">\<paramref ></span><span class="sxs-lookup"><span data-stu-id="8fc6a-119">\<paramref></span></span>](../../../visual-basic/language-reference/xmldoc/paramref.md)|  
|<span data-ttu-id="8fc6a-120">[\<uprawnienia >](../../../visual-basic/language-reference/xmldoc/permission.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="8fc6a-120">[\<permission>](../../../visual-basic/language-reference/xmldoc/permission.md) <sup>1</sup></span></span>|[<span data-ttu-id="8fc6a-121">\<Remarks ></span><span class="sxs-lookup"><span data-stu-id="8fc6a-121">\<remarks></span></span>](../../../visual-basic/language-reference/xmldoc/remarks.md)|[<span data-ttu-id="8fc6a-122">\<Zwraca ></span><span class="sxs-lookup"><span data-stu-id="8fc6a-122">\<returns></span></span>](../../../visual-basic/language-reference/xmldoc/returns.md)|  
|<span data-ttu-id="8fc6a-123">[\<zobacz >](../../../visual-basic/language-reference/xmldoc/see.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="8fc6a-123">[\<see>](../../../visual-basic/language-reference/xmldoc/see.md) <sup>1</sup></span></span>|<span data-ttu-id="8fc6a-124">[\<SeeAlso >](../../../visual-basic/language-reference/xmldoc/seealso.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="8fc6a-124">[\<seealso>](../../../visual-basic/language-reference/xmldoc/seealso.md) <sup>1</sup></span></span>|[<span data-ttu-id="8fc6a-125">\<podsumowania ></span><span class="sxs-lookup"><span data-stu-id="8fc6a-125">\<summary></span></span>](../../../visual-basic/language-reference/xmldoc/summary.md)|  
|<span data-ttu-id="8fc6a-126">[\<typeparam >](../../../visual-basic/language-reference/xmldoc/typeparam.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="8fc6a-126">[\<typeparam>](../../../visual-basic/language-reference/xmldoc/typeparam.md) <sup>1</sup></span></span>|[<span data-ttu-id="8fc6a-127">\<wartość ></span><span class="sxs-lookup"><span data-stu-id="8fc6a-127">\<value></span></span>](../../../visual-basic/language-reference/xmldoc/value.md)||  
  
 <span data-ttu-id="8fc6a-128">(<sup>1</sup> kompilator sprawdza składnię.)</span><span class="sxs-lookup"><span data-stu-id="8fc6a-128">(<sup>1</sup> The compiler verifies syntax.)</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8fc6a-129">Nawiasy się pojawić w tekście komentarza do dokumentacji, należy użyć `<` i `>`.</span><span class="sxs-lookup"><span data-stu-id="8fc6a-129">If you want angle brackets to appear in the text of a documentation comment, use `<` and `>`.</span></span> <span data-ttu-id="8fc6a-130">Na przykład ciąg `"<text in angle brackets>"` będą wyświetlane jako `<text in angle``brackets>`.</span><span class="sxs-lookup"><span data-stu-id="8fc6a-130">For example, the string `"<text in angle brackets>"` will appear as `<text in angle``brackets>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fc6a-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8fc6a-131">See Also</span></span>  
 [<span data-ttu-id="8fc6a-132">Dokumentowanie kodu za pomocą XML</span><span class="sxs-lookup"><span data-stu-id="8fc6a-132">Documenting Your Code with XML</span></span>](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)  
 [<span data-ttu-id="8fc6a-133">/ doc</span><span class="sxs-lookup"><span data-stu-id="8fc6a-133">/doc</span></span>](../../../visual-basic/reference/command-line-compiler/doc.md)  
 [<span data-ttu-id="8fc6a-134">Porady: tworzenie dokumentacji XML</span><span class="sxs-lookup"><span data-stu-id="8fc6a-134">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
