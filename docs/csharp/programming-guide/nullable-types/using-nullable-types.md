---
title: Korzystanie z typów dopuszczających wartość null — C# Przewodnik programowania
ms.custom: seodec18
description: Dowiedz się, jak C# korzystać z typów dopuszczających wartość null
ms.date: 08/02/2018
helpviewer_keywords:
- nullable types [C#], about nullable types
ms.assetid: 0bacbe72-ce15-4b14-83e1-9c14e6380c28
ms.openlocfilehash: 75b8889f5f1f1b0dab4aa365daa34ef5ae226b02
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588833"
---
# <a name="using-nullable-types-c-programming-guide"></a><span data-ttu-id="44ae8-103">Korzystanie z typów dopuszczających wartość null (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="44ae8-103">Using nullable types (C# Programming Guide)</span></span>

<span data-ttu-id="44ae8-104">Typy dopuszczające wartości null to typy reprezentujące wszystkie wartości bazowego typu `T`wartości oraz dodatkową wartość [null](../../language-reference/keywords/null.md) .</span><span class="sxs-lookup"><span data-stu-id="44ae8-104">Nullable types are types that represent all the values of an underlying value type `T`, and an additional [null](../../language-reference/keywords/null.md) value.</span></span> <span data-ttu-id="44ae8-105">Aby uzyskać więcej informacji, zobacz temat [Typy dopuszczające wartość null](index.md) .</span><span class="sxs-lookup"><span data-stu-id="44ae8-105">For more information, see the [Nullable types](index.md) topic.</span></span>

<span data-ttu-id="44ae8-106">Można odwołać się do typu dopuszczającego wartość null w dowolnej z `Nullable<T>` następujących `T?`form: lub.</span><span class="sxs-lookup"><span data-stu-id="44ae8-106">You can refer to a nullable type in any of the following forms: `Nullable<T>` or `T?`.</span></span> <span data-ttu-id="44ae8-107">Te dwa formularze są zamienne.</span><span class="sxs-lookup"><span data-stu-id="44ae8-107">These two forms are interchangeable.</span></span>  
  
## <a name="declaration-and-assignment"></a><span data-ttu-id="44ae8-108">Deklaracja i przypisanie</span><span class="sxs-lookup"><span data-stu-id="44ae8-108">Declaration and assignment</span></span>

<span data-ttu-id="44ae8-109">Jako typ wartości można niejawnie skonwertować do odpowiadającego typu dopuszczającego wartość null, można przypisać wartości do typu dopuszczającego wartość null jak dla jego bazowego typu wartości.</span><span class="sxs-lookup"><span data-stu-id="44ae8-109">As a value type can be implicitly converted to the corresponding nullable type, you assign a value to a nullable type as you would for its underlying value type.</span></span> <span data-ttu-id="44ae8-110">Możesz również przypisać `null` wartość.</span><span class="sxs-lookup"><span data-stu-id="44ae8-110">You also can assign the `null` value.</span></span>  <span data-ttu-id="44ae8-111">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="44ae8-111">For example:</span></span>
  
[!code-csharp[declare and assign](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#1)]

## <a name="examination-of-a-nullable-type-value"></a><span data-ttu-id="44ae8-112">Badanie wartości typu dopuszczającego wartość null</span><span class="sxs-lookup"><span data-stu-id="44ae8-112">Examination of a nullable type value</span></span>

<span data-ttu-id="44ae8-113">Użyj następujących właściwości tylko do odczytu, aby przeanalizować wystąpienie typu dopuszczającego wartość null w celu wyzerowania i pobrać wartość typu podstawowego:</span><span class="sxs-lookup"><span data-stu-id="44ae8-113">Use the following readonly properties to examine an instance of a nullable type for null and retrieve a value of an underlying type:</span></span>  
  
- <span data-ttu-id="44ae8-114"><xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType>wskazuje, czy wystąpienie typu wartości null ma wartość jego typu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="44ae8-114"><xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> indicates whether an instance of a nullable type has a value of its underlying type.</span></span>
  
- <span data-ttu-id="44ae8-115"><xref:System.Nullable%601.Value%2A?displayProperty=nameWithType>Pobiera wartość typu podstawowego, jeśli <xref:System.Nullable%601.HasValue%2A> jest. `true`</span><span class="sxs-lookup"><span data-stu-id="44ae8-115"><xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> gets the value of an underlying type if <xref:System.Nullable%601.HasValue%2A> is `true`.</span></span> <span data-ttu-id="44ae8-116">Jeśli <xref:System.Nullable%601.HasValue%2A> ma `false`wartość ,<xref:System.Nullable%601.Value%2A>Właściwość zgłasza .<xref:System.InvalidOperationException></span><span class="sxs-lookup"><span data-stu-id="44ae8-116">If <xref:System.Nullable%601.HasValue%2A> is `false`, the <xref:System.Nullable%601.Value%2A> property throws an <xref:System.InvalidOperationException>.</span></span>
  
<span data-ttu-id="44ae8-117">Kod w poniższym przykładzie używa właściwości, `HasValue` aby sprawdzić, czy zmienna zawiera wartość przed wyświetleniem:</span><span class="sxs-lookup"><span data-stu-id="44ae8-117">The code in the following example uses the `HasValue` property to test whether the variable contains a value before displaying it:</span></span>
  
[!code-csharp-interactive[use HasValue](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#2)]
  
<span data-ttu-id="44ae8-118">Możesz również porównać zmienną typu Nullable z `null` zamiast `HasValue` używać właściwości, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="44ae8-118">You also can compare a nullable type variable with `null` instead of using the `HasValue` property, as the following example shows:</span></span>  
  
[!code-csharp-interactive[use comparison with null](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#3)]

<span data-ttu-id="44ae8-119">Począwszy od C# 7,0, można użyć [dopasowania wzorca](../../pattern-matching.md) do obu badań i pobrać wartość typu dopuszczającego wartości null:</span><span class="sxs-lookup"><span data-stu-id="44ae8-119">Beginning with C# 7.0, you can use [pattern matching](../../pattern-matching.md) to both examine and get a value of a nullable type:</span></span>

[!code-csharp-interactive[use pattern matching](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#4)]

## <a name="conversion-from-a-nullable-type-to-an-underlying-type"></a><span data-ttu-id="44ae8-120">Konwersja z typu dopuszczającego wartość null na typ podstawowy</span><span class="sxs-lookup"><span data-stu-id="44ae8-120">Conversion from a nullable type to an underlying type</span></span>

<span data-ttu-id="44ae8-121">Jeśli musisz przypisać wartość typu null do typu niedopuszczający wartości null, użyj [operatora `??` łączenia wartości null](../../language-reference/operators/null-coalescing-operator.md) , aby określić wartość, która ma zostać przypisana, jeśli wartość typu null jest równa null (można <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> również użyć metody, aby to zrobić):</span><span class="sxs-lookup"><span data-stu-id="44ae8-121">If you need to assign a nullable type value to a non-nullable type, use the [null-coalescing operator `??`](../../language-reference/operators/null-coalescing-operator.md) to specify the value to be assigned if a nullable type value is null (you also can use the <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> method to do that):</span></span>
  
[!code-csharp-interactive[?? operator](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#5)]

<span data-ttu-id="44ae8-122">Użyj metody <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> , jeśli wartość, która ma zostać użyta, gdy wartość typu null jest równa null powinna być wartością domyślną bazowego typu wartości.</span><span class="sxs-lookup"><span data-stu-id="44ae8-122">Use the <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> method if the value to be used when a nullable type value is null should be the default value of the underlying value type.</span></span>
  
<span data-ttu-id="44ae8-123">Typ dopuszczający wartość null można jawnie rzutować na typ, który nie dopuszcza wartości null.</span><span class="sxs-lookup"><span data-stu-id="44ae8-123">You can explicitly cast a nullable type to a non-nullable type.</span></span> <span data-ttu-id="44ae8-124">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="44ae8-124">For example:</span></span>  
  
[!code-csharp[explicit cast](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#6)]

<span data-ttu-id="44ae8-125">W czasie wykonywania, jeśli wartość typu Nullable ma wartość null, jawne rzutowanie zgłosi <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="44ae8-125">At run time, if the value of a nullable type is null, the explicit cast throws an <xref:System.InvalidOperationException>.</span></span>

<span data-ttu-id="44ae8-126">Typ wartości niedopuszczający wartości null jest niejawnie konwertowany na odpowiedni typ dopuszczający wartość null.</span><span class="sxs-lookup"><span data-stu-id="44ae8-126">A non-nullable value type is implicitly converted to the corresponding nullable type.</span></span>
  
## <a name="operators"></a><span data-ttu-id="44ae8-127">Operatory</span><span class="sxs-lookup"><span data-stu-id="44ae8-127">Operators</span></span>

<span data-ttu-id="44ae8-128">Wstępnie zdefiniowane operatory jednoargumentowe i binarne oraz wszelkie Operatory zdefiniowane przez użytkownika, które istnieją dla typów wartości mogą być również używane przez Typy dopuszczające wartość null.</span><span class="sxs-lookup"><span data-stu-id="44ae8-128">The predefined unary and binary operators and any user-defined operators that exist for value types may also be used by nullable types.</span></span> <span data-ttu-id="44ae8-129">Te operatory tworzą wartość null, jeśli jeden lub oba operandy mają wartość null; w przeciwnym razie operator używa zawartych wartości, aby obliczyć wynik.</span><span class="sxs-lookup"><span data-stu-id="44ae8-129">These operators produce a null value if one or both operands are null; otherwise, the operator uses the contained values to calculate the result.</span></span> <span data-ttu-id="44ae8-130">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="44ae8-130">For example:</span></span>  
  
[!code-csharp[operators](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#7)]

> [!NOTE]
> <span data-ttu-id="44ae8-131">Dla typu, wstępnie zdefiniowane `&` operatory i `|` nie przestrzegają zasad opisanych w tej sekcji: wynik oceny operatora może być inny niż null, nawet jeśli jeden z operandów ma wartość null. `bool?`</span><span class="sxs-lookup"><span data-stu-id="44ae8-131">For the `bool?` type, the predefined `&` and `|` operators don't follow the rules described in this section: the result of an operator evaluation can be non-null even if one of the operands is null.</span></span> <span data-ttu-id="44ae8-132">Aby uzyskać więcej informacji, zobacz sekcję [Operatory logiczne wartości null](../../language-reference/operators/boolean-logical-operators.md#nullable-boolean-logical-operators) w artykule [Operatory logiczne Boolean](../../language-reference/operators/boolean-logical-operators.md) .</span><span class="sxs-lookup"><span data-stu-id="44ae8-132">For more information, see the [Nullable Boolean logical operators](../../language-reference/operators/boolean-logical-operators.md#nullable-boolean-logical-operators) section of the [Boolean logical operators](../../language-reference/operators/boolean-logical-operators.md) article.</span></span>
  
<span data-ttu-id="44ae8-133">W przypadku operatorów relacyjnych`<`( `>`, `<=`, `>=`,), jeśli jeden lub oba operandy mają wartość null, wynik `false`to.</span><span class="sxs-lookup"><span data-stu-id="44ae8-133">For the relational operators (`<`, `>`, `<=`, `>=`), if one or both operands are null, the result is `false`.</span></span> <span data-ttu-id="44ae8-134">Nie należy zakładać, że ponieważ określone porównanie (na przykład `<=`) zwraca `false`, odwrotne porównanie (`>`) zwraca `true`wartość.</span><span class="sxs-lookup"><span data-stu-id="44ae8-134">Do not assume that because a particular comparison (for example, `<=`) returns `false`, the opposite comparison (`>`) returns `true`.</span></span> <span data-ttu-id="44ae8-135">Poniższy przykład pokazuje, że 10 jest</span><span class="sxs-lookup"><span data-stu-id="44ae8-135">The following example shows that 10 is</span></span>

- <span data-ttu-id="44ae8-136">nie może być większa niż lub równa null,</span><span class="sxs-lookup"><span data-stu-id="44ae8-136">neither greater than or equal to null,</span></span>
- <span data-ttu-id="44ae8-137">ani mniejsze od wartości null.</span><span class="sxs-lookup"><span data-stu-id="44ae8-137">nor less than null.</span></span>
  
[!code-csharp-interactive[relational and equality operators](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#8)]
  
<span data-ttu-id="44ae8-138">Powyższy przykład pokazuje również, że porównanie równości dwóch typów dopuszczających wartości null, które są równe zero `true`.</span><span class="sxs-lookup"><span data-stu-id="44ae8-138">The above example also shows that an equality comparison of two nullable types that are both null evaluates to `true`.</span></span>

<span data-ttu-id="44ae8-139">Aby uzyskać więcej informacji, zobacz sekcję [zniesione operatory](~/_csharplang/spec/expressions.md#lifted-operators) w [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="44ae8-139">For more information, see the [Lifted operators](~/_csharplang/spec/expressions.md#lifted-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="boxing-and-unboxing"></a><span data-ttu-id="44ae8-140">Pakowanie i rozpakowywanie</span><span class="sxs-lookup"><span data-stu-id="44ae8-140">Boxing and unboxing</span></span>

<span data-ttu-id="44ae8-141">Typ wartości null jest [opakowany](../types/boxing-and-unboxing.md) przez następujące reguły:</span><span class="sxs-lookup"><span data-stu-id="44ae8-141">A nullable value type is [boxed](../types/boxing-and-unboxing.md) by the following rules:</span></span>

- <span data-ttu-id="44ae8-142">Jeśli <xref:System.Nullable%601.HasValue%2A> zwraca`false`, zostanie utworzone odwołanie o wartości null.</span><span class="sxs-lookup"><span data-stu-id="44ae8-142">If <xref:System.Nullable%601.HasValue%2A> returns `false`, the null reference is produced.</span></span>  
- <span data-ttu-id="44ae8-143">Jeśli <xref:System.Nullable%601.HasValue%2A> `T` <xref:System.Nullable%601>zwraca `true`, wartość bazowego typu wartości jest opakowana, a nie wystąpieniem.</span><span class="sxs-lookup"><span data-stu-id="44ae8-143">If <xref:System.Nullable%601.HasValue%2A> returns `true`, a value of the underlying value type `T` is boxed, not the instance of <xref:System.Nullable%601>.</span></span>

<span data-ttu-id="44ae8-144">Można Unbox opakowany typ wartości do odpowiedniego typu dopuszczającego wartość null, co ilustruje poniższy przykład:</span><span class="sxs-lookup"><span data-stu-id="44ae8-144">You can unbox the boxed value type to the corresponding nullable type, as the following example shows:</span></span>

[!code-csharp-interactive[boxing and unboxing](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#9)]

## <a name="see-also"></a><span data-ttu-id="44ae8-145">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="44ae8-145">See also</span></span>

- [<span data-ttu-id="44ae8-146">Typy dopuszczające wartości null</span><span class="sxs-lookup"><span data-stu-id="44ae8-146">Nullable types</span></span>](index.md)
- [<span data-ttu-id="44ae8-147">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="44ae8-147">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="44ae8-148">Co dokładnie ma znaczenie "zniesione"?</span><span class="sxs-lookup"><span data-stu-id="44ae8-148">What exactly does 'lifted' mean?</span></span>](https://blogs.msdn.microsoft.com/ericlippert/2007/06/27/what-exactly-does-lifted-mean/)
