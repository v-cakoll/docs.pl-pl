---
title: == Operator — C# odwołania
ms.custom: seodec18
ms.date: 12/14/2018
f1_keywords:
- ==_CSharpKeyword
helpviewer_keywords:
- == operator [C#]
- equality operator [C#]
ms.assetid: 34c6b597-caa2-4855-a7cd-38ecdd11bd07
ms.openlocfilehash: 6d86348eefc87e847267f262141ff49e5d51faae
ms.sourcegitcommit: 3d0c29b878f00caec288dfecb3a5c959de5aa629
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2018
ms.locfileid: "53655962"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="9b2c4-102">Operator == (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="9b2c4-102">== Operator (C# Reference)</span></span>

<span data-ttu-id="9b2c4-103">Operator równości `==` zwraca `true` jego operandy są równe, `false` inaczej.</span><span class="sxs-lookup"><span data-stu-id="9b2c4-103">The equality operator `==` returns `true` if its operands are equal, `false` otherwise.</span></span>

## <a name="value-types-equality"></a><span data-ttu-id="9b2c4-104">Równość typów wartości</span><span class="sxs-lookup"><span data-stu-id="9b2c4-104">Value types equality</span></span>

<span data-ttu-id="9b2c4-105">Argumenty operacji [typy wbudowane wartości](../keywords/value-types-table.md) są takie same, jeśli ich wartości są równe:</span><span class="sxs-lookup"><span data-stu-id="9b2c4-105">Operands of the [built-in value types](../keywords/value-types-table.md) are equal if their values are equal:</span></span>

[!code-csharp-interactive[value types equality](~/samples/snippets/csharp/language-reference/operators/EqualityAndNonEqualityExamples.cs#ValueTypesEquality)]

> [!NOTE]
> <span data-ttu-id="9b2c4-106">Dla operatorów relacyjnych `==`, `>`, `<`, `>=`, i `<=`, jeśli dowolny z argumentów nie jest liczbą (<xref:System.Double.NaN?displayProperty=nameWithType> lub <xref:System.Single.NaN?displayProperty=nameWithType>) wynik operacji jest `false`.</span><span class="sxs-lookup"><span data-stu-id="9b2c4-106">For relational operators `==`, `>`, `<`, `>=`, and `<=`, if any of the operands is not a number (<xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType>) the result of operation is `false`.</span></span> <span data-ttu-id="9b2c4-107">Oznacza to, że `NaN` wartość jest większe niż, mniejsze ani równy do żadnej innej `double` (lub `float`) wartość.</span><span class="sxs-lookup"><span data-stu-id="9b2c4-107">That means that the `NaN` value is neither greater than, less than, nor equal to any other `double` (or `float`) value.</span></span> <span data-ttu-id="9b2c4-108">Aby uzyskać więcej informacji i przykładów, zobacz <xref:System.Double.NaN?displayProperty=nameWithType> lub <xref:System.Single.NaN?displayProperty=nameWithType> artykule dotyczącym struktury.</span><span class="sxs-lookup"><span data-stu-id="9b2c4-108">For more information and examples, see the <xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType> reference article.</span></span>

<span data-ttu-id="9b2c4-109">Dwóch argumentów operacji tego samego [wyliczenia](../keywords/enum.md) typu są takie same, jeśli odpowiednie wartości typu całkowitego podstawowej są równe.</span><span class="sxs-lookup"><span data-stu-id="9b2c4-109">Two operands of the same [enum](../keywords/enum.md) type are equal if the corresponding values of the underlying integral type are equal.</span></span>

<span data-ttu-id="9b2c4-110">Domyślnie `==` operator nie jest zdefiniowany dla zdefiniowanej przez użytkownika [struktury](../keywords/struct.md) typu.</span><span class="sxs-lookup"><span data-stu-id="9b2c4-110">By default, the `==` operator is not defined for a user-defined [struct](../keywords/struct.md) type.</span></span> <span data-ttu-id="9b2c4-111">Typ zdefiniowany przez użytkownika może [przeciążenia](#operator-overloadability) `==` operatora.</span><span class="sxs-lookup"><span data-stu-id="9b2c4-111">A user-defined type can [overload](#operator-overloadability) the `==` operator.</span></span>

<span data-ttu-id="9b2c4-112">Począwszy od C# 7.3, `==` i [ `!=` ](not-equal-operator.md) operatory są obsługiwane przez C# [krotek](../../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="9b2c4-112">Beginning with C# 7.3, the `==` and [`!=`](not-equal-operator.md) operators are supported by C# [tuples](../../tuples.md).</span></span> <span data-ttu-id="9b2c4-113">Aby uzyskać więcej informacji, zobacz [równości i krotek](../../tuples.md#equality-and-tuples) części [ C# typy krotki](../../tuples.md) artykułu.</span><span class="sxs-lookup"><span data-stu-id="9b2c4-113">For more information, see the [Equality and tuples](../../tuples.md#equality-and-tuples) section of the [C# tuple types](../../tuples.md) article.</span></span>

## <a name="string-equality"></a><span data-ttu-id="9b2c4-114">Ciąg znaków równości</span><span class="sxs-lookup"><span data-stu-id="9b2c4-114">String equality</span></span>

<span data-ttu-id="9b2c4-115">Dwa [ciąg](../keywords/string.md) operandy są takie same w przypadku, gdy obie z nich są `null` lub oba wystąpienia ciągu mają tę samą długość i mają identyczne znaki w każdym znaku na pozycji:</span><span class="sxs-lookup"><span data-stu-id="9b2c4-115">Two [string](../keywords/string.md) operands are equal when both of them are `null` or both string instances are of the same length and have identical characters in each character position:</span></span>

[!code-csharp-interactive[string equality](~/samples/snippets/csharp/language-reference/operators/EqualityAndNonEqualityExamples.cs#StringEquality)]

<span data-ttu-id="9b2c4-116">To porównanie porządkowe uwzględniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="9b2c4-116">That is case-sensitive ordinal comparison.</span></span> <span data-ttu-id="9b2c4-117">Aby uzyskać więcej informacji dotyczących sposobu porównywania ciągów, zobacz [sposób porównywania ciągów w C# ](../../how-to/compare-strings.md).</span><span class="sxs-lookup"><span data-stu-id="9b2c4-117">For more information about how to compare strings, see [How to compare strings in C#](../../how-to/compare-strings.md).</span></span>

## <a name="reference-types-equality"></a><span data-ttu-id="9b2c4-118">Równość typów odwołań</span><span class="sxs-lookup"><span data-stu-id="9b2c4-118">Reference types equality</span></span>

<span data-ttu-id="9b2c4-119">Dwie inne niż `string` operandy typu odwołania są równe, gdy odnoszą się do tego samego obiektu:</span><span class="sxs-lookup"><span data-stu-id="9b2c4-119">Two other than `string` reference type operands are equal when they refer to the same object:</span></span>

[!code-csharp-interactive[reference type equality](~/samples/snippets/csharp/language-reference/operators/EqualityAndNonEqualityExamples.cs#ReferenceTypesEquality)]

<span data-ttu-id="9b2c4-120">W przykładzie pokazano, że `==` operator jest obsługiwany przez typy odwołań zdefiniowanych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="9b2c4-120">The example shows that the `==` operator is supported by user-defined reference types.</span></span> <span data-ttu-id="9b2c4-121">Jednakże, typ odwołania zdefiniowane przez użytkownika może doprowadzić do przeciążenia `==` operatora.</span><span class="sxs-lookup"><span data-stu-id="9b2c4-121">However, a user-defined reference type can overload the `==` operator.</span></span> <span data-ttu-id="9b2c4-122">Jeśli typ referencyjny przeciążenia `==` operatora, użyj <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> metodę sprawdzania, jeśli dwa odwołania do tego typu odnoszą się do tego samego obiektu.</span><span class="sxs-lookup"><span data-stu-id="9b2c4-122">If a reference type overloads the `==` operator, use the <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> method to check if two references of that type refer to the same object.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="9b2c4-123">Overloadability — operator</span><span class="sxs-lookup"><span data-stu-id="9b2c4-123">Operator overloadability</span></span>

<span data-ttu-id="9b2c4-124">Typy zdefiniowane przez użytkownika może [przeciążenia](../keywords/operator.md) `==` operatora.</span><span class="sxs-lookup"><span data-stu-id="9b2c4-124">User-defined types can [overload](../keywords/operator.md) the `==` operator.</span></span> <span data-ttu-id="9b2c4-125">Jeśli typem przeciążenia operatora równości `==`, należy także przeciążyć [operator nierówności](not-equal-operator.md) `!=`.</span><span class="sxs-lookup"><span data-stu-id="9b2c4-125">If a type overloads the equality operator `==`, it must also overload the [inequality operator](not-equal-operator.md) `!=`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="9b2c4-126">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="9b2c4-126">C# language specification</span></span>

<span data-ttu-id="9b2c4-127">Aby uzyskać więcej informacji, zobacz [relacyjne i badania typu operatory](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) części [ C# specyfikacji języka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="9b2c4-127">For more information, see the [Relational and type-testing operators](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9b2c4-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9b2c4-128">See also</span></span>

- [<span data-ttu-id="9b2c4-129">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="9b2c4-129">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="9b2c4-130">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="9b2c4-130">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="9b2c4-131">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="9b2c4-131">C# Operators</span></span>](index.md)
- [<span data-ttu-id="9b2c4-132">Porównywanie równości</span><span class="sxs-lookup"><span data-stu-id="9b2c4-132">Equality comparisons</span></span>](../../programming-guide/statements-expressions-operators/equality-comparisons.md)
