---
title: Operatory arytmetyczne — odwołanie do języka C#
description: Dowiedz się więcej o operatorach języka C#, które wykonują operacje mnożenia, dzielenia, reszty, dodawania i odejmowania za pomocą typów liczbowych.
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
ms.openlocfilehash: f03084fa611c35c5504190b28fab79563d560d03
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399260"
---
# <a name="arithmetic-operators-c-reference"></a><span data-ttu-id="03515-103">Operatory arytmetyczne (odwołanie do języka C#)</span><span class="sxs-lookup"><span data-stu-id="03515-103">Arithmetic operators (C# reference)</span></span>

<span data-ttu-id="03515-104">Następujące operatory wykonują operacje arytmetyczne z operandami typów numerycznych:</span><span class="sxs-lookup"><span data-stu-id="03515-104">The following operators perform arithmetic operations with operands of numeric types:</span></span>

- <span data-ttu-id="03515-105">Operatory [ `++` nieulatyczni (przyrostowe),](#increment-operator-) [ `--` (decrement)](#decrement-operator---), [ `+` (plus)](#unary-plus-and-minus-operators)i [ `-` (minus)](#unary-plus-and-minus-operators)</span><span class="sxs-lookup"><span data-stu-id="03515-105">Unary [`++` (increment)](#increment-operator-), [`--` (decrement)](#decrement-operator---), [`+` (plus)](#unary-plus-and-minus-operators), and [`-` (minus)](#unary-plus-and-minus-operators) operators</span></span>
- <span data-ttu-id="03515-106">Operatory [ `*` binarne (mnożenie),](#multiplication-operator-) [ `/` (podział),](#division-operator-) [ `%` (reszta)](#remainder-operator-) [ `+` , (dodawanie)](#addition-operator-)i [ `-` (odejmowanie)](#subtraction-operator--)</span><span class="sxs-lookup"><span data-stu-id="03515-106">Binary [`*` (multiplication)](#multiplication-operator-), [`/` (division)](#division-operator-), [`%` (remainder)](#remainder-operator-), [`+` (addition)](#addition-operator-), and [`-` (subtraction)](#subtraction-operator--) operators</span></span>

<span data-ttu-id="03515-107">Te operatory są obsługiwane przez wszystkie [typy liczbowe integralne](../builtin-types/integral-numeric-types.md) i [zmiennoprzecinkowe.](../builtin-types/floating-point-numeric-types.md)</span><span class="sxs-lookup"><span data-stu-id="03515-107">Those operators are supported by all [integral](../builtin-types/integral-numeric-types.md) and [floating-point](../builtin-types/floating-point-numeric-types.md) numeric types.</span></span>

## <a name="increment-operator-"></a><span data-ttu-id="03515-108">Operator przyrostu ++</span><span class="sxs-lookup"><span data-stu-id="03515-108">Increment operator ++</span></span>

<span data-ttu-id="03515-109">Operator `++` przyrostu unary zwiększa swój operand o 1.</span><span class="sxs-lookup"><span data-stu-id="03515-109">The unary increment operator `++` increments its operand by 1.</span></span> <span data-ttu-id="03515-110">Operand musi być zmienną, dostępem do [właściwości](../../programming-guide/classes-and-structs/properties.md) lub dostępem [do indeksatora.](../../programming-guide/indexers/index.md)</span><span class="sxs-lookup"><span data-stu-id="03515-110">The operand must be a variable, a [property](../../programming-guide/classes-and-structs/properties.md) access, or an [indexer](../../programming-guide/indexers/index.md) access.</span></span>

<span data-ttu-id="03515-111">Operator przyrostu jest obsługiwany w dwóch formach: operator przyrostu przyrostu przyrostu, `x++`i `++x`operator przyrostu prefiksu, .</span><span class="sxs-lookup"><span data-stu-id="03515-111">The increment operator is supported in two forms: the postfix increment operator, `x++`, and the prefix increment operator, `++x`.</span></span>

### <a name="postfix-increment-operator"></a><span data-ttu-id="03515-112">Operator inkrementacji przyrostkowej</span><span class="sxs-lookup"><span data-stu-id="03515-112">Postfix increment operator</span></span>

<span data-ttu-id="03515-113">Wynik `x++` jest wartością `x` *przed* operacją, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="03515-113">The result of `x++` is the value of `x` *before* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[postfix increment](snippets/ArithmeticOperators.cs#PostfixIncrement)]

### <a name="prefix-increment-operator"></a><span data-ttu-id="03515-114">Operator przyrostu prefiksu</span><span class="sxs-lookup"><span data-stu-id="03515-114">Prefix increment operator</span></span>

<span data-ttu-id="03515-115">Wynik `++x` jest wartością `x` *po* operacji, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="03515-115">The result of `++x` is the value of `x` *after* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[prefix increment](snippets/ArithmeticOperators.cs#PrefixIncrement)]

## <a name="decrement-operator---"></a><span data-ttu-id="03515-116">Operator decrement --</span><span class="sxs-lookup"><span data-stu-id="03515-116">Decrement operator --</span></span>

<span data-ttu-id="03515-117">Operator `--` unary decrementzmniejsza swój operand o 1.</span><span class="sxs-lookup"><span data-stu-id="03515-117">The unary decrement operator `--` decrements its operand by 1.</span></span> <span data-ttu-id="03515-118">Operand musi być zmienną, dostępem do [właściwości](../../programming-guide/classes-and-structs/properties.md) lub dostępem [do indeksatora.](../../programming-guide/indexers/index.md)</span><span class="sxs-lookup"><span data-stu-id="03515-118">The operand must be a variable, a [property](../../programming-guide/classes-and-structs/properties.md) access, or an [indexer](../../programming-guide/indexers/index.md) access.</span></span>

<span data-ttu-id="03515-119">Operator decrement jest obsługiwany w dwóch formach: operator `x--`decrement przyrostka, i `--x`operator decrement prefiksu, .</span><span class="sxs-lookup"><span data-stu-id="03515-119">The decrement operator is supported in two forms: the postfix decrement operator, `x--`, and the prefix decrement operator, `--x`.</span></span>

### <a name="postfix-decrement-operator"></a><span data-ttu-id="03515-120">Operator dekrementacji przyrostkowej</span><span class="sxs-lookup"><span data-stu-id="03515-120">Postfix decrement operator</span></span>

<span data-ttu-id="03515-121">Wynik `x--` jest wartością `x` *przed* operacją, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="03515-121">The result of `x--` is the value of `x` *before* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[postfix decrement](snippets/ArithmeticOperators.cs#PostfixDecrement)]

### <a name="prefix-decrement-operator"></a><span data-ttu-id="03515-122">Operator zmniejszania prefiksów</span><span class="sxs-lookup"><span data-stu-id="03515-122">Prefix decrement operator</span></span>

<span data-ttu-id="03515-123">Wynik `--x` jest wartością `x` *po* operacji, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="03515-123">The result of `--x` is the value of `x` *after* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[prefix decrement](snippets/ArithmeticOperators.cs#PrefixDecrement)]

## <a name="unary-plus-and-minus-operators"></a><span data-ttu-id="03515-124">Operatorzy bezsilnikowy plus i minus</span><span class="sxs-lookup"><span data-stu-id="03515-124">Unary plus and minus operators</span></span>

<span data-ttu-id="03515-125">Operator unary `+` zwraca wartość swojego operandu.</span><span class="sxs-lookup"><span data-stu-id="03515-125">The unary `+` operator returns the value of its operand.</span></span> <span data-ttu-id="03515-126">Operator unary `-` oblicza numeryczną negacja jego operandu.</span><span class="sxs-lookup"><span data-stu-id="03515-126">The unary `-` operator computes the numeric negation of its operand.</span></span>

[!code-csharp-interactive[unary plus and minus](snippets/ArithmeticOperators.cs#UnaryPlusAndMinus)]

<span data-ttu-id="03515-127">[Ulong](../builtin-types/integral-numeric-types.md) type nie obsługuje operatora `-` unary.</span><span class="sxs-lookup"><span data-stu-id="03515-127">The [ulong](../builtin-types/integral-numeric-types.md) type doesn't support the unary `-` operator.</span></span>

## <a name="multiplication-operator-"></a><span data-ttu-id="03515-128">Operator mnożenia \*</span><span class="sxs-lookup"><span data-stu-id="03515-128">Multiplication operator \*</span></span>

<span data-ttu-id="03515-129">Operator `*` mnożenia oblicza iloczyn swoich operandów:</span><span class="sxs-lookup"><span data-stu-id="03515-129">The multiplication operator `*` computes the product of its operands:</span></span>

[!code-csharp-interactive[multiplication operator](snippets/ArithmeticOperators.cs#Multiplication)]

<span data-ttu-id="03515-130">Operator jednoargumentowy `*` jest [operatorem pośredniowym wskaźnika](pointer-related-operators.md#pointer-indirection-operator-).</span><span class="sxs-lookup"><span data-stu-id="03515-130">The unary `*` operator is the [pointer indirection operator](pointer-related-operators.md#pointer-indirection-operator-).</span></span>

## <a name="division-operator-"></a><span data-ttu-id="03515-131">Operator działu /</span><span class="sxs-lookup"><span data-stu-id="03515-131">Division operator /</span></span>

<span data-ttu-id="03515-132">Operator `/` podziału dzieli swój lewy operand przez jego prawy operand.</span><span class="sxs-lookup"><span data-stu-id="03515-132">The division operator `/` divides its left-hand operand by its right-hand operand.</span></span>

### <a name="integer-division"></a><span data-ttu-id="03515-133">Podział liczby całkowitej</span><span class="sxs-lookup"><span data-stu-id="03515-133">Integer division</span></span>

<span data-ttu-id="03515-134">W przypadku argumentów typów całkowitych wynik `/` operatora jest typu całkowitego i jest równy ilorazowi dwóch argumentów zaokrąglonych w kierunku zera:</span><span class="sxs-lookup"><span data-stu-id="03515-134">For the operands of integer types, the result of the `/` operator is of an integer type and equals the quotient of the two operands rounded towards zero:</span></span>

[!code-csharp-interactive[integer division](snippets/ArithmeticOperators.cs#IntegerDivision)]

<span data-ttu-id="03515-135">Aby uzyskać iloraz dwóch argumentów jako liczby zmiennoprzecinkowej, należy użyć `float`, `double`lub `decimal` typu:</span><span class="sxs-lookup"><span data-stu-id="03515-135">To obtain the quotient of the two operands as a floating-point number, use the `float`, `double`, or `decimal` type:</span></span>

[!code-csharp-interactive[integer as floating-point division](snippets/ArithmeticOperators.cs#IntegerAsFloatingPointDivision)]

### <a name="floating-point-division"></a><span data-ttu-id="03515-136">Podział zmiennoprzecinkowych</span><span class="sxs-lookup"><span data-stu-id="03515-136">Floating-point division</span></span>

<span data-ttu-id="03515-137">Dla `float`, `double`i `decimal` typy, wynik `/` operatora jest iloraz emancypów dwóch argumentów:</span><span class="sxs-lookup"><span data-stu-id="03515-137">For the `float`, `double`, and `decimal` types, the result of the `/` operator is the quotient of the two operands:</span></span>

[!code-csharp-interactive[floating-point division](snippets/ArithmeticOperators.cs#FloatingPointDivision)]

<span data-ttu-id="03515-138">Jeśli jednym z argumentów `decimal`jest , inny operand nie może `float` `double` być ani, `float` ani `double`, ponieważ ani nie jest niejawnie cabrio do `decimal`.</span><span class="sxs-lookup"><span data-stu-id="03515-138">If one of the operands is `decimal`, another operand can be neither `float` nor `double`, because neither `float` nor `double` is implicitly convertible to `decimal`.</span></span> <span data-ttu-id="03515-139">Należy jawnie przekonwertować `float` lub `double` `decimal` operand do typu.</span><span class="sxs-lookup"><span data-stu-id="03515-139">You must explicitly convert the `float` or `double` operand to the `decimal` type.</span></span> <span data-ttu-id="03515-140">Aby uzyskać więcej informacji o konwersjach między typami liczbowymi, zobacz [Wbudowane konwersje liczbowe](../builtin-types/numeric-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="03515-140">For more information about conversions between numeric types, see [Built-in numeric conversions](../builtin-types/numeric-conversions.md).</span></span>

## <a name="remainder-operator-"></a><span data-ttu-id="03515-141">Reszta operatora %</span><span class="sxs-lookup"><span data-stu-id="03515-141">Remainder operator %</span></span>

<span data-ttu-id="03515-142">Pozostały operator `%` oblicza pozostałą część po podzieleniu jego polewej operand przez jego prawostronny operand.</span><span class="sxs-lookup"><span data-stu-id="03515-142">The remainder operator `%` computes the remainder after dividing its left-hand operand by its right-hand operand.</span></span>

### <a name="integer-remainder"></a><span data-ttu-id="03515-143">Pozostała liczba całkowita</span><span class="sxs-lookup"><span data-stu-id="03515-143">Integer remainder</span></span>

<span data-ttu-id="03515-144">Dla operandów typów całkowitych `a % b` wynikiem jest wartość produkowana przez `a - (a / b) * b`.</span><span class="sxs-lookup"><span data-stu-id="03515-144">For the operands of integer types, the result of `a % b` is the value produced by `a - (a / b) * b`.</span></span> <span data-ttu-id="03515-145">Znak pozostałej reszty niezerowej jest taki sam jak w przypadku operandu po lewej stronie, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="03515-145">The sign of the non-zero remainder is the same as that of the left-hand operand, as the following example shows:</span></span>

[!code-csharp-interactive[integer remainder](snippets/ArithmeticOperators.cs#IntegerRemainder)]

<span data-ttu-id="03515-146">Metoda <xref:System.Math.DivRem%2A?displayProperty=nameWithType> służy do obliczania zarówno podziału liczby całkowitej, jak i pozostałych wyników.</span><span class="sxs-lookup"><span data-stu-id="03515-146">Use the <xref:System.Math.DivRem%2A?displayProperty=nameWithType> method to compute both integer division and remainder results.</span></span>

### <a name="floating-point-remainder"></a><span data-ttu-id="03515-147">Pozostała część zmiennoprzecinkową</span><span class="sxs-lookup"><span data-stu-id="03515-147">Floating-point remainder</span></span>

<span data-ttu-id="03515-148">W `float` przypadku `double` argumentów, wynikiem `x % y` dla `x` skończonego `y` i `z` jest wartość taka, że</span><span class="sxs-lookup"><span data-stu-id="03515-148">For the `float` and `double` operands, the result of `x % y` for the finite `x` and `y` is the value `z` such that</span></span>

- <span data-ttu-id="03515-149">Znak `z`, jeśli nie zero, jest taki sam `x`jak znak .</span><span class="sxs-lookup"><span data-stu-id="03515-149">The sign of `z`, if non-zero, is the same as the sign of `x`.</span></span>
- <span data-ttu-id="03515-150">Wartość bezwzględna `z` jest wartością `|x| - n * |y|` `n` wytwarzaną przez to, gdzie jest to `|x| / |y|` największa `|x|` `|y|` możliwa liczba `x` całkowita, która jest mniejsza lub równa i są wartościami bezwzględnymi i `y`, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="03515-150">The absolute value of `z` is the value produced by `|x| - n * |y|` where `n` is the largest possible integer that is less than or equal to `|x| / |y|` and `|x|` and `|y|` are the absolute values of `x` and `y`, respectively.</span></span>

> [!NOTE]
> <span data-ttu-id="03515-151">Ta metoda obliczania pozostałej kwoty jest analogiczna do metody stosowanej w przypadku operacji całkowitych, ale różni się od specyfikacji IEEE 754.</span><span class="sxs-lookup"><span data-stu-id="03515-151">This method of computing the remainder is analogous to that used for integer operands, but different from the IEEE 754 specification.</span></span> <span data-ttu-id="03515-152">Jeśli potrzebujesz pozostałej operacji zgodnej ze specyfikacją IEEE <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType> 754, użyj tej metody.</span><span class="sxs-lookup"><span data-stu-id="03515-152">If you need the remainder operation that complies with the IEEE 754 specification, use the <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="03515-153">Aby uzyskać informacje na `%` temat zachowania operatora z nieskończonych operandów, zobacz [reszta operator](~/_csharplang/spec/expressions.md#remainder-operator) sekcji [specyfikacji języka C#.](~/_csharplang/spec/introduction.md)</span><span class="sxs-lookup"><span data-stu-id="03515-153">For information about the behavior of the `%` operator with non-finite operands, see the [Remainder operator](~/_csharplang/spec/expressions.md#remainder-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="03515-154">W `decimal` przypadku operandów pozostały `%` operator jest odpowiednikiem <xref:System.Decimal?displayProperty=nameWithType> [pozostałego operatora](<xref:System.Decimal.op_Modulus(System.Decimal,System.Decimal)>) typu.</span><span class="sxs-lookup"><span data-stu-id="03515-154">For the `decimal` operands, the remainder operator `%` is equivalent to the [remainder operator](<xref:System.Decimal.op_Modulus(System.Decimal,System.Decimal)>) of the <xref:System.Decimal?displayProperty=nameWithType> type.</span></span>

<span data-ttu-id="03515-155">W poniższym przykładzie przedstawiono zachowanie pozostałego operatora z argumentami zmiennoprzecinkowych:</span><span class="sxs-lookup"><span data-stu-id="03515-155">The following example demonstrates the behavior of the remainder operator with floating-point operands:</span></span>

[!code-csharp-interactive[floating-point remainder](snippets/ArithmeticOperators.cs#FloatingPointRemainder)]

## <a name="addition-operator-"></a><span data-ttu-id="03515-156">Operator dodawania +</span><span class="sxs-lookup"><span data-stu-id="03515-156">Addition operator +</span></span>

<span data-ttu-id="03515-157">Operator `+` dodawania oblicza sumę swoich argumentów:</span><span class="sxs-lookup"><span data-stu-id="03515-157">The addition operator `+` computes the sum of its operands:</span></span>

[!code-csharp-interactive[addition operator](snippets/ArithmeticOperators.cs#Addition)]

<span data-ttu-id="03515-158">Można również użyć `+` operatora dla kombinacji ciągów i delegować kombinacji.</span><span class="sxs-lookup"><span data-stu-id="03515-158">You also can use the `+` operator for string concatenation and delegate combination.</span></span> <span data-ttu-id="03515-159">Aby uzyskać więcej informacji, zobacz [ `+` artykuł `+=` i operatorów.](addition-operator.md)</span><span class="sxs-lookup"><span data-stu-id="03515-159">For more information, see the [`+` and `+=` operators](addition-operator.md) article.</span></span>

## <a name="subtraction-operator--"></a><span data-ttu-id="03515-160">Operator odejmowania -</span><span class="sxs-lookup"><span data-stu-id="03515-160">Subtraction operator -</span></span>

<span data-ttu-id="03515-161">Operator `-` odejmowania odejmuje swój prawy operand od lewego operandu:</span><span class="sxs-lookup"><span data-stu-id="03515-161">The subtraction operator `-` subtracts its right-hand operand from its left-hand operand:</span></span>

[!code-csharp-interactive[subtraction operator](snippets/ArithmeticOperators.cs#Subtraction)]

<span data-ttu-id="03515-162">Można również użyć `-` operatora do usuwania delegata.</span><span class="sxs-lookup"><span data-stu-id="03515-162">You also can use the `-` operator for delegate removal.</span></span> <span data-ttu-id="03515-163">Aby uzyskać więcej informacji, zobacz [ `-` artykuł `-=` i operatorów.](subtraction-operator.md)</span><span class="sxs-lookup"><span data-stu-id="03515-163">For more information, see the [`-` and `-=` operators](subtraction-operator.md) article.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="03515-164">Przypisanie złożone</span><span class="sxs-lookup"><span data-stu-id="03515-164">Compound assignment</span></span>

<span data-ttu-id="03515-165">Dla operatora `op`binarnego wyrażenie przypisania złożonego formularza</span><span class="sxs-lookup"><span data-stu-id="03515-165">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="03515-166">jest równoważny</span><span class="sxs-lookup"><span data-stu-id="03515-166">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="03515-167">chyba `x` że jest oceniana tylko raz.</span><span class="sxs-lookup"><span data-stu-id="03515-167">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="03515-168">W poniższym przykładzie przedstawiono użycie przypisania złożonego z operatorami arytmetycznymi:</span><span class="sxs-lookup"><span data-stu-id="03515-168">The following example demonstrates the usage of compound assignment with arithmetic operators:</span></span>

[!code-csharp-interactive[compound assignment](snippets/ArithmeticOperators.cs#CompoundAssignment)]

<span data-ttu-id="03515-169">Ze względu na [promocje liczbowe](~/_csharplang/spec/expressions.md#numeric-promotions)wynik `op` operacji może nie być `T` `x`niejawnie konwertowalny na typ .</span><span class="sxs-lookup"><span data-stu-id="03515-169">Because of [numeric promotions](~/_csharplang/spec/expressions.md#numeric-promotions), the result of the `op` operation might be not implicitly convertible to the type `T` of `x`.</span></span> <span data-ttu-id="03515-170">W takim przypadku, `op` jeśli jest wstępnie zdefiniowanyoperator i wynik operacji jest `T` jawnie konwertowalne na typ `x`, wyrażenie przypisania złożonego formularza `x op= y` jest równoważne `x = (T)(x op y)`, z wyjątkiem, że `x` jest oceniane tylko raz.</span><span class="sxs-lookup"><span data-stu-id="03515-170">In such a case, if `op` is a predefined operator and the result of the operation is explicitly convertible to the type `T` of `x`, a compound assignment expression of the form `x op= y` is equivalent to `x = (T)(x op y)`, except that `x` is only evaluated once.</span></span> <span data-ttu-id="03515-171">W poniższym przykładzie przedstawiono to zachowanie:</span><span class="sxs-lookup"><span data-stu-id="03515-171">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[compound assignment with cast](snippets/ArithmeticOperators.cs#CompoundAssignmentWithCast)]

<span data-ttu-id="03515-172">Użytkownik korzysta `+=` również `-=` z operatorów i do subskrybowania i rezygnacji z [subskrypcji wydarzenia,](../keywords/event.md)odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="03515-172">You also use the `+=` and `-=` operators to subscribe to and unsubscribe from an [event](../keywords/event.md), respectively.</span></span> <span data-ttu-id="03515-173">Aby uzyskać więcej informacji, zobacz [Jak subskrybować wydarzenia i zniej subskrybować je.](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)</span><span class="sxs-lookup"><span data-stu-id="03515-173">For more information, see [How to subscribe to and unsubscribe from events](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="operator-precedence-and-associativity"></a><span data-ttu-id="03515-174">Pierwszeństwo operatora i zespolenie</span><span class="sxs-lookup"><span data-stu-id="03515-174">Operator precedence and associativity</span></span>

<span data-ttu-id="03515-175">Następująca lista nakazuje operatorom arytmetycznym począwszy od najwyższego pierwszeństwa do najniższego:</span><span class="sxs-lookup"><span data-stu-id="03515-175">The following list orders arithmetic operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="03515-176">Operatory przyrostkowe `x++` i `x--` zmniejszania</span><span class="sxs-lookup"><span data-stu-id="03515-176">Postfix increment `x++` and decrement `x--` operators</span></span>
- <span data-ttu-id="03515-177">`++x` Przyrost prefiksu i `--x` dekrementacji i unary `+` i `-` operatorów</span><span class="sxs-lookup"><span data-stu-id="03515-177">Prefix increment `++x` and decrement `--x` and unary `+` and `-` operators</span></span>
- <span data-ttu-id="03515-178">`*`Mnożenie `/`i `%` operatory</span><span class="sxs-lookup"><span data-stu-id="03515-178">Multiplicative `*`, `/`, and `%` operators</span></span>
- <span data-ttu-id="03515-179">`+` Dodatki `-` i podmioty gospodarcze</span><span class="sxs-lookup"><span data-stu-id="03515-179">Additive `+` and `-` operators</span></span>

<span data-ttu-id="03515-180">Operatory arytmetyczne binarne są lewoskojarzone.</span><span class="sxs-lookup"><span data-stu-id="03515-180">Binary arithmetic operators are left-associative.</span></span> <span data-ttu-id="03515-181">Oznacza to, że operatory o tym samym poziomie pierwszeństwa są oceniane od lewej do prawej.</span><span class="sxs-lookup"><span data-stu-id="03515-181">That is, operators with the same precedence level are evaluated from left to right.</span></span>

<span data-ttu-id="03515-182">Użyj nawiasów, `()`, aby zmienić kolejność oceny narzuconą przez pierwszeństwo operatora i kojarzenie.</span><span class="sxs-lookup"><span data-stu-id="03515-182">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence and associativity.</span></span>

[!code-csharp-interactive[precedence and associativity](snippets/ArithmeticOperators.cs#PrecedenceAndAssociativity)]

<span data-ttu-id="03515-183">Aby uzyskać pełną listę operatorów Języka C# uporządkowane według poziomu pierwszeństwa, zobacz [pierwszeństwo operatora](index.md#operator-precedence) sekcji [operatorów C#artykułu.](index.md)</span><span class="sxs-lookup"><span data-stu-id="03515-183">For the complete list of C# operators ordered by precedence level, see the [Operator precedence](index.md#operator-precedence) section of the [C# operators](index.md) article.</span></span>

## <a name="arithmetic-overflow-and-division-by-zero"></a><span data-ttu-id="03515-184">Przepełnienie arytmetyczne i dzielenie przez zero</span><span class="sxs-lookup"><span data-stu-id="03515-184">Arithmetic overflow and division by zero</span></span>

<span data-ttu-id="03515-185">Gdy wynik operacji arytmetycznej wykracza poza zakres możliwych skończonych wartości typu liczbowego, zachowanie operatora arytmetycznego zależy od typu jego operandów.</span><span class="sxs-lookup"><span data-stu-id="03515-185">When the result of an arithmetic operation is outside the range of possible finite values of the involved numeric type, the behavior of an arithmetic operator depends on the type of its operands.</span></span>

### <a name="integer-arithmetic-overflow"></a><span data-ttu-id="03515-186">Całkowite przepełnienie arytmetyczne</span><span class="sxs-lookup"><span data-stu-id="03515-186">Integer arithmetic overflow</span></span>

<span data-ttu-id="03515-187">Podział całkowity przez zero zawsze <xref:System.DivideByZeroException>rzuca .</span><span class="sxs-lookup"><span data-stu-id="03515-187">Integer division by zero always throws a <xref:System.DivideByZeroException>.</span></span>

<span data-ttu-id="03515-188">W przypadku przepełnienia arytmetycznego liczby całkowitej kontekst sprawdzania przepełnienia, który można [sprawdzić lub odznaczyć,](../keywords/checked-and-unchecked.md)kontroluje wynikowe zachowanie:</span><span class="sxs-lookup"><span data-stu-id="03515-188">In case of integer arithmetic overflow, an overflow checking context, which can be [checked or unchecked](../keywords/checked-and-unchecked.md), controls the resulting behavior:</span></span>

- <span data-ttu-id="03515-189">W kontekście sprawdzonym jeśli przepełnienie dzieje się w wyrażeniu stałym, występuje błąd w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="03515-189">In a checked context, if overflow happens in a constant expression, a compile-time error occurs.</span></span> <span data-ttu-id="03515-190">W przeciwnym razie, gdy operacja jest <xref:System.OverflowException> wykonywana w czasie wykonywania, jest generowany.</span><span class="sxs-lookup"><span data-stu-id="03515-190">Otherwise, when the operation is performed at run time, an <xref:System.OverflowException> is thrown.</span></span>
- <span data-ttu-id="03515-191">W kontekście niezaznaczone wynik jest obcinane przez odrzucenie wszelkie bity wysokiego rzędu, które nie mieszczą się w typie docelowym.</span><span class="sxs-lookup"><span data-stu-id="03515-191">In an unchecked context, the result is truncated by discarding any high-order bits that don't fit in the destination type.</span></span>

<span data-ttu-id="03515-192">Wraz z [instrukcjami zaznaczone i niezaznaczone,](../keywords/checked-and-unchecked.md) można użyć `checked` i `unchecked` operatorów do kontrolowania kontekstu sprawdzania przepełnienia, w którym wyrażenie jest oceniane:</span><span class="sxs-lookup"><span data-stu-id="03515-192">Along with the [checked and unchecked](../keywords/checked-and-unchecked.md) statements, you can use the `checked` and `unchecked` operators to control the overflow checking context, in which an expression is evaluated:</span></span>

[!code-csharp-interactive[checked and unchecked](snippets/ArithmeticOperators.cs#CheckedUnchecked)]

<span data-ttu-id="03515-193">Domyślnie operacje arytmetyczne występują w *niezaznaczonej* kontekście.</span><span class="sxs-lookup"><span data-stu-id="03515-193">By default, arithmetic operations occur in an *unchecked* context.</span></span>

### <a name="floating-point-arithmetic-overflow"></a><span data-ttu-id="03515-194">Przepełnienie arytmetyczne zmiennoprzecinkowe</span><span class="sxs-lookup"><span data-stu-id="03515-194">Floating-point arithmetic overflow</span></span>

<span data-ttu-id="03515-195">Operacje arytmetyczne `float` z `double` i typów nigdy nie zgłaszać wyjątek.</span><span class="sxs-lookup"><span data-stu-id="03515-195">Arithmetic operations with the `float` and `double` types never throw an exception.</span></span> <span data-ttu-id="03515-196">Wynik operacji arytmetycznych z tymi typami może być jedną ze specjalnych wartości, które reprezentują nieskończoność, a nie liczbę:</span><span class="sxs-lookup"><span data-stu-id="03515-196">The result of arithmetic operations with those types can be one of special values that represent infinity and not-a-number:</span></span>

[!code-csharp-interactive[double non-finite values](snippets/ArithmeticOperators.cs#FloatingPointOverflow)]

<span data-ttu-id="03515-197">Dla operandów `decimal` typu, przepełnienie arytmetyczne zawsze <xref:System.OverflowException> rzuca i podział przez <xref:System.DivideByZeroException>zero zawsze rzuca .</span><span class="sxs-lookup"><span data-stu-id="03515-197">For the operands of the `decimal` type, arithmetic overflow always throws an <xref:System.OverflowException> and division by zero always throws a <xref:System.DivideByZeroException>.</span></span>

## <a name="round-off-errors"></a><span data-ttu-id="03515-198">Błędy zaokrąglania</span><span class="sxs-lookup"><span data-stu-id="03515-198">Round-off errors</span></span>

<span data-ttu-id="03515-199">Ze względu na ogólne ograniczenia przestawnej reprezentacji liczb rzeczywistych i arytmetyki zmiennoprzecinkowej, błędy zaokrąglania mogą występować w obliczeniach z typami zmiennoprzecinkowymi.</span><span class="sxs-lookup"><span data-stu-id="03515-199">Because of general limitations of the floating-point representation of real numbers and floating-point arithmetic, round-off errors might occur in calculations with floating-point types.</span></span> <span data-ttu-id="03515-200">Oznacza to, że wynik wyrażenia może różnić się od oczekiwanego wyniku matematycznego.</span><span class="sxs-lookup"><span data-stu-id="03515-200">That is, the produced result of an expression might differ from the expected mathematical result.</span></span> <span data-ttu-id="03515-201">Poniższy przykład pokazuje kilka takich przypadków:</span><span class="sxs-lookup"><span data-stu-id="03515-201">The following example demonstrates several such cases:</span></span>

[!code-csharp-interactive[round-off errors](snippets/ArithmeticOperators.cs#RoundOffErrors)]

<span data-ttu-id="03515-202">Aby uzyskać więcej informacji, zobacz uwagi na stronach odniesienia [System.Double](/dotnet/api/system.double#remarks), [System.Single](/dotnet/api/system.single#remarks)lub [System.Decimal.](/dotnet/api/system.decimal#remarks)</span><span class="sxs-lookup"><span data-stu-id="03515-202">For more information, see remarks at the [System.Double](/dotnet/api/system.double#remarks), [System.Single](/dotnet/api/system.single#remarks), or [System.Decimal](/dotnet/api/system.decimal#remarks) reference pages.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="03515-203">Przeciążenie operatora</span><span class="sxs-lookup"><span data-stu-id="03515-203">Operator overloadability</span></span>

<span data-ttu-id="03515-204">Typ zdefiniowany przez użytkownika może [przeciążać](operator-overloading.md) operatory arytmetyczne `%` `+`bezzasadne (`++` `--`, `+`, i ) i `-`binarne (`*`, `/`, , i ) operatory `-`arytmetyczne.</span><span class="sxs-lookup"><span data-stu-id="03515-204">A user-defined type can [overload](operator-overloading.md) the unary (`++`, `--`, `+`, and `-`) and binary (`*`, `/`, `%`, `+`, and `-`) arithmetic operators.</span></span> <span data-ttu-id="03515-205">Gdy operator binarny jest przeciążony, odpowiedni operator przypisania złożonego jest również niejawnie przeciążony.</span><span class="sxs-lookup"><span data-stu-id="03515-205">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="03515-206">Typ zdefiniowany przez użytkownika nie może jawnie przeciążać operatora przypisania złożonego.</span><span class="sxs-lookup"><span data-stu-id="03515-206">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="03515-207">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="03515-207">C# language specification</span></span>

<span data-ttu-id="03515-208">Aby uzyskać więcej informacji, zobacz następujące sekcje [specyfikacji języka Języka C#:](~/_csharplang/spec/introduction.md)</span><span class="sxs-lookup"><span data-stu-id="03515-208">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="03515-209">Operatory przyrostkowe i zmniejszania</span><span class="sxs-lookup"><span data-stu-id="03515-209">Postfix increment and decrement operators</span></span>](~/_csharplang/spec/expressions.md#postfix-increment-and-decrement-operators)
- [<span data-ttu-id="03515-210">Operatory przyrostu prefiksu i zmniejszania</span><span class="sxs-lookup"><span data-stu-id="03515-210">Prefix increment and decrement operators</span></span>](~/_csharplang/spec/expressions.md#prefix-increment-and-decrement-operators)
- [<span data-ttu-id="03515-211">Operator Unary plus</span><span class="sxs-lookup"><span data-stu-id="03515-211">Unary plus operator</span></span>](~/_csharplang/spec/expressions.md#unary-plus-operator)
- [<span data-ttu-id="03515-212">Operator minus nieary</span><span class="sxs-lookup"><span data-stu-id="03515-212">Unary minus operator</span></span>](~/_csharplang/spec/expressions.md#unary-minus-operator)
- [<span data-ttu-id="03515-213">Operator mnożenia</span><span class="sxs-lookup"><span data-stu-id="03515-213">Multiplication operator</span></span>](~/_csharplang/spec/expressions.md#multiplication-operator)
- [<span data-ttu-id="03515-214">Operator oddziału</span><span class="sxs-lookup"><span data-stu-id="03515-214">Division operator</span></span>](~/_csharplang/spec/expressions.md#division-operator)
- [<span data-ttu-id="03515-215">Operator pozostałej części</span><span class="sxs-lookup"><span data-stu-id="03515-215">Remainder operator</span></span>](~/_csharplang/spec/expressions.md#remainder-operator)
- [<span data-ttu-id="03515-216">Operator dodawania</span><span class="sxs-lookup"><span data-stu-id="03515-216">Addition operator</span></span>](~/_csharplang/spec/expressions.md#addition-operator)
- [<span data-ttu-id="03515-217">Operator odejmowania</span><span class="sxs-lookup"><span data-stu-id="03515-217">Subtraction operator</span></span>](~/_csharplang/spec/expressions.md#subtraction-operator)
- [<span data-ttu-id="03515-218">Przypisanie złożone</span><span class="sxs-lookup"><span data-stu-id="03515-218">Compound assignment</span></span>](~/_csharplang/spec/expressions.md#compound-assignment)
- [<span data-ttu-id="03515-219">Sprawdzone i niesprawdzone operatory</span><span class="sxs-lookup"><span data-stu-id="03515-219">The checked and unchecked operators</span></span>](~/_csharplang/spec/expressions.md#the-checked-and-unchecked-operators)
- [<span data-ttu-id="03515-220">Promocje numeryczne</span><span class="sxs-lookup"><span data-stu-id="03515-220">Numeric promotions</span></span>](~/_csharplang/spec/expressions.md#numeric-promotions)

## <a name="see-also"></a><span data-ttu-id="03515-221">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="03515-221">See also</span></span>

- [<span data-ttu-id="03515-222">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="03515-222">C# reference</span></span>](../index.md)
- [<span data-ttu-id="03515-223">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="03515-223">C# operators</span></span>](index.md)
- <xref:System.Math?displayProperty=nameWithType>
- <xref:System.MathF?displayProperty=nameWithType>
- [<span data-ttu-id="03515-224">Wartości numeryczne na platformie .NET</span><span class="sxs-lookup"><span data-stu-id="03515-224">Numerics in .NET</span></span>](../../../standard/numerics.md)
