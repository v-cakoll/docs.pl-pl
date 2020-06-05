---
title: Protected Friend
ms.date: 05/10/2018
helpviewer_keywords:
- Protected Friend keyword [Visual Basic]
- Protected Friend keyword [Visual Basic], syntax
ms.openlocfilehash: 202d4f4a3a05a64ab1d74621268f28f6b55e8952
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404839"
---
# <a name="protected-friend-visual-basic"></a>Chroniony znajomy (Visual Basic)

`Protected Friend`Kombinacja słowa kluczowego jest modyfikatorem dostępu składowej. Przyznaje zarówno dostęp [znajomy](friend.md) i [chroniony](protected.md) dostęp do elementów zadeklarowanych, więc są one dostępne z dowolnego miejsca w tym samym zestawie, z własnej klasy i z klas pochodnych. Można określić `Protected Friend` tylko dla elementów członkowskich klasy; nie można stosować `Protected Friend` do elementów członkowskich struktury, ponieważ struktury nie mogą być dziedziczone.

> [!NOTE]
> W programie Visual Studio wybierz pozycję Pomoc F1, aby uzyskać pomoc dotyczącą `protected friend` [ochrony](protected.md) lub [znajomych](friend.md). IDE wybiera pojedynczy token w obszarze kursora zamiast słowa złożonego.

## <a name="rules"></a>Reguły

**Kontekst deklaracji.** Można używać `Protected Friend` tylko na poziomie klasy. Oznacza to, że kontekst deklaracji dla `Protected` elementu musi być klasą i nie może być plikiem źródłowym, przestrzenią nazw, interfejsem, modułem, strukturą ani procedurą.

## <a name="see-also"></a>Zobacz też

- [Społeczeństwo](public.md)
- [Chronione](protected.md)
- [Osoby](friend.md)
- [Użytek](private.md)
- [Prywatne chronione](./private-protected.md)
- [Poziomy dostępu w Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md)
- [Procedury](../../programming-guide/language-features/procedures/index.md)
- [Struktury](../../programming-guide/language-features/data-types/structures.md)
- [Obiekty i klasy](../../programming-guide/language-features/objects-and-classes/index.md)
