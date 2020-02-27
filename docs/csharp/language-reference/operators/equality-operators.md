---
title: Operatory równości — C# odwołanie
description: Dowiedz C# się więcej na temat C# operatorów porównania równości i równości typów.
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
ms.openlocfilehash: 578413b053fc1daab0c3162d9032f4d64d3e470d
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626701"
---
# <a name="equality-operators-c-reference"></a><span data-ttu-id="29aa5-103">Operatory równości (C# odwołanie)</span><span class="sxs-lookup"><span data-stu-id="29aa5-103">Equality operators (C# reference)</span></span>

<span data-ttu-id="29aa5-104">Operatory [`==` (równość)](#equality-operator-) i [`!=` (nierówność)](#inequality-operator-) sprawdzają, czy ich operandy są równe, czy nie.</span><span class="sxs-lookup"><span data-stu-id="29aa5-104">The [`==` (equality)](#equality-operator-) and [`!=` (inequality)](#inequality-operator-) operators check if their operands are equal or not.</span></span>

## <a name="equality-operator-"></a><span data-ttu-id="29aa5-105">Operator równości = =</span><span class="sxs-lookup"><span data-stu-id="29aa5-105">Equality operator ==</span></span>

<span data-ttu-id="29aa5-106">Operator równości `==` zwraca `true`, jeśli jego operandy są równe, `false` w przeciwnym razie.</span><span class="sxs-lookup"><span data-stu-id="29aa5-106">The equality operator `==` returns `true` if its operands are equal, `false` otherwise.</span></span>

### <a name="value-types-equality"></a><span data-ttu-id="29aa5-107">Równość typów wartości</span><span class="sxs-lookup"><span data-stu-id="29aa5-107">Value types equality</span></span>

<span data-ttu-id="29aa5-108">Argumenty operacji [wbudowanych typów wartości](../builtin-types/value-types.md#built-in-value-types) są równe, jeśli ich wartości są równe:</span><span class="sxs-lookup"><span data-stu-id="29aa5-108">Operands of the [built-in value types](../builtin-types/value-types.md#built-in-value-types) are equal if their values are equal:</span></span>

[!code-csharp-interactive[value types equality](~/samples/csharp/language-reference/operators/EqualityOperators.cs#ValueTypesEquality)]

> [!NOTE]
> <span data-ttu-id="29aa5-109">Dla operatorów `==`, [`<`, `>`, `<=`i `>=`](comparison-operators.md) , jeśli którykolwiek z operandów nie jest liczbą (<xref:System.Double.NaN?displayProperty=nameWithType> lub <xref:System.Single.NaN?displayProperty=nameWithType>), wynik operacji jest `false`.</span><span class="sxs-lookup"><span data-stu-id="29aa5-109">For the `==`, [`<`, `>`, `<=`, and `>=`](comparison-operators.md) operators, if any of the operands is not a number (<xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType>), the result of operation is `false`.</span></span> <span data-ttu-id="29aa5-110">Oznacza to, że wartość `NaN` nie może być większa niż ani równa żadnej innej wartości `double` (lub `float`), w tym `NaN`.</span><span class="sxs-lookup"><span data-stu-id="29aa5-110">That means that the `NaN` value is neither greater than, less than, nor equal to any other `double` (or `float`) value, including `NaN`.</span></span> <span data-ttu-id="29aa5-111">Aby uzyskać więcej informacji i przykładów, zobacz artykuł <xref:System.Double.NaN?displayProperty=nameWithType> lub <xref:System.Single.NaN?displayProperty=nameWithType> Reference.</span><span class="sxs-lookup"><span data-stu-id="29aa5-111">For more information and examples, see the <xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType> reference article.</span></span>

<span data-ttu-id="29aa5-112">Dwa operandy tego samego typu [wyliczeniowego](../builtin-types/enum.md) są równe, jeśli odpowiadające wartości bazowego typu całkowitego są równe.</span><span class="sxs-lookup"><span data-stu-id="29aa5-112">Two operands of the same [enum](../builtin-types/enum.md) type are equal if the corresponding values of the underlying integral type are equal.</span></span>

<span data-ttu-id="29aa5-113">Zdefiniowane przez użytkownika typy [struktur](../builtin-types/struct.md) nie obsługują domyślnie operatora `==`.</span><span class="sxs-lookup"><span data-stu-id="29aa5-113">User-defined [struct](../builtin-types/struct.md) types don't support the `==` operator by default.</span></span> <span data-ttu-id="29aa5-114">Aby zapewnić obsługę operatora `==`, struktura zdefiniowana przez użytkownika musi [przeciążać](operator-overloading.md) ją.</span><span class="sxs-lookup"><span data-stu-id="29aa5-114">To support the `==` operator, a user-defined struct must [overload](operator-overloading.md) it.</span></span>

<span data-ttu-id="29aa5-115">Począwszy od C# 7,3 operatory `==` i `!=` są obsługiwane przez C# [krotki](../../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="29aa5-115">Beginning with C# 7.3, the `==` and `!=` operators are supported by C# [tuples](../../tuples.md).</span></span> <span data-ttu-id="29aa5-116">Aby uzyskać więcej informacji, zobacz sekcję [równości i krotek](../../tuples.md#equality-and-tuples) w artykule [ C# typy krotek](../../tuples.md) .</span><span class="sxs-lookup"><span data-stu-id="29aa5-116">For more information, see the [Equality and tuples](../../tuples.md#equality-and-tuples) section of the [C# tuple types](../../tuples.md) article.</span></span>

### <a name="reference-types-equality"></a><span data-ttu-id="29aa5-117">Równość typów referencyjnych</span><span class="sxs-lookup"><span data-stu-id="29aa5-117">Reference types equality</span></span>

<span data-ttu-id="29aa5-118">Domyślnie dwa operandy typu odwołania są równe, jeśli odwołują się do tego samego obiektu:</span><span class="sxs-lookup"><span data-stu-id="29aa5-118">By default, two reference-type operands are equal if they refer to the same object:</span></span>

[!code-csharp[reference type equality](~/samples/csharp/language-reference/operators/EqualityOperators.cs#ReferenceTypesEquality)]

<span data-ttu-id="29aa5-119">Jak pokazano na przykładzie, zdefiniowane przez użytkownika typy odwołań domyślnie obsługują operator `==`.</span><span class="sxs-lookup"><span data-stu-id="29aa5-119">As the example shows, user-defined reference types support the `==` operator by default.</span></span> <span data-ttu-id="29aa5-120">Jednak typ referencyjny może przeciążać operator `==`.</span><span class="sxs-lookup"><span data-stu-id="29aa5-120">However, a reference type can overload the `==` operator.</span></span> <span data-ttu-id="29aa5-121">Jeśli typ referencyjny przeciąża operator `==`, użyj metody <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType>, aby sprawdzić, czy dwa odwołania tego typu odwołują się do tego samego obiektu.</span><span class="sxs-lookup"><span data-stu-id="29aa5-121">If a reference type overloads the `==` operator, use the <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> method to check if two references of that type refer to the same object.</span></span>

### <a name="string-equality"></a><span data-ttu-id="29aa5-122">Równość ciągów</span><span class="sxs-lookup"><span data-stu-id="29aa5-122">String equality</span></span>

<span data-ttu-id="29aa5-123">Dwa operandy [ciągu](../builtin-types/reference-types.md#the-string-type) są równe, gdy oba z nich są `null` lub oba wystąpienia ciągu mają taką samą długość i mają identyczne znaki w każdej pozycji znaku:</span><span class="sxs-lookup"><span data-stu-id="29aa5-123">Two [string](../builtin-types/reference-types.md#the-string-type) operands are equal when both of them are `null` or both string instances are of the same length and have identical characters in each character position:</span></span>

[!code-csharp-interactive[string equality](~/samples/csharp/language-reference/operators/EqualityOperators.cs#StringEquality)]

<span data-ttu-id="29aa5-124">Jest to porównanie porządkowe z uwzględnieniem wielkości liter.</span><span class="sxs-lookup"><span data-stu-id="29aa5-124">That is a case-sensitive ordinal comparison.</span></span> <span data-ttu-id="29aa5-125">Aby uzyskać więcej informacji na temat porównywania ciągów, zobacz [Jak porównać C#ciągi w ](../../how-to/compare-strings.md).</span><span class="sxs-lookup"><span data-stu-id="29aa5-125">For more information about string comparison, see [How to compare strings in C#](../../how-to/compare-strings.md).</span></span>

### <a name="delegate-equality"></a><span data-ttu-id="29aa5-126">Równość delegowania</span><span class="sxs-lookup"><span data-stu-id="29aa5-126">Delegate equality</span></span>

<span data-ttu-id="29aa5-127">Dwa operandy [delegatów](../../programming-guide/delegates/index.md) tego samego typu środowiska uruchomieniowego są równe, gdy oba z nich są `null` lub ich listy wywołań są o tej samej długości i mają równe wpisy w każdej pozycji:</span><span class="sxs-lookup"><span data-stu-id="29aa5-127">Two [delegate](../../programming-guide/delegates/index.md) operands of the same runtime type are equal when both of them are `null` or their invocation lists are of the same length and have equal entries in each position:</span></span>

[!code-csharp-interactive[delegate equality](~/samples/csharp/language-reference/operators/EqualityOperators.cs#DelegateEquality)]

<span data-ttu-id="29aa5-128">Aby uzyskać więcej informacji, zobacz sekcję [delegowanie operatorów równości](~/_csharplang/spec/expressions.md#delegate-equality-operators) w [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="29aa5-128">For more information, see the [Delegate equality operators](~/_csharplang/spec/expressions.md#delegate-equality-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="29aa5-129">Delegaty wytwarzane z oceny semantycznie identycznych [wyrażeń lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) nie są równe, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="29aa5-129">Delegates that are produced from evaluation of semantically identical [lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md) are not equal, as the following example shows:</span></span>

[!code-csharp-interactive[from identical lambdas](~/samples/csharp/language-reference/operators/EqualityOperators.cs#IdenticalLambdas)]

## <a name="inequality-operator-"></a><span data-ttu-id="29aa5-130">Operator nierówności! =</span><span class="sxs-lookup"><span data-stu-id="29aa5-130">Inequality operator !=</span></span>

<span data-ttu-id="29aa5-131">Operator nierówności `!=` zwraca `true`, jeśli jego operandy nie są równe, `false` w przeciwnym razie.</span><span class="sxs-lookup"><span data-stu-id="29aa5-131">The inequality operator `!=` returns `true` if its operands are not equal, `false` otherwise.</span></span> <span data-ttu-id="29aa5-132">Dla argumentów operacji [typu wbudowanego](../builtin-types/built-in-types.md)wyrażenie `x != y` daje ten sam wynik, co `!(x == y)`wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="29aa5-132">For the operands of the [built-in types](../builtin-types/built-in-types.md), the expression `x != y` produces the same result as the expression `!(x == y)`.</span></span> <span data-ttu-id="29aa5-133">Aby uzyskać więcej informacji na temat równości typów, zobacz sekcję [operator równości](#equality-operator-) .</span><span class="sxs-lookup"><span data-stu-id="29aa5-133">For more information about type equality, see the [Equality operator](#equality-operator-) section.</span></span>

<span data-ttu-id="29aa5-134">Poniższy przykład ilustruje użycie operatora `!=`:</span><span class="sxs-lookup"><span data-stu-id="29aa5-134">The following example demonstrates the usage of the `!=` operator:</span></span>

[!code-csharp-interactive[non-equality examples](~/samples/csharp/language-reference/operators/EqualityOperators.cs#NonEquality)]

## <a name="operator-overloadability"></a><span data-ttu-id="29aa5-135">Przeciążanie operatora</span><span class="sxs-lookup"><span data-stu-id="29aa5-135">Operator overloadability</span></span>

<span data-ttu-id="29aa5-136">Typ zdefiniowany przez użytkownika może [przeciążać](operator-overloading.md) operatory `==` i `!=`.</span><span class="sxs-lookup"><span data-stu-id="29aa5-136">A user-defined type can [overload](operator-overloading.md) the `==` and `!=` operators.</span></span> <span data-ttu-id="29aa5-137">Jeśli typ przeciąża jeden z dwóch operatorów, musi również przeciążać inny.</span><span class="sxs-lookup"><span data-stu-id="29aa5-137">If a type overloads one of the two operators, it must also overload another one.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="29aa5-138">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="29aa5-138">C# language specification</span></span>

<span data-ttu-id="29aa5-139">Aby uzyskać więcej informacji, zobacz sekcję [Operatory relacyjne i testowe typu](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) w [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="29aa5-139">For more information, see the [Relational and type-testing operators](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="29aa5-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="29aa5-140">See also</span></span>

- [<span data-ttu-id="29aa5-141">C#odwoła</span><span class="sxs-lookup"><span data-stu-id="29aa5-141">C# reference</span></span>](../index.md)
- [<span data-ttu-id="29aa5-142">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="29aa5-142">C# operators</span></span>](index.md)
- <xref:System.IEquatable%601?displayProperty=nameWithType>
- <xref:System.Object.Equals%2A?displayProperty=nameWithType>
- <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType>
- [<span data-ttu-id="29aa5-143">Porównania równości</span><span class="sxs-lookup"><span data-stu-id="29aa5-143">Equality comparisons</span></span>](../../programming-guide/statements-expressions-operators/equality-comparisons.md)
- [<span data-ttu-id="29aa5-144">Operatory porównania</span><span class="sxs-lookup"><span data-stu-id="29aa5-144">Comparison operators</span></span>](comparison-operators.md)
