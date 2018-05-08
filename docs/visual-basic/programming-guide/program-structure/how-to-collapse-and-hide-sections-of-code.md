---
title: 'Porady: zwijanie i ukrywanie fragmentów kodu (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic, code collapsing
- Visual Basic, code hiding
- Visual Basic code, collapsing and hiding
ms.assetid: b770e8f5-e07d-491a-ab4b-a977980f9ba2
ms.openlocfilehash: f6c272b7ac016258d99873512cb789bba6739727
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-collapse-and-hide-sections-of-code-visual-basic"></a>Porady: zwijanie i ukrywanie fragmentów kodu (Visual Basic)
`#Region` Dyrektywy umożliwia zwijanie i ukrywanie fragmentów kodu w plikach języka Visual Basic. `#Region` Dyrektywy pozwala określić blok kodu, który można rozwinąć lub Zwiń, gdy za pomocą edytora kodu programu Visual Studio. Możliwość selektywnego ukrywanie kodu sprawia, że pliki można zarządzać i czytelne. Aby uzyskać więcej informacji, zobacz [Tworzenie konspektu](/visualstudio/ide/outlining).  
  
 `#Region` dyrektywy obsługuje semantyki blok kodu `#If...#End If`. Oznacza to nie może zaczynać się jeden blok, a kończyć się w innym; rozpoczęcia i zakończenia musi być w tym samym bloku. `#Region` dyrektywy nie są obsługiwane w funkcjach.  
  
### <a name="to-collapse-and-hide-a-section-of-code"></a>Zwijanie i ukrywanie sekcji kodu  
  
-   Umieść sekcji kodu między `#Region` i `#End Region` instrukcje, jak w poniższym przykładzie:  
  
     [!code-vb[VbVbalrConditionalComp#6](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/how-to-collapse-and-hide-sections-of-code_1.vb)]  
  
     `#Region` Bloku można używać wiele razy w pliku kodu, w związku z tym użytkownicy mogą definiować własne bloki procedur i klasy, które z kolei może zostać zwinięty. `#Region` bloki mogą być zagnieżdżone w innych `#Region` bloków.  
  
    > [!NOTE]
    >  Ukrywanie kodu nie uniemożliwia jej kompilowany i nie ma wpływu na `#If...#End If` instrukcje.  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilacja warunkowa](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 [#Region, dyrektywa](../../../visual-basic/language-reference/directives/region-directive.md)  
 [#If...Then...#Else, dyrektywy](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [Obramowanie](/visualstudio/ide/outlining)
