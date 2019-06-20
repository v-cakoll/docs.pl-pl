---
title: Operatory porównania — C# odwołania
description: Dowiedz się więcej o C# operatory porównania równości.
ms.date: 03/28/2019
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
ms.openlocfilehash: f60d62d1823a8bd06b0417638719a81e95d7438b
ms.sourcegitcommit: 4c41ec195caf03d98b7900007c3c8e24eba20d34
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/20/2019
ms.locfileid: "67267701"
---
# <a name="equality-operators-c-reference"></a><span data-ttu-id="f5733-103">Operatory porównania (C# odwołania)</span><span class="sxs-lookup"><span data-stu-id="f5733-103">Equality operators (C# reference)</span></span>

<span data-ttu-id="f5733-104">[ `==` (Równości)](#equality-operator-) i [ `!=` (nierówność)](#inequality-operator-) operatorów, sprawdź, czy operandy są równe.</span><span class="sxs-lookup"><span data-stu-id="f5733-104">The [`==` (equality)](#equality-operator-) and [`!=` (inequality)](#inequality-operator-) operators check if their operands are equal or not.</span></span>

## <a name="equality-operator-"></a><span data-ttu-id="f5733-105">Operator równości ==</span><span class="sxs-lookup"><span data-stu-id="f5733-105">Equality operator ==</span></span>

<span data-ttu-id="f5733-106">Operator równości `==` zwraca `true` jego operandy są równe, `false` inaczej.</span><span class="sxs-lookup"><span data-stu-id="f5733-106">The equality operator `==` returns `true` if its operands are equal, `false` otherwise.</span></span>

### <a name="value-types-equality"></a><span data-ttu-id="f5733-107">Równość typów wartości</span><span class="sxs-lookup"><span data-stu-id="f5733-107">Value types equality</span></span>

<span data-ttu-id="f5733-108">Argumenty operacji [typy wbudowane wartości](../keywords/value-types-table.md) są takie same, jeśli ich wartości są równe:</span><span class="sxs-lookup"><span data-stu-id="f5733-108">Operands of the [built-in value types](../keywords/value-types-table.md) are equal if their values are equal:</span></span>

[!code-csharp-interactive[value types equality](~/samples/csharp/language-reference/operators/EqualityOperators.cs#ValueTypesEquality)]

> [!NOTE]
> <span data-ttu-id="f5733-109">Aby uzyskać `==`, [ `<`, `>`, `<=`, i `>=` ](comparison-operators.md) operatorów, jeśli dowolny z argumentów nie jest liczbą (<xref:System.Double.NaN?displayProperty=nameWithType> lub <xref:System.Single.NaN?displayProperty=nameWithType>), wynik operacji jest `false`.</span><span class="sxs-lookup"><span data-stu-id="f5733-109">For the `==`, [`<`, `>`, `<=`, and `>=`](comparison-operators.md) operators, if any of the operands is not a number (<xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType>), the result of operation is `false`.</span></span> <span data-ttu-id="f5733-110">Oznacza to, że `NaN` wartość jest większe niż, mniejsze ani równy do żadnej innej `double` (lub `float`) wartość, tym `NaN`.</span><span class="sxs-lookup"><span data-stu-id="f5733-110">That means that the `NaN` value is neither greater than, less than, nor equal to any other `double` (or `float`) value, including `NaN`.</span></span> <span data-ttu-id="f5733-111">Aby uzyskać więcej informacji i przykładów, zobacz <xref:System.Double.NaN?displayProperty=nameWithType> lub <xref:System.Single.NaN?displayProperty=nameWithType> artykule dotyczącym struktury.</span><span class="sxs-lookup"><span data-stu-id="f5733-111">For more information and examples, see the <xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType> reference article.</span></span>

<span data-ttu-id="f5733-112">Dwóch argumentów operacji tego samego [wyliczenia](../keywords/enum.md) typu są takie same, jeśli odpowiednie wartości typu całkowitego podstawowej są równe.</span><span class="sxs-lookup"><span data-stu-id="f5733-112">Two operands of the same [enum](../keywords/enum.md) type are equal if the corresponding values of the underlying integral type are equal.</span></span>

<span data-ttu-id="f5733-113">Zdefiniowane przez użytkownika [struktury](../keywords/struct.md) typów nie obsługują `==` operator domyślnie.</span><span class="sxs-lookup"><span data-stu-id="f5733-113">User-defined [struct](../keywords/struct.md) types don't support the `==` operator by default.</span></span> <span data-ttu-id="f5733-114">Do obsługi `==` musi struktury zdefiniowany przez użytkownika operatora [przeciążenia](#operator-overloadability) go.</span><span class="sxs-lookup"><span data-stu-id="f5733-114">To support the `==` operator, a user-defined struct must [overload](#operator-overloadability) it.</span></span>

<span data-ttu-id="f5733-115">Począwszy od C# 7.3, `==` i `!=` operatory są obsługiwane przez C# [krotek](../../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="f5733-115">Beginning with C# 7.3, the `==` and `!=` operators are supported by C# [tuples](../../tuples.md).</span></span> <span data-ttu-id="f5733-116">Aby uzyskać więcej informacji, zobacz [równości i krotek](../../tuples.md#equality-and-tuples) części [ C# typy krotki](../../tuples.md) artykułu.</span><span class="sxs-lookup"><span data-stu-id="f5733-116">For more information, see the [Equality and tuples](../../tuples.md#equality-and-tuples) section of the [C# tuple types](../../tuples.md) article.</span></span>

### <a name="string-equality"></a><span data-ttu-id="f5733-117">Ciąg znaków równości</span><span class="sxs-lookup"><span data-stu-id="f5733-117">String equality</span></span>

<span data-ttu-id="f5733-118">Dwa [ciąg](../keywords/string.md) operandy są takie same w przypadku, gdy obie z nich są `null` lub oba wystąpienia ciągu mają tę samą długość i mają identyczne znaki w każdym znaku na pozycji:</span><span class="sxs-lookup"><span data-stu-id="f5733-118">Two [string](../keywords/string.md) operands are equal when both of them are `null` or both string instances are of the same length and have identical characters in each character position:</span></span>

[!code-csharp-interactive[string equality](~/samples/csharp/language-reference/operators/EqualityOperators.cs#StringEquality)]

<span data-ttu-id="f5733-119">To porównanie porządkowe uwzględniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="f5733-119">That is case-sensitive ordinal comparison.</span></span> <span data-ttu-id="f5733-120">Aby uzyskać więcej informacji na temat porównania ciągów, zobacz [sposób porównywania ciągów w C# ](../../how-to/compare-strings.md).</span><span class="sxs-lookup"><span data-stu-id="f5733-120">For more information about string comparison, see [How to compare strings in C#](../../how-to/compare-strings.md).</span></span>

### <a name="reference-types-equality"></a><span data-ttu-id="f5733-121">Równość typów odwołań</span><span class="sxs-lookup"><span data-stu-id="f5733-121">Reference types equality</span></span>

<span data-ttu-id="f5733-122">Dwie inne niż `string` operandy typu odwołania są równe, gdy odnoszą się do tego samego obiektu:</span><span class="sxs-lookup"><span data-stu-id="f5733-122">Two other than `string` reference type operands are equal when they refer to the same object:</span></span>

[!code-csharp[reference type equality](~/samples/csharp/language-reference/operators/EqualityOperators.cs#ReferenceTypesEquality)]

<span data-ttu-id="f5733-123">Jak pokazano w przykładzie, odwołanie do zdefiniowanych przez użytkownika typy obsługi `==` operator domyślnie.</span><span class="sxs-lookup"><span data-stu-id="f5733-123">As the example shows, user-defined reference types support the `==` operator by default.</span></span> <span data-ttu-id="f5733-124">Jednakże, typ odwołania zdefiniowane przez użytkownika może doprowadzić do przeciążenia `==` operatora.</span><span class="sxs-lookup"><span data-stu-id="f5733-124">However, a user-defined reference type can overload the `==` operator.</span></span> <span data-ttu-id="f5733-125">Jeśli typ referencyjny przeciążenia `==` operatora, użyj <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> metodę sprawdzania, jeśli dwa odwołania do tego typu odnoszą się do tego samego obiektu.</span><span class="sxs-lookup"><span data-stu-id="f5733-125">If a reference type overloads the `==` operator, use the <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> method to check if two references of that type refer to the same object.</span></span>

## <a name="inequality-operator-"></a><span data-ttu-id="f5733-126">Operator nierówności! =</span><span class="sxs-lookup"><span data-stu-id="f5733-126">Inequality operator !=</span></span>

<span data-ttu-id="f5733-127">Operator nierówności `!=` zwraca `true` argumentów nie są równe, `false` inaczej.</span><span class="sxs-lookup"><span data-stu-id="f5733-127">The inequality operator `!=` returns `true` if its operands are not equal, `false` otherwise.</span></span> <span data-ttu-id="f5733-128">Dla argumentów operacji [wbudowanych typów](../keywords/built-in-types-table.md), wyrażenie `x != y` daje ten sam wynik jako wyrażenie `!(x == y)`.</span><span class="sxs-lookup"><span data-stu-id="f5733-128">For the operands of the [built-in types](../keywords/built-in-types-table.md), the expression `x != y` produces the same result as the expression `!(x == y)`.</span></span> <span data-ttu-id="f5733-129">Aby uzyskać więcej informacji na temat typu równości zobacz [operatora równości](#equality-operator-) sekcji.</span><span class="sxs-lookup"><span data-stu-id="f5733-129">For more information about type equality, see the [Equality operator](#equality-operator-) section.</span></span>

<span data-ttu-id="f5733-130">W poniższym przykładzie pokazano użycie `!=` operator:</span><span class="sxs-lookup"><span data-stu-id="f5733-130">The following example demonstrates the usage of the `!=` operator:</span></span>

[!code-csharp-interactive[non-equality examples](~/samples/csharp/language-reference/operators/EqualityOperators.cs#NonEquality)]

## <a name="operator-overloadability"></a><span data-ttu-id="f5733-131">Overloadability — operator</span><span class="sxs-lookup"><span data-stu-id="f5733-131">Operator overloadability</span></span>

<span data-ttu-id="f5733-132">Typ zdefiniowany przez użytkownika może [przeciążenia](../keywords/operator.md) `==` i `!=` operatorów.</span><span class="sxs-lookup"><span data-stu-id="f5733-132">A user-defined type can [overload](../keywords/operator.md) the `==` and `!=` operators.</span></span> <span data-ttu-id="f5733-133">Jeśli typem przeciążeń, jeden z dwóch operatorów on także przeciążać inny.</span><span class="sxs-lookup"><span data-stu-id="f5733-133">If a type overloads one of the two operators, it must also overload another one.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="f5733-134">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="f5733-134">C# language specification</span></span>

<span data-ttu-id="f5733-135">Aby uzyskać więcej informacji, zobacz [relacyjne i badania typu operatory](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) części [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="f5733-135">For more information, see the [Relational and type-testing operators](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f5733-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f5733-136">See also</span></span>

- [<span data-ttu-id="f5733-137">C#Odwołanie</span><span class="sxs-lookup"><span data-stu-id="f5733-137">C# reference</span></span>](../index.md)
- [<span data-ttu-id="f5733-138">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="f5733-138">C# operators</span></span>](index.md)
- <xref:System.IEquatable%601?displayProperty=nameWithType>
- <xref:System.Object.Equals%2A?displayProperty=nameWithType>
- <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType>
- [<span data-ttu-id="f5733-139">Porównywanie równości</span><span class="sxs-lookup"><span data-stu-id="f5733-139">Equality comparisons</span></span>](../../programming-guide/statements-expressions-operators/equality-comparisons.md)
- [<span data-ttu-id="f5733-140">Operatory porównania</span><span class="sxs-lookup"><span data-stu-id="f5733-140">Comparison operators</span></span>](comparison-operators.md)
