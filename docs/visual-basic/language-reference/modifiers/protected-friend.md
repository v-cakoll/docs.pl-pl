---
title: Chronione Friend (Visual Basic)
ms.date: 05/10/2018
helpviewer_keywords:
- Protected Friend keyword [Visual Basic]
- Protected Friend keyword [Visual Basic], syntax
ms.openlocfilehash: 1858411e5543448e6d822c97b6e5c18da4a6c11e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54639604"
---
# <a name="protected-friend-visual-basic"></a>Chronione Friend (Visual Basic)

`Protected Friend` Kombinacja słów kluczowych jest modyfikator dostępu składowej. Wiąże się zarówno [Friend](friend.md) dostępu i [chronione](protected.md) dostęp do elementów zadeklarowanych, dzięki czemu są one dostępne z dowolnego miejsca na tym samym zestawie, z własnych klas i klasach pochodnych. Można określić `Protected Friend` tylko na składowych klas; nie można zastosować `Protected Friend` do elementów członkowskich struktury ponieważ struktury nie może być dziedziczona.

> [!NOTE]
> W programie Visual Studio, wybierając opcję pomocy F1 na `protected friend` zapewnia pomoc dla dowolnego [chronione](protected.md) lub [friend](friend.md). Środowisko IDE wybiera jednego tokenu pod kursorem, a nie jako wyraz złożony.

## <a name="rules"></a>reguły

- **Kontekst deklaracji.** Możesz użyć `Protected Friend` tylko na poziomie klasy. Oznacza to, że kontekst deklaracji `Protected` element musi być klasą i nie może być plik źródłowy, przestrzeń nazw, interfejsu, moduł, struktura lub procedury. 


## <a name="see-also"></a>Zobacz także

- [Public](../../../visual-basic/language-reference/modifiers/public.md)
- [Protected](../../../visual-basic/language-reference/modifiers/protected.md)
- [Friend](friend.md)
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
- [Private Protected](./private-protected.md)
- [Poziomy dostępu w języku Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Procedury](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [Struktury](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Obiekty i klasy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
