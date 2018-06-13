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
ms.openlocfilehash: 3fae1a4b587c379dbc459cbc973982851e713785
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33600756"
---
# <a name="notoverridable-visual-basic"></a>NotOverridable (Visual Basic)
Określa, że właściwość lub procedura nie można zastąpić w klasie pochodnej.  
  
## <a name="remarks"></a>Uwagi  
 `NotOverridable` Modyfikator zapobiega zastępowaniu w klasie pochodnej właściwości lub metody.  [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) modyfikator umożliwia właściwości lub metody w klasie do zastąpienia w klasie pochodnej. Aby uzyskać więcej informacji, zobacz [podstawowe informacje o dziedziczeniu](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).  
  
 Jeśli `Overridable` lub `NotOverridable` modyfikator nie zostanie określony, domyślnie zależy od tego, czy właściwości lub metody zastępuje właściwości klasy podstawowej lub metody. Jeśli właściwość lub metoda zastępuje właściwości klasy podstawowej lub metody, ustawienie domyślne to `Overridable`; w przeciwnym razie jest `NotOverridable`.  
  
 Nie można zastąpić element jest czasami nazywany *zapieczętowanego* elementu.  
  
 Można użyć `NotOverridable` tylko w instrukcji deklaracji właściwość lub procedura. Można określić `NotOverridable` tylko na właściwość lub procedura, która zastępuje inną właściwość lub procedura, oznacza to, że tylko w połączeniu z `Overrides`.  
  
## <a name="combined-modifiers"></a>Modyfikatory połączone  
 Nie można określić `Overridable` lub `NotOverridable` dla `Private` metody.  
  
 Nie można określić `NotOverridable` razem z `MustOverride`, `Overridable`, lub `Shared` w tej samej deklaracji.  
  
## <a name="usage"></a>Użycie  
 `NotOverridable` Modyfikatora można używać w tych sytuacjach:  
  
 [Function, instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Property, instrukcja](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub, instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Modyfikatory](../../../visual-basic/language-reference/modifiers/index.md)  
 [Podstawowe informacje o dziedziczeniu](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
 [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)  
 [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)  
 [Słowa kluczowe](../../../visual-basic/language-reference/keywords/index.md)  
 [Przesłanianie w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
