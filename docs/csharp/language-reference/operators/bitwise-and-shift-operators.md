---
title: Operatory bitowe i przesuwowe — odwołanie do języka C#
description: Dowiedz się więcej o operatorach języka C#, które wykonują operacje logiczne lub przesunięcia bitowego za pomocą operacji typów całkowitych.
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
ms.openlocfilehash: 54198368672e0c9324210a232c7851b5a90402cb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399267"
---
# <a name="bitwise-and-shift-operators-c-reference"></a><span data-ttu-id="bc3f7-103">Operatory bitowe i przesuwne (odwołanie do języka C#)</span><span class="sxs-lookup"><span data-stu-id="bc3f7-103">Bitwise and shift operators (C# reference)</span></span>

<span data-ttu-id="bc3f7-104">Następujące operatory wykonują operacje bitowe lub przesuwne z operandami [zintegrowanych typów numerycznych](../builtin-types/integral-numeric-types.md) lub typu [char:](../builtin-types/char.md)</span><span class="sxs-lookup"><span data-stu-id="bc3f7-104">The following operators perform bitwise or shift operations with operands of the [integral numeric types](../builtin-types/integral-numeric-types.md) or the [char](../builtin-types/char.md) type:</span></span>

- <span data-ttu-id="bc3f7-105">Operator bezary [ `~` (bitowy dopełnienie)](#bitwise-complement-operator-)</span><span class="sxs-lookup"><span data-stu-id="bc3f7-105">Unary [`~` (bitwise complement)](#bitwise-complement-operator-) operator</span></span>
- <span data-ttu-id="bc3f7-106">Operatory przesunięcia binarnego [ `<<` (przesunięcie w lewo)](#left-shift-operator-) i [ `>>` (przesunięcie w prawo)](#right-shift-operator-)</span><span class="sxs-lookup"><span data-stu-id="bc3f7-106">Binary [`<<` (left shift)](#left-shift-operator-) and [`>>` (right shift)](#right-shift-operator-) shift operators</span></span>
- <span data-ttu-id="bc3f7-107">Operatory [ `&` binarne (logiczne I)](#logical-and-operator-) [ `|` ( logiczne LUB)](#logical-or-operator-)i [ `^` (logiczne wyłączne LUB)](#logical-exclusive-or-operator-)</span><span class="sxs-lookup"><span data-stu-id="bc3f7-107">Binary [`&` (logical AND)](#logical-and-operator-), [`|` (logical OR)](#logical-or-operator-), and [`^` (logical exclusive OR)](#logical-exclusive-or-operator-) operators</span></span>

<span data-ttu-id="bc3f7-108">Te operatory są `int`zdefiniowane `uint` `long`dla `ulong` , , i typów.</span><span class="sxs-lookup"><span data-stu-id="bc3f7-108">Those operators are defined for the `int`, `uint`, `long`, and `ulong` types.</span></span> <span data-ttu-id="bc3f7-109">Gdy oba operandy są innych`sbyte` `byte`typów `short` `ushort`integralnych `char`( , , , `int` lub ), ich wartości są konwertowane na typ, który jest również typu wynik operacji.</span><span class="sxs-lookup"><span data-stu-id="bc3f7-109">When both operands are of other integral types (`sbyte`, `byte`, `short`, `ushort`, or `char`), their values are converted to the `int` type, which is also the result type of an operation.</span></span> <span data-ttu-id="bc3f7-110">Gdy operandy są różnych typów całki, ich wartości są konwertowane na najbliższy zawierający typ całki.</span><span class="sxs-lookup"><span data-stu-id="bc3f7-110">When operands are of different integral types, their values are converted to the closest containing integral type.</span></span> <span data-ttu-id="bc3f7-111">Aby uzyskać więcej informacji, zobacz [numeryczne promocje](~/_csharplang/spec/expressions.md#numeric-promotions) sekcji [specyfikacji języka Języka C#.](~/_csharplang/spec/introduction.md)</span><span class="sxs-lookup"><span data-stu-id="bc3f7-111">For more information, see the [Numeric promotions](~/_csharplang/spec/expressions.md#numeric-promotions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="bc3f7-112">, `&` `|`i `^` operatory są również zdefiniowane dla `bool` operandów typu.</span><span class="sxs-lookup"><span data-stu-id="bc3f7-112">The `&`, `|`, and `^` operators are also defined for operands of the `bool` type.</span></span> <span data-ttu-id="bc3f7-113">Aby uzyskać więcej informacji, zobacz [Logiczne operatory logiczne](boolean-logical-operators.md).</span><span class="sxs-lookup"><span data-stu-id="bc3f7-113">For more information, see [Boolean logical operators](boolean-logical-operators.md).</span></span>

<span data-ttu-id="bc3f7-114">Operacje bitowe i przesuwne nigdy nie powodują przepełnienia i dają takie same wyniki w [kontekstach sprawdzanych i niezaznaczonych.](../keywords/checked-and-unchecked.md)</span><span class="sxs-lookup"><span data-stu-id="bc3f7-114">Bitwise and shift operations never cause overflow and produce the same results in [checked and unchecked](../keywords/checked-and-unchecked.md) contexts.</span></span>

## <a name="bitwise-complement-operator-"></a><span data-ttu-id="bc3f7-115">Bitowy operator dopełniacza ~</span><span class="sxs-lookup"><span data-stu-id="bc3f7-115">Bitwise complement operator ~</span></span>

<span data-ttu-id="bc3f7-116">Operator `~` tworzy bitowy uzupełnienie swojego operandu, odwracając każdy bit:</span><span class="sxs-lookup"><span data-stu-id="bc3f7-116">The `~` operator produces a bitwise complement of its operand by reversing each bit:</span></span>

[!code-csharp-interactive[bitwise NOT](snippets/BitwiseAndShiftOperators.cs#BitwiseComplement)]

<span data-ttu-id="bc3f7-117">Można również użyć `~` symbolu do deklarowania finalizatorów.</span><span class="sxs-lookup"><span data-stu-id="bc3f7-117">You can also use the `~` symbol to declare finalizers.</span></span> <span data-ttu-id="bc3f7-118">Aby uzyskać więcej informacji, zobacz [Finalizatory](../../programming-guide/classes-and-structs/destructors.md).</span><span class="sxs-lookup"><span data-stu-id="bc3f7-118">For more information, see [Finalizers](../../programming-guide/classes-and-structs/destructors.md).</span></span>

## <a name="left-shift-operator-"></a><span data-ttu-id="bc3f7-119">Operator zmiany lewej\<\<</span><span class="sxs-lookup"><span data-stu-id="bc3f7-119">Left-shift operator \<\<</span></span>

<span data-ttu-id="bc3f7-120">Operator `<<` przesuwa swój lewy operand w lewo przez [liczbę bitów zdefiniowanych przez jego prawostronny operand](#shift-count-of-the-shift-operators).</span><span class="sxs-lookup"><span data-stu-id="bc3f7-120">The `<<` operator shifts its left-hand operand left by the [number of bits defined by its right-hand operand](#shift-count-of-the-shift-operators).</span></span>

<span data-ttu-id="bc3f7-121">Operacja zmiany po lewej stronie odrzuca bity wysokiego rzędu, które znajdują się poza zakresem typu wynikowego i ustawia niskie pozycje pustych bitów na zero, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="bc3f7-121">The left-shift operation discards the high-order bits that are outside the range of the result type and sets the low-order empty bit positions to zero, as the following example shows:</span></span>

[!code-csharp-interactive[left shift](snippets/BitwiseAndShiftOperators.cs#LeftShift)]

<span data-ttu-id="bc3f7-122">Ponieważ operatory przesunięcia `int`są `uint` `long`zdefiniowane `ulong` tylko dla , , i typów, wynik operacji zawsze zawiera co najmniej 32 bity.</span><span class="sxs-lookup"><span data-stu-id="bc3f7-122">Because the shift operators are defined only for the `int`, `uint`, `long`, and `ulong` types, the result of an operation always contains at least 32 bits.</span></span> <span data-ttu-id="bc3f7-123">Jeśli argument po lewej stronie jest innego`sbyte` `byte`typu `short` `ushort`integralnego `char`( , , , `int` lub ), jego wartość jest konwertowana na typ, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="bc3f7-123">If the left-hand operand is of another integral type (`sbyte`, `byte`, `short`, `ushort`, or `char`), its value is converted to the `int` type, as the following example shows:</span></span>

[!code-csharp-interactive[left shift with promotion](snippets/BitwiseAndShiftOperators.cs#LeftShiftPromoted)]

<span data-ttu-id="bc3f7-124">Aby uzyskać informacje o tym, jak `<<` operand po prawej stronie operatora definiuje liczbę zmian, zobacz Licznik zmian w sekcji [operatorzy zmian.](#shift-count-of-the-shift-operators)</span><span class="sxs-lookup"><span data-stu-id="bc3f7-124">For information about how the right-hand operand of the `<<` operator defines the shift count, see the [Shift count of the shift operators](#shift-count-of-the-shift-operators) section.</span></span>

## <a name="right-shift-operator-"></a><span data-ttu-id="bc3f7-125"> >> operatora zmiany prawej</span><span class="sxs-lookup"><span data-stu-id="bc3f7-125">Right-shift operator >></span></span>

<span data-ttu-id="bc3f7-126">Operator `>>` przesuwa swój lewy operand w prawo o [liczbę bitów zdefiniowanych przez jego prawy operand](#shift-count-of-the-shift-operators).</span><span class="sxs-lookup"><span data-stu-id="bc3f7-126">The `>>` operator shifts its left-hand operand right by the [number of bits defined by its right-hand operand](#shift-count-of-the-shift-operators).</span></span>

<span data-ttu-id="bc3f7-127">Operacja zmiany po prawej stronie odrzuca bity niskiego rzędu, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="bc3f7-127">The right-shift operation discards the low-order bits, as the following example shows:</span></span>

[!code-csharp-interactive[right shift](snippets/BitwiseAndShiftOperators.cs#RightShift)]

<span data-ttu-id="bc3f7-128">Puste pozycje bitowe o wysokim zamówieniu są ustawiane na podstawie typu operandu po lewej stronie w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="bc3f7-128">The high-order empty bit positions are set based on the type of the left-hand operand as follows:</span></span>

- <span data-ttu-id="bc3f7-129">Jeśli operand po lewej stronie `int` `long`jest typu lub , operator prawego shift wykonuje przesunięcie *arytmetyczne:* wartość najbardziej znaczącego bitu (bitu znaku) operandu po lewej stronie jest propagowana do pozycji pustych bitów o wysokim rzędu.</span><span class="sxs-lookup"><span data-stu-id="bc3f7-129">If the left-hand operand is of type `int` or `long`, the right-shift operator performs an *arithmetic* shift: the value of the most significant bit (the sign bit) of the left-hand operand is propagated to the high-order empty bit positions.</span></span> <span data-ttu-id="bc3f7-130">Oznacza to, że pozycje pustebitu wysokiego rzędu są ustawione na zero, jeśli argument po lewej stronie jest nieujemna i ustawiona na jedną, jeśli jest ujemna.</span><span class="sxs-lookup"><span data-stu-id="bc3f7-130">That is, the high-order empty bit positions are set to zero if the left-hand operand is non-negative and set to one if it's negative.</span></span>

  [!code-csharp-interactive[arithmetic right shift](snippets/BitwiseAndShiftOperators.cs#ArithmeticRightShift)]

- <span data-ttu-id="bc3f7-131">Jeśli operand po lewej stronie `uint` `ulong`jest typu lub , operator prawego przesunięcia wykonuje *logiczną* zmianę: wysokiej klasy puste pozycje bitowe są zawsze ustawione na zero.</span><span class="sxs-lookup"><span data-stu-id="bc3f7-131">If the left-hand operand is of type `uint` or `ulong`, the right-shift operator performs a *logical* shift: the high-order empty bit positions are always set to zero.</span></span>

  [!code-csharp-interactive[logical right shift](snippets/BitwiseAndShiftOperators.cs#LogicalRightShift)]

<span data-ttu-id="bc3f7-132">Aby uzyskać informacje o tym, jak `>>` operand po prawej stronie operatora definiuje liczbę zmian, zobacz Licznik zmian w sekcji [operatorzy zmian.](#shift-count-of-the-shift-operators)</span><span class="sxs-lookup"><span data-stu-id="bc3f7-132">For information about how the right-hand operand of the `>>` operator defines the shift count, see the [Shift count of the shift operators](#shift-count-of-the-shift-operators) section.</span></span>

## <a name="logical-and-operator-"></a><span data-ttu-id="bc3f7-133">Operator logiczny AND&amp;</span><span class="sxs-lookup"><span data-stu-id="bc3f7-133">Logical AND operator &amp;</span></span>

<span data-ttu-id="bc3f7-134">Operator `&` oblicza bitwise logiczne i jego operands:</span><span class="sxs-lookup"><span data-stu-id="bc3f7-134">The `&` operator computes the bitwise logical AND of its operands:</span></span>

[!code-csharp-interactive[bitwise AND](snippets/BitwiseAndShiftOperators.cs#BitwiseAnd)]

<span data-ttu-id="bc3f7-135">W `bool` przypadku operandów `&` operator oblicza [logiczną i](boolean-logical-operators.md#logical-and-operator-) jego argumenty.</span><span class="sxs-lookup"><span data-stu-id="bc3f7-135">For `bool` operands, the `&` operator computes the [logical AND](boolean-logical-operators.md#logical-and-operator-) of its operands.</span></span> <span data-ttu-id="bc3f7-136">Operator `&` emancypuje. [address-of operator](pointer-related-operators.md#address-of-operator-)</span><span class="sxs-lookup"><span data-stu-id="bc3f7-136">The unary `&` operator is the [address-of operator](pointer-related-operators.md#address-of-operator-).</span></span>

## <a name="logical-exclusive-or-operator-"></a><span data-ttu-id="bc3f7-137">Logiczny wyłączny operator OR ^</span><span class="sxs-lookup"><span data-stu-id="bc3f7-137">Logical exclusive OR operator ^</span></span>

<span data-ttu-id="bc3f7-138">Operator `^` oblicza bitwise logiczne wyłączne LUB, znany również jako bitowy logiczny XOR, jego operands:</span><span class="sxs-lookup"><span data-stu-id="bc3f7-138">The `^` operator computes the bitwise logical exclusive OR, also known as the bitwise logical XOR, of its operands:</span></span>

[!code-csharp-interactive[bitwise XOR](snippets/BitwiseAndShiftOperators.cs#BitwiseXor)]

<span data-ttu-id="bc3f7-139">W `bool` przypadku operandów `^` operator oblicza [logiczną wyłączną lub](boolean-logical-operators.md#logical-exclusive-or-operator-) jego operandów.</span><span class="sxs-lookup"><span data-stu-id="bc3f7-139">For `bool` operands, the `^` operator computes the [logical exclusive OR](boolean-logical-operators.md#logical-exclusive-or-operator-) of its operands.</span></span>

## <a name="logical-or-operator-"></a><span data-ttu-id="bc3f7-140">Logiczny operator OR |</span><span class="sxs-lookup"><span data-stu-id="bc3f7-140">Logical OR operator |</span></span>

<span data-ttu-id="bc3f7-141">Operator `|` oblicza bitowy logiczny LUB jego operandów:</span><span class="sxs-lookup"><span data-stu-id="bc3f7-141">The `|` operator computes the bitwise logical OR of its operands:</span></span>

[!code-csharp-interactive[bitwise OR](snippets/BitwiseAndShiftOperators.cs#BitwiseOr)]

<span data-ttu-id="bc3f7-142">W `bool` przypadku operandów `|` operator oblicza [logiczny OR](boolean-logical-operators.md#logical-or-operator-) jego argumentów.</span><span class="sxs-lookup"><span data-stu-id="bc3f7-142">For `bool` operands, the `|` operator computes the [logical OR](boolean-logical-operators.md#logical-or-operator-) of its operands.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="bc3f7-143">Przypisanie złożone</span><span class="sxs-lookup"><span data-stu-id="bc3f7-143">Compound assignment</span></span>

<span data-ttu-id="bc3f7-144">Dla operatora `op`binarnego wyrażenie przypisania złożonego formularza</span><span class="sxs-lookup"><span data-stu-id="bc3f7-144">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="bc3f7-145">jest równoważny</span><span class="sxs-lookup"><span data-stu-id="bc3f7-145">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="bc3f7-146">chyba `x` że jest oceniana tylko raz.</span><span class="sxs-lookup"><span data-stu-id="bc3f7-146">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="bc3f7-147">W poniższym przykładzie pokazano użycie przypisania złożonego z operatorami bitowym i shift:</span><span class="sxs-lookup"><span data-stu-id="bc3f7-147">The following example demonstrates the usage of compound assignment with bitwise and shift operators:</span></span>

[!code-csharp-interactive[compound assignment](snippets/BitwiseAndShiftOperators.cs#CompoundAssignment)]

<span data-ttu-id="bc3f7-148">Ze względu na [promocje liczbowe](~/_csharplang/spec/expressions.md#numeric-promotions)wynik `op` operacji może nie być `T` `x`niejawnie konwertowalny na typ .</span><span class="sxs-lookup"><span data-stu-id="bc3f7-148">Because of [numeric promotions](~/_csharplang/spec/expressions.md#numeric-promotions), the result of the `op` operation might be not implicitly convertible to the type `T` of `x`.</span></span> <span data-ttu-id="bc3f7-149">W takim przypadku, `op` jeśli jest wstępnie zdefiniowanyoperator i wynik operacji jest `T` jawnie konwertowalne na typ `x`, wyrażenie przypisania złożonego formularza `x op= y` jest równoważne `x = (T)(x op y)`, z wyjątkiem, że `x` jest oceniane tylko raz.</span><span class="sxs-lookup"><span data-stu-id="bc3f7-149">In such a case, if `op` is a predefined operator and the result of the operation is explicitly convertible to the type `T` of `x`, a compound assignment expression of the form `x op= y` is equivalent to `x = (T)(x op y)`, except that `x` is only evaluated once.</span></span> <span data-ttu-id="bc3f7-150">W poniższym przykładzie przedstawiono to zachowanie:</span><span class="sxs-lookup"><span data-stu-id="bc3f7-150">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[compound assignment with cast](snippets/BitwiseAndShiftOperators.cs#CompoundAssignmentWithCast)]

## <a name="operator-precedence"></a><span data-ttu-id="bc3f7-151">Pierwszeństwo operatorów</span><span class="sxs-lookup"><span data-stu-id="bc3f7-151">Operator precedence</span></span>

<span data-ttu-id="bc3f7-152">Następująca lista zamówienia bitowej i operatory zmiany ruchu, począwszy od najwyższego pierwszeństwa do najniższego:</span><span class="sxs-lookup"><span data-stu-id="bc3f7-152">The following list orders bitwise and shift operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="bc3f7-153">Operator dopełniacza bitowego`~`</span><span class="sxs-lookup"><span data-stu-id="bc3f7-153">Bitwise complement operator `~`</span></span>
- <span data-ttu-id="bc3f7-154">Operatorzy zmian `<<` i`>>`</span><span class="sxs-lookup"><span data-stu-id="bc3f7-154">Shift operators `<<` and `>>`</span></span>
- <span data-ttu-id="bc3f7-155">Operator logiczny AND`&`</span><span class="sxs-lookup"><span data-stu-id="bc3f7-155">Logical AND operator `&`</span></span>
- <span data-ttu-id="bc3f7-156">Logiczny wyłączny operator OR`^`</span><span class="sxs-lookup"><span data-stu-id="bc3f7-156">Logical exclusive OR operator `^`</span></span>
- <span data-ttu-id="bc3f7-157">Operator logiczny OR`|`</span><span class="sxs-lookup"><span data-stu-id="bc3f7-157">Logical OR operator `|`</span></span>

<span data-ttu-id="bc3f7-158">Użyj nawiasów, `()`, aby zmienić kolejność oceny narzuconą przez pierwszeństwo operatora:</span><span class="sxs-lookup"><span data-stu-id="bc3f7-158">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence:</span></span>

[!code-csharp-interactive[operator precedence](snippets/BitwiseAndShiftOperators.cs#Precedence)]

<span data-ttu-id="bc3f7-159">Aby uzyskać pełną listę operatorów Języka C# uporządkowane według poziomu pierwszeństwa, zobacz [pierwszeństwo operatora](index.md#operator-precedence) sekcji [operatorów C#artykułu.](index.md)</span><span class="sxs-lookup"><span data-stu-id="bc3f7-159">For the complete list of C# operators ordered by precedence level, see the [Operator precedence](index.md#operator-precedence) section of the [C# operators](index.md) article.</span></span>

## <a name="shift-count-of-the-shift-operators"></a><span data-ttu-id="bc3f7-160">Liczba zmian operatorów zmianowych</span><span class="sxs-lookup"><span data-stu-id="bc3f7-160">Shift count of the shift operators</span></span>

<span data-ttu-id="bc3f7-161">`<<` Dla operatorów przesunięcia i `>>`, typ operand `int` po prawej stronie musi być lub typu, który ma [wstępnie zdefiniowane niejawne konwersji liczbowej](../builtin-types/numeric-conversions.md#implicit-numeric-conversions) do `int`.</span><span class="sxs-lookup"><span data-stu-id="bc3f7-161">For the shift operators `<<` and `>>`, the type of the right-hand operand must be `int` or a type that has a [predefined implicit numeric conversion](../builtin-types/numeric-conversions.md#implicit-numeric-conversions) to `int`.</span></span>

<span data-ttu-id="bc3f7-162">Dla `x << count` wyrażeń i `x >> count` wyrażenia rzeczywista liczba `x` zmian zależy od typu w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="bc3f7-162">For the `x << count` and `x >> count` expressions, the actual shift count depends on the type of `x` as follows:</span></span>

- <span data-ttu-id="bc3f7-163">Jeśli typ `x` jest `int` `uint`lub , liczba zmian jest definiowana przez niskokondygnacje *pięć* bitów operandpo prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="bc3f7-163">If the type of `x` is `int` or `uint`, the shift count is defined by the low-order *five* bits of the right-hand operand.</span></span> <span data-ttu-id="bc3f7-164">Oznacza to, że liczba zmian `count & 0x1F` jest `count & 0b_1_1111`obliczana z (lub ).</span><span class="sxs-lookup"><span data-stu-id="bc3f7-164">That is, the shift count is computed from `count & 0x1F` (or `count & 0b_1_1111`).</span></span>

- <span data-ttu-id="bc3f7-165">Jeśli typ `x` jest `long` `ulong`lub , liczba zmian jest definiowana przez niskokondygnacje *sześć* bitów operandpo prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="bc3f7-165">If the type of `x` is `long` or `ulong`, the shift count is defined by the low-order *six* bits of the right-hand operand.</span></span> <span data-ttu-id="bc3f7-166">Oznacza to, że liczba zmian `count & 0x3F` jest `count & 0b_11_1111`obliczana z (lub ).</span><span class="sxs-lookup"><span data-stu-id="bc3f7-166">That is, the shift count is computed from `count & 0x3F` (or `count & 0b_11_1111`).</span></span>

<span data-ttu-id="bc3f7-167">W poniższym przykładzie przedstawiono to zachowanie:</span><span class="sxs-lookup"><span data-stu-id="bc3f7-167">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[shift count example](snippets/BitwiseAndShiftOperators.cs#ShiftCount)]

> [!NOTE]
> <span data-ttu-id="bc3f7-168">Jak pokazano w poprzednim przykładzie, wynik operacji zmiany może być różny od zera, nawet jeśli wartość operandu po prawej stronie jest większa niż liczba bitów w operandzie po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="bc3f7-168">As the preceding example shows, the result of a shift operation can be non-zero even if the value of the right-hand operand is greater than the number of bits in the left-hand operand.</span></span>

## <a name="enumeration-logical-operators"></a><span data-ttu-id="bc3f7-169">Operatory logiczne wyliczania</span><span class="sxs-lookup"><span data-stu-id="bc3f7-169">Enumeration logical operators</span></span>

<span data-ttu-id="bc3f7-170">Program `~` `&`, `|`, `^` i operatory są również obsługiwane przez dowolny typ [wyliczenia.](../builtin-types/enum.md)</span><span class="sxs-lookup"><span data-stu-id="bc3f7-170">The `~`, `&`, `|`, and `^` operators are also supported by any [enumeration](../builtin-types/enum.md) type.</span></span> <span data-ttu-id="bc3f7-171">W przypadku argumentów tego samego typu wyliczenia wykonywana jest operacja logiczna na odpowiednich wartościach podstawowego typu integralnego.</span><span class="sxs-lookup"><span data-stu-id="bc3f7-171">For operands of the same enumeration type, a logical operation is performed on the corresponding values of the underlying integral type.</span></span> <span data-ttu-id="bc3f7-172">Na przykład dla `x` `y` dowolnego `T` i typu wyliczenia `U`z `x & y` typem bazowym wyrażenie `(T)((U)x & (U)y)` daje taki sam wynik jak wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="bc3f7-172">For example, for any `x` and `y` of an enumeration type `T` with an underlying type `U`, the `x & y` expression produces the same result as the `(T)((U)x & (U)y)` expression.</span></span>

<span data-ttu-id="bc3f7-173">Zazwyczaj używasz bitowych operatorów logicznych z typem wyliczenia, który jest zdefiniowany za pomocą [Flags](xref:System.FlagsAttribute) atrybutu.</span><span class="sxs-lookup"><span data-stu-id="bc3f7-173">You typically use bitwise logical operators with an enumeration type that is defined with the [Flags](xref:System.FlagsAttribute) attribute.</span></span> <span data-ttu-id="bc3f7-174">Aby uzyskać więcej informacji, zobacz [Typy wyliczania jako flagi bitowe](../builtin-types/enum.md#enumeration-types-as-bit-flags) sekcji [Typy wyliczania.](../builtin-types/enum.md)</span><span class="sxs-lookup"><span data-stu-id="bc3f7-174">For more information, see the [Enumeration types as bit flags](../builtin-types/enum.md#enumeration-types-as-bit-flags) section of the [Enumeration types](../builtin-types/enum.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="bc3f7-175">Przeciążenie operatora</span><span class="sxs-lookup"><span data-stu-id="bc3f7-175">Operator overloadability</span></span>

<span data-ttu-id="bc3f7-176">Typ zdefiniowany przez użytkownika `~`może `<<` `>>` `&` [przeciążyć](operator-overloading.md) `^` operatory , , , i `|`operatorów.</span><span class="sxs-lookup"><span data-stu-id="bc3f7-176">A user-defined type can [overload](operator-overloading.md) the `~`, `<<`, `>>`, `&`, `|`, and `^` operators.</span></span> <span data-ttu-id="bc3f7-177">Gdy operator binarny jest przeciążony, odpowiedni operator przypisania złożonego jest również niejawnie przeciążony.</span><span class="sxs-lookup"><span data-stu-id="bc3f7-177">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="bc3f7-178">Typ zdefiniowany przez użytkownika nie może jawnie przeciążać operatora przypisania złożonego.</span><span class="sxs-lookup"><span data-stu-id="bc3f7-178">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

<span data-ttu-id="bc3f7-179">Jeśli `T` typ zdefiniowany przez `<<` użytkownika `>>` przeciąża lub operator, musi być `T` typ operandu po lewej stronie `int`i typ argumentu po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="bc3f7-179">If a user-defined type `T` overloads the `<<` or `>>` operator, the type of the left-hand operand must be `T` and the type of the right-hand operand must be `int`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="bc3f7-180">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="bc3f7-180">C# language specification</span></span>

<span data-ttu-id="bc3f7-181">Aby uzyskać więcej informacji, zobacz następujące sekcje [specyfikacji języka Języka C#:](~/_csharplang/spec/introduction.md)</span><span class="sxs-lookup"><span data-stu-id="bc3f7-181">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="bc3f7-182">Operator dopełniacza bitowego</span><span class="sxs-lookup"><span data-stu-id="bc3f7-182">Bitwise complement operator</span></span>](~/_csharplang/spec/expressions.md#bitwise-complement-operator)
- [<span data-ttu-id="bc3f7-183">Operatory przesunięcia</span><span class="sxs-lookup"><span data-stu-id="bc3f7-183">Shift operators</span></span>](~/_csharplang/spec/expressions.md#shift-operators)
- [<span data-ttu-id="bc3f7-184">Operatory logiczne</span><span class="sxs-lookup"><span data-stu-id="bc3f7-184">Logical operators</span></span>](~/_csharplang/spec/expressions.md#logical-operators)
- [<span data-ttu-id="bc3f7-185">Przypisanie złożone</span><span class="sxs-lookup"><span data-stu-id="bc3f7-185">Compound assignment</span></span>](~/_csharplang/spec/expressions.md#compound-assignment)
- [<span data-ttu-id="bc3f7-186">Promocje numeryczne</span><span class="sxs-lookup"><span data-stu-id="bc3f7-186">Numeric promotions</span></span>](~/_csharplang/spec/expressions.md#numeric-promotions)

## <a name="see-also"></a><span data-ttu-id="bc3f7-187">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bc3f7-187">See also</span></span>

- [<span data-ttu-id="bc3f7-188">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="bc3f7-188">C# reference</span></span>](../index.md)
- [<span data-ttu-id="bc3f7-189">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="bc3f7-189">C# operators</span></span>](index.md)
- [<span data-ttu-id="bc3f7-190">Operatory logiczne (Boolean)</span><span class="sxs-lookup"><span data-stu-id="bc3f7-190">Boolean logical operators</span></span>](boolean-logical-operators.md)
