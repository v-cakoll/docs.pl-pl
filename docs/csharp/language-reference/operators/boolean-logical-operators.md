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
ms.openlocfilehash: 1a53f2862727318112eae8e9723cabb794fb4f37
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59977941"
---
# <a name="boolean-logical-operators-c-reference"></a><span data-ttu-id="68069-103">Wartość logiczna operatorów logicznych (C# odwołania)</span><span class="sxs-lookup"><span data-stu-id="68069-103">Boolean logical operators (C# Reference)</span></span>

<span data-ttu-id="68069-104">Następujące operatory logiczne wykonania operacji związanych z [bool](../keywords/bool.md) argumenty:</span><span class="sxs-lookup"><span data-stu-id="68069-104">The following operators perform logical operations with the [bool](../keywords/bool.md) operands:</span></span>

- <span data-ttu-id="68069-105">Jednoargumentowy [ `!` (negacja logiczna)](#logical-negation-operator-) operatora.</span><span class="sxs-lookup"><span data-stu-id="68069-105">Unary [`!` (logical negation)](#logical-negation-operator-) operator.</span></span>
- <span data-ttu-id="68069-106">Binarny [ `&` (operator logiczny oraz)](#logical-and-operator-), [ `|` (operator logiczny lub)](#logical-or-operator-), i [ `^` (logiczne OR wyłączne)](#logical-exclusive-or-operator-) operatorów.</span><span class="sxs-lookup"><span data-stu-id="68069-106">Binary [`&` (logical AND)](#logical-and-operator-), [`|` (logical OR)](#logical-or-operator-), and [`^` (logical exclusive OR)](#logical-exclusive-or-operator-) operators.</span></span> <span data-ttu-id="68069-107">Te operatory zawsze należy przeprowadzić ocenę oba operandy.</span><span class="sxs-lookup"><span data-stu-id="68069-107">Those operators always evaluate both operands.</span></span>
- <span data-ttu-id="68069-108">Binarny [ `&&` (warunkowego operator logiczny oraz)](#conditional-logical-and-operator-) i [ `||` (logiczne OR warunkowe)](#conditional-logical-or-operator-) operatorów.</span><span class="sxs-lookup"><span data-stu-id="68069-108">Binary [`&&` (conditional logical AND)](#conditional-logical-and-operator-) and [`||` (conditional logical OR)](#conditional-logical-or-operator-) operators.</span></span> <span data-ttu-id="68069-109">Te operatory ocenić drugi argument operacji tylko wtedy, gdy jest to konieczne.</span><span class="sxs-lookup"><span data-stu-id="68069-109">Those operators evaluate the second operand only if it's necessary.</span></span>

<span data-ttu-id="68069-110">Dla argumentów operacji [całkowitego](../keywords/integral-types-table.md) typów `&`, `|`, i `^` Operatorzy wykonywać operacje logiczne bitowe.</span><span class="sxs-lookup"><span data-stu-id="68069-110">For the operands of the [integral](../keywords/integral-types-table.md) types, the `&`, `|`, and `^` operators perform bitwise logical operations.</span></span> <span data-ttu-id="68069-111">Aby uzyskać więcej informacji, zobacz [operatory bitowe- and -shift](bitwise-and-shift-operators.md).</span><span class="sxs-lookup"><span data-stu-id="68069-111">For more information, see [Bitwise and shift operators](bitwise-and-shift-operators.md).</span></span>

## <a name="logical-negation-operator-"></a><span data-ttu-id="68069-112">Operator logiczny negacji!</span><span class="sxs-lookup"><span data-stu-id="68069-112">Logical negation operator !</span></span>

<span data-ttu-id="68069-113">`!` Operator oblicza Negacja logiczna swojego operandu.</span><span class="sxs-lookup"><span data-stu-id="68069-113">The `!` operator computes logical negation of its operand.</span></span> <span data-ttu-id="68069-114">Oznacza to, tworzy `true`, jeśli argument daje w wyniku `false`, i `false`, jeśli argument daje w wyniku `true`:</span><span class="sxs-lookup"><span data-stu-id="68069-114">That is, it produces `true`, if the operand evaluates to `false`, and `false`, if the operand evaluates to `true`:</span></span>

[!code-csharp-interactive[logical negation](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#Negation)]

## <a name="logical-and-operator-amp"></a><span data-ttu-id="68069-115">Operator logiczny AND &amp;</span><span class="sxs-lookup"><span data-stu-id="68069-115">Logical AND operator &amp;</span></span>

<span data-ttu-id="68069-116">`&` Operator oblicza logicznego i jego operandu.</span><span class="sxs-lookup"><span data-stu-id="68069-116">The `&` operator computes the logical AND of its operands.</span></span> <span data-ttu-id="68069-117">Wynik `x & y` jest `true` Jeśli oba `x` i `y` zwrócić `true`.</span><span class="sxs-lookup"><span data-stu-id="68069-117">The result of `x & y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="68069-118">W przeciwnym razie wynikiem jest `false`.</span><span class="sxs-lookup"><span data-stu-id="68069-118">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="68069-119">`&` Operator ocenia oba operandy nawet wtedy, gdy pierwszy operand ma wartość `false`, dzięki czemu wynik musi być `false` bez względu na wartość drugiego operandu.</span><span class="sxs-lookup"><span data-stu-id="68069-119">The `&` operator evaluates both operands even if the first operand evaluates to `false`, so that the result must be `false` regardless of the value of the second operand.</span></span>

<span data-ttu-id="68069-120">W poniższym przykładzie, drugi operand `&` operator jest wywołanie metody, które jest wykonywane niezależnie od wartości pierwszego operandu:</span><span class="sxs-lookup"><span data-stu-id="68069-120">In the following example, the second operand of the `&` operator is a method call, which is performed regardless of the value of the first operand:</span></span>

[!code-csharp-interactive[logical AND](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#And)]

<span data-ttu-id="68069-121">[Warunkowego logicznego operatora AND](#conditional-logical-and-operator-) `&&` również oblicza logicznego i jego operandu, ale nie ocenia drugiego operandu, jeśli pierwszy operand ma wartość `false`.</span><span class="sxs-lookup"><span data-stu-id="68069-121">The [conditional logical AND operator](#conditional-logical-and-operator-) `&&` also computes the logical AND of its operands, but doesn't evaluate the second operand if the first operand evaluates to `false`.</span></span>

<span data-ttu-id="68069-122">Dla argumentów operacji typu całkowitoliczbowego `&` oblicza operator [iloczynu bitowego AND logiczne](bitwise-and-shift-operators.md#logical-and-operator-) z argumentów.</span><span class="sxs-lookup"><span data-stu-id="68069-122">For the operands of the integral types, the `&` operator computes the [bitwise logical AND](bitwise-and-shift-operators.md#logical-and-operator-) of its operands.</span></span> <span data-ttu-id="68069-123">Jednoargumentowy `&` operator jest [operatora address-of](and-operator.md#unary-address-of-operator).</span><span class="sxs-lookup"><span data-stu-id="68069-123">The unary `&` operator is the [address-of operator](and-operator.md#unary-address-of-operator).</span></span>

## <a name="logical-exclusive-or-operator-"></a><span data-ttu-id="68069-124">Operator logiczny OR wyłączne ^</span><span class="sxs-lookup"><span data-stu-id="68069-124">Logical exclusive OR operator ^</span></span>

<span data-ttu-id="68069-125">`^` Operator oblicza wyłącznie logiczny lub, znany także jako XOR logiczne, z argumentów.</span><span class="sxs-lookup"><span data-stu-id="68069-125">The `^` operator computes the logical exclusive OR, also known as the logical XOR, of its operands.</span></span> <span data-ttu-id="68069-126">Wynik `x ^ y` jest `true` Jeśli `x` daje w wyniku `true` i `y` daje w wyniku `false`, lub `x` daje w wyniku `false` i `y` daje w wyniku `true`.</span><span class="sxs-lookup"><span data-stu-id="68069-126">The result of `x ^ y` is `true` if `x` evaluates to `true` and `y` evaluates to `false`, or `x` evaluates to `false` and `y` evaluates to `true`.</span></span> <span data-ttu-id="68069-127">W przeciwnym razie wynikiem jest `false`.</span><span class="sxs-lookup"><span data-stu-id="68069-127">Otherwise, the result is `false`.</span></span> <span data-ttu-id="68069-128">Oznacza to aby uzyskać `bool` operandów, `^` operator oblicza ten sam wynik jako [operator nierówności](equality-operators.md#inequality-operator-) `!=`.</span><span class="sxs-lookup"><span data-stu-id="68069-128">That is, for the `bool` operands, the `^` operator computes the same result as the [inequality operator](equality-operators.md#inequality-operator-) `!=`.</span></span>

[!code-csharp-interactive[logical exclusive OR](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#Xor)]

<span data-ttu-id="68069-129">Dla argumentów operacji typu całkowitoliczbowego `^` oblicza operator [bitowe wykluczające OR logiczne](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) z argumentów.</span><span class="sxs-lookup"><span data-stu-id="68069-129">For the operands of the integral types, the `^` operator computes the [bitwise logical exclusive OR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) of its operands.</span></span>

## <a name="logical-or-operator-"></a><span data-ttu-id="68069-130">Operator logiczny OR |</span><span class="sxs-lookup"><span data-stu-id="68069-130">Logical OR operator |</span></span>

<span data-ttu-id="68069-131">`|` Operator oblicza operator logiczny lub jego operandu.</span><span class="sxs-lookup"><span data-stu-id="68069-131">The `|` operator computes the logical OR of its operands.</span></span> <span data-ttu-id="68069-132">Wynik `x | y` jest `true` Jeśli `x` lub `y` daje w wyniku `true`.</span><span class="sxs-lookup"><span data-stu-id="68069-132">The result of `x | y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="68069-133">W przeciwnym razie wynikiem jest `false`.</span><span class="sxs-lookup"><span data-stu-id="68069-133">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="68069-134">`|` Operator ocenia oba operandy nawet wtedy, gdy pierwszy operand ma wartość `true`, dzięki czemu wynik musi być `true` bez względu na wartość drugiego operandu.</span><span class="sxs-lookup"><span data-stu-id="68069-134">The `|` operator evaluates both operands even if the first operand evaluates to `true`, so that the result must be `true` regardless of the value of the second operand.</span></span>

<span data-ttu-id="68069-135">W poniższym przykładzie, drugi operand `|` operator jest wywołanie metody, które jest wykonywane niezależnie od wartości pierwszego operandu:</span><span class="sxs-lookup"><span data-stu-id="68069-135">In the following example, the second operand of the `|` operator is a method call, which is performed regardless of the value of the first operand:</span></span>

[!code-csharp-interactive[logical OR](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#Or)]

<span data-ttu-id="68069-136">[Warunkowego logicznego operatora OR](#conditional-logical-or-operator-) `||` również oblicza logiczne OR z argumentów, ale nie ocenia drugiego operandu, jeśli pierwszy operand ma wartość `true`.</span><span class="sxs-lookup"><span data-stu-id="68069-136">The [conditional logical OR operator](#conditional-logical-or-operator-) `||` also computes the logical OR of its operands, but doesn't evaluate the second operand if the first operand evaluates to `true`.</span></span>

<span data-ttu-id="68069-137">Dla argumentów operacji typu całkowitoliczbowego `|` oblicza operator [bitowe OR logiczne](bitwise-and-shift-operators.md#logical-or-operator-) z argumentów.</span><span class="sxs-lookup"><span data-stu-id="68069-137">For the operands of the integral types, the `|` operator computes the [bitwise logical OR](bitwise-and-shift-operators.md#logical-or-operator-) of its operands.</span></span>

## <a name="conditional-logical-and-operator-ampamp"></a><span data-ttu-id="68069-138">Operator logiczny AND warunkowe &amp;&amp;</span><span class="sxs-lookup"><span data-stu-id="68069-138">Conditional logical AND operator &amp;&amp;</span></span>

<span data-ttu-id="68069-139">Operator logiczny AND warunkowe `&&`, znany także jako "zwarcie" logicznego operatora AND, oblicza logicznego i jego operandu.</span><span class="sxs-lookup"><span data-stu-id="68069-139">The conditional logical AND operator `&&`, also known as the "short-circuiting" logical AND operator, computes the logical AND of its operands.</span></span> <span data-ttu-id="68069-140">Wynik `x && y` jest `true` Jeśli oba `x` i `y` zwrócić `true`.</span><span class="sxs-lookup"><span data-stu-id="68069-140">The result of `x && y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="68069-141">W przeciwnym razie wynikiem jest `false`.</span><span class="sxs-lookup"><span data-stu-id="68069-141">Otherwise, the result is `false`.</span></span> <span data-ttu-id="68069-142">Jeśli pierwszy operand ma wartość `false`, drugi operand nie jest oceniany.</span><span class="sxs-lookup"><span data-stu-id="68069-142">If the first operand evaluates to `false`, the second operand is not evaluated.</span></span>

<span data-ttu-id="68069-143">W poniższym przykładzie, drugi operand `&&` operator jest wywołanie metody, które nie jest wykonywane, jeśli pierwszy operand ma wartość `false`:</span><span class="sxs-lookup"><span data-stu-id="68069-143">In the following example, the second operand of the `&&` operator is a method call, which isn't performed if the first operand evaluates to `false`:</span></span>

[!code-csharp-interactive[conditional logical AND](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#ConditionalAnd)]

<span data-ttu-id="68069-144">[Logicznego operatora AND](#logical-and-operator-) `&` oblicza również operator logiczny oraz z argumentów, ale zawsze ocenia oba operandy.</span><span class="sxs-lookup"><span data-stu-id="68069-144">The [logical AND operator](#logical-and-operator-) `&` also computes the logical AND of its operands, but always evaluates both operands.</span></span>

## <a name="conditional-logical-or-operator-"></a><span data-ttu-id="68069-145">Operator warunkowy OR logiczne ||</span><span class="sxs-lookup"><span data-stu-id="68069-145">Conditional logical OR operator ||</span></span>

<span data-ttu-id="68069-146">Operator logiczny OR warunkowe `||`, znany także jako "zwarcie" logicznego operatora OR, oblicza operator logiczny lub jego operandu.</span><span class="sxs-lookup"><span data-stu-id="68069-146">The conditional logical OR operator `||`, also known as the "short-circuiting" logical OR operator, computes the logical OR of its operands.</span></span> <span data-ttu-id="68069-147">Wynik `x || y` jest `true` Jeśli `x` lub `y` daje w wyniku `true`.</span><span class="sxs-lookup"><span data-stu-id="68069-147">The result of `x || y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="68069-148">W przeciwnym razie wynikiem jest `false`.</span><span class="sxs-lookup"><span data-stu-id="68069-148">Otherwise, the result is `false`.</span></span> <span data-ttu-id="68069-149">Jeśli pierwszy operand ma wartość `true`, drugi operand nie jest oceniany.</span><span class="sxs-lookup"><span data-stu-id="68069-149">If the first operand evaluates to `true`, the second operand is not evaluated.</span></span>

<span data-ttu-id="68069-150">W poniższym przykładzie, drugi operand `||` operator jest wywołanie metody, które nie jest wykonywane, jeśli pierwszy operand ma wartość `true`:</span><span class="sxs-lookup"><span data-stu-id="68069-150">In the following example, the second operand of the `||` operator is a method call, which isn't performed if the first operand evaluates to `true`:</span></span>

[!code-csharp-interactive[conditional logical OR](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#ConditionalOr)]

<span data-ttu-id="68069-151">[Operator logiczny OR](#logical-or-operator-) `|` oblicza również logiczne OR z argumentów, ale zawsze ocenia oba operandy.</span><span class="sxs-lookup"><span data-stu-id="68069-151">The [logical OR operator](#logical-or-operator-) `|` also computes the logical OR of its operands, but always evaluates both operands.</span></span>

## <a name="nullable-boolean-logical-operators"></a><span data-ttu-id="68069-152">Operatory dopuszczające wartość null, Boolean i logiczne</span><span class="sxs-lookup"><span data-stu-id="68069-152">Nullable Boolean logical operators</span></span>

<span data-ttu-id="68069-153">Dla `bool?` operandów, `&` i `|` Operatorzy pomocy technicznej przechowywanymi w trzech logiki.</span><span class="sxs-lookup"><span data-stu-id="68069-153">For the `bool?` operands, the `&` and `|` operators support the three-valued logic.</span></span> <span data-ttu-id="68069-154">Semantyka te operatory jest zdefiniowane w poniższej tabeli:</span><span class="sxs-lookup"><span data-stu-id="68069-154">The semantics of these operators is defined by the following table:</span></span>  
  
|<span data-ttu-id="68069-155">x</span><span class="sxs-lookup"><span data-stu-id="68069-155">x</span></span>|<span data-ttu-id="68069-156">t</span><span class="sxs-lookup"><span data-stu-id="68069-156">y</span></span>|<span data-ttu-id="68069-157">x i y</span><span class="sxs-lookup"><span data-stu-id="68069-157">x&y</span></span>|<span data-ttu-id="68069-158">x&#124;y</span><span class="sxs-lookup"><span data-stu-id="68069-158">x&#124;y</span></span>|  
|----|----|----|----|  
|<span data-ttu-id="68069-159">true</span><span class="sxs-lookup"><span data-stu-id="68069-159">true</span></span>|<span data-ttu-id="68069-160">true</span><span class="sxs-lookup"><span data-stu-id="68069-160">true</span></span>|<span data-ttu-id="68069-161">true</span><span class="sxs-lookup"><span data-stu-id="68069-161">true</span></span>|<span data-ttu-id="68069-162">true</span><span class="sxs-lookup"><span data-stu-id="68069-162">true</span></span>|  
|<span data-ttu-id="68069-163">true</span><span class="sxs-lookup"><span data-stu-id="68069-163">true</span></span>|<span data-ttu-id="68069-164">false</span><span class="sxs-lookup"><span data-stu-id="68069-164">false</span></span>|<span data-ttu-id="68069-165">false</span><span class="sxs-lookup"><span data-stu-id="68069-165">false</span></span>|<span data-ttu-id="68069-166">true</span><span class="sxs-lookup"><span data-stu-id="68069-166">true</span></span>|  
|<span data-ttu-id="68069-167">true</span><span class="sxs-lookup"><span data-stu-id="68069-167">true</span></span>|<span data-ttu-id="68069-168">wartość null</span><span class="sxs-lookup"><span data-stu-id="68069-168">null</span></span>|<span data-ttu-id="68069-169">wartość null</span><span class="sxs-lookup"><span data-stu-id="68069-169">null</span></span>|<span data-ttu-id="68069-170">true</span><span class="sxs-lookup"><span data-stu-id="68069-170">true</span></span>|  
|<span data-ttu-id="68069-171">false</span><span class="sxs-lookup"><span data-stu-id="68069-171">false</span></span>|<span data-ttu-id="68069-172">true</span><span class="sxs-lookup"><span data-stu-id="68069-172">true</span></span>|<span data-ttu-id="68069-173">false</span><span class="sxs-lookup"><span data-stu-id="68069-173">false</span></span>|<span data-ttu-id="68069-174">true</span><span class="sxs-lookup"><span data-stu-id="68069-174">true</span></span>|  
|<span data-ttu-id="68069-175">false</span><span class="sxs-lookup"><span data-stu-id="68069-175">false</span></span>|<span data-ttu-id="68069-176">false</span><span class="sxs-lookup"><span data-stu-id="68069-176">false</span></span>|<span data-ttu-id="68069-177">false</span><span class="sxs-lookup"><span data-stu-id="68069-177">false</span></span>|<span data-ttu-id="68069-178">false</span><span class="sxs-lookup"><span data-stu-id="68069-178">false</span></span>|  
|<span data-ttu-id="68069-179">false</span><span class="sxs-lookup"><span data-stu-id="68069-179">false</span></span>|<span data-ttu-id="68069-180">wartość null</span><span class="sxs-lookup"><span data-stu-id="68069-180">null</span></span>|<span data-ttu-id="68069-181">false</span><span class="sxs-lookup"><span data-stu-id="68069-181">false</span></span>|<span data-ttu-id="68069-182">wartość null</span><span class="sxs-lookup"><span data-stu-id="68069-182">null</span></span>|  
|<span data-ttu-id="68069-183">wartość null</span><span class="sxs-lookup"><span data-stu-id="68069-183">null</span></span>|<span data-ttu-id="68069-184">true</span><span class="sxs-lookup"><span data-stu-id="68069-184">true</span></span>|<span data-ttu-id="68069-185">wartość null</span><span class="sxs-lookup"><span data-stu-id="68069-185">null</span></span>|<span data-ttu-id="68069-186">true</span><span class="sxs-lookup"><span data-stu-id="68069-186">true</span></span>|  
|<span data-ttu-id="68069-187">wartość null</span><span class="sxs-lookup"><span data-stu-id="68069-187">null</span></span>|<span data-ttu-id="68069-188">false</span><span class="sxs-lookup"><span data-stu-id="68069-188">false</span></span>|<span data-ttu-id="68069-189">false</span><span class="sxs-lookup"><span data-stu-id="68069-189">false</span></span>|<span data-ttu-id="68069-190">wartość null</span><span class="sxs-lookup"><span data-stu-id="68069-190">null</span></span>|  
|<span data-ttu-id="68069-191">wartość null</span><span class="sxs-lookup"><span data-stu-id="68069-191">null</span></span>|<span data-ttu-id="68069-192">wartość null</span><span class="sxs-lookup"><span data-stu-id="68069-192">null</span></span>|<span data-ttu-id="68069-193">wartość null</span><span class="sxs-lookup"><span data-stu-id="68069-193">null</span></span>|<span data-ttu-id="68069-194">wartość null</span><span class="sxs-lookup"><span data-stu-id="68069-194">null</span></span>|  

<span data-ttu-id="68069-195">Zachowanie tych operatorów różni się od zachowania typowe operatora z typami wartości null.</span><span class="sxs-lookup"><span data-stu-id="68069-195">The behavior of those operators differs from the typical operator behavior with nullable value types.</span></span> <span data-ttu-id="68069-196">Zazwyczaj operator, który jest zdefiniowany w przypadku argumentów operacji typu wartości również można argumentów odpowiedni typ wartości null.</span><span class="sxs-lookup"><span data-stu-id="68069-196">Typically, an operator which is defined for operands of a value type can be also used with operands of the corresponding nullable value type.</span></span> <span data-ttu-id="68069-197">Generuje taki operator `null` Jeśli którykolwiek z argumentów jest `null`.</span><span class="sxs-lookup"><span data-stu-id="68069-197">Such an operator produces `null` if any of its operands is `null`.</span></span> <span data-ttu-id="68069-198">Jednak `&` i `|` operatorów może utworzyć inną niż null, nawet jeśli jeden z argumentów jest `null`.</span><span class="sxs-lookup"><span data-stu-id="68069-198">However, the `&` and `|` operators can produce non-null even if one of the operands is `null`.</span></span> <span data-ttu-id="68069-199">Aby uzyskać więcej informacji o zachowaniu operatora z typami wartości null, zobacz [operatory](../../programming-guide/nullable-types/using-nullable-types.md#operators) części [przy użyciu typów dopuszczających wartości zerowe](../../programming-guide/nullable-types/using-nullable-types.md) artykułu.</span><span class="sxs-lookup"><span data-stu-id="68069-199">For more information about the operator behavior with nullable value types, see the [Operators](../../programming-guide/nullable-types/using-nullable-types.md#operators) section of the [Using nullable types](../../programming-guide/nullable-types/using-nullable-types.md) article.</span></span>

<span data-ttu-id="68069-200">Można również użyć `!` i `^` operatory o `bool?` operandów, co ilustruje poniższy przykład:</span><span class="sxs-lookup"><span data-stu-id="68069-200">You can also use the `!` and `^` operators with the `bool?` operands, as the following example shows:</span></span>

[!code-csharp-interactive[lifted negation and xor](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#WithNullableBoolean)]

<span data-ttu-id="68069-201">Operatory logiczne warunkowe `&&` i `||` nie obsługują `bool?` argumentów operacji.</span><span class="sxs-lookup"><span data-stu-id="68069-201">The conditional logical operators `&&` and `||` don't support the `bool?` operands.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="68069-202">Przydział złożony</span><span class="sxs-lookup"><span data-stu-id="68069-202">Compound assignment</span></span>

<span data-ttu-id="68069-203">Dla operatora binarnego `op`, wyrażenie przypisania złożonego formularza</span><span class="sxs-lookup"><span data-stu-id="68069-203">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="68069-204">odpowiada wyrażeniu</span><span class="sxs-lookup"><span data-stu-id="68069-204">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="68069-205">z tą różnicą, że `x` jest obliczany tylko raz.</span><span class="sxs-lookup"><span data-stu-id="68069-205">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="68069-206">`&`, `|`, I `^` operatory obsługują także przypisanie złożone, co ilustruje poniższy przykład:</span><span class="sxs-lookup"><span data-stu-id="68069-206">The `&`, `|`, and `^` operators support compound assignment, as the following example shows:</span></span>

[!code-csharp-interactive[compound assignment](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#CompoundAssignment)]

<span data-ttu-id="68069-207">Operatory logiczne warunkowe `&&` i `||` nie obsługują przypisania złożonego.</span><span class="sxs-lookup"><span data-stu-id="68069-207">The conditional logical operators `&&` and `||` don't support compound assignment.</span></span>

## <a name="operator-precedence"></a><span data-ttu-id="68069-208">Pierwszeństwo operatorów</span><span class="sxs-lookup"><span data-stu-id="68069-208">Operator precedence</span></span>

<span data-ttu-id="68069-209">Poniższa lista zamówień operatorów logicznych, zaczynając od najwyższy priorytet do najniższego:</span><span class="sxs-lookup"><span data-stu-id="68069-209">The following list orders logical operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="68069-210">Operator logiczny negacji `!`</span><span class="sxs-lookup"><span data-stu-id="68069-210">Logical negation operator `!`</span></span>
- <span data-ttu-id="68069-211">Operator logiczny AND `&`</span><span class="sxs-lookup"><span data-stu-id="68069-211">Logical AND operator `&`</span></span>
- <span data-ttu-id="68069-212">Operator logiczny OR wyłączne `^`</span><span class="sxs-lookup"><span data-stu-id="68069-212">Logical exclusive OR operator `^`</span></span>
- <span data-ttu-id="68069-213">Operator logiczny OR `|`</span><span class="sxs-lookup"><span data-stu-id="68069-213">Logical OR operator `|`</span></span>
- <span data-ttu-id="68069-214">Operator logiczny AND warunkowe `&&`</span><span class="sxs-lookup"><span data-stu-id="68069-214">Conditional logical AND operator `&&`</span></span>
- <span data-ttu-id="68069-215">Operator logiczny OR warunkowe `||`</span><span class="sxs-lookup"><span data-stu-id="68069-215">Conditional logical OR operator `||`</span></span>

<span data-ttu-id="68069-216">Użyj nawiasów, `()`, aby zmienić kolejność oceny nałożonych przez pierwszeństwo operatorów:</span><span class="sxs-lookup"><span data-stu-id="68069-216">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence:</span></span>

[!code-csharp-interactive[operator precedence](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#Precedence)]

<span data-ttu-id="68069-217">Aby uzyskać pełną listę C# operatory uporządkowane według poziomu priorytetu, zobacz [ C# operatory](index.md).</span><span class="sxs-lookup"><span data-stu-id="68069-217">For the complete list of C# operators ordered by precedence level, see [C# operators](index.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="68069-218">Overloadability — operator</span><span class="sxs-lookup"><span data-stu-id="68069-218">Operator overloadability</span></span>

<span data-ttu-id="68069-219">Typ zdefiniowany przez użytkownika może [przeciążenia](../keywords/operator.md) `!`, `&`, `|`, i `^` operatorów.</span><span class="sxs-lookup"><span data-stu-id="68069-219">A user-defined type can [overload](../keywords/operator.md) the `!`, `&`, `|`, and `^` operators.</span></span> <span data-ttu-id="68069-220">Gdy jest przeciążony operator binarny, odpowiedniego operatora przypisania złożonego jest również niejawnie przeciążona.</span><span class="sxs-lookup"><span data-stu-id="68069-220">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="68069-221">Typ zdefiniowany przez użytkownika nie można jawnie przeciążyć operator przypisania złożonego.</span><span class="sxs-lookup"><span data-stu-id="68069-221">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

<span data-ttu-id="68069-222">Typ zdefiniowany przez użytkownika nie mogą przeciążać operatory logiczne warunkowe `&&` i `||`.</span><span class="sxs-lookup"><span data-stu-id="68069-222">A user-defined type cannot overload the conditional logical operators `&&` and `||`.</span></span> <span data-ttu-id="68069-223">Jednak jeśli typ zdefiniowany przez użytkownika przeciążenia [operatory true i false](../keywords/true-false-operators.md) i `&` lub `|` operatora w określony sposób, `&&` lub `||` operacji, odpowiednio, może zostać obliczone dla Operandy typu.</span><span class="sxs-lookup"><span data-stu-id="68069-223">However, if a user-defined type overloads the [true and false operators](../keywords/true-false-operators.md) and the `&` or `|` operator in a certain way, the `&&` or `||` operation, respectively, can be evaluated for the operands of that type.</span></span> <span data-ttu-id="68069-224">Aby uzyskać więcej informacji, zobacz [zdefiniowanych przez użytkownika operatorów logicznych warunkowych](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) części [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="68069-224">For more information, see the [User-defined conditional logical operators](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="68069-225">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="68069-225">C# language specification</span></span>

<span data-ttu-id="68069-226">Aby uzyskać więcej informacji, zobacz następujące sekcje [ C# specyfikacji języka](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="68069-226">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="68069-227">Operator logiczny negacji</span><span class="sxs-lookup"><span data-stu-id="68069-227">Logical negation operator</span></span>](~/_csharplang/spec/expressions.md#logical-negation-operator)
- [<span data-ttu-id="68069-228">Operatory logiczne</span><span class="sxs-lookup"><span data-stu-id="68069-228">Logical operators</span></span>](~/_csharplang/spec/expressions.md#logical-operators)
- [<span data-ttu-id="68069-229">Operatory logiczne warunkowe</span><span class="sxs-lookup"><span data-stu-id="68069-229">Conditional logical operators</span></span>](~/_csharplang/spec/expressions.md#conditional-logical-operators)
- [<span data-ttu-id="68069-230">Przydział złożony</span><span class="sxs-lookup"><span data-stu-id="68069-230">Compound assignment</span></span>](~/_csharplang/spec/expressions.md#compound-assignment)

## <a name="see-also"></a><span data-ttu-id="68069-231">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="68069-231">See also</span></span>

- [<span data-ttu-id="68069-232">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="68069-232">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="68069-233">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="68069-233">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="68069-234">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="68069-234">C# Operators</span></span>](index.md)
- [<span data-ttu-id="68069-235">Bitowe i operatory przesunięcia</span><span class="sxs-lookup"><span data-stu-id="68069-235">Bitwise and shift operators</span></span>](bitwise-and-shift-operators.md)
