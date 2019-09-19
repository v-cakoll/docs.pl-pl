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
ms.openlocfilehash: 45af31d10d77f4c63b27b34595b97fdd11ef95a1
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71116125"
---
# <a name="member-access-operators-c-reference"></a><span data-ttu-id="feeaa-103">Operatory dostępu do elementówC# członkowskich (odwołanie)</span><span class="sxs-lookup"><span data-stu-id="feeaa-103">Member access operators (C# reference)</span></span>

<span data-ttu-id="feeaa-104">Podczas uzyskiwania dostępu do elementu członkowskiego typu mogą być używane następujące operatory:</span><span class="sxs-lookup"><span data-stu-id="feeaa-104">You might use the following operators when you access a type member:</span></span>

- <span data-ttu-id="feeaa-105">[(dostęp do elementu członkowskiego): Aby uzyskać dostęp do elementu członkowskiego przestrzeni nazw lub typu `.` ](#member-access-operator-)</span><span class="sxs-lookup"><span data-stu-id="feeaa-105">[`.` (member access)](#member-access-operator-): to access a member of a namespace or a type</span></span>
- <span data-ttu-id="feeaa-106">[(dostęp do elementu tablicy lub indeksatora): Aby uzyskać dostęp do elementu tablicy lub indeksatora typu `[]` ](#indexer-operator-)</span><span class="sxs-lookup"><span data-stu-id="feeaa-106">[`[]` (array element or indexer access)](#indexer-operator-): to access an array element or a type indexer</span></span>
- <span data-ttu-id="feeaa-107">[and (operatorywarunkoweowartościnull):dowykonywaniaoperacjidostępudoelementuczłonkowskiegolubelementówtylkowtedy,gdyoperandmawartośćróżnąodnull`?[]` `?.` ](#null-conditional-operators--and-)</span><span class="sxs-lookup"><span data-stu-id="feeaa-107">[`?.` and `?[]` (null-conditional operators)](#null-conditional-operators--and-): to perform a member or element access operation only if an operand is non-null</span></span>
- <span data-ttu-id="feeaa-108">(wywołanie): aby wywołać metodę dostępu lub wywołać delegata [ `()` ](#invocation-operator-)</span><span class="sxs-lookup"><span data-stu-id="feeaa-108">[`()` (invocation)](#invocation-operator-): to call an accessed method or invoke a delegate</span></span>
- <span data-ttu-id="feeaa-109">[(indeks od końca): wskazuje, że pozycja elementu jest z końca sekwencji `^` ](#index-from-end-operator-)</span><span class="sxs-lookup"><span data-stu-id="feeaa-109">[`^` (index from end)](#index-from-end-operator-): to indicate that the element position is from the end of a sequence</span></span>
- <span data-ttu-id="feeaa-110">(zakres): aby określić zakres indeksów, których można użyć w celu uzyskania zakresu elementów sekwencji [ `..` ](#range-operator-)</span><span class="sxs-lookup"><span data-stu-id="feeaa-110">[`..` (range)](#range-operator-): to specify a range of indices that you can use to obtain a range of sequence elements</span></span>

## <a name="member-access-operator-"></a><span data-ttu-id="feeaa-111">Operator dostępu do elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="feeaa-111">Member access operator .</span></span>

<span data-ttu-id="feeaa-112">`.` Token służy do uzyskiwania dostępu do składowej przestrzeni nazw lub typu, jak pokazano w poniższych przykładach:</span><span class="sxs-lookup"><span data-stu-id="feeaa-112">You use the `.` token to access a member of a namespace or a type, as the following examples demonstrate:</span></span>

- <span data-ttu-id="feeaa-113">Użyj `.` , aby uzyskać dostęp do zagnieżdżonej przestrzeni nazw w przestrzeni nazw, jak pokazano w poniższym przykładzie [ `using` dyrektywy](../keywords/using-directive.md) :</span><span class="sxs-lookup"><span data-stu-id="feeaa-113">Use `.` to access a nested namespace within a namespace, as the following example of a [`using` directive](../keywords/using-directive.md) shows:</span></span>

  [!code-csharp[nested namespaces](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#NestedNamespace)]

- <span data-ttu-id="feeaa-114">Użyj `.` , aby utworzyć *kwalifikowaną nazwę* do uzyskania dostępu do typu w przestrzeni nazw, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="feeaa-114">Use `.` to form a *qualified name* to access a type within a namespace, as the following code shows:</span></span>

  [!code-csharp[qualified name](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#QualifiedName)]

  <span data-ttu-id="feeaa-115">Użyj dyrektywy, aby użyć kwalifikujących się nazw jako opcjonalnych. [ `using` ](../keywords/using-directive.md)</span><span class="sxs-lookup"><span data-stu-id="feeaa-115">Use a [`using` directive](../keywords/using-directive.md) to make the use of qualified names optional.</span></span>

- <span data-ttu-id="feeaa-116">Służy `.` do uzyskiwania dostępu do [składowych typu](../../programming-guide/classes-and-structs/index.md#members)statycznego i niestatycznego, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="feeaa-116">Use `.` to access [type members](../../programming-guide/classes-and-structs/index.md#members), static and non-static, as the following code shows:</span></span>

  [!code-csharp-interactive[type members](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#TypeMemberAccess)]

<span data-ttu-id="feeaa-117">Można również użyć `.` , aby uzyskać dostęp do [metody rozszerzenia](../../programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="feeaa-117">You can also use `.` to access an [extension method](../../programming-guide/classes-and-structs/extension-methods.md).</span></span>

## <a name="indexer-operator-"></a><span data-ttu-id="feeaa-118">Indeksator — operator []</span><span class="sxs-lookup"><span data-stu-id="feeaa-118">Indexer operator []</span></span>

<span data-ttu-id="feeaa-119">Nawiasy kwadratowe, `[]`, są zwykle używane dla dostępu do elementu Array, indeksatora lub wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="feeaa-119">Square brackets, `[]`, are typically used for array, indexer, or pointer element access.</span></span>

### <a name="array-access"></a><span data-ttu-id="feeaa-120">Dostęp do tablicy</span><span class="sxs-lookup"><span data-stu-id="feeaa-120">Array access</span></span>

<span data-ttu-id="feeaa-121">W poniższym przykładzie pokazano, jak uzyskać dostęp do elementów tablicy:</span><span class="sxs-lookup"><span data-stu-id="feeaa-121">The following example demonstrates how to access array elements:</span></span>

[!code-csharp-interactive[array access](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Arrays)]

<span data-ttu-id="feeaa-122">Jeśli indeks tablicy znajduje się poza granicami odpowiedniego wymiaru tablicy, <xref:System.IndexOutOfRangeException> jest zgłaszany.</span><span class="sxs-lookup"><span data-stu-id="feeaa-122">If an array index is outside the bounds of the corresponding dimension of an array, an <xref:System.IndexOutOfRangeException> is thrown.</span></span>

<span data-ttu-id="feeaa-123">Jak pokazano w powyższym przykładzie, można również użyć nawiasów kwadratowych w przypadku deklarowania typu tablicy lub wystąpienia instancji Array.</span><span class="sxs-lookup"><span data-stu-id="feeaa-123">As the preceding example shows, you also use square brackets when you declare an array type or instantiate an array instance.</span></span>

<span data-ttu-id="feeaa-124">Aby uzyskać więcej informacji na temat tablic, zobacz [tablice](../../programming-guide/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="feeaa-124">For more information about arrays, see [Arrays](../../programming-guide/arrays/index.md).</span></span>

### <a name="indexer-access"></a><span data-ttu-id="feeaa-125">Dostęp indeksatora</span><span class="sxs-lookup"><span data-stu-id="feeaa-125">Indexer access</span></span>

<span data-ttu-id="feeaa-126">Poniższy przykład używa typu .NET <xref:System.Collections.Generic.Dictionary%602> do zademonstrowania dostępu indeksatora:</span><span class="sxs-lookup"><span data-stu-id="feeaa-126">The following example uses .NET <xref:System.Collections.Generic.Dictionary%602> type to demonstrate indexer access:</span></span>

[!code-csharp-interactive[indexer access](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Indexers)]

<span data-ttu-id="feeaa-127">Indeksatory umożliwiają indeksowanie wystąpień typu zdefiniowanego przez użytkownika w podobny sposób jak indeksowanie tablicy.</span><span class="sxs-lookup"><span data-stu-id="feeaa-127">Indexers allow you to index instances of a user-defined type in the similar way as array indexing.</span></span> <span data-ttu-id="feeaa-128">W przeciwieństwie do indeksów tablicowych, które muszą być liczbami całkowitymi, argumenty indeksatora mogą być zadeklarowane jako dowolnego typu.</span><span class="sxs-lookup"><span data-stu-id="feeaa-128">Unlike array indices, which must be integer, the indexer arguments can be declared to be of any type.</span></span>

<span data-ttu-id="feeaa-129">Aby uzyskać więcej informacji na temat indeksatorów, zobacz [indeksatory](../../programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="feeaa-129">For more information about indexers, see [Indexers](../../programming-guide/indexers/index.md).</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="feeaa-130">Inne użycie []</span><span class="sxs-lookup"><span data-stu-id="feeaa-130">Other usages of []</span></span>

<span data-ttu-id="feeaa-131">Aby uzyskać informacje o dostępie do elementów wskaźnika, zobacz sekcję [wskaźnik dostępu do elementu wskaźnika []](pointer-related-operators.md#pointer-element-access-operator-) w artykule [Operatory pokrewne wskaźnika](pointer-related-operators.md) .</span><span class="sxs-lookup"><span data-stu-id="feeaa-131">For information about pointer element access, see the [Pointer element access operator []](pointer-related-operators.md#pointer-element-access-operator-) section of the [Pointer related operators](pointer-related-operators.md) article.</span></span>

<span data-ttu-id="feeaa-132">Aby określić [atrybuty](../../programming-guide/concepts/attributes/index.md), należy również użyć nawiasów kwadratowych:</span><span class="sxs-lookup"><span data-stu-id="feeaa-132">You also use square brackets to specify [attributes](../../programming-guide/concepts/attributes/index.md):</span></span>

```csharp
[System.Diagnostics.Conditional("DEBUG")]
void TraceMethod() {}
```

## <a name="null-conditional-operators--and-"></a><span data-ttu-id="feeaa-133">Operatory warunkowe o wartości null?.</span><span class="sxs-lookup"><span data-stu-id="feeaa-133">Null-conditional operators ?.</span></span> <span data-ttu-id="feeaa-134">lub? []</span><span class="sxs-lookup"><span data-stu-id="feeaa-134">and ?[]</span></span>

<span data-ttu-id="feeaa-135">Operator warunkowy, który jest dostępny w C# wartości 6 i nowszych, ma zastosowanie do `?.`elementu członkowskiego, lub `?[]`dostępu do elementów, operacji do jego operandu tylko wtedy, gdy ten operand ma wartość różną od null.</span><span class="sxs-lookup"><span data-stu-id="feeaa-135">Available in C# 6 and later, a null-conditional operator applies a member access, `?.`, or element access, `?[]`, operation to its operand only if that operand evaluates to non-null.</span></span> <span data-ttu-id="feeaa-136">Jeśli argument ma wartość `null`, wynik zastosowania operatora to. `null`</span><span class="sxs-lookup"><span data-stu-id="feeaa-136">If the operand evaluates to `null`, the result of applying the operator is `null`.</span></span> <span data-ttu-id="feeaa-137">Operator `?.` dostępu warunkowego o wartości null jest również znany jako operator Elvis.</span><span class="sxs-lookup"><span data-stu-id="feeaa-137">The null-conditional member access operator `?.` is also known as the Elvis operator.</span></span>

<span data-ttu-id="feeaa-138">Operatory warunkowe `null` skracają łańcuch wykonywania operacji.</span><span class="sxs-lookup"><span data-stu-id="feeaa-138">The null-conditional operators are short-circuiting.</span></span> <span data-ttu-id="feeaa-139">Oznacza to, że jeśli jedna operacja w łańcuchu operacji warunkowego elementu członkowskiego lub `null`dostępu do elementu zwraca, reszta łańcucha nie jest wykonywana.</span><span class="sxs-lookup"><span data-stu-id="feeaa-139">That is, if one operation in a chain of conditional member or element access operations returns `null`, the rest of the chain doesn't execute.</span></span> <span data-ttu-id="feeaa-140">W poniższym przykładzie nie jest `B` oceniana, jeśli `A` jest obliczana wartość `null` i `C` nie jest szacowana, `A` Jeśli `B` lub szacuje `null`:</span><span class="sxs-lookup"><span data-stu-id="feeaa-140">In the following example, `B` is not evaluated if `A` evaluates to `null` and `C` is not evaluated if `A` or `B` evaluates to `null`:</span></span>

```csharp
A?.B?.Do(C);
A?.B?[C];
```

<span data-ttu-id="feeaa-141">Poniższy przykład ilustruje użycie `?.` operatorów i: `?[]`</span><span class="sxs-lookup"><span data-stu-id="feeaa-141">The following example demonstrates the usage of the `?.` and `?[]` operators:</span></span>

[!code-csharp-interactive[null-conditional operators](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#NullConditional)]

<span data-ttu-id="feeaa-142">W poprzednim przykładzie pokazano także użycie [operatora łączenia wartości null](null-coalescing-operator.md).</span><span class="sxs-lookup"><span data-stu-id="feeaa-142">The preceding example also shows the usage of the [null-coalescing operator](null-coalescing-operator.md).</span></span> <span data-ttu-id="feeaa-143">Możesz użyć operatora łączenia wartości null, aby podać alternatywne wyrażenie do obliczenia w przypadku, gdy wynikiem operacji warunkowej jest `null`wartość null.</span><span class="sxs-lookup"><span data-stu-id="feeaa-143">You might use the null-coalescing operator to provide an alternative expression to evaluate in case the result of the null-conditional operation is `null`.</span></span>

### <a name="thread-safe-delegate-invocation"></a><span data-ttu-id="feeaa-144">Wywołanie delegowania bezpiecznego wątku</span><span class="sxs-lookup"><span data-stu-id="feeaa-144">Thread-safe delegate invocation</span></span>

<span data-ttu-id="feeaa-145">Użyj operatora `?.` , aby sprawdzić, czy delegat ma wartość różną od null i wywołać go w sposób bezpieczny dla wątków (na przykład po [podniesieniu zdarzenia](../../../standard/events/how-to-raise-and-consume-events.md)), jak poniższy kod ilustruje:</span><span class="sxs-lookup"><span data-stu-id="feeaa-145">Use the `?.` operator to check if a delegate is non-null and invoke it in a thread-safe way (for example, when you [raise an event](../../../standard/events/how-to-raise-and-consume-events.md)), as the following code shows:</span></span>

```csharp
PropertyChanged?.Invoke(…)
```

<span data-ttu-id="feeaa-146">Ten kod jest odpowiednikiem poniższego kodu, który będzie używany w C# 5 lub wcześniejszych wersjach:</span><span class="sxs-lookup"><span data-stu-id="feeaa-146">That code is equivalent to the following code that you would use in C# 5 or earlier:</span></span>

```csharp
var handler = this.PropertyChanged;
if (handler != null)
{
    handler(…);
}
```

## <a name="invocation-operator-"></a><span data-ttu-id="feeaa-147">Operator wywołania ()</span><span class="sxs-lookup"><span data-stu-id="feeaa-147">Invocation operator ()</span></span>

<span data-ttu-id="feeaa-148">Użyj nawiasów, `()`,, aby wywołać [metodę](../../programming-guide/classes-and-structs/methods.md) lub wywołać [delegata](../../programming-guide/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="feeaa-148">Use parentheses, `()`, to call a [method](../../programming-guide/classes-and-structs/methods.md) or invoke a [delegate](../../programming-guide/delegates/index.md).</span></span>

<span data-ttu-id="feeaa-149">Poniższy przykład ilustruje sposób wywołania metody z argumentami lub bez nich i Wywołaj delegata:</span><span class="sxs-lookup"><span data-stu-id="feeaa-149">The following example demonstrates how to call a method, with or without arguments, and invoke a delegate:</span></span>

[!code-csharp-interactive[invocation with ()](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Invocation)]

<span data-ttu-id="feeaa-150">Po wywołaniu [konstruktora](../../programming-guide/classes-and-structs/constructors.md) za pomocą [`new`](new-operator.md) operatora należy również użyć nawiasów.</span><span class="sxs-lookup"><span data-stu-id="feeaa-150">You also use parentheses when you invoke a [constructor](../../programming-guide/classes-and-structs/constructors.md) with the [`new`](new-operator.md) operator.</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="feeaa-151">Inne użycie ()</span><span class="sxs-lookup"><span data-stu-id="feeaa-151">Other usages of ()</span></span>

<span data-ttu-id="feeaa-152">Należy również użyć nawiasów, aby dostosować kolejność, w której mają być oceniane operacje w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="feeaa-152">You also use parentheses to adjust the order in which to evaluate operations in an expression.</span></span> <span data-ttu-id="feeaa-153">Aby uzyskać więcej informacji, zobacz [ C# operatory](index.md).</span><span class="sxs-lookup"><span data-stu-id="feeaa-153">For more information, see [C# operators](index.md).</span></span>

<span data-ttu-id="feeaa-154">[Wyrażenia rzutowania](type-testing-and-cast.md#cast-operator-), które wykonują jawne konwersje typów, również używają nawiasów.</span><span class="sxs-lookup"><span data-stu-id="feeaa-154">[Cast expressions](type-testing-and-cast.md#cast-operator-), which perform explicit type conversions, also use parentheses.</span></span>

## <a name="index-from-end-operator-"></a><span data-ttu-id="feeaa-155">Indeks z operatora końcowego ^</span><span class="sxs-lookup"><span data-stu-id="feeaa-155">Index from end operator ^</span></span>

<span data-ttu-id="feeaa-156">Dostępne w C# 8,0 i nowszych, `^` operator wskazuje położenie elementu od końca sekwencji.</span><span class="sxs-lookup"><span data-stu-id="feeaa-156">Available in C# 8.0 and later, the `^` operator indicates the element position from the end of a sequence.</span></span> <span data-ttu-id="feeaa-157">Dla sekwencji o długości `length` `^n` wskazuje element z przesunięciem `length - n` od początku sekwencji.</span><span class="sxs-lookup"><span data-stu-id="feeaa-157">For a sequence of length `length`, `^n` points to the element with offset `length - n` from the start of a sequence.</span></span> <span data-ttu-id="feeaa-158">Na przykład `^1` wskazuje ostatni element sekwencji i `^length` wskazuje na pierwszy element sekwencji.</span><span class="sxs-lookup"><span data-stu-id="feeaa-158">For example, `^1` points to the last element of a sequence and `^length` points to the first element of a sequence.</span></span>

[!code-csharp[index from end](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#IndexFromEnd)]

<span data-ttu-id="feeaa-159">Jak pokazano w powyższym przykładzie `^e` , wyrażenie jest <xref:System.Index?displayProperty=nameWithType> typu.</span><span class="sxs-lookup"><span data-stu-id="feeaa-159">As the preceding example shows, expression `^e` is of the <xref:System.Index?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="feeaa-160">W wyrażeniu `^e` `e` wynik musi być niejawnie konwertowany na `int`.</span><span class="sxs-lookup"><span data-stu-id="feeaa-160">In expression `^e`, the result of `e` must be implicitly convertible to `int`.</span></span>

<span data-ttu-id="feeaa-161">Można też użyć `^` operatora z [operatorem zakresu](#range-operator-) , aby utworzyć zakres indeksów.</span><span class="sxs-lookup"><span data-stu-id="feeaa-161">You also can use the `^` operator with the [range operator](#range-operator-) to create a range of indices.</span></span> <span data-ttu-id="feeaa-162">Aby uzyskać więcej informacji, zobacz [indeksy i zakresy](../../tutorials/ranges-indexes.md).</span><span class="sxs-lookup"><span data-stu-id="feeaa-162">For more information, see [Indices and ranges](../../tutorials/ranges-indexes.md).</span></span>

## <a name="range-operator-"></a><span data-ttu-id="feeaa-163">Operator zakresu..</span><span class="sxs-lookup"><span data-stu-id="feeaa-163">Range operator ..</span></span>

<span data-ttu-id="feeaa-164">Dostępne w C# 8,0 i nowszych, `..` operator określa początek i koniec zakresu indeksów jako operandy.</span><span class="sxs-lookup"><span data-stu-id="feeaa-164">Available in C# 8.0 and later, the `..` operator specifies the start and end of a range of indices as its operands.</span></span> <span data-ttu-id="feeaa-165">Argument operacji po lewej stronie *jest początkową* częścią zakresu.</span><span class="sxs-lookup"><span data-stu-id="feeaa-165">The left-hand operand is an *inclusive* start of a range.</span></span> <span data-ttu-id="feeaa-166">Prawy operand jest *wyłącznym* końcem zakresu.</span><span class="sxs-lookup"><span data-stu-id="feeaa-166">The right-hand operand is an *exclusive* end of a range.</span></span> <span data-ttu-id="feeaa-167">Jeden z operandów może być indeksem od początku lub od końca sekwencji, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="feeaa-167">Either of operands can be an index from the start or from the end of a sequence, as the following example shows:</span></span>

[!code-csharp[range examples](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Ranges)]

<span data-ttu-id="feeaa-168">Jak pokazano w powyższym przykładzie `a..b` , wyrażenie jest <xref:System.Range?displayProperty=nameWithType> typu.</span><span class="sxs-lookup"><span data-stu-id="feeaa-168">As the preceding example shows, expression `a..b` is of the <xref:System.Range?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="feeaa-169">W wyrażeniu `a..b` `a` wyniki i `b` muszą być niejawnie konwertowane na `int` lub <xref:System.Index>.</span><span class="sxs-lookup"><span data-stu-id="feeaa-169">In expression `a..b`, the results of `a` and `b` must be implicitly convertible to `int` or <xref:System.Index>.</span></span>

<span data-ttu-id="feeaa-170">Możesz pominąć dowolny operand `..` operatora, aby uzyskać otwarty zakres:</span><span class="sxs-lookup"><span data-stu-id="feeaa-170">You can omit any of the operands of the `..` operator to obtain an open-ended range:</span></span>

- <span data-ttu-id="feeaa-171">`a..`jest równoważne`a..^0`</span><span class="sxs-lookup"><span data-stu-id="feeaa-171">`a..` is equivalent to `a..^0`</span></span>
- <span data-ttu-id="feeaa-172">`..b`jest równoważne`0..b`</span><span class="sxs-lookup"><span data-stu-id="feeaa-172">`..b` is equivalent to `0..b`</span></span>
- <span data-ttu-id="feeaa-173">`..`jest równoważne`0..^0`</span><span class="sxs-lookup"><span data-stu-id="feeaa-173">`..` is equivalent to `0..^0`</span></span>

[!code-csharp[ranges with omitted operands](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#RangesOptional)]

<span data-ttu-id="feeaa-174">Aby uzyskać więcej informacji, zobacz [indeksy i zakresy](../../tutorials/ranges-indexes.md).</span><span class="sxs-lookup"><span data-stu-id="feeaa-174">For more information, see [Indices and ranges](../../tutorials/ranges-indexes.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="feeaa-175">Przeciążanie operatora</span><span class="sxs-lookup"><span data-stu-id="feeaa-175">Operator overloadability</span></span>

<span data-ttu-id="feeaa-176">Operatory `.`, `()`, `^`i niemogąbyćprzeciążone.`..`</span><span class="sxs-lookup"><span data-stu-id="feeaa-176">The `.`, `()`, `^`, and `..` operators cannot be overloaded.</span></span> <span data-ttu-id="feeaa-177">`[]` Operator jest również traktowany jako operator niepodlegający obciążeniu.</span><span class="sxs-lookup"><span data-stu-id="feeaa-177">The `[]` operator is also considered a non-overloadable operator.</span></span> <span data-ttu-id="feeaa-178">Używanie [indeksatorów](../../programming-guide/indexers/index.md) do obsługi indeksowania z typami zdefiniowanymi przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="feeaa-178">Use [indexers](../../programming-guide/indexers/index.md) to support indexing with user-defined types.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="feeaa-179">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="feeaa-179">C# language specification</span></span>

<span data-ttu-id="feeaa-180">Aby uzyskać więcej informacji, zobacz następujące sekcje [ C# specyfikacji języka](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="feeaa-180">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="feeaa-181">Dostęp do elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="feeaa-181">Member access</span></span>](~/_csharplang/spec/expressions.md#member-access)
- [<span data-ttu-id="feeaa-182">Dostęp do elementu</span><span class="sxs-lookup"><span data-stu-id="feeaa-182">Element access</span></span>](~/_csharplang/spec/expressions.md#element-access)
- [<span data-ttu-id="feeaa-183">Operator warunkowy o wartości null</span><span class="sxs-lookup"><span data-stu-id="feeaa-183">Null-conditional operator</span></span>](~/_csharplang/spec/expressions.md#null-conditional-operator)
- [<span data-ttu-id="feeaa-184">Wyrażenia wywołania</span><span class="sxs-lookup"><span data-stu-id="feeaa-184">Invocation expressions</span></span>](~/_csharplang/spec/expressions.md#invocation-expressions)

## <a name="see-also"></a><span data-ttu-id="feeaa-185">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="feeaa-185">See also</span></span>

- [<span data-ttu-id="feeaa-186">C#odwoła</span><span class="sxs-lookup"><span data-stu-id="feeaa-186">C# reference</span></span>](../index.md)
- [<span data-ttu-id="feeaa-187">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="feeaa-187">C# operators</span></span>](index.md)
- [<span data-ttu-id="feeaa-188">?? (operator łączenia wartości null)</span><span class="sxs-lookup"><span data-stu-id="feeaa-188">?? (null-coalescing operator)</span></span>](null-coalescing-operator.md)
- [<span data-ttu-id="feeaa-189">:: operator</span><span class="sxs-lookup"><span data-stu-id="feeaa-189">:: operator</span></span>](namespace-alias-qualifier.md)
