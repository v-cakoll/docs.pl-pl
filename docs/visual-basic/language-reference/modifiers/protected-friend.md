---
title: Protected Friend
ms.date: 05/10/2018
helpviewer_keywords:
- Protected Friend keyword [Visual Basic]
- Protected Friend keyword [Visual Basic], syntax
ms.openlocfilehash: f92021f5f0dab9762470c270bdd5182187d587e5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351319"
---
# <a name="protected-friend-visual-basic"></a>Chroniony znajomy (Visual Basic)

Kombinacja słowa kluczowego `Protected Friend` jest modyfikatorem dostępu składowej. Przyznaje zarówno dostęp [znajomy](friend.md) i [chroniony](protected.md) dostęp do elementów zadeklarowanych, więc są one dostępne z dowolnego miejsca w tym samym zestawie, z własnej klasy i z klas pochodnych. Można określić `Protected Friend` tylko dla elementów członkowskich klasy; nie można zastosować `Protected Friend` do elementów członkowskich struktury, ponieważ struktury nie mogą być dziedziczone.

> [!NOTE]
> W programie Visual Studio wybierz pozycję Pomoc F1 na `protected friend` zapewnia pomoc dla [ochrony](protected.md) lub [znajomych](friend.md). IDE wybiera pojedynczy token w obszarze kursora zamiast słowa złożonego.

## <a name="rules"></a>Reguły

**Kontekst deklaracji.** `Protected Friend` można używać tylko na poziomie klasy. Oznacza to, że kontekst deklaracji dla elementu `Protected` musi być klasą i nie może być plikiem źródłowym, przestrzenią nazw, interfejsem, strukturą ani procedurą.

## <a name="see-also"></a>Zobacz także

- [Public](../../../visual-basic/language-reference/modifiers/public.md)
- [Protected](../../../visual-basic/language-reference/modifiers/protected.md)
- [Friend](friend.md)
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
- [Private Protected](./private-protected.md)
- [Poziomy dostępu w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Procedury](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [Struktury](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Obiekty i klasy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
