---
title: Korzystanie z typów wartości null C# — Przewodnik programowania
ms.custom: seodec18
description: Dowiedz się, jak C# korzystać z typów wartości null
ms.date: 09/26/2019
helpviewer_keywords:
- nullable types [C#], about nullable types
ms.assetid: 0bacbe72-ce15-4b14-83e1-9c14e6380c28
ms.openlocfilehash: 65fc3b0ca94f9a41c9375e96000449b52cb7db26
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71396164"
---
# <a name="using-nullable-value-types-c-programming-guide"></a><span data-ttu-id="7872f-103">Używanie typów wartości null (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="7872f-103">Using nullable value types (C# Programming Guide)</span></span>

<span data-ttu-id="7872f-104">Typy wartości null są typami, które reprezentują wszystkie wartości bazowego typu wartości `T` i dodatkową wartość [null](../../language-reference/keywords/null.md) .</span><span class="sxs-lookup"><span data-stu-id="7872f-104">Nullable value types are types that represent all the values of an underlying value type `T`, and an additional [null](../../language-reference/keywords/null.md) value.</span></span> <span data-ttu-id="7872f-105">Aby uzyskać więcej informacji, zobacz temat [typy wartości null](index.md) .</span><span class="sxs-lookup"><span data-stu-id="7872f-105">For more information, see the [Nullable value types](index.md) topic.</span></span>

> [!NOTE]
> <span data-ttu-id="7872f-106">C#8,0 wprowadza funkcję typów odwołań do wartości null.</span><span class="sxs-lookup"><span data-stu-id="7872f-106">C# 8.0 introduces the nullable reference types feature.</span></span> <span data-ttu-id="7872f-107">Aby uzyskać więcej informacji, zobacz [typy referencyjne dopuszczające wartość null](../../nullable-references.md).</span><span class="sxs-lookup"><span data-stu-id="7872f-107">For more information, see [Nullable reference types](../../nullable-references.md).</span></span> <span data-ttu-id="7872f-108">Typy wartości null są dostępne od C# 2.</span><span class="sxs-lookup"><span data-stu-id="7872f-108">The nullable value types are available starting with C# 2.</span></span>

<span data-ttu-id="7872f-109">Można odwołać się do typu wartości null w dowolnej z następujących metod zamiennych: `Nullable<T>` lub `T?`.</span><span class="sxs-lookup"><span data-stu-id="7872f-109">You can refer to a nullable value type in any of the following interchangeable forms: `Nullable<T>` or `T?`.</span></span> <span data-ttu-id="7872f-110">`T` musi być typem wartości.</span><span class="sxs-lookup"><span data-stu-id="7872f-110">`T` must be a value type.</span></span>

## <a name="declaration-and-assignment"></a><span data-ttu-id="7872f-111">Deklaracja i przypisanie</span><span class="sxs-lookup"><span data-stu-id="7872f-111">Declaration and assignment</span></span>

<span data-ttu-id="7872f-112">Ponieważ typ wartości może być niejawnie konwertowany do odpowiadającego typu wartości null, przypisujesz wartość do typu dopuszczającego wartości null jak dla jego bazowego typu wartości.</span><span class="sxs-lookup"><span data-stu-id="7872f-112">As a value type can be implicitly converted to the corresponding nullable value type, you assign a value to a nullable type as you would for its underlying value type.</span></span> <span data-ttu-id="7872f-113">Można również przypisać wartość `null`.</span><span class="sxs-lookup"><span data-stu-id="7872f-113">You also can assign the `null` value.</span></span> <span data-ttu-id="7872f-114">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="7872f-114">For example:</span></span>

[!code-csharp[declare and assign](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#1)]

## <a name="examination-of-a-nullable-type-value"></a><span data-ttu-id="7872f-115">Badanie wartości typu dopuszczającego wartość null</span><span class="sxs-lookup"><span data-stu-id="7872f-115">Examination of a nullable type value</span></span>

<span data-ttu-id="7872f-116">Użyj następujących właściwości tylko do odczytu w celu sprawdzenia wystąpienia typu wartości null dla wartości null i pobrania wartości typu podstawowego:</span><span class="sxs-lookup"><span data-stu-id="7872f-116">Use the following readonly properties to examine an instance of a nullable value type for null and retrieve a value of an underlying type:</span></span>

- <span data-ttu-id="7872f-117"><xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> wskazuje, czy wystąpienie typu wartości null ma wartość jego typu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="7872f-117"><xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> indicates whether an instance of a nullable type has a value of its underlying type.</span></span>

- <span data-ttu-id="7872f-118"><xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> pobiera wartość typu podstawowego, jeśli <xref:System.Nullable%601.HasValue%2A> jest `true`.</span><span class="sxs-lookup"><span data-stu-id="7872f-118"><xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> gets the value of an underlying type if <xref:System.Nullable%601.HasValue%2A> is `true`.</span></span> <span data-ttu-id="7872f-119">Jeśli <xref:System.Nullable%601.HasValue%2A> jest `false`, właściwość <xref:System.Nullable%601.Value%2A> zgłasza <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="7872f-119">If <xref:System.Nullable%601.HasValue%2A> is `false`, the <xref:System.Nullable%601.Value%2A> property throws an <xref:System.InvalidOperationException>.</span></span>

<span data-ttu-id="7872f-120">W poniższym przykładzie kod używa właściwości `HasValue` do sprawdzenia, czy zmienna zawiera wartość przed wyświetleniem:</span><span class="sxs-lookup"><span data-stu-id="7872f-120">The code in the following example uses the `HasValue` property to test whether the variable contains a value before displaying it:</span></span>

[!code-csharp-interactive[use HasValue](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#2)]

<span data-ttu-id="7872f-121">Można także porównać zmienną typu wartości null z `null` zamiast używać właściwości `HasValue`, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="7872f-121">You also can compare a variable of a nullable value type with `null` instead of using the `HasValue` property, as the following example shows:</span></span>

[!code-csharp-interactive[use comparison with null](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#3)]

<span data-ttu-id="7872f-122">Począwszy od C# 7,0, można użyć [dopasowania wzorca](../../pattern-matching.md) do obu badań i pobrać wartość typu wartości null:</span><span class="sxs-lookup"><span data-stu-id="7872f-122">Beginning with C# 7.0, you can use [pattern matching](../../pattern-matching.md) to both examine and get a value of a nullable value type:</span></span>

[!code-csharp-interactive[use pattern matching](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#4)]

## <a name="conversion-from-a-nullable-value-type-to-an-underlying-type"></a><span data-ttu-id="7872f-123">Konwersja z typu wartości null na typ podstawowy</span><span class="sxs-lookup"><span data-stu-id="7872f-123">Conversion from a nullable value type to an underlying type</span></span>

<span data-ttu-id="7872f-124">Jeśli musisz przypisać wartość typu wartości null do typu, który nie dopuszcza wartości null, użyj [operatora łączenia wartości null `??`](../../language-reference/operators/null-coalescing-operator.md) , aby określić wartość, która ma zostać przypisana, jeśli wartość typu wartości null jest równa null (można również użyć metody <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType>, aby to zrobić) :</span><span class="sxs-lookup"><span data-stu-id="7872f-124">If you need to assign a value of a nullable value type to a non-nullable type, use the [null-coalescing operator `??`](../../language-reference/operators/null-coalescing-operator.md) to specify the value to be assigned if a value of a nullable value type is null (you also can use the <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> method to do that):</span></span>

[!code-csharp-interactive[?? operator](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#5)]

<span data-ttu-id="7872f-125">Użyj metody <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType>, jeśli wartość, która ma zostać użyta, gdy wartość typu wartości null jest `null` powinna być wartością domyślną bazowego typu wartości.</span><span class="sxs-lookup"><span data-stu-id="7872f-125">Use the <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> method if the value to be used when a value of a nullable value type is `null` should be the default value of the underlying value type.</span></span>

<span data-ttu-id="7872f-126">Można jawnie rzutować typ wartości null na typ, który nie dopuszcza wartości null.</span><span class="sxs-lookup"><span data-stu-id="7872f-126">You can explicitly cast a nullable value type to a non-nullable type.</span></span> <span data-ttu-id="7872f-127">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="7872f-127">For example:</span></span>

[!code-csharp[explicit cast](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#6)]

<span data-ttu-id="7872f-128">W czasie wykonywania, jeśli wartość typu wartości null jest `null`, jawne rzutowanie zgłasza <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="7872f-128">At run time, if the value of a nullable value type is `null`, the explicit cast throws an <xref:System.InvalidOperationException>.</span></span>

<span data-ttu-id="7872f-129">Typ wartości niedopuszczający wartości null jest niejawnie konwertowany na odpowiedni typ dopuszczający wartość null.</span><span class="sxs-lookup"><span data-stu-id="7872f-129">A non-nullable value type is implicitly converted to the corresponding nullable type.</span></span>

## <a name="operators"></a><span data-ttu-id="7872f-130">Operatory</span><span class="sxs-lookup"><span data-stu-id="7872f-130">Operators</span></span>

<span data-ttu-id="7872f-131">Wstępnie zdefiniowane operatory jednoargumentowe i binarne oraz wszelkie Operatory zdefiniowane przez użytkownika, które istnieją dla typów wartości mogą również być używane przez odpowiednie typy dopuszczające wartość null.</span><span class="sxs-lookup"><span data-stu-id="7872f-131">The predefined unary and binary operators and any user-defined operators that exist for value types may also be used by corresponding nullable types.</span></span> <span data-ttu-id="7872f-132">Te operatory generują `null`, jeśli jeden lub oba operandy są `null`; w przeciwnym razie operator używa zawartych wartości, aby obliczyć wynik.</span><span class="sxs-lookup"><span data-stu-id="7872f-132">These operators produce `null` if one or both operands are `null`; otherwise, the operator uses the contained values to calculate the result.</span></span> <span data-ttu-id="7872f-133">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="7872f-133">For example:</span></span>

[!code-csharp[operators](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#7)]

> [!NOTE]
> <span data-ttu-id="7872f-134">W przypadku typu `bool?` wstępnie zdefiniowane operatory `&` i `|` nie przestrzegają reguł opisanych w tej sekcji: wynik oceny operatora może być inny niż null, nawet jeśli jeden z operandów jest `null`.</span><span class="sxs-lookup"><span data-stu-id="7872f-134">For the `bool?` type, the predefined `&` and `|` operators don't follow the rules described in this section: the result of an operator evaluation can be non-null even if one of the operands is `null`.</span></span> <span data-ttu-id="7872f-135">Aby uzyskać więcej informacji, zobacz sekcję [Operatory logiczne wartości null](../../language-reference/operators/boolean-logical-operators.md#nullable-boolean-logical-operators) w artykule [Operatory logiczne Boolean](../../language-reference/operators/boolean-logical-operators.md) .</span><span class="sxs-lookup"><span data-stu-id="7872f-135">For more information, see the [Nullable Boolean logical operators](../../language-reference/operators/boolean-logical-operators.md#nullable-boolean-logical-operators) section of the [Boolean logical operators](../../language-reference/operators/boolean-logical-operators.md) article.</span></span>
  
<span data-ttu-id="7872f-136">Dla operatorów relacyjnych (`<`, `>`, `<=`, `>=`), jeśli jeden lub oba operandy są `null`, wynik jest `false`.</span><span class="sxs-lookup"><span data-stu-id="7872f-136">For the relational operators (`<`, `>`, `<=`, `>=`), if one or both operands are `null`, the result is `false`.</span></span> <span data-ttu-id="7872f-137">Nie należy zakładać, że ponieważ określone porównanie (na przykład `<=`) zwraca `false`, przeciwieństwo porównania (`>`) zwraca `true`.</span><span class="sxs-lookup"><span data-stu-id="7872f-137">Do not assume that because a particular comparison (for example, `<=`) returns `false`, the opposite comparison (`>`) returns `true`.</span></span> <span data-ttu-id="7872f-138">Poniższy przykład pokazuje, że 10 jest</span><span class="sxs-lookup"><span data-stu-id="7872f-138">The following example shows that 10 is</span></span>

- <span data-ttu-id="7872f-139">nie większe niż ani równe `null`,</span><span class="sxs-lookup"><span data-stu-id="7872f-139">neither greater than or equal to `null`,</span></span>
- <span data-ttu-id="7872f-140">nie mniej niż `null`.</span><span class="sxs-lookup"><span data-stu-id="7872f-140">nor less than `null`.</span></span>

[!code-csharp-interactive[relational and equality operators](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#8)]

<span data-ttu-id="7872f-141">Powyższy przykład pokazuje również, że porównanie równości dwóch typów wartości null, które mają wartość null, jest równe `true`.</span><span class="sxs-lookup"><span data-stu-id="7872f-141">The above example also shows that an equality comparison of two nullable value types that are both null evaluates to `true`.</span></span>

<span data-ttu-id="7872f-142">Aby uzyskać więcej informacji, zobacz sekcję [zniesione operatory](~/_csharplang/spec/expressions.md#lifted-operators) w [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="7872f-142">For more information, see the [Lifted operators](~/_csharplang/spec/expressions.md#lifted-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="boxing-and-unboxing"></a><span data-ttu-id="7872f-143">Pakowanie i rozpakowywanie</span><span class="sxs-lookup"><span data-stu-id="7872f-143">Boxing and unboxing</span></span>

<span data-ttu-id="7872f-144">Typ wartości null jest [opakowany](../types/boxing-and-unboxing.md) przez następujące reguły:</span><span class="sxs-lookup"><span data-stu-id="7872f-144">A nullable value type is [boxed](../types/boxing-and-unboxing.md) by the following rules:</span></span>

- <span data-ttu-id="7872f-145">Jeśli <xref:System.Nullable%601.HasValue%2A> zwraca `false`, tworzone jest odwołanie o wartości null.</span><span class="sxs-lookup"><span data-stu-id="7872f-145">If <xref:System.Nullable%601.HasValue%2A> returns `false`, the null reference is produced.</span></span>
- <span data-ttu-id="7872f-146">Jeśli <xref:System.Nullable%601.HasValue%2A> zwraca `true`, wartość bazowego typu wartości `T` jest opakowany, a nie wystąpieniem <xref:System.Nullable%601>.</span><span class="sxs-lookup"><span data-stu-id="7872f-146">If <xref:System.Nullable%601.HasValue%2A> returns `true`, a value of the underlying value type `T` is boxed, not the instance of <xref:System.Nullable%601>.</span></span>

<span data-ttu-id="7872f-147">Można Unbox opakowany typ wartości do odpowiedniego typu dopuszczającego wartość null, co ilustruje poniższy przykład:</span><span class="sxs-lookup"><span data-stu-id="7872f-147">You can unbox the boxed value type to the corresponding nullable type, as the following example shows:</span></span>

[!code-csharp-interactive[boxing and unboxing](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#9)]

## <a name="see-also"></a><span data-ttu-id="7872f-148">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7872f-148">See also</span></span>

- [<span data-ttu-id="7872f-149">Typy wartości null</span><span class="sxs-lookup"><span data-stu-id="7872f-149">Nullable value types</span></span>](index.md)
- [<span data-ttu-id="7872f-150">Co dokładnie ma znaczenie "zniesione"?</span><span class="sxs-lookup"><span data-stu-id="7872f-150">What exactly does 'lifted' mean?</span></span>](https://blogs.msdn.microsoft.com/ericlippert/2007/06/27/what-exactly-does-lifted-mean/)
