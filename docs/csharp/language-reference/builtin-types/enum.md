---
title: Typy wyliczeniowe — C# odwołanie
description: Dowiedz C# się więcej na temat typów wyliczeniowych, które reprezentują wybór lub kombinację opcji
ms.date: 12/13/2019
f1_keywords:
- enum
- enum_CSharpKeyword
helpviewer_keywords:
- enum keyword [C#]
- enum type [C#]
- enumeration type [C#]
- bit flags [C#]
ms.assetid: bbeb9a0f-e9b3-41ab-b0a6-c41b1a08974c
ms.openlocfilehash: ac4dafef92bbc900d291a5b653c55ba295f1a6d6
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2020
ms.locfileid: "77093230"
---
# <a name="enumeration-types-c-reference"></a>Typy wyliczeniowe (C# odwołanie)

*Typ wyliczenia* (lub *Typ wyliczeniowy*) jest [typem wartości](value-types.md) zdefiniowanym przez zestaw nazwanych stałych podstawowego typu [liczbowego](integral-numeric-types.md) . Aby zdefiniować typ wyliczeniowy, użyj słowa kluczowego `enum` i określ nazwy *elementów członkowskich wyliczenia*:

```csharp
enum Season
{
    Spring,
    Summer,
    Autumn,
    Winter
}
```

Domyślnie skojarzone wartości stałe elementów członkowskich wyliczenia są przypisane do typu `int`; zaczynają się od zera i zwiększają się o jeden po kolejności tekstu definicji. Można jawnie określić dowolny inny typ [liczbowy całkowity](integral-numeric-types.md) jako typ podstawowy typu wyliczenia. Można również jawnie określić skojarzone wartości stałe, jak pokazano na poniższym przykładzie:

```csharp
enum ErrorCode : ushort
{
    None = 0,
    Unknown = 1,
    ConnectionLost = 100,
    OutlierReading = 200
}
```

Nie można zdefiniować metody wewnątrz definicji typu wyliczenia. Aby dodać funkcjonalność do typu wyliczenia, Utwórz [metodę rozszerzenia](../../programming-guide/classes-and-structs/extension-methods.md).

Wartość domyślna typu wyliczeniowego `E` jest wartością wygenerowaną przez wyrażenie `(E)0`, nawet jeśli zero nie ma odpowiedniego elementu członkowskiego wyliczenia.

Typ wyliczenia służy do reprezentowania wyboru z zestawu wzajemnie wykluczających się wartości lub kombinacji wyboru. Aby przedstawić kombinację opcji, zdefiniuj typ wyliczenia jako flagi bitowe.

## <a name="enumeration-types-as-bit-flags"></a>Typy wyliczeniowe jako flagi bitowe

Jeśli chcesz, aby typ wyliczeniowy reprezentował kombinację opcji, Zdefiniuj elementy członkowskie wyliczenia dla tych opcji, tak że pojedynczy wybór jest polem bitowym. Oznacza to, że skojarzone wartości tych elementów członkowskich wyliczenia powinny być potęgami dwóch. Następnie można użyć [bitowe operatory logiczne `|` lub `&`](../operators/bitwise-and-shift-operators.md#enumeration-logical-operators) do łączenia opcji lub przecinających się kombinacji opcji. Aby wskazać, że typ wyliczeniowy deklaruje pola bitowe, Zastosuj do niego atrybut [flags](xref:System.FlagsAttribute) . Jak pokazano na poniższym przykładzie, można również uwzględnić niektóre typowe kombinacje w definicji typu wyliczenia.

[!code-csharp[enum flags](~/samples/csharp/language-reference/builtin-types/EnumType.cs#Flags)]

Aby uzyskać więcej informacji i przykładów, zobacz stronę referencyjną API <xref:System.FlagsAttribute?displayProperty=nameWithType> i [niewyłączne elementy członkowskie i atrybuty flag](/dotnet/api/system.enum#non-exclusive-members-and-the-flags-attribute) na stronie Dokumentacja interfejsu API <xref:System.Enum?displayProperty=nameWithType>.

## <a name="the-systemenum-type-and-enum-constraint"></a>Typ System. Enum i ograniczenie wyliczenia

Typ <xref:System.Enum?displayProperty=nameWithType> jest abstrakcyjną klasą bazową wszystkich typów wyliczeniowych. Zawiera kilka metod uzyskiwania informacji na temat typu wyliczenia i jego wartości. Aby uzyskać więcej informacji i przykładów, zobacz stronę referencyjną interfejsu API <xref:System.Enum?displayProperty=nameWithType>.

Począwszy od C# 7,3, można użyć `System.Enum` w ograniczeniu klasy bazowej (znanym jako [ograniczenie wyliczenia](../../programming-guide/generics/constraints-on-type-parameters.md#enum-constraints)), aby określić, że parametr typu jest typem wyliczenia.

## <a name="conversions"></a>Konwersje

Dla dowolnego typu wyliczenia istnieją jawne konwersje między typem wyliczenia i jego podstawowym typem całkowitym. W przypadku [rzutowania](../operators/type-testing-and-cast.md#cast-operator-) wartości wyliczenia na jej typ podstawowy wynik jest skojarzoną wartością całkowitą elementu członkowskiego wyliczenia.

[!code-csharp[enum conversions](~/samples/csharp/language-reference/builtin-types/EnumType.cs#Conversions)]

Użyj metody <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType>, aby określić, czy typ wyliczeniowy zawiera element członkowski wyliczenia z określoną wartością skojarzoną.

Dla dowolnego typu wyliczenia istnieją konwersje pakowania [i rozpakowywanie](../../programming-guide/types/boxing-and-unboxing.md) do i z typu <xref:System.Enum?displayProperty=nameWithType>.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz następujące sekcje [ C# specyfikacji języka](~/_csharplang/spec/introduction.md):

- [Wyliczenia](~/_csharplang/spec/enums.md)
- [Wartości wyliczeniowe i operacje](~/_csharplang/spec/enums.md#enum-values-and-operations)
- [Wyliczanie operatorów logicznych](~/_csharplang/spec/expressions.md#enumeration-logical-operators)
- [Operatory porównania wyliczenia](~/_csharplang/spec/expressions.md#enumeration-comparison-operators)
- [Jawne konwersje wyliczenia](~/_csharplang/spec/conversions.md#explicit-enumeration-conversions)
- [Niejawne konwersje wyliczenia](~/_csharplang/spec/conversions.md#implicit-enumeration-conversions)

## <a name="see-also"></a>Zobacz też

- [C#odwoła](../index.md)
- [Ciągi formatujące Wyliczenie](../../../standard/base-types/enumeration-format-strings.md)
- [Wyliczeniowe konwencje nazewnictwa](../../../standard/design-guidelines/names-of-classes-structs-and-interfaces.md#naming-enumerations)
- [Switch, instrukcja](../keywords/switch.md)
