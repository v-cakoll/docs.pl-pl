---
title: Typy wyliczenia — odwołanie do języka C#
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
ms.openlocfilehash: 15f5e9ccb1396277229ba935381812700f63ece8
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121160"
---
# <a name="enumeration-types-c-reference"></a>Typy wyliczenia (odwołanie do języka C#)

*Typ wyliczenia* (lub *typ wyliczenia*) jest [typem wartości](value-types.md) zdefiniowanym przez zestaw nazwanych stałych podstawowego integralnego typu [liczbowego.](integral-numeric-types.md) Aby zdefiniować typ wyliczenia, użyj `enum` słowa kluczowego i określ nazwy elementów *wyliczenia:*

```csharp
enum Season
{
    Spring,
    Summer,
    Autumn,
    Winter
}
```

Domyślnie skojarzone wartości stałe elementów wyliczenia są typu; `int` zaczynają się od zera i zwiększają się o jeden po kolejności tekstu definicji. Można jawnie określić dowolny inny [całkowy](integral-numeric-types.md) typ liczbowy jako podstawowy typ typu wyliczenia. Można również jawnie określić skojarzone wartości stałe, jak pokazano w poniższym przykładzie:

```csharp
enum ErrorCode : ushort
{
    None = 0,
    Unknown = 1,
    ConnectionLost = 100,
    OutlierReading = 200
}
```

Nie można zdefiniować metody wewnątrz definicji typu wyliczenia. Aby dodać funkcjonalność do typu wyliczenia, utwórz [metodę rozszerzenia](../../programming-guide/classes-and-structs/extension-methods.md).

Domyślną wartością typu `E` wyliczenia jest wartość `(E)0`wytwarzana przez wyrażenie, nawet jeśli zero nie ma odpowiedniego elementu członkowskiego wyliczenia.

Typ wyliczenia służy do reprezentowania wyboru z zestawu wzajemnie wykluczające się wartości lub kombinacji wyborów. Aby reprezentować kombinację wyborów, zdefiniuj typ wyliczenia jako flagi bitowe.

## <a name="enumeration-types-as-bit-flags"></a>Typy wyliczenia jako flagi bitowe

Jeśli chcesz, aby typ wyliczenia reprezentował kombinację wyborów, zdefiniuj elementy członkowskie wyliczenia dla tych wyborów, tak aby indywidualny wybór był polem bitowym. Oznacza to, że powiązane wartości tych członków wyliczenia powinny być uprawnieniami dwóch. Następnie można użyć [bitowych operatorów `|` logicznych lub `&` ](../operators/bitwise-and-shift-operators.md#enumeration-logical-operators) połączyć wybory lub przecinać kombinacje wyborów, odpowiednio. Aby wskazać, że typ wyliczenia deklaruje pola bitowe, zastosuj do niego atrybut [Flags.](xref:System.FlagsAttribute) Jak pokazano w poniższym przykładzie, można również uwzględnić niektóre typowe kombinacje w definicji typu wyliczenia.

[!code-csharp[enum flags](snippets/EnumType.cs#Flags)]

Aby uzyskać więcej informacji i <xref:System.FlagsAttribute?displayProperty=nameWithType> przykładów, zobacz stronę odwołania interfejsu API i [niewyłącznych członków i flagi atrybut](/dotnet/api/system.enum#non-exclusive-members-and-the-flags-attribute) sekcji na stronie odwołania interfejsu <xref:System.Enum?displayProperty=nameWithType> API.

## <a name="the-systemenum-type-and-enum-constraint"></a>Ograniczenie typu i wyliczenia System.Enum

Typ <xref:System.Enum?displayProperty=nameWithType> jest abstrakcyjną klasą podstawową wszystkich typów wyliczenia. Zawiera szereg metod, aby uzyskać informacje o typie wyliczenia i jego wartości. Aby uzyskać więcej informacji i <xref:System.Enum?displayProperty=nameWithType> przykładów, zobacz stronę odwołania do interfejsu API.

Począwszy od języka C# 7.3, można użyć `System.Enum` w ograniczeniu klasy podstawowej (który jest znany jako ograniczenie [wyliczenia](../../programming-guide/generics/constraints-on-type-parameters.md#enum-constraints)), aby określić, że parametr typu jest typem wyliczenia.

## <a name="conversions"></a>Konwersje

Dla każdego typu wyliczenia istnieją jawne konwersje między typem wyliczenia i jego podstawowym typem integralnym. Jeśli [rzutujesz](../operators/type-testing-and-cast.md#cast-expression) wartość wyliczenia do jego typu bazowego, wynikiem jest skojarzona wartość całkowita elementu członkowskiego wyliczenia.

[!code-csharp[enum conversions](snippets/EnumType.cs#Conversions)]

Użyj <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> metody, aby ustalić, czy typ wyliczenia zawiera element członkowski wyliczenia z określoną skojarzoną wartością.

Dla każdego typu wyliczenia istnieje [boks i unboxing](../../programming-guide/types/boxing-and-unboxing.md) konwersji do iz <xref:System.Enum?displayProperty=nameWithType> typu, odpowiednio.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz następujące sekcje [specyfikacji języka języka C#:](~/_csharplang/spec/introduction.md)

- [Wyliczenia](~/_csharplang/spec/enums.md)
- [Wartości wyliczenia i operacje](~/_csharplang/spec/enums.md#enum-values-and-operations)
- [Operatory logiczne wyliczenia](~/_csharplang/spec/expressions.md#enumeration-logical-operators)
- [Operatory porównania wyliczenia](~/_csharplang/spec/expressions.md#enumeration-comparison-operators)
- [Jawne konwersje wyliczenia](~/_csharplang/spec/conversions.md#explicit-enumeration-conversions)
- [Konwersje wyliczenia niejawnego](~/_csharplang/spec/conversions.md#implicit-enumeration-conversions)

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)
- [Wyliczanie ciągów formatujących](../../../standard/base-types/enumeration-format-strings.md)
- [Wytyczne dotyczące projektowania — projektowanie wyliczenia](../../../standard/design-guidelines/enum.md)
- [Wskazówki dotyczące projektowania — konwencje nazewnictwa wyliczenia](../../../standard/design-guidelines/names-of-classes-structs-and-interfaces.md#naming-enumerations)
- [instrukcja przełączania](../keywords/switch.md)
