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
ms.openlocfilehash: e69cc5a9634f0b5232562782557645894f94ce2e
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345303"
---
# <a name="member-access-operators-c-reference"></a><span data-ttu-id="81d49-103">Operatory dostępu do elementówC# członkowskich (odwołanie)</span><span class="sxs-lookup"><span data-stu-id="81d49-103">Member access operators (C# reference)</span></span>

<span data-ttu-id="81d49-104">Podczas uzyskiwania dostępu do elementu członkowskiego typu można użyć następujących operatorów:</span><span class="sxs-lookup"><span data-stu-id="81d49-104">You can use the following operators when you access a type member:</span></span>

- <span data-ttu-id="81d49-105">[`.` (dostęp do elementu członkowskiego)](#member-access-operator-): Aby uzyskać dostęp do elementu członkowskiego przestrzeni nazw lub typu</span><span class="sxs-lookup"><span data-stu-id="81d49-105">[`.` (member access)](#member-access-operator-): to access a member of a namespace or a type</span></span>
- <span data-ttu-id="81d49-106">[`[]` (dostęp do elementu tablicy lub indeksatora)](#indexer-operator-): Aby uzyskać dostęp do elementu tablicy lub indeksatora typu</span><span class="sxs-lookup"><span data-stu-id="81d49-106">[`[]` (array element or indexer access)](#indexer-operator-): to access an array element or a type indexer</span></span>
- <span data-ttu-id="81d49-107">[`?.` i `?[]` (operatory warunkowe o wartości null)](#null-conditional-operators--and-): Aby wykonać operację dostępu do elementu członkowskiego lub tylko wtedy, gdy operand ma wartość różną od null</span><span class="sxs-lookup"><span data-stu-id="81d49-107">[`?.` and `?[]` (null-conditional operators)](#null-conditional-operators--and-): to perform a member or element access operation only if an operand is non-null</span></span>
- <span data-ttu-id="81d49-108">[`()` (wywołanie)](#invocation-operator-): aby wywołać metodę dostępu lub wywołać delegata</span><span class="sxs-lookup"><span data-stu-id="81d49-108">[`()` (invocation)](#invocation-operator-): to call an accessed method or invoke a delegate</span></span>
- <span data-ttu-id="81d49-109">[`^` (indeks od końca)](#index-from-end-operator-): wskazuje, że pozycja elementu jest z końca sekwencji</span><span class="sxs-lookup"><span data-stu-id="81d49-109">[`^` (index from end)](#index-from-end-operator-): to indicate that the element position is from the end of a sequence</span></span>
- <span data-ttu-id="81d49-110">[`..` (zakres)](#range-operator-): aby określić zakres indeksów, których można użyć w celu uzyskania zakresu elementów sekwencji</span><span class="sxs-lookup"><span data-stu-id="81d49-110">[`..` (range)](#range-operator-): to specify a range of indices that you can use to obtain a range of sequence elements</span></span>

## <a name="member-access-operator-"></a><span data-ttu-id="81d49-111">Operator dostępu do elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="81d49-111">Member access operator .</span></span>

<span data-ttu-id="81d49-112">Token `.` służy do uzyskiwania dostępu do elementu członkowskiego przestrzeni nazw lub typu, jak pokazano w poniższych przykładach:</span><span class="sxs-lookup"><span data-stu-id="81d49-112">You use the `.` token to access a member of a namespace or a type, as the following examples demonstrate:</span></span>

- <span data-ttu-id="81d49-113">Użyj `.`, aby uzyskać dostęp do zagnieżdżonej przestrzeni nazw w przestrzeni nazw, jak pokazano w poniższym przykładzie [dyrektywy`using`](../keywords/using-directive.md) :</span><span class="sxs-lookup"><span data-stu-id="81d49-113">Use `.` to access a nested namespace within a namespace, as the following example of a [`using` directive](../keywords/using-directive.md) shows:</span></span>

  [!code-csharp[nested namespaces](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#NestedNamespace)]

- <span data-ttu-id="81d49-114">Użyj `.`, aby utworzyć *kwalifikowaną nazwę* do uzyskania dostępu do typu w przestrzeni nazw, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="81d49-114">Use `.` to form a *qualified name* to access a type within a namespace, as the following code shows:</span></span>

  [!code-csharp[qualified name](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#QualifiedName)]

  <span data-ttu-id="81d49-115">Użyj [dyrektywy`using`](../keywords/using-directive.md) , aby użyć kwalifikowanych nazw jako opcjonalnych.</span><span class="sxs-lookup"><span data-stu-id="81d49-115">Use a [`using` directive](../keywords/using-directive.md) to make the use of qualified names optional.</span></span>

- <span data-ttu-id="81d49-116">Użyj `.`, aby uzyskać dostęp do [składowych typu](../../programming-guide/classes-and-structs/index.md#members)static i unstatic, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="81d49-116">Use `.` to access [type members](../../programming-guide/classes-and-structs/index.md#members), static and non-static, as the following code shows:</span></span>

  [!code-csharp-interactive[type members](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#TypeMemberAccess)]

<span data-ttu-id="81d49-117">Możesz również użyć `.`, aby uzyskać dostęp do [metody rozszerzenia](../../programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="81d49-117">You can also use `.` to access an [extension method](../../programming-guide/classes-and-structs/extension-methods.md).</span></span>

## <a name="indexer-operator-"></a><span data-ttu-id="81d49-118">Indeksator — operator []</span><span class="sxs-lookup"><span data-stu-id="81d49-118">Indexer operator []</span></span>

<span data-ttu-id="81d49-119">Nawiasy kwadratowe, `[]`, są zwykle używane dla dostępu do elementu Array, indeksatora lub wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="81d49-119">Square brackets, `[]`, are typically used for array, indexer, or pointer element access.</span></span>

### <a name="array-access"></a><span data-ttu-id="81d49-120">Dostęp do tablicy</span><span class="sxs-lookup"><span data-stu-id="81d49-120">Array access</span></span>

<span data-ttu-id="81d49-121">W poniższym przykładzie pokazano, jak uzyskać dostęp do elementów tablicy:</span><span class="sxs-lookup"><span data-stu-id="81d49-121">The following example demonstrates how to access array elements:</span></span>

[!code-csharp-interactive[array access](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Arrays)]

<span data-ttu-id="81d49-122">Jeśli indeks tablicy znajduje się poza granicami odpowiedniego wymiaru tablicy, zostanie zgłoszony <xref:System.IndexOutOfRangeException>.</span><span class="sxs-lookup"><span data-stu-id="81d49-122">If an array index is outside the bounds of the corresponding dimension of an array, an <xref:System.IndexOutOfRangeException> is thrown.</span></span>

<span data-ttu-id="81d49-123">Jak pokazano w powyższym przykładzie, można również użyć nawiasów kwadratowych w przypadku deklarowania typu tablicy lub wystąpienia instancji Array.</span><span class="sxs-lookup"><span data-stu-id="81d49-123">As the preceding example shows, you also use square brackets when you declare an array type or instantiate an array instance.</span></span>

<span data-ttu-id="81d49-124">Aby uzyskać więcej informacji na temat tablic, zobacz [tablice](../../programming-guide/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="81d49-124">For more information about arrays, see [Arrays](../../programming-guide/arrays/index.md).</span></span>

### <a name="indexer-access"></a><span data-ttu-id="81d49-125">Dostęp indeksatora</span><span class="sxs-lookup"><span data-stu-id="81d49-125">Indexer access</span></span>

<span data-ttu-id="81d49-126">Poniższy przykład używa typu <xref:System.Collections.Generic.Dictionary%602> .NET do zademonstrowania dostępu indeksatora:</span><span class="sxs-lookup"><span data-stu-id="81d49-126">The following example uses the .NET <xref:System.Collections.Generic.Dictionary%602> type to demonstrate indexer access:</span></span>

[!code-csharp-interactive[indexer access](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Indexers)]

<span data-ttu-id="81d49-127">Indeksatory umożliwiają indeksowanie wystąpień typu zdefiniowanego przez użytkownika w podobny sposób jak indeksowanie tablicy.</span><span class="sxs-lookup"><span data-stu-id="81d49-127">Indexers allow you to index instances of a user-defined type in the similar way as array indexing.</span></span> <span data-ttu-id="81d49-128">W przeciwieństwie do indeksów tablicowych, które muszą być liczbami całkowitymi, parametry indeksatora mogą być zadeklarowane jako dowolnego typu.</span><span class="sxs-lookup"><span data-stu-id="81d49-128">Unlike array indices, which must be integer, the indexer parameters can be declared to be of any type.</span></span>

<span data-ttu-id="81d49-129">Aby uzyskać więcej informacji na temat indeksatorów, zobacz [indeksatory](../../programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="81d49-129">For more information about indexers, see [Indexers](../../programming-guide/indexers/index.md).</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="81d49-130">Inne użycie []</span><span class="sxs-lookup"><span data-stu-id="81d49-130">Other usages of []</span></span>

<span data-ttu-id="81d49-131">Aby uzyskać informacje o dostępie do elementów wskaźnika, zobacz sekcję [wskaźnik dostępu do elementu wskaźnika []](pointer-related-operators.md#pointer-element-access-operator-) w artykule [Operatory pokrewne wskaźnika](pointer-related-operators.md) .</span><span class="sxs-lookup"><span data-stu-id="81d49-131">For information about pointer element access, see the [Pointer element access operator []](pointer-related-operators.md#pointer-element-access-operator-) section of the [Pointer related operators](pointer-related-operators.md) article.</span></span>

<span data-ttu-id="81d49-132">Aby określić [atrybuty](../../programming-guide/concepts/attributes/index.md), należy również użyć nawiasów kwadratowych:</span><span class="sxs-lookup"><span data-stu-id="81d49-132">You also use square brackets to specify [attributes](../../programming-guide/concepts/attributes/index.md):</span></span>

```csharp
[System.Diagnostics.Conditional("DEBUG")]
void TraceMethod() {}
```

## <a name="null-conditional-operators--and-"></a><span data-ttu-id="81d49-133">Operatory warunkowe o wartości null?.</span><span class="sxs-lookup"><span data-stu-id="81d49-133">Null-conditional operators ?.</span></span> <span data-ttu-id="81d49-134">lub? []</span><span class="sxs-lookup"><span data-stu-id="81d49-134">and ?[]</span></span>

<span data-ttu-id="81d49-135">W C# wersji 6 i nowszych operator warunkowy o wartości null stosuje dostęp do elementu [członkowskiego](#member-access-operator-), `?.`lub [dostęp do elementów](#indexer-operator-), `?[]`, operacji do operandu tylko wtedy, gdy ten operand zwróci wartość różną od null; w przeciwnym razie zwraca `null`.</span><span class="sxs-lookup"><span data-stu-id="81d49-135">Available in C# 6 and later, a null-conditional operator applies a [member access](#member-access-operator-), `?.`, or [element access](#indexer-operator-), `?[]`, operation to its operand only if that operand evaluates to non-null; otherwise, it returns `null`.</span></span> <span data-ttu-id="81d49-136">Czyli</span><span class="sxs-lookup"><span data-stu-id="81d49-136">That is,</span></span>

- <span data-ttu-id="81d49-137">Jeśli `a` oblicza `null`, wynik `a?.x` lub `a?[x]` jest `null`.</span><span class="sxs-lookup"><span data-stu-id="81d49-137">If `a` evaluates to `null`, the result of `a?.x` or `a?[x]` is `null`.</span></span>
- <span data-ttu-id="81d49-138">Jeśli `a` ma wartość różną od null, wynik `a?.x` lub `a?[x]` jest taki sam jak wynik `a.x` lub `a[x]`.</span><span class="sxs-lookup"><span data-stu-id="81d49-138">If `a` evaluates to non-null, the result of `a?.x` or `a?[x]` is the same as the result of `a.x` or `a[x]`, respectively.</span></span>

  > [!NOTE]
  > <span data-ttu-id="81d49-139">Jeśli `a.x` lub `a[x]` zgłasza wyjątek, `a?.x` lub `a?[x]` zgłosi ten sam wyjątek dla niezerowego `a`.</span><span class="sxs-lookup"><span data-stu-id="81d49-139">If `a.x` or `a[x]` throws an exception, `a?.x` or `a?[x]` would throw the same exception for non-null `a`.</span></span> <span data-ttu-id="81d49-140">Na przykład jeśli `a` jest wystąpieniem tablicy o wartości innej niż null i `x` wykracza poza granice `a`, `a?[x]` spowodowałaby zgłoszenie <xref:System.IndexOutOfRangeException>.</span><span class="sxs-lookup"><span data-stu-id="81d49-140">For example, if `a` is a non-null array instance and `x` is outside the bounds of `a`, `a?[x]` would throw an <xref:System.IndexOutOfRangeException>.</span></span>

<span data-ttu-id="81d49-141">Operatory warunkowe `null` skracają łańcuch wykonywania operacji.</span><span class="sxs-lookup"><span data-stu-id="81d49-141">The null-conditional operators are short-circuiting.</span></span> <span data-ttu-id="81d49-142">Oznacza to, że jeśli jedna operacja w łańcuchu operacji warunkowego elementu członkowskiego lub dostępu do elementu zwraca `null`, reszta łańcucha nie zostanie wykonana.</span><span class="sxs-lookup"><span data-stu-id="81d49-142">That is, if one operation in a chain of conditional member or element access operations returns `null`, the rest of the chain doesn't execute.</span></span> <span data-ttu-id="81d49-143">W poniższym przykładzie `B` nie zostanie oceniona, jeśli `A` szacuje się w `null` i `C` nie zostanie oceniona, jeśli `A` lub `B` oblicza `null`:</span><span class="sxs-lookup"><span data-stu-id="81d49-143">In the following example, `B` is not evaluated if `A` evaluates to `null` and `C` is not evaluated if `A` or `B` evaluates to `null`:</span></span>

```csharp
A?.B?.Do(C);
A?.B?[C];
```

<span data-ttu-id="81d49-144">Poniższy przykład ilustruje użycie operatorów `?.` i `?[]`:</span><span class="sxs-lookup"><span data-stu-id="81d49-144">The following example demonstrates the usage of the `?.` and `?[]` operators:</span></span>

[!code-csharp-interactive[null-conditional operators](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#NullConditional)]

<span data-ttu-id="81d49-145">Powyższy przykład używa również [operatora łączenia wartości null `??`](null-coalescing-operator.md) , aby określić alternatywne wyrażenie do obliczenia w przypadku, gdy wynik operacji warunkowej o wartości null jest `null`.</span><span class="sxs-lookup"><span data-stu-id="81d49-145">The preceding example also uses the [null-coalescing operator `??`](null-coalescing-operator.md) to specify an alternative expression to evaluate in case the result of a null-conditional operation is `null`.</span></span>

<span data-ttu-id="81d49-146">Operator dostępu warunkowego o wartości null `?.` jest również znany jako operator Elvis.</span><span class="sxs-lookup"><span data-stu-id="81d49-146">The null-conditional member access operator `?.` is also known as the Elvis operator.</span></span>

### <a name="thread-safe-delegate-invocation"></a><span data-ttu-id="81d49-147">Wywołanie delegowania bezpiecznego wątku</span><span class="sxs-lookup"><span data-stu-id="81d49-147">Thread-safe delegate invocation</span></span>

<span data-ttu-id="81d49-148">Użyj operatora `?.`, aby sprawdzić, czy delegat ma wartość różną od null i wywoływać go w sposób bezpieczny dla wątków (na przykład po [podniesieniu zdarzenia](../../../standard/events/how-to-raise-and-consume-events.md)), jak poniższy kod ilustruje:</span><span class="sxs-lookup"><span data-stu-id="81d49-148">Use the `?.` operator to check if a delegate is non-null and invoke it in a thread-safe way (for example, when you [raise an event](../../../standard/events/how-to-raise-and-consume-events.md)), as the following code shows:</span></span>

```csharp
PropertyChanged?.Invoke(…)
```

<span data-ttu-id="81d49-149">Ten kod jest odpowiednikiem poniższego kodu, który będzie używany w C# 5 lub wcześniejszych wersjach:</span><span class="sxs-lookup"><span data-stu-id="81d49-149">That code is equivalent to the following code that you would use in C# 5 or earlier:</span></span>

```csharp
var handler = this.PropertyChanged;
if (handler != null)
{
    handler(…);
}
```

## <a name="invocation-operator-"></a><span data-ttu-id="81d49-150">Operator wywołania ()</span><span class="sxs-lookup"><span data-stu-id="81d49-150">Invocation operator ()</span></span>

<span data-ttu-id="81d49-151">Użyj nawiasów, `()`, aby wywołać [metodę](../../programming-guide/classes-and-structs/methods.md) lub wywołać [delegata](../../programming-guide/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="81d49-151">Use parentheses, `()`, to call a [method](../../programming-guide/classes-and-structs/methods.md) or invoke a [delegate](../../programming-guide/delegates/index.md).</span></span>

<span data-ttu-id="81d49-152">Poniższy przykład ilustruje sposób wywołania metody z argumentami lub bez nich i Wywołaj delegata:</span><span class="sxs-lookup"><span data-stu-id="81d49-152">The following example demonstrates how to call a method, with or without arguments, and invoke a delegate:</span></span>

[!code-csharp-interactive[invocation with ()](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Invocation)]

<span data-ttu-id="81d49-153">Po wywołaniu [konstruktora](../../programming-guide/classes-and-structs/constructors.md) za pomocą operatora [`new`](new-operator.md) należy również użyć nawiasów.</span><span class="sxs-lookup"><span data-stu-id="81d49-153">You also use parentheses when you invoke a [constructor](../../programming-guide/classes-and-structs/constructors.md) with the [`new`](new-operator.md) operator.</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="81d49-154">Inne użycie ()</span><span class="sxs-lookup"><span data-stu-id="81d49-154">Other usages of ()</span></span>

<span data-ttu-id="81d49-155">Należy również użyć nawiasów, aby dostosować kolejność, w której mają być oceniane operacje w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="81d49-155">You also use parentheses to adjust the order in which to evaluate operations in an expression.</span></span> <span data-ttu-id="81d49-156">Aby uzyskać więcej informacji, zobacz [ C# operatory](index.md).</span><span class="sxs-lookup"><span data-stu-id="81d49-156">For more information, see [C# operators](index.md).</span></span>

<span data-ttu-id="81d49-157">[Wyrażenia rzutowania](type-testing-and-cast.md#cast-operator-), które wykonują jawne konwersje typów, również używają nawiasów.</span><span class="sxs-lookup"><span data-stu-id="81d49-157">[Cast expressions](type-testing-and-cast.md#cast-operator-), which perform explicit type conversions, also use parentheses.</span></span>

## <a name="index-from-end-operator-"></a><span data-ttu-id="81d49-158">Indeks z operatora końcowego ^</span><span class="sxs-lookup"><span data-stu-id="81d49-158">Index from end operator ^</span></span>

<span data-ttu-id="81d49-159">Dostępne w C# 8,0 i nowszych `^` operator wskazuje położenie elementu od końca sekwencji.</span><span class="sxs-lookup"><span data-stu-id="81d49-159">Available in C# 8.0 and later, the `^` operator indicates the element position from the end of a sequence.</span></span> <span data-ttu-id="81d49-160">Dla sekwencji `^n` `length`długość wskazuje element z przesunięciem `length - n` od początku sekwencji.</span><span class="sxs-lookup"><span data-stu-id="81d49-160">For a sequence of length `length`, `^n` points to the element with offset `length - n` from the start of a sequence.</span></span> <span data-ttu-id="81d49-161">Na przykład `^1` wskazuje ostatni element sekwencji i `^length` wskazuje na pierwszy element sekwencji.</span><span class="sxs-lookup"><span data-stu-id="81d49-161">For example, `^1` points to the last element of a sequence and `^length` points to the first element of a sequence.</span></span>

[!code-csharp[index from end](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#IndexFromEnd)]

<span data-ttu-id="81d49-162">Jak pokazano w poprzednim przykładzie, `^e` Expression jest typu <xref:System.Index?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="81d49-162">As the preceding example shows, expression `^e` is of the <xref:System.Index?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="81d49-163">W `^e`Expression wynik `e` musi być niejawnie konwertowany na `int`.</span><span class="sxs-lookup"><span data-stu-id="81d49-163">In expression `^e`, the result of `e` must be implicitly convertible to `int`.</span></span>

<span data-ttu-id="81d49-164">Można też użyć operatora `^` z [operatorem zakresu](#range-operator-) , aby utworzyć zakres indeksów.</span><span class="sxs-lookup"><span data-stu-id="81d49-164">You also can use the `^` operator with the [range operator](#range-operator-) to create a range of indices.</span></span> <span data-ttu-id="81d49-165">Aby uzyskać więcej informacji, zobacz [indeksy i zakresy](../../tutorials/ranges-indexes.md).</span><span class="sxs-lookup"><span data-stu-id="81d49-165">For more information, see [Indices and ranges](../../tutorials/ranges-indexes.md).</span></span>

## <a name="range-operator-"></a><span data-ttu-id="81d49-166">Operator zakresu..</span><span class="sxs-lookup"><span data-stu-id="81d49-166">Range operator ..</span></span>

<span data-ttu-id="81d49-167">Dostępne w C# 8,0 i nowszych operator `..` określa początek i koniec zakresu indeksów jako operandy.</span><span class="sxs-lookup"><span data-stu-id="81d49-167">Available in C# 8.0 and later, the `..` operator specifies the start and end of a range of indices as its operands.</span></span> <span data-ttu-id="81d49-168">Argument operacji po lewej stronie *jest początkową* częścią zakresu.</span><span class="sxs-lookup"><span data-stu-id="81d49-168">The left-hand operand is an *inclusive* start of a range.</span></span> <span data-ttu-id="81d49-169">Prawy operand jest *wyłącznym* końcem zakresu.</span><span class="sxs-lookup"><span data-stu-id="81d49-169">The right-hand operand is an *exclusive* end of a range.</span></span> <span data-ttu-id="81d49-170">Jeden z operandów może być indeksem od początku lub od końca sekwencji, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="81d49-170">Either of operands can be an index from the start or from the end of a sequence, as the following example shows:</span></span>

[!code-csharp[range examples](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Ranges)]

<span data-ttu-id="81d49-171">Jak pokazano w poprzednim przykładzie, `a..b` Expression jest typu <xref:System.Range?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="81d49-171">As the preceding example shows, expression `a..b` is of the <xref:System.Range?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="81d49-172">W `a..b`wyrażeń wyniki `a` i `b` muszą być niejawnie konwertowane na `int` lub <xref:System.Index>.</span><span class="sxs-lookup"><span data-stu-id="81d49-172">In expression `a..b`, the results of `a` and `b` must be implicitly convertible to `int` or <xref:System.Index>.</span></span>

<span data-ttu-id="81d49-173">Możesz pominąć dowolny operand operatora `..`, aby uzyskać otwarty zakres:</span><span class="sxs-lookup"><span data-stu-id="81d49-173">You can omit any of the operands of the `..` operator to obtain an open-ended range:</span></span>

- <span data-ttu-id="81d49-174">`a..` jest równoznaczna z `a..^0`</span><span class="sxs-lookup"><span data-stu-id="81d49-174">`a..` is equivalent to `a..^0`</span></span>
- <span data-ttu-id="81d49-175">`..b` jest równoznaczna z `0..b`</span><span class="sxs-lookup"><span data-stu-id="81d49-175">`..b` is equivalent to `0..b`</span></span>
- <span data-ttu-id="81d49-176">`..` jest równoznaczna z `0..^0`</span><span class="sxs-lookup"><span data-stu-id="81d49-176">`..` is equivalent to `0..^0`</span></span>

[!code-csharp[ranges with omitted operands](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#RangesOptional)]

<span data-ttu-id="81d49-177">Aby uzyskać więcej informacji, zobacz [indeksy i zakresy](../../tutorials/ranges-indexes.md).</span><span class="sxs-lookup"><span data-stu-id="81d49-177">For more information, see [Indices and ranges](../../tutorials/ranges-indexes.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="81d49-178">Przeciążanie operatora</span><span class="sxs-lookup"><span data-stu-id="81d49-178">Operator overloadability</span></span>

<span data-ttu-id="81d49-179">Operatory `.`, `()`, `^`i `..` nie mogą być przeciążone.</span><span class="sxs-lookup"><span data-stu-id="81d49-179">The `.`, `()`, `^`, and `..` operators cannot be overloaded.</span></span> <span data-ttu-id="81d49-180">Operator `[]` jest również traktowany jako operator niepodlegający obciążeniu.</span><span class="sxs-lookup"><span data-stu-id="81d49-180">The `[]` operator is also considered a non-overloadable operator.</span></span> <span data-ttu-id="81d49-181">Używanie [indeksatorów](../../programming-guide/indexers/index.md) do obsługi indeksowania z typami zdefiniowanymi przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="81d49-181">Use [indexers](../../programming-guide/indexers/index.md) to support indexing with user-defined types.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="81d49-182">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="81d49-182">C# language specification</span></span>

<span data-ttu-id="81d49-183">Aby uzyskać więcej informacji, zobacz następujące sekcje [ C# specyfikacji języka](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="81d49-183">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="81d49-184">Dostęp do elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="81d49-184">Member access</span></span>](~/_csharplang/spec/expressions.md#member-access)
- [<span data-ttu-id="81d49-185">Dostęp do elementu</span><span class="sxs-lookup"><span data-stu-id="81d49-185">Element access</span></span>](~/_csharplang/spec/expressions.md#element-access)
- [<span data-ttu-id="81d49-186">Operator warunkowy o wartości null</span><span class="sxs-lookup"><span data-stu-id="81d49-186">Null-conditional operator</span></span>](~/_csharplang/spec/expressions.md#null-conditional-operator)
- [<span data-ttu-id="81d49-187">Wyrażenia wywołania</span><span class="sxs-lookup"><span data-stu-id="81d49-187">Invocation expressions</span></span>](~/_csharplang/spec/expressions.md#invocation-expressions)

<span data-ttu-id="81d49-188">Aby uzyskać więcej informacji na temat indeksów i zakresów, zobacz [Uwaga dotycząca oferty funkcji](~/_csharplang/proposals/csharp-8.0/ranges.md).</span><span class="sxs-lookup"><span data-stu-id="81d49-188">For more information about indices and ranges, see the [feature proposal note](~/_csharplang/proposals/csharp-8.0/ranges.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="81d49-189">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="81d49-189">See also</span></span>

- [<span data-ttu-id="81d49-190">C#odwoła</span><span class="sxs-lookup"><span data-stu-id="81d49-190">C# reference</span></span>](../index.md)
- [<span data-ttu-id="81d49-191">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="81d49-191">C# operators</span></span>](index.md)
- [<span data-ttu-id="81d49-192">?? (operator łączenia wartości null)</span><span class="sxs-lookup"><span data-stu-id="81d49-192">?? (null-coalescing operator)</span></span>](null-coalescing-operator.md)
- [<span data-ttu-id="81d49-193">:: operator</span><span class="sxs-lookup"><span data-stu-id="81d49-193">:: operator</span></span>](namespace-alias-qualifier.md)
