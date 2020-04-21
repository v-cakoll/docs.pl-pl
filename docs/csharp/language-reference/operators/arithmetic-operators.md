---
title: Operatory arytmetyczne — odwołanie do języka C#
description: Dowiedz się więcej o operatorach języka C#, które wykonują operacje mnożenia, dzielenia, pozostałej, dodawania i odejmowania za pomocą typów liczbowych.
ms.date: 03/27/2019
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
ms.openlocfilehash: ea9bf9e065b2953fd20e0503a19d1dc143064c5d
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738735"
---
# <a name="arithmetic-operators-c-reference"></a><span data-ttu-id="4c605-103">Operatory arytmetyczne (odwołanie do języka C#)</span><span class="sxs-lookup"><span data-stu-id="4c605-103">Arithmetic operators (C# reference)</span></span>

<span data-ttu-id="4c605-104">Następujące operatory wykonują operacje arytmetyczne z operandami typów liczbowych:</span><span class="sxs-lookup"><span data-stu-id="4c605-104">The following operators perform arithmetic operations with operands of numeric types:</span></span>

- <span data-ttu-id="4c605-105">Operatory [ `++` niepokalane (przyrost)](#increment-operator-), [ `--` (dekrementowanie)](#decrement-operator---), [ `+` (plus)](#unary-plus-and-minus-operators)i [ `-` (minus)](#unary-plus-and-minus-operators)</span><span class="sxs-lookup"><span data-stu-id="4c605-105">Unary [`++` (increment)](#increment-operator-), [`--` (decrement)](#decrement-operator---), [`+` (plus)](#unary-plus-and-minus-operators), and [`-` (minus)](#unary-plus-and-minus-operators) operators</span></span>
- <span data-ttu-id="4c605-106">Operatory [ `*` binarne (mnożenie)](#multiplication-operator-), [ `/` (podział)](#division-operator-), [ `%` (reszta)](#remainder-operator-), [ `+` (dodawanie)](#addition-operator-)i [ `-` (odejmowanie)](#subtraction-operator--)</span><span class="sxs-lookup"><span data-stu-id="4c605-106">Binary [`*` (multiplication)](#multiplication-operator-), [`/` (division)](#division-operator-), [`%` (remainder)](#remainder-operator-), [`+` (addition)](#addition-operator-), and [`-` (subtraction)](#subtraction-operator--) operators</span></span>

<span data-ttu-id="4c605-107">Operatory te są obsługiwane przez wszystkie typy liczbowe [całkowane](../builtin-types/integral-numeric-types.md) i [zmiennoprzecinkowe.](../builtin-types/floating-point-numeric-types.md)</span><span class="sxs-lookup"><span data-stu-id="4c605-107">Those operators are supported by all [integral](../builtin-types/integral-numeric-types.md) and [floating-point](../builtin-types/floating-point-numeric-types.md) numeric types.</span></span>

## <a name="increment-operator-"></a><span data-ttu-id="4c605-108">Operator przyrostu ++</span><span class="sxs-lookup"><span data-stu-id="4c605-108">Increment operator ++</span></span>

<span data-ttu-id="4c605-109">Operator `++` przyrostu bezemisowego zwiększa swój operand o 1.</span><span class="sxs-lookup"><span data-stu-id="4c605-109">The unary increment operator `++` increments its operand by 1.</span></span> <span data-ttu-id="4c605-110">Operand musi być zmienną, dostępem do [właściwości](../../programming-guide/classes-and-structs/properties.md) lub dostępem [do indeksatora.](../../programming-guide/indexers/index.md)</span><span class="sxs-lookup"><span data-stu-id="4c605-110">The operand must be a variable, a [property](../../programming-guide/classes-and-structs/properties.md) access, or an [indexer](../../programming-guide/indexers/index.md) access.</span></span>

<span data-ttu-id="4c605-111">Operator przyrostu jest obsługiwany w dwóch formach: operator `x++`przyrostu po poprawce i operator `++x`przyrostu prefiksu, .</span><span class="sxs-lookup"><span data-stu-id="4c605-111">The increment operator is supported in two forms: the postfix increment operator, `x++`, and the prefix increment operator, `++x`.</span></span>

### <a name="postfix-increment-operator"></a><span data-ttu-id="4c605-112">Operator inkrementacji przyrostkowej</span><span class="sxs-lookup"><span data-stu-id="4c605-112">Postfix increment operator</span></span>

<span data-ttu-id="4c605-113">Wynik `x++` jest wartość `x` *przed* operacją, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="4c605-113">The result of `x++` is the value of `x` *before* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[postfix increment](snippets/ArithmeticOperators.cs#PostfixIncrement)]

### <a name="prefix-increment-operator"></a><span data-ttu-id="4c605-114">Operator przyrostu prefiksu</span><span class="sxs-lookup"><span data-stu-id="4c605-114">Prefix increment operator</span></span>

<span data-ttu-id="4c605-115">Wynik `++x` jest wartość `x` *po* operacji, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="4c605-115">The result of `++x` is the value of `x` *after* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[prefix increment](snippets/ArithmeticOperators.cs#PrefixIncrement)]

## <a name="decrement-operator---"></a><span data-ttu-id="4c605-116">Operator dekrementacji --</span><span class="sxs-lookup"><span data-stu-id="4c605-116">Decrement operator --</span></span>

<span data-ttu-id="4c605-117">Operator `--` dekrementacji nieobsadzowej zmniejsza swoją operand o 1.</span><span class="sxs-lookup"><span data-stu-id="4c605-117">The unary decrement operator `--` decrements its operand by 1.</span></span> <span data-ttu-id="4c605-118">Operand musi być zmienną, dostępem do [właściwości](../../programming-guide/classes-and-structs/properties.md) lub dostępem [do indeksatora.](../../programming-guide/indexers/index.md)</span><span class="sxs-lookup"><span data-stu-id="4c605-118">The operand must be a variable, a [property](../../programming-guide/classes-and-structs/properties.md) access, or an [indexer](../../programming-guide/indexers/index.md) access.</span></span>

<span data-ttu-id="4c605-119">Operator dekrementacji jest obsługiwany w dwóch formach: operator `x--`usuwania poprawek i operator `--x`dekrementacji prefiksu, .</span><span class="sxs-lookup"><span data-stu-id="4c605-119">The decrement operator is supported in two forms: the postfix decrement operator, `x--`, and the prefix decrement operator, `--x`.</span></span>

### <a name="postfix-decrement-operator"></a><span data-ttu-id="4c605-120">Operator dekrementacji przyrostkowej</span><span class="sxs-lookup"><span data-stu-id="4c605-120">Postfix decrement operator</span></span>

<span data-ttu-id="4c605-121">Wynik `x--` jest wartość `x` *przed* operacją, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="4c605-121">The result of `x--` is the value of `x` *before* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[postfix decrement](snippets/ArithmeticOperators.cs#PostfixDecrement)]

### <a name="prefix-decrement-operator"></a><span data-ttu-id="4c605-122">Operator dekrementacji prefiksu</span><span class="sxs-lookup"><span data-stu-id="4c605-122">Prefix decrement operator</span></span>

<span data-ttu-id="4c605-123">Wynik `--x` jest wartość `x` *po* operacji, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="4c605-123">The result of `--x` is the value of `x` *after* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[prefix decrement](snippets/ArithmeticOperators.cs#PrefixDecrement)]

## <a name="unary-plus-and-minus-operators"></a><span data-ttu-id="4c605-124">Operatory Unary plus i minus</span><span class="sxs-lookup"><span data-stu-id="4c605-124">Unary plus and minus operators</span></span>

<span data-ttu-id="4c605-125">Operator unary `+` zwraca wartość jego operand.</span><span class="sxs-lookup"><span data-stu-id="4c605-125">The unary `+` operator returns the value of its operand.</span></span> <span data-ttu-id="4c605-126">Operator unary `-` oblicza numeryczne negację jego operandu.</span><span class="sxs-lookup"><span data-stu-id="4c605-126">The unary `-` operator computes the numeric negation of its operand.</span></span>

[!code-csharp-interactive[unary plus and minus](snippets/ArithmeticOperators.cs#UnaryPlusAndMinus)]

<span data-ttu-id="4c605-127">Typ [ulong](../builtin-types/integral-numeric-types.md) nie obsługuje operatora `-` bezparowi.</span><span class="sxs-lookup"><span data-stu-id="4c605-127">The [ulong](../builtin-types/integral-numeric-types.md) type doesn't support the unary `-` operator.</span></span>

## <a name="multiplication-operator-"></a><span data-ttu-id="4c605-128">Operator mnożenia \*</span><span class="sxs-lookup"><span data-stu-id="4c605-128">Multiplication operator \*</span></span>

<span data-ttu-id="4c605-129">Operator `*` mnożenia oblicza produkt swoich operandów:</span><span class="sxs-lookup"><span data-stu-id="4c605-129">The multiplication operator `*` computes the product of its operands:</span></span>

[!code-csharp-interactive[multiplication operator](snippets/ArithmeticOperators.cs#Multiplication)]

<span data-ttu-id="4c605-130">Operator unary `*` jest [operatorem pośrednim wskaźnika](pointer-related-operators.md#pointer-indirection-operator-).</span><span class="sxs-lookup"><span data-stu-id="4c605-130">The unary `*` operator is the [pointer indirection operator](pointer-related-operators.md#pointer-indirection-operator-).</span></span>

## <a name="division-operator-"></a><span data-ttu-id="4c605-131">Operator działu /</span><span class="sxs-lookup"><span data-stu-id="4c605-131">Division operator /</span></span>

<span data-ttu-id="4c605-132">Operator `/` dywizji dzieli swój lewoskręt przez jego prawicowy operand.</span><span class="sxs-lookup"><span data-stu-id="4c605-132">The division operator `/` divides its left-hand operand by its right-hand operand.</span></span>

### <a name="integer-division"></a><span data-ttu-id="4c605-133">Podział liczby całkowitej</span><span class="sxs-lookup"><span data-stu-id="4c605-133">Integer division</span></span>

<span data-ttu-id="4c605-134">W przypadku argumentów typów całkowitych wynik `/` operatora jest typu całkowitej i jest równy ilorazowi dwóch argumentów zaokrąglonych do zera:</span><span class="sxs-lookup"><span data-stu-id="4c605-134">For the operands of integer types, the result of the `/` operator is of an integer type and equals the quotient of the two operands rounded towards zero:</span></span>

[!code-csharp-interactive[integer division](snippets/ArithmeticOperators.cs#IntegerDivision)]

<span data-ttu-id="4c605-135">Aby uzyskać iloraz dwóch argumentów jako liczbę zmiennoprzecinkową, należy użyć `float`, `double`lub `decimal` typu:</span><span class="sxs-lookup"><span data-stu-id="4c605-135">To obtain the quotient of the two operands as a floating-point number, use the `float`, `double`, or `decimal` type:</span></span>

[!code-csharp-interactive[integer as floating-point division](snippets/ArithmeticOperators.cs#IntegerAsFloatingPointDivision)]

### <a name="floating-point-division"></a><span data-ttu-id="4c605-136">Podział zmiennoprzecinowy</span><span class="sxs-lookup"><span data-stu-id="4c605-136">Floating-point division</span></span>

<span data-ttu-id="4c605-137">Dla `float`, `double`i `decimal` typów, wynikiem `/` operatora jest iloraz dwóch operandów:</span><span class="sxs-lookup"><span data-stu-id="4c605-137">For the `float`, `double`, and `decimal` types, the result of the `/` operator is the quotient of the two operands:</span></span>

[!code-csharp-interactive[floating-point division](snippets/ArithmeticOperators.cs#FloatingPointDivision)]

<span data-ttu-id="4c605-138">Jeśli jeden z `decimal`operandów jest , inny `float` operand nie może być ani, `double`ponieważ ani `float` nie `double` jest w sposób dorozumiany zamienny na `decimal`.</span><span class="sxs-lookup"><span data-stu-id="4c605-138">If one of the operands is `decimal`, another operand can be neither `float` nor `double`, because neither `float` nor `double` is implicitly convertible to `decimal`.</span></span> <span data-ttu-id="4c605-139">Należy jawnie przekonwertować `float` lub `decimal` `double` operand do typu.</span><span class="sxs-lookup"><span data-stu-id="4c605-139">You must explicitly convert the `float` or `double` operand to the `decimal` type.</span></span> <span data-ttu-id="4c605-140">Aby uzyskać więcej informacji o konwersjach między typami liczbowymi, zobacz [Wbudowane konwersje liczbowe](../builtin-types/numeric-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="4c605-140">For more information about conversions between numeric types, see [Built-in numeric conversions](../builtin-types/numeric-conversions.md).</span></span>

## <a name="remainder-operator-"></a><span data-ttu-id="4c605-141">Pozostały operator %</span><span class="sxs-lookup"><span data-stu-id="4c605-141">Remainder operator %</span></span>

<span data-ttu-id="4c605-142">Pozostała część `%` operatora oblicza pozostałą część po podzieleniu jego lewej opery przez jego prawej operyndu.</span><span class="sxs-lookup"><span data-stu-id="4c605-142">The remainder operator `%` computes the remainder after dividing its left-hand operand by its right-hand operand.</span></span>

### <a name="integer-remainder"></a><span data-ttu-id="4c605-143">Pozostała część całkowita</span><span class="sxs-lookup"><span data-stu-id="4c605-143">Integer remainder</span></span>

<span data-ttu-id="4c605-144">Dla argumentów typów całkowitych wynikiem `a % b` jest wartość wyprodukowana `a - (a / b) * b`przez .</span><span class="sxs-lookup"><span data-stu-id="4c605-144">For the operands of integer types, the result of `a % b` is the value produced by `a - (a / b) * b`.</span></span> <span data-ttu-id="4c605-145">Znak pozostałej niezerowej jest taki sam jak w leworęcznym operand, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="4c605-145">The sign of the non-zero remainder is the same as that of the left-hand operand, as the following example shows:</span></span>

[!code-csharp-interactive[integer remainder](snippets/ArithmeticOperators.cs#IntegerRemainder)]

<span data-ttu-id="4c605-146"><xref:System.Math.DivRem%2A?displayProperty=nameWithType> Metoda służy do obliczania zarówno wyników podziału liczby całkowitej, jak i pozostałej.</span><span class="sxs-lookup"><span data-stu-id="4c605-146">Use the <xref:System.Math.DivRem%2A?displayProperty=nameWithType> method to compute both integer division and remainder results.</span></span>

### <a name="floating-point-remainder"></a><span data-ttu-id="4c605-147">Pozostała część zmiennoprzecinowa</span><span class="sxs-lookup"><span data-stu-id="4c605-147">Floating-point remainder</span></span>

<span data-ttu-id="4c605-148">Dla `float` i `double` operands, wynik `x % y` dla skończonego `x` i `z` `y` jest wartość taka, że</span><span class="sxs-lookup"><span data-stu-id="4c605-148">For the `float` and `double` operands, the result of `x % y` for the finite `x` and `y` is the value `z` such that</span></span>

- <span data-ttu-id="4c605-149">Znak `z`, jeśli nie zero, jest taki sam `x`jak znak .</span><span class="sxs-lookup"><span data-stu-id="4c605-149">The sign of `z`, if non-zero, is the same as the sign of `x`.</span></span>
- <span data-ttu-id="4c605-150">Wartość bezwzględna `z` jest wartością `|x| - n * |y|` `n` wytwarzaną przez miejsce, w którym jest `|x| / |y|` największą możliwą liczą całkowitą, która jest mniejsza lub równa `|x|` i i `|y|` jest wartością bezwzględną `x` i `y`, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="4c605-150">The absolute value of `z` is the value produced by `|x| - n * |y|` where `n` is the largest possible integer that is less than or equal to `|x| / |y|` and `|x|` and `|y|` are the absolute values of `x` and `y`, respectively.</span></span>

> [!NOTE]
> <span data-ttu-id="4c605-151">Ta metoda obliczania pozostałej części jest analogiczna do tej używanej dla argumentów całkowitych, ale różni się od specyfikacji IEEE 754.</span><span class="sxs-lookup"><span data-stu-id="4c605-151">This method of computing the remainder is analogous to that used for integer operands, but different from the IEEE 754 specification.</span></span> <span data-ttu-id="4c605-152">Jeśli potrzebujesz pozostałej operacji zgodnej ze specyfikacją IEEE 754, użyj tej <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="4c605-152">If you need the remainder operation that complies with the IEEE 754 specification, use the <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="4c605-153">Aby uzyskać informacje na `%` temat zachowania operatora z nieo skończonymi operandami, zobacz sekcję [Operator reszty](~/_csharplang/spec/expressions.md#remainder-operator) [specyfikacji języka Języka C#.](~/_csharplang/spec/introduction.md)</span><span class="sxs-lookup"><span data-stu-id="4c605-153">For information about the behavior of the `%` operator with non-finite operands, see the [Remainder operator](~/_csharplang/spec/expressions.md#remainder-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="4c605-154">W `decimal` przypadku argumentów operator `%` pozostałej części jest odpowiednikiem [pozostałego operatora](<xref:System.Decimal.op_Modulus(System.Decimal,System.Decimal)>) <xref:System.Decimal?displayProperty=nameWithType> typu.</span><span class="sxs-lookup"><span data-stu-id="4c605-154">For the `decimal` operands, the remainder operator `%` is equivalent to the [remainder operator](<xref:System.Decimal.op_Modulus(System.Decimal,System.Decimal)>) of the <xref:System.Decimal?displayProperty=nameWithType> type.</span></span>

<span data-ttu-id="4c605-155">Poniższy przykład pokazuje zachowanie pozostałego operatora z argumentami zmiennoprzecinkowymi:</span><span class="sxs-lookup"><span data-stu-id="4c605-155">The following example demonstrates the behavior of the remainder operator with floating-point operands:</span></span>

[!code-csharp-interactive[floating-point remainder](snippets/ArithmeticOperators.cs#FloatingPointRemainder)]

## <a name="addition-operator-"></a><span data-ttu-id="4c605-156">Operator dodawania +</span><span class="sxs-lookup"><span data-stu-id="4c605-156">Addition operator +</span></span>

<span data-ttu-id="4c605-157">Operator `+` dodawania oblicza sumę swoich operandów:</span><span class="sxs-lookup"><span data-stu-id="4c605-157">The addition operator `+` computes the sum of its operands:</span></span>

[!code-csharp-interactive[addition operator](snippets/ArithmeticOperators.cs#Addition)]

<span data-ttu-id="4c605-158">Operator można również `+` użyć do łączenia ciągów i delegować kombinację.</span><span class="sxs-lookup"><span data-stu-id="4c605-158">You can also use the `+` operator for string concatenation and delegate combination.</span></span> <span data-ttu-id="4c605-159">Aby uzyskać więcej informacji, zobacz artykuł [ `+` i `+=` operatorów.](addition-operator.md)</span><span class="sxs-lookup"><span data-stu-id="4c605-159">For more information, see the [`+` and `+=` operators](addition-operator.md) article.</span></span>

## <a name="subtraction-operator--"></a><span data-ttu-id="4c605-160">Operator odejmowania -</span><span class="sxs-lookup"><span data-stu-id="4c605-160">Subtraction operator -</span></span>

<span data-ttu-id="4c605-161">Operator odejmowania `-` odejmuje jego prawej opery od jego lewej operndu:</span><span class="sxs-lookup"><span data-stu-id="4c605-161">The subtraction operator `-` subtracts its right-hand operand from its left-hand operand:</span></span>

[!code-csharp-interactive[subtraction operator](snippets/ArithmeticOperators.cs#Subtraction)]

<span data-ttu-id="4c605-162">Można również użyć `-` operatora do usuwania delegatów.</span><span class="sxs-lookup"><span data-stu-id="4c605-162">You can also use the `-` operator for delegate removal.</span></span> <span data-ttu-id="4c605-163">Aby uzyskać więcej informacji, zobacz artykuł [ `-` i `-=` operatorów.](subtraction-operator.md)</span><span class="sxs-lookup"><span data-stu-id="4c605-163">For more information, see the [`-` and `-=` operators](subtraction-operator.md) article.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="4c605-164">Przypisanie złożone</span><span class="sxs-lookup"><span data-stu-id="4c605-164">Compound assignment</span></span>

<span data-ttu-id="4c605-165">Dla operatora `op`binarnego wyrażenie przypisania złożonego formularza</span><span class="sxs-lookup"><span data-stu-id="4c605-165">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="4c605-166">jest równoważny</span><span class="sxs-lookup"><span data-stu-id="4c605-166">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="4c605-167">z `x` tą różnicą, że jest oceniana tylko raz.</span><span class="sxs-lookup"><span data-stu-id="4c605-167">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="4c605-168">Poniższy przykład pokazuje użycie przypisania złożonego z operatorami arytmetycznymi:</span><span class="sxs-lookup"><span data-stu-id="4c605-168">The following example demonstrates the usage of compound assignment with arithmetic operators:</span></span>

[!code-csharp-interactive[compound assignment](snippets/ArithmeticOperators.cs#CompoundAssignment)]

<span data-ttu-id="4c605-169">Ze względu na [promocje numeryczne](~/_csharplang/spec/expressions.md#numeric-promotions)wynik `op` operacji może nie być `T` niejawnie wymienialny na typ `x`.</span><span class="sxs-lookup"><span data-stu-id="4c605-169">Because of [numeric promotions](~/_csharplang/spec/expressions.md#numeric-promotions), the result of the `op` operation might be not implicitly convertible to the type `T` of `x`.</span></span> <span data-ttu-id="4c605-170">W takim przypadku, `op` jeśli jest wstępnie zdefiniowanym operatorem, a wynik operacji jest `T` `x`jawnie wymienialny na `x op= y` typ , `x = (T)(x op y)`wyrażenie `x` przypisania złożonego formularza jest równoważne , z tą różnicą, że jest oceniane tylko raz.</span><span class="sxs-lookup"><span data-stu-id="4c605-170">In such a case, if `op` is a predefined operator and the result of the operation is explicitly convertible to the type `T` of `x`, a compound assignment expression of the form `x op= y` is equivalent to `x = (T)(x op y)`, except that `x` is only evaluated once.</span></span> <span data-ttu-id="4c605-171">Poniższy przykład pokazuje, że zachowanie:</span><span class="sxs-lookup"><span data-stu-id="4c605-171">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[compound assignment with cast](snippets/ArithmeticOperators.cs#CompoundAssignmentWithCast)]

<span data-ttu-id="4c605-172">Operatory `+=` i `-=` operatorzy również subskrybują i wypisują się z [wydarzenia,](../keywords/event.md)odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="4c605-172">You also use the `+=` and `-=` operators to subscribe to and unsubscribe from an [event](../keywords/event.md), respectively.</span></span> <span data-ttu-id="4c605-173">Aby uzyskać więcej informacji, zobacz [Jak subskrybować wydarzenia i anulować subskrypcję .](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)</span><span class="sxs-lookup"><span data-stu-id="4c605-173">For more information, see [How to subscribe to and unsubscribe from events](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="operator-precedence-and-associativity"></a><span data-ttu-id="4c605-174">Pierwszeństwo i zespolenie operatora</span><span class="sxs-lookup"><span data-stu-id="4c605-174">Operator precedence and associativity</span></span>

<span data-ttu-id="4c605-175">Następująca lista porządkuuje operatorów arytmetycznych, począwszy od najwyższego pierwszeństwa do najniższego:</span><span class="sxs-lookup"><span data-stu-id="4c605-175">The following list orders arithmetic operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="4c605-176">Operatory przyrostu `x++` i zmniejszania `x--` poprawek</span><span class="sxs-lookup"><span data-stu-id="4c605-176">Postfix increment `x++` and decrement `x--` operators</span></span>
- <span data-ttu-id="4c605-177">`++x` Przyrost prefiksu i `--x` dekrementacji i unary `+` i `-` operatorów</span><span class="sxs-lookup"><span data-stu-id="4c605-177">Prefix increment `++x` and decrement `--x` and unary `+` and `-` operators</span></span>
- <span data-ttu-id="4c605-178">`*`Mnożenie `/`i `%` operatory</span><span class="sxs-lookup"><span data-stu-id="4c605-178">Multiplicative `*`, `/`, and `%` operators</span></span>
- <span data-ttu-id="4c605-179">Dodatki `+` `-` i podmioty gospodarcze</span><span class="sxs-lookup"><span data-stu-id="4c605-179">Additive `+` and `-` operators</span></span>

<span data-ttu-id="4c605-180">Operatory arytmetyczne binarne są lewozespole.</span><span class="sxs-lookup"><span data-stu-id="4c605-180">Binary arithmetic operators are left-associative.</span></span> <span data-ttu-id="4c605-181">Oznacza to, że operatory o tym samym poziomie pierwszeństwa są oceniane od lewej do prawej.</span><span class="sxs-lookup"><span data-stu-id="4c605-181">That is, operators with the same precedence level are evaluated from left to right.</span></span>

<span data-ttu-id="4c605-182">Użyj nawiasów, `()`aby zmienić kolejność oceny narzuconą przez pierwszeństwo operatora i zespolenie.</span><span class="sxs-lookup"><span data-stu-id="4c605-182">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence and associativity.</span></span>

[!code-csharp-interactive[precedence and associativity](snippets/ArithmeticOperators.cs#PrecedenceAndAssociativity)]

<span data-ttu-id="4c605-183">Aby uzyskać pełną listę operatorów języka C# uporządkowanych według poziomu [pierwszeństwa, zobacz sekcję pierwszeństwo operatora](index.md#operator-precedence) w artykule [Operatory języka C#.](index.md)</span><span class="sxs-lookup"><span data-stu-id="4c605-183">For the complete list of C# operators ordered by precedence level, see the [Operator precedence](index.md#operator-precedence) section of the [C# operators](index.md) article.</span></span>

## <a name="arithmetic-overflow-and-division-by-zero"></a><span data-ttu-id="4c605-184">Przepełnienie i podział arytmetyczny przez zero</span><span class="sxs-lookup"><span data-stu-id="4c605-184">Arithmetic overflow and division by zero</span></span>

<span data-ttu-id="4c605-185">Gdy wynik operacji arytmetycznej znajduje się poza zakresem możliwych wartości skończonych danego typu liczbowego, zachowanie operatora arytmetycznego zależy od typu jego argumentów.</span><span class="sxs-lookup"><span data-stu-id="4c605-185">When the result of an arithmetic operation is outside the range of possible finite values of the involved numeric type, the behavior of an arithmetic operator depends on the type of its operands.</span></span>

### <a name="integer-arithmetic-overflow"></a><span data-ttu-id="4c605-186">Przepełnienie arytmetyczne liczby całkowitej</span><span class="sxs-lookup"><span data-stu-id="4c605-186">Integer arithmetic overflow</span></span>

<span data-ttu-id="4c605-187">Podział liczby całkowitej przez zero <xref:System.DivideByZeroException>zawsze rzuca .</span><span class="sxs-lookup"><span data-stu-id="4c605-187">Integer division by zero always throws a <xref:System.DivideByZeroException>.</span></span>

<span data-ttu-id="4c605-188">W przypadku przepełnienia arytmetycznego liczby całkowitej kontekst sprawdzania przepełnienia, który można [sprawdzić lub odeszło od zaznaczenia,](../keywords/checked-and-unchecked.md)kontroluje wynikowe zachowanie:</span><span class="sxs-lookup"><span data-stu-id="4c605-188">In case of integer arithmetic overflow, an overflow checking context, which can be [checked or unchecked](../keywords/checked-and-unchecked.md), controls the resulting behavior:</span></span>

- <span data-ttu-id="4c605-189">W sprawdzonym kontekście, jeśli przepełnienie odbywa się w wyrażeniu stałym, występuje błąd w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="4c605-189">In a checked context, if overflow happens in a constant expression, a compile-time error occurs.</span></span> <span data-ttu-id="4c605-190">W przeciwnym razie, gdy operacja jest <xref:System.OverflowException> wykonywana w czasie wykonywania, jest generowany.</span><span class="sxs-lookup"><span data-stu-id="4c605-190">Otherwise, when the operation is performed at run time, an <xref:System.OverflowException> is thrown.</span></span>
- <span data-ttu-id="4c605-191">W kontekście niezaznaczone wynik jest obcinana przez odrzucenie bitów wysokiego rzędu, które nie mieszczą się w typie docelowym.</span><span class="sxs-lookup"><span data-stu-id="4c605-191">In an unchecked context, the result is truncated by discarding any high-order bits that don't fit in the destination type.</span></span>

<span data-ttu-id="4c605-192">Wraz z [zaznaczonych i niesprawdzonych](../keywords/checked-and-unchecked.md) instrukcji, można użyć `checked` i `unchecked` operatorów do kontrolowania kontekstu sprawdzania przepełnienia, w którym wyrażenie jest oceniane:</span><span class="sxs-lookup"><span data-stu-id="4c605-192">Along with the [checked and unchecked](../keywords/checked-and-unchecked.md) statements, you can use the `checked` and `unchecked` operators to control the overflow checking context, in which an expression is evaluated:</span></span>

[!code-csharp-interactive[checked and unchecked](snippets/ArithmeticOperators.cs#CheckedUnchecked)]

<span data-ttu-id="4c605-193">Domyślnie operacje arytmetyczne występują w *niezaznaczone kontekście.*</span><span class="sxs-lookup"><span data-stu-id="4c605-193">By default, arithmetic operations occur in an *unchecked* context.</span></span>

### <a name="floating-point-arithmetic-overflow"></a><span data-ttu-id="4c605-194">Przepełnienie arytmetyczne zmiennoprzecinające</span><span class="sxs-lookup"><span data-stu-id="4c605-194">Floating-point arithmetic overflow</span></span>

<span data-ttu-id="4c605-195">Operacje arytmetyczne `float` z `double` i typów nigdy nie zgłaszać wyjątek.</span><span class="sxs-lookup"><span data-stu-id="4c605-195">Arithmetic operations with the `float` and `double` types never throw an exception.</span></span> <span data-ttu-id="4c605-196">Wynik operacji arytmetycznych z tymi typami może być jedną ze specjalnych wartości, które reprezentują nieskończoność i nie-liczbę:</span><span class="sxs-lookup"><span data-stu-id="4c605-196">The result of arithmetic operations with those types can be one of special values that represent infinity and not-a-number:</span></span>

[!code-csharp-interactive[double non-finite values](snippets/ArithmeticOperators.cs#FloatingPointOverflow)]

<span data-ttu-id="4c605-197">Dla operandów `decimal` typu przepełnienie arytmetyczne zawsze <xref:System.OverflowException> rzuca i dzielenie przez <xref:System.DivideByZeroException>zero zawsze rzuca .</span><span class="sxs-lookup"><span data-stu-id="4c605-197">For the operands of the `decimal` type, arithmetic overflow always throws an <xref:System.OverflowException> and division by zero always throws a <xref:System.DivideByZeroException>.</span></span>

## <a name="round-off-errors"></a><span data-ttu-id="4c605-198">Błędy zaokrąglania</span><span class="sxs-lookup"><span data-stu-id="4c605-198">Round-off errors</span></span>

<span data-ttu-id="4c605-199">Ze względu na ogólne ograniczenia zmiennoprzecinkową reprezentacji liczb rzeczywistych i arytmetyki zmiennoprzecinkowej błędy zaokrąglania mogą wystąpić w obliczeniach z typami zmiennoprzecinkowymi.</span><span class="sxs-lookup"><span data-stu-id="4c605-199">Because of general limitations of the floating-point representation of real numbers and floating-point arithmetic, round-off errors might occur in calculations with floating-point types.</span></span> <span data-ttu-id="4c605-200">Oznacza to, że wynik wytworzyny wyrażenia może różnić się od oczekiwanego wyniku matematycznego.</span><span class="sxs-lookup"><span data-stu-id="4c605-200">That is, the produced result of an expression might differ from the expected mathematical result.</span></span> <span data-ttu-id="4c605-201">Poniższy przykład pokazuje kilka takich przypadków:</span><span class="sxs-lookup"><span data-stu-id="4c605-201">The following example demonstrates several such cases:</span></span>

[!code-csharp-interactive[round-off errors](snippets/ArithmeticOperators.cs#RoundOffErrors)]

<span data-ttu-id="4c605-202">Aby uzyskać więcej informacji, zobacz uwagi na [stronach System.Double](/dotnet/api/system.double#remarks), [System.Single](/dotnet/api/system.single#remarks)lub [System.Decimal.](/dotnet/api/system.decimal#remarks)</span><span class="sxs-lookup"><span data-stu-id="4c605-202">For more information, see remarks at the [System.Double](/dotnet/api/system.double#remarks), [System.Single](/dotnet/api/system.single#remarks), or [System.Decimal](/dotnet/api/system.decimal#remarks) reference pages.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="4c605-203">Przeciążenie operatora</span><span class="sxs-lookup"><span data-stu-id="4c605-203">Operator overloadability</span></span>

<span data-ttu-id="4c605-204">Typ zdefiniowany przez użytkownika może [przeciążać](operator-overloading.md) operatory arytmetyczne dwuarchikę (`++`, `--` `+` `-`, , i ) i binarne (`*` `/`, `%`, `+`, i `-`) .</span><span class="sxs-lookup"><span data-stu-id="4c605-204">A user-defined type can [overload](operator-overloading.md) the unary (`++`, `--`, `+`, and `-`) and binary (`*`, `/`, `%`, `+`, and `-`) arithmetic operators.</span></span> <span data-ttu-id="4c605-205">Gdy operator binarny jest przeciążony, odpowiedni operator przypisania złożonego jest również niejawnie przeciążony.</span><span class="sxs-lookup"><span data-stu-id="4c605-205">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="4c605-206">Typ zdefiniowany przez użytkownika nie może jawnie przeciążać operatora przypisania złożonego.</span><span class="sxs-lookup"><span data-stu-id="4c605-206">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="4c605-207">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="4c605-207">C# language specification</span></span>

<span data-ttu-id="4c605-208">Aby uzyskać więcej informacji, zobacz następujące sekcje [specyfikacji języka języka C#:](~/_csharplang/spec/introduction.md)</span><span class="sxs-lookup"><span data-stu-id="4c605-208">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="4c605-209">Operatory przyrostu i zmniejszania poprawek</span><span class="sxs-lookup"><span data-stu-id="4c605-209">Postfix increment and decrement operators</span></span>](~/_csharplang/spec/expressions.md#postfix-increment-and-decrement-operators)
- [<span data-ttu-id="4c605-210">Operatory przyrostu i zmniejszania prefiksów</span><span class="sxs-lookup"><span data-stu-id="4c605-210">Prefix increment and decrement operators</span></span>](~/_csharplang/spec/expressions.md#prefix-increment-and-decrement-operators)
- [<span data-ttu-id="4c605-211">Operator Unary plus</span><span class="sxs-lookup"><span data-stu-id="4c605-211">Unary plus operator</span></span>](~/_csharplang/spec/expressions.md#unary-plus-operator)
- [<span data-ttu-id="4c605-212">Operator unary minus</span><span class="sxs-lookup"><span data-stu-id="4c605-212">Unary minus operator</span></span>](~/_csharplang/spec/expressions.md#unary-minus-operator)
- [<span data-ttu-id="4c605-213">Operator mnożenia</span><span class="sxs-lookup"><span data-stu-id="4c605-213">Multiplication operator</span></span>](~/_csharplang/spec/expressions.md#multiplication-operator)
- [<span data-ttu-id="4c605-214">Operator działu</span><span class="sxs-lookup"><span data-stu-id="4c605-214">Division operator</span></span>](~/_csharplang/spec/expressions.md#division-operator)
- [<span data-ttu-id="4c605-215">Operator pozostałej części</span><span class="sxs-lookup"><span data-stu-id="4c605-215">Remainder operator</span></span>](~/_csharplang/spec/expressions.md#remainder-operator)
- [<span data-ttu-id="4c605-216">Operator dodawania</span><span class="sxs-lookup"><span data-stu-id="4c605-216">Addition operator</span></span>](~/_csharplang/spec/expressions.md#addition-operator)
- [<span data-ttu-id="4c605-217">Operator odejmowania</span><span class="sxs-lookup"><span data-stu-id="4c605-217">Subtraction operator</span></span>](~/_csharplang/spec/expressions.md#subtraction-operator)
- [<span data-ttu-id="4c605-218">Przypisanie złożone</span><span class="sxs-lookup"><span data-stu-id="4c605-218">Compound assignment</span></span>](~/_csharplang/spec/expressions.md#compound-assignment)
- [<span data-ttu-id="4c605-219">Sprawdzone i niesprawdzone operatory</span><span class="sxs-lookup"><span data-stu-id="4c605-219">The checked and unchecked operators</span></span>](~/_csharplang/spec/expressions.md#the-checked-and-unchecked-operators)
- [<span data-ttu-id="4c605-220">Promocje numeryczne</span><span class="sxs-lookup"><span data-stu-id="4c605-220">Numeric promotions</span></span>](~/_csharplang/spec/expressions.md#numeric-promotions)

## <a name="see-also"></a><span data-ttu-id="4c605-221">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4c605-221">See also</span></span>

- [<span data-ttu-id="4c605-222">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="4c605-222">C# reference</span></span>](../index.md)
- [<span data-ttu-id="4c605-223">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="4c605-223">C# operators</span></span>](index.md)
- <xref:System.Math?displayProperty=nameWithType>
- <xref:System.MathF?displayProperty=nameWithType>
- [<span data-ttu-id="4c605-224">Wartości numeryczne na platformie .NET</span><span class="sxs-lookup"><span data-stu-id="4c605-224">Numerics in .NET</span></span>](../../../standard/numerics.md)
