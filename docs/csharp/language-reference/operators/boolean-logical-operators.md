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
ms.openlocfilehash: e355a89e27ea5bd6e4335b39c4e669610c4b0553
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319107"
---
# <a name="boolean-logical-operators-c-reference"></a><span data-ttu-id="0f7b3-103">Logiczna operatory logiczne (C# odwołanie)</span><span class="sxs-lookup"><span data-stu-id="0f7b3-103">Boolean logical operators (C# reference)</span></span>

<span data-ttu-id="0f7b3-104">Następujące operatory wykonują operacje logiczne przy użyciu operandów [bool](../keywords/bool.md) :</span><span class="sxs-lookup"><span data-stu-id="0f7b3-104">The following operators perform logical operations with the [bool](../keywords/bool.md) operands:</span></span>

- <span data-ttu-id="0f7b3-105">Jednoargumentowy [`!` (Negacja logiczna)](#logical-negation-operator-) .</span><span class="sxs-lookup"><span data-stu-id="0f7b3-105">Unary [`!` (logical negation)](#logical-negation-operator-) operator.</span></span>
- <span data-ttu-id="0f7b3-106">Binarny [`&` (logiczny i)](#logical-and-operator-), [`|` (logiczne OR)](#logical-or-operator-)i [`^` (logiczne wyłącznych lub)](#logical-exclusive-or-operator-) .</span><span class="sxs-lookup"><span data-stu-id="0f7b3-106">Binary [`&` (logical AND)](#logical-and-operator-), [`|` (logical OR)](#logical-or-operator-), and [`^` (logical exclusive OR)](#logical-exclusive-or-operator-) operators.</span></span> <span data-ttu-id="0f7b3-107">Te operatory zawsze obliczają oba operandy.</span><span class="sxs-lookup"><span data-stu-id="0f7b3-107">Those operators always evaluate both operands.</span></span>
- <span data-ttu-id="0f7b3-108">Binarny [`&&` (warunkowe logiczne i)](#conditional-logical-and-operator-) i [`||` (warunkowe operatory logiczne or)](#conditional-logical-or-operator-) .</span><span class="sxs-lookup"><span data-stu-id="0f7b3-108">Binary [`&&` (conditional logical AND)](#conditional-logical-and-operator-) and [`||` (conditional logical OR)](#conditional-logical-or-operator-) operators.</span></span> <span data-ttu-id="0f7b3-109">Te operatory obliczają operand z prawej strony tylko wtedy, gdy jest to konieczne.</span><span class="sxs-lookup"><span data-stu-id="0f7b3-109">Those operators evaluate the right-hand operand only if it's necessary.</span></span>

<span data-ttu-id="0f7b3-110">Dla argumentów operacji typów [całkowitych](../builtin-types/integral-numeric-types.md) operatory `&`, `|` i `^` wykonują bitowe operacje logiczne.</span><span class="sxs-lookup"><span data-stu-id="0f7b3-110">For the operands of the [integral](../builtin-types/integral-numeric-types.md) types, the `&`, `|`, and `^` operators perform bitwise logical operations.</span></span> <span data-ttu-id="0f7b3-111">Aby uzyskać więcej informacji, zobacz [Operatory bitowe i przesunięcia](bitwise-and-shift-operators.md).</span><span class="sxs-lookup"><span data-stu-id="0f7b3-111">For more information, see [Bitwise and shift operators](bitwise-and-shift-operators.md).</span></span>

## <a name="logical-negation-operator-"></a><span data-ttu-id="0f7b3-112">Operator logiczny negacji</span><span class="sxs-lookup"><span data-stu-id="0f7b3-112">Logical negation operator !</span></span>

<span data-ttu-id="0f7b3-113">Prefiks jednoargumentowy `!` oblicza logiczne Negacja operandu.</span><span class="sxs-lookup"><span data-stu-id="0f7b3-113">The unary prefix `!` operator computes logical negation of its operand.</span></span> <span data-ttu-id="0f7b3-114">Oznacza to, że generuje `true`, jeśli operand zostanie obliczony do `false` i `false`, jeśli operand zostanie obliczony do `true`:</span><span class="sxs-lookup"><span data-stu-id="0f7b3-114">That is, it produces `true`, if the operand evaluates to `false`, and `false`, if the operand evaluates to `true`:</span></span>

[!code-csharp-interactive[logical negation](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Negation)]

<span data-ttu-id="0f7b3-115">Począwszy od C# 8,0, jednoargumentowy przyrostek `!` jest [operatorem null-łagodniejszej](null-forgiving.md).</span><span class="sxs-lookup"><span data-stu-id="0f7b3-115">Starting with C# 8.0, the unary postfix `!` operator is the [null-forgiving operator](null-forgiving.md).</span></span>

## <a name="logical-and-operator-"></a><span data-ttu-id="0f7b3-116">Operatory logiczne i &amp;</span><span class="sxs-lookup"><span data-stu-id="0f7b3-116">Logical AND operator &amp;</span></span>

<span data-ttu-id="0f7b3-117">Operator `&` oblicza wartość logiczną i jej operandów.</span><span class="sxs-lookup"><span data-stu-id="0f7b3-117">The `&` operator computes the logical AND of its operands.</span></span> <span data-ttu-id="0f7b3-118">Wynik `x & y` jest `true`, jeśli oba `x` i `y` są oceniane do `true`.</span><span class="sxs-lookup"><span data-stu-id="0f7b3-118">The result of `x & y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="0f7b3-119">W przeciwnym razie wynik jest `false`.</span><span class="sxs-lookup"><span data-stu-id="0f7b3-119">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="0f7b3-120">Operator `&` oblicza oba operandy nawet wtedy, gdy operand z lewej strony jest obliczany do `false`, tak aby wynik musi być `false` niezależnie od wartości operandu po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="0f7b3-120">The `&` operator evaluates both operands even if the left-hand operand evaluates to `false`, so that the result must be `false` regardless of the value of the right-hand operand.</span></span>

<span data-ttu-id="0f7b3-121">W poniższym przykładzie operand z prawej strony operatora `&` jest wywołaniem metody, które jest wykonywane niezależnie od wartości operandu po lewej stronie:</span><span class="sxs-lookup"><span data-stu-id="0f7b3-121">In the following example, the right-hand operand of the `&` operator is a method call, which is performed regardless of the value of the left-hand operand:</span></span>

[!code-csharp-interactive[logical AND](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#And)]

<span data-ttu-id="0f7b3-122">[Warunkowe operatory logiczne i](#conditional-logical-and-operator-) `&&` oblicza również wartość logiczną i jej operandy, ale nie oblicza wartości operandu po prawej stronie, jeśli wartość argumentu po lewej strony jest równa `false`.</span><span class="sxs-lookup"><span data-stu-id="0f7b3-122">The [conditional logical AND operator](#conditional-logical-and-operator-) `&&` also computes the logical AND of its operands, but doesn't evaluate the right-hand operand if the left-hand operand evaluates to `false`.</span></span>

<span data-ttu-id="0f7b3-123">Dla operandów typów całkowitych operator `&` oblicza koniunkcję [bitową i](bitwise-and-shift-operators.md#logical-and-operator-) jej operandy.</span><span class="sxs-lookup"><span data-stu-id="0f7b3-123">For the operands of the integral types, the `&` operator computes the [bitwise logical AND](bitwise-and-shift-operators.md#logical-and-operator-) of its operands.</span></span> <span data-ttu-id="0f7b3-124">Operator jednoargumentowy `&` jest operatorem [Address-of](pointer-related-operators.md#address-of-operator-).</span><span class="sxs-lookup"><span data-stu-id="0f7b3-124">The unary `&` operator is the [address-of operator](pointer-related-operators.md#address-of-operator-).</span></span>

## <a name="logical-exclusive-or-operator-"></a><span data-ttu-id="0f7b3-125">Operator wyłączny logicznego OR ^</span><span class="sxs-lookup"><span data-stu-id="0f7b3-125">Logical exclusive OR operator ^</span></span>

<span data-ttu-id="0f7b3-126">Operator `^` oblicza wartość logiczną na wyłączność lub, znaną również jako logiczna XOR, dla argumentów operacji.</span><span class="sxs-lookup"><span data-stu-id="0f7b3-126">The `^` operator computes the logical exclusive OR, also known as the logical XOR, of its operands.</span></span> <span data-ttu-id="0f7b3-127">Wynik `x ^ y` to `true`, jeśli `x` szacuje się `true` i `y` oblicza do `false`, lub `x` szacuje się `false` i `y` szacuje się `true`.</span><span class="sxs-lookup"><span data-stu-id="0f7b3-127">The result of `x ^ y` is `true` if `x` evaluates to `true` and `y` evaluates to `false`, or `x` evaluates to `false` and `y` evaluates to `true`.</span></span> <span data-ttu-id="0f7b3-128">W przeciwnym razie wynik jest `false`.</span><span class="sxs-lookup"><span data-stu-id="0f7b3-128">Otherwise, the result is `false`.</span></span> <span data-ttu-id="0f7b3-129">Oznacza to, że w przypadku operandów `bool` operator `^` oblicza ten sam wynik jako [operatora nierówności](equality-operators.md#inequality-operator-) `!=`.</span><span class="sxs-lookup"><span data-stu-id="0f7b3-129">That is, for the `bool` operands, the `^` operator computes the same result as the [inequality operator](equality-operators.md#inequality-operator-) `!=`.</span></span>

[!code-csharp-interactive[logical exclusive OR](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Xor)]

<span data-ttu-id="0f7b3-130">Dla operandów typów całkowitych operator `^` oblicza [bitową koniunkcję logiczną wyłącznych lub](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) jego operandów.</span><span class="sxs-lookup"><span data-stu-id="0f7b3-130">For the operands of the integral types, the `^` operator computes the [bitwise logical exclusive OR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) of its operands.</span></span>

## <a name="logical-or-operator-"></a><span data-ttu-id="0f7b3-131">Operator logiczny OR |</span><span class="sxs-lookup"><span data-stu-id="0f7b3-131">Logical OR operator |</span></span>

<span data-ttu-id="0f7b3-132">Operator `|` oblicza wartość logiczną lub argumentów operacji.</span><span class="sxs-lookup"><span data-stu-id="0f7b3-132">The `|` operator computes the logical OR of its operands.</span></span> <span data-ttu-id="0f7b3-133">Wynik `x | y` jest `true`, jeśli `x` lub `y` są oceniane do `true`.</span><span class="sxs-lookup"><span data-stu-id="0f7b3-133">The result of `x | y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="0f7b3-134">W przeciwnym razie wynik jest `false`.</span><span class="sxs-lookup"><span data-stu-id="0f7b3-134">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="0f7b3-135">Operator `|` oblicza oba operandy nawet wtedy, gdy operand z lewej strony jest obliczany do `true`, tak aby wynik musi być `true` niezależnie od wartości operandu po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="0f7b3-135">The `|` operator evaluates both operands even if the left-hand operand evaluates to `true`, so that the result must be `true` regardless of the value of the right-hand operand.</span></span>

<span data-ttu-id="0f7b3-136">W poniższym przykładzie operand z prawej strony operatora `|` jest wywołaniem metody, które jest wykonywane niezależnie od wartości operandu po lewej stronie:</span><span class="sxs-lookup"><span data-stu-id="0f7b3-136">In the following example, the right-hand operand of the `|` operator is a method call, which is performed regardless of the value of the left-hand operand:</span></span>

[!code-csharp-interactive[logical OR](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Or)]

<span data-ttu-id="0f7b3-137">[Warunkowe operatory logiczne or](#conditional-logical-or-operator-) `||` oblicza również wartość logiczną lub jej operandy, ale nie oblicza wartości operandu po prawej stronie, jeśli argument operacji leworęcznych ma wartość `true`.</span><span class="sxs-lookup"><span data-stu-id="0f7b3-137">The [conditional logical OR operator](#conditional-logical-or-operator-) `||` also computes the logical OR of its operands, but doesn't evaluate the right-hand operand if the left-hand operand evaluates to `true`.</span></span>

<span data-ttu-id="0f7b3-138">Dla operandów typów całkowitych operator `|` oblicza [bitową](bitwise-and-shift-operators.md#logical-or-operator-) koniunkcję lub jej operandów.</span><span class="sxs-lookup"><span data-stu-id="0f7b3-138">For the operands of the integral types, the `|` operator computes the [bitwise logical OR](bitwise-and-shift-operators.md#logical-or-operator-) of its operands.</span></span>

## <a name="conditional-logical-and-operator-"></a><span data-ttu-id="0f7b3-139">Warunkowe operatory logiczne i &amp; @ no__t-2</span><span class="sxs-lookup"><span data-stu-id="0f7b3-139">Conditional logical AND operator &amp;&amp;</span></span>

<span data-ttu-id="0f7b3-140">Warunkowe operatory logiczne i operator `&&`, znane także jako "koniunkcja" typu "Short-obwóding", oblicza wartość logiczną i jej operandów.</span><span class="sxs-lookup"><span data-stu-id="0f7b3-140">The conditional logical AND operator `&&`, also known as the "short-circuiting" logical AND operator, computes the logical AND of its operands.</span></span> <span data-ttu-id="0f7b3-141">Wynik `x && y` jest `true`, jeśli oba `x` i `y` są oceniane do `true`.</span><span class="sxs-lookup"><span data-stu-id="0f7b3-141">The result of `x && y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="0f7b3-142">W przeciwnym razie wynik jest `false`.</span><span class="sxs-lookup"><span data-stu-id="0f7b3-142">Otherwise, the result is `false`.</span></span> <span data-ttu-id="0f7b3-143">Jeśli `x` szacuje się do `false`, `y` nie jest oceniane.</span><span class="sxs-lookup"><span data-stu-id="0f7b3-143">If `x` evaluates to `false`, `y` is not evaluated.</span></span>

<span data-ttu-id="0f7b3-144">W poniższym przykładzie operand z prawej strony operatora `&&` jest wywołaniem metody, które nie jest wykonywane, jeśli argument operacji po lewej stronie szacuje się na `false`:</span><span class="sxs-lookup"><span data-stu-id="0f7b3-144">In the following example, the right-hand operand of the `&&` operator is a method call, which isn't performed if the left-hand operand evaluates to `false`:</span></span>

[!code-csharp-interactive[conditional logical AND](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#ConditionalAnd)]

<span data-ttu-id="0f7b3-145">[Operator logiczny i](#logical-and-operator-) `&` oblicza również wartość logiczną i jej operandy, ale zawsze oblicza oba operandy.</span><span class="sxs-lookup"><span data-stu-id="0f7b3-145">The [logical AND operator](#logical-and-operator-) `&` also computes the logical AND of its operands, but always evaluates both operands.</span></span>

## <a name="conditional-logical-or-operator-"></a><span data-ttu-id="0f7b3-146">Warunkowe logiczne OR operator | |</span><span class="sxs-lookup"><span data-stu-id="0f7b3-146">Conditional logical OR operator ||</span></span>

<span data-ttu-id="0f7b3-147">Warunkowe operatory logiczne OR `||`, nazywane także "operatorem" krótkiego obwodu ", oblicza wartość logiczną lub argumentów operacji.</span><span class="sxs-lookup"><span data-stu-id="0f7b3-147">The conditional logical OR operator `||`, also known as the "short-circuiting" logical OR operator, computes the logical OR of its operands.</span></span> <span data-ttu-id="0f7b3-148">Wynik `x || y` jest `true`, jeśli `x` lub `y` są oceniane do `true`.</span><span class="sxs-lookup"><span data-stu-id="0f7b3-148">The result of `x || y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="0f7b3-149">W przeciwnym razie wynik jest `false`.</span><span class="sxs-lookup"><span data-stu-id="0f7b3-149">Otherwise, the result is `false`.</span></span> <span data-ttu-id="0f7b3-150">Jeśli `x` szacuje się do `true`, `y` nie jest oceniane.</span><span class="sxs-lookup"><span data-stu-id="0f7b3-150">If `x` evaluates to `true`, `y` is not evaluated.</span></span>

<span data-ttu-id="0f7b3-151">W poniższym przykładzie operand z prawej strony operatora `||` jest wywołaniem metody, które nie jest wykonywane, jeśli argument operacji po lewej stronie szacuje się na `true`:</span><span class="sxs-lookup"><span data-stu-id="0f7b3-151">In the following example, the right-hand operand of the `||` operator is a method call, which isn't performed if the left-hand operand evaluates to `true`:</span></span>

[!code-csharp-interactive[conditional logical OR](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#ConditionalOr)]

<span data-ttu-id="0f7b3-152">[Operator logiczny or](#logical-or-operator-) `|` oblicza również wartość logiczną lub argumentów operacji, ale zawsze oblicza oba operandy.</span><span class="sxs-lookup"><span data-stu-id="0f7b3-152">The [logical OR operator](#logical-or-operator-) `|` also computes the logical OR of its operands, but always evaluates both operands.</span></span>

## <a name="nullable-boolean-logical-operators"></a><span data-ttu-id="0f7b3-153">Logiczne operatory wartości null</span><span class="sxs-lookup"><span data-stu-id="0f7b3-153">Nullable Boolean logical operators</span></span>

<span data-ttu-id="0f7b3-154">W przypadku operandów `bool?` operatory `&` i `|` obsługują logikę z trzema wartościami.</span><span class="sxs-lookup"><span data-stu-id="0f7b3-154">For the `bool?` operands, the `&` and `|` operators support the three-valued logic.</span></span> <span data-ttu-id="0f7b3-155">Semantyka tych operatorów jest definiowana przez następującą tabelę:</span><span class="sxs-lookup"><span data-stu-id="0f7b3-155">The semantics of these operators is defined by the following table:</span></span>  
  
|<span data-ttu-id="0f7b3-156">x</span><span class="sxs-lookup"><span data-stu-id="0f7b3-156">x</span></span>|<span data-ttu-id="0f7b3-157">t</span><span class="sxs-lookup"><span data-stu-id="0f7b3-157">y</span></span>|<span data-ttu-id="0f7b3-158">x & y</span><span class="sxs-lookup"><span data-stu-id="0f7b3-158">x&y</span></span>|<span data-ttu-id="0f7b3-159">x&#124;y</span><span class="sxs-lookup"><span data-stu-id="0f7b3-159">x&#124;y</span></span>|  
|----|----|----|----|  
|<span data-ttu-id="0f7b3-160">true</span><span class="sxs-lookup"><span data-stu-id="0f7b3-160">true</span></span>|<span data-ttu-id="0f7b3-161">true</span><span class="sxs-lookup"><span data-stu-id="0f7b3-161">true</span></span>|<span data-ttu-id="0f7b3-162">true</span><span class="sxs-lookup"><span data-stu-id="0f7b3-162">true</span></span>|<span data-ttu-id="0f7b3-163">true</span><span class="sxs-lookup"><span data-stu-id="0f7b3-163">true</span></span>|  
|<span data-ttu-id="0f7b3-164">true</span><span class="sxs-lookup"><span data-stu-id="0f7b3-164">true</span></span>|<span data-ttu-id="0f7b3-165">false</span><span class="sxs-lookup"><span data-stu-id="0f7b3-165">false</span></span>|<span data-ttu-id="0f7b3-166">false</span><span class="sxs-lookup"><span data-stu-id="0f7b3-166">false</span></span>|<span data-ttu-id="0f7b3-167">true</span><span class="sxs-lookup"><span data-stu-id="0f7b3-167">true</span></span>|  
|<span data-ttu-id="0f7b3-168">true</span><span class="sxs-lookup"><span data-stu-id="0f7b3-168">true</span></span>|<span data-ttu-id="0f7b3-169">wartość null</span><span class="sxs-lookup"><span data-stu-id="0f7b3-169">null</span></span>|<span data-ttu-id="0f7b3-170">wartość null</span><span class="sxs-lookup"><span data-stu-id="0f7b3-170">null</span></span>|<span data-ttu-id="0f7b3-171">true</span><span class="sxs-lookup"><span data-stu-id="0f7b3-171">true</span></span>|  
|<span data-ttu-id="0f7b3-172">false</span><span class="sxs-lookup"><span data-stu-id="0f7b3-172">false</span></span>|<span data-ttu-id="0f7b3-173">true</span><span class="sxs-lookup"><span data-stu-id="0f7b3-173">true</span></span>|<span data-ttu-id="0f7b3-174">false</span><span class="sxs-lookup"><span data-stu-id="0f7b3-174">false</span></span>|<span data-ttu-id="0f7b3-175">true</span><span class="sxs-lookup"><span data-stu-id="0f7b3-175">true</span></span>|  
|<span data-ttu-id="0f7b3-176">false</span><span class="sxs-lookup"><span data-stu-id="0f7b3-176">false</span></span>|<span data-ttu-id="0f7b3-177">false</span><span class="sxs-lookup"><span data-stu-id="0f7b3-177">false</span></span>|<span data-ttu-id="0f7b3-178">false</span><span class="sxs-lookup"><span data-stu-id="0f7b3-178">false</span></span>|<span data-ttu-id="0f7b3-179">false</span><span class="sxs-lookup"><span data-stu-id="0f7b3-179">false</span></span>|  
|<span data-ttu-id="0f7b3-180">false</span><span class="sxs-lookup"><span data-stu-id="0f7b3-180">false</span></span>|<span data-ttu-id="0f7b3-181">wartość null</span><span class="sxs-lookup"><span data-stu-id="0f7b3-181">null</span></span>|<span data-ttu-id="0f7b3-182">false</span><span class="sxs-lookup"><span data-stu-id="0f7b3-182">false</span></span>|<span data-ttu-id="0f7b3-183">wartość null</span><span class="sxs-lookup"><span data-stu-id="0f7b3-183">null</span></span>|  
|<span data-ttu-id="0f7b3-184">wartość null</span><span class="sxs-lookup"><span data-stu-id="0f7b3-184">null</span></span>|<span data-ttu-id="0f7b3-185">true</span><span class="sxs-lookup"><span data-stu-id="0f7b3-185">true</span></span>|<span data-ttu-id="0f7b3-186">wartość null</span><span class="sxs-lookup"><span data-stu-id="0f7b3-186">null</span></span>|<span data-ttu-id="0f7b3-187">true</span><span class="sxs-lookup"><span data-stu-id="0f7b3-187">true</span></span>|  
|<span data-ttu-id="0f7b3-188">wartość null</span><span class="sxs-lookup"><span data-stu-id="0f7b3-188">null</span></span>|<span data-ttu-id="0f7b3-189">false</span><span class="sxs-lookup"><span data-stu-id="0f7b3-189">false</span></span>|<span data-ttu-id="0f7b3-190">false</span><span class="sxs-lookup"><span data-stu-id="0f7b3-190">false</span></span>|<span data-ttu-id="0f7b3-191">wartość null</span><span class="sxs-lookup"><span data-stu-id="0f7b3-191">null</span></span>|  
|<span data-ttu-id="0f7b3-192">wartość null</span><span class="sxs-lookup"><span data-stu-id="0f7b3-192">null</span></span>|<span data-ttu-id="0f7b3-193">wartość null</span><span class="sxs-lookup"><span data-stu-id="0f7b3-193">null</span></span>|<span data-ttu-id="0f7b3-194">wartość null</span><span class="sxs-lookup"><span data-stu-id="0f7b3-194">null</span></span>|<span data-ttu-id="0f7b3-195">wartość null</span><span class="sxs-lookup"><span data-stu-id="0f7b3-195">null</span></span>|  

<span data-ttu-id="0f7b3-196">Zachowanie tych operatorów różni się od typowego zachowania operatora z zerowymi typami wartości.</span><span class="sxs-lookup"><span data-stu-id="0f7b3-196">The behavior of those operators differs from the typical operator behavior with nullable value types.</span></span> <span data-ttu-id="0f7b3-197">Zazwyczaj operator, który jest zdefiniowany dla operandów typu wartości, może być również używany z operandami odpowiadającego typu wartości null.</span><span class="sxs-lookup"><span data-stu-id="0f7b3-197">Typically, an operator which is defined for operands of a value type can be also used with operands of the corresponding nullable value type.</span></span> <span data-ttu-id="0f7b3-198">Taki operator wytwarza `null`, jeśli którykolwiek z jego operandów jest `null`.</span><span class="sxs-lookup"><span data-stu-id="0f7b3-198">Such an operator produces `null` if any of its operands is `null`.</span></span> <span data-ttu-id="0f7b3-199">Jednak operatory `&` i `|` mogą generować wartości inne niż null, nawet jeśli jeden z operandów jest `null`.</span><span class="sxs-lookup"><span data-stu-id="0f7b3-199">However, the `&` and `|` operators can produce non-null even if one of the operands is `null`.</span></span> <span data-ttu-id="0f7b3-200">Aby uzyskać więcej informacji o zachowaniu operatora z typami wartości null, zobacz sekcję [operatorów](../../programming-guide/nullable-types/using-nullable-types.md#operators) w artykule [używanie typów wartości dopuszczających wartość null](../../programming-guide/nullable-types/using-nullable-types.md) .</span><span class="sxs-lookup"><span data-stu-id="0f7b3-200">For more information about the operator behavior with nullable value types, see the [Operators](../../programming-guide/nullable-types/using-nullable-types.md#operators) section of the [Using nullable value types](../../programming-guide/nullable-types/using-nullable-types.md) article.</span></span>

<span data-ttu-id="0f7b3-201">Można również użyć operatorów `!` i `^` z operandami `bool?`, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="0f7b3-201">You can also use the `!` and `^` operators with the `bool?` operands, as the following example shows:</span></span>

[!code-csharp-interactive[lifted negation and xor](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#WithNullableBoolean)]

<span data-ttu-id="0f7b3-202">Warunkowe operatory logiczne `&&` i `||` nie obsługują argumentów operacji `bool?`.</span><span class="sxs-lookup"><span data-stu-id="0f7b3-202">The conditional logical operators `&&` and `||` don't support the `bool?` operands.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="0f7b3-203">Przypisanie złożone</span><span class="sxs-lookup"><span data-stu-id="0f7b3-203">Compound assignment</span></span>

<span data-ttu-id="0f7b3-204">Dla operatora binarnego `op` wyrażenie złożonego przypisania formularza</span><span class="sxs-lookup"><span data-stu-id="0f7b3-204">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="0f7b3-205">jest równoważny</span><span class="sxs-lookup"><span data-stu-id="0f7b3-205">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="0f7b3-206">z tą różnicą, że `x` jest obliczana tylko raz.</span><span class="sxs-lookup"><span data-stu-id="0f7b3-206">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="0f7b3-207">Operatory `&`, `|` i `^` obsługują przypisanie złożone, co ilustruje poniższy przykład:</span><span class="sxs-lookup"><span data-stu-id="0f7b3-207">The `&`, `|`, and `^` operators support compound assignment, as the following example shows:</span></span>

[!code-csharp-interactive[compound assignment](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#CompoundAssignment)]

<span data-ttu-id="0f7b3-208">Warunkowe operatory logiczne `&&` i `||` nie obsługują przypisania złożonego.</span><span class="sxs-lookup"><span data-stu-id="0f7b3-208">The conditional logical operators `&&` and `||` don't support compound assignment.</span></span>

## <a name="operator-precedence"></a><span data-ttu-id="0f7b3-209">Pierwszeństwo operatorów</span><span class="sxs-lookup"><span data-stu-id="0f7b3-209">Operator precedence</span></span>

<span data-ttu-id="0f7b3-210">Poniższa lista porządkuje operatory logiczne rozpoczynając od najwyższego priorytetu do najniższego:</span><span class="sxs-lookup"><span data-stu-id="0f7b3-210">The following list orders logical operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="0f7b3-211">Operator logiczny negacji `!`</span><span class="sxs-lookup"><span data-stu-id="0f7b3-211">Logical negation operator `!`</span></span>
- <span data-ttu-id="0f7b3-212">Operatory logiczne i `&`</span><span class="sxs-lookup"><span data-stu-id="0f7b3-212">Logical AND operator `&`</span></span>
- <span data-ttu-id="0f7b3-213">Operator wyłączny logicznego OR `^`</span><span class="sxs-lookup"><span data-stu-id="0f7b3-213">Logical exclusive OR operator `^`</span></span>
- <span data-ttu-id="0f7b3-214">@No__t operatora logicznego OR — 0</span><span class="sxs-lookup"><span data-stu-id="0f7b3-214">Logical OR operator `|`</span></span>
- <span data-ttu-id="0f7b3-215">Warunkowe operatory logiczne i `&&`</span><span class="sxs-lookup"><span data-stu-id="0f7b3-215">Conditional logical AND operator `&&`</span></span>
- <span data-ttu-id="0f7b3-216">Warunkowe operatory logiczne OR `||`</span><span class="sxs-lookup"><span data-stu-id="0f7b3-216">Conditional logical OR operator `||`</span></span>

<span data-ttu-id="0f7b3-217">Użyj nawiasów, `()`, aby zmienić kolejność oceny nałożona przez pierwszeństwo operatorów:</span><span class="sxs-lookup"><span data-stu-id="0f7b3-217">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence:</span></span>

[!code-csharp-interactive[operator precedence](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Precedence)]

<span data-ttu-id="0f7b3-218">Aby uzyskać pełną listę C# operatorów uporządkowanych według poziomu pierwszeństwa, zobacz [ C# operatory](index.md).</span><span class="sxs-lookup"><span data-stu-id="0f7b3-218">For the complete list of C# operators ordered by precedence level, see [C# operators](index.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="0f7b3-219">Przeciążanie operatora</span><span class="sxs-lookup"><span data-stu-id="0f7b3-219">Operator overloadability</span></span>

<span data-ttu-id="0f7b3-220">Typ zdefiniowany przez użytkownika może [przeciążać](operator-overloading.md) operatory `!`, `&`, `|` i `^`.</span><span class="sxs-lookup"><span data-stu-id="0f7b3-220">A user-defined type can [overload](operator-overloading.md) the `!`, `&`, `|`, and `^` operators.</span></span> <span data-ttu-id="0f7b3-221">Gdy operator binarny jest przeciążony, odpowiadający mu operator przypisania złożonego jest również niejawnie przeciążony.</span><span class="sxs-lookup"><span data-stu-id="0f7b3-221">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="0f7b3-222">Typ zdefiniowany przez użytkownika nie może jawnie przeciążać złożonego operatora przypisania.</span><span class="sxs-lookup"><span data-stu-id="0f7b3-222">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

<span data-ttu-id="0f7b3-223">Typ zdefiniowany przez użytkownika nie może przeciążać warunkowych operatorów logicznych `&&` i `||`.</span><span class="sxs-lookup"><span data-stu-id="0f7b3-223">A user-defined type cannot overload the conditional logical operators `&&` and `||`.</span></span> <span data-ttu-id="0f7b3-224">Jednakże, jeśli typ zdefiniowany przez użytkownika przeciążuje [Operatory prawdy i FAŁSZ](true-false-operators.md) oraz operator `&` lub `|` w określony sposób, można również ocenić operacje `&&` lub `||` dla operandów tego typu.</span><span class="sxs-lookup"><span data-stu-id="0f7b3-224">However, if a user-defined type overloads the [true and false operators](true-false-operators.md) and the `&` or `|` operator in a certain way, the `&&` or `||` operation, respectively, can be evaluated for the operands of that type.</span></span> <span data-ttu-id="0f7b3-225">Aby uzyskać więcej informacji, zapoznaj się z sekcją [Operatory logiczne warunkowe](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) w [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="0f7b3-225">For more information, see the [User-defined conditional logical operators](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="0f7b3-226">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="0f7b3-226">C# language specification</span></span>

<span data-ttu-id="0f7b3-227">Aby uzyskać więcej informacji, zobacz następujące sekcje [ C# specyfikacji języka](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="0f7b3-227">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="0f7b3-228">Operator logiczny negacji</span><span class="sxs-lookup"><span data-stu-id="0f7b3-228">Logical negation operator</span></span>](~/_csharplang/spec/expressions.md#logical-negation-operator)
- [<span data-ttu-id="0f7b3-229">Operatory logiczne</span><span class="sxs-lookup"><span data-stu-id="0f7b3-229">Logical operators</span></span>](~/_csharplang/spec/expressions.md#logical-operators)
- [<span data-ttu-id="0f7b3-230">Warunkowe operatory logiczne</span><span class="sxs-lookup"><span data-stu-id="0f7b3-230">Conditional logical operators</span></span>](~/_csharplang/spec/expressions.md#conditional-logical-operators)
- [<span data-ttu-id="0f7b3-231">Przypisanie złożone</span><span class="sxs-lookup"><span data-stu-id="0f7b3-231">Compound assignment</span></span>](~/_csharplang/spec/expressions.md#compound-assignment)

## <a name="see-also"></a><span data-ttu-id="0f7b3-232">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0f7b3-232">See also</span></span>

- [<span data-ttu-id="0f7b3-233">C#odwoła</span><span class="sxs-lookup"><span data-stu-id="0f7b3-233">C# reference</span></span>](../index.md)
- [<span data-ttu-id="0f7b3-234">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="0f7b3-234">C# operators</span></span>](index.md)
- [<span data-ttu-id="0f7b3-235">Operatory bitowe i przesunięcia</span><span class="sxs-lookup"><span data-stu-id="0f7b3-235">Bitwise and shift operators</span></span>](bitwise-and-shift-operators.md)
