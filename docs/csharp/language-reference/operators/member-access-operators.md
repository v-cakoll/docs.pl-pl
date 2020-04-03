---
title: Operatory i wyrażenia dostępu do elementów członkowskich — odwołanie do języka C#
description: Dowiedz się więcej o operatorach języka C#, których można użyć do uzyskania dostępu do elementów członkowskich typu.
ms.date: 03/31/2020
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
ms.openlocfilehash: a132e527deadcffb4826c1965987fc09da470a09
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635303"
---
# <a name="member-access-operators-and-expressions-c-reference"></a><span data-ttu-id="f937f-103">Operatory i wyrażenia dostępu do elementów członkowskich (odwołanie do języka C#)</span><span class="sxs-lookup"><span data-stu-id="f937f-103">Member access operators and expressions (C# reference)</span></span>

<span data-ttu-id="f937f-104">Podczas uzyskiwania dostępu do elementu członkowskiego typu można używać następujących operatorów i wyrażeń:</span><span class="sxs-lookup"><span data-stu-id="f937f-104">You can use the following operators and expressions when you access a type member:</span></span>

- <span data-ttu-id="f937f-105">(dostęp członkowski) : aby uzyskać dostęp do członka obszaru nazw lub typu [ `.` ](#member-access-expression-)</span><span class="sxs-lookup"><span data-stu-id="f937f-105">[`.` (member access)](#member-access-expression-): to access a member of a namespace or a type</span></span>
- <span data-ttu-id="f937f-106">[(dostęp do elementu tablicy lub indeksatora): aby uzyskać dostęp do elementu tablicy lub indeksatora typów `[]` ](#indexer-operator-)</span><span class="sxs-lookup"><span data-stu-id="f937f-106">[`[]` (array element or indexer access)](#indexer-operator-): to access an array element or a type indexer</span></span>
- <span data-ttu-id="f937f-107">[i `?[]` (operatory warunkowe zerowe): aby wykonać operację dostępu do elementu członkowskiego lub elementu tylko wtedy, gdy operand jest nieuprawny `?.` ](#null-conditional-operators--and-)</span><span class="sxs-lookup"><span data-stu-id="f937f-107">[`?.` and `?[]` (null-conditional operators)](#null-conditional-operators--and-): to perform a member or element access operation only if an operand is non-null</span></span>
- <span data-ttu-id="f937f-108">(wywołanie) : wywołać metodę dostępną lub wywołać pełnomocnika [ `()` ](#invocation-expression-)</span><span class="sxs-lookup"><span data-stu-id="f937f-108">[`()` (invocation)](#invocation-expression-): to call an accessed method or invoke a delegate</span></span>
- <span data-ttu-id="f937f-109">(indeks od końca) : aby wskazać, że pozycja elementu znajduje się od końca sekwencji [ `^` ](#index-from-end-operator-)</span><span class="sxs-lookup"><span data-stu-id="f937f-109">[`^` (index from end)](#index-from-end-operator-): to indicate that the element position is from the end of a sequence</span></span>
- <span data-ttu-id="f937f-110">(zakres) : określenie zakresu wskaźników, których można użyć do uzyskania zakresu elementów sekwencji [ `..` ](#range-operator-)</span><span class="sxs-lookup"><span data-stu-id="f937f-110">[`..` (range)](#range-operator-): to specify a range of indices that you can use to obtain a range of sequence elements</span></span>

## <a name="member-access-expression-"></a><span data-ttu-id="f937f-111">Wyrażenie dostępu do elementu członkowskiego .</span><span class="sxs-lookup"><span data-stu-id="f937f-111">Member access expression .</span></span>

<span data-ttu-id="f937f-112">Token służy `.` do uzyskiwania dostępu do elementu członkowskiego obszaru nazw lub typu, jak pokazano w poniższych przykładach:</span><span class="sxs-lookup"><span data-stu-id="f937f-112">You use the `.` token to access a member of a namespace or a type, as the following examples demonstrate:</span></span>

- <span data-ttu-id="f937f-113">Służy `.` do uzyskiwania dostępu do zagnieżdżonego obszaru nazw w obszarze nazw, zgodnie z poniższym przykładem [ `using` dyrektywy:](../keywords/using-directive.md)</span><span class="sxs-lookup"><span data-stu-id="f937f-113">Use `.` to access a nested namespace within a namespace, as the following example of a [`using` directive](../keywords/using-directive.md) shows:</span></span>

  [!code-csharp[nested namespaces](snippets/MemberAccessOperators.cs#NestedNamespace)]

- <span data-ttu-id="f937f-114">Służy `.` do tworzenia *nazwy kwalifikowanej,* aby uzyskać dostęp do typu w obszarze nazw, jak pokazano w następującym kodzie:</span><span class="sxs-lookup"><span data-stu-id="f937f-114">Use `.` to form a *qualified name* to access a type within a namespace, as the following code shows:</span></span>

  [!code-csharp[qualified name](snippets/MemberAccessOperators.cs#QualifiedName)]

  <span data-ttu-id="f937f-115">Użyj [ `using` dyrektywy,](../keywords/using-directive.md) aby używać kwalifikowanych nazw opcjonalnie.</span><span class="sxs-lookup"><span data-stu-id="f937f-115">Use a [`using` directive](../keywords/using-directive.md) to make the use of qualified names optional.</span></span>

- <span data-ttu-id="f937f-116">Służy `.` do uzyskiwania dostępu do [elementów członkowskich typu,](../../programming-guide/classes-and-structs/index.md#members)statycznych i niestatycznych, jak pokazuje następujący kod:</span><span class="sxs-lookup"><span data-stu-id="f937f-116">Use `.` to access [type members](../../programming-guide/classes-and-structs/index.md#members), static and non-static, as the following code shows:</span></span>

  [!code-csharp-interactive[type members](snippets/MemberAccessOperators.cs#TypeMemberAccess)]

<span data-ttu-id="f937f-117">Można również `.` użyć, aby uzyskać dostęp do [metody rozszerzenia](../../programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="f937f-117">You can also use `.` to access an [extension method](../../programming-guide/classes-and-structs/extension-methods.md).</span></span>

## <a name="indexer-operator-"></a><span data-ttu-id="f937f-118">Operator indeksatora []</span><span class="sxs-lookup"><span data-stu-id="f937f-118">Indexer operator []</span></span>

<span data-ttu-id="f937f-119">Nawiasy kwadratowe , `[]`są zwykle używane dla dostępu do tablicy, indeksatora lub elementu wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="f937f-119">Square brackets, `[]`, are typically used for array, indexer, or pointer element access.</span></span>

### <a name="array-access"></a><span data-ttu-id="f937f-120">Dostęp do tablicy</span><span class="sxs-lookup"><span data-stu-id="f937f-120">Array access</span></span>

<span data-ttu-id="f937f-121">W poniższym przykładzie pokazano, jak uzyskać dostęp do elementów tablicy:</span><span class="sxs-lookup"><span data-stu-id="f937f-121">The following example demonstrates how to access array elements:</span></span>

[!code-csharp-interactive[array access](snippets/MemberAccessOperators.cs#Arrays)]

<span data-ttu-id="f937f-122">Jeśli indeks tablicy znajduje się poza granicami odpowiedniego <xref:System.IndexOutOfRangeException> wymiaru tablicy, jest generowany.</span><span class="sxs-lookup"><span data-stu-id="f937f-122">If an array index is outside the bounds of the corresponding dimension of an array, an <xref:System.IndexOutOfRangeException> is thrown.</span></span>

<span data-ttu-id="f937f-123">Jak pokazano w poprzednim przykładzie, należy również użyć nawiasów kwadratowych podczas deklarowania typu tablicy lub wystąpienia wystąpienia tablicy.</span><span class="sxs-lookup"><span data-stu-id="f937f-123">As the preceding example shows, you also use square brackets when you declare an array type or instantiate an array instance.</span></span>

<span data-ttu-id="f937f-124">Aby uzyskać więcej informacji o tablicach, zobacz [Tablice](../../programming-guide/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="f937f-124">For more information about arrays, see [Arrays](../../programming-guide/arrays/index.md).</span></span>

### <a name="indexer-access"></a><span data-ttu-id="f937f-125">Dostęp do indeksatora</span><span class="sxs-lookup"><span data-stu-id="f937f-125">Indexer access</span></span>

<span data-ttu-id="f937f-126">W poniższym przykładzie <xref:System.Collections.Generic.Dictionary%602> użyto typu .NET, aby zademonstrować dostęp do indeksatora:</span><span class="sxs-lookup"><span data-stu-id="f937f-126">The following example uses the .NET <xref:System.Collections.Generic.Dictionary%602> type to demonstrate indexer access:</span></span>

[!code-csharp-interactive[indexer access](snippets/MemberAccessOperators.cs#Indexers)]

<span data-ttu-id="f937f-127">Indeksatory umożliwiają indeksowanie wystąpień typu zdefiniowanego przez użytkownika w podobny sposób jak indeksowanie tablicy.</span><span class="sxs-lookup"><span data-stu-id="f937f-127">Indexers allow you to index instances of a user-defined type in the similar way as array indexing.</span></span> <span data-ttu-id="f937f-128">W przeciwieństwie do indeksów tablicowych, które muszą być liczby całkowitej, parametry indeksatora mogą być zadeklarowane jako dowolnego typu.</span><span class="sxs-lookup"><span data-stu-id="f937f-128">Unlike array indices, which must be integer, the indexer parameters can be declared to be of any type.</span></span>

<span data-ttu-id="f937f-129">Aby uzyskać więcej informacji na temat indeksatorów, zobacz [Indeksatory](../../programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="f937f-129">For more information about indexers, see [Indexers](../../programming-guide/indexers/index.md).</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="f937f-130">Inne zastosowania []</span><span class="sxs-lookup"><span data-stu-id="f937f-130">Other usages of []</span></span>

<span data-ttu-id="f937f-131">Aby uzyskać informacje na temat dostępu do elementu wskaźnika, zobacz [operator dostępu do elementu wskaźnik []](pointer-related-operators.md#pointer-element-access-operator-) sekcji [operatorów związanych z wskaźnikiem.](pointer-related-operators.md)</span><span class="sxs-lookup"><span data-stu-id="f937f-131">For information about pointer element access, see the [Pointer element access operator []](pointer-related-operators.md#pointer-element-access-operator-) section of the [Pointer related operators](pointer-related-operators.md) article.</span></span>

<span data-ttu-id="f937f-132">Nawiasy kwadratowe są również używane do określania [atrybutów:](../../programming-guide/concepts/attributes/index.md)</span><span class="sxs-lookup"><span data-stu-id="f937f-132">You also use square brackets to specify [attributes](../../programming-guide/concepts/attributes/index.md):</span></span>

```csharp
[System.Diagnostics.Conditional("DEBUG")]
void TraceMethod() {}
```

## <a name="null-conditional-operators--and-"></a><span data-ttu-id="f937f-133">Operatory warunkowe zerowe?.</span><span class="sxs-lookup"><span data-stu-id="f937f-133">Null-conditional operators ?.</span></span> <span data-ttu-id="f937f-134">I? []</span><span class="sxs-lookup"><span data-stu-id="f937f-134">and ?[]</span></span>

<span data-ttu-id="f937f-135">Dostępne w języku C# 6 i nowszych, operator `?.`warunkowy null stosuje dostęp elementu [członkowskiego](#member-access-expression-), lub [dostęp do elementu](#indexer-operator-), `?[]`operacji do jego operand tylko wtedy, gdy operand ocenia non-null; w przeciwnym `null`razie zwraca .</span><span class="sxs-lookup"><span data-stu-id="f937f-135">Available in C# 6 and later, a null-conditional operator applies a [member access](#member-access-expression-), `?.`, or [element access](#indexer-operator-), `?[]`, operation to its operand only if that operand evaluates to non-null; otherwise, it returns `null`.</span></span> <span data-ttu-id="f937f-136">Czyli</span><span class="sxs-lookup"><span data-stu-id="f937f-136">That is,</span></span>

- <span data-ttu-id="f937f-137">Jeśli `a` ocenia `null`się , `a?.x` wynik `a?[x]` `null`lub jest .</span><span class="sxs-lookup"><span data-stu-id="f937f-137">If `a` evaluates to `null`, the result of `a?.x` or `a?[x]` is `null`.</span></span>
- <span data-ttu-id="f937f-138">Jeśli `a` ma wartość `a?.x` nienawiązaną, `a?[x]` wynik lub jest `a.x` taki `a[x]`sam jak wynik lub , odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="f937f-138">If `a` evaluates to non-null, the result of `a?.x` or `a?[x]` is the same as the result of `a.x` or `a[x]`, respectively.</span></span>

  > [!NOTE]
  > <span data-ttu-id="f937f-139">Jeśli `a.x` `a[x]` lub zgłasza `a?.x` wyjątek `a?[x]` lub zgłosić ten sam `a`wyjątek dla innych niż null .</span><span class="sxs-lookup"><span data-stu-id="f937f-139">If `a.x` or `a[x]` throws an exception, `a?.x` or `a?[x]` would throw the same exception for non-null `a`.</span></span> <span data-ttu-id="f937f-140">Na przykład, `a` jeśli jest instancją tablicy `a`innej `a?[x]` niż <xref:System.IndexOutOfRangeException>null i `x` znajduje się poza granicami , będzie rzutować .</span><span class="sxs-lookup"><span data-stu-id="f937f-140">For example, if `a` is a non-null array instance and `x` is outside the bounds of `a`, `a?[x]` would throw an <xref:System.IndexOutOfRangeException>.</span></span>

<span data-ttu-id="f937f-141">Operatory warunkowe zerowe są zwarcie.</span><span class="sxs-lookup"><span data-stu-id="f937f-141">The null-conditional operators are short-circuiting.</span></span> <span data-ttu-id="f937f-142">Oznacza to, że jeśli jedna operacja w łańcuchu `null`operacji dostępu do elementu warunkowego lub elementu zwraca, reszta łańcucha nie jest wykonywana.</span><span class="sxs-lookup"><span data-stu-id="f937f-142">That is, if one operation in a chain of conditional member or element access operations returns `null`, the rest of the chain doesn't execute.</span></span> <span data-ttu-id="f937f-143">W poniższym `B` przykładzie nie `A` jest `null` oceniana, jeśli ocenia `C` i nie jest oceniana, jeśli `A` lub `B` `null`ocenia:</span><span class="sxs-lookup"><span data-stu-id="f937f-143">In the following example, `B` is not evaluated if `A` evaluates to `null` and `C` is not evaluated if `A` or `B` evaluates to `null`:</span></span>

```csharp
A?.B?.Do(C);
A?.B?[C];
```

<span data-ttu-id="f937f-144">Poniższy przykład pokazuje użycie `?.` i `?[]` operatorów:</span><span class="sxs-lookup"><span data-stu-id="f937f-144">The following example demonstrates the usage of the `?.` and `?[]` operators:</span></span>

[!code-csharp-interactive[null-conditional operators](snippets/MemberAccessOperators.cs#NullConditional)]

<span data-ttu-id="f937f-145">W poprzednim przykładzie użyto również [operatora `??` scalania null,](null-coalescing-operator.md) aby określić alternatywne wyrażenie do oceny `null`w przypadku, gdy wynikiem operacji warunkowej zerowej jest .</span><span class="sxs-lookup"><span data-stu-id="f937f-145">The preceding example also uses the [null-coalescing operator `??`](null-coalescing-operator.md) to specify an alternative expression to evaluate in case the result of a null-conditional operation is `null`.</span></span>

<span data-ttu-id="f937f-146">Jeśli `a.x` `a[x]` lub ma typ `T`wartości nienastępnej wartości `a?.x` null lub `a?[x]` ma odpowiedni typ `T?`wartości [nullable](../builtin-types/nullable-value-types.md) .</span><span class="sxs-lookup"><span data-stu-id="f937f-146">If `a.x` or `a[x]` is of a non-nullable value type `T`, `a?.x` or `a?[x]` is of the corresponding [nullable value type](../builtin-types/nullable-value-types.md) `T?`.</span></span> <span data-ttu-id="f937f-147">Jeśli potrzebne jest wyrażenie `T`typu, zastosuj operatora `??` scalania null do wyrażenia warunkowego null, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="f937f-147">If you need an expression of type `T`, apply the null-coalescing operator `??` to a null-conditional expression, as the following example shows:</span></span>

[!code-csharp-interactive[null-conditional with null-coalescing](snippets/MemberAccessOperators.cs#NullConditionalWithNullCoalescing)]

<span data-ttu-id="f937f-148">W poprzednim `??` przykładzie, jeśli nie używasz `numbers?.Length < 2` operatora, `false` ocenia, kiedy `numbers` jest `null`.</span><span class="sxs-lookup"><span data-stu-id="f937f-148">In the preceding example, if you don't use the `??` operator, `numbers?.Length < 2` evaluates to `false` when `numbers` is `null`.</span></span>

<span data-ttu-id="f937f-149">Operator `?.` dostępu warunkowego null jest również znany jako operator Elvis.</span><span class="sxs-lookup"><span data-stu-id="f937f-149">The null-conditional member access operator `?.` is also known as the Elvis operator.</span></span>

### <a name="thread-safe-delegate-invocation"></a><span data-ttu-id="f937f-150">Wywołanie delegata bezpieczne dla wątków</span><span class="sxs-lookup"><span data-stu-id="f937f-150">Thread-safe delegate invocation</span></span>

<span data-ttu-id="f937f-151">`?.` Operator służy do sprawdzania, czy pełnomocnik jest nie-null i wywołać go w sposób bezpieczny dla wątków (na przykład podczas wywoływania zdarzenia ), jak pokazano w [poniższym](../../../standard/events/how-to-raise-and-consume-events.md)kodzie:</span><span class="sxs-lookup"><span data-stu-id="f937f-151">Use the `?.` operator to check if a delegate is non-null and invoke it in a thread-safe way (for example, when you [raise an event](../../../standard/events/how-to-raise-and-consume-events.md)), as the following code shows:</span></span>

```csharp
PropertyChanged?.Invoke(…)
```

<span data-ttu-id="f937f-152">Ten kod jest odpowiednikiem następującego kodu, który można użyć w języku C# 5 lub wcześniej:</span><span class="sxs-lookup"><span data-stu-id="f937f-152">That code is equivalent to the following code that you would use in C# 5 or earlier:</span></span>

```csharp
var handler = this.PropertyChanged;
if (handler != null)
{
    handler(…);
}
```

## <a name="invocation-expression-"></a><span data-ttu-id="f937f-153">Wyrażenie wywołania ()</span><span class="sxs-lookup"><span data-stu-id="f937f-153">Invocation expression ()</span></span>

<span data-ttu-id="f937f-154">Użyj nawiasów, `()`, aby wywołać [metodę](../../programming-guide/classes-and-structs/methods.md) lub wywołać [pełnomocnika](../../programming-guide/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="f937f-154">Use parentheses, `()`, to call a [method](../../programming-guide/classes-and-structs/methods.md) or invoke a [delegate](../../programming-guide/delegates/index.md).</span></span>

<span data-ttu-id="f937f-155">W poniższym przykładzie pokazano, jak wywołać metodę, z argumentami lub bez argumentów i wywołać delegata:</span><span class="sxs-lookup"><span data-stu-id="f937f-155">The following example demonstrates how to call a method, with or without arguments, and invoke a delegate:</span></span>

[!code-csharp-interactive[invocation with ()](snippets/MemberAccessOperators.cs#Invocation)]

<span data-ttu-id="f937f-156">Nawiasy są również używane podczas wywoływania [konstruktora](../../programming-guide/classes-and-structs/constructors.md) z operatorem. [`new`](new-operator.md)</span><span class="sxs-lookup"><span data-stu-id="f937f-156">You also use parentheses when you invoke a [constructor](../../programming-guide/classes-and-structs/constructors.md) with the [`new`](new-operator.md) operator.</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="f937f-157">Inne zastosowania ()</span><span class="sxs-lookup"><span data-stu-id="f937f-157">Other usages of ()</span></span>

<span data-ttu-id="f937f-158">Nawiasy są również używane do dostosowywania kolejności, w jakiej mają być oceniane operacje w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="f937f-158">You also use parentheses to adjust the order in which to evaluate operations in an expression.</span></span> <span data-ttu-id="f937f-159">Aby uzyskać więcej informacji, zobacz [operatory języka C#.](index.md)</span><span class="sxs-lookup"><span data-stu-id="f937f-159">For more information, see [C# operators](index.md).</span></span>

<span data-ttu-id="f937f-160">[Wyrażenia rzutowe,](type-testing-and-cast.md#cast-operator-)które wykonują jawne konwersje typu, również używają nawiasów.</span><span class="sxs-lookup"><span data-stu-id="f937f-160">[Cast expressions](type-testing-and-cast.md#cast-operator-), which perform explicit type conversions, also use parentheses.</span></span>

## <a name="index-from-end-operator-"></a><span data-ttu-id="f937f-161">Indeks od operatora końcowego ^</span><span class="sxs-lookup"><span data-stu-id="f937f-161">Index from end operator ^</span></span>

<span data-ttu-id="f937f-162">Dostępne w języku C# 8.0 i nowszych, `^` operator wskazuje położenie elementu od końca sekwencji.</span><span class="sxs-lookup"><span data-stu-id="f937f-162">Available in C# 8.0 and later, the `^` operator indicates the element position from the end of a sequence.</span></span> <span data-ttu-id="f937f-163">Dla sekwencji `length`długości `^n` wskazuje element z `length - n` przesunięciem od początku sekwencji.</span><span class="sxs-lookup"><span data-stu-id="f937f-163">For a sequence of length `length`, `^n` points to the element with offset `length - n` from the start of a sequence.</span></span> <span data-ttu-id="f937f-164">Na przykład `^1` wskazuje ostatni element sekwencji `^length` i wskazuje na pierwszy element sekwencji.</span><span class="sxs-lookup"><span data-stu-id="f937f-164">For example, `^1` points to the last element of a sequence and `^length` points to the first element of a sequence.</span></span>

[!code-csharp[index from end](snippets/MemberAccessOperators.cs#IndexFromEnd)]

<span data-ttu-id="f937f-165">Jak pokazano w poprzednim `^e` przykładzie, <xref:System.Index?displayProperty=nameWithType> wyrażenie jest typu.</span><span class="sxs-lookup"><span data-stu-id="f937f-165">As the preceding example shows, expression `^e` is of the <xref:System.Index?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="f937f-166">W `^e`wyrażeniu `e` wynik musi być `int`niejawnie wymienialny na .</span><span class="sxs-lookup"><span data-stu-id="f937f-166">In expression `^e`, the result of `e` must be implicitly convertible to `int`.</span></span>

<span data-ttu-id="f937f-167">Operator z `^` [operatorem zakresu](#range-operator-) służy również do tworzenia zakresu indeksów.</span><span class="sxs-lookup"><span data-stu-id="f937f-167">You also can use the `^` operator with the [range operator](#range-operator-) to create a range of indices.</span></span> <span data-ttu-id="f937f-168">Aby uzyskać więcej informacji, zobacz [Indeksy i zakresy](../../tutorials/ranges-indexes.md).</span><span class="sxs-lookup"><span data-stu-id="f937f-168">For more information, see [Indices and ranges](../../tutorials/ranges-indexes.md).</span></span>

## <a name="range-operator-"></a><span data-ttu-id="f937f-169">Operator zasięgu ..</span><span class="sxs-lookup"><span data-stu-id="f937f-169">Range operator ..</span></span>

<span data-ttu-id="f937f-170">Dostępne w języku C# 8.0 i nowszych, `..` operator określa początek i koniec zakresu indeksów jako jego operandy.</span><span class="sxs-lookup"><span data-stu-id="f937f-170">Available in C# 8.0 and later, the `..` operator specifies the start and end of a range of indices as its operands.</span></span> <span data-ttu-id="f937f-171">Po lewej stronie operand jest *integracyjnym* początkiem zakresu.</span><span class="sxs-lookup"><span data-stu-id="f937f-171">The left-hand operand is an *inclusive* start of a range.</span></span> <span data-ttu-id="f937f-172">Operand po prawej stronie to *ekskluzywny* koniec szeregu.</span><span class="sxs-lookup"><span data-stu-id="f937f-172">The right-hand operand is an *exclusive* end of a range.</span></span> <span data-ttu-id="f937f-173">Jeden z operandów może być indeksem od początku lub od końca sekwencji, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="f937f-173">Either of operands can be an index from the start or from the end of a sequence, as the following example shows:</span></span>

[!code-csharp[range examples](snippets/MemberAccessOperators.cs#Ranges)]

<span data-ttu-id="f937f-174">Jak pokazano w poprzednim `a..b` przykładzie, <xref:System.Range?displayProperty=nameWithType> wyrażenie jest typu.</span><span class="sxs-lookup"><span data-stu-id="f937f-174">As the preceding example shows, expression `a..b` is of the <xref:System.Range?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="f937f-175">W `a..b`wyrazie , `a` `b` wyniki i muszą być `int` <xref:System.Index>w sposób dorozumiany wymienialne lub .</span><span class="sxs-lookup"><span data-stu-id="f937f-175">In expression `a..b`, the results of `a` and `b` must be implicitly convertible to `int` or <xref:System.Index>.</span></span>

<span data-ttu-id="f937f-176">Można pominąć dowolny z argumentów `..` operatora, aby uzyskać zakres otwarty:</span><span class="sxs-lookup"><span data-stu-id="f937f-176">You can omit any of the operands of the `..` operator to obtain an open-ended range:</span></span>

- <span data-ttu-id="f937f-177">`a..`jest równoznaczne z`a..^0`</span><span class="sxs-lookup"><span data-stu-id="f937f-177">`a..` is equivalent to `a..^0`</span></span>
- <span data-ttu-id="f937f-178">`..b`jest równoznaczne z`0..b`</span><span class="sxs-lookup"><span data-stu-id="f937f-178">`..b` is equivalent to `0..b`</span></span>
- <span data-ttu-id="f937f-179">`..`jest równoznaczne z`0..^0`</span><span class="sxs-lookup"><span data-stu-id="f937f-179">`..` is equivalent to `0..^0`</span></span>

[!code-csharp[ranges with omitted operands](snippets/MemberAccessOperators.cs#RangesOptional)]

<span data-ttu-id="f937f-180">Aby uzyskać więcej informacji, zobacz [Indeksy i zakresy](../../tutorials/ranges-indexes.md).</span><span class="sxs-lookup"><span data-stu-id="f937f-180">For more information, see [Indices and ranges](../../tutorials/ranges-indexes.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="f937f-181">Przeciążenie operatora</span><span class="sxs-lookup"><span data-stu-id="f937f-181">Operator overloadability</span></span>

<span data-ttu-id="f937f-182">`.`Operatory `()` `^`, `..` , i nie mogą być przeciążone.</span><span class="sxs-lookup"><span data-stu-id="f937f-182">The `.`, `()`, `^`, and `..` operators cannot be overloaded.</span></span> <span data-ttu-id="f937f-183">Operator `[]` jest również uważany za operatora niedościsty.</span><span class="sxs-lookup"><span data-stu-id="f937f-183">The `[]` operator is also considered a non-overloadable operator.</span></span> <span data-ttu-id="f937f-184">Użyj [indeksatorów](../../programming-guide/indexers/index.md) do obsługi indeksowania z typami zdefiniowanymi przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="f937f-184">Use [indexers](../../programming-guide/indexers/index.md) to support indexing with user-defined types.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="f937f-185">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="f937f-185">C# language specification</span></span>

<span data-ttu-id="f937f-186">Aby uzyskać więcej informacji, zobacz następujące sekcje [specyfikacji języka języka C#:](~/_csharplang/spec/introduction.md)</span><span class="sxs-lookup"><span data-stu-id="f937f-186">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="f937f-187">Dostęp do członków</span><span class="sxs-lookup"><span data-stu-id="f937f-187">Member access</span></span>](~/_csharplang/spec/expressions.md#member-access)
- [<span data-ttu-id="f937f-188">Dostęp do elementów</span><span class="sxs-lookup"><span data-stu-id="f937f-188">Element access</span></span>](~/_csharplang/spec/expressions.md#element-access)
- [<span data-ttu-id="f937f-189">Operator warunkowy zerowy</span><span class="sxs-lookup"><span data-stu-id="f937f-189">Null-conditional operator</span></span>](~/_csharplang/spec/expressions.md#null-conditional-operator)
- [<span data-ttu-id="f937f-190">Wyrażenia wywołania</span><span class="sxs-lookup"><span data-stu-id="f937f-190">Invocation expressions</span></span>](~/_csharplang/spec/expressions.md#invocation-expressions)

<span data-ttu-id="f937f-191">Aby uzyskać więcej informacji na temat indeksów i zakresów, zobacz [notatkę dotyczącą propozycji funkcji](~/_csharplang/proposals/csharp-8.0/ranges.md).</span><span class="sxs-lookup"><span data-stu-id="f937f-191">For more information about indices and ranges, see the [feature proposal note](~/_csharplang/proposals/csharp-8.0/ranges.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f937f-192">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f937f-192">See also</span></span>

- [<span data-ttu-id="f937f-193">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="f937f-193">C# reference</span></span>](../index.md)
- [<span data-ttu-id="f937f-194">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="f937f-194">C# operators</span></span>](index.md)
- [<span data-ttu-id="f937f-195">?? (operator zrzekania się wartości null)</span><span class="sxs-lookup"><span data-stu-id="f937f-195">?? (null-coalescing operator)</span></span>](null-coalescing-operator.md)
- [<span data-ttu-id="f937f-196">:: — Operator</span><span class="sxs-lookup"><span data-stu-id="f937f-196">:: operator</span></span>](namespace-alias-qualifier.md)
