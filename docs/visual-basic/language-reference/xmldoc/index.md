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
ms.openlocfilehash: af57fc7d55c5cfda24a2fd9406b17dedee898760
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400101"
---
# <a name="recommended-xml-tags-for-documentation-comments-visual-basic"></a>Zalecane tagi XML dla komentarzy dokumentacji (Visual Basic)
Kompilator Visual Basic może przetwarzać komentarze dokumentacji w kodzie do pliku XML. Możesz użyć dodatkowych narzędzi do przetworzenia pliku XML w dokumentacji.  
  
 Komentarze XML są dozwolone w konstrukcjach kodu, takich jak typy i elementy członkowskie typu. W przypadku typów częściowych tylko jedna część typu może zawierać komentarze XML, chociaż nie ma żadnych ograniczeń dotyczących komentowania jej elementów członkowskich.  
  
> [!NOTE]
> Komentarzy do dokumentacji nie można stosować do przestrzeni nazw. Przyczyną jest to, że jedna przestrzeń nazw może obejmować kilka zestawów, a nie wszystkie zestawy muszą być ładowane w tym samym czasie.  
  
 Kompilator przetwarza dowolny tag, który jest prawidłowym kodem XML. Poniższe Tagi zapewniają powszechnie używane funkcje w dokumentacji użytkownika.  
  
||||  
|---|---|---|  
|[\<c>](c.md)|[\<code>](code.md)|[\<example>](example.md)|  
|[\<exception>](exception.md)<sup>1</sup>|[\<include>](include.md)<sup>1</sup>|[\<list>](list.md)|  
|[\<para>](para.md)|[\<param>](param.md)<sup>1</sup>|[\<paramref>](paramref.md)|  
|[\<permission>](permission.md)<sup>1</sup>|[\<remarks>](remarks.md)|[\<returns>](returns.md)|  
|[\<see>](see.md)<sup>1</sup>|[\<seealso>](seealso.md)<sup>1</sup>|[\<summary>](summary.md)|  
|[\<typeparam>](typeparam.md)<sup>1</sup>|[\<value>](value.md)||  
  
 (<sup>1</sup> kompilator weryfikuje składnię).  
  
> [!NOTE]
> Jeśli chcesz, aby w tekście komentarza do dokumentacji pojawiły się nawiasy kątowe, użyj `&lt;` i `&gt;` . Na przykład ciąg `"&lt;text in angle brackets&gt;"` będzie wyświetlany jako `<text in angle brackets>` .  
  
## <a name="see-also"></a>Zobacz też

- [Dokumentowanie kodu za pomocą XML](../../programming-guide/program-structure/documenting-your-code-with-xml.md)
- [-doc](../../reference/command-line-compiler/doc.md)
- [Instrukcje: tworzenie dokumentacji XML](../../programming-guide/program-structure/how-to-create-xml-documentation.md)
