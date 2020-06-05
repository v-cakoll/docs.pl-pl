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
ms.openlocfilehash: dcbabde8464dd8a0ce5fad24d7d72b1e780270d3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392122"
---
# <a name="overridable-visual-basic"></a>Overridable (Visual Basic)
Określa, że właściwość lub procedura może być zastąpiona przez właściwość lub procedurę o identycznej nazwie w klasie pochodnej.  
  
## <a name="remarks"></a>Uwagi  
 `Overridable`Modyfikator zezwala na przesłanianie właściwości lub metody w klasie klasy pochodnej. Modyfikator [NotOverridable](notoverridable.md) uniemożliwia przesłanianie właściwości lub metody w klasie pochodnej.  Aby uzyskać więcej informacji, zobacz podstawowe informacje o [dziedziczeniu](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md).  
  
 Jeśli `Overridable` modyfikator or `NotOverridable` nie jest określony, ustawienie domyślne zależy od tego, czy właściwość lub metoda przesłania właściwość lub metodę klasy bazowej. Jeśli właściwość lub metoda przesłania właściwość lub metodę klasy bazowej, ustawienie domyślne to `Overridable` ; w przeciwnym razie jest `NotOverridable` .  
  
 Można wykonać cień lub przesłonięcie, aby ponownie zdefiniować Dziedziczony element, ale istnieją znaczne różnice między tymi dwoma podejściami. Aby uzyskać więcej informacji, zobacz [przesłanianie w Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md).  
  
 Element, który może być przesłonięty, jest czasami nazywany elementem *wirtualnym* . Jeśli może być zastąpiony, ale nie musi być, jest również czasami nazywane *konkretnym* elementem.  
  
 Można użyć `Overridable` tylko w instrukcji deklaracji właściwości lub procedury.  
  
## <a name="combined-modifiers"></a>Połączone Modyfikatory  
 Nie można określić `Overridable` lub `NotOverridable` dla `Private` metody.  
  
 Nie można określić `Overridable` razem z `MustOverride` , `NotOverridable` , lub `Shared` w tej samej deklaracji.  
  
 Ponieważ przesłaniający element jest niejawnie możliwy do zastąpienia, nie można połączyć `Overridable` się z `Overrides` .  
  
## <a name="usage"></a>Użycie  
 `Overridable`Modyfikator może być używany w tych kontekstach:  
  
 [Function, instrukcja](../statements/function-statement.md)  
  
 [Property — Instrukcja](../statements/property-statement.md)  
  
 [Sub, instrukcja](../statements/sub-statement.md)  
  
## <a name="see-also"></a>Zobacz też

- [Modyfikatory](index.md)
- [Podstawowe informacje o dziedziczeniu](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [MustOverride](mustoverride.md)
- [NotOverridable](notoverridable.md)
- [Przesłonięcia](overrides.md)
- [Słowa kluczowe](../keywords/index.md)
- [Przesłanianie w Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md)
