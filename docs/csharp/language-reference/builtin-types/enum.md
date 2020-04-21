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
ms.openlocfilehash: 617c5ec037ad7a47b43cca2c13da4a77aa682997
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739092"
---
# <a name="enumeration-types-c-reference"></a><span data-ttu-id="1c057-103">Typy wyliczenia (odwołanie do języka C#)</span><span class="sxs-lookup"><span data-stu-id="1c057-103">Enumeration types (C# reference)</span></span>

<span data-ttu-id="1c057-104">*Typ wyliczenia* (lub *typ wyliczenia*) jest [typem wartości](value-types.md) zdefiniowanym przez zestaw nazwanych stałych podstawowego integralnego typu [liczbowego.](integral-numeric-types.md)</span><span class="sxs-lookup"><span data-stu-id="1c057-104">An *enumeration type* (or *enum type*) is a [value type](value-types.md) defined by a set of named constants of the underlying [integral numeric](integral-numeric-types.md) type.</span></span> <span data-ttu-id="1c057-105">Aby zdefiniować typ wyliczenia, użyj `enum` słowa kluczowego i określ nazwy elementów *wyliczenia:*</span><span class="sxs-lookup"><span data-stu-id="1c057-105">To define an enumeration type, use the `enum` keyword and specify the names of *enum members*:</span></span>

```csharp
enum Season
{
    Spring,
    Summer,
    Autumn,
    Winter
}
```

<span data-ttu-id="1c057-106">Domyślnie skojarzone wartości stałe elementów wyliczenia są typu; `int` zaczynają się od zera i zwiększają się o jeden po kolejności tekstu definicji.</span><span class="sxs-lookup"><span data-stu-id="1c057-106">By default, the associated constant values of enum members are of type `int`; they start with zero and increase by one following the definition text order.</span></span> <span data-ttu-id="1c057-107">Można jawnie określić dowolny inny [całkowy](integral-numeric-types.md) typ liczbowy jako podstawowy typ typu wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="1c057-107">You can explicitly specify any other [integral numeric](integral-numeric-types.md) type as an underlying type of an enumeration type.</span></span> <span data-ttu-id="1c057-108">Można również jawnie określić skojarzone wartości stałe, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="1c057-108">You can also explicitly specify the associated constant values, as the following example shows:</span></span>

```csharp
enum ErrorCode : ushort
{
    None = 0,
    Unknown = 1,
    ConnectionLost = 100,
    OutlierReading = 200
}
```

