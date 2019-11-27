---
title: Overrides
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
ms.openlocfilehash: 04f1cb27d6a8366c2dd13f8fdc1d975d382f1cfd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351386"
---
# <a name="overrides-visual-basic"></a>Overrides (Visual Basic)

Określa, że właściwość lub procedura przesłania właściwość lub procedurę, która jest dziedziczona z klasy bazowej.

## <a name="rules"></a>Reguły

- **Kontekst deklaracji.** `Overrides` można użyć tylko w instrukcji deklaracji właściwości lub procedury.

- **Połączone modyfikatory.** Nie można określić `Overrides` razem z `Shadows` lub `Shared` w tej samej deklaracji. Ponieważ przesłaniający element jest niejawnie możliwy do zastąpienia, nie można połączyć `Overridable` z `Overrides`.

- **Pasujące podpisy.** Podpis tej deklaracji musi być dokładnie zgodny z *podpisem* właściwości lub procedury, która zastąpi. Oznacza to, że listy parametrów muszą mieć taką samą liczbę parametrów, w tej samej kolejności, przy użyciu tych samych typów danych.

  Oprócz podpisu, deklaracja zastępująca musi być dokładnie zgodna z następującymi:

  - Poziom dostępu

  - Zwracany typ, jeśli istnieje

- **Podpisy ogólne.** W przypadku procedury ogólnej podpis obejmuje liczbę parametrów typu. W związku z tym, deklaracja zastępująca musi być zgodna z wersją klasy bazowej w tym zakresie.

- **Dodatkowe dopasowanie.** Oprócz dopasowania sygnatury wersji klasy bazowej, ta deklaracja musi również być zgodna z następującymi kwestiami:

  - Modyfikator poziomu dostępu (na przykład [publiczny](../../../visual-basic/language-reference/modifiers/public.md))

  - Mechanizm przekazywania każdego parametru ([ByVal](../../../visual-basic/language-reference/modifiers/byval.md) lub [ByRef](../../../visual-basic/language-reference/modifiers/byref.md))

  - Listy ograniczeń dla każdego parametru typu procedury ogólnej

- **Przesłanianie i zastępowanie.** Zarówno przesłanianie, jak i przesłonięcie przedefiniują Dziedziczony element, ale istnieją znaczne różnice między tymi dwoma podejściami. Aby uzyskać więcej informacji, zobacz [przesłanianie w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).

Jeśli używasz `Overrides`, kompilator niejawnie dodaje `Overloads` tak, aby interfejsy API biblioteki działały C# łatwiej.

Modyfikator `Overrides` może być używany w tych kontekstach:

- [Function, instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)

- [Property, instrukcja](../../../visual-basic/language-reference/statements/property-statement.md)

- [Sub, instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)

## <a name="see-also"></a>Zobacz także

- [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)
- [Słowa kluczowe](../../../visual-basic/language-reference/keywords/index.md)
- [Obserwowanie w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [Typy ogólne w Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Lista typów](../../../visual-basic/language-reference/statements/type-list.md)
