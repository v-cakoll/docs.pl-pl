---
title: Operatory arytmetyczne C# — odwołanie
description: Dowiedz C# się więcej na temat operatorów, które wykonują operacje mnożenia, dzielenia, reszty, dodawania i odejmowania z typami liczbowymi.
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
ms.openlocfilehash: ac04ba72ed0c25aa576bf10150fc80410890eda0
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69608367"
---
# <a name="arithmetic-operators-c-reference"></a><span data-ttu-id="b18bb-103">Operatory arytmetyczneC# (odwołanie)</span><span class="sxs-lookup"><span data-stu-id="b18bb-103">Arithmetic operators (C# reference)</span></span>

<span data-ttu-id="b18bb-104">Następujące operatory wykonują operacje arytmetyczne z typami liczbowymi:</span><span class="sxs-lookup"><span data-stu-id="b18bb-104">The following operators perform arithmetic operations with numeric types:</span></span>

- <span data-ttu-id="b18bb-105">Operatory jednoargumentowe [ `--` ](#decrement-operator---) [ `++` (przyrostowe)](#increment-operator-), (zmniejszanie), [ `+` (plus)](#unary-plus-and-minus-operators)i [ `-` (minus)](#unary-plus-and-minus-operators)</span><span class="sxs-lookup"><span data-stu-id="b18bb-105">Unary [`++` (increment)](#increment-operator-), [`--` (decrement)](#decrement-operator---), [`+` (plus)](#unary-plus-and-minus-operators), and [`-` (minus)](#unary-plus-and-minus-operators) operators</span></span>
- <span data-ttu-id="b18bb-106">Operatory [ `*` binarne (mnożenie)](#multiplication-operator-) [ `/` , (dzielenie)](#division-operator-), [ `%` (reszta)](#remainder-operator-), [ `+` (Dodawanie)](#addition-operator-)i [ `-` (Odejmowanie)](#subtraction-operator--)</span><span class="sxs-lookup"><span data-stu-id="b18bb-106">Binary [`*` (multiplication)](#multiplication-operator-), [`/` (division)](#division-operator-), [`%` (remainder)](#remainder-operator-), [`+` (addition)](#addition-operator-), and [`-` (subtraction)](#subtraction-operator--) operators</span></span>

<span data-ttu-id="b18bb-107">Te operatory obsługują wszystkie typy liczbowe [całkowite](../builtin-types/integral-numeric-types.md) i [zmiennoprzecinkowe](../builtin-types/floating-point-numeric-types.md) .</span><span class="sxs-lookup"><span data-stu-id="b18bb-107">Those operators support all [integral](../builtin-types/integral-numeric-types.md) and [floating-point](../builtin-types/floating-point-numeric-types.md) numeric types.</span></span>

## <a name="increment-operator-"></a><span data-ttu-id="b18bb-108">Increment — operator + +</span><span class="sxs-lookup"><span data-stu-id="b18bb-108">Increment operator ++</span></span>

<span data-ttu-id="b18bb-109">Jednoargumentowy operator `++` przyrostu zwiększa jego operand o 1.</span><span class="sxs-lookup"><span data-stu-id="b18bb-109">The unary increment operator `++` increments its operand by 1.</span></span> <span data-ttu-id="b18bb-110">Operand musi być zmienną, dostępem do [Właściwości](../../programming-guide/classes-and-structs/properties.md) lub dostępem indeksatora. [](../../programming-guide/indexers/index.md)</span><span class="sxs-lookup"><span data-stu-id="b18bb-110">The operand must be a variable, a [property](../../programming-guide/classes-and-structs/properties.md) access, or an [indexer](../../programming-guide/indexers/index.md) access.</span></span>

<span data-ttu-id="b18bb-111">Operator przyrostu jest obsługiwany w dwóch formach: Przyrostkowy operator `x++`przyrostu, i `++x`operator przyrostu wartości prefiksu.</span><span class="sxs-lookup"><span data-stu-id="b18bb-111">The increment operator is supported in two forms: the postfix increment operator, `x++`, and the prefix increment operator, `++x`.</span></span>

### <a name="postfix-increment-operator"></a><span data-ttu-id="b18bb-112">Operator inkrementacji przyrostkowej</span><span class="sxs-lookup"><span data-stu-id="b18bb-112">Postfix increment operator</span></span>

<span data-ttu-id="b18bb-113">Wynik `x++` jest *wartością przed* operacją, jak pokazano w poniższym przykładzie: `x`</span><span class="sxs-lookup"><span data-stu-id="b18bb-113">The result of `x++` is the value of `x` *before* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[postfix increment](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#PostfixIncrement)]

### <a name="prefix-increment-operator"></a><span data-ttu-id="b18bb-114">Operator przyrostu prefiksu</span><span class="sxs-lookup"><span data-stu-id="b18bb-114">Prefix increment operator</span></span>

<span data-ttu-id="b18bb-115">Wynik `++x` jest *wartością po* operacji, jak pokazano w poniższym przykładzie: `x`</span><span class="sxs-lookup"><span data-stu-id="b18bb-115">The result of `++x` is the value of `x` *after* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[prefix increment](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#PrefixIncrement)]

## <a name="decrement-operator---"></a><span data-ttu-id="b18bb-116">Zmniejsz operator--</span><span class="sxs-lookup"><span data-stu-id="b18bb-116">Decrement operator --</span></span>

<span data-ttu-id="b18bb-117">Operator `--` zmniejszania jednoargumentowego zmniejsza jego operand o 1.</span><span class="sxs-lookup"><span data-stu-id="b18bb-117">The unary decrement operator `--` decrements its operand by 1.</span></span> <span data-ttu-id="b18bb-118">Operand musi być zmienną, dostępem do [Właściwości](../../programming-guide/classes-and-structs/properties.md) lub dostępem indeksatora. [](../../programming-guide/indexers/index.md)</span><span class="sxs-lookup"><span data-stu-id="b18bb-118">The operand must be a variable, a [property](../../programming-guide/classes-and-structs/properties.md) access, or an [indexer](../../programming-guide/indexers/index.md) access.</span></span>

<span data-ttu-id="b18bb-119">Operator zmniejszania jest obsługiwany w dwóch formach: operator zmniejszania przyrostu, `x--`i `--x`operator zmniejszania prefiksu.</span><span class="sxs-lookup"><span data-stu-id="b18bb-119">The decrement operator is supported in two forms: the postfix decrement operator, `x--`, and the prefix decrement operator, `--x`.</span></span>

### <a name="postfix-decrement-operator"></a><span data-ttu-id="b18bb-120">Operator dekrementacji przyrostkowej</span><span class="sxs-lookup"><span data-stu-id="b18bb-120">Postfix decrement operator</span></span>

<span data-ttu-id="b18bb-121">Wynik `x--` jest *wartością przed* operacją, jak pokazano w poniższym przykładzie: `x`</span><span class="sxs-lookup"><span data-stu-id="b18bb-121">The result of `x--` is the value of `x` *before* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[postfix decrement](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#PostfixDecrement)]

### <a name="prefix-decrement-operator"></a><span data-ttu-id="b18bb-122">Operator zmniejszania prefiksu</span><span class="sxs-lookup"><span data-stu-id="b18bb-122">Prefix decrement operator</span></span>

<span data-ttu-id="b18bb-123">Wynik `--x` jest *wartością po* operacji, jak pokazano w poniższym przykładzie: `x`</span><span class="sxs-lookup"><span data-stu-id="b18bb-123">The result of `--x` is the value of `x` *after* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[prefix decrement](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#PrefixDecrement)]

## <a name="unary-plus-and-minus-operators"></a><span data-ttu-id="b18bb-124">Operatory jednoargumentowe Plus i minus</span><span class="sxs-lookup"><span data-stu-id="b18bb-124">Unary plus and minus operators</span></span>

<span data-ttu-id="b18bb-125">Operator jednoargumentowy `+` zwraca wartość jego operandu.</span><span class="sxs-lookup"><span data-stu-id="b18bb-125">The unary `+` operator returns the value of its operand.</span></span> <span data-ttu-id="b18bb-126">Operator jednoargumentowy `-` oblicza liczbę negacji operandu.</span><span class="sxs-lookup"><span data-stu-id="b18bb-126">The unary `-` operator computes the numeric negation of its operand.</span></span>

[!code-csharp-interactive[unary plus and minus](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#UnaryPlusAndMinus)]

<span data-ttu-id="b18bb-127">Operator jednoargumentowy `-` nie obsługuje typu [ULONG](../builtin-types/integral-numeric-types.md) .</span><span class="sxs-lookup"><span data-stu-id="b18bb-127">The unary `-` operator doesn't support the [ulong](../builtin-types/integral-numeric-types.md) type.</span></span>

## <a name="multiplication-operator-"></a><span data-ttu-id="b18bb-128">Operator mnożenia \*</span><span class="sxs-lookup"><span data-stu-id="b18bb-128">Multiplication operator \*</span></span>

<span data-ttu-id="b18bb-129">Operator `*` mnożenia Oblicza iloczyn argumentów operacji:</span><span class="sxs-lookup"><span data-stu-id="b18bb-129">The multiplication operator `*` computes the product of its operands:</span></span>

[!code-csharp-interactive[multiplication operator](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#Multiplication)]

<span data-ttu-id="b18bb-130">Operator jednoargumentowy `*` jest [operatorem pośredni wskaźnika](pointer-related-operators.md#pointer-indirection-operator-).</span><span class="sxs-lookup"><span data-stu-id="b18bb-130">The unary `*` operator is the [pointer indirection operator](pointer-related-operators.md#pointer-indirection-operator-).</span></span>

## <a name="division-operator-"></a><span data-ttu-id="b18bb-131">Operator dzielenia/</span><span class="sxs-lookup"><span data-stu-id="b18bb-131">Division operator /</span></span>

<span data-ttu-id="b18bb-132">Operator `/` dzielenia dzieli swój operand z lewej strony przez jego operand po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="b18bb-132">The division operator `/` divides its left-hand operand by its right-hand operand.</span></span>

### <a name="integer-division"></a><span data-ttu-id="b18bb-133">Dzielenie liczb całkowitych</span><span class="sxs-lookup"><span data-stu-id="b18bb-133">Integer division</span></span>

<span data-ttu-id="b18bb-134">Dla argumentów operacji typu Integer wynik `/` operatora jest typu integer i jest równy ilorazowi dwóch operandów zaokrąglonych na zero:</span><span class="sxs-lookup"><span data-stu-id="b18bb-134">For the operands of integer types, the result of the `/` operator is of an integer type and equals the quotient of the two operands rounded towards zero:</span></span>

[!code-csharp-interactive[integer division](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#IntegerDivision)]

<span data-ttu-id="b18bb-135">Aby uzyskać iloraz dwóch operandów jako liczby zmiennoprzecinkowej, użyj `float`typu, `double`, lub `decimal` :</span><span class="sxs-lookup"><span data-stu-id="b18bb-135">To obtain the quotient of the two operands as a floating-point number, use the `float`, `double`, or `decimal` type:</span></span>

[!code-csharp-interactive[integer as floating-point division](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#IntegerAsFloatingPointDivision)]

### <a name="floating-point-division"></a><span data-ttu-id="b18bb-136">Dzielenie zmiennoprzecinkowe</span><span class="sxs-lookup"><span data-stu-id="b18bb-136">Floating-point division</span></span>

<span data-ttu-id="b18bb-137">W przypadku typów `double` `decimal` , i, wynik `/` operatora jest ilorazem dwóch operandów: `float`</span><span class="sxs-lookup"><span data-stu-id="b18bb-137">For the `float`, `double`, and `decimal` types, the result of the `/` operator is the quotient of the two operands:</span></span>

[!code-csharp-interactive[floating-point division](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#FloatingPointDivision)]

<span data-ttu-id="b18bb-138">Jeśli `decimal`jeden z operandów to, inny operand nie może `float` być `double`ani, ponieważ `float` `double` ani nie jest niejawnie konwertowany na `decimal`.</span><span class="sxs-lookup"><span data-stu-id="b18bb-138">If one of the operands is `decimal`, another operand can be neither `float` nor `double`, because neither `float` nor `double` is implicitly convertible to `decimal`.</span></span> <span data-ttu-id="b18bb-139">Należy jawnie skonwertować `float` operand or `double` na `decimal` typ.</span><span class="sxs-lookup"><span data-stu-id="b18bb-139">You must explicitly convert the `float` or `double` operand to the `decimal` type.</span></span> <span data-ttu-id="b18bb-140">Aby uzyskać więcej informacji na temat niejawnych konwersji między typami numerycznymi, zobacz [tabela niejawnych konwersji liczbowych](../keywords/implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="b18bb-140">For more information about implicit conversions between numeric types, see [Implicit numeric conversions table](../keywords/implicit-numeric-conversions-table.md).</span></span>

## <a name="remainder-operator-"></a><span data-ttu-id="b18bb-141">Procent pozostałej części</span><span class="sxs-lookup"><span data-stu-id="b18bb-141">Remainder operator %</span></span>

<span data-ttu-id="b18bb-142">Operator `%` reszty oblicza resztę po podzieleniu operandu po lewej stronie przez jego operand po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="b18bb-142">The remainder operator `%` computes the remainder after dividing its left-hand operand by its right-hand operand.</span></span>

### <a name="integer-remainder"></a><span data-ttu-id="b18bb-143">Reszta całkowita</span><span class="sxs-lookup"><span data-stu-id="b18bb-143">Integer remainder</span></span>
  
<span data-ttu-id="b18bb-144">W przypadku operandów typu Integer wynik `a % b` jest wartością wygenerowaną przez. `a - (a / b) * b`</span><span class="sxs-lookup"><span data-stu-id="b18bb-144">For the operands of integer types, the result of `a % b` is the value produced by `a - (a / b) * b`.</span></span> <span data-ttu-id="b18bb-145">Znak niezerowej reszty jest taki sam jak w przypadku operandu po lewej stronie, jak pokazano na poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="b18bb-145">The sign of the non-zero remainder is the same as that of the left-hand operand, as the following example shows:</span></span>

[!code-csharp-interactive[integer remainder](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#IntegerRemainder)]

<span data-ttu-id="b18bb-146">Użyj metody <xref:System.Math.DivRem%2A?displayProperty=nameWithType> , aby obliczyć podział liczby całkowitej i reszty.</span><span class="sxs-lookup"><span data-stu-id="b18bb-146">Use the <xref:System.Math.DivRem%2A?displayProperty=nameWithType> method to compute both integer division and remainder results.</span></span>

### <a name="floating-point-remainder"></a><span data-ttu-id="b18bb-147">Pozostała część zmiennoprzecinkowa</span><span class="sxs-lookup"><span data-stu-id="b18bb-147">Floating-point remainder</span></span>

<span data-ttu-id="b18bb-148">`double` `y` `z` Dla argumentów `x % y` i, wynik dla wartości skończone `x` i jest wartością taką jak `float`</span><span class="sxs-lookup"><span data-stu-id="b18bb-148">For the `float` and `double` operands, the result of `x % y` for the finite `x` and `y` is the value `z` such that</span></span>

- <span data-ttu-id="b18bb-149">Znak `z`, jeśli wartość niezerowa, jest taki sam jak `x`znak.</span><span class="sxs-lookup"><span data-stu-id="b18bb-149">The sign of `z`, if non-zero, is the same as the sign of `x`.</span></span>
- <span data-ttu-id="b18bb-150">`z` Wartość bezwzględna jest wartością wygenerowaną, `|x| - n * |y|` gdzie `n` jest największą możliwą `|x| / |y|` liczbą całkowitą, która `|y|` jest mniejsza lub równa `|x|` i jest wartościami bezwzględnymi `x` z i `y`odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="b18bb-150">The absolute value of `z` is the value produced by `|x| - n * |y|` where `n` is the largest possible integer that is less than or equal to `|x| / |y|` and `|x|` and `|y|` are the absolute values of `x` and `y`, respectively.</span></span>

> [!NOTE]
> <span data-ttu-id="b18bb-151">Ta metoda przetwarzania reszty jest analogiczna do tego, który jest używany dla argumentów wartości całkowitych, ale różni się od IEEE 754.</span><span class="sxs-lookup"><span data-stu-id="b18bb-151">This method of computing the remainder is analogous to that used for integer operands, but differs from the IEEE 754.</span></span> <span data-ttu-id="b18bb-152">Jeśli potrzebujesz pozostałej operacji, która jest zgodna z IEEE 754, użyj <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="b18bb-152">If you need the remainder operation that complies with the IEEE 754, use the <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="b18bb-153">Aby uzyskać informacje o zachowaniu `%` operatora z nieskończone operandów, zobacz sekcję [operator reszty](~/_csharplang/spec/expressions.md#remainder-operator) w [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="b18bb-153">For information about the behavior of the `%` operator with non-finite operands, see the [Remainder operator](~/_csharplang/spec/expressions.md#remainder-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="b18bb-154">Dla operandów operator `%` reszty jest równoważny <xref:System.Decimal?displayProperty=nameWithType> operatorowi reszty typu. [](<xref:System.Decimal.op_Modulus(System.Decimal,System.Decimal)>) `decimal`</span><span class="sxs-lookup"><span data-stu-id="b18bb-154">For the `decimal` operands, the remainder operator `%` is equivalent to the [remainder operator](<xref:System.Decimal.op_Modulus(System.Decimal,System.Decimal)>) of the <xref:System.Decimal?displayProperty=nameWithType> type.</span></span>

<span data-ttu-id="b18bb-155">Poniższy przykład demonstruje zachowanie operatora reszty z argumentami operacji zmiennoprzecinkowych:</span><span class="sxs-lookup"><span data-stu-id="b18bb-155">The following example demonstrates the behavior of the remainder operator with floating-point operands:</span></span>

[!code-csharp-interactive[floating-point remainder](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#FloatingPointRemainder)]

## <a name="addition-operator-"></a><span data-ttu-id="b18bb-156">Operator dodawania +</span><span class="sxs-lookup"><span data-stu-id="b18bb-156">Addition operator +</span></span>

<span data-ttu-id="b18bb-157">Operator `+` dodawania oblicza sumę argumentów operacji:</span><span class="sxs-lookup"><span data-stu-id="b18bb-157">The addition operator `+` computes the sum of its operands:</span></span>

[!code-csharp-interactive[addition operator](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#Addition)]

<span data-ttu-id="b18bb-158">Można też użyć `+` operatora do łączenia ciągów i delegatów.</span><span class="sxs-lookup"><span data-stu-id="b18bb-158">You also can use the `+` operator for string concatenation and delegate combination.</span></span> <span data-ttu-id="b18bb-159">Aby uzyskać więcej informacji, zobacz [ `+` artykuł `+=` operatory i](addition-operator.md) .</span><span class="sxs-lookup"><span data-stu-id="b18bb-159">For more information, see the [`+` and `+=` operators](addition-operator.md) article.</span></span>

## <a name="subtraction-operator--"></a><span data-ttu-id="b18bb-160">Operator odejmowania —</span><span class="sxs-lookup"><span data-stu-id="b18bb-160">Subtraction operator -</span></span>

<span data-ttu-id="b18bb-161">Operator `-` odejmowania odejmuje swój prawy operand od jego operandu po lewej stronie:</span><span class="sxs-lookup"><span data-stu-id="b18bb-161">The subtraction operator `-` subtracts its right-hand operand from its left-hand operand:</span></span>

[!code-csharp-interactive[subtraction operator](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#Subtraction)]

<span data-ttu-id="b18bb-162">Można też użyć `-` operatora do usuwania delegatów.</span><span class="sxs-lookup"><span data-stu-id="b18bb-162">You also can use the `-` operator for delegate removal.</span></span> <span data-ttu-id="b18bb-163">Aby uzyskać więcej informacji, zobacz [ `-` ](subtraction-operator.md) artykuł dotyczący operatorów.</span><span class="sxs-lookup"><span data-stu-id="b18bb-163">For more information, see the [`-` operator](subtraction-operator.md) article.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="b18bb-164">Przypisanie złożone</span><span class="sxs-lookup"><span data-stu-id="b18bb-164">Compound assignment</span></span>

<span data-ttu-id="b18bb-165">Dla operatora `op`binarnego wyrażenie złożonego przypisania formularza</span><span class="sxs-lookup"><span data-stu-id="b18bb-165">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="b18bb-166">odpowiada wyrażeniu</span><span class="sxs-lookup"><span data-stu-id="b18bb-166">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="b18bb-167">z tą różnicą, że `x` jest obliczany tylko raz.</span><span class="sxs-lookup"><span data-stu-id="b18bb-167">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="b18bb-168">Poniższy przykład ilustruje użycie przypisania złożonego z operatorami arytmetycznymi:</span><span class="sxs-lookup"><span data-stu-id="b18bb-168">The following example demonstrates the usage of compound assignment with arithmetic operators:</span></span>

[!code-csharp-interactive[compound assignment](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#CompoundAssignment)]

<span data-ttu-id="b18bb-169">Ze względu na [promocje liczbowe](~/_csharplang/spec/expressions.md#numeric-promotions)wynik `op` operacji może nie być niejawnie konwertowany `x`na typ `T` .</span><span class="sxs-lookup"><span data-stu-id="b18bb-169">Because of [numeric promotions](~/_csharplang/spec/expressions.md#numeric-promotions), the result of the `op` operation might be not implicitly convertible to the type `T` of `x`.</span></span> <span data-ttu-id="b18bb-170">W takim przypadku, jeśli `op` jest wstępnie zdefiniowanym operatorem, a wynik operacji jest jawnie konwertowany na `x`typ `T` , wyrażenie przypisania złożonego formularza `x op= y` jest równoważne z `x = (T)(x op y)`, z wyjątkiem `x` jest to oceniane tylko raz.</span><span class="sxs-lookup"><span data-stu-id="b18bb-170">In such a case, if `op` is a predefined operator and the result of the operation is explicitly convertible to the type `T` of `x`, a compound assignment expression of the form `x op= y` is equivalent to `x = (T)(x op y)`, except that `x` is only evaluated once.</span></span> <span data-ttu-id="b18bb-171">Poniższy przykład ilustruje takie zachowanie:</span><span class="sxs-lookup"><span data-stu-id="b18bb-171">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[compound assignment with cast](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#CompoundAssignmentWithCast)]

<span data-ttu-id="b18bb-172">Operatory `+=` i `-=` umożliwiają również subskrybowanie i anulowanie subskrypcji [zdarzeń](../keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="b18bb-172">You also use the `+=` and `-=` operators to subscribe to and unsubscribe from [events](../keywords/event.md).</span></span> <span data-ttu-id="b18bb-173">Aby uzyskać więcej informacji, zobacz [How to: subskrybowanie i anulowanie subskrypcji zdarzeń](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="b18bb-173">For more information, see [How to: subscribe to and unsubscribe from events](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="operator-precedence-and-associativity"></a><span data-ttu-id="b18bb-174">Pierwszeństwo operatorów i łączność</span><span class="sxs-lookup"><span data-stu-id="b18bb-174">Operator precedence and associativity</span></span>

<span data-ttu-id="b18bb-175">Na poniższej liście przedstawiono operatory arytmetyczne zaczynające się od najwyższego priorytetu do najniższego:</span><span class="sxs-lookup"><span data-stu-id="b18bb-175">The following list orders arithmetic operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="b18bb-176">Operatory przyrostka `x++` i `x--` zmniejszenie</span><span class="sxs-lookup"><span data-stu-id="b18bb-176">Postfix increment `x++` and decrement `x--` operators</span></span>
- <span data-ttu-id="b18bb-177">Przyrost `++x` i zmniejszenie `--x` prefiksu oraz `+` jednoargumentowe i `-` operatory</span><span class="sxs-lookup"><span data-stu-id="b18bb-177">Prefix increment `++x` and decrement `--x` and unary `+` and `-` operators</span></span>
- <span data-ttu-id="b18bb-178">Mnożenia `*`, `/`, i `%` operatory</span><span class="sxs-lookup"><span data-stu-id="b18bb-178">Multiplicative `*`, `/`, and `%` operators</span></span>
- <span data-ttu-id="b18bb-179">Dodatek `+` i `-` operatory</span><span class="sxs-lookup"><span data-stu-id="b18bb-179">Additive `+` and `-` operators</span></span>

<span data-ttu-id="b18bb-180">Binarne operatory arytmetyczne są z lewej strony skojarzenia.</span><span class="sxs-lookup"><span data-stu-id="b18bb-180">Binary arithmetic operators are left-associative.</span></span> <span data-ttu-id="b18bb-181">Oznacza to, że operatory o tym samym poziomie pierwszeństwa są oceniane od lewej do prawej.</span><span class="sxs-lookup"><span data-stu-id="b18bb-181">That is, operators with the same precedence level are evaluated from left to right.</span></span>

<span data-ttu-id="b18bb-182">Użyj nawiasów, `()`, aby zmienić kolejność oceny nałożona przez pierwszeństwo operatorów i łączność.</span><span class="sxs-lookup"><span data-stu-id="b18bb-182">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence and associativity.</span></span>

[!code-csharp-interactive[precedence and associativity](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#PrecedenceAndAssociativity)]

<span data-ttu-id="b18bb-183">Aby uzyskać pełną listę C# operatorów uporządkowanych według poziomu pierwszeństwa, zobacz [ C# operatory](index.md).</span><span class="sxs-lookup"><span data-stu-id="b18bb-183">For the complete list of C# operators ordered by precedence level, see [C# operators](index.md).</span></span>

## <a name="arithmetic-overflow-and-division-by-zero"></a><span data-ttu-id="b18bb-184">Przepełnienie arytmetyczne i dzielenie przez zero</span><span class="sxs-lookup"><span data-stu-id="b18bb-184">Arithmetic overflow and division by zero</span></span>

<span data-ttu-id="b18bb-185">Gdy wynik operacji arytmetycznej jest poza zakresem możliwych wartości skończonego typu liczbowego, zachowanie operatora arytmetycznego zależy od typu jego operandów.</span><span class="sxs-lookup"><span data-stu-id="b18bb-185">When the result of an arithmetic operation is outside the range of possible finite values of the involved numeric type, the behavior of an arithmetic operator depends on the type of its operands.</span></span>

### <a name="integer-arithmetic-overflow"></a><span data-ttu-id="b18bb-186">Przepełnienie arytmetyczne liczb całkowitych</span><span class="sxs-lookup"><span data-stu-id="b18bb-186">Integer arithmetic overflow</span></span>

<span data-ttu-id="b18bb-187">Dzielenie liczby całkowitej przez zero zawsze zgłasza <xref:System.DivideByZeroException>.</span><span class="sxs-lookup"><span data-stu-id="b18bb-187">Integer division by zero always throws a <xref:System.DivideByZeroException>.</span></span>

<span data-ttu-id="b18bb-188">W przypadku przepełnienia arytmetycznego wartości całkowitych, kontekst sprawdzania przepełnienia, który można [sprawdzić lub nie zaznaczyć](../keywords/checked-and-unchecked.md), kontroluje zachowanie wyników:</span><span class="sxs-lookup"><span data-stu-id="b18bb-188">In case of integer arithmetic overflow, an overflow checking context, which can be [checked or unchecked](../keywords/checked-and-unchecked.md), controls the resulting behavior:</span></span>

- <span data-ttu-id="b18bb-189">Jeśli przepełnienie ma miejsce w wyrażeniu stałym, wystąpi błąd w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="b18bb-189">In a checked context, if overflow happens in a constant expression, a compile-time error occurs.</span></span> <span data-ttu-id="b18bb-190">W przeciwnym razie, gdy operacja zostanie wykonana w czasie wykonywania, <xref:System.OverflowException> zostanie zgłoszony.</span><span class="sxs-lookup"><span data-stu-id="b18bb-190">Otherwise, when the operation is performed at run time, an <xref:System.OverflowException> is thrown.</span></span>
- <span data-ttu-id="b18bb-191">W kontekście niesprawdzonym wynik zostanie obcięty przez odrzucenie wszystkich bitów o dużej kolejności, które nie mieszczą się w typie docelowym.</span><span class="sxs-lookup"><span data-stu-id="b18bb-191">In an unchecked context, the result is truncated by discarding any high-order bits that don't fit in the destination type.</span></span>

<span data-ttu-id="b18bb-192">Wraz z [sprawdzonymi i](../keywords/checked-and-unchecked.md) niesprawdzonymi instrukcjami można użyć `checked` operatorów i `unchecked` , aby kontrolować kontekst sprawdzania przepełnienia, w którym jest oceniane wyrażenie:</span><span class="sxs-lookup"><span data-stu-id="b18bb-192">Along with the [checked and unchecked](../keywords/checked-and-unchecked.md) statements, you can use the `checked` and `unchecked` operators to control the overflow checking context, in which an expression is evaluated:</span></span>

[!code-csharp-interactive[checked and unchecked](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#CheckedUnchecked)]

<span data-ttu-id="b18bb-193">Domyślnie operacje arytmetyczne odbywają się w niesprawdzonym kontekście.</span><span class="sxs-lookup"><span data-stu-id="b18bb-193">By default, arithmetic operations occur in an *unchecked* context.</span></span>

### <a name="floating-point-arithmetic-overflow"></a><span data-ttu-id="b18bb-194">Przepełnienie arytmetyczne zmiennoprzecinkowe</span><span class="sxs-lookup"><span data-stu-id="b18bb-194">Floating-point arithmetic overflow</span></span>

<span data-ttu-id="b18bb-195">Operacje arytmetyczne z `float` typami `double` i nigdy nie generują wyjątku.</span><span class="sxs-lookup"><span data-stu-id="b18bb-195">Arithmetic operations with the `float` and `double` types never throw an exception.</span></span> <span data-ttu-id="b18bb-196">Wynik operacji arytmetycznych z tymi typami może być jedną z wartości specjalnych, które reprezentują nieskończoność i nie liczbę:</span><span class="sxs-lookup"><span data-stu-id="b18bb-196">The result of arithmetic operations with those types can be one of special values that represent infinity and not-a-number:</span></span>

[!code-csharp-interactive[double non-finite values](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#FloatingPointOverflow)]

<span data-ttu-id="b18bb-197">W przypadku operandów `decimal` typu, przepełnienie arytmetyczne zawsze <xref:System.OverflowException> zgłasza, a dzielenie <xref:System.DivideByZeroException>przez zero zawsze zgłasza.</span><span class="sxs-lookup"><span data-stu-id="b18bb-197">For the operands of the `decimal` type, arithmetic overflow always throws an <xref:System.OverflowException> and division by zero always throws a <xref:System.DivideByZeroException>.</span></span>

## <a name="round-off-errors"></a><span data-ttu-id="b18bb-198">Błędy zaokrągleń</span><span class="sxs-lookup"><span data-stu-id="b18bb-198">Round-off errors</span></span>

<span data-ttu-id="b18bb-199">Ze względu na ogólne ograniczenia reprezentacji liczb rzeczywistych i arytmetycznych zmiennoprzecinkowych błędy zaokrągleń mogą wystąpić w obliczeniach z typami zmiennoprzecinkowymi.</span><span class="sxs-lookup"><span data-stu-id="b18bb-199">Because of general limitations of the floating-point representation of real numbers and floating-point arithmetic, the round-off errors might occur in calculations with floating-point types.</span></span> <span data-ttu-id="b18bb-200">Oznacza to, że wygenerowany wynik wyrażenia może być inny niż oczekiwany wynik matematyczny.</span><span class="sxs-lookup"><span data-stu-id="b18bb-200">That is, the produced result of an expression might differ from the expected mathematical result.</span></span> <span data-ttu-id="b18bb-201">Poniższy przykład ilustruje kilka takich przypadków:</span><span class="sxs-lookup"><span data-stu-id="b18bb-201">The following example demonstrates several such cases:</span></span>

[!code-csharp-interactive[round-off errors](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#RoundOffErrors)]

<span data-ttu-id="b18bb-202">Aby uzyskać więcej informacji, zobacz uwagi na stronie odwołań [System. Double](/dotnet/api/system.double#remarks), [System. Single](/dotnet/api/system.single#remarks)lub [System. Decimal](/dotnet/api/system.decimal#remarks) .</span><span class="sxs-lookup"><span data-stu-id="b18bb-202">For more information, see remarks at [System.Double](/dotnet/api/system.double#remarks), [System.Single](/dotnet/api/system.single#remarks), or [System.Decimal](/dotnet/api/system.decimal#remarks) reference pages.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="b18bb-203">Przeciążanie operatora</span><span class="sxs-lookup"><span data-stu-id="b18bb-203">Operator overloadability</span></span>

<span data-ttu-id="b18bb-204">Typ zdefiniowany przez użytkownika może przeciążać jednoargumentowe `--`( `+` [](operator-overloading.md) `++`,, `-`, i) operacje`*`arytmetyczne `%`( `+`, `/`, `-`, i). zainteresowanych.</span><span class="sxs-lookup"><span data-stu-id="b18bb-204">A user-defined type can [overload](operator-overloading.md) the unary (`++`, `--`, `+`, and `-`) and binary (`*`, `/`, `%`, `+`, and `-`) arithmetic operators.</span></span> <span data-ttu-id="b18bb-205">Gdy operator binarny jest przeciążony, odpowiadający mu operator przypisania złożonego jest również niejawnie przeciążony.</span><span class="sxs-lookup"><span data-stu-id="b18bb-205">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="b18bb-206">Typ zdefiniowany przez użytkownika nie może jawnie przeciążać złożonego operatora przypisania.</span><span class="sxs-lookup"><span data-stu-id="b18bb-206">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="b18bb-207">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="b18bb-207">C# language specification</span></span>

<span data-ttu-id="b18bb-208">Aby uzyskać więcej informacji, zobacz następujące sekcje [ C# specyfikacji języka](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="b18bb-208">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="b18bb-209">Operatory przyrostka i zmniejszenie</span><span class="sxs-lookup"><span data-stu-id="b18bb-209">Postfix increment and decrement operators</span></span>](~/_csharplang/spec/expressions.md#postfix-increment-and-decrement-operators)
- [<span data-ttu-id="b18bb-210">Operatory przyrostu i zmniejszania prefiksu</span><span class="sxs-lookup"><span data-stu-id="b18bb-210">Prefix increment and decrement operators</span></span>](~/_csharplang/spec/expressions.md#prefix-increment-and-decrement-operators)
- [<span data-ttu-id="b18bb-211">Jednoargumentowy operator plus</span><span class="sxs-lookup"><span data-stu-id="b18bb-211">Unary plus operator</span></span>](~/_csharplang/spec/expressions.md#unary-plus-operator)
- [<span data-ttu-id="b18bb-212">Jednoargumentowy operator minus</span><span class="sxs-lookup"><span data-stu-id="b18bb-212">Unary minus operator</span></span>](~/_csharplang/spec/expressions.md#unary-minus-operator)
- [<span data-ttu-id="b18bb-213">Operator mnożenia</span><span class="sxs-lookup"><span data-stu-id="b18bb-213">Multiplication operator</span></span>](~/_csharplang/spec/expressions.md#multiplication-operator)
- [<span data-ttu-id="b18bb-214">Operator dzielenia</span><span class="sxs-lookup"><span data-stu-id="b18bb-214">Division operator</span></span>](~/_csharplang/spec/expressions.md#division-operator)
- [<span data-ttu-id="b18bb-215">Operator reszty</span><span class="sxs-lookup"><span data-stu-id="b18bb-215">Remainder operator</span></span>](~/_csharplang/spec/expressions.md#remainder-operator)
- [<span data-ttu-id="b18bb-216">Operator dodawania</span><span class="sxs-lookup"><span data-stu-id="b18bb-216">Addition operator</span></span>](~/_csharplang/spec/expressions.md#addition-operator)
- [<span data-ttu-id="b18bb-217">Operator odejmowania</span><span class="sxs-lookup"><span data-stu-id="b18bb-217">Subtraction operator</span></span>](~/_csharplang/spec/expressions.md#subtraction-operator)
- [<span data-ttu-id="b18bb-218">Przypisanie złożone</span><span class="sxs-lookup"><span data-stu-id="b18bb-218">Compound assignment</span></span>](~/_csharplang/spec/expressions.md#compound-assignment)
- [<span data-ttu-id="b18bb-219">Sprawdzone i niesprawdzone operatory</span><span class="sxs-lookup"><span data-stu-id="b18bb-219">The checked and unchecked operators</span></span>](~/_csharplang/spec/expressions.md#the-checked-and-unchecked-operators)
- [<span data-ttu-id="b18bb-220">Promocje numeryczne</span><span class="sxs-lookup"><span data-stu-id="b18bb-220">Numeric promotions</span></span>](~/_csharplang/spec/expressions.md#numeric-promotions)

## <a name="see-also"></a><span data-ttu-id="b18bb-221">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b18bb-221">See also</span></span>

- [<span data-ttu-id="b18bb-222">C#odwoła</span><span class="sxs-lookup"><span data-stu-id="b18bb-222">C# reference</span></span>](../index.md)
- [<span data-ttu-id="b18bb-223">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="b18bb-223">C# operators</span></span>](index.md)
- <xref:System.Math?displayProperty=nameWithType>
- <xref:System.MathF?displayProperty=nameWithType>
- [<span data-ttu-id="b18bb-224">Wartości numeryczne na platformie .NET</span><span class="sxs-lookup"><span data-stu-id="b18bb-224">Numerics in .NET</span></span>](../../../standard/numerics.md)
