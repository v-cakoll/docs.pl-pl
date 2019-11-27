---
title: Implements, klauzula
ms.date: 07/20/2015
f1_keywords:
- vb.ImplementsClause
helpviewer_keywords:
- interface implementation [Visual Basic], reimplementation
- interface members [Visual Basic], reimplementation
- interface members [Visual Basic], Implements keyword
- interface members
- members [Visual Basic], reimplementation
- interface implementation [Visual Basic], Implements keyword
- interface members [Visual Basic], implementing
- Implements keyword [Visual Basic]
- Implements statement [Visual Basic], about Implements
- members [Visual Basic], implementing
- members [Visual Basic], Implements keyword
- reimplementation
ms.assetid: 5252cdf9-964d-4fc6-af0f-0449b7126b5a
ms.openlocfilehash: f114aee75356e59eafd9d3ba6af9c64402cb374f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345872"
---
# <a name="implements-clause-visual-basic"></a>Implements — Klauzula (Visual Basic)
Wskazuje, że składowa klasy lub struktury dostarcza implementację dla składowej zdefiniowanej w interfejsie.  
  
## <a name="remarks"></a>Uwagi  
Słowo kluczowe `Implements` nie jest takie samo jak [instrukcja Implements](../../../visual-basic/language-reference/statements/implements-statement.md). Użyj instrukcji `Implements`, aby określić, że Klasa lub struktura implementuje jeden lub więcej interfejsów, a następnie dla każdego elementu członkowskiego Użyj słowa kluczowego `Implements`, aby określić, który interfejs i który element członkowski implementuje.

Jeśli klasa lub struktura implementuje interfejs, musi on zawierać instrukcję `Implements` bezpośrednio po [instrukcji Class](../../../visual-basic/language-reference/statements/class-statement.md) lub [instrukcji Structure](../../../visual-basic/language-reference/statements/structure-statement.md)i musi implementować wszystkie elementy członkowskie zdefiniowane przez interfejs.

## <a name="reimplementation"></a>Reimplementacja  
W klasie pochodnej można wykonać ponowną implementację elementu członkowskiego interfejsu, który został już zaimplementowany przez klasę bazową. Różni się to od przesłaniania składowej klasy bazowej w następujących aspektach:

- Składowa klasy bazowej nie musi być zaimplementowana [, aby](../../../visual-basic/language-reference/modifiers/overridable.md) można ją było ponownie zaimplementować.
- Można wykonać ponowną implementację elementu członkowskiego z inną nazwą.

Słowo kluczowe `Implements` może być używane w następujących kontekstach:

- [Event, instrukcja](../../../visual-basic/language-reference/statements/event-statement.md)
- [Function, instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)
- [Property, instrukcja](../../../visual-basic/language-reference/statements/property-statement.md)
- [Sub, instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Zobacz także

- [Implements, instrukcja](../../../visual-basic/language-reference/statements/implements-statement.md)
- [Interface, instrukcja](../../../visual-basic/language-reference/statements/interface-statement.md)
- [Class, instrukcja](../../../visual-basic/language-reference/statements/class-statement.md)
- [Structure, instrukcja](../../../visual-basic/language-reference/statements/structure-statement.md)
