---
title: Overridable
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
ms.openlocfilehash: 9c639665fd92a56de6fb6e5147cda873ef457b45
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351400"
---
# <a name="overridable-visual-basic"></a>Overridable (Visual Basic)
Określa, że właściwość lub procedura może być zastąpiona przez właściwość lub procedurę o identycznej nazwie w klasie pochodnej.  
  
## <a name="remarks"></a>Uwagi  
 Modyfikator `Overridable` pozwala na zastąpienie właściwości lub metody w klasie klasy pochodnej. Modyfikator [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md) uniemożliwia przesłanianie właściwości lub metody w klasie pochodnej.  Aby uzyskać więcej informacji, zobacz podstawowe informacje o [dziedziczeniu](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).  
  
 Jeśli nie określono modyfikatora `Overridable` lub `NotOverridable`, domyślne ustawienie zależy od tego, czy właściwość lub metoda przesłania właściwość lub metodę klasy bazowej. Jeśli właściwość lub metoda przesłania właściwość lub metodę klasy bazowej, ustawienie domyślne to `Overridable`; w przeciwnym razie jest `NotOverridable`.  
  
 Można wykonać cień lub przesłonięcie, aby ponownie zdefiniować Dziedziczony element, ale istnieją znaczne różnice między tymi dwoma podejściami. Aby uzyskać więcej informacji, zobacz [przesłanianie w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).  
  
 Element, który może być przesłonięty, jest czasami nazywany elementem *wirtualnym* . Jeśli może być zastąpiony, ale nie musi być, jest również czasami nazywane *konkretnym* elementem.  
  
 `Overridable` można użyć tylko w instrukcji deklaracji właściwości lub procedury.  
  
## <a name="combined-modifiers"></a>Połączone Modyfikatory  
 Nie można określić `Overridable` lub `NotOverridable` dla metody `Private`.  
  
 Nie można określić `Overridable` razem z `MustOverride`, `NotOverridable`lub `Shared` w tej samej deklaracji.  
  
 Ponieważ przesłaniający element jest niejawnie możliwy do zastąpienia, nie można połączyć `Overridable` z `Overrides`.  
  
## <a name="usage"></a>Sposób użycia  
 Modyfikator `Overridable` może być używany w tych kontekstach:  
  
 [Function, instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Property, instrukcja](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub, instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Zobacz także

- [Modyfikatory](../../../visual-basic/language-reference/modifiers/index.md)
- [Podstawowe informacje o dziedziczeniu](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)
- [Słowa kluczowe](../../../visual-basic/language-reference/keywords/index.md)
- [Obserwowanie w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
