---
title: 'Instrukcje: Zwijanie i ukrywanie fragmentów kodu (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic, code collapsing
- Visual Basic, code hiding
- Visual Basic code, collapsing and hiding
ms.assetid: b770e8f5-e07d-491a-ab4b-a977980f9ba2
ms.openlocfilehash: db396adf24c12542f720d3b235068aea2329288d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69949730"
---
# <a name="how-to-collapse-and-hide-sections-of-code-visual-basic"></a>Instrukcje: Zwijanie i ukrywanie fragmentów kodu (Visual Basic)
`#Region` Dyrektywa umożliwia zwijanie i ukrywanie fragmentów kodu w plikach Visual Basic. `#Region` Dyrektywa pozwala określić blok kodu, który można rozwijać lub zwijać podczas korzystania z edytora kodu programu Visual Studio. Możliwość ukrycia kodu selektywnie sprawia, że pliki są bardziej łatwe do zarządzania i łatwiejsze do odczytania. Aby uzyskać więcej informacji, zobacz [Tworzenie konspektu](/visualstudio/ide/outlining).  
  
 `#Region`dyrektywy obsługują semantykę bloków kodu, taką `#If...#End If`jak. Oznacza to, że nie mogą rozpoczynać się w jednym bloku i kończyć w innym; początkowy i końcowy musi znajdować się w tym samym bloku. `#Region`dyrektywy nie są obsługiwane w funkcjach.  
  
### <a name="to-collapse-and-hide-a-section-of-code"></a>Aby zwinąć i ukryć sekcję kodu  
  
- Umieść sekcję kodu między `#Region` instrukcjami i `#End Region` , jak w poniższym przykładzie:  
  
     [!code-vb[VbVbalrConditionalComp#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#6)]  
  
     `#Region` Blok może być używany wiele razy w pliku kodu. w ten sposób użytkownicy mogą definiować własne bloki procedur i klas, które mogą z kolei być zwinięte. `#Region`bloki mogą być również zagnieżdżane w `#Region` innych blokach.  
  
    > [!NOTE]
    > Ukrycie kodu nie uniemożliwia jego skompilowania i nie wpływa na `#If...#End If` instrukcje.  
  
## <a name="see-also"></a>Zobacz także

- [Kompilacja warunkowa](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- [#Region, dyrektywa](../../../visual-basic/language-reference/directives/region-directive.md)
- [#If...Then...#Else, dyrektywy](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [Obramowanie](/visualstudio/ide/outlining)
