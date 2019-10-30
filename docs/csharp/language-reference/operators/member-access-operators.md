---
title: Operatory dostępu do elementów C# członkowskich — odwołanie
description: Dowiedz C# się więcej na temat operatorów, których można użyć w celu uzyskania dostępu do elementów członkowskich typu.
ms.date: 09/18/2019
author: pkulikov
f1_keywords:
- ._CSharpKeyword
- '[]_CSharpKeyword'
- ()_CSharpKeyword
- ^_CSharpKeyword
- .._CSharpKeyword
helpviewer_keywords:
- member access operators [C#]
- member access operator [C#]
- dot operator [C#]
- . operator [C#]
- subscript operator [C#]
- square brackets [] operator [C#]
- indexer operator [C#]
- '[] operator [C#]'
- null-conditional operators [C#]
- Elvis operator [C#]
- ?. operator [C#]
- ?[] operator [C#]
- invocation operator [C#]
- method call [C#]
- method invocation [C#]
- delegate invocation [C#]
- () operator [C#]
- ^ operator [C#]
- index from end operator [C#]
- hat operator [C#]
- .. operator [C#]
- range operator [C#]
ms.openlocfilehash: ba2a8cd4995b9baab2071d3fb3c7980e45565692
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73038998"
---
# <a name="member-access-operators-c-reference"></a><span data-ttu-id="26329-103">Operatory dostępu do elementówC# członkowskich (odwołanie)</span><span class="sxs-lookup"><span data-stu-id="26329-103">Member access operators (C# reference)</span></span>

<span data-ttu-id="26329-104">Podczas uzyskiwania dostępu do elementu członkowskiego typu można użyć następujących operatorów:</span><span class="sxs-lookup"><span data-stu-id="26329-104">You can use the following operators when you access a type member:</span></span>

- <span data-ttu-id="26329-105">[`.` (dostęp do elementu członkowskiego)](#member-access-operator-): Aby uzyskać dostęp do elementu członkowskiego przestrzeni nazw lub typu</span><span class="sxs-lookup"><span data-stu-id="26329-105">[`.` (member access)](#member-access-operator-): to access a member of a namespace or a type</span></span>
- <span data-ttu-id="26329-106">[`[]` (dostęp do elementu tablicy lub indeksatora)](#indexer-operator-): Aby uzyskać dostęp do elementu tablicy lub indeksatora typu</span><span class="sxs-lookup"><span data-stu-id="26329-106">[`[]` (array element or indexer access)](#indexer-operator-): to access an array element or a type indexer</span></span>
- <span data-ttu-id="26329-107">[`?.` i `?[]` (operatory warunkowe o wartości null)](#null-conditional-operators--and-): Aby wykonać operację dostępu do elementu członkowskiego lub tylko wtedy, gdy operand ma wartość różną od null</span><span class="sxs-lookup"><span data-stu-id="26329-107">[`?.` and `?[]` (null-conditional operators)](#null-conditional-operators--and-): to perform a member or element access operation only if an operand is non-null</span></span>
- <span data-ttu-id="26329-108">[`()` (wywołanie)](#invocation-operator-): aby wywołać metodę dostępu lub wywołać delegata</span><span class="sxs-lookup"><span data-stu-id="26329-108">[`()` (invocation)](#invocation-operator-): to call an accessed method or invoke a delegate</span></span>
- <span data-ttu-id="26329-109">[`^` (indeks od końca)](#index-from-end-operator-): wskazuje, że pozycja elementu jest z końca sekwencji</span><span class="sxs-lookup"><span data-stu-id="26329-109">[`^` (index from end)](#index-from-end-operator-): to indicate that the element position is from the end of a sequence</span></span>
- <span data-ttu-id="26329-110">[`..` (zakres)](#range-operator-): aby określić zakres indeksów, których można użyć w celu uzyskania zakresu elementów sekwencji</span><span class="sxs-lookup"><span data-stu-id="26329-110">[`..` (range)](#range-operator-): to specify a range of indices that you can use to obtain a range of sequence elements</span></span>

## <a name="member-access-operator-"></a><span data-ttu-id="26329-111">Operator dostępu do elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="26329-111">Member access operator .</span></span>

<span data-ttu-id="26329-112">Token `.` służy do uzyskiwania dostępu do elementu członkowskiego przestrzeni nazw lub typu, jak pokazano w poniższych przykładach:</span><span class="sxs-lookup"><span data-stu-id="26329-112">You use the `.` token to access a member of a namespace or a type, as the following examples demonstrate:</span></span>

- <span data-ttu-id="26329-113">Użyj `.`, aby uzyskać dostęp do zagnieżdżonej przestrzeni nazw w przestrzeni nazw, jak pokazano w poniższym przykładzie [dyrektywy`using`](../keywords/using-directive.md) :</span><span class="sxs-lookup"><span data-stu-id="26329-113">Use `.` to access a nested namespace within a namespace, as the following example of a [`using` directive](../keywords/using-directive.md) shows:</span></span>

  [!code-csharp[nested namespaces](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#NestedNamespace)]

- <span data-ttu-id="26329-114">Użyj `.`, aby utworzyć *kwalifikowaną nazwę* do uzyskania dostępu do typu w przestrzeni nazw, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="26329-114">Use `.` to form a *qualified name* to access a type within a namespace, as the following code shows:</span></span>

  [!code-csharp[qualified name](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#QualifiedName)]

  <span data-ttu-id="26329-115">Użyj [dyrektywy`using`](../keywords/using-directive.md) , aby użyć kwalifikowanych nazw jako opcjonalnych.</span><span class="sxs-lookup"><span data-stu-id="26329-115">Use a [`using` directive](../keywords/using-directive.md) to make the use of qualified names optional.</span></span>

- <span data-ttu-id="26329-116">Użyj `.`, aby uzyskać dostęp do [składowych typu](../../programming-guide/classes-and-structs/index.md#members)static i unstatic, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="26329-116">Use `.` to access [type members](../../programming-guide/classes-and-structs/index.md#members), static and non-static, as the following code shows:</span></span>

  [!code-csharp-interactive[type members](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#TypeMemberAccess)]

<span data-ttu-id="26329-117">Możesz również użyć `.`, aby uzyskać dostęp do [metody rozszerzenia](../../programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="26329-117">You can also use `.` to access an [extension method](../../programming-guide/classes-and-structs/extension-methods.md).</span></span>

## <a name="indexer-operator-"></a><span data-ttu-id="26329-118">Indeksator — operator []</span><span class="sxs-lookup"><span data-stu-id="26329-118">Indexer operator []</span></span>

<span data-ttu-id="26329-119">Nawiasy kwadratowe, `[]`, są zwykle używane dla dostępu do elementu Array, indeksatora lub wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="26329-119">Square brackets, `[]`, are typically used for array, indexer, or pointer element access.</span></span>

### <a name="array-access"></a><span data-ttu-id="26329-120">Dostęp do tablicy</span><span class="sxs-lookup"><span data-stu-id="26329-120">Array access</span></span>

<span data-ttu-id="26329-121">W poniższym przykładzie pokazano, jak uzyskać dostęp do elementów tablicy:</span><span class="sxs-lookup"><span data-stu-id="26329-121">The following example demonstrates how to access array elements:</span></span>

[!code-csharp-interactive[array access](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Arrays)]

<span data-ttu-id="26329-122">Jeśli indeks tablicy znajduje się poza granicami odpowiedniego wymiaru tablicy, zostanie zgłoszony <xref:System.IndexOutOfRangeException>.</span><span class="sxs-lookup"><span data-stu-id="26329-122">If an array index is outside the bounds of the corresponding dimension of an array, an <xref:System.IndexOutOfRangeException> is thrown.</span></span>

<span data-ttu-id="26329-123">Jak pokazano w powyższym przykładzie, można również użyć nawiasów kwadratowych w przypadku deklarowania typu tablicy lub wystąpienia instancji Array.</span><span class="sxs-lookup"><span data-stu-id="26329-123">As the preceding example shows, you also use square brackets when you declare an array type or instantiate an array instance.</span></span>

<span data-ttu-id="26329-124">Aby uzyskać więcej informacji na temat tablic, zobacz [tablice](../../programming-guide/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="26329-124">For more information about arrays, see [Arrays](../../programming-guide/arrays/index.md).</span></span>

### <a name="indexer-access"></a><span data-ttu-id="26329-125">Dostęp indeksatora</span><span class="sxs-lookup"><span data-stu-id="26329-125">Indexer access</span></span>

<span data-ttu-id="26329-126">Poniższy przykład używa typu <xref:System.Collections.Generic.Dictionary%602> .NET do zademonstrowania dostępu indeksatora:</span><span class="sxs-lookup"><span data-stu-id="26329-126">The following example uses the .NET <xref:System.Collections.Generic.Dictionary%602> type to demonstrate indexer access:</span></span>

[!code-csharp-interactive[indexer access](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Indexers)]

<span data-ttu-id="26329-127">Indeksatory umożliwiają indeksowanie wystąpień typu zdefiniowanego przez użytkownika w podobny sposób jak indeksowanie tablicy.</span><span class="sxs-lookup"><span data-stu-id="26329-127">Indexers allow you to index instances of a user-defined type in the similar way as array indexing.</span></span> <span data-ttu-id="26329-128">W przeciwieństwie do indeksów tablicowych, które muszą być liczbami całkowitymi, parametry indeksatora mogą być zadeklarowane jako dowolnego typu.</span><span class="sxs-lookup"><span data-stu-id="26329-128">Unlike array indices, which must be integer, the indexer parameters can be declared to be of any type.</span></span>

<span data-ttu-id="26329-129">Aby uzyskać więcej informacji na temat indeksatorów, zobacz [indeksatory](../../programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="26329-129">For more information about indexers, see [Indexers](../../programming-guide/indexers/index.md).</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="26329-130">Inne użycie []</span><span class="sxs-lookup"><span data-stu-id="26329-130">Other usages of []</span></span>

<span data-ttu-id="26329-131">Aby uzyskać informacje o dostępie do elementów wskaźnika, zobacz sekcję [wskaźnik dostępu do elementu wskaźnika []](pointer-related-operators.md#pointer-element-access-operator-) w artykule [Operatory pokrewne wskaźnika](pointer-related-operators.md) .</span><span class="sxs-lookup"><span data-stu-id="26329-131">For information about pointer element access, see the [Pointer element access operator []](pointer-related-operators.md#pointer-element-access-operator-) section of the [Pointer related operators](pointer-related-operators.md) article.</span></span>

<span data-ttu-id="26329-132">Aby określić [atrybuty](../../programming-guide/concepts/attributes/index.md), należy również użyć nawiasów kwadratowych:</span><span class="sxs-lookup"><span data-stu-id="26329-132">You also use square brackets to specify [attributes](../../programming-guide/concepts/attributes/index.md):</span></span>

```csharp
[System.Diagnostics.Conditional("DEBUG")]
void TraceMethod() {}
```

## <a name="null-conditional-operators--and-"></a><span data-ttu-id="26329-133">Operatory warunkowe o wartości null?.</span><span class="sxs-lookup"><span data-stu-id="26329-133">Null-conditional operators ?.</span></span> <span data-ttu-id="26329-134">lub? []</span><span class="sxs-lookup"><span data-stu-id="26329-134">and ?[]</span></span>

<span data-ttu-id="26329-135">W C# wersji 6 i nowszych operator warunkowy o wartości null stosuje dostęp do elementu członkowskiego,`?.`lub dostęp do elementów,`?[]`, operacji do operandu tylko wtedy, gdy ten operand zostanie obliczony do wartości innej niż null.</span><span class="sxs-lookup"><span data-stu-id="26329-135">Available in C# 6 and later, a null-conditional operator applies a member access, `?.`, or element access, `?[]`, operation to its operand only if that operand evaluates to non-null.</span></span> <span data-ttu-id="26329-136">Jeśli operand zostanie obliczony do `null`, wynik zastosowania operatora jest `null`.</span><span class="sxs-lookup"><span data-stu-id="26329-136">If the operand evaluates to `null`, the result of applying the operator is `null`.</span></span> <span data-ttu-id="26329-137">Operator dostępu warunkowego o wartości null `?.` jest również znany jako operator Elvis.</span><span class="sxs-lookup"><span data-stu-id="26329-137">The null-conditional member access operator `?.` is also known as the Elvis operator.</span></span>

<span data-ttu-id="26329-138">Operatory warunkowe o wartości null są krótkimi obwodami.</span><span class="sxs-lookup"><span data-stu-id="26329-138">The null-conditional operators are short-circuiting.</span></span> <span data-ttu-id="26329-139">Oznacza to, że jeśli jedna operacja w łańcuchu operacji warunkowego elementu członkowskiego lub dostępu do elementu zwraca `null`, reszta łańcucha nie zostanie wykonana.</span><span class="sxs-lookup"><span data-stu-id="26329-139">That is, if one operation in a chain of conditional member or element access operations returns `null`, the rest of the chain doesn't execute.</span></span> <span data-ttu-id="26329-140">W poniższym przykładzie `B` nie zostanie oceniona, jeśli `A` szacuje się w `null` i `C` nie zostanie oceniona, jeśli `A` lub `B` oblicza `null`:</span><span class="sxs-lookup"><span data-stu-id="26329-140">In the following example, `B` is not evaluated if `A` evaluates to `null` and `C` is not evaluated if `A` or `B` evaluates to `null`:</span></span>

```csharp
A?.B?.Do(C);
A?.B?[C];
```

<span data-ttu-id="26329-141">Poniższy przykład ilustruje użycie operatorów `?.` i `?[]`:</span><span class="sxs-lookup"><span data-stu-id="26329-141">The following example demonstrates the usage of the `?.` and `?[]` operators:</span></span>

[!code-csharp-interactive[null-conditional operators](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#NullConditional)]

<span data-ttu-id="26329-142">Powyższy przykład używa również [operatora łączenia wartości null `??`](null-coalescing-operator.md) , aby określić alternatywne wyrażenie do obliczenia w przypadku, gdy wynik operacji warunkowej o wartości null jest `null`.</span><span class="sxs-lookup"><span data-stu-id="26329-142">The preceding example also uses the [null-coalescing operator `??`](null-coalescing-operator.md) to specify an alternative expression to evaluate in case the result of a null-conditional operation is `null`.</span></span>

### <a name="thread-safe-delegate-invocation"></a><span data-ttu-id="26329-143">Wywołanie delegowania bezpiecznego wątku</span><span class="sxs-lookup"><span data-stu-id="26329-143">Thread-safe delegate invocation</span></span>

<span data-ttu-id="26329-144">Użyj operatora `?.`, aby sprawdzić, czy delegat ma wartość różną od null i wywoływać go w sposób bezpieczny dla wątków (na przykład po [podniesieniu zdarzenia](../../../standard/events/how-to-raise-and-consume-events.md)), jak poniższy kod ilustruje:</span><span class="sxs-lookup"><span data-stu-id="26329-144">Use the `?.` operator to check if a delegate is non-null and invoke it in a thread-safe way (for example, when you [raise an event](../../../standard/events/how-to-raise-and-consume-events.md)), as the following code shows:</span></span>

```csharp
PropertyChanged?.Invoke(…)
```

<span data-ttu-id="26329-145">Ten kod jest odpowiednikiem poniższego kodu, który będzie używany w C# 5 lub wcześniejszych wersjach:</span><span class="sxs-lookup"><span data-stu-id="26329-145">That code is equivalent to the following code that you would use in C# 5 or earlier:</span></span>

```csharp
var handler = this.PropertyChanged;
if (handler != null)
{
    handler(…);
}
```

## <a name="invocation-operator-"></a><span data-ttu-id="26329-146">Operator wywołania ()</span><span class="sxs-lookup"><span data-stu-id="26329-146">Invocation operator ()</span></span>

<span data-ttu-id="26329-147">Użyj nawiasów, `()`, aby wywołać [metodę](../../programming-guide/classes-and-structs/methods.md) lub wywołać [delegata](../../programming-guide/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="26329-147">Use parentheses, `()`, to call a [method](../../programming-guide/classes-and-structs/methods.md) or invoke a [delegate](../../programming-guide/delegates/index.md).</span></span>

<span data-ttu-id="26329-148">Poniższy przykład ilustruje sposób wywołania metody z argumentami lub bez nich i Wywołaj delegata:</span><span class="sxs-lookup"><span data-stu-id="26329-148">The following example demonstrates how to call a method, with or without arguments, and invoke a delegate:</span></span>

[!code-csharp-interactive[invocation with ()](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Invocation)]

<span data-ttu-id="26329-149">Po wywołaniu [konstruktora](../../programming-guide/classes-and-structs/constructors.md) za pomocą operatora [`new`](new-operator.md) należy również użyć nawiasów.</span><span class="sxs-lookup"><span data-stu-id="26329-149">You also use parentheses when you invoke a [constructor](../../programming-guide/classes-and-structs/constructors.md) with the [`new`](new-operator.md) operator.</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="26329-150">Inne użycie ()</span><span class="sxs-lookup"><span data-stu-id="26329-150">Other usages of ()</span></span>

<span data-ttu-id="26329-151">Należy również użyć nawiasów, aby dostosować kolejność, w której mają być oceniane operacje w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="26329-151">You also use parentheses to adjust the order in which to evaluate operations in an expression.</span></span> <span data-ttu-id="26329-152">Aby uzyskać więcej informacji, zobacz [ C# operatory](index.md).</span><span class="sxs-lookup"><span data-stu-id="26329-152">For more information, see [C# operators](index.md).</span></span>

<span data-ttu-id="26329-153">[Wyrażenia rzutowania](type-testing-and-cast.md#cast-operator-), które wykonują jawne konwersje typów, również używają nawiasów.</span><span class="sxs-lookup"><span data-stu-id="26329-153">[Cast expressions](type-testing-and-cast.md#cast-operator-), which perform explicit type conversions, also use parentheses.</span></span>

## <a name="index-from-end-operator-"></a><span data-ttu-id="26329-154">Indeks z operatora końcowego ^</span><span class="sxs-lookup"><span data-stu-id="26329-154">Index from end operator ^</span></span>

<span data-ttu-id="26329-155">Dostępne w C# 8,0 i nowszych`^`operator wskazuje położenie elementu od końca sekwencji.</span><span class="sxs-lookup"><span data-stu-id="26329-155">Available in C# 8.0 and later, the `^` operator indicates the element position from the end of a sequence.</span></span> <span data-ttu-id="26329-156">Dla sekwencji `^n` `length`długość wskazuje element z przesunięciem `length - n` od początku sekwencji.</span><span class="sxs-lookup"><span data-stu-id="26329-156">For a sequence of length `length`, `^n` points to the element with offset `length - n` from the start of a sequence.</span></span> <span data-ttu-id="26329-157">Na przykład `^1` wskazuje ostatni element sekwencji i `^length` wskazuje na pierwszy element sekwencji.</span><span class="sxs-lookup"><span data-stu-id="26329-157">For example, `^1` points to the last element of a sequence and `^length` points to the first element of a sequence.</span></span>

[!code-csharp[index from end](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#IndexFromEnd)]

<span data-ttu-id="26329-158">Jak pokazano w poprzednim przykładzie, `^e` Expression jest typu <xref:System.Index?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="26329-158">As the preceding example shows, expression `^e` is of the <xref:System.Index?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="26329-159">W `^e`Expression wynik `e` musi być niejawnie konwertowany na `int`.</span><span class="sxs-lookup"><span data-stu-id="26329-159">In expression `^e`, the result of `e` must be implicitly convertible to `int`.</span></span>

<span data-ttu-id="26329-160">Można też użyć operatora `^` z [operatorem zakresu](#range-operator-) , aby utworzyć zakres indeksów.</span><span class="sxs-lookup"><span data-stu-id="26329-160">You also can use the `^` operator with the [range operator](#range-operator-) to create a range of indices.</span></span> <span data-ttu-id="26329-161">Aby uzyskać więcej informacji, zobacz [indeksy i zakresy](../../tutorials/ranges-indexes.md).</span><span class="sxs-lookup"><span data-stu-id="26329-161">For more information, see [Indices and ranges](../../tutorials/ranges-indexes.md).</span></span>

## <a name="range-operator-"></a><span data-ttu-id="26329-162">Operator zakresu..</span><span class="sxs-lookup"><span data-stu-id="26329-162">Range operator ..</span></span>

<span data-ttu-id="26329-163">Dostępne w C# 8,0 i nowszych operator`..`określa początek i koniec zakresu indeksów jako operandy.</span><span class="sxs-lookup"><span data-stu-id="26329-163">Available in C# 8.0 and later, the `..` operator specifies the start and end of a range of indices as its operands.</span></span> <span data-ttu-id="26329-164">Argument operacji po lewej stronie *jest początkową* częścią zakresu.</span><span class="sxs-lookup"><span data-stu-id="26329-164">The left-hand operand is an *inclusive* start of a range.</span></span> <span data-ttu-id="26329-165">Prawy operand jest *wyłącznym* końcem zakresu.</span><span class="sxs-lookup"><span data-stu-id="26329-165">The right-hand operand is an *exclusive* end of a range.</span></span> <span data-ttu-id="26329-166">Jeden z operandów może być indeksem od początku lub od końca sekwencji, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="26329-166">Either of operands can be an index from the start or from the end of a sequence, as the following example shows:</span></span>

[!code-csharp[range examples](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Ranges)]

<span data-ttu-id="26329-167">Jak pokazano w poprzednim przykładzie, `a..b` Expression jest typu <xref:System.Range?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="26329-167">As the preceding example shows, expression `a..b` is of the <xref:System.Range?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="26329-168">W `a..b`wyrażeń wyniki `a` i `b` muszą być niejawnie konwertowane na `int` lub <xref:System.Index>.</span><span class="sxs-lookup"><span data-stu-id="26329-168">In expression `a..b`, the results of `a` and `b` must be implicitly convertible to `int` or <xref:System.Index>.</span></span>

<span data-ttu-id="26329-169">Możesz pominąć dowolny operand operatora `..`, aby uzyskać otwarty zakres:</span><span class="sxs-lookup"><span data-stu-id="26329-169">You can omit any of the operands of the `..` operator to obtain an open-ended range:</span></span>

- <span data-ttu-id="26329-170">`a..` jest równoznaczna z `a..^0`</span><span class="sxs-lookup"><span data-stu-id="26329-170">`a..` is equivalent to `a..^0`</span></span>
- <span data-ttu-id="26329-171">`..b` jest równoznaczna z `0..b`</span><span class="sxs-lookup"><span data-stu-id="26329-171">`..b` is equivalent to `0..b`</span></span>
- <span data-ttu-id="26329-172">`..` jest równoznaczna z `0..^0`</span><span class="sxs-lookup"><span data-stu-id="26329-172">`..` is equivalent to `0..^0`</span></span>

[!code-csharp[ranges with omitted operands](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#RangesOptional)]

<span data-ttu-id="26329-173">Aby uzyskać więcej informacji, zobacz [indeksy i zakresy](../../tutorials/ranges-indexes.md).</span><span class="sxs-lookup"><span data-stu-id="26329-173">For more information, see [Indices and ranges](../../tutorials/ranges-indexes.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="26329-174">Przeciążanie operatora</span><span class="sxs-lookup"><span data-stu-id="26329-174">Operator overloadability</span></span>

<span data-ttu-id="26329-175">Operatory `.`, `()`, `^`i `..` nie mogą być przeciążone.</span><span class="sxs-lookup"><span data-stu-id="26329-175">The `.`, `()`, `^`, and `..` operators cannot be overloaded.</span></span> <span data-ttu-id="26329-176">Operator `[]` jest również traktowany jako operator niepodlegający obciążeniu.</span><span class="sxs-lookup"><span data-stu-id="26329-176">The `[]` operator is also considered a non-overloadable operator.</span></span> <span data-ttu-id="26329-177">Używanie [indeksatorów](../../programming-guide/indexers/index.md) do obsługi indeksowania z typami zdefiniowanymi przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="26329-177">Use [indexers](../../programming-guide/indexers/index.md) to support indexing with user-defined types.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="26329-178">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="26329-178">C# language specification</span></span>

<span data-ttu-id="26329-179">Aby uzyskać więcej informacji, zobacz następujące sekcje [ C# specyfikacji języka](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="26329-179">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="26329-180">Dostęp do elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="26329-180">Member access</span></span>](~/_csharplang/spec/expressions.md#member-access)
- [<span data-ttu-id="26329-181">Dostęp do elementu</span><span class="sxs-lookup"><span data-stu-id="26329-181">Element access</span></span>](~/_csharplang/spec/expressions.md#element-access)
- [<span data-ttu-id="26329-182">Operator warunkowy o wartości null</span><span class="sxs-lookup"><span data-stu-id="26329-182">Null-conditional operator</span></span>](~/_csharplang/spec/expressions.md#null-conditional-operator)
- [<span data-ttu-id="26329-183">Wyrażenia wywołania</span><span class="sxs-lookup"><span data-stu-id="26329-183">Invocation expressions</span></span>](~/_csharplang/spec/expressions.md#invocation-expressions)

<span data-ttu-id="26329-184">Aby uzyskać więcej informacji na temat indeksów i zakresów, zobacz [Uwaga dotycząca oferty funkcji](~/_csharplang/proposals/csharp-8.0/ranges.md).</span><span class="sxs-lookup"><span data-stu-id="26329-184">For more information about indices and ranges, see the [feature proposal note](~/_csharplang/proposals/csharp-8.0/ranges.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="26329-185">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="26329-185">See also</span></span>

- [<span data-ttu-id="26329-186">C#odwoła</span><span class="sxs-lookup"><span data-stu-id="26329-186">C# reference</span></span>](../index.md)
- [<span data-ttu-id="26329-187">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="26329-187">C# operators</span></span>](index.md)
- [<span data-ttu-id="26329-188">?? (operator łączenia wartości null)</span><span class="sxs-lookup"><span data-stu-id="26329-188">?? (null-coalescing operator)</span></span>](null-coalescing-operator.md)
- [<span data-ttu-id="26329-189">:: operator</span><span class="sxs-lookup"><span data-stu-id="26329-189">:: operator</span></span>](namespace-alias-qualifier.md)
