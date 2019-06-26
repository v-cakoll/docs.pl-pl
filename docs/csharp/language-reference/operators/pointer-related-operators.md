---
title: Wskaźnik związane z operatorów - C# odwołania
description: Dowiedz się więcej o C# operatorów, które można użyć podczas pracy z wskaźników.
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
ms.openlocfilehash: 03d6ed19ef01be7712ff2fdde0c1be2a6673e64f
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2019
ms.locfileid: "67401441"
---
# <a name="pointer-related-operators-c-reference"></a><span data-ttu-id="640d2-103">Wskaźnik związane z operatorów (C# odwołania)</span><span class="sxs-lookup"><span data-stu-id="640d2-103">Pointer related operators (C# reference)</span></span>

<span data-ttu-id="640d2-104">Pracować ze wskaźnikami, można używać następujących operatorów:</span><span class="sxs-lookup"><span data-stu-id="640d2-104">You can use the following operators to work with pointers:</span></span>

- <span data-ttu-id="640d2-105">Jednoargumentowy [ `&` (adresu z)](#address-of-operator-) operator: można pobrać adresu zmiennej</span><span class="sxs-lookup"><span data-stu-id="640d2-105">Unary [`&` (address-of)](#address-of-operator-) operator: to get the address of a variable</span></span>
- <span data-ttu-id="640d2-106">Jednoargumentowy [ `*` (operację wskaźnika pośredniego)](#pointer-indirection-operator-) operator: uzyskanie zmiennej wskazywana przez wskaźnik</span><span class="sxs-lookup"><span data-stu-id="640d2-106">Unary [`*` (pointer indirection)](#pointer-indirection-operator-) operator: to obtain the variable pointed by a pointer</span></span>
- <span data-ttu-id="640d2-107">[ `->` (Dostęp do elementu członkowskiego)](#pointer-member-access-operator--) i [ `[]` (dostęp do elementu)](#pointer-element-access-operator-) operatorów</span><span class="sxs-lookup"><span data-stu-id="640d2-107">The [`->` (member access)](#pointer-member-access-operator--) and [`[]` (element access)](#pointer-element-access-operator-) operators</span></span>
- <span data-ttu-id="640d2-108">Operatory arytmetyczne [ `+`, `-`, `++`, i `--`](#pointer-arithmetic-operators)</span><span class="sxs-lookup"><span data-stu-id="640d2-108">Arithmetic operators [`+`, `-`, `++`, and `--`](#pointer-arithmetic-operators)</span></span>
- <span data-ttu-id="640d2-109">Operatory porównania [ `==`, `!=`, `<`, `>`, `<=`, i `>=`](#pointer-comparison-operators)</span><span class="sxs-lookup"><span data-stu-id="640d2-109">Comparison operators [`==`, `!=`, `<`, `>`, `<=`, and `>=`](#pointer-comparison-operators)</span></span>

<span data-ttu-id="640d2-110">Aby uzyskać informacje dotyczące typów wskaźnika, zobacz [typy wskaźników](../../programming-guide/unsafe-code-pointers/pointer-types.md).</span><span class="sxs-lookup"><span data-stu-id="640d2-110">For information about pointer types, see [Pointer types](../../programming-guide/unsafe-code-pointers/pointer-types.md).</span></span>

> [!NOTE]
> <span data-ttu-id="640d2-111">Wszelkie działania, za pomocą wskaźników wymaga [niebezpieczne](../keywords/unsafe.md) kontekstu.</span><span class="sxs-lookup"><span data-stu-id="640d2-111">Any operation with pointers requires an [unsafe](../keywords/unsafe.md) context.</span></span> <span data-ttu-id="640d2-112">Kod, który zawiera bloki niebezpieczne musi być skompilowana przy użyciu [ `-unsafe` ](../compiler-options/unsafe-compiler-option.md) — opcja kompilatora.</span><span class="sxs-lookup"><span data-stu-id="640d2-112">The code that contains unsafe blocks must be compiled with the [`-unsafe`](../compiler-options/unsafe-compiler-option.md) compiler option.</span></span>

## <a name="address-of-operator-"></a> <span data-ttu-id="640d2-113">Operator Address-of &amp;</span><span class="sxs-lookup"><span data-stu-id="640d2-113">Address-of operator &amp;</span></span>

<span data-ttu-id="640d2-114">Jednoargumentowy `&` operator zwraca adres jego operandu:</span><span class="sxs-lookup"><span data-stu-id="640d2-114">The unary `&` operator returns the address of its operand:</span></span>

[!code-csharp[address of local](~/samples/csharp/language-reference/operators/PointerOperators.cs#AddressOf)]

<span data-ttu-id="640d2-115">Argument operacji `&` operator musi być zmienna ustalona.</span><span class="sxs-lookup"><span data-stu-id="640d2-115">The operand of the `&` operator must be a fixed variable.</span></span> <span data-ttu-id="640d2-116">*Naprawiono* zmienne są zmienne, które znajdują się w lokalizacji przechowywania, które nie ma wpływu na działanie [modułu zbierającego elementy bezużyteczne](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="640d2-116">*Fixed* variables are variables that reside in storage locations that are unaffected by operation of the [garbage collector](../../../standard/garbage-collection/index.md).</span></span> <span data-ttu-id="640d2-117">W poprzednim przykładzie, zmienna lokalna `number` jest zmienna ustalona, ponieważ znajduje się on na stosie.</span><span class="sxs-lookup"><span data-stu-id="640d2-117">In the preceding example, the local variable `number` is a fixed variable, because it resides on the stack.</span></span> <span data-ttu-id="640d2-118">Zmienne, które znajdują się w lokalizacji przechowywania, które mogą mieć wpływ moduł odśmiecania pamięci (na przykład przenieść) są nazywane *ruchome* zmiennych.</span><span class="sxs-lookup"><span data-stu-id="640d2-118">Variables that reside in storage locations that can be affected by the garbage collector (for example, relocated) are called *movable* variables.</span></span> <span data-ttu-id="640d2-119">Pola obiektu i elementy tablicy są przykłady ruchome zmiennych.</span><span class="sxs-lookup"><span data-stu-id="640d2-119">Object fields and array elements are examples of movable variables.</span></span> <span data-ttu-id="640d2-120">Można uzyskać adresu zmiennej ruchome, jeśli "naprawić" lub "przypinając" je za pomocą [stałej](../keywords/fixed-statement.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="640d2-120">You can get the address of a movable variable if you "fix", or "pin", it with the [fixed](../keywords/fixed-statement.md) statement.</span></span> <span data-ttu-id="640d2-121">Uzyskanej adres jest prawidłowy tylko na czas trwania `fixed` blok instrukcji.</span><span class="sxs-lookup"><span data-stu-id="640d2-121">The obtained address is valid only for the duration of the `fixed` statement block.</span></span> <span data-ttu-id="640d2-122">Poniższy przykład pokazuje, jak używać `fixed` instrukcji i `&` operator:</span><span class="sxs-lookup"><span data-stu-id="640d2-122">The following example shows how to use the `fixed` statement and the `&` operator:</span></span>

[!code-csharp[address of fixed](~/samples/csharp/language-reference/operators/PointerOperators.cs#AddressOfFixed)]

<span data-ttu-id="640d2-123">Nie można pobrać adresu stała lub wartość.</span><span class="sxs-lookup"><span data-stu-id="640d2-123">You can't get the address of a constant or a value.</span></span>

<span data-ttu-id="640d2-124">Aby uzyskać więcej informacji na temat zmiennych stałych i okazjonalnych zobacz [stałe i zmienne ruchome](~/_csharplang/spec/unsafe-code.md#fixed-and-moveable-variables) części [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="640d2-124">For more information about fixed and movable variables, see the [Fixed and moveable variables](~/_csharplang/spec/unsafe-code.md#fixed-and-moveable-variables) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="640d2-125">Plik binarny `&` oblicza operator [operator logiczny oraz](boolean-logical-operators.md#logical-and-operator-) z argumentów logicznych lub [iloczynu bitowego AND logiczne](bitwise-and-shift-operators.md#logical-and-operator-) jej całkowitego operandu.</span><span class="sxs-lookup"><span data-stu-id="640d2-125">The binary `&` operator computes the [logical AND](boolean-logical-operators.md#logical-and-operator-) of its Boolean operands or the [bitwise logical AND](bitwise-and-shift-operators.md#logical-and-operator-) of its integral operands.</span></span>

## <a name="pointer-indirection-operator-"></a><span data-ttu-id="640d2-126">Operatora pośredniego wskaźnika \*</span><span class="sxs-lookup"><span data-stu-id="640d2-126">Pointer indirection operator \*</span></span>

<span data-ttu-id="640d2-127">Jednoargumentowy operator pośredni wskaźnik `*` uzyskuje zmiennej, do którego wskazuje operand.</span><span class="sxs-lookup"><span data-stu-id="640d2-127">The unary pointer indirection operator `*` obtains the variable to which its operand points.</span></span> <span data-ttu-id="640d2-128">Jest również nazywany operator wyłuskania.</span><span class="sxs-lookup"><span data-stu-id="640d2-128">It's also known as the dereference operator.</span></span> <span data-ttu-id="640d2-129">Argument operacji `*` operatora musi być typem wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="640d2-129">The operand of the `*` operator must be of a pointer type.</span></span>

[!code-csharp[pointer indirection](~/samples/csharp/language-reference/operators/PointerOperators.cs#PointerIndirection)]

<span data-ttu-id="640d2-130">Nie można zastosować `*` operatora wyrażenia typu `void*`.</span><span class="sxs-lookup"><span data-stu-id="640d2-130">You cannot apply the `*` operator to an expression of type `void*`.</span></span>

<span data-ttu-id="640d2-131">Plik binarny `*` oblicza operator [produktu](arithmetic-operators.md#multiplication-operator-) z liczbową argumentów.</span><span class="sxs-lookup"><span data-stu-id="640d2-131">The binary `*` operator computes the [product](arithmetic-operators.md#multiplication-operator-) of its numeric operands.</span></span>

## <a name="pointer-member-access-operator--"></a><span data-ttu-id="640d2-132">Operator dostępu do elementu członkowskiego wskaźnik -></span><span class="sxs-lookup"><span data-stu-id="640d2-132">Pointer member access operator -></span></span>

<span data-ttu-id="640d2-133">`->` Łączy operator [operację wskaźnika pośredniego](#pointer-indirection-operator-) i [dostęp do elementu członkowskiego](member-access-operators.md#member-access-operator-).</span><span class="sxs-lookup"><span data-stu-id="640d2-133">The `->` operator combines [pointer indirection](#pointer-indirection-operator-) and [member access](member-access-operators.md#member-access-operator-).</span></span> <span data-ttu-id="640d2-134">Oznacza to jeśli `x` jest wskaźnikiem typu `T*` i `y` jest dostępny członek `T`, wyrażenie formularza</span><span class="sxs-lookup"><span data-stu-id="640d2-134">That is, if `x` is a pointer of type `T*` and `y` is an accessible member of `T`, an expression of the form</span></span>

```csharp
x->y
```

<span data-ttu-id="640d2-135">odpowiada wyrażeniu</span><span class="sxs-lookup"><span data-stu-id="640d2-135">is equivalent to</span></span>

```csharp
(*x).y
```

<span data-ttu-id="640d2-136">W poniższym przykładzie pokazano użycie `->` operator:</span><span class="sxs-lookup"><span data-stu-id="640d2-136">The following example demonstrates the usage of the `->` operator:</span></span>

[!code-csharp[pointer member access](~/samples/csharp/language-reference/operators/PointerOperators.cs#MemberAccess)]

<span data-ttu-id="640d2-137">Nie można zastosować `->` operatora wyrażenia typu `void*`.</span><span class="sxs-lookup"><span data-stu-id="640d2-137">You cannot apply the `->` operator to an expression of type `void*`.</span></span>

## <a name="pointer-element-access-operator-"></a><span data-ttu-id="640d2-138">Wskaźnik elementu dostępu operator w]</span><span class="sxs-lookup"><span data-stu-id="640d2-138">Pointer element access operator []</span></span>

<span data-ttu-id="640d2-139">Wyrażenie `p` typu wskaźnika, dostęp do elementu wskaźnika w postaci `p[n]` jest oceniane jako `*(p + n)`, gdzie `n` musi być typu niejawnej konwersji `int`, `uint`, `long`, lub `ulong`.</span><span class="sxs-lookup"><span data-stu-id="640d2-139">For an expression `p` of a pointer type, a pointer element access of the form `p[n]` is evaluated as `*(p + n)`, where `n` must be of a type implicitly convertible to `int`, `uint`, `long`, or `ulong`.</span></span> <span data-ttu-id="640d2-140">Aby uzyskać informacje o zachowanie `+` operator za pomocą wskaźników, zobacz [dodawania lub odejmowania liczb całkowitych do lub ze wskaźnika](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) sekcji.</span><span class="sxs-lookup"><span data-stu-id="640d2-140">For information about the behavior of the `+` operator with pointers, see the [Addition or subtraction of an integral value to or from a pointer](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) section.</span></span>

<span data-ttu-id="640d2-141">Poniższy przykład pokazuje, jak uzyskać dostęp do elementów tablicy ze wskaźnikiem i `[]` operator:</span><span class="sxs-lookup"><span data-stu-id="640d2-141">The following example demonstrates how to access array elements with a pointer and the `[]` operator:</span></span>

[!code-csharp[pointer element access](~/samples/csharp/language-reference/operators/PointerOperators.cs#ElementAccess)]

<span data-ttu-id="640d2-142">W przykładzie użyto [ `stackalloc` operator](stackalloc.md) przydzielić blok pamięci na stosie.</span><span class="sxs-lookup"><span data-stu-id="640d2-142">The example uses the [`stackalloc` operator](stackalloc.md) to allocate a block of memory on the stack.</span></span>

> [!NOTE]
> <span data-ttu-id="640d2-143">Operator dostępu do elementu wskaźnik nie sprawdzaj liczbach błędy.</span><span class="sxs-lookup"><span data-stu-id="640d2-143">The pointer element access operator doesn't check for out-of-bounds errors.</span></span>

<span data-ttu-id="640d2-144">Nie można użyć `[]` wskaźnika elementu dostępu za pomocą wyrażenia typu `void*`.</span><span class="sxs-lookup"><span data-stu-id="640d2-144">You cannot use `[]` for pointer element access with an expression of type `void*`.</span></span>

<span data-ttu-id="640d2-145">Możesz również użyć `[]` operator [tablicy dostępu do elementu lub indeksator](member-access-operators.md#indexer-operator-).</span><span class="sxs-lookup"><span data-stu-id="640d2-145">You also can use the `[]` operator for [array element or indexer access](member-access-operators.md#indexer-operator-).</span></span>

## <a name="pointer-arithmetic-operators"></a><span data-ttu-id="640d2-146">Operatory arytmetyczne wskaźnika</span><span class="sxs-lookup"><span data-stu-id="640d2-146">Pointer arithmetic operators</span></span>

<span data-ttu-id="640d2-147">Można wykonywać następujące operacje arytmetyczne ze wskaźnikami:</span><span class="sxs-lookup"><span data-stu-id="640d2-147">You can perform the following arithmetic operations with pointers:</span></span>

- <span data-ttu-id="640d2-148">Dodaj lub Odejmij wartość całkowitą na lub ze wskaźnika</span><span class="sxs-lookup"><span data-stu-id="640d2-148">Add or subtract an integral value to or from a pointer</span></span>
- <span data-ttu-id="640d2-149">Odejmowania dwóch wskaźników</span><span class="sxs-lookup"><span data-stu-id="640d2-149">Subtract two pointers</span></span>
- <span data-ttu-id="640d2-150">Inkrementacyjna lub dekrementacyjna wskaźnika</span><span class="sxs-lookup"><span data-stu-id="640d2-150">Increment or decrement a pointer</span></span>

<span data-ttu-id="640d2-151">Nie można wykonać te operacje za pomocą wskaźników typu `void*`.</span><span class="sxs-lookup"><span data-stu-id="640d2-151">You cannot perform those operations with pointers of type `void*`.</span></span>

<span data-ttu-id="640d2-152">Aby uzyskać informacji na temat obsługiwanych operacji arytmetycznych na wartościach typów liczbowych, zobacz [operatorów arytmetycznych](arithmetic-operators.md).</span><span class="sxs-lookup"><span data-stu-id="640d2-152">For information about supported arithmetic operations with numeric types, see [Arithmetic operators](arithmetic-operators.md).</span></span>

### <a name="addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer"></a><span data-ttu-id="640d2-153">Dodawania lub odejmowania liczb całkowitych do lub ze wskaźnika</span><span class="sxs-lookup"><span data-stu-id="640d2-153">Addition or subtraction of an integral value to or from a pointer</span></span>

<span data-ttu-id="640d2-154">Dla wskaźnika `p` typu `T*` i wyrażenie `n` niejawnej konwersji typu `int`, `uint`, `long`, lub `ulong`, dodawania i odejmowania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="640d2-154">For a pointer `p` of type `T*` and an expression `n` of a type implicitly convertible to `int`, `uint`, `long`, or `ulong`, addition and subtraction are defined as follows:</span></span>

- <span data-ttu-id="640d2-155">Zarówno `p + n` i `n + p` wyrażenia dają wskaźnika typu `T*` , wynikiem dodawania `n * sizeof(T)` adres podany przez `p`.</span><span class="sxs-lookup"><span data-stu-id="640d2-155">Both `p + n` and `n + p` expressions produce a pointer of type `T*` that results from adding `n * sizeof(T)` to the address given by `p`.</span></span>
- <span data-ttu-id="640d2-156">`p - n` Wyrażenie powoduje wskaźnika typu `T*` , wynikiem odejmowania `n * sizeof(T)` z adresem podanym przez `p`.</span><span class="sxs-lookup"><span data-stu-id="640d2-156">The `p - n` expression produces a pointer of type `T*` that results from subtracting `n * sizeof(T)` from the address given by `p`.</span></span>

<span data-ttu-id="640d2-157">[ `sizeof` Operator](../keywords/sizeof.md) uzyskuje rozmiar typu w bajtach.</span><span class="sxs-lookup"><span data-stu-id="640d2-157">The [`sizeof` operator](../keywords/sizeof.md) obtains the size of a type in bytes.</span></span>

<span data-ttu-id="640d2-158">W poniższym przykładzie pokazano użycie `+` operator za pomocą wskaźnika:</span><span class="sxs-lookup"><span data-stu-id="640d2-158">The following example demonstrates the usage of the `+` operator with a pointer:</span></span>

[!code-csharp[pointer addition](~/samples/csharp/language-reference/operators/PointerOperators.cs#AddNumber)]

### <a name="pointer-subtraction"></a><span data-ttu-id="640d2-159">Odejmowanie wskaźnika</span><span class="sxs-lookup"><span data-stu-id="640d2-159">Pointer subtraction</span></span>

<span data-ttu-id="640d2-160">Dla dwóch wskaźników `p1` i `p2` typu `T*`, wyrażenie `p1 - p2` tworzy różnica między adresy podane przez `p1` i `p2` podzielona przez `sizeof(T)`.</span><span class="sxs-lookup"><span data-stu-id="640d2-160">For two pointers `p1` and `p2` of type `T*`, the expression `p1 - p2` produces the difference between the addresses given by `p1` and `p2` divided by `sizeof(T)`.</span></span> <span data-ttu-id="640d2-161">Typ wyniku jest `long`.</span><span class="sxs-lookup"><span data-stu-id="640d2-161">The type of the result is `long`.</span></span> <span data-ttu-id="640d2-162">Oznacza to, że `p1 - p2` jest obliczana jako `((long)(p1) - (long)(p2)) / sizeof(T)`.</span><span class="sxs-lookup"><span data-stu-id="640d2-162">That is, `p1 - p2` is computed as `((long)(p1) - (long)(p2)) / sizeof(T)`.</span></span>

<span data-ttu-id="640d2-163">W poniższym przykładzie pokazano odejmowanie wskaźnika:</span><span class="sxs-lookup"><span data-stu-id="640d2-163">The following example demonstrates the pointer subtraction:</span></span>

[!code-csharp[pointer subtraction](~/samples/csharp/language-reference/operators/PointerOperators.cs#SubtractPointers)]

### <a name="pointer-increment-and-decrement"></a><span data-ttu-id="640d2-164">Wskaźnik inkrementacja i dekrementacja</span><span class="sxs-lookup"><span data-stu-id="640d2-164">Pointer increment and decrement</span></span>

<span data-ttu-id="640d2-165">`++` Operator inkrementacji [dodaje](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) 1 do swojego operandu wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="640d2-165">The `++` increment operator [adds](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) 1 to its pointer operand.</span></span> <span data-ttu-id="640d2-166">`--` Operatora dekrementacyjnego [odejmuje](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) 1 z argumentem wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="640d2-166">The `--` decrement operator [subtracts](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) 1 from its pointer operand.</span></span>

<span data-ttu-id="640d2-167">Oba operatory są obsługiwane w dwóch formach: przyrostków (`p++` i `p--`) i prefiksu (`++p` i `--p`).</span><span class="sxs-lookup"><span data-stu-id="640d2-167">Both operators are supported in two forms: postfix (`p++` and `p--`) and prefix (`++p` and `--p`).</span></span> <span data-ttu-id="640d2-168">Wynik `p++` i `p--` jest wartością `p` *przed* wykonać operację.</span><span class="sxs-lookup"><span data-stu-id="640d2-168">The result of `p++` and `p--` is the value of `p` *before* the operation.</span></span> <span data-ttu-id="640d2-169">Wynik `++p` i `--p` jest wartością `p` *po* wykonać operację.</span><span class="sxs-lookup"><span data-stu-id="640d2-169">The result of `++p` and `--p` is the value of `p` *after* the operation.</span></span>

<span data-ttu-id="640d2-170">Poniższy przykład pokazuje zachowanie operatory inkrementacji przyrostka i prefiksu:</span><span class="sxs-lookup"><span data-stu-id="640d2-170">The following example demonstrates the behavior of both postfix and prefix increment operators:</span></span>

[!code-csharp[pointer increment](~/samples/csharp/language-reference/operators/PointerOperators.cs#Increment)]

## <a name="pointer-comparison-operators"></a><span data-ttu-id="640d2-171">Operatory porównania wskaźnika</span><span class="sxs-lookup"><span data-stu-id="640d2-171">Pointer comparison operators</span></span>

<span data-ttu-id="640d2-172">Możesz użyć `==`, `!=`, `<`, `>`, `<=`, i `>=` operatory, aby porównać argumentów operacji typu wskaźnika, w tym `void*`.</span><span class="sxs-lookup"><span data-stu-id="640d2-172">You can use the `==`, `!=`, `<`, `>`, `<=`, and `>=` operators to compare operands of any pointer type, including `void*`.</span></span> <span data-ttu-id="640d2-173">Te operatory porównują adresy podane przez dwa operandy tak, jakby były one liczb całkowitych bez znaku.</span><span class="sxs-lookup"><span data-stu-id="640d2-173">Those operators compare the addresses given by the two operands as if they were unsigned integers.</span></span>

<span data-ttu-id="640d2-174">Aby uzyskać informacje o zachowaniu tych operatorów w przypadku argumentów operacji innych typów, zobacz [Operatory równości](equality-operators.md) i [operatory porównania](comparison-operators.md) artykułów.</span><span class="sxs-lookup"><span data-stu-id="640d2-174">For information about the behavior of those operators for operands of other types, see the [Equality operators](equality-operators.md) and [Comparison operators](comparison-operators.md) articles.</span></span>

## <a name="operator-precedence"></a><span data-ttu-id="640d2-175">Pierwszeństwo operatorów</span><span class="sxs-lookup"><span data-stu-id="640d2-175">Operator precedence</span></span>

<span data-ttu-id="640d2-176">Następujący wskaźnik zamówienia listy powiązane operatory rozpoczyna się od najwyższy priorytet najniższy:</span><span class="sxs-lookup"><span data-stu-id="640d2-176">The following list orders pointer related operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="640d2-177">Inkrementacja przyrostkowa `x++` i dekrementacyjne `x--` operatorów i `->` i `[]` operatorów</span><span class="sxs-lookup"><span data-stu-id="640d2-177">Postfix increment `x++` and decrement `x--` operators and the `->` and `[]` operators</span></span>
- <span data-ttu-id="640d2-178">Inkrementacja przedrostkowa `++x` i dekrementacyjne `--x` operatorów i `&` i `*` operatorów</span><span class="sxs-lookup"><span data-stu-id="640d2-178">Prefix increment `++x` and decrement `--x` operators and the `&` and `*` operators</span></span>
- <span data-ttu-id="640d2-179">Dodatek `+` i `-` operatorów</span><span class="sxs-lookup"><span data-stu-id="640d2-179">Additive `+` and `-` operators</span></span>
- <span data-ttu-id="640d2-180">Porównanie `<`, `>`, `<=`, i `>=` operatorów</span><span class="sxs-lookup"><span data-stu-id="640d2-180">Comparison `<`, `>`, `<=`, and `>=` operators</span></span>
- <span data-ttu-id="640d2-181">Równość `==` i `!=` operatorów</span><span class="sxs-lookup"><span data-stu-id="640d2-181">Equality `==` and `!=` operators</span></span>

<span data-ttu-id="640d2-182">Użyj nawiasów, `()`, aby zmienić kolejność oceny nałożonych przez pierwszeństwo operatorów.</span><span class="sxs-lookup"><span data-stu-id="640d2-182">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence.</span></span>

<span data-ttu-id="640d2-183">Aby uzyskać pełną listę C# operatory uporządkowane według poziomu priorytetu, zobacz [ C# operatory](index.md).</span><span class="sxs-lookup"><span data-stu-id="640d2-183">For the complete list of C# operators ordered by precedence level, see [C# operators](index.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="640d2-184">Overloadability — operator</span><span class="sxs-lookup"><span data-stu-id="640d2-184">Operator overloadability</span></span>

<span data-ttu-id="640d2-185">Typ zdefiniowany przez użytkownika nie mogą przeciążać wskaźnik związane z operatorów `&`, `*`, `->`, i `[]`.</span><span class="sxs-lookup"><span data-stu-id="640d2-185">A user-defined type cannot overload the pointer related operators `&`, `*`, `->`, and `[]`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="640d2-186">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="640d2-186">C# language specification</span></span>

<span data-ttu-id="640d2-187">Aby uzyskać więcej informacji, zobacz następujące sekcje [ C# specyfikacji języka](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="640d2-187">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="640d2-188">Stałe i ruchome zmiennych</span><span class="sxs-lookup"><span data-stu-id="640d2-188">Fixed and moveable variables</span></span>](~/_csharplang/spec/unsafe-code.md#fixed-and-moveable-variables)
- [<span data-ttu-id="640d2-189">Operator address-of</span><span class="sxs-lookup"><span data-stu-id="640d2-189">The address-of operator</span></span>](~/_csharplang/spec/unsafe-code.md#the-address-of-operator)
- [<span data-ttu-id="640d2-190">Operatora pośredniego wskaźnika</span><span class="sxs-lookup"><span data-stu-id="640d2-190">Pointer indirection</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-indirection)
- [<span data-ttu-id="640d2-191">Dostęp do elementu członkowskiego wskaźnika</span><span class="sxs-lookup"><span data-stu-id="640d2-191">Pointer member access</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-member-access)
- [<span data-ttu-id="640d2-192">Dostęp do elementu wskaźnika</span><span class="sxs-lookup"><span data-stu-id="640d2-192">Pointer element access</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-element-access)
- [<span data-ttu-id="640d2-193">Arytmetyczny wskaźnik</span><span class="sxs-lookup"><span data-stu-id="640d2-193">Pointer arithmetic</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-arithmetic)
- [<span data-ttu-id="640d2-194">Wskaźnik inkrementacja i dekrementacja</span><span class="sxs-lookup"><span data-stu-id="640d2-194">Pointer increment and decrement</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-increment-and-decrement)
- [<span data-ttu-id="640d2-195">Porównanie wskaźników</span><span class="sxs-lookup"><span data-stu-id="640d2-195">Pointer comparison</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-comparison)

## <a name="see-also"></a><span data-ttu-id="640d2-196">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="640d2-196">See also</span></span>

- [<span data-ttu-id="640d2-197">C#Odwołanie</span><span class="sxs-lookup"><span data-stu-id="640d2-197">C# reference</span></span>](../index.md)
- [<span data-ttu-id="640d2-198">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="640d2-198">C# operators</span></span>](index.md)
- [<span data-ttu-id="640d2-199">Typy wskaźników</span><span class="sxs-lookup"><span data-stu-id="640d2-199">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="640d2-200">słowa kluczowego unsafe</span><span class="sxs-lookup"><span data-stu-id="640d2-200">unsafe keyword</span></span>](../keywords/unsafe.md)
- [<span data-ttu-id="640d2-201">Fixed — słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="640d2-201">fixed keyword</span></span>](../keywords/fixed-statement.md)
- [<span data-ttu-id="640d2-202">stackalloc — operator</span><span class="sxs-lookup"><span data-stu-id="640d2-202">stackalloc operator</span></span>](stackalloc.md)
- [<span data-ttu-id="640d2-203">sizeof — operator</span><span class="sxs-lookup"><span data-stu-id="640d2-203">sizeof operator</span></span>](../keywords/sizeof.md)
