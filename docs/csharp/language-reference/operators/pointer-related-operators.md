---
title: Operatory powiązane ze wskaźnikiem — odwołanie do języka C#
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
ms.openlocfilehash: fd25cd419f8c3bfe905850e6a252f4a8cf65478c
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79507103"
---
# <a name="pointer-related-operators-c-reference"></a><span data-ttu-id="56c9c-103">Operatory powiązane ze wskaźnikiem (odwołanie do języka C#)</span><span class="sxs-lookup"><span data-stu-id="56c9c-103">Pointer related operators (C# reference)</span></span>

<span data-ttu-id="56c9c-104">Do pracy ze wskaźnikami można używać następujących operatorów:</span><span class="sxs-lookup"><span data-stu-id="56c9c-104">You can use the following operators to work with pointers:</span></span>

- <span data-ttu-id="56c9c-105">Operator [ `&` dwuaryjny (adres:](#address-of-operator-) aby uzyskać adres zmiennej</span><span class="sxs-lookup"><span data-stu-id="56c9c-105">Unary [`&` (address-of)](#address-of-operator-) operator: to get the address of a variable</span></span>
- <span data-ttu-id="56c9c-106">Operator unary [ `*` (pośredni wskaźnik):](#pointer-indirection-operator-) aby uzyskać zmienną wskazywana przez wskaźnik</span><span class="sxs-lookup"><span data-stu-id="56c9c-106">Unary [`*` (pointer indirection)](#pointer-indirection-operator-) operator: to obtain the variable pointed by a pointer</span></span>
- <span data-ttu-id="56c9c-107">Operatory [ `->` (dostęp do elementów członkowskich)](#pointer-member-access-operator--) i [ `[]` (dostęp do elementów)](#pointer-element-access-operator-)</span><span class="sxs-lookup"><span data-stu-id="56c9c-107">The [`->` (member access)](#pointer-member-access-operator--) and [`[]` (element access)](#pointer-element-access-operator-) operators</span></span>
- <span data-ttu-id="56c9c-108">Operatory [ `+` `-`arytmetyczne `++`, , i`--`](#pointer-arithmetic-operators)</span><span class="sxs-lookup"><span data-stu-id="56c9c-108">Arithmetic operators [`+`, `-`, `++`, and `--`](#pointer-arithmetic-operators)</span></span>
- <span data-ttu-id="56c9c-109">Operatory [ `==` `!=`porównawcze `>` `<=`, `<`, , , i`>=`](#pointer-comparison-operators)</span><span class="sxs-lookup"><span data-stu-id="56c9c-109">Comparison operators [`==`, `!=`, `<`, `>`, `<=`, and `>=`](#pointer-comparison-operators)</span></span>

<span data-ttu-id="56c9c-110">Aby uzyskać informacje o typach wskaźników, zobacz [Typy wskaźników](../../programming-guide/unsafe-code-pointers/pointer-types.md).</span><span class="sxs-lookup"><span data-stu-id="56c9c-110">For information about pointer types, see [Pointer types](../../programming-guide/unsafe-code-pointers/pointer-types.md).</span></span>

> [!NOTE]
> <span data-ttu-id="56c9c-111">Każda operacja ze wskaźnikami wymaga [niebezpiecznego](../keywords/unsafe.md) kontekstu.</span><span class="sxs-lookup"><span data-stu-id="56c9c-111">Any operation with pointers requires an [unsafe](../keywords/unsafe.md) context.</span></span> <span data-ttu-id="56c9c-112">Kod, który zawiera niebezpieczne bloki muszą [`-unsafe`](../compiler-options/unsafe-compiler-option.md) być skompilowane z opcją kompilatora.</span><span class="sxs-lookup"><span data-stu-id="56c9c-112">The code that contains unsafe blocks must be compiled with the [`-unsafe`](../compiler-options/unsafe-compiler-option.md) compiler option.</span></span>

## <a name="address-of-operator-amp"></a><a name="address-of-operator-"></a><span data-ttu-id="56c9c-113">Adres operatora&amp;</span><span class="sxs-lookup"><span data-stu-id="56c9c-113">Address-of operator &amp;</span></span>

<span data-ttu-id="56c9c-114">Operator unary `&` zwraca adres swojego operandu:</span><span class="sxs-lookup"><span data-stu-id="56c9c-114">The unary `&` operator returns the address of its operand:</span></span>

[!code-csharp[address of local](snippets/PointerOperators.cs#AddressOf)]

<span data-ttu-id="56c9c-115">Operand `&` operatora musi być zmienną stałą.</span><span class="sxs-lookup"><span data-stu-id="56c9c-115">The operand of the `&` operator must be a fixed variable.</span></span> <span data-ttu-id="56c9c-116">*Stałe* zmienne to zmienne, które znajdują się w lokalizacjach magazynu, na które nie ma wpływu działanie modułu zbierającego [elementy bezużyteczne.](../../../standard/garbage-collection/index.md)</span><span class="sxs-lookup"><span data-stu-id="56c9c-116">*Fixed* variables are variables that reside in storage locations that are unaffected by operation of the [garbage collector](../../../standard/garbage-collection/index.md).</span></span> <span data-ttu-id="56c9c-117">W poprzednim przykładzie zmienna `number` lokalna jest zmienną stałą, ponieważ znajduje się na stosie.</span><span class="sxs-lookup"><span data-stu-id="56c9c-117">In the preceding example, the local variable `number` is a fixed variable, because it resides on the stack.</span></span> <span data-ttu-id="56c9c-118">Zmienne, które znajdują się w lokalizacjach magazynu, które mogą mieć wpływ na moduł zbierający elementy bezużyteczne (na przykład przeniesiony) są *nazywane* zmiennymi ruchomymi.</span><span class="sxs-lookup"><span data-stu-id="56c9c-118">Variables that reside in storage locations that can be affected by the garbage collector (for example, relocated) are called *movable* variables.</span></span> <span data-ttu-id="56c9c-119">Pola obiektów i elementy tablicy są przykładami zmiennych ruchomych.</span><span class="sxs-lookup"><span data-stu-id="56c9c-119">Object fields and array elements are examples of movable variables.</span></span> <span data-ttu-id="56c9c-120">Możesz uzyskać adres zmiennej ruchomej, jeśli "naprawić" lub "przypiąć", to z [ `fixed` instrukcją](../keywords/fixed-statement.md).</span><span class="sxs-lookup"><span data-stu-id="56c9c-120">You can get the address of a movable variable if you "fix", or "pin", it with a [`fixed` statement](../keywords/fixed-statement.md).</span></span> <span data-ttu-id="56c9c-121">Uzyskany adres jest prawidłowy tylko `fixed` wewnątrz bloku instrukcji.</span><span class="sxs-lookup"><span data-stu-id="56c9c-121">The obtained address is valid only inside the block of a `fixed` statement.</span></span> <span data-ttu-id="56c9c-122">W poniższym `fixed` przykładzie pokazano, `&` jak używać instrukcji i operatora:</span><span class="sxs-lookup"><span data-stu-id="56c9c-122">The following example shows how to use a `fixed` statement and the `&` operator:</span></span>

[!code-csharp[address of fixed](snippets/PointerOperators.cs#AddressOfFixed)]

<span data-ttu-id="56c9c-123">Nie można uzyskać adresu stałej lub wartości.</span><span class="sxs-lookup"><span data-stu-id="56c9c-123">You can't get the address of a constant or a value.</span></span>

<span data-ttu-id="56c9c-124">Aby uzyskać więcej informacji na temat zmiennych stałych i ruchomych, zobacz sekcję [Stałe i ruchome zmienne](~/_csharplang/spec/unsafe-code.md#fixed-and-moveable-variables) [specyfikacji języka C#.](~/_csharplang/spec/introduction.md)</span><span class="sxs-lookup"><span data-stu-id="56c9c-124">For more information about fixed and movable variables, see the [Fixed and moveable variables](~/_csharplang/spec/unsafe-code.md#fixed-and-moveable-variables) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="56c9c-125">Operator `&` binarny oblicza [logiczne i](boolean-logical-operators.md#logical-and-operator-) jego boolean operands lub [bitowe logiczne i](bitwise-and-shift-operators.md#logical-and-operator-) jego integralną operands.</span><span class="sxs-lookup"><span data-stu-id="56c9c-125">The binary `&` operator computes the [logical AND](boolean-logical-operators.md#logical-and-operator-) of its Boolean operands or the [bitwise logical AND](bitwise-and-shift-operators.md#logical-and-operator-) of its integral operands.</span></span>

## <a name="pointer-indirection-operator-"></a><span data-ttu-id="56c9c-126">Operator pośredni wskaźnik \*</span><span class="sxs-lookup"><span data-stu-id="56c9c-126">Pointer indirection operator \*</span></span>

<span data-ttu-id="56c9c-127">Operator pośredni wskaźnika `*` ujednawczy uzyskuje zmienną, do której wskazuje jego operand.</span><span class="sxs-lookup"><span data-stu-id="56c9c-127">The unary pointer indirection operator `*` obtains the variable to which its operand points.</span></span> <span data-ttu-id="56c9c-128">Jest również znany jako operator dereference.</span><span class="sxs-lookup"><span data-stu-id="56c9c-128">It's also known as the dereference operator.</span></span> <span data-ttu-id="56c9c-129">Operand `*` operatora musi być typu wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="56c9c-129">The operand of the `*` operator must be of a pointer type.</span></span>

[!code-csharp[pointer indirection](snippets/PointerOperators.cs#PointerIndirection)]

<span data-ttu-id="56c9c-130">Nie można `*` zastosować operatora do `void*`wyrażenia typu .</span><span class="sxs-lookup"><span data-stu-id="56c9c-130">You cannot apply the `*` operator to an expression of type `void*`.</span></span>

<span data-ttu-id="56c9c-131">Operator `*` binarny oblicza [iloczyn](arithmetic-operators.md#multiplication-operator-) jego argumentów liczbowych.</span><span class="sxs-lookup"><span data-stu-id="56c9c-131">The binary `*` operator computes the [product](arithmetic-operators.md#multiplication-operator-) of its numeric operands.</span></span>

## <a name="pointer-member-access-operator--"></a><span data-ttu-id="56c9c-132">Operator dostępu do elementu członkowskiego wskaźnika -></span><span class="sxs-lookup"><span data-stu-id="56c9c-132">Pointer member access operator -></span></span>

<span data-ttu-id="56c9c-133">Operator `->` łączy [pośredni wskaźnik](#pointer-indirection-operator-) i [dostęp do elementu członkowskiego](member-access-operators.md#member-access-expression-).</span><span class="sxs-lookup"><span data-stu-id="56c9c-133">The `->` operator combines [pointer indirection](#pointer-indirection-operator-) and [member access](member-access-operators.md#member-access-expression-).</span></span> <span data-ttu-id="56c9c-134">Oznacza to, `x` że jeśli `T*` jest `y` wskaźnikiem typu `T`i jest dostępnym elementem członkowskim typu, wyrażenie formularza</span><span class="sxs-lookup"><span data-stu-id="56c9c-134">That is, if `x` is a pointer of type `T*` and `y` is an accessible member of type `T`, an expression of the form</span></span>

```csharp
x->y
```

<span data-ttu-id="56c9c-135">jest równoważny</span><span class="sxs-lookup"><span data-stu-id="56c9c-135">is equivalent to</span></span>

```csharp
(*x).y
```

<span data-ttu-id="56c9c-136">Poniższy przykład pokazuje użycie `->` operatora:</span><span class="sxs-lookup"><span data-stu-id="56c9c-136">The following example demonstrates the usage of the `->` operator:</span></span>

[!code-csharp[pointer member access](snippets/PointerOperators.cs#MemberAccess)]

<span data-ttu-id="56c9c-137">Nie można `->` zastosować operatora do `void*`wyrażenia typu .</span><span class="sxs-lookup"><span data-stu-id="56c9c-137">You cannot apply the `->` operator to an expression of type `void*`.</span></span>

## <a name="pointer-element-access-operator-"></a><span data-ttu-id="56c9c-138">Operator dostępu do elementu wskaźnika []</span><span class="sxs-lookup"><span data-stu-id="56c9c-138">Pointer element access operator []</span></span>

<span data-ttu-id="56c9c-139">W przypadku `p` wyrażenia typu wskaźnika dostęp do `p[n]` elementu wskaźnika formularza jest oceniany jako `*(p + n)`, `int`gdzie `long` `n` musi `ulong`być typu niejawnie konwertowane na , `uint`, lub .</span><span class="sxs-lookup"><span data-stu-id="56c9c-139">For an expression `p` of a pointer type, a pointer element access of the form `p[n]` is evaluated as `*(p + n)`, where `n` must be of a type implicitly convertible to `int`, `uint`, `long`, or `ulong`.</span></span> <span data-ttu-id="56c9c-140">Aby uzyskać informacje na `+` temat zachowania operatora ze wskaźnikami, zobacz [Dodawanie lub odejmowanie wartości integralnej do lub z sekcji wskaźnika.](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer)</span><span class="sxs-lookup"><span data-stu-id="56c9c-140">For information about the behavior of the `+` operator with pointers, see the [Addition or subtraction of an integral value to or from a pointer](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) section.</span></span>

<span data-ttu-id="56c9c-141">W poniższym przykładzie pokazano, jak uzyskać `[]` dostęp do elementów tablicy za pomocą wskaźnika i operatora:</span><span class="sxs-lookup"><span data-stu-id="56c9c-141">The following example demonstrates how to access array elements with a pointer and the `[]` operator:</span></span>

[!code-csharp[pointer element access](snippets/PointerOperators.cs#ElementAccess)]

<span data-ttu-id="56c9c-142">W poprzednim przykładzie [ `stackalloc` wyrażenie](stackalloc.md) przydziela blok pamięci na stosie.</span><span class="sxs-lookup"><span data-stu-id="56c9c-142">In the preceding example, a [`stackalloc` expression](stackalloc.md) allocates a block of memory on the stack.</span></span>

> [!NOTE]
> <span data-ttu-id="56c9c-143">Operator dostępu do elementu wskaźnika nie sprawdza błędów poza granicami.</span><span class="sxs-lookup"><span data-stu-id="56c9c-143">The pointer element access operator doesn't check for out-of-bounds errors.</span></span>

<span data-ttu-id="56c9c-144">Nie można `[]` używać dostępu do elementu `void*`wskaźnika z wyrażeniem typu .</span><span class="sxs-lookup"><span data-stu-id="56c9c-144">You cannot use `[]` for pointer element access with an expression of type `void*`.</span></span>

<span data-ttu-id="56c9c-145">Można również użyć `[]` operatora dla [elementu tablicy lub dostępu do indeksatora](member-access-operators.md#indexer-operator-).</span><span class="sxs-lookup"><span data-stu-id="56c9c-145">You also can use the `[]` operator for [array element or indexer access](member-access-operators.md#indexer-operator-).</span></span>

## <a name="pointer-arithmetic-operators"></a><span data-ttu-id="56c9c-146">Operatory arytmetyczne wskaźnika</span><span class="sxs-lookup"><span data-stu-id="56c9c-146">Pointer arithmetic operators</span></span>

<span data-ttu-id="56c9c-147">Za pomocą wskaźników można wykonywać następujące operacje arytmetyczne:</span><span class="sxs-lookup"><span data-stu-id="56c9c-147">You can perform the following arithmetic operations with pointers:</span></span>

- <span data-ttu-id="56c9c-148">Dodawanie lub odejmowanie wartości integralnej do lub ze wskaźnika</span><span class="sxs-lookup"><span data-stu-id="56c9c-148">Add or subtract an integral value to or from a pointer</span></span>
- <span data-ttu-id="56c9c-149">Odejmij dwa wskaźniki</span><span class="sxs-lookup"><span data-stu-id="56c9c-149">Subtract two pointers</span></span>
- <span data-ttu-id="56c9c-150">Zwiększanie lub zmniejszanie wskaźnika</span><span class="sxs-lookup"><span data-stu-id="56c9c-150">Increment or decrement a pointer</span></span>

<span data-ttu-id="56c9c-151">Nie można wykonywać tych operacji `void*`ze wskaźnikami typu .</span><span class="sxs-lookup"><span data-stu-id="56c9c-151">You cannot perform those operations with pointers of type `void*`.</span></span>

<span data-ttu-id="56c9c-152">Aby uzyskać informacje na temat obsługiwanych operacji arytmetycznych z typami liczbowymi, zobacz [Operatory arytmetyczne](arithmetic-operators.md).</span><span class="sxs-lookup"><span data-stu-id="56c9c-152">For information about supported arithmetic operations with numeric types, see [Arithmetic operators](arithmetic-operators.md).</span></span>

### <a name="addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer"></a><span data-ttu-id="56c9c-153">Dodawanie lub odejmowanie wartości integralnej do lub ze wskaźnika</span><span class="sxs-lookup"><span data-stu-id="56c9c-153">Addition or subtraction of an integral value to or from a pointer</span></span>

<span data-ttu-id="56c9c-154">Dla wskaźnika `p` `T*` typu i `n` wyrażenia typu niejawnie `int` `uint`konwertowane na , `long`, lub `ulong`, dodawanie i odejmowanie są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="56c9c-154">For a pointer `p` of type `T*` and an expression `n` of a type implicitly convertible to `int`, `uint`, `long`, or `ulong`, addition and subtraction are defined as follows:</span></span>

- <span data-ttu-id="56c9c-155">Zarówno `p + n` `n + p` wyrażenia, jak i `T*` wyrażenia dają `n * sizeof(T)` wskaźnik typu, `p`który wynika z dodania do adresu podanego przez program .</span><span class="sxs-lookup"><span data-stu-id="56c9c-155">Both `p + n` and `n + p` expressions produce a pointer of type `T*` that results from adding `n * sizeof(T)` to the address given by `p`.</span></span>
- <span data-ttu-id="56c9c-156">Wyrażenie `p - n` tworzy wskaźnik typu, `T*` który wynika z `n * sizeof(T)` odejmowania `p`od adresu podanego przez .</span><span class="sxs-lookup"><span data-stu-id="56c9c-156">The `p - n` expression produces a pointer of type `T*` that results from subtracting `n * sizeof(T)` from the address given by `p`.</span></span>

<span data-ttu-id="56c9c-157">[ `sizeof` Operator](sizeof.md) uzyskuje rozmiar typu w bajtach.</span><span class="sxs-lookup"><span data-stu-id="56c9c-157">The [`sizeof` operator](sizeof.md) obtains the size of a type in bytes.</span></span>

<span data-ttu-id="56c9c-158">Poniższy przykład pokazuje użycie `+` operatora ze wskaźnikiem:</span><span class="sxs-lookup"><span data-stu-id="56c9c-158">The following example demonstrates the usage of the `+` operator with a pointer:</span></span>

[!code-csharp[pointer addition](snippets/PointerOperators.cs#AddNumber)]

### <a name="pointer-subtraction"></a><span data-ttu-id="56c9c-159">Odejmowanie wskaźnika</span><span class="sxs-lookup"><span data-stu-id="56c9c-159">Pointer subtraction</span></span>

<span data-ttu-id="56c9c-160">Dla dwóch `p1` wskaźników `p2` i `T*`typu `p1 - p2` wyrażenie tworzy różnicę między adresami `p2` podanymi `sizeof(T)`przez `p1` i podzielonymi przez .</span><span class="sxs-lookup"><span data-stu-id="56c9c-160">For two pointers `p1` and `p2` of type `T*`, the expression `p1 - p2` produces the difference between the addresses given by `p1` and `p2` divided by `sizeof(T)`.</span></span> <span data-ttu-id="56c9c-161">Typem wyniku jest `long`.</span><span class="sxs-lookup"><span data-stu-id="56c9c-161">The type of the result is `long`.</span></span> <span data-ttu-id="56c9c-162">Oznacza to, `p1 - p2` że `((long)(p1) - (long)(p2)) / sizeof(T)`jest obliczany jako .</span><span class="sxs-lookup"><span data-stu-id="56c9c-162">That is, `p1 - p2` is computed as `((long)(p1) - (long)(p2)) / sizeof(T)`.</span></span>

<span data-ttu-id="56c9c-163">W poniższym przykładzie pokazano odejmowanie wskaźnika:</span><span class="sxs-lookup"><span data-stu-id="56c9c-163">The following example demonstrates the pointer subtraction:</span></span>

[!code-csharp[pointer subtraction](snippets/PointerOperators.cs#SubtractPointers)]

### <a name="pointer-increment-and-decrement"></a><span data-ttu-id="56c9c-164">Zwiększanie i zmniejszanie wskaźnika</span><span class="sxs-lookup"><span data-stu-id="56c9c-164">Pointer increment and decrement</span></span>

<span data-ttu-id="56c9c-165">Operator `++` przyrostu [dodaje](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) 1 do jego operand wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="56c9c-165">The `++` increment operator [adds](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) 1 to its pointer operand.</span></span> <span data-ttu-id="56c9c-166">Operator `--` dekrementacji [odejmuje](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) 1 od jego operand wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="56c9c-166">The `--` decrement operator [subtracts](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) 1 from its pointer operand.</span></span>

<span data-ttu-id="56c9c-167">Oba operatory są obsługiwane w dwóch`p++` `p--`formach: postfix ( i ) i prefiks (`++p` i `--p`).</span><span class="sxs-lookup"><span data-stu-id="56c9c-167">Both operators are supported in two forms: postfix (`p++` and `p--`) and prefix (`++p` and `--p`).</span></span> <span data-ttu-id="56c9c-168">Wynik `p++` i `p--` jest wartością `p` *przed* operacją.</span><span class="sxs-lookup"><span data-stu-id="56c9c-168">The result of `p++` and `p--` is the value of `p` *before* the operation.</span></span> <span data-ttu-id="56c9c-169">Wynik `++p` i `--p` jest wartością `p` *po* operacji.</span><span class="sxs-lookup"><span data-stu-id="56c9c-169">The result of `++p` and `--p` is the value of `p` *after* the operation.</span></span>

<span data-ttu-id="56c9c-170">Poniższy przykład pokazuje zachowanie operatorów przyrostu postfix i prefiksu:</span><span class="sxs-lookup"><span data-stu-id="56c9c-170">The following example demonstrates the behavior of both postfix and prefix increment operators:</span></span>

[!code-csharp[pointer increment](snippets/PointerOperators.cs#Increment)]

## <a name="pointer-comparison-operators"></a><span data-ttu-id="56c9c-171">Operatory porównania wskaźników</span><span class="sxs-lookup"><span data-stu-id="56c9c-171">Pointer comparison operators</span></span>

<span data-ttu-id="56c9c-172">`==`Operatory można `!=`użyć `<` `>`, `<=`, `>=` , i operatorów, aby porównać argumenty dowolnego typu wskaźnika, w tym `void*`.</span><span class="sxs-lookup"><span data-stu-id="56c9c-172">You can use the `==`, `!=`, `<`, `>`, `<=`, and `>=` operators to compare operands of any pointer type, including `void*`.</span></span> <span data-ttu-id="56c9c-173">Operatorzy ci porównują adresy podane przez dwa argumenty tak, jakby były niepodpisanymi liczbami całkowitymi.</span><span class="sxs-lookup"><span data-stu-id="56c9c-173">Those operators compare the addresses given by the two operands as if they were unsigned integers.</span></span>

<span data-ttu-id="56c9c-174">Aby uzyskać informacje na temat zachowania tych operatorów dla operandów innych typów, zobacz [równości operatorów](equality-operators.md) i [porównania operatorów](comparison-operators.md) artykułów.</span><span class="sxs-lookup"><span data-stu-id="56c9c-174">For information about the behavior of those operators for operands of other types, see the [Equality operators](equality-operators.md) and [Comparison operators](comparison-operators.md) articles.</span></span>

## <a name="operator-precedence"></a><span data-ttu-id="56c9c-175">Pierwszeństwo operatorów</span><span class="sxs-lookup"><span data-stu-id="56c9c-175">Operator precedence</span></span>

<span data-ttu-id="56c9c-176">Następująca lista porządkuuje operatorów powiązanych wskaźnik, począwszy od najwyższego pierwszeństwa do najniższego:</span><span class="sxs-lookup"><span data-stu-id="56c9c-176">The following list orders pointer related operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="56c9c-177">Operatory przyrostu `x++` i `x--` dekrementacji `->` `[]` poprawek oraz operatorzy i operatorzy</span><span class="sxs-lookup"><span data-stu-id="56c9c-177">Postfix increment `x++` and decrement `x--` operators and the `->` and `[]` operators</span></span>
- <span data-ttu-id="56c9c-178">Operatory przyrostu `++x` i `--x` dekrementacji `&` `*` prefiksów oraz operatory i operatory</span><span class="sxs-lookup"><span data-stu-id="56c9c-178">Prefix increment `++x` and decrement `--x` operators and the `&` and `*` operators</span></span>
- <span data-ttu-id="56c9c-179">Dodatki `+` `-` i podmioty gospodarcze</span><span class="sxs-lookup"><span data-stu-id="56c9c-179">Additive `+` and `-` operators</span></span>
- <span data-ttu-id="56c9c-180">Porównanie `<` `>`, `<=`, `>=` i operatorów</span><span class="sxs-lookup"><span data-stu-id="56c9c-180">Comparison `<`, `>`, `<=`, and `>=` operators</span></span>
- <span data-ttu-id="56c9c-181">`==` Równość `!=` i operatorzy</span><span class="sxs-lookup"><span data-stu-id="56c9c-181">Equality `==` and `!=` operators</span></span>

<span data-ttu-id="56c9c-182">Użyj nawiasów, `()`aby zmienić kolejność oceny narzuconą przez pierwszeństwo operatora.</span><span class="sxs-lookup"><span data-stu-id="56c9c-182">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence.</span></span>

<span data-ttu-id="56c9c-183">Aby uzyskać pełną listę operatorów języka C# uporządkowanych według poziomu [pierwszeństwa, zobacz sekcję pierwszeństwo operatora](index.md#operator-precedence) w artykule [Operatory języka C#.](index.md)</span><span class="sxs-lookup"><span data-stu-id="56c9c-183">For the complete list of C# operators ordered by precedence level, see the [Operator precedence](index.md#operator-precedence) section of the [C# operators](index.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="56c9c-184">Przeciążenie operatora</span><span class="sxs-lookup"><span data-stu-id="56c9c-184">Operator overloadability</span></span>

<span data-ttu-id="56c9c-185">Typ zdefiniowany przez użytkownika nie może `&` `*`przeciążać operatorów powiązanych ze wskaźnikiem , `->`i `[]`.</span><span class="sxs-lookup"><span data-stu-id="56c9c-185">A user-defined type cannot overload the pointer related operators `&`, `*`, `->`, and `[]`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="56c9c-186">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="56c9c-186">C# language specification</span></span>

<span data-ttu-id="56c9c-187">Aby uzyskać więcej informacji, zobacz następujące sekcje [specyfikacji języka języka C#:](~/_csharplang/spec/introduction.md)</span><span class="sxs-lookup"><span data-stu-id="56c9c-187">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="56c9c-188">Stałe i ruchome zmienne</span><span class="sxs-lookup"><span data-stu-id="56c9c-188">Fixed and moveable variables</span></span>](~/_csharplang/spec/unsafe-code.md#fixed-and-moveable-variables)
- [<span data-ttu-id="56c9c-189">Adres operatora</span><span class="sxs-lookup"><span data-stu-id="56c9c-189">The address-of operator</span></span>](~/_csharplang/spec/unsafe-code.md#the-address-of-operator)
- [<span data-ttu-id="56c9c-190">Pośredni wskaźnik</span><span class="sxs-lookup"><span data-stu-id="56c9c-190">Pointer indirection</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-indirection)
- [<span data-ttu-id="56c9c-191">Dostęp do elementu członkowskiego wskaźnika</span><span class="sxs-lookup"><span data-stu-id="56c9c-191">Pointer member access</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-member-access)
- [<span data-ttu-id="56c9c-192">Dostęp do elementu wskaźnika</span><span class="sxs-lookup"><span data-stu-id="56c9c-192">Pointer element access</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-element-access)
- [<span data-ttu-id="56c9c-193">Arytmetyczny wskaźnik</span><span class="sxs-lookup"><span data-stu-id="56c9c-193">Pointer arithmetic</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-arithmetic)
- [<span data-ttu-id="56c9c-194">Zwiększanie i zmniejszanie wskaźnika</span><span class="sxs-lookup"><span data-stu-id="56c9c-194">Pointer increment and decrement</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-increment-and-decrement)
- [<span data-ttu-id="56c9c-195">Porównanie wskaźników</span><span class="sxs-lookup"><span data-stu-id="56c9c-195">Pointer comparison</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-comparison)

## <a name="see-also"></a><span data-ttu-id="56c9c-196">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="56c9c-196">See also</span></span>

- [<span data-ttu-id="56c9c-197">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="56c9c-197">C# reference</span></span>](../index.md)
- [<span data-ttu-id="56c9c-198">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="56c9c-198">C# operators</span></span>](index.md)
- [<span data-ttu-id="56c9c-199">Typy wskaźnika</span><span class="sxs-lookup"><span data-stu-id="56c9c-199">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="56c9c-200">niebezpieczne słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="56c9c-200">unsafe keyword</span></span>](../keywords/unsafe.md)
- [<span data-ttu-id="56c9c-201">stałe słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="56c9c-201">fixed keyword</span></span>](../keywords/fixed-statement.md)
- [<span data-ttu-id="56c9c-202">stackalloc</span><span class="sxs-lookup"><span data-stu-id="56c9c-202">stackalloc</span></span>](stackalloc.md)
- [<span data-ttu-id="56c9c-203">sizeof, operator</span><span class="sxs-lookup"><span data-stu-id="56c9c-203">sizeof operator</span></span>](sizeof.md)
