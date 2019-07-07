---
title: Operatory logiczne logiczne - C# odwołania
description: Dowiedz się więcej o C# operatorów, które wykonują logiczna Negacja, połączeniu (oraz) i operacje włączne i wyłączne rozłączenia (lub) argumentów logicznych.
ms.date: 04/08/2019
author: pkulikov
f1_keywords:
- '!_CSharpKeyword'
- '&_CSharpKeyword'
- ^_CSharpKeyword
- '|_CSharpKeyword'
- '&&_CSharpKeyword'
- '||_CSharpKeyword'
helpviewer_keywords:
- logical operators [C#]
- short-circuiting operators [C#]
- logical negation operator [C#]
- NOT operator [C#]
- '! operator [C#]'
- AND operator [C#]
- ampersand operator [C#]
- conjunction operator [C#]
- '& operator [C#]'
- exclusive OR operator [C#]
- XOR operator [C#]
- ^ operator [C#]
- OR operator [C#]
- disjunction operator [C#]
- '| operator [C#]'
- conditional AND operator [C#]
- short-circuiting AND operator [C#]
- '&& operator [C#]'
- conditional OR operator [C#]
- short-circuiting OR operator [C#]
- '|| operator [C#]'
ms.openlocfilehash: b2c3553f527e9fec8856297c7424a081b5b31db0
ms.sourcegitcommit: eaa6d5cd0f4e7189dbe0bd756e9f53508b01989e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/07/2019
ms.locfileid: "67609927"
---
# <a name="boolean-logical-operators-c-reference"></a><span data-ttu-id="10ce2-103">Wartość logiczna operatorów logicznych (C# odwołania)</span><span class="sxs-lookup"><span data-stu-id="10ce2-103">Boolean logical operators (C# reference)</span></span>

<span data-ttu-id="10ce2-104">Następujące operatory logiczne wykonania operacji związanych z [bool](../keywords/bool.md) argumenty:</span><span class="sxs-lookup"><span data-stu-id="10ce2-104">The following operators perform logical operations with the [bool](../keywords/bool.md) operands:</span></span>

- <span data-ttu-id="10ce2-105">Jednoargumentowy [ `!` (negacja logiczna)](#logical-negation-operator-) operatora.</span><span class="sxs-lookup"><span data-stu-id="10ce2-105">Unary [`!` (logical negation)](#logical-negation-operator-) operator.</span></span>
- <span data-ttu-id="10ce2-106">Binarny [ `&` (operator logiczny oraz)](#logical-and-operator-), [ `|` (operator logiczny lub)](#logical-or-operator-), i [ `^` (logiczne OR wyłączne)](#logical-exclusive-or-operator-) operatorów.</span><span class="sxs-lookup"><span data-stu-id="10ce2-106">Binary [`&` (logical AND)](#logical-and-operator-), [`|` (logical OR)](#logical-or-operator-), and [`^` (logical exclusive OR)](#logical-exclusive-or-operator-) operators.</span></span> <span data-ttu-id="10ce2-107">Te operatory zawsze należy przeprowadzić ocenę oba operandy.</span><span class="sxs-lookup"><span data-stu-id="10ce2-107">Those operators always evaluate both operands.</span></span>
- <span data-ttu-id="10ce2-108">Binarny [ `&&` (warunkowego operator logiczny oraz)](#conditional-logical-and-operator-) i [ `||` (logiczne OR warunkowe)](#conditional-logical-or-operator-) operatorów.</span><span class="sxs-lookup"><span data-stu-id="10ce2-108">Binary [`&&` (conditional logical AND)](#conditional-logical-and-operator-) and [`||` (conditional logical OR)](#conditional-logical-or-operator-) operators.</span></span> <span data-ttu-id="10ce2-109">Te operatory ocenić prawostronny operand tylko wtedy, gdy jest to konieczne.</span><span class="sxs-lookup"><span data-stu-id="10ce2-109">Those operators evaluate the right-hand operand only if it's necessary.</span></span>

<span data-ttu-id="10ce2-110">Dla argumentów operacji [całkowitego](../builtin-types/integral-numeric-types.md) typów `&`, `|`, i `^` Operatorzy wykonywać operacje logiczne bitowe.</span><span class="sxs-lookup"><span data-stu-id="10ce2-110">For the operands of the [integral](../builtin-types/integral-numeric-types.md) types, the `&`, `|`, and `^` operators perform bitwise logical operations.</span></span> <span data-ttu-id="10ce2-111">Aby uzyskać więcej informacji, zobacz [operatory bitowe- and -shift](bitwise-and-shift-operators.md).</span><span class="sxs-lookup"><span data-stu-id="10ce2-111">For more information, see [Bitwise and shift operators](bitwise-and-shift-operators.md).</span></span>

## <a name="logical-negation-operator-"></a><span data-ttu-id="10ce2-112">Operator logiczny negacji!</span><span class="sxs-lookup"><span data-stu-id="10ce2-112">Logical negation operator !</span></span>

<span data-ttu-id="10ce2-113">`!` Operator oblicza Negacja logiczna swojego operandu.</span><span class="sxs-lookup"><span data-stu-id="10ce2-113">The `!` operator computes logical negation of its operand.</span></span> <span data-ttu-id="10ce2-114">Oznacza to, tworzy `true`, jeśli argument daje w wyniku `false`, i `false`, jeśli argument daje w wyniku `true`:</span><span class="sxs-lookup"><span data-stu-id="10ce2-114">That is, it produces `true`, if the operand evaluates to `false`, and `false`, if the operand evaluates to `true`:</span></span>

[!code-csharp-interactive[logical negation](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Negation)]

## <a name="logical-and-operator-"></a> <span data-ttu-id="10ce2-115">Operator logiczny AND &amp;</span><span class="sxs-lookup"><span data-stu-id="10ce2-115">Logical AND operator &amp;</span></span>

<span data-ttu-id="10ce2-116">`&` Operator oblicza logicznego i jego operandu.</span><span class="sxs-lookup"><span data-stu-id="10ce2-116">The `&` operator computes the logical AND of its operands.</span></span> <span data-ttu-id="10ce2-117">Wynik `x & y` jest `true` Jeśli oba `x` i `y` zwrócić `true`.</span><span class="sxs-lookup"><span data-stu-id="10ce2-117">The result of `x & y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="10ce2-118">W przeciwnym razie wynikiem jest `false`.</span><span class="sxs-lookup"><span data-stu-id="10ce2-118">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="10ce2-119">`&` Operator ocenia oba operandy nawet wtedy, gdy po lewej stronie operand ma wartość `false`, dzięki czemu wynik musi być `false` niezależnie od wartości prawostronny operand.</span><span class="sxs-lookup"><span data-stu-id="10ce2-119">The `&` operator evaluates both operands even if the left-hand operand evaluates to `false`, so that the result must be `false` regardless of the value of the right-hand operand.</span></span>

<span data-ttu-id="10ce2-120">W poniższym przykładzie prawostronny operand `&` operator jest wywołanie metody, które jest wykonywane niezależnie od wartości lewostronny operand:</span><span class="sxs-lookup"><span data-stu-id="10ce2-120">In the following example, the right-hand operand of the `&` operator is a method call, which is performed regardless of the value of the left-hand operand:</span></span>

[!code-csharp-interactive[logical AND](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#And)]

<span data-ttu-id="10ce2-121">[Warunkowego logicznego operatora AND](#conditional-logical-and-operator-) `&&` również oblicza operator logiczny oraz z argumentów, ale nie ocenia prawostronny operand, jeśli po lewej stronie operand ma wartość `false`.</span><span class="sxs-lookup"><span data-stu-id="10ce2-121">The [conditional logical AND operator](#conditional-logical-and-operator-) `&&` also computes the logical AND of its operands, but doesn't evaluate the right-hand operand if the left-hand operand evaluates to `false`.</span></span>

<span data-ttu-id="10ce2-122">Dla argumentów operacji typu całkowitoliczbowego `&` oblicza operator [iloczynu bitowego AND logiczne](bitwise-and-shift-operators.md#logical-and-operator-) z argumentów.</span><span class="sxs-lookup"><span data-stu-id="10ce2-122">For the operands of the integral types, the `&` operator computes the [bitwise logical AND](bitwise-and-shift-operators.md#logical-and-operator-) of its operands.</span></span> <span data-ttu-id="10ce2-123">Jednoargumentowy `&` operator jest [operatora address-of](pointer-related-operators.md#address-of-operator-).</span><span class="sxs-lookup"><span data-stu-id="10ce2-123">The unary `&` operator is the [address-of operator](pointer-related-operators.md#address-of-operator-).</span></span>

## <a name="logical-exclusive-or-operator-"></a><span data-ttu-id="10ce2-124">Operator logiczny OR wyłączne ^</span><span class="sxs-lookup"><span data-stu-id="10ce2-124">Logical exclusive OR operator ^</span></span>

<span data-ttu-id="10ce2-125">`^` Operator oblicza wyłącznie logiczny lub, znany także jako XOR logiczne, z argumentów.</span><span class="sxs-lookup"><span data-stu-id="10ce2-125">The `^` operator computes the logical exclusive OR, also known as the logical XOR, of its operands.</span></span> <span data-ttu-id="10ce2-126">Wynik `x ^ y` jest `true` Jeśli `x` daje w wyniku `true` i `y` daje w wyniku `false`, lub `x` daje w wyniku `false` i `y` daje w wyniku `true`.</span><span class="sxs-lookup"><span data-stu-id="10ce2-126">The result of `x ^ y` is `true` if `x` evaluates to `true` and `y` evaluates to `false`, or `x` evaluates to `false` and `y` evaluates to `true`.</span></span> <span data-ttu-id="10ce2-127">W przeciwnym razie wynikiem jest `false`.</span><span class="sxs-lookup"><span data-stu-id="10ce2-127">Otherwise, the result is `false`.</span></span> <span data-ttu-id="10ce2-128">Oznacza to aby uzyskać `bool` operandów, `^` operator oblicza ten sam wynik jako [operator nierówności](equality-operators.md#inequality-operator-) `!=`.</span><span class="sxs-lookup"><span data-stu-id="10ce2-128">That is, for the `bool` operands, the `^` operator computes the same result as the [inequality operator](equality-operators.md#inequality-operator-) `!=`.</span></span>

[!code-csharp-interactive[logical exclusive OR](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Xor)]

<span data-ttu-id="10ce2-129">Dla argumentów operacji typu całkowitoliczbowego `^` oblicza operator [bitowe wykluczające OR logiczne](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) z argumentów.</span><span class="sxs-lookup"><span data-stu-id="10ce2-129">For the operands of the integral types, the `^` operator computes the [bitwise logical exclusive OR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) of its operands.</span></span>

## <a name="logical-or-operator-"></a><span data-ttu-id="10ce2-130">Operator logiczny OR |</span><span class="sxs-lookup"><span data-stu-id="10ce2-130">Logical OR operator |</span></span>

<span data-ttu-id="10ce2-131">`|` Operator oblicza operator logiczny lub jego operandu.</span><span class="sxs-lookup"><span data-stu-id="10ce2-131">The `|` operator computes the logical OR of its operands.</span></span> <span data-ttu-id="10ce2-132">Wynik `x | y` jest `true` Jeśli `x` lub `y` daje w wyniku `true`.</span><span class="sxs-lookup"><span data-stu-id="10ce2-132">The result of `x | y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="10ce2-133">W przeciwnym razie wynikiem jest `false`.</span><span class="sxs-lookup"><span data-stu-id="10ce2-133">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="10ce2-134">`|` Operator ocenia oba operandy nawet wtedy, gdy po lewej stronie operand ma wartość `true`, dzięki czemu wynik musi być `true` niezależnie od wartości prawostronny operand.</span><span class="sxs-lookup"><span data-stu-id="10ce2-134">The `|` operator evaluates both operands even if the left-hand operand evaluates to `true`, so that the result must be `true` regardless of the value of the right-hand operand.</span></span>

<span data-ttu-id="10ce2-135">W poniższym przykładzie prawostronny operand `|` operator jest wywołanie metody, które jest wykonywane niezależnie od wartości lewostronny operand:</span><span class="sxs-lookup"><span data-stu-id="10ce2-135">In the following example, the right-hand operand of the `|` operator is a method call, which is performed regardless of the value of the left-hand operand:</span></span>

[!code-csharp-interactive[logical OR](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Or)]

<span data-ttu-id="10ce2-136">[Warunkowego logicznego operatora OR](#conditional-logical-or-operator-) `||` również oblicza logiczne OR z argumentów, ale nie ocenia prawostronny operand, jeśli po lewej stronie operand ma wartość `true`.</span><span class="sxs-lookup"><span data-stu-id="10ce2-136">The [conditional logical OR operator](#conditional-logical-or-operator-) `||` also computes the logical OR of its operands, but doesn't evaluate the right-hand operand if the left-hand operand evaluates to `true`.</span></span>

<span data-ttu-id="10ce2-137">Dla argumentów operacji typu całkowitoliczbowego `|` oblicza operator [bitowe OR logiczne](bitwise-and-shift-operators.md#logical-or-operator-) z argumentów.</span><span class="sxs-lookup"><span data-stu-id="10ce2-137">For the operands of the integral types, the `|` operator computes the [bitwise logical OR](bitwise-and-shift-operators.md#logical-or-operator-) of its operands.</span></span>

## <a name="conditional-logical-and-operator-"></a> <span data-ttu-id="10ce2-138">Operator logiczny AND warunkowe &amp;&amp;</span><span class="sxs-lookup"><span data-stu-id="10ce2-138">Conditional logical AND operator &amp;&amp;</span></span>

<span data-ttu-id="10ce2-139">Operator logiczny AND warunkowe `&&`, znany także jako "zwarcie" logicznego operatora AND, oblicza logicznego i jego operandu.</span><span class="sxs-lookup"><span data-stu-id="10ce2-139">The conditional logical AND operator `&&`, also known as the "short-circuiting" logical AND operator, computes the logical AND of its operands.</span></span> <span data-ttu-id="10ce2-140">Wynik `x && y` jest `true` Jeśli oba `x` i `y` zwrócić `true`.</span><span class="sxs-lookup"><span data-stu-id="10ce2-140">The result of `x && y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="10ce2-141">W przeciwnym razie wynikiem jest `false`.</span><span class="sxs-lookup"><span data-stu-id="10ce2-141">Otherwise, the result is `false`.</span></span> <span data-ttu-id="10ce2-142">Jeśli `x` daje w wyniku `false`, `y` nie jest oceniany.</span><span class="sxs-lookup"><span data-stu-id="10ce2-142">If `x` evaluates to `false`, `y` is not evaluated.</span></span>

<span data-ttu-id="10ce2-143">W poniższym przykładzie prawostronny operand `&&` operator jest wywołanie metody, które nie jest wykonywane, jeśli argument po lewej stronie, które daje w wyniku `false`:</span><span class="sxs-lookup"><span data-stu-id="10ce2-143">In the following example, the right-hand operand of the `&&` operator is a method call, which isn't performed if the left-hand operand evaluates to `false`:</span></span>

[!code-csharp-interactive[conditional logical AND](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#ConditionalAnd)]

<span data-ttu-id="10ce2-144">[Logicznego operatora AND](#logical-and-operator-) `&` oblicza również operator logiczny oraz z argumentów, ale zawsze ocenia oba operandy.</span><span class="sxs-lookup"><span data-stu-id="10ce2-144">The [logical AND operator](#logical-and-operator-) `&` also computes the logical AND of its operands, but always evaluates both operands.</span></span>

## <a name="conditional-logical-or-operator-"></a><span data-ttu-id="10ce2-145">Operator warunkowy OR logiczne ||</span><span class="sxs-lookup"><span data-stu-id="10ce2-145">Conditional logical OR operator ||</span></span>

<span data-ttu-id="10ce2-146">Operator logiczny OR warunkowe `||`, znany także jako "zwarcie" logicznego operatora OR, oblicza operator logiczny lub jego operandu.</span><span class="sxs-lookup"><span data-stu-id="10ce2-146">The conditional logical OR operator `||`, also known as the "short-circuiting" logical OR operator, computes the logical OR of its operands.</span></span> <span data-ttu-id="10ce2-147">Wynik `x || y` jest `true` Jeśli `x` lub `y` daje w wyniku `true`.</span><span class="sxs-lookup"><span data-stu-id="10ce2-147">The result of `x || y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="10ce2-148">W przeciwnym razie wynikiem jest `false`.</span><span class="sxs-lookup"><span data-stu-id="10ce2-148">Otherwise, the result is `false`.</span></span> <span data-ttu-id="10ce2-149">Jeśli `x` daje w wyniku `true`, `y` nie jest oceniany.</span><span class="sxs-lookup"><span data-stu-id="10ce2-149">If `x` evaluates to `true`, `y` is not evaluated.</span></span>

<span data-ttu-id="10ce2-150">W poniższym przykładzie prawostronny operand `||` operator jest wywołanie metody, które nie jest wykonywane, jeśli argument po lewej stronie, które daje w wyniku `true`:</span><span class="sxs-lookup"><span data-stu-id="10ce2-150">In the following example, the right-hand operand of the `||` operator is a method call, which isn't performed if the left-hand operand evaluates to `true`:</span></span>

[!code-csharp-interactive[conditional logical OR](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#ConditionalOr)]

<span data-ttu-id="10ce2-151">[Operator logiczny OR](#logical-or-operator-) `|` oblicza również logiczne OR z argumentów, ale zawsze ocenia oba operandy.</span><span class="sxs-lookup"><span data-stu-id="10ce2-151">The [logical OR operator](#logical-or-operator-) `|` also computes the logical OR of its operands, but always evaluates both operands.</span></span>

## <a name="nullable-boolean-logical-operators"></a><span data-ttu-id="10ce2-152">Operatory dopuszczające wartość null, Boolean i logiczne</span><span class="sxs-lookup"><span data-stu-id="10ce2-152">Nullable Boolean logical operators</span></span>

<span data-ttu-id="10ce2-153">Dla `bool?` operandów, `&` i `|` Operatorzy pomocy technicznej przechowywanymi w trzech logiki.</span><span class="sxs-lookup"><span data-stu-id="10ce2-153">For the `bool?` operands, the `&` and `|` operators support the three-valued logic.</span></span> <span data-ttu-id="10ce2-154">Semantyka te operatory jest zdefiniowane w poniższej tabeli:</span><span class="sxs-lookup"><span data-stu-id="10ce2-154">The semantics of these operators is defined by the following table:</span></span>  
  
|<span data-ttu-id="10ce2-155">x</span><span class="sxs-lookup"><span data-stu-id="10ce2-155">x</span></span>|<span data-ttu-id="10ce2-156">t</span><span class="sxs-lookup"><span data-stu-id="10ce2-156">y</span></span>|<span data-ttu-id="10ce2-157">x i y</span><span class="sxs-lookup"><span data-stu-id="10ce2-157">x&y</span></span>|<span data-ttu-id="10ce2-158">x&#124;y</span><span class="sxs-lookup"><span data-stu-id="10ce2-158">x&#124;y</span></span>|  
|----|----|----|----|  
|<span data-ttu-id="10ce2-159">true</span><span class="sxs-lookup"><span data-stu-id="10ce2-159">true</span></span>|<span data-ttu-id="10ce2-160">true</span><span class="sxs-lookup"><span data-stu-id="10ce2-160">true</span></span>|<span data-ttu-id="10ce2-161">true</span><span class="sxs-lookup"><span data-stu-id="10ce2-161">true</span></span>|<span data-ttu-id="10ce2-162">true</span><span class="sxs-lookup"><span data-stu-id="10ce2-162">true</span></span>|  
|<span data-ttu-id="10ce2-163">true</span><span class="sxs-lookup"><span data-stu-id="10ce2-163">true</span></span>|<span data-ttu-id="10ce2-164">false</span><span class="sxs-lookup"><span data-stu-id="10ce2-164">false</span></span>|<span data-ttu-id="10ce2-165">false</span><span class="sxs-lookup"><span data-stu-id="10ce2-165">false</span></span>|<span data-ttu-id="10ce2-166">true</span><span class="sxs-lookup"><span data-stu-id="10ce2-166">true</span></span>|  
|<span data-ttu-id="10ce2-167">true</span><span class="sxs-lookup"><span data-stu-id="10ce2-167">true</span></span>|<span data-ttu-id="10ce2-168">wartość null</span><span class="sxs-lookup"><span data-stu-id="10ce2-168">null</span></span>|<span data-ttu-id="10ce2-169">wartość null</span><span class="sxs-lookup"><span data-stu-id="10ce2-169">null</span></span>|<span data-ttu-id="10ce2-170">true</span><span class="sxs-lookup"><span data-stu-id="10ce2-170">true</span></span>|  
|<span data-ttu-id="10ce2-171">false</span><span class="sxs-lookup"><span data-stu-id="10ce2-171">false</span></span>|<span data-ttu-id="10ce2-172">true</span><span class="sxs-lookup"><span data-stu-id="10ce2-172">true</span></span>|<span data-ttu-id="10ce2-173">false</span><span class="sxs-lookup"><span data-stu-id="10ce2-173">false</span></span>|<span data-ttu-id="10ce2-174">true</span><span class="sxs-lookup"><span data-stu-id="10ce2-174">true</span></span>|  
|<span data-ttu-id="10ce2-175">false</span><span class="sxs-lookup"><span data-stu-id="10ce2-175">false</span></span>|<span data-ttu-id="10ce2-176">false</span><span class="sxs-lookup"><span data-stu-id="10ce2-176">false</span></span>|<span data-ttu-id="10ce2-177">false</span><span class="sxs-lookup"><span data-stu-id="10ce2-177">false</span></span>|<span data-ttu-id="10ce2-178">false</span><span class="sxs-lookup"><span data-stu-id="10ce2-178">false</span></span>|  
|<span data-ttu-id="10ce2-179">false</span><span class="sxs-lookup"><span data-stu-id="10ce2-179">false</span></span>|<span data-ttu-id="10ce2-180">wartość null</span><span class="sxs-lookup"><span data-stu-id="10ce2-180">null</span></span>|<span data-ttu-id="10ce2-181">false</span><span class="sxs-lookup"><span data-stu-id="10ce2-181">false</span></span>|<span data-ttu-id="10ce2-182">wartość null</span><span class="sxs-lookup"><span data-stu-id="10ce2-182">null</span></span>|  
|<span data-ttu-id="10ce2-183">wartość null</span><span class="sxs-lookup"><span data-stu-id="10ce2-183">null</span></span>|<span data-ttu-id="10ce2-184">true</span><span class="sxs-lookup"><span data-stu-id="10ce2-184">true</span></span>|<span data-ttu-id="10ce2-185">wartość null</span><span class="sxs-lookup"><span data-stu-id="10ce2-185">null</span></span>|<span data-ttu-id="10ce2-186">true</span><span class="sxs-lookup"><span data-stu-id="10ce2-186">true</span></span>|  
|<span data-ttu-id="10ce2-187">wartość null</span><span class="sxs-lookup"><span data-stu-id="10ce2-187">null</span></span>|<span data-ttu-id="10ce2-188">false</span><span class="sxs-lookup"><span data-stu-id="10ce2-188">false</span></span>|<span data-ttu-id="10ce2-189">false</span><span class="sxs-lookup"><span data-stu-id="10ce2-189">false</span></span>|<span data-ttu-id="10ce2-190">wartość null</span><span class="sxs-lookup"><span data-stu-id="10ce2-190">null</span></span>|  
|<span data-ttu-id="10ce2-191">wartość null</span><span class="sxs-lookup"><span data-stu-id="10ce2-191">null</span></span>|<span data-ttu-id="10ce2-192">wartość null</span><span class="sxs-lookup"><span data-stu-id="10ce2-192">null</span></span>|<span data-ttu-id="10ce2-193">wartość null</span><span class="sxs-lookup"><span data-stu-id="10ce2-193">null</span></span>|<span data-ttu-id="10ce2-194">wartość null</span><span class="sxs-lookup"><span data-stu-id="10ce2-194">null</span></span>|  

<span data-ttu-id="10ce2-195">Zachowanie tych operatorów różni się od zachowania typowe operatora z typami wartości null.</span><span class="sxs-lookup"><span data-stu-id="10ce2-195">The behavior of those operators differs from the typical operator behavior with nullable value types.</span></span> <span data-ttu-id="10ce2-196">Zazwyczaj operator, który jest zdefiniowany w przypadku argumentów operacji typu wartości również można argumentów odpowiedni typ wartości null.</span><span class="sxs-lookup"><span data-stu-id="10ce2-196">Typically, an operator which is defined for operands of a value type can be also used with operands of the corresponding nullable value type.</span></span> <span data-ttu-id="10ce2-197">Generuje taki operator `null` Jeśli którykolwiek z argumentów jest `null`.</span><span class="sxs-lookup"><span data-stu-id="10ce2-197">Such an operator produces `null` if any of its operands is `null`.</span></span> <span data-ttu-id="10ce2-198">Jednak `&` i `|` operatorów może utworzyć inną niż null, nawet jeśli jeden z argumentów jest `null`.</span><span class="sxs-lookup"><span data-stu-id="10ce2-198">However, the `&` and `|` operators can produce non-null even if one of the operands is `null`.</span></span> <span data-ttu-id="10ce2-199">Aby uzyskać więcej informacji o zachowaniu operatora z typami wartości null, zobacz [operatory](../../programming-guide/nullable-types/using-nullable-types.md#operators) części [przy użyciu typów dopuszczających wartości zerowe](../../programming-guide/nullable-types/using-nullable-types.md) artykułu.</span><span class="sxs-lookup"><span data-stu-id="10ce2-199">For more information about the operator behavior with nullable value types, see the [Operators](../../programming-guide/nullable-types/using-nullable-types.md#operators) section of the [Using nullable types](../../programming-guide/nullable-types/using-nullable-types.md) article.</span></span>

<span data-ttu-id="10ce2-200">Można również użyć `!` i `^` operatory o `bool?` operandów, co ilustruje poniższy przykład:</span><span class="sxs-lookup"><span data-stu-id="10ce2-200">You can also use the `!` and `^` operators with the `bool?` operands, as the following example shows:</span></span>

[!code-csharp-interactive[lifted negation and xor](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#WithNullableBoolean)]

<span data-ttu-id="10ce2-201">Operatory logiczne warunkowe `&&` i `||` nie obsługują `bool?` argumentów operacji.</span><span class="sxs-lookup"><span data-stu-id="10ce2-201">The conditional logical operators `&&` and `||` don't support the `bool?` operands.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="10ce2-202">Przydział złożony</span><span class="sxs-lookup"><span data-stu-id="10ce2-202">Compound assignment</span></span>

<span data-ttu-id="10ce2-203">Dla operatora binarnego `op`, wyrażenie przypisania złożonego formularza</span><span class="sxs-lookup"><span data-stu-id="10ce2-203">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="10ce2-204">odpowiada wyrażeniu</span><span class="sxs-lookup"><span data-stu-id="10ce2-204">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="10ce2-205">z tą różnicą, że `x` jest obliczany tylko raz.</span><span class="sxs-lookup"><span data-stu-id="10ce2-205">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="10ce2-206">`&`, `|`, I `^` operatory obsługują także przypisanie złożone, co ilustruje poniższy przykład:</span><span class="sxs-lookup"><span data-stu-id="10ce2-206">The `&`, `|`, and `^` operators support compound assignment, as the following example shows:</span></span>

[!code-csharp-interactive[compound assignment](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#CompoundAssignment)]

<span data-ttu-id="10ce2-207">Operatory logiczne warunkowe `&&` i `||` nie obsługują przypisania złożonego.</span><span class="sxs-lookup"><span data-stu-id="10ce2-207">The conditional logical operators `&&` and `||` don't support compound assignment.</span></span>

## <a name="operator-precedence"></a><span data-ttu-id="10ce2-208">Pierwszeństwo operatorów</span><span class="sxs-lookup"><span data-stu-id="10ce2-208">Operator precedence</span></span>

<span data-ttu-id="10ce2-209">Poniższa lista zamówień operatorów logicznych, zaczynając od najwyższy priorytet do najniższego:</span><span class="sxs-lookup"><span data-stu-id="10ce2-209">The following list orders logical operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="10ce2-210">Operator logiczny negacji `!`</span><span class="sxs-lookup"><span data-stu-id="10ce2-210">Logical negation operator `!`</span></span>
- <span data-ttu-id="10ce2-211">Operator logiczny AND `&`</span><span class="sxs-lookup"><span data-stu-id="10ce2-211">Logical AND operator `&`</span></span>
- <span data-ttu-id="10ce2-212">Operator logiczny OR wyłączne `^`</span><span class="sxs-lookup"><span data-stu-id="10ce2-212">Logical exclusive OR operator `^`</span></span>
- <span data-ttu-id="10ce2-213">Operator logiczny OR `|`</span><span class="sxs-lookup"><span data-stu-id="10ce2-213">Logical OR operator `|`</span></span>
- <span data-ttu-id="10ce2-214">Operator logiczny AND warunkowe `&&`</span><span class="sxs-lookup"><span data-stu-id="10ce2-214">Conditional logical AND operator `&&`</span></span>
- <span data-ttu-id="10ce2-215">Operator logiczny OR warunkowe `||`</span><span class="sxs-lookup"><span data-stu-id="10ce2-215">Conditional logical OR operator `||`</span></span>

<span data-ttu-id="10ce2-216">Użyj nawiasów, `()`, aby zmienić kolejność oceny nałożonych przez pierwszeństwo operatorów:</span><span class="sxs-lookup"><span data-stu-id="10ce2-216">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence:</span></span>

[!code-csharp-interactive[operator precedence](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Precedence)]

<span data-ttu-id="10ce2-217">Aby uzyskać pełną listę C# operatory uporządkowane według poziomu priorytetu, zobacz [ C# operatory](index.md).</span><span class="sxs-lookup"><span data-stu-id="10ce2-217">For the complete list of C# operators ordered by precedence level, see [C# operators](index.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="10ce2-218">Overloadability — operator</span><span class="sxs-lookup"><span data-stu-id="10ce2-218">Operator overloadability</span></span>

<span data-ttu-id="10ce2-219">Typ zdefiniowany przez użytkownika może [przeciążenia](operator-overloading.md) `!`, `&`, `|`, i `^` operatorów.</span><span class="sxs-lookup"><span data-stu-id="10ce2-219">A user-defined type can [overload](operator-overloading.md) the `!`, `&`, `|`, and `^` operators.</span></span> <span data-ttu-id="10ce2-220">Gdy jest przeciążony operator binarny, odpowiedniego operatora przypisania złożonego jest również niejawnie przeciążona.</span><span class="sxs-lookup"><span data-stu-id="10ce2-220">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="10ce2-221">Typ zdefiniowany przez użytkownika nie można jawnie przeciążyć operator przypisania złożonego.</span><span class="sxs-lookup"><span data-stu-id="10ce2-221">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

<span data-ttu-id="10ce2-222">Typ zdefiniowany przez użytkownika nie mogą przeciążać operatory logiczne warunkowe `&&` i `||`.</span><span class="sxs-lookup"><span data-stu-id="10ce2-222">A user-defined type cannot overload the conditional logical operators `&&` and `||`.</span></span> <span data-ttu-id="10ce2-223">Jednak jeśli typ zdefiniowany przez użytkownika przeciążenia [operatory true i false](true-false-operators.md) i `&` lub `|` operatora w określony sposób, `&&` lub `||` operacji, odpowiednio, może zostać obliczone dla Operandy typu.</span><span class="sxs-lookup"><span data-stu-id="10ce2-223">However, if a user-defined type overloads the [true and false operators](true-false-operators.md) and the `&` or `|` operator in a certain way, the `&&` or `||` operation, respectively, can be evaluated for the operands of that type.</span></span> <span data-ttu-id="10ce2-224">Aby uzyskać więcej informacji, zobacz [zdefiniowanych przez użytkownika operatorów logicznych warunkowych](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) części [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="10ce2-224">For more information, see the [User-defined conditional logical operators](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="10ce2-225">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="10ce2-225">C# language specification</span></span>

<span data-ttu-id="10ce2-226">Aby uzyskać więcej informacji, zobacz następujące sekcje [ C# specyfikacji języka](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="10ce2-226">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="10ce2-227">Operator logiczny negacji</span><span class="sxs-lookup"><span data-stu-id="10ce2-227">Logical negation operator</span></span>](~/_csharplang/spec/expressions.md#logical-negation-operator)
- [<span data-ttu-id="10ce2-228">Operatory logiczne</span><span class="sxs-lookup"><span data-stu-id="10ce2-228">Logical operators</span></span>](~/_csharplang/spec/expressions.md#logical-operators)
- [<span data-ttu-id="10ce2-229">Operatory logiczne warunkowe</span><span class="sxs-lookup"><span data-stu-id="10ce2-229">Conditional logical operators</span></span>](~/_csharplang/spec/expressions.md#conditional-logical-operators)
- [<span data-ttu-id="10ce2-230">Przydział złożony</span><span class="sxs-lookup"><span data-stu-id="10ce2-230">Compound assignment</span></span>](~/_csharplang/spec/expressions.md#compound-assignment)

## <a name="see-also"></a><span data-ttu-id="10ce2-231">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="10ce2-231">See also</span></span>

- [<span data-ttu-id="10ce2-232">C#Odwołanie</span><span class="sxs-lookup"><span data-stu-id="10ce2-232">C# reference</span></span>](../index.md)
- [<span data-ttu-id="10ce2-233">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="10ce2-233">C# operators</span></span>](index.md)
- [<span data-ttu-id="10ce2-234">Bitowe i operatory przesunięcia</span><span class="sxs-lookup"><span data-stu-id="10ce2-234">Bitwise and shift operators</span></span>](bitwise-and-shift-operators.md)
