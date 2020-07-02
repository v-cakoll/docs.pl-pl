---
title: Boolean operatory logiczne — odwołanie w C#
description: Dowiedz się więcej na temat operatorów języka C#, które wykonują logiczne negacje, połączenie (i), a także wyłączne operacje odłączenia (lub) z argumentami operacji logicznych.
ms.date: 06/29/2020
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
ms.openlocfilehash: a19c804c624153ef608885bc6493537302275765
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618197"
---
# <a name="boolean-logical-operators-c-reference"></a><span data-ttu-id="2f873-103">Boolean operatory logiczne (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="2f873-103">Boolean logical operators (C# reference)</span></span>

<span data-ttu-id="2f873-104">Następujące operatory wykonują operacje logiczne z argumentami operacji [bool](../builtin-types/bool.md) :</span><span class="sxs-lookup"><span data-stu-id="2f873-104">The following operators perform logical operations with [bool](../builtin-types/bool.md) operands:</span></span>

- <span data-ttu-id="2f873-105">Operator jednoargumentowy [ `!` (logiczne Negacja)](#logical-negation-operator-) .</span><span class="sxs-lookup"><span data-stu-id="2f873-105">Unary [`!` (logical negation)](#logical-negation-operator-) operator.</span></span>
- <span data-ttu-id="2f873-106">Operatory binarne [ `&` (logiczne i)](#logical-and-operator-), [ `|` (logiczne lub)](#logical-or-operator-)i [ `^` (logiczne wyłączne lub)](#logical-exclusive-or-operator-) .</span><span class="sxs-lookup"><span data-stu-id="2f873-106">Binary [`&` (logical AND)](#logical-and-operator-), [`|` (logical OR)](#logical-or-operator-), and [`^` (logical exclusive OR)](#logical-exclusive-or-operator-) operators.</span></span> <span data-ttu-id="2f873-107">Te operatory zawsze obliczają oba operandy.</span><span class="sxs-lookup"><span data-stu-id="2f873-107">Those operators always evaluate both operands.</span></span>
- <span data-ttu-id="2f873-108">Binary [ `&&` (warunkowe logiczne i)](#conditional-logical-and-operator-) oraz operatory [ `||` warunkowe logiczne or](#conditional-logical-or-operator-) .</span><span class="sxs-lookup"><span data-stu-id="2f873-108">Binary [`&&` (conditional logical AND)](#conditional-logical-and-operator-) and [`||` (conditional logical OR)](#conditional-logical-or-operator-) operators.</span></span> <span data-ttu-id="2f873-109">Te operatory obliczają operand z prawej strony tylko wtedy, gdy jest to konieczne.</span><span class="sxs-lookup"><span data-stu-id="2f873-109">Those operators evaluate the right-hand operand only if it's necessary.</span></span>

<span data-ttu-id="2f873-110">W przypadku operandów [całkowitych typów liczbowych](../builtin-types/integral-numeric-types.md) `&` operatory, `|` i `^` wykonują bitowe operacje logiczne.</span><span class="sxs-lookup"><span data-stu-id="2f873-110">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `&`, `|`, and `^` operators perform bitwise logical operations.</span></span> <span data-ttu-id="2f873-111">Aby uzyskać więcej informacji, zobacz [Operatory bitowe i przesunięcia](bitwise-and-shift-operators.md).</span><span class="sxs-lookup"><span data-stu-id="2f873-111">For more information, see [Bitwise and shift operators](bitwise-and-shift-operators.md).</span></span>

## <a name="logical-negation-operator-"></a><span data-ttu-id="2f873-112">Operator logiczny negacji</span><span class="sxs-lookup"><span data-stu-id="2f873-112">Logical negation operator !</span></span>

<span data-ttu-id="2f873-113">Jednoargumentowy `!` operator prefiksu oblicza logiczne Negacja operandu.</span><span class="sxs-lookup"><span data-stu-id="2f873-113">The unary prefix `!` operator computes logical negation of its operand.</span></span> <span data-ttu-id="2f873-114">To znaczy, `true` gdy operand jest obliczany do `false` , i `false` , jeśli operand ma wartość `true` :</span><span class="sxs-lookup"><span data-stu-id="2f873-114">That is, it produces `true`, if the operand evaluates to `false`, and `false`, if the operand evaluates to `true`:</span></span>

[!code-csharp-interactive[logical negation](snippets/BooleanLogicalOperators.cs#Negation)]

<span data-ttu-id="2f873-115">Począwszy od języka C# 8,0, jednoargumentowy operator przyrostkowy `!` jest [operatorem łagodniejszej o wartości null](null-forgiving.md).</span><span class="sxs-lookup"><span data-stu-id="2f873-115">Beginning with C# 8.0, the unary postfix `!` operator is the [null-forgiving operator](null-forgiving.md).</span></span>

## <a name="logical-and-operator-amp"></a><a name="logical-and-operator-"></a><span data-ttu-id="2f873-116">Operator logiczny AND&amp;</span><span class="sxs-lookup"><span data-stu-id="2f873-116">Logical AND operator &amp;</span></span>

<span data-ttu-id="2f873-117">`&`Operator oblicza wartość logiczną i jej operandów.</span><span class="sxs-lookup"><span data-stu-id="2f873-117">The `&` operator computes the logical AND of its operands.</span></span> <span data-ttu-id="2f873-118">Wynik `x & y` jest `true` Jeśli oba i są `x` `y` oceniane do `true` .</span><span class="sxs-lookup"><span data-stu-id="2f873-118">The result of `x & y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="2f873-119">W przeciwnym razie wynik jest `false` .</span><span class="sxs-lookup"><span data-stu-id="2f873-119">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="2f873-120">`&`Operator oblicza oba operandy, nawet jeśli argument operacji po lewej stronie jest obliczany do `false` , tak że wynik operacji jest `false` niezależnie od wartości operandu po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="2f873-120">The `&` operator evaluates both operands even if the left-hand operand evaluates to `false`, so that the operation result is `false` regardless of the value of the right-hand operand.</span></span>

<span data-ttu-id="2f873-121">W poniższym przykładzie operand z prawej strony `&` operatora jest wywołaniem metody, które jest wykonywane niezależnie od wartości operandu po lewej stronie:</span><span class="sxs-lookup"><span data-stu-id="2f873-121">In the following example, the right-hand operand of the `&` operator is a method call, which is performed regardless of the value of the left-hand operand:</span></span>

[!code-csharp-interactive[logical AND](snippets/BooleanLogicalOperators.cs#And)]

<span data-ttu-id="2f873-122">[Warunkowy operator logiczny and](#conditional-logical-and-operator-) `&&` oblicza również wartość logiczną i jej operandy, ale nie oblicza wartości argumentu po prawej stronie, jeśli argument operacji po lewej stronie ma wartość `false` .</span><span class="sxs-lookup"><span data-stu-id="2f873-122">The [conditional logical AND operator](#conditional-logical-and-operator-) `&&` also computes the logical AND of its operands, but doesn't evaluate the right-hand operand if the left-hand operand evaluates to `false`.</span></span>

<span data-ttu-id="2f873-123">Dla operandów [całkowitych typów liczbowych](../builtin-types/integral-numeric-types.md) `&` operator oblicza koniunkcję [bitową i](bitwise-and-shift-operators.md#logical-and-operator-) jej operandy.</span><span class="sxs-lookup"><span data-stu-id="2f873-123">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `&` operator computes the [bitwise logical AND](bitwise-and-shift-operators.md#logical-and-operator-) of its operands.</span></span> <span data-ttu-id="2f873-124">Operator jednoargumentowy jest operatorem `&` [Address-of](pointer-related-operators.md#address-of-operator-).</span><span class="sxs-lookup"><span data-stu-id="2f873-124">The unary `&` operator is the [address-of operator](pointer-related-operators.md#address-of-operator-).</span></span>

## <a name="logical-exclusive-or-operator-"></a><span data-ttu-id="2f873-125">Operator wyłączny logicznego OR ^</span><span class="sxs-lookup"><span data-stu-id="2f873-125">Logical exclusive OR operator ^</span></span>

<span data-ttu-id="2f873-126">`^`Operator oblicza wartość logiczną na wyłączność lub, znaną również jako logiczna XOR, dla argumentów operacji.</span><span class="sxs-lookup"><span data-stu-id="2f873-126">The `^` operator computes the logical exclusive OR, also known as the logical XOR, of its operands.</span></span> <span data-ttu-id="2f873-127">Wynik jest w `x ^ y` `true` przypadku, gdy jest `x` obliczany i obliczany do `true` `y` `false` , lub `x` szacuje `false` `y` `true` się w.</span><span class="sxs-lookup"><span data-stu-id="2f873-127">The result of `x ^ y` is `true` if `x` evaluates to `true` and `y` evaluates to `false`, or `x` evaluates to `false` and `y` evaluates to `true`.</span></span> <span data-ttu-id="2f873-128">W przeciwnym razie wynik jest `false` .</span><span class="sxs-lookup"><span data-stu-id="2f873-128">Otherwise, the result is `false`.</span></span> <span data-ttu-id="2f873-129">Oznacza to, że dla `bool` operandów `^` operator oblicza ten sam wynik jako [operator nierówności](equality-operators.md#inequality-operator-) `!=` .</span><span class="sxs-lookup"><span data-stu-id="2f873-129">That is, for the `bool` operands, the `^` operator computes the same result as the [inequality operator](equality-operators.md#inequality-operator-) `!=`.</span></span>

[!code-csharp-interactive[logical exclusive OR](snippets/BooleanLogicalOperators.cs#Xor)]

<span data-ttu-id="2f873-130">W przypadku operandów [całkowitych typów liczbowych](../builtin-types/integral-numeric-types.md) `^` operator oblicza [bitową logiczną na wyłączność lub](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) z jej argumentów operacji.</span><span class="sxs-lookup"><span data-stu-id="2f873-130">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `^` operator computes the [bitwise logical exclusive OR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) of its operands.</span></span>

## <a name="logical-or-operator-"></a><span data-ttu-id="2f873-131">Operator logiczny OR |</span><span class="sxs-lookup"><span data-stu-id="2f873-131">Logical OR operator |</span></span>

<span data-ttu-id="2f873-132">`|`Operator oblicza wartość logiczną lub argumentów operacji.</span><span class="sxs-lookup"><span data-stu-id="2f873-132">The `|` operator computes the logical OR of its operands.</span></span> <span data-ttu-id="2f873-133">Wynik jest, `x | y` `true` Jeśli lub jest `x` `y` obliczany do `true` .</span><span class="sxs-lookup"><span data-stu-id="2f873-133">The result of `x | y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="2f873-134">W przeciwnym razie wynik jest `false` .</span><span class="sxs-lookup"><span data-stu-id="2f873-134">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="2f873-135">`|`Operator oblicza oba operandy, nawet jeśli argument operacji po lewej stronie jest obliczany do `true` , tak że wynik operacji jest `true` niezależnie od wartości operandu po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="2f873-135">The `|` operator evaluates both operands even if the left-hand operand evaluates to `true`, so that the operation result is `true` regardless of the value of the right-hand operand.</span></span>

<span data-ttu-id="2f873-136">W poniższym przykładzie operand z prawej strony `|` operatora jest wywołaniem metody, które jest wykonywane niezależnie od wartości operandu po lewej stronie:</span><span class="sxs-lookup"><span data-stu-id="2f873-136">In the following example, the right-hand operand of the `|` operator is a method call, which is performed regardless of the value of the left-hand operand:</span></span>

[!code-csharp-interactive[logical OR](snippets/BooleanLogicalOperators.cs#Or)]

<span data-ttu-id="2f873-137">[Operator logiczny or](#conditional-logical-or-operator-) `||` oblicza również wartość logiczną lub jej operandy, ale nie oblicza wartości operandu po prawej stronie, jeśli argument operacji po lewej stronie ma wartość `true` .</span><span class="sxs-lookup"><span data-stu-id="2f873-137">The [conditional logical OR operator](#conditional-logical-or-operator-) `||` also computes the logical OR of its operands, but doesn't evaluate the right-hand operand if the left-hand operand evaluates to `true`.</span></span>

<span data-ttu-id="2f873-138">Dla argumentów operacji [całkowitych typów liczbowych](../builtin-types/integral-numeric-types.md) `|` operator oblicza bitową koniunkcję [logiczną lub](bitwise-and-shift-operators.md#logical-or-operator-) argumentów operacji.</span><span class="sxs-lookup"><span data-stu-id="2f873-138">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `|` operator computes the [bitwise logical OR](bitwise-and-shift-operators.md#logical-or-operator-) of its operands.</span></span>

## <a name="conditional-logical-and-operator-ampamp"></a><a name="conditional-logical-and-operator-"></a><span data-ttu-id="2f873-139">Warunkowe operatory logiczne i&amp;&amp;</span><span class="sxs-lookup"><span data-stu-id="2f873-139">Conditional logical AND operator &amp;&amp;</span></span>

<span data-ttu-id="2f873-140">Warunkowy operator logiczny AND `&&` , znany także jako operator logiczny "krótki-obwód", oblicza wartość logiczną i argumentów operacji.</span><span class="sxs-lookup"><span data-stu-id="2f873-140">The conditional logical AND operator `&&`, also known as the "short-circuiting" logical AND operator, computes the logical AND of its operands.</span></span> <span data-ttu-id="2f873-141">Wynik `x && y` jest `true` Jeśli oba i są `x` `y` oceniane do `true` .</span><span class="sxs-lookup"><span data-stu-id="2f873-141">The result of `x && y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="2f873-142">W przeciwnym razie wynik jest `false` .</span><span class="sxs-lookup"><span data-stu-id="2f873-142">Otherwise, the result is `false`.</span></span> <span data-ttu-id="2f873-143">Jeśli ma `x` wartość `false` , `y` nie jest oceniane.</span><span class="sxs-lookup"><span data-stu-id="2f873-143">If `x` evaluates to `false`, `y` is not evaluated.</span></span>

<span data-ttu-id="2f873-144">W poniższym przykładzie operand z prawej strony `&&` operatora jest wywołaniem metody, które nie jest wykonywane, jeśli argument operacji po lewej stronie ma wartość `false` :</span><span class="sxs-lookup"><span data-stu-id="2f873-144">In the following example, the right-hand operand of the `&&` operator is a method call, which isn't performed if the left-hand operand evaluates to `false`:</span></span>

[!code-csharp-interactive[conditional logical AND](snippets/BooleanLogicalOperators.cs#ConditionalAnd)]

<span data-ttu-id="2f873-145">[Operator logiczny and](#logical-and-operator-) `&` oblicza również wartość logiczną i jej operandy, ale zawsze oblicza oba operandy.</span><span class="sxs-lookup"><span data-stu-id="2f873-145">The [logical AND operator](#logical-and-operator-) `&` also computes the logical AND of its operands, but always evaluates both operands.</span></span>

## <a name="conditional-logical-or-operator-"></a><span data-ttu-id="2f873-146">Warunkowe logiczne OR operator | |</span><span class="sxs-lookup"><span data-stu-id="2f873-146">Conditional logical OR operator ||</span></span>

<span data-ttu-id="2f873-147">Warunkowy operator logiczny OR `||` , nazywany także "operatorem" krótki-obwód ", oblicza wartość logiczną lub argumentów operacji.</span><span class="sxs-lookup"><span data-stu-id="2f873-147">The conditional logical OR operator `||`, also known as the "short-circuiting" logical OR operator, computes the logical OR of its operands.</span></span> <span data-ttu-id="2f873-148">Wynik jest, `x || y` `true` Jeśli lub jest `x` `y` obliczany do `true` .</span><span class="sxs-lookup"><span data-stu-id="2f873-148">The result of `x || y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="2f873-149">W przeciwnym razie wynik jest `false` .</span><span class="sxs-lookup"><span data-stu-id="2f873-149">Otherwise, the result is `false`.</span></span> <span data-ttu-id="2f873-150">Jeśli ma `x` wartość `true` , `y` nie jest oceniane.</span><span class="sxs-lookup"><span data-stu-id="2f873-150">If `x` evaluates to `true`, `y` is not evaluated.</span></span>

<span data-ttu-id="2f873-151">W poniższym przykładzie operand z prawej strony `||` operatora jest wywołaniem metody, które nie jest wykonywane, jeśli argument operacji po lewej stronie ma wartość `true` :</span><span class="sxs-lookup"><span data-stu-id="2f873-151">In the following example, the right-hand operand of the `||` operator is a method call, which isn't performed if the left-hand operand evaluates to `true`:</span></span>

[!code-csharp-interactive[conditional logical OR](snippets/BooleanLogicalOperators.cs#ConditionalOr)]

<span data-ttu-id="2f873-152">[Operator logiczny or](#logical-or-operator-) `|` oblicza również wartość logiczną lub argumentów operacji, ale zawsze oblicza oba operandy.</span><span class="sxs-lookup"><span data-stu-id="2f873-152">The [logical OR operator](#logical-or-operator-) `|` also computes the logical OR of its operands, but always evaluates both operands.</span></span>

## <a name="nullable-boolean-logical-operators"></a><span data-ttu-id="2f873-153">Logiczne operatory wartości null</span><span class="sxs-lookup"><span data-stu-id="2f873-153">Nullable Boolean logical operators</span></span>

<span data-ttu-id="2f873-154">Dla `bool?` operandów operatory [ `&` (logiczne i)](#logical-and-operator-) i [ `|` (logiczne or)](#logical-or-operator-) obsługują logikę o wartości trójwarstwowej w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="2f873-154">For `bool?` operands, the [`&` (logical AND)](#logical-and-operator-) and [`|` (logical OR)](#logical-or-operator-) operators support the three-valued logic as follows:</span></span>

- <span data-ttu-id="2f873-155">`&`Operator produkuje `true` tylko wtedy, gdy oba jego operandy są szacowane do `true` .</span><span class="sxs-lookup"><span data-stu-id="2f873-155">The `&` operator produces `true` only if both its operands evaluate to `true`.</span></span> <span data-ttu-id="2f873-156">Jeśli `x` lub `y` jest obliczany do `false` , `x & y` powstaje `false` (nawet jeśli inny operand jest obliczany do `null` ).</span><span class="sxs-lookup"><span data-stu-id="2f873-156">If either `x` or `y` evaluates to `false`, `x & y` produces `false` (even if another operand evaluates to `null`).</span></span> <span data-ttu-id="2f873-157">W przeciwnym razie wynik `x & y` jest `null` .</span><span class="sxs-lookup"><span data-stu-id="2f873-157">Otherwise, the result of `x & y` is `null`.</span></span>

- <span data-ttu-id="2f873-158">`|`Operator produkuje `false` tylko wtedy, gdy oba jego operandy są szacowane do `false` .</span><span class="sxs-lookup"><span data-stu-id="2f873-158">The `|` operator produces `false` only if both its operands evaluate to `false`.</span></span> <span data-ttu-id="2f873-159">Jeśli `x` lub `y` jest obliczany do `true` , `x | y` powstaje `true` (nawet jeśli inny operand jest obliczany do `null` ).</span><span class="sxs-lookup"><span data-stu-id="2f873-159">If either `x` or `y` evaluates to `true`, `x | y` produces `true` (even if another operand evaluates to `null`).</span></span> <span data-ttu-id="2f873-160">W przeciwnym razie wynik `x | y` jest `null` .</span><span class="sxs-lookup"><span data-stu-id="2f873-160">Otherwise, the result of `x | y` is `null`.</span></span>

<span data-ttu-id="2f873-161">W poniższej tabeli przedstawiono semantykę:</span><span class="sxs-lookup"><span data-stu-id="2f873-161">The following table presents that semantics:</span></span>

|<span data-ttu-id="2f873-162">x</span><span class="sxs-lookup"><span data-stu-id="2f873-162">x</span></span>|<span data-ttu-id="2f873-163">Y</span><span class="sxs-lookup"><span data-stu-id="2f873-163">y</span></span>|<span data-ttu-id="2f873-164">x&y</span><span class="sxs-lookup"><span data-stu-id="2f873-164">x&y</span></span>|<span data-ttu-id="2f873-165">x&#124;y</span><span class="sxs-lookup"><span data-stu-id="2f873-165">x&#124;y</span></span>|  
|----|----|----|----|  
|<span data-ttu-id="2f873-166">true</span><span class="sxs-lookup"><span data-stu-id="2f873-166">true</span></span>|<span data-ttu-id="2f873-167">true</span><span class="sxs-lookup"><span data-stu-id="2f873-167">true</span></span>|<span data-ttu-id="2f873-168">true</span><span class="sxs-lookup"><span data-stu-id="2f873-168">true</span></span>|<span data-ttu-id="2f873-169">true</span><span class="sxs-lookup"><span data-stu-id="2f873-169">true</span></span>|  
|<span data-ttu-id="2f873-170">true</span><span class="sxs-lookup"><span data-stu-id="2f873-170">true</span></span>|<span data-ttu-id="2f873-171">fałsz</span><span class="sxs-lookup"><span data-stu-id="2f873-171">false</span></span>|<span data-ttu-id="2f873-172">fałsz</span><span class="sxs-lookup"><span data-stu-id="2f873-172">false</span></span>|<span data-ttu-id="2f873-173">true</span><span class="sxs-lookup"><span data-stu-id="2f873-173">true</span></span>|  
|<span data-ttu-id="2f873-174">true</span><span class="sxs-lookup"><span data-stu-id="2f873-174">true</span></span>|<span data-ttu-id="2f873-175">wartość null</span><span class="sxs-lookup"><span data-stu-id="2f873-175">null</span></span>|<span data-ttu-id="2f873-176">wartość null</span><span class="sxs-lookup"><span data-stu-id="2f873-176">null</span></span>|<span data-ttu-id="2f873-177">true</span><span class="sxs-lookup"><span data-stu-id="2f873-177">true</span></span>|  
|<span data-ttu-id="2f873-178">fałsz</span><span class="sxs-lookup"><span data-stu-id="2f873-178">false</span></span>|<span data-ttu-id="2f873-179">true</span><span class="sxs-lookup"><span data-stu-id="2f873-179">true</span></span>|<span data-ttu-id="2f873-180">fałsz</span><span class="sxs-lookup"><span data-stu-id="2f873-180">false</span></span>|<span data-ttu-id="2f873-181">true</span><span class="sxs-lookup"><span data-stu-id="2f873-181">true</span></span>|  
|<span data-ttu-id="2f873-182">fałsz</span><span class="sxs-lookup"><span data-stu-id="2f873-182">false</span></span>|<span data-ttu-id="2f873-183">fałsz</span><span class="sxs-lookup"><span data-stu-id="2f873-183">false</span></span>|<span data-ttu-id="2f873-184">fałsz</span><span class="sxs-lookup"><span data-stu-id="2f873-184">false</span></span>|<span data-ttu-id="2f873-185">fałsz</span><span class="sxs-lookup"><span data-stu-id="2f873-185">false</span></span>|  
|<span data-ttu-id="2f873-186">fałsz</span><span class="sxs-lookup"><span data-stu-id="2f873-186">false</span></span>|<span data-ttu-id="2f873-187">wartość null</span><span class="sxs-lookup"><span data-stu-id="2f873-187">null</span></span>|<span data-ttu-id="2f873-188">fałsz</span><span class="sxs-lookup"><span data-stu-id="2f873-188">false</span></span>|<span data-ttu-id="2f873-189">wartość null</span><span class="sxs-lookup"><span data-stu-id="2f873-189">null</span></span>|  
|<span data-ttu-id="2f873-190">wartość null</span><span class="sxs-lookup"><span data-stu-id="2f873-190">null</span></span>|<span data-ttu-id="2f873-191">true</span><span class="sxs-lookup"><span data-stu-id="2f873-191">true</span></span>|<span data-ttu-id="2f873-192">wartość null</span><span class="sxs-lookup"><span data-stu-id="2f873-192">null</span></span>|<span data-ttu-id="2f873-193">true</span><span class="sxs-lookup"><span data-stu-id="2f873-193">true</span></span>|  
|<span data-ttu-id="2f873-194">wartość null</span><span class="sxs-lookup"><span data-stu-id="2f873-194">null</span></span>|<span data-ttu-id="2f873-195">fałsz</span><span class="sxs-lookup"><span data-stu-id="2f873-195">false</span></span>|<span data-ttu-id="2f873-196">fałsz</span><span class="sxs-lookup"><span data-stu-id="2f873-196">false</span></span>|<span data-ttu-id="2f873-197">wartość null</span><span class="sxs-lookup"><span data-stu-id="2f873-197">null</span></span>|  
|<span data-ttu-id="2f873-198">wartość null</span><span class="sxs-lookup"><span data-stu-id="2f873-198">null</span></span>|<span data-ttu-id="2f873-199">wartość null</span><span class="sxs-lookup"><span data-stu-id="2f873-199">null</span></span>|<span data-ttu-id="2f873-200">wartość null</span><span class="sxs-lookup"><span data-stu-id="2f873-200">null</span></span>|<span data-ttu-id="2f873-201">wartość null</span><span class="sxs-lookup"><span data-stu-id="2f873-201">null</span></span>|  

<span data-ttu-id="2f873-202">Zachowanie tych operatorów różni się od typowego zachowania operatora z zerowymi typami wartości.</span><span class="sxs-lookup"><span data-stu-id="2f873-202">The behavior of those operators differs from the typical operator behavior with nullable value types.</span></span> <span data-ttu-id="2f873-203">Zazwyczaj operator, który jest zdefiniowany dla operandów typu wartości, może być również używany z operandami odpowiadającego typu wartości null.</span><span class="sxs-lookup"><span data-stu-id="2f873-203">Typically, an operator which is defined for operands of a value type can be also used with operands of the corresponding nullable value type.</span></span> <span data-ttu-id="2f873-204">Taki operator wytwarza, `null` Jeśli którykolwiek z jego operandów zwróci wartość `null` .</span><span class="sxs-lookup"><span data-stu-id="2f873-204">Such an operator produces `null` if any of its operands evaluates to `null`.</span></span> <span data-ttu-id="2f873-205">Jednak `&` `|` Operatory i mogą generować wartości inne niż null, nawet jeśli jeden z operandów jest wynikiem `null` .</span><span class="sxs-lookup"><span data-stu-id="2f873-205">However, the `&` and `|` operators can produce non-null even if one of the operands evaluates to `null`.</span></span> <span data-ttu-id="2f873-206">Aby uzyskać więcej informacji o zachowaniu operatora z typem wartości null, zobacz sekcję [zniesione operatory](../builtin-types/nullable-value-types.md#lifted-operators) w artykule [typy wartości null](../builtin-types/nullable-value-types.md) .</span><span class="sxs-lookup"><span data-stu-id="2f873-206">For more information about the operator behavior with nullable value types, see the [Lifted operators](../builtin-types/nullable-value-types.md#lifted-operators) section of the [Nullable value types](../builtin-types/nullable-value-types.md) article.</span></span>

<span data-ttu-id="2f873-207">Można również użyć `!` `^` operatorów i z `bool?` operandami, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="2f873-207">You can also use the `!` and `^` operators with `bool?` operands, as the following example shows:</span></span>

[!code-csharp-interactive[lifted negation and xor](snippets/BooleanLogicalOperators.cs#WithNullableBoolean)]

<span data-ttu-id="2f873-208">Operatory logiczne warunkowe `&&` i `||` nie obsługują `bool?` argumentów operacji.</span><span class="sxs-lookup"><span data-stu-id="2f873-208">The conditional logical operators `&&` and `||` don't support `bool?` operands.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="2f873-209">Przypisanie złożone</span><span class="sxs-lookup"><span data-stu-id="2f873-209">Compound assignment</span></span>

<span data-ttu-id="2f873-210">Dla operatora binarnego `op` wyrażenie złożonego przypisania formularza</span><span class="sxs-lookup"><span data-stu-id="2f873-210">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="2f873-211">jest równoważny</span><span class="sxs-lookup"><span data-stu-id="2f873-211">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="2f873-212">z tą różnicą, że `x` jest obliczana tylko raz.</span><span class="sxs-lookup"><span data-stu-id="2f873-212">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="2f873-213">`&`Operatory, `|` i `^` obsługują przypisanie złożone, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="2f873-213">The `&`, `|`, and `^` operators support compound assignment, as the following example shows:</span></span>

[!code-csharp-interactive[compound assignment](snippets/BooleanLogicalOperators.cs#CompoundAssignment)]

> [!NOTE]
> <span data-ttu-id="2f873-214">Warunkowe operatory logiczne `&&` i `||` nie obsługują przypisania złożonego.</span><span class="sxs-lookup"><span data-stu-id="2f873-214">The conditional logical operators `&&` and `||` don't support compound assignment.</span></span>

## <a name="operator-precedence"></a><span data-ttu-id="2f873-215">Pierwszeństwo operatorów</span><span class="sxs-lookup"><span data-stu-id="2f873-215">Operator precedence</span></span>

<span data-ttu-id="2f873-216">Poniższa lista porządkuje operatory logiczne rozpoczynając od najwyższego priorytetu do najniższego:</span><span class="sxs-lookup"><span data-stu-id="2f873-216">The following list orders logical operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="2f873-217">Operator logiczny negacji`!`</span><span class="sxs-lookup"><span data-stu-id="2f873-217">Logical negation operator `!`</span></span>
- <span data-ttu-id="2f873-218">Operator logiczny AND`&`</span><span class="sxs-lookup"><span data-stu-id="2f873-218">Logical AND operator `&`</span></span>
- <span data-ttu-id="2f873-219">Operator wyłączny logicznego OR`^`</span><span class="sxs-lookup"><span data-stu-id="2f873-219">Logical exclusive OR operator `^`</span></span>
- <span data-ttu-id="2f873-220">Operator logiczny OR`|`</span><span class="sxs-lookup"><span data-stu-id="2f873-220">Logical OR operator `|`</span></span>
- <span data-ttu-id="2f873-221">Warunkowe operatory logiczne i`&&`</span><span class="sxs-lookup"><span data-stu-id="2f873-221">Conditional logical AND operator `&&`</span></span>
- <span data-ttu-id="2f873-222">Warunkowy operator logiczny OR`||`</span><span class="sxs-lookup"><span data-stu-id="2f873-222">Conditional logical OR operator `||`</span></span>

<span data-ttu-id="2f873-223">Użyj nawiasów, `()` Aby zmienić kolejność oceny nałożona przez pierwszeństwo operatorów:</span><span class="sxs-lookup"><span data-stu-id="2f873-223">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence:</span></span>

[!code-csharp-interactive[operator precedence](snippets/BooleanLogicalOperators.cs#Precedence)]

<span data-ttu-id="2f873-224">Aby uzyskać pełną listę operatorów języka C# uporządkowanych według poziomu pierwszeństwa, zobacz sekcję [pierwszeństwo](index.md#operator-precedence) operatorów w artykule [operatory języka c#](index.md) .</span><span class="sxs-lookup"><span data-stu-id="2f873-224">For the complete list of C# operators ordered by precedence level, see the [Operator precedence](index.md#operator-precedence) section of the [C# operators](index.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="2f873-225">Przeciążanie operatora</span><span class="sxs-lookup"><span data-stu-id="2f873-225">Operator overloadability</span></span>

<span data-ttu-id="2f873-226">Typ zdefiniowany przez użytkownika może [przeciążać](operator-overloading.md) `!` `&` operatory,, `|` , i `^` .</span><span class="sxs-lookup"><span data-stu-id="2f873-226">A user-defined type can [overload](operator-overloading.md) the `!`, `&`, `|`, and `^` operators.</span></span> <span data-ttu-id="2f873-227">Gdy operator binarny jest przeciążony, odpowiadający mu operator przypisania złożonego jest również niejawnie przeciążony.</span><span class="sxs-lookup"><span data-stu-id="2f873-227">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="2f873-228">Typ zdefiniowany przez użytkownika nie może jawnie przeciążać złożonego operatora przypisania.</span><span class="sxs-lookup"><span data-stu-id="2f873-228">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

<span data-ttu-id="2f873-229">Typ zdefiniowany przez użytkownika nie może przeciążać warunkowych operatorów logicznych `&&` i `||` .</span><span class="sxs-lookup"><span data-stu-id="2f873-229">A user-defined type cannot overload the conditional logical operators `&&` and `||`.</span></span> <span data-ttu-id="2f873-230">Jednakże, jeśli typ zdefiniowany przez użytkownika przeciążuje [Operatory true i false](true-false-operators.md) oraz `&` operator or `|` w określony sposób, `&&` lub `||` operację, odpowiednio, można obliczyć dla operandów tego typu.</span><span class="sxs-lookup"><span data-stu-id="2f873-230">However, if a user-defined type overloads the [true and false operators](true-false-operators.md) and the `&` or `|` operator in a certain way, the `&&` or `||` operation, respectively, can be evaluated for the operands of that type.</span></span> <span data-ttu-id="2f873-231">Aby uzyskać więcej informacji, zapoznaj się z sekcją wyrażenia [warunkowe operatory logiczne zdefiniowane przez użytkownika](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) w [specyfikacji języka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="2f873-231">For more information, see the [User-defined conditional logical operators](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="2f873-232">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="2f873-232">C# language specification</span></span>

<span data-ttu-id="2f873-233">Aby uzyskać więcej informacji, zobacz następujące sekcje [specyfikacji języka C#](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="2f873-233">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="2f873-234">Operator logiczny negacji</span><span class="sxs-lookup"><span data-stu-id="2f873-234">Logical negation operator</span></span>](~/_csharplang/spec/expressions.md#logical-negation-operator)
- [<span data-ttu-id="2f873-235">Operatory logiczne</span><span class="sxs-lookup"><span data-stu-id="2f873-235">Logical operators</span></span>](~/_csharplang/spec/expressions.md#logical-operators)
- [<span data-ttu-id="2f873-236">Warunkowe operatory logiczne</span><span class="sxs-lookup"><span data-stu-id="2f873-236">Conditional logical operators</span></span>](~/_csharplang/spec/expressions.md#conditional-logical-operators)
- [<span data-ttu-id="2f873-237">Przypisanie złożone</span><span class="sxs-lookup"><span data-stu-id="2f873-237">Compound assignment</span></span>](~/_csharplang/spec/expressions.md#compound-assignment)

## <a name="see-also"></a><span data-ttu-id="2f873-238">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2f873-238">See also</span></span>

- [<span data-ttu-id="2f873-239">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="2f873-239">C# reference</span></span>](../index.md)
- [<span data-ttu-id="2f873-240">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="2f873-240">C# operators</span></span>](index.md)
- [<span data-ttu-id="2f873-241">Operatory przesunięcia i operatory bitowe</span><span class="sxs-lookup"><span data-stu-id="2f873-241">Bitwise and shift operators</span></span>](bitwise-and-shift-operators.md)
