---
title: Typy wartości null — C# Przewodnik programowania
ms.custom: seodec18
description: Dowiedz C# się więcej o typach wartości null i sposobach ich użycia
ms.date: 09/26/2019
helpviewer_keywords:
- nullable value types [C#]
ms.assetid: e473cb01-28ca-42be-9cea-f717055d72c6
ms.openlocfilehash: b8b52e7fb34adf65d5c76d59811ea6dd0ab16a98
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71396221"
---
# <a name="nullable-value-types-c-programming-guide"></a>Typy wartości null (C# Przewodnik programowania)

Typy wartości null są wystąpieniami struktury <xref:System.Nullable%601?displayProperty=nameWithType>. Typy wartości null mogą reprezentować wszystkie wartości typu podstawowego `T` i dodatkową wartość [null](../../language-reference/keywords/null.md) . Typ podstawowy `T` może być dowolnym [typem wartości](../../language-reference/keywords/value-types.md)innym niż null. `T` nie może być typem referencyjnym.

> [!NOTE]
> C#8,0 wprowadza funkcję typów odwołań do wartości null. Aby uzyskać więcej informacji, zobacz [typy referencyjne dopuszczające wartość null](../../nullable-references.md). Typy wartości null są dostępne od C# 2.

Na przykład można przypisać wartość `null` lub dowolną liczbę całkowitą z zakresu od <xref:System.Int32.MinValue?displayProperty=nameWithType> do <xref:System.Int32.MaxValue?displayProperty=nameWithType> do `Nullable<int>` i [true](../../language-reference/keywords/true-literal.md), [false](../../language-reference/keywords/false-literal.md)lub `null` do `Nullable<bool>`.

Typ wartości null jest używany w przypadku konieczności reprezentowania niezdefiniowanej wartości typu podstawowego. Zmienna logiczna może mieć tylko dwie wartości: `true` i `false`. Brak wartości "undefined". W wielu aplikacjach programistycznych, szczególnie w przypadku interakcji z bazami danych, wartość zmiennej może być niezdefiniowana lub brakująca. Na przykład pole w bazie danych może zawierać wartości true lub false lub nie może zawierać żadnej wartości. W takim przypadku należy użyć typu `Nullable<bool>`.

Typy wartości null mają następującą charakterystykę:

- Typy wartości null reprezentują zmienne typu wartości, do których można przypisać wartość `null`.

- Składnia `T?` jest skrótem dla `Nullable<T>`. Dwa formularze są zamienne.

- Przypisz wartość do typu wartości null tak samo jak dla bazowego typu wartości: `int? x = 10;` lub `double? d = 4.108;`. Można również przypisać wartość `null`: `int? x = null;`.

- Użyj właściwości typu <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> i <xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> do przetestowania wartości null i pobrania wartości, jak pokazano w następującym przykładzie: `if (x.HasValue) y = x.Value;`

  - Właściwość <xref:System.Nullable%601.HasValue%2A> zwraca `true`, jeśli zmienna zawiera wartość lub `false`, jeśli jest `null`.

  - Właściwość <xref:System.Nullable%601.Value%2A> zwraca wartość, jeśli <xref:System.Nullable%601.HasValue%2A> zwróci `true`. W przeciwnym razie zostanie zgłoszony <xref:System.InvalidOperationException>.

- Można również użyć operatorów `==` i `!=` z typem wartości null, jak pokazano w następującym przykładzie: `if (x != null) y = x.Value;`. Jeśli `a` i `b` są równe null, `a == b` szacuje się do `true`.

- Począwszy od C# 7,0, można użyć [dopasowania wzorca](../../pattern-matching.md#the-is-type-pattern-expression) do obu badań i pobrać wartość typu dopuszczającego wartości null: `if (x is int valueOfX) y = valueOfX;`.

- Wartość domyślna `T?` to wystąpienie, którego właściwość <xref:System.Nullable%601.HasValue%2A> zwraca `false`.

- Użyj metody <xref:System.Nullable%601.GetValueOrDefault> do zwrócenia przypisanej wartości lub wartości [domyślnej](../../language-reference/keywords/default-values-table.md) bazowego typu wartości, jeśli wartość tego typu jest `null`.

- Użyj metody <xref:System.Nullable%601.GetValueOrDefault(%600)> do zwrócenia przypisanej wartości lub podanej wartości domyślnej, jeśli wartość tego typu jest `null`.

- Użyj [operatora łączenia wartości null](../../language-reference/operators/null-coalescing-operator.md), `??`, aby przypisać wartość do zmiennej bazowego typu wartości na podstawie wartości typu nullable: `int? x = null; int y = x ?? -1;`. W przykładzie, ponieważ `x` jest `null`, wartość wyniku `y` jest `-1`.

- Jeśli zdefiniowana przez użytkownika konwersja jest zdefiniowana między dwoma typami wartości, można także użyć tej samej konwersji z odpowiadającymi im typami dopuszczającymi wartość null.

- Zagnieżdżone typy wartości null są niedozwolone. Następujący wiersz nie kompiluje się: `Nullable<Nullable<int>> n;`

Aby uzyskać więcej informacji, zobacz [Korzystanie z typów wartości null](using-nullable-types.md) i [instrukcje: Identyfikowanie tematów o typie wartości null](how-to-identify-a-nullable-type.md) .

## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [?? operator](../../language-reference/operators/null-coalescing-operator.md)
- [Typy wartości null (Visual Basic)](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- <xref:System.Nullable%601?displayProperty=nameWithType>
- <xref:System.Nullable?displayProperty=nameWithType>
