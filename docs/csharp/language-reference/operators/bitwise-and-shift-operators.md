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
ms.openlocfilehash: a6319cbbbe8a691f5d2a01a13a5abfa2550b3705
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/03/2020
ms.locfileid: "78239524"
---
# <a name="bitwise-and-shift-operators-c-reference"></a><span data-ttu-id="8a628-103">Operatory bitowe i przesunięciaC# (odwołanie)</span><span class="sxs-lookup"><span data-stu-id="8a628-103">Bitwise and shift operators (C# reference)</span></span>

<span data-ttu-id="8a628-104">Następujące operatory wykonują operacje bitowe lub przesunięcia przy użyciu operandów [całkowitych typów liczbowych](../builtin-types/integral-numeric-types.md) lub typu [char](../builtin-types/char.md) :</span><span class="sxs-lookup"><span data-stu-id="8a628-104">The following operators perform bitwise or shift operations with operands of the [integral numeric types](../builtin-types/integral-numeric-types.md) or the [char](../builtin-types/char.md) type:</span></span>

- <span data-ttu-id="8a628-105">Operator jednoargumentowy [`~` (uzupełnienie bitowe)](#bitwise-complement-operator-)</span><span class="sxs-lookup"><span data-stu-id="8a628-105">Unary [`~` (bitwise complement)](#bitwise-complement-operator-) operator</span></span>
- <span data-ttu-id="8a628-106">Operatory przesunięcia`<<` binarnych [(LEFT SHIFT)](#left-shift-operator-) i [`>>` (prawy shift)](#right-shift-operator-)</span><span class="sxs-lookup"><span data-stu-id="8a628-106">Binary [`<<` (left shift)](#left-shift-operator-) and [`>>` (right shift)](#right-shift-operator-) shift operators</span></span>
- <span data-ttu-id="8a628-107">Binarne [`&` (logiczne i)](#logical-and-operator-), [`|` (logiczne lub)](#logical-or-operator-)i [`^` (logiczne wyłącznych lub)](#logical-exclusive-or-operator-)</span><span class="sxs-lookup"><span data-stu-id="8a628-107">Binary [`&` (logical AND)](#logical-and-operator-), [`|` (logical OR)](#logical-or-operator-), and [`^` (logical exclusive OR)](#logical-exclusive-or-operator-) operators</span></span>

<span data-ttu-id="8a628-108">Te operatory są zdefiniowane dla typów `int`, `uint`, `long`i `ulong`.</span><span class="sxs-lookup"><span data-stu-id="8a628-108">Those operators are defined for the `int`, `uint`, `long`, and `ulong` types.</span></span> <span data-ttu-id="8a628-109">Gdy oba operandy są innymi typami całkowitymi (`sbyte`, `byte`, `short`, `ushort`lub `char`), ich wartości są konwertowane na typ `int`, który jest również typem wyniku operacji.</span><span class="sxs-lookup"><span data-stu-id="8a628-109">When both operands are of other integral types (`sbyte`, `byte`, `short`, `ushort`, or `char`), their values are converted to the `int` type, which is also the result type of an operation.</span></span> <span data-ttu-id="8a628-110">Gdy operandy są różnymi typami całkowitymi, ich wartości są konwertowane na najbliższy typ całkowity.</span><span class="sxs-lookup"><span data-stu-id="8a628-110">When operands are of different integral types, their values are converted to the closest containing integral type.</span></span> <span data-ttu-id="8a628-111">Aby uzyskać więcej informacji, zobacz sekcję " [promocje liczbowe](~/_csharplang/spec/expressions.md#numeric-promotions) " [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="8a628-111">For more information, see the [Numeric promotions](~/_csharplang/spec/expressions.md#numeric-promotions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="8a628-112">Operatory `&`, `|`i `^` są również zdefiniowane dla argumentów operacji typu `bool`.</span><span class="sxs-lookup"><span data-stu-id="8a628-112">The `&`, `|`, and `^` operators are also defined for operands of the `bool` type.</span></span> <span data-ttu-id="8a628-113">Aby uzyskać więcej informacji, zobacz logiczne [Operatory logiczne](boolean-logical-operators.md).</span><span class="sxs-lookup"><span data-stu-id="8a628-113">For more information, see [Boolean logical operators](boolean-logical-operators.md).</span></span>

<span data-ttu-id="8a628-114">Operacje bitowe i przesunięcia nigdy nie powodują przepełnienia i tworzą te same wyniki w kontekstach [zaewidencjonowanych i](../keywords/checked-and-unchecked.md) niezaznaczone.</span><span class="sxs-lookup"><span data-stu-id="8a628-114">Bitwise and shift operations never cause overflow and produce the same results in [checked and unchecked](../keywords/checked-and-unchecked.md) contexts.</span></span>

## <a name="bitwise-complement-operator-"></a><span data-ttu-id="8a628-115">Operator uzupełnienia bitowego ~</span><span class="sxs-lookup"><span data-stu-id="8a628-115">Bitwise complement operator ~</span></span>

<span data-ttu-id="8a628-116">Operator `~` generuje bitowe uzupełnienie jego operandu przez odwrócenie każdego bitu:</span><span class="sxs-lookup"><span data-stu-id="8a628-116">The `~` operator produces a bitwise complement of its operand by reversing each bit:</span></span>

[!code-csharp-interactive[bitwise NOT](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseComplement)]

<span data-ttu-id="8a628-117">Można również użyć symbolu `~`, aby zadeklarować finalizatory.</span><span class="sxs-lookup"><span data-stu-id="8a628-117">You can also use the `~` symbol to declare finalizers.</span></span> <span data-ttu-id="8a628-118">Aby uzyskać więcej informacji, zobacz [finalizatory](../../programming-guide/classes-and-structs/destructors.md).</span><span class="sxs-lookup"><span data-stu-id="8a628-118">For more information, see [Finalizers](../../programming-guide/classes-and-structs/destructors.md).</span></span>

## <a name="left-shift-operator-"></a><span data-ttu-id="8a628-119">Operator przesunięcia w lewo \<\<</span><span class="sxs-lookup"><span data-stu-id="8a628-119">Left-shift operator \<\<</span></span>

<span data-ttu-id="8a628-120">Operator `<<` przesuwa swój lewy argument operacji w lewo o [liczbę bitów określoną przez jego operand po prawej stronie](#shift-count-of-the-shift-operators).</span><span class="sxs-lookup"><span data-stu-id="8a628-120">The `<<` operator shifts its left-hand operand left by the [number of bits defined by its right-hand operand](#shift-count-of-the-shift-operators).</span></span>

<span data-ttu-id="8a628-121">Operacja przesunięcia w lewo odrzuca bity o wysokim stopniu, które znajdują się poza zakresem wyników, i ustawia puste pozycje bitu w porządku o wartości zero, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="8a628-121">The left-shift operation discards the high-order bits that are outside the range of the result type and sets the low-order empty bit positions to zero, as the following example shows:</span></span>

[!code-csharp-interactive[left shift](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#LeftShift)]

<span data-ttu-id="8a628-122">Ponieważ operatory przesunięcia są zdefiniowane tylko dla typów `int`, `uint`, `long`i `ulong`, wynik operacji zawsze zawiera co najmniej 32 bitów.</span><span class="sxs-lookup"><span data-stu-id="8a628-122">Because the shift operators are defined only for the `int`, `uint`, `long`, and `ulong` types, the result of an operation always contains at least 32 bits.</span></span> <span data-ttu-id="8a628-123">Jeśli argument operacji po lewej stronie jest innego typu całkowitego (`sbyte`, `byte`, `short`, `ushort`lub `char`), jego wartość jest konwertowana na typ `int`, jak pokazano na poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="8a628-123">If the left-hand operand is of another integral type (`sbyte`, `byte`, `short`, `ushort`, or `char`), its value is converted to the `int` type, as the following example shows:</span></span>

[!code-csharp-interactive[left shift with promotion](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#LeftShiftPromoted)]

<span data-ttu-id="8a628-124">Aby uzyskać informacje o tym, jak argument operacji po prawej stronie operatora `<<` definiuje liczbę przesunięć, zobacz [Liczba przesunięć w sekcji operatory przesunięcia](#shift-count-of-the-shift-operators) .</span><span class="sxs-lookup"><span data-stu-id="8a628-124">For information about how the right-hand operand of the `<<` operator defines the shift count, see the [Shift count of the shift operators](#shift-count-of-the-shift-operators) section.</span></span>

## <a name="right-shift-operator-"></a><span data-ttu-id="8a628-125">Operator przesunięcia w prawo > ></span><span class="sxs-lookup"><span data-stu-id="8a628-125">Right-shift operator >></span></span>

<span data-ttu-id="8a628-126">Operator `>>` przesuwa swój lewy argument operacji bezpośrednio przez [liczbę bitów zdefiniowanych przez swój operand z prawej strony](#shift-count-of-the-shift-operators).</span><span class="sxs-lookup"><span data-stu-id="8a628-126">The `>>` operator shifts its left-hand operand right by the [number of bits defined by its right-hand operand](#shift-count-of-the-shift-operators).</span></span>

<span data-ttu-id="8a628-127">Operacja przesunięcia w prawo powoduje odrzucenie bitów o niskiej kolejności, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="8a628-127">The right-shift operation discards the low-order bits, as the following example shows:</span></span>

[!code-csharp-interactive[right shift](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#RightShift)]

<span data-ttu-id="8a628-128">Puste pozycje w dużej kolejności są ustawiane na podstawie typu operandu po lewej stronie w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="8a628-128">The high-order empty bit positions are set based on the type of the left-hand operand as follows:</span></span>

- <span data-ttu-id="8a628-129">Jeśli argument operacji po lewej stronie jest typu `int` lub `long`, operator przesunięcia w prawo wykonuje *arytmetyczne* przesunięcie: wartość najbardziej znaczącego bitu (bit znaku) operandu po lewej stronie jest propagowana do pustych pozycji o dużej liczbie bitów.</span><span class="sxs-lookup"><span data-stu-id="8a628-129">If the left-hand operand is of type `int` or `long`, the right-shift operator performs an *arithmetic* shift: the value of the most significant bit (the sign bit) of the left-hand operand is propagated to the high-order empty bit positions.</span></span> <span data-ttu-id="8a628-130">Oznacza to, że puste pozycje bitu o wysokim stopniu kolejności są ustawione na zero, jeśli argument operacji po lewej stronie jest nieujemny i ustawiony na jeden, jeśli jest ujemny.</span><span class="sxs-lookup"><span data-stu-id="8a628-130">That is, the high-order empty bit positions are set to zero if the left-hand operand is non-negative and set to one if it's negative.</span></span>

  [!code-csharp-interactive[arithmetic right shift](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#ArithmeticRightShift)]

- <span data-ttu-id="8a628-131">Jeśli argument operacji po lewej stronie jest typu `uint` lub `ulong`, operator przesunięcia w prawo wykonuje *logiczne* przesunięcie: wartość pustych pozycji w kolejności pustej jest zawsze równa zero.</span><span class="sxs-lookup"><span data-stu-id="8a628-131">If the left-hand operand is of type `uint` or `ulong`, the right-shift operator performs a *logical* shift: the high-order empty bit positions are always set to zero.</span></span>

  [!code-csharp-interactive[logical right shift](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#LogicalRightShift)]

<span data-ttu-id="8a628-132">Aby uzyskać informacje o tym, jak argument operacji po prawej stronie operatora `>>` definiuje liczbę przesunięć, zobacz [Liczba przesunięć w sekcji operatory przesunięcia](#shift-count-of-the-shift-operators) .</span><span class="sxs-lookup"><span data-stu-id="8a628-132">For information about how the right-hand operand of the `>>` operator defines the shift count, see the [Shift count of the shift operators](#shift-count-of-the-shift-operators) section.</span></span>

## <a name="logical-and-operator-"></a><span data-ttu-id="8a628-133">Operatory logiczne i &amp;</span><span class="sxs-lookup"><span data-stu-id="8a628-133">Logical AND operator &amp;</span></span>

<span data-ttu-id="8a628-134">Operator `&` oblicza koniunkcję bitową i jej operandy:</span><span class="sxs-lookup"><span data-stu-id="8a628-134">The `&` operator computes the bitwise logical AND of its operands:</span></span>

[!code-csharp-interactive[bitwise AND](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseAnd)]

<span data-ttu-id="8a628-135">Dla argumentów operacji `bool` operator `&` oblicza wartość [logiczną i](boolean-logical-operators.md#logical-and-operator-) jej operandów.</span><span class="sxs-lookup"><span data-stu-id="8a628-135">For `bool` operands, the `&` operator computes the [logical AND](boolean-logical-operators.md#logical-and-operator-) of its operands.</span></span> <span data-ttu-id="8a628-136">Jednoargumentowy operator `&` jest [operatorem address-of](pointer-related-operators.md#address-of-operator-).</span><span class="sxs-lookup"><span data-stu-id="8a628-136">The unary `&` operator is the [address-of operator](pointer-related-operators.md#address-of-operator-).</span></span>

## <a name="logical-exclusive-or-operator-"></a><span data-ttu-id="8a628-137">Operator wyłączny logicznego OR ^</span><span class="sxs-lookup"><span data-stu-id="8a628-137">Logical exclusive OR operator ^</span></span>

<span data-ttu-id="8a628-138">Operator `^` oblicza koniunkcję bitową na wyłączność lub, znaną również jako bitowe koniunkcja logiczna XOR, argumentów operacji:</span><span class="sxs-lookup"><span data-stu-id="8a628-138">The `^` operator computes the bitwise logical exclusive OR, also known as the bitwise logical XOR, of its operands:</span></span>

[!code-csharp-interactive[bitwise XOR](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseXor)]

<span data-ttu-id="8a628-139">Dla argumentów operacji `bool` operator `^` oblicza wartość [logiczną na wyłączność lub](boolean-logical-operators.md#logical-exclusive-or-operator-) z jej argumentów operacji.</span><span class="sxs-lookup"><span data-stu-id="8a628-139">For `bool` operands, the `^` operator computes the [logical exclusive OR](boolean-logical-operators.md#logical-exclusive-or-operator-) of its operands.</span></span>

## <a name="logical-or-operator-"></a><span data-ttu-id="8a628-140">Operator logiczny OR |</span><span class="sxs-lookup"><span data-stu-id="8a628-140">Logical OR operator |</span></span>

<span data-ttu-id="8a628-141">Operator `|` oblicza bitowe logiczne lub jego operandy:</span><span class="sxs-lookup"><span data-stu-id="8a628-141">The `|` operator computes the bitwise logical OR of its operands:</span></span>

[!code-csharp-interactive[bitwise OR](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseOr)]

<span data-ttu-id="8a628-142">Dla argumentów operacji `bool` operator `|` oblicza wartość [logiczną lub](boolean-logical-operators.md#logical-or-operator-) argumentów operacji.</span><span class="sxs-lookup"><span data-stu-id="8a628-142">For `bool` operands, the `|` operator computes the [logical OR](boolean-logical-operators.md#logical-or-operator-) of its operands.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="8a628-143">Przypisanie złożone</span><span class="sxs-lookup"><span data-stu-id="8a628-143">Compound assignment</span></span>

<span data-ttu-id="8a628-144">Dla operatora binarnego `op`wyrażenie złożonego przypisania formularza</span><span class="sxs-lookup"><span data-stu-id="8a628-144">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="8a628-145">odpowiada wyrażeniu</span><span class="sxs-lookup"><span data-stu-id="8a628-145">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="8a628-146">z tą różnicą, że `x` są oceniane tylko raz.</span><span class="sxs-lookup"><span data-stu-id="8a628-146">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="8a628-147">Poniższy przykład ilustruje użycie przypisania złożonego z operatory bitowe i przesunięcia:</span><span class="sxs-lookup"><span data-stu-id="8a628-147">The following example demonstrates the usage of compound assignment with bitwise and shift operators:</span></span>

[!code-csharp-interactive[compound assignment](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#CompoundAssignment)]

<span data-ttu-id="8a628-148">Ze względu na [promocje liczbowe](~/_csharplang/spec/expressions.md#numeric-promotions)wynik operacji `op` może nie być niejawnie konwertowany na typ `T` `x`.</span><span class="sxs-lookup"><span data-stu-id="8a628-148">Because of [numeric promotions](~/_csharplang/spec/expressions.md#numeric-promotions), the result of the `op` operation might be not implicitly convertible to the type `T` of `x`.</span></span> <span data-ttu-id="8a628-149">W takim przypadku, jeśli `op` jest wstępnie zdefiniowanym operatorem, a wynik operacji jest jawnie konwertowany na typ `T` `x`, wyrażenie przypisania złożonego `x op= y` jest równoważne z `x = (T)(x op y)`, z tą różnicą, że `x` są oceniane tylko raz.</span><span class="sxs-lookup"><span data-stu-id="8a628-149">In such a case, if `op` is a predefined operator and the result of the operation is explicitly convertible to the type `T` of `x`, a compound assignment expression of the form `x op= y` is equivalent to `x = (T)(x op y)`, except that `x` is only evaluated once.</span></span> <span data-ttu-id="8a628-150">Poniższy przykład ilustruje takie zachowanie:</span><span class="sxs-lookup"><span data-stu-id="8a628-150">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[compound assignment with cast](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#CompoundAssignmentWithCast)]

## <a name="operator-precedence"></a><span data-ttu-id="8a628-151">Pierwszeństwo operatorów</span><span class="sxs-lookup"><span data-stu-id="8a628-151">Operator precedence</span></span>

<span data-ttu-id="8a628-152">Poniższa lista porządkuje operatory bitowe i przesunięcia, rozpoczynając od najwyższego priorytetu do najniższego:</span><span class="sxs-lookup"><span data-stu-id="8a628-152">The following list orders bitwise and shift operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="8a628-153">`~` operatora uzupełniania bitowego</span><span class="sxs-lookup"><span data-stu-id="8a628-153">Bitwise complement operator `~`</span></span>
- <span data-ttu-id="8a628-154">Operatory przesunięcia `<<` i `>>`</span><span class="sxs-lookup"><span data-stu-id="8a628-154">Shift operators `<<` and `>>`</span></span>
- <span data-ttu-id="8a628-155">Operatory logiczne i `&`</span><span class="sxs-lookup"><span data-stu-id="8a628-155">Logical AND operator `&`</span></span>
- <span data-ttu-id="8a628-156">`^` operatora logicznego wyłącznego OR</span><span class="sxs-lookup"><span data-stu-id="8a628-156">Logical exclusive OR operator `^`</span></span>
- <span data-ttu-id="8a628-157">`|` operatora logicznego OR</span><span class="sxs-lookup"><span data-stu-id="8a628-157">Logical OR operator `|`</span></span>

<span data-ttu-id="8a628-158">Użyj nawiasów `()`, aby zmienić kolejność oceny nałożona przez pierwszeństwo operatorów:</span><span class="sxs-lookup"><span data-stu-id="8a628-158">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence:</span></span>

[!code-csharp-interactive[operator precedence](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#Precedence)]

<span data-ttu-id="8a628-159">Aby uzyskać pełną listę C# operatorów uporządkowanych według poziomu pierwszeństwa, zobacz sekcję [pierwszeństwo](index.md#operator-precedence) operatorów w artykule [ C# Operators](index.md) .</span><span class="sxs-lookup"><span data-stu-id="8a628-159">For the complete list of C# operators ordered by precedence level, see the [Operator precedence](index.md#operator-precedence) section of the [C# operators](index.md) article.</span></span>

## <a name="shift-count-of-the-shift-operators"></a><span data-ttu-id="8a628-160">Liczba przesunięć operatorów przesunięcia</span><span class="sxs-lookup"><span data-stu-id="8a628-160">Shift count of the shift operators</span></span>

<span data-ttu-id="8a628-161">Dla operatorów przesunięcia `<<` i `>>`typ operandu po prawej stronie musi być `int` lub typem, który ma [wstępnie zdefiniowaną niejawną konwersję liczbową](../builtin-types/numeric-conversions.md#implicit-numeric-conversions) do `int`.</span><span class="sxs-lookup"><span data-stu-id="8a628-161">For the shift operators `<<` and `>>`, the type of the right-hand operand must be `int` or a type that has a [predefined implicit numeric conversion](../builtin-types/numeric-conversions.md#implicit-numeric-conversions) to `int`.</span></span>

<span data-ttu-id="8a628-162">W przypadku wyrażeń `x << count` i `x >> count` rzeczywista liczba przesunięć zależy od typu `x` w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="8a628-162">For the `x << count` and `x >> count` expressions, the actual shift count depends on the type of `x` as follows:</span></span>

- <span data-ttu-id="8a628-163">Jeśli typ `x` jest `int` lub `uint`, liczba przesunięć jest definiowana przez *pięć* bitów z prawej strony.</span><span class="sxs-lookup"><span data-stu-id="8a628-163">If the type of `x` is `int` or `uint`, the shift count is defined by the low-order *five* bits of the right-hand operand.</span></span> <span data-ttu-id="8a628-164">Oznacza to, że licznik przesunięć jest obliczany na podstawie `count & 0x1F` (lub `count & 0b_1_1111`).</span><span class="sxs-lookup"><span data-stu-id="8a628-164">That is, the shift count is computed from `count & 0x1F` (or `count & 0b_1_1111`).</span></span>

- <span data-ttu-id="8a628-165">Jeśli typ `x` jest `long` lub `ulong`, licznik przesunięć jest definiowany przez *sześć* -znaczących bitów operandu po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="8a628-165">If the type of `x` is `long` or `ulong`, the shift count is defined by the low-order *six* bits of the right-hand operand.</span></span> <span data-ttu-id="8a628-166">Oznacza to, że licznik przesunięć jest obliczany na podstawie `count & 0x3F` (lub `count & 0b_11_1111`).</span><span class="sxs-lookup"><span data-stu-id="8a628-166">That is, the shift count is computed from `count & 0x3F` (or `count & 0b_11_1111`).</span></span>

<span data-ttu-id="8a628-167">Poniższy przykład ilustruje takie zachowanie:</span><span class="sxs-lookup"><span data-stu-id="8a628-167">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[shift count example](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#ShiftCount)]

> [!NOTE]
> <span data-ttu-id="8a628-168">Jak pokazano w powyższym przykładzie, wynik operacji przesunięcia może być różny od zera, nawet jeśli wartość operandu po prawej stronie jest większa niż liczba bitów w lewym operandzie.</span><span class="sxs-lookup"><span data-stu-id="8a628-168">As the preceding example shows, the result of a shift operation can be non-zero even if the value of the right-hand operand is greater than the number of bits in the left-hand operand.</span></span>

## <a name="enumeration-logical-operators"></a><span data-ttu-id="8a628-169">Wyliczanie operatorów logicznych</span><span class="sxs-lookup"><span data-stu-id="8a628-169">Enumeration logical operators</span></span>

<span data-ttu-id="8a628-170">Operatory `~`, `&`, `|`i `^` są również obsługiwane przez dowolny typ [wyliczeniowy](../builtin-types/enum.md) .</span><span class="sxs-lookup"><span data-stu-id="8a628-170">The `~`, `&`, `|`, and `^` operators are also supported by any [enumeration](../builtin-types/enum.md) type.</span></span> <span data-ttu-id="8a628-171">Dla operandów o tym samym typie wyliczeniowym operacja logiczna jest wykonywana na odpowiednich wartościach bazowego typu całkowitego.</span><span class="sxs-lookup"><span data-stu-id="8a628-171">For operands of the same enumeration type, a logical operation is performed on the corresponding values of the underlying integral type.</span></span> <span data-ttu-id="8a628-172">Na przykład dla dowolnych `x` i `y` typu wyliczenia `T` z typem podstawowym `U`, wyrażenie `x & y` generuje ten sam wynik jako wyrażenie `(T)((U)x & (U)y)`.</span><span class="sxs-lookup"><span data-stu-id="8a628-172">For example, for any `x` and `y` of an enumeration type `T` with an underlying type `U`, the `x & y` expression produces the same result as the `(T)((U)x & (U)y)` expression.</span></span>

<span data-ttu-id="8a628-173">Zwykle używane są bitowe operatory logiczne z typem wyliczenia, który jest zdefiniowany przy użyciu atrybutu [flags](xref:System.FlagsAttribute) .</span><span class="sxs-lookup"><span data-stu-id="8a628-173">You typically use bitwise logical operators with an enumeration type that is defined with the [Flags](xref:System.FlagsAttribute) attribute.</span></span> <span data-ttu-id="8a628-174">Aby uzyskać więcej informacji, zobacz sekcję [typy wyliczeniowe jako flagi bitowe](../builtin-types/enum.md#enumeration-types-as-bit-flags) artykułu [typy wyliczeniowe](../builtin-types/enum.md) .</span><span class="sxs-lookup"><span data-stu-id="8a628-174">For more information, see the [Enumeration types as bit flags](../builtin-types/enum.md#enumeration-types-as-bit-flags) section of the [Enumeration types](../builtin-types/enum.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="8a628-175">Przeciążanie operatora</span><span class="sxs-lookup"><span data-stu-id="8a628-175">Operator overloadability</span></span>

<span data-ttu-id="8a628-176">Typ zdefiniowany przez użytkownika może [przeciążać](operator-overloading.md) operatory `~`, `<<`, `>>`, `&`, `|`i `^`.</span><span class="sxs-lookup"><span data-stu-id="8a628-176">A user-defined type can [overload](operator-overloading.md) the `~`, `<<`, `>>`, `&`, `|`, and `^` operators.</span></span> <span data-ttu-id="8a628-177">Gdy operator binarny jest przeciążony, odpowiadający mu operator przypisania złożonego jest również niejawnie przeciążony.</span><span class="sxs-lookup"><span data-stu-id="8a628-177">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="8a628-178">Typ zdefiniowany przez użytkownika nie może jawnie przeciążać złożonego operatora przypisania.</span><span class="sxs-lookup"><span data-stu-id="8a628-178">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

<span data-ttu-id="8a628-179">Jeśli typ zdefiniowany przez użytkownika `T` przeciążania operatora `<<` lub `>>`, typem operandu po lewej stronie musi być `T`, a typ operacji po prawej stronie musi być `int`.</span><span class="sxs-lookup"><span data-stu-id="8a628-179">If a user-defined type `T` overloads the `<<` or `>>` operator, the type of the left-hand operand must be `T` and the type of the right-hand operand must be `int`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="8a628-180">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="8a628-180">C# language specification</span></span>

<span data-ttu-id="8a628-181">Aby uzyskać więcej informacji, zobacz następujące sekcje [ C# specyfikacji języka](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="8a628-181">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="8a628-182">Operator dopełnienia bitowego</span><span class="sxs-lookup"><span data-stu-id="8a628-182">Bitwise complement operator</span></span>](~/_csharplang/spec/expressions.md#bitwise-complement-operator)
- [<span data-ttu-id="8a628-183">Operatory przesunięcia</span><span class="sxs-lookup"><span data-stu-id="8a628-183">Shift operators</span></span>](~/_csharplang/spec/expressions.md#shift-operators)
- [<span data-ttu-id="8a628-184">Operatory logiczne</span><span class="sxs-lookup"><span data-stu-id="8a628-184">Logical operators</span></span>](~/_csharplang/spec/expressions.md#logical-operators)
- [<span data-ttu-id="8a628-185">Przypisanie złożone</span><span class="sxs-lookup"><span data-stu-id="8a628-185">Compound assignment</span></span>](~/_csharplang/spec/expressions.md#compound-assignment)
- [<span data-ttu-id="8a628-186">Promocje numeryczne</span><span class="sxs-lookup"><span data-stu-id="8a628-186">Numeric promotions</span></span>](~/_csharplang/spec/expressions.md#numeric-promotions)

## <a name="see-also"></a><span data-ttu-id="8a628-187">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8a628-187">See also</span></span>

- [<span data-ttu-id="8a628-188">C#odwoła</span><span class="sxs-lookup"><span data-stu-id="8a628-188">C# reference</span></span>](../index.md)
- [<span data-ttu-id="8a628-189">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="8a628-189">C# operators</span></span>](index.md)
- [<span data-ttu-id="8a628-190">Operatory logiczne Boolean</span><span class="sxs-lookup"><span data-stu-id="8a628-190">Boolean logical operators</span></span>](boolean-logical-operators.md)
