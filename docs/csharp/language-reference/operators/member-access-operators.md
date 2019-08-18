---
title: Operatory dostępu do elementów C# członkowskich — odwołanie
description: Dowiedz C# się więcej na temat operatorów, których można użyć w celu uzyskania dostępu do elementów członkowskich typu.
ms.date: 05/09/2019
author: pkulikov
f1_keywords:
- ._CSharpKeyword
- '[]_CSharpKeyword'
- ()_CSharpKeyword
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
ms.openlocfilehash: 763fdb442fa0037dafd51f89badd04436e24d254
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/17/2019
ms.locfileid: "69566832"
---
# <a name="member-access-operators-c-reference"></a><span data-ttu-id="690c4-103">Operatory dostępu do elementówC# członkowskich (odwołanie)</span><span class="sxs-lookup"><span data-stu-id="690c4-103">Member access operators (C# reference)</span></span>

<span data-ttu-id="690c4-104">Podczas uzyskiwania dostępu do elementu członkowskiego typu mogą być używane następujące operatory:</span><span class="sxs-lookup"><span data-stu-id="690c4-104">You might use the following operators when you access a type member:</span></span>

- <span data-ttu-id="690c4-105">[(dostęp do elementu członkowskiego): Aby uzyskać dostęp do elementu członkowskiego przestrzeni nazw lub typu `.` ](#member-access-operator-)</span><span class="sxs-lookup"><span data-stu-id="690c4-105">[`.` (member access)](#member-access-operator-): to access a member of a namespace or a type</span></span>
- <span data-ttu-id="690c4-106">[(dostęp do elementu tablicy lub indeksatora): Aby uzyskać dostęp do elementu tablicy lub indeksatora typu `[]` ](#indexer-operator-)</span><span class="sxs-lookup"><span data-stu-id="690c4-106">[`[]` (array element or indexer access)](#indexer-operator-): to access an array element or a type indexer</span></span>
- <span data-ttu-id="690c4-107">[and (operatory warunkowe o wartości null): do wykonywania operacji dostępu do elementu członkowskiego lub elementów tylko wtedy, gdy operand ma wartość różną od null `?[]` `?.` ](#null-conditional-operators--and-)</span><span class="sxs-lookup"><span data-stu-id="690c4-107">[`?.` and `?[]` (null-conditional operators)](#null-conditional-operators--and-): to perform a member or element access operation only if an operand is non-null</span></span>
- <span data-ttu-id="690c4-108">(wywołanie): aby wywołać metodę dostępu lub wywołać delegata [ `()` ](#invocation-operator-)</span><span class="sxs-lookup"><span data-stu-id="690c4-108">[`()` (invocation)](#invocation-operator-): to call an accessed method or invoke a delegate</span></span>

## <a name="member-access-operator-"></a><span data-ttu-id="690c4-109">Operator dostępu do elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="690c4-109">Member access operator .</span></span>

<span data-ttu-id="690c4-110">`.` Token służy do uzyskiwania dostępu do składowej przestrzeni nazw lub typu, jak pokazano w poniższych przykładach:</span><span class="sxs-lookup"><span data-stu-id="690c4-110">You use the `.` token to access a member of a namespace or a type, as the following examples demonstrate:</span></span>

- <span data-ttu-id="690c4-111">Użyj `.` , aby uzyskać dostęp do zagnieżdżonej przestrzeni nazw w przestrzeni nazw, jak pokazano w poniższym przykładzie [ `using` dyrektywy](../keywords/using-directive.md) :</span><span class="sxs-lookup"><span data-stu-id="690c4-111">Use `.` to access a nested namespace within a namespace, as the following example of a [`using` directive](../keywords/using-directive.md) shows:</span></span>

  [!code-csharp[nested namespaces](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#NestedNamespace)]

- <span data-ttu-id="690c4-112">Użyj `.` , aby utworzyć *kwalifikowaną nazwę* do uzyskania dostępu do typu w przestrzeni nazw, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="690c4-112">Use `.` to form a *qualified name* to access a type within a namespace, as the following code shows:</span></span>

  [!code-csharp[qualified name](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#QualifiedName)]

  <span data-ttu-id="690c4-113">Użyj dyrektywy, aby użyć kwalifikujących się nazw jako opcjonalnych. [ `using` ](../keywords/using-directive.md)</span><span class="sxs-lookup"><span data-stu-id="690c4-113">Use a [`using` directive](../keywords/using-directive.md) to make the use of qualified names optional.</span></span>

- <span data-ttu-id="690c4-114">Służy `.` do uzyskiwania dostępu do [składowych typu](../../programming-guide/classes-and-structs/index.md#members)statycznego i niestatycznego, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="690c4-114">Use `.` to access [type members](../../programming-guide/classes-and-structs/index.md#members), static and non-static, as the following code shows:</span></span>

  [!code-csharp-interactive[type members](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#TypeMemberAccess)]

<span data-ttu-id="690c4-115">Można również użyć `.` , aby uzyskać dostęp do [metody rozszerzenia](../../programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="690c4-115">You can also use `.` to access an [extension method](../../programming-guide/classes-and-structs/extension-methods.md).</span></span>

## <a name="indexer-operator-"></a><span data-ttu-id="690c4-116">Indeksator — operator []</span><span class="sxs-lookup"><span data-stu-id="690c4-116">Indexer operator []</span></span>

<span data-ttu-id="690c4-117">Nawiasy kwadratowe, `[]`, są zwykle używane dla dostępu do elementu Array, indeksatora lub wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="690c4-117">Square brackets, `[]`, are typically used for array, indexer, or pointer element access.</span></span>

### <a name="array-access"></a><span data-ttu-id="690c4-118">Dostęp do tablicy</span><span class="sxs-lookup"><span data-stu-id="690c4-118">Array access</span></span>

<span data-ttu-id="690c4-119">W poniższym przykładzie pokazano, jak uzyskać dostęp do elementów tablicy:</span><span class="sxs-lookup"><span data-stu-id="690c4-119">The following example demonstrates how to access array elements:</span></span>

[!code-csharp-interactive[array access](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Arrays)]

<span data-ttu-id="690c4-120">Jeśli indeks tablicy znajduje się poza granicami odpowiedniego wymiaru tablicy, <xref:System.IndexOutOfRangeException> jest zgłaszany.</span><span class="sxs-lookup"><span data-stu-id="690c4-120">If an array index is outside the bounds of the corresponding dimension of an array, an <xref:System.IndexOutOfRangeException> is thrown.</span></span>

<span data-ttu-id="690c4-121">Jak pokazano w powyższym przykładzie, można również użyć nawiasów kwadratowych w przypadku deklarowania typu tablicy lub wystąpienia instancji Array.</span><span class="sxs-lookup"><span data-stu-id="690c4-121">As the preceding example shows, you also use square brackets when you declare an array type or instantiate an array instance.</span></span>

<span data-ttu-id="690c4-122">Aby uzyskać więcej informacji na temat tablic, zobacz [tablice](../../programming-guide/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="690c4-122">For more information about arrays, see [Arrays](../../programming-guide/arrays/index.md).</span></span>

### <a name="indexer-access"></a><span data-ttu-id="690c4-123">Dostęp indeksatora</span><span class="sxs-lookup"><span data-stu-id="690c4-123">Indexer access</span></span>

<span data-ttu-id="690c4-124">Poniższy przykład używa typu .NET <xref:System.Collections.Generic.Dictionary%602> do zademonstrowania dostępu indeksatora:</span><span class="sxs-lookup"><span data-stu-id="690c4-124">The following example uses .NET <xref:System.Collections.Generic.Dictionary%602> type to demonstrate indexer access:</span></span>

[!code-csharp-interactive[indexer access](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Indexers)]

<span data-ttu-id="690c4-125">Indeksatory umożliwiają indeksowanie wystąpień typu zdefiniowanego przez użytkownika w podobny sposób jak indeksowanie tablicy.</span><span class="sxs-lookup"><span data-stu-id="690c4-125">Indexers allow you to index instances of a user-defined type in the similar way as array indexing.</span></span> <span data-ttu-id="690c4-126">W przeciwieństwie do indeksów tablicowych, które muszą być liczbami całkowitymi, argumenty indeksatora mogą być zadeklarowane jako dowolnego typu.</span><span class="sxs-lookup"><span data-stu-id="690c4-126">Unlike array indices, which must be integer, the indexer arguments can be declared to be of any type.</span></span>

<span data-ttu-id="690c4-127">Aby uzyskać więcej informacji na temat indeksatorów [](../../programming-guide/indexers/index.md), zobacz indeksatory.</span><span class="sxs-lookup"><span data-stu-id="690c4-127">For more information about indexers, see [Indexers](../../programming-guide/indexers/index.md).</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="690c4-128">Inne użycie []</span><span class="sxs-lookup"><span data-stu-id="690c4-128">Other usages of []</span></span>

<span data-ttu-id="690c4-129">Aby uzyskać informacje o dostępie do elementów wskaźnika, zobacz sekcję [wskaźnik dostępu do elementu wskaźnika []](pointer-related-operators.md#pointer-element-access-operator-) w artykule [Operatory pokrewne wskaźnika](pointer-related-operators.md) .</span><span class="sxs-lookup"><span data-stu-id="690c4-129">For information about pointer element access, see the [Pointer element access operator []](pointer-related-operators.md#pointer-element-access-operator-) section of the [Pointer related operators](pointer-related-operators.md) article.</span></span>

<span data-ttu-id="690c4-130">Aby określić [atrybuty](../../programming-guide/concepts/attributes/index.md), należy również użyć nawiasów kwadratowych:</span><span class="sxs-lookup"><span data-stu-id="690c4-130">You also use square brackets to specify [attributes](../../programming-guide/concepts/attributes/index.md):</span></span>

```csharp
[System.Diagnostics.Conditional("DEBUG")]
void TraceMethod() {}
```

## <a name="null-conditional-operators--and-"></a><span data-ttu-id="690c4-131">Operatory warunkowe o wartości null?.</span><span class="sxs-lookup"><span data-stu-id="690c4-131">Null-conditional operators ?.</span></span> <span data-ttu-id="690c4-132">lub? []</span><span class="sxs-lookup"><span data-stu-id="690c4-132">and ?[]</span></span>

<span data-ttu-id="690c4-133">Operator warunkowy, który jest dostępny w C# wartości 6 i nowszych, ma zastosowanie do `?.`elementu członkowskiego, lub `?[]`dostępu do elementów, operacji do jego operandu tylko wtedy, gdy ten operand ma wartość różną od null.</span><span class="sxs-lookup"><span data-stu-id="690c4-133">Available in C# 6 and later, a null-conditional operator applies a member access, `?.`, or element access, `?[]`, operation to its operand only if that operand evaluates to non-null.</span></span> <span data-ttu-id="690c4-134">Jeśli argument ma wartość `null`, wynik zastosowania operatora to. `null`</span><span class="sxs-lookup"><span data-stu-id="690c4-134">If the operand evaluates to `null`, the result of applying the operator is `null`.</span></span> <span data-ttu-id="690c4-135">Operator `?.` dostępu warunkowego o wartości null jest również znany jako operator Elvis.</span><span class="sxs-lookup"><span data-stu-id="690c4-135">The null-conditional member access operator `?.` is also known as the Elvis operator.</span></span>

<span data-ttu-id="690c4-136">Operatory warunkowe `null` skracają łańcuch wykonywania operacji.</span><span class="sxs-lookup"><span data-stu-id="690c4-136">The null-conditional operators are short-circuiting.</span></span> <span data-ttu-id="690c4-137">Oznacza to, że jeśli jedna operacja w łańcuchu operacji warunkowego elementu członkowskiego lub `null`dostępu do elementu zwraca, reszta łańcucha nie jest wykonywana.</span><span class="sxs-lookup"><span data-stu-id="690c4-137">That is, if one operation in a chain of conditional member or element access operations returns `null`, the rest of the chain doesn't execute.</span></span> <span data-ttu-id="690c4-138">W poniższym przykładzie nie jest `B` oceniana, jeśli `A` jest obliczana wartość `null` i `C` nie jest szacowana, `A` Jeśli `B` lub szacuje `null`:</span><span class="sxs-lookup"><span data-stu-id="690c4-138">In the following example, `B` is not evaluated if `A` evaluates to `null` and `C` is not evaluated if `A` or `B` evaluates to `null`:</span></span>

```csharp
A?.B?.Do(C);
A?.B?[C];
```

<span data-ttu-id="690c4-139">Poniższy przykład ilustruje użycie `?.` operatorów i: `?[]`</span><span class="sxs-lookup"><span data-stu-id="690c4-139">The following example demonstrates the usage of the `?.` and `?[]` operators:</span></span>

[!code-csharp-interactive[null-conditional operators](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#NullConditional)]

<span data-ttu-id="690c4-140">W poprzednim przykładzie pokazano także użycie [operatora łączenia wartości null](null-coalescing-operator.md).</span><span class="sxs-lookup"><span data-stu-id="690c4-140">The preceding example also shows the usage of the [null-coalescing operator](null-coalescing-operator.md).</span></span> <span data-ttu-id="690c4-141">Możesz użyć operatora łączenia wartości null, aby podać alternatywne wyrażenie do obliczenia w przypadku, gdy wynikiem operacji warunkowej jest `null`wartość null.</span><span class="sxs-lookup"><span data-stu-id="690c4-141">You might use the null-coalescing operator to provide an alternative expression to evaluate in case the result of the null-conditional operation is `null`.</span></span>

### <a name="thread-safe-delegate-invocation"></a><span data-ttu-id="690c4-142">Wywołanie delegowania bezpiecznego wątku</span><span class="sxs-lookup"><span data-stu-id="690c4-142">Thread-safe delegate invocation</span></span>

<span data-ttu-id="690c4-143">Użyj operatora `?.` , aby sprawdzić, czy delegat ma wartość różną od null i wywołać go w sposób bezpieczny dla wątków (na przykład po podniesieniu [zdarzenia](../../../standard/events/how-to-raise-and-consume-events.md)), jak poniższy kod ilustruje:</span><span class="sxs-lookup"><span data-stu-id="690c4-143">Use the `?.` operator to check if a delegate is non-null and invoke it in a thread-safe way (for example, when you [raise an event](../../../standard/events/how-to-raise-and-consume-events.md)), as the following code shows:</span></span>

```csharp
PropertyChanged?.Invoke(…)
```

<span data-ttu-id="690c4-144">Ten kod jest odpowiednikiem poniższego kodu, który będzie używany w C# 5 lub wcześniejszych wersjach:</span><span class="sxs-lookup"><span data-stu-id="690c4-144">That code is equivalent to the following code that you would use in C# 5 or earlier:</span></span>

```csharp
var handler = this.PropertyChanged;
if (handler != null)
{
    handler(…);
}
```

## <a name="invocation-operator-"></a><span data-ttu-id="690c4-145">Operator wywołania ()</span><span class="sxs-lookup"><span data-stu-id="690c4-145">Invocation operator ()</span></span>

<span data-ttu-id="690c4-146">Użyj nawiasów, `()`,, aby wywołać [metodę](../../programming-guide/classes-and-structs/methods.md) lub wywołać [delegata](../../programming-guide/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="690c4-146">Use parentheses, `()`, to call a [method](../../programming-guide/classes-and-structs/methods.md) or invoke a [delegate](../../programming-guide/delegates/index.md).</span></span>

<span data-ttu-id="690c4-147">Poniższy przykład ilustruje sposób wywołania metody z argumentami lub bez nich i Wywołaj delegata:</span><span class="sxs-lookup"><span data-stu-id="690c4-147">The following example demonstrates how to call a method, with or without arguments, and invoke a delegate:</span></span>

[!code-csharp-interactive[invocation with ()](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Invocation)]

<span data-ttu-id="690c4-148">Po wywołaniu [konstruktora](../../programming-guide/classes-and-structs/constructors.md) za pomocą [`new`](new-operator.md) operatora należy również użyć nawiasów.</span><span class="sxs-lookup"><span data-stu-id="690c4-148">You also use parentheses when you invoke a [constructor](../../programming-guide/classes-and-structs/constructors.md) with the [`new`](new-operator.md) operator.</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="690c4-149">Inne użycie ()</span><span class="sxs-lookup"><span data-stu-id="690c4-149">Other usages of ()</span></span>

<span data-ttu-id="690c4-150">Należy również użyć nawiasów, aby określić kolejność, w której mają być oceniane operacje w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="690c4-150">You also use parentheses to specify the order in which to evaluate operations in an expression.</span></span> <span data-ttu-id="690c4-151">Aby uzyskać więcej informacji, zobacz sekcję [Dodawanie nawiasów](../../programming-guide/statements-expressions-operators/operators.md#adding-parentheses) w artykule [operatorzy](../../programming-guide/statements-expressions-operators/operators.md) .</span><span class="sxs-lookup"><span data-stu-id="690c4-151">For more information, see the [Adding parentheses](../../programming-guide/statements-expressions-operators/operators.md#adding-parentheses) section of the [Operators](../../programming-guide/statements-expressions-operators/operators.md) article.</span></span> <span data-ttu-id="690c4-152">Aby uzyskać listę operatorów uporządkowanych według poziomu pierwszeństwa, zobacz [ C# operatory](index.md).</span><span class="sxs-lookup"><span data-stu-id="690c4-152">For the list of operators ordered by precedence level, see [C# operators](index.md).</span></span>

<span data-ttu-id="690c4-153">[Wyrażenia rzutowania](type-testing-and-cast.md#cast-operator-), które wykonują jawne konwersje typów, również używają nawiasów.</span><span class="sxs-lookup"><span data-stu-id="690c4-153">[Cast expressions](type-testing-and-cast.md#cast-operator-), which perform explicit type conversions, also use parentheses.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="690c4-154">Przeciążanie operatora</span><span class="sxs-lookup"><span data-stu-id="690c4-154">Operator overloadability</span></span>

<span data-ttu-id="690c4-155">Operatory `.` i`()` nie mogą być przeciążone.</span><span class="sxs-lookup"><span data-stu-id="690c4-155">The `.` and `()` operators cannot be overloaded.</span></span> <span data-ttu-id="690c4-156">`[]` Operator jest również traktowany jako operator niepodlegający obciążeniu.</span><span class="sxs-lookup"><span data-stu-id="690c4-156">The `[]` operator is also considered a non-overloadable operator.</span></span> <span data-ttu-id="690c4-157">Używanie [indeksatorów](../../programming-guide/indexers/index.md) do obsługi indeksowania z typami zdefiniowanymi przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="690c4-157">Use [indexers](../../programming-guide/indexers/index.md) to support indexing with user-defined types.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="690c4-158">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="690c4-158">C# language specification</span></span>

<span data-ttu-id="690c4-159">Aby uzyskać więcej informacji, zobacz następujące sekcje [ C# specyfikacji języka](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="690c4-159">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="690c4-160">Dostęp do elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="690c4-160">Member access</span></span>](~/_csharplang/spec/expressions.md#member-access)
- [<span data-ttu-id="690c4-161">Dostęp do elementu</span><span class="sxs-lookup"><span data-stu-id="690c4-161">Element access</span></span>](~/_csharplang/spec/expressions.md#element-access)
- [<span data-ttu-id="690c4-162">Operator warunkowy o wartości null</span><span class="sxs-lookup"><span data-stu-id="690c4-162">Null-conditional operator</span></span>](~/_csharplang/spec/expressions.md#null-conditional-operator)
- [<span data-ttu-id="690c4-163">Wyrażenia wywołania</span><span class="sxs-lookup"><span data-stu-id="690c4-163">Invocation expressions</span></span>](~/_csharplang/spec/expressions.md#invocation-expressions)

## <a name="see-also"></a><span data-ttu-id="690c4-164">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="690c4-164">See also</span></span>

- [<span data-ttu-id="690c4-165">C#odwoła</span><span class="sxs-lookup"><span data-stu-id="690c4-165">C# reference</span></span>](../index.md)
- [<span data-ttu-id="690c4-166">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="690c4-166">C# operators</span></span>](index.md)
- [<span data-ttu-id="690c4-167">?? (operator łączenia wartości null)</span><span class="sxs-lookup"><span data-stu-id="690c4-167">?? (null-coalescing operator)</span></span>](null-coalescing-operator.md)
- [<span data-ttu-id="690c4-168">:: operator</span><span class="sxs-lookup"><span data-stu-id="690c4-168">:: operator</span></span>](namespace-alias-qualifier.md)
