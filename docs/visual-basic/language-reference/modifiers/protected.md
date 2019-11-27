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
ms.openlocfilehash: 740c998b8a6ccc6798bce37e9b08e408dac7c17d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351302"
---
# <a name="protected-visual-basic"></a>Protected (Visual Basic)

Modyfikator dostępu składowej, który określa, że co najmniej jeden zadeklarowany element programistyczny jest dostępny tylko w obrębie swojej klasy lub z klasy pochodnej.

## <a name="remarks"></a>Uwagi

Czasami element programowania zadeklarowany w klasie zawiera dane poufne lub ograniczony kod i chcesz ograniczyć dostęp do elementu. Jeśli jednak Klasa jest dziedziczona i oczekiwana jest hierarchia klas pochodnych, może być konieczne, aby te klasy pochodne miały dostęp do danych lub kodu. W takim przypadku element ma być dostępny zarówno z klasy podstawowej, jak i ze wszystkich klas pochodnych. Aby ograniczyć dostęp do elementu w ten sposób, można zadeklarować go przy użyciu `Protected`.

> [!NOTE]
> Modyfikator dostępu `Protected` można łączyć z dwoma innymi modyfikatorami:
>
> - Modyfikator [Protected Friend](protected-friend.md) sprawia, że element członkowski klasy jest dostępny z tej klasy, z klas pochodnych i z tego samego zestawu, w którym jest zdefiniowana Klasa.
> - Modyfikator [Private Protected](private-protected.md) umożliwia członkom klasy dostęp do typów pochodnych, ale tylko w obrębie zawierającego go zestawu.

## <a name="rules"></a>Reguły

**Kontekst deklaracji.** `Protected` można używać tylko na poziomie klasy. Oznacza to, że kontekst deklaracji dla elementu `Protected` musi być klasą i nie może być plikiem źródłowym, przestrzenią nazw, interfejsem, strukturą ani procedurą.

## <a name="behavior"></a>Zachowanie

- **Poziom dostępu.** Cały kod w klasie ma dostęp do jego elementów. Kod w dowolnej klasie, która dziedziczy z klasy bazowej, może uzyskać dostęp do wszystkich `Protected` elementów klasy bazowej. Jest to prawdziwe dla wszystkich generacji wyprowadzania. Oznacza to, że Klasa może uzyskać dostęp do `Protected` elementów klasy podstawowej klasy podstawowej i tak dalej.

     Chroniony dostęp nie jest nadzbiorem lub podzbiorem przyjaznego dostępu.

- **Modyfikatory dostępu.** Słowa kluczowe określające poziom dostępu są nazywane *modyfikatorami dostępu*. Aby porównać Modyfikatory dostępu, zobacz [poziomy dostępu w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).

Modyfikator `Protected` może być używany w tych kontekstach:

- [Class, instrukcja](../../../visual-basic/language-reference/statements/class-statement.md)

- [Const, instrukcja](../../../visual-basic/language-reference/statements/const-statement.md)

- [Declare, instrukcja](../../../visual-basic/language-reference/statements/declare-statement.md)

- [Delegate, instrukcja](../../../visual-basic/language-reference/statements/delegate-statement.md)

- [Dim, instrukcja](../../../visual-basic/language-reference/statements/dim-statement.md)

- [Enum, instrukcja](../../../visual-basic/language-reference/statements/enum-statement.md)

- [Event, instrukcja](../../../visual-basic/language-reference/statements/event-statement.md)

- [Function, instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)

- [Interface, instrukcja](../../../visual-basic/language-reference/statements/interface-statement.md)

- [Property, instrukcja](../../../visual-basic/language-reference/statements/property-statement.md)

- [Structure, instrukcja](../../../visual-basic/language-reference/statements/structure-statement.md)

- [Sub, instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)

## <a name="see-also"></a>Zobacz także

- [Public](../../../visual-basic/language-reference/modifiers/public.md)
- [Friend](../../../visual-basic/language-reference/modifiers/friend.md)
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
- [Private Protected](private-protected.md)
- [Protected Friend](protected-friend.md)
- [Poziomy dostępu w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Procedury](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [Struktury](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Obiekty i klasy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
