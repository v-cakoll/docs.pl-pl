---
title: Zalecane tagi XML dla komentarzy dokumentacji (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.XmlDocComment
helpviewer_keywords:
- tags, XML
- XML comments, recommended tags [Visual Basic]
- comments, recommended XML tags
ms.assetid: 294e0736-ff1e-498e-af83-6db71ed41a72
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 54712deb8bb2a5ed1e7b1f5fb8aa073dcdaf76d6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="recommended-xml-tags-for-documentation-comments-visual-basic"></a>Zalecane tagi XML dla komentarzy dokumentacji (Visual Basic)
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Kompilatora może przetwarzać komentarze do dokumentacji w kodzie do pliku XML. Dodatkowe narzędzia służy do przetwarzania pliku XML do dokumentacji.  
  
 Komentarze XML są dozwolone w konstrukcji kodu, takie jak typy i elementy członkowskie typu. Dla typów częściowych tylko jedną część typu może mieć komentarze XML, mimo że nie ma ograniczenia komentowania jej elementów członkowskich.  
  
> [!NOTE]
>  Komentarze dokumentacji nie można zastosować do przestrzeni nazw. Dzieje się tak że jednej przestrzeni nazw może obejmować kilka zestawów, a nie wszystkie zestawy muszą być załadowany w tym samym czasie.  
  
 Kompilator przetwarza wszystkie tag, który jest prawidłowym kodem XML. Następujące tagi zawierają często używane funkcje w dokumentacji użytkownika.  
  
||||  
|---|---|---|  
|[\<c >](../../../visual-basic/language-reference/xmldoc/c.md)|[\<Kod >](../../../visual-basic/language-reference/xmldoc/code.md)|[\<przykład >](../../../visual-basic/language-reference/xmldoc/example.md)|  
|[\<wyjątek >](../../../visual-basic/language-reference/xmldoc/exception.md) <sup>1</sup>|[\<obejmują >](../../../visual-basic/language-reference/xmldoc/include.md) <sup>1</sup>|[\<listy >](../../../visual-basic/language-reference/xmldoc/list.md)|  
|[\<para >](../../../visual-basic/language-reference/xmldoc/para.md)|[\<param >](../../../visual-basic/language-reference/xmldoc/param.md) <sup>1</sup>|[\<paramref >](../../../visual-basic/language-reference/xmldoc/paramref.md)|  
|[\<uprawnienia >](../../../visual-basic/language-reference/xmldoc/permission.md) <sup>1</sup>|[\<Remarks >](../../../visual-basic/language-reference/xmldoc/remarks.md)|[\<Zwraca >](../../../visual-basic/language-reference/xmldoc/returns.md)|  
|[\<zobacz >](../../../visual-basic/language-reference/xmldoc/see.md) <sup>1</sup>|[\<SeeAlso >](../../../visual-basic/language-reference/xmldoc/seealso.md) <sup>1</sup>|[\<podsumowania >](../../../visual-basic/language-reference/xmldoc/summary.md)|  
|[\<typeparam >](../../../visual-basic/language-reference/xmldoc/typeparam.md) <sup>1</sup>|[\<wartość >](../../../visual-basic/language-reference/xmldoc/value.md)||  
  
 (<sup>1</sup> kompilator sprawdza składnię.)  
  
> [!NOTE]
>  Nawiasy się pojawić w tekście komentarza do dokumentacji, należy użyć `<` i `>`. Na przykład ciąg `"<text in angle brackets>"` będą wyświetlane jako `<text in angle``brackets>`.  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentowanie kodu za pomocą XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)  
 [/ doc](../../../visual-basic/reference/command-line-compiler/doc.md)  
 [Porady: tworzenie dokumentacji XML](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
