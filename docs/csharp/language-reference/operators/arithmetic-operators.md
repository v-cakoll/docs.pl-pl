---
title: Operatory arytmetyczne — odwołanie w C#
description: Dowiedz się więcej na temat operatorów języka C#, które wykonują operacje mnożenia, dzielenia, reszty, dodawania i odejmowania z typami liczbowymi.
ms.date: 05/11/2020
author: pkulikov
f1_keywords:
- ++_CSharpKeyword
- --_CSharpKeyword
- '*_CSharpKeyword'
- /_CSharpKeyword
- '%_CSharpKeyword'
- +_CSharpKeyword
- -_CSharpKeyword
helpviewer_keywords:
- arithmetic operators [C#]
- increment operator [C#]
- ++ operator [C#]
- decrement operator [C#]
- -- operator [C#]
- multiplication operator [C#]
- '* operator [C#]'
- division operator [C#]
- / operator [C#]
- remainder operator [C#]
- '% operator [C#]'
- addition operator [C#]
- + operator [C#]
- subtraction operator [C#]
- '- operator [C#]'
ms.openlocfilehash: d004ab466bc053ed286d85bcbee2766d8a087286
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83207239"
---
# <a name="arithmetic-operators-c-reference"></a><span data-ttu-id="f7351-103">Operatory arytmetyczne (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="f7351-103">Arithmetic operators (C# reference)</span></span>

<span data-ttu-id="f7351-104">Następujące operatory wykonują operacje arytmetyczne z argumentami typu liczbowego:</span><span class="sxs-lookup"><span data-stu-id="f7351-104">The following operators perform arithmetic operations with operands of numeric types:</span></span>

- <span data-ttu-id="f7351-105">Operatory jednoargumentowe [ `++` (przyrostowe)](#increment-operator-), ( [ `--` zmniejszanie](#decrement-operator---)), [ `+` (plus)](#unary-plus-and-minus-operators)i [ `-` (minus)](#unary-plus-and-minus-operators)</span><span class="sxs-lookup"><span data-stu-id="f7351-105">Unary [`++` (increment)](#increment-operator-), [`--` (decrement)](#decrement-operator---), [`+` (plus)](#unary-plus-and-minus-operators), and [`-` (minus)](#unary-plus-and-minus-operators) operators</span></span>
- <span data-ttu-id="f7351-106">Operatory binarne [ `*` (mnożenie)](#multiplication-operator-), [ `/` (dzielenie)](#division-operator-), [ `%` (reszta)](#remainder-operator-), [ `+` (Dodawanie)](#addition-operator-)i [ `-` (Odejmowanie)](#subtraction-operator--)</span><span class="sxs-lookup"><span data-stu-id="f7351-106">Binary [`*` (multiplication)](#multiplication-operator-), [`/` (division)](#division-operator-), [`%` (remainder)](#remainder-operator-), [`+` (addition)](#addition-operator-), and [`-` (subtraction)](#subtraction-operator--) operators</span></span>

<span data-ttu-id="f7351-107">Te operatory są obsługiwane przez wszystkie typy liczbowe [całkowite](../builtin-types/integral-numeric-types.md) i [zmiennoprzecinkowe](../builtin-types/floating-point-numeric-types.md) .</span><span class="sxs-lookup"><span data-stu-id="f7351-107">Those operators are supported by all [integral](../builtin-types/integral-numeric-types.md) and [floating-point](../builtin-types/floating-point-numeric-types.md) numeric types.</span></span>

<span data-ttu-id="f7351-108">W przypadku typów całkowitych operatory te (poza `++` `--` operatorami i) są zdefiniowane dla `int` `uint` typów,, `long` i `ulong` .</span><span class="sxs-lookup"><span data-stu-id="f7351-108">In the case of integral types, those operators (except the `++` and `--` operators) are defined for the `int`, `uint`, `long`, and `ulong` types.</span></span> <span data-ttu-id="f7351-109">Gdy operandy są innymi typami całkowitymi ( `sbyte` , `byte` , `short` , `ushort` lub `char` ), ich wartości są konwertowane na `int` Typ, który jest również typem wyniku operacji.</span><span class="sxs-lookup"><span data-stu-id="f7351-109">When operands are of other integral types (`sbyte`, `byte`, `short`, `ushort`, or `char`), their values are converted to the `int` type, which is also the result type of an operation.</span></span> <span data-ttu-id="f7351-110">Gdy operandy są różnych typów całkowitych lub zmiennoprzecinkowych, ich wartości są konwertowane na najbliższy typ zawierający, jeśli taki typ istnieje.</span><span class="sxs-lookup"><span data-stu-id="f7351-110">When operands are of different integral or floating-point types, their values are converted to the closest containing type, if such a type exists.</span></span> <span data-ttu-id="f7351-111">Aby uzyskać więcej informacji, zobacz sekcję [promocje liczbowe](~/_csharplang/spec/expressions.md#numeric-promotions) w [specyfikacji języka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="f7351-111">For more information, see the [Numeric promotions](~/_csharplang/spec/expressions.md#numeric-promotions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span> <span data-ttu-id="f7351-112">`++`Operatory i `--` są zdefiniowane dla wszystkich typów liczb całkowitych i zmiennoprzecinkowych oraz typu [char](../builtin-types/char.md) .</span><span class="sxs-lookup"><span data-stu-id="f7351-112">The `++` and `--` operators are defined for all integral and floating-point numeric types and the [char](../builtin-types/char.md) type.</span></span>

## <a name="increment-operator-"></a><span data-ttu-id="f7351-113">Increment — operator + +</span><span class="sxs-lookup"><span data-stu-id="f7351-113">Increment operator ++</span></span>

<span data-ttu-id="f7351-114">Jednoargumentowy operator przyrostu `++` zwiększa jego operand o 1.</span><span class="sxs-lookup"><span data-stu-id="f7351-114">The unary increment operator `++` increments its operand by 1.</span></span> <span data-ttu-id="f7351-115">Operand musi być zmienną, dostępem do [Właściwości](../../programming-guide/classes-and-structs/properties.md) lub dostępem [indeksatora](../../programming-guide/indexers/index.md) .</span><span class="sxs-lookup"><span data-stu-id="f7351-115">The operand must be a variable, a [property](../../programming-guide/classes-and-structs/properties.md) access, or an [indexer](../../programming-guide/indexers/index.md) access.</span></span>

<span data-ttu-id="f7351-116">Operator przyrostu jest obsługiwany w dwóch formach: Przyrostkowy operator przyrostu, `x++` i operator przyrostu wartości prefiksu `++x` .</span><span class="sxs-lookup"><span data-stu-id="f7351-116">The increment operator is supported in two forms: the postfix increment operator, `x++`, and the prefix increment operator, `++x`.</span></span>

### <a name="postfix-increment-operator"></a><span data-ttu-id="f7351-117">Operator inkrementacji przyrostkowej</span><span class="sxs-lookup"><span data-stu-id="f7351-117">Postfix increment operator</span></span>

<span data-ttu-id="f7351-118">Wynik `x++` jest wartością `x` *przed* operacją, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="f7351-118">The result of `x++` is the value of `x` *before* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[postfix increment](snippets/ArithmeticOperators.cs#PostfixIncrement)]

### <a name="prefix-increment-operator"></a><span data-ttu-id="f7351-119">Operator przyrostu prefiksu</span><span class="sxs-lookup"><span data-stu-id="f7351-119">Prefix increment operator</span></span>

<span data-ttu-id="f7351-120">Wynik `++x` jest wartością `x` *po* operacji, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="f7351-120">The result of `++x` is the value of `x` *after* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[prefix increment](snippets/ArithmeticOperators.cs#PrefixIncrement)]

## <a name="decrement-operator---"></a><span data-ttu-id="f7351-121">Zmniejsz operator--</span><span class="sxs-lookup"><span data-stu-id="f7351-121">Decrement operator --</span></span>

<span data-ttu-id="f7351-122">Operator zmniejszania jednoargumentowego `--` zmniejsza jego operand o 1.</span><span class="sxs-lookup"><span data-stu-id="f7351-122">The unary decrement operator `--` decrements its operand by 1.</span></span> <span data-ttu-id="f7351-123">Operand musi być zmienną, dostępem do [Właściwości](../../programming-guide/classes-and-structs/properties.md) lub dostępem [indeksatora](../../programming-guide/indexers/index.md) .</span><span class="sxs-lookup"><span data-stu-id="f7351-123">The operand must be a variable, a [property](../../programming-guide/classes-and-structs/properties.md) access, or an [indexer](../../programming-guide/indexers/index.md) access.</span></span>

<span data-ttu-id="f7351-124">Operator zmniejszania jest obsługiwany w dwóch formach: operator zmniejszania przyrostu, `x--` i operator zmniejszania prefiksu `--x` .</span><span class="sxs-lookup"><span data-stu-id="f7351-124">The decrement operator is supported in two forms: the postfix decrement operator, `x--`, and the prefix decrement operator, `--x`.</span></span>

### <a name="postfix-decrement-operator"></a><span data-ttu-id="f7351-125">Operator dekrementacji przyrostkowej</span><span class="sxs-lookup"><span data-stu-id="f7351-125">Postfix decrement operator</span></span>

<span data-ttu-id="f7351-126">Wynik `x--` jest wartością `x` *przed* operacją, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="f7351-126">The result of `x--` is the value of `x` *before* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[postfix decrement](snippets/ArithmeticOperators.cs#PostfixDecrement)]

### <a name="prefix-decrement-operator"></a><span data-ttu-id="f7351-127">Operator zmniejszania prefiksu</span><span class="sxs-lookup"><span data-stu-id="f7351-127">Prefix decrement operator</span></span>

<span data-ttu-id="f7351-128">Wynik `--x` jest wartością `x` *po* operacji, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="f7351-128">The result of `--x` is the value of `x` *after* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[prefix decrement](snippets/ArithmeticOperators.cs#PrefixDecrement)]

## <a name="unary-plus-and-minus-operators"></a><span data-ttu-id="f7351-129">Operatory jednoargumentowe Plus i minus</span><span class="sxs-lookup"><span data-stu-id="f7351-129">Unary plus and minus operators</span></span>

<span data-ttu-id="f7351-130">Operator jednoargumentowy `+` zwraca wartość jego operandu.</span><span class="sxs-lookup"><span data-stu-id="f7351-130">The unary `+` operator returns the value of its operand.</span></span> <span data-ttu-id="f7351-131">Operator jednoargumentowy `-` oblicza liczbę negacji operandu.</span><span class="sxs-lookup"><span data-stu-id="f7351-131">The unary `-` operator computes the numeric negation of its operand.</span></span>

[!code-csharp-interactive[unary plus and minus](snippets/ArithmeticOperators.cs#UnaryPlusAndMinus)]

<span data-ttu-id="f7351-132">Typ [ULONG](../builtin-types/integral-numeric-types.md) nie obsługuje operatora jednoargumentowego `-` .</span><span class="sxs-lookup"><span data-stu-id="f7351-132">The [ulong](../builtin-types/integral-numeric-types.md) type doesn't support the unary `-` operator.</span></span>

## <a name="multiplication-operator-"></a><span data-ttu-id="f7351-133">Operator mnożenia \*</span><span class="sxs-lookup"><span data-stu-id="f7351-133">Multiplication operator \*</span></span>

<span data-ttu-id="f7351-134">Operator mnożenia `*` Oblicza iloczyn argumentów operacji:</span><span class="sxs-lookup"><span data-stu-id="f7351-134">The multiplication operator `*` computes the product of its operands:</span></span>

[!code-csharp-interactive[multiplication operator](snippets/ArithmeticOperators.cs#Multiplication)]

<span data-ttu-id="f7351-135">Operator jednoargumentowy `*` jest [operatorem pośredni wskaźnika](pointer-related-operators.md#pointer-indirection-operator-).</span><span class="sxs-lookup"><span data-stu-id="f7351-135">The unary `*` operator is the [pointer indirection operator](pointer-related-operators.md#pointer-indirection-operator-).</span></span>

## <a name="division-operator-"></a><span data-ttu-id="f7351-136">Operator dzielenia/</span><span class="sxs-lookup"><span data-stu-id="f7351-136">Division operator /</span></span>

<span data-ttu-id="f7351-137">Operator dzielenia `/` dzieli swój operand z lewej strony przez jego operand po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="f7351-137">The division operator `/` divides its left-hand operand by its right-hand operand.</span></span>

### <a name="integer-division"></a><span data-ttu-id="f7351-138">Dzielenie liczb całkowitych</span><span class="sxs-lookup"><span data-stu-id="f7351-138">Integer division</span></span>

<span data-ttu-id="f7351-139">Dla argumentów operacji typu Integer wynik `/` operatora jest typu integer i jest równy ilorazowi dwóch operandów zaokrąglonych na zero:</span><span class="sxs-lookup"><span data-stu-id="f7351-139">For the operands of integer types, the result of the `/` operator is of an integer type and equals the quotient of the two operands rounded towards zero:</span></span>

[!code-csharp-interactive[integer division](snippets/ArithmeticOperators.cs#IntegerDivision)]

<span data-ttu-id="f7351-140">Aby uzyskać iloraz dwóch operandów jako liczby zmiennoprzecinkowej, użyj `float` `double` typu,, lub `decimal` :</span><span class="sxs-lookup"><span data-stu-id="f7351-140">To obtain the quotient of the two operands as a floating-point number, use the `float`, `double`, or `decimal` type:</span></span>

[!code-csharp-interactive[integer as floating-point division](snippets/ArithmeticOperators.cs#IntegerAsFloatingPointDivision)]

### <a name="floating-point-division"></a><span data-ttu-id="f7351-141">Dzielenie zmiennoprzecinkowe</span><span class="sxs-lookup"><span data-stu-id="f7351-141">Floating-point division</span></span>

<span data-ttu-id="f7351-142">W przypadku `float` `double` typów, i `decimal` , wynik `/` operatora jest ilorazem dwóch operandów:</span><span class="sxs-lookup"><span data-stu-id="f7351-142">For the `float`, `double`, and `decimal` types, the result of the `/` operator is the quotient of the two operands:</span></span>

[!code-csharp-interactive[floating-point division](snippets/ArithmeticOperators.cs#FloatingPointDivision)]

<span data-ttu-id="f7351-143">Jeśli jeden z operandów to `decimal` , inny operand nie może być ani `float` `double` , ponieważ ani nie `float` `double` jest niejawnie konwertowany na `decimal` .</span><span class="sxs-lookup"><span data-stu-id="f7351-143">If one of the operands is `decimal`, another operand can be neither `float` nor `double`, because neither `float` nor `double` is implicitly convertible to `decimal`.</span></span> <span data-ttu-id="f7351-144">Należy jawnie skonwertować `float` `double` operand or na `decimal` Typ.</span><span class="sxs-lookup"><span data-stu-id="f7351-144">You must explicitly convert the `float` or `double` operand to the `decimal` type.</span></span> <span data-ttu-id="f7351-145">Aby uzyskać więcej informacji na temat konwersji typów liczbowych, zobacz [wbudowane konwersje numeryczne](../builtin-types/numeric-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="f7351-145">For more information about conversions between numeric types, see [Built-in numeric conversions](../builtin-types/numeric-conversions.md).</span></span>

## <a name="remainder-operator-"></a><span data-ttu-id="f7351-146">Procent pozostałej części</span><span class="sxs-lookup"><span data-stu-id="f7351-146">Remainder operator %</span></span>

<span data-ttu-id="f7351-147">Operator reszty `%` oblicza resztę po podzieleniu operandu po lewej stronie przez jego operand po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="f7351-147">The remainder operator `%` computes the remainder after dividing its left-hand operand by its right-hand operand.</span></span>

### <a name="integer-remainder"></a><span data-ttu-id="f7351-148">Reszta całkowita</span><span class="sxs-lookup"><span data-stu-id="f7351-148">Integer remainder</span></span>

<span data-ttu-id="f7351-149">W przypadku operandów typu Integer wynik `a % b` jest wartością wygenerowaną przez `a - (a / b) * b` .</span><span class="sxs-lookup"><span data-stu-id="f7351-149">For the operands of integer types, the result of `a % b` is the value produced by `a - (a / b) * b`.</span></span> <span data-ttu-id="f7351-150">Znak niezerowej reszty jest taki sam jak w przypadku operandu po lewej stronie, jak pokazano na poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="f7351-150">The sign of the non-zero remainder is the same as that of the left-hand operand, as the following example shows:</span></span>

[!code-csharp-interactive[integer remainder](snippets/ArithmeticOperators.cs#IntegerRemainder)]

<span data-ttu-id="f7351-151">Użyj <xref:System.Math.DivRem%2A?displayProperty=nameWithType> metody, aby obliczyć podział liczby całkowitej i reszty.</span><span class="sxs-lookup"><span data-stu-id="f7351-151">Use the <xref:System.Math.DivRem%2A?displayProperty=nameWithType> method to compute both integer division and remainder results.</span></span>

### <a name="floating-point-remainder"></a><span data-ttu-id="f7351-152">Pozostała część zmiennoprzecinkowa</span><span class="sxs-lookup"><span data-stu-id="f7351-152">Floating-point remainder</span></span>

<span data-ttu-id="f7351-153">Dla `float` argumentów i `double` , wynik `x % y` dla `x` wartości skończone i `y` jest wartością `z` taką jak</span><span class="sxs-lookup"><span data-stu-id="f7351-153">For the `float` and `double` operands, the result of `x % y` for the finite `x` and `y` is the value `z` such that</span></span>

- <span data-ttu-id="f7351-154">Znak `z` , jeśli wartość niezerowa, jest taki sam jak znak `x` .</span><span class="sxs-lookup"><span data-stu-id="f7351-154">The sign of `z`, if non-zero, is the same as the sign of `x`.</span></span>
- <span data-ttu-id="f7351-155">Wartość bezwzględna `z` jest wartością wygenerowaną przez, `|x| - n * |y|` gdzie `n` jest największą możliwą liczbą całkowitą, która jest mniejsza lub równa `|x| / |y|` i jest `|x|` `|y|` odpowiednio wartością bezwzględną `x` i `y` .</span><span class="sxs-lookup"><span data-stu-id="f7351-155">The absolute value of `z` is the value produced by `|x| - n * |y|` where `n` is the largest possible integer that is less than or equal to `|x| / |y|` and `|x|` and `|y|` are the absolute values of `x` and `y`, respectively.</span></span>

> [!NOTE]
> <span data-ttu-id="f7351-156">Ta metoda przetwarzania reszty jest analogiczna do tego, który jest używany dla argumentów wartości całkowitych, ale różni się od specyfikacji IEEE 754.</span><span class="sxs-lookup"><span data-stu-id="f7351-156">This method of computing the remainder is analogous to that used for integer operands, but different from the IEEE 754 specification.</span></span> <span data-ttu-id="f7351-157">Jeśli potrzebujesz pozostałej operacji, która jest zgodna ze specyfikacją IEEE 754, użyj <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="f7351-157">If you need the remainder operation that complies with the IEEE 754 specification, use the <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="f7351-158">Aby uzyskać informacje o zachowaniu `%` operatora z nieskończone operandami, zobacz sekcję [operator reszty](~/_csharplang/spec/expressions.md#remainder-operator) w [specyfikacji języka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="f7351-158">For information about the behavior of the `%` operator with non-finite operands, see the [Remainder operator](~/_csharplang/spec/expressions.md#remainder-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="f7351-159">Dla `decimal` operandów operator reszty `%` jest równoważny [operatorowi reszty](<xref:System.Decimal.op_Modulus(System.Decimal,System.Decimal)>) <xref:System.Decimal?displayProperty=nameWithType> typu.</span><span class="sxs-lookup"><span data-stu-id="f7351-159">For the `decimal` operands, the remainder operator `%` is equivalent to the [remainder operator](<xref:System.Decimal.op_Modulus(System.Decimal,System.Decimal)>) of the <xref:System.Decimal?displayProperty=nameWithType> type.</span></span>

<span data-ttu-id="f7351-160">Poniższy przykład demonstruje zachowanie operatora reszty z argumentami operacji zmiennoprzecinkowych:</span><span class="sxs-lookup"><span data-stu-id="f7351-160">The following example demonstrates the behavior of the remainder operator with floating-point operands:</span></span>

[!code-csharp-interactive[floating-point remainder](snippets/ArithmeticOperators.cs#FloatingPointRemainder)]

## <a name="addition-operator-"></a><span data-ttu-id="f7351-161">Operator dodawania +</span><span class="sxs-lookup"><span data-stu-id="f7351-161">Addition operator +</span></span>

<span data-ttu-id="f7351-162">Operator dodawania `+` oblicza sumę argumentów operacji:</span><span class="sxs-lookup"><span data-stu-id="f7351-162">The addition operator `+` computes the sum of its operands:</span></span>

[!code-csharp-interactive[addition operator](snippets/ArithmeticOperators.cs#Addition)]

<span data-ttu-id="f7351-163">Operatora można także użyć `+` do łączenia ciągów i delegatów.</span><span class="sxs-lookup"><span data-stu-id="f7351-163">You can also use the `+` operator for string concatenation and delegate combination.</span></span> <span data-ttu-id="f7351-164">Aby uzyskać więcej informacji, zobacz artykuł [ `+` `+=` Operatory i](addition-operator.md) .</span><span class="sxs-lookup"><span data-stu-id="f7351-164">For more information, see the [`+` and `+=` operators](addition-operator.md) article.</span></span>

## <a name="subtraction-operator--"></a><span data-ttu-id="f7351-165">Operator odejmowania —</span><span class="sxs-lookup"><span data-stu-id="f7351-165">Subtraction operator -</span></span>

<span data-ttu-id="f7351-166">Operator odejmowania `-` odejmuje swój prawy operand od jego operandu po lewej stronie:</span><span class="sxs-lookup"><span data-stu-id="f7351-166">The subtraction operator `-` subtracts its right-hand operand from its left-hand operand:</span></span>

[!code-csharp-interactive[subtraction operator](snippets/ArithmeticOperators.cs#Subtraction)]

<span data-ttu-id="f7351-167">Można również użyć `-` operatora do usuwania delegatów.</span><span class="sxs-lookup"><span data-stu-id="f7351-167">You can also use the `-` operator for delegate removal.</span></span> <span data-ttu-id="f7351-168">Aby uzyskać więcej informacji, zobacz artykuł [ `-` `-=` Operatory i](subtraction-operator.md) .</span><span class="sxs-lookup"><span data-stu-id="f7351-168">For more information, see the [`-` and `-=` operators](subtraction-operator.md) article.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="f7351-169">Przypisanie złożone</span><span class="sxs-lookup"><span data-stu-id="f7351-169">Compound assignment</span></span>

<span data-ttu-id="f7351-170">Dla operatora binarnego `op` wyrażenie złożonego przypisania formularza</span><span class="sxs-lookup"><span data-stu-id="f7351-170">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="f7351-171">jest równoważny</span><span class="sxs-lookup"><span data-stu-id="f7351-171">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="f7351-172">z tą różnicą, że `x` jest obliczana tylko raz.</span><span class="sxs-lookup"><span data-stu-id="f7351-172">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="f7351-173">Poniższy przykład ilustruje użycie przypisania złożonego z operatorami arytmetycznymi:</span><span class="sxs-lookup"><span data-stu-id="f7351-173">The following example demonstrates the usage of compound assignment with arithmetic operators:</span></span>

[!code-csharp-interactive[compound assignment](snippets/ArithmeticOperators.cs#CompoundAssignment)]

<span data-ttu-id="f7351-174">Ze względu na [promocje liczbowe](~/_csharplang/spec/expressions.md#numeric-promotions)wynik `op` operacji może nie być niejawnie konwertowany na typ `T` `x` .</span><span class="sxs-lookup"><span data-stu-id="f7351-174">Because of [numeric promotions](~/_csharplang/spec/expressions.md#numeric-promotions), the result of the `op` operation might be not implicitly convertible to the type `T` of `x`.</span></span> <span data-ttu-id="f7351-175">W takim przypadku, jeśli `op` jest wstępnie zdefiniowanym operatorem, a wynik operacji jest jawnie konwertowany na typ `T` `x` , wyrażenie przypisania złożonego formularza `x op= y` jest równoważne z `x = (T)(x op y)` , z tą różnicą, że `x` jest tylko raz oceniane.</span><span class="sxs-lookup"><span data-stu-id="f7351-175">In such a case, if `op` is a predefined operator and the result of the operation is explicitly convertible to the type `T` of `x`, a compound assignment expression of the form `x op= y` is equivalent to `x = (T)(x op y)`, except that `x` is only evaluated once.</span></span> <span data-ttu-id="f7351-176">Poniższy przykład ilustruje takie zachowanie:</span><span class="sxs-lookup"><span data-stu-id="f7351-176">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[compound assignment with cast](snippets/ArithmeticOperators.cs#CompoundAssignmentWithCast)]

<span data-ttu-id="f7351-177">Należy również użyć `+=` operatorów i `-=` , aby subskrybować lub anulować subskrypcję [zdarzenia](../keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="f7351-177">You also use the `+=` and `-=` operators to subscribe to and unsubscribe from an [event](../keywords/event.md), respectively.</span></span> <span data-ttu-id="f7351-178">Aby uzyskać więcej informacji, zobacz [subskrybowanie i anulowanie subskrypcji zdarzeń](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="f7351-178">For more information, see [How to subscribe to and unsubscribe from events](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="operator-precedence-and-associativity"></a><span data-ttu-id="f7351-179">Pierwszeństwo operatorów i łączność</span><span class="sxs-lookup"><span data-stu-id="f7351-179">Operator precedence and associativity</span></span>

<span data-ttu-id="f7351-180">Na poniższej liście przedstawiono operatory arytmetyczne zaczynające się od najwyższego priorytetu do najniższego:</span><span class="sxs-lookup"><span data-stu-id="f7351-180">The following list orders arithmetic operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="f7351-181">Operatory przyrostka `x++` i zmniejszenie `x--`</span><span class="sxs-lookup"><span data-stu-id="f7351-181">Postfix increment `x++` and decrement `x--` operators</span></span>
- <span data-ttu-id="f7351-182">Przyrost i `++x` zmniejszenie prefiksu `--x` oraz jednoargumentowe `+` i `-` Operatory</span><span class="sxs-lookup"><span data-stu-id="f7351-182">Prefix increment `++x` and decrement `--x` and unary `+` and `-` operators</span></span>
- <span data-ttu-id="f7351-183">Mnożenia `*` , `/` , i `%` Operatory</span><span class="sxs-lookup"><span data-stu-id="f7351-183">Multiplicative `*`, `/`, and `%` operators</span></span>
- <span data-ttu-id="f7351-184">Dodatek `+` i `-` Operatory</span><span class="sxs-lookup"><span data-stu-id="f7351-184">Additive `+` and `-` operators</span></span>

<span data-ttu-id="f7351-185">Binarne operatory arytmetyczne są z lewej strony skojarzenia.</span><span class="sxs-lookup"><span data-stu-id="f7351-185">Binary arithmetic operators are left-associative.</span></span> <span data-ttu-id="f7351-186">Oznacza to, że operatory o tym samym poziomie pierwszeństwa są oceniane od lewej do prawej.</span><span class="sxs-lookup"><span data-stu-id="f7351-186">That is, operators with the same precedence level are evaluated from left to right.</span></span>

<span data-ttu-id="f7351-187">Użyj nawiasów, `()` , aby zmienić kolejność oceny nałożona przez pierwszeństwo operatorów i łączność.</span><span class="sxs-lookup"><span data-stu-id="f7351-187">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence and associativity.</span></span>

[!code-csharp-interactive[precedence and associativity](snippets/ArithmeticOperators.cs#PrecedenceAndAssociativity)]

<span data-ttu-id="f7351-188">Aby uzyskać pełną listę operatorów języka C# uporządkowanych według poziomu pierwszeństwa, zobacz sekcję [pierwszeństwo](index.md#operator-precedence) operatorów w artykule [operatory języka c#](index.md) .</span><span class="sxs-lookup"><span data-stu-id="f7351-188">For the complete list of C# operators ordered by precedence level, see the [Operator precedence](index.md#operator-precedence) section of the [C# operators](index.md) article.</span></span>

## <a name="arithmetic-overflow-and-division-by-zero"></a><span data-ttu-id="f7351-189">Przepełnienie arytmetyczne i dzielenie przez zero</span><span class="sxs-lookup"><span data-stu-id="f7351-189">Arithmetic overflow and division by zero</span></span>

<span data-ttu-id="f7351-190">Gdy wynik operacji arytmetycznej jest poza zakresem możliwych wartości skończonego typu liczbowego, zachowanie operatora arytmetycznego zależy od typu jego operandów.</span><span class="sxs-lookup"><span data-stu-id="f7351-190">When the result of an arithmetic operation is outside the range of possible finite values of the involved numeric type, the behavior of an arithmetic operator depends on the type of its operands.</span></span>

### <a name="integer-arithmetic-overflow"></a><span data-ttu-id="f7351-191">Przepełnienie arytmetyczne liczb całkowitych</span><span class="sxs-lookup"><span data-stu-id="f7351-191">Integer arithmetic overflow</span></span>

<span data-ttu-id="f7351-192">Dzielenie liczby całkowitej przez zero zawsze zgłasza <xref:System.DivideByZeroException> .</span><span class="sxs-lookup"><span data-stu-id="f7351-192">Integer division by zero always throws a <xref:System.DivideByZeroException>.</span></span>

<span data-ttu-id="f7351-193">W przypadku przepełnienia arytmetycznego wartości całkowitych, kontekst sprawdzania przepełnienia, który można [sprawdzić lub nie zaznaczyć](../keywords/checked-and-unchecked.md), kontroluje zachowanie wyników:</span><span class="sxs-lookup"><span data-stu-id="f7351-193">In case of integer arithmetic overflow, an overflow checking context, which can be [checked or unchecked](../keywords/checked-and-unchecked.md), controls the resulting behavior:</span></span>

- <span data-ttu-id="f7351-194">Jeśli przepełnienie ma miejsce w wyrażeniu stałym, wystąpi błąd w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="f7351-194">In a checked context, if overflow happens in a constant expression, a compile-time error occurs.</span></span> <span data-ttu-id="f7351-195">W przeciwnym razie, gdy operacja zostanie wykonana w czasie wykonywania, <xref:System.OverflowException> zostanie zgłoszony.</span><span class="sxs-lookup"><span data-stu-id="f7351-195">Otherwise, when the operation is performed at run time, an <xref:System.OverflowException> is thrown.</span></span>
- <span data-ttu-id="f7351-196">W kontekście niesprawdzonym wynik zostanie obcięty przez odrzucenie wszystkich bitów o dużej kolejności, które nie mieszczą się w typie docelowym.</span><span class="sxs-lookup"><span data-stu-id="f7351-196">In an unchecked context, the result is truncated by discarding any high-order bits that don't fit in the destination type.</span></span>

<span data-ttu-id="f7351-197">Wraz z [sprawdzonymi i niesprawdzonymi](../keywords/checked-and-unchecked.md) instrukcjami można użyć `checked` operatorów i, `unchecked` Aby kontrolować kontekst sprawdzania przepełnienia, w którym jest oceniane wyrażenie:</span><span class="sxs-lookup"><span data-stu-id="f7351-197">Along with the [checked and unchecked](../keywords/checked-and-unchecked.md) statements, you can use the `checked` and `unchecked` operators to control the overflow checking context, in which an expression is evaluated:</span></span>

[!code-csharp-interactive[checked and unchecked](snippets/ArithmeticOperators.cs#CheckedUnchecked)]

<span data-ttu-id="f7351-198">Domyślnie operacje arytmetyczne odbywają się w *niesprawdzonym* kontekście.</span><span class="sxs-lookup"><span data-stu-id="f7351-198">By default, arithmetic operations occur in an *unchecked* context.</span></span>

### <a name="floating-point-arithmetic-overflow"></a><span data-ttu-id="f7351-199">Przepełnienie arytmetyczne zmiennoprzecinkowe</span><span class="sxs-lookup"><span data-stu-id="f7351-199">Floating-point arithmetic overflow</span></span>

<span data-ttu-id="f7351-200">Operacje arytmetyczne z `float` `double` typami i nigdy nie generują wyjątku.</span><span class="sxs-lookup"><span data-stu-id="f7351-200">Arithmetic operations with the `float` and `double` types never throw an exception.</span></span> <span data-ttu-id="f7351-201">Wynik operacji arytmetycznych z tymi typami może być jedną z wartości specjalnych, które reprezentują nieskończoność i nie liczbę:</span><span class="sxs-lookup"><span data-stu-id="f7351-201">The result of arithmetic operations with those types can be one of special values that represent infinity and not-a-number:</span></span>

[!code-csharp-interactive[double non-finite values](snippets/ArithmeticOperators.cs#FloatingPointOverflow)]

<span data-ttu-id="f7351-202">W przypadku operandów `decimal` typu, przepełnienie arytmetyczne zawsze zgłasza, <xref:System.OverflowException> a dzielenie przez zero zawsze zgłasza <xref:System.DivideByZeroException> .</span><span class="sxs-lookup"><span data-stu-id="f7351-202">For the operands of the `decimal` type, arithmetic overflow always throws an <xref:System.OverflowException> and division by zero always throws a <xref:System.DivideByZeroException>.</span></span>

## <a name="round-off-errors"></a><span data-ttu-id="f7351-203">Błędy zaokrągleń</span><span class="sxs-lookup"><span data-stu-id="f7351-203">Round-off errors</span></span>

<span data-ttu-id="f7351-204">Ze względu na ogólne ograniczenia reprezentacji liczb zmiennoprzecinkowych i arytmetycznych zmiennoprzecinkowych błędy zaokrągleń mogą wystąpić w obliczeniach z typami zmiennoprzecinkowymi.</span><span class="sxs-lookup"><span data-stu-id="f7351-204">Because of general limitations of the floating-point representation of real numbers and floating-point arithmetic, round-off errors might occur in calculations with floating-point types.</span></span> <span data-ttu-id="f7351-205">Oznacza to, że wygenerowany wynik wyrażenia może być inny niż oczekiwany wynik matematyczny.</span><span class="sxs-lookup"><span data-stu-id="f7351-205">That is, the produced result of an expression might differ from the expected mathematical result.</span></span> <span data-ttu-id="f7351-206">Poniższy przykład ilustruje kilka takich przypadków:</span><span class="sxs-lookup"><span data-stu-id="f7351-206">The following example demonstrates several such cases:</span></span>

[!code-csharp-interactive[round-off errors](snippets/ArithmeticOperators.cs#RoundOffErrors)]

<span data-ttu-id="f7351-207">Aby uzyskać więcej informacji, zobacz uwagi na stronach referencyjnych [System. Double](/dotnet/api/system.double#remarks), [System. Single](/dotnet/api/system.single#remarks)lub [System. Decimal](/dotnet/api/system.decimal#remarks) .</span><span class="sxs-lookup"><span data-stu-id="f7351-207">For more information, see remarks at the [System.Double](/dotnet/api/system.double#remarks), [System.Single](/dotnet/api/system.single#remarks), or [System.Decimal](/dotnet/api/system.decimal#remarks) reference pages.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="f7351-208">Przeciążanie operatora</span><span class="sxs-lookup"><span data-stu-id="f7351-208">Operator overloadability</span></span>

<span data-ttu-id="f7351-209">Typ zdefiniowany przez użytkownika może [przeciążać](operator-overloading.md) operatory jednoargumentowe ( `++` , `--` , `+` i `-` ) oraz binarnych ( `*` , `/` ,, `%` `+` i `-` ) arytmetycznych.</span><span class="sxs-lookup"><span data-stu-id="f7351-209">A user-defined type can [overload](operator-overloading.md) the unary (`++`, `--`, `+`, and `-`) and binary (`*`, `/`, `%`, `+`, and `-`) arithmetic operators.</span></span> <span data-ttu-id="f7351-210">Gdy operator binarny jest przeciążony, odpowiadający mu operator przypisania złożonego jest również niejawnie przeciążony.</span><span class="sxs-lookup"><span data-stu-id="f7351-210">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="f7351-211">Typ zdefiniowany przez użytkownika nie może jawnie przeciążać złożonego operatora przypisania.</span><span class="sxs-lookup"><span data-stu-id="f7351-211">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="f7351-212">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="f7351-212">C# language specification</span></span>

<span data-ttu-id="f7351-213">Aby uzyskać więcej informacji, zobacz następujące sekcje [specyfikacji języka C#](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="f7351-213">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="f7351-214">Operatory przyrostka i zmniejszenie</span><span class="sxs-lookup"><span data-stu-id="f7351-214">Postfix increment and decrement operators</span></span>](~/_csharplang/spec/expressions.md#postfix-increment-and-decrement-operators)
- [<span data-ttu-id="f7351-215">Operatory prefiksów inkrementacji i dekrementacji</span><span class="sxs-lookup"><span data-stu-id="f7351-215">Prefix increment and decrement operators</span></span>](~/_csharplang/spec/expressions.md#prefix-increment-and-decrement-operators)
- [<span data-ttu-id="f7351-216">Jednoargumentowy operator plus</span><span class="sxs-lookup"><span data-stu-id="f7351-216">Unary plus operator</span></span>](~/_csharplang/spec/expressions.md#unary-plus-operator)
- [<span data-ttu-id="f7351-217">Jednoargumentowy operator minus</span><span class="sxs-lookup"><span data-stu-id="f7351-217">Unary minus operator</span></span>](~/_csharplang/spec/expressions.md#unary-minus-operator)
- [<span data-ttu-id="f7351-218">Operator mnożenia</span><span class="sxs-lookup"><span data-stu-id="f7351-218">Multiplication operator</span></span>](~/_csharplang/spec/expressions.md#multiplication-operator)
- [<span data-ttu-id="f7351-219">Operator dzielenia</span><span class="sxs-lookup"><span data-stu-id="f7351-219">Division operator</span></span>](~/_csharplang/spec/expressions.md#division-operator)
- [<span data-ttu-id="f7351-220">Operator reszty</span><span class="sxs-lookup"><span data-stu-id="f7351-220">Remainder operator</span></span>](~/_csharplang/spec/expressions.md#remainder-operator)
- [<span data-ttu-id="f7351-221">Operator dodawania</span><span class="sxs-lookup"><span data-stu-id="f7351-221">Addition operator</span></span>](~/_csharplang/spec/expressions.md#addition-operator)
- [<span data-ttu-id="f7351-222">Operator odejmowania</span><span class="sxs-lookup"><span data-stu-id="f7351-222">Subtraction operator</span></span>](~/_csharplang/spec/expressions.md#subtraction-operator)
- [<span data-ttu-id="f7351-223">Przypisanie złożone</span><span class="sxs-lookup"><span data-stu-id="f7351-223">Compound assignment</span></span>](~/_csharplang/spec/expressions.md#compound-assignment)
- [<span data-ttu-id="f7351-224">Sprawdzone i niesprawdzone operatory</span><span class="sxs-lookup"><span data-stu-id="f7351-224">The checked and unchecked operators</span></span>](~/_csharplang/spec/expressions.md#the-checked-and-unchecked-operators)
- [<span data-ttu-id="f7351-225">Promocje numeryczne</span><span class="sxs-lookup"><span data-stu-id="f7351-225">Numeric promotions</span></span>](~/_csharplang/spec/expressions.md#numeric-promotions)

## <a name="see-also"></a><span data-ttu-id="f7351-226">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f7351-226">See also</span></span>

- [<span data-ttu-id="f7351-227">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="f7351-227">C# reference</span></span>](../index.md)
- [<span data-ttu-id="f7351-228">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="f7351-228">C# operators</span></span>](index.md)
- <xref:System.Math?displayProperty=nameWithType>
- <xref:System.MathF?displayProperty=nameWithType>
- [<span data-ttu-id="f7351-229">Wartości numeryczne na platformie .NET</span><span class="sxs-lookup"><span data-stu-id="f7351-229">Numerics in .NET</span></span>](../../../standard/numerics.md)
