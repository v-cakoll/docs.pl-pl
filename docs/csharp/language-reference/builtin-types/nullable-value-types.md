---
title: Typy wartości null — C# odwołanie
description: Dowiedz C# się więcej o typach wartości null i sposobach ich użycia
ms.date: 11/04/2019
helpviewer_keywords:
- nullable value types [C#]
ms.openlocfilehash: 661b5e8502cba42588a07d757f056c715c1c82e8
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2020
ms.locfileid: "75936900"
---
# <a name="nullable-value-types-c-reference"></a><span data-ttu-id="4d4a4-103">Typy wartości null (C# odwołanie)</span><span class="sxs-lookup"><span data-stu-id="4d4a4-103">Nullable value types (C# reference)</span></span>

<span data-ttu-id="4d4a4-104">Typ wartości null `T?` reprezentuje wszystkie wartości jego bazowego [typu wartości](../keywords/value-types.md) `T` i dodatkową wartość [null](../keywords/null.md) .</span><span class="sxs-lookup"><span data-stu-id="4d4a4-104">A nullable value type `T?` represents all values of its underlying [value type](../keywords/value-types.md) `T` and an additional [null](../keywords/null.md) value.</span></span> <span data-ttu-id="4d4a4-105">Na przykład można przypisać jedną z następujących trzech wartości do zmiennej `bool?`: `true`, `false`lub `null`.</span><span class="sxs-lookup"><span data-stu-id="4d4a4-105">For example, you can assign any of the following three values to a `bool?` variable: `true`, `false`, or `null`.</span></span> <span data-ttu-id="4d4a4-106">Podstawowy typ wartości `T` nie może być samym typem wartości null.</span><span class="sxs-lookup"><span data-stu-id="4d4a4-106">An underlying value type `T` cannot be a nullable value type itself.</span></span>

> [!NOTE]
> <span data-ttu-id="4d4a4-107">C#8,0 wprowadza funkcję typów odwołań do wartości null.</span><span class="sxs-lookup"><span data-stu-id="4d4a4-107">C# 8.0 introduces the nullable reference types feature.</span></span> <span data-ttu-id="4d4a4-108">Aby uzyskać więcej informacji, zobacz [typy referencyjne dopuszczające wartość null](../../nullable-references.md).</span><span class="sxs-lookup"><span data-stu-id="4d4a4-108">For more information, see [Nullable reference types](../../nullable-references.md).</span></span> <span data-ttu-id="4d4a4-109">Typy wartości null są dostępne od C# 2.</span><span class="sxs-lookup"><span data-stu-id="4d4a4-109">The nullable value types are available beginning with C# 2.</span></span>

<span data-ttu-id="4d4a4-110">Każdy typ wartości null jest wystąpieniem ogólnej struktury <xref:System.Nullable%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4d4a4-110">Any nullable value type is an instance of the generic <xref:System.Nullable%601?displayProperty=nameWithType> structure.</span></span> <span data-ttu-id="4d4a4-111">Można odwołać się do typu wartości null z typem podstawowym `T` w dowolnej z następujących formularzy, które można zmieniać: `Nullable<T>` lub `T?`.</span><span class="sxs-lookup"><span data-stu-id="4d4a4-111">You can refer to a nullable value type with an underlying type `T` in any of the following interchangeable forms: `Nullable<T>` or `T?`.</span></span>

<span data-ttu-id="4d4a4-112">Typ wartości null jest zazwyczaj używany, gdy trzeba reprezentować niezdefiniowaną wartość bazowego typu wartości.</span><span class="sxs-lookup"><span data-stu-id="4d4a4-112">You typically use a nullable value type when you need to represent the undefined value of an underlying value type.</span></span> <span data-ttu-id="4d4a4-113">Na przykład wartość logiczna lub `bool`zmienna może być tylko `true` lub `false`.</span><span class="sxs-lookup"><span data-stu-id="4d4a4-113">For example, a Boolean, or `bool`, variable can only be either `true` or `false`.</span></span> <span data-ttu-id="4d4a4-114">Jednak w niektórych aplikacjach wartość zmiennej może być niezdefiniowana lub brakująca.</span><span class="sxs-lookup"><span data-stu-id="4d4a4-114">However, in some applications a variable value can be undefined or missing.</span></span> <span data-ttu-id="4d4a4-115">Na przykład pole bazy danych może zawierać `true` lub `false`lub nie może zawierać żadnej wartości, czyli `NULL`.</span><span class="sxs-lookup"><span data-stu-id="4d4a4-115">For example, a database field may contain `true` or `false`, or it may contain no value at all, that is, `NULL`.</span></span> <span data-ttu-id="4d4a4-116">W tym scenariuszu można użyć typu `bool?`.</span><span class="sxs-lookup"><span data-stu-id="4d4a4-116">You can use the `bool?` type in that scenario.</span></span>

## <a name="declaration-and-assignment"></a><span data-ttu-id="4d4a4-117">Deklaracja i przypisanie</span><span class="sxs-lookup"><span data-stu-id="4d4a4-117">Declaration and assignment</span></span>

<span data-ttu-id="4d4a4-118">Ponieważ typ wartości jest niejawnie konwertowany do odpowiadającego typu wartości null, można przypisać wartość do zmiennej typu wartości null, tak jak w przypadku jego bazowego typu wartości.</span><span class="sxs-lookup"><span data-stu-id="4d4a4-118">As a value type is implicitly convertible to the corresponding nullable value type, you can assign a value to a variable of a nullable value type as you would do that for its underlying value type.</span></span> <span data-ttu-id="4d4a4-119">Możesz również przypisać wartość `null`.</span><span class="sxs-lookup"><span data-stu-id="4d4a4-119">You also can assign the `null` value.</span></span> <span data-ttu-id="4d4a4-120">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="4d4a4-120">For example:</span></span>

[!code-csharp[declare and assign](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#Declaration)]

<span data-ttu-id="4d4a4-121">Wartość domyślna typu wartości null reprezentuje `null`, czyli jest to wystąpienie, którego właściwość <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> zwraca `false`.</span><span class="sxs-lookup"><span data-stu-id="4d4a4-121">The default value of a nullable value type represents `null`, that is, it's an instance whose <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> property returns `false`.</span></span>

## <a name="examination-of-an-instance-of-a-nullable-value-type"></a><span data-ttu-id="4d4a4-122">Badanie wystąpienia typu wartości null</span><span class="sxs-lookup"><span data-stu-id="4d4a4-122">Examination of an instance of a nullable value type</span></span>

<span data-ttu-id="4d4a4-123">Począwszy od C# 7,0, można użyć [operatora`is` ze wzorcem typu](../operators/type-testing-and-cast.md#type-testing-with-pattern-matching) do obu badań wystąpienie typu wartości null dla `null` i pobrać wartość typu podstawowego:</span><span class="sxs-lookup"><span data-stu-id="4d4a4-123">Beginning with C# 7.0, you can use the [`is` operator with a type pattern](../operators/type-testing-and-cast.md#type-testing-with-pattern-matching) to both examine an instance of a nullable value type for `null` and retrieve a value of an underlying type:</span></span>

[!code-csharp-interactive[use pattern matching](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#PatternMatching)]

<span data-ttu-id="4d4a4-124">Aby sprawdzać i pobierać wartość zmiennej typu wartości null, zawsze można użyć następujących właściwości tylko do odczytu:</span><span class="sxs-lookup"><span data-stu-id="4d4a4-124">You always can use the following read-only properties to examine and get a value of a nullable value type variable:</span></span>

- <span data-ttu-id="4d4a4-125"><xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> wskazuje, czy wystąpienie typu wartości null ma wartość jego typu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="4d4a4-125"><xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> indicates whether an instance of a nullable value type has a value of its underlying type.</span></span>

- <span data-ttu-id="4d4a4-126"><xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> Pobiera wartość typu podstawowego, jeśli <xref:System.Nullable%601.HasValue%2A> jest `true`.</span><span class="sxs-lookup"><span data-stu-id="4d4a4-126"><xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> gets the value of an underlying type if <xref:System.Nullable%601.HasValue%2A> is `true`.</span></span> <span data-ttu-id="4d4a4-127">Jeśli <xref:System.Nullable%601.HasValue%2A> jest `false`, właściwość <xref:System.Nullable%601.Value%2A> zgłasza <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="4d4a4-127">If <xref:System.Nullable%601.HasValue%2A> is `false`, the <xref:System.Nullable%601.Value%2A> property throws an <xref:System.InvalidOperationException>.</span></span>

<span data-ttu-id="4d4a4-128">W poniższym przykładzie zastosowano Właściwość `HasValue`, aby sprawdzić, czy zmienna zawiera wartość przed wyświetleniem:</span><span class="sxs-lookup"><span data-stu-id="4d4a4-128">The following example uses the `HasValue` property to test whether the variable contains a value before displaying it:</span></span>

[!code-csharp-interactive[use HasValue](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#HasValue)]

<span data-ttu-id="4d4a4-129">Można także porównać zmienną typu wartości null z `null` zamiast korzystać z właściwości `HasValue`, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="4d4a4-129">You also can compare a variable of a nullable value type with `null` instead of using the `HasValue` property, as the following example shows:</span></span>

[!code-csharp-interactive[use comparison with null](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#CompareWithNull)]

## <a name="conversion-from-a-nullable-value-type-to-an-underlying-type"></a><span data-ttu-id="4d4a4-130">Konwersja z typu wartości null na typ podstawowy</span><span class="sxs-lookup"><span data-stu-id="4d4a4-130">Conversion from a nullable value type to an underlying type</span></span>

<span data-ttu-id="4d4a4-131">Jeśli chcesz przypisać wartość typu wartości null do zmiennej typu wartości, która nie dopuszcza wartości null, może być konieczne określenie wartości, która ma zostać przypisana zamiast `null`.</span><span class="sxs-lookup"><span data-stu-id="4d4a4-131">If you want to assign a value of a nullable value type to a non-nullable value type variable, you might need to specify the value to be assigned in place of `null`.</span></span> <span data-ttu-id="4d4a4-132">Użyj [`??`operatora łączenia wartości null](../operators/null-coalescing-operator.md) , aby to zrobić (można również użyć metody <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> do tego samego celu):</span><span class="sxs-lookup"><span data-stu-id="4d4a4-132">Use the [null-coalescing operator `??`](../operators/null-coalescing-operator.md) to do that (you also can use the <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> method for the same purpose):</span></span>

[!code-csharp-interactive[?? operator](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#NullCoalescing)]

<span data-ttu-id="4d4a4-133">Jeśli chcesz użyć [domyślnej](../keywords/default-values-table.md) wartości bazowego typu wartości zamiast `null`, użyj metody <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4d4a4-133">If you want to use the [default](../keywords/default-values-table.md) value of the underlying value type in place of `null`, use the <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="4d4a4-134">Można również jawnie rzutować typ wartości null na typ niedopuszczający wartości null, co ilustruje poniższy przykład:</span><span class="sxs-lookup"><span data-stu-id="4d4a4-134">You also can explicitly cast a nullable value type to a non-nullable type, as the following example shows:</span></span>

[!code-csharp[explicit cast](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#Cast)]

<span data-ttu-id="4d4a4-135">W czasie wykonywania, jeśli wartość typu wartości null jest `null`, jawne rzutowanie zgłosi <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="4d4a4-135">At run time, if the value of a nullable value type is `null`, the explicit cast throws an <xref:System.InvalidOperationException>.</span></span>

<span data-ttu-id="4d4a4-136">Typ wartości niedopuszczający wartości null `T` jest niejawnie konwertowany na odpowiedni typ wartości null `T?`.</span><span class="sxs-lookup"><span data-stu-id="4d4a4-136">A non-nullable value type `T` is implicitly convertible to the corresponding nullable value type `T?`.</span></span>

## <a name="lifted-operators"></a><span data-ttu-id="4d4a4-137">Podniesione operatory</span><span class="sxs-lookup"><span data-stu-id="4d4a4-137">Lifted operators</span></span>

<span data-ttu-id="4d4a4-138">Wstępnie zdefiniowane operatory jednoargumentowe i binarne lub wszelkie przeciążone operatory obsługiwane przez typ wartości `T` są również obsługiwane przez odpowiedni typ wartości null `T?`.</span><span class="sxs-lookup"><span data-stu-id="4d4a4-138">The predefined unary and binary operators or any overloaded operators that are supported by a value type `T` are also supported by the corresponding nullable value type `T?`.</span></span> <span data-ttu-id="4d4a4-139">Te operatory, znane także jako *zniesione operatory*, tworzą `null`, jeśli jeden lub oba operandy są `null`; w przeciwnym razie operator używa zawartych wartości argumentów operacji, aby obliczyć wynik.</span><span class="sxs-lookup"><span data-stu-id="4d4a4-139">These operators, also known as *lifted operators*, produce `null` if one or both operands are `null`; otherwise, the operator uses the contained values of its operands to calculate the result.</span></span> <span data-ttu-id="4d4a4-140">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="4d4a4-140">For example:</span></span>

[!code-csharp[lifted operators](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#LiftedOperator)]

> [!NOTE]
> <span data-ttu-id="4d4a4-141">Dla typu `bool?` wstępnie zdefiniowane operatory `&` i `|` nie są zgodne z regułami opisanymi w tej sekcji: wynik oceny operatora może być inny niż null, nawet jeśli jeden z operandów jest `null`.</span><span class="sxs-lookup"><span data-stu-id="4d4a4-141">For the `bool?` type, the predefined `&` and `|` operators don't follow the rules described in this section: the result of an operator evaluation can be non-null even if one of the operands is `null`.</span></span> <span data-ttu-id="4d4a4-142">Aby uzyskać więcej informacji, zobacz sekcję [Operatory logiczne wartości null](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) w artykule [Operatory logiczne Boolean](../operators/boolean-logical-operators.md) .</span><span class="sxs-lookup"><span data-stu-id="4d4a4-142">For more information, see the [Nullable Boolean logical operators](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) section of the [Boolean logical operators](../operators/boolean-logical-operators.md) article.</span></span>

<span data-ttu-id="4d4a4-143">Dla [operatorów porównania](../operators/comparison-operators.md) `<`, `>`, `<=`i `>=`, jeśli jeden lub oba operandy są `null`, wynik jest `false`; w przeciwnym razie zawarte wartości argumentów operacji są porównywane.</span><span class="sxs-lookup"><span data-stu-id="4d4a4-143">For the [comparison operators](../operators/comparison-operators.md) `<`, `>`, `<=`, and `>=`, if one or both operands are `null`, the result is `false`; otherwise the contained values of operands are compared.</span></span> <span data-ttu-id="4d4a4-144">Nie należy zakładać, że ponieważ określone porównanie (na przykład `<=`) zwraca `false`, przeciwieństwo do porównania (`>`) zwraca `true`.</span><span class="sxs-lookup"><span data-stu-id="4d4a4-144">Do not assume that because a particular comparison (for example, `<=`) returns `false`, the opposite comparison (`>`) returns `true`.</span></span> <span data-ttu-id="4d4a4-145">Poniższy przykład pokazuje, że 10 jest</span><span class="sxs-lookup"><span data-stu-id="4d4a4-145">The following example shows that 10 is</span></span>

- <span data-ttu-id="4d4a4-146">nie większe niż ani równe `null`</span><span class="sxs-lookup"><span data-stu-id="4d4a4-146">neither greater than or equal to `null`</span></span>
- <span data-ttu-id="4d4a4-147">ani nie mniejsze niż `null`</span><span class="sxs-lookup"><span data-stu-id="4d4a4-147">nor less than `null`</span></span>

[!code-csharp-interactive[relational and equality operators](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#ComparisonOperators)]

<span data-ttu-id="4d4a4-148">W powyższym przykładzie przedstawiono również, że porównanie równości dwóch wystąpień typu wartości null, które są jednocześnie `null` oblicza `true`.</span><span class="sxs-lookup"><span data-stu-id="4d4a4-148">The preceding example also shows that an equality comparison of two nullable value type instances that are both `null` evaluates to `true`.</span></span>

<span data-ttu-id="4d4a4-149">Jeśli istnieje [konwersja zdefiniowana przez użytkownika](../operators/user-defined-conversion-operators.md) między dwoma typami wartości, można także użyć tej samej konwersji między odpowiednimi typami wartości null.</span><span class="sxs-lookup"><span data-stu-id="4d4a4-149">If there exists a [user-defined conversion](../operators/user-defined-conversion-operators.md) between two value types, the same conversion can also be used between the corresponding nullable value types.</span></span>

## <a name="boxing-and-unboxing"></a><span data-ttu-id="4d4a4-150">Pakowanie i rozpakowywanie</span><span class="sxs-lookup"><span data-stu-id="4d4a4-150">Boxing and unboxing</span></span>

<span data-ttu-id="4d4a4-151">Wystąpienie typu wartości null `T?` jest [opakowane](../../programming-guide/types/boxing-and-unboxing.md) w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="4d4a4-151">An instance of a nullable value type `T?` is [boxed](../../programming-guide/types/boxing-and-unboxing.md) as follows:</span></span>

- <span data-ttu-id="4d4a4-152">Jeśli <xref:System.Nullable%601.HasValue%2A> zwraca `false`, zostanie wygenerowane odwołanie o wartości null.</span><span class="sxs-lookup"><span data-stu-id="4d4a4-152">If <xref:System.Nullable%601.HasValue%2A> returns `false`, the null reference is produced.</span></span>
- <span data-ttu-id="4d4a4-153">Jeśli <xref:System.Nullable%601.HasValue%2A> zwraca `true`, odpowiadająca wartość bazowego typu wartości `T` jest opakowana, a nie wystąpieniem <xref:System.Nullable%601>.</span><span class="sxs-lookup"><span data-stu-id="4d4a4-153">If <xref:System.Nullable%601.HasValue%2A> returns `true`, the corresponding value of the underlying value type `T` is boxed, not the instance of <xref:System.Nullable%601>.</span></span>

<span data-ttu-id="4d4a4-154">Można Unbox wartość opakowaną typu wartości `T` do odpowiadającego typu wartości null `T?`, jak pokazano na poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="4d4a4-154">You can unbox a boxed value of a value type `T` to the corresponding nullable value type `T?`, as the following example shows:</span></span>

[!code-csharp-interactive[boxing and unboxing](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#Boxing)]

## <a name="how-to-identify-a-nullable-value-type"></a><span data-ttu-id="4d4a4-155">Jak zidentyfikować typ wartości null</span><span class="sxs-lookup"><span data-stu-id="4d4a4-155">How to identify a nullable value type</span></span>

<span data-ttu-id="4d4a4-156">Poniższy przykład pokazuje, jak ustalić, czy wystąpienie <xref:System.Type?displayProperty=nameWithType> reprezentuje skonstruowany typ wartości null, czyli typ <xref:System.Nullable%601?displayProperty=nameWithType> z określonym parametrem typu `T`:</span><span class="sxs-lookup"><span data-stu-id="4d4a4-156">The following example shows how to determine whether a <xref:System.Type?displayProperty=nameWithType> instance represents a constructed nullable value type, that is, the <xref:System.Nullable%601?displayProperty=nameWithType> type with a specified type parameter `T`:</span></span>

[!code-csharp-interactive[whether Type is nullable](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#IsTypeNullable)]

<span data-ttu-id="4d4a4-157">Jak pokazano w przykładzie, należy użyć operatora [typeof](../operators/type-testing-and-cast.md#typeof-operator) , aby utworzyć wystąpienie <xref:System.Type?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4d4a4-157">As the example shows, you use the [typeof](../operators/type-testing-and-cast.md#typeof-operator) operator to create a <xref:System.Type?displayProperty=nameWithType> instance.</span></span>

<span data-ttu-id="4d4a4-158">Aby określić, czy wystąpienie ma typ wartości null, nie należy używać metody <xref:System.Object.GetType%2A?displayProperty=nameWithType>, aby uzyskać <xref:System.Type> wystąpienie do przetestowania przy użyciu poprzedniego kodu.</span><span class="sxs-lookup"><span data-stu-id="4d4a4-158">If you want to determine whether an instance is of a nullable value type, don't use the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method to get a <xref:System.Type> instance to be tested with the preceding code.</span></span> <span data-ttu-id="4d4a4-159">Po wywołaniu metody <xref:System.Object.GetType%2A?displayProperty=nameWithType> w wystąpieniu typu wartości null wystąpienie jest [opakowane](#boxing-and-unboxing) do <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="4d4a4-159">When you call the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method on an instance of a nullable value type, the instance is [boxed](#boxing-and-unboxing) to <xref:System.Object>.</span></span> <span data-ttu-id="4d4a4-160">Jako opakowanie niezerowego typu wartości null jest równoważne z opakowaniem wartości typu podstawowego, <xref:System.Object.GetType%2A> zwraca wystąpienie <xref:System.Type> reprezentujące typ podstawowy typu wartości null:</span><span class="sxs-lookup"><span data-stu-id="4d4a4-160">As boxing of a non-null instance of a nullable value type is equivalent to boxing of a value of the underlying type, <xref:System.Object.GetType%2A> returns a <xref:System.Type> instance that represents the underlying type of a nullable value type:</span></span>

[!code-csharp-interactive[GetType example](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#GetType)]

<span data-ttu-id="4d4a4-161">Ponadto nie należy używać operatora [is](../operators/type-testing-and-cast.md#is-operator) , aby określić, czy wystąpienie ma typ wartości null.</span><span class="sxs-lookup"><span data-stu-id="4d4a4-161">Also, don't use the [is](../operators/type-testing-and-cast.md#is-operator) operator to determine whether an instance is of a nullable value type.</span></span> <span data-ttu-id="4d4a4-162">Jak pokazano na poniższym przykładzie, nie można rozróżnić typów wystąpienia typu wartości null i jego wystąpienia podstawowego z operatorem `is`:</span><span class="sxs-lookup"><span data-stu-id="4d4a4-162">As the following example shows, you cannot distinguish types of a nullable value type instance and its underlying type instance with the `is` operator:</span></span>

[!code-csharp-interactive[is operator example](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#IsOperator)]

<span data-ttu-id="4d4a4-163">Możesz użyć kodu przedstawionego w poniższym przykładzie, aby określić, czy wystąpienie ma typ wartości null:</span><span class="sxs-lookup"><span data-stu-id="4d4a4-163">You can use the code presented in the following example to determine whether an instance is of a nullable value type:</span></span>

[!code-csharp-interactive[whether an instance is of a nullable type](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#IsInstanceNullable)]

> [!NOTE]
> <span data-ttu-id="4d4a4-164">Metody opisane w tej sekcji nie mają zastosowania w przypadku [typów referencyjnych dopuszczających wartość null](../../nullable-references.md).</span><span class="sxs-lookup"><span data-stu-id="4d4a4-164">The methods described in this section are not applicable in the case of [nullable reference types](../../nullable-references.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="4d4a4-165">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="4d4a4-165">C# language specification</span></span>

<span data-ttu-id="4d4a4-166">Aby uzyskać więcej informacji, zobacz następujące sekcje [ C# specyfikacji języka](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="4d4a4-166">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="4d4a4-167">Typy dopuszczające wartości null</span><span class="sxs-lookup"><span data-stu-id="4d4a4-167">Nullable types</span></span>](~/_csharplang/spec/types.md#nullable-types)
- [<span data-ttu-id="4d4a4-168">Podniesione operatory</span><span class="sxs-lookup"><span data-stu-id="4d4a4-168">Lifted operators</span></span>](~/_csharplang/spec/expressions.md#lifted-operators)
- [<span data-ttu-id="4d4a4-169">Niejawne konwersje dopuszczające wartość null</span><span class="sxs-lookup"><span data-stu-id="4d4a4-169">Implicit nullable conversions</span></span>](~/_csharplang/spec/conversions.md#implicit-nullable-conversions)
- [<span data-ttu-id="4d4a4-170">Jawne konwersje dopuszczające wartość null</span><span class="sxs-lookup"><span data-stu-id="4d4a4-170">Explicit nullable conversions</span></span>](~/_csharplang/spec/conversions.md#explicit-nullable-conversions)
- [<span data-ttu-id="4d4a4-171">Przenoszone operatory konwersji</span><span class="sxs-lookup"><span data-stu-id="4d4a4-171">Lifted conversion operators</span></span>](~/_csharplang/spec/conversions.md#lifted-conversion-operators)

## <a name="see-also"></a><span data-ttu-id="4d4a4-172">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4d4a4-172">See also</span></span>

- [<span data-ttu-id="4d4a4-173">C#odwoła</span><span class="sxs-lookup"><span data-stu-id="4d4a4-173">C# reference</span></span>](../index.md)
- [<span data-ttu-id="4d4a4-174">Co dokładnie ma znaczenie "zniesione"?</span><span class="sxs-lookup"><span data-stu-id="4d4a4-174">What exactly does 'lifted' mean?</span></span>](https://docs.microsoft.com/archive/blogs/ericlippert/what-exactly-does-lifted-mean)
- <xref:System.Nullable%601?displayProperty=nameWithType>
- <xref:System.Nullable?displayProperty=nameWithType>
- <xref:System.Nullable.GetUnderlyingType%2A?displayProperty=nameWithType>
- [<span data-ttu-id="4d4a4-175">Typy referencyjne dopuszczające wartość null</span><span class="sxs-lookup"><span data-stu-id="4d4a4-175">Nullable reference types</span></span>](../../nullable-references.md)
