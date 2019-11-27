---
title: 'Porady: zwijanie i ukrywanie fragmentów kodu'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic, code collapsing
- Visual Basic, code hiding
- Visual Basic code, collapsing and hiding
ms.assetid: b770e8f5-e07d-491a-ab4b-a977980f9ba2
ms.openlocfilehash: e7aacdc3f41199127b00d276b382ec4a5f258da0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347408"
---
# <a name="how-to-collapse-and-hide-sections-of-code-visual-basic"></a>Porady: zwijanie i ukrywanie fragmentów kodu (Visual Basic)

Dyrektywa `#Region` umożliwia zwijanie i ukrywanie fragmentów kodu w Visual Basic plikach. Dyrektywa `#Region` umożliwia określenie bloku kodu, który można rozwijać lub zwijać podczas korzystania z edytora kodu programu Visual Studio. Możliwość ukrycia kodu selektywnie sprawia, że pliki są bardziej łatwe do zarządzania i łatwiejsze do odczytania. Aby uzyskać więcej informacji, zobacz [Tworzenie konspektu](/visualstudio/ide/outlining).

dyrektywy `#Region` obsługują semantykę bloków kodu, taką jak `#If...#End If`. Oznacza to, że nie mogą rozpoczynać się w jednym bloku i kończyć w innym; początkowy i końcowy musi znajdować się w tym samym bloku. dyrektywy `#Region` nie są obsługiwane w funkcjach.

## <a name="to-collapse-and-hide-a-section-of-code"></a>Aby zwinąć i ukryć sekcję kodu

Umieść sekcję kodu między instrukcjami `#Region` i `#End Region`, jak w poniższym przykładzie:

[!code-vb[VbVbalrConditionalComp#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#6)]

Blok `#Region` może być używany wiele razy w pliku kodu; w ten sposób użytkownicy mogą definiować własne bloki procedur i klas, które mogą z kolei być zwinięte. bloki `#Region` mogą być również zagnieżdżane w innych blokach `#Region`.

> [!NOTE]
> Ukrycie kodu nie uniemożliwia jego skompilowania i nie ma wpływu na instrukcje `#If...#End If`.

## <a name="see-also"></a>Zobacz także

- [Kompilacja warunkowa](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- [#Region, dyrektywa](../../../visual-basic/language-reference/directives/region-directive.md)
- [#If...Then...#Else, dyrektywy](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [Obramowanie](/visualstudio/ide/outlining)
