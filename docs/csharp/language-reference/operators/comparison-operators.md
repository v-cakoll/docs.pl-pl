---
title: Operatory porównania — odwołanie w C#
description: Więcej informacji na temat operatorów porównania języka C#, których można użyć do sprawdzenia kolejności wartości liczbowych.
ms.date: 05/11/2020
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
ms.openlocfilehash: eda039d950e4be13d9c041c8bb95b6ea773b83f6
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83207228"
---
# <a name="comparison-operators-c-reference"></a><span data-ttu-id="acc1b-103">Operatory porównania (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="acc1b-103">Comparison operators (C# reference)</span></span>

<span data-ttu-id="acc1b-104">[ `<` (Mniejsze niż)](#less-than-operator-), [ `>` (większe](#greater-than-operator-)niż), [ `<=` (mniejsze niż lub równe)](#less-than-or-equal-operator-)i [ `>=` (większe niż lub równe)](#greater-than-or-equal-operator-) porównanie, znane także jako relacyjne, operatory porównują ich operandy.</span><span class="sxs-lookup"><span data-stu-id="acc1b-104">The [`<` (less than)](#less-than-operator-), [`>` (greater than)](#greater-than-operator-), [`<=` (less than or equal)](#less-than-or-equal-operator-), and [`>=` (greater than or equal)](#greater-than-or-equal-operator-) comparison, also known as relational, operators compare their operands.</span></span> <span data-ttu-id="acc1b-105">Te operatory są obsługiwane przez wszystkie typy liczbowe [całkowite](../builtin-types/integral-numeric-types.md) i [zmiennoprzecinkowe](../builtin-types/floating-point-numeric-types.md) .</span><span class="sxs-lookup"><span data-stu-id="acc1b-105">Those operators are supported by all [integral](../builtin-types/integral-numeric-types.md) and [floating-point](../builtin-types/floating-point-numeric-types.md) numeric types.</span></span>

> [!NOTE]
> <span data-ttu-id="acc1b-106">Dla `==` operatorów, `<` , `>` , `<=` i `>=` , jeśli którykolwiek z operandów nie jest liczbą ( <xref:System.Double.NaN?displayProperty=nameWithType> lub <xref:System.Single.NaN?displayProperty=nameWithType> ), wynikiem operacji jest `false` .</span><span class="sxs-lookup"><span data-stu-id="acc1b-106">For the `==`, `<`, `>`, `<=`, and `>=` operators, if any of the operands is not a number (<xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType>), the result of operation is `false`.</span></span> <span data-ttu-id="acc1b-107">Oznacza to, że `NaN` wartość nie jest większa niż, mniejsza niż ani równa żadnej innej `double` wartości (lub `float` ), w tym `NaN` .</span><span class="sxs-lookup"><span data-stu-id="acc1b-107">That means that the `NaN` value is neither greater than, less than, nor equal to any other `double` (or `float`) value, including `NaN`.</span></span> <span data-ttu-id="acc1b-108">Aby uzyskać więcej informacji i przykładów, zobacz <xref:System.Double.NaN?displayProperty=nameWithType> <xref:System.Single.NaN?displayProperty=nameWithType> artykuł lub dokumentacja.</span><span class="sxs-lookup"><span data-stu-id="acc1b-108">For more information and examples, see the <xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType> reference article.</span></span>

<span data-ttu-id="acc1b-109">Typ [char](../builtin-types/char.md) obsługuje również operatory porównania.</span><span class="sxs-lookup"><span data-stu-id="acc1b-109">The [char](../builtin-types/char.md) type also supports comparison operators.</span></span> <span data-ttu-id="acc1b-110">W przypadku `char` operandów, odpowiednie kody znaków są porównywane.</span><span class="sxs-lookup"><span data-stu-id="acc1b-110">In the case of `char` operands, the corresponding character codes are compared.</span></span>

<span data-ttu-id="acc1b-111">Typy wyliczeniowe obsługują również operatory porównania.</span><span class="sxs-lookup"><span data-stu-id="acc1b-111">Enumeration types also support comparison operators.</span></span> <span data-ttu-id="acc1b-112">Dla operandów tego samego typu [wyliczeniowego](../builtin-types/enum.md) , odpowiadające wartości podstawowego typu całkowitego są porównywane.</span><span class="sxs-lookup"><span data-stu-id="acc1b-112">For operands of the same [enum](../builtin-types/enum.md) type, the corresponding values of the underlying integral type are compared.</span></span>

<span data-ttu-id="acc1b-113">[ `==` `!=` Operatory i](equality-operators.md) sprawdzają, czy ich operandy są równe, czy nie.</span><span class="sxs-lookup"><span data-stu-id="acc1b-113">The [`==` and `!=` operators](equality-operators.md) check if their operands are equal or not.</span></span>

## <a name="less-than-operator-"></a><span data-ttu-id="acc1b-114">Operator mniejszości\<</span><span class="sxs-lookup"><span data-stu-id="acc1b-114">Less than operator \<</span></span>

<span data-ttu-id="acc1b-115">`<`Operator zwraca `true` , jeśli jego lewy argument operacji jest mniejszy niż jego prawy operand, `false` w przeciwnym razie:</span><span class="sxs-lookup"><span data-stu-id="acc1b-115">The `<` operator returns `true` if its left-hand operand is less than its right-hand operand, `false` otherwise:</span></span>

[!code-csharp-interactive[less than example](snippets/ComparisonOperators.cs#Less)]

## <a name="greater-than-operator-"></a><span data-ttu-id="acc1b-116">Więcej niż > operatora</span><span class="sxs-lookup"><span data-stu-id="acc1b-116">Greater than operator ></span></span>

<span data-ttu-id="acc1b-117">`>`Operator zwraca `true` , jeśli jego argument operacji po lewej stronie jest większy niż jego prawy operand, `false` w przeciwnym razie:</span><span class="sxs-lookup"><span data-stu-id="acc1b-117">The `>` operator returns `true` if its left-hand operand is greater than its right-hand operand, `false` otherwise:</span></span>

[!code-csharp-interactive[greater than example](snippets/ComparisonOperators.cs#Greater)]

## <a name="less-than-or-equal-operator-"></a><span data-ttu-id="acc1b-118">Operator mniejszości lub równości\<=</span><span class="sxs-lookup"><span data-stu-id="acc1b-118">Less than or equal operator \<=</span></span>

<span data-ttu-id="acc1b-119">`<=`Operator zwraca `true` , jeśli jego lewy argument operacji jest mniejszy lub równy jego operandu po prawej stronie, `false` w przeciwnym razie:</span><span class="sxs-lookup"><span data-stu-id="acc1b-119">The `<=` operator returns `true` if its left-hand operand is less than or equal to its right-hand operand, `false` otherwise:</span></span>

[!code-csharp-interactive[less than or equal example](snippets/ComparisonOperators.cs#LessOrEqual)]

## <a name="greater-than-or-equal-operator-"></a><span data-ttu-id="acc1b-120">Większe niż lub równe >operatora =</span><span class="sxs-lookup"><span data-stu-id="acc1b-120">Greater than or equal operator >=</span></span>

<span data-ttu-id="acc1b-121">`>=`Operator zwraca `true` , jeśli jego argument operacji po lewej stronie jest większy lub równy jego operandu po prawej stronie, `false` w przeciwnym razie:</span><span class="sxs-lookup"><span data-stu-id="acc1b-121">The `>=` operator returns `true` if its left-hand operand is greater than or equal to its right-hand operand, `false` otherwise:</span></span>

[!code-csharp-interactive[greater than or equal example](snippets/ComparisonOperators.cs#GreaterOrEqual)]

## <a name="operator-overloadability"></a><span data-ttu-id="acc1b-122">Przeciążanie operatora</span><span class="sxs-lookup"><span data-stu-id="acc1b-122">Operator overloadability</span></span>

<span data-ttu-id="acc1b-123">Typ zdefiniowany przez użytkownika może [przeciążać](operator-overloading.md) `<` `>` operatory,, `<=` , i `>=` .</span><span class="sxs-lookup"><span data-stu-id="acc1b-123">A user-defined type can [overload](operator-overloading.md) the `<`, `>`, `<=`, and `>=` operators.</span></span>

<span data-ttu-id="acc1b-124">Jeśli typ przeciąża jeden z `<` `>` operatorów lub, musi przeciążać jednocześnie `<` i `>` .</span><span class="sxs-lookup"><span data-stu-id="acc1b-124">If a type overloads one of the `<` or `>` operators, it must overload both `<` and `>`.</span></span> <span data-ttu-id="acc1b-125">Jeśli typ przeciąża jeden z `<=` `>=` operatorów lub, musi przeciążać jednocześnie `<=` i `>=` .</span><span class="sxs-lookup"><span data-stu-id="acc1b-125">If a type overloads one of the `<=` or `>=` operators, it must overload both `<=` and `>=`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="acc1b-126">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="acc1b-126">C# language specification</span></span>

<span data-ttu-id="acc1b-127">Aby uzyskać więcej informacji, zobacz sekcję [Operatory relacyjne i testowe typu](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) w [specyfikacji języka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="acc1b-127">For more information, see the [Relational and type-testing operators](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="acc1b-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="acc1b-128">See also</span></span>

- [<span data-ttu-id="acc1b-129">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="acc1b-129">C# reference</span></span>](../index.md)
- [<span data-ttu-id="acc1b-130">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="acc1b-130">C# operators</span></span>](index.md)
- <xref:System.IComparable%601?displayProperty=nameWithType>
- [<span data-ttu-id="acc1b-131">Operatory równości</span><span class="sxs-lookup"><span data-stu-id="acc1b-131">Equality operators</span></span>](equality-operators.md)
