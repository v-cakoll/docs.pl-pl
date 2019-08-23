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
ms.openlocfilehash: 2d6519af8ca1a0e2d59131eec4d63646dce7318b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913506"
---
# <a name="recommended-xml-tags-for-documentation-comments-visual-basic"></a>Zalecane tagi XML dla komentarzy dokumentacji (Visual Basic)
Kompilator Visual Basic może przetwarzać komentarze dokumentacji w kodzie do pliku XML. Możesz użyć dodatkowych narzędzi do przetworzenia pliku XML w dokumentacji.  
  
 Komentarze XML są dozwolone w konstrukcjach kodu, takich jak typy i elementy członkowskie typu. W przypadku typów częściowych tylko jedna część typu może zawierać komentarze XML, chociaż nie ma żadnych ograniczeń dotyczących komentowania jej elementów członkowskich.  
  
> [!NOTE]
> Komentarzy do dokumentacji nie można stosować do przestrzeni nazw. Przyczyną jest to, że jedna przestrzeń nazw może obejmować kilka zestawów, a nie wszystkie zestawy muszą być ładowane w tym samym czasie.  
  
 Kompilator przetwarza dowolny tag, który jest prawidłowym kodem XML. Poniższe Tagi zapewniają powszechnie używane funkcje w dokumentacji użytkownika.  
  
||||  
|---|---|---|  
|[\<c>](../../../visual-basic/language-reference/xmldoc/c.md)|[\<> kodu](../../../visual-basic/language-reference/xmldoc/code.md)|[\<przykład >](../../../visual-basic/language-reference/xmldoc/example.md)|  
|wyjątek > <sup>1</sup> [ \<](../../../visual-basic/language-reference/xmldoc/exception.md)|Uwzględnij > <sup>1</sup> [ \<](../../../visual-basic/language-reference/xmldoc/include.md)|[\<list>](../../../visual-basic/language-reference/xmldoc/list.md)|  
|[\<> para](../../../visual-basic/language-reference/xmldoc/para.md)|param > <sup>1</sup> [ \<](../../../visual-basic/language-reference/xmldoc/param.md)|[\<paramref >](../../../visual-basic/language-reference/xmldoc/paramref.md)|  
|uprawnienie > <sup>1</sup> [ \<](../../../visual-basic/language-reference/xmldoc/permission.md)|[\<uwagi >](../../../visual-basic/language-reference/xmldoc/remarks.md)|[\<returns>](../../../visual-basic/language-reference/xmldoc/returns.md)|  
|Zobacz > <sup>1</sup> [ \<](../../../visual-basic/language-reference/xmldoc/see.md)|seealso — > <sup>1</sup> [ \<](../../../visual-basic/language-reference/xmldoc/seealso.md)|[\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md)|  
|typeparam > <sup>1</sup> [ \<](../../../visual-basic/language-reference/xmldoc/typeparam.md)|[\<value>](../../../visual-basic/language-reference/xmldoc/value.md)||  
  
 (<sup>1</sup> kompilator weryfikuje składnię).  
  
> [!NOTE]
> Jeśli chcesz, aby w tekście komentarza do dokumentacji pojawiły się nawiasy kątowe `&gt;`, użyj `&lt;` i. Na przykład ciąg `"&lt;text in angle brackets&gt;"` będzie wyświetlany jako `<text in angle brackets>`.  
  
## <a name="see-also"></a>Zobacz także

- [Dokumentowanie kodu za pomocą XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
- [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)
- [Instrukcje: Utwórz dokumentację XML](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
