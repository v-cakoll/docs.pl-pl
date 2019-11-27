---
title: MustOverride
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
ms.openlocfilehash: dc6a153a604fd0e5cee9d7d46ebcd63294f33628
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351485"
---
# <a name="mustoverride-visual-basic"></a>MustOverride (Visual Basic)
Określa, że właściwość lub procedura nie jest zaimplementowana w tej klasie i musi zostać przesłonięta w klasie pochodnej, zanim będzie mogła zostać użyta.  
  
## <a name="remarks"></a>Uwagi  
 `MustOverride` można użyć tylko w instrukcji deklaracji właściwości lub procedury. Właściwość lub procedura, która określa `MustOverride` musi być elementem członkowskim klasy, a Klasa musi być oznaczona jako [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).  
  
## <a name="rules"></a>Reguły  
  
- **Niekompletna deklaracja.** Po określeniu `MustOverride`nie są dostarczane żadne dodatkowe wiersze kodu dla właściwości lub procedury, a nie nawet instrukcji `End Function`, `End Property`lub `End Sub`.  
  
- **Połączone modyfikatory.** Nie można określić `MustOverride` razem z `NotOverridable`, `Overridable`lub `Shared` w tej samej deklaracji.  
  
- **Przesłanianie i zastępowanie.** Zarówno przesłanianie, jak i przesłonięcie przedefiniują Dziedziczony element, ale istnieją znaczne różnice między tymi dwoma podejściami. Aby uzyskać więcej informacji, zobacz [przesłanianie w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).  
  
- **Alternatywne warunki.** Element, którego nie można użyć z wyjątkiem przesłonięcia, jest czasami nazywany *czystym elementem wirtualnym* .  
  
 Modyfikator `MustOverride` może być używany w tych kontekstach:  
  
 [Function, instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Property, instrukcja](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub, instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Zobacz także

- [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)
- [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)
- [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)
- [Słowa kluczowe](../../../visual-basic/language-reference/keywords/index.md)
- [Obserwowanie w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
