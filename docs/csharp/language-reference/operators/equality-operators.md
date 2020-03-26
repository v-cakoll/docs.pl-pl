---
title: Operatory równości — odwołanie do języka C#
description: Dowiedz się więcej o operatorach porównania równości języka C# i równości typu C#.
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
ms.openlocfilehash: 7dd3e544dc03fb94577892b42aecd1a15a6621ac
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80110922"
---
# <a name="equality-operators-c-reference"></a><span data-ttu-id="a58f6-103">Operatory równości (odwołanie do języka C#)</span><span class="sxs-lookup"><span data-stu-id="a58f6-103">Equality operators (C# reference)</span></span>

<span data-ttu-id="a58f6-104">Operatorzy [ `==` (równości)](#equality-operator-) i [ `!=` (nierówności)](#inequality-operator-) sprawdzają, czy ich argumenty są równe, czy nie.</span><span class="sxs-lookup"><span data-stu-id="a58f6-104">The [`==` (equality)](#equality-operator-) and [`!=` (inequality)](#inequality-operator-) operators check if their operands are equal or not.</span></span>

## <a name="equality-operator-"></a><span data-ttu-id="a58f6-105">Operator równości ==</span><span class="sxs-lookup"><span data-stu-id="a58f6-105">Equality operator ==</span></span>

<span data-ttu-id="a58f6-106">Operator `==` równości `true` zwraca, jeśli jego argumenty `false` są równe, w przeciwnym razie.</span><span class="sxs-lookup"><span data-stu-id="a58f6-106">The equality operator `==` returns `true` if its operands are equal, `false` otherwise.</span></span>

### <a name="value-types-equality"></a><span data-ttu-id="a58f6-107">Równość typów wartości</span><span class="sxs-lookup"><span data-stu-id="a58f6-107">Value types equality</span></span>

<span data-ttu-id="a58f6-108">Argumenty [wbudowanych typów wartości](../builtin-types/value-types.md#built-in-value-types) są równe, jeśli ich wartości są równe:</span><span class="sxs-lookup"><span data-stu-id="a58f6-108">Operands of the [built-in value types](../builtin-types/value-types.md#built-in-value-types) are equal if their values are equal:</span></span>

[!code-csharp-interactive[value types equality](snippets/EqualityOperators.cs#ValueTypesEquality)]

> [!NOTE]
> <span data-ttu-id="a58f6-109">Dla `==`, [ `<` `>`, `<=`, `>=` i](comparison-operators.md) operatorów, jeśli którykolwiek z<xref:System.Double.NaN?displayProperty=nameWithType> argumentów nie jest liczbą ( lub <xref:System.Single.NaN?displayProperty=nameWithType>), wynikiem operacji jest `false`.</span><span class="sxs-lookup"><span data-stu-id="a58f6-109">For the `==`, [`<`, `>`, `<=`, and `>=`](comparison-operators.md) operators, if any of the operands is not a number (<xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType>), the result of operation is `false`.</span></span> <span data-ttu-id="a58f6-110">Oznacza to, `NaN` że wartość nie jest większa niż, mniejsza `double` ani `float`równa żadnej `NaN`innej (lub) wartości, w tym .</span><span class="sxs-lookup"><span data-stu-id="a58f6-110">That means that the `NaN` value is neither greater than, less than, nor equal to any other `double` (or `float`) value, including `NaN`.</span></span> <span data-ttu-id="a58f6-111">Aby uzyskać więcej informacji i <xref:System.Double.NaN?displayProperty=nameWithType> <xref:System.Single.NaN?displayProperty=nameWithType> przykładów, zobacz artykuł lub odwołania.</span><span class="sxs-lookup"><span data-stu-id="a58f6-111">For more information and examples, see the <xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType> reference article.</span></span>

<span data-ttu-id="a58f6-112">Dwa argumenty tego samego typu [wyliczenia](../builtin-types/enum.md) są równe, jeśli odpowiednie wartości typu całkowitego są równe.</span><span class="sxs-lookup"><span data-stu-id="a58f6-112">Two operands of the same [enum](../builtin-types/enum.md) type are equal if the corresponding values of the underlying integral type are equal.</span></span>

<span data-ttu-id="a58f6-113">Typy [struktury](../builtin-types/struct.md) zdefiniowane przez użytkownika `==` domyślnie nie obsługują operatora.</span><span class="sxs-lookup"><span data-stu-id="a58f6-113">User-defined [struct](../builtin-types/struct.md) types don't support the `==` operator by default.</span></span> <span data-ttu-id="a58f6-114">Aby obsługiwać `==` operatora, struktura zdefiniowana przez użytkownika musi ją [przeciążyć.](operator-overloading.md)</span><span class="sxs-lookup"><span data-stu-id="a58f6-114">To support the `==` operator, a user-defined struct must [overload](operator-overloading.md) it.</span></span>

<span data-ttu-id="a58f6-115">Począwszy od języka C# 7.3, `==` i `!=` operatorów są obsługiwane przez [krotek](../../tuples.md)C# .</span><span class="sxs-lookup"><span data-stu-id="a58f6-115">Beginning with C# 7.3, the `==` and `!=` operators are supported by C# [tuples](../../tuples.md).</span></span> <span data-ttu-id="a58f6-116">Aby uzyskać więcej informacji, zobacz [równości i krotek](../../tuples.md#equality-and-tuples) sekcji [C# krotka artykułu.](../../tuples.md)</span><span class="sxs-lookup"><span data-stu-id="a58f6-116">For more information, see the [Equality and tuples](../../tuples.md#equality-and-tuples) section of the [C# tuple types](../../tuples.md) article.</span></span>

### <a name="reference-types-equality"></a><span data-ttu-id="a58f6-117">Równość typów odwołań</span><span class="sxs-lookup"><span data-stu-id="a58f6-117">Reference types equality</span></span>

<span data-ttu-id="a58f6-118">Domyślnie dwa argumenty typu odwołania są równe, jeśli odnoszą się do tego samego obiektu:</span><span class="sxs-lookup"><span data-stu-id="a58f6-118">By default, two reference-type operands are equal if they refer to the same object:</span></span>

[!code-csharp[reference type equality](snippets/EqualityOperators.cs#ReferenceTypesEquality)]

<span data-ttu-id="a58f6-119">Jak pokazano w przykładzie, typy `==` odwołań zdefiniowane przez użytkownika domyślnie obsługują operatora.</span><span class="sxs-lookup"><span data-stu-id="a58f6-119">As the example shows, user-defined reference types support the `==` operator by default.</span></span> <span data-ttu-id="a58f6-120">Jednak typ odwołania może przeciążyć `==` operatora.</span><span class="sxs-lookup"><span data-stu-id="a58f6-120">However, a reference type can overload the `==` operator.</span></span> <span data-ttu-id="a58f6-121">Jeśli typ odwołania przeciąża `==` operatora, <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> należy użyć metody, aby sprawdzić, czy dwa odwołania tego typu odnoszą się do tego samego obiektu.</span><span class="sxs-lookup"><span data-stu-id="a58f6-121">If a reference type overloads the `==` operator, use the <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> method to check if two references of that type refer to the same object.</span></span>

### <a name="string-equality"></a><span data-ttu-id="a58f6-122">Równość ciągów</span><span class="sxs-lookup"><span data-stu-id="a58f6-122">String equality</span></span>

<span data-ttu-id="a58f6-123">Dwa [ciągi](../builtin-types/reference-types.md#the-string-type) są równe, gdy `null` oba wystąpienia są lub oba wystąpienia ciągu mają taką samą długość i mają identyczne znaki w każdej pozycji znaku:</span><span class="sxs-lookup"><span data-stu-id="a58f6-123">Two [string](../builtin-types/reference-types.md#the-string-type) operands are equal when both of them are `null` or both string instances are of the same length and have identical characters in each character position:</span></span>

[!code-csharp-interactive[string equality](snippets/EqualityOperators.cs#StringEquality)]

<span data-ttu-id="a58f6-124">Jest to porównanie porządkowe z uwzględnieniem wielkości liter.</span><span class="sxs-lookup"><span data-stu-id="a58f6-124">That is a case-sensitive ordinal comparison.</span></span> <span data-ttu-id="a58f6-125">Aby uzyskać więcej informacji na temat porównywania [ciągów, zobacz Jak porównać ciągi w języku C#](../../how-to/compare-strings.md).</span><span class="sxs-lookup"><span data-stu-id="a58f6-125">For more information about string comparison, see [How to compare strings in C#](../../how-to/compare-strings.md).</span></span>

### <a name="delegate-equality"></a><span data-ttu-id="a58f6-126">Deleguj równość</span><span class="sxs-lookup"><span data-stu-id="a58f6-126">Delegate equality</span></span>

<span data-ttu-id="a58f6-127">Dwa [argumenty delegata](../../programming-guide/delegates/index.md) tego samego typu środowiska uruchomieniowego `null` są równe, gdy oba są lub ich listy wywołania są tej samej długości i mają równe wpisy w każdej pozycji:</span><span class="sxs-lookup"><span data-stu-id="a58f6-127">Two [delegate](../../programming-guide/delegates/index.md) operands of the same runtime type are equal when both of them are `null` or their invocation lists are of the same length and have equal entries in each position:</span></span>

[!code-csharp-interactive[delegate equality](snippets/EqualityOperators.cs#DelegateEquality)]

<span data-ttu-id="a58f6-128">Aby uzyskać więcej informacji, zobacz delegowania operatorów równości sekcji [specyfikacji języka języka Języka C #, zobacz](~/_csharplang/spec/introduction.md) [delegowanie operatorów równości.](~/_csharplang/spec/expressions.md#delegate-equality-operators)</span><span class="sxs-lookup"><span data-stu-id="a58f6-128">For more information, see the [Delegate equality operators](~/_csharplang/spec/expressions.md#delegate-equality-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="a58f6-129">Delegatów, które są tworzone z oceny semantycznie [identyczne wyrażenia lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) nie są równe, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="a58f6-129">Delegates that are produced from evaluation of semantically identical [lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md) are not equal, as the following example shows:</span></span>

[!code-csharp-interactive[from identical lambdas](snippets/EqualityOperators.cs#IdenticalLambdas)]

## <a name="inequality-operator-"></a><span data-ttu-id="a58f6-130">Operator nierówności !=</span><span class="sxs-lookup"><span data-stu-id="a58f6-130">Inequality operator !=</span></span>

<span data-ttu-id="a58f6-131">Operator `!=` nierówności zwraca, `true` jeśli jego argumenty nie `false` są równe, w przeciwnym razie.</span><span class="sxs-lookup"><span data-stu-id="a58f6-131">The inequality operator `!=` returns `true` if its operands are not equal, `false` otherwise.</span></span> <span data-ttu-id="a58f6-132">W przypadku argumentów [wbudowanych typów](../builtin-types/built-in-types.md)wyrażenie `x != y` daje taki sam wynik `!(x == y)`jak wyrażenie .</span><span class="sxs-lookup"><span data-stu-id="a58f6-132">For the operands of the [built-in types](../builtin-types/built-in-types.md), the expression `x != y` produces the same result as the expression `!(x == y)`.</span></span> <span data-ttu-id="a58f6-133">Aby uzyskać więcej informacji na temat równości typu, zobacz sekcję [operatora równości.](#equality-operator-)</span><span class="sxs-lookup"><span data-stu-id="a58f6-133">For more information about type equality, see the [Equality operator](#equality-operator-) section.</span></span>

<span data-ttu-id="a58f6-134">Poniższy przykład pokazuje użycie `!=` operatora:</span><span class="sxs-lookup"><span data-stu-id="a58f6-134">The following example demonstrates the usage of the `!=` operator:</span></span>

[!code-csharp-interactive[non-equality examples](snippets/EqualityOperators.cs#NonEquality)]

## <a name="operator-overloadability"></a><span data-ttu-id="a58f6-135">Przeciążenie operatora</span><span class="sxs-lookup"><span data-stu-id="a58f6-135">Operator overloadability</span></span>

<span data-ttu-id="a58f6-136">Typ zdefiniowany przez użytkownika `==` może `!=` [przeciążać](operator-overloading.md) operatorów i operatorów.</span><span class="sxs-lookup"><span data-stu-id="a58f6-136">A user-defined type can [overload](operator-overloading.md) the `==` and `!=` operators.</span></span> <span data-ttu-id="a58f6-137">Jeśli typ przeciąża jeden z dwóch operatorów, musi również przeciążyć drugi.</span><span class="sxs-lookup"><span data-stu-id="a58f6-137">If a type overloads one of the two operators, it must also overload the other one.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="a58f6-138">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="a58f6-138">C# language specification</span></span>

<span data-ttu-id="a58f6-139">Aby uzyskać więcej informacji, zobacz [relacyjne i testowania typów operatorów](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) sekcji [specyfikacji języka C#.](~/_csharplang/spec/introduction.md)</span><span class="sxs-lookup"><span data-stu-id="a58f6-139">For more information, see the [Relational and type-testing operators](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a58f6-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a58f6-140">See also</span></span>

- [<span data-ttu-id="a58f6-141">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="a58f6-141">C# reference</span></span>](../index.md)
- [<span data-ttu-id="a58f6-142">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="a58f6-142">C# operators</span></span>](index.md)
- <xref:System.IEquatable%601?displayProperty=nameWithType>
- <xref:System.Object.Equals%2A?displayProperty=nameWithType>
- <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType>
- [<span data-ttu-id="a58f6-143">Porównywanie równości</span><span class="sxs-lookup"><span data-stu-id="a58f6-143">Equality comparisons</span></span>](../../programming-guide/statements-expressions-operators/equality-comparisons.md)
- [<span data-ttu-id="a58f6-144">Operatory porównania</span><span class="sxs-lookup"><span data-stu-id="a58f6-144">Comparison operators</span></span>](comparison-operators.md)
