---
title: MustOverride (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.MustOverride
- MustOverride
helpviewer_keywords:
- virtual elements [Visual Basic], pure
- elements [Visual Basic], pure virtual
- properties [Visual Basic], redefining
- procedures [Visual Basic], overriding
- overriding, MustOverride keyword
- procedures [Visual Basic], redefining
- pure virtual elements [Visual Basic]
- MustOverride keyword [Visual Basic]
- properties [Visual Basic], overriding
ms.assetid: 6e9d9ad6-bb64-433f-b32b-3ef84293bf96
ms.openlocfilehash: 0ddd7d0d2a57afc02aa7483ba5e83b65c48af534
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58822820"
---
# <a name="mustoverride-visual-basic"></a>MustOverride (Visual Basic)
Określa, że właściwość lub procedura nie jest zaimplementowana w tej klasie i musi zostać zastąpiona w klasie pochodnej, zanim będzie można jej używać.  
  
## <a name="remarks"></a>Uwagi  
 Możesz użyć `MustOverride` tylko w instrukcji deklaracji właściwość lub procedura. Właściwość lub procedura, która określa `MustOverride` musi należeć do klasy, a klasy muszą być oznaczone jako [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).  
  
## <a name="rules"></a>reguły  
  
-   **Deklaracja niekompletne.** Po określeniu `MustOverride`, nie trzeba dostarczać żadnych dodatkowych wierszy kodu właściwość lub procedura, nie nawet `End Function`, `End Property`, lub `End Sub` instrukcji.  
  
-   **Modyfikatory połączone.** Nie można określić `MustOverride` wraz z `NotOverridable`, `Overridable`, lub `Shared` w tej samej deklaracji.  
  
-   **Przesłanianiem i zastępowaniem.** Zarówno przesłanianiem i zastępowaniem przedefiniować dziedziczonego elementu, ale istnieją znaczne różnice między dwa podejścia. Aby uzyskać więcej informacji, zobacz [przesłanianie w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).  
  
-   **Alternatywne warunki.** Element, którego nie można użyć z wyjątkiem w zastąpieniu jest czasami nazywane *czystej wirtualnej* elementu.  
  
 `MustOverride` Modyfikator mogą być używane w tych kontekstach:  
  
 [Function, instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Instrukcja Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub, instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Zobacz także

- [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)
- [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)
- [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)
- [Słowa kluczowe](../../../visual-basic/language-reference/keywords/index.md)
- [Przesłanianie w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
