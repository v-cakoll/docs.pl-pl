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
ms.openlocfilehash: d8fe68fc04300b65bea9b66a6dc6c20e3c69abf4
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/03/2020
ms.locfileid: "78239446"
---
# <a name="boolean-logical-operators-c-reference"></a><span data-ttu-id="66b5f-103">Logiczna operatory logiczne (C# odwołanie)</span><span class="sxs-lookup"><span data-stu-id="66b5f-103">Boolean logical operators (C# reference)</span></span>

<span data-ttu-id="66b5f-104">Następujące operatory wykonują operacje logiczne z argumentami operacji [bool](../builtin-types/bool.md) :</span><span class="sxs-lookup"><span data-stu-id="66b5f-104">The following operators perform logical operations with [bool](../builtin-types/bool.md) operands:</span></span>

- <span data-ttu-id="66b5f-105">Operator jednoargumentowy [`!` (logiczne Negacja)](#logical-negation-operator-) .</span><span class="sxs-lookup"><span data-stu-id="66b5f-105">Unary [`!` (logical negation)](#logical-negation-operator-) operator.</span></span>
- <span data-ttu-id="66b5f-106">Binarne [`&` (logiczne i)](#logical-and-operator-), [`|` (logiczne lub)](#logical-or-operator-)i [`^` (logiczne wyłącznych lub)](#logical-exclusive-or-operator-) .</span><span class="sxs-lookup"><span data-stu-id="66b5f-106">Binary [`&` (logical AND)](#logical-and-operator-), [`|` (logical OR)](#logical-or-operator-), and [`^` (logical exclusive OR)](#logical-exclusive-or-operator-) operators.</span></span> <span data-ttu-id="66b5f-107">Te operatory zawsze obliczają oba operandy.</span><span class="sxs-lookup"><span data-stu-id="66b5f-107">Those operators always evaluate both operands.</span></span>
- <span data-ttu-id="66b5f-108">Binarne [`&&` (warunkowe logiczne i)](#conditional-logical-and-operator-) i [`||` (warunkowe operatory logiczne or)](#conditional-logical-or-operator-) .</span><span class="sxs-lookup"><span data-stu-id="66b5f-108">Binary [`&&` (conditional logical AND)](#conditional-logical-and-operator-) and [`||` (conditional logical OR)](#conditional-logical-or-operator-) operators.</span></span> <span data-ttu-id="66b5f-109">Te operatory obliczają operand z prawej strony tylko wtedy, gdy jest to konieczne.</span><span class="sxs-lookup"><span data-stu-id="66b5f-109">Those operators evaluate the right-hand operand only if it's necessary.</span></span>

<span data-ttu-id="66b5f-110">W przypadku operandów [całkowitych typów liczbowych](../builtin-types/integral-numeric-types.md)operatory `&`, `|`i `^` wykonują bitowe operacje logiczne.</span><span class="sxs-lookup"><span data-stu-id="66b5f-110">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `&`, `|`, and `^` operators perform bitwise logical operations.</span></span> <span data-ttu-id="66b5f-111">Aby uzyskać więcej informacji, zobacz [Operatory bitowe i przesunięcia](bitwise-and-shift-operators.md).</span><span class="sxs-lookup"><span data-stu-id="66b5f-111">For more information, see [Bitwise and shift operators](bitwise-and-shift-operators.md).</span></span>

## <a name="logical-negation-operator-"></a><span data-ttu-id="66b5f-112">Operator logiczny negacji</span><span class="sxs-lookup"><span data-stu-id="66b5f-112">Logical negation operator !</span></span>

<span data-ttu-id="66b5f-113">Operator jednoargumentowy `!` oblicza logiczne Negacja operandu.</span><span class="sxs-lookup"><span data-stu-id="66b5f-113">The unary prefix `!` operator computes logical negation of its operand.</span></span> <span data-ttu-id="66b5f-114">Oznacza to, że generuje `true`, jeśli operand zostanie obliczony do `false`i `false`, jeśli operand zostanie obliczony do `true`:</span><span class="sxs-lookup"><span data-stu-id="66b5f-114">That is, it produces `true`, if the operand evaluates to `false`, and `false`, if the operand evaluates to `true`:</span></span>

[!code-csharp-interactive[logical negation](~/samples/snippets/csharp/language-reference/operators/BooleanLogicalOperators.cs#Negation)]

<span data-ttu-id="66b5f-115">Począwszy od C# 8,0, operator jednoargumentowy `!` jest operatorem o [wartości null-łagodniejszej](null-forgiving.md).</span><span class="sxs-lookup"><span data-stu-id="66b5f-115">Beginning with C# 8.0, the unary postfix `!` operator is the [null-forgiving operator](null-forgiving.md).</span></span>

## <a name="logical-and-operator-"></a><span data-ttu-id="66b5f-116">Operatory logiczne i &amp;</span><span class="sxs-lookup"><span data-stu-id="66b5f-116">Logical AND operator &amp;</span></span>

<span data-ttu-id="66b5f-117">Operator `&` oblicza wartość logiczną i jej operandów.</span><span class="sxs-lookup"><span data-stu-id="66b5f-117">The `&` operator computes the logical AND of its operands.</span></span> <span data-ttu-id="66b5f-118">Wynik `x & y` jest `true`, jeśli oba `x` i `y` są oceniane do `true`.</span><span class="sxs-lookup"><span data-stu-id="66b5f-118">The result of `x & y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="66b5f-119">W przeciwnym razie wynik jest `false`.</span><span class="sxs-lookup"><span data-stu-id="66b5f-119">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="66b5f-120">Operator `&` oblicza oba operandy, nawet jeśli argument operacji po lewej stronie szacuje się na `false`, dzięki czemu wynik operacji jest `false` niezależnie od wartości operandu po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="66b5f-120">The `&` operator evaluates both operands even if the left-hand operand evaluates to `false`, so that the operation result is `false` regardless of the value of the right-hand operand.</span></span>

<span data-ttu-id="66b5f-121">W poniższym przykładzie argument operacji z prawej strony operatora `&` jest wywołaniem metody, które jest wykonywane niezależnie od wartości operandu po lewej stronie:</span><span class="sxs-lookup"><span data-stu-id="66b5f-121">In the following example, the right-hand operand of the `&` operator is a method call, which is performed regardless of the value of the left-hand operand:</span></span>

[!code-csharp-interactive[logical AND](~/samples/snippets/csharp/language-reference/operators/BooleanLogicalOperators.cs#And)]

<span data-ttu-id="66b5f-122">[Warunkowe operatory logiczne i](#conditional-logical-and-operator-) `&&` oblicza również wartości logiczne i jego operandy, ale nie oblicza wartości operandu po prawej stronie, jeśli argument operacji po lewej stronie ma wartość `false`.</span><span class="sxs-lookup"><span data-stu-id="66b5f-122">The [conditional logical AND operator](#conditional-logical-and-operator-) `&&` also computes the logical AND of its operands, but doesn't evaluate the right-hand operand if the left-hand operand evaluates to `false`.</span></span>

<span data-ttu-id="66b5f-123">Dla operandów [całkowitych typów liczbowych](../builtin-types/integral-numeric-types.md)operator `&` oblicza koniunkcję [bitową i](bitwise-and-shift-operators.md#logical-and-operator-) jej operandy.</span><span class="sxs-lookup"><span data-stu-id="66b5f-123">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `&` operator computes the [bitwise logical AND](bitwise-and-shift-operators.md#logical-and-operator-) of its operands.</span></span> <span data-ttu-id="66b5f-124">Jednoargumentowy operator `&` jest [operatorem address-of](pointer-related-operators.md#address-of-operator-).</span><span class="sxs-lookup"><span data-stu-id="66b5f-124">The unary `&` operator is the [address-of operator](pointer-related-operators.md#address-of-operator-).</span></span>

## <a name="logical-exclusive-or-operator-"></a><span data-ttu-id="66b5f-125">Operator wyłączny logicznego OR ^</span><span class="sxs-lookup"><span data-stu-id="66b5f-125">Logical exclusive OR operator ^</span></span>

<span data-ttu-id="66b5f-126">Operator `^` oblicza wartość logiczną na wyłączność lub, znaną również jako logiczna XOR, jego operandów.</span><span class="sxs-lookup"><span data-stu-id="66b5f-126">The `^` operator computes the logical exclusive OR, also known as the logical XOR, of its operands.</span></span> <span data-ttu-id="66b5f-127">Wynik `x ^ y` jest `true`, jeśli `x` oblicza `true` i `y` oblicza `false`, lub `x` oblicza `false`, a `y` oblicza `true`.</span><span class="sxs-lookup"><span data-stu-id="66b5f-127">The result of `x ^ y` is `true` if `x` evaluates to `true` and `y` evaluates to `false`, or `x` evaluates to `false` and `y` evaluates to `true`.</span></span> <span data-ttu-id="66b5f-128">W przeciwnym razie wynik jest `false`.</span><span class="sxs-lookup"><span data-stu-id="66b5f-128">Otherwise, the result is `false`.</span></span> <span data-ttu-id="66b5f-129">Oznacza to, że dla operandów `bool` operator `^` oblicza ten sam wynik, co `!=`[operatora nierówności](equality-operators.md#inequality-operator-) .</span><span class="sxs-lookup"><span data-stu-id="66b5f-129">That is, for the `bool` operands, the `^` operator computes the same result as the [inequality operator](equality-operators.md#inequality-operator-) `!=`.</span></span>

[!code-csharp-interactive[logical exclusive OR](~/samples/snippets/csharp/language-reference/operators/BooleanLogicalOperators.cs#Xor)]

<span data-ttu-id="66b5f-130">W przypadku operandów [całkowitych typów liczbowych](../builtin-types/integral-numeric-types.md)operator `^` oblicza [bitowe logiczne wyłącznych lub](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) jego operandów.</span><span class="sxs-lookup"><span data-stu-id="66b5f-130">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `^` operator computes the [bitwise logical exclusive OR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) of its operands.</span></span>

## <a name="logical-or-operator-"></a><span data-ttu-id="66b5f-131">Operator logiczny OR |</span><span class="sxs-lookup"><span data-stu-id="66b5f-131">Logical OR operator |</span></span>

<span data-ttu-id="66b5f-132">Operator `|` oblicza wartość logiczną lub argumentów operacji.</span><span class="sxs-lookup"><span data-stu-id="66b5f-132">The `|` operator computes the logical OR of its operands.</span></span> <span data-ttu-id="66b5f-133">Wynik `x | y` jest `true`, jeśli `x` lub `y` szacuje się `true`.</span><span class="sxs-lookup"><span data-stu-id="66b5f-133">The result of `x | y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="66b5f-134">W przeciwnym razie wynik jest `false`.</span><span class="sxs-lookup"><span data-stu-id="66b5f-134">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="66b5f-135">Operator `|` oblicza oba operandy, nawet jeśli argument operacji po lewej stronie szacuje się na `true`, dzięki czemu wynik operacji jest `true` niezależnie od wartości operandu po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="66b5f-135">The `|` operator evaluates both operands even if the left-hand operand evaluates to `true`, so that the operation result is `true` regardless of the value of the right-hand operand.</span></span>

<span data-ttu-id="66b5f-136">W poniższym przykładzie argument operacji z prawej strony operatora `|` jest wywołaniem metody, które jest wykonywane niezależnie od wartości operandu po lewej stronie:</span><span class="sxs-lookup"><span data-stu-id="66b5f-136">In the following example, the right-hand operand of the `|` operator is a method call, which is performed regardless of the value of the left-hand operand:</span></span>

[!code-csharp-interactive[logical OR](~/samples/snippets/csharp/language-reference/operators/BooleanLogicalOperators.cs#Or)]

<span data-ttu-id="66b5f-137">[Warunkowy operator logiczny or](#conditional-logical-or-operator-) `||` oblicza również wartość logiczną lub jej operandów, ale nie oblicza wartości operandu po prawej stronie, jeśli argument operacji po lewej stronie szacuje się na `true`.</span><span class="sxs-lookup"><span data-stu-id="66b5f-137">The [conditional logical OR operator](#conditional-logical-or-operator-) `||` also computes the logical OR of its operands, but doesn't evaluate the right-hand operand if the left-hand operand evaluates to `true`.</span></span>

<span data-ttu-id="66b5f-138">Dla operandów [całkowitych typów liczbowych](../builtin-types/integral-numeric-types.md)operator `|` oblicza [bitową wartość logiczną lub](bitwise-and-shift-operators.md#logical-or-operator-) jej operandów.</span><span class="sxs-lookup"><span data-stu-id="66b5f-138">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `|` operator computes the [bitwise logical OR](bitwise-and-shift-operators.md#logical-or-operator-) of its operands.</span></span>

## <a name="conditional-logical-and-operator-"></a><span data-ttu-id="66b5f-139">Warunkowe &amp;logiczne i operatory &amp;</span><span class="sxs-lookup"><span data-stu-id="66b5f-139">Conditional logical AND operator &amp;&amp;</span></span>

<span data-ttu-id="66b5f-140">Warunkowe operatory logiczne i `&&`, znane także jako operator logiczny "krótki-obwód", oblicza wartość logiczną i argumentów operacji.</span><span class="sxs-lookup"><span data-stu-id="66b5f-140">The conditional logical AND operator `&&`, also known as the "short-circuiting" logical AND operator, computes the logical AND of its operands.</span></span> <span data-ttu-id="66b5f-141">Wynik `x && y` jest `true`, jeśli oba `x` i `y` są oceniane do `true`.</span><span class="sxs-lookup"><span data-stu-id="66b5f-141">The result of `x && y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="66b5f-142">W przeciwnym razie wynik jest `false`.</span><span class="sxs-lookup"><span data-stu-id="66b5f-142">Otherwise, the result is `false`.</span></span> <span data-ttu-id="66b5f-143">Jeśli `x` oblicza `false`, `y` nie jest oceniane.</span><span class="sxs-lookup"><span data-stu-id="66b5f-143">If `x` evaluates to `false`, `y` is not evaluated.</span></span>

<span data-ttu-id="66b5f-144">W poniższym przykładzie argument operacji po prawej stronie operatora `&&` jest wywołaniem metody, które nie jest wykonywane, jeśli argument operacji po lewej stronie szacuje się na `false`:</span><span class="sxs-lookup"><span data-stu-id="66b5f-144">In the following example, the right-hand operand of the `&&` operator is a method call, which isn't performed if the left-hand operand evaluates to `false`:</span></span>

[!code-csharp-interactive[conditional logical AND](~/samples/snippets/csharp/language-reference/operators/BooleanLogicalOperators.cs#ConditionalAnd)]

<span data-ttu-id="66b5f-145">[Operator logiczny i](#logical-and-operator-) `&` oblicza również wartości logiczne i jego operandy, ale zawsze oblicza oba operandy.</span><span class="sxs-lookup"><span data-stu-id="66b5f-145">The [logical AND operator](#logical-and-operator-) `&` also computes the logical AND of its operands, but always evaluates both operands.</span></span>

## <a name="conditional-logical-or-operator-"></a><span data-ttu-id="66b5f-146">Warunkowe logiczne OR operator | |</span><span class="sxs-lookup"><span data-stu-id="66b5f-146">Conditional logical OR operator ||</span></span>

<span data-ttu-id="66b5f-147">Warunkowe operatory logiczne OR `||`, znane także jako operator logiczny OR "krótkie-obwód", oblicza wartość logiczną lub argumentów operacji.</span><span class="sxs-lookup"><span data-stu-id="66b5f-147">The conditional logical OR operator `||`, also known as the "short-circuiting" logical OR operator, computes the logical OR of its operands.</span></span> <span data-ttu-id="66b5f-148">Wynik `x || y` jest `true`, jeśli `x` lub `y` szacuje się `true`.</span><span class="sxs-lookup"><span data-stu-id="66b5f-148">The result of `x || y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="66b5f-149">W przeciwnym razie wynik jest `false`.</span><span class="sxs-lookup"><span data-stu-id="66b5f-149">Otherwise, the result is `false`.</span></span> <span data-ttu-id="66b5f-150">Jeśli `x` oblicza `true`, `y` nie jest oceniane.</span><span class="sxs-lookup"><span data-stu-id="66b5f-150">If `x` evaluates to `true`, `y` is not evaluated.</span></span>

<span data-ttu-id="66b5f-151">W poniższym przykładzie argument operacji po prawej stronie operatora `||` jest wywołaniem metody, które nie jest wykonywane, jeśli argument operacji po lewej stronie szacuje się na `true`:</span><span class="sxs-lookup"><span data-stu-id="66b5f-151">In the following example, the right-hand operand of the `||` operator is a method call, which isn't performed if the left-hand operand evaluates to `true`:</span></span>

[!code-csharp-interactive[conditional logical OR](~/samples/snippets/csharp/language-reference/operators/BooleanLogicalOperators.cs#ConditionalOr)]

<span data-ttu-id="66b5f-152">[Operator logiczny or](#logical-or-operator-) `|` oblicza również wartości logiczne lub jego operandy, ale zawsze oblicza oba operandy.</span><span class="sxs-lookup"><span data-stu-id="66b5f-152">The [logical OR operator](#logical-or-operator-) `|` also computes the logical OR of its operands, but always evaluates both operands.</span></span>

## <a name="nullable-boolean-logical-operators"></a><span data-ttu-id="66b5f-153">Logiczne operatory wartości null</span><span class="sxs-lookup"><span data-stu-id="66b5f-153">Nullable Boolean logical operators</span></span>

<span data-ttu-id="66b5f-154">Dla argumentów operacji `bool?` operatory `&` i `|` obsługują logikę z trzema wartościami.</span><span class="sxs-lookup"><span data-stu-id="66b5f-154">For `bool?` operands, the `&` and `|` operators support the three-valued logic.</span></span> <span data-ttu-id="66b5f-155">Semantyka tych operatorów jest definiowana przez następującą tabelę:</span><span class="sxs-lookup"><span data-stu-id="66b5f-155">The semantics of these operators is defined by the following table:</span></span>  
  
|<span data-ttu-id="66b5f-156">x</span><span class="sxs-lookup"><span data-stu-id="66b5f-156">x</span></span>|<span data-ttu-id="66b5f-157">{1&gt;y&lt;1}</span><span class="sxs-lookup"><span data-stu-id="66b5f-157">y</span></span>|<span data-ttu-id="66b5f-158">x & y</span><span class="sxs-lookup"><span data-stu-id="66b5f-158">x&y</span></span>|<span data-ttu-id="66b5f-159">x&#124;y</span><span class="sxs-lookup"><span data-stu-id="66b5f-159">x&#124;y</span></span>|  
|----|----|----|----|  
|<span data-ttu-id="66b5f-160">true</span><span class="sxs-lookup"><span data-stu-id="66b5f-160">true</span></span>|<span data-ttu-id="66b5f-161">true</span><span class="sxs-lookup"><span data-stu-id="66b5f-161">true</span></span>|<span data-ttu-id="66b5f-162">true</span><span class="sxs-lookup"><span data-stu-id="66b5f-162">true</span></span>|<span data-ttu-id="66b5f-163">true</span><span class="sxs-lookup"><span data-stu-id="66b5f-163">true</span></span>|  
|<span data-ttu-id="66b5f-164">true</span><span class="sxs-lookup"><span data-stu-id="66b5f-164">true</span></span>|<span data-ttu-id="66b5f-165">false</span><span class="sxs-lookup"><span data-stu-id="66b5f-165">false</span></span>|<span data-ttu-id="66b5f-166">false</span><span class="sxs-lookup"><span data-stu-id="66b5f-166">false</span></span>|<span data-ttu-id="66b5f-167">true</span><span class="sxs-lookup"><span data-stu-id="66b5f-167">true</span></span>|  
|<span data-ttu-id="66b5f-168">true</span><span class="sxs-lookup"><span data-stu-id="66b5f-168">true</span></span>|<span data-ttu-id="66b5f-169">null</span><span class="sxs-lookup"><span data-stu-id="66b5f-169">null</span></span>|<span data-ttu-id="66b5f-170">null</span><span class="sxs-lookup"><span data-stu-id="66b5f-170">null</span></span>|<span data-ttu-id="66b5f-171">true</span><span class="sxs-lookup"><span data-stu-id="66b5f-171">true</span></span>|  
|<span data-ttu-id="66b5f-172">false</span><span class="sxs-lookup"><span data-stu-id="66b5f-172">false</span></span>|<span data-ttu-id="66b5f-173">true</span><span class="sxs-lookup"><span data-stu-id="66b5f-173">true</span></span>|<span data-ttu-id="66b5f-174">false</span><span class="sxs-lookup"><span data-stu-id="66b5f-174">false</span></span>|<span data-ttu-id="66b5f-175">true</span><span class="sxs-lookup"><span data-stu-id="66b5f-175">true</span></span>|  
|<span data-ttu-id="66b5f-176">false</span><span class="sxs-lookup"><span data-stu-id="66b5f-176">false</span></span>|<span data-ttu-id="66b5f-177">false</span><span class="sxs-lookup"><span data-stu-id="66b5f-177">false</span></span>|<span data-ttu-id="66b5f-178">false</span><span class="sxs-lookup"><span data-stu-id="66b5f-178">false</span></span>|<span data-ttu-id="66b5f-179">false</span><span class="sxs-lookup"><span data-stu-id="66b5f-179">false</span></span>|  
|<span data-ttu-id="66b5f-180">false</span><span class="sxs-lookup"><span data-stu-id="66b5f-180">false</span></span>|<span data-ttu-id="66b5f-181">null</span><span class="sxs-lookup"><span data-stu-id="66b5f-181">null</span></span>|<span data-ttu-id="66b5f-182">false</span><span class="sxs-lookup"><span data-stu-id="66b5f-182">false</span></span>|<span data-ttu-id="66b5f-183">null</span><span class="sxs-lookup"><span data-stu-id="66b5f-183">null</span></span>|  
|<span data-ttu-id="66b5f-184">null</span><span class="sxs-lookup"><span data-stu-id="66b5f-184">null</span></span>|<span data-ttu-id="66b5f-185">true</span><span class="sxs-lookup"><span data-stu-id="66b5f-185">true</span></span>|<span data-ttu-id="66b5f-186">null</span><span class="sxs-lookup"><span data-stu-id="66b5f-186">null</span></span>|<span data-ttu-id="66b5f-187">true</span><span class="sxs-lookup"><span data-stu-id="66b5f-187">true</span></span>|  
|<span data-ttu-id="66b5f-188">null</span><span class="sxs-lookup"><span data-stu-id="66b5f-188">null</span></span>|<span data-ttu-id="66b5f-189">false</span><span class="sxs-lookup"><span data-stu-id="66b5f-189">false</span></span>|<span data-ttu-id="66b5f-190">false</span><span class="sxs-lookup"><span data-stu-id="66b5f-190">false</span></span>|<span data-ttu-id="66b5f-191">null</span><span class="sxs-lookup"><span data-stu-id="66b5f-191">null</span></span>|  
|<span data-ttu-id="66b5f-192">null</span><span class="sxs-lookup"><span data-stu-id="66b5f-192">null</span></span>|<span data-ttu-id="66b5f-193">null</span><span class="sxs-lookup"><span data-stu-id="66b5f-193">null</span></span>|<span data-ttu-id="66b5f-194">null</span><span class="sxs-lookup"><span data-stu-id="66b5f-194">null</span></span>|<span data-ttu-id="66b5f-195">null</span><span class="sxs-lookup"><span data-stu-id="66b5f-195">null</span></span>|  

<span data-ttu-id="66b5f-196">Zachowanie tych operatorów różni się od typowego zachowania operatora z zerowymi typami wartości.</span><span class="sxs-lookup"><span data-stu-id="66b5f-196">The behavior of those operators differs from the typical operator behavior with nullable value types.</span></span> <span data-ttu-id="66b5f-197">Zazwyczaj operator, który jest zdefiniowany dla operandów typu wartości, może być również używany z operandami odpowiadającego typu wartości null.</span><span class="sxs-lookup"><span data-stu-id="66b5f-197">Typically, an operator which is defined for operands of a value type can be also used with operands of the corresponding nullable value type.</span></span> <span data-ttu-id="66b5f-198">Taki operator wytwarza `null`, jeśli którykolwiek z jego operandów zwróci `null`.</span><span class="sxs-lookup"><span data-stu-id="66b5f-198">Such an operator produces `null` if any of its operands evaluates to `null`.</span></span> <span data-ttu-id="66b5f-199">Jednak operatory `&` i `|` mogą generować wartości inne niż null, nawet jeśli jeden z operandów szacuje się w `null`.</span><span class="sxs-lookup"><span data-stu-id="66b5f-199">However, the `&` and `|` operators can produce non-null even if one of the operands evaluates to `null`.</span></span> <span data-ttu-id="66b5f-200">Aby uzyskać więcej informacji o zachowaniu operatora z typem wartości null, zobacz sekcję [zniesione operatory](../builtin-types/nullable-value-types.md#lifted-operators) w artykule [typy wartości null](../builtin-types/nullable-value-types.md) .</span><span class="sxs-lookup"><span data-stu-id="66b5f-200">For more information about the operator behavior with nullable value types, see the [Lifted operators](../builtin-types/nullable-value-types.md#lifted-operators) section of the [Nullable value types](../builtin-types/nullable-value-types.md) article.</span></span>

<span data-ttu-id="66b5f-201">Można również użyć operatorów `!` i `^` z argumentami operacji `bool?`, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="66b5f-201">You can also use the `!` and `^` operators with `bool?` operands, as the following example shows:</span></span>

[!code-csharp-interactive[lifted negation and xor](~/samples/snippets/csharp/language-reference/operators/BooleanLogicalOperators.cs#WithNullableBoolean)]

<span data-ttu-id="66b5f-202">Warunkowe operatory logiczne `&&` i `||` nie obsługują argumentów operacji `bool?`.</span><span class="sxs-lookup"><span data-stu-id="66b5f-202">The conditional logical operators `&&` and `||` don't support `bool?` operands.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="66b5f-203">Przypisanie złożone</span><span class="sxs-lookup"><span data-stu-id="66b5f-203">Compound assignment</span></span>

<span data-ttu-id="66b5f-204">Dla operatora binarnego `op`wyrażenie złożonego przypisania formularza</span><span class="sxs-lookup"><span data-stu-id="66b5f-204">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="66b5f-205">odpowiada wyrażeniu</span><span class="sxs-lookup"><span data-stu-id="66b5f-205">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="66b5f-206">z tą różnicą, że `x` są oceniane tylko raz.</span><span class="sxs-lookup"><span data-stu-id="66b5f-206">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="66b5f-207">Operatory `&`, `|`i `^` obsługują przypisanie złożone, co ilustruje poniższy przykład:</span><span class="sxs-lookup"><span data-stu-id="66b5f-207">The `&`, `|`, and `^` operators support compound assignment, as the following example shows:</span></span>

[!code-csharp-interactive[compound assignment](~/samples/snippets/csharp/language-reference/operators/BooleanLogicalOperators.cs#CompoundAssignment)]

<span data-ttu-id="66b5f-208">Warunkowe operatory logiczne `&&` i `||` nie obsługują przypisania złożonego.</span><span class="sxs-lookup"><span data-stu-id="66b5f-208">The conditional logical operators `&&` and `||` don't support compound assignment.</span></span>

## <a name="operator-precedence"></a><span data-ttu-id="66b5f-209">Pierwszeństwo operatorów</span><span class="sxs-lookup"><span data-stu-id="66b5f-209">Operator precedence</span></span>

<span data-ttu-id="66b5f-210">Poniższa lista porządkuje operatory logiczne rozpoczynając od najwyższego priorytetu do najniższego:</span><span class="sxs-lookup"><span data-stu-id="66b5f-210">The following list orders logical operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="66b5f-211">`!` operatora negacji logicznej</span><span class="sxs-lookup"><span data-stu-id="66b5f-211">Logical negation operator `!`</span></span>
- <span data-ttu-id="66b5f-212">Operatory logiczne i `&`</span><span class="sxs-lookup"><span data-stu-id="66b5f-212">Logical AND operator `&`</span></span>
- <span data-ttu-id="66b5f-213">`^` operatora logicznego wyłącznego OR</span><span class="sxs-lookup"><span data-stu-id="66b5f-213">Logical exclusive OR operator `^`</span></span>
- <span data-ttu-id="66b5f-214">`|` operatora logicznego OR</span><span class="sxs-lookup"><span data-stu-id="66b5f-214">Logical OR operator `|`</span></span>
- <span data-ttu-id="66b5f-215">Warunkowe operatory logiczne i `&&`</span><span class="sxs-lookup"><span data-stu-id="66b5f-215">Conditional logical AND operator `&&`</span></span>
- <span data-ttu-id="66b5f-216">Warunkowe `||` operatora logicznego OR</span><span class="sxs-lookup"><span data-stu-id="66b5f-216">Conditional logical OR operator `||`</span></span>

<span data-ttu-id="66b5f-217">Użyj nawiasów `()`, aby zmienić kolejność oceny nałożona przez pierwszeństwo operatorów:</span><span class="sxs-lookup"><span data-stu-id="66b5f-217">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence:</span></span>

[!code-csharp-interactive[operator precedence](~/samples/snippets/csharp/language-reference/operators/BooleanLogicalOperators.cs#Precedence)]

<span data-ttu-id="66b5f-218">Aby uzyskać pełną listę C# operatorów uporządkowanych według poziomu pierwszeństwa, zobacz sekcję [pierwszeństwo](index.md#operator-precedence) operatorów w artykule [ C# Operators](index.md) .</span><span class="sxs-lookup"><span data-stu-id="66b5f-218">For the complete list of C# operators ordered by precedence level, see the [Operator precedence](index.md#operator-precedence) section of the [C# operators](index.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="66b5f-219">Przeciążanie operatora</span><span class="sxs-lookup"><span data-stu-id="66b5f-219">Operator overloadability</span></span>

<span data-ttu-id="66b5f-220">Typ zdefiniowany przez użytkownika może [przeciążać](operator-overloading.md) operatory `!`, `&`, `|`i `^`.</span><span class="sxs-lookup"><span data-stu-id="66b5f-220">A user-defined type can [overload](operator-overloading.md) the `!`, `&`, `|`, and `^` operators.</span></span> <span data-ttu-id="66b5f-221">Gdy operator binarny jest przeciążony, odpowiadający mu operator przypisania złożonego jest również niejawnie przeciążony.</span><span class="sxs-lookup"><span data-stu-id="66b5f-221">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="66b5f-222">Typ zdefiniowany przez użytkownika nie może jawnie przeciążać złożonego operatora przypisania.</span><span class="sxs-lookup"><span data-stu-id="66b5f-222">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

<span data-ttu-id="66b5f-223">Typ zdefiniowany przez użytkownika nie może przeciążać warunkowych operatorów logicznych `&&` i `||`.</span><span class="sxs-lookup"><span data-stu-id="66b5f-223">A user-defined type cannot overload the conditional logical operators `&&` and `||`.</span></span> <span data-ttu-id="66b5f-224">Jednakże, jeśli typ zdefiniowany przez użytkownika przeciążuje [Operatory true i false](true-false-operators.md) oraz operator `&` lub `|` w określony sposób, `&&` lub `||` operacji, można je obliczyć odpowiednio dla operandów tego typu.</span><span class="sxs-lookup"><span data-stu-id="66b5f-224">However, if a user-defined type overloads the [true and false operators](true-false-operators.md) and the `&` or `|` operator in a certain way, the `&&` or `||` operation, respectively, can be evaluated for the operands of that type.</span></span> <span data-ttu-id="66b5f-225">Aby uzyskać więcej informacji, zapoznaj się z sekcją [Operatory logiczne warunkowe](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) w [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="66b5f-225">For more information, see the [User-defined conditional logical operators](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="66b5f-226">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="66b5f-226">C# language specification</span></span>

<span data-ttu-id="66b5f-227">Aby uzyskać więcej informacji, zobacz następujące sekcje [ C# specyfikacji języka](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="66b5f-227">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="66b5f-228">Operator logiczny negacji</span><span class="sxs-lookup"><span data-stu-id="66b5f-228">Logical negation operator</span></span>](~/_csharplang/spec/expressions.md#logical-negation-operator)
- [<span data-ttu-id="66b5f-229">Operatory logiczne</span><span class="sxs-lookup"><span data-stu-id="66b5f-229">Logical operators</span></span>](~/_csharplang/spec/expressions.md#logical-operators)
- [<span data-ttu-id="66b5f-230">Warunkowe operatory logiczne</span><span class="sxs-lookup"><span data-stu-id="66b5f-230">Conditional logical operators</span></span>](~/_csharplang/spec/expressions.md#conditional-logical-operators)
- [<span data-ttu-id="66b5f-231">Przypisanie złożone</span><span class="sxs-lookup"><span data-stu-id="66b5f-231">Compound assignment</span></span>](~/_csharplang/spec/expressions.md#compound-assignment)

## <a name="see-also"></a><span data-ttu-id="66b5f-232">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="66b5f-232">See also</span></span>

- [<span data-ttu-id="66b5f-233">C#odwoła</span><span class="sxs-lookup"><span data-stu-id="66b5f-233">C# reference</span></span>](../index.md)
- [<span data-ttu-id="66b5f-234">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="66b5f-234">C# operators</span></span>](index.md)
- [<span data-ttu-id="66b5f-235">Operatory bitowe i przesunięcia</span><span class="sxs-lookup"><span data-stu-id="66b5f-235">Bitwise and shift operators</span></span>](bitwise-and-shift-operators.md)
