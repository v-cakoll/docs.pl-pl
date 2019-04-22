---
title: Implements — Klauzula (Visual Basic)
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
ms.openlocfilehash: 05de1d9f8966c17d84deba34f27819cce4aff3fe
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58832622"
---
# <a name="implements-clause-visual-basic"></a>Implements — Klauzula (Visual Basic)
Wskazuje, że składowa klasy lub struktury dostarcza implementację dla składowej zdefiniowanej w interfejsie.  
  
## <a name="remarks"></a>Uwagi  
`Implements` — Słowo kluczowe nie jest taka sama jak [Implements — instrukcja](../../../visual-basic/language-reference/statements/implements-statement.md). Możesz użyć `Implements` instrukcję, aby określić, że klasa lub struktura implementuje jeden lub więcej interfejsów, a następnie dla każdego elementu członkowskiego przy użyciu `Implements` — słowo kluczowe, aby określić, które interfejsu i członka, który implementuje.

Jeśli klasa lub struktura implementuje interfejs, musi on zawierać `Implements` instrukcji natychmiast po [Class — instrukcja](../../../visual-basic/language-reference/statements/class-statement.md) lub [Structure — instrukcja](../../../visual-basic/language-reference/statements/structure-statement.md), i musi on implementować wszystkie elementy członkowskie zdefiniowane przez interfejs.

## <a name="reimplementation"></a>Reimplementation  
W klasie pochodnej można ponownie składowej interfejsu, która klasa bazowa została już zaimplementowana. To różni się od przesłanianie składowej klasy bazowej pod następującymi względami:

- Składowej klasy bazowej nie musi być [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) do być reimplemented.
- Można ponownie element członkowski o innej nazwie.

`Implements` — Słowo kluczowe może służyć w następujących okolicznościach:
- [Event, instrukcja](../../../visual-basic/language-reference/statements/event-statement.md)
- [Function, instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)
- [Instrukcja Property](../../../visual-basic/language-reference/statements/property-statement.md)
- [Sub, instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Zobacz także

- [Implements, instrukcja](../../../visual-basic/language-reference/statements/implements-statement.md)
- [Instrukcja Interface](../../../visual-basic/language-reference/statements/interface-statement.md)
- [Class, instrukcja](../../../visual-basic/language-reference/statements/class-statement.md)
- [Structure, instrukcja](../../../visual-basic/language-reference/statements/structure-statement.md)
