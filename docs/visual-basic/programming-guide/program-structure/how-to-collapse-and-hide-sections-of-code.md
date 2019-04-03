---
title: 'Instrukcje: Zwijanie i ukrywanie fragmentów kodu (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic, code collapsing
- Visual Basic, code hiding
- Visual Basic code, collapsing and hiding
ms.assetid: b770e8f5-e07d-491a-ab4b-a977980f9ba2
ms.openlocfilehash: bf2a7188456097ac227039e4d902a14eb182664c
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58822302"
---
# <a name="how-to-collapse-and-hide-sections-of-code-visual-basic"></a>Instrukcje: Zwijanie i ukrywanie fragmentów kodu (Visual Basic)
`#Region` Dyrektywy umożliwia zwijanie i ukrywanie fragmentów kodu w plikach języka Visual Basic. `#Region` Dyrektywy umożliwia określenie blok kodu, który będzie można rozszerzać lub Zwiń, korzystając z edytora kodu Visual Studio. Możliwość selektywnego Ukryj kod sprawia, że pliki w zarządzaniu i czytelne. Aby uzyskać więcej informacji, zobacz [konspekt](/visualstudio/ide/outlining).  
  
 `#Region` dyrektywy obsługują semantyki bloku kodu, takie jak `#If...#End If`. Oznacza, że ich nie może rozpoczynać się w jednym bloku i kończyć w innym; wartości początkowa i końcowa musi być w tym samym bloku. `#Region` dyrektywy nie są obsługiwane w obrębie funkcji.  
  
### <a name="to-collapse-and-hide-a-section-of-code"></a>Aby zwinąć i ukryć sekcję kodu  
  
-   Umieść części kodu między `#Region` i `#End Region` instrukcje, jak w poniższym przykładzie:  
  
     [!code-vb[VbVbalrConditionalComp#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#6)]  
  
     `#Region` Bloku można używać wiele razy w pliku kodu; w związku z tym, użytkownicy mogą definiować własne bloki procedur i klas, które z kolei mogą zostać zwinięty. `#Region` bloki mogą być zagnieżdżone w innych `#Region` bloków.  
  
    > [!NOTE]
    >  Ukrywanie kodu nie zapobiega on kompilowany i nie ma wpływu na `#If...#End If` instrukcji.  
  
## <a name="see-also"></a>Zobacz także

- [Kompilacja warunkowa](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- [#Region, dyrektywa](../../../visual-basic/language-reference/directives/region-directive.md)
- [#If...Then...#Else, dyrektywy](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [Obramowanie](/visualstudio/ide/outlining)
