---
title: Typy wartości null - odwołanie do języka C#
description: Dowiedz się więcej o typach wartości null z wartościami języka C# i sposobie ich używania
ms.date: 11/04/2019
helpviewer_keywords:
- nullable value types [C#]
ms.openlocfilehash: a84b3d60269491846b783e5046a84a1d14e258a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399589"
---
# <a name="nullable-value-types-c-reference"></a><span data-ttu-id="a8429-103">Typy wartości null (odwołanie do języka C#)</span><span class="sxs-lookup"><span data-stu-id="a8429-103">Nullable value types (C# reference)</span></span>

<span data-ttu-id="a8429-104">*Typ* `T?` wartości nullable reprezentuje wszystkie wartości jego podstawowego typu `T` [wartości](value-types.md) i dodatkowej wartości [null.](../keywords/null.md)</span><span class="sxs-lookup"><span data-stu-id="a8429-104">A *nullable value type* `T?` represents all values of its underlying [value type](value-types.md) `T` and an additional [null](../keywords/null.md) value.</span></span> <span data-ttu-id="a8429-105">Na przykład do `bool?` zmiennej można przypisać dowolną z `true` `false`następujących `null`trzech wartości: , , lub .</span><span class="sxs-lookup"><span data-stu-id="a8429-105">For example, you can assign any of the following three values to a `bool?` variable: `true`, `false`, or `null`.</span></span> <span data-ttu-id="a8429-106">Typ wartości podstawowej `T` nie może być typem wartości null.</span><span class="sxs-lookup"><span data-stu-id="a8429-106">An underlying value type `T` cannot be a nullable value type itself.</span></span>

> [!NOTE]
> <span data-ttu-id="a8429-107">C# 8.0 wprowadza funkcję typów odwołań nullable.</span><span class="sxs-lookup"><span data-stu-id="a8429-107">C# 8.0 introduces the nullable reference types feature.</span></span> <span data-ttu-id="a8429-108">Aby uzyskać więcej informacji, zobacz [Typy odwołań nullable](../../nullable-references.md).</span><span class="sxs-lookup"><span data-stu-id="a8429-108">For more information, see [Nullable reference types](../../nullable-references.md).</span></span> <span data-ttu-id="a8429-109">Typy wartości nullable są dostępne począwszy od Języka C# 2.</span><span class="sxs-lookup"><span data-stu-id="a8429-109">The nullable value types are available beginning with C# 2.</span></span>

<span data-ttu-id="a8429-110">Każdy typ wartości nullable jest <xref:System.Nullable%601?displayProperty=nameWithType> wystąpieniem struktury ogólnej.</span><span class="sxs-lookup"><span data-stu-id="a8429-110">Any nullable value type is an instance of the generic <xref:System.Nullable%601?displayProperty=nameWithType> structure.</span></span> <span data-ttu-id="a8429-111">Można odwołać się do typu wartości null `T` z typem bazowym `Nullable<T>` w `T?`dowolnej z następujących form wymiennych: lub .</span><span class="sxs-lookup"><span data-stu-id="a8429-111">You can refer to a nullable value type with an underlying type `T` in any of the following interchangeable forms: `Nullable<T>` or `T?`.</span></span>

<span data-ttu-id="a8429-112">Zazwyczaj należy użyć typu wartości null, gdy trzeba reprezentować niezdefiniowaną wartość podstawowego typu wartości.</span><span class="sxs-lookup"><span data-stu-id="a8429-112">You typically use a nullable value type when you need to represent the undefined value of an underlying value type.</span></span> <span data-ttu-id="a8429-113">Na przykład wartość logiczna `bool`lub zmienna `true` może `false`być tylko jedną lub zmienną.</span><span class="sxs-lookup"><span data-stu-id="a8429-113">For example, a Boolean, or `bool`, variable can only be either `true` or `false`.</span></span> <span data-ttu-id="a8429-114">Jednak w niektórych aplikacjach wartość zmiennej może być niezdefiniowana lub brakuje.</span><span class="sxs-lookup"><span data-stu-id="a8429-114">However, in some applications a variable value can be undefined or missing.</span></span> <span data-ttu-id="a8429-115">Na przykład pole bazy `true` danych `false`może zawierać lub , lub może `NULL`zawierać żadnej wartości w ogóle, to znaczy .</span><span class="sxs-lookup"><span data-stu-id="a8429-115">For example, a database field may contain `true` or `false`, or it may contain no value at all, that is, `NULL`.</span></span> <span data-ttu-id="a8429-116">Można użyć `bool?` tego typu w tym scenariuszu.</span><span class="sxs-lookup"><span data-stu-id="a8429-116">You can use the `bool?` type in that scenario.</span></span>

## <a name="declaration-and-assignment"></a><span data-ttu-id="a8429-117">Deklaracja i przypisanie</span><span class="sxs-lookup"><span data-stu-id="a8429-117">Declaration and assignment</span></span>

<span data-ttu-id="a8429-118">Jako typ wartości jest niejawnie konwertowalne do odpowiedniego typu wartości nullable, można przypisać wartość do zmiennej typu wartości null, jak to zrobić dla jego podstawowego typu wartości.</span><span class="sxs-lookup"><span data-stu-id="a8429-118">As a value type is implicitly convertible to the corresponding nullable value type, you can assign a value to a variable of a nullable value type as you would do that for its underlying value type.</span></span> <span data-ttu-id="a8429-119">Można również przypisać `null` wartość.</span><span class="sxs-lookup"><span data-stu-id="a8429-119">You also can assign the `null` value.</span></span> <span data-ttu-id="a8429-120">Przykład:</span><span class="sxs-lookup"><span data-stu-id="a8429-120">For example:</span></span>

[!code-csharp[declare and assign](snippets/NullableValueTypes.cs#Declaration)]

<span data-ttu-id="a8429-121">Wartość domyślna typu wartości nullable `null`reprezentuje , oznacza to, <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> że `false`jest to wystąpienie, którego właściwość zwraca .</span><span class="sxs-lookup"><span data-stu-id="a8429-121">The default value of a nullable value type represents `null`, that is, it's an instance whose <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> property returns `false`.</span></span>

## <a name="examination-of-an-instance-of-a-nullable-value-type"></a><span data-ttu-id="a8429-122">Badanie wystąpienia typu wartości podleganej null</span><span class="sxs-lookup"><span data-stu-id="a8429-122">Examination of an instance of a nullable value type</span></span>

<span data-ttu-id="a8429-123">Począwszy od Języka C# 7.0, można użyć [ `is` operatora z wzorcem typu](../operators/type-testing-and-cast.md#type-testing-with-pattern-matching) zarówno `null` zbadać wystąpienie typu wartości nullable dla i pobrać wartość typu źródłowego:</span><span class="sxs-lookup"><span data-stu-id="a8429-123">Beginning with C# 7.0, you can use the [`is` operator with a type pattern](../operators/type-testing-and-cast.md#type-testing-with-pattern-matching) to both examine an instance of a nullable value type for `null` and retrieve a value of an underlying type:</span></span>

[!code-csharp-interactive[use pattern matching](snippets/NullableValueTypes.cs#PatternMatching)]

<span data-ttu-id="a8429-124">Zawsze można użyć następujących właściwości tylko do odczytu, aby sprawdzić i uzyskać wartość zmiennej typu wartości nullable:</span><span class="sxs-lookup"><span data-stu-id="a8429-124">You always can use the following read-only properties to examine and get a value of a nullable value type variable:</span></span>

- <span data-ttu-id="a8429-125"><xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType>wskazuje, czy wystąpienie typu wartości nullable ma wartość jego typu bazowego.</span><span class="sxs-lookup"><span data-stu-id="a8429-125"><xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> indicates whether an instance of a nullable value type has a value of its underlying type.</span></span>

- <span data-ttu-id="a8429-126"><xref:System.Nullable%601.Value%2A?displayProperty=nameWithType>pobiera wartość typu bazowego, <xref:System.Nullable%601.HasValue%2A> `true`jeśli jest .</span><span class="sxs-lookup"><span data-stu-id="a8429-126"><xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> gets the value of an underlying type if <xref:System.Nullable%601.HasValue%2A> is `true`.</span></span> <span data-ttu-id="a8429-127">Jeśli <xref:System.Nullable%601.HasValue%2A> `false`jest <xref:System.Nullable%601.Value%2A> , właściwość <xref:System.InvalidOperationException>rzuca .</span><span class="sxs-lookup"><span data-stu-id="a8429-127">If <xref:System.Nullable%601.HasValue%2A> is `false`, the <xref:System.Nullable%601.Value%2A> property throws an <xref:System.InvalidOperationException>.</span></span>

<span data-ttu-id="a8429-128">W poniższym `HasValue` przykładzie użyto właściwości, aby sprawdzić, czy zmienna zawiera wartość przed wyświetleniem go:</span><span class="sxs-lookup"><span data-stu-id="a8429-128">The following example uses the `HasValue` property to test whether the variable contains a value before displaying it:</span></span>

[!code-csharp-interactive[use HasValue](snippets/NullableValueTypes.cs#HasValue)]

<span data-ttu-id="a8429-129">Można również porównać zmienną typu wartości `null` nullable z `HasValue` zamiast przy użyciu właściwości, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="a8429-129">You also can compare a variable of a nullable value type with `null` instead of using the `HasValue` property, as the following example shows:</span></span>

[!code-csharp-interactive[use comparison with null](snippets/NullableValueTypes.cs#CompareWithNull)]

## <a name="conversion-from-a-nullable-value-type-to-an-underlying-type"></a><span data-ttu-id="a8429-130">Konwersja z typu wartości null do typu bazowego</span><span class="sxs-lookup"><span data-stu-id="a8429-130">Conversion from a nullable value type to an underlying type</span></span>

<span data-ttu-id="a8429-131">Jeśli chcesz przypisać wartość typu wartości nullable do zmiennej typu wartości niepodleganej null, może być konieczne określenie `null`wartości, która ma być przypisana w miejsce .</span><span class="sxs-lookup"><span data-stu-id="a8429-131">If you want to assign a value of a nullable value type to a non-nullable value type variable, you might need to specify the value to be assigned in place of `null`.</span></span> <span data-ttu-id="a8429-132">Użyj [operatora `??` łączenia wartości null,](../operators/null-coalescing-operator.md) aby to zrobić (można <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> również użyć metody w tym samym celu):</span><span class="sxs-lookup"><span data-stu-id="a8429-132">Use the [null-coalescing operator `??`](../operators/null-coalescing-operator.md) to do that (you also can use the <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> method for the same purpose):</span></span>

[!code-csharp-interactive[?? operator](snippets/NullableValueTypes.cs#NullCoalescing)]

<span data-ttu-id="a8429-133">Jeśli chcesz użyć [wartości domyślnej](default-values.md) podstawowego typu wartości `null`w <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> miejsce , należy użyć tej metody.</span><span class="sxs-lookup"><span data-stu-id="a8429-133">If you want to use the [default](default-values.md) value of the underlying value type in place of `null`, use the <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="a8429-134">Można również jawnie rzutować typ wartości nullable do typu niedopuszczającowego, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="a8429-134">You also can explicitly cast a nullable value type to a non-nullable type, as the following example shows:</span></span>

[!code-csharp[explicit cast](snippets/NullableValueTypes.cs#Cast)]

<span data-ttu-id="a8429-135">W czasie wykonywania, jeśli wartość typu `null`wartości nullable jest <xref:System.InvalidOperationException>, jawne rzutnie rzuca .</span><span class="sxs-lookup"><span data-stu-id="a8429-135">At run time, if the value of a nullable value type is `null`, the explicit cast throws an <xref:System.InvalidOperationException>.</span></span>

<span data-ttu-id="a8429-136">Typ `T` wartości niepodlegający null jest niejawnie konwertowalny na `T?`odpowiadający mu typ wartości nullable .</span><span class="sxs-lookup"><span data-stu-id="a8429-136">A non-nullable value type `T` is implicitly convertible to the corresponding nullable value type `T?`.</span></span>

## <a name="lifted-operators"></a><span data-ttu-id="a8429-137">Operatorzy podnoszenia</span><span class="sxs-lookup"><span data-stu-id="a8429-137">Lifted operators</span></span>

<span data-ttu-id="a8429-138">Wstępnie zdefiniowane [operatory](../operators/index.md) nieoparte i binarne lub wszelkie przeciążone operatory, które są obsługiwane przez typ `T` wartości, są również obsługiwane przez odpowiedni typ `T?`wartości nullable .</span><span class="sxs-lookup"><span data-stu-id="a8429-138">The predefined unary and binary [operators](../operators/index.md) or any overloaded operators that are supported by a value type `T` are also supported by the corresponding nullable value type `T?`.</span></span> <span data-ttu-id="a8429-139">Podmioty te, znane również jako `null` *operatorzy podnoszenia,* `null`produkują, jeśli jeden lub oba operandy są; w przeciwnym razie operator używa zawartych wartości swoich operandów do obliczenia wyniku.</span><span class="sxs-lookup"><span data-stu-id="a8429-139">These operators, also known as *lifted operators*, produce `null` if one or both operands are `null`; otherwise, the operator uses the contained values of its operands to calculate the result.</span></span> <span data-ttu-id="a8429-140">Przykład:</span><span class="sxs-lookup"><span data-stu-id="a8429-140">For example:</span></span>

[!code-csharp[lifted operators](snippets/NullableValueTypes.cs#LiftedOperator)]

> [!NOTE]
> <span data-ttu-id="a8429-141">Dla `bool?` typu wstępnie zdefiniowane `&` i `|` operatory nie są zgodne z regułami opisanymi w tej sekcji: wynik oceny operatora może `null`być non-null, nawet jeśli jeden z operands jest .</span><span class="sxs-lookup"><span data-stu-id="a8429-141">For the `bool?` type, the predefined `&` and `|` operators don't follow the rules described in this section: the result of an operator evaluation can be non-null even if one of the operands is `null`.</span></span> <span data-ttu-id="a8429-142">Aby uzyskać więcej informacji, zobacz [nullable logicznych operatorów logicznych](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) sekcji [logicznych operatorów logicznych.](../operators/boolean-logical-operators.md)</span><span class="sxs-lookup"><span data-stu-id="a8429-142">For more information, see the [Nullable Boolean logical operators](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) section of the [Boolean logical operators](../operators/boolean-logical-operators.md) article.</span></span>

<span data-ttu-id="a8429-143">Dla [operatorów](../operators/comparison-operators.md) `<`porównawczych `<=`, `>=` `>`, i , jeśli `null`jeden lub `false`oba argumenty są , wynik jest; w przeciwnym razie porównywane są zawarte wartości argumentów.</span><span class="sxs-lookup"><span data-stu-id="a8429-143">For the [comparison operators](../operators/comparison-operators.md) `<`, `>`, `<=`, and `>=`, if one or both operands are `null`, the result is `false`; otherwise, the contained values of operands are compared.</span></span> <span data-ttu-id="a8429-144">Nie zakładaj, że ponieważ określone `<=`porównanie `false`(na przykład)`>`zwraca, odwrotne porównanie ( ) zwraca `true`.</span><span class="sxs-lookup"><span data-stu-id="a8429-144">Do not assume that because a particular comparison (for example, `<=`) returns `false`, the opposite comparison (`>`) returns `true`.</span></span> <span data-ttu-id="a8429-145">W poniższym przykładzie pokazano, że 10</span><span class="sxs-lookup"><span data-stu-id="a8429-145">The following example shows that 10 is</span></span>

- <span data-ttu-id="a8429-146">ani większe niż równe`null`</span><span class="sxs-lookup"><span data-stu-id="a8429-146">neither greater than or equal to `null`</span></span>
- <span data-ttu-id="a8429-147">ani mniej niż`null`</span><span class="sxs-lookup"><span data-stu-id="a8429-147">nor less than `null`</span></span>

[!code-csharp-interactive[relational and equality operators](snippets/NullableValueTypes.cs#ComparisonOperators)]

<span data-ttu-id="a8429-148">Dla [operatora](../operators/equality-operators.md#equality-operator-) `==`równości , jeśli oba `null`operandy `true`są , wynik jest , `null`jeśli tylko `false`jeden z argumentów jest , wynik jest; w przeciwnym razie porównywane są zawarte wartości argumentów.</span><span class="sxs-lookup"><span data-stu-id="a8429-148">For the [equality operator](../operators/equality-operators.md#equality-operator-) `==`, if both operands are `null`, the result is `true`, if only one of the operands is `null`, the result is `false`; otherwise, the contained values of operands are compared.</span></span>

<span data-ttu-id="a8429-149">Dla [operatora](../operators/equality-operators.md#inequality-operator-) `!=`nierówności , jeśli oba `null`argumenty `false`są , wynik jest , `null`jeśli tylko `true`jeden z argumentów jest , wynik jest; w przeciwnym razie porównywane są zawarte wartości argumentów.</span><span class="sxs-lookup"><span data-stu-id="a8429-149">For the [inequality operator](../operators/equality-operators.md#inequality-operator-) `!=`, if both operands are `null`, the result is `false`, if only one of the operands is `null`, the result is `true`; otherwise, the contained values of operands are compared.</span></span>

<span data-ttu-id="a8429-150">Jeśli istnieje [konwersja zdefiniowana przez użytkownika](../operators/user-defined-conversion-operators.md) między dwoma typami wartości, ta sama konwersja może być również używana między odpowiadającymi typami wartości nullable.</span><span class="sxs-lookup"><span data-stu-id="a8429-150">If there exists a [user-defined conversion](../operators/user-defined-conversion-operators.md) between two value types, the same conversion can also be used between the corresponding nullable value types.</span></span>

## <a name="boxing-and-unboxing"></a><span data-ttu-id="a8429-151">Boks i rozpakowywanie</span><span class="sxs-lookup"><span data-stu-id="a8429-151">Boxing and unboxing</span></span>

<span data-ttu-id="a8429-152">Wystąpienie typu `T?` wartości nullable jest [zapakowane w](../../programming-guide/types/boxing-and-unboxing.md) następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="a8429-152">An instance of a nullable value type `T?` is [boxed](../../programming-guide/types/boxing-and-unboxing.md) as follows:</span></span>

- <span data-ttu-id="a8429-153">Jeśli <xref:System.Nullable%601.HasValue%2A> `false`zwraca, odwołanie null jest tworzony.</span><span class="sxs-lookup"><span data-stu-id="a8429-153">If <xref:System.Nullable%601.HasValue%2A> returns `false`, the null reference is produced.</span></span>
- <span data-ttu-id="a8429-154">Jeśli <xref:System.Nullable%601.HasValue%2A> `true`zwraca, odpowiednia wartość podstawowego `T` typu wartości jest zapakowana, a nie wystąpienie <xref:System.Nullable%601>.</span><span class="sxs-lookup"><span data-stu-id="a8429-154">If <xref:System.Nullable%601.HasValue%2A> returns `true`, the corresponding value of the underlying value type `T` is boxed, not the instance of <xref:System.Nullable%601>.</span></span>

<span data-ttu-id="a8429-155">Można rozpakować zakrojoną `T` wartość typu wartości do `T?`odpowiedniego typu wartości nullable , jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="a8429-155">You can unbox a boxed value of a value type `T` to the corresponding nullable value type `T?`, as the following example shows:</span></span>

[!code-csharp-interactive[boxing and unboxing](snippets/NullableValueTypes.cs#Boxing)]

## <a name="how-to-identify-a-nullable-value-type"></a><span data-ttu-id="a8429-156">Jak zidentyfikować typ wartości z wartością nullable</span><span class="sxs-lookup"><span data-stu-id="a8429-156">How to identify a nullable value type</span></span>

<span data-ttu-id="a8429-157">W poniższym przykładzie pokazano, jak określić, czy <xref:System.Type?displayProperty=nameWithType> wystąpienie reprezentuje skonstruowany typ wartości nullable, czyli <xref:System.Nullable%601?displayProperty=nameWithType> typ z parametrem `T`określonego typu:</span><span class="sxs-lookup"><span data-stu-id="a8429-157">The following example shows how to determine whether a <xref:System.Type?displayProperty=nameWithType> instance represents a constructed nullable value type, that is, the <xref:System.Nullable%601?displayProperty=nameWithType> type with a specified type parameter `T`:</span></span>

[!code-csharp-interactive[whether Type is nullable](snippets/NullableValueTypes.cs#IsTypeNullable)]

<span data-ttu-id="a8429-158">Jak pokazano w przykładzie, należy użyć <xref:System.Type?displayProperty=nameWithType> [operatora typeof](../operators/type-testing-and-cast.md#typeof-operator) do utworzenia wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="a8429-158">As the example shows, you use the [typeof](../operators/type-testing-and-cast.md#typeof-operator) operator to create a <xref:System.Type?displayProperty=nameWithType> instance.</span></span>

<span data-ttu-id="a8429-159">Jeśli chcesz ustalić, czy wystąpienie ma wartość nullable, nie <xref:System.Object.GetType%2A?displayProperty=nameWithType> należy używać <xref:System.Type> metody, aby uzyskać wystąpienie do przetestowania z poprzednim kodem.</span><span class="sxs-lookup"><span data-stu-id="a8429-159">If you want to determine whether an instance is of a nullable value type, don't use the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method to get a <xref:System.Type> instance to be tested with the preceding code.</span></span> <span data-ttu-id="a8429-160">Podczas wywoływania <xref:System.Object.GetType%2A?displayProperty=nameWithType> metody w wystąpieniu typu wartości nullable, wystąpienie <xref:System.Object>jest [zapakowane](#boxing-and-unboxing) w .</span><span class="sxs-lookup"><span data-stu-id="a8429-160">When you call the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method on an instance of a nullable value type, the instance is [boxed](#boxing-and-unboxing) to <xref:System.Object>.</span></span> <span data-ttu-id="a8429-161">Jako boks wystąpienia non-null typu wartości nulljest odpowiednik bokserskiej wartości typu podstawowego, <xref:System.Type> zwraca wystąpienie, <xref:System.Object.GetType%2A> które reprezentuje typ wartości o wartości null:</span><span class="sxs-lookup"><span data-stu-id="a8429-161">As boxing of a non-null instance of a nullable value type is equivalent to boxing of a value of the underlying type, <xref:System.Object.GetType%2A> returns a <xref:System.Type> instance that represents the underlying type of a nullable value type:</span></span>

[!code-csharp-interactive[GetType example](snippets/NullableValueTypes.cs#GetType)]

<span data-ttu-id="a8429-162">Ponadto nie należy używać [is](../operators/type-testing-and-cast.md#is-operator) operator, aby ustalić, czy wystąpienie jest typu wartości null.</span><span class="sxs-lookup"><span data-stu-id="a8429-162">Also, don't use the [is](../operators/type-testing-and-cast.md#is-operator) operator to determine whether an instance is of a nullable value type.</span></span> <span data-ttu-id="a8429-163">Jak pokazano w poniższym przykładzie, nie można odróżnić typów wystąpienia typu `is` wartości nulli z jego wystąpieniem typu źródłowego z operatorem:</span><span class="sxs-lookup"><span data-stu-id="a8429-163">As the following example shows, you cannot distinguish types of a nullable value type instance and its underlying type instance with the `is` operator:</span></span>

[!code-csharp-interactive[is operator example](snippets/NullableValueTypes.cs#IsOperator)]

<span data-ttu-id="a8429-164">Kod przedstawiony w poniższym przykładzie, aby ustalić, czy wystąpienie ma wartość nullable:</span><span class="sxs-lookup"><span data-stu-id="a8429-164">You can use the code presented in the following example to determine whether an instance is of a nullable value type:</span></span>

[!code-csharp-interactive[whether an instance is of a nullable type](snippets/NullableValueTypes.cs#IsInstanceNullable)]

> [!NOTE]
> <span data-ttu-id="a8429-165">Metody opisane w tej sekcji nie mają zastosowania w przypadku [typów odwołań podlegających wartości null.](../../nullable-references.md)</span><span class="sxs-lookup"><span data-stu-id="a8429-165">The methods described in this section are not applicable in the case of [nullable reference types](../../nullable-references.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="a8429-166">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="a8429-166">C# language specification</span></span>

<span data-ttu-id="a8429-167">Aby uzyskać więcej informacji, zobacz następujące sekcje [specyfikacji języka Języka C#:](~/_csharplang/spec/introduction.md)</span><span class="sxs-lookup"><span data-stu-id="a8429-167">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="a8429-168">Typy z możliwością null</span><span class="sxs-lookup"><span data-stu-id="a8429-168">Nullable types</span></span>](~/_csharplang/spec/types.md#nullable-types)
- [<span data-ttu-id="a8429-169">Operatorzy podnoszenia</span><span class="sxs-lookup"><span data-stu-id="a8429-169">Lifted operators</span></span>](~/_csharplang/spec/expressions.md#lifted-operators)
- [<span data-ttu-id="a8429-170">Niejawne konwersje nullable</span><span class="sxs-lookup"><span data-stu-id="a8429-170">Implicit nullable conversions</span></span>](~/_csharplang/spec/conversions.md#implicit-nullable-conversions)
- [<span data-ttu-id="a8429-171">Jawne konwersje nullable</span><span class="sxs-lookup"><span data-stu-id="a8429-171">Explicit nullable conversions</span></span>](~/_csharplang/spec/conversions.md#explicit-nullable-conversions)
- [<span data-ttu-id="a8429-172">Operatorzy konwersji podniesionej</span><span class="sxs-lookup"><span data-stu-id="a8429-172">Lifted conversion operators</span></span>](~/_csharplang/spec/conversions.md#lifted-conversion-operators)

## <a name="see-also"></a><span data-ttu-id="a8429-173">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a8429-173">See also</span></span>

- [<span data-ttu-id="a8429-174">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="a8429-174">C# reference</span></span>](../index.md)
- [<span data-ttu-id="a8429-175">Co dokładnie oznacza "zniesione"?</span><span class="sxs-lookup"><span data-stu-id="a8429-175">What exactly does 'lifted' mean?</span></span>](https://docs.microsoft.com/archive/blogs/ericlippert/what-exactly-does-lifted-mean)
- <xref:System.Nullable%601?displayProperty=nameWithType>
- <xref:System.Nullable?displayProperty=nameWithType>
- <xref:System.Nullable.GetUnderlyingType%2A?displayProperty=nameWithType>
- [<span data-ttu-id="a8429-176">Typy referencyjne dopuszczające wartość null</span><span class="sxs-lookup"><span data-stu-id="a8429-176">Nullable reference types</span></span>](../../nullable-references.md)
