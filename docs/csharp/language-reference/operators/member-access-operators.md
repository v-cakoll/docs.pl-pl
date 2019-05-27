---
title: Operatory dostępu do elementów członkowskich — C# odwołania
description: Dowiedz się więcej o C# operatorów, które umożliwiają dostęp do elementów członkowskich typu.
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
ms.openlocfilehash: eec70f5446eec11fa4e241b86eed4ed8d6146f85
ms.sourcegitcommit: 96543603ae29bc05cecccb8667974d058af63b4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66195780"
---
# <a name="member-access-operators-c-reference"></a><span data-ttu-id="5e3be-103">Operatory dostępu do składowych (C# odwołania)</span><span class="sxs-lookup"><span data-stu-id="5e3be-103">Member access operators (C# Reference)</span></span>

<span data-ttu-id="5e3be-104">Gdy uzyskujesz dostęp do składowej typu można używać następujących operatorów:</span><span class="sxs-lookup"><span data-stu-id="5e3be-104">You might use the following operators when you access a type member:</span></span>

- <span data-ttu-id="5e3be-105">[`.` (dostęp do elementu członkowskiego) ](#member-access-operator-): do uzyskania dostępu do członka przestrzeni nazw lub typ</span><span class="sxs-lookup"><span data-stu-id="5e3be-105">[`.` (member access)](#member-access-operator-): to access a member of a namespace or a type</span></span>
- <span data-ttu-id="5e3be-106">[`[]` (element lub indeksator dostęp do tablicy) ](#indexer-operator-): Aby uzyskać dostęp do elementu tablicy i indeksatora typu</span><span class="sxs-lookup"><span data-stu-id="5e3be-106">[`[]` (array element or indexer access)](#indexer-operator-): to access an array element or a type indexer</span></span>
- <span data-ttu-id="5e3be-107">[`?.` i `?[]` (operatorów warunkowych działających z wartością null)](#null-conditional-operators--and-): do wykonywania operacji dostępu do elementu członkowskiego lub elementu, tylko wtedy, gdy argument jest różna od null</span><span class="sxs-lookup"><span data-stu-id="5e3be-107">[`?.` and `?[]` (null-conditional operators)](#null-conditional-operators--and-): to perform a member or element access operation only if an operand is non-null</span></span>
- <span data-ttu-id="5e3be-108">[`()` (wywołanie) ](#invocation-operator-): wywoływanie metody dostępu lub wywołanie delegata</span><span class="sxs-lookup"><span data-stu-id="5e3be-108">[`()` (invocation)](#invocation-operator-): to call an accessed method or invoke a delegate</span></span>

## <a name="member-access-operator-"></a><span data-ttu-id="5e3be-109">Operator dostępu do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="5e3be-109">Member access operator .</span></span>

<span data-ttu-id="5e3be-110">Możesz użyć `.` token w celu uzyskania dostępu do członka przestrzeni nazw lub typ, jak w poniższych przykładach pokazano:</span><span class="sxs-lookup"><span data-stu-id="5e3be-110">You use the `.` token to access a member of a namespace or a type, as the following examples demonstrate:</span></span>

- <span data-ttu-id="5e3be-111">Użyj `.` dostępu zagnieżdżone przestrzenie nazw w przestrzeni nazw, w poniższym przykładzie z do [ `using` dyrektywy](../keywords/using-directive.md) pokazuje:</span><span class="sxs-lookup"><span data-stu-id="5e3be-111">Use `.` to access a nested namespace within a namespace, as the following example of a [`using` directive](../keywords/using-directive.md) shows:</span></span>

  [!code-csharp[nested namespaces](~/samples/snippets/csharp/language-reference/operators/MemberAccessOperators.cs#NestedNamespace)]

- <span data-ttu-id="5e3be-112">Użyj `.` do formularza *kwalifikowana nazwa* uzyskiwać dostęp do typu, w przestrzeni nazw, co ilustruje poniższy kod:</span><span class="sxs-lookup"><span data-stu-id="5e3be-112">Use `.` to form a *qualified name* to access a type within a namespace, as the following code shows:</span></span>

  [!code-csharp[qualified name](~/samples/snippets/csharp/language-reference/operators/MemberAccessOperators.cs#QualifiedName)]

  <span data-ttu-id="5e3be-113">Użyj [ `using` dyrektywy](../keywords/using-directive.md) powoduje użycie kwalifikowane nazwy są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="5e3be-113">Use a [`using` directive](../keywords/using-directive.md) to make the use of qualified names optional.</span></span>

- <span data-ttu-id="5e3be-114">Użyj `.` dostęp do [elementy członkowskie typu](../../programming-guide/classes-and-structs/index.md#members)statycznych i niestatycznych, co ilustruje poniższy kod:</span><span class="sxs-lookup"><span data-stu-id="5e3be-114">Use `.` to access [type members](../../programming-guide/classes-and-structs/index.md#members), static and non-static, as the following code shows:</span></span>

  [!code-csharp-interactive[type members](~/samples/snippets/csharp/language-reference/operators/MemberAccessOperators.cs#TypeMemberAccess)]

<span data-ttu-id="5e3be-115">Można również użyć `.` dostęp do [— metoda rozszerzenia](../../programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="5e3be-115">You can also use `.` to access an [extension method](../../programming-guide/classes-and-structs/extension-methods.md).</span></span>

## <a name="indexer-operator-"></a><span data-ttu-id="5e3be-116">Indeksator operator]</span><span class="sxs-lookup"><span data-stu-id="5e3be-116">Indexer operator []</span></span>

<span data-ttu-id="5e3be-117">Nawiasy kwadratowe `[]`, są zwykle używane do dostępu do elementu tablicy, indeksator lub wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="5e3be-117">Square brackets, `[]`, are typically used for array, indexer, or pointer element access.</span></span>

### <a name="array-access"></a><span data-ttu-id="5e3be-118">Dostęp do tablicy</span><span class="sxs-lookup"><span data-stu-id="5e3be-118">Array access</span></span>

<span data-ttu-id="5e3be-119">Poniższy przykład pokazuje, jak uzyskać dostęp do elementów tablicy:</span><span class="sxs-lookup"><span data-stu-id="5e3be-119">The following example demonstrates how to access array elements:</span></span>

[!code-csharp-interactive[array access](~/samples/snippets/csharp/language-reference/operators/MemberAccessOperators.cs#Arrays)]

<span data-ttu-id="5e3be-120">Jeśli indeks tablicy jest poza granicami odpowiedniego wymiaru tablicy, <xref:System.IndexOutOfRangeException> zgłaszany.</span><span class="sxs-lookup"><span data-stu-id="5e3be-120">If an array index is outside the bounds of the corresponding dimension of an array, an <xref:System.IndexOutOfRangeException> is thrown.</span></span>

<span data-ttu-id="5e3be-121">Jak pokazano na poprzednim przykładzie, możesz także użyć nawiasami kwadratowymi podczas deklarowania typu tablicowego lub tworzy wystąpienie tablicy.</span><span class="sxs-lookup"><span data-stu-id="5e3be-121">As the preceding example shows, you also use square brackets when you declare an array type or instantiate an array instance.</span></span>

<span data-ttu-id="5e3be-122">Aby uzyskać więcej informacji na temat tablic, zobacz [tablic](../../programming-guide/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="5e3be-122">For more information about arrays, see [Arrays](../../programming-guide/arrays/index.md).</span></span>

### <a name="indexer-access"></a><span data-ttu-id="5e3be-123">Dostęp indeksatora</span><span class="sxs-lookup"><span data-stu-id="5e3be-123">Indexer access</span></span>

<span data-ttu-id="5e3be-124">W poniższym przykładzie użyto .NET <xref:System.Collections.Generic.Dictionary%602> typu, aby zademonstrować dostęp indeksatora:</span><span class="sxs-lookup"><span data-stu-id="5e3be-124">The following example uses .NET <xref:System.Collections.Generic.Dictionary%602> type to demonstrate indexer access:</span></span>

[!code-csharp-interactive[indexer access](~/samples/snippets/csharp/language-reference/operators/MemberAccessOperators.cs#Indexers)]

<span data-ttu-id="5e3be-125">Indeksatory pozwalają na indeks wystąpienia typu zdefiniowanego przez użytkownika w podobny sposób jak indeksowanie tablicy.</span><span class="sxs-lookup"><span data-stu-id="5e3be-125">Indexers allow you to index instances of a user-defined type in the similar way as array indexing.</span></span> <span data-ttu-id="5e3be-126">W przeciwieństwie do tablicy wskaźników, które musi być liczbą całkowitą, argumenty indeksator może być zadeklarowana jako dowolnego typu.</span><span class="sxs-lookup"><span data-stu-id="5e3be-126">Unlike array indices, which must be integer, the indexer arguments can be declared to be of any type.</span></span>

<span data-ttu-id="5e3be-127">Aby uzyskać więcej informacji na temat indeksatorów, zobacz [indeksatory](../../programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="5e3be-127">For more information about indexers, see [Indexers](../../programming-guide/indexers/index.md).</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="5e3be-128">Inne sposoby użycia]</span><span class="sxs-lookup"><span data-stu-id="5e3be-128">Other usages of []</span></span>

<span data-ttu-id="5e3be-129">Uzyskać informacji o dostępie do elementu wskaźnika, zobacz [wskaźnika elementu dostępu operator []](pointer-related-operators.md#pointer-element-access-operator-) części [wskaźnik związane z operatorów](pointer-related-operators.md) artykułu.</span><span class="sxs-lookup"><span data-stu-id="5e3be-129">For information about pointer element access, see the [Pointer element access operator []](pointer-related-operators.md#pointer-element-access-operator-) section of the [Pointer related operators](pointer-related-operators.md) article.</span></span>

<span data-ttu-id="5e3be-130">Nawiasy kwadratowe również służy do określania [atrybuty](../../programming-guide/concepts/attributes/index.md):</span><span class="sxs-lookup"><span data-stu-id="5e3be-130">You also use square brackets to specify [attributes](../../programming-guide/concepts/attributes/index.md):</span></span>

```csharp
[System.Diagnostics.Conditional("DEBUG")]
void TraceMethod() {}
```

## <a name="null-conditional-operators--and-"></a><span data-ttu-id="5e3be-131">Operatory warunkowe null?</span><span class="sxs-lookup"><span data-stu-id="5e3be-131">Null-conditional operators ?.</span></span> <span data-ttu-id="5e3be-132">i? []</span><span class="sxs-lookup"><span data-stu-id="5e3be-132">and ?[]</span></span>

<span data-ttu-id="5e3be-133">Dostępne w C# 6 i nowsze, operatorów warunkowych działających z wartością null dotyczy dostęp do elementu członkowskiego `?.`, lub dostęp do elementu `?[]`, operacja argumentem operacji tylko wtedy, gdy ten argument operacji ma inną niż null.</span><span class="sxs-lookup"><span data-stu-id="5e3be-133">Available in C# 6 and later, a null-conditional operator applies a member access, `?.`, or element access, `?[]`, operation to its operand only if that operand evaluates to non-null.</span></span> <span data-ttu-id="5e3be-134">Jeśli argument daje w wyniku `null`, wynik zastosowania operatora jest `null`.</span><span class="sxs-lookup"><span data-stu-id="5e3be-134">If the operand evaluates to `null`, the result of applying the operator is `null`.</span></span> <span data-ttu-id="5e3be-135">Operator dostępu do elementu członkowskiego warunkowe null `?.` jest także znana jako Elvis operator.</span><span class="sxs-lookup"><span data-stu-id="5e3be-135">The null-conditional member access operator `?.` is also known as the Elvis operator.</span></span>

<span data-ttu-id="5e3be-136">Operatory warunkowe `null` skracają łańcuch wykonywania operacji.</span><span class="sxs-lookup"><span data-stu-id="5e3be-136">The null-conditional operators are short-circuiting.</span></span> <span data-ttu-id="5e3be-137">Oznacza to, jeśli jedna operacja w łańcuchu warunkowa składowa lub elementu dostępu do operacji zwraca `null`, pozostała część łańcucha nie jest wykonywany.</span><span class="sxs-lookup"><span data-stu-id="5e3be-137">That is, if one operation in a chain of conditional member or element access operations returns `null`, the rest of the chain doesn't execute.</span></span> <span data-ttu-id="5e3be-138">W poniższym przykładzie `B` nie jest oceniany, jeśli `A` daje w wyniku `null` i `C` nie jest oceniany, jeśli `A` lub `B` daje w wyniku `null`:</span><span class="sxs-lookup"><span data-stu-id="5e3be-138">In the following example, `B` is not evaluated if `A` evaluates to `null` and `C` is not evaluated if `A` or `B` evaluates to `null`:</span></span>

```csharp
A?.B?.Do(C);
A?.B?[C];
```

<span data-ttu-id="5e3be-139">W poniższym przykładzie pokazano użycie `?.` i `?[]` operatory:</span><span class="sxs-lookup"><span data-stu-id="5e3be-139">The following example demonstrates the usage of the `?.` and `?[]` operators:</span></span>

[!code-csharp-interactive[null-conditional operators](~/samples/snippets/csharp/language-reference/operators/MemberAccessOperators.cs#NullConditional)]

<span data-ttu-id="5e3be-140">Powyższy przykład pokazuje również użycie [operatorem łączenia wartości null](null-coalescing-operator.md).</span><span class="sxs-lookup"><span data-stu-id="5e3be-140">The preceding example also shows the usage of the [null-coalescing operator](null-coalescing-operator.md).</span></span> <span data-ttu-id="5e3be-141">Można na przykład operatora łączenia wartości null do zapewnienia alternatywnych wyrażenie do oceny, w przypadku, gdy jest wynikiem operacji warunkowych działających z wartością null `null`.</span><span class="sxs-lookup"><span data-stu-id="5e3be-141">You might use the null-coalescing operator to provide an alternative expression to evaluate in case the result of the null-conditional operation is `null`.</span></span>

### <a name="thread-safe-delegate-invocation"></a><span data-ttu-id="5e3be-142">Wywołanie delegata metodą o bezpiecznych wątkach</span><span class="sxs-lookup"><span data-stu-id="5e3be-142">Thread-safe delegate invocation</span></span>

<span data-ttu-id="5e3be-143">Użyj `?.` operatora, sprawdź, czy obiekt delegowany jest inna niż null i wywoływać ją w sposób wątkowo (na przykład, gdy użytkownik [wywołać zdarzenie](../../../standard/events/how-to-raise-and-consume-events.md)), jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="5e3be-143">Use the `?.` operator to check if a delegate is non-null and invoke it in a thread-safe way (for example, when you [raise an event](../../../standard/events/how-to-raise-and-consume-events.md)), as the following code shows:</span></span>

```csharp
PropertyChanged?.Invoke(…)
```

<span data-ttu-id="5e3be-144">Czy kod jest odpowiednikiem następujący kod, który zostanie wykorzystany w C# 5 lub starszy:</span><span class="sxs-lookup"><span data-stu-id="5e3be-144">That code is equivalent to the following code that you would use in C# 5 or earlier:</span></span>

```csharp
var handler = this.PropertyChanged;
if (handler != null)
{
    handler(…);
}
```

## <a name="invocation-operator-"></a><span data-ttu-id="5e3be-145">Wywołanie — operator)</span><span class="sxs-lookup"><span data-stu-id="5e3be-145">Invocation operator ()</span></span>

<span data-ttu-id="5e3be-146">Użyj nawiasów, `()`, aby wywołać [metoda](../../programming-guide/classes-and-structs/methods.md) lub wywołaj [delegować](../../programming-guide/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="5e3be-146">Use parentheses, `()`, to call a [method](../../programming-guide/classes-and-structs/methods.md) or invoke a [delegate](../../programming-guide/delegates/index.md).</span></span>

<span data-ttu-id="5e3be-147">Poniższy przykład pokazuje sposób wywołania metody, z lub bez argumentów i wywołanie delegata:</span><span class="sxs-lookup"><span data-stu-id="5e3be-147">The following example demonstrates how to call a method, with or without arguments, and invoke a delegate:</span></span>

[!code-csharp-interactive[invocation with ()](~/samples/snippets/csharp/language-reference/operators/MemberAccessOperators.cs#Invocation)]

<span data-ttu-id="5e3be-148">Można także użyć nawiasów podczas wywołujesz [Konstruktor](../../programming-guide/classes-and-structs/constructors.md) z [ `new` ](../keywords/new-operator.md) operatora.</span><span class="sxs-lookup"><span data-stu-id="5e3be-148">You also use parentheses when you invoke a [constructor](../../programming-guide/classes-and-structs/constructors.md) with a [`new`](../keywords/new-operator.md) operator.</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="5e3be-149">Inne sposoby użycia)</span><span class="sxs-lookup"><span data-stu-id="5e3be-149">Other usages of ()</span></span>

<span data-ttu-id="5e3be-150">Możesz także użyć nawiasów, aby określić kolejność, w którym ma być operacji w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="5e3be-150">You also use parentheses to specify the order in which to evaluate operations in an expression.</span></span> <span data-ttu-id="5e3be-151">Aby uzyskać więcej informacji, zobacz [Dodawanie nawiasów](../../programming-guide/statements-expressions-operators/operators.md#adding-parentheses) części [operatory](../../programming-guide/statements-expressions-operators/operators.md) artykułu.</span><span class="sxs-lookup"><span data-stu-id="5e3be-151">For more information, see the [Adding parentheses](../../programming-guide/statements-expressions-operators/operators.md#adding-parentheses) section of the [Operators](../../programming-guide/statements-expressions-operators/operators.md) article.</span></span> <span data-ttu-id="5e3be-152">Listy uporządkowane według poziomu pierwszeństwo operatorów, zobacz [ C# operatory](index.md).</span><span class="sxs-lookup"><span data-stu-id="5e3be-152">For the list of operators ordered by precedence level, see [C# operators](index.md).</span></span>

<span data-ttu-id="5e3be-153">[Rzutowane wyrażenia,](invocation-operator.md#cast-expression), który wywołać operatora konwersji, należy również użyć nawiasów.</span><span class="sxs-lookup"><span data-stu-id="5e3be-153">[Cast expressions](invocation-operator.md#cast-expression), which invoke a conversion operator, also use parentheses.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="5e3be-154">Overloadability — operator</span><span class="sxs-lookup"><span data-stu-id="5e3be-154">Operator overloadability</span></span>

<span data-ttu-id="5e3be-155">`.` i `()` nie mogą być przeciążone operatory.</span><span class="sxs-lookup"><span data-stu-id="5e3be-155">The `.` and `()` operators cannot be overloaded.</span></span> <span data-ttu-id="5e3be-156">`[]` Operator jest traktowana jako inne niż z możliwością przeciążenia operatora.</span><span class="sxs-lookup"><span data-stu-id="5e3be-156">The `[]` operator is also considered a non-overloadable operator.</span></span> <span data-ttu-id="5e3be-157">Użyj [indeksatory](../../programming-guide/indexers/index.md) do obsługi indeksowanie z typami zdefiniowanymi przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5e3be-157">Use [indexers](../../programming-guide/indexers/index.md) to support indexing with user-defined types.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="5e3be-158">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="5e3be-158">C# language specification</span></span>

<span data-ttu-id="5e3be-159">Aby uzyskać więcej informacji, zobacz następujące sekcje [ C# specyfikacji języka](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="5e3be-159">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="5e3be-160">Dostęp do elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="5e3be-160">Member access</span></span>](~/_csharplang/spec/expressions.md#member-access)
- [<span data-ttu-id="5e3be-161">Dostęp do elementu</span><span class="sxs-lookup"><span data-stu-id="5e3be-161">Element access</span></span>](~/_csharplang/spec/expressions.md#element-access)
- [<span data-ttu-id="5e3be-162">Operatorów warunkowych działających z wartością null</span><span class="sxs-lookup"><span data-stu-id="5e3be-162">Null-conditional operator</span></span>](~/_csharplang/spec/expressions.md#null-conditional-operator)
- [<span data-ttu-id="5e3be-163">Wyrażenia wywołania</span><span class="sxs-lookup"><span data-stu-id="5e3be-163">Invocation expressions</span></span>](~/_csharplang/spec/expressions.md#invocation-expressions)

## <a name="see-also"></a><span data-ttu-id="5e3be-164">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5e3be-164">See also</span></span>

- [<span data-ttu-id="5e3be-165">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="5e3be-165">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="5e3be-166">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="5e3be-166">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="5e3be-167">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="5e3be-167">C# Operators</span></span>](index.md)
- [<span data-ttu-id="5e3be-168">?? (z operatorem łączenia wartości null)</span><span class="sxs-lookup"><span data-stu-id="5e3be-168">?? (null-coalescing operator)</span></span>](null-coalescing-operator.md)
