---
title: Operatory porównania — odwołanie do języka C#
description: Dowiedz się więcej o operatorach porównania języka C#, których można użyć do sprawdzenia kolejności wartości liczbowych.
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
ms.openlocfilehash: 68502205193a1fc8ab7410053e13274560ffffb0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399246"
---
# <a name="comparison-operators-c-reference"></a><span data-ttu-id="bd151-103">Operatory porównania (odwołanie do języka C#)</span><span class="sxs-lookup"><span data-stu-id="bd151-103">Comparison operators (C# reference)</span></span>

<span data-ttu-id="bd151-104">[ `<` (mniej niż)](#less-than-operator-) [ `>` (większe niż)](#greater-than-operator-), [ `<=` (mniejsze lub równe)](#less-than-or-equal-operator-)i [ `>=` (większe lub równe)](#greater-than-or-equal-operator-) porównanie, znane również jako relacyjne, operatorzy porównują swoje argumenty.</span><span class="sxs-lookup"><span data-stu-id="bd151-104">The [`<` (less than)](#less-than-operator-), [`>` (greater than)](#greater-than-operator-), [`<=` (less than or equal)](#less-than-or-equal-operator-), and [`>=` (greater than or equal)](#greater-than-or-equal-operator-) comparison, also known as relational, operators compare their operands.</span></span> <span data-ttu-id="bd151-105">Te operatory są obsługiwane przez wszystkie [typy liczbowe integralne](../builtin-types/integral-numeric-types.md) i [zmiennoprzecinkowe.](../builtin-types/floating-point-numeric-types.md)</span><span class="sxs-lookup"><span data-stu-id="bd151-105">Those operators are supported by all [integral](../builtin-types/integral-numeric-types.md) and [floating-point](../builtin-types/floating-point-numeric-types.md) numeric types.</span></span>

> [!NOTE]
> <span data-ttu-id="bd151-106">Dla `==`, `<` `>`, `<=`, `>=` i operatorów, jeśli którykolwiek z argumentów nie jest liczbą (<xref:System.Double.NaN?displayProperty=nameWithType> lub <xref:System.Single.NaN?displayProperty=nameWithType>), wynikiem działania jest `false`.</span><span class="sxs-lookup"><span data-stu-id="bd151-106">For the `==`, `<`, `>`, `<=`, and `>=` operators, if any of the operands is not a number (<xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType>), the result of operation is `false`.</span></span> <span data-ttu-id="bd151-107">Oznacza to, `NaN` że wartość nie jest większa niż, mniejsza `double` niż, ani równa żadnej innej (lub) `float`wartości, w tym `NaN`.</span><span class="sxs-lookup"><span data-stu-id="bd151-107">That means that the `NaN` value is neither greater than, less than, nor equal to any other `double` (or `float`) value, including `NaN`.</span></span> <span data-ttu-id="bd151-108">Aby uzyskać więcej informacji i <xref:System.Double.NaN?displayProperty=nameWithType> <xref:System.Single.NaN?displayProperty=nameWithType> przykładów, zobacz artykuł lub odwołanie.</span><span class="sxs-lookup"><span data-stu-id="bd151-108">For more information and examples, see the <xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType> reference article.</span></span>

<span data-ttu-id="bd151-109">Typy wyliczania obsługują również operatory porównania.</span><span class="sxs-lookup"><span data-stu-id="bd151-109">Enumeration types also support comparison operators.</span></span> <span data-ttu-id="bd151-110">W przypadku argumentów tego samego typu [wyliczenia](../builtin-types/enum.md) porównywane są odpowiednie wartości podstawowego typu integralnego.</span><span class="sxs-lookup"><span data-stu-id="bd151-110">For operands of the same [enum](../builtin-types/enum.md) type, the corresponding values of the underlying integral type are compared.</span></span>

<span data-ttu-id="bd151-111">[ `==` Operatorzy i `!=` ](equality-operators.md) sprawdzić, czy ich operandy są równe, czy nie.</span><span class="sxs-lookup"><span data-stu-id="bd151-111">The [`==` and `!=` operators](equality-operators.md) check if their operands are equal or not.</span></span>

## <a name="less-than-operator-"></a><span data-ttu-id="bd151-112">Mniej niż operator\<</span><span class="sxs-lookup"><span data-stu-id="bd151-112">Less than operator \<</span></span>

<span data-ttu-id="bd151-113">Operator `<` zwraca, `true` jeśli jego po lewej stronie operand jest `false` mniejsza niż jego prawostronny argument, w przeciwnym razie:</span><span class="sxs-lookup"><span data-stu-id="bd151-113">The `<` operator returns `true` if its left-hand operand is less than its right-hand operand, `false` otherwise:</span></span>

[!code-csharp-interactive[less than example](snippets/ComparisonOperators.cs#Less)]

## <a name="greater-than-operator-"></a><span data-ttu-id="bd151-114">Większa niż > operatora</span><span class="sxs-lookup"><span data-stu-id="bd151-114">Greater than operator ></span></span>

<span data-ttu-id="bd151-115">Operator `>` zwraca, `true` jeśli jego po lewej stronie operand jest `false` większa niż jego prawostronny operand, w przeciwnym razie:</span><span class="sxs-lookup"><span data-stu-id="bd151-115">The `>` operator returns `true` if its left-hand operand is greater than its right-hand operand, `false` otherwise:</span></span>

[!code-csharp-interactive[greater than example](snippets/ComparisonOperators.cs#Greater)]

## <a name="less-than-or-equal-operator-"></a><span data-ttu-id="bd151-116">Mniej niż lub równe operatora\<=</span><span class="sxs-lookup"><span data-stu-id="bd151-116">Less than or equal operator \<=</span></span>

<span data-ttu-id="bd151-117">Operator `<=` zwraca, `true` jeśli jego lewy argument jest mniejszy lub równy jego `false` prawostronnemu argumentowi, w przeciwnym razie:</span><span class="sxs-lookup"><span data-stu-id="bd151-117">The `<=` operator returns `true` if its left-hand operand is less than or equal to its right-hand operand, `false` otherwise:</span></span>

[!code-csharp-interactive[less than or equal example](snippets/ComparisonOperators.cs#LessOrEqual)]

## <a name="greater-than-or-equal-operator-"></a><span data-ttu-id="bd151-118">Większa lub równa >operatora =</span><span class="sxs-lookup"><span data-stu-id="bd151-118">Greater than or equal operator >=</span></span>

<span data-ttu-id="bd151-119">Operator `>=` zwraca, `true` jeśli jego lewy argument jest większy lub równy jego `false` prawostronnemu argumentowi, w przeciwnym razie:</span><span class="sxs-lookup"><span data-stu-id="bd151-119">The `>=` operator returns `true` if its left-hand operand is greater than or equal to its right-hand operand, `false` otherwise:</span></span>

[!code-csharp-interactive[greater than or equal example](snippets/ComparisonOperators.cs#GreaterOrEqual)]

## <a name="operator-overloadability"></a><span data-ttu-id="bd151-120">Przeciążenie operatora</span><span class="sxs-lookup"><span data-stu-id="bd151-120">Operator overloadability</span></span>

<span data-ttu-id="bd151-121">Typ zdefiniowany przez użytkownika `<`może `>` `<=` `>=` [przeciążyć](operator-overloading.md) , , i operatorów.</span><span class="sxs-lookup"><span data-stu-id="bd151-121">A user-defined type can [overload](operator-overloading.md) the `<`, `>`, `<=`, and `>=` operators.</span></span>

<span data-ttu-id="bd151-122">Jeśli typ przeciążenia `<` jednego `>` z operatorów, musi `<` `>`przeciążać zarówno i .</span><span class="sxs-lookup"><span data-stu-id="bd151-122">If a type overloads one of the `<` or `>` operators, it must overload both `<` and `>`.</span></span> <span data-ttu-id="bd151-123">Jeśli typ przeciążenia `<=` jednego `>=` z operatorów, musi `<=` `>=`przeciążać zarówno i .</span><span class="sxs-lookup"><span data-stu-id="bd151-123">If a type overloads one of the `<=` or `>=` operators, it must overload both `<=` and `>=`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="bd151-124">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="bd151-124">C# language specification</span></span>

<span data-ttu-id="bd151-125">Aby uzyskać więcej informacji, zobacz [relacyjne i typ testowania operatorów](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) sekcji [specyfikacji języka C#.](~/_csharplang/spec/introduction.md)</span><span class="sxs-lookup"><span data-stu-id="bd151-125">For more information, see the [Relational and type-testing operators](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="bd151-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bd151-126">See also</span></span>

- [<span data-ttu-id="bd151-127">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="bd151-127">C# reference</span></span>](../index.md)
- [<span data-ttu-id="bd151-128">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="bd151-128">C# operators</span></span>](index.md)
- <xref:System.IComparable%601?displayProperty=nameWithType>
- [<span data-ttu-id="bd151-129">Operatorzy równości</span><span class="sxs-lookup"><span data-stu-id="bd151-129">Equality operators</span></span>](equality-operators.md)
