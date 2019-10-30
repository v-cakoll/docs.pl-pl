---
title: Operatory porównania — C# odwołanie
description: Więcej informacji C# na temat operatorów porównania, których można użyć do sprawdzenia kolejności wartości liczbowych.
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
ms.openlocfilehash: bb28e2adba896ae85b189858283376fbe3250dce
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039068"
---
# <a name="comparison-operators-c-reference"></a><span data-ttu-id="18b93-103">Operatory porównania (C# odwołanie)</span><span class="sxs-lookup"><span data-stu-id="18b93-103">Comparison operators (C# reference)</span></span>

<span data-ttu-id="18b93-104">[`<` (mniejsze niż)](#less-than-operator-), [`>` (większe niż)](#greater-than-operator-), [`<=` (mniejsze niż lub równe)](#less-than-or-equal-operator-)i [`>=` (większe niż lub równe)](#greater-than-or-equal-operator-) porównanie, znane także jako relacyjne, operatory porównują operandy.</span><span class="sxs-lookup"><span data-stu-id="18b93-104">The [`<` (less than)](#less-than-operator-), [`>` (greater than)](#greater-than-operator-), [`<=` (less than or equal)](#less-than-or-equal-operator-), and [`>=` (greater than or equal)](#greater-than-or-equal-operator-) comparison, also known as relational, operators compare their operands.</span></span> <span data-ttu-id="18b93-105">Te operatory są obsługiwane przez wszystkie typy liczbowe [całkowite](../builtin-types/integral-numeric-types.md) i [zmiennoprzecinkowe](../builtin-types/floating-point-numeric-types.md) .</span><span class="sxs-lookup"><span data-stu-id="18b93-105">Those operators are supported by all [integral](../builtin-types/integral-numeric-types.md) and [floating-point](../builtin-types/floating-point-numeric-types.md) numeric types.</span></span>

> [!NOTE]
> <span data-ttu-id="18b93-106">Dla operatorów `==`, `<`, `>`, `<=`i `>=`, jeśli którykolwiek z operandów nie jest liczbą (<xref:System.Double.NaN?displayProperty=nameWithType> lub <xref:System.Single.NaN?displayProperty=nameWithType>), wynik operacji jest `false`.</span><span class="sxs-lookup"><span data-stu-id="18b93-106">For the `==`, `<`, `>`, `<=`, and `>=` operators, if any of the operands is not a number (<xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType>), the result of operation is `false`.</span></span> <span data-ttu-id="18b93-107">Oznacza to, że wartość `NaN` nie może być większa niż ani równa żadnej innej wartości `double` (lub `float`), w tym `NaN`.</span><span class="sxs-lookup"><span data-stu-id="18b93-107">That means that the `NaN` value is neither greater than, less than, nor equal to any other `double` (or `float`) value, including `NaN`.</span></span> <span data-ttu-id="18b93-108">Aby uzyskać więcej informacji i przykładów, zobacz artykuł dotyczący odniesienia <xref:System.Double.NaN?displayProperty=nameWithType> lub <xref:System.Single.NaN?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="18b93-108">For more information and examples, see the <xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType> reference article.</span></span>

<span data-ttu-id="18b93-109">Typy wyliczeniowe obsługują również operatory porównania.</span><span class="sxs-lookup"><span data-stu-id="18b93-109">Enumeration types also support comparison operators.</span></span> <span data-ttu-id="18b93-110">Dla operandów tego samego typu [wyliczeniowego](../keywords/enum.md) , odpowiadające wartości podstawowego typu całkowitego są porównywane.</span><span class="sxs-lookup"><span data-stu-id="18b93-110">For operands of the same [enum](../keywords/enum.md) type, the corresponding values of the underlying integral type are compared.</span></span>

<span data-ttu-id="18b93-111">[Operatory`==` i `!=`](equality-operators.md) sprawdzają, czy ich operandy są równe, czy nie.</span><span class="sxs-lookup"><span data-stu-id="18b93-111">The [`==` and `!=` operators](equality-operators.md) check if their operands are equal or not.</span></span>

## <a name="less-than-operator-"></a><span data-ttu-id="18b93-112">\< operatora mniejszego niż</span><span class="sxs-lookup"><span data-stu-id="18b93-112">Less than operator \<</span></span>

<span data-ttu-id="18b93-113">Operator `<` zwraca `true`, jeśli jego argument operacji po lewej stronie jest krótszy od jego operandu po prawej stronie, `false` w przeciwnym razie:</span><span class="sxs-lookup"><span data-stu-id="18b93-113">The `<` operator returns `true` if its left-hand operand is less than its right-hand operand, `false` otherwise:</span></span>

[!code-csharp-interactive[less than example](~/samples/csharp/language-reference/operators/ComparisonOperators.cs#Less)]

## <a name="greater-than-operator-"></a><span data-ttu-id="18b93-114">Więcej niż > operatora</span><span class="sxs-lookup"><span data-stu-id="18b93-114">Greater than operator ></span></span>

<span data-ttu-id="18b93-115">Operator `>` zwraca `true`, jeśli jego argument operacji po lewej stronie jest większy niż jego prawy operand, `false` w przeciwnym razie:</span><span class="sxs-lookup"><span data-stu-id="18b93-115">The `>` operator returns `true` if its left-hand operand is greater than its right-hand operand, `false` otherwise:</span></span>

[!code-csharp-interactive[greater than example](~/samples/csharp/language-reference/operators/ComparisonOperators.cs#Greater)]

## <a name="less-than-or-equal-operator-"></a><span data-ttu-id="18b93-116">Mniejsze niż lub równe \<operatora=</span><span class="sxs-lookup"><span data-stu-id="18b93-116">Less than or equal operator \<=</span></span>

<span data-ttu-id="18b93-117">Operator `<=` zwraca `true`, jeśli jego argument operacji po lewej stronie jest mniejszy lub równy jego operandu po prawej stronie, `false` w przeciwnym razie:</span><span class="sxs-lookup"><span data-stu-id="18b93-117">The `<=` operator returns `true` if its left-hand operand is less than or equal to its right-hand operand, `false` otherwise:</span></span>

[!code-csharp-interactive[less than or equal example](~/samples/csharp/language-reference/operators/ComparisonOperators.cs#LessOrEqual)]

## <a name="greater-than-or-equal-operator-"></a><span data-ttu-id="18b93-118">Większe niż lub równe > operatora =</span><span class="sxs-lookup"><span data-stu-id="18b93-118">Greater than or equal operator >=</span></span>

<span data-ttu-id="18b93-119">Operator `>=` zwraca `true`, jeśli jego argument operacji po lewej stronie jest większy lub równy jego operandu po prawej stronie, `false` w przeciwnym razie:</span><span class="sxs-lookup"><span data-stu-id="18b93-119">The `>=` operator returns `true` if its left-hand operand is greater than or equal to its right-hand operand, `false` otherwise:</span></span>

[!code-csharp-interactive[greater than or equal example](~/samples/csharp/language-reference/operators/ComparisonOperators.cs#GreaterOrEqual)]

## <a name="operator-overloadability"></a><span data-ttu-id="18b93-120">Przeciążanie operatora</span><span class="sxs-lookup"><span data-stu-id="18b93-120">Operator overloadability</span></span>

<span data-ttu-id="18b93-121">Typ zdefiniowany przez użytkownika może [przeciążać](operator-overloading.md) operatory `<`, `>`, `<=`i `>=`.</span><span class="sxs-lookup"><span data-stu-id="18b93-121">A user-defined type can [overload](operator-overloading.md) the `<`, `>`, `<=`, and `>=` operators.</span></span>

<span data-ttu-id="18b93-122">Jeśli typ przeciążenia jednego z operatorów `<` lub `>`, musi przeciążać zarówno `<`, jak i `>`.</span><span class="sxs-lookup"><span data-stu-id="18b93-122">If a type overloads one of the `<` or `>` operators, it must overload both `<` and `>`.</span></span> <span data-ttu-id="18b93-123">Jeśli typ przeciążenia jednego z operatorów `<=` lub `>=`, musi przeciążać zarówno `<=`, jak i `>=`.</span><span class="sxs-lookup"><span data-stu-id="18b93-123">If a type overloads one of the `<=` or `>=` operators, it must overload both `<=` and `>=`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="18b93-124">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="18b93-124">C# language specification</span></span>

<span data-ttu-id="18b93-125">Aby uzyskać więcej informacji, zobacz sekcję [Operatory relacyjne i testowe typu](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) w [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="18b93-125">For more information, see the [Relational and type-testing operators](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="18b93-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="18b93-126">See also</span></span>

- [<span data-ttu-id="18b93-127">C#odwoła</span><span class="sxs-lookup"><span data-stu-id="18b93-127">C# reference</span></span>](../index.md)
- [<span data-ttu-id="18b93-128">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="18b93-128">C# operators</span></span>](index.md)
- <xref:System.IComparable%601?displayProperty=nameWithType>
- [<span data-ttu-id="18b93-129">Operatory równości</span><span class="sxs-lookup"><span data-stu-id="18b93-129">Equality operators</span></span>](equality-operators.md)