<span data-ttu-id="1c057-109">Nie można zdefiniować metody wewnątrz definicji typu wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="1c057-109">You cannot define a method inside the definition of an enumeration type.</span></span> <span data-ttu-id="1c057-110">Aby dodać funkcjonalność do typu wyliczenia, utwórz [metodę rozszerzenia](../../programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="1c057-110">To add functionality to an enumeration type, create an [extension method](../../programming-guide/classes-and-structs/extension-methods.md).</span></span>

<span data-ttu-id="1c057-111">Domyślną wartością typu `E` wyliczenia jest wartość `(E)0`wytwarzana przez wyrażenie, nawet jeśli zero nie ma odpowiedniego elementu członkowskiego wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="1c057-111">The default value of an enumeration type `E` is the value produced by expression `(E)0`, even if zero doesn't have the corresponding enum member.</span></span>

<span data-ttu-id="1c057-112">Typ wyliczenia służy do reprezentowania wyboru z zestawu wzajemnie wykluczające się wartości lub kombinacji wyborów.</span><span class="sxs-lookup"><span data-stu-id="1c057-112">You use an enumeration type to represent a choice from a set of mutually exclusive values or a combination of choices.</span></span> <span data-ttu-id="1c057-113">Aby reprezentować kombinację wyborów, zdefiniuj typ wyliczenia jako flagi bitowe.</span><span class="sxs-lookup"><span data-stu-id="1c057-113">To represent a combination of choices, define an enumeration type as bit flags.</span></span>

## <a name="enumeration-types-as-bit-flags"></a><span data-ttu-id="1c057-114">Typy wyliczenia jako flagi bitowe</span><span class="sxs-lookup"><span data-stu-id="1c057-114">Enumeration types as bit flags</span></span>

<span data-ttu-id="1c057-115">Jeśli chcesz, aby typ wyliczenia reprezentował kombinację wyborów, zdefiniuj elementy członkowskie wyliczenia dla tych wyborów, tak aby indywidualny wybór był polem bitowym.</span><span class="sxs-lookup"><span data-stu-id="1c057-115">If you want an enumeration type to represent a combination of choices, define enum members for those choices such that an individual choice is a bit field.</span></span> <span data-ttu-id="1c057-116">Oznacza to, że powiązane wartości tych członków wyliczenia powinny być uprawnieniami dwóch.</span><span class="sxs-lookup"><span data-stu-id="1c057-116">That is, the associated values of those enum members should be the powers of two.</span></span> <span data-ttu-id="1c057-117">Następnie można użyć [bitowych operatorów `|` logicznych lub `&` ](../operators/bitwise-and-shift-operators.md#enumeration-logical-operators) połączyć wybory lub przecinać kombinacje wyborów, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="1c057-117">Then, you can use the [bitwise logical operators `|` or `&`](../operators/bitwise-and-shift-operators.md#enumeration-logical-operators) to combine choices or intersect combinations of choices, respectively.</span></span> <span data-ttu-id="1c057-118">Aby wskazać, że typ wyliczenia deklaruje pola bitowe, zastosuj do niego atrybut [Flags.](xref:System.FlagsAttribute)</span><span class="sxs-lookup"><span data-stu-id="1c057-118">To indicate that an enumeration type declares bit fields, apply the [Flags](xref:System.FlagsAttribute) attribute to it.</span></span> <span data-ttu-id="1c057-119">Jak pokazano w poniższym przykładzie, można również uwzględnić niektóre typowe kombinacje w definicji typu wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="1c057-119">As the following example shows, you can also include some typical combinations in the definition of an enumeration type.</span></span>

[!code-csharp[enum flags](snippets/EnumType.cs#Flags)]

<span data-ttu-id="1c057-120">Aby uzyskać więcej informacji i <xref:System.FlagsAttribute?displayProperty=nameWithType> przykładów, zobacz stronę odwołania interfejsu API i [niewyłącznych członków i flagi atrybut](/dotnet/api/system.enum#non-exclusive-members-and-the-flags-attribute) sekcji na stronie odwołania interfejsu <xref:System.Enum?displayProperty=nameWithType> API.</span><span class="sxs-lookup"><span data-stu-id="1c057-120">For more information and examples, see the <xref:System.FlagsAttribute?displayProperty=nameWithType> API reference page and the [Non-exclusive members and the Flags attribute](/dotnet/api/system.enum#non-exclusive-members-and-the-flags-attribute) section of the <xref:System.Enum?displayProperty=nameWithType> API reference page.</span></span>

## <a name="the-systemenum-type-and-enum-constraint"></a><span data-ttu-id="1c057-121">Ograniczenie typu i wyliczenia System.Enum</span><span class="sxs-lookup"><span data-stu-id="1c057-121">The System.Enum type and enum constraint</span></span>

<span data-ttu-id="1c057-122">Typ <xref:System.Enum?displayProperty=nameWithType> jest abstrakcyjną klasą podstawową wszystkich typów wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="1c057-122">The <xref:System.Enum?displayProperty=nameWithType> type is the abstract base class of all enumeration types.</span></span> <span data-ttu-id="1c057-123">Zawiera szereg metod, aby uzyskać informacje o typie wyliczenia i jego wartości.</span><span class="sxs-lookup"><span data-stu-id="1c057-123">It provides a number of methods to get information about an enumeration type and its values.</span></span> <span data-ttu-id="1c057-124">Aby uzyskać więcej informacji i <xref:System.Enum?displayProperty=nameWithType> przykładów, zobacz stronę odwołania do interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="1c057-124">For more information and examples, see the <xref:System.Enum?displayProperty=nameWithType> API reference page.</span></span>

<span data-ttu-id="1c057-125">Począwszy od języka C# 7.3, można użyć `System.Enum` w ograniczeniu klasy podstawowej (który jest znany jako ograniczenie [wyliczenia](../../programming-guide/generics/constraints-on-type-parameters.md#enum-constraints)), aby określić, że parametr typu jest typem wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="1c057-125">Beginning with C# 7.3, you can use `System.Enum` in a base class constraint (that is known as the [enum constraint](../../programming-guide/generics/constraints-on-type-parameters.md#enum-constraints)) to specify that a type parameter is an enumeration type.</span></span>

## <a name="conversions"></a><span data-ttu-id="1c057-126">Konwersje</span><span class="sxs-lookup"><span data-stu-id="1c057-126">Conversions</span></span>

<span data-ttu-id="1c057-127">Dla każdego typu wyliczenia istnieją jawne konwersje między typem wyliczenia i jego podstawowym typem integralnym.</span><span class="sxs-lookup"><span data-stu-id="1c057-127">For any enumeration type, there exist explicit conversions between the enumeration type and its underlying integral type.</span></span> <span data-ttu-id="1c057-128">Jeśli [rzutujesz](../operators/type-testing-and-cast.md#cast-expression) wartość wyliczenia do jego typu bazowego, wynikiem jest skojarzona wartość całkowita elementu członkowskiego wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="1c057-128">If you [cast](../operators/type-testing-and-cast.md#cast-expression) an enum value to its underlying type, the result is the associated integral value of an enum member.</span></span>

[!code-csharp[enum conversions](snippets/EnumType.cs#Conversions)]

<span data-ttu-id="1c057-129">Użyj <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> metody, aby ustalić, czy typ wyliczenia zawiera element członkowski wyliczenia z określoną skojarzoną wartością.</span><span class="sxs-lookup"><span data-stu-id="1c057-129">Use the <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> method to determine whether an enumeration type contains an enum member with the certain associated value.</span></span>

<span data-ttu-id="1c057-130">Dla każdego typu wyliczenia istnieje [boks i unboxing](../../programming-guide/types/boxing-and-unboxing.md) konwersji do iz <xref:System.Enum?displayProperty=nameWithType> typu, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="1c057-130">For any enumeration type, there exist [boxing and unboxing](../../programming-guide/types/boxing-and-unboxing.md) conversions to and from the <xref:System.Enum?displayProperty=nameWithType> type, respectively.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="1c057-131">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="1c057-131">C# language specification</span></span>

<span data-ttu-id="1c057-132">Aby uzyskać więcej informacji, zobacz następujące sekcje [specyfikacji języka języka C#:](~/_csharplang/spec/introduction.md)</span><span class="sxs-lookup"><span data-stu-id="1c057-132">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="1c057-133">Wyliczenia</span><span class="sxs-lookup"><span data-stu-id="1c057-133">Enums</span></span>](~/_csharplang/spec/enums.md)
- [<span data-ttu-id="1c057-134">Wartości wyliczenia i operacje</span><span class="sxs-lookup"><span data-stu-id="1c057-134">Enum values and operations</span></span>](~/_csharplang/spec/enums.md#enum-values-and-operations)
- [<span data-ttu-id="1c057-135">Operatory logiczne wyliczenia</span><span class="sxs-lookup"><span data-stu-id="1c057-135">Enumeration logical operators</span></span>](~/_csharplang/spec/expressions.md#enumeration-logical-operators)
- [<span data-ttu-id="1c057-136">Operatory porównania wyliczenia</span><span class="sxs-lookup"><span data-stu-id="1c057-136">Enumeration comparison operators</span></span>](~/_csharplang/spec/expressions.md#enumeration-comparison-operators)
- [<span data-ttu-id="1c057-137">Jawne konwersje wyliczenia</span><span class="sxs-lookup"><span data-stu-id="1c057-137">Explicit enumeration conversions</span></span>](~/_csharplang/spec/conversions.md#explicit-enumeration-conversions)
- [<span data-ttu-id="1c057-138">Konwersje wyliczenia niejawnego</span><span class="sxs-lookup"><span data-stu-id="1c057-138">Implicit enumeration conversions</span></span>](~/_csharplang/spec/conversions.md#implicit-enumeration-conversions)

## <a name="see-also"></a><span data-ttu-id="1c057-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1c057-139">See also</span></span>

- [<span data-ttu-id="1c057-140">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="1c057-140">C# reference</span></span>](../index.md)
- [<span data-ttu-id="1c057-141">Wyliczanie ciągów formatujących</span><span class="sxs-lookup"><span data-stu-id="1c057-141">Enumeration format strings</span></span>](../../../standard/base-types/enumeration-format-strings.md)
- [<span data-ttu-id="1c057-142">Wytyczne dotyczące projektowania — projektowanie wyliczenia</span><span class="sxs-lookup"><span data-stu-id="1c057-142">Design guidelines - Enum design</span></span>](../../../standard/design-guidelines/enum.md)
- [<span data-ttu-id="1c057-143">Wskazówki dotyczące projektowania — konwencje nazewnictwa wyliczenia</span><span class="sxs-lookup"><span data-stu-id="1c057-143">Design guidelines - Enum naming conventions</span></span>](../../../standard/design-guidelines/names-of-classes-structs-and-interfaces.md#naming-enumerations)
- [<span data-ttu-id="1c057-144">instrukcja przełączania</span><span class="sxs-lookup"><span data-stu-id="1c057-144">switch statement</span></span>](../keywords/switch.md)
