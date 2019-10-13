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
ms.openlocfilehash: f711bd04aeadb584eac1ecb0b644a36e2e496d08
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2019
ms.locfileid: "72290946"
---
# <a name="boolean-logical-operators-c-reference"></a><span data-ttu-id="14f4a-103">Logiczna operatory logiczne (C# odwołanie)</span><span class="sxs-lookup"><span data-stu-id="14f4a-103">Boolean logical operators (C# reference)</span></span>

<span data-ttu-id="14f4a-104">Następujące operatory wykonują operacje logiczne przy użyciu operandów [bool](../keywords/bool.md) :</span><span class="sxs-lookup"><span data-stu-id="14f4a-104">The following operators perform logical operations with the [bool](../keywords/bool.md) operands:</span></span>

- <span data-ttu-id="14f4a-105">Jednoargumentowy [`!` (Negacja logiczna)](#logical-negation-operator-) .</span><span class="sxs-lookup"><span data-stu-id="14f4a-105">Unary [`!` (logical negation)](#logical-negation-operator-) operator.</span></span>
- <span data-ttu-id="14f4a-106">Binarny [`&` (logiczny i)](#logical-and-operator-), [`|` (logiczne OR)](#logical-or-operator-)i [`^` (logiczne wyłącznych lub)](#logical-exclusive-or-operator-) .</span><span class="sxs-lookup"><span data-stu-id="14f4a-106">Binary [`&` (logical AND)](#logical-and-operator-), [`|` (logical OR)](#logical-or-operator-), and [`^` (logical exclusive OR)](#logical-exclusive-or-operator-) operators.</span></span> <span data-ttu-id="14f4a-107">Te operatory zawsze obliczają oba operandy.</span><span class="sxs-lookup"><span data-stu-id="14f4a-107">Those operators always evaluate both operands.</span></span>
- <span data-ttu-id="14f4a-108">Binarny [`&&` (warunkowe logiczne i)](#conditional-logical-and-operator-) i [`||` (warunkowe operatory logiczne or)](#conditional-logical-or-operator-) .</span><span class="sxs-lookup"><span data-stu-id="14f4a-108">Binary [`&&` (conditional logical AND)](#conditional-logical-and-operator-) and [`||` (conditional logical OR)](#conditional-logical-or-operator-) operators.</span></span> <span data-ttu-id="14f4a-109">Te operatory obliczają operand z prawej strony tylko wtedy, gdy jest to konieczne.</span><span class="sxs-lookup"><span data-stu-id="14f4a-109">Those operators evaluate the right-hand operand only if it's necessary.</span></span>

<span data-ttu-id="14f4a-110">Dla argumentów operacji typów [całkowitych](../builtin-types/integral-numeric-types.md) operatory `&`, `|` i `^` wykonują bitowe operacje logiczne.</span><span class="sxs-lookup"><span data-stu-id="14f4a-110">For the operands of the [integral](../builtin-types/integral-numeric-types.md) types, the `&`, `|`, and `^` operators perform bitwise logical operations.</span></span> <span data-ttu-id="14f4a-111">Aby uzyskać więcej informacji, zobacz [Operatory bitowe i przesunięcia](bitwise-and-shift-operators.md).</span><span class="sxs-lookup"><span data-stu-id="14f4a-111">For more information, see [Bitwise and shift operators](bitwise-and-shift-operators.md).</span></span>

## <a name="logical-negation-operator-"></a><span data-ttu-id="14f4a-112">Operator logiczny negacji</span><span class="sxs-lookup"><span data-stu-id="14f4a-112">Logical negation operator !</span></span>

<span data-ttu-id="14f4a-113">Prefiks jednoargumentowy `!` oblicza logiczne Negacja operandu.</span><span class="sxs-lookup"><span data-stu-id="14f4a-113">The unary prefix `!` operator computes logical negation of its operand.</span></span> <span data-ttu-id="14f4a-114">Oznacza to, że generuje `true`, jeśli operand zostanie obliczony do `false` i `false`, jeśli operand zostanie obliczony do `true`:</span><span class="sxs-lookup"><span data-stu-id="14f4a-114">That is, it produces `true`, if the operand evaluates to `false`, and `false`, if the operand evaluates to `true`:</span></span>

[!code-csharp-interactive[logical negation](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Negation)]

<span data-ttu-id="14f4a-115">Począwszy od C# 8,0, jednoargumentowy przyrostek `!` jest [operatorem o wartości null-łagodniejszej](null-forgiving.md).</span><span class="sxs-lookup"><span data-stu-id="14f4a-115">Starting with C# 8.0, the unary postfix `!` operator is a [null-forgiving operator](null-forgiving.md).</span></span>

## <a name="logical-and-operator-"></a><span data-ttu-id="14f4a-116">Operatory logiczne i &amp;</span><span class="sxs-lookup"><span data-stu-id="14f4a-116">Logical AND operator &amp;</span></span>

<span data-ttu-id="14f4a-117">Operator `&` oblicza wartość logiczną i jej operandów.</span><span class="sxs-lookup"><span data-stu-id="14f4a-117">The `&` operator computes the logical AND of its operands.</span></span> <span data-ttu-id="14f4a-118">Wynik `x & y` jest `true`, jeśli oba `x` i `y` są oceniane do `true`.</span><span class="sxs-lookup"><span data-stu-id="14f4a-118">The result of `x & y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="14f4a-119">W przeciwnym razie wynik jest `false`.</span><span class="sxs-lookup"><span data-stu-id="14f4a-119">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="14f4a-120">Operator `&` oblicza oba operandy nawet wtedy, gdy operand z lewej strony jest obliczany do `false`, tak aby wynik musi być `false` niezależnie od wartości operandu po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="14f4a-120">The `&` operator evaluates both operands even if the left-hand operand evaluates to `false`, so that the result must be `false` regardless of the value of the right-hand operand.</span></span>

<span data-ttu-id="14f4a-121">W poniższym przykładzie operand z prawej strony operatora `&` jest wywołaniem metody, które jest wykonywane niezależnie od wartości operandu po lewej stronie:</span><span class="sxs-lookup"><span data-stu-id="14f4a-121">In the following example, the right-hand operand of the `&` operator is a method call, which is performed regardless of the value of the left-hand operand:</span></span>

[!code-csharp-interactive[logical AND](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#And)]

<span data-ttu-id="14f4a-122">[Warunkowe operatory logiczne i](#conditional-logical-and-operator-) `&&` oblicza również wartość logiczną i jej operandy, ale nie oblicza wartości operandu po prawej stronie, jeśli wartość argumentu po lewej strony jest równa `false`.</span><span class="sxs-lookup"><span data-stu-id="14f4a-122">The [conditional logical AND operator](#conditional-logical-and-operator-) `&&` also computes the logical AND of its operands, but doesn't evaluate the right-hand operand if the left-hand operand evaluates to `false`.</span></span>

<span data-ttu-id="14f4a-123">Dla operandów typów całkowitych operator `&` oblicza koniunkcję [bitową i](bitwise-and-shift-operators.md#logical-and-operator-) jej operandy.</span><span class="sxs-lookup"><span data-stu-id="14f4a-123">For the operands of the integral types, the `&` operator computes the [bitwise logical AND](bitwise-and-shift-operators.md#logical-and-operator-) of its operands.</span></span> <span data-ttu-id="14f4a-124">Operator jednoargumentowy `&` jest operatorem [Address-of](pointer-related-operators.md#address-of-operator-).</span><span class="sxs-lookup"><span data-stu-id="14f4a-124">The unary `&` operator is the [address-of operator](pointer-related-operators.md#address-of-operator-).</span></span>

## <a name="logical-exclusive-or-operator-"></a><span data-ttu-id="14f4a-125">Operator wyłączny logicznego OR ^</span><span class="sxs-lookup"><span data-stu-id="14f4a-125">Logical exclusive OR operator ^</span></span>

<span data-ttu-id="14f4a-126">Operator `^` oblicza wartość logiczną na wyłączność lub, znaną również jako logiczna XOR, dla argumentów operacji.</span><span class="sxs-lookup"><span data-stu-id="14f4a-126">The `^` operator computes the logical exclusive OR, also known as the logical XOR, of its operands.</span></span> <span data-ttu-id="14f4a-127">Wynik `x ^ y` to `true`, jeśli `x` szacuje się `true` i `y` oblicza do `false`, lub `x` szacuje się `false` i `y` szacuje się `true`.</span><span class="sxs-lookup"><span data-stu-id="14f4a-127">The result of `x ^ y` is `true` if `x` evaluates to `true` and `y` evaluates to `false`, or `x` evaluates to `false` and `y` evaluates to `true`.</span></span> <span data-ttu-id="14f4a-128">W przeciwnym razie wynik jest `false`.</span><span class="sxs-lookup"><span data-stu-id="14f4a-128">Otherwise, the result is `false`.</span></span> <span data-ttu-id="14f4a-129">Oznacza to, że w przypadku operandów `bool` operator `^` oblicza ten sam wynik jako [operatora nierówności](equality-operators.md#inequality-operator-) `!=`.</span><span class="sxs-lookup"><span data-stu-id="14f4a-129">That is, for the `bool` operands, the `^` operator computes the same result as the [inequality operator](equality-operators.md#inequality-operator-) `!=`.</span></span>

[!code-csharp-interactive[logical exclusive OR](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Xor)]

<span data-ttu-id="14f4a-130">Dla operandów typów całkowitych operator `^` oblicza [bitową koniunkcję logiczną wyłącznych lub](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) jego operandów.</span><span class="sxs-lookup"><span data-stu-id="14f4a-130">For the operands of the integral types, the `^` operator computes the [bitwise logical exclusive OR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) of its operands.</span></span>

## <a name="logical-or-operator-"></a><span data-ttu-id="14f4a-131">Operator logiczny OR |</span><span class="sxs-lookup"><span data-stu-id="14f4a-131">Logical OR operator |</span></span>

<span data-ttu-id="14f4a-132">Operator `|` oblicza wartość logiczną lub argumentów operacji.</span><span class="sxs-lookup"><span data-stu-id="14f4a-132">The `|` operator computes the logical OR of its operands.</span></span> <span data-ttu-id="14f4a-133">Wynik `x | y` jest `true`, jeśli `x` lub `y` są oceniane do `true`.</span><span class="sxs-lookup"><span data-stu-id="14f4a-133">The result of `x | y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="14f4a-134">W przeciwnym razie wynik jest `false`.</span><span class="sxs-lookup"><span data-stu-id="14f4a-134">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="14f4a-135">Operator `|` oblicza oba operandy nawet wtedy, gdy operand z lewej strony jest obliczany do `true`, tak aby wynik musi być `true` niezależnie od wartości operandu po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="14f4a-135">The `|` operator evaluates both operands even if the left-hand operand evaluates to `true`, so that the result must be `true` regardless of the value of the right-hand operand.</span></span>

<span data-ttu-id="14f4a-136">W poniższym przykładzie operand z prawej strony operatora `|` jest wywołaniem metody, które jest wykonywane niezależnie od wartości operandu po lewej stronie:</span><span class="sxs-lookup"><span data-stu-id="14f4a-136">In the following example, the right-hand operand of the `|` operator is a method call, which is performed regardless of the value of the left-hand operand:</span></span>

[!code-csharp-interactive[logical OR](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Or)]

<span data-ttu-id="14f4a-137">[Warunkowe operatory logiczne or](#conditional-logical-or-operator-) `||` oblicza również wartość logiczną lub jej operandy, ale nie oblicza wartości operandu po prawej stronie, jeśli argument operacji leworęcznych ma wartość `true`.</span><span class="sxs-lookup"><span data-stu-id="14f4a-137">The [conditional logical OR operator](#conditional-logical-or-operator-) `||` also computes the logical OR of its operands, but doesn't evaluate the right-hand operand if the left-hand operand evaluates to `true`.</span></span>

<span data-ttu-id="14f4a-138">Dla operandów typów całkowitych operator `|` oblicza [bitową](bitwise-and-shift-operators.md#logical-or-operator-) koniunkcję lub jej operandów.</span><span class="sxs-lookup"><span data-stu-id="14f4a-138">For the operands of the integral types, the `|` operator computes the [bitwise logical OR](bitwise-and-shift-operators.md#logical-or-operator-) of its operands.</span></span>

## <a name="conditional-logical-and-operator-"></a><span data-ttu-id="14f4a-139">Warunkowe operatory logiczne i &amp; @ no__t-2</span><span class="sxs-lookup"><span data-stu-id="14f4a-139">Conditional logical AND operator &amp;&amp;</span></span>

<span data-ttu-id="14f4a-140">Warunkowe operatory logiczne i operator `&&`, znane także jako "koniunkcja" typu "Short-obwóding", oblicza wartość logiczną i jej operandów.</span><span class="sxs-lookup"><span data-stu-id="14f4a-140">The conditional logical AND operator `&&`, also known as the "short-circuiting" logical AND operator, computes the logical AND of its operands.</span></span> <span data-ttu-id="14f4a-141">Wynik `x && y` jest `true`, jeśli oba `x` i `y` są oceniane do `true`.</span><span class="sxs-lookup"><span data-stu-id="14f4a-141">The result of `x && y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="14f4a-142">W przeciwnym razie wynik jest `false`.</span><span class="sxs-lookup"><span data-stu-id="14f4a-142">Otherwise, the result is `false`.</span></span> <span data-ttu-id="14f4a-143">Jeśli `x` szacuje się do `false`, `y` nie jest oceniane.</span><span class="sxs-lookup"><span data-stu-id="14f4a-143">If `x` evaluates to `false`, `y` is not evaluated.</span></span>

<span data-ttu-id="14f4a-144">W poniższym przykładzie operand z prawej strony operatora `&&` jest wywołaniem metody, które nie jest wykonywane, jeśli argument operacji po lewej stronie szacuje się na `false`:</span><span class="sxs-lookup"><span data-stu-id="14f4a-144">In the following example, the right-hand operand of the `&&` operator is a method call, which isn't performed if the left-hand operand evaluates to `false`:</span></span>

[!code-csharp-interactive[conditional logical AND](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#ConditionalAnd)]

<span data-ttu-id="14f4a-145">[Operator logiczny i](#logical-and-operator-) `&` oblicza również wartość logiczną i jej operandy, ale zawsze oblicza oba operandy.</span><span class="sxs-lookup"><span data-stu-id="14f4a-145">The [logical AND operator](#logical-and-operator-) `&` also computes the logical AND of its operands, but always evaluates both operands.</span></span>

## <a name="conditional-logical-or-operator-"></a><span data-ttu-id="14f4a-146">Warunkowe logiczne OR operator | |</span><span class="sxs-lookup"><span data-stu-id="14f4a-146">Conditional logical OR operator ||</span></span>

<span data-ttu-id="14f4a-147">Warunkowe operatory logiczne OR `||`, nazywane także "operatorem" krótkiego obwodu ", oblicza wartość logiczną lub argumentów operacji.</span><span class="sxs-lookup"><span data-stu-id="14f4a-147">The conditional logical OR operator `||`, also known as the "short-circuiting" logical OR operator, computes the logical OR of its operands.</span></span> <span data-ttu-id="14f4a-148">Wynik `x || y` jest `true`, jeśli `x` lub `y` są oceniane do `true`.</span><span class="sxs-lookup"><span data-stu-id="14f4a-148">The result of `x || y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="14f4a-149">W przeciwnym razie wynik jest `false`.</span><span class="sxs-lookup"><span data-stu-id="14f4a-149">Otherwise, the result is `false`.</span></span> <span data-ttu-id="14f4a-150">Jeśli `x` szacuje się do `true`, `y` nie jest oceniane.</span><span class="sxs-lookup"><span data-stu-id="14f4a-150">If `x` evaluates to `true`, `y` is not evaluated.</span></span>

<span data-ttu-id="14f4a-151">W poniższym przykładzie operand z prawej strony operatora `||` jest wywołaniem metody, które nie jest wykonywane, jeśli argument operacji po lewej stronie szacuje się na `true`:</span><span class="sxs-lookup"><span data-stu-id="14f4a-151">In the following example, the right-hand operand of the `||` operator is a method call, which isn't performed if the left-hand operand evaluates to `true`:</span></span>

[!code-csharp-interactive[conditional logical OR](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#ConditionalOr)]

<span data-ttu-id="14f4a-152">[Operator logiczny or](#logical-or-operator-) `|` oblicza również wartość logiczną lub argumentów operacji, ale zawsze oblicza oba operandy.</span><span class="sxs-lookup"><span data-stu-id="14f4a-152">The [logical OR operator](#logical-or-operator-) `|` also computes the logical OR of its operands, but always evaluates both operands.</span></span>

## <a name="nullable-boolean-logical-operators"></a><span data-ttu-id="14f4a-153">Logiczne operatory wartości null</span><span class="sxs-lookup"><span data-stu-id="14f4a-153">Nullable Boolean logical operators</span></span>

<span data-ttu-id="14f4a-154">W przypadku operandów `bool?` operatory `&` i `|` obsługują logikę z trzema wartościami.</span><span class="sxs-lookup"><span data-stu-id="14f4a-154">For the `bool?` operands, the `&` and `|` operators support the three-valued logic.</span></span> <span data-ttu-id="14f4a-155">Semantyka tych operatorów jest definiowana przez następującą tabelę:</span><span class="sxs-lookup"><span data-stu-id="14f4a-155">The semantics of these operators is defined by the following table:</span></span>  
  
|<span data-ttu-id="14f4a-156">x</span><span class="sxs-lookup"><span data-stu-id="14f4a-156">x</span></span>|<span data-ttu-id="14f4a-157">T</span><span class="sxs-lookup"><span data-stu-id="14f4a-157">y</span></span>|<span data-ttu-id="14f4a-158">x & y</span><span class="sxs-lookup"><span data-stu-id="14f4a-158">x&y</span></span>|<span data-ttu-id="14f4a-159">x&#124;y</span><span class="sxs-lookup"><span data-stu-id="14f4a-159">x&#124;y</span></span>|  
|----|----|----|----|  
|<span data-ttu-id="14f4a-160">true</span><span class="sxs-lookup"><span data-stu-id="14f4a-160">true</span></span>|<span data-ttu-id="14f4a-161">true</span><span class="sxs-lookup"><span data-stu-id="14f4a-161">true</span></span>|<span data-ttu-id="14f4a-162">true</span><span class="sxs-lookup"><span data-stu-id="14f4a-162">true</span></span>|<span data-ttu-id="14f4a-163">true</span><span class="sxs-lookup"><span data-stu-id="14f4a-163">true</span></span>|  
|<span data-ttu-id="14f4a-164">true</span><span class="sxs-lookup"><span data-stu-id="14f4a-164">true</span></span>|<span data-ttu-id="14f4a-165">false</span><span class="sxs-lookup"><span data-stu-id="14f4a-165">false</span></span>|<span data-ttu-id="14f4a-166">false</span><span class="sxs-lookup"><span data-stu-id="14f4a-166">false</span></span>|<span data-ttu-id="14f4a-167">true</span><span class="sxs-lookup"><span data-stu-id="14f4a-167">true</span></span>|  
|<span data-ttu-id="14f4a-168">true</span><span class="sxs-lookup"><span data-stu-id="14f4a-168">true</span></span>|<span data-ttu-id="14f4a-169">null</span><span class="sxs-lookup"><span data-stu-id="14f4a-169">null</span></span>|<span data-ttu-id="14f4a-170">null</span><span class="sxs-lookup"><span data-stu-id="14f4a-170">null</span></span>|<span data-ttu-id="14f4a-171">true</span><span class="sxs-lookup"><span data-stu-id="14f4a-171">true</span></span>|  
|<span data-ttu-id="14f4a-172">false</span><span class="sxs-lookup"><span data-stu-id="14f4a-172">false</span></span>|<span data-ttu-id="14f4a-173">true</span><span class="sxs-lookup"><span data-stu-id="14f4a-173">true</span></span>|<span data-ttu-id="14f4a-174">false</span><span class="sxs-lookup"><span data-stu-id="14f4a-174">false</span></span>|<span data-ttu-id="14f4a-175">true</span><span class="sxs-lookup"><span data-stu-id="14f4a-175">true</span></span>|  
|<span data-ttu-id="14f4a-176">false</span><span class="sxs-lookup"><span data-stu-id="14f4a-176">false</span></span>|<span data-ttu-id="14f4a-177">false</span><span class="sxs-lookup"><span data-stu-id="14f4a-177">false</span></span>|<span data-ttu-id="14f4a-178">false</span><span class="sxs-lookup"><span data-stu-id="14f4a-178">false</span></span>|<span data-ttu-id="14f4a-179">false</span><span class="sxs-lookup"><span data-stu-id="14f4a-179">false</span></span>|  
|<span data-ttu-id="14f4a-180">false</span><span class="sxs-lookup"><span data-stu-id="14f4a-180">false</span></span>|<span data-ttu-id="14f4a-181">null</span><span class="sxs-lookup"><span data-stu-id="14f4a-181">null</span></span>|<span data-ttu-id="14f4a-182">false</span><span class="sxs-lookup"><span data-stu-id="14f4a-182">false</span></span>|<span data-ttu-id="14f4a-183">null</span><span class="sxs-lookup"><span data-stu-id="14f4a-183">null</span></span>|  
|<span data-ttu-id="14f4a-184">null</span><span class="sxs-lookup"><span data-stu-id="14f4a-184">null</span></span>|<span data-ttu-id="14f4a-185">true</span><span class="sxs-lookup"><span data-stu-id="14f4a-185">true</span></span>|<span data-ttu-id="14f4a-186">null</span><span class="sxs-lookup"><span data-stu-id="14f4a-186">null</span></span>|<span data-ttu-id="14f4a-187">true</span><span class="sxs-lookup"><span data-stu-id="14f4a-187">true</span></span>|  
|<span data-ttu-id="14f4a-188">null</span><span class="sxs-lookup"><span data-stu-id="14f4a-188">null</span></span>|<span data-ttu-id="14f4a-189">false</span><span class="sxs-lookup"><span data-stu-id="14f4a-189">false</span></span>|<span data-ttu-id="14f4a-190">false</span><span class="sxs-lookup"><span data-stu-id="14f4a-190">false</span></span>|<span data-ttu-id="14f4a-191">null</span><span class="sxs-lookup"><span data-stu-id="14f4a-191">null</span></span>|  
|<span data-ttu-id="14f4a-192">null</span><span class="sxs-lookup"><span data-stu-id="14f4a-192">null</span></span>|<span data-ttu-id="14f4a-193">null</span><span class="sxs-lookup"><span data-stu-id="14f4a-193">null</span></span>|<span data-ttu-id="14f4a-194">null</span><span class="sxs-lookup"><span data-stu-id="14f4a-194">null</span></span>|<span data-ttu-id="14f4a-195">null</span><span class="sxs-lookup"><span data-stu-id="14f4a-195">null</span></span>|  

<span data-ttu-id="14f4a-196">Zachowanie tych operatorów różni się od typowego zachowania operatora z zerowymi typami wartości.</span><span class="sxs-lookup"><span data-stu-id="14f4a-196">The behavior of those operators differs from the typical operator behavior with nullable value types.</span></span> <span data-ttu-id="14f4a-197">Zazwyczaj operator, który jest zdefiniowany dla operandów typu wartości, może być również używany z operandami odpowiadającego typu wartości null.</span><span class="sxs-lookup"><span data-stu-id="14f4a-197">Typically, an operator which is defined for operands of a value type can be also used with operands of the corresponding nullable value type.</span></span> <span data-ttu-id="14f4a-198">Taki operator wytwarza `null`, jeśli którykolwiek z jego operandów jest `null`.</span><span class="sxs-lookup"><span data-stu-id="14f4a-198">Such an operator produces `null` if any of its operands is `null`.</span></span> <span data-ttu-id="14f4a-199">Jednak operatory `&` i `|` mogą generować wartości inne niż null, nawet jeśli jeden z operandów jest `null`.</span><span class="sxs-lookup"><span data-stu-id="14f4a-199">However, the `&` and `|` operators can produce non-null even if one of the operands is `null`.</span></span> <span data-ttu-id="14f4a-200">Aby uzyskać więcej informacji o zachowaniu operatora z typami wartości null, zobacz sekcję [operatorów](../../programming-guide/nullable-types/using-nullable-types.md#operators) w artykule [używanie typów wartości dopuszczających wartość null](../../programming-guide/nullable-types/using-nullable-types.md) .</span><span class="sxs-lookup"><span data-stu-id="14f4a-200">For more information about the operator behavior with nullable value types, see the [Operators](../../programming-guide/nullable-types/using-nullable-types.md#operators) section of the [Using nullable value types](../../programming-guide/nullable-types/using-nullable-types.md) article.</span></span>

<span data-ttu-id="14f4a-201">Można również użyć operatorów `!` i `^` z operandami `bool?`, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="14f4a-201">You can also use the `!` and `^` operators with the `bool?` operands, as the following example shows:</span></span>

[!code-csharp-interactive[lifted negation and xor](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#WithNullableBoolean)]

<span data-ttu-id="14f4a-202">Warunkowe operatory logiczne `&&` i `||` nie obsługują argumentów operacji `bool?`.</span><span class="sxs-lookup"><span data-stu-id="14f4a-202">The conditional logical operators `&&` and `||` don't support the `bool?` operands.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="14f4a-203">Przypisanie złożone</span><span class="sxs-lookup"><span data-stu-id="14f4a-203">Compound assignment</span></span>

<span data-ttu-id="14f4a-204">Dla operatora binarnego `op` wyrażenie złożonego przypisania formularza</span><span class="sxs-lookup"><span data-stu-id="14f4a-204">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="14f4a-205">jest równoważne</span><span class="sxs-lookup"><span data-stu-id="14f4a-205">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="14f4a-206">z tą różnicą, że `x` jest obliczana tylko raz.</span><span class="sxs-lookup"><span data-stu-id="14f4a-206">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="14f4a-207">Operatory `&`, `|` i `^` obsługują przypisanie złożone, co ilustruje poniższy przykład:</span><span class="sxs-lookup"><span data-stu-id="14f4a-207">The `&`, `|`, and `^` operators support compound assignment, as the following example shows:</span></span>

[!code-csharp-interactive[compound assignment](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#CompoundAssignment)]

<span data-ttu-id="14f4a-208">Warunkowe operatory logiczne `&&` i `||` nie obsługują przypisania złożonego.</span><span class="sxs-lookup"><span data-stu-id="14f4a-208">The conditional logical operators `&&` and `||` don't support compound assignment.</span></span>

## <a name="operator-precedence"></a><span data-ttu-id="14f4a-209">Pierwszeństwo operatorów</span><span class="sxs-lookup"><span data-stu-id="14f4a-209">Operator precedence</span></span>

<span data-ttu-id="14f4a-210">Poniższa lista porządkuje operatory logiczne rozpoczynając od najwyższego priorytetu do najniższego:</span><span class="sxs-lookup"><span data-stu-id="14f4a-210">The following list orders logical operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="14f4a-211">Operator logiczny negacji `!`</span><span class="sxs-lookup"><span data-stu-id="14f4a-211">Logical negation operator `!`</span></span>
- <span data-ttu-id="14f4a-212">Operatory logiczne i `&`</span><span class="sxs-lookup"><span data-stu-id="14f4a-212">Logical AND operator `&`</span></span>
- <span data-ttu-id="14f4a-213">Operator wyłączny logicznego OR `^`</span><span class="sxs-lookup"><span data-stu-id="14f4a-213">Logical exclusive OR operator `^`</span></span>
- <span data-ttu-id="14f4a-214">@No__t operatora logicznego OR — 0</span><span class="sxs-lookup"><span data-stu-id="14f4a-214">Logical OR operator `|`</span></span>
- <span data-ttu-id="14f4a-215">Warunkowe operatory logiczne i `&&`</span><span class="sxs-lookup"><span data-stu-id="14f4a-215">Conditional logical AND operator `&&`</span></span>
- <span data-ttu-id="14f4a-216">Warunkowe operatory logiczne OR `||`</span><span class="sxs-lookup"><span data-stu-id="14f4a-216">Conditional logical OR operator `||`</span></span>

<span data-ttu-id="14f4a-217">Użyj nawiasów, `()`, aby zmienić kolejność oceny nałożona przez pierwszeństwo operatorów:</span><span class="sxs-lookup"><span data-stu-id="14f4a-217">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence:</span></span>

[!code-csharp-interactive[operator precedence](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Precedence)]

<span data-ttu-id="14f4a-218">Aby uzyskać pełną listę C# operatorów uporządkowanych według poziomu pierwszeństwa, zobacz [ C# operatory](index.md).</span><span class="sxs-lookup"><span data-stu-id="14f4a-218">For the complete list of C# operators ordered by precedence level, see [C# operators](index.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="14f4a-219">Przeciążanie operatora</span><span class="sxs-lookup"><span data-stu-id="14f4a-219">Operator overloadability</span></span>

<span data-ttu-id="14f4a-220">Typ zdefiniowany przez użytkownika może [przeciążać](operator-overloading.md) operatory `!`, `&`, `|` i `^`.</span><span class="sxs-lookup"><span data-stu-id="14f4a-220">A user-defined type can [overload](operator-overloading.md) the `!`, `&`, `|`, and `^` operators.</span></span> <span data-ttu-id="14f4a-221">Gdy operator binarny jest przeciążony, odpowiadający mu operator przypisania złożonego jest również niejawnie przeciążony.</span><span class="sxs-lookup"><span data-stu-id="14f4a-221">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="14f4a-222">Typ zdefiniowany przez użytkownika nie może jawnie przeciążać złożonego operatora przypisania.</span><span class="sxs-lookup"><span data-stu-id="14f4a-222">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

<span data-ttu-id="14f4a-223">Typ zdefiniowany przez użytkownika nie może przeciążać warunkowych operatorów logicznych `&&` i `||`.</span><span class="sxs-lookup"><span data-stu-id="14f4a-223">A user-defined type cannot overload the conditional logical operators `&&` and `||`.</span></span> <span data-ttu-id="14f4a-224">Jednakże, jeśli typ zdefiniowany przez użytkownika przeciążuje [Operatory prawdy i FAŁSZ](true-false-operators.md) oraz operator `&` lub `|` w określony sposób, można również ocenić operacje `&&` lub `||` dla operandów tego typu.</span><span class="sxs-lookup"><span data-stu-id="14f4a-224">However, if a user-defined type overloads the [true and false operators](true-false-operators.md) and the `&` or `|` operator in a certain way, the `&&` or `||` operation, respectively, can be evaluated for the operands of that type.</span></span> <span data-ttu-id="14f4a-225">Aby uzyskać więcej informacji, zapoznaj się z sekcją [Operatory logiczne warunkowe](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) w [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="14f4a-225">For more information, see the [User-defined conditional logical operators](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="14f4a-226">C#Specyfikacja języka</span><span class="sxs-lookup"><span data-stu-id="14f4a-226">C# language specification</span></span>

<span data-ttu-id="14f4a-227">Aby uzyskać więcej informacji, zobacz następujące sekcje [ C# specyfikacji języka](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="14f4a-227">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="14f4a-228">Operator logiczny negacji</span><span class="sxs-lookup"><span data-stu-id="14f4a-228">Logical negation operator</span></span>](~/_csharplang/spec/expressions.md#logical-negation-operator)
- [<span data-ttu-id="14f4a-229">Operatory logiczne</span><span class="sxs-lookup"><span data-stu-id="14f4a-229">Logical operators</span></span>](~/_csharplang/spec/expressions.md#logical-operators)
- [<span data-ttu-id="14f4a-230">Warunkowe operatory logiczne</span><span class="sxs-lookup"><span data-stu-id="14f4a-230">Conditional logical operators</span></span>](~/_csharplang/spec/expressions.md#conditional-logical-operators)
- [<span data-ttu-id="14f4a-231">Przypisanie złożone</span><span class="sxs-lookup"><span data-stu-id="14f4a-231">Compound assignment</span></span>](~/_csharplang/spec/expressions.md#compound-assignment)

## <a name="see-also"></a><span data-ttu-id="14f4a-232">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="14f4a-232">See also</span></span>

- [<span data-ttu-id="14f4a-233">C#odwoła</span><span class="sxs-lookup"><span data-stu-id="14f4a-233">C# reference</span></span>](../index.md)
- [<span data-ttu-id="14f4a-234">C#zainteresowanych</span><span class="sxs-lookup"><span data-stu-id="14f4a-234">C# operators</span></span>](index.md)
- [<span data-ttu-id="14f4a-235">Operatory bitowe i przesunięcia</span><span class="sxs-lookup"><span data-stu-id="14f4a-235">Bitwise and shift operators</span></span>](bitwise-and-shift-operators.md)
