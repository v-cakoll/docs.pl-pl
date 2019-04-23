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
ms.openlocfilehash: de621b26334bbc9679ba7e48a9d5a0cbaec67eab
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59427321"
---
# <a name="boolean-logical-operators-c-reference"></a><span data-ttu-id="6b4bf-103">Wartość logiczna operatorów logicznych (C# odwołania)</span><span class="sxs-lookup"><span data-stu-id="6b4bf-103">Boolean logical operators (C# Reference)</span></span>

<span data-ttu-id="6b4bf-104">Następujące operatory logiczne wykonania operacji związanych z [bool](../keywords/bool.md) argumenty:</span><span class="sxs-lookup"><span data-stu-id="6b4bf-104">The following operators perform logical operations with the [bool](../keywords/bool.md) operands:</span></span>

- <span data-ttu-id="6b4bf-105">Jednoargumentowy [ `!` (negacja logiczna)](#logical-negation-operator-) operatora.</span><span class="sxs-lookup"><span data-stu-id="6b4bf-105">Unary [`!` (logical negation)](#logical-negation-operator-) operator.</span></span>
- <span data-ttu-id="6b4bf-106">Binarny [ `&` (operator logiczny oraz)](#logical-and-operator-), [ `|` (operator logiczny lub)](#logical-or-operator-), i [ `^` (logiczne OR wyłączne)](#logical-exclusive-or-operator-) operatorów.</span><span class="sxs-lookup"><span data-stu-id="6b4bf-106">Binary [`&` (logical AND)](#logical-and-operator-), [`|` (logical OR)](#logical-or-operator-), and [`^` (logical exclusive OR)](#logical-exclusive-or-operator-) operators.</span></span> <span data-ttu-id="6b4bf-107">Te operatory zawsze należy przeprowadzić ocenę oba operandy.</span><span class="sxs-lookup"><span data-stu-id="6b4bf-107">Those operators always evaluate both operands.</span></span>
- <span data-ttu-id="6b4bf-108">Binarny [ `&&` (warunkowego operator logiczny oraz)](#conditional-logical-and-operator-) i [ `||` (logiczne OR warunkowe)](#conditional-logical-or-operator-) operatorów.</span><span class="sxs-lookup"><span data-stu-id="6b4bf-108">Binary [`&&` (conditional logical AND)](#conditional-logical-and-operator-) and [`||` (conditional logical OR)](#conditional-logical-or-operator-) operators.</span></span> <span data-ttu-id="6b4bf-109">Te operatory ocenić drugi argument operacji tylko wtedy, gdy jest to konieczne.</span><span class="sxs-lookup"><span data-stu-id="6b4bf-109">Those operators evaluate the second operand only if it's necessary.</span></span>

<span data-ttu-id="6b4bf-110">Dla argumentów operacji [całkowitego](../keywords/integral-types-table.md) typów `&`, `|`, i `^` Operatorzy wykonywać operacje logiczne bitowe.</span><span class="sxs-lookup"><span data-stu-id="6b4bf-110">For the operands of [integral](../keywords/integral-types-table.md) types, the `&`, `|`, and `^` operators perform bitwise logical operations.</span></span>

## <a name="logical-negation-operator-"></a><span data-ttu-id="6b4bf-111">Operator logiczny negacji!</span><span class="sxs-lookup"><span data-stu-id="6b4bf-111">Logical negation operator !</span></span>

<span data-ttu-id="6b4bf-112">`!` Operator oblicza Negacja logiczna swojego operandu.</span><span class="sxs-lookup"><span data-stu-id="6b4bf-112">The `!` operator computes logical negation of its operand.</span></span> <span data-ttu-id="6b4bf-113">Oznacza to, tworzy `true`, jeśli argument daje w wyniku `false`, i `false`, jeśli argument daje w wyniku `true`:</span><span class="sxs-lookup"><span data-stu-id="6b4bf-113">That is, it produces `true`, if the operand evaluates to `false`, and `false`, if the operand evaluates to `true`:</span></span>

[!code-csharp-interactive[logical negation](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#Negation)]

## <a name="logical-and-operator-amp"></a><span data-ttu-id="6b4bf-114">Operator logiczny AND &amp;</span><span class="sxs-lookup"><span data-stu-id="6b4bf-114">Logical AND operator &amp;</span></span>

<span data-ttu-id="6b4bf-115">`&` Operator oblicza logicznego i jego operandu.</span><span class="sxs-lookup"><span data-stu-id="6b4bf-115">The `&` operator computes the logical AND of its operands.</span></span> <span data-ttu-id="6b4bf-116">Wynik `x & y` jest `true` Jeśli oba `x` i `y` zwrócić `true`.</span><span class="sxs-lookup"><span data-stu-id="6b4bf-116">The result of `x & y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="6b4bf-117">W przeciwnym razie wynikiem jest `false`.</span><span class="sxs-lookup"><span data-stu-id="6b4bf-117">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="6b4bf-118">`&` Operator ocenia oba operandy nawet wtedy, gdy pierwszy operand ma wartość `false`, dzięki czemu wynik musi być `false` bez względu na wartość drugiego operandu.</span><span class="sxs-lookup"><span data-stu-id="6b4bf-118">The `&` operator evaluates both operands even if the first operand evaluates to `false`, so that the result must be `false` regardless of the value of the second operand.</span></span>

<span data-ttu-id="6b4bf-119">W poniższym przykładzie, drugi operand `&` operator jest wywołanie metody, które jest wykonywane niezależnie od wartości pierwszego operandu:</span><span class="sxs-lookup"><span data-stu-id="6b4bf-119">In the following example, the second operand of the `&` operator is a method call, which is performed regardless of the value of the first operand:</span></span>

[!code-csharp-interactive[logical AND](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#And)]

<span data-ttu-id="6b4bf-120">[Warunkowego logicznego operatora AND](#conditional-logical-and-operator-) `&&` również oblicza logicznego i jego operandu, ale nie ocenia drugiego operandu, jeśli pierwszy operand ma wartość `false`.</span><span class="sxs-lookup"><span data-stu-id="6b4bf-120">The [conditional logical AND operator](#conditional-logical-and-operator-) `&&` also computes the logical AND of its operands, but doesn't evaluate the second operand if the first operand evaluates to `false`.</span></span>

<span data-ttu-id="6b4bf-121">Dla argumentów operacji typu całkowitoliczbowego `&` oblicza operator [iloczynu bitowego AND logiczne](and-operator.md#integer-logical-bitwise-and-operator) z argumentów.</span><span class="sxs-lookup"><span data-stu-id="6b4bf-121">For the operands of integral types, the `&` operator computes [bitwise logical AND](and-operator.md#integer-logical-bitwise-and-operator) of its operands.</span></span> <span data-ttu-id="6b4bf-122">Jednoargumentowy `&` operator jest [operatora address-of](and-operator.md#unary-address-of-operator).</span><span class="sxs-lookup"><span data-stu-id="6b4bf-122">The unary `&` operator is the [address-of operator](and-operator.md#unary-address-of-operator).</span></span>

## <a name="logical-exclusive-or-operator-"></a><span data-ttu-id="6b4bf-123">Operator logiczny OR wyłączne ^</span><span class="sxs-lookup"><span data-stu-id="6b4bf-123">Logical exclusive OR operator ^</span></span>

<span data-ttu-id="6b4bf-124">`^` Operator oblicza wyłącznie logiczny lub, znany także jako XOR logiczne, z argumentów.</span><span class="sxs-lookup"><span data-stu-id="6b4bf-124">The `^` operator computes the logical exclusive OR, also known as the logical XOR, of its operands.</span></span> <span data-ttu-id="6b4bf-125">Wynik `x ^ y` jest `true` Jeśli `x` daje w wyniku `true` i `y` daje w wyniku `false`, lub `x` daje w wyniku `false` i `y` daje w wyniku `true`.</span><span class="sxs-lookup"><span data-stu-id="6b4bf-125">The result of `x ^ y` is `true` if `x` evaluates to `true` and `y` evaluates to `false`, or `x` evaluates to `false` and `y` evaluates to `true`.</span></span> <span data-ttu-id="6b4bf-126">W przeciwnym razie wynikiem jest `false`.</span><span class="sxs-lookup"><span data-stu-id="6b4bf-126">Otherwise, the result is `false`.</span></span> <span data-ttu-id="6b4bf-127">Oznacza to aby uzyskać `bool` operandów, `^` operator oblicza ten sam wynik jako [operator nierówności](equality-operators.md#inequality-operator-) `!=`.</span><span class="sxs-lookup"><span data-stu-id="6b4bf-127">That is, for the `bool` operands, the `^` operator computes the same result as the [inequality operator](equality-operators.md#inequality-operator-) `!=`.</span></span>

[!code-csharp-interactive[logical exclusive OR](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#Xor)]

<span data-ttu-id="6b4bf-128">Dla argumentów operacji typu całkowitoliczbowego `^` oblicza operator [bitowe wykluczające OR logiczne](xor-operator.md) z argumentów.</span><span class="sxs-lookup"><span data-stu-id="6b4bf-128">For the operands of integral types, the `^` operator computes [bitwise logical exclusive OR](xor-operator.md) of its operands.</span></span>

## <a name="logical-or-operator-"></a><span data-ttu-id="6b4bf-129">Operator logiczny OR |</span><span class="sxs-lookup"><span data-stu-id="6b4bf-129">Logical OR operator |</span></span>

<span data-ttu-id="6b4bf-130">`|` Operator oblicza operator logiczny lub jego operandu.</span><span class="sxs-lookup"><span data-stu-id="6b4bf-130">The `|` operator computes the logical OR of its operands.</span></span> <span data-ttu-id="6b4bf-131">Wynik `x | y` jest `true` Jeśli `x` lub `y` daje w wyniku `true`.</span><span class="sxs-lookup"><span data-stu-id="6b4bf-131">The result of `x | y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="6b4bf-132">W przeciwnym razie wynikiem jest `false`.</span><span class="sxs-lookup"><span data-stu-id="6b4bf-132">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="6b4bf-133">`|` Operator ocenia oba operandy nawet wtedy, gdy pierwszy operand ma wartość `true`, dzięki czemu wynik musi być `true` bez względu na wartość drugiego operandu.</span><span class="sxs-lookup"><span data-stu-id="6b4bf-133">The `|` operator evaluates both operands even if the first operand evaluates to `true`, so that the result must be `true` regardless of the value of the second operand.</span></span>

<span data-ttu-id="6b4bf-134">W poniższym przykładzie, drugi operand `|` operator jest wywołanie metody, które jest wykonywane niezależnie od wartości pierwszego operandu:</span><span class="sxs-lookup"><span data-stu-id="6b4bf-134">In the following example, the second operand of the `|` operator is a method call, which is performed regardless of the value of the first operand:</span></span>

[!code-csharp-interactive[logical OR](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#Or)]

<span data-ttu-id="6b4bf-135">[Warunkowego logicznego operatora OR](#conditional-logical-or-operator-) `||` również oblicza logiczne OR z argumentów, ale nie ocenia drugiego operandu, jeśli pierwszy operand ma wartość `true`.</span><span class="sxs-lookup"><span data-stu-id="6b4bf-135">The [conditional logical OR operator](#conditional-logical-or-operator-) `||` also computes the logical OR of its operands, but doesn't evaluate the second operand if the first operand evaluates to `true`.</span></span>

<span data-ttu-id="6b4bf-136">Dla argumentów operacji typu całkowitoliczbowego `|` oblicza operator [bitowe OR logiczne](or-operator.md) z argumentów.</span><span class="sxs-lookup"><span data-stu-id="6b4bf-136">For the operands of integral types, the `|` operator computes [bitwise logical OR](or-operator.md) of its operands.</span></span>

## <a name="conditional-logical-and-operator-ampamp"></a><span data-ttu-id="6b4bf-137">Operator logiczny AND warunkowe &amp;&amp;</span><span class="sxs-lookup"><span data-stu-id="6b4bf-137">Conditional logical AND operator &amp;&amp;</span></span>

<span data-ttu-id="6b4bf-138">Operator logiczny AND warunkowe `&&`, znany także jako "zwarcie" logicznego operatora AND, oblicza logicznego i jego operandu.</span><span class="sxs-lookup"><span data-stu-id="6b4bf-138">The conditional logical AND operator `&&`, also known as the "short-circuiting" logical AND operator, computes the logical AND of its operands.</span></span> <span data-ttu-id="6b4bf-139">Wynik `x && y` jest `true` Jeśli oba `x` i `y` zwrócić `true`.</span><span class="sxs-lookup"><span data-stu-id="6b4bf-139">The result of `x && y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="6b4bf-140">W przeciwnym razie wynikiem jest `false`.</span><span class="sxs-lookup"><span data-stu-id="6b4bf-140">Otherwise, the result is `false`.</span></span> <span data-ttu-id="6b4bf-141">Jeśli pierwszy operand ma wartość `false`, drugi operand nie jest oceniany.</span><span class="sxs-lookup"><span data-stu-id="6b4bf-141">If the first operand evaluates to `false`, the second operand is not evaluated.</span></span>

<span data-ttu-id="6b4bf-142">W poniższym przykładzie, drugi operand `&&` operator jest wywołanie metody, które nie jest wykonywane, jeśli pierwszy operand ma wartość `false`:</span><span class="sxs-lookup"><span data-stu-id="6b4bf-142">In the following example, the second operand of the `&&` operator is a method call, which isn't performed if the first operand evaluates to `false`:</span></span>

[!code-csharp-interactive[conditional logical AND](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#ConditionalAnd)]

<span data-ttu-id="6b4bf-143">[Logicznego operatora AND](#logical-and-operator-) `&` oblicza również operator logiczny oraz z argumentów, ale zawsze ocenia oba operandy.</span><span class="sxs-lookup"><span data-stu-id="6b4bf-143">The [logical AND operator](#logical-and-operator-) `&` also computes the logical AND of its operands, but always evaluates both operands.</span></span>

## <a name="conditional-logical-or-operator-"></a><span data-ttu-id="6b4bf-144">Operator warunkowy OR logiczne ||</span><span class="sxs-lookup"><span data-stu-id="6b4bf-144">Conditional logical OR operator ||</span></span>

<span data-ttu-id="6b4bf-145">Operator logiczny OR warunkowe `||`, znany także jako "zwarcie" logicznego operatora OR, oblicza operator logiczny lub jego operandu.</span><span class="sxs-lookup"><span data-stu-id="6b4bf-145">The conditional logical OR operator `||`, also known as the "short-circuiting" logical OR operator, computes the logical OR of its operands.</span></span> <span data-ttu-id="6b4bf-146">Wynik `x || y` jest `true` Jeśli `x` lub `y` daje w wyniku `true`.</span><span class="sxs-lookup"><span data-stu-id="6b4bf-146">The result of `x || y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="6b4bf-147">W przeciwnym razie wynikiem jest `false`.</span><span class="sxs-lookup"><span data-stu-id="6b4bf-147">Otherwise, the result is `false`.</span></span> <span data-ttu-id="6b4bf-148">Jeśli pierwszy operand ma wartość `true`, drugi operand nie jest oceniany.</span><span class="sxs-lookup"><span data-stu-id="6b4bf-148">If the first operand evaluates to `true`, the second operand is not evaluated.</span></span>

<span data-ttu-id="6b4bf-149">W poniższym przykładzie, drugi operand `||` operator jest wywołanie metody, które nie jest wykonywane, jeśli pierwszy operand ma wartość `true`:</span><span class="sxs-lookup"><span data-stu-id="6b4bf-149">In the following example, the second operand of the `||` operator is a method call, which isn't performed if the first operand evaluates to `true`:</span></span>

[!code-csharp-interactive[conditional logical OR](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#ConditionalOr)]

<span data-ttu-id="6b4bf-150">[Operator logiczny OR](#logical-or-operator-) `|` oblicza również logiczne OR z argumentów, ale zawsze ocenia oba operandy.</span><span class="sxs-lookup"><span data-stu-id="6b4bf-150">The [logical OR operator](#logical-or-operator-) `|` also computes the logical OR of its operands, but always evaluates both operands.</span></span>

## <a name="nullable-boolean-logical-operators"></a><span data-ttu-id="6b4bf-151">Operatory dopuszczające wartość null, Boolean i logiczne</span><span class="sxs-lookup"><span data-stu-id="6b4bf-151">Nullable Boolean logical operators</span></span>

<span data-ttu-id="6b4bf-152">Dla `bool?` operandów, `&` i `|` Operatorzy pomocy technicznej przechowywanymi w trzech logiki.</span><span class="sxs-lookup"><span data-stu-id="6b4bf-152">For the `bool?` operands, the `&` and `|` operators support the three-valued logic.</span></span> <span data-ttu-id="6b4bf-153">Semantyka te operatory jest zdefiniowane w poniższej tabeli:</span><span class="sxs-lookup"><span data-stu-id="6b4bf-153">The semantics of these operators is defined by the following table:</span></span>  
  
|<span data-ttu-id="6b4bf-154">x</span><span class="sxs-lookup"><span data-stu-id="6b4bf-154">x</span></span>|<span data-ttu-id="6b4bf-155">t</span><span class="sxs-lookup"><span data-stu-id="6b4bf-155">y</span></span>|<span data-ttu-id="6b4bf-156">x i y</span><span class="sxs-lookup"><span data-stu-id="6b4bf-156">x&y</span></span>|<span data-ttu-id="6b4bf-157">x&#124;y</span><span class="sxs-lookup"><span data-stu-id="6b4bf-157">x&#124;y</span></span>|  
|----|----|----|----|  
|<span data-ttu-id="6b4bf-158">true</span><span class="sxs-lookup"><span data-stu-id="6b4bf-158">true</span></span>|<span data-ttu-id="6b4bf-159">true</span><span class="sxs-lookup"><span data-stu-id="6b4bf-159">true</span></span>|<span data-ttu-id="6b4bf-160">true</span><span class="sxs-lookup"><span data-stu-id="6b4bf-160">true</span></span>|<span data-ttu-id="6b4bf-161">true</span><span class="sxs-lookup"><span data-stu-id="6b4bf-161">true</span></span>|  
|<span data-ttu-id="6b4bf-162">true</span><span class="sxs-lookup"><span data-stu-id="6b4bf-162">true</span></span>|<span data-ttu-id="6b4bf-163">false</span><span class="sxs-lookup"><span data-stu-id="6b4bf-163">false</span></span>|<span data-ttu-id="6b4bf-164">false</span><span class="sxs-lookup"><span data-stu-id="6b4bf-164">false</span></span>|<span data-ttu-id="6b4bf-165">true</span><span class="sxs-lookup"><span data-stu-id="6b4bf-165">true</span></span>|  
|<span data-ttu-id="6b4bf-166">true</span><span class="sxs-lookup"><span data-stu-id="6b4bf-166">true</span></span>|<span data-ttu-id="6b4bf-167">wartość null</span><span class="sxs-lookup"><span data-stu-id="6b4bf-167">null</span></span>|<span data-ttu-id="6b4bf-168">wartość null</span><span class="sxs-lookup"><span data-stu-id="6b4bf-168">null</span></span>|<span data-ttu-id="6b4bf-169">true</span><span class="sxs-lookup"><span data-stu-id="6b4bf-169">true</span></span>|  
|<span data-ttu-id="6b4bf-170">false</span><span class="sxs-lookup"><span data-stu-id="6b4bf-170">false</span></span>|<span data-ttu-id="6b4bf-171">true</span><span class="sxs-lookup"><span data-stu-id="6b4bf-171">true</span></span>|<span data-ttu-id="6b4bf-172">false</span><span class="sxs-lookup"><span data-stu-id="6b4bf-172">false</span></span>|<span data-ttu-id="6b4bf-173">true</span><span class="sxs-lookup"><span data-stu-id="6b4bf-173">true</span></span>|  
|<span data-ttu-id="6b4bf-174">false</span><span class="sxs-lookup"><span data-stu-id="6b4bf-174">false</span></span>|<span data-ttu-id="6b4bf-175">false</span><span class="sxs-lookup"><span data-stu-id="6b4bf-175">false</span></span>|<span data-ttu-id="6b4bf-176">false</span><span class="sxs-lookup"><span data-stu-id="6b4bf-176">false</span></span>|<span data-ttu-id="6b4bf-177">false</span><span class="sxs-lookup"><span data-stu-id="6b4bf-177">false</span></span>|  
|<span data-ttu-id="6b4bf-178">false</span><span class="sxs-lookup"><span data-stu-id="6b4bf-178">false</span></span>|<span data-ttu-id="6b4bf-179">wartość null</span><span class="sxs-lookup"><span data-stu-id="6b4bf-179">null</span></span>|<span data-ttu-id="6b4bf-180">false</span><span class="sxs-lookup"><span data-stu-id="6b4bf-180">false</span></span>|<span data-ttu-id="6b4bf-181">wartość null</span><span class="sxs-lookup"><span data-stu-id="6b4bf-181">null</span></span>|  
|<span data-ttu-id="6b4bf-182">wartość null</span><span class="sxs-lookup"><span data-stu-id="6b4bf-182">null</span></span>|<span data-ttu-id="6b4bf-183">true</span><span class="sxs-lookup"><span data-stu-id="6b4bf-183">true</span></span>|<span data-ttu-id="6b4bf-184">wartość null</span><span class="sxs-lookup"><span data-stu-id="6b4bf-184">null</span></span>|<span data-ttu-id="6b4bf-185">true</span><span class="sxs-lookup"><span data-stu-id="6b4bf-185">true</span></span>|  
|<span data-ttu-id="6b4bf-186">wartość null</span><span class="sxs-lookup"><span data-stu-id="6b4bf-186">null</span></span>|<span data-ttu-id="6b4bf-187">false</span><span class="sxs-lookup"><span data-stu-id="6b4bf-187">false</span></span>|<span data-ttu-id="6b4bf-188">false</span><span class="sxs-lookup"><span data-stu-id="6b4bf-188">false</span></span>|<span data-ttu-id="6b4bf-189">wartość null</span><span class="sxs-lookup"><span data-stu-id="6b4bf-189">null</span></span>|  
|<span data-ttu-id="6b4bf-190">wartość null</span><span class="sxs-lookup"><span data-stu-id="6b4bf-190">null</span></span>|<span data-ttu-id="6b4bf-191">wartość null</span><span class="sxs-lookup"><span data-stu-id="6b4bf-191">null</span></span>|<span data-ttu-id="6b4bf-192">wartość null</span><span class="sxs-lookup"><span data-stu-id="6b4bf-192">null</span></span>|<span data-ttu-id="6b4bf-193">wartość null</span><span class="sxs-lookup"><span data-stu-id="6b4bf-193">null</span></span>|  

<span data-ttu-id="6b4bf-194">Zachowanie tych operatorów różni się od zachowania typowe operatora z typami wartości null.</span><span class="sxs-lookup"><span data-stu-id="6b4bf-194">The behavior of those operators differs from the typical operator behavior with nullable value types.</span></span> <span data-ttu-id="6b4bf-195">Zazwyczaj operator, który jest zdefiniowany w przypadku argumentów operacji typu wartości również można argumentów odpowiedni typ wartości null.</span><span class="sxs-lookup"><span data-stu-id="6b4bf-195">Typically, an operator which is defined for operands of a value type can be also used with operands of the corresponding nullable value type.</span></span> <span data-ttu-id="6b4bf-196">Generuje taki operator `null` Jeśli którykolwiek z argumentów jest `null`.</span><span class="sxs-lookup"><span data-stu-id="6b4bf-196">Such an operator produces `null` if any of its operands is `null`.</span></span> <span data-ttu-id="6b4bf-197">Jednak `&` i `|` operatorów może utworzyć inną niż null, nawet jeśli jeden z argumentów jest `null`.</span><span class="sxs-lookup"><span data-stu-id="6b4bf-197">However, the `&` and `|` operators can produce non-null even if one of the operands is `null`.</span></span> <span data-ttu-id="6b4bf-198">Aby uzyskać więcej informacji o zachowaniu operatora z typami wartości null, zobacz [operatory](../../programming-guide/nullable-types/using-nullable-types.md#operators) części [przy użyciu typów dopuszczających wartości zerowe](../../programming-guide/nullable-types/using-nullable-types.md) artykułu.</span><span class="sxs-lookup"><span data-stu-id="6b4bf-198">For more information about the operator behavior with nullable value types, see the [Operators](../../programming-guide/nullable-types/using-nullable-types.md#operators) section of the [Using nullable types](../../programming-guide/nullable-types/using-nullable-types.md) article.</span></span>

<span data-ttu-id="6b4bf-199">Można również użyć `!` i `^` operatory o `bool?` operandów, co ilustruje poniższy przykład:</span><span class="sxs-lookup"><span data-stu-id="6b4bf-199">You can also use the `!` and `^` operators with the `bool?` operands, as the following example shows:</span></span>

[!code-csharp-interactive[lifted negation and xor](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#WithNullableBoolean)]

<span data-ttu-id="6b4bf-200">Operatory logiczne warunkowe `&&` i `||` nie obsługują `bool?` argumentów operacji.</span><span class="sxs-lookup"><span data-stu-id="6b4bf-200">The conditional logical operators `&&` and `||` don't support the `bool?` operands.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="6b4bf-201">Przydział złożony</span><span class="sxs-lookup"><span data-stu-id="6b4bf-201">Compound assignment</span></span>

<span data-ttu-id="6b4bf-202">Dla operatora binarnego `op`, wyrażenie przypisania złożonego formularza</span><span class="sxs-lookup"><span data-stu-id="6b4bf-202">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="6b4bf-203">odpowiada wyrażeniu</span><span class="sxs-lookup"><span data-stu-id="6b4bf-203">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="6b4bf-204">z tą różnicą, że `x` jest obliczany tylko raz.</span><span class="sxs-lookup"><span data-stu-id="6b4bf-204">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="6b4bf-205">`&`, `|`, I `^` operatory obsługują także przypisanie złożone, co ilustruje poniższy przykład:</span><span class="sxs-lookup"><span data-stu-id="6b4bf-205">The `&`, `|`, and `^` operators support compound assignment, as the following example shows:</span></span>

[!code-csharp-interactive[compound assignment](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#CompoundAssignment)]

<span data-ttu-id="6b4bf-206">Operatory logiczne warunkowe `&&` i `||` nie obsługują przypisania złożonego.</span><span class="sxs-lookup"><span data-stu-id="6b4bf-206">The conditional logical operators `&&` and `||` don't support compound assignment.</span></span>

## <a name="operator-precedence"></a><span data-ttu-id="6b4bf-207">Pierwszeństwo operatorów</span><span class="sxs-lookup"><span data-stu-id="6b4bf-207">Operator precedence</span></span>

<span data-ttu-id="6b4bf-208">Poniższa lista zamówień operatorów logicznych, zaczynając od najwyższy priorytet do najniższego:</span><span class="sxs-lookup"><span data-stu-id="6b4bf-208">The following list orders logical operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="6b4bf-209">Operator logiczny negacji `!`</span><span class="sxs-lookup"><span data-stu-id="6b4bf-209">Logical negation operator `!`</span></span>
- <span data-ttu-id="6b4bf-210">Operator logiczny AND `&`</span><span class="sxs-lookup"><span data-stu-id="6b4bf-210">Logical AND operator `&`</span></span>
- <span data-ttu-id="6b4bf-211">Operator logiczny OR wyłączne `^`</span><span class="sxs-lookup"><span data-stu-id="6b4bf-211">Logical exclusive OR operator `^`</span></span>
- <span data-ttu-id="6b4bf-212">Operator logiczny OR `|`</span><span class="sxs-lookup"><span data-stu-id="6b4bf-212">Logical OR operator `|`</span></span>
- <span data-ttu-id="6b4bf-213">Operator logiczny AND warunkowe `&&`</span><span class="sxs-lookup"><span data-stu-id="6b4bf-213">Conditional logical AND operator `&&`</span></span>
- <span data-ttu-id="6b4bf-214">Operator logiczny OR warunkowe `||`</span><span class="sxs-lookup"><span data-stu-id="6b4bf-214">Conditional logical OR operator `||`</span></span>

<span data-ttu-id="6b4bf-215">Użyj nawiasów, `()`, aby zmienić kolejność oceny nałożonych przez pierwszeństwo operatorów:</span><span class="sxs-lookup"><span data-stu-id="6b4bf-215">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence:</span></span>

[!code-csharp-interactive[operator precedence](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#Precedence)]

<span data-ttu-id="6b4bf-216">Aby uzyskać pełną listę C# operatory uporządkowane według poziomu priorytetu, zobacz [ C# operatory](index.md).</span><span class="sxs-lookup"><span data-stu-id="6b4bf-216">For the complete list of C# operators ordered by precedence level, see [C# operators](index.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="6b4bf-217">Overloadability — operator</span><span class="sxs-lookup"><span data-stu-id="6b4bf-217">Operator overloadability</span></span>

<span data-ttu-id="6b4bf-218">Typ zdefiniowany przez użytkownika może [przeciążenia](../keywords/operator.md) `!`, `&`, `|`, i `^` operatorów.</span><span class="sxs-lookup"><span data-stu-id="6b4bf-218">A user-defined type can [overload](../keywords/operator.md) the `!`, `&`, `|`, and `^` operators.</span></span> <span data-ttu-id="6b4bf-219">Gdy jest przeciążony operator binarny, odpowiedniego operatora przypisania złożonego jest również niejawnie przeciążona.</span><span class="sxs-lookup"><span data-stu-id="6b4bf-219">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="6b4bf-220">Typ zdefiniowany przez użytkownika nie można jawnie przeciążyć operator przypisania złożonego.</span><span class="sxs-lookup"><span data-stu-id="6b4bf-220">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

<span data-ttu-id="6b4bf-221">Typ zdefiniowany przez użytkownika nie mogą przeciążać operatory logiczne warunkowe `&&` i `||`.</span><span class="sxs-lookup"><span data-stu-id="6b4bf-221">A user-defined type cannot overload the conditional logical operators `&&` and `||`.</span></span> <span data-ttu-id="6b4bf-222">Jednak jeśli typ zdefiniowany przez użytkownika przeciążenia [operatory true i false](../keywords/true-false-operators.md) i `&` lub `|` operatora w określony sposób, `&&` lub `||` operacji, odpowiednio, może zostać obliczone dla Operandy typu.</span><span class="sxs-lookup"><span data-stu-id="6b4bf-222">However, if a user-defined type overloads the [true and false operators](../keywords/true-false-operators.md) and the `&` or `|` operator in a certain way, the `&&` or `||` operation, respectively, can be evaluated for the operands of that type.</span></span> <span data-ttu-id="6b4bf-223">Aby uzyskać więcej informacji, zobacz [zdefiniowanych przez użytkownika operatorów logicznych warunkowych](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) części [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="6b4bf-223">For more information, see the [User-defined conditional logical operators](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="6b4bf-224">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="6b4bf-224">C# language specification</span></span>

<span data-ttu-id="6b4bf-225">Aby uzyskać więcej informacji, zobacz następujące sekcje [ C# specyfikacji języka](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="6b4bf-225">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="6b4bf-226">Operator logiczny negacji</span><span class="sxs-lookup"><span data-stu-id="6b4bf-226">Logical negation operator</span></span>](~/_csharplang/spec/expressions.md#logical-negation-operator)
- [<span data-ttu-id="6b4bf-227">Operatory logiczne</span><span class="sxs-lookup"><span data-stu-id="6b4bf-227">Logical operators</span></span>](~/_csharplang/spec/expressions.md#logical-operators)
- [<span data-ttu-id="6b4bf-228">Operatory logiczne warunkowe</span><span class="sxs-lookup"><span data-stu-id="6b4bf-228">Conditional logical operators</span></span>](~/_csharplang/spec/expressions.md#conditional-logical-operators)

## <a name="see-also"></a><span data-ttu-id="6b4bf-229">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6b4bf-229">See also</span></span>

- [<span data-ttu-id="6b4bf-230">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="6b4bf-230">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="6b4bf-231">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="6b4bf-231">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="6b4bf-232">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="6b4bf-232">C# Operators</span></span>](index.md)
