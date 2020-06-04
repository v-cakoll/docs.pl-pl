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
ms.openlocfilehash: 46ab1a1148e8d73d91293aedfc407e5efdc7cfb4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404566"
---
# <a name="implements-clause-visual-basic"></a>Implements — Klauzula (Visual Basic)
Wskazuje, że składowa klasy lub struktury dostarcza implementację dla składowej zdefiniowanej w interfejsie.  
  
## <a name="remarks"></a>Uwagi  
`Implements`Słowo kluczowe nie jest takie samo jak [instrukcja Implements](implements-statement.md). Możesz użyć `Implements` instrukcji, aby określić, że Klasa lub struktura implementuje jeden lub więcej interfejsów, a następnie dla każdego elementu członkowskiego używa `Implements` słowa kluczowego, aby określić, który interfejs i który element członkowski implementuje.

Jeśli klasa lub struktura implementuje interfejs, musi zawierać `Implements` instrukcję bezpośrednio po [instrukcji klasy](class-statement.md) lub [instrukcji struktury](structure-statement.md)i musi zaimplementować wszystkie elementy członkowskie zdefiniowane przez interfejs.

## <a name="reimplementation"></a>Reimplementacja  
W klasie pochodnej można wykonać ponowną implementację elementu członkowskiego interfejsu, który został już zaimplementowany przez klasę bazową. Różni się to od przesłaniania składowej klasy bazowej w następujących aspektach:

- Składowa klasy bazowej nie musi być zaimplementowana [, aby](../modifiers/overridable.md) można ją było ponownie zaimplementować.
- Można wykonać ponowną implementację elementu członkowskiego z inną nazwą.

`Implements`Słowo kluczowe może być używane w następujących kontekstach:

- [Event — Instrukcja](event-statement.md)
- [Function, instrukcja](function-statement.md)
- [Property — Instrukcja](property-statement.md)
- [Sub, instrukcja](sub-statement.md)  
  
## <a name="see-also"></a>Zobacz też

- [Implements — Instrukcja](implements-statement.md)
- [Interface, instrukcja](interface-statement.md)
- [Class, instrukcja](class-statement.md)
- [Structure — Instrukcja](structure-statement.md)
