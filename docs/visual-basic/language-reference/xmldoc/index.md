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
ms.openlocfilehash: e59ee25b22c51e47dc83233af33099e6c55de87b
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58814953"
---
# <a name="recommended-xml-tags-for-documentation-comments-visual-basic"></a>Zalecane tagi XML dla komentarzy dokumentacji (Visual Basic)
Kompilator Visual Basic przetwarzanie komentarzy dokumentacji w kodzie do pliku XML. Można użyć dodatkowych narzędzi do przetwarzania pliku XML do dokumentacji.  
  
 Komentarze XML są dozwolone na kodzie konstrukcji, takich jak typy i elementy członkowskie typu. Dla typów częściowych tylko jedną część tego typu może mieć komentarze XML, mimo że nie ma żadnych ograniczeń na dodawanie komentarza do jego członków.  
  
> [!NOTE]
>  Komentarze dokumentacji nie można zastosować do przestrzeni nazw. Przyczyną jest, że jedną przestrzeń nazw może obejmować kilka zestawów, a nie wszystkie zestawy posiadają do załadowania w tym samym czasie.  
  
 Kompilator przetworzy dowolnymi tagami, które jest prawidłowym kodem XML. Następujące znaczniki oferuje powszechnie używanych w dokumentacji użytkownika.  
  
||||  
|---|---|---|  
|[\<c>](../../../visual-basic/language-reference/xmldoc/c.md)|[\<code>](../../../visual-basic/language-reference/xmldoc/code.md)|[\<przykład >](../../../visual-basic/language-reference/xmldoc/example.md)|  
|[\<wyjątek >](../../../visual-basic/language-reference/xmldoc/exception.md) <sup>1</sup>|[\<obejmują >](../../../visual-basic/language-reference/xmldoc/include.md) <sup>1</sup>|[\<list>](../../../visual-basic/language-reference/xmldoc/list.md)|  
|[\<para>](../../../visual-basic/language-reference/xmldoc/para.md)|[\<param>](../../../visual-basic/language-reference/xmldoc/param.md) <sup>1</sup>|[\<paramref>](../../../visual-basic/language-reference/xmldoc/paramref.md)|  
|[\<uprawnienie >](../../../visual-basic/language-reference/xmldoc/permission.md) <sup>1</sup>|[\<Remarks >](../../../visual-basic/language-reference/xmldoc/remarks.md)|[\<returns>](../../../visual-basic/language-reference/xmldoc/returns.md)|  
|[\<see>](../../../visual-basic/language-reference/xmldoc/see.md) <sup>1</sup>|[\<seealso>](../../../visual-basic/language-reference/xmldoc/seealso.md) <sup>1</sup>|[\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md)|  
|[\<typeparam >](../../../visual-basic/language-reference/xmldoc/typeparam.md) <sup>1</sup>|[\<value>](../../../visual-basic/language-reference/xmldoc/value.md)||  
  
 (<sup>1</sup> kompilator sprawdza składnię.)  
  
> [!NOTE]
>  Nawiasy są wyświetlane w tekście komentarza do dokumentacji, użyć `&lt;` i `&gt;`. Na przykład ciąg `"&lt;text in angle brackets&gt;"` będą wyświetlane jako `<text in angle brackets>`.  
  
## <a name="see-also"></a>Zobacz także

- [Dokumentowanie kodu za pomocą XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
- [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)
- [Instrukcje: Tworzenie dokumentacji XML](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
