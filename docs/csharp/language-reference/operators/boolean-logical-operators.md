---
title: Logiczne operatory logiczne logiczne — odwołanie do języka C#
description: Dowiedz się więcej o operatorach języka C#, które wykonują logiczne negacji, spójnik (I) i włącznie i wyłączne operacje rozłączenia (OR) z operandów logicznych.
ms.date: 09/27/2019
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
ms.openlocfilehash: 930329b922f585ac4763e6a66d3b192ae839f14f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399498"
---
# <a name="boolean-logical-operators-c-reference"></a><span data-ttu-id="5e102-103">Logiczne operatory logiczne (odwołanie do języka C#)</span><span class="sxs-lookup"><span data-stu-id="5e102-103">Boolean logical operators (C# reference)</span></span>

<span data-ttu-id="5e102-104">Następujące operatory wykonują operacje logiczne z [bool](../builtin-types/bool.md) operands:</span><span class="sxs-lookup"><span data-stu-id="5e102-104">The following operators perform logical operations with [bool](../builtin-types/bool.md) operands:</span></span>

- <span data-ttu-id="5e102-105">Operator unary [ `!` (logiczne negacji).](#logical-negation-operator-)</span><span class="sxs-lookup"><span data-stu-id="5e102-105">Unary [`!` (logical negation)](#logical-negation-operator-) operator.</span></span>
- <span data-ttu-id="5e102-106">Operatory [ `&` binarne (logiczne i),](#logical-and-operator-) [ `|` (logiczne LUB)](#logical-or-operator-)i [ `^` (logiczne wyłączne LUB).](#logical-exclusive-or-operator-)</span><span class="sxs-lookup"><span data-stu-id="5e102-106">Binary [`&` (logical AND)](#logical-and-operator-), [`|` (logical OR)](#logical-or-operator-), and [`^` (logical exclusive OR)](#logical-exclusive-or-operator-) operators.</span></span> <span data-ttu-id="5e102-107">Operatorzy ci zawsze oceniają oba argumenty.</span><span class="sxs-lookup"><span data-stu-id="5e102-107">Those operators always evaluate both operands.</span></span>
- <span data-ttu-id="5e102-108">Operatory [ `&&` binarne (warunkowe logiczne I)](#conditional-logical-and-operator-) i [ `||` (warunkowe logiczne LUB).](#conditional-logical-or-operator-)</span><span class="sxs-lookup"><span data-stu-id="5e102-108">Binary [`&&` (conditional logical AND)](#conditional-logical-and-operator-) and [`||` (conditional logical OR)](#conditional-logical-or-operator-) operators.</span></span> <span data-ttu-id="5e102-109">Operatorzy ci oceniają argument y po prawej stronie tylko wtedy, gdy jest to konieczne.</span><span class="sxs-lookup"><span data-stu-id="5e102-109">Those operators evaluate the right-hand operand only if it's necessary.</span></span>

<span data-ttu-id="5e102-110">W przypadku operandów [zintegrowanych typów numerycznych](../builtin-types/integral-numeric-types.md) `&`, , `|`i `^` operatory wykonują operacje logiczne bitwise.</span><span class="sxs-lookup"><span data-stu-id="5e102-110">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `&`, `|`, and `^` operators perform bitwise logical operations.</span></span> <span data-ttu-id="5e102-111">Aby uzyskać więcej informacji, zobacz [Operatory bitowe i przesuwne](bitwise-and-shift-operators.md).</span><span class="sxs-lookup"><span data-stu-id="5e102-111">For more information, see [Bitwise and shift operators](bitwise-and-shift-operators.md).</span></span>

## <a name="logical-negation-operator-"></a><span data-ttu-id="5e102-112">Logiczny operator negacji!</span><span class="sxs-lookup"><span data-stu-id="5e102-112">Logical negation operator !</span></span>

<span data-ttu-id="5e102-113">Operator przedrostka `!` unary oblicza logiczne negacji jego operand.</span><span class="sxs-lookup"><span data-stu-id="5e102-113">The unary prefix `!` operator computes logical negation of its operand.</span></span> <span data-ttu-id="5e102-114">Oznacza to, że `true`produkuje , jeśli operand ocenia , `false`i `false`, `true`jeśli operand ocenia:</span><span class="sxs-lookup"><span data-stu-id="5e102-114">That is, it produces `true`, if the operand evaluates to `false`, and `false`, if the operand evaluates to `true`:</span></span>

[!code-csharp-interactive[logical negation](snippets/BooleanLogicalOperators.cs#Negation)]

<span data-ttu-id="5e102-115">Począwszy od Języka C# 8.0, `!` operator postfix unary jest [operatorem wyrozumiałym.](null-forgiving.md)</span><span class="sxs-lookup"><span data-stu-id="5e102-115">Beginning with C# 8.0, the unary postfix `!` operator is the [null-forgiving operator](null-forgiving.md).</span></span>

## <a name="logical-and-operator-"></a><span data-ttu-id="5e102-116">Operator logiczny AND&amp;</span><span class="sxs-lookup"><span data-stu-id="5e102-116">Logical AND operator &amp;</span></span>

<span data-ttu-id="5e102-117">Operator `&` oblicza logiczną i jego operands.</span><span class="sxs-lookup"><span data-stu-id="5e102-117">The `&` operator computes the logical AND of its operands.</span></span> <span data-ttu-id="5e102-118">Wynik `x & y` jest, `true` jeśli `x` `y` oba `true`i ocenić .</span><span class="sxs-lookup"><span data-stu-id="5e102-118">The result of `x & y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="5e102-119">W przeciwnym razie `false`wynikiem jest .</span><span class="sxs-lookup"><span data-stu-id="5e102-119">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="5e102-120">Operator `&` ocenia oba argumenty, nawet jeśli operand po `false`lewej stronie ocenia , `false` tak, że wynik operacji jest niezależnie od wartości operand po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="5e102-120">The `&` operator evaluates both operands even if the left-hand operand evaluates to `false`, so that the operation result is `false` regardless of the value of the right-hand operand.</span></span>

<span data-ttu-id="5e102-121">W poniższym przykładzie operand po prawej `&` stronie operatora jest wywołanie metody, które jest wykonywane niezależnie od wartości operand po lewej stronie:</span><span class="sxs-lookup"><span data-stu-id="5e102-121">In the following example, the right-hand operand of the `&` operator is a method call, which is performed regardless of the value of the left-hand operand:</span></span>

[!code-csharp-interactive[logical AND](snippets/BooleanLogicalOperators.cs#And)]

<span data-ttu-id="5e102-122">[Warunkowe logiczne and operator](#conditional-logical-and-operator-) `&&` oblicza również logiczne i jego operands, ale nie ocenia operand po prawej stronie, `false`jeśli po lewej stronie operand ocenia .</span><span class="sxs-lookup"><span data-stu-id="5e102-122">The [conditional logical AND operator](#conditional-logical-and-operator-) `&&` also computes the logical AND of its operands, but doesn't evaluate the right-hand operand if the left-hand operand evaluates to `false`.</span></span>

<span data-ttu-id="5e102-123">W przypadku operandów [zintegrowanych typów numerycznych](../builtin-types/integral-numeric-types.md) `&` operator oblicza [bitowy logiczny i](bitwise-and-shift-operators.md#logical-and-operator-) jego argumentów.</span><span class="sxs-lookup"><span data-stu-id="5e102-123">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `&` operator computes the [bitwise logical AND](bitwise-and-shift-operators.md#logical-and-operator-) of its operands.</span></span> <span data-ttu-id="5e102-124">Operator `&` emancypuje. [address-of operator](pointer-related-operators.md#address-of-operator-)</span><span class="sxs-lookup"><span data-stu-id="5e102-124">The unary `&` operator is the [address-of operator](pointer-related-operators.md#address-of-operator-).</span></span>

## <a name="logical-exclusive-or-operator-"></a><span data-ttu-id="5e102-125">Logiczny wyłączny operator OR ^</span><span class="sxs-lookup"><span data-stu-id="5e102-125">Logical exclusive OR operator ^</span></span>

<span data-ttu-id="5e102-126">Operator `^` oblicza logiczne wyłączne OR, znany również jako logiczne XOR, jego operands.</span><span class="sxs-lookup"><span data-stu-id="5e102-126">The `^` operator computes the logical exclusive OR, also known as the logical XOR, of its operands.</span></span> <span data-ttu-id="5e102-127">`x ^ y` Wynik jest, `true` `x` jeśli ocenia `true` `y` i ocenia `false`, `x` lub `false` ocenia `y` i `true`ocenia .</span><span class="sxs-lookup"><span data-stu-id="5e102-127">The result of `x ^ y` is `true` if `x` evaluates to `true` and `y` evaluates to `false`, or `x` evaluates to `false` and `y` evaluates to `true`.</span></span> <span data-ttu-id="5e102-128">W przeciwnym razie `false`wynikiem jest .</span><span class="sxs-lookup"><span data-stu-id="5e102-128">Otherwise, the result is `false`.</span></span> <span data-ttu-id="5e102-129">Oznacza to, `bool` że w przypadku `^` operandów operator oblicza taki sam wynik jak [operator](equality-operators.md#inequality-operator-) `!=`nierówności.</span><span class="sxs-lookup"><span data-stu-id="5e102-129">That is, for the `bool` operands, the `^` operator computes the same result as the [inequality operator](equality-operators.md#inequality-operator-) `!=`.</span></span>

[!code-csharp-interactive[logical exclusive OR](snippets/BooleanLogicalOperators.cs#Xor)]

<span data-ttu-id="5e102-130">W przypadku operandów [zintegrowanych typów numerycznych](../builtin-types/integral-numeric-types.md) `^` operator oblicza [bitowy logiczny wyłączny lub](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) jego operandów.</span><span class="sxs-lookup"><span data-stu-id="5e102-130">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `^` operator computes the [bitwise logical exclusive OR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) of its operands.</span></span>

## <a name="logical-or-operator-"></a><span data-ttu-id="5e102-131">Logiczny operator OR |</span><span class="sxs-lookup"><span data-stu-id="5e102-131">Logical OR operator |</span></span>

<span data-ttu-id="5e102-132">Operator `|` oblicza logiczne LUB jego operandów.</span><span class="sxs-lookup"><span data-stu-id="5e102-132">The `|` operator computes the logical OR of its operands.</span></span> <span data-ttu-id="5e102-133">Wynik `x | y` jest, `true` jeśli `x` `y` albo lub `true`ocenia .</span><span class="sxs-lookup"><span data-stu-id="5e102-133">The result of `x | y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="5e102-134">W przeciwnym razie `false`wynikiem jest .</span><span class="sxs-lookup"><span data-stu-id="5e102-134">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="5e102-135">Operator `|` ocenia oba argumenty, nawet jeśli operand po `true`lewej stronie ocenia , `true` tak, że wynik operacji jest niezależnie od wartości operand po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="5e102-135">The `|` operator evaluates both operands even if the left-hand operand evaluates to `true`, so that the operation result is `true` regardless of the value of the right-hand operand.</span></span>

<span data-ttu-id="5e102-136">W poniższym przykładzie operand po prawej `|` stronie operatora jest wywołanie metody, które jest wykonywane niezależnie od wartości operand po lewej stronie:</span><span class="sxs-lookup"><span data-stu-id="5e102-136">In the following example, the right-hand operand of the `|` operator is a method call, which is performed regardless of the value of the left-hand operand:</span></span>

[!code-csharp-interactive[logical OR](snippets/BooleanLogicalOperators.cs#Or)]

<span data-ttu-id="5e102-137">[Operator logiczny warunkowy OR](#conditional-logical-or-operator-) `||` oblicza również logiczny OR jego argumentów, ale nie ocenia operandu po `true`prawej stronie, jeśli lewy operand ocenia .</span><span class="sxs-lookup"><span data-stu-id="5e102-137">The [conditional logical OR operator](#conditional-logical-or-operator-) `||` also computes the logical OR of its operands, but doesn't evaluate the right-hand operand if the left-hand operand evaluates to `true`.</span></span>

<span data-ttu-id="5e102-138">W przypadku argumentów [zintegrowanych typów numerycznych](../builtin-types/integral-numeric-types.md) `|` operator oblicza [bitowy logiczny LUB](bitwise-and-shift-operators.md#logical-or-operator-) jego argumentów.</span><span class="sxs-lookup"><span data-stu-id="5e102-138">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `|` operator computes the [bitwise logical OR](bitwise-and-shift-operators.md#logical-or-operator-) of its operands.</span></span>

## <a name="conditional-logical-and-operator-"></a><span data-ttu-id="5e102-139">Operator warunkowego logicznego AND&amp;&amp;</span><span class="sxs-lookup"><span data-stu-id="5e102-139">Conditional logical AND operator &amp;&amp;</span></span>

<span data-ttu-id="5e102-140">Warunkowe logiczne and `&&`operator , znany również jako "zwarcie" logiczne i operator, oblicza logiczne i jego operands.</span><span class="sxs-lookup"><span data-stu-id="5e102-140">The conditional logical AND operator `&&`, also known as the "short-circuiting" logical AND operator, computes the logical AND of its operands.</span></span> <span data-ttu-id="5e102-141">Wynik `x && y` jest, `true` jeśli `x` `y` oba `true`i ocenić .</span><span class="sxs-lookup"><span data-stu-id="5e102-141">The result of `x && y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="5e102-142">W przeciwnym razie `false`wynikiem jest .</span><span class="sxs-lookup"><span data-stu-id="5e102-142">Otherwise, the result is `false`.</span></span> <span data-ttu-id="5e102-143">Jeśli `x` zostanie `false`oceniona , `y` nie jest oceniana.</span><span class="sxs-lookup"><span data-stu-id="5e102-143">If `x` evaluates to `false`, `y` is not evaluated.</span></span>

<span data-ttu-id="5e102-144">W poniższym przykładzie operand po prawej `&&` stronie operatora jest wywołanie metody, które nie jest wykonywane, `false`jeśli po lewej stronie operand ocenia:</span><span class="sxs-lookup"><span data-stu-id="5e102-144">In the following example, the right-hand operand of the `&&` operator is a method call, which isn't performed if the left-hand operand evaluates to `false`:</span></span>

[!code-csharp-interactive[conditional logical AND](snippets/BooleanLogicalOperators.cs#ConditionalAnd)]

<span data-ttu-id="5e102-145">[Operator logiczny AND](#logical-and-operator-) `&` oblicza również logiczną i jego argumenty, ale zawsze ocenia oba argumenty.</span><span class="sxs-lookup"><span data-stu-id="5e102-145">The [logical AND operator](#logical-and-operator-) `&` also computes the logical AND of its operands, but always evaluates both operands.</span></span>

## <a name="conditional-logical-or-operator-"></a><span data-ttu-id="5e102-146">Warunkowy operator logiczny OR ||</span><span class="sxs-lookup"><span data-stu-id="5e102-146">Conditional logical OR operator ||</span></span>

<span data-ttu-id="5e102-147">Warunkowe logiczne or `||`operator , znany również jako "zwarcie" logiczny operator OR, oblicza logiczne LUB jego operandów.</span><span class="sxs-lookup"><span data-stu-id="5e102-147">The conditional logical OR operator `||`, also known as the "short-circuiting" logical OR operator, computes the logical OR of its operands.</span></span> <span data-ttu-id="5e102-148">Wynik `x || y` jest, `true` jeśli `x` `y` albo lub `true`ocenia .</span><span class="sxs-lookup"><span data-stu-id="5e102-148">The result of `x || y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="5e102-149">W przeciwnym razie `false`wynikiem jest .</span><span class="sxs-lookup"><span data-stu-id="5e102-149">Otherwise, the result is `false`.</span></span> <span data-ttu-id="5e102-150">Jeśli `x` zostanie `true`oceniona , `y` nie jest oceniana.</span><span class="sxs-lookup"><span data-stu-id="5e102-150">If `x` evaluates to `true`, `y` is not evaluated.</span></span>

<span data-ttu-id="5e102-151">W poniższym przykładzie operand po prawej `||` stronie operatora jest wywołanie metody, które nie jest wykonywane, `true`jeśli po lewej stronie operand ocenia:</span><span class="sxs-lookup"><span data-stu-id="5e102-151">In the following example, the right-hand operand of the `||` operator is a method call, which isn't performed if the left-hand operand evaluates to `true`:</span></span>

[!code-csharp-interactive[conditional logical OR](snippets/BooleanLogicalOperators.cs#ConditionalOr)]

<span data-ttu-id="5e102-152">[Operator logiczny OR](#logical-or-operator-) `|` oblicza również logiczny LUB jego argumentów, ale zawsze ocenia oba argumenty.</span><span class="sxs-lookup"><span data-stu-id="5e102-152">The [logical OR operator](#logical-or-operator-) `|` also computes the logical OR of its operands, but always evaluates both operands.</span></span>

## <a name="nullable-boolean-logical-operators"></a><span data-ttu-id="5e102-153">Operatory logiczne logiczne logiczne wartości null</span><span class="sxs-lookup"><span data-stu-id="5e102-153">Nullable Boolean logical operators</span></span>

<span data-ttu-id="5e102-154">W `bool?` przypadku `&` operandów `|` operatorzy i operatorzy obsługują logikę trójwartościową.</span><span class="sxs-lookup"><span data-stu-id="5e102-154">For `bool?` operands, the `&` and `|` operators support the three-valued logic.</span></span> <span data-ttu-id="5e102-155">Semantyka tych operatorów jest zdefiniowana przez następującą tabelę:</span><span class="sxs-lookup"><span data-stu-id="5e102-155">The semantics of these operators is defined by the following table:</span></span>  
  
|<span data-ttu-id="5e102-156">x</span><span class="sxs-lookup"><span data-stu-id="5e102-156">x</span></span>|<span data-ttu-id="5e102-157">t</span><span class="sxs-lookup"><span data-stu-id="5e102-157">y</span></span>|<span data-ttu-id="5e102-158">x&y</span><span class="sxs-lookup"><span data-stu-id="5e102-158">x&y</span></span>|<span data-ttu-id="5e102-159">x&#124;y</span><span class="sxs-lookup"><span data-stu-id="5e102-159">x&#124;y</span></span>|  
|----|----|----|----|  
|<span data-ttu-id="5e102-160">true</span><span class="sxs-lookup"><span data-stu-id="5e102-160">true</span></span>|<span data-ttu-id="5e102-161">true</span><span class="sxs-lookup"><span data-stu-id="5e102-161">true</span></span>|<span data-ttu-id="5e102-162">true</span><span class="sxs-lookup"><span data-stu-id="5e102-162">true</span></span>|<span data-ttu-id="5e102-163">true</span><span class="sxs-lookup"><span data-stu-id="5e102-163">true</span></span>|  
|<span data-ttu-id="5e102-164">true</span><span class="sxs-lookup"><span data-stu-id="5e102-164">true</span></span>|<span data-ttu-id="5e102-165">false</span><span class="sxs-lookup"><span data-stu-id="5e102-165">false</span></span>|<span data-ttu-id="5e102-166">false</span><span class="sxs-lookup"><span data-stu-id="5e102-166">false</span></span>|<span data-ttu-id="5e102-167">true</span><span class="sxs-lookup"><span data-stu-id="5e102-167">true</span></span>|  
|<span data-ttu-id="5e102-168">true</span><span class="sxs-lookup"><span data-stu-id="5e102-168">true</span></span>|<span data-ttu-id="5e102-169">null</span><span class="sxs-lookup"><span data-stu-id="5e102-169">null</span></span>|<span data-ttu-id="5e102-170">null</span><span class="sxs-lookup"><span data-stu-id="5e102-170">null</span></span>|<span data-ttu-id="5e102-171">true</span><span class="sxs-lookup"><span data-stu-id="5e102-171">true</span></span>|  
|<span data-ttu-id="5e102-172">false</span><span class="sxs-lookup"><span data-stu-id="5e102-172">false</span></span>|<span data-ttu-id="5e102-173">true</span><span class="sxs-lookup"><span data-stu-id="5e102-173">true</span></span>|<span data-ttu-id="5e102-174">false</span><span class="sxs-lookup"><span data-stu-id="5e102-174">false</span></span>|<span data-ttu-id="5e102-175">true</span><span class="sxs-lookup"><span data-stu-id="5e102-175">true</span></span>|  
|<span data-ttu-id="5e102-176">false</span><span class="sxs-lookup"><span data-stu-id="5e102-176">false</span></span>|<span data-ttu-id="5e102-177">false</span><span class="sxs-lookup"><span data-stu-id="5e102-177">false</span></span>|<span data-ttu-id="5e102-178">false</span><span class="sxs-lookup"><span data-stu-id="5e102-178">false</span></span>|<span data-ttu-id="5e102-179">false</span><span class="sxs-lookup"><span data-stu-id="5e102-179">false</span></span>|  
|<span data-ttu-id="5e102-180">false</span><span class="sxs-lookup"><span data-stu-id="5e102-180">false</span></span>|<span data-ttu-id="5e102-181">null</span><span class="sxs-lookup"><span data-stu-id="5e102-181">null</span></span>|<span data-ttu-id="5e102-182">false</span><span class="sxs-lookup"><span data-stu-id="5e102-182">false</span></span>|<span data-ttu-id="5e102-183">null</span><span class="sxs-lookup"><span data-stu-id="5e102-183">null</span></span>|  
|<span data-ttu-id="5e102-184">null</span><span class="sxs-lookup"><span data-stu-id="5e102-184">null</span></span>|<span data-ttu-id="5e102-185">true</span><span class="sxs-lookup"><span data-stu-id="5e102-185">true</span></span>|<span data-ttu-id="5e102-186">null</span><span class="sxs-lookup"><span data-stu-id="5e102-186">null</span></span>|<span data-ttu-id="5e102-187">true</span><span class="sxs-lookup"><span data-stu-id="5e102-187">true</span></span>|  
|<span data-ttu-id="5e102-188">null</span><span class="sxs-lookup"><span data-stu-id="5e102-188">null</span></span>|<span data-ttu-id="5e102-189">false</span><span class="sxs-lookup"><span data-stu-id="5e102-189">false</span></span>|<span data-ttu-id="5e102-190">false</span><span class="sxs-lookup"><span data-stu-id="5e102-190">false</span></span>|<span data-ttu-id="5e102-191">null</span><span class="sxs-lookup"><span data-stu-id="5e102-191">null</span></span>|  
|<span data-ttu-id="5e102-192">null</span><span class="sxs-lookup"><span data-stu-id="5e102-192">null</span></span>|<span data-ttu-id="5e102-193">null</span><span class="sxs-lookup"><span data-stu-id="5e102-193">null</span></span>|<span data-ttu-id="5e102-194">null</span><span class="sxs-lookup"><span data-stu-id="5e102-194">null</span></span>|<span data-ttu-id="5e102-195">null</span><span class="sxs-lookup"><span data-stu-id="5e102-195">null</span></span>|  

<span data-ttu-id="5e102-196">Zachowanie tych operatorów różni się od typowezachowanie operatora z typami wartości nullable.</span><span class="sxs-lookup"><span data-stu-id="5e102-196">The behavior of those operators differs from the typical operator behavior with nullable value types.</span></span> <span data-ttu-id="5e102-197">Zazwyczaj operator, który jest zdefiniowany dla operandów typu wartości może być również używany z argumentów odpowiedniego typu wartości nullable.</span><span class="sxs-lookup"><span data-stu-id="5e102-197">Typically, an operator which is defined for operands of a value type can be also used with operands of the corresponding nullable value type.</span></span> <span data-ttu-id="5e102-198">Taki operator produkuje, `null` jeśli którykolwiek z jego `null`operands ocenia .</span><span class="sxs-lookup"><span data-stu-id="5e102-198">Such an operator produces `null` if any of its operands evaluates to `null`.</span></span> <span data-ttu-id="5e102-199">Jednak `&` operatory `|` i może produkować non-null, nawet jeśli jeden `null`z operands ocenia .</span><span class="sxs-lookup"><span data-stu-id="5e102-199">However, the `&` and `|` operators can produce non-null even if one of the operands evaluates to `null`.</span></span> <span data-ttu-id="5e102-200">Aby uzyskać więcej informacji na temat zachowania operatora z typami wartości nullable, zobacz [Lifted operatorów](../builtin-types/nullable-value-types.md#lifted-operators) sekcji [typy wartości nullable.](../builtin-types/nullable-value-types.md)</span><span class="sxs-lookup"><span data-stu-id="5e102-200">For more information about the operator behavior with nullable value types, see the [Lifted operators](../builtin-types/nullable-value-types.md#lifted-operators) section of the [Nullable value types](../builtin-types/nullable-value-types.md) article.</span></span>

<span data-ttu-id="5e102-201">Można również użyć `!` `^` i `bool?` operatorów z operandów, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="5e102-201">You can also use the `!` and `^` operators with `bool?` operands, as the following example shows:</span></span>

[!code-csharp-interactive[lifted negation and xor](snippets/BooleanLogicalOperators.cs#WithNullableBoolean)]

<span data-ttu-id="5e102-202">Warunkowe operatory `&&` `||` logiczne i `bool?` nie obsługują operandów.</span><span class="sxs-lookup"><span data-stu-id="5e102-202">The conditional logical operators `&&` and `||` don't support `bool?` operands.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="5e102-203">Przypisanie złożone</span><span class="sxs-lookup"><span data-stu-id="5e102-203">Compound assignment</span></span>

<span data-ttu-id="5e102-204">Dla operatora `op`binarnego wyrażenie przypisania złożonego formularza</span><span class="sxs-lookup"><span data-stu-id="5e102-204">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="5e102-205">jest równoważny</span><span class="sxs-lookup"><span data-stu-id="5e102-205">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="5e102-206">chyba `x` że jest oceniana tylko raz.</span><span class="sxs-lookup"><span data-stu-id="5e102-206">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="5e102-207">Program `&` `|`, `^` i operatory obsługują przypisanie złożone, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="5e102-207">The `&`, `|`, and `^` operators support compound assignment, as the following example shows:</span></span>

[!code-csharp-interactive[compound assignment](snippets/BooleanLogicalOperators.cs#CompoundAssignment)]

<span data-ttu-id="5e102-208">Warunkowe operatory `&&` `||` logiczne i nie obsługują przypisania złożonego.</span><span class="sxs-lookup"><span data-stu-id="5e102-208">The conditional logical operators `&&` and `||` don't support compound assignment.</span></span>

## <a name="operator-precedence"></a><span data-ttu-id="5e102-209">Pierwszeństwo operatorów</span><span class="sxs-lookup"><span data-stu-id="5e102-209">Operator precedence</span></span>

<span data-ttu-id="5e102-210">Poniższa lista porządkuje operatory logiczne, począwszy od najwyższego pierwszeństwa do najniższego:</span><span class="sxs-lookup"><span data-stu-id="5e102-210">The following list orders logical operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="5e102-211">Logiczny operator negacji`!`</span><span class="sxs-lookup"><span data-stu-id="5e102-211">Logical negation operator `!`</span></span>
- <span data-ttu-id="5e102-212">Operator logiczny AND`&`</span><span class="sxs-lookup"><span data-stu-id="5e102-212">Logical AND operator `&`</span></span>
- <span data-ttu-id="5e102-213">Logiczny wyłączny operator OR`^`</span><span class="sxs-lookup"><span data-stu-id="5e102-213">Logical exclusive OR operator `^`</span></span>
- <span data-ttu-id="5e102-214">Operator logiczny OR`|`</span><span class="sxs-lookup"><span data-stu-id="5e102-214">Logical OR operator `|`</span></span>
- <span data-ttu-id="5e102-215">Operator warunkowego logicznego AND`&&`</span><span class="sxs-lookup"><span data-stu-id="5e102-215">Conditional logical AND operator `&&`</span></span>
- <span data-ttu-id="5e102-216">Operator logiczny warunkowy OR`||`</span><span class="sxs-lookup"><span data-stu-id="5e102-216">Conditional logical OR operator `||`</span></span>

<span data-ttu-id="5e102-217">Użyj nawiasów, `()`, aby zmienić kolejność oceny narzuconą przez pierwszeństwo operatora:</span><span class="sxs-lookup"><span data-stu-id="5e102-217">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence:</span></span>

[!code-csharp-interactive[operator precedence](snippets/BooleanLogicalOperators.cs#Precedence)]

<span data-ttu-id="5e102-218">Aby uzyskać pełną listę operatorów Języka C# uporządkowane według poziomu pierwszeństwa, zobacz [pierwszeństwo operatora](index.md#operator-precedence) sekcji [operatorów C#artykułu.](index.md)</span><span class="sxs-lookup"><span data-stu-id="5e102-218">For the complete list of C# operators ordered by precedence level, see the [Operator precedence](index.md#operator-precedence) section of the [C# operators](index.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="5e102-219">Przeciążenie operatora</span><span class="sxs-lookup"><span data-stu-id="5e102-219">Operator overloadability</span></span>

<span data-ttu-id="5e102-220">Typ zdefiniowany przez użytkownika `!`może `&` `|` `^` [przeciążyć](operator-overloading.md) , , i operatorów.</span><span class="sxs-lookup"><span data-stu-id="5e102-220">A user-defined type can [overload](operator-overloading.md) the `!`, `&`, `|`, and `^` operators.</span></span> <span data-ttu-id="5e102-221">Gdy operator binarny jest przeciążony, odpowiedni operator przypisania złożonego jest również niejawnie przeciążony.</span><span class="sxs-lookup"><span data-stu-id="5e102-221">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="5e102-222">Typ zdefiniowany przez użytkownika nie może jawnie przeciążać operatora przypisania złożonego.</span><span class="sxs-lookup"><span data-stu-id="5e102-222">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

<span data-ttu-id="5e102-223">Typ zdefiniowany przez użytkownika nie może `&&` `||`przeciążać operatorów logicznych warunkowych i .</span><span class="sxs-lookup"><span data-stu-id="5e102-223">A user-defined type cannot overload the conditional logical operators `&&` and `||`.</span></span> <span data-ttu-id="5e102-224">Jednak jeśli typ zdefiniowany przez użytkownika przeciąża `&` [operatory true i false](true-false-operators.md) `||` i lub `|` operator w określony sposób, `&&` lub operacji, odpowiednio, mogą być oceniane dla operandów tego typu.</span><span class="sxs-lookup"><span data-stu-id="5e102-224">However, if a user-defined type overloads the [true and false operators](true-false-operators.md) and the `&` or `|` operator in a certain way, the `&&` or `||` operation, respectively, can be evaluated for the operands of that type.</span></span> <span data-ttu-id="5e102-225">Aby uzyskać więcej informacji, zobacz sekcję [Operatory logiczne warunkowe zdefiniowane przez użytkownika](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) [specyfikacji języka Języka C#.](~/_csharplang/spec/introduction.md)</span><span class="sxs-lookup"><span data-stu-id="5e102-225">For more information, see the [User-defined conditional logical operators](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="5e102-226">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="5e102-226">C# language specification</span></span>

<span data-ttu-id="5e102-227">Aby uzyskać więcej informacji, zobacz następujące sekcje [specyfikacji języka Języka C#:](~/_csharplang/spec/introduction.md)</span><span class="sxs-lookup"><span data-stu-id="5e102-227">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="5e102-228">Logiczny operator negacji</span><span class="sxs-lookup"><span data-stu-id="5e102-228">Logical negation operator</span></span>](~/_csharplang/spec/expressions.md#logical-negation-operator)
- [<span data-ttu-id="5e102-229">Operatory logiczne</span><span class="sxs-lookup"><span data-stu-id="5e102-229">Logical operators</span></span>](~/_csharplang/spec/expressions.md#logical-operators)
- [<span data-ttu-id="5e102-230">Warunkowe operatory logiczne</span><span class="sxs-lookup"><span data-stu-id="5e102-230">Conditional logical operators</span></span>](~/_csharplang/spec/expressions.md#conditional-logical-operators)
- [<span data-ttu-id="5e102-231">Przypisanie złożone</span><span class="sxs-lookup"><span data-stu-id="5e102-231">Compound assignment</span></span>](~/_csharplang/spec/expressions.md#compound-assignment)

## <a name="see-also"></a><span data-ttu-id="5e102-232">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5e102-232">See also</span></span>

- [<span data-ttu-id="5e102-233">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="5e102-233">C# reference</span></span>](../index.md)
- [<span data-ttu-id="5e102-234">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="5e102-234">C# operators</span></span>](index.md)
- [<span data-ttu-id="5e102-235">Operatory przesunięcia i operatory bitowe</span><span class="sxs-lookup"><span data-stu-id="5e102-235">Bitwise and shift operators</span></span>](bitwise-and-shift-operators.md)
