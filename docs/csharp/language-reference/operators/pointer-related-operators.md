---
title: Operatory powiązane z wskaźnikiem — odwołanie do języka C#
description: Dowiedz się więcej o operatorach języka C#, których można używać podczas pracy ze wskaźnikami.
ms.date: 05/20/2019
author: pkulikov
f1_keywords:
- ->_CSharpKeyword
helpviewer_keywords:
- pointer related operators [C#]
- address-of operator [C#]
- '& operator [C#]'
- pointer indirection operator [C#]
- dereference operator [C#]
- '* operator [C#]'
- pointer member access operator [C#]
- -> operator [C#]
- pointer element access [C#]
- '[] operator [C#]'
- pointer arithmetic [C#]
- pointer increment [C#]
- pointer decrement [C#]
- pointer comparison [C#]
ms.openlocfilehash: 7c95fe07220a78b388a5c6850e4123feb029d951
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399547"
---
# <a name="pointer-related-operators-c-reference"></a><span data-ttu-id="f1901-103">Operatory powiązane ze wskaźnikiem (odwołanie do języka C#)</span><span class="sxs-lookup"><span data-stu-id="f1901-103">Pointer related operators (C# reference)</span></span>

<span data-ttu-id="f1901-104">Do pracy ze wskaźnikami można używać następujących operatorów:</span><span class="sxs-lookup"><span data-stu-id="f1901-104">You can use the following operators to work with pointers:</span></span>

- <span data-ttu-id="f1901-105">Operator unary [ `&` (address-of):](#address-of-operator-) aby uzyskać adres zmiennej</span><span class="sxs-lookup"><span data-stu-id="f1901-105">Unary [`&` (address-of)](#address-of-operator-) operator: to get the address of a variable</span></span>
- <span data-ttu-id="f1901-106">Operator jednoargumentowy [ `*` (pośredni wskaźnik):](#pointer-indirection-operator-) aby uzyskać zmienną wskazywaną przez wskaźnik</span><span class="sxs-lookup"><span data-stu-id="f1901-106">Unary [`*` (pointer indirection)](#pointer-indirection-operator-) operator: to obtain the variable pointed by a pointer</span></span>
- <span data-ttu-id="f1901-107">[ `->` Operatorzy (dostęp do elementów członkowskich)](#pointer-member-access-operator--) i [ `[]` (dostęp do elementów)](#pointer-element-access-operator-)</span><span class="sxs-lookup"><span data-stu-id="f1901-107">The [`->` (member access)](#pointer-member-access-operator--) and [`[]` (element access)](#pointer-element-access-operator-) operators</span></span>
- <span data-ttu-id="f1901-108">Operatory [ `+` `-`arytmetyczne `++`, , i`--`](#pointer-arithmetic-operators)</span><span class="sxs-lookup"><span data-stu-id="f1901-108">Arithmetic operators [`+`, `-`, `++`, and `--`](#pointer-arithmetic-operators)</span></span>
- <span data-ttu-id="f1901-109">Operatorzy [ `==` `!=` `<`porównania `>` `<=`, , , i`>=`](#pointer-comparison-operators)</span><span class="sxs-lookup"><span data-stu-id="f1901-109">Comparison operators [`==`, `!=`, `<`, `>`, `<=`, and `>=`](#pointer-comparison-operators)</span></span>

<span data-ttu-id="f1901-110">Aby uzyskać informacje o typach wskaźników, zobacz [Typy wskaźników](../../programming-guide/unsafe-code-pointers/pointer-types.md).</span><span class="sxs-lookup"><span data-stu-id="f1901-110">For information about pointer types, see [Pointer types](../../programming-guide/unsafe-code-pointers/pointer-types.md).</span></span>

> [!NOTE]
> <span data-ttu-id="f1901-111">Każda operacja ze wskaźnikami wymaga [niebezpiecznego](../keywords/unsafe.md) kontekstu.</span><span class="sxs-lookup"><span data-stu-id="f1901-111">Any operation with pointers requires an [unsafe](../keywords/unsafe.md) context.</span></span> <span data-ttu-id="f1901-112">Kod, który zawiera niebezpieczne bloki [`-unsafe`](../compiler-options/unsafe-compiler-option.md) muszą być skompilowane z opcją kompilatora.</span><span class="sxs-lookup"><span data-stu-id="f1901-112">The code that contains unsafe blocks must be compiled with the [`-unsafe`](../compiler-options/unsafe-compiler-option.md) compiler option.</span></span>

## <a name="address-of-operator-"></a><span data-ttu-id="f1901-113">Operator adresowy&amp;</span><span class="sxs-lookup"><span data-stu-id="f1901-113">Address-of operator &amp;</span></span>

<span data-ttu-id="f1901-114">Operator nieurodzajny `&` zwraca adres swojego operandu:</span><span class="sxs-lookup"><span data-stu-id="f1901-114">The unary `&` operator returns the address of its operand:</span></span>

[!code-csharp[address of local](snippets/PointerOperators.cs#AddressOf)]

<span data-ttu-id="f1901-115">Operand `&` operatora musi być zmienną stałą.</span><span class="sxs-lookup"><span data-stu-id="f1901-115">The operand of the `&` operator must be a fixed variable.</span></span> <span data-ttu-id="f1901-116">*Zmienne stałe* są zmienne, które znajdują się w miejscach magazynowania, które nie mają wpływu na działanie [modułu odśmiecania pamięci](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="f1901-116">*Fixed* variables are variables that reside in storage locations that are unaffected by operation of the [garbage collector](../../../standard/garbage-collection/index.md).</span></span> <span data-ttu-id="f1901-117">W poprzednim przykładzie zmienna `number` lokalna jest zmienną stałą, ponieważ znajduje się na stosie.</span><span class="sxs-lookup"><span data-stu-id="f1901-117">In the preceding example, the local variable `number` is a fixed variable, because it resides on the stack.</span></span> <span data-ttu-id="f1901-118">Zmienne znajdujące się w lokalizacjach magazynu, na które może mieć wpływ moduł odśmiecania pamięci (na przykład przeniesiony) są nazywane zmiennymi *ruchomymi.*</span><span class="sxs-lookup"><span data-stu-id="f1901-118">Variables that reside in storage locations that can be affected by the garbage collector (for example, relocated) are called *movable* variables.</span></span> <span data-ttu-id="f1901-119">Pola obiektów i elementy tablicy są przykładami zmiennych ruchomych.</span><span class="sxs-lookup"><span data-stu-id="f1901-119">Object fields and array elements are examples of movable variables.</span></span> <span data-ttu-id="f1901-120">Możesz uzyskać adres ruchomej zmiennej, jeśli "naprawisz" lub "pin", z [ `fixed` oświadczeniem](../keywords/fixed-statement.md).</span><span class="sxs-lookup"><span data-stu-id="f1901-120">You can get the address of a movable variable if you "fix", or "pin", it with a [`fixed` statement](../keywords/fixed-statement.md).</span></span> <span data-ttu-id="f1901-121">Otrzymany adres jest prawidłowy tylko `fixed` wewnątrz bloku instrukcji.</span><span class="sxs-lookup"><span data-stu-id="f1901-121">The obtained address is valid only inside the block of a `fixed` statement.</span></span> <span data-ttu-id="f1901-122">W poniższym przykładzie pokazano, `fixed` `&` jak używać instrukcji i operatora:</span><span class="sxs-lookup"><span data-stu-id="f1901-122">The following example shows how to use a `fixed` statement and the `&` operator:</span></span>

[!code-csharp[address of fixed](snippets/PointerOperators.cs#AddressOfFixed)]

<span data-ttu-id="f1901-123">Nie można uzyskać adresu stałej lub wartości.</span><span class="sxs-lookup"><span data-stu-id="f1901-123">You can't get the address of a constant or a value.</span></span>

<span data-ttu-id="f1901-124">Aby uzyskać więcej informacji na temat zmiennych stałych i ruchomych, zobacz [stałe i ruchome zmienne](~/_csharplang/spec/unsafe-code.md#fixed-and-moveable-variables) sekcji [specyfikacji języka C#.](~/_csharplang/spec/introduction.md)</span><span class="sxs-lookup"><span data-stu-id="f1901-124">For more information about fixed and movable variables, see the [Fixed and moveable variables](~/_csharplang/spec/unsafe-code.md#fixed-and-moveable-variables) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="f1901-125">Operator `&` binarny oblicza [logiczne i jego](boolean-logical-operators.md#logical-and-operator-) operands boolean lub [bitwise logiczne i](bitwise-and-shift-operators.md#logical-and-operator-) jego integralną operands.</span><span class="sxs-lookup"><span data-stu-id="f1901-125">The binary `&` operator computes the [logical AND](boolean-logical-operators.md#logical-and-operator-) of its Boolean operands or the [bitwise logical AND](bitwise-and-shift-operators.md#logical-and-operator-) of its integral operands.</span></span>

## <a name="pointer-indirection-operator-"></a><span data-ttu-id="f1901-126">Operator pośredni wskaźnika \*</span><span class="sxs-lookup"><span data-stu-id="f1901-126">Pointer indirection operator \*</span></span>

<span data-ttu-id="f1901-127">Operator `*` pośredni wskaźnika jednoargumentowego uzyskuje zmienną, do której wskazuje jego operand.</span><span class="sxs-lookup"><span data-stu-id="f1901-127">The unary pointer indirection operator `*` obtains the variable to which its operand points.</span></span> <span data-ttu-id="f1901-128">Jest również znany jako operator wyłusk.</span><span class="sxs-lookup"><span data-stu-id="f1901-128">It's also known as the dereference operator.</span></span> <span data-ttu-id="f1901-129">Operand `*` operatora musi być typu wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="f1901-129">The operand of the `*` operator must be of a pointer type.</span></span>

[!code-csharp[pointer indirection](snippets/PointerOperators.cs#PointerIndirection)]

<span data-ttu-id="f1901-130">Nie można `*` zastosować operatora do `void*`wyrażenia typu .</span><span class="sxs-lookup"><span data-stu-id="f1901-130">You cannot apply the `*` operator to an expression of type `void*`.</span></span>

<span data-ttu-id="f1901-131">Operator `*` binarny oblicza [iloczyn](arithmetic-operators.md#multiplication-operator-) swoich operacji numerycznych.</span><span class="sxs-lookup"><span data-stu-id="f1901-131">The binary `*` operator computes the [product](arithmetic-operators.md#multiplication-operator-) of its numeric operands.</span></span>

## <a name="pointer-member-access-operator--"></a><span data-ttu-id="f1901-132">Operator dostępu do elementu członkowskiego wskaźnika -></span><span class="sxs-lookup"><span data-stu-id="f1901-132">Pointer member access operator -></span></span>

<span data-ttu-id="f1901-133">Operator `->` łączy [wskaźnik pośredni](#pointer-indirection-operator-) i [dostęp do elementu członkowskiego](member-access-operators.md#member-access-operator-).</span><span class="sxs-lookup"><span data-stu-id="f1901-133">The `->` operator combines [pointer indirection](#pointer-indirection-operator-) and [member access](member-access-operators.md#member-access-operator-).</span></span> <span data-ttu-id="f1901-134">Oznacza to, `x` że jeśli `T*` jest `y` wskaźnikiem typu `T`i jest dostępnym elementem członkowskim typu , wyrażenie monin</span><span class="sxs-lookup"><span data-stu-id="f1901-134">That is, if `x` is a pointer of type `T*` and `y` is an accessible member of type `T`, an expression of the form</span></span>

```csharp
x->y
```

<span data-ttu-id="f1901-135">jest równoważny</span><span class="sxs-lookup"><span data-stu-id="f1901-135">is equivalent to</span></span>

```csharp
(*x).y
```

<span data-ttu-id="f1901-136">W poniższym przykładzie przedstawiono `->` użycie operatora:</span><span class="sxs-lookup"><span data-stu-id="f1901-136">The following example demonstrates the usage of the `->` operator:</span></span>

[!code-csharp[pointer member access](snippets/PointerOperators.cs#MemberAccess)]

<span data-ttu-id="f1901-137">Nie można `->` zastosować operatora do `void*`wyrażenia typu .</span><span class="sxs-lookup"><span data-stu-id="f1901-137">You cannot apply the `->` operator to an expression of type `void*`.</span></span>

## <a name="pointer-element-access-operator-"></a><span data-ttu-id="f1901-138">Operator dostępu do elementu wskaźnika []</span><span class="sxs-lookup"><span data-stu-id="f1901-138">Pointer element access operator []</span></span>

<span data-ttu-id="f1901-139">Dla wyrażenia `p` typu wskaźnika dostęp elementu wskaźnika `p[n]` formularza jest `*(p + n)` `n` obliczany jako , gdzie musi `int`być `uint` `long`typu `ulong`niejawnie cabrio do , , , lub .</span><span class="sxs-lookup"><span data-stu-id="f1901-139">For an expression `p` of a pointer type, a pointer element access of the form `p[n]` is evaluated as `*(p + n)`, where `n` must be of a type implicitly convertible to `int`, `uint`, `long`, or `ulong`.</span></span> <span data-ttu-id="f1901-140">Aby uzyskać informacje na `+` temat zachowania operatora ze wskaźnikami, zobacz [Dodawanie lub odejmowanie wartości integralnej do lub z sekcji wskaźnika.](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer)</span><span class="sxs-lookup"><span data-stu-id="f1901-140">For information about the behavior of the `+` operator with pointers, see the [Addition or subtraction of an integral value to or from a pointer](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) section.</span></span>

<span data-ttu-id="f1901-141">W poniższym przykładzie pokazano, jak uzyskać `[]` dostęp do elementów tablicy ze wskaźnikiem i operatorem:</span><span class="sxs-lookup"><span data-stu-id="f1901-141">The following example demonstrates how to access array elements with a pointer and the `[]` operator:</span></span>

[!code-csharp[pointer element access](snippets/PointerOperators.cs#ElementAccess)]

<span data-ttu-id="f1901-142">W przykładzie [ `stackalloc` ](stackalloc.md) użyto operatora do przydzielenia bloku pamięci na stosie.</span><span class="sxs-lookup"><span data-stu-id="f1901-142">The example uses the [`stackalloc` operator](stackalloc.md) to allocate a block of memory on the stack.</span></span>

> [!NOTE]
> <span data-ttu-id="f1901-143">Operator dostępu do elementu wskaźnika nie sprawdza błędów poza granicami.</span><span class="sxs-lookup"><span data-stu-id="f1901-143">The pointer element access operator doesn't check for out-of-bounds errors.</span></span>

<span data-ttu-id="f1901-144">Nie można `[]` użyć dostępu do elementu `void*`wskaźnika z wyrażeniem typu .</span><span class="sxs-lookup"><span data-stu-id="f1901-144">You cannot use `[]` for pointer element access with an expression of type `void*`.</span></span>

<span data-ttu-id="f1901-145">Można również użyć `[]` operatora dla [dostępu do elementu tablicy lub indeksatora](member-access-operators.md#indexer-operator-).</span><span class="sxs-lookup"><span data-stu-id="f1901-145">You also can use the `[]` operator for [array element or indexer access](member-access-operators.md#indexer-operator-).</span></span>

## <a name="pointer-arithmetic-operators"></a><span data-ttu-id="f1901-146">Operatory arytmetyczne wskaźnika</span><span class="sxs-lookup"><span data-stu-id="f1901-146">Pointer arithmetic operators</span></span>

<span data-ttu-id="f1901-147">Za pomocą wskaźników można wykonywać następujące operacje arytmetyczne:</span><span class="sxs-lookup"><span data-stu-id="f1901-147">You can perform the following arithmetic operations with pointers:</span></span>

- <span data-ttu-id="f1901-148">Dodawanie lub odejmowanie wartości integralnej do lub ze wskaźnika</span><span class="sxs-lookup"><span data-stu-id="f1901-148">Add or subtract an integral value to or from a pointer</span></span>
- <span data-ttu-id="f1901-149">Odejmowanie dwóch wskaźników</span><span class="sxs-lookup"><span data-stu-id="f1901-149">Subtract two pointers</span></span>
- <span data-ttu-id="f1901-150">Zwiększanie lub zmniejszanie wskaźnika</span><span class="sxs-lookup"><span data-stu-id="f1901-150">Increment or decrement a pointer</span></span>

<span data-ttu-id="f1901-151">Nie można wykonać tych operacji `void*`ze wskaźnikami typu .</span><span class="sxs-lookup"><span data-stu-id="f1901-151">You cannot perform those operations with pointers of type `void*`.</span></span>

<span data-ttu-id="f1901-152">Aby uzyskać informacje o obsługiwanych operacjach arytmetycznych z typami liczbowymi, zobacz [Operatory arytmetyczne](arithmetic-operators.md).</span><span class="sxs-lookup"><span data-stu-id="f1901-152">For information about supported arithmetic operations with numeric types, see [Arithmetic operators](arithmetic-operators.md).</span></span>

### <a name="addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer"></a><span data-ttu-id="f1901-153">Dodawanie lub odejmowanie wartości integralnej do lub ze wskaźnika</span><span class="sxs-lookup"><span data-stu-id="f1901-153">Addition or subtraction of an integral value to or from a pointer</span></span>

<span data-ttu-id="f1901-154">`p` Dla wskaźnika `T*` typu i `n` wyrażenia typu niejawnie `int` `uint`konwertowalne na , , `long`lub `ulong`, dodawanie i odejmowanie są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="f1901-154">For a pointer `p` of type `T*` and an expression `n` of a type implicitly convertible to `int`, `uint`, `long`, or `ulong`, addition and subtraction are defined as follows:</span></span>

- <span data-ttu-id="f1901-155">Oba `p + n` `n + p` i wyrażenia dają wskaźnik `T*` typu, `n * sizeof(T)` który wynika z `p`dodawania do adresu podane przez .</span><span class="sxs-lookup"><span data-stu-id="f1901-155">Both `p + n` and `n + p` expressions produce a pointer of type `T*` that results from adding `n * sizeof(T)` to the address given by `p`.</span></span>
- <span data-ttu-id="f1901-156">Wyrażenie `p - n` generuje wskaźnik typu, `T*` który wynika z `n * sizeof(T)` odjęcia `p`od adresu podane przez .</span><span class="sxs-lookup"><span data-stu-id="f1901-156">The `p - n` expression produces a pointer of type `T*` that results from subtracting `n * sizeof(T)` from the address given by `p`.</span></span>

<span data-ttu-id="f1901-157">[ `sizeof` Operator](sizeof.md) uzyskuje rozmiar typu w bajtach.</span><span class="sxs-lookup"><span data-stu-id="f1901-157">The [`sizeof` operator](sizeof.md) obtains the size of a type in bytes.</span></span>

<span data-ttu-id="f1901-158">W poniższym przykładzie przedstawiono `+` użycie operatora ze wskaźnikiem:</span><span class="sxs-lookup"><span data-stu-id="f1901-158">The following example demonstrates the usage of the `+` operator with a pointer:</span></span>

[!code-csharp[pointer addition](snippets/PointerOperators.cs#AddNumber)]

### <a name="pointer-subtraction"></a><span data-ttu-id="f1901-159">Odejmowanie wskaźnika</span><span class="sxs-lookup"><span data-stu-id="f1901-159">Pointer subtraction</span></span>

<span data-ttu-id="f1901-160">Dla dwóch `p1` wskaźników `p2` i `T*`typu `p1 - p2` wyrażenie tworzy różnicę między adresami podanymi przez `p1` i `p2` podzielonymi przez `sizeof(T)`.</span><span class="sxs-lookup"><span data-stu-id="f1901-160">For two pointers `p1` and `p2` of type `T*`, the expression `p1 - p2` produces the difference between the addresses given by `p1` and `p2` divided by `sizeof(T)`.</span></span> <span data-ttu-id="f1901-161">Typem wyniku jest `long`.</span><span class="sxs-lookup"><span data-stu-id="f1901-161">The type of the result is `long`.</span></span> <span data-ttu-id="f1901-162">Oznacza to, `p1 - p2` że `((long)(p1) - (long)(p2)) / sizeof(T)`jest obliczana jako .</span><span class="sxs-lookup"><span data-stu-id="f1901-162">That is, `p1 - p2` is computed as `((long)(p1) - (long)(p2)) / sizeof(T)`.</span></span>

<span data-ttu-id="f1901-163">W poniższym przykładzie przedstawiono odejmowanie wskaźnika:</span><span class="sxs-lookup"><span data-stu-id="f1901-163">The following example demonstrates the pointer subtraction:</span></span>

[!code-csharp[pointer subtraction](snippets/PointerOperators.cs#SubtractPointers)]

### <a name="pointer-increment-and-decrement"></a><span data-ttu-id="f1901-164">Przyrost wskaźnika i zmniejszanie</span><span class="sxs-lookup"><span data-stu-id="f1901-164">Pointer increment and decrement</span></span>

<span data-ttu-id="f1901-165">Operator `++` przyrostu [dodaje](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) 1 do swojego operandu wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="f1901-165">The `++` increment operator [adds](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) 1 to its pointer operand.</span></span> <span data-ttu-id="f1901-166">Operator `--` zmniejszania [odejmuje](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) 1 od swojego operandu wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="f1901-166">The `--` decrement operator [subtracts](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) 1 from its pointer operand.</span></span>

<span data-ttu-id="f1901-167">Oba operatory są obsługiwane w dwóch`p++` `p--`formach: postfix ( i ) i prefiks (`++p` i `--p`).</span><span class="sxs-lookup"><span data-stu-id="f1901-167">Both operators are supported in two forms: postfix (`p++` and `p--`) and prefix (`++p` and `--p`).</span></span> <span data-ttu-id="f1901-168">Wynik `p++` i `p--` jest wartością `p` *przed* operacją.</span><span class="sxs-lookup"><span data-stu-id="f1901-168">The result of `p++` and `p--` is the value of `p` *before* the operation.</span></span> <span data-ttu-id="f1901-169">Wynik `++p` i `--p` jest wartością `p` *po* operacji.</span><span class="sxs-lookup"><span data-stu-id="f1901-169">The result of `++p` and `--p` is the value of `p` *after* the operation.</span></span>

<span data-ttu-id="f1901-170">W poniższym przykładzie przedstawiono zachowanie zarówno operatorów przyrostu postfix i prefiksu:</span><span class="sxs-lookup"><span data-stu-id="f1901-170">The following example demonstrates the behavior of both postfix and prefix increment operators:</span></span>

[!code-csharp[pointer increment](snippets/PointerOperators.cs#Increment)]

## <a name="pointer-comparison-operators"></a><span data-ttu-id="f1901-171">Operatory porównania wskaźników</span><span class="sxs-lookup"><span data-stu-id="f1901-171">Pointer comparison operators</span></span>

<span data-ttu-id="f1901-172">Za pomocą `==`operacji `!=` `<` `>` `<=` `>=` można porównywać operandy dowolnego typu wskaźnika, `void*`w tym .</span><span class="sxs-lookup"><span data-stu-id="f1901-172">You can use the `==`, `!=`, `<`, `>`, `<=`, and `>=` operators to compare operands of any pointer type, including `void*`.</span></span> <span data-ttu-id="f1901-173">Operatorzy ci porównują adresy podane przez dwa argumenty tak, jakby były liczbami całkowitymi bez znaku.</span><span class="sxs-lookup"><span data-stu-id="f1901-173">Those operators compare the addresses given by the two operands as if they were unsigned integers.</span></span>

<span data-ttu-id="f1901-174">Aby uzyskać informacje na temat zachowania tych operatorów dla operandów innych typów, zobacz [Operatory równości](equality-operators.md) i [porównywania operatorów artykułów.](comparison-operators.md)</span><span class="sxs-lookup"><span data-stu-id="f1901-174">For information about the behavior of those operators for operands of other types, see the [Equality operators](equality-operators.md) and [Comparison operators](comparison-operators.md) articles.</span></span>

## <a name="operator-precedence"></a><span data-ttu-id="f1901-175">Pierwszeństwo operatorów</span><span class="sxs-lookup"><span data-stu-id="f1901-175">Operator precedence</span></span>

<span data-ttu-id="f1901-176">Następująca lista zleca operatory powiązane ze wskaźnikiem, zaczynając od najwyższego pierwszeństwa do najniższego:</span><span class="sxs-lookup"><span data-stu-id="f1901-176">The following list orders pointer related operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="f1901-177">Operatory `x++` przyrostkowe i `x--` zmniejszania `->` `[]` oraz operatorzy i operatorzy</span><span class="sxs-lookup"><span data-stu-id="f1901-177">Postfix increment `x++` and decrement `x--` operators and the `->` and `[]` operators</span></span>
- <span data-ttu-id="f1901-178">Operatory przyrostu `++x` i zmniejszania `--x` prefiksów oraz operatorzy `&` i `*` operatorzy</span><span class="sxs-lookup"><span data-stu-id="f1901-178">Prefix increment `++x` and decrement `--x` operators and the `&` and `*` operators</span></span>
- <span data-ttu-id="f1901-179">`+` Dodatki `-` i podmioty gospodarcze</span><span class="sxs-lookup"><span data-stu-id="f1901-179">Additive `+` and `-` operators</span></span>
- <span data-ttu-id="f1901-180">Porównanie `<` `>`, `<=`i `>=` operatorzy</span><span class="sxs-lookup"><span data-stu-id="f1901-180">Comparison `<`, `>`, `<=`, and `>=` operators</span></span>
- <span data-ttu-id="f1901-181">`==` Równość `!=` i operatorzy</span><span class="sxs-lookup"><span data-stu-id="f1901-181">Equality `==` and `!=` operators</span></span>

<span data-ttu-id="f1901-182">Użyj nawiasów, `()`, aby zmienić kolejność oceny narzuconą przez pierwszeństwo operatora.</span><span class="sxs-lookup"><span data-stu-id="f1901-182">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence.</span></span>

<span data-ttu-id="f1901-183">Aby uzyskać pełną listę operatorów Języka C# uporządkowane według poziomu pierwszeństwa, zobacz [pierwszeństwo operatora](index.md#operator-precedence) sekcji [operatorów C#artykułu.](index.md)</span><span class="sxs-lookup"><span data-stu-id="f1901-183">For the complete list of C# operators ordered by precedence level, see the [Operator precedence](index.md#operator-precedence) section of the [C# operators](index.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="f1901-184">Przeciążenie operatora</span><span class="sxs-lookup"><span data-stu-id="f1901-184">Operator overloadability</span></span>

<span data-ttu-id="f1901-185">Typ zdefiniowany przez użytkownika nie może `&` `*`przeciążyć operatorów związanych ze wskaźnikiem , , `->`i `[]`.</span><span class="sxs-lookup"><span data-stu-id="f1901-185">A user-defined type cannot overload the pointer related operators `&`, `*`, `->`, and `[]`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="f1901-186">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="f1901-186">C# language specification</span></span>

<span data-ttu-id="f1901-187">Aby uzyskać więcej informacji, zobacz następujące sekcje [specyfikacji języka Języka C#:](~/_csharplang/spec/introduction.md)</span><span class="sxs-lookup"><span data-stu-id="f1901-187">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="f1901-188">Zmienne stałe i ruchome</span><span class="sxs-lookup"><span data-stu-id="f1901-188">Fixed and moveable variables</span></span>](~/_csharplang/spec/unsafe-code.md#fixed-and-moveable-variables)
- [<span data-ttu-id="f1901-189">Operator adresowy</span><span class="sxs-lookup"><span data-stu-id="f1901-189">The address-of operator</span></span>](~/_csharplang/spec/unsafe-code.md#the-address-of-operator)
- [<span data-ttu-id="f1901-190">Wskaźnik pośredni</span><span class="sxs-lookup"><span data-stu-id="f1901-190">Pointer indirection</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-indirection)
- [<span data-ttu-id="f1901-191">Dostęp do elementu członkowskiego wskaźnika</span><span class="sxs-lookup"><span data-stu-id="f1901-191">Pointer member access</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-member-access)
- [<span data-ttu-id="f1901-192">Dostęp do elementu wskaźnika</span><span class="sxs-lookup"><span data-stu-id="f1901-192">Pointer element access</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-element-access)
- [<span data-ttu-id="f1901-193">Arytmetyczny wskaźnik</span><span class="sxs-lookup"><span data-stu-id="f1901-193">Pointer arithmetic</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-arithmetic)
- [<span data-ttu-id="f1901-194">Przyrost wskaźnika i zmniejszanie</span><span class="sxs-lookup"><span data-stu-id="f1901-194">Pointer increment and decrement</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-increment-and-decrement)
- [<span data-ttu-id="f1901-195">Porównanie wskaźnika</span><span class="sxs-lookup"><span data-stu-id="f1901-195">Pointer comparison</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-comparison)

## <a name="see-also"></a><span data-ttu-id="f1901-196">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f1901-196">See also</span></span>

- [<span data-ttu-id="f1901-197">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="f1901-197">C# reference</span></span>](../index.md)
- [<span data-ttu-id="f1901-198">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="f1901-198">C# operators</span></span>](index.md)
- [<span data-ttu-id="f1901-199">Typy wskaźnika</span><span class="sxs-lookup"><span data-stu-id="f1901-199">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="f1901-200">niebezpieczne słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="f1901-200">unsafe keyword</span></span>](../keywords/unsafe.md)
- [<span data-ttu-id="f1901-201">stałe słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="f1901-201">fixed keyword</span></span>](../keywords/fixed-statement.md)
- [<span data-ttu-id="f1901-202">stackalloc, operator</span><span class="sxs-lookup"><span data-stu-id="f1901-202">stackalloc operator</span></span>](stackalloc.md)
- [<span data-ttu-id="f1901-203">sizeof, operator</span><span class="sxs-lookup"><span data-stu-id="f1901-203">sizeof operator</span></span>](sizeof.md)
