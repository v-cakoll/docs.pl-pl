---
title: Overridable (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- Overridable
- vb.Overridable
helpviewer_keywords:
- elements [Visual Basic], concrete
- properties [Visual Basic], redefining
- overriding, Overridable keyword
- elements [Visual Basic], virtual
- virtual [elements VB]
- procedures [Visual Basic], overriding
- concrete [elements VB]
- procedures [Visual Basic], redefining
- Overridable keyword [Visual Basic]
- properties [Visual Basic], overriding
ms.assetid: 612581e7-8a4c-4a5d-beff-3402fffa6f35
ms.openlocfilehash: 7002589b303c41b26b611588f339fa70dd19f959
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54537598"
---
# <a name="overridable-visual-basic"></a>Overridable (Visual Basic)
Określa, że właściwość lub procedura może być zastąpione o identycznej nazwie właściwość lub procedura w klasie pochodnej.  
  
## <a name="remarks"></a>Uwagi  
 `Overridable` Modyfikator umożliwia właściwość lub metoda klasy został nadpisany w klasie pochodnej. [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md) modyfikator zapobiega zastępowaniu w klasie pochodnej właściwości lub metody.  Aby uzyskać więcej informacji, zobacz [podstawowe informacje o dziedziczeniu](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).  
  
 Jeśli `Overridable` lub `NotOverridable` modyfikator nie zostanie określony, domyślnie zależy od tego, czy właściwość lub metoda zastępuje właściwości klasy bazowej lub metody. Jeśli właściwość lub metoda zastępuje właściwości klasy bazowej lub metody, domyślne ustawienie to `Overridable`; w przeciwnym razie jest `NotOverridable`.  
  
 Można w tle lub Przesłoń, aby zdefiniować dziedziczonego elementu, ale istnieją znaczne różnice między dwa podejścia. Aby uzyskać więcej informacji, zobacz [przesłanianie w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).  
  
 Element, który może zostać przesłonięta jest czasami określane jako *wirtualnego* elementu. Jeśli może zostać zastąpiona, ale nie musi być, niekiedy nazywanych również *konkretnych* elementu.  
  
 Możesz użyć `Overridable` tylko w instrukcji deklaracji właściwość lub procedura.  
  
## <a name="combined-modifiers"></a>Modyfikatory połączone  
 Nie można określić `Overridable` lub `NotOverridable` dla `Private` metody.  
  
 Nie można określić `Overridable` wraz z `MustOverride`, `NotOverridable`, lub `Shared` w tej samej deklaracji.  
  
 Ponieważ element nadrzędnych jest niejawnie możliwym do zastąpienia, nie można połączyć `Overridable` z `Overrides`.  
  
## <a name="usage"></a>Użycie  
 `Overridable` Modyfikator mogą być używane w tych kontekstach:  
  
 [Function, instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Instrukcja Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub, instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Zobacz także
- [Modyfikatory](../../../visual-basic/language-reference/modifiers/index.md)
- [Podstawowe informacje o dziedziczeniu](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)
- [Słowa kluczowe](../../../visual-basic/language-reference/keywords/index.md)
- [Przesłanianie w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
