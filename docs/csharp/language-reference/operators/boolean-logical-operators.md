---
title: Boolean operatory logiczne — odwołanie w C#
description: Dowiedz się więcej na temat operatorów języka C#, które wykonują logiczne negacje, połączenie (i), a także wyłączne operacje odłączenia (lub) z argumentami operacji logicznych.
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
ms.openlocfilehash: 5f85b88236c2e643f97453c64173a3f4f7159a35
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795004"
---
# <a name="boolean-logical-operators-c-reference"></a><span data-ttu-id="15fde-103">Boolean operatory logiczne (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="15fde-103">Boolean logical operators (C# reference)</span></span>

<span data-ttu-id="15fde-104">Następujące operatory wykonują operacje logiczne z argumentami operacji [bool](../builtin-types/bool.md) :</span><span class="sxs-lookup"><span data-stu-id="15fde-104">The following operators perform logical operations with [bool](../builtin-types/bool.md) operands:</span></span>

- <span data-ttu-id="15fde-105">Operator jednoargumentowy [ `!` (logiczne Negacja)](#logical-negation-operator-) .</span><span class="sxs-lookup"><span data-stu-id="15fde-105">Unary [`!` (logical negation)](#logical-negation-operator-) operator.</span></span>
- <span data-ttu-id="15fde-106">Operatory binarne [ `&` (logiczne i)](#logical-and-operator-), [ `|` (logiczne lub)](#logical-or-operator-)i [ `^` (logiczne wyłączne lub)](#logical-exclusive-or-operator-) .</span><span class="sxs-lookup"><span data-stu-id="15fde-106">Binary [`&` (logical AND)](#logical-and-operator-), [`|` (logical OR)](#logical-or-operator-), and [`^` (logical exclusive OR)](#logical-exclusive-or-operator-) operators.</span></span> <span data-ttu-id="15fde-107">Te operatory zawsze obliczają oba operandy.</span><span class="sxs-lookup"><span data-stu-id="15fde-107">Those operators always evaluate both operands.</span></span>
- <span data-ttu-id="15fde-108">Binary [ `&&` (warunkowe logiczne i)](#conditional-logical-and-operator-) oraz [ `||` operatory warunkowe logiczne or](#conditional-logical-or-operator-) .</span><span class="sxs-lookup"><span data-stu-id="15fde-108">Binary [`&&` (conditional logical AND)](#conditional-logical-and-operator-) and [`||` (conditional logical OR)](#conditional-logical-or-operator-) operators.</span></span> <span data-ttu-id="15fde-109">Te operatory obliczają operand z prawej strony tylko wtedy, gdy jest to konieczne.</span><span class="sxs-lookup"><span data-stu-id="15fde-109">Those operators evaluate the right-hand operand only if it's necessary.</span></span>

<span data-ttu-id="15fde-110">W przypadku operandów [całkowitych typów liczbowych](../builtin-types/integral-numeric-types.md)operatory `&`, `|`i `^` wykonują bitowe operacje logiczne.</span><span class="sxs-lookup"><span data-stu-id="15fde-110">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `&`, `|`, and `^` operators perform bitwise logical operations.</span></span> <span data-ttu-id="15fde-111">Aby uzyskać więcej informacji, zobacz [Operatory bitowe i przesunięcia](bitwise-and-shift-operators.md).</span><span class="sxs-lookup"><span data-stu-id="15fde-111">For more information, see [Bitwise and shift operators](bitwise-and-shift-operators.md).</span></span>

## <a name="logical-negation-operator-"></a><span data-ttu-id="15fde-112">Operator logiczny negacji</span><span class="sxs-lookup"><span data-stu-id="15fde-112">Logical negation operator !</span></span>

<span data-ttu-id="15fde-113">Jednoargumentowy `!` operator prefiksu oblicza logiczne Negacja operandu.</span><span class="sxs-lookup"><span data-stu-id="15fde-113">The unary prefix `!` operator computes logical negation of its operand.</span></span> <span data-ttu-id="15fde-114">To znaczy, gdy operand `true`jest obliczany do `false`, i `false`, jeśli operand ma `true`wartość:</span><span class="sxs-lookup"><span data-stu-id="15fde-114">That is, it produces `true`, if the operand evaluates to `false`, and `false`, if the operand evaluates to `true`:</span></span>

[!code-csharp-interactive[logical negation](snippets/BooleanLogicalOperators.cs#Negation)]

<span data-ttu-id="15fde-115">Począwszy od języka C# 8,0, jednoargumentowy operator przyrostkowy `!` jest [operatorem łagodniejszej o wartości null](null-forgiving.md).</span><span class="sxs-lookup"><span data-stu-id="15fde-115">Beginning with C# 8.0, the unary postfix `!` operator is the [null-forgiving operator](null-forgiving.md).</span></span>

## <a name="logical-and-operator-amp"></a><a name="logical-and-operator-"></a><span data-ttu-id="15fde-116">Operator logiczny AND&amp;</span><span class="sxs-lookup"><span data-stu-id="15fde-116">Logical AND operator &amp;</span></span>

<span data-ttu-id="15fde-117">`&` Operator oblicza wartość logiczną i jej operandów.</span><span class="sxs-lookup"><span data-stu-id="15fde-117">The `&` operator computes the logical AND of its operands.</span></span> <span data-ttu-id="15fde-118">Wynik `x & y` jest Jeśli oba `true` `x` i `y` są oceniane do `true`.</span><span class="sxs-lookup"><span data-stu-id="15fde-118">The result of `x & y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="15fde-119">W przeciwnym razie wynik jest `false`.</span><span class="sxs-lookup"><span data-stu-id="15fde-119">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="15fde-120">`&` Operator oblicza oba operandy, nawet jeśli argument operacji po lewej stronie jest obliczany do `false`, tak że wynik operacji jest `false` niezależnie od wartości operandu po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="15fde-120">The `&` operator evaluates both operands even if the left-hand operand evaluates to `false`, so that the operation result is `false` regardless of the value of the right-hand operand.</span></span>

<span data-ttu-id="15fde-121">W poniższym przykładzie operand z prawej strony `&` operatora jest wywołaniem metody, które jest wykonywane niezależnie od wartości operandu po lewej stronie:</span><span class="sxs-lookup"><span data-stu-id="15fde-121">In the following example, the right-hand operand of the `&` operator is a method call, which is performed regardless of the value of the left-hand operand:</span></span>

[!code-csharp-interactive[logical AND](snippets/BooleanLogicalOperators.cs#And)]

<span data-ttu-id="15fde-122">`&&` `false` [Warunkowy operator logiczny and](#conditional-logical-and-operator-) oblicza również wartość logiczną i jej operandy, ale nie oblicza wartości argumentu po prawej stronie, jeśli argument operacji po lewej stronie ma wartość.</span><span class="sxs-lookup"><span data-stu-id="15fde-122">The [conditional logical AND operator](#conditional-logical-and-operator-) `&&` also computes the logical AND of its operands, but doesn't evaluate the right-hand operand if the left-hand operand evaluates to `false`.</span></span>

<span data-ttu-id="15fde-123">Dla operandów [całkowitych typów liczbowych](../builtin-types/integral-numeric-types.md) `&` operator oblicza koniunkcję [bitową i](bitwise-and-shift-operators.md#logical-and-operator-) jej operandy.</span><span class="sxs-lookup"><span data-stu-id="15fde-123">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `&` operator computes the [bitwise logical AND](bitwise-and-shift-operators.md#logical-and-operator-) of its operands.</span></span> <span data-ttu-id="15fde-124">Operator jednoargumentowy `&` jest operatorem [Address-of](pointer-related-operators.md#address-of-operator-).</span><span class="sxs-lookup"><span data-stu-id="15fde-124">The unary `&` operator is the [address-of operator](pointer-related-operators.md#address-of-operator-).</span></span>

## <a name="logical-exclusive-or-operator-"></a><span data-ttu-id="15fde-125">Operator wyłączny logicznego OR ^</span><span class="sxs-lookup"><span data-stu-id="15fde-125">Logical exclusive OR operator ^</span></span>

<span data-ttu-id="15fde-126">`^` Operator oblicza wartość logiczną na wyłączność lub, znaną również jako logiczna XOR, dla argumentów operacji.</span><span class="sxs-lookup"><span data-stu-id="15fde-126">The `^` operator computes the logical exclusive OR, also known as the logical XOR, of its operands.</span></span> <span data-ttu-id="15fde-127">Wynik `x ^ y` jest w przypadku `true` `x` `true` `y` `x` `false` `y` `true`, gdy jest obliczany i obliczany do, lub szacuje się w. `false`</span><span class="sxs-lookup"><span data-stu-id="15fde-127">The result of `x ^ y` is `true` if `x` evaluates to `true` and `y` evaluates to `false`, or `x` evaluates to `false` and `y` evaluates to `true`.</span></span> <span data-ttu-id="15fde-128">W przeciwnym razie wynik jest `false`.</span><span class="sxs-lookup"><span data-stu-id="15fde-128">Otherwise, the result is `false`.</span></span> <span data-ttu-id="15fde-129">Oznacza to, że dla `bool` operandów `^` operator oblicza ten sam wynik jako `!=` [operator nierówności](equality-operators.md#inequality-operator-) .</span><span class="sxs-lookup"><span data-stu-id="15fde-129">That is, for the `bool` operands, the `^` operator computes the same result as the [inequality operator](equality-operators.md#inequality-operator-) `!=`.</span></span>

[!code-csharp-interactive[logical exclusive OR](snippets/BooleanLogicalOperators.cs#Xor)]

<span data-ttu-id="15fde-130">W przypadku operandów [całkowitych typów liczbowych](../builtin-types/integral-numeric-types.md) `^` operator oblicza [bitową logiczną na wyłączność lub](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) z jej argumentów operacji.</span><span class="sxs-lookup"><span data-stu-id="15fde-130">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `^` operator computes the [bitwise logical exclusive OR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) of its operands.</span></span>

## <a name="logical-or-operator-"></a><span data-ttu-id="15fde-131">Operator logiczny OR |</span><span class="sxs-lookup"><span data-stu-id="15fde-131">Logical OR operator |</span></span>

<span data-ttu-id="15fde-132">`|` Operator oblicza wartość logiczną lub argumentów operacji.</span><span class="sxs-lookup"><span data-stu-id="15fde-132">The `|` operator computes the logical OR of its operands.</span></span> <span data-ttu-id="15fde-133">Wynik `x | y` jest, jeśli `true` `x` lub `y` jest obliczany do `true`.</span><span class="sxs-lookup"><span data-stu-id="15fde-133">The result of `x | y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="15fde-134">W przeciwnym razie wynik jest `false`.</span><span class="sxs-lookup"><span data-stu-id="15fde-134">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="15fde-135">`|` Operator oblicza oba operandy, nawet jeśli argument operacji po lewej stronie jest obliczany do `true`, tak że wynik operacji jest `true` niezależnie od wartości operandu po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="15fde-135">The `|` operator evaluates both operands even if the left-hand operand evaluates to `true`, so that the operation result is `true` regardless of the value of the right-hand operand.</span></span>

<span data-ttu-id="15fde-136">W poniższym przykładzie operand z prawej strony `|` operatora jest wywołaniem metody, które jest wykonywane niezależnie od wartości operandu po lewej stronie:</span><span class="sxs-lookup"><span data-stu-id="15fde-136">In the following example, the right-hand operand of the `|` operator is a method call, which is performed regardless of the value of the left-hand operand:</span></span>

[!code-csharp-interactive[logical OR](snippets/BooleanLogicalOperators.cs#Or)]

<span data-ttu-id="15fde-137">`||` `true` [Operator logiczny or](#conditional-logical-or-operator-) oblicza również wartość logiczną lub jej operandy, ale nie oblicza wartości operandu po prawej stronie, jeśli argument operacji po lewej stronie ma wartość.</span><span class="sxs-lookup"><span data-stu-id="15fde-137">The [conditional logical OR operator](#conditional-logical-or-operator-) `||` also computes the logical OR of its operands, but doesn't evaluate the right-hand operand if the left-hand operand evaluates to `true`.</span></span>

<span data-ttu-id="15fde-138">Dla argumentów operacji [całkowitych typów liczbowych](../builtin-types/integral-numeric-types.md) `|` operator oblicza bitową koniunkcję [logiczną lub](bitwise-and-shift-operators.md#logical-or-operator-) argumentów operacji.</span><span class="sxs-lookup"><span data-stu-id="15fde-138">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `|` operator computes the [bitwise logical OR](bitwise-and-shift-operators.md#logical-or-operator-) of its operands.</span></span>

## <a name="conditional-logical-and-operator-ampamp"></a><a name="conditional-logical-and-operator-"></a><span data-ttu-id="15fde-139">Warunkowe operatory logiczne i&amp;&amp;</span><span class="sxs-lookup"><span data-stu-id="15fde-139">Conditional logical AND operator &amp;&amp;</span></span>

<span data-ttu-id="15fde-140">Warunkowy operator `&&`logiczny and, znany także jako operator logiczny "krótki-obwód", oblicza wartość logiczną i argumentów operacji.</span><span class="sxs-lookup"><span data-stu-id="15fde-140">The conditional logical AND operator `&&`, also known as the "short-circuiting" logical AND operator, computes the logical AND of its operands.</span></span> <span data-ttu-id="15fde-141">Wynik `x && y` jest Jeśli oba `true` `x` i `y` są oceniane do `true`.</span><span class="sxs-lookup"><span data-stu-id="15fde-141">The result of `x && y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="15fde-142">W przeciwnym razie wynik jest `false`.</span><span class="sxs-lookup"><span data-stu-id="15fde-142">Otherwise, the result is `false`.</span></span> <span data-ttu-id="15fde-143">Jeśli `x` ma wartość `false`, `y` nie jest oceniane.</span><span class="sxs-lookup"><span data-stu-id="15fde-143">If `x` evaluates to `false`, `y` is not evaluated.</span></span>

<span data-ttu-id="15fde-144">W poniższym przykładzie operand z prawej strony `&&` operatora jest wywołaniem metody, które nie jest wykonywane, jeśli argument operacji po lewej stronie ma `false`wartość:</span><span class="sxs-lookup"><span data-stu-id="15fde-144">In the following example, the right-hand operand of the `&&` operator is a method call, which isn't performed if the left-hand operand evaluates to `false`:</span></span>

[!code-csharp-interactive[conditional logical AND](snippets/BooleanLogicalOperators.cs#ConditionalAnd)]

<span data-ttu-id="15fde-145">`&` [Operator logiczny and](#logical-and-operator-) oblicza również wartość logiczną i jej operandy, ale zawsze oblicza oba operandy.</span><span class="sxs-lookup"><span data-stu-id="15fde-145">The [logical AND operator](#logical-and-operator-) `&` also computes the logical AND of its operands, but always evaluates both operands.</span></span>

## <a name="conditional-logical-or-operator-"></a><span data-ttu-id="15fde-146">Warunkowe logiczne OR operator | |</span><span class="sxs-lookup"><span data-stu-id="15fde-146">Conditional logical OR operator ||</span></span>

<span data-ttu-id="15fde-147">Warunkowy operator `||`logiczny or, nazywany także "operatorem" krótki-obwód ", oblicza wartość logiczną lub argumentów operacji.</span><span class="sxs-lookup"><span data-stu-id="15fde-147">The conditional logical OR operator `||`, also known as the "short-circuiting" logical OR operator, computes the logical OR of its operands.</span></span> <span data-ttu-id="15fde-148">Wynik `x || y` jest, jeśli `true` `x` lub `y` jest obliczany do `true`.</span><span class="sxs-lookup"><span data-stu-id="15fde-148">The result of `x || y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="15fde-149">W przeciwnym razie wynik jest `false`.</span><span class="sxs-lookup"><span data-stu-id="15fde-149">Otherwise, the result is `false`.</span></span> <span data-ttu-id="15fde-150">Jeśli `x` ma wartość `true`, `y` nie jest oceniane.</span><span class="sxs-lookup"><span data-stu-id="15fde-150">If `x` evaluates to `true`, `y` is not evaluated.</span></span>

<span data-ttu-id="15fde-151">W poniższym przykładzie operand z prawej strony `||` operatora jest wywołaniem metody, które nie jest wykonywane, jeśli argument operacji po lewej stronie ma `true`wartość:</span><span class="sxs-lookup"><span data-stu-id="15fde-151">In the following example, the right-hand operand of the `||` operator is a method call, which isn't performed if the left-hand operand evaluates to `true`:</span></span>

[!code-csharp-interactive[conditional logical OR](snippets/BooleanLogicalOperators.cs#ConditionalOr)]

<span data-ttu-id="15fde-152">`|` [Operator logiczny or](#logical-or-operator-) oblicza również wartość logiczną lub argumentów operacji, ale zawsze oblicza oba operandy.</span><span class="sxs-lookup"><span data-stu-id="15fde-152">The [logical OR operator](#logical-or-operator-) `|` also computes the logical OR of its operands, but always evaluates both operands.</span></span>

## <a name="nullable-boolean-logical-operators"></a><span data-ttu-id="15fde-153">Logiczne operatory wartości null</span><span class="sxs-lookup"><span data-stu-id="15fde-153">Nullable Boolean logical operators</span></span>

<span data-ttu-id="15fde-154">Dla `bool?` operandów operatory `&` i `|` obsługują logikę z trzema wartościami.</span><span class="sxs-lookup"><span data-stu-id="15fde-154">For `bool?` operands, the `&` and `|` operators support the three-valued logic.</span></span> <span data-ttu-id="15fde-155">Semantyka tych operatorów jest definiowana przez następującą tabelę:</span><span class="sxs-lookup"><span data-stu-id="15fde-155">The semantics of these operators is defined by the following table:</span></span>  
  
|<span data-ttu-id="15fde-156">x</span><span class="sxs-lookup"><span data-stu-id="15fde-156">x</span></span>|<span data-ttu-id="15fde-157">t</span><span class="sxs-lookup"><span data-stu-id="15fde-157">y</span></span>|<span data-ttu-id="15fde-158">x&y</span><span class="sxs-lookup"><span data-stu-id="15fde-158">x&y</span></span>|<span data-ttu-id="15fde-159">x&#124;y</span><span class="sxs-lookup"><span data-stu-id="15fde-159">x&#124;y</span></span>|  
|----|----|----|----|  
|<span data-ttu-id="15fde-160">true</span><span class="sxs-lookup"><span data-stu-id="15fde-160">true</span></span>|<span data-ttu-id="15fde-161">true</span><span class="sxs-lookup"><span data-stu-id="15fde-161">true</span></span>|<span data-ttu-id="15fde-162">true</span><span class="sxs-lookup"><span data-stu-id="15fde-162">true</span></span>|<span data-ttu-id="15fde-163">true</span><span class="sxs-lookup"><span data-stu-id="15fde-163">true</span></span>|  
|<span data-ttu-id="15fde-164">true</span><span class="sxs-lookup"><span data-stu-id="15fde-164">true</span></span>|<span data-ttu-id="15fde-165">fałsz</span><span class="sxs-lookup"><span data-stu-id="15fde-165">false</span></span>|<span data-ttu-id="15fde-166">fałsz</span><span class="sxs-lookup"><span data-stu-id="15fde-166">false</span></span>|<span data-ttu-id="15fde-167">true</span><span class="sxs-lookup"><span data-stu-id="15fde-167">true</span></span>|  
|<span data-ttu-id="15fde-168">true</span><span class="sxs-lookup"><span data-stu-id="15fde-168">true</span></span>|<span data-ttu-id="15fde-169">wartość null</span><span class="sxs-lookup"><span data-stu-id="15fde-169">null</span></span>|<span data-ttu-id="15fde-170">wartość null</span><span class="sxs-lookup"><span data-stu-id="15fde-170">null</span></span>|<span data-ttu-id="15fde-171">true</span><span class="sxs-lookup"><span data-stu-id="15fde-171">true</span></span>|  
|<span data-ttu-id="15fde-172">fałsz</span><span class="sxs-lookup"><span data-stu-id="15fde-172">false</span></span>|<span data-ttu-id="15fde-173">true</span><span class="sxs-lookup"><span data-stu-id="15fde-173">true</span></span>|<span data-ttu-id="15fde-174">fałsz</span><span class="sxs-lookup"><span data-stu-id="15fde-174">false</span></span>|<span data-ttu-id="15fde-175">true</span><span class="sxs-lookup"><span data-stu-id="15fde-175">true</span></span>|  
|<span data-ttu-id="15fde-176">fałsz</span><span class="sxs-lookup"><span data-stu-id="15fde-176">false</span></span>|<span data-ttu-id="15fde-177">fałsz</span><span class="sxs-lookup"><span data-stu-id="15fde-177">false</span></span>|<span data-ttu-id="15fde-178">fałsz</span><span class="sxs-lookup"><span data-stu-id="15fde-178">false</span></span>|<span data-ttu-id="15fde-179">fałsz</span><span class="sxs-lookup"><span data-stu-id="15fde-179">false</span></span>|  
|<span data-ttu-id="15fde-180">fałsz</span><span class="sxs-lookup"><span data-stu-id="15fde-180">false</span></span>|<span data-ttu-id="15fde-181">wartość null</span><span class="sxs-lookup"><span data-stu-id="15fde-181">null</span></span>|<span data-ttu-id="15fde-182">fałsz</span><span class="sxs-lookup"><span data-stu-id="15fde-182">false</span></span>|<span data-ttu-id="15fde-183">wartość null</span><span class="sxs-lookup"><span data-stu-id="15fde-183">null</span></span>|  
|<span data-ttu-id="15fde-184">wartość null</span><span class="sxs-lookup"><span data-stu-id="15fde-184">null</span></span>|<span data-ttu-id="15fde-185">true</span><span class="sxs-lookup"><span data-stu-id="15fde-185">true</span></span>|<span data-ttu-id="15fde-186">wartość null</span><span class="sxs-lookup"><span data-stu-id="15fde-186">null</span></span>|<span data-ttu-id="15fde-187">true</span><span class="sxs-lookup"><span data-stu-id="15fde-187">true</span></span>|  
|<span data-ttu-id="15fde-188">wartość null</span><span class="sxs-lookup"><span data-stu-id="15fde-188">null</span></span>|<span data-ttu-id="15fde-189">fałsz</span><span class="sxs-lookup"><span data-stu-id="15fde-189">false</span></span>|<span data-ttu-id="15fde-190">fałsz</span><span class="sxs-lookup"><span data-stu-id="15fde-190">false</span></span>|<span data-ttu-id="15fde-191">wartość null</span><span class="sxs-lookup"><span data-stu-id="15fde-191">null</span></span>|  
|<span data-ttu-id="15fde-192">wartość null</span><span class="sxs-lookup"><span data-stu-id="15fde-192">null</span></span>|<span data-ttu-id="15fde-193">wartość null</span><span class="sxs-lookup"><span data-stu-id="15fde-193">null</span></span>|<span data-ttu-id="15fde-194">wartość null</span><span class="sxs-lookup"><span data-stu-id="15fde-194">null</span></span>|<span data-ttu-id="15fde-195">wartość null</span><span class="sxs-lookup"><span data-stu-id="15fde-195">null</span></span>|  

<span data-ttu-id="15fde-196">Zachowanie tych operatorów różni się od typowego zachowania operatora z zerowymi typami wartości.</span><span class="sxs-lookup"><span data-stu-id="15fde-196">The behavior of those operators differs from the typical operator behavior with nullable value types.</span></span> <span data-ttu-id="15fde-197">Zazwyczaj operator, który jest zdefiniowany dla operandów typu wartości, może być również używany z operandami odpowiadającego typu wartości null.</span><span class="sxs-lookup"><span data-stu-id="15fde-197">Typically, an operator which is defined for operands of a value type can be also used with operands of the corresponding nullable value type.</span></span> <span data-ttu-id="15fde-198">Taki operator wytwarza `null` , jeśli którykolwiek z jego operandów zwróci wartość `null`.</span><span class="sxs-lookup"><span data-stu-id="15fde-198">Such an operator produces `null` if any of its operands evaluates to `null`.</span></span> <span data-ttu-id="15fde-199">Jednak operatory `&` i mogą `|` generować wartości inne niż null, nawet jeśli jeden z operandów jest wynikiem `null`.</span><span class="sxs-lookup"><span data-stu-id="15fde-199">However, the `&` and `|` operators can produce non-null even if one of the operands evaluates to `null`.</span></span> <span data-ttu-id="15fde-200">Aby uzyskać więcej informacji o zachowaniu operatora z typem wartości null, zobacz sekcję [zniesione operatory](../builtin-types/nullable-value-types.md#lifted-operators) w artykule [typy wartości null](../builtin-types/nullable-value-types.md) .</span><span class="sxs-lookup"><span data-stu-id="15fde-200">For more information about the operator behavior with nullable value types, see the [Lifted operators](../builtin-types/nullable-value-types.md#lifted-operators) section of the [Nullable value types](../builtin-types/nullable-value-types.md) article.</span></span>

<span data-ttu-id="15fde-201">Można również użyć operatorów `!` i `^` z `bool?` operandami, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="15fde-201">You can also use the `!` and `^` operators with `bool?` operands, as the following example shows:</span></span>

[!code-csharp-interactive[lifted negation and xor](snippets/BooleanLogicalOperators.cs#WithNullableBoolean)]

<span data-ttu-id="15fde-202">Operatory `&&` logiczne warunkowe i `||` nie obsługują `bool?` argumentów operacji.</span><span class="sxs-lookup"><span data-stu-id="15fde-202">The conditional logical operators `&&` and `||` don't support `bool?` operands.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="15fde-203">Przypisanie złożone</span><span class="sxs-lookup"><span data-stu-id="15fde-203">Compound assignment</span></span>

<span data-ttu-id="15fde-204">Dla operatora `op`binarnego wyrażenie złożonego przypisania formularza</span><span class="sxs-lookup"><span data-stu-id="15fde-204">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="15fde-205">jest równoważny</span><span class="sxs-lookup"><span data-stu-id="15fde-205">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="15fde-206">z tą `x` różnicą, że jest obliczana tylko raz.</span><span class="sxs-lookup"><span data-stu-id="15fde-206">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="15fde-207">Operatory `&`, `|`i `^` obsługują przypisanie złożone, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="15fde-207">The `&`, `|`, and `^` operators support compound assignment, as the following example shows:</span></span>

[!code-csharp-interactive[compound assignment](snippets/BooleanLogicalOperators.cs#CompoundAssignment)]

> [!NOTE]
> <span data-ttu-id="15fde-208">Warunkowe operatory `&&` logiczne i `||` nie obsługują przypisania złożonego.</span><span class="sxs-lookup"><span data-stu-id="15fde-208">The conditional logical operators `&&` and `||` don't support compound assignment.</span></span>

## <a name="operator-precedence"></a><span data-ttu-id="15fde-209">Pierwszeństwo operatorów</span><span class="sxs-lookup"><span data-stu-id="15fde-209">Operator precedence</span></span>

<span data-ttu-id="15fde-210">Poniższa lista porządkuje operatory logiczne rozpoczynając od najwyższego priorytetu do najniższego:</span><span class="sxs-lookup"><span data-stu-id="15fde-210">The following list orders logical operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="15fde-211">Operator logiczny negacji`!`</span><span class="sxs-lookup"><span data-stu-id="15fde-211">Logical negation operator `!`</span></span>
- <span data-ttu-id="15fde-212">Operator logiczny AND`&`</span><span class="sxs-lookup"><span data-stu-id="15fde-212">Logical AND operator `&`</span></span>
- <span data-ttu-id="15fde-213">Operator wyłączny logicznego OR`^`</span><span class="sxs-lookup"><span data-stu-id="15fde-213">Logical exclusive OR operator `^`</span></span>
- <span data-ttu-id="15fde-214">Operator logiczny OR`|`</span><span class="sxs-lookup"><span data-stu-id="15fde-214">Logical OR operator `|`</span></span>
- <span data-ttu-id="15fde-215">Warunkowe operatory logiczne i`&&`</span><span class="sxs-lookup"><span data-stu-id="15fde-215">Conditional logical AND operator `&&`</span></span>
- <span data-ttu-id="15fde-216">Warunkowy operator logiczny OR`||`</span><span class="sxs-lookup"><span data-stu-id="15fde-216">Conditional logical OR operator `||`</span></span>

<span data-ttu-id="15fde-217">Użyj nawiasów, `()`aby zmienić kolejność oceny nałożona przez pierwszeństwo operatorów:</span><span class="sxs-lookup"><span data-stu-id="15fde-217">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence:</span></span>

[!code-csharp-interactive[operator precedence](snippets/BooleanLogicalOperators.cs#Precedence)]

<span data-ttu-id="15fde-218">Aby uzyskać pełną listę operatorów języka C# uporządkowanych według poziomu pierwszeństwa, zobacz sekcję [pierwszeństwo](index.md#operator-precedence) operatorów w artykule [operatory języka c#](index.md) .</span><span class="sxs-lookup"><span data-stu-id="15fde-218">For the complete list of C# operators ordered by precedence level, see the [Operator precedence](index.md#operator-precedence) section of the [C# operators](index.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="15fde-219">Przeciążanie operatora</span><span class="sxs-lookup"><span data-stu-id="15fde-219">Operator overloadability</span></span>

<span data-ttu-id="15fde-220">Typ zdefiniowany przez użytkownika może [przeciążać](operator-overloading.md) `!`operatory `&`, `|`,, `^` i.</span><span class="sxs-lookup"><span data-stu-id="15fde-220">A user-defined type can [overload](operator-overloading.md) the `!`, `&`, `|`, and `^` operators.</span></span> <span data-ttu-id="15fde-221">Gdy operator binarny jest przeciążony, odpowiadający mu operator przypisania złożonego jest również niejawnie przeciążony.</span><span class="sxs-lookup"><span data-stu-id="15fde-221">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="15fde-222">Typ zdefiniowany przez użytkownika nie może jawnie przeciążać złożonego operatora przypisania.</span><span class="sxs-lookup"><span data-stu-id="15fde-222">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

<span data-ttu-id="15fde-223">Typ zdefiniowany przez użytkownika nie może przeciążać warunkowych `&&` operatorów `||`logicznych i.</span><span class="sxs-lookup"><span data-stu-id="15fde-223">A user-defined type cannot overload the conditional logical operators `&&` and `||`.</span></span> <span data-ttu-id="15fde-224">Jednakże, jeśli typ zdefiniowany przez użytkownika przeciążuje [Operatory true i false](true-false-operators.md) oraz operator `&` or `|` w określony sposób, `&&` lub `||` operację, odpowiednio, można obliczyć dla operandów tego typu.</span><span class="sxs-lookup"><span data-stu-id="15fde-224">However, if a user-defined type overloads the [true and false operators](true-false-operators.md) and the `&` or `|` operator in a certain way, the `&&` or `||` operation, respectively, can be evaluated for the operands of that type.</span></span> <span data-ttu-id="15fde-225">Aby uzyskać więcej informacji, zapoznaj się z sekcją wyrażenia [warunkowe operatory logiczne zdefiniowane przez użytkownika](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) w [specyfikacji języka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="15fde-225">For more information, see the [User-defined conditional logical operators](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="15fde-226">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="15fde-226">C# language specification</span></span>

<span data-ttu-id="15fde-227">Aby uzyskać więcej informacji, zobacz następujące sekcje [specyfikacji języka C#](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="15fde-227">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="15fde-228">Operator logiczny negacji</span><span class="sxs-lookup"><span data-stu-id="15fde-228">Logical negation operator</span></span>](~/_csharplang/spec/expressions.md#logical-negation-operator)
- [<span data-ttu-id="15fde-229">Operatory logiczne</span><span class="sxs-lookup"><span data-stu-id="15fde-229">Logical operators</span></span>](~/_csharplang/spec/expressions.md#logical-operators)
- [<span data-ttu-id="15fde-230">Warunkowe operatory logiczne</span><span class="sxs-lookup"><span data-stu-id="15fde-230">Conditional logical operators</span></span>](~/_csharplang/spec/expressions.md#conditional-logical-operators)
- [<span data-ttu-id="15fde-231">Przypisanie złożone</span><span class="sxs-lookup"><span data-stu-id="15fde-231">Compound assignment</span></span>](~/_csharplang/spec/expressions.md#compound-assignment)

## <a name="see-also"></a><span data-ttu-id="15fde-232">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="15fde-232">See also</span></span>

- [<span data-ttu-id="15fde-233">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="15fde-233">C# reference</span></span>](../index.md)
- [<span data-ttu-id="15fde-234">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="15fde-234">C# operators</span></span>](index.md)
- [<span data-ttu-id="15fde-235">Operatory przesunięcia i operatory bitowe</span><span class="sxs-lookup"><span data-stu-id="15fde-235">Bitwise and shift operators</span></span>](bitwise-and-shift-operators.md)
