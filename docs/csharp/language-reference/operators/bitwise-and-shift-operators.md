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
ms.openlocfilehash: bf42a53a89676f457d3d2df8d193a83299c3e4cc
ms.sourcegitcommit: 904b98d8d706f0e2d5ceaa00ce17ffbd92adfb88
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/07/2019
ms.locfileid: "66758372"
---
# <a name="bitwise-and-shift-operators-c-reference"></a><span data-ttu-id="27d2b-103">Bitowe i operatory przesunięcia (C# odwołania)</span><span class="sxs-lookup"><span data-stu-id="27d2b-103">Bitwise and shift operators (C# Reference)</span></span>

<span data-ttu-id="27d2b-104">Następujące operatory bitowe wykonywania lub shift operacji przy użyciu argumentów operacji [typów całkowitych](../keywords/integral-types-table.md):</span><span class="sxs-lookup"><span data-stu-id="27d2b-104">The following operators perform bitwise or shift operations with operands of the [integral types](../keywords/integral-types-table.md):</span></span>

- <span data-ttu-id="27d2b-105">Jednoargumentowy [ `~` (dopełnienia bitowego)](#bitwise-complement-operator-) — operator</span><span class="sxs-lookup"><span data-stu-id="27d2b-105">Unary [`~` (bitwise complement)](#bitwise-complement-operator-) operator</span></span>
- <span data-ttu-id="27d2b-106">Binarny [ `<<` (przesunięcia w lewo)](#left-shift-operator-) i [ `>>` (przesunięcia bitowego w prawo)](#right-shift-operator-) operatory przesunięcia</span><span class="sxs-lookup"><span data-stu-id="27d2b-106">Binary [`<<` (left shift)](#left-shift-operator-) and [`>>` (right shift)](#right-shift-operator-) shift operators</span></span>
- <span data-ttu-id="27d2b-107">Binarny [ `&` (operator logiczny oraz)](#logical-and-operator-), [ `|` (operator logiczny lub)](#logical-or-operator-), i [ `^` (logiczne OR wyłączne)](#logical-exclusive-or-operator-) operatorów</span><span class="sxs-lookup"><span data-stu-id="27d2b-107">Binary [`&` (logical AND)](#logical-and-operator-), [`|` (logical OR)](#logical-or-operator-), and [`^` (logical exclusive OR)](#logical-exclusive-or-operator-) operators</span></span>

<span data-ttu-id="27d2b-108">Te operatory są zdefiniowane dla `int`, `uint`, `long`, i `ulong` typów.</span><span class="sxs-lookup"><span data-stu-id="27d2b-108">Those operators are defined for the `int`, `uint`, `long`, and `ulong` types.</span></span> <span data-ttu-id="27d2b-109">Gdy oba operandy są inne typy całkowitoliczbowe (`sbyte`, `byte`, `short`, `ushort`, lub `char`), ich wartości są konwertowane na `int` typ, który jest również typ wyniku operacji.</span><span class="sxs-lookup"><span data-stu-id="27d2b-109">When both operands are of other integral types (`sbyte`, `byte`, `short`, `ushort`, or `char`), their values are converted to the `int` type, which is also the result type of an operation.</span></span> <span data-ttu-id="27d2b-110">W przypadku argumentów operacji z różnymi typami całkowitymi, ich wartości są konwertowane do najbliższego zawierającego typu całkowitego.</span><span class="sxs-lookup"><span data-stu-id="27d2b-110">When operands are of different integral types, their values are converted to the closest containing integral type.</span></span> <span data-ttu-id="27d2b-111">Aby uzyskać więcej informacji, zobacz [promocji na liczbowe](~/_csharplang/spec/expressions.md#numeric-promotions) części [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="27d2b-111">For more information, see the [Numeric promotions](~/_csharplang/spec/expressions.md#numeric-promotions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="27d2b-112">`&`, `|`, I `^` operatory są również określone w przypadku argumentów operacji `bool` typu.</span><span class="sxs-lookup"><span data-stu-id="27d2b-112">The `&`, `|`, and `^` operators are also defined for the operands of the `bool` type.</span></span> <span data-ttu-id="27d2b-113">Aby uzyskać więcej informacji, zobacz [logiczna operatorów logicznych](boolean-logical-operators.md).</span><span class="sxs-lookup"><span data-stu-id="27d2b-113">For more information, see [Boolean logical operators](boolean-logical-operators.md).</span></span>

<span data-ttu-id="27d2b-114">Bitowe OR i operacje przesunięcia nigdy nie spowodować przepełnienie działają tak samo w [checked i unchecked](../keywords/checked-and-unchecked.md) kontekstów.</span><span class="sxs-lookup"><span data-stu-id="27d2b-114">Bitwise and shift operations never cause overflow and produce the same results in [checked and unchecked](../keywords/checked-and-unchecked.md) contexts.</span></span>

## <a name="bitwise-complement-operator-"></a><span data-ttu-id="27d2b-115">Operator dopełnienia bitowego ~</span><span class="sxs-lookup"><span data-stu-id="27d2b-115">Bitwise complement operator ~</span></span>

<span data-ttu-id="27d2b-116">`~` Operator wytwarza bitowe uzupełnienie swojego operandu odwracając każdy bit:</span><span class="sxs-lookup"><span data-stu-id="27d2b-116">The `~` operator produces a bitwise complement of its operand by reversing each bit:</span></span>

[!code-csharp-interactive[bitwise NOT](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseComplement)]

<span data-ttu-id="27d2b-117">Można również użyć `~` symbolu, aby zadeklarować finalizatorów.</span><span class="sxs-lookup"><span data-stu-id="27d2b-117">You can also use the `~` symbol to declare finalizers.</span></span> <span data-ttu-id="27d2b-118">Aby uzyskać więcej informacji, zobacz [finalizatory](../../programming-guide/classes-and-structs/destructors.md).</span><span class="sxs-lookup"><span data-stu-id="27d2b-118">For more information, see [Finalizers](../../programming-guide/classes-and-structs/destructors.md).</span></span>

## <a name="left-shift-operator-"></a><span data-ttu-id="27d2b-119">Operator przesunięcia w lewo \<\<</span><span class="sxs-lookup"><span data-stu-id="27d2b-119">Left-shift operator \<\<</span></span>

<span data-ttu-id="27d2b-120">`<<` Operator przenosi jego pierwszego operandu w lewo o liczbę bitów definicją drugim argumentem.</span><span class="sxs-lookup"><span data-stu-id="27d2b-120">The `<<` operator shifts its first operand left by the number of bits defined by its second operand.</span></span>

<span data-ttu-id="27d2b-121">Operacja przesunięcia w lewo odrzuca najbardziej znaczących bitów, które są poza zakresem typu wyniku i ustawia pozycje bitów pusty niskiego rzędu na zero, co ilustruje poniższy przykład:</span><span class="sxs-lookup"><span data-stu-id="27d2b-121">The left-shift operation discards the high-order bits that are outside the range of the result type and sets the low-order empty bit positions to zero, as the following example shows:</span></span>

[!code-csharp-interactive[left shift](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#LeftShift)]

<span data-ttu-id="27d2b-122">Ponieważ operatory przesunięcia, są zdefiniowane tylko w przypadku `int`, `uint`, `long`, i `ulong` typów, wynik operacji zawsze zawiera co najmniej 32-bitowy.</span><span class="sxs-lookup"><span data-stu-id="27d2b-122">Because the shift operators are defined only for the `int`, `uint`, `long`, and `ulong` types, the result of an operation always contains at least 32 bits.</span></span> <span data-ttu-id="27d2b-123">Jeśli pierwszy argument jest innego typu całkowitego (`sbyte`, `byte`, `short`, `ushort`, lub `char`), jego wartość jest konwertowana na `int` typu, co ilustruje poniższy przykład:</span><span class="sxs-lookup"><span data-stu-id="27d2b-123">If the first operand is of another integral type (`sbyte`, `byte`, `short`, `ushort`, or `char`), its value is converted to the `int` type, as the following example shows:</span></span>

[!code-csharp-interactive[left shift with promotion](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#LeftShiftPromoted)]

<span data-ttu-id="27d2b-124">Aby uzyskać informacje o tym, jak drugi argument operacji `<<` operator definiuje licznik przesunięć, zobacz [licznik operatory przesunięcia przesunięć](#shift-count-of-the-shift-operators) sekcji.</span><span class="sxs-lookup"><span data-stu-id="27d2b-124">For information about how the second operand of the `<<` operator defines the shift count, see the [Shift count of the shift operators](#shift-count-of-the-shift-operators) section.</span></span>

## <a name="right-shift-operator-"></a><span data-ttu-id="27d2b-125">Operator przesunięcia w prawo >></span><span class="sxs-lookup"><span data-stu-id="27d2b-125">Right-shift operator >></span></span>

<span data-ttu-id="27d2b-126">`>>` Operator przenosi pierwszy argument operacji bezpośrednio przez liczbę bitów definicją drugim argumentem.</span><span class="sxs-lookup"><span data-stu-id="27d2b-126">The `>>` operator shifts its first operand right by the number of bits defined by its second operand.</span></span>

<span data-ttu-id="27d2b-127">Operacja przesunięcia w prawo powoduje odrzucenie mniej znaczące bity, co ilustruje poniższy przykład:</span><span class="sxs-lookup"><span data-stu-id="27d2b-127">The right-shift operation discards the low-order bits, as the following example shows:</span></span>

[!code-csharp-interactive[right shift](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#RightShift)]

<span data-ttu-id="27d2b-128">Pozycje bitów pusty wyższego rzędu jest ustawiona na podstawie typu pierwszego operandu w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="27d2b-128">The high-order empty bit positions are set based on the type of the first operand as follows:</span></span>

- <span data-ttu-id="27d2b-129">Jeśli pierwszy operand jest typu [int](../keywords/int.md) lub [długie](../keywords/long.md), operator przesunięcia w prawo wykonuje *arytmetyczne* shift: wartość najbardziej znaczący bit (bit znaku) pierwszego argument operacji jest propagowana do pozycji bitów pusty wyższego rzędu.</span><span class="sxs-lookup"><span data-stu-id="27d2b-129">If the first operand is of type [int](../keywords/int.md) or [long](../keywords/long.md), the right-shift operator performs an *arithmetic* shift: the value of the most significant bit (the sign bit) of the first operand is propagated to the high-order empty bit positions.</span></span> <span data-ttu-id="27d2b-130">Oznacza to, pozycje bitów pusty wyższego rzędu są ustawiane na zero, jeśli pierwszy argument jest ujemna i ustawiony na wartość 1, jeśli jest ujemna.</span><span class="sxs-lookup"><span data-stu-id="27d2b-130">That is, the high-order empty bit positions are set to zero if the first operand is non-negative and set to one if it's negative.</span></span>

  [!code-csharp-interactive[arithmetic right shift](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#ArithmeticRightShift)]

- <span data-ttu-id="27d2b-131">Jeśli pierwszy operand jest typu [uint](../keywords/uint.md) lub [ulong](../keywords/ulong.md), operator przesunięcia w prawo wykonuje *logiczne* shift: pozycje bitów pusty wyższego rzędu są zawsze ustawione na zero.</span><span class="sxs-lookup"><span data-stu-id="27d2b-131">If the first operand is of type [uint](../keywords/uint.md) or [ulong](../keywords/ulong.md), the right-shift operator performs a *logical* shift: the high-order empty bit positions are always set to zero.</span></span>

  [!code-csharp-interactive[logical right shift](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#LogicalRightShift)]

<span data-ttu-id="27d2b-132">Aby uzyskać informacje o tym, jak drugi argument operacji `>>` operator definiuje licznik przesunięć, zobacz [licznik operatory przesunięcia przesunięć](#shift-count-of-the-shift-operators) sekcji.</span><span class="sxs-lookup"><span data-stu-id="27d2b-132">For information about how the second operand of the `>>` operator defines the shift count, see the [Shift count of the shift operators](#shift-count-of-the-shift-operators) section.</span></span>

## <a name="logical-and-operator-amp"></a><span data-ttu-id="27d2b-133">Operator logiczny AND &amp;</span><span class="sxs-lookup"><span data-stu-id="27d2b-133">Logical AND operator &amp;</span></span>

<span data-ttu-id="27d2b-134">`&` Operator oblicza iloczynu bitowego AND logiczne z argumentów:</span><span class="sxs-lookup"><span data-stu-id="27d2b-134">The `&` operator computes the bitwise logical AND of its operands:</span></span>

[!code-csharp-interactive[bitwise AND](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseAnd)]

<span data-ttu-id="27d2b-135">Dla argumentów operacji `bool` typu `&` oblicza operator [operator logiczny oraz](boolean-logical-operators.md#logical-and-operator-) z argumentów.</span><span class="sxs-lookup"><span data-stu-id="27d2b-135">For the operands of the `bool` type, the `&` operator computes the [logical AND](boolean-logical-operators.md#logical-and-operator-) of its operands.</span></span> <span data-ttu-id="27d2b-136">Jednoargumentowy `&` operator jest [operatora address-of](pointer-related-operators.md#address-of-operator-).</span><span class="sxs-lookup"><span data-stu-id="27d2b-136">The unary `&` operator is the [address-of operator](pointer-related-operators.md#address-of-operator-).</span></span>

## <a name="logical-exclusive-or-operator-"></a><span data-ttu-id="27d2b-137">Operator logiczny OR wyłączne ^</span><span class="sxs-lookup"><span data-stu-id="27d2b-137">Logical exclusive OR operator ^</span></span>

<span data-ttu-id="27d2b-138">`^` Operator oblicza wyłączny sumy bitowej dla logicznej lub znany także jako bitowe XOR logiczne z argumentów:</span><span class="sxs-lookup"><span data-stu-id="27d2b-138">The `^` operator computes the bitwise logical exclusive OR, also known as the bitwise logical XOR, of its operands:</span></span>

[!code-csharp-interactive[bitwise XOR](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseXor)]

<span data-ttu-id="27d2b-139">Dla argumentów operacji `bool` typu `^` oblicza operator [logiczne OR wyłączne](boolean-logical-operators.md#logical-exclusive-or-operator-) z argumentów.</span><span class="sxs-lookup"><span data-stu-id="27d2b-139">For the operands of the `bool` type, the `^` operator computes the [logical exclusive OR](boolean-logical-operators.md#logical-exclusive-or-operator-) of its operands.</span></span>

## <a name="logical-or-operator-"></a><span data-ttu-id="27d2b-140">Operator logiczny OR |</span><span class="sxs-lookup"><span data-stu-id="27d2b-140">Logical OR operator |</span></span>

<span data-ttu-id="27d2b-141">`|` Operator oblicza bitowe OR logiczne z argumentów:</span><span class="sxs-lookup"><span data-stu-id="27d2b-141">The `|` operator computes the bitwise logical OR of its operands:</span></span>

[!code-csharp-interactive[bitwise OR](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseOr)]

<span data-ttu-id="27d2b-142">Dla argumentów operacji `bool` typu `|` oblicza operator [logiczne OR](boolean-logical-operators.md#logical-or-operator-) z argumentów.</span><span class="sxs-lookup"><span data-stu-id="27d2b-142">For the operands of the `bool` type, the `|` operator computes the [logical OR](boolean-logical-operators.md#logical-or-operator-) of its operands.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="27d2b-143">Przydział złożony</span><span class="sxs-lookup"><span data-stu-id="27d2b-143">Compound assignment</span></span>

<span data-ttu-id="27d2b-144">Dla operatora binarnego `op`, wyrażenie przypisania złożonego formularza</span><span class="sxs-lookup"><span data-stu-id="27d2b-144">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="27d2b-145">odpowiada wyrażeniu</span><span class="sxs-lookup"><span data-stu-id="27d2b-145">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="27d2b-146">z tą różnicą, że `x` jest obliczany tylko raz.</span><span class="sxs-lookup"><span data-stu-id="27d2b-146">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="27d2b-147">Poniższy przykład ilustruje użycie przydział złożony przy użyciu bitowego operatora i operatory przesunięcia:</span><span class="sxs-lookup"><span data-stu-id="27d2b-147">The following example demonstrates the usage of compound assignment with bitwise and shift operators:</span></span>

[!code-csharp-interactive[compound assignment](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#CompoundAssignment)]

<span data-ttu-id="27d2b-148">Z powodu [promocji na liczbowe](~/_csharplang/spec/expressions.md#numeric-promotions), wynikiem `op` operacji może nie być niejawnie konwertowane na typ `T` z `x`.</span><span class="sxs-lookup"><span data-stu-id="27d2b-148">Because of [numeric promotions](~/_csharplang/spec/expressions.md#numeric-promotions), the result of the `op` operation might be not implicitly convertible to the type `T` of `x`.</span></span> <span data-ttu-id="27d2b-149">W takim przypadku jeśli `op` jest wstępnie zdefiniowanego operatora, a wynik operacji jest jawnie konwertowany na typ `T` z `x`, wyrażenia przypisania złożonego w postaci `x op= y` jest odpowiednikiem `x = (T)(x op y)`, z wyjątkiem które `x` jest oceniane tylko raz.</span><span class="sxs-lookup"><span data-stu-id="27d2b-149">In such a case, if `op` is a predefined operator and the result of the operation is explicitly convertible to the type `T` of `x`, a compound assignment expression of the form `x op= y` is equivalent to `x = (T)(x op y)`, except that `x` is only evaluated once.</span></span> <span data-ttu-id="27d2b-150">Poniższy przykład przedstawia tego zachowania:</span><span class="sxs-lookup"><span data-stu-id="27d2b-150">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[compound assignment with cast](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#CompoundAssignmentWithCast)]

## <a name="operator-precedence"></a><span data-ttu-id="27d2b-151">Pierwszeństwo operatorów</span><span class="sxs-lookup"><span data-stu-id="27d2b-151">Operator precedence</span></span>

<span data-ttu-id="27d2b-152">Następujące listy zamówienia bitowe i operatory przesunięcia od najwyższy priorytet, do najniższego:</span><span class="sxs-lookup"><span data-stu-id="27d2b-152">The following list orders bitwise and shift operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="27d2b-153">Operator dopełnienia bitowego `~`</span><span class="sxs-lookup"><span data-stu-id="27d2b-153">Bitwise complement operator `~`</span></span>
- <span data-ttu-id="27d2b-154">Operatory przesunięcia `<<` i `>>`</span><span class="sxs-lookup"><span data-stu-id="27d2b-154">Shift operators `<<` and `>>`</span></span>
- <span data-ttu-id="27d2b-155">Operator logiczny AND `&`</span><span class="sxs-lookup"><span data-stu-id="27d2b-155">Logical AND operator `&`</span></span>
- <span data-ttu-id="27d2b-156">Operator logiczny OR wyłączne `^`</span><span class="sxs-lookup"><span data-stu-id="27d2b-156">Logical exclusive OR operator `^`</span></span>
- <span data-ttu-id="27d2b-157">Operator logiczny OR `|`</span><span class="sxs-lookup"><span data-stu-id="27d2b-157">Logical OR operator `|`</span></span>

<span data-ttu-id="27d2b-158">Użyj nawiasów, `()`, aby zmienić kolejność oceny nałożonych przez pierwszeństwo operatorów:</span><span class="sxs-lookup"><span data-stu-id="27d2b-158">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence:</span></span>

[!code-csharp-interactive[operator precedence](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#Precedence)]

<span data-ttu-id="27d2b-159">Aby uzyskać pełną listę C# operatory uporządkowane według poziomu priorytetu, zobacz [ C# operatory](index.md).</span><span class="sxs-lookup"><span data-stu-id="27d2b-159">For the complete list of C# operators ordered by precedence level, see [C# operators](index.md).</span></span>

## <a name="shift-count-of-the-shift-operators"></a><span data-ttu-id="27d2b-160">Licznik przesunięć operatorów przesunięcia</span><span class="sxs-lookup"><span data-stu-id="27d2b-160">Shift count of the shift operators</span></span>

<span data-ttu-id="27d2b-161">Dla operatorów przesunięcia `<<` i `>>`, typ drugiego argumentu operacji musi być [int](../keywords/int.md) lub typ, który ma [wstępnie zdefiniowane niejawnych konwersji liczbowych](../keywords/implicit-numeric-conversions-table.md) do `int`.</span><span class="sxs-lookup"><span data-stu-id="27d2b-161">For the shift operators `<<` and `>>`, the type of the second operand must be [int](../keywords/int.md) or a type that has a [predefined implicit numeric conversion](../keywords/implicit-numeric-conversions-table.md) to `int`.</span></span>

<span data-ttu-id="27d2b-162">Aby uzyskać `x << count` i `x >> count` wyrażeń, licznik przesunięć rzeczywistego zależy od rodzaju `x` w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="27d2b-162">For the `x << count` and `x >> count` expressions, the actual shift count depends on the type of `x` as follows:</span></span>

- <span data-ttu-id="27d2b-163">Jeśli typ `x` jest [int](../keywords/int.md) lub [uint](../keywords/uint.md), licznik przesunięć jest definiowany przez niskiego rzędu *pięć* bitów drugiego operandu.</span><span class="sxs-lookup"><span data-stu-id="27d2b-163">If the type of `x` is [int](../keywords/int.md) or [uint](../keywords/uint.md), the shift count is defined by the low-order *five* bits of the second operand.</span></span> <span data-ttu-id="27d2b-164">Oznacza to, że licznik przesunięć jest obliczany na podstawie `count & 0x1F` (lub `count & 0b_1_1111`).</span><span class="sxs-lookup"><span data-stu-id="27d2b-164">That is, the shift count is computed from `count & 0x1F` (or `count & 0b_1_1111`).</span></span>

- <span data-ttu-id="27d2b-165">Jeśli typ `x` jest [długie](../keywords/long.md) lub [ulong](../keywords/ulong.md), licznik przesunięć jest definiowany przez niskiego rzędu *sześć* bitów drugiego operandu.</span><span class="sxs-lookup"><span data-stu-id="27d2b-165">If the type of `x` is [long](../keywords/long.md) or [ulong](../keywords/ulong.md), the shift count is defined by the low-order *six* bits of the second operand.</span></span> <span data-ttu-id="27d2b-166">Oznacza to, że licznik przesunięć jest obliczany na podstawie `count & 0x3F` (lub `count & 0b_11_1111`).</span><span class="sxs-lookup"><span data-stu-id="27d2b-166">That is, the shift count is computed from `count & 0x3F` (or `count & 0b_11_1111`).</span></span>

<span data-ttu-id="27d2b-167">Poniższy przykład przedstawia tego zachowania:</span><span class="sxs-lookup"><span data-stu-id="27d2b-167">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[shift count example](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#ShiftCount)]

## <a name="enumeration-logical-operators"></a><span data-ttu-id="27d2b-168">Operatory logiczne wyliczenia</span><span class="sxs-lookup"><span data-stu-id="27d2b-168">Enumeration logical operators</span></span>

<span data-ttu-id="27d2b-169">`~`, `&`, `|`, I `^` operatory również są zdefiniowane dla dowolnego [wyliczenie](../keywords/enum.md) typu.</span><span class="sxs-lookup"><span data-stu-id="27d2b-169">The `~`, `&`, `|`, and `^` operators are also defined for any [enumeration](../keywords/enum.md) type.</span></span> <span data-ttu-id="27d2b-170">Operandy typu wyliczenia operacji logicznej jest wykonywane na odpowiadające im wartości bazowego typu całkowitego.</span><span class="sxs-lookup"><span data-stu-id="27d2b-170">For the operands of the same enumeration type, a logical operation is performed on the corresponding values of the underlying integral type.</span></span> <span data-ttu-id="27d2b-171">Na przykład dla dowolnego `x` i `y` typu wyliczeniowego `T` z typu podstawowego `U`, `x & y` wyrażenie daje ten sam wynik jako `(T)((U)x & (U)y)` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="27d2b-171">For example, for any `x` and `y` of an enumeration type `T` with an underlying type `U`, the `x & y` expression produces the same result as the `(T)((U)x & (U)y)` expression.</span></span>

<span data-ttu-id="27d2b-172">Zazwyczaj używa się operatory logiczne bitowe dla typu wyliczenia, która jest zdefiniowana za pomocą [flagi](xref:System.FlagsAttribute) atrybutu.</span><span class="sxs-lookup"><span data-stu-id="27d2b-172">You typically use bitwise logical operators with an enumeration type which is defined with the [Flags](xref:System.FlagsAttribute) attribute.</span></span> <span data-ttu-id="27d2b-173">Aby uzyskać więcej informacji, zobacz [Typy wyliczeniowe jako znaczniki bitowe](../../programming-guide/enumeration-types.md#enumeration-types-as-bit-flags) części [Typy wyliczeniowe](../../programming-guide/enumeration-types.md) artykułu.</span><span class="sxs-lookup"><span data-stu-id="27d2b-173">For more information, see the [Enumeration types as bit flags](../../programming-guide/enumeration-types.md#enumeration-types-as-bit-flags) section of the [Enumeration types](../../programming-guide/enumeration-types.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="27d2b-174">Overloadability — operator</span><span class="sxs-lookup"><span data-stu-id="27d2b-174">Operator overloadability</span></span>

<span data-ttu-id="27d2b-175">Typ zdefiniowany przez użytkownika może [przeciążenia](../keywords/operator.md) `~`, `<<`, `>>`, `&`, `|`, i `^` operatorów.</span><span class="sxs-lookup"><span data-stu-id="27d2b-175">A user-defined type can [overload](../keywords/operator.md) the `~`, `<<`, `>>`, `&`, `|`, and `^` operators.</span></span> <span data-ttu-id="27d2b-176">Gdy jest przeciążony operator binarny, odpowiedniego operatora przypisania złożonego jest również niejawnie przeciążona.</span><span class="sxs-lookup"><span data-stu-id="27d2b-176">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="27d2b-177">Typ zdefiniowany przez użytkownika nie można jawnie przeciążyć operator przypisania złożonego.</span><span class="sxs-lookup"><span data-stu-id="27d2b-177">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

<span data-ttu-id="27d2b-178">Jeśli typ zdefiniowany przez użytkownika `T` przeciążenia `<<` lub `>>` operatora, musi być typem pierwszego operandu `T` i typ drugiego argumentu operacji musi być `int`.</span><span class="sxs-lookup"><span data-stu-id="27d2b-178">If a user-defined type `T` overloads the `<<` or `>>` operator, the type of the first operand must be `T` and the type of the second operand must be `int`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="27d2b-179">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="27d2b-179">C# language specification</span></span>

<span data-ttu-id="27d2b-180">Aby uzyskać więcej informacji, zobacz następujące sekcje [ C# specyfikacji języka](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="27d2b-180">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="27d2b-181">Operator dopełnienia bitowego</span><span class="sxs-lookup"><span data-stu-id="27d2b-181">Bitwise complement operator</span></span>](~/_csharplang/spec/expressions.md#bitwise-complement-operator)
- [<span data-ttu-id="27d2b-182">Operatory przesunięcia</span><span class="sxs-lookup"><span data-stu-id="27d2b-182">Shift operators</span></span>](~/_csharplang/spec/expressions.md#shift-operators)
- [<span data-ttu-id="27d2b-183">Operatory logiczne</span><span class="sxs-lookup"><span data-stu-id="27d2b-183">Logical operators</span></span>](~/_csharplang/spec/expressions.md#logical-operators)
- [<span data-ttu-id="27d2b-184">Przydział złożony</span><span class="sxs-lookup"><span data-stu-id="27d2b-184">Compound assignment</span></span>](~/_csharplang/spec/expressions.md#compound-assignment)
- [<span data-ttu-id="27d2b-185">Promocji na liczbowe</span><span class="sxs-lookup"><span data-stu-id="27d2b-185">Numeric promotions</span></span>](~/_csharplang/spec/expressions.md#numeric-promotions)

## <a name="see-also"></a><span data-ttu-id="27d2b-186">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="27d2b-186">See also</span></span>

- [<span data-ttu-id="27d2b-187">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="27d2b-187">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="27d2b-188">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="27d2b-188">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="27d2b-189">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="27d2b-189">C# Operators</span></span>](index.md)
- [<span data-ttu-id="27d2b-190">Operatory logiczne logiczne</span><span class="sxs-lookup"><span data-stu-id="27d2b-190">Boolean logical operators</span></span>](boolean-logical-operators.md)
