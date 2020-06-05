---
title: Protected
ms.date: 07/20/2015
f1_keywords:
- vb.Protected
helpviewer_keywords:
- Protected Friend keyword combination
- Protected keyword [Visual Basic], and Friend
- Protected keyword [Visual Basic], syntax
- Protected access modifier
- Protected keyword [Visual Basic]
ms.assetid: 74ad3d56-309f-49d2-b60c-1d0157d010e8
ms.openlocfilehash: d66ed68004f8b6ef21ae703f02b317589814764b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398223"
---
# <a name="protected-visual-basic"></a>Protected (Visual Basic)

Modyfikator dostępu składowej, który określa, że co najmniej jeden zadeklarowany element programistyczny jest dostępny tylko w obrębie swojej klasy lub z klasy pochodnej.

## <a name="remarks"></a>Uwagi

Czasami element programowania zadeklarowany w klasie zawiera dane poufne lub ograniczony kod i chcesz ograniczyć dostęp do elementu. Jeśli jednak Klasa jest dziedziczona i oczekiwana jest hierarchia klas pochodnych, może być konieczne, aby te klasy pochodne miały dostęp do danych lub kodu. W takim przypadku element ma być dostępny zarówno z klasy podstawowej, jak i ze wszystkich klas pochodnych. Aby ograniczyć dostęp do elementu w ten sposób, można go zadeklarować za pomocą `Protected` .

> [!NOTE]
> `Protected`Modyfikator dostępu można łączyć z dwoma innymi modyfikatorami:
>
> - Modyfikator [Protected Friend](protected-friend.md) sprawia, że element członkowski klasy jest dostępny z tej klasy, z klas pochodnych i z tego samego zestawu, w którym jest zdefiniowana Klasa.
> - Modyfikator [Private Protected](private-protected.md) umożliwia członkom klasy dostęp do typów pochodnych, ale tylko w obrębie zawierającego go zestawu.

## <a name="rules"></a>Reguły

**Kontekst deklaracji.** Można używać `Protected` tylko na poziomie klasy. Oznacza to, że kontekst deklaracji dla `Protected` elementu musi być klasą i nie może być plikiem źródłowym, przestrzenią nazw, interfejsem, modułem, strukturą ani procedurą.

## <a name="behavior"></a>Zachowanie

- **Poziom dostępu.** Cały kod w klasie ma dostęp do jego elementów. Kod w dowolnej klasie, która dziedziczy z klasy bazowej, może uzyskać dostęp do wszystkich `Protected` elementów klasy podstawowej. Jest to prawdziwe dla wszystkich generacji wyprowadzania. Oznacza to, że Klasa może uzyskać dostęp do `Protected` elementów klasy podstawowej klasy podstawowej i tak dalej.

     Chroniony dostęp nie jest nadzbiorem lub podzbiorem przyjaznego dostępu.

- **Modyfikatory dostępu.** Słowa kluczowe określające poziom dostępu są nazywane *modyfikatorami dostępu*. Aby porównać Modyfikatory dostępu, zobacz [poziomy dostępu w Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).

`Protected`Modyfikator może być używany w tych kontekstach:

- [Class, instrukcja](../statements/class-statement.md)

- [Const, instrukcja](../statements/const-statement.md)

- [Declare — Instrukcja](../statements/declare-statement.md)

- [Delegate — Instrukcja](../statements/delegate-statement.md)

- [Dim, instrukcja](../statements/dim-statement.md)

- [Enum, instrukcja](../statements/enum-statement.md)

- [Event — Instrukcja](../statements/event-statement.md)

- [Function, instrukcja](../statements/function-statement.md)

- [Interface, instrukcja](../statements/interface-statement.md)

- [Property — Instrukcja](../statements/property-statement.md)

- [Structure — Instrukcja](../statements/structure-statement.md)

- [Sub, instrukcja](../statements/sub-statement.md)

## <a name="see-also"></a>Zobacz też

- [Społeczeństwo](public.md)
- [Osoby](friend.md)
- [Użytek](private.md)
- [Prywatne chronione](private-protected.md)
- [Protected Friend](protected-friend.md)
- [Poziomy dostępu w Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md)
- [Procedury](../../programming-guide/language-features/procedures/index.md)
- [Struktury](../../programming-guide/language-features/data-types/structures.md)
- [Obiekty i klasy](../../programming-guide/language-features/objects-and-classes/index.md)
