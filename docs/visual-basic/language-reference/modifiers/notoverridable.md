---
title: NotOverridable (Visual Basic)
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
ms.openlocfilehash: 41c08a48fdb7501081e887fb5cf9f99c334c72ac
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58822318"
---
# <a name="notoverridable-visual-basic"></a>NotOverridable (Visual Basic)
Określa, że właściwość lub procedura nie może być przesłoniona w klasie pochodnej.  
  
## <a name="remarks"></a>Uwagi  
 `NotOverridable` Modyfikator zapobiega zastępowaniu w klasie pochodnej właściwości lub metody.  [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) modyfikator umożliwia właściwość lub metoda klasy został nadpisany w klasie pochodnej. Aby uzyskać więcej informacji, zobacz [podstawowe informacje o dziedziczeniu](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).  
  
 Jeśli `Overridable` lub `NotOverridable` modyfikator nie zostanie określony, domyślnie zależy od tego, czy właściwość lub metoda zastępuje właściwości klasy bazowej lub metody. Jeśli właściwość lub metoda zastępuje właściwości klasy bazowej lub metody, domyślne ustawienie to `Overridable`; w przeciwnym razie jest `NotOverridable`.  
  
 Element, który nie może być zastąpiona jest czasami nazywane *zapieczętowanego* elementu.  
  
 Możesz użyć `NotOverridable` tylko w instrukcji deklaracji właściwość lub procedura. Można określić `NotOverridable` tylko na właściwość lub procedura, która zastępuje inną właściwość lub procedura, oznacza to, że tylko w połączeniu z `Overrides`.  
  
## <a name="combined-modifiers"></a>Modyfikatory połączone  
 Nie można określić `Overridable` lub `NotOverridable` dla `Private` metody.  
  
 Nie można określić `NotOverridable` wraz z `MustOverride`, `Overridable`, lub `Shared` w tej samej deklaracji.  
  
## <a name="usage"></a>Użycie  
 `NotOverridable` Modyfikator mogą być używane w tych kontekstach:  
  
 [Function, instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Instrukcja Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub, instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Zobacz także

- [Modyfikatory](../../../visual-basic/language-reference/modifiers/index.md)
- [Podstawowe informacje o dziedziczeniu](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)
- [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)
- [Słowa kluczowe](../../../visual-basic/language-reference/keywords/index.md)
- [Przesłanianie w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
