---
title: Typy wartości — odwołanie do języka C#
ms.date: 01/22/2020
f1_keywords:
- cs.valuetypes
helpviewer_keywords:
- value types [C#]
- types [C#], value types
- C# language, value types
ms.assetid: 471eb994-2958-49d5-a6be-19b4313f80a3
ms.openlocfilehash: 406e5b8bbe0802146a65bb4b9a053e753a7827ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399582"
---
# <a name="value-types-c-reference"></a>Typy wartości (odwołanie do języka C#)

*Typy wartości* i [typy odwołań](../keywords/reference-types.md) są dwiegłówne kategorie typów C#. Zmienna typu wartości zawiera wystąpienie typu. Różni się od zmiennej typu odwołania, która zawiera odwołanie do wystąpienia typu. Domyślnie w przypadku [przypisania](../operators/assignment-operator.md), przekazywania argumentu do metody i zwracania wyniku metody są kopiowane wartości zmiennych. W przypadku zmiennych typu wartości są kopiowane odpowiednie wystąpienia typu. W poniższym przykładzie przedstawiono to zachowanie:

[!code-csharp[copy of values](snippets/ValueTypes.cs#ValueTypeCopied)]

Jak pokazano w poprzednim przykładzie, operacje na zmiennej typu wartości wpływają tylko na to wystąpienie typu wartości, przechowywane w zmiennej.

Jeśli typ wartości zawiera element członkowski danych typu odwołania, tylko odwołanie do wystąpienia typu odwołania jest kopiowane podczas kopiowania wystąpienia typu wartości. Zarówno kopia, jak i oryginalne wystąpienie typu wartości mają dostęp do tego samego wystąpienia typu odwołania. W poniższym przykładzie przedstawiono to zachowanie:

[!code-csharp[shallow copy](snippets/ValueTypes.cs#ShallowCopy)]

> [!NOTE]
> Aby kod był mniej podatny na błędy i bardziej niezawodny, należy zdefiniować i użyć niezmiennych typów wartości. W tym artykule użyto typów wartości zapisywalnych tylko do celów demonstracyjnych.

## <a name="kinds-of-value-types"></a>Rodzaje typów wartości

Typ wartości może być jednym z dwóch następujących rodzajów:

- [typ konstrukcji,](struct.md)który hermetyzuje dane i powiązane funkcje
- [typ wyliczenia](enum.md), który jest definiowany przez zestaw nazwanych stałych i reprezentuje wybór lub kombinację wyborów

[Typ](nullable-value-types.md) `T?` wartości nullable reprezentuje wszystkie wartości jego `T` podstawowego typu wartości i dodatkowej wartości [null.](../keywords/null.md) Nie można `null` przypisać do zmiennej typu wartości, chyba że jest to typ wartości z wartością null.

## <a name="built-in-value-types"></a>Wbudowane typy wartości

C# zawiera następujące wbudowane typy wartości, znane również jako *typy proste:*

- [Typy liczb całkowitych](integral-numeric-types.md)
- [Zmiennoprzecinkowe rodzaje wartości numerycznych](floating-point-numeric-types.md)
- [bool](bool.md) reprezentujący wartość logiczną
- [char,](char.md) który reprezentuje znak Unicode UTF-16

Wszystkie typy proste są typy struktury i różnią się od innych typów struktury, ponieważ pozwalają one na pewne dodatkowe operacje:

- Można użyć literału, aby zapewnić wartość typu prostego. Na przykład `'A'` jest literałem `char` `2001` typu i jest `int`literałem typu .

- Za pomocą słowa kluczowego [const](../keywords/const.md) można deklarować stałe typów prostych. Nie jest możliwe, aby mieć stałe innych typów struktury.

- Wyrażenia stałe, których argumenty są wszystkie stałe typów prostych, są oceniane w czasie kompilacji.

Począwszy od języka C# 7.0, C# obsługuje [krotek wartości](../../tuples.md). Krotka wartości jest typem wartości, ale nie jest typem prostym.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz następujące sekcje [specyfikacji języka Języka C#:](~/_csharplang/spec/introduction.md)

- [Typy wartości](~/_csharplang/spec/types.md#value-types)
- [Typy proste](~/_csharplang/spec/types.md#simple-types)
- [Zmienne](~/_csharplang/spec/variables.md)

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)
- <xref:System.ValueType?displayProperty=nameWithType>
- [Typy odwołań](../keywords/reference-types.md)
