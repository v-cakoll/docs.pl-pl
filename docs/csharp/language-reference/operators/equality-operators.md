---
title: Operatory równości — odwołanie do języka C#
description: Dowiedz się więcej o operatorach porównania równości języka C# i równości typów Języka C#.
ms.date: 06/26/2019
author: pkulikov
f1_keywords:
- ==_CSharpKeyword
- '!=_CSharpKeyword'
helpviewer_keywords:
- comparison operators [C#]
- relational operators [C#]
- equality operator [C#]
- equals operator [C#]
- == operator [C#]
- inequality operator [C#]
- not equals operator [C#]
- '!= operator [C#]'
ms.openlocfilehash: 079522b18afdf86a942d502672174516d45d37fc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399568"
---
# <a name="equality-operators-c-reference"></a><span data-ttu-id="bedb1-103">Operatory równości (odwołanie do języka C#)</span><span class="sxs-lookup"><span data-stu-id="bedb1-103">Equality operators (C# reference)</span></span>

<span data-ttu-id="bedb1-104">[ `==` Operatorzy (równości)](#equality-operator-) i [ `!=` (nierówności)](#inequality-operator-) sprawdzają, czy ich argumenty są równe, czy nie.</span><span class="sxs-lookup"><span data-stu-id="bedb1-104">The [`==` (equality)](#equality-operator-) and [`!=` (inequality)](#inequality-operator-) operators check if their operands are equal or not.</span></span>

## <a name="equality-operator-"></a><span data-ttu-id="bedb1-105">Operator równości ==</span><span class="sxs-lookup"><span data-stu-id="bedb1-105">Equality operator ==</span></span>

<span data-ttu-id="bedb1-106">Operator `==` równości `true` zwraca, jeśli jego argumenty są równe, `false` w przeciwnym razie.</span><span class="sxs-lookup"><span data-stu-id="bedb1-106">The equality operator `==` returns `true` if its operands are equal, `false` otherwise.</span></span>

### <a name="value-types-equality"></a><span data-ttu-id="bedb1-107">Równość typów wartości</span><span class="sxs-lookup"><span data-stu-id="bedb1-107">Value types equality</span></span>

<span data-ttu-id="bedb1-108">Argumenty [wbudowanych typów wartości](../builtin-types/value-types.md#built-in-value-types) są równe, jeśli ich wartości są równe:</span><span class="sxs-lookup"><span data-stu-id="bedb1-108">Operands of the [built-in value types](../builtin-types/value-types.md#built-in-value-types) are equal if their values are equal:</span></span>

[!code-csharp-interactive[value types equality](snippets/EqualityOperators.cs#ValueTypesEquality)]

> [!NOTE]
> <span data-ttu-id="bedb1-109">Dla `==`, [ `<` `>`, `<=`, `>=` i](comparison-operators.md) operatorów, jeśli którykolwiek z argumentów <xref:System.Single.NaN?displayProperty=nameWithType>nie jest liczbą ( `false`<xref:System.Double.NaN?displayProperty=nameWithType> lub ), wynikiem działania jest .</span><span class="sxs-lookup"><span data-stu-id="bedb1-109">For the `==`, [`<`, `>`, `<=`, and `>=`](comparison-operators.md) operators, if any of the operands is not a number (<xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType>), the result of operation is `false`.</span></span> <span data-ttu-id="bedb1-110">Oznacza to, `NaN` że wartość nie jest większa niż, mniejsza `double` niż, ani równa żadnej innej (lub) `float`wartości, w tym `NaN`.</span><span class="sxs-lookup"><span data-stu-id="bedb1-110">That means that the `NaN` value is neither greater than, less than, nor equal to any other `double` (or `float`) value, including `NaN`.</span></span> <span data-ttu-id="bedb1-111">Aby uzyskać więcej informacji i <xref:System.Double.NaN?displayProperty=nameWithType> <xref:System.Single.NaN?displayProperty=nameWithType> przykładów, zobacz artykuł lub odwołanie.</span><span class="sxs-lookup"><span data-stu-id="bedb1-111">For more information and examples, see the <xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType> reference article.</span></span>

<span data-ttu-id="bedb1-112">Dwa argumenty tego samego typu [wyliczenia](../builtin-types/enum.md) są równe, jeśli odpowiednie wartości podstawowego typu integralnego są równe.</span><span class="sxs-lookup"><span data-stu-id="bedb1-112">Two operands of the same [enum](../builtin-types/enum.md) type are equal if the corresponding values of the underlying integral type are equal.</span></span>

<span data-ttu-id="bedb1-113">Typy [struktury](../builtin-types/struct.md) zdefiniowane przez użytkownika nie `==` obsługują operatora domyślnie.</span><span class="sxs-lookup"><span data-stu-id="bedb1-113">User-defined [struct](../builtin-types/struct.md) types don't support the `==` operator by default.</span></span> <span data-ttu-id="bedb1-114">Aby obsługiwać `==` operatora, struktury zdefiniowane przez użytkownika musi [przeciążać](operator-overloading.md) go.</span><span class="sxs-lookup"><span data-stu-id="bedb1-114">To support the `==` operator, a user-defined struct must [overload](operator-overloading.md) it.</span></span>

<span data-ttu-id="bedb1-115">Począwszy od języka C# `==` `!=` 7.3, operatory i są obsługiwane przez [krotek C#](../../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="bedb1-115">Beginning with C# 7.3, the `==` and `!=` operators are supported by C# [tuples](../../tuples.md).</span></span> <span data-ttu-id="bedb1-116">Aby uzyskać więcej informacji, zobacz [Równości i krotek](../../tuples.md#equality-and-tuples) sekcji [typu krotka Języka C#.](../../tuples.md)</span><span class="sxs-lookup"><span data-stu-id="bedb1-116">For more information, see the [Equality and tuples](../../tuples.md#equality-and-tuples) section of the [C# tuple types](../../tuples.md) article.</span></span>

### <a name="reference-types-equality"></a><span data-ttu-id="bedb1-117">Równość typów odwołań</span><span class="sxs-lookup"><span data-stu-id="bedb1-117">Reference types equality</span></span>

<span data-ttu-id="bedb1-118">Domyślnie dwa operandy typu odwołania są równe, jeśli odnoszą się do tego samego obiektu:</span><span class="sxs-lookup"><span data-stu-id="bedb1-118">By default, two reference-type operands are equal if they refer to the same object:</span></span>

[!code-csharp[reference type equality](snippets/EqualityOperators.cs#ReferenceTypesEquality)]

<span data-ttu-id="bedb1-119">Jak pokazano w przykładzie, typy odwołań zdefiniowane przez `==` użytkownika domyślnie obsługują operatora.</span><span class="sxs-lookup"><span data-stu-id="bedb1-119">As the example shows, user-defined reference types support the `==` operator by default.</span></span> <span data-ttu-id="bedb1-120">Jednak typ odwołania może przeciążać `==` operatora.</span><span class="sxs-lookup"><span data-stu-id="bedb1-120">However, a reference type can overload the `==` operator.</span></span> <span data-ttu-id="bedb1-121">Jeśli typ odwołania przeciążenia `==` operatora, należy użyć <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> metody, aby sprawdzić, czy dwa odwołania tego typu odnoszą się do tego samego obiektu.</span><span class="sxs-lookup"><span data-stu-id="bedb1-121">If a reference type overloads the `==` operator, use the <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> method to check if two references of that type refer to the same object.</span></span>

### <a name="string-equality"></a><span data-ttu-id="bedb1-122">Równość ciągów</span><span class="sxs-lookup"><span data-stu-id="bedb1-122">String equality</span></span>

<span data-ttu-id="bedb1-123">Dwa [argumenty smyczkowe](../builtin-types/reference-types.md#the-string-type) są równe, `null` gdy oba z nich są lub oba instancje ciągów mają tę samą długość i mają identyczne znaki w każdej pozycji znaku:</span><span class="sxs-lookup"><span data-stu-id="bedb1-123">Two [string](../builtin-types/reference-types.md#the-string-type) operands are equal when both of them are `null` or both string instances are of the same length and have identical characters in each character position:</span></span>

[!code-csharp-interactive[string equality](snippets/EqualityOperators.cs#StringEquality)]

<span data-ttu-id="bedb1-124">Jest to porównanie z uwzględnieniem wielkości liter.</span><span class="sxs-lookup"><span data-stu-id="bedb1-124">That is a case-sensitive ordinal comparison.</span></span> <span data-ttu-id="bedb1-125">Aby uzyskać więcej informacji na temat porównywania [ciągów, zobacz Jak porównać ciągi w języku C#](../../how-to/compare-strings.md).</span><span class="sxs-lookup"><span data-stu-id="bedb1-125">For more information about string comparison, see [How to compare strings in C#](../../how-to/compare-strings.md).</span></span>

### <a name="delegate-equality"></a><span data-ttu-id="bedb1-126">Delegowanie równości</span><span class="sxs-lookup"><span data-stu-id="bedb1-126">Delegate equality</span></span>

<span data-ttu-id="bedb1-127">Dwa operandy [delegata](../../programming-guide/delegates/index.md) tego samego typu wykonywania są `null` równe, gdy oba z nich są lub ich listy wywołań są tej samej długości i mają równe wpisy w każdej pozycji:</span><span class="sxs-lookup"><span data-stu-id="bedb1-127">Two [delegate](../../programming-guide/delegates/index.md) operands of the same runtime type are equal when both of them are `null` or their invocation lists are of the same length and have equal entries in each position:</span></span>

[!code-csharp-interactive[delegate equality](snippets/EqualityOperators.cs#DelegateEquality)]

<span data-ttu-id="bedb1-128">Aby uzyskać więcej informacji, zobacz [delegowanie operatorów równości](~/_csharplang/spec/expressions.md#delegate-equality-operators) sekcji [specyfikacji języka Języka C#.](~/_csharplang/spec/introduction.md)</span><span class="sxs-lookup"><span data-stu-id="bedb1-128">For more information, see the [Delegate equality operators](~/_csharplang/spec/expressions.md#delegate-equality-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="bedb1-129">Delegatów, które są produkowane z oceny semantycznie [identyczne wyrażenia lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) nie są równe, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="bedb1-129">Delegates that are produced from evaluation of semantically identical [lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md) are not equal, as the following example shows:</span></span>

[!code-csharp-interactive[from identical lambdas](snippets/EqualityOperators.cs#IdenticalLambdas)]

## <a name="inequality-operator-"></a><span data-ttu-id="bedb1-130">Operator nierówności !=</span><span class="sxs-lookup"><span data-stu-id="bedb1-130">Inequality operator !=</span></span>

<span data-ttu-id="bedb1-131">Operator `!=` nierówności `true` zwraca, jeśli jego argumenty `false` nie są równe, w przeciwnym razie.</span><span class="sxs-lookup"><span data-stu-id="bedb1-131">The inequality operator `!=` returns `true` if its operands are not equal, `false` otherwise.</span></span> <span data-ttu-id="bedb1-132">Dla operandów [typów wbudowanych](../builtin-types/built-in-types.md)wyrażenie `x != y` daje taki sam wynik jak `!(x == y)`wyrażenie .</span><span class="sxs-lookup"><span data-stu-id="bedb1-132">For the operands of the [built-in types](../builtin-types/built-in-types.md), the expression `x != y` produces the same result as the expression `!(x == y)`.</span></span> <span data-ttu-id="bedb1-133">Aby uzyskać więcej informacji na temat równości typów, zobacz [Equality operator](#equality-operator-) sekcji.</span><span class="sxs-lookup"><span data-stu-id="bedb1-133">For more information about type equality, see the [Equality operator](#equality-operator-) section.</span></span>

<span data-ttu-id="bedb1-134">W poniższym przykładzie przedstawiono `!=` użycie operatora:</span><span class="sxs-lookup"><span data-stu-id="bedb1-134">The following example demonstrates the usage of the `!=` operator:</span></span>

[!code-csharp-interactive[non-equality examples](snippets/EqualityOperators.cs#NonEquality)]

## <a name="operator-overloadability"></a><span data-ttu-id="bedb1-135">Przeciążenie operatora</span><span class="sxs-lookup"><span data-stu-id="bedb1-135">Operator overloadability</span></span>

<span data-ttu-id="bedb1-136">Typ zdefiniowany przez użytkownika `==` może `!=` [przeciążać](operator-overloading.md) i operatorów.</span><span class="sxs-lookup"><span data-stu-id="bedb1-136">A user-defined type can [overload](operator-overloading.md) the `==` and `!=` operators.</span></span> <span data-ttu-id="bedb1-137">Jeśli typ przeciążenia jednego z dwóch operatorów, musi również przeciążenia innego.</span><span class="sxs-lookup"><span data-stu-id="bedb1-137">If a type overloads one of the two operators, it must also overload another one.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="bedb1-138">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="bedb1-138">C# language specification</span></span>

<span data-ttu-id="bedb1-139">Aby uzyskać więcej informacji, zobacz [relacyjne i typ testowania operatorów](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) sekcji [specyfikacji języka C#.](~/_csharplang/spec/introduction.md)</span><span class="sxs-lookup"><span data-stu-id="bedb1-139">For more information, see the [Relational and type-testing operators](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="bedb1-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bedb1-140">See also</span></span>

- [<span data-ttu-id="bedb1-141">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="bedb1-141">C# reference</span></span>](../index.md)
- [<span data-ttu-id="bedb1-142">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="bedb1-142">C# operators</span></span>](index.md)
- <xref:System.IEquatable%601?displayProperty=nameWithType>
- <xref:System.Object.Equals%2A?displayProperty=nameWithType>
- <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType>
- [<span data-ttu-id="bedb1-143">Porównywanie równości</span><span class="sxs-lookup"><span data-stu-id="bedb1-143">Equality comparisons</span></span>](../../programming-guide/statements-expressions-operators/equality-comparisons.md)
- [<span data-ttu-id="bedb1-144">Operatory porównania</span><span class="sxs-lookup"><span data-stu-id="bedb1-144">Comparison operators</span></span>](comparison-operators.md)
