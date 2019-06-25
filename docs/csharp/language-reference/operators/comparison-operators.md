---
title: Operatory porównania — C# odwołania
description: Dowiedz się więcej o C# operatorów porównania, które służy do Sprawdź kolejność wartości liczbowych.
ms.date: 04/25/2019
author: pkulikov
f1_keywords:
- <_CSharpKeyword
- '>_CSharpKeyword'
- <=_CSharpKeyword
- '>=_CSharpKeyword'
helpviewer_keywords:
- comparison operators [C#]
- relational operators [C#]
- less than operator [C#]
- < operator [C#]
- greater than operator [C#]
- '> operator [C#]'
- less than or equal to operator [C#]
- <= operator [C#]
- greater than or equal to operator [C#]
- '>= operator [C#]'
ms.openlocfilehash: 0e6edf9bcc0954bf06e76b238b2bb07dea040a9c
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2019
ms.locfileid: "67347895"
---
# <a name="comparison-operators-c-reference"></a><span data-ttu-id="93c58-103">Operatory porównania (C# odwołania)</span><span class="sxs-lookup"><span data-stu-id="93c58-103">Comparison operators (C# reference)</span></span>

<span data-ttu-id="93c58-104">[ `<` (Mniejsze niż)](#less-than-operator-), [ `>` (większe niż)](#greater-than-operator-), [ `<=` (mniejsze niż lub równe)](#less-than-or-equal-operator-), i [ `>=` () większe niż lub równe)](#greater-than-or-equal-operator-) porównania, nazywana również relacyjna, operatory porównania ich operandami.</span><span class="sxs-lookup"><span data-stu-id="93c58-104">The [`<` (less than)](#less-than-operator-), [`>` (greater than)](#greater-than-operator-), [`<=` (less than or equal)](#less-than-or-equal-operator-), and [`>=` (greater than or equal)](#greater-than-or-equal-operator-) comparison, also known as relational, operators compare their operands.</span></span> <span data-ttu-id="93c58-105">Te operatory obsługują wszystkie [całkowitego](../keywords/integral-types-table.md) i [zmiennoprzecinkowych](../keywords/floating-point-types-table.md) typów liczbowych.</span><span class="sxs-lookup"><span data-stu-id="93c58-105">Those operators support all [integral](../keywords/integral-types-table.md) and [floating-point](../keywords/floating-point-types-table.md) numeric types.</span></span>

> [!NOTE]
> <span data-ttu-id="93c58-106">Aby uzyskać `==`, `<`, `>`, `<=`, i `>=` operatorów, jeśli dowolny z argumentów nie jest liczbą (<xref:System.Double.NaN?displayProperty=nameWithType> lub <xref:System.Single.NaN?displayProperty=nameWithType>), wynik operacji jest `false`.</span><span class="sxs-lookup"><span data-stu-id="93c58-106">For the `==`, `<`, `>`, `<=`, and `>=` operators, if any of the operands is not a number (<xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType>), the result of operation is `false`.</span></span> <span data-ttu-id="93c58-107">Oznacza to, że `NaN` wartość jest większe niż, mniejsze ani równy do żadnej innej `double` (lub `float`) wartość, tym `NaN`.</span><span class="sxs-lookup"><span data-stu-id="93c58-107">That means that the `NaN` value is neither greater than, less than, nor equal to any other `double` (or `float`) value, including `NaN`.</span></span> <span data-ttu-id="93c58-108">Aby uzyskać więcej informacji i przykładów, zobacz <xref:System.Double.NaN?displayProperty=nameWithType> lub <xref:System.Single.NaN?displayProperty=nameWithType> artykule dotyczącym struktury.</span><span class="sxs-lookup"><span data-stu-id="93c58-108">For more information and examples, see the <xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType> reference article.</span></span>

<span data-ttu-id="93c58-109">Typy wyliczeniowe obsługują także operatory porównania.</span><span class="sxs-lookup"><span data-stu-id="93c58-109">Enumeration types also support comparison operators.</span></span> <span data-ttu-id="93c58-110">Dla argumentów operacji tego samego [wyliczenia](../keywords/enum.md) typu, odpowiadające im wartości typu całkowitego podstawowej są porównywane.</span><span class="sxs-lookup"><span data-stu-id="93c58-110">For operands of the same [enum](../keywords/enum.md) type, the corresponding values of the underlying integral type are compared.</span></span>

<span data-ttu-id="93c58-111">[ `==` i `!=` operatory](equality-operators.md) Sprawdź, czy operandy są równe.</span><span class="sxs-lookup"><span data-stu-id="93c58-111">The [`==` and `!=` operators](equality-operators.md) check if their operands are equal or not.</span></span>

## <a name="less-than-operator-"></a><span data-ttu-id="93c58-112">Operator mniejszości \<</span><span class="sxs-lookup"><span data-stu-id="93c58-112">Less than operator \<</span></span>

<span data-ttu-id="93c58-113">`<` Operator zwraca `true` jeśli jej argument po lewej stronie jest mniejsza niż jej prawostronny operand `false` inaczej:</span><span class="sxs-lookup"><span data-stu-id="93c58-113">The `<` operator returns `true` if its left-hand operand is less than its right-hand operand, `false` otherwise:</span></span>

[!code-csharp-interactive[less than example](~/samples/csharp/language-reference/operators/ComparisonOperators.cs#Less)]

## <a name="greater-than-operator-"></a><span data-ttu-id="93c58-114">Operator Grater than ></span><span class="sxs-lookup"><span data-stu-id="93c58-114">Greater than operator ></span></span>

<span data-ttu-id="93c58-115">`>` Operator zwraca `true` jeśli jej argument po lewej stronie jest większa niż jego prawostronny operand `false` inaczej:</span><span class="sxs-lookup"><span data-stu-id="93c58-115">The `>` operator returns `true` if its left-hand operand is greater than its right-hand operand, `false` otherwise:</span></span>

[!code-csharp-interactive[greater than example](~/samples/csharp/language-reference/operators/ComparisonOperators.cs#Greater)]

## <a name="less-than-or-equal-operator-"></a><span data-ttu-id="93c58-116">Mniejsze niż lub równe — operator \<=</span><span class="sxs-lookup"><span data-stu-id="93c58-116">Less than or equal operator \<=</span></span>

<span data-ttu-id="93c58-117">`<=` Operator zwraca `true` Jeśli argumentem operacji po lewej stronie jest mniejsza niż jej prawostronny operand `false` inaczej:</span><span class="sxs-lookup"><span data-stu-id="93c58-117">The `<=` operator returns `true` if its left-hand operand is less than or equal to its right-hand operand, `false` otherwise:</span></span>

[!code-csharp-interactive[less than or equal example](~/samples/csharp/language-reference/operators/ComparisonOperators.cs#LessOrEqual)]

## <a name="greater-than-or-equal-operator-"></a><span data-ttu-id="93c58-118">Większe lub równe — operator > =</span><span class="sxs-lookup"><span data-stu-id="93c58-118">Greater than or equal operator >=</span></span>

<span data-ttu-id="93c58-119">`>=` Operator zwraca `true` jeśli jej argument po lewej stronie jest większa lub równa jego prawostronny operand `false` inaczej:</span><span class="sxs-lookup"><span data-stu-id="93c58-119">The `>=` operator returns `true` if its left-hand operand is greater than or equal to its right-hand operand, `false` otherwise:</span></span>

[!code-csharp-interactive[greater than or equal example](~/samples/csharp/language-reference/operators/ComparisonOperators.cs#GreaterOrEqual)]

## <a name="operator-overloadability"></a><span data-ttu-id="93c58-120">Overloadability — operator</span><span class="sxs-lookup"><span data-stu-id="93c58-120">Operator overloadability</span></span>

<span data-ttu-id="93c58-121">Typ zdefiniowany przez użytkownika może [przeciążenia](../keywords/operator.md) `<`, `>`, `<=`, i `>=` operatorów.</span><span class="sxs-lookup"><span data-stu-id="93c58-121">A user-defined type can [overload](../keywords/operator.md) the `<`, `>`, `<=`, and `>=` operators.</span></span>

<span data-ttu-id="93c58-122">Jeśli typem przeciążenia, jeden z `<` lub `>` operatorów, należy przeciąża zarówno `<` i `>`.</span><span class="sxs-lookup"><span data-stu-id="93c58-122">If a type overloads one of the `<` or `>` operators, it must overload both `<` and `>`.</span></span> <span data-ttu-id="93c58-123">Jeśli typem przeciążenia, jeden z `<=` lub `>=` operatorów, należy przeciąża zarówno `<=` i `>=`.</span><span class="sxs-lookup"><span data-stu-id="93c58-123">If a type overloads one of the `<=` or `>=` operators, it must overload both `<=` and `>=`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="93c58-124">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="93c58-124">C# language specification</span></span>

<span data-ttu-id="93c58-125">Aby uzyskać więcej informacji, zobacz [relacyjne i badania typu operatory](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) części [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="93c58-125">For more information, see the [Relational and type-testing operators](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="93c58-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="93c58-126">See also</span></span>

- [<span data-ttu-id="93c58-127">C#Odwołanie</span><span class="sxs-lookup"><span data-stu-id="93c58-127">C# reference</span></span>](../index.md)
- [<span data-ttu-id="93c58-128">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="93c58-128">C# operators</span></span>](index.md)
- <xref:System.IComparable%601?displayProperty=nameWithType>
- [<span data-ttu-id="93c58-129">Operatory równości</span><span class="sxs-lookup"><span data-stu-id="93c58-129">Equality operators</span></span>](equality-operators.md)
