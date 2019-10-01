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
ms.openlocfilehash: cc25d4bfd444dc0acb30fc1c6e6c3c9918af537c
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698683"
---
# <a name="boolean-logical-operators-c-reference"></a><span data-ttu-id="910d3-103">Logiczna operatory logiczne (C# odwołanie)</span><span class="sxs-lookup"><span data-stu-id="910d3-103">Boolean logical operators (C# reference)</span></span>

<span data-ttu-id="910d3-104">Następujące operatory wykonują operacje logiczne przy użyciu operandów [bool](../keywords/bool.md) :</span><span class="sxs-lookup"><span data-stu-id="910d3-104">The following operators perform logical operations with the [bool](../keywords/bool.md) operands:</span></span>

- <span data-ttu-id="910d3-105">Jednoargumentowy [`!` (Negacja logiczna)](#logical-negation-operator-) .</span><span class="sxs-lookup"><span data-stu-id="910d3-105">Unary [`!` (logical negation)](#logical-negation-operator-) operator.</span></span>
- <span data-ttu-id="910d3-106">Binarny [`&` (logiczny i)](#logical-and-operator-), [`|` (logiczne OR)](#logical-or-operator-)i [`^` (logiczne wyłącznych lub)](#logical-exclusive-or-operator-) .</span><span class="sxs-lookup"><span data-stu-id="910d3-106">Binary [`&` (logical AND)](#logical-and-operator-), [`|` (logical OR)](#logical-or-operator-), and [`^` (logical exclusive OR)](#logical-exclusive-or-operator-) operators.</span></span> <span data-ttu-id="910d3-107">Te operatory zawsze obliczają oba operandy.</span><span class="sxs-lookup"><span data-stu-id="910d3-107">Those operators always evaluate both operands.</span></span>
- <span data-ttu-id="910d3-108">Binarny [`&&` (warunkowe logiczne i)](#conditional-logical-and-operator-) i [`||` (warunkowe operatory logiczne or)](#conditional-logical-or-operator-) .</span><span class="sxs-lookup"><span data-stu-id="910d3-108">Binary [`&&` (conditional logical AND)](#conditional-logical-and-operator-) and [`||` (conditional logical OR)](#conditional-logical-or-operator-) operators.</span></span> <span data-ttu-id="910d3-109">Te operatory obliczają operand z prawej strony tylko wtedy, gdy jest to konieczne.</span><span class="sxs-lookup"><span data-stu-id="910d3-109">Those operators evaluate the right-hand operand only if it's necessary.</span></span>

<span data-ttu-id="910d3-110">Dla argumentów operacji typów [całkowitych](../builtin-types/integral-numeric-types.md) operatory `&`, `|` i `^` wykonują bitowe operacje logiczne.</span><span class="sxs-lookup"><span data-stu-id="910d3-110">For the operands of the [integral](../builtin-types/integral-numeric-types.md) types, the `&`, `|`, and `^` operators perform bitwise logical operations.</span></span> <span data-ttu-id="910d3-111">Aby uzyskać więcej informacji, zobacz [Operatory bitowe i przesunięcia](bitwise-and-shift-operators.md).</span><span class="sxs-lookup"><span data-stu-id="910d3-111">For more information, see [Bitwise and shift operators](bitwise-and-shift-operators.md).</span></span>

## <a name="logical-negation-operator-"></a><span data-ttu-id="910d3-112">Operator logiczny negacji</span><span class="sxs-lookup"><span data-stu-id="910d3-112">Logical negation operator !</span></span>

<span data-ttu-id="910d3-113">Operator `!` oblicza logiczne Negacja operandu.</span><span class="sxs-lookup"><span data-stu-id="910d3-113">The `!` operator computes logical negation of its operand.</span></span> <span data-ttu-id="910d3-114">Oznacza to, że generuje `true`, jeśli operand zostanie obliczony do `false` i `false`, jeśli operand zostanie obliczony do `true`:</span><span class="sxs-lookup"><span data-stu-id="910d3-114">That is, it produces `true`, if the operand evaluates to `false`, and `false`, if the operand evaluates to `true`:</span></span>

[!code-csharp-interactive[logical negation](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Negation)]

<span data-ttu-id="910d3-115">Począwszy od C# 8,0, jednoargumentowy przyrostek `!` jest operatorem o wartości null-łagodniejszej.</span><span class="sxs-lookup"><span data-stu-id="910d3-115">Starting with C# 8.0, the unary postfix `!` operator is a null-forgiving operator.</span></span> <span data-ttu-id="910d3-116">W włączonym kontekście dopuszczającym wartość null można używać go do deklarowania wyrażenia `x` typu odwołania do wartości null nie ma wartości null: `x!`.</span><span class="sxs-lookup"><span data-stu-id="910d3-116">In an enabled nullable annotation context, you use it to declare that expression `x` of a nullable reference type isn't null: `x!`.</span></span> <span data-ttu-id="910d3-117">Aby uzyskać więcej informacji, zobacz [typy referencyjne dopuszczające wartość null](../../nullable-references.md).</span><span class="sxs-lookup"><span data-stu-id="910d3-117">For more information, see [Nullable reference types](../../nullable-references.md).</span></span>

## <a name="logical-and-operator-"></a><span data-ttu-id="910d3-118">Operatory logiczne i &amp;</span><span class="sxs-lookup"><span data-stu-id="910d3-118">Logical AND operator &amp;</span></span>

<span data-ttu-id="910d3-119">Operator `&` oblicza wartość logiczną i jej operandów.</span><span class="sxs-lookup"><span data-stu-id="910d3-119">The `&` operator computes the logical AND of its operands.</span></span> <span data-ttu-id="910d3-120">Wynik `x & y` jest `true`, jeśli oba `x` i `y` są oceniane do `true`.</span><span class="sxs-lookup"><span data-stu-id="910d3-120">The result of `x & y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="910d3-121">W przeciwnym razie wynik jest `false`.</span><span class="sxs-lookup"><span data-stu-id="910d3-121">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="910d3-122">Operator `&` oblicza oba operandy nawet wtedy, gdy operand z lewej strony jest obliczany do `false`, tak aby wynik musi być `false` niezależnie od wartości operandu po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="910d3-122">The `&` operator evaluates both operands even if the left-hand operand evaluates to `false`, so that the result must be `false` regardless of the value of the right-hand operand.</span></span>

<span data-ttu-id="910d3-123">W poniższym przykładzie operand z prawej strony operatora `&` jest wywołaniem metody, które jest wykonywane niezależnie od wartości operandu po lewej stronie:</span><span class="sxs-lookup"><span data-stu-id="910d3-123">In the following example, the right-hand operand of the `&` operator is a method call, which is performed regardless of the value of the left-hand operand:</span></span>

[!code-csharp-interactive[logical AND](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#And)]

<span data-ttu-id="910d3-124">[Warunkowe operatory logiczne i](#conditional-logical-and-operator-) `&&` oblicza również wartość logiczną i jej operandy, ale nie oblicza wartości operandu po prawej stronie, jeśli wartość argumentu po lewej strony jest równa `false`.</span><span class="sxs-lookup"><span data-stu-id="910d3-124">The [conditional logical AND operator](#conditional-logical-and-operator-) `&&` also computes the logical AND of its operands, but doesn't evaluate the right-hand operand if the left-hand operand evaluates to `false`.</span></span>

<span data-ttu-id="910d3-125">Dla operandów typów całkowitych operator `&` oblicza koniunkcję [bitową i](bitwise-and-shift-operators.md#logical-and-operator-) jej operandy.</span><span class="sxs-lookup"><span data-stu-id="910d3-125">For the operands of the integral types, the `&` operator computes the [bitwise logical AND](bitwise-and-shift-operators.md#logical-and-operator-) of its operands.</span></span> <span data-ttu-id="910d3-126">Operator jednoargumentowy `&` jest operatorem [Address-of](pointer-related-operators.md#address-of-operator-).</span><span class="sxs-lookup"><span data-stu-id="910d3-126">The unary `&` operator is the [address-of operator](pointer-related-operators.md#address-of-operator-).</span></span>

## <a name="logical-exclusive-or-operator-"></a><span data-ttu-id="910d3-127">Operator wyłączny logicznego OR ^</span><span class="sxs-lookup"><span data-stu-id="910d3-127">Logical exclusive OR operator ^</span></span>

<span data-ttu-id="910d3-128">Operator `^` oblicza wartość logiczną na wyłączność lub, znaną również jako logiczna XOR, dla argumentów operacji.</span><span class="sxs-lookup"><span data-stu-id="910d3-128">The `^` operator computes the logical exclusive OR, also known as the logical XOR, of its operands.</span></span> <span data-ttu-id="910d3-129">Wynik `x ^ y` to `true`, jeśli `x` szacuje się `true` i `y` oblicza do `false`, lub `x` szacuje się `false` i `y` szacuje się `true`.</span><span class="sxs-lookup"><span data-stu-id="910d3-129">The result of `x ^ y` is `true` if `x` evaluates to `true` and `y` evaluates to `false`, or `x` evaluates to `false` and `y` evaluates to `true`.</span></span> <span data-ttu-id="910d3-130">W przeciwnym razie wynik jest `false`.</span><span class="sxs-lookup"><span data-stu-id="910d3-130">Otherwise, the result is `false`.</span></span> <span data-ttu-id="910d3-131">Oznacza to, że w przypadku operandów `bool` operator `^` oblicza ten sam wynik jako [operatora nierówności](equality-operators.md#inequality-operator-) `!=`.</span><span class="sxs-lookup"><span data-stu-id="910d3-131">That is, for the `bool` operands, the `^` operator computes the same result as the [inequality operator](equality-operators.md#inequality-operator-) `!=`.</span></span>

[!code-csharp-interactive[logical exclusive OR](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Xor)]

<span data-ttu-id="910d3-132">Dla operandów typów całkowitych operator `^` oblicza [bitową koniunkcję logiczną wyłącznych lub](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) jego operandów.</span><span class="sxs-lookup"><span data-stu-id="910d3-132">For the operands of the integral types, the `^` operator computes the [bitwise logical exclusive OR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) of its operands.</span></span>

## <a name="logical-or-operator-"></a><span data-ttu-id="910d3-133">Operator logiczny OR |</span><span class="sxs-lookup"><span data-stu-id="910d3-133">Logical OR operator |</span></span>

<span data-ttu-id="910d3-134">Operator `|` oblicza wartość logiczną lub argumentów operacji.</span><span class="sxs-lookup"><span data-stu-id="910d3-134">The `|` operator computes the logical OR of its operands.</span></span> <span data-ttu-id="910d3-135">Wynik `x | y` jest `true`, jeśli `x` lub `y` są oceniane do `true`.</span><span class="sxs-lookup"><span data-stu-id="910d3-135">The result of `x | y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="910d3-136">W przeciwnym razie wynik jest `false`.</span><span class="sxs-lookup"><span data-stu-id="910d3-136">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="910d3-137">Operator `|` oblicza oba operandy nawet wtedy, gdy operand z lewej strony jest obliczany do `true`, tak aby wynik musi być `true` niezależnie od wartości operandu po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="910d3-137">The `|` operator evaluates both operands even if the left-hand operand evaluates to `true`, so that the result must be `true` regardless of the value of the right-hand operand.</span></span>

<span data-ttu-id="910d3-138">W poniższym przykładzie operand z prawej strony operatora `|` jest wywołaniem metody, które jest wykonywane niezależnie od wartości operandu po lewej stronie:</span><span class="sxs-lookup"><span data-stu-id="910d3-138">In the following example, the right-hand operand of the `|` operator is a method call, which is performed regardless of the value of the left-hand operand:</span></span>

[!code-csharp-interactive[logical OR](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Or)]

<span data-ttu-id="910d3-139">[Warunkowe operatory logiczne or](#conditional-logical-or-operator-) `||` oblicza również wartość logiczną lub jej operandy, ale nie oblicza wartości operandu po prawej stronie, jeśli argument operacji leworęcznych ma wartość `true`.</span><span class="sxs-lookup"><span data-stu-id="910d3-139">The [conditional logical OR operator](#conditional-logical-or-operator-) `||` also computes the logical OR of its operands, but doesn't evaluate the right-hand operand if the left-hand operand evaluates to `true`.</span></span>

<span data-ttu-id="910d3-140">Dla operandów typów całkowitych operator `|` oblicza [bitową](bitwise-and-shift-operators.md#logical-or-operator-) koniunkcję lub jej operandów.</span><span class="sxs-lookup"><span data-stu-id="910d3-140">For the operands of the integral types, the `|` operator computes the [bitwise logical OR](bitwise-and-shift-operators.md#logical-or-operator-) of its operands.</span></span>

## <a name="conditional-logical-and-operator-"></a><span data-ttu-id="910d3-141">Warunkowe operatory logiczne i &amp; @ no__t-2</span><span class="sxs-lookup"><span data-stu-id="910d3-141">Conditional logical AND operator &amp;&amp;</span></span>

<span data-ttu-id="910d3-142">Warunkowe operatory logiczne i operator `&&`, znane także jako "koniunkcja" typu "Short-obwóding", oblicza wartość logiczną i jej operandów.</span><span class="sxs-lookup"><span data-stu-id="910d3-142">The conditional logical AND operator `&&`, also known as the "short-circuiting" logical AND operator, computes the logical AND of its operands.</span></span> <span data-ttu-id="910d3-143">Wynik `x && y` jest `true`, jeśli oba `x` i `y` są oceniane do `true`.</span><span class="sxs-lookup"><span data-stu-id="910d3-143">The result of `x && y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="910d3-144">W przeciwnym razie wynik jest `false`.</span><span class="sxs-lookup"><span data-stu-id="910d3-144">Otherwise, the result is `false`.</span></span> <span data-ttu-id="910d3-145">Jeśli `x` szacuje się do `false`, `y` nie jest oceniane.</span><span class="sxs-lookup"><span data-stu-id="910d3-145">If `x` evaluates to `false`, `y` is not evaluated.</span></span>

<span data-ttu-id="910d3-146">W poniższym przykładzie operand z prawej strony operatora `&&` jest wywołaniem metody, które nie jest wykonywane, jeśli argument operacji po lewej stronie szacuje się na `false`:</span><span class="sxs-lookup"><span data-stu-id="910d3-146">In the following example, the right-hand operand of the `&&` operator is a method call, which isn't performed if the left-hand operand evaluates to `false`:</span></span>

[!code-csharp-interactive[conditional logical AND](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#ConditionalAnd)]

<span data-ttu-id="910d3-147">[Operator logiczny i](#logical-and-operator-) `&` oblicza również wartość logiczną i jej operandy, ale zawsze oblicza oba operandy.</span><span class="sxs-lookup"><span data-stu-id="910d3-147">The [logical AND operator](#logical-and-operator-) `&` also computes the logical AND of its operands, but always evaluates both operands.</span></span>

## <a name="conditional-logical-or-operator-"></a><span data-ttu-id="910d3-148">Warunkowe logiczne OR operator | |</span><span class="sxs-lookup"><span data-stu-id="910d3-148">Conditional logical OR operator ||</span></span>

<span data-ttu-id="910d3-149">Warunkowe operatory logiczne OR `||`, nazywane także "operatorem" krótkiego obwodu ", oblicza wartość logiczną lub argumentów operacji.</span><span class="sxs-lookup"><span data-stu-id="910d3-149">The conditional logical OR operator `||`, also known as the "short-circuiting" logical OR operator, computes the logical OR of its operands.</span></span> <span data-ttu-id="910d3-150">Wynik `x || y` jest `true`, jeśli `x` lub `y` są oceniane do `true`.</span><span class="sxs-lookup"><span data-stu-id="910d3-150">The result of `x || y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="910d3-151">W przeciwnym razie wynik jest `false`.</span><span class="sxs-lookup"><span data-stu-id="910d3-151">Otherwise, the result is `false`.</span></span> <span data-ttu-id="910d3-152">Jeśli `x` szacuje się do `true`, `y` nie jest oceniane.</span><span class="sxs-lookup"><span data-stu-id="910d3-152">If `x` evaluates to `true`, `y` is not evaluated.</span></span>

<span data-ttu-id="910d3-153">W poniższym przykładzie operand z prawej strony operatora `||` jest wywołaniem metody, które nie jest wykonywane, jeśli argument operacji po lewej stronie szacuje się na `true`:</span><span class="sxs-lookup"><span data-stu-id="910d3-153">In the following example, the right-hand operand of the `||` operator is a method call, which isn't performed if the left-hand operand evaluates to `true`:</span></span>

[!code-csharp-interactive[conditional logical OR](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#ConditionalOr)]

<span data-ttu-id="910d3-154">[Operator logiczny or](#logical-or-operator-) `|` oblicza również wartość logiczną lub argumentów operacji, ale zawsze oblicza oba operandy.</span><span class="sxs-lookup"><span data-stu-id="910d3-154">The [logical OR operator](#logical-or-operator-) `|` also computes the logical OR of its operands, but always evaluates both operands.</span></span>

## <a name="nullable-boolean-logical-operators"></a><span data-ttu-id="910d3-155">Logiczne operatory wartości null</span><span class="sxs-lookup"><span data-stu-id="910d3-155">Nullable Boolean logical operators</span></span>

<span data-ttu-id="910d3-156">W przypadku operandów `bool?` operatory `&` i `|` obsługują logikę z trzema wartościami.</span><span class="sxs-lookup"><span data-stu-id="910d3-156">For the `bool?` operands, the `&` and `|` operators support the three-valued logic.</span></span> <span data-ttu-id="910d3-157">Semantyka tych operatorów jest definiowana przez następującą tabelę:</span><span class="sxs-lookup"><span data-stu-id="910d3-157">The semantics of these operators is defined by the following table:</span></span>  
  
|<span data-ttu-id="910d3-158">x</span><span class="sxs-lookup"><span data-stu-id="910d3-158">x</span></span>|<span data-ttu-id="910d3-159">t</span><span class="sxs-lookup"><span data-stu-id="910d3-159">y</span></span>|<span data-ttu-id="910d3-160">x & y</span><span class="sxs-lookup"><span data-stu-id="910d3-160">x&y</span></span>|<span data-ttu-id="910d3-161">x&#124;y</span><span class="sxs-lookup"><span data-stu-id="910d3-161">x&#124;y</span></span>|  
|----|----|----|----|  
|<span data-ttu-id="910d3-162">true</span><span class="sxs-lookup"><span data-stu-id="910d3-162">true</span></span>|<span data-ttu-id="910d3-163">true</span><span class="sxs-lookup"><span data-stu-id="910d3-163">true</span></span>|<span data-ttu-id="910d3-164">true</span><span class="sxs-lookup"><span data-stu-id="910d3-164">true</span></span>|<span data-ttu-id="910d3-165">true</span><span class="sxs-lookup"><span data-stu-id="910d3-165">true</span></span>|  
|<span data-ttu-id="910d3-166">true</span><span class="sxs-lookup"><span data-stu-id="910d3-166">true</span></span>|<span data-ttu-id="910d3-167">false</span><span class="sxs-lookup"><span data-stu-id="910d3-167">false</span></span>|<span data-ttu-id="910d3-168">false</span><span class="sxs-lookup"><span data-stu-id="910d3-168">false</span></span>|<span data-ttu-id="910d3-169">true</span><span class="sxs-lookup"><span data-stu-id="910d3-169">true</span></span>|  
|<span data-ttu-id="910d3-170">true</span><span class="sxs-lookup"><span data-stu-id="910d3-170">true</span></span>|<span data-ttu-id="910d3-171">wartość null</span><span class="sxs-lookup"><span data-stu-id="910d3-171">null</span></span>|<span data-ttu-id="910d3-172">wartość null</span><span class="sxs-lookup"><span data-stu-id="910d3-172">null</span></span>|<span data-ttu-id="910d3-173">true</span><span class="sxs-lookup"><span data-stu-id="910d3-173">true</span></span>|  
|<span data-ttu-id="910d3-174">false</span><span class="sxs-lookup"><span data-stu-id="910d3-174">false</span></span>|<span data-ttu-id="910d3-175">true</span><span class="sxs-lookup"><span data-stu-id="910d3-175">true</span></span>|<span data-ttu-id="910d3-176">false</span><span class="sxs-lookup"><span data-stu-id="910d3-176">false</span></span>|<span data-ttu-id="910d3-177">true</span><span class="sxs-lookup"><span data-stu-id="910d3-177">true</span></span>|  
|<span data-ttu-id="910d3-178">false</span><span class="sxs-lookup"><span data-stu-id="910d3-178">false</span></span>|<span data-ttu-id="910d3-179">false</span><span class="sxs-lookup"><span data-stu-id="910d3-179">false</span></span>|<span data-ttu-id="910d3-180">false</span><span class="sxs-lookup"><span data-stu-id="910d3-180">false</span></span>|<span data-ttu-id="910d3-181">false</span><span class="sxs-lookup"><span data-stu-id="910d3-181">false</span></span>|  
|<span data-ttu-id="910d3-182">false</span><span class="sxs-lookup"><span data-stu-id="910d3-182">false</span></span>|<span data-ttu-id="910d3-183">wartość null</span><span class="sxs-lookup"><span data-stu-id="910d3-183">null</span></span>|<span data-ttu-id="910d3-184">false</span><span class="sxs-lookup"><span data-stu-id="910d3-184">false</span></span>|<span data-ttu-id="910d3-185">wartość null</span><span class="sxs-lookup"><span data-stu-id="910d3-185">null</span></span>|  
|<span data-ttu-id="910d3-186">wartość null</span><span class="sxs-lookup"><span data-stu-id="910d3-186">null</span></span>|<span data-ttu-id="910d3-187">true</span><span class="sxs-lookup"><span data-stu-id="910d3-187">true</span></span>|<span data-ttu-id="910d3-188">wartość null</span><span class="sxs-lookup"><span data-stu-id="910d3-188">null</span></span>|<span data-ttu-id="910d3-189">true</span><span class="sxs-lookup"><span data-stu-id="910d3-189">true</span></span>|  
|<span data-ttu-id="910d3-190">wartość null</span><span class="sxs-lookup"><span data-stu-id="910d3-190">null</span></span>|<span data-ttu-id="910d3-191">false</span><span class="sxs-lookup"><span data-stu-id="910d3-191">false</span></span>|<span data-ttu-id="910d3-192">false</span><span class="sxs-lookup"><span data-stu-id="910d3-192">false</span></span>|<span data-ttu-id="910d3-193">wartość null</span><span class="sxs-lookup"><span data-stu-id="910d3-193">null</span></span>|  
|<span data-ttu-id="910d3-194">wartość null</span><span class="sxs-lookup"><span data-stu-id="910d3-194">null</span></span>|<span data-ttu-id="910d3-195">wartość null</span><span class="sxs-lookup"><span data-stu-id="910d3-195">null</span></span>|<span data-ttu-id="910d3-196">wartość null</span><span class="sxs-lookup"><span data-stu-id="910d3-196">null</span></span>|<span data-ttu-id="910d3-197">wartość null</span><span class="sxs-lookup"><span data-stu-id="910d3-197">null</span></span>|  

<span data-ttu-id="910d3-198">Zachowanie tych operatorów różni się od typowego zachowania operatora z zerowymi typami wartości.</span><span class="sxs-lookup"><span data-stu-id="910d3-198">The behavior of those operators differs from the typical operator behavior with nullable value types.</span></span> <span data-ttu-id="910d3-199">Zazwyczaj operator, który jest zdefiniowany dla operandów typu wartości, może być również używany z operandami odpowiadającego typu wartości null.</span><span class="sxs-lookup"><span data-stu-id="910d3-199">Typically, an operator which is defined for operands of a value type can be also used with operands of the corresponding nullable value type.</span></span> <span data-ttu-id="910d3-200">Taki operator wytwarza `null`, jeśli którykolwiek z jego operandów jest `null`.</span><span class="sxs-lookup"><span data-stu-id="910d3-200">Such an operator produces `null` if any of its operands is `null`.</span></span> <span data-ttu-id="910d3-201">Jednak operatory `&` i `|` mogą generować wartości inne niż null, nawet jeśli jeden z operandów jest `null`.</span><span class="sxs-lookup"><span data-stu-id="910d3-201">However, the `&` and `|` operators can produce non-null even if one of the operands is `null`.</span></span> <span data-ttu-id="910d3-202">Aby uzyskać więcej informacji o zachowaniu operatora z typami wartości null, zobacz sekcję [operatorów](../../programming-guide/nullable-types/using-nullable-types.md#operators) w artykule [używanie typów wartości dopuszczających wartość null](../../programming-guide/nullable-types/using-nullable-types.md) .</span><span class="sxs-lookup"><span data-stu-id="910d3-202">For more information about the operator behavior with nullable value types, see the [Operators](../../programming-guide/nullable-types/using-nullable-types.md#operators) section of the [Using nullable value types](../../programming-guide/nullable-types/using-nullable-types.md) article.</span></span>

<span data-ttu-id="910d3-203">Można również użyć operatorów `!` i `^` z operandami `bool?`, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="910d3-203">You can also use the `!` and `^` operators with the `bool?` operands, as the following example shows:</span></span>

[!code-csharp-interactive[lifted negation and xor](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#WithNullableBoolean)]

<span data-ttu-id="910d3-204">Warunkowe operatory logiczne `&&` i `||` nie obsługują argumentów operacji `bool?`.</span><span class="sxs-lookup"><span data-stu-id="910d3-204">The conditional logical operators `&&` and `||` don't support the `bool?` operands.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="910d3-205">Przypisanie złożone</span><span class="sxs-lookup"><span data-stu-id="910d3-205">Compound assignment</span></span>

<span data-ttu-id="910d3-206">Dla operatora binarnego `op` wyrażenie złożonego przypisania formularza</span><span class="sxs-lookup"><span data-stu-id="910d3-206">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="910d3-207">jest równoważny</span><span class="sxs-lookup"><span data-stu-id="910d3-207">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="910d3-208">z tą różnicą, że `x` jest obliczana tylko raz.</span><span class="sxs-lookup"><span data-stu-id="910d3-208">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="910d3-209">Operatory `&`, `|` i `^` obsługują przypisanie złożone, co ilustruje poniższy przykład:</span><span class="sxs-lookup"><span data-stu-id="910d3-209">The `&`, `|`, and `^` operators support compound assignment, as the following example shows:</span></span>

[!code-csharp-interactive[compound assignment](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#CompoundAssignment)]

<span data-ttu-id="910d3-210">Warunkowe operatory logiczne `&&` i `||` nie obsługują przypisania złożonego.</span><span class="sxs-lookup"><span data-stu-id="910d3-210">The conditional logical operators `&&` and `||` don't support compound assignment.</span></span>

## <a name="operator-precedence"></a><span data-ttu-id="910d3-211">Pierwszeństwo operatorów</span><span class="sxs-lookup"><span data-stu-id="910d3-211">Operator precedence</span></span>

<span data-ttu-id="910d3-212">Poniższa lista porządkuje operatory logiczne rozpoczynając od najwyższego priorytetu do najniższego:</span><span class="sxs-lookup"><span data-stu-id="910d3-212">The following list orders logical operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="910d3-213">Operator logiczny negacji `!`</span><span class="sxs-lookup"><span data-stu-id="910d3-213">Logical negation operator `!`</span></span>
- <span data-ttu-id="910d3-214">Operatory logiczne i `&`</span><span class="sxs-lookup"><span data-stu-id="910d3-214">Logical AND operator `&`</span></span>
- <span data-ttu-id="910d3-215">Operator wyłączny logicznego OR `^`</span><span class="sxs-lookup"><span data-stu-id="910d3-215">Logical exclusive OR operator `^`</span></span>
- <span data-ttu-id="910d3-216">@No__t operatora logicznego OR — 0</span><span class="sxs-lookup"><span data-stu-id="910d3-216">Logical OR operator `|`</span></span>
- <span data-ttu-id="910d3-217">Warunkowe operatory logiczne i `&&`</span><span class="sxs-lookup"><span data-stu-id="910d3-217">Conditional logical AND operator `&&`</span></span>
- <span data-ttu-id="910d3-218">Warunkowe operatory logiczne OR `||`</span><span class="sxs-lookup"><span data-stu-id="910d3-218">Conditional logical OR operator `||`</span></span>

<span data-ttu-id="910d3-219">Użyj nawiasów, `()`, aby zmienić kolejność oceny nałożona przez pierwszeństwo operatorów:</span><span class="sxs-lookup"><span data-stu-id="910d3-219">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence:</span></span>

[!code-csharp-interactive[operator precedence](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Precedence)]

<span data-ttu-id="910d3-220">Aby uzyskać pełną listę C# operatorów uporządkowanych według poziomu pierwszeństwa, zobacz [ C# operatory](index.md).</span><span class="sxs-lookup"><span data-stu-id="910d3-220">For the complete list of C# operators ordered by precedence level, see [C# operators](index.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="910d3-221">Przeciążanie operatora</span><span class="sxs-lookup"><span data-stu-id="910d3-221">Operator overloadability</span></span>

<span data-ttu-id="910d3-222">Typ zdefiniowany przez użytkownika może [przeciążać](operator-overloading.md) operatory `!`, `&`, `|` i `^`.</span><span class="sxs-lookup"><span data-stu-id="910d3-222">A user-defined type can [overload](operator-overloading.md) the `!`, `&`, `|`, and `^` operators.</span></span> <span data-ttu-id="910d3-223">Gdy operator binarny jest przeciążony, odpowiadający mu operator przypisania złożonego jest również niejawnie przeciążony.</span><span class="sxs-lookup"><span data-stu-id="910d3-223">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="910d3-224">Typ zdefiniowany przez użytkownika nie może jawnie przeciążać złożonego operatora przypisania.</span><span class="sxs-lookup"><span data-stu-id="910d3-224">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

<span data-ttu-id="910d3-225">Typ zdefiniowany przez użytkownika nie może przeciążać warunkowych operatorów logicznych `&&` i `||`.</span><span class="sxs-lookup"><span data-stu-id="910d3-225">A user-defined type cannot overload the conditional logical operators `&&` and `||`.</span></span> <span data-ttu-id="910d3-226">Jednakże, jeśli typ zdefiniowany przez użytkownika przeciążuje [Operatory prawdy i FAŁSZ](true-false-operators.md) oraz operator `&` lub `|` w określony sposób, można również ocenić operacje `&&` lub `||` dla operandów tego typu.</span><span class="sxs-lookup"><span data-stu-id="910d3-226">However, if a user-defined type overloads the [true and false operators](true-false-operators.md) and the `&` or `|` operator in a certain way, the `&&` or `||` operation, respectively, can be evaluated for the operands of that type.</span></span> <span data-ttu-id="910d3-227">Aby uzyskać więcej informacji, zapoznaj się z sekcją [Operatory logiczne warunkowe](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) w [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="910d3-227">For more information, see the [User-defined conditional logical operators](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="910d3-228">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="910d3-228">C# language specification</span></span>

<span data-ttu-id="910d3-229">Aby uzyskać więcej informacji, zobacz następujące sekcje [ C# specyfikacji języka](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="910d3-229">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="910d3-230">Operator logiczny negacji</span><span class="sxs-lookup"><span data-stu-id="910d3-230">Logical negation operator</span></span>](~/_csharplang/spec/expressions.md#logical-negation-operator)
- [<span data-ttu-id="910d3-231">Operatory logiczne</span><span class="sxs-lookup"><span data-stu-id="910d3-231">Logical operators</span></span>](~/_csharplang/spec/expressions.md#logical-operators)
- [<span data-ttu-id="910d3-232">Warunkowe operatory logiczne</span><span class="sxs-lookup"><span data-stu-id="910d3-232">Conditional logical operators</span></span>](~/_csharplang/spec/expressions.md#conditional-logical-operators)
- [<span data-ttu-id="910d3-233">Przypisanie złożone</span><span class="sxs-lookup"><span data-stu-id="910d3-233">Compound assignment</span></span>](~/_csharplang/spec/expressions.md#compound-assignment)

## <a name="see-also"></a><span data-ttu-id="910d3-234">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="910d3-234">See also</span></span>

- [<span data-ttu-id="910d3-235">C#odwoła</span><span class="sxs-lookup"><span data-stu-id="910d3-235">C# reference</span></span>](../index.md)
- [<span data-ttu-id="910d3-236">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="910d3-236">C# operators</span></span>](index.md)
- [<span data-ttu-id="910d3-237">Operatory bitowe i przesunięcia</span><span class="sxs-lookup"><span data-stu-id="910d3-237">Bitwise and shift operators</span></span>](bitwise-and-shift-operators.md)
