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
# <a name="recommended-xml-tags-for-documentation-comments-visual-basic"></a>Zalecane tagi XML dla komentarzy dokumentacji (Visual Basic)
Kompilator Visual Basic może przetwarzać komentarze dokumentacji w kodzie do pliku XML. Możesz użyć dodatkowych narzędzi do przetworzenia pliku XML w dokumentacji.  
  
 Komentarze XML są dozwolone w konstrukcjach kodu, takich jak typy i elementy członkowskie typu. W przypadku typów częściowych tylko jedna część typu może zawierać komentarze XML, chociaż nie ma żadnych ograniczeń dotyczących komentowania jej elementów członkowskich.  
  
> [!NOTE]
> Komentarzy do dokumentacji nie można stosować do przestrzeni nazw. Przyczyną jest to, że jedna przestrzeń nazw może obejmować kilka zestawów, a nie wszystkie zestawy muszą być ładowane w tym samym czasie.  
  
 Kompilator przetwarza dowolny tag, który jest prawidłowym kodem XML. Poniższe Tagi zapewniają powszechnie używane funkcje w dokumentacji użytkownika.  
  
||||  
|---|---|---|  
|[\<c >](../../../visual-basic/language-reference/xmldoc/c.md)|[> kodu \<](../../../visual-basic/language-reference/xmldoc/code.md)|[przykład \<>](../../../visual-basic/language-reference/xmldoc/example.md)|  
|[\<wyjątek >](../../../visual-basic/language-reference/xmldoc/exception.md) <sup>1</sup>|[\<uwzględnij >](../../../visual-basic/language-reference/xmldoc/include.md) <sup>1</sup>|[> Lista \<](../../../visual-basic/language-reference/xmldoc/list.md)|  
|[\<para >](../../../visual-basic/language-reference/xmldoc/para.md)|[\<param >](../../../visual-basic/language-reference/xmldoc/param.md) <sup>1</sup>|[\<paramref >](../../../visual-basic/language-reference/xmldoc/paramref.md)|  
|[> uprawnień\<](../../../visual-basic/language-reference/xmldoc/permission.md) <sup>1</sup>|[\<uwagi >](../../../visual-basic/language-reference/xmldoc/remarks.md)|[\<returns>](../../../visual-basic/language-reference/xmldoc/returns.md)|  
|[\<zobacz >](../../../visual-basic/language-reference/xmldoc/see.md) <sup>1</sup>|[\<seealso — >](../../../visual-basic/language-reference/xmldoc/seealso.md) <sup>1</sup>|[\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md)|  
|[\<typeparam >](../../../visual-basic/language-reference/xmldoc/typeparam.md) <sup>1</sup>|[\<value>](../../../visual-basic/language-reference/xmldoc/value.md)||  
  
 (<sup>1</sup> kompilator weryfikuje składnię).  
  
> [!NOTE]
> Jeśli chcesz, aby nawiasy kątowe pojawiały się w tekście komentarza do dokumentacji, użyj `&lt;` i `&gt;`. Na przykład ciąg `"&lt;text in angle brackets&gt;"` będzie wyświetlany jako `<text in angle brackets>`.  
  
## <a name="see-also"></a>Zobacz także

- [Dokumentowanie kodu za pomocą XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
- [-doc](../../../visual-basic/reference/command-line-compiler/doc.md)
- [Instrukcje: tworzenie dokumentacji XML](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
