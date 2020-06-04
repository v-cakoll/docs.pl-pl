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
ms.openlocfilehash: 1b20108a2d42e82c0af7598fde8d60a08fea28ec
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396197"
---
# <a name="mustoverride-visual-basic"></a>MustOverride (Visual Basic)
Określa, że właściwość lub procedura nie jest zaimplementowana w tej klasie i musi zostać przesłonięta w klasie pochodnej, zanim będzie mogła zostać użyta.  
  
## <a name="remarks"></a>Uwagi  
 Można użyć `MustOverride` tylko w instrukcji deklaracji właściwości lub procedury. Właściwość lub procedura, która określa, `MustOverride` musi być elementem członkowskim klasy, a Klasa musi być oznaczona jako [MustInherit](mustinherit.md).  
  
## <a name="rules"></a>Reguły  
  
- **Niekompletna deklaracja.** Jeśli określisz `MustOverride` , nie podasz żadnych dodatkowych wierszy kodu dla właściwości lub procedury, a nie `End Function` `End Property` instrukcji, lub `End Sub` .  
  
- **Połączone modyfikatory.** Nie można określić `MustOverride` razem z `NotOverridable` , `Overridable` , lub `Shared` w tej samej deklaracji.  
  
- **Przesłanianie i zastępowanie.** Zarówno przesłanianie, jak i przesłonięcie przedefiniują Dziedziczony element, ale istnieją znaczne różnice między tymi dwoma podejściami. Aby uzyskać więcej informacji, zobacz [przesłanianie w Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md).  
  
- **Alternatywne warunki.** Element, którego nie można użyć z wyjątkiem przesłonięcia, jest czasami nazywany *czystym elementem wirtualnym* .  
  
 `MustOverride`Modyfikator może być używany w tych kontekstach:  
  
 [Function, instrukcja](../statements/function-statement.md)  
  
 [Property — Instrukcja](../statements/property-statement.md)  
  
 [Sub, instrukcja](../statements/sub-statement.md)  
  
## <a name="see-also"></a>Zobacz też

- [NotOverridable](notoverridable.md)
- [Overridable](overridable.md)
- [Przesłonięcia](overrides.md)
- [MustInherit](mustinherit.md)
- [Słowa kluczowe](../keywords/index.md)
- [Przesłanianie w Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md)
