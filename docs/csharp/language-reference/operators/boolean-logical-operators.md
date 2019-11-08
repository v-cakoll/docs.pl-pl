---
title: Operatory logiczne Boolean — C# odwołanie
description: Dowiedz C# się więcej na temat operatorów, które wykonują logiczne negacje, połączenie (i) i Włączne i wyłączne operacje odłączania (lub) z argumentami operacji logicznych.
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
ms.openlocfilehash: 327a2a8a95809923446107e6ba1c4b331eee82b7
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73737890"
---
# <a name="boolean-logical-operators-c-reference"></a><span data-ttu-id="4897d-103">Logiczna operatory logiczne (C# odwołanie)</span><span class="sxs-lookup"><span data-stu-id="4897d-103">Boolean logical operators (C# reference)</span></span>

<span data-ttu-id="4897d-104">Następujące operatory wykonują operacje logiczne z argumentami operacji [bool](../keywords/bool.md) :</span><span class="sxs-lookup"><span data-stu-id="4897d-104">The following operators perform logical operations with [bool](../keywords/bool.md) operands:</span></span>

- <span data-ttu-id="4897d-105">Jednoargumentowy [`!` (Negacja logiczna)](#logical-negation-operator-) .</span><span class="sxs-lookup"><span data-stu-id="4897d-105">Unary [`!` (logical negation)](#logical-negation-operator-) operator.</span></span>
- <span data-ttu-id="4897d-106">Binarne [`&` (logiczne i)](#logical-and-operator-), [`|` (logiczne lub)](#logical-or-operator-)i [`^` (logiczne wyłącznych lub)](#logical-exclusive-or-operator-) .</span><span class="sxs-lookup"><span data-stu-id="4897d-106">Binary [`&` (logical AND)](#logical-and-operator-), [`|` (logical OR)](#logical-or-operator-), and [`^` (logical exclusive OR)](#logical-exclusive-or-operator-) operators.</span></span> <span data-ttu-id="4897d-107">Te operatory zawsze obliczają oba operandy.</span><span class="sxs-lookup"><span data-stu-id="4897d-107">Those operators always evaluate both operands.</span></span>
- <span data-ttu-id="4897d-108">Binarny [`&&` (warunkowe logiczne i)](#conditional-logical-and-operator-) i [`||` (warunkowe operatory logiczne or)](#conditional-logical-or-operator-) .</span><span class="sxs-lookup"><span data-stu-id="4897d-108">Binary [`&&` (conditional logical AND)](#conditional-logical-and-operator-) and [`||` (conditional logical OR)](#conditional-logical-or-operator-) operators.</span></span> <span data-ttu-id="4897d-109">Te operatory obliczają operand z prawej strony tylko wtedy, gdy jest to konieczne.</span><span class="sxs-lookup"><span data-stu-id="4897d-109">Those operators evaluate the right-hand operand only if it's necessary.</span></span>

<span data-ttu-id="4897d-110">W przypadku operandów [całkowitych typów liczbowych](../builtin-types/integral-numeric-types.md)operatory `&`, `|`i `^` wykonują bitowe operacje logiczne.</span><span class="sxs-lookup"><span data-stu-id="4897d-110">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `&`, `|`, and `^` operators perform bitwise logical operations.</span></span> <span data-ttu-id="4897d-111">Aby uzyskać więcej informacji, zobacz [Operatory bitowe i przesunięcia](bitwise-and-shift-operators.md).</span><span class="sxs-lookup"><span data-stu-id="4897d-111">For more information, see [Bitwise and shift operators](bitwise-and-shift-operators.md).</span></span>

## <a name="logical-negation-operator-"></a><span data-ttu-id="4897d-112">Operator logiczny negacji</span><span class="sxs-lookup"><span data-stu-id="4897d-112">Logical negation operator !</span></span>

<span data-ttu-id="4897d-113">Prefiks jednoargumentowy `!` oblicza logiczne Negacja operandu.</span><span class="sxs-lookup"><span data-stu-id="4897d-113">The unary prefix `!` operator computes logical negation of its operand.</span></span> <span data-ttu-id="4897d-114">Oznacza to, że generuje `true`, jeśli operand zostanie obliczony do `false` i `false`, jeśli operand zostanie obliczony do `true`:</span><span class="sxs-lookup"><span data-stu-id="4897d-114">That is, it produces `true`, if the operand evaluates to `false`, and `false`, if the operand evaluates to `true`:</span></span>

[!code-csharp-interactive[logical negation](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Negation)]

<span data-ttu-id="4897d-115">Począwszy od C# 8,0, operator jednoargumentowy`!`jest operatorem o [wartości null-łagodniejszej](null-forgiving.md).</span><span class="sxs-lookup"><span data-stu-id="4897d-115">Beginning with C# 8.0, the unary postfix `!` operator is the [null-forgiving operator](null-forgiving.md).</span></span>

## <a name="logical-and-operator-"></a><span data-ttu-id="4897d-116">Operatory logiczne i &amp;</span><span class="sxs-lookup"><span data-stu-id="4897d-116">Logical AND operator &amp;</span></span>

<span data-ttu-id="4897d-117">Operator `&` oblicza wartość logiczną i jej operandów.</span><span class="sxs-lookup"><span data-stu-id="4897d-117">The `&` operator computes the logical AND of its operands.</span></span> <span data-ttu-id="4897d-118">Wynik `x & y` jest `true`, jeśli oba `x` i `y` są oceniane do `true`.</span><span class="sxs-lookup"><span data-stu-id="4897d-118">The result of `x & y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="4897d-119">W przeciwnym razie wynik jest `false`.</span><span class="sxs-lookup"><span data-stu-id="4897d-119">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="4897d-120">Operator `&` oblicza oba operandy, nawet jeśli argument operacji po lewej stronie szacuje się na `false`, dzięki czemu wynik operacji jest `false` niezależnie od wartości operandu po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="4897d-120">The `&` operator evaluates both operands even if the left-hand operand evaluates to `false`, so that the operation result is `false` regardless of the value of the right-hand operand.</span></span>

<span data-ttu-id="4897d-121">W poniższym przykładzie operand z prawej strony operatora `&` jest wywołaniem metody, które jest wykonywane niezależnie od wartości operandu po lewej stronie:</span><span class="sxs-lookup"><span data-stu-id="4897d-121">In the following example, the right-hand operand of the `&` operator is a method call, which is performed regardless of the value of the left-hand operand:</span></span>

[!code-csharp-interactive[logical AND](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#And)]

<span data-ttu-id="4897d-122">[Warunkowe operatory logiczne i](#conditional-logical-and-operator-) `&&` oblicza również wartość logiczną i jej operandy, ale nie oblicza wartości operandu po prawej stronie, jeśli wartość argumentu po lewej strony jest równa `false`.</span><span class="sxs-lookup"><span data-stu-id="4897d-122">The [conditional logical AND operator](#conditional-logical-and-operator-) `&&` also computes the logical AND of its operands, but doesn't evaluate the right-hand operand if the left-hand operand evaluates to `false`.</span></span>

<span data-ttu-id="4897d-123">Dla operandów [całkowitych typów liczbowych](../builtin-types/integral-numeric-types.md)operator `&` oblicza koniunkcję [bitową i](bitwise-and-shift-operators.md#logical-and-operator-) jej operandy.</span><span class="sxs-lookup"><span data-stu-id="4897d-123">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `&` operator computes the [bitwise logical AND](bitwise-and-shift-operators.md#logical-and-operator-) of its operands.</span></span> <span data-ttu-id="4897d-124">Operator jednoargumentowy `&` jest operatorem [Address-of](pointer-related-operators.md#address-of-operator-).</span><span class="sxs-lookup"><span data-stu-id="4897d-124">The unary `&` operator is the [address-of operator](pointer-related-operators.md#address-of-operator-).</span></span>

## <a name="logical-exclusive-or-operator-"></a><span data-ttu-id="4897d-125">Operator wyłączny logicznego OR ^</span><span class="sxs-lookup"><span data-stu-id="4897d-125">Logical exclusive OR operator ^</span></span>

<span data-ttu-id="4897d-126">Operator `^` oblicza wartość logiczną na wyłączność lub, znaną również jako logiczna XOR, jego operandów.</span><span class="sxs-lookup"><span data-stu-id="4897d-126">The `^` operator computes the logical exclusive OR, also known as the logical XOR, of its operands.</span></span> <span data-ttu-id="4897d-127">Wynik `x ^ y` jest `true`, jeśli `x` oblicza `true` i `y` oblicza `false`, lub `x` oblicza `false`, a `y` oblicza `true`.</span><span class="sxs-lookup"><span data-stu-id="4897d-127">The result of `x ^ y` is `true` if `x` evaluates to `true` and `y` evaluates to `false`, or `x` evaluates to `false` and `y` evaluates to `true`.</span></span> <span data-ttu-id="4897d-128">W przeciwnym razie wynik jest `false`.</span><span class="sxs-lookup"><span data-stu-id="4897d-128">Otherwise, the result is `false`.</span></span> <span data-ttu-id="4897d-129">Oznacza to, że dla operandów `bool` operator `^` oblicza ten sam wynik, co `!=`[operatora nierówności](equality-operators.md#inequality-operator-) .</span><span class="sxs-lookup"><span data-stu-id="4897d-129">That is, for the `bool` operands, the `^` operator computes the same result as the [inequality operator](equality-operators.md#inequality-operator-) `!=`.</span></span>

[!code-csharp-interactive[logical exclusive OR](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Xor)]

<span data-ttu-id="4897d-130">W przypadku operandów [całkowitych typów liczbowych](../builtin-types/integral-numeric-types.md)operator `^` oblicza [bitowe logiczne wyłącznych lub](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) jego operandów.</span><span class="sxs-lookup"><span data-stu-id="4897d-130">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `^` operator computes the [bitwise logical exclusive OR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) of its operands.</span></span>

## <a name="logical-or-operator-"></a><span data-ttu-id="4897d-131">Operator logiczny OR |</span><span class="sxs-lookup"><span data-stu-id="4897d-131">Logical OR operator |</span></span>

<span data-ttu-id="4897d-132">Operator `|` oblicza wartość logiczną lub argumentów operacji.</span><span class="sxs-lookup"><span data-stu-id="4897d-132">The `|` operator computes the logical OR of its operands.</span></span> <span data-ttu-id="4897d-133">Wynik `x | y` jest `true`, jeśli `x` lub `y` są oceniane do `true`.</span><span class="sxs-lookup"><span data-stu-id="4897d-133">The result of `x | y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="4897d-134">W przeciwnym razie wynik jest `false`.</span><span class="sxs-lookup"><span data-stu-id="4897d-134">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="4897d-135">Operator `|` oblicza oba operandy, nawet jeśli argument operacji po lewej stronie szacuje się na `true`, dzięki czemu wynik operacji jest `true` niezależnie od wartości operandu po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="4897d-135">The `|` operator evaluates both operands even if the left-hand operand evaluates to `true`, so that the operation result is `true` regardless of the value of the right-hand operand.</span></span>

<span data-ttu-id="4897d-136">W poniższym przykładzie operand z prawej strony operatora `|` jest wywołaniem metody, które jest wykonywane niezależnie od wartości operandu po lewej stronie:</span><span class="sxs-lookup"><span data-stu-id="4897d-136">In the following example, the right-hand operand of the `|` operator is a method call, which is performed regardless of the value of the left-hand operand:</span></span>

[!code-csharp-interactive[logical OR](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Or)]

<span data-ttu-id="4897d-137">[Warunkowe operatory logiczne or](#conditional-logical-or-operator-) `||` oblicza również wartość logiczną lub jej operandy, ale nie oblicza wartości operandu po prawej stronie, jeśli argument operacji leworęcznych ma wartość `true`.</span><span class="sxs-lookup"><span data-stu-id="4897d-137">The [conditional logical OR operator](#conditional-logical-or-operator-) `||` also computes the logical OR of its operands, but doesn't evaluate the right-hand operand if the left-hand operand evaluates to `true`.</span></span>

<span data-ttu-id="4897d-138">Dla operandów [całkowitych typów liczbowych](../builtin-types/integral-numeric-types.md)operator `|` oblicza [bitową wartość logiczną lub](bitwise-and-shift-operators.md#logical-or-operator-) jej operandów.</span><span class="sxs-lookup"><span data-stu-id="4897d-138">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `|` operator computes the [bitwise logical OR](bitwise-and-shift-operators.md#logical-or-operator-) of its operands.</span></span>

## <a name="conditional-logical-and-operator-"></a><span data-ttu-id="4897d-139">Warunkowe &amp;logiczne i operatory&amp;</span><span class="sxs-lookup"><span data-stu-id="4897d-139">Conditional logical AND operator &amp;&amp;</span></span>

<span data-ttu-id="4897d-140">Warunkowe operatory logiczne i operator `&&`, znane także jako "koniunkcja" typu "Short-obwóding", oblicza wartość logiczną i jej operandów.</span><span class="sxs-lookup"><span data-stu-id="4897d-140">The conditional logical AND operator `&&`, also known as the "short-circuiting" logical AND operator, computes the logical AND of its operands.</span></span> <span data-ttu-id="4897d-141">Wynik `x && y` jest `true`, jeśli oba `x` i `y` są oceniane do `true`.</span><span class="sxs-lookup"><span data-stu-id="4897d-141">The result of `x && y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="4897d-142">W przeciwnym razie wynik jest `false`.</span><span class="sxs-lookup"><span data-stu-id="4897d-142">Otherwise, the result is `false`.</span></span> <span data-ttu-id="4897d-143">Jeśli `x` szacuje się do `false`, `y` nie jest oceniane.</span><span class="sxs-lookup"><span data-stu-id="4897d-143">If `x` evaluates to `false`, `y` is not evaluated.</span></span>

<span data-ttu-id="4897d-144">W poniższym przykładzie operand z prawej strony operatora `&&` jest wywołaniem metody, które nie jest wykonywane, jeśli argument operacji po lewej stronie szacuje się na `false`:</span><span class="sxs-lookup"><span data-stu-id="4897d-144">In the following example, the right-hand operand of the `&&` operator is a method call, which isn't performed if the left-hand operand evaluates to `false`:</span></span>

[!code-csharp-interactive[conditional logical AND](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#ConditionalAnd)]

<span data-ttu-id="4897d-145">[Operator logiczny i](#logical-and-operator-) `&` oblicza również wartość logiczną i jej operandy, ale zawsze oblicza oba operandy.</span><span class="sxs-lookup"><span data-stu-id="4897d-145">The [logical AND operator](#logical-and-operator-) `&` also computes the logical AND of its operands, but always evaluates both operands.</span></span>

## <a name="conditional-logical-or-operator-"></a><span data-ttu-id="4897d-146">Warunkowe logiczne OR operator | |</span><span class="sxs-lookup"><span data-stu-id="4897d-146">Conditional logical OR operator ||</span></span>

<span data-ttu-id="4897d-147">Warunkowe operatory logiczne OR `||`, nazywane także "operatorem" krótkiego obwodu ", oblicza wartość logiczną lub argumentów operacji.</span><span class="sxs-lookup"><span data-stu-id="4897d-147">The conditional logical OR operator `||`, also known as the "short-circuiting" logical OR operator, computes the logical OR of its operands.</span></span> <span data-ttu-id="4897d-148">Wynik `x || y` jest `true`, jeśli `x` lub `y` są oceniane do `true`.</span><span class="sxs-lookup"><span data-stu-id="4897d-148">The result of `x || y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="4897d-149">W przeciwnym razie wynik jest `false`.</span><span class="sxs-lookup"><span data-stu-id="4897d-149">Otherwise, the result is `false`.</span></span> <span data-ttu-id="4897d-150">Jeśli `x` szacuje się do `true`, `y` nie jest oceniane.</span><span class="sxs-lookup"><span data-stu-id="4897d-150">If `x` evaluates to `true`, `y` is not evaluated.</span></span>

<span data-ttu-id="4897d-151">W poniższym przykładzie operand z prawej strony operatora `||` jest wywołaniem metody, które nie jest wykonywane, jeśli argument operacji po lewej stronie szacuje się na `true`:</span><span class="sxs-lookup"><span data-stu-id="4897d-151">In the following example, the right-hand operand of the `||` operator is a method call, which isn't performed if the left-hand operand evaluates to `true`:</span></span>

[!code-csharp-interactive[conditional logical OR](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#ConditionalOr)]

<span data-ttu-id="4897d-152">[Operator logiczny or](#logical-or-operator-) `|` oblicza również wartość logiczną lub argumentów operacji, ale zawsze oblicza oba operandy.</span><span class="sxs-lookup"><span data-stu-id="4897d-152">The [logical OR operator](#logical-or-operator-) `|` also computes the logical OR of its operands, but always evaluates both operands.</span></span>

## <a name="nullable-boolean-logical-operators"></a><span data-ttu-id="4897d-153">Logiczne operatory wartości null</span><span class="sxs-lookup"><span data-stu-id="4897d-153">Nullable Boolean logical operators</span></span>

<span data-ttu-id="4897d-154">Dla argumentów operacji `bool?` operatory `&` i `|` obsługują logikę z trzema wartościami.</span><span class="sxs-lookup"><span data-stu-id="4897d-154">For `bool?` operands, the `&` and `|` operators support the three-valued logic.</span></span> <span data-ttu-id="4897d-155">Semantyka tych operatorów jest definiowana przez następującą tabelę:</span><span class="sxs-lookup"><span data-stu-id="4897d-155">The semantics of these operators is defined by the following table:</span></span>  
  
|<span data-ttu-id="4897d-156">x</span><span class="sxs-lookup"><span data-stu-id="4897d-156">x</span></span>|<span data-ttu-id="4897d-157">t</span><span class="sxs-lookup"><span data-stu-id="4897d-157">y</span></span>|<span data-ttu-id="4897d-158">x & y</span><span class="sxs-lookup"><span data-stu-id="4897d-158">x&y</span></span>|<span data-ttu-id="4897d-159">x&#124;y</span><span class="sxs-lookup"><span data-stu-id="4897d-159">x&#124;y</span></span>|  
|----|----|----|----|  
|<span data-ttu-id="4897d-160">true</span><span class="sxs-lookup"><span data-stu-id="4897d-160">true</span></span>|<span data-ttu-id="4897d-161">true</span><span class="sxs-lookup"><span data-stu-id="4897d-161">true</span></span>|<span data-ttu-id="4897d-162">true</span><span class="sxs-lookup"><span data-stu-id="4897d-162">true</span></span>|<span data-ttu-id="4897d-163">true</span><span class="sxs-lookup"><span data-stu-id="4897d-163">true</span></span>|  
|<span data-ttu-id="4897d-164">true</span><span class="sxs-lookup"><span data-stu-id="4897d-164">true</span></span>|<span data-ttu-id="4897d-165">false</span><span class="sxs-lookup"><span data-stu-id="4897d-165">false</span></span>|<span data-ttu-id="4897d-166">false</span><span class="sxs-lookup"><span data-stu-id="4897d-166">false</span></span>|<span data-ttu-id="4897d-167">true</span><span class="sxs-lookup"><span data-stu-id="4897d-167">true</span></span>|  
|<span data-ttu-id="4897d-168">true</span><span class="sxs-lookup"><span data-stu-id="4897d-168">true</span></span>|<span data-ttu-id="4897d-169">wartość null</span><span class="sxs-lookup"><span data-stu-id="4897d-169">null</span></span>|<span data-ttu-id="4897d-170">wartość null</span><span class="sxs-lookup"><span data-stu-id="4897d-170">null</span></span>|<span data-ttu-id="4897d-171">true</span><span class="sxs-lookup"><span data-stu-id="4897d-171">true</span></span>|  
|<span data-ttu-id="4897d-172">false</span><span class="sxs-lookup"><span data-stu-id="4897d-172">false</span></span>|<span data-ttu-id="4897d-173">true</span><span class="sxs-lookup"><span data-stu-id="4897d-173">true</span></span>|<span data-ttu-id="4897d-174">false</span><span class="sxs-lookup"><span data-stu-id="4897d-174">false</span></span>|<span data-ttu-id="4897d-175">true</span><span class="sxs-lookup"><span data-stu-id="4897d-175">true</span></span>|  
|<span data-ttu-id="4897d-176">false</span><span class="sxs-lookup"><span data-stu-id="4897d-176">false</span></span>|<span data-ttu-id="4897d-177">false</span><span class="sxs-lookup"><span data-stu-id="4897d-177">false</span></span>|<span data-ttu-id="4897d-178">false</span><span class="sxs-lookup"><span data-stu-id="4897d-178">false</span></span>|<span data-ttu-id="4897d-179">false</span><span class="sxs-lookup"><span data-stu-id="4897d-179">false</span></span>|  
|<span data-ttu-id="4897d-180">false</span><span class="sxs-lookup"><span data-stu-id="4897d-180">false</span></span>|<span data-ttu-id="4897d-181">wartość null</span><span class="sxs-lookup"><span data-stu-id="4897d-181">null</span></span>|<span data-ttu-id="4897d-182">false</span><span class="sxs-lookup"><span data-stu-id="4897d-182">false</span></span>|<span data-ttu-id="4897d-183">wartość null</span><span class="sxs-lookup"><span data-stu-id="4897d-183">null</span></span>|  
|<span data-ttu-id="4897d-184">wartość null</span><span class="sxs-lookup"><span data-stu-id="4897d-184">null</span></span>|<span data-ttu-id="4897d-185">true</span><span class="sxs-lookup"><span data-stu-id="4897d-185">true</span></span>|<span data-ttu-id="4897d-186">wartość null</span><span class="sxs-lookup"><span data-stu-id="4897d-186">null</span></span>|<span data-ttu-id="4897d-187">true</span><span class="sxs-lookup"><span data-stu-id="4897d-187">true</span></span>|  
|<span data-ttu-id="4897d-188">wartość null</span><span class="sxs-lookup"><span data-stu-id="4897d-188">null</span></span>|<span data-ttu-id="4897d-189">false</span><span class="sxs-lookup"><span data-stu-id="4897d-189">false</span></span>|<span data-ttu-id="4897d-190">false</span><span class="sxs-lookup"><span data-stu-id="4897d-190">false</span></span>|<span data-ttu-id="4897d-191">wartość null</span><span class="sxs-lookup"><span data-stu-id="4897d-191">null</span></span>|  
|<span data-ttu-id="4897d-192">wartość null</span><span class="sxs-lookup"><span data-stu-id="4897d-192">null</span></span>|<span data-ttu-id="4897d-193">wartość null</span><span class="sxs-lookup"><span data-stu-id="4897d-193">null</span></span>|<span data-ttu-id="4897d-194">wartość null</span><span class="sxs-lookup"><span data-stu-id="4897d-194">null</span></span>|<span data-ttu-id="4897d-195">wartość null</span><span class="sxs-lookup"><span data-stu-id="4897d-195">null</span></span>|  

<span data-ttu-id="4897d-196">Zachowanie tych operatorów różni się od typowego zachowania operatora z zerowymi typami wartości.</span><span class="sxs-lookup"><span data-stu-id="4897d-196">The behavior of those operators differs from the typical operator behavior with nullable value types.</span></span> <span data-ttu-id="4897d-197">Zazwyczaj operator, który jest zdefiniowany dla operandów typu wartości, może być również używany z operandami odpowiadającego typu wartości null.</span><span class="sxs-lookup"><span data-stu-id="4897d-197">Typically, an operator which is defined for operands of a value type can be also used with operands of the corresponding nullable value type.</span></span> <span data-ttu-id="4897d-198">Taki operator wytwarza `null`, jeśli którykolwiek z jego operandów zwróci `null`.</span><span class="sxs-lookup"><span data-stu-id="4897d-198">Such an operator produces `null` if any of its operands evaluates to `null`.</span></span> <span data-ttu-id="4897d-199">Jednak operatory `&` i `|` mogą generować wartości inne niż null, nawet jeśli jeden z operandów szacuje się w `null`.</span><span class="sxs-lookup"><span data-stu-id="4897d-199">However, the `&` and `|` operators can produce non-null even if one of the operands evaluates to `null`.</span></span> <span data-ttu-id="4897d-200">Aby uzyskać więcej informacji o zachowaniu operatora z typem wartości null, zobacz sekcję [zniesione operatory](../builtin-types/nullable-value-types.md#lifted-operators) w artykule [typy wartości null](../builtin-types/nullable-value-types.md) .</span><span class="sxs-lookup"><span data-stu-id="4897d-200">For more information about the operator behavior with nullable value types, see the [Lifted operators](../builtin-types/nullable-value-types.md#lifted-operators) section of the [Nullable value types](../builtin-types/nullable-value-types.md) article.</span></span>

<span data-ttu-id="4897d-201">Można również użyć operatorów `!` i `^` z argumentami operacji `bool?`, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="4897d-201">You can also use the `!` and `^` operators with `bool?` operands, as the following example shows:</span></span>

[!code-csharp-interactive[lifted negation and xor](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#WithNullableBoolean)]

<span data-ttu-id="4897d-202">Warunkowe operatory logiczne `&&` i `||` nie obsługują argumentów operacji `bool?`.</span><span class="sxs-lookup"><span data-stu-id="4897d-202">The conditional logical operators `&&` and `||` don't support `bool?` operands.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="4897d-203">Przypisanie złożone</span><span class="sxs-lookup"><span data-stu-id="4897d-203">Compound assignment</span></span>

<span data-ttu-id="4897d-204">Dla operatora binarnego `op` wyrażenie złożonego przypisania formularza</span><span class="sxs-lookup"><span data-stu-id="4897d-204">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="4897d-205">jest równoważny</span><span class="sxs-lookup"><span data-stu-id="4897d-205">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="4897d-206">z tą różnicą, że `x` jest obliczana tylko raz.</span><span class="sxs-lookup"><span data-stu-id="4897d-206">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="4897d-207">Operatory `&`, `|`i `^` obsługują przypisanie złożone, co ilustruje poniższy przykład:</span><span class="sxs-lookup"><span data-stu-id="4897d-207">The `&`, `|`, and `^` operators support compound assignment, as the following example shows:</span></span>

[!code-csharp-interactive[compound assignment](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#CompoundAssignment)]

<span data-ttu-id="4897d-208">Warunkowe operatory logiczne `&&` i `||` nie obsługują przypisania złożonego.</span><span class="sxs-lookup"><span data-stu-id="4897d-208">The conditional logical operators `&&` and `||` don't support compound assignment.</span></span>

## <a name="operator-precedence"></a><span data-ttu-id="4897d-209">Pierwszeństwo operatorów</span><span class="sxs-lookup"><span data-stu-id="4897d-209">Operator precedence</span></span>

<span data-ttu-id="4897d-210">Poniższa lista porządkuje operatory logiczne rozpoczynając od najwyższego priorytetu do najniższego:</span><span class="sxs-lookup"><span data-stu-id="4897d-210">The following list orders logical operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="4897d-211">Operator logiczny negacji `!`</span><span class="sxs-lookup"><span data-stu-id="4897d-211">Logical negation operator `!`</span></span>
- <span data-ttu-id="4897d-212">Operatory logiczne i `&`</span><span class="sxs-lookup"><span data-stu-id="4897d-212">Logical AND operator `&`</span></span>
- <span data-ttu-id="4897d-213">`^` operatora logicznego wyłącznego OR</span><span class="sxs-lookup"><span data-stu-id="4897d-213">Logical exclusive OR operator `^`</span></span>
- <span data-ttu-id="4897d-214">`|` operatora logicznego OR</span><span class="sxs-lookup"><span data-stu-id="4897d-214">Logical OR operator `|`</span></span>
- <span data-ttu-id="4897d-215">Warunkowe operatory logiczne i `&&`</span><span class="sxs-lookup"><span data-stu-id="4897d-215">Conditional logical AND operator `&&`</span></span>
- <span data-ttu-id="4897d-216">Warunkowe operatory logiczne OR `||`</span><span class="sxs-lookup"><span data-stu-id="4897d-216">Conditional logical OR operator `||`</span></span>

<span data-ttu-id="4897d-217">Użyj nawiasów, `()`, aby zmienić kolejność oceny nałożona przez pierwszeństwo operatorów:</span><span class="sxs-lookup"><span data-stu-id="4897d-217">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence:</span></span>

[!code-csharp-interactive[operator precedence](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Precedence)]

<span data-ttu-id="4897d-218">Aby uzyskać pełną listę C# operatorów uporządkowanych według poziomu pierwszeństwa, zobacz sekcję [pierwszeństwo](index.md#operator-precedence) operatorów w artykule [ C# Operators](index.md) .</span><span class="sxs-lookup"><span data-stu-id="4897d-218">For the complete list of C# operators ordered by precedence level, see the [Operator precedence](index.md#operator-precedence) section of the [C# operators](index.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="4897d-219">Przeciążanie operatora</span><span class="sxs-lookup"><span data-stu-id="4897d-219">Operator overloadability</span></span>

<span data-ttu-id="4897d-220">Typ zdefiniowany przez użytkownika może [przeciążać](operator-overloading.md) operatory `!`, `&`, `|`i `^`.</span><span class="sxs-lookup"><span data-stu-id="4897d-220">A user-defined type can [overload](operator-overloading.md) the `!`, `&`, `|`, and `^` operators.</span></span> <span data-ttu-id="4897d-221">Gdy operator binarny jest przeciążony, odpowiadający mu operator przypisania złożonego jest również niejawnie przeciążony.</span><span class="sxs-lookup"><span data-stu-id="4897d-221">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="4897d-222">Typ zdefiniowany przez użytkownika nie może jawnie przeciążać złożonego operatora przypisania.</span><span class="sxs-lookup"><span data-stu-id="4897d-222">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

<span data-ttu-id="4897d-223">Typ zdefiniowany przez użytkownika nie może przeciążać warunkowych operatorów logicznych `&&` i `||`.</span><span class="sxs-lookup"><span data-stu-id="4897d-223">A user-defined type cannot overload the conditional logical operators `&&` and `||`.</span></span> <span data-ttu-id="4897d-224">Jednakże, jeśli typ zdefiniowany przez użytkownika przeciążuje [Operatory prawdy i FAŁSZ](true-false-operators.md) oraz operator `&` lub `|` w określony sposób, można również ocenić operacje `&&` lub `||` dla operandów tego typu.</span><span class="sxs-lookup"><span data-stu-id="4897d-224">However, if a user-defined type overloads the [true and false operators](true-false-operators.md) and the `&` or `|` operator in a certain way, the `&&` or `||` operation, respectively, can be evaluated for the operands of that type.</span></span> <span data-ttu-id="4897d-225">Aby uzyskać więcej informacji, zapoznaj się z sekcją [Operatory logiczne warunkowe](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) w [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="4897d-225">For more information, see the [User-defined conditional logical operators](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="4897d-226">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="4897d-226">C# language specification</span></span>

<span data-ttu-id="4897d-227">Aby uzyskać więcej informacji, zobacz następujące sekcje [ C# specyfikacji języka](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="4897d-227">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="4897d-228">Operator logiczny negacji</span><span class="sxs-lookup"><span data-stu-id="4897d-228">Logical negation operator</span></span>](~/_csharplang/spec/expressions.md#logical-negation-operator)
- [<span data-ttu-id="4897d-229">Operatory logiczne</span><span class="sxs-lookup"><span data-stu-id="4897d-229">Logical operators</span></span>](~/_csharplang/spec/expressions.md#logical-operators)
- [<span data-ttu-id="4897d-230">Warunkowe operatory logiczne</span><span class="sxs-lookup"><span data-stu-id="4897d-230">Conditional logical operators</span></span>](~/_csharplang/spec/expressions.md#conditional-logical-operators)
- [<span data-ttu-id="4897d-231">Przypisanie złożone</span><span class="sxs-lookup"><span data-stu-id="4897d-231">Compound assignment</span></span>](~/_csharplang/spec/expressions.md#compound-assignment)

## <a name="see-also"></a><span data-ttu-id="4897d-232">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4897d-232">See also</span></span>

- [<span data-ttu-id="4897d-233">C#odwoła</span><span class="sxs-lookup"><span data-stu-id="4897d-233">C# reference</span></span>](../index.md)
- [<span data-ttu-id="4897d-234">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="4897d-234">C# operators</span></span>](index.md)
- [<span data-ttu-id="4897d-235">Operatory bitowe i przesunięcia</span><span class="sxs-lookup"><span data-stu-id="4897d-235">Bitwise and shift operators</span></span>](bitwise-and-shift-operators.md)
