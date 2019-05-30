---
title: Operatory arytmetyczne - C# odwołania
description: Dowiedz się więcej o C# operatorów, które wykonują operacje mnożenie, dzielenie, pozostałą, dodawania i odejmowania za pomocą typów liczbowych.
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
ms.openlocfilehash: 84976d37514db851fd19c882b2c4c9cb003fc4bf
ms.sourcegitcommit: 26f4a7697c32978f6a328c89dc4ea87034065989
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/28/2019
ms.locfileid: "66250803"
---
# <a name="arithmetic-operators-c-reference"></a><span data-ttu-id="86506-103">Operatory arytmetyczne (C# odwołania)</span><span class="sxs-lookup"><span data-stu-id="86506-103">Arithmetic operators (C# Reference)</span></span>

<span data-ttu-id="86506-104">Następujące operatory wykonywać operacji arytmetycznych na wartościach typy liczbowe:</span><span class="sxs-lookup"><span data-stu-id="86506-104">The following operators perform arithmetic operations with numeric types:</span></span>

- <span data-ttu-id="86506-105">Jednoargumentowy [ `++` (inkrementacja)](#increment-operator-), [ `--` (dekrementacja)](#decrement-operator---), [ `+` (plus)](#unary-plus-and-minus-operators), i [ `-` (minus)](#unary-plus-and-minus-operators) operatorów</span><span class="sxs-lookup"><span data-stu-id="86506-105">Unary [`++` (increment)](#increment-operator-), [`--` (decrement)](#decrement-operator---), [`+` (plus)](#unary-plus-and-minus-operators), and [`-` (minus)](#unary-plus-and-minus-operators) operators</span></span>
- <span data-ttu-id="86506-106">Binarny [ `*` (mnożenie)](#multiplication-operator-), [ `/` (dział)](#division-operator-), [ `%` (resztę)](#remainder-operator-), [ `+` () Dodawanie)](#addition-operator-), i [ `-` (odejmowanie)](#subtraction-operator--) operatorów</span><span class="sxs-lookup"><span data-stu-id="86506-106">Binary [`*` (multiplication)](#multiplication-operator-), [`/` (division)](#division-operator-), [`%` (remainder)](#remainder-operator-), [`+` (addition)](#addition-operator-), and [`-` (subtraction)](#subtraction-operator--) operators</span></span>

<span data-ttu-id="86506-107">Te operatory obsługują wszystkie [całkowitego](../keywords/integral-types-table.md) i [zmiennoprzecinkowych](../keywords/floating-point-types-table.md) typów liczbowych.</span><span class="sxs-lookup"><span data-stu-id="86506-107">Those operators support all [integral](../keywords/integral-types-table.md) and [floating-point](../keywords/floating-point-types-table.md) numeric types.</span></span>

## <a name="increment-operator-"></a><span data-ttu-id="86506-108">Operator inkrementacji ++</span><span class="sxs-lookup"><span data-stu-id="86506-108">Increment operator ++</span></span>

<span data-ttu-id="86506-109">Jednoargumentowy operator inkrementacji `++` zwiększa się argumentem operacji o 1.</span><span class="sxs-lookup"><span data-stu-id="86506-109">The unary increment operator `++` increments its operand by 1.</span></span> <span data-ttu-id="86506-110">Argument musi być zmienną, [właściwość](../../programming-guide/classes-and-structs/properties.md) dostęp, lub [indeksatora](../../../csharp/programming-guide/indexers/index.md) dostępu.</span><span class="sxs-lookup"><span data-stu-id="86506-110">The operand must be a variable, a [property](../../programming-guide/classes-and-structs/properties.md) access, or an [indexer](../../../csharp/programming-guide/indexers/index.md) access.</span></span>

<span data-ttu-id="86506-111">Operator inkrementacji jest obsługiwana w dwóch formach: przyrostkowego operatora inkrementacyjnego `x++`i operator inkrementacji prefiks `++x`.</span><span class="sxs-lookup"><span data-stu-id="86506-111">The increment operator is supported in two forms: the postfix increment operator, `x++`, and the prefix increment operator, `++x`.</span></span>

### <a name="postfix-increment-operator"></a><span data-ttu-id="86506-112">Operator inkrementacji przyrostkowej</span><span class="sxs-lookup"><span data-stu-id="86506-112">Postfix increment operator</span></span>

<span data-ttu-id="86506-113">Wynik `x++` jest wartością `x` *przed* operacji, co ilustruje poniższy przykład:</span><span class="sxs-lookup"><span data-stu-id="86506-113">The result of `x++` is the value of `x` *before* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[postfix increment](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#PostfixIncrement)]

### <a name="prefix-increment-operator"></a><span data-ttu-id="86506-114">Operator inkrementacji przedrostka</span><span class="sxs-lookup"><span data-stu-id="86506-114">Prefix increment operator</span></span>

<span data-ttu-id="86506-115">Wynik `++x` jest wartością `x` *po* operacji, co ilustruje poniższy przykład:</span><span class="sxs-lookup"><span data-stu-id="86506-115">The result of `++x` is the value of `x` *after* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[prefix increment](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#PrefixIncrement)]

## <a name="decrement-operator---"></a><span data-ttu-id="86506-116">Operator dekrementacji--</span><span class="sxs-lookup"><span data-stu-id="86506-116">Decrement operator --</span></span>

<span data-ttu-id="86506-117">Jednoargumentowy operator dekrementacji `--` zmniejsza argumentem operacji o 1.</span><span class="sxs-lookup"><span data-stu-id="86506-117">The unary decrement operator `--` decrements its operand by 1.</span></span> <span data-ttu-id="86506-118">Argument musi być zmienną, [właściwość](../../programming-guide/classes-and-structs/properties.md) dostęp, lub [indeksatora](../../../csharp/programming-guide/indexers/index.md) dostępu.</span><span class="sxs-lookup"><span data-stu-id="86506-118">The operand must be a variable, a [property](../../programming-guide/classes-and-structs/properties.md) access, or an [indexer](../../../csharp/programming-guide/indexers/index.md) access.</span></span>

<span data-ttu-id="86506-119">Operator dekrementacji jest obsługiwany w dwóch formach: przyrostkowego operatora dekrementacyjnego `x--`i operator dekrementacji prefiksu, `--x`.</span><span class="sxs-lookup"><span data-stu-id="86506-119">The decrement operator is supported in two forms: the postfix decrement operator, `x--`, and the prefix decrement operator, `--x`.</span></span>

### <a name="postfix-decrement-operator"></a><span data-ttu-id="86506-120">Operator dekrementacji przyrostkowej</span><span class="sxs-lookup"><span data-stu-id="86506-120">Postfix decrement operator</span></span>

<span data-ttu-id="86506-121">Wynik `x--` jest wartością `x` *przed* operacji, co ilustruje poniższy przykład:</span><span class="sxs-lookup"><span data-stu-id="86506-121">The result of `x--` is the value of `x` *before* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[postfix decrement](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#PostfixDecrement)]

### <a name="prefix-decrement-operator"></a><span data-ttu-id="86506-122">Operator dekrementacji przedrostka</span><span class="sxs-lookup"><span data-stu-id="86506-122">Prefix decrement operator</span></span>

<span data-ttu-id="86506-123">Wynik `--x` jest wartością `x` *po* operacji, co ilustruje poniższy przykład:</span><span class="sxs-lookup"><span data-stu-id="86506-123">The result of `--x` is the value of `x` *after* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[prefix decrement](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#PrefixDecrement)]

## <a name="unary-plus-and-minus-operators"></a><span data-ttu-id="86506-124">Jednoargumentowe plus lub minus operatorów</span><span class="sxs-lookup"><span data-stu-id="86506-124">Unary plus and minus operators</span></span>

<span data-ttu-id="86506-125">Jednoargumentowy `+` operator zwraca wartość swojego operandu.</span><span class="sxs-lookup"><span data-stu-id="86506-125">The unary `+` operator returns the value of its operand.</span></span> <span data-ttu-id="86506-126">Jednoargumentowy `-` operator oblicza liczbowych negacji swojego operandu.</span><span class="sxs-lookup"><span data-stu-id="86506-126">The unary `-` operator computes the numeric negation of its operand.</span></span>

[!code-csharp-interactive[unary plus and minus](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#UnaryPlusAndMinus)]

<span data-ttu-id="86506-127">Jednoargumentowy `-` nie obsługuje operatora [ulong](../keywords/ulong.md) typu.</span><span class="sxs-lookup"><span data-stu-id="86506-127">The unary `-` operator doesn't support the [ulong](../keywords/ulong.md) type.</span></span>

## <a name="multiplication-operator-"></a><span data-ttu-id="86506-128">Operator mnożenia \*</span><span class="sxs-lookup"><span data-stu-id="86506-128">Multiplication operator \*</span></span>

<span data-ttu-id="86506-129">Operator mnożenia `*` Oblicza iloczyn argumentów:</span><span class="sxs-lookup"><span data-stu-id="86506-129">The multiplication operator `*` computes the product of its operands:</span></span>

[!code-csharp-interactive[multiplication operator](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#Multiplication)]

<span data-ttu-id="86506-130">Jednoargumentowy `*` operator jest [operatora pośredniego wskaźnika](pointer-related-operators.md#pointer-indirection-operator-).</span><span class="sxs-lookup"><span data-stu-id="86506-130">The unary `*` operator is the [pointer indirection operator](pointer-related-operators.md#pointer-indirection-operator-).</span></span>

## <a name="division-operator-"></a><span data-ttu-id="86506-131">Operator dzielenia /</span><span class="sxs-lookup"><span data-stu-id="86506-131">Division operator /</span></span>

<span data-ttu-id="86506-132">Operator dzielenia `/` dzieli pierwszy argument operacji za drugim argumentem.</span><span class="sxs-lookup"><span data-stu-id="86506-132">The division operator `/` divides its first operand by its second operand.</span></span>

### <a name="integer-division"></a><span data-ttu-id="86506-133">Dzielenie liczby całkowitej</span><span class="sxs-lookup"><span data-stu-id="86506-133">Integer division</span></span>

<span data-ttu-id="86506-134">Dla argumentów typu Liczba całkowita, wynikiem `/` operator jest typu Liczba całkowita i równości iloraz dwóch argumentów operacji, zaokrąglana w kierunku zera:</span><span class="sxs-lookup"><span data-stu-id="86506-134">For the operands of integer types, the result of the `/` operator is of an integer type and equals the quotient of the two operands rounded towards zero:</span></span>

[!code-csharp-interactive[integer division](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#IntegerDivision)]

<span data-ttu-id="86506-135">Aby uzyskać iloraz dwóch argumentów operacji jako liczba zmiennoprzecinkowa, należy użyć `float`, `double`, lub `decimal` typu:</span><span class="sxs-lookup"><span data-stu-id="86506-135">To obtain the quotient of the two operands as a floating-point number, use the `float`, `double`, or `decimal` type:</span></span>

[!code-csharp-interactive[integer as floating-point division](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#IntegerAsFloatingPointDivision)]

### <a name="floating-point-division"></a><span data-ttu-id="86506-136">Dzielenie zmiennoprzecinkowe</span><span class="sxs-lookup"><span data-stu-id="86506-136">Floating-point division</span></span>

<span data-ttu-id="86506-137">Aby uzyskać `float`, `double`, i `decimal` typów, wynikiem `/` operatora jest równy ilorazowi dwóch argumentów operacji:</span><span class="sxs-lookup"><span data-stu-id="86506-137">For the `float`, `double`, and `decimal` types, the result of the `/` operator is the quotient of the two operands:</span></span>

[!code-csharp-interactive[floating-point division](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#FloatingPointDivision)]

<span data-ttu-id="86506-138">Jeśli jeden z operandów jest `decimal`, inny argument może być żadnego `float` ani `double`, ponieważ ani `float` ani `double` jest niejawnie konwertowany na `decimal`.</span><span class="sxs-lookup"><span data-stu-id="86506-138">If one of the operands is `decimal`, another operand can be neither `float` nor `double`, because neither `float` nor `double` is implicitly convertible to `decimal`.</span></span> <span data-ttu-id="86506-139">Należy jawnie przekonwertować `float` lub `double` operand `decimal` typu.</span><span class="sxs-lookup"><span data-stu-id="86506-139">You must explicitly convert the `float` or `double` operand to the `decimal` type.</span></span> <span data-ttu-id="86506-140">Aby uzyskać więcej informacji na temat niejawne konwersje między typów liczbowych, zobacz [Tabela niejawnych konwersji liczbowych](../keywords/implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="86506-140">For more information about implicit conversions between numeric types, see [Implicit numeric conversions table](../keywords/implicit-numeric-conversions-table.md).</span></span>

## <a name="remainder-operator-"></a><span data-ttu-id="86506-141">Resztę operator %</span><span class="sxs-lookup"><span data-stu-id="86506-141">Remainder operator %</span></span>

<span data-ttu-id="86506-142">Operator reszty `%` oblicza pozostałą po podzieleniu pierwszy argument operacji za drugim argumentem.</span><span class="sxs-lookup"><span data-stu-id="86506-142">The remainder operator `%` computes the remainder after dividing its first operand by its second operand.</span></span>

### <a name="integer-remainder"></a><span data-ttu-id="86506-143">Pozostała liczba całkowita</span><span class="sxs-lookup"><span data-stu-id="86506-143">Integer remainder</span></span>
  
<span data-ttu-id="86506-144">Dla argumentów typu Liczba całkowita, wynikiem `a % b` wartość jest generowany przez `a - (a / b) * b`.</span><span class="sxs-lookup"><span data-stu-id="86506-144">For the operands of integer types, the result of `a % b` is the value produced by `a - (a / b) * b`.</span></span> <span data-ttu-id="86506-145">Znak resztę różna od zera jest taka sama, jak w przypadku pierwszego operandu w poniższym przykładzie pokazano:</span><span class="sxs-lookup"><span data-stu-id="86506-145">The sign of the non-zero remainder is the same as that of the first operand, as the following example shows:</span></span>

[!code-csharp-interactive[integer remainder](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#IntegerRemainder)]

<span data-ttu-id="86506-146">Użyj <xref:System.Math.DivRem%2A?displayProperty=nameWithType> metodę w celu obliczenia zarówno dzielenie liczby całkowitej, jak i resztę wyników.</span><span class="sxs-lookup"><span data-stu-id="86506-146">Use the <xref:System.Math.DivRem%2A?displayProperty=nameWithType> method to compute both integer division and remainder results.</span></span>

### <a name="floating-point-remainder"></a><span data-ttu-id="86506-147">Zmiennoprzecinkową resztę</span><span class="sxs-lookup"><span data-stu-id="86506-147">Floating-point remainder</span></span>

<span data-ttu-id="86506-148">Aby uzyskać `float` i `double` operandów, wynik `x % y` dla skończonego `x` i `y` jest wartością `z` tak, aby</span><span class="sxs-lookup"><span data-stu-id="86506-148">For the `float` and `double` operands, the result of `x % y` for the finite `x` and `y` is the value `z` such that</span></span>

- <span data-ttu-id="86506-149">Znak `z`, jeśli różna od zera, jest taka sama jak znak `x`.</span><span class="sxs-lookup"><span data-stu-id="86506-149">The sign of `z`, if non-zero, is the same as the sign of `x`.</span></span>
- <span data-ttu-id="86506-150">wartość bezwzględna `z` wartość jest generowany przez `|x| - n * |y|` gdzie `n` jest największa możliwa liczba całkowita, która jest mniejsza niż lub równa `|x| / |y|` i `|x|` i `|y|` są wartości bezwzględne dla `x` i `y`, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="86506-150">The absolute value of `z` is the value produced by `|x| - n * |y|` where `n` is the largest possible integer that is less than or equal to `|x| / |y|` and `|x|` and `|y|` are the absolute values of `x` and `y`, respectively.</span></span>

> [!NOTE]
> <span data-ttu-id="86506-151">Ta metoda obliczeniowych reszta jest odpowiednikiem używanym dla liczby całkowitej argumentów, ale różni się od IEEE 754.</span><span class="sxs-lookup"><span data-stu-id="86506-151">This method of computing the remainder is analogous to that used for integer operands, but differs from the IEEE 754.</span></span> <span data-ttu-id="86506-152">Operacja Reminder, który jest zgodny z IEEE 754, należy użyć <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="86506-152">If you need the remainder operation that complies with the IEEE 754, use the <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="86506-153">Aby uzyskać informacje o zachowanie `%` operator nieskończona argumentów, zobacz [operator reszty](~/_csharplang/spec/expressions.md#remainder-operator) części [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="86506-153">For information about the behavior of the `%` operator with non-finite operands, see the [Remainder operator](~/_csharplang/spec/expressions.md#remainder-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="86506-154">Aby uzyskać `decimal` argumentów operacji, operator reszty `%` jest odpowiednikiem [operator reszty](<xref:System.Decimal.op_Modulus(System.Decimal,System.Decimal)>) z <xref:System.Decimal?displayProperty=nameWithType> typu.</span><span class="sxs-lookup"><span data-stu-id="86506-154">For the `decimal` operands, the remainder operator `%` is equivalent to the [remainder operator](<xref:System.Decimal.op_Modulus(System.Decimal,System.Decimal)>) of the <xref:System.Decimal?displayProperty=nameWithType> type.</span></span>

<span data-ttu-id="86506-155">Poniższy przykład pokazuje zachowanie operator reszty z argumentów operacji zmiennoprzecinkowej:</span><span class="sxs-lookup"><span data-stu-id="86506-155">The following example demonstrates the behavior of the remainder operator with floating-point operands:</span></span>

[!code-csharp-interactive[floating-point remainder](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#FloatingPointRemainder)]

## <a name="addition-operator-"></a><span data-ttu-id="86506-156">Operator dodawania +</span><span class="sxs-lookup"><span data-stu-id="86506-156">Addition operator +</span></span>

<span data-ttu-id="86506-157">Operator dodawania `+` oblicza sumę argumentów:</span><span class="sxs-lookup"><span data-stu-id="86506-157">The addition operator `+` computes the sum of its operands:</span></span>

[!code-csharp-interactive[addition operator](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#Addition)]

<span data-ttu-id="86506-158">Możesz również użyć `+` operator dla kombinacji parametrów łączenia i delegata.</span><span class="sxs-lookup"><span data-stu-id="86506-158">You also can use the `+` operator for string concatenation and delegate combination.</span></span> <span data-ttu-id="86506-159">Aby uzyskać więcej informacji, zobacz [ `+` i `+=` operatory](addition-operator.md) artykułu.</span><span class="sxs-lookup"><span data-stu-id="86506-159">For more information, see the [`+` and `+=` operators](addition-operator.md) article.</span></span>

## <a name="subtraction-operator--"></a><span data-ttu-id="86506-160">Operator odejmowania-</span><span class="sxs-lookup"><span data-stu-id="86506-160">Subtraction operator -</span></span>

<span data-ttu-id="86506-161">Operator odejmowania `-` odejmuje jej drugiego operandu od jego pierwszego operandu:</span><span class="sxs-lookup"><span data-stu-id="86506-161">The subtraction operator `-` subtracts its second operand from its first operand:</span></span>

[!code-csharp-interactive[subtraction operator](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#Subtraction)]

<span data-ttu-id="86506-162">Możesz również użyć `-` operator usuwanie delegata.</span><span class="sxs-lookup"><span data-stu-id="86506-162">You also can use the `-` operator for delegate removal.</span></span> <span data-ttu-id="86506-163">Aby uzyskać więcej informacji, zobacz [ `-` operator](subtraction-operator.md) artykułu.</span><span class="sxs-lookup"><span data-stu-id="86506-163">For more information, see the [`-` operator](subtraction-operator.md) article.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="86506-164">Przydział złożony</span><span class="sxs-lookup"><span data-stu-id="86506-164">Compound assignment</span></span>

<span data-ttu-id="86506-165">Dla operatora binarnego `op`, wyrażenie przypisania złożonego formularza</span><span class="sxs-lookup"><span data-stu-id="86506-165">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="86506-166">odpowiada wyrażeniu</span><span class="sxs-lookup"><span data-stu-id="86506-166">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="86506-167">z tą różnicą, że `x` jest obliczany tylko raz.</span><span class="sxs-lookup"><span data-stu-id="86506-167">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="86506-168">W poniższym przykładzie pokazano użycie przydział złożony z operatorów arytmetycznych:</span><span class="sxs-lookup"><span data-stu-id="86506-168">The following example demonstrates the usage of compound assignment with arithmetic operators:</span></span>

[!code-csharp-interactive[compound assignment](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#CompoundAssignment)]

<span data-ttu-id="86506-169">Z powodu [promocji na liczbowe](~/_csharplang/spec/expressions.md#numeric-promotions), wynikiem `op` operacji może nie być niejawnie konwertowane na typ `T` z `x`.</span><span class="sxs-lookup"><span data-stu-id="86506-169">Because of [numeric promotions](~/_csharplang/spec/expressions.md#numeric-promotions), the result of the `op` operation might be not implicitly convertible to the type `T` of `x`.</span></span> <span data-ttu-id="86506-170">W takim przypadku jeśli `op` jest wstępnie zdefiniowanego operatora, a wynik operacji jest jawnie konwertowany na typ `T` z `x`, wyrażenia przypisania złożonego w postaci `x op= y` jest odpowiednikiem `x = (T)(x op y)`, z wyjątkiem które `x` jest oceniane tylko raz.</span><span class="sxs-lookup"><span data-stu-id="86506-170">In such a case, if `op` is a predefined operator and the result of the operation is explicitly convertible to the type `T` of `x`, a compound assignment expression of the form `x op= y` is equivalent to `x = (T)(x op y)`, except that `x` is only evaluated once.</span></span> <span data-ttu-id="86506-171">Poniższy przykład przedstawia tego zachowania:</span><span class="sxs-lookup"><span data-stu-id="86506-171">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[compound assignment with cast](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#CompoundAssignmentWithCast)]

<span data-ttu-id="86506-172">Możesz także użyć `+=` i `-=` operatory subskrybowanie i anulowanie subskrypcji [zdarzenia](../keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="86506-172">You also use the `+=` and `-=` operators to subscribe to and unsubscribe from [events](../keywords/event.md).</span></span> <span data-ttu-id="86506-173">Aby uzyskać więcej informacji, zobacz [porady: subskrybowanie i anulowanie subskrypcji zdarzeń](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="86506-173">For more information, see [How to: subscribe to and unsubscribe from events](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="operator-precedence-and-associativity"></a><span data-ttu-id="86506-174">Pierwszeństwo i kojarzenie operatorów</span><span class="sxs-lookup"><span data-stu-id="86506-174">Operator precedence and associativity</span></span>

<span data-ttu-id="86506-175">Poniższa lista zamówień operatorów arytmetycznych, zaczynając od najwyższy priorytet do najniższego:</span><span class="sxs-lookup"><span data-stu-id="86506-175">The following list orders arithmetic operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="86506-176">Inkrementacja przyrostkowa `x++` i dekrementacyjne `x--` operatorów</span><span class="sxs-lookup"><span data-stu-id="86506-176">Postfix increment `x++` and decrement `x--` operators</span></span>
- <span data-ttu-id="86506-177">Inkrementacja przedrostkowa `++x` i dekrementacyjne `--x` i jednoargumentowe `+` i `-` operatorów</span><span class="sxs-lookup"><span data-stu-id="86506-177">Prefix increment `++x` and decrement `--x` and unary `+` and `-` operators</span></span>
- <span data-ttu-id="86506-178">Mnożenia `*`, `/`, i `%` operatorów</span><span class="sxs-lookup"><span data-stu-id="86506-178">Multiplicative `*`, `/`, and `%` operators</span></span>
- <span data-ttu-id="86506-179">Dodatek `+` i `-` operatorów</span><span class="sxs-lookup"><span data-stu-id="86506-179">Additive `+` and `-` operators</span></span>

<span data-ttu-id="86506-180">Operatory arytmetyczne binarne są lewostronne.</span><span class="sxs-lookup"><span data-stu-id="86506-180">Binary arithmetic operators are left-associative.</span></span> <span data-ttu-id="86506-181">Oznacza to operatory o tym samym poziomie priorytetu są obliczane od lewej do prawej.</span><span class="sxs-lookup"><span data-stu-id="86506-181">That is, operators with the same precedence level are evaluated from left to right.</span></span>

<span data-ttu-id="86506-182">Użyj nawiasów, `()`, aby zmienić kolejność oceny nałożonych przez pierwszeństwo i kojarzenie operatorów.</span><span class="sxs-lookup"><span data-stu-id="86506-182">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence and associativity.</span></span>

[!code-csharp-interactive[precedence and associativity](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#PrecedenceAndAssociativity)]

<span data-ttu-id="86506-183">Aby uzyskać pełną listę C# operatory uporządkowane według poziomu priorytetu, zobacz [ C# operatory](index.md).</span><span class="sxs-lookup"><span data-stu-id="86506-183">For the complete list of C# operators ordered by precedence level, see [C# operators](index.md).</span></span>

## <a name="arithmetic-overflow-and-division-by-zero"></a><span data-ttu-id="86506-184">Przepełnienie arytmetyczne i dzielenie przez zero</span><span class="sxs-lookup"><span data-stu-id="86506-184">Arithmetic overflow and division by zero</span></span>

<span data-ttu-id="86506-185">Gdy wynik operacji arytmetycznej jest spoza zakresu możliwych wartości skończoną zaangażowane typu liczbowego, zachowanie jest operator arytmetyczny zależy od typu argumentów.</span><span class="sxs-lookup"><span data-stu-id="86506-185">When the result of an arithmetic operation is outside the range of possible finite values of the involved numeric type, the behavior of an arithmetic operator depends on the type of its operands.</span></span>

### <a name="integer-arithmetic-overflow"></a><span data-ttu-id="86506-186">Liczba całkowita przepełnienie arytmetyczne</span><span class="sxs-lookup"><span data-stu-id="86506-186">Integer arithmetic overflow</span></span>

<span data-ttu-id="86506-187">Dzielenie liczby całkowitej przez zero zawsze generuje wyjątek <xref:System.DivideByZeroException>.</span><span class="sxs-lookup"><span data-stu-id="86506-187">Integer division by zero always throws a <xref:System.DivideByZeroException>.</span></span>

<span data-ttu-id="86506-188">W przypadku przepełnienia arytmetycznego liczby całkowitej, przepełnienie sprawdzanie kontekstu, który może być [zaznaczony lub niezaznaczony](../keywords/checked-and-unchecked.md), kontroluje zachowanie wynikową:</span><span class="sxs-lookup"><span data-stu-id="86506-188">In case of integer arithmetic overflow, an overflow checking context, which can be [checked or unchecked](../keywords/checked-and-unchecked.md), controls the resulting behavior:</span></span>

- <span data-ttu-id="86506-189">W kontekście sprawdzanym przepełnienie odbywa się w wyrażeniu stałym kompilacji błędu.</span><span class="sxs-lookup"><span data-stu-id="86506-189">In a checked context, if overflow happens in a constant expression, a compile-time error occurs.</span></span> <span data-ttu-id="86506-190">W przeciwnym razie, gdy operacja jest wykonywana w czasie wykonywania, <xref:System.OverflowException> zgłaszany.</span><span class="sxs-lookup"><span data-stu-id="86506-190">Otherwise, when the operation is performed at run time, an <xref:System.OverflowException> is thrown.</span></span>
- <span data-ttu-id="86506-191">W kontekście niesprawdzanym wynik jest obcinana odrzucając wszystkie bity wyższego rzędu, które nie mieszczą się w typie docelowym.</span><span class="sxs-lookup"><span data-stu-id="86506-191">In an unchecked context, the result is truncated by discarding any high-order bits that don't fit in the destination type.</span></span>

<span data-ttu-id="86506-192">Wraz z [checked i unchecked](../keywords/checked-and-unchecked.md) instrukcji, można użyć `checked` i `unchecked` operatory, aby kontrolować przepełnienia, sprawdzając kontekst, w którym wyrażenie jest obliczane:</span><span class="sxs-lookup"><span data-stu-id="86506-192">Along with the [checked and unchecked](../keywords/checked-and-unchecked.md) statements, you can use the `checked` and `unchecked` operators to control the overflow checking context, in which an expression is evaluated:</span></span>

[!code-csharp-interactive[checked and unchecked](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#CheckedUnchecked)]

<span data-ttu-id="86506-193">Domyślnie operacje arytmetyczne występują w *unchecked* kontekstu.</span><span class="sxs-lookup"><span data-stu-id="86506-193">By default, arithmetic operations occur in an *unchecked* context.</span></span>

### <a name="floating-point-arithmetic-overflow"></a><span data-ttu-id="86506-194">Zmiennoprzecinkowe przepełnienie arytmetyczne</span><span class="sxs-lookup"><span data-stu-id="86506-194">Floating-point arithmetic overflow</span></span>

<span data-ttu-id="86506-195">Operacji arytmetycznych na wartościach `float` i `double` typy nigdy nie zgłasza wyjątku.</span><span class="sxs-lookup"><span data-stu-id="86506-195">Arithmetic operations with the `float` and `double` types never throw an exception.</span></span> <span data-ttu-id="86506-196">Wynik operacji arytmetycznych na wartościach tych typów może być jedną z wartości specjalne, które reprezentują nieskończoność i nie nieliczbowych:</span><span class="sxs-lookup"><span data-stu-id="86506-196">The result of arithmetic operations with those types can be one of special values that represent infinity and not-a-number:</span></span>

[!code-csharp-interactive[double non-finite values](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#FloatingPointOverflow)]

<span data-ttu-id="86506-197">Dla argumentów operacji `decimal` typu arytmetycznego przepełnienia zawsze zgłasza <xref:System.OverflowException> i dzielenie przez zero zawsze generuje wyjątek <xref:System.DivideByZeroException>.</span><span class="sxs-lookup"><span data-stu-id="86506-197">For the operands of the `decimal` type, arithmetic overflow always throws an <xref:System.OverflowException> and division by zero always throws a <xref:System.DivideByZeroException>.</span></span>

## <a name="round-off-errors"></a><span data-ttu-id="86506-198">Błędy zaokrąglania</span><span class="sxs-lookup"><span data-stu-id="86506-198">Round-off errors</span></span>

<span data-ttu-id="86506-199">Ze względu na ograniczenia ogólne zmiennoprzecinkowych reprezentacji w postaci liczby rzeczywiste i arytmetyki zmiennoprzecinkowej mogą wystąpić błędy zaokrąglania, w obliczeniach z typów zmiennoprzecinkowych.</span><span class="sxs-lookup"><span data-stu-id="86506-199">Because of general limitations of the floating-point representation of real numbers and floating-point arithmetic, the round-off errors might occur in calculations with floating-point types.</span></span> <span data-ttu-id="86506-200">Oznacza to, że utworzone wynik wyrażenia różnić się od oczekiwanego wyniku matematyczne.</span><span class="sxs-lookup"><span data-stu-id="86506-200">That is, the produced result of an expression might differ from the expected mathematical result.</span></span> <span data-ttu-id="86506-201">W poniższym przykładzie pokazano kilka takich przypadkach:</span><span class="sxs-lookup"><span data-stu-id="86506-201">The following example demonstrates several such cases:</span></span>

[!code-csharp-interactive[round-off errors](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#RoundOffErrors)]

<span data-ttu-id="86506-202">Aby uzyskać więcej informacji, zobacz uwagi w [System.Double](/dotnet/api/system.double#remarks), [System.Single](/dotnet/api/system.single#remarks), lub [System.Decimal](/dotnet/api/system.decimal#remarks) odwoływać się do strony.</span><span class="sxs-lookup"><span data-stu-id="86506-202">For more information, see remarks at [System.Double](/dotnet/api/system.double#remarks), [System.Single](/dotnet/api/system.single#remarks), or [System.Decimal](/dotnet/api/system.decimal#remarks) reference pages.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="86506-203">Overloadability — operator</span><span class="sxs-lookup"><span data-stu-id="86506-203">Operator overloadability</span></span>

<span data-ttu-id="86506-204">Typ zdefiniowany przez użytkownika może [przeciążenia](../keywords/operator.md) jednoargumentowe (`++`, `--`, `+`, i `-`) i binarny (`*`, `/`, `%`, `+`i `-`) operatory arytmetyczne.</span><span class="sxs-lookup"><span data-stu-id="86506-204">A user-defined type can [overload](../keywords/operator.md) the unary (`++`, `--`, `+`, and `-`) and binary (`*`, `/`, `%`, `+`, and `-`) arithmetic operators.</span></span> <span data-ttu-id="86506-205">Gdy jest przeciążony operator binarny, odpowiedniego operatora przypisania złożonego jest również niejawnie przeciążona.</span><span class="sxs-lookup"><span data-stu-id="86506-205">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="86506-206">Typ zdefiniowany przez użytkownika nie można jawnie przeciążyć operator przypisania złożonego.</span><span class="sxs-lookup"><span data-stu-id="86506-206">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="86506-207">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="86506-207">C# language specification</span></span>

<span data-ttu-id="86506-208">Aby uzyskać więcej informacji, zobacz następujące sekcje [ C# specyfikacji języka](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="86506-208">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="86506-209">Inkrementacja przyrostkowa i operatory dekrementacji</span><span class="sxs-lookup"><span data-stu-id="86506-209">Postfix increment and decrement operators</span></span>](~/_csharplang/spec/expressions.md#postfix-increment-and-decrement-operators)
- [<span data-ttu-id="86506-210">Przedrostkowe i operatory dekrementacji</span><span class="sxs-lookup"><span data-stu-id="86506-210">Prefix increment and decrement operators</span></span>](~/_csharplang/spec/expressions.md#prefix-increment-and-decrement-operators)
- [<span data-ttu-id="86506-211">Jednoargumentowy operator plus</span><span class="sxs-lookup"><span data-stu-id="86506-211">Unary plus operator</span></span>](~/_csharplang/spec/expressions.md#unary-plus-operator)
- [<span data-ttu-id="86506-212">Jednoargumentowy operator minus</span><span class="sxs-lookup"><span data-stu-id="86506-212">Unary minus operator</span></span>](~/_csharplang/spec/expressions.md#unary-minus-operator)
- [<span data-ttu-id="86506-213">Operator mnożenia</span><span class="sxs-lookup"><span data-stu-id="86506-213">Multiplication operator</span></span>](~/_csharplang/spec/expressions.md#multiplication-operator)
- [<span data-ttu-id="86506-214">Operator dzielenia</span><span class="sxs-lookup"><span data-stu-id="86506-214">Division operator</span></span>](~/_csharplang/spec/expressions.md#division-operator)
- [<span data-ttu-id="86506-215">Operator reszty</span><span class="sxs-lookup"><span data-stu-id="86506-215">Remainder operator</span></span>](~/_csharplang/spec/expressions.md#remainder-operator)
- [<span data-ttu-id="86506-216">Operator dodawania</span><span class="sxs-lookup"><span data-stu-id="86506-216">Addition operator</span></span>](~/_csharplang/spec/expressions.md#addition-operator)
- [<span data-ttu-id="86506-217">Operator odejmowania</span><span class="sxs-lookup"><span data-stu-id="86506-217">Subtraction operator</span></span>](~/_csharplang/spec/expressions.md#subtraction-operator)
- [<span data-ttu-id="86506-218">Przydział złożony</span><span class="sxs-lookup"><span data-stu-id="86506-218">Compound assignment</span></span>](~/_csharplang/spec/expressions.md#compound-assignment)
- [<span data-ttu-id="86506-219">Operatory checked i unchecked</span><span class="sxs-lookup"><span data-stu-id="86506-219">The checked and unchecked operators</span></span>](~/_csharplang/spec/expressions.md#the-checked-and-unchecked-operators)
- [<span data-ttu-id="86506-220">Promocji na liczbowe</span><span class="sxs-lookup"><span data-stu-id="86506-220">Numeric promotions</span></span>](~/_csharplang/spec/expressions.md#numeric-promotions)

## <a name="see-also"></a><span data-ttu-id="86506-221">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="86506-221">See also</span></span>

- [<span data-ttu-id="86506-222">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="86506-222">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="86506-223">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="86506-223">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="86506-224">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="86506-224">C# Operators</span></span>](index.md)
- <xref:System.Math?displayProperty=nameWithType>
- <xref:System.MathF?displayProperty=nameWithType>
- [<span data-ttu-id="86506-225">Wartości numeryczne na platformie .NET</span><span class="sxs-lookup"><span data-stu-id="86506-225">Numerics in .NET</span></span>](../../../standard/numerics.md)
