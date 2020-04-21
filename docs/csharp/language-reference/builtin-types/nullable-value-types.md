---
title: Typy wartości możliwe do wartości null — odwołanie do języka C#
description: Dowiedz się więcej o typach wartości nullable języka C# i o tym, jak z nich korzystać
ms.date: 11/04/2019
helpviewer_keywords:
- nullable value types [C#]
ms.openlocfilehash: fcd49d7d25b0ad23363db8cb61596004b2e87a8d
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738997"
---
# <a name="nullable-value-types-c-reference"></a><span data-ttu-id="db525-103">Typy wartości możliwe do wartości null (odwołanie do języka C#)</span><span class="sxs-lookup"><span data-stu-id="db525-103">Nullable value types (C# reference)</span></span>

<span data-ttu-id="db525-104">`T?` *Typ wartości możliwej do wartości null* reprezentuje wszystkie wartości jego typ `T` [wartości](value-types.md) podstawowej i dodatkową wartość [null.](../keywords/null.md)</span><span class="sxs-lookup"><span data-stu-id="db525-104">A *nullable value type* `T?` represents all values of its underlying [value type](value-types.md) `T` and an additional [null](../keywords/null.md) value.</span></span> <span data-ttu-id="db525-105">Na przykład `bool?` do zmiennej można przypisać dowolną z `true` `false`następujących `null`trzech wartości: , , lub .</span><span class="sxs-lookup"><span data-stu-id="db525-105">For example, you can assign any of the following three values to a `bool?` variable: `true`, `false`, or `null`.</span></span> <span data-ttu-id="db525-106">Typ `T` wartości podstawowej nie może być typem wartości możliwej do wartości null.</span><span class="sxs-lookup"><span data-stu-id="db525-106">An underlying value type `T` cannot be a nullable value type itself.</span></span>

> [!NOTE]
> <span data-ttu-id="db525-107">C# 8.0 wprowadza funkcję typów odwołań nullable.</span><span class="sxs-lookup"><span data-stu-id="db525-107">C# 8.0 introduces the nullable reference types feature.</span></span> <span data-ttu-id="db525-108">Aby uzyskać więcej informacji, zobacz [Typy odwołań do wartości null.](nullable-reference-types.md)</span><span class="sxs-lookup"><span data-stu-id="db525-108">For more information, see [Nullable reference types](nullable-reference-types.md).</span></span> <span data-ttu-id="db525-109">Typy wartości możliwe do wartości null są dostępne począwszy od języka C# 2.</span><span class="sxs-lookup"><span data-stu-id="db525-109">The nullable value types are available beginning with C# 2.</span></span>

<span data-ttu-id="db525-110">Każdy typ wartości nullable jest <xref:System.Nullable%601?displayProperty=nameWithType> wystąpieniem struktury ogólnej.</span><span class="sxs-lookup"><span data-stu-id="db525-110">Any nullable value type is an instance of the generic <xref:System.Nullable%601?displayProperty=nameWithType> structure.</span></span> <span data-ttu-id="db525-111">Można odwołać się do typu wartości `T` nullable z typem bazowym w dowolnej z następujących wymiennych formularzy: `Nullable<T>` lub `T?`.</span><span class="sxs-lookup"><span data-stu-id="db525-111">You can refer to a nullable value type with an underlying type `T` in any of the following interchangeable forms: `Nullable<T>` or `T?`.</span></span>

<span data-ttu-id="db525-112">Typ wartości z możliwością wartości nullable jest zazwyczaj używany, gdy należy przedstawić niezdefiniowana wartość typu wartości podstawowej.</span><span class="sxs-lookup"><span data-stu-id="db525-112">You typically use a nullable value type when you need to represent the undefined value of an underlying value type.</span></span> <span data-ttu-id="db525-113">Na przykład wartość logiczna `bool`lub zmienna może `true` `false`być tylko jedną lub .</span><span class="sxs-lookup"><span data-stu-id="db525-113">For example, a Boolean, or `bool`, variable can only be either `true` or `false`.</span></span> <span data-ttu-id="db525-114">Jednak w niektórych aplikacjach wartość zmiennej może być niezdefiniowana lub brakuje.</span><span class="sxs-lookup"><span data-stu-id="db525-114">However, in some applications a variable value can be undefined or missing.</span></span> <span data-ttu-id="db525-115">Na przykład pole bazy `true` danych `false`może zawierać lub , lub może `NULL`zawierać żadną wartość, to znaczy .</span><span class="sxs-lookup"><span data-stu-id="db525-115">For example, a database field may contain `true` or `false`, or it may contain no value at all, that is, `NULL`.</span></span> <span data-ttu-id="db525-116">Można użyć `bool?` typu w tym scenariuszu.</span><span class="sxs-lookup"><span data-stu-id="db525-116">You can use the `bool?` type in that scenario.</span></span>

## <a name="declaration-and-assignment"></a><span data-ttu-id="db525-117">Deklaracja i przydział</span><span class="sxs-lookup"><span data-stu-id="db525-117">Declaration and assignment</span></span>

<span data-ttu-id="db525-118">Jako typ wartości jest niejawnie konwertowane do odpowiedniego typu wartości nullable, można przypisać wartość do zmiennej typu wartości nullable, jak to zrobić dla jego typ wartości podstawowej.</span><span class="sxs-lookup"><span data-stu-id="db525-118">As a value type is implicitly convertible to the corresponding nullable value type, you can assign a value to a variable of a nullable value type as you would do that for its underlying value type.</span></span> <span data-ttu-id="db525-119">Można również przypisać `null` wartość.</span><span class="sxs-lookup"><span data-stu-id="db525-119">You can also assign the `null` value.</span></span> <span data-ttu-id="db525-120">Przykład:</span><span class="sxs-lookup"><span data-stu-id="db525-120">For example:</span></span>

[!code-csharp[declare and assign](snippets/NullableValueTypes.cs#Declaration)]

<span data-ttu-id="db525-121">Wartość domyślna typu wartości możliwej do wartości null reprezentuje `null` <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> , `false`to znaczy, że jest to wystąpienie, którego właściwość zwraca .</span><span class="sxs-lookup"><span data-stu-id="db525-121">The default value of a nullable value type represents `null`, that is, it's an instance whose <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> property returns `false`.</span></span>

## <a name="examination-of-an-instance-of-a-nullable-value-type"></a><span data-ttu-id="db525-122">Badanie wystąpienia typu wartości możliwej domina</span><span class="sxs-lookup"><span data-stu-id="db525-122">Examination of an instance of a nullable value type</span></span>

<span data-ttu-id="db525-123">Począwszy od języka C# 7.0, można użyć [ `is` operatora z wzorcem typu,](../operators/type-testing-and-cast.md#type-testing-with-pattern-matching) aby zarówno zbadać wystąpienie typu wartości możliwej do wartości null dla `null` i pobrać wartość typu bazowego:</span><span class="sxs-lookup"><span data-stu-id="db525-123">Beginning with C# 7.0, you can use the [`is` operator with a type pattern](../operators/type-testing-and-cast.md#type-testing-with-pattern-matching) to both examine an instance of a nullable value type for `null` and retrieve a value of an underlying type:</span></span>

[!code-csharp-interactive[use pattern matching](snippets/NullableValueTypes.cs#PatternMatching)]

<span data-ttu-id="db525-124">Zawsze można użyć następujących właściwości tylko do odczytu, aby zbadać i uzyskać wartość zmiennej typu wartości nullable:</span><span class="sxs-lookup"><span data-stu-id="db525-124">You always can use the following read-only properties to examine and get a value of a nullable value type variable:</span></span>

- <span data-ttu-id="db525-125"><xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType>wskazuje, czy wystąpienie typu wartości możliwej do wartości null ma wartość jego typu bazowego.</span><span class="sxs-lookup"><span data-stu-id="db525-125"><xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> indicates whether an instance of a nullable value type has a value of its underlying type.</span></span>

- <span data-ttu-id="db525-126"><xref:System.Nullable%601.Value%2A?displayProperty=nameWithType>pobiera wartość typu bazowego, jeśli <xref:System.Nullable%601.HasValue%2A> jest `true`.</span><span class="sxs-lookup"><span data-stu-id="db525-126"><xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> gets the value of an underlying type if <xref:System.Nullable%601.HasValue%2A> is `true`.</span></span> <span data-ttu-id="db525-127">Jeśli <xref:System.Nullable%601.HasValue%2A> `false`tak, <xref:System.Nullable%601.Value%2A> właściwość <xref:System.InvalidOperationException>rzuca .</span><span class="sxs-lookup"><span data-stu-id="db525-127">If <xref:System.Nullable%601.HasValue%2A> is `false`, the <xref:System.Nullable%601.Value%2A> property throws an <xref:System.InvalidOperationException>.</span></span>

<span data-ttu-id="db525-128">Poniższy przykład używa `HasValue` właściwości, aby sprawdzić, czy zmienna zawiera wartość przed wyświetleniem go:</span><span class="sxs-lookup"><span data-stu-id="db525-128">The following example uses the `HasValue` property to test whether the variable contains a value before displaying it:</span></span>

[!code-csharp-interactive[use HasValue](snippets/NullableValueTypes.cs#HasValue)]

<span data-ttu-id="db525-129">Można również porównać zmienną typu wartości `null` nullable z `HasValue` zamiast używać właściwości, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="db525-129">You can also compare a variable of a nullable value type with `null` instead of using the `HasValue` property, as the following example shows:</span></span>

[!code-csharp-interactive[use comparison with null](snippets/NullableValueTypes.cs#CompareWithNull)]

## <a name="conversion-from-a-nullable-value-type-to-an-underlying-type"></a><span data-ttu-id="db525-130">Konwersja z typu wartości możliwej do wartości null do typu bazowego</span><span class="sxs-lookup"><span data-stu-id="db525-130">Conversion from a nullable value type to an underlying type</span></span>

<span data-ttu-id="db525-131">Jeśli chcesz przypisać wartość typu wartości możliwej do wartości null do zmiennej typu wartości nienastępującej wartość `null`null, może być konieczne określenie wartości, która ma być przypisana zamiast pliku .</span><span class="sxs-lookup"><span data-stu-id="db525-131">If you want to assign a value of a nullable value type to a non-nullable value type variable, you might need to specify the value to be assigned in place of `null`.</span></span> <span data-ttu-id="db525-132">Użyj [operatora `??` scalania null,](../operators/null-coalescing-operator.md) aby to zrobić (można również użyć metody w <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> tym samym celu):</span><span class="sxs-lookup"><span data-stu-id="db525-132">Use the [null-coalescing operator `??`](../operators/null-coalescing-operator.md) to do that (you can also use the <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> method for the same purpose):</span></span>

[!code-csharp-interactive[?? operator](snippets/NullableValueTypes.cs#NullCoalescing)]

<span data-ttu-id="db525-133">Jeśli chcesz użyć wartości [domyślnej](default-values.md) typu wartości podstawowej `null`zamiast <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> , użyj metody.</span><span class="sxs-lookup"><span data-stu-id="db525-133">If you want to use the [default](default-values.md) value of the underlying value type in place of `null`, use the <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="db525-134">Można również jawnie rzutować typ wartości nullable do typu niedopuszczalnyego do wartości null, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="db525-134">You can also explicitly cast a nullable value type to a non-nullable type, as the following example shows:</span></span>

[!code-csharp[explicit cast](snippets/NullableValueTypes.cs#Cast)]

<span data-ttu-id="db525-135">W czasie wykonywania, jeśli wartość typu wartości `null`możliwej do wartości <xref:System.InvalidOperationException>nullable jest , jawne rzut rzutnie zgłasza .</span><span class="sxs-lookup"><span data-stu-id="db525-135">At run time, if the value of a nullable value type is `null`, the explicit cast throws an <xref:System.InvalidOperationException>.</span></span>

<span data-ttu-id="db525-136">Typ `T` wartości nienastępnej wartości jest niejawnie konwertowany na odpowiedni typ `T?`wartości null.</span><span class="sxs-lookup"><span data-stu-id="db525-136">A non-nullable value type `T` is implicitly convertible to the corresponding nullable value type `T?`.</span></span>

## <a name="lifted-operators"></a><span data-ttu-id="db525-137">Operatorzy podnoszony</span><span class="sxs-lookup"><span data-stu-id="db525-137">Lifted operators</span></span>

<span data-ttu-id="db525-138">Wstępnie zdefiniowane [operatory](../operators/index.md) jednoarbyowe i binarne lub wszelkie przeciążone operatory obsługiwane przez `T` typ `T?`wartości są również obsługiwane przez odpowiedni typ wartości nullable .</span><span class="sxs-lookup"><span data-stu-id="db525-138">The predefined unary and binary [operators](../operators/index.md) or any overloaded operators that are supported by a value type `T` are also supported by the corresponding nullable value type `T?`.</span></span> <span data-ttu-id="db525-139">Operatorzy ci, znani również jako `null` *operatorzy podniesiony,* produkują, jeśli jeden lub oba argumenty są; `null` w przeciwnym razie operator używa zawartych wartości swoich argumentów do obliczania wyniku.</span><span class="sxs-lookup"><span data-stu-id="db525-139">These operators, also known as *lifted operators*, produce `null` if one or both operands are `null`; otherwise, the operator uses the contained values of its operands to calculate the result.</span></span> <span data-ttu-id="db525-140">Przykład:</span><span class="sxs-lookup"><span data-stu-id="db525-140">For example:</span></span>

[!code-csharp[lifted operators](snippets/NullableValueTypes.cs#LiftedOperator)]

> [!NOTE]
> <span data-ttu-id="db525-141">Dla `bool?` typu wstępnie zdefiniowane `&` i `|` operatory nie są zgodne z regułami opisanymi w tej sekcji: wynik oceny operatora może `null`być nie-null, nawet jeśli jeden z argumentów jest .</span><span class="sxs-lookup"><span data-stu-id="db525-141">For the `bool?` type, the predefined `&` and `|` operators don't follow the rules described in this section: the result of an operator evaluation can be non-null even if one of the operands is `null`.</span></span> <span data-ttu-id="db525-142">Aby uzyskać więcej informacji, zobacz [nullable logiczne operatory logiczne](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) sekcji [logiczne logiczne](../operators/boolean-logical-operators.md) logiczne artykułu.</span><span class="sxs-lookup"><span data-stu-id="db525-142">For more information, see the [Nullable Boolean logical operators](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) section of the [Boolean logical operators](../operators/boolean-logical-operators.md) article.</span></span>

<span data-ttu-id="db525-143">Dla [operatorów](../operators/comparison-operators.md) `<` `>`porównania `<=`, `>=`, , i , `null`jeśli jeden `false`lub oba argumenty są , wynik jest; w przeciwnym razie porównywane są zawarte wartości operandów.</span><span class="sxs-lookup"><span data-stu-id="db525-143">For the [comparison operators](../operators/comparison-operators.md) `<`, `>`, `<=`, and `>=`, if one or both operands are `null`, the result is `false`; otherwise, the contained values of operands are compared.</span></span> <span data-ttu-id="db525-144">Nie należy zakładać, że ponieważ `<=`określone `false`porównanie (na`>`przykład) `true`zwraca , zwraca porównanie przeciwne ( ) zwraca .</span><span class="sxs-lookup"><span data-stu-id="db525-144">Do not assume that because a particular comparison (for example, `<=`) returns `false`, the opposite comparison (`>`) returns `true`.</span></span> <span data-ttu-id="db525-145">Poniższy przykład pokazuje, że 10 jest</span><span class="sxs-lookup"><span data-stu-id="db525-145">The following example shows that 10 is</span></span>

- <span data-ttu-id="db525-146">ani większe niż lub równe`null`</span><span class="sxs-lookup"><span data-stu-id="db525-146">neither greater than or equal to `null`</span></span>
- <span data-ttu-id="db525-147">ani mniej niż`null`</span><span class="sxs-lookup"><span data-stu-id="db525-147">nor less than `null`</span></span>

[!code-csharp-interactive[relational and equality operators](snippets/NullableValueTypes.cs#ComparisonOperators)]

<span data-ttu-id="db525-148">Dla [operatora](../operators/equality-operators.md#equality-operator-) `==`równości , jeśli oba `null`argumenty są `true`, wynik jest, jeśli `null`tylko jeden `false`z argumentów jest , wynik jest ; w przeciwnym razie porównywane są zawarte wartości operandów.</span><span class="sxs-lookup"><span data-stu-id="db525-148">For the [equality operator](../operators/equality-operators.md#equality-operator-) `==`, if both operands are `null`, the result is `true`, if only one of the operands is `null`, the result is `false`; otherwise, the contained values of operands are compared.</span></span>

<span data-ttu-id="db525-149">Dla [operatora](../operators/equality-operators.md#inequality-operator-) `!=`nierówności , jeśli oba `null`argumenty są `false`, wynik jest, jeśli tylko `null`jeden z `true`argumentów jest , wynik jest ; w przeciwnym razie porównywane są zawarte wartości operandów.</span><span class="sxs-lookup"><span data-stu-id="db525-149">For the [inequality operator](../operators/equality-operators.md#inequality-operator-) `!=`, if both operands are `null`, the result is `false`, if only one of the operands is `null`, the result is `true`; otherwise, the contained values of operands are compared.</span></span>

<span data-ttu-id="db525-150">Jeśli istnieje [konwersja zdefiniowana przez użytkownika](../operators/user-defined-conversion-operators.md) między dwoma typami wartości, ta sama konwersja może być również używana między odpowiednimi typami wartości nullable.</span><span class="sxs-lookup"><span data-stu-id="db525-150">If there exists a [user-defined conversion](../operators/user-defined-conversion-operators.md) between two value types, the same conversion can also be used between the corresponding nullable value types.</span></span>

## <a name="boxing-and-unboxing"></a><span data-ttu-id="db525-151">Boks i rozpakowywanie</span><span class="sxs-lookup"><span data-stu-id="db525-151">Boxing and unboxing</span></span>

<span data-ttu-id="db525-152">Wystąpienie typu `T?` wartości możliwej do wartości null jest [zapakowane w](../../programming-guide/types/boxing-and-unboxing.md) następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="db525-152">An instance of a nullable value type `T?` is [boxed](../../programming-guide/types/boxing-and-unboxing.md) as follows:</span></span>

- <span data-ttu-id="db525-153">Jeśli <xref:System.Nullable%601.HasValue%2A> `false`zwraca , wywoływane jest odwołanie null.</span><span class="sxs-lookup"><span data-stu-id="db525-153">If <xref:System.Nullable%601.HasValue%2A> returns `false`, the null reference is produced.</span></span>
- <span data-ttu-id="db525-154">Jeśli <xref:System.Nullable%601.HasValue%2A> `true`zwraca , odpowiednia wartość `T` typu wartości podstawowej jest <xref:System.Nullable%601>zapakowana, a nie wystąpienie .</span><span class="sxs-lookup"><span data-stu-id="db525-154">If <xref:System.Nullable%601.HasValue%2A> returns `true`, the corresponding value of the underlying value type `T` is boxed, not the instance of <xref:System.Nullable%601>.</span></span>

<span data-ttu-id="db525-155">Można rozpakować wartość pudełkową typu `T` wartości do odpowiedniego `T?`typu wartości nullable , jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="db525-155">You can unbox a boxed value of a value type `T` to the corresponding nullable value type `T?`, as the following example shows:</span></span>

[!code-csharp-interactive[boxing and unboxing](snippets/NullableValueTypes.cs#Boxing)]

## <a name="how-to-identify-a-nullable-value-type"></a><span data-ttu-id="db525-156">Jak zidentyfikować typ wartości z do wartości możliwej do wartości null</span><span class="sxs-lookup"><span data-stu-id="db525-156">How to identify a nullable value type</span></span>

<span data-ttu-id="db525-157">Poniższy przykład pokazuje, jak <xref:System.Type?displayProperty=nameWithType> ustalić, czy wystąpienie reprezentuje skonstruowany <xref:System.Nullable%601?displayProperty=nameWithType> typ wartości nullable, czyli typ z określonym parametrem `T`typu:</span><span class="sxs-lookup"><span data-stu-id="db525-157">The following example shows how to determine whether a <xref:System.Type?displayProperty=nameWithType> instance represents a constructed nullable value type, that is, the <xref:System.Nullable%601?displayProperty=nameWithType> type with a specified type parameter `T`:</span></span>

[!code-csharp-interactive[whether Type is nullable](snippets/NullableValueTypes.cs#IsTypeNullable)]

<span data-ttu-id="db525-158">Jak pokazano w przykładzie, operator [typeof](../operators/type-testing-and-cast.md#typeof-operator) służy do tworzenia <xref:System.Type?displayProperty=nameWithType> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="db525-158">As the example shows, you use the [typeof](../operators/type-testing-and-cast.md#typeof-operator) operator to create a <xref:System.Type?displayProperty=nameWithType> instance.</span></span>

<span data-ttu-id="db525-159">Jeśli chcesz ustalić, czy wystąpienie ma typ wartości powodującej <xref:System.Object.GetType%2A?displayProperty=nameWithType> wartość null, <xref:System.Type> nie używaj metody, aby uzyskać wystąpienie do przetestowania z poprzednim kodem.</span><span class="sxs-lookup"><span data-stu-id="db525-159">If you want to determine whether an instance is of a nullable value type, don't use the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method to get a <xref:System.Type> instance to be tested with the preceding code.</span></span> <span data-ttu-id="db525-160">Po wywołaniu <xref:System.Object.GetType%2A?displayProperty=nameWithType> metody w wystąpieniu typu wartości możliwej do <xref:System.Object>wartości null, wystąpienie jest [zapakowane](#boxing-and-unboxing) do .</span><span class="sxs-lookup"><span data-stu-id="db525-160">When you call the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method on an instance of a nullable value type, the instance is [boxed](#boxing-and-unboxing) to <xref:System.Object>.</span></span> <span data-ttu-id="db525-161">Jako boks wystąpienia nie null typu wartości nullable jest odpowiednikiem boksu <xref:System.Object.GetType%2A> wartości <xref:System.Type> typu bazowego, zwraca wystąpienie, które reprezentuje podstawowy typ typu wartości nullable:</span><span class="sxs-lookup"><span data-stu-id="db525-161">As boxing of a non-null instance of a nullable value type is equivalent to boxing of a value of the underlying type, <xref:System.Object.GetType%2A> returns a <xref:System.Type> instance that represents the underlying type of a nullable value type:</span></span>

[!code-csharp-interactive[GetType example](snippets/NullableValueTypes.cs#GetType)]

<span data-ttu-id="db525-162">Ponadto nie należy używać operatora [is,](../operators/type-testing-and-cast.md#is-operator) aby ustalić, czy wystąpienie ma typ wartości nullable.</span><span class="sxs-lookup"><span data-stu-id="db525-162">Also, don't use the [is](../operators/type-testing-and-cast.md#is-operator) operator to determine whether an instance is of a nullable value type.</span></span> <span data-ttu-id="db525-163">Jak pokazano w poniższym przykładzie, nie można odróżnić typów wystąpienia `is` typu nullable i jego wystąpienia typu bazowego za pomocą operatora:</span><span class="sxs-lookup"><span data-stu-id="db525-163">As the following example shows, you cannot distinguish types of a nullable value type instance and its underlying type instance with the `is` operator:</span></span>

[!code-csharp-interactive[is operator example](snippets/NullableValueTypes.cs#IsOperator)]

<span data-ttu-id="db525-164">Można użyć kodu przedstawionego w poniższym przykładzie, aby ustalić, czy wystąpienie ma typ wartości nullable:</span><span class="sxs-lookup"><span data-stu-id="db525-164">You can use the code presented in the following example to determine whether an instance is of a nullable value type:</span></span>

[!code-csharp-interactive[whether an instance is of a nullable type](snippets/NullableValueTypes.cs#IsInstanceNullable)]

> [!NOTE]
> <span data-ttu-id="db525-165">Metody opisane w tej sekcji nie mają zastosowania w przypadku [typów odwołań, których można unieważnić.](nullable-reference-types.md)</span><span class="sxs-lookup"><span data-stu-id="db525-165">The methods described in this section are not applicable in the case of [nullable reference types](nullable-reference-types.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="db525-166">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="db525-166">C# language specification</span></span>

<span data-ttu-id="db525-167">Aby uzyskać więcej informacji, zobacz następujące sekcje [specyfikacji języka języka C#:](~/_csharplang/spec/introduction.md)</span><span class="sxs-lookup"><span data-stu-id="db525-167">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="db525-168">Typy nullowalne</span><span class="sxs-lookup"><span data-stu-id="db525-168">Nullable types</span></span>](~/_csharplang/spec/types.md#nullable-types)
- [<span data-ttu-id="db525-169">Operatorzy podnoszony</span><span class="sxs-lookup"><span data-stu-id="db525-169">Lifted operators</span></span>](~/_csharplang/spec/expressions.md#lifted-operators)
- [<span data-ttu-id="db525-170">Niejawne konwersje możliwe do unieważnienia</span><span class="sxs-lookup"><span data-stu-id="db525-170">Implicit nullable conversions</span></span>](~/_csharplang/spec/conversions.md#implicit-nullable-conversions)
- [<span data-ttu-id="db525-171">Jawne konwersje możliwe do unieważnienia</span><span class="sxs-lookup"><span data-stu-id="db525-171">Explicit nullable conversions</span></span>](~/_csharplang/spec/conversions.md#explicit-nullable-conversions)
- [<span data-ttu-id="db525-172">Udźwignięty operator konwersji</span><span class="sxs-lookup"><span data-stu-id="db525-172">Lifted conversion operators</span></span>](~/_csharplang/spec/conversions.md#lifted-conversion-operators)

## <a name="see-also"></a><span data-ttu-id="db525-173">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="db525-173">See also</span></span>

- [<span data-ttu-id="db525-174">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="db525-174">C# reference</span></span>](../index.md)
- [<span data-ttu-id="db525-175">Co dokładnie oznacza "podniesiony"?</span><span class="sxs-lookup"><span data-stu-id="db525-175">What exactly does 'lifted' mean?</span></span>](https://docs.microsoft.com/archive/blogs/ericlippert/what-exactly-does-lifted-mean)
- <xref:System.Nullable%601?displayProperty=nameWithType>
- <xref:System.Nullable?displayProperty=nameWithType>
- <xref:System.Nullable.GetUnderlyingType%2A?displayProperty=nameWithType>
- [<span data-ttu-id="db525-176">Typy referencyjne dopuszczające wartość null</span><span class="sxs-lookup"><span data-stu-id="db525-176">Nullable reference types</span></span>](nullable-reference-types.md)
