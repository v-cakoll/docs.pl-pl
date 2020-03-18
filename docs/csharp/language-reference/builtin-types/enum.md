---
title: Typy wyliczania — odwołanie do języka C#
description: Dowiedz się więcej o typach wyliczenia języka C#, które reprezentują wybór lub kombinację opcji
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
ms.openlocfilehash: ab5eb1679f846bf0e25d90a4d0e0a71f0bdb0096
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847715"
---
# <a name="enumeration-types-c-reference"></a>Typy wyliczania (odwołanie do języka C#)

*Typ wyliczenia* (lub *typ wyliczenia)* jest [typem wartości](value-types.md) zdefiniowanym przez zestaw nazwanych stałych podstawowego integralnego typu [liczbowego.](integral-numeric-types.md) Aby zdefiniować typ wyliczenia, użyj słowa kluczowego `enum` i określ nazwy elementów członkowskich *wyliczenia:*

```csharp
enum Season
{
    Spring,
    Summer,
    Autumn,
    Winter
}
```

Domyślnie skojarzone stałe wartości elementów członkowskich `int`wyliczenia są typu ; zaczynają się od zera i zwiększają się o jeden po kolejności tekstu definicji. Można jawnie określić dowolny inny [typ liczbowy integralną](integral-numeric-types.md) jako typ podstawowy typu wyliczenia. Można również jawnie określić skojarzone wartości stałe, jak pokazano w poniższym przykładzie:

```csharp
enum ErrorCode : ushort
{
    None = 0,
    Unknown = 1,
    ConnectionLost = 100,
    OutlierReading = 200
}
```

Nie można zdefiniować metody wewnątrz definicji typu wyliczenia. Aby dodać funkcje do typu wyliczenia, należy utworzyć [metodę rozszerzenia](../../programming-guide/classes-and-structs/extension-methods.md).

Domyślną wartością typu `E` wyliczenia jest `(E)0`wartość tworzona przez wyrażenie , nawet jeśli zero nie ma odpowiedniego elementu członkowskiego wyliczenia.

Typ wyliczenia służy do reprezentowania wyboru z zestawu wzajemnie wykluczające się wartości lub kombinacji wyborów. Aby reprezentować kombinację opcji, należy zdefiniować typ wyliczenia jako flagi bitowe.

## <a name="enumeration-types-as-bit-flags"></a>Typy wyliczenia jako flagi bitowe

Jeśli typ wyliczenia ma reprezentować kombinację opcji, należy zdefiniować elementy członkowskie wyliczenia dla tych wyborów, tak aby pojedynczy wybór był polem bitowym. Oznacza to, że powiązane wartości tych członków wyliczenia powinny być uprawnieniami dwóch osób. Następnie można użyć [bitowych operatorów `|` `&` logicznych lub](../operators/bitwise-and-shift-operators.md#enumeration-logical-operators) połączyć wybory lub przecinające się kombinacje wyborów, odpowiednio. Aby wskazać, że typ wyliczenia deklaruje pola bitowe, zastosuj do niego atrybut [Flagi.](xref:System.FlagsAttribute) Jak pokazano w poniższym przykładzie, można również uwzględnić niektóre typowe kombinacje w definicji typu wyliczenia.

[!code-csharp[enum flags](snippets/EnumType.cs#Flags)]

Aby uzyskać więcej informacji i <xref:System.FlagsAttribute?displayProperty=nameWithType> przykładów, zobacz stronę odwołania interfejsu API i [niewyłącznych członków i Flagi atrybut](/dotnet/api/system.enum#non-exclusive-members-and-the-flags-attribute) sekcji strony odwołania <xref:System.Enum?displayProperty=nameWithType> interfejsu API.

## <a name="the-systemenum-type-and-enum-constraint"></a>Ograniczenie typu System.Enum i wyliczenia

Typ <xref:System.Enum?displayProperty=nameWithType> jest abstrakcyjną klasą podstawową wszystkich typów wyliczenia. Zawiera szereg metod, aby uzyskać informacje o typie wyliczenia i jego wartości. Aby uzyskać więcej informacji i <xref:System.Enum?displayProperty=nameWithType> przykłady, zobacz stronę referencyjną interfejsu API.

Począwszy od C# 7.3, można użyć `System.Enum` w ograniczeniu klasy podstawowej (który jest znany jako ograniczenie [wyliczenia),](../../programming-guide/generics/constraints-on-type-parameters.md#enum-constraints)aby określić, że parametr typu jest typem wyliczenia.

## <a name="conversions"></a>Konwersje

Dla dowolnego typu wyliczenia istnieją jawne konwersje między typem wyliczenia a jego podstawowym typem całki. Jeśli [rzutujesz](../operators/type-testing-and-cast.md#cast-operator-) wartość wyliczeniową na jego typ bazowy, wynik jest skojarzoną wartością całkowitą elementu członkowskiego wyliczenia.

[!code-csharp[enum conversions](snippets/EnumType.cs#Conversions)]

Użyj <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> metody, aby ustalić, czy typ wyliczenia zawiera element członkowski wyliczenia z określoną skojarzoną wartością.

Dla każdego typu wyliczenia istnieje [boks i rozpakowywanie](../../programming-guide/types/boxing-and-unboxing.md) konwersji do iz <xref:System.Enum?displayProperty=nameWithType> typu, odpowiednio.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz następujące sekcje [specyfikacji języka Języka C#:](~/_csharplang/spec/introduction.md)

- [Wyliczenia](~/_csharplang/spec/enums.md)
- [Wartości wyliczeniowe i operacje](~/_csharplang/spec/enums.md#enum-values-and-operations)
- [Operatory logiczne wyliczania](~/_csharplang/spec/expressions.md#enumeration-logical-operators)
- [Operatory porównania wyliczenia](~/_csharplang/spec/expressions.md#enumeration-comparison-operators)
- [Jawne konwersje wyliczania](~/_csharplang/spec/conversions.md#explicit-enumeration-conversions)
- [Niejawne konwersje wyliczania](~/_csharplang/spec/conversions.md#implicit-enumeration-conversions)

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)
- [Ciągi formatu wyliczenia](../../../standard/base-types/enumeration-format-strings.md)
- [Wytyczne projektowe - Projektowanie enum](../../../standard/design-guidelines/enum.md)
- [Wytyczne projektowe — konwencje nazewnictwa wyliczenia](../../../standard/design-guidelines/names-of-classes-structs-and-interfaces.md#naming-enumerations)
- [instrukcja switch](../keywords/switch.md)
