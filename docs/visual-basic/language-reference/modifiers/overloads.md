---
title: Przeciążenia
ms.date: 07/20/2015
f1_keywords:
- vb.Overloads
- Overloads
helpviewer_keywords:
- Overloads keyword [Visual Basic]
- hiding by signature
- Shadows keyword [Visual Basic]
- signature, hiding by
ms.assetid: 0c6820b8-25b2-4664-bc59-5ca93c99c042
ms.openlocfilehash: bd0931cab520f8580c0d7473a44e350752e287bb
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392109"
---
# <a name="overloads-visual-basic"></a>Overloads (Visual Basic)

Określa, że właściwość lub procedura ponownie deklaruje jedną lub więcej istniejących właściwości lub procedur o tej samej nazwie.

## <a name="remarks"></a>Uwagi

*Przeciążanie* jest sposobem dostarczenia więcej niż jednej definicji dla danej właściwości lub nazwy procedury w tym samym zakresie. Redeklaruj właściwość lub procedurę z innym podpisem jest czasami nazywana *ukrywaniem przez podpis*.

## <a name="rules"></a>Reguły

- **Kontekst deklaracji.** Można użyć `Overloads` tylko w instrukcji deklaracji właściwości lub procedury.

- **Połączone modyfikatory.** Nie można określić `Overloads` razem z [cieniami](shadows.md) w tej samej deklaracji procedury.

- **Wymagane różnice.** *Sygnatura* w tej deklaracji musi być różna od sygnatury każdej właściwości lub procedury, która została przeciążać. Podpis składa się z nazwy właściwości lub procedury wraz z następującymi:

  - liczba parametrów

  - kolejność parametrów

  - typy danych parametrów

  - liczba parametrów typu (dla procedury ogólnej)

  - zwracany typ (tylko dla procedury operatora konwersji)

  Wszystkie przeciążenia muszą mieć taką samą nazwę, ale każdy z nich musi się różnić od wszystkich innych w jednym lub więcej z powyższych kwestii. Dzięki temu kompilator może odróżnić, która wersja, która ma zostać użyta, gdy kod wywołuje właściwość lub procedurę.

- **Niedozwolone różnice.** Zmiana co najmniej jednego z następujących elementów nie jest prawidłowa w celu przeładowania właściwości lub procedury, ponieważ nie są one częścią podpisu:

  - Czy zwraca wartość (dla procedury)

  - Typ danych wartości zwracanej (z wyjątkiem operatora konwersji)

  - nazwy parametrów lub parametrów typu

  - ograniczenia dotyczące parametrów typu (dla procedury ogólnej)

  - Słowa kluczowe modyfikatora parametru (takie jak `ByRef` lub `Optional` )

  - Słowa kluczowe modyfikatora właściwości lub procedury (takie jak `Public` lub `Shared` )

- **Modyfikator opcjonalny.** Nie trzeba używać `Overloads` modyfikatora podczas definiowania wielu przeciążonych właściwości lub procedur w tej samej klasie. Jeśli jednak używasz `Overloads` w jednej z deklaracji, musisz użyć go we wszystkich z nich.

- **Obserwowanie i Przeciążenie.** `Overloads`może również służyć do cieniowania istniejącego elementu członkowskiego lub zestawu przeciążonych elementów członkowskich w klasie bazowej. Gdy używasz `Overloads` w ten sposób, deklarujesz właściwość lub metodę o tej samej nazwie i tej samej liście parametrów co element członkowski klasy bazowej i nie podasz `Shadows` słowa kluczowego.

W przypadku korzystania `Overrides` z programu kompilator niejawnie dodaje w `Overloads` taki sposób, aby interfejsy API biblioteki działały w łatwiejszy sposób.

`Overloads`Modyfikator może być używany w tych kontekstach:

- [Function, instrukcja](../statements/function-statement.md)

- [Operator — Instrukcja](../statements/operator-statement.md)

- [Property — Instrukcja](../statements/property-statement.md)

- [Sub, instrukcja](../statements/sub-statement.md)

## <a name="see-also"></a>Zobacz też

- [Shadows](shadows.md)
- [Przeciążanie procedury](../../programming-guide/language-features/procedures/procedure-overloading.md)
- [Typy ogólne w Visual Basic](../../programming-guide/language-features/data-types/generic-types.md)
- [Procedury operatorów](../../programming-guide/language-features/procedures/operator-procedures.md)
- [Instrukcje: definiowanie operatora konwersji](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
