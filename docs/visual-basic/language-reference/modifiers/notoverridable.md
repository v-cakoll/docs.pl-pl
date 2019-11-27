---
title: NotOverridable
ms.date: 07/20/2015
f1_keywords:
- vb.NotOverridable
- NotOverridable
helpviewer_keywords:
- sealed methods [Visual Basic]
- NotOverridable keyword [Visual Basic]
- properties [Visual Basic], redefining
- elements [Visual Basic], sealed
- sealed [elements VB]
- procedures [Visual Basic], overriding
- procedures [Visual Basic], redefining
- overriding
- methods [Visual Basic], sealed
- properties [Visual Basic], overriding
ms.assetid: 66ec6984-f5f5-4857-b362-6a3907aaf9e0
ms.openlocfilehash: c55d57bb3008b2825fe5382844908ea32f0d500c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351443"
---
# <a name="notoverridable-visual-basic"></a>NotOverridable (Visual Basic)
Określa, że właściwość lub procedura nie może zostać zastąpiona w klasie pochodnej.  
  
## <a name="remarks"></a>Uwagi  
 Modyfikator `NotOverridable` uniemożliwia przesłanianie właściwości lub metody w klasie pochodnej.  Modyfikator [, który umożliwia](../../../visual-basic/language-reference/modifiers/overridable.md) zastąpienie właściwości lub metody w klasie klasy pochodnej. Aby uzyskać więcej informacji, zobacz podstawowe informacje o [dziedziczeniu](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).  
  
 Jeśli nie określono modyfikatora `Overridable` lub `NotOverridable`, domyślne ustawienie zależy od tego, czy właściwość lub metoda przesłania właściwość lub metodę klasy bazowej. Jeśli właściwość lub metoda przesłania właściwość lub metodę klasy bazowej, ustawienie domyślne to `Overridable`; w przeciwnym razie jest `NotOverridable`.  
  
 Element, który nie może zostać zastąpiony, jest czasami nazywany *zapieczętowanym* elementem.  
  
 `NotOverridable` można użyć tylko w instrukcji deklaracji właściwości lub procedury. `NotOverridable` można określić tylko w przypadku właściwości lub procedury, która zastępuje inną właściwość lub procedurę, czyli tylko w połączeniu z `Overrides`.  
  
## <a name="combined-modifiers"></a>Połączone Modyfikatory  
 Nie można określić `Overridable` lub `NotOverridable` dla metody `Private`.  
  
 Nie można określić `NotOverridable` razem z `MustOverride`, `Overridable`lub `Shared` w tej samej deklaracji.  
  
## <a name="usage"></a>Sposób użycia  
 Modyfikator `NotOverridable` może być używany w tych kontekstach:  
  
 [Function, instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Property, instrukcja](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub, instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Zobacz także

- [Modyfikatory](../../../visual-basic/language-reference/modifiers/index.md)
- [Podstawowe informacje o dziedziczeniu](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)
- [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)
- [Słowa kluczowe](../../../visual-basic/language-reference/keywords/index.md)
- [Obserwowanie w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
