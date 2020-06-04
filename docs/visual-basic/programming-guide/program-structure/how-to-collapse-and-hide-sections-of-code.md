---
title: 'Instrukcje: Zwijanie i ukrywanie fragmentów kodu'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic, code collapsing
- Visual Basic, code hiding
- Visual Basic code, collapsing and hiding
ms.assetid: b770e8f5-e07d-491a-ab4b-a977980f9ba2
ms.openlocfilehash: c11affe9c4dd4251ba8ff4b87029d314970b5fcb
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404852"
---
# <a name="how-to-collapse-and-hide-sections-of-code-visual-basic"></a>Porady: zwijanie i ukrywanie fragmentów kodu (Visual Basic)

`#Region`Dyrektywa umożliwia zwijanie i ukrywanie fragmentów kodu w plikach Visual Basic. `#Region`Dyrektywa pozwala określić blok kodu, który można rozwijać lub zwijać podczas korzystania z edytora kodu programu Visual Studio. Możliwość ukrycia kodu selektywnie sprawia, że pliki są bardziej łatwe do zarządzania i łatwiejsze do odczytania. Aby uzyskać więcej informacji, zobacz [Tworzenie konspektu](/visualstudio/ide/outlining).

`#Region`dyrektywy obsługują semantykę bloków kodu, taką jak `#If...#End If` . Oznacza to, że nie mogą rozpoczynać się w jednym bloku i kończyć w innym; początkowy i końcowy musi znajdować się w tym samym bloku. `#Region`dyrektywy nie są obsługiwane w funkcjach.

## <a name="to-collapse-and-hide-a-section-of-code"></a>Aby zwinąć i ukryć sekcję kodu

Umieść sekcję kodu między `#Region` `#End Region` instrukcjami i, jak w poniższym przykładzie:

[!code-vb[VbVbalrConditionalComp#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#6)]

`#Region`Blok może być używany wiele razy w pliku kodu. w ten sposób użytkownicy mogą definiować własne bloki procedur i klas, które mogą z kolei być zwinięte. `#Region`bloki mogą być również zagnieżdżane w innych `#Region` blokach.

> [!NOTE]
> Ukrycie kodu nie uniemożliwia jego skompilowania i nie wpływa na `#If...#End If` instrukcje.

## <a name="see-also"></a>Zobacz też

- [Kompilacja warunkowa](conditional-compilation.md)
- [#Region — dyrektywa](../../language-reference/directives/region-directive.md)
- [#If... Then... #Else — dyrektywy](../../language-reference/directives/if-then-else-directives.md)
- [Tworzenie konspektu](/visualstudio/ide/outlining)
