---
title: Bitowe i operatory przesunięcia - C# odwołania
description: Dowiedz się więcej o C# operatorów, które wykonują bitowe logicznej lub operacje przesunięcia z argumentów operacji typu całkowitoliczbowego.
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
ms.openlocfilehash: c18a06971887049a443f0bd1af7c77610a787a27
ms.sourcegitcommit: eaa6d5cd0f4e7189dbe0bd756e9f53508b01989e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/07/2019
ms.locfileid: "67609944"
---
# <a name="bitwise-and-shift-operators-c-reference"></a><span data-ttu-id="3f3f1-103">Bitowe i operatory przesunięcia (C# odwołania)</span><span class="sxs-lookup"><span data-stu-id="3f3f1-103">Bitwise and shift operators (C# reference)</span></span>

<span data-ttu-id="3f3f1-104">Następujące operatory bitowe wykonywania lub shift operacji przy użyciu argumentów operacji [typów całkowitych](../builtin-types/integral-numeric-types.md):</span><span class="sxs-lookup"><span data-stu-id="3f3f1-104">The following operators perform bitwise or shift operations with operands of the [integral types](../builtin-types/integral-numeric-types.md):</span></span>

- <span data-ttu-id="3f3f1-105">Jednoargumentowy [ `~` (dopełnienia bitowego)](#bitwise-complement-operator-) — operator</span><span class="sxs-lookup"><span data-stu-id="3f3f1-105">Unary [`~` (bitwise complement)](#bitwise-complement-operator-) operator</span></span>
- <span data-ttu-id="3f3f1-106">Binarny [ `<<` (przesunięcia w lewo)](#left-shift-operator-) i [ `>>` (przesunięcia bitowego w prawo)](#right-shift-operator-) operatory przesunięcia</span><span class="sxs-lookup"><span data-stu-id="3f3f1-106">Binary [`<<` (left shift)](#left-shift-operator-) and [`>>` (right shift)](#right-shift-operator-) shift operators</span></span>
- <span data-ttu-id="3f3f1-107">Binarny [ `&` (operator logiczny oraz)](#logical-and-operator-), [ `|` (operator logiczny lub)](#logical-or-operator-), i [ `^` (logiczne OR wyłączne)](#logical-exclusive-or-operator-) operatorów</span><span class="sxs-lookup"><span data-stu-id="3f3f1-107">Binary [`&` (logical AND)](#logical-and-operator-), [`|` (logical OR)](#logical-or-operator-), and [`^` (logical exclusive OR)](#logical-exclusive-or-operator-) operators</span></span>

<span data-ttu-id="3f3f1-108">Te operatory są zdefiniowane dla `int`, `uint`, `long`, i `ulong` typów.</span><span class="sxs-lookup"><span data-stu-id="3f3f1-108">Those operators are defined for the `int`, `uint`, `long`, and `ulong` types.</span></span> <span data-ttu-id="3f3f1-109">Gdy oba operandy są inne typy całkowitoliczbowe (`sbyte`, `byte`, `short`, `ushort`, lub `char`), ich wartości są konwertowane na `int` typ, który jest również typ wyniku operacji.</span><span class="sxs-lookup"><span data-stu-id="3f3f1-109">When both operands are of other integral types (`sbyte`, `byte`, `short`, `ushort`, or `char`), their values are converted to the `int` type, which is also the result type of an operation.</span></span> <span data-ttu-id="3f3f1-110">W przypadku argumentów operacji z różnymi typami całkowitymi, ich wartości są konwertowane do najbliższego zawierającego typu całkowitego.</span><span class="sxs-lookup"><span data-stu-id="3f3f1-110">When operands are of different integral types, their values are converted to the closest containing integral type.</span></span> <span data-ttu-id="3f3f1-111">Aby uzyskać więcej informacji, zobacz [promocji na liczbowe](~/_csharplang/spec/expressions.md#numeric-promotions) części [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="3f3f1-111">For more information, see the [Numeric promotions](~/_csharplang/spec/expressions.md#numeric-promotions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="3f3f1-112">`&`, `|`, I `^` operatory są również określone w przypadku argumentów operacji `bool` typu.</span><span class="sxs-lookup"><span data-stu-id="3f3f1-112">The `&`, `|`, and `^` operators are also defined for the operands of the `bool` type.</span></span> <span data-ttu-id="3f3f1-113">Aby uzyskać więcej informacji, zobacz [logiczna operatorów logicznych](boolean-logical-operators.md).</span><span class="sxs-lookup"><span data-stu-id="3f3f1-113">For more information, see [Boolean logical operators](boolean-logical-operators.md).</span></span>

<span data-ttu-id="3f3f1-114">Bitowe OR i operacje przesunięcia nigdy nie spowodować przepełnienie działają tak samo w [checked i unchecked](../keywords/checked-and-unchecked.md) kontekstów.</span><span class="sxs-lookup"><span data-stu-id="3f3f1-114">Bitwise and shift operations never cause overflow and produce the same results in [checked and unchecked](../keywords/checked-and-unchecked.md) contexts.</span></span>

## <a name="bitwise-complement-operator-"></a><span data-ttu-id="3f3f1-115">Operator dopełnienia bitowego ~</span><span class="sxs-lookup"><span data-stu-id="3f3f1-115">Bitwise complement operator ~</span></span>

<span data-ttu-id="3f3f1-116">`~` Operator wytwarza bitowe uzupełnienie swojego operandu odwracając każdy bit:</span><span class="sxs-lookup"><span data-stu-id="3f3f1-116">The `~` operator produces a bitwise complement of its operand by reversing each bit:</span></span>

[!code-csharp-interactive[bitwise NOT](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseComplement)]

<span data-ttu-id="3f3f1-117">Można również użyć `~` symbolu, aby zadeklarować finalizatorów.</span><span class="sxs-lookup"><span data-stu-id="3f3f1-117">You can also use the `~` symbol to declare finalizers.</span></span> <span data-ttu-id="3f3f1-118">Aby uzyskać więcej informacji, zobacz [finalizatory](../../programming-guide/classes-and-structs/destructors.md).</span><span class="sxs-lookup"><span data-stu-id="3f3f1-118">For more information, see [Finalizers](../../programming-guide/classes-and-structs/destructors.md).</span></span>

## <a name="left-shift-operator-"></a><span data-ttu-id="3f3f1-119">Operator przesunięcia w lewo \<\<</span><span class="sxs-lookup"><span data-stu-id="3f3f1-119">Left-shift operator \<\<</span></span>

<span data-ttu-id="3f3f1-120">`<<` Operator przenosi swojego operandu po lewej stronie, w lewo o liczbę bitów zdefiniowane przez jej argument po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="3f3f1-120">The `<<` operator shifts its left-hand operand left by the number of bits defined by its right-hand operand.</span></span>

<span data-ttu-id="3f3f1-121">Operacja przesunięcia w lewo odrzuca najbardziej znaczących bitów, które są poza zakresem typu wyniku i ustawia pozycje bitów pusty niskiego rzędu na zero, co ilustruje poniższy przykład:</span><span class="sxs-lookup"><span data-stu-id="3f3f1-121">The left-shift operation discards the high-order bits that are outside the range of the result type and sets the low-order empty bit positions to zero, as the following example shows:</span></span>

[!code-csharp-interactive[left shift](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#LeftShift)]

<span data-ttu-id="3f3f1-122">Ponieważ operatory przesunięcia, są zdefiniowane tylko w przypadku `int`, `uint`, `long`, i `ulong` typów, wynik operacji zawsze zawiera co najmniej 32-bitowy.</span><span class="sxs-lookup"><span data-stu-id="3f3f1-122">Because the shift operators are defined only for the `int`, `uint`, `long`, and `ulong` types, the result of an operation always contains at least 32 bits.</span></span> <span data-ttu-id="3f3f1-123">Jeśli argument po lewej stronie jest innego typu całkowitego (`sbyte`, `byte`, `short`, `ushort`, lub `char`), jego wartość jest konwertowana na `int` typu, co ilustruje poniższy przykład:</span><span class="sxs-lookup"><span data-stu-id="3f3f1-123">If the left-hand operand is of another integral type (`sbyte`, `byte`, `short`, `ushort`, or `char`), its value is converted to the `int` type, as the following example shows:</span></span>

[!code-csharp-interactive[left shift with promotion](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#LeftShiftPromoted)]

<span data-ttu-id="3f3f1-124">Aby uzyskać informacje na temat prawostronny operand `<<` operator definiuje licznik przesunięć, zobacz [licznik operatory przesunięcia przesunięć](#shift-count-of-the-shift-operators) sekcji.</span><span class="sxs-lookup"><span data-stu-id="3f3f1-124">For information about how the right-hand operand of the `<<` operator defines the shift count, see the [Shift count of the shift operators](#shift-count-of-the-shift-operators) section.</span></span>

## <a name="right-shift-operator-"></a><span data-ttu-id="3f3f1-125">Operator przesunięcia w prawo >></span><span class="sxs-lookup"><span data-stu-id="3f3f1-125">Right-shift operator >></span></span>

<span data-ttu-id="3f3f1-126">`>>` Operator przenosi jego lewostronny operand bezpośrednio przez liczbę bitów zdefiniowane przez jej argument po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="3f3f1-126">The `>>` operator shifts its left-hand operand right by the number of bits defined by its right-hand operand.</span></span>

<span data-ttu-id="3f3f1-127">Operacja przesunięcia w prawo powoduje odrzucenie mniej znaczące bity, co ilustruje poniższy przykład:</span><span class="sxs-lookup"><span data-stu-id="3f3f1-127">The right-shift operation discards the low-order bits, as the following example shows:</span></span>

[!code-csharp-interactive[right shift](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#RightShift)]

<span data-ttu-id="3f3f1-128">Pozycje bitów pusty wyższego rzędu jest ustawiona na podstawie typ operandu po lewej stronie w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="3f3f1-128">The high-order empty bit positions are set based on the type of the left-hand operand as follows:</span></span>

- <span data-ttu-id="3f3f1-129">Jeśli lewostronny operand jest typu [int](../builtin-types/integral-numeric-types.md) lub [długie](../builtin-types/integral-numeric-types.md), wykonuje operator przesunięcia w prawo *arytmetyczne* shift: wartość najbardziej znaczący bit (bit znaku) z Lewostronny operand jest propagowana do pozycji bitów pusty wyższego rzędu.</span><span class="sxs-lookup"><span data-stu-id="3f3f1-129">If the left-hand operand is of type [int](../builtin-types/integral-numeric-types.md) or [long](../builtin-types/integral-numeric-types.md), the right-shift operator performs an *arithmetic* shift: the value of the most significant bit (the sign bit) of the left-hand operand is propagated to the high-order empty bit positions.</span></span> <span data-ttu-id="3f3f1-130">Oznacza to, pozycje bitów pusty wyższego rzędu są ustawiane na zero, jeśli argument po lewej stronie jest ujemna i ustawiony na wartość 1, jeśli jest ujemna.</span><span class="sxs-lookup"><span data-stu-id="3f3f1-130">That is, the high-order empty bit positions are set to zero if the left-hand operand is non-negative and set to one if it's negative.</span></span>

  [!code-csharp-interactive[arithmetic right shift](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#ArithmeticRightShift)]

- <span data-ttu-id="3f3f1-131">Lewostronny operand jest typu [uint](../builtin-types/integral-numeric-types.md) lub [ulong](../builtin-types/integral-numeric-types.md), operator przesunięcia w prawo wykonuje *logiczne* shift: pozycje bitów pusty wyższego rzędu są zawsze ustawione na zero.</span><span class="sxs-lookup"><span data-stu-id="3f3f1-131">If the left-hand operand is of type [uint](../builtin-types/integral-numeric-types.md) or [ulong](../builtin-types/integral-numeric-types.md), the right-shift operator performs a *logical* shift: the high-order empty bit positions are always set to zero.</span></span>

  [!code-csharp-interactive[logical right shift](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#LogicalRightShift)]

<span data-ttu-id="3f3f1-132">Aby uzyskać informacje na temat prawostronny operand `>>` operator definiuje licznik przesunięć, zobacz [licznik operatory przesunięcia przesunięć](#shift-count-of-the-shift-operators) sekcji.</span><span class="sxs-lookup"><span data-stu-id="3f3f1-132">For information about how the right-hand operand of the `>>` operator defines the shift count, see the [Shift count of the shift operators](#shift-count-of-the-shift-operators) section.</span></span>

## <a name="logical-and-operator-"></a> <span data-ttu-id="3f3f1-133">Operator logiczny AND &amp;</span><span class="sxs-lookup"><span data-stu-id="3f3f1-133">Logical AND operator &amp;</span></span>

<span data-ttu-id="3f3f1-134">`&` Operator oblicza iloczynu bitowego AND logiczne z argumentów:</span><span class="sxs-lookup"><span data-stu-id="3f3f1-134">The `&` operator computes the bitwise logical AND of its operands:</span></span>

[!code-csharp-interactive[bitwise AND](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseAnd)]

<span data-ttu-id="3f3f1-135">Dla argumentów operacji `bool` typu `&` oblicza operator [operator logiczny oraz](boolean-logical-operators.md#logical-and-operator-) z argumentów.</span><span class="sxs-lookup"><span data-stu-id="3f3f1-135">For the operands of the `bool` type, the `&` operator computes the [logical AND](boolean-logical-operators.md#logical-and-operator-) of its operands.</span></span> <span data-ttu-id="3f3f1-136">Jednoargumentowy `&` operator jest [operatora address-of](pointer-related-operators.md#address-of-operator-).</span><span class="sxs-lookup"><span data-stu-id="3f3f1-136">The unary `&` operator is the [address-of operator](pointer-related-operators.md#address-of-operator-).</span></span>

## <a name="logical-exclusive-or-operator-"></a><span data-ttu-id="3f3f1-137">Operator logiczny OR wyłączne ^</span><span class="sxs-lookup"><span data-stu-id="3f3f1-137">Logical exclusive OR operator ^</span></span>

<span data-ttu-id="3f3f1-138">`^` Operator oblicza wyłączny sumy bitowej dla logicznej lub znany także jako bitowe XOR logiczne z argumentów:</span><span class="sxs-lookup"><span data-stu-id="3f3f1-138">The `^` operator computes the bitwise logical exclusive OR, also known as the bitwise logical XOR, of its operands:</span></span>

[!code-csharp-interactive[bitwise XOR](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseXor)]

<span data-ttu-id="3f3f1-139">Dla argumentów operacji `bool` typu `^` oblicza operator [logiczne OR wyłączne](boolean-logical-operators.md#logical-exclusive-or-operator-) z argumentów.</span><span class="sxs-lookup"><span data-stu-id="3f3f1-139">For the operands of the `bool` type, the `^` operator computes the [logical exclusive OR](boolean-logical-operators.md#logical-exclusive-or-operator-) of its operands.</span></span>

## <a name="logical-or-operator-"></a><span data-ttu-id="3f3f1-140">Operator logiczny OR |</span><span class="sxs-lookup"><span data-stu-id="3f3f1-140">Logical OR operator |</span></span>

<span data-ttu-id="3f3f1-141">`|` Operator oblicza bitowe OR logiczne z argumentów:</span><span class="sxs-lookup"><span data-stu-id="3f3f1-141">The `|` operator computes the bitwise logical OR of its operands:</span></span>

[!code-csharp-interactive[bitwise OR](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseOr)]

<span data-ttu-id="3f3f1-142">Dla argumentów operacji `bool` typu `|` oblicza operator [logiczne OR](boolean-logical-operators.md#logical-or-operator-) z argumentów.</span><span class="sxs-lookup"><span data-stu-id="3f3f1-142">For the operands of the `bool` type, the `|` operator computes the [logical OR](boolean-logical-operators.md#logical-or-operator-) of its operands.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="3f3f1-143">Przydział złożony</span><span class="sxs-lookup"><span data-stu-id="3f3f1-143">Compound assignment</span></span>

<span data-ttu-id="3f3f1-144">Dla operatora binarnego `op`, wyrażenie przypisania złożonego formularza</span><span class="sxs-lookup"><span data-stu-id="3f3f1-144">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="3f3f1-145">odpowiada wyrażeniu</span><span class="sxs-lookup"><span data-stu-id="3f3f1-145">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="3f3f1-146">z tą różnicą, że `x` jest obliczany tylko raz.</span><span class="sxs-lookup"><span data-stu-id="3f3f1-146">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="3f3f1-147">Poniższy przykład ilustruje użycie przydział złożony przy użyciu bitowego operatora i operatory przesunięcia:</span><span class="sxs-lookup"><span data-stu-id="3f3f1-147">The following example demonstrates the usage of compound assignment with bitwise and shift operators:</span></span>

[!code-csharp-interactive[compound assignment](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#CompoundAssignment)]

<span data-ttu-id="3f3f1-148">Z powodu [promocji na liczbowe](~/_csharplang/spec/expressions.md#numeric-promotions), wynikiem `op` operacji może nie być niejawnie konwertowane na typ `T` z `x`.</span><span class="sxs-lookup"><span data-stu-id="3f3f1-148">Because of [numeric promotions](~/_csharplang/spec/expressions.md#numeric-promotions), the result of the `op` operation might be not implicitly convertible to the type `T` of `x`.</span></span> <span data-ttu-id="3f3f1-149">W takim przypadku jeśli `op` jest wstępnie zdefiniowanego operatora, a wynik operacji jest jawnie konwertowany na typ `T` z `x`, wyrażenia przypisania złożonego w postaci `x op= y` jest odpowiednikiem `x = (T)(x op y)`, z wyjątkiem które `x` jest oceniane tylko raz.</span><span class="sxs-lookup"><span data-stu-id="3f3f1-149">In such a case, if `op` is a predefined operator and the result of the operation is explicitly convertible to the type `T` of `x`, a compound assignment expression of the form `x op= y` is equivalent to `x = (T)(x op y)`, except that `x` is only evaluated once.</span></span> <span data-ttu-id="3f3f1-150">Poniższy przykład przedstawia tego zachowania:</span><span class="sxs-lookup"><span data-stu-id="3f3f1-150">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[compound assignment with cast](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#CompoundAssignmentWithCast)]

## <a name="operator-precedence"></a><span data-ttu-id="3f3f1-151">Pierwszeństwo operatorów</span><span class="sxs-lookup"><span data-stu-id="3f3f1-151">Operator precedence</span></span>

<span data-ttu-id="3f3f1-152">Następujące listy zamówienia bitowe i operatory przesunięcia od najwyższy priorytet, do najniższego:</span><span class="sxs-lookup"><span data-stu-id="3f3f1-152">The following list orders bitwise and shift operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="3f3f1-153">Operator dopełnienia bitowego `~`</span><span class="sxs-lookup"><span data-stu-id="3f3f1-153">Bitwise complement operator `~`</span></span>
- <span data-ttu-id="3f3f1-154">Operatory przesunięcia `<<` i `>>`</span><span class="sxs-lookup"><span data-stu-id="3f3f1-154">Shift operators `<<` and `>>`</span></span>
- <span data-ttu-id="3f3f1-155">Operator logiczny AND `&`</span><span class="sxs-lookup"><span data-stu-id="3f3f1-155">Logical AND operator `&`</span></span>
- <span data-ttu-id="3f3f1-156">Operator logiczny OR wyłączne `^`</span><span class="sxs-lookup"><span data-stu-id="3f3f1-156">Logical exclusive OR operator `^`</span></span>
- <span data-ttu-id="3f3f1-157">Operator logiczny OR `|`</span><span class="sxs-lookup"><span data-stu-id="3f3f1-157">Logical OR operator `|`</span></span>

<span data-ttu-id="3f3f1-158">Użyj nawiasów, `()`, aby zmienić kolejność oceny nałożonych przez pierwszeństwo operatorów:</span><span class="sxs-lookup"><span data-stu-id="3f3f1-158">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence:</span></span>

[!code-csharp-interactive[operator precedence](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#Precedence)]

<span data-ttu-id="3f3f1-159">Aby uzyskać pełną listę C# operatory uporządkowane według poziomu priorytetu, zobacz [ C# operatory](index.md).</span><span class="sxs-lookup"><span data-stu-id="3f3f1-159">For the complete list of C# operators ordered by precedence level, see [C# operators](index.md).</span></span>

## <a name="shift-count-of-the-shift-operators"></a><span data-ttu-id="3f3f1-160">Licznik przesunięć operatorów przesunięcia</span><span class="sxs-lookup"><span data-stu-id="3f3f1-160">Shift count of the shift operators</span></span>

<span data-ttu-id="3f3f1-161">Dla operatorów przesunięcia `<<` i `>>`, typ prawostronny operand musi być [int](../builtin-types/integral-numeric-types.md) lub typ, który ma [wstępnie zdefiniowane niejawnych konwersji liczbowych](../keywords/implicit-numeric-conversions-table.md) do `int`.</span><span class="sxs-lookup"><span data-stu-id="3f3f1-161">For the shift operators `<<` and `>>`, the type of the right-hand operand must be [int](../builtin-types/integral-numeric-types.md) or a type that has a [predefined implicit numeric conversion](../keywords/implicit-numeric-conversions-table.md) to `int`.</span></span>

<span data-ttu-id="3f3f1-162">Aby uzyskać `x << count` i `x >> count` wyrażeń, licznik przesunięć rzeczywistego zależy od rodzaju `x` w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="3f3f1-162">For the `x << count` and `x >> count` expressions, the actual shift count depends on the type of `x` as follows:</span></span>

- <span data-ttu-id="3f3f1-163">Jeśli typ `x` jest [int](../builtin-types/integral-numeric-types.md) lub [uint](../builtin-types/integral-numeric-types.md), licznik przesunięć jest definiowany przez niskiego rzędu *pięć* bitów prawostronny operand.</span><span class="sxs-lookup"><span data-stu-id="3f3f1-163">If the type of `x` is [int](../builtin-types/integral-numeric-types.md) or [uint](../builtin-types/integral-numeric-types.md), the shift count is defined by the low-order *five* bits of the right-hand operand.</span></span> <span data-ttu-id="3f3f1-164">Oznacza to, że licznik przesunięć jest obliczany na podstawie `count & 0x1F` (lub `count & 0b_1_1111`).</span><span class="sxs-lookup"><span data-stu-id="3f3f1-164">That is, the shift count is computed from `count & 0x1F` (or `count & 0b_1_1111`).</span></span>

- <span data-ttu-id="3f3f1-165">Jeśli typ `x` jest [długie](../builtin-types/integral-numeric-types.md) lub [ulong](../builtin-types/integral-numeric-types.md), licznik przesunięć jest definiowany przez niskiego rzędu *sześć* bitów prawostronny operand.</span><span class="sxs-lookup"><span data-stu-id="3f3f1-165">If the type of `x` is [long](../builtin-types/integral-numeric-types.md) or [ulong](../builtin-types/integral-numeric-types.md), the shift count is defined by the low-order *six* bits of the right-hand operand.</span></span> <span data-ttu-id="3f3f1-166">Oznacza to, że licznik przesunięć jest obliczany na podstawie `count & 0x3F` (lub `count & 0b_11_1111`).</span><span class="sxs-lookup"><span data-stu-id="3f3f1-166">That is, the shift count is computed from `count & 0x3F` (or `count & 0b_11_1111`).</span></span>

<span data-ttu-id="3f3f1-167">Poniższy przykład przedstawia tego zachowania:</span><span class="sxs-lookup"><span data-stu-id="3f3f1-167">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[shift count example](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#ShiftCount)]

## <a name="enumeration-logical-operators"></a><span data-ttu-id="3f3f1-168">Operatory logiczne wyliczenia</span><span class="sxs-lookup"><span data-stu-id="3f3f1-168">Enumeration logical operators</span></span>

<span data-ttu-id="3f3f1-169">`~`, `&`, `|`, I `^` operatory również są zdefiniowane dla dowolnego [wyliczenie](../keywords/enum.md) typu.</span><span class="sxs-lookup"><span data-stu-id="3f3f1-169">The `~`, `&`, `|`, and `^` operators are also defined for any [enumeration](../keywords/enum.md) type.</span></span> <span data-ttu-id="3f3f1-170">Operandy typu wyliczenia operacji logicznej jest wykonywane na odpowiadające im wartości bazowego typu całkowitego.</span><span class="sxs-lookup"><span data-stu-id="3f3f1-170">For the operands of the same enumeration type, a logical operation is performed on the corresponding values of the underlying integral type.</span></span> <span data-ttu-id="3f3f1-171">Na przykład dla dowolnego `x` i `y` typu wyliczeniowego `T` z typu podstawowego `U`, `x & y` wyrażenie daje ten sam wynik jako `(T)((U)x & (U)y)` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="3f3f1-171">For example, for any `x` and `y` of an enumeration type `T` with an underlying type `U`, the `x & y` expression produces the same result as the `(T)((U)x & (U)y)` expression.</span></span>

<span data-ttu-id="3f3f1-172">Zazwyczaj używa się operatory logiczne bitowe dla typu wyliczenia, która jest zdefiniowana za pomocą [flagi](xref:System.FlagsAttribute) atrybutu.</span><span class="sxs-lookup"><span data-stu-id="3f3f1-172">You typically use bitwise logical operators with an enumeration type which is defined with the [Flags](xref:System.FlagsAttribute) attribute.</span></span> <span data-ttu-id="3f3f1-173">Aby uzyskać więcej informacji, zobacz [Typy wyliczeniowe jako znaczniki bitowe](../../programming-guide/enumeration-types.md#enumeration-types-as-bit-flags) części [Typy wyliczeniowe](../../programming-guide/enumeration-types.md) artykułu.</span><span class="sxs-lookup"><span data-stu-id="3f3f1-173">For more information, see the [Enumeration types as bit flags](../../programming-guide/enumeration-types.md#enumeration-types-as-bit-flags) section of the [Enumeration types](../../programming-guide/enumeration-types.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="3f3f1-174">Overloadability — operator</span><span class="sxs-lookup"><span data-stu-id="3f3f1-174">Operator overloadability</span></span>

<span data-ttu-id="3f3f1-175">Typ zdefiniowany przez użytkownika może [przeciążenia](operator-overloading.md) `~`, `<<`, `>>`, `&`, `|`, i `^` operatorów.</span><span class="sxs-lookup"><span data-stu-id="3f3f1-175">A user-defined type can [overload](operator-overloading.md) the `~`, `<<`, `>>`, `&`, `|`, and `^` operators.</span></span> <span data-ttu-id="3f3f1-176">Gdy jest przeciążony operator binarny, odpowiedniego operatora przypisania złożonego jest również niejawnie przeciążona.</span><span class="sxs-lookup"><span data-stu-id="3f3f1-176">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="3f3f1-177">Typ zdefiniowany przez użytkownika nie można jawnie przeciążyć operator przypisania złożonego.</span><span class="sxs-lookup"><span data-stu-id="3f3f1-177">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

<span data-ttu-id="3f3f1-178">Jeśli typ zdefiniowany przez użytkownika `T` przeciążenia `<<` lub `>>` operatora, typ lewostronny operand musi być `T` i typ prawostronny operand musi być `int`.</span><span class="sxs-lookup"><span data-stu-id="3f3f1-178">If a user-defined type `T` overloads the `<<` or `>>` operator, the type of the left-hand operand must be `T` and the type of the right-hand operand must be `int`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="3f3f1-179">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="3f3f1-179">C# language specification</span></span>

<span data-ttu-id="3f3f1-180">Aby uzyskać więcej informacji, zobacz następujące sekcje [ C# specyfikacji języka](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="3f3f1-180">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="3f3f1-181">Operator dopełnienia bitowego</span><span class="sxs-lookup"><span data-stu-id="3f3f1-181">Bitwise complement operator</span></span>](~/_csharplang/spec/expressions.md#bitwise-complement-operator)
- [<span data-ttu-id="3f3f1-182">Operatory przesunięcia</span><span class="sxs-lookup"><span data-stu-id="3f3f1-182">Shift operators</span></span>](~/_csharplang/spec/expressions.md#shift-operators)
- [<span data-ttu-id="3f3f1-183">Operatory logiczne</span><span class="sxs-lookup"><span data-stu-id="3f3f1-183">Logical operators</span></span>](~/_csharplang/spec/expressions.md#logical-operators)
- [<span data-ttu-id="3f3f1-184">Przydział złożony</span><span class="sxs-lookup"><span data-stu-id="3f3f1-184">Compound assignment</span></span>](~/_csharplang/spec/expressions.md#compound-assignment)
- [<span data-ttu-id="3f3f1-185">Promocji na liczbowe</span><span class="sxs-lookup"><span data-stu-id="3f3f1-185">Numeric promotions</span></span>](~/_csharplang/spec/expressions.md#numeric-promotions)

## <a name="see-also"></a><span data-ttu-id="3f3f1-186">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3f3f1-186">See also</span></span>

- [<span data-ttu-id="3f3f1-187">C#Odwołanie</span><span class="sxs-lookup"><span data-stu-id="3f3f1-187">C# reference</span></span>](../index.md)
- [<span data-ttu-id="3f3f1-188">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="3f3f1-188">C# operators</span></span>](index.md)
- [<span data-ttu-id="3f3f1-189">Operatory logiczne logiczne</span><span class="sxs-lookup"><span data-stu-id="3f3f1-189">Boolean logical operators</span></span>](boolean-logical-operators.md)
