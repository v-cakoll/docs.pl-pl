---
title: Chronione Friend (Visual Basic)
ms.date: 05/10/2018
helpviewer_keywords:
- Protected Friend keyword [Visual Basic]
- Protected Friend keyword [Visual Basic], syntax
ms.openlocfilehash: b72cbee0394043620e792d1c014bfe55121e175e
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/18/2018
---
# <a name="protected-friend-visual-basic"></a>Chronione Friend (Visual Basic)

`Protected Friend` Kombinacja słów kluczowych jest modyfikator dostępu elementu członkowskiego. Wiąże się zarówno [Friend](friend.md) dostępu i [chronione](protected.md) dostępu na zadeklarowane elementy, dzięki czemu są one dostępne z dowolnej lokalizacji w tym samym zestawie, swojej klasy oraz klas pochodnych. Można określić `Protected Friend` tylko w elementach członkowskich klas; nie można zastosować `Protected Friend` do elementów członkowskich struktury ponieważ struktur nie może być dziedziczona.

> [!NOTE]
> W programie Visual Studio, wybierając pomocy F1 w `protected friend` zawiera informacje pomocne w obu [chronione](protected.md) lub [friend](friend.md). IDE wybiera jeden token pod kursorem zamiast wyraz złożony.

## <a name="rules"></a>Reguły

- **Kontekst deklaracji.** Można użyć `Protected Friend` tylko na poziomie klasy. Oznacza to, że w kontekście deklaracji `Protected` elementu musi być klasą i nie może być plik źródłowy, przestrzeni nazw, interfejsu, modułu, struktury lub procedury. 


## <a name="see-also"></a>Zobacz też

[Public](../../../visual-basic/language-reference/modifiers/public.md)  
[Protected](../../../visual-basic/language-reference/modifiers/protected.md)  
[Friend](friend.md)   
[Private](../../../visual-basic/language-reference/modifiers/private.md)  
[Prywatne chronione](./private-protected.md)   
[Poziomy dostępu w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
[Procedury](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
[Struktury](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
[Obiekty i klasy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
