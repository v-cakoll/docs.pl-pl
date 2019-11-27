---
title: Operatory bitowe i przesunięcia C# — odwołanie
description: Dowiedz C# się więcej na temat operatorów, które wykonują bitowe operacje logiczne lub przesunięcia przy użyciu operandów typów całkowitych.
ms.date: 04/18/2019
author: pkulikov
f1_keywords:
- ~_CSharpKeyword
- <<_CSharpKeyword
- '>>_CSharpKeyword'
- '&_CSharpKeyword'
- ^_CSharpKeyword
- '|_CSharpKeyword'
helpviewer_keywords:
- bitwise logical operators [C#]
- shift operators [C#]
- tilde operator [C#]
- one's complement operator [C#]
- bitwise complement operator [C#]
- ~ operator [C#]
- left shift operator [C#]
- << operator [C#]
- right shift operator [C#]
- '>> operator [C#]'
- bitwise logical AND operator [C#]
- ampersand operator [C#]
- '& operator [C#]'
- bitwise logical exclusive OR operator [C#]
- bitwise logical XOR operator [C#]
- ^ operator [C#]
- bitwise logical OR operator [C#]
- '| operator [C#]'
ms.openlocfilehash: 27f7cf46bd3e344503f74527df34506d38ad4545
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428438"
---
# <a name="bitwise-and-shift-operators-c-reference"></a><span data-ttu-id="ee162-103">Operatory bitowe i przesunięciaC# (odwołanie)</span><span class="sxs-lookup"><span data-stu-id="ee162-103">Bitwise and shift operators (C# reference)</span></span>

<span data-ttu-id="ee162-104">Następujące operatory wykonują operacje bitowe lub przesunięcia przy użyciu operandów [całkowitych typów liczbowych](../builtin-types/integral-numeric-types.md) lub typu [char](../builtin-types/char.md) :</span><span class="sxs-lookup"><span data-stu-id="ee162-104">The following operators perform bitwise or shift operations with operands of the [integral numeric types](../builtin-types/integral-numeric-types.md) or the [char](../builtin-types/char.md) type:</span></span>

- <span data-ttu-id="ee162-105">Operator jednoargumentowy [`~` (uzupełnienie bitowe)](#bitwise-complement-operator-)</span><span class="sxs-lookup"><span data-stu-id="ee162-105">Unary [`~` (bitwise complement)](#bitwise-complement-operator-) operator</span></span>
- <span data-ttu-id="ee162-106">Operatory przesunięcia`<<` binarnych [(LEFT SHIFT)](#left-shift-operator-) i [`>>` (prawy shift)](#right-shift-operator-)</span><span class="sxs-lookup"><span data-stu-id="ee162-106">Binary [`<<` (left shift)](#left-shift-operator-) and [`>>` (right shift)](#right-shift-operator-) shift operators</span></span>
- <span data-ttu-id="ee162-107">Binarne [`&` (logiczne i)](#logical-and-operator-), [`|` (logiczne lub)](#logical-or-operator-)i [`^` (logiczne wyłącznych lub)](#logical-exclusive-or-operator-)</span><span class="sxs-lookup"><span data-stu-id="ee162-107">Binary [`&` (logical AND)](#logical-and-operator-), [`|` (logical OR)](#logical-or-operator-), and [`^` (logical exclusive OR)](#logical-exclusive-or-operator-) operators</span></span>

<span data-ttu-id="ee162-108">Te operatory są zdefiniowane dla typów `int`, `uint`, `long`i `ulong`.</span><span class="sxs-lookup"><span data-stu-id="ee162-108">Those operators are defined for the `int`, `uint`, `long`, and `ulong` types.</span></span> <span data-ttu-id="ee162-109">Gdy oba operandy są innymi typami całkowitymi (`sbyte`, `byte`, `short`, `ushort`lub `char`), ich wartości są konwertowane na typ `int`, który jest również typem wyniku operacji.</span><span class="sxs-lookup"><span data-stu-id="ee162-109">When both operands are of other integral types (`sbyte`, `byte`, `short`, `ushort`, or `char`), their values are converted to the `int` type, which is also the result type of an operation.</span></span> <span data-ttu-id="ee162-110">Gdy operandy są różnymi typami całkowitymi, ich wartości są konwertowane na najbliższy typ całkowity.</span><span class="sxs-lookup"><span data-stu-id="ee162-110">When operands are of different integral types, their values are converted to the closest containing integral type.</span></span> <span data-ttu-id="ee162-111">Aby uzyskać więcej informacji, zobacz sekcję " [promocje liczbowe](~/_csharplang/spec/expressions.md#numeric-promotions) " [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="ee162-111">For more information, see the [Numeric promotions](~/_csharplang/spec/expressions.md#numeric-promotions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="ee162-112">Operatory `&`, `|`i `^` są również zdefiniowane dla argumentów operacji typu `bool`.</span><span class="sxs-lookup"><span data-stu-id="ee162-112">The `&`, `|`, and `^` operators are also defined for operands of the `bool` type.</span></span> <span data-ttu-id="ee162-113">Aby uzyskać więcej informacji, zobacz logiczne [Operatory logiczne](boolean-logical-operators.md).</span><span class="sxs-lookup"><span data-stu-id="ee162-113">For more information, see [Boolean logical operators](boolean-logical-operators.md).</span></span>

<span data-ttu-id="ee162-114">Operacje bitowe i przesunięcia nigdy nie powodują przepełnienia i tworzą te same wyniki w kontekstach [zaewidencjonowanych i](../keywords/checked-and-unchecked.md) niezaznaczone.</span><span class="sxs-lookup"><span data-stu-id="ee162-114">Bitwise and shift operations never cause overflow and produce the same results in [checked and unchecked](../keywords/checked-and-unchecked.md) contexts.</span></span>

## <a name="bitwise-complement-operator-"></a><span data-ttu-id="ee162-115">Operator uzupełnienia bitowego ~</span><span class="sxs-lookup"><span data-stu-id="ee162-115">Bitwise complement operator ~</span></span>

<span data-ttu-id="ee162-116">Operator `~` generuje bitowe uzupełnienie jego operandu przez odwrócenie każdego bitu:</span><span class="sxs-lookup"><span data-stu-id="ee162-116">The `~` operator produces a bitwise complement of its operand by reversing each bit:</span></span>

[!code-csharp-interactive[bitwise NOT](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseComplement)]

<span data-ttu-id="ee162-117">Można również użyć symbolu `~`, aby zadeklarować finalizatory.</span><span class="sxs-lookup"><span data-stu-id="ee162-117">You can also use the `~` symbol to declare finalizers.</span></span> <span data-ttu-id="ee162-118">Aby uzyskać więcej informacji, zobacz [finalizatory](../../programming-guide/classes-and-structs/destructors.md).</span><span class="sxs-lookup"><span data-stu-id="ee162-118">For more information, see [Finalizers](../../programming-guide/classes-and-structs/destructors.md).</span></span>

## <a name="left-shift-operator-"></a><span data-ttu-id="ee162-119">Operator przesunięcia w lewo \<\<</span><span class="sxs-lookup"><span data-stu-id="ee162-119">Left-shift operator \<\<</span></span>

<span data-ttu-id="ee162-120">Operator `<<` przesuwa swój lewy argument operacji w lewo o liczbę bitów określoną przez jego operand po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="ee162-120">The `<<` operator shifts its left-hand operand left by the number of bits defined by its right-hand operand.</span></span>

<span data-ttu-id="ee162-121">Operacja przesunięcia w lewo odrzuca bity o wysokim stopniu, które znajdują się poza zakresem wyników, i ustawia puste pozycje bitu w porządku o wartości zero, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="ee162-121">The left-shift operation discards the high-order bits that are outside the range of the result type and sets the low-order empty bit positions to zero, as the following example shows:</span></span>

[!code-csharp-interactive[left shift](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#LeftShift)]

<span data-ttu-id="ee162-122">Ponieważ operatory przesunięcia są zdefiniowane tylko dla typów `int`, `uint`, `long`i `ulong`, wynik operacji zawsze zawiera co najmniej 32 bitów.</span><span class="sxs-lookup"><span data-stu-id="ee162-122">Because the shift operators are defined only for the `int`, `uint`, `long`, and `ulong` types, the result of an operation always contains at least 32 bits.</span></span> <span data-ttu-id="ee162-123">Jeśli argument operacji po lewej stronie jest innego typu całkowitego (`sbyte`, `byte`, `short`, `ushort`lub `char`), jego wartość jest konwertowana na typ `int`, jak pokazano na poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="ee162-123">If the left-hand operand is of another integral type (`sbyte`, `byte`, `short`, `ushort`, or `char`), its value is converted to the `int` type, as the following example shows:</span></span>

[!code-csharp-interactive[left shift with promotion](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#LeftShiftPromoted)]

<span data-ttu-id="ee162-124">Aby uzyskać informacje o tym, jak argument operacji po prawej stronie operatora `<<` definiuje liczbę przesunięć, zobacz [Liczba przesunięć w sekcji operatory przesunięcia](#shift-count-of-the-shift-operators) .</span><span class="sxs-lookup"><span data-stu-id="ee162-124">For information about how the right-hand operand of the `<<` operator defines the shift count, see the [Shift count of the shift operators](#shift-count-of-the-shift-operators) section.</span></span>

## <a name="right-shift-operator-"></a><span data-ttu-id="ee162-125">Operator przesunięcia w prawo > ></span><span class="sxs-lookup"><span data-stu-id="ee162-125">Right-shift operator >></span></span>

<span data-ttu-id="ee162-126">Operator `>>` przesuwa swój lewy argument operacji bezpośrednio przez liczbę bitów zdefiniowanych przez swój operand z prawej strony.</span><span class="sxs-lookup"><span data-stu-id="ee162-126">The `>>` operator shifts its left-hand operand right by the number of bits defined by its right-hand operand.</span></span>

<span data-ttu-id="ee162-127">Operacja przesunięcia w prawo powoduje odrzucenie bitów o niskiej kolejności, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="ee162-127">The right-shift operation discards the low-order bits, as the following example shows:</span></span>

[!code-csharp-interactive[right shift](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#RightShift)]

<span data-ttu-id="ee162-128">Puste pozycje w dużej kolejności są ustawiane na podstawie typu operandu po lewej stronie w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="ee162-128">The high-order empty bit positions are set based on the type of the left-hand operand as follows:</span></span>

- <span data-ttu-id="ee162-129">Jeśli argument operacji po lewej stronie jest typu `int` lub `long`, operator przesunięcia w prawo wykonuje *arytmetyczne* przesunięcie: wartość najbardziej znaczącego bitu (bit znaku) operandu po lewej stronie jest propagowana do pustych pozycji o dużej liczbie bitów.</span><span class="sxs-lookup"><span data-stu-id="ee162-129">If the left-hand operand is of type `int` or `long`, the right-shift operator performs an *arithmetic* shift: the value of the most significant bit (the sign bit) of the left-hand operand is propagated to the high-order empty bit positions.</span></span> <span data-ttu-id="ee162-130">Oznacza to, że puste pozycje bitu o wysokim stopniu kolejności są ustawione na zero, jeśli argument operacji po lewej stronie jest nieujemny i ustawiony na jeden, jeśli jest ujemny.</span><span class="sxs-lookup"><span data-stu-id="ee162-130">That is, the high-order empty bit positions are set to zero if the left-hand operand is non-negative and set to one if it's negative.</span></span>

  [!code-csharp-interactive[arithmetic right shift](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#ArithmeticRightShift)]

- <span data-ttu-id="ee162-131">Jeśli argument operacji po lewej stronie jest typu `uint` lub `ulong`, operator przesunięcia w prawo wykonuje *logiczne* przesunięcie: wartość pustych pozycji w kolejności pustej jest zawsze równa zero.</span><span class="sxs-lookup"><span data-stu-id="ee162-131">If the left-hand operand is of type `uint` or `ulong`, the right-shift operator performs a *logical* shift: the high-order empty bit positions are always set to zero.</span></span>

  [!code-csharp-interactive[logical right shift](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#LogicalRightShift)]

<span data-ttu-id="ee162-132">Aby uzyskać informacje o tym, jak argument operacji po prawej stronie operatora `>>` definiuje liczbę przesunięć, zobacz [Liczba przesunięć w sekcji operatory przesunięcia](#shift-count-of-the-shift-operators) .</span><span class="sxs-lookup"><span data-stu-id="ee162-132">For information about how the right-hand operand of the `>>` operator defines the shift count, see the [Shift count of the shift operators](#shift-count-of-the-shift-operators) section.</span></span>

## <a name="logical-and-operator-"></a><span data-ttu-id="ee162-133">Operatory logiczne i &amp;</span><span class="sxs-lookup"><span data-stu-id="ee162-133">Logical AND operator &amp;</span></span>

<span data-ttu-id="ee162-134">Operator `&` oblicza koniunkcję bitową i jej operandy:</span><span class="sxs-lookup"><span data-stu-id="ee162-134">The `&` operator computes the bitwise logical AND of its operands:</span></span>

[!code-csharp-interactive[bitwise AND](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseAnd)]

<span data-ttu-id="ee162-135">Dla argumentów operacji `bool` operator `&` oblicza wartość [logiczną i](boolean-logical-operators.md#logical-and-operator-) jej operandów.</span><span class="sxs-lookup"><span data-stu-id="ee162-135">For `bool` operands, the `&` operator computes the [logical AND](boolean-logical-operators.md#logical-and-operator-) of its operands.</span></span> <span data-ttu-id="ee162-136">Jednoargumentowy operator `&` jest [operatorem address-of](pointer-related-operators.md#address-of-operator-).</span><span class="sxs-lookup"><span data-stu-id="ee162-136">The unary `&` operator is the [address-of operator](pointer-related-operators.md#address-of-operator-).</span></span>

## <a name="logical-exclusive-or-operator-"></a><span data-ttu-id="ee162-137">Operator wyłączny logicznego OR ^</span><span class="sxs-lookup"><span data-stu-id="ee162-137">Logical exclusive OR operator ^</span></span>

<span data-ttu-id="ee162-138">Operator `^` oblicza koniunkcję bitową na wyłączność lub, znaną również jako bitowe koniunkcja logiczna XOR, argumentów operacji:</span><span class="sxs-lookup"><span data-stu-id="ee162-138">The `^` operator computes the bitwise logical exclusive OR, also known as the bitwise logical XOR, of its operands:</span></span>

[!code-csharp-interactive[bitwise XOR](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseXor)]

<span data-ttu-id="ee162-139">Dla argumentów operacji `bool` operator `^` oblicza wartość [logiczną na wyłączność lub](boolean-logical-operators.md#logical-exclusive-or-operator-) z jej argumentów operacji.</span><span class="sxs-lookup"><span data-stu-id="ee162-139">For `bool` operands, the `^` operator computes the [logical exclusive OR](boolean-logical-operators.md#logical-exclusive-or-operator-) of its operands.</span></span>

## <a name="logical-or-operator-"></a><span data-ttu-id="ee162-140">Operator logiczny OR |</span><span class="sxs-lookup"><span data-stu-id="ee162-140">Logical OR operator |</span></span>

<span data-ttu-id="ee162-141">Operator `|` oblicza bitowe logiczne lub jego operandy:</span><span class="sxs-lookup"><span data-stu-id="ee162-141">The `|` operator computes the bitwise logical OR of its operands:</span></span>

[!code-csharp-interactive[bitwise OR](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseOr)]

<span data-ttu-id="ee162-142">Dla argumentów operacji `bool` operator `|` oblicza wartość [logiczną lub](boolean-logical-operators.md#logical-or-operator-) argumentów operacji.</span><span class="sxs-lookup"><span data-stu-id="ee162-142">For `bool` operands, the `|` operator computes the [logical OR](boolean-logical-operators.md#logical-or-operator-) of its operands.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="ee162-143">Przypisanie złożone</span><span class="sxs-lookup"><span data-stu-id="ee162-143">Compound assignment</span></span>

<span data-ttu-id="ee162-144">Dla operatora binarnego `op`wyrażenie złożonego przypisania formularza</span><span class="sxs-lookup"><span data-stu-id="ee162-144">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="ee162-145">jest równoważny</span><span class="sxs-lookup"><span data-stu-id="ee162-145">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="ee162-146">z tą różnicą, że `x` są oceniane tylko raz.</span><span class="sxs-lookup"><span data-stu-id="ee162-146">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="ee162-147">Poniższy przykład ilustruje użycie przypisania złożonego z operatory bitowe i przesunięcia:</span><span class="sxs-lookup"><span data-stu-id="ee162-147">The following example demonstrates the usage of compound assignment with bitwise and shift operators:</span></span>

[!code-csharp-interactive[compound assignment](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#CompoundAssignment)]

<span data-ttu-id="ee162-148">Ze względu na [promocje liczbowe](~/_csharplang/spec/expressions.md#numeric-promotions)wynik operacji `op` może nie być niejawnie konwertowany na typ `T` `x`.</span><span class="sxs-lookup"><span data-stu-id="ee162-148">Because of [numeric promotions](~/_csharplang/spec/expressions.md#numeric-promotions), the result of the `op` operation might be not implicitly convertible to the type `T` of `x`.</span></span> <span data-ttu-id="ee162-149">W takim przypadku, jeśli `op` jest wstępnie zdefiniowanym operatorem, a wynik operacji jest jawnie konwertowany na typ `T` `x`, wyrażenie przypisania złożonego `x op= y` jest równoważne z `x = (T)(x op y)`, z tą różnicą, że `x` są oceniane tylko raz.</span><span class="sxs-lookup"><span data-stu-id="ee162-149">In such a case, if `op` is a predefined operator and the result of the operation is explicitly convertible to the type `T` of `x`, a compound assignment expression of the form `x op= y` is equivalent to `x = (T)(x op y)`, except that `x` is only evaluated once.</span></span> <span data-ttu-id="ee162-150">Poniższy przykład ilustruje takie zachowanie:</span><span class="sxs-lookup"><span data-stu-id="ee162-150">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[compound assignment with cast](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#CompoundAssignmentWithCast)]

## <a name="operator-precedence"></a><span data-ttu-id="ee162-151">Pierwszeństwo operatorów</span><span class="sxs-lookup"><span data-stu-id="ee162-151">Operator precedence</span></span>

<span data-ttu-id="ee162-152">Poniższa lista porządkuje operatory bitowe i przesunięcia, rozpoczynając od najwyższego priorytetu do najniższego:</span><span class="sxs-lookup"><span data-stu-id="ee162-152">The following list orders bitwise and shift operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="ee162-153">`~` operatora uzupełniania bitowego</span><span class="sxs-lookup"><span data-stu-id="ee162-153">Bitwise complement operator `~`</span></span>
- <span data-ttu-id="ee162-154">Operatory przesunięcia `<<` i `>>`</span><span class="sxs-lookup"><span data-stu-id="ee162-154">Shift operators `<<` and `>>`</span></span>
- <span data-ttu-id="ee162-155">Operatory logiczne i `&`</span><span class="sxs-lookup"><span data-stu-id="ee162-155">Logical AND operator `&`</span></span>
- <span data-ttu-id="ee162-156">`^` operatora logicznego wyłącznego OR</span><span class="sxs-lookup"><span data-stu-id="ee162-156">Logical exclusive OR operator `^`</span></span>
- <span data-ttu-id="ee162-157">`|` operatora logicznego OR</span><span class="sxs-lookup"><span data-stu-id="ee162-157">Logical OR operator `|`</span></span>

<span data-ttu-id="ee162-158">Użyj nawiasów `()`, aby zmienić kolejność oceny nałożona przez pierwszeństwo operatorów:</span><span class="sxs-lookup"><span data-stu-id="ee162-158">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence:</span></span>

[!code-csharp-interactive[operator precedence](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#Precedence)]

<span data-ttu-id="ee162-159">Aby uzyskać pełną listę C# operatorów uporządkowanych według poziomu pierwszeństwa, zobacz sekcję [pierwszeństwo](index.md#operator-precedence) operatorów w artykule [ C# Operators](index.md) .</span><span class="sxs-lookup"><span data-stu-id="ee162-159">For the complete list of C# operators ordered by precedence level, see the [Operator precedence](index.md#operator-precedence) section of the [C# operators](index.md) article.</span></span>

## <a name="shift-count-of-the-shift-operators"></a><span data-ttu-id="ee162-160">Liczba przesunięć operatorów przesunięcia</span><span class="sxs-lookup"><span data-stu-id="ee162-160">Shift count of the shift operators</span></span>

<span data-ttu-id="ee162-161">Dla operatorów przesunięcia `<<` i `>>`typ operandu po prawej stronie musi być `int` lub typem, który ma [wstępnie zdefiniowaną niejawną konwersję liczbową](../builtin-types/numeric-conversions.md#implicit-numeric-conversions) do `int`.</span><span class="sxs-lookup"><span data-stu-id="ee162-161">For the shift operators `<<` and `>>`, the type of the right-hand operand must be `int` or a type that has a [predefined implicit numeric conversion](../builtin-types/numeric-conversions.md#implicit-numeric-conversions) to `int`.</span></span>

<span data-ttu-id="ee162-162">W przypadku wyrażeń `x << count` i `x >> count` rzeczywista liczba przesunięć zależy od typu `x` w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="ee162-162">For the `x << count` and `x >> count` expressions, the actual shift count depends on the type of `x` as follows:</span></span>

- <span data-ttu-id="ee162-163">Jeśli typ `x` jest `int` lub `uint`, liczba przesunięć jest definiowana przez *pięć* bitów z prawej strony.</span><span class="sxs-lookup"><span data-stu-id="ee162-163">If the type of `x` is `int` or `uint`, the shift count is defined by the low-order *five* bits of the right-hand operand.</span></span> <span data-ttu-id="ee162-164">Oznacza to, że licznik przesunięć jest obliczany na podstawie `count & 0x1F` (lub `count & 0b_1_1111`).</span><span class="sxs-lookup"><span data-stu-id="ee162-164">That is, the shift count is computed from `count & 0x1F` (or `count & 0b_1_1111`).</span></span>

- <span data-ttu-id="ee162-165">Jeśli typ `x` jest `long` lub `ulong`, licznik przesunięć jest definiowany przez *sześć* -znaczących bitów operandu po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="ee162-165">If the type of `x` is `long` or `ulong`, the shift count is defined by the low-order *six* bits of the right-hand operand.</span></span> <span data-ttu-id="ee162-166">Oznacza to, że licznik przesunięć jest obliczany na podstawie `count & 0x3F` (lub `count & 0b_11_1111`).</span><span class="sxs-lookup"><span data-stu-id="ee162-166">That is, the shift count is computed from `count & 0x3F` (or `count & 0b_11_1111`).</span></span>

<span data-ttu-id="ee162-167">Poniższy przykład ilustruje takie zachowanie:</span><span class="sxs-lookup"><span data-stu-id="ee162-167">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[shift count example](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#ShiftCount)]

## <a name="enumeration-logical-operators"></a><span data-ttu-id="ee162-168">Wyliczanie operatorów logicznych</span><span class="sxs-lookup"><span data-stu-id="ee162-168">Enumeration logical operators</span></span>

<span data-ttu-id="ee162-169">Operatory `~`, `&`, `|`i `^` są również obsługiwane przez dowolny typ [wyliczeniowy](../keywords/enum.md) .</span><span class="sxs-lookup"><span data-stu-id="ee162-169">The `~`, `&`, `|`, and `^` operators are also supported by any [enumeration](../keywords/enum.md) type.</span></span> <span data-ttu-id="ee162-170">Dla operandów o tym samym typie wyliczeniowym operacja logiczna jest wykonywana na odpowiednich wartościach bazowego typu całkowitego.</span><span class="sxs-lookup"><span data-stu-id="ee162-170">For operands of the same enumeration type, a logical operation is performed on the corresponding values of the underlying integral type.</span></span> <span data-ttu-id="ee162-171">Na przykład dla dowolnych `x` i `y` typu wyliczenia `T` z typem podstawowym `U`, wyrażenie `x & y` generuje ten sam wynik jako wyrażenie `(T)((U)x & (U)y)`.</span><span class="sxs-lookup"><span data-stu-id="ee162-171">For example, for any `x` and `y` of an enumeration type `T` with an underlying type `U`, the `x & y` expression produces the same result as the `(T)((U)x & (U)y)` expression.</span></span>

<span data-ttu-id="ee162-172">Zwykle używane są bitowe operatory logiczne z typem wyliczenia, który jest zdefiniowany przy użyciu atrybutu [flags](xref:System.FlagsAttribute) .</span><span class="sxs-lookup"><span data-stu-id="ee162-172">You typically use bitwise logical operators with an enumeration type which is defined with the [Flags](xref:System.FlagsAttribute) attribute.</span></span> <span data-ttu-id="ee162-173">Aby uzyskać więcej informacji, zobacz sekcję [typy wyliczeniowe jako flagi bitowe](../../programming-guide/enumeration-types.md#enumeration-types-as-bit-flags) artykułu [typy wyliczeniowe](../../programming-guide/enumeration-types.md) .</span><span class="sxs-lookup"><span data-stu-id="ee162-173">For more information, see the [Enumeration types as bit flags](../../programming-guide/enumeration-types.md#enumeration-types-as-bit-flags) section of the [Enumeration types](../../programming-guide/enumeration-types.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="ee162-174">Przeciążanie operatora</span><span class="sxs-lookup"><span data-stu-id="ee162-174">Operator overloadability</span></span>

<span data-ttu-id="ee162-175">Typ zdefiniowany przez użytkownika może [przeciążać](operator-overloading.md) operatory `~`, `<<`, `>>`, `&`, `|`i `^`.</span><span class="sxs-lookup"><span data-stu-id="ee162-175">A user-defined type can [overload](operator-overloading.md) the `~`, `<<`, `>>`, `&`, `|`, and `^` operators.</span></span> <span data-ttu-id="ee162-176">Gdy operator binarny jest przeciążony, odpowiadający mu operator przypisania złożonego jest również niejawnie przeciążony.</span><span class="sxs-lookup"><span data-stu-id="ee162-176">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="ee162-177">Typ zdefiniowany przez użytkownika nie może jawnie przeciążać złożonego operatora przypisania.</span><span class="sxs-lookup"><span data-stu-id="ee162-177">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

<span data-ttu-id="ee162-178">Jeśli typ zdefiniowany przez użytkownika `T` przeciążania operatora `<<` lub `>>`, typem operandu po lewej stronie musi być `T`, a typ operacji po prawej stronie musi być `int`.</span><span class="sxs-lookup"><span data-stu-id="ee162-178">If a user-defined type `T` overloads the `<<` or `>>` operator, the type of the left-hand operand must be `T` and the type of the right-hand operand must be `int`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="ee162-179">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="ee162-179">C# language specification</span></span>

<span data-ttu-id="ee162-180">Aby uzyskać więcej informacji, zobacz następujące sekcje [ C# specyfikacji języka](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="ee162-180">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="ee162-181">Operator dopełnienia bitowego</span><span class="sxs-lookup"><span data-stu-id="ee162-181">Bitwise complement operator</span></span>](~/_csharplang/spec/expressions.md#bitwise-complement-operator)
- [<span data-ttu-id="ee162-182">Operatory przesunięcia</span><span class="sxs-lookup"><span data-stu-id="ee162-182">Shift operators</span></span>](~/_csharplang/spec/expressions.md#shift-operators)
- [<span data-ttu-id="ee162-183">Operatory logiczne</span><span class="sxs-lookup"><span data-stu-id="ee162-183">Logical operators</span></span>](~/_csharplang/spec/expressions.md#logical-operators)
- [<span data-ttu-id="ee162-184">Przypisanie złożone</span><span class="sxs-lookup"><span data-stu-id="ee162-184">Compound assignment</span></span>](~/_csharplang/spec/expressions.md#compound-assignment)
- [<span data-ttu-id="ee162-185">Promocje numeryczne</span><span class="sxs-lookup"><span data-stu-id="ee162-185">Numeric promotions</span></span>](~/_csharplang/spec/expressions.md#numeric-promotions)

## <a name="see-also"></a><span data-ttu-id="ee162-186">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ee162-186">See also</span></span>

- [<span data-ttu-id="ee162-187">C#odwoła</span><span class="sxs-lookup"><span data-stu-id="ee162-187">C# reference</span></span>](../index.md)
- [<span data-ttu-id="ee162-188">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="ee162-188">C# operators</span></span>](index.md)
- [<span data-ttu-id="ee162-189">Operatory logiczne Boolean</span><span class="sxs-lookup"><span data-stu-id="ee162-189">Boolean logical operators</span></span>](boolean-logical-operators.md)
