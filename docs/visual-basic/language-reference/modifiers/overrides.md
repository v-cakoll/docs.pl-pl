---
title: Przesłonięcia
ms.date: 07/20/2015
f1_keywords:
- Overrides
- vb.Overrides
helpviewer_keywords:
- properties [Visual Basic], redefining
- procedures [Visual Basic], overriding
- procedures [Visual Basic], redefining
- overriding
- Overrides keyword [Visual Basic]
- overriding, Overrides keyword
- properties [Visual Basic], overriding
ms.assetid: 9f5e6144-ce10-465e-842b-1a8f8760af90
ms.openlocfilehash: 657f838b2959a5b6a7cef5ff18295a4ada709e9a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392031"
---
# <a name="overrides-visual-basic"></a>Overrides (Visual Basic)

Określa, że właściwość lub procedura przesłania właściwość lub procedurę, która jest dziedziczona z klasy bazowej.

## <a name="rules"></a>Reguły

- **Kontekst deklaracji.** Można użyć `Overrides` tylko w instrukcji deklaracji właściwości lub procedury.

- **Połączone modyfikatory.** Nie można określić `Overrides` razem z `Shadows` lub `Shared` w tej samej deklaracji. Ponieważ przesłaniający element jest niejawnie możliwy do zastąpienia, nie można połączyć `Overridable` się z `Overrides` .

- **Pasujące podpisy.** Podpis tej deklaracji musi być dokładnie zgodny z *podpisem* właściwości lub procedury, która zastąpi. Oznacza to, że listy parametrów muszą mieć taką samą liczbę parametrów, w tej samej kolejności, przy użyciu tych samych typów danych.

  Oprócz podpisu, deklaracja zastępująca musi być dokładnie zgodna z następującymi:

  - Poziom dostępu

  - Zwracany typ, jeśli istnieje

- **Podpisy ogólne.** W przypadku procedury ogólnej podpis obejmuje liczbę parametrów typu. W związku z tym, deklaracja zastępująca musi być zgodna z wersją klasy bazowej w tym zakresie.

- **Dodatkowe dopasowanie.** Oprócz dopasowania sygnatury wersji klasy bazowej, ta deklaracja musi również być zgodna z następującymi kwestiami:

  - Modyfikator poziomu dostępu (na przykład [publiczny](public.md))

  - Mechanizm przekazywania każdego parametru ([ByVal](byval.md) lub [ByRef](byref.md))

  - Listy ograniczeń dla każdego parametru typu procedury ogólnej

- **Przesłanianie i zastępowanie.** Zarówno przesłanianie, jak i przesłonięcie przedefiniują Dziedziczony element, ale istnieją znaczne różnice między tymi dwoma podejściami. Aby uzyskać więcej informacji, zobacz [przesłanianie w Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md).

W przypadku korzystania `Overrides` z programu kompilator niejawnie dodaje w `Overloads` taki sposób, aby interfejsy API biblioteki działały w łatwiejszy sposób.

`Overrides`Modyfikator może być używany w tych kontekstach:

- [Function, instrukcja](../statements/function-statement.md)

- [Property — Instrukcja](../statements/property-statement.md)

- [Sub, instrukcja](../statements/sub-statement.md)

## <a name="see-also"></a>Zobacz też

- [MustOverride](mustoverride.md)
- [NotOverridable](notoverridable.md)
- [Overridable](overridable.md)
- [Słowa kluczowe](../keywords/index.md)
- [Przesłanianie w Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md)
- [Typy ogólne w Visual Basic](../../programming-guide/language-features/data-types/generic-types.md)
- [Lista typów](../statements/type-list.md)
