---
title: Typy wartości — C# odwołanie
ms.date: 01/22/2020
f1_keywords:
- cs.valuetypes
helpviewer_keywords:
- value types [C#]
- types [C#], value types
- C# language, value types
ms.assetid: 471eb994-2958-49d5-a6be-19b4313f80a3
ms.openlocfilehash: 6b96d65f657f2af1af5c9a245e956640ee06260e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76748518"
---
# <a name="value-types-c-reference"></a>Typy wartości (C# odwołanie)

*Typy wartości* i [typy odwołań](../keywords/reference-types.md) to dwie główne kategorie C# typów. Zmienna typu wartości zawiera wystąpienie typu. Różni się to od zmiennej typu referencyjnego, która zawiera odwołanie do wystąpienia typu. Domyślnie podczas [przypisywania](../operators/assignment-operator.md), przekazywania argumentu do metody lub zwracając wynik metody, kopiowane są wartości zmiennych. W przypadku zmiennych typu wartość są kopiowane odpowiednie wystąpienia typu. Poniższy przykład ilustruje takie zachowanie:

[!code-csharp[copy of values](~/samples/csharp/language-reference/builtin-types/ValueTypes.cs#ValueTypeCopied)]

Jak pokazano w powyższym przykładzie, operacje na zmiennej typu wartości wpływają tylko na to wystąpienie typu wartości przechowywane w zmiennej.

Jeśli typ wartości zawiera element członkowski danych typu referencyjnego, podczas kopiowania wystąpienia typu wartości jest kopiowane tylko odwołanie do wystąpienia typu referencyjnego. Zarówno kopia, jak i oryginalne wystąpienie typu wartości mają dostęp do tego samego wystąpienia typu odwołania. Poniższy przykład ilustruje takie zachowanie:

[!code-csharp[shallow copy](~/samples/csharp/language-reference/builtin-types/ValueTypes.cs#ShallowCopy)]

> [!NOTE]
> Aby kod był mniej podatny na błędy i bardziej niezawodny, definiować i korzystać z niezmiennego typu wartości. W tym artykule są stosowane modyfikowalne typy wartości tylko w celach demonstracyjnych.

## <a name="kinds-of-value-types"></a>Rodzaje typów wartości

Typ wartości może być jednym z dwóch następujących rodzajów:

- [Typ struktury](../keywords/struct.md), który hermetyzuje dane i powiązane funkcje
- [Typ wyliczeniowy](enum.md), który jest zdefiniowany przez zestaw nazwanych stałych i reprezentuje wybór lub kombinację opcji

[Typ wartości null](nullable-value-types.md) `T?` reprezentuje wszystkie wartości jego bazowego typu wartości `T` i dodatkową wartość [null](../keywords/null.md) . Nie można przypisać `null` do zmiennej typu wartości, chyba że jest to typ wartości null.

## <a name="built-in-value-types"></a>Wbudowane typy wartości

C#Program udostępnia następujące wbudowane typy wartości, znane także jako *typy proste*:

- [Całkowite typy liczbowe](integral-numeric-types.md)
- [Zmiennoprzecinkowe typy liczbowe](floating-point-numeric-types.md)
- [bool](bool.md) reprezentujący wartość logiczną
- [char](char.md) , który reprezentuje znak Unicode UTF-16

Wszystkie typy proste są typami struktury i różnią się od innych typów struktury w tym, że dopuszczają pewne dodatkowe operacje:

- Można użyć literałów, aby podać wartość typu prostego. Na przykład `'A'` jest literałem typu `char`, a `2001` jest literałem typu `int`.

- Stałe typów prostych można zadeklarować za pomocą słowa kluczowego [const](../keywords/const.md) . Nie jest możliwe posiadanie stałych dla innych typów struktury.

- Wyrażenia stałe, których operandy to wszystkie stałe typów prostych, są oceniane w czasie kompilacji.

Począwszy od C# 7,0, C# obsługuje [krotki wartości](../../tuples.md). Krotka wartości jest typem wartości, ale nie typem prostym.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz następujące sekcje [ C# specyfikacji języka](~/_csharplang/spec/introduction.md):

- [Typy wartości](~/_csharplang/spec/types.md#value-types)
- [Typy proste](~/_csharplang/spec/types.md#simple-types)
- [Zmienne](~/_csharplang/spec/variables.md)

## <a name="see-also"></a>Zobacz także

- [C#odwoła](../index.md)
- <xref:System.ValueType?displayProperty=nameWithType>
- [Typy odwołań](../keywords/reference-types.md)
