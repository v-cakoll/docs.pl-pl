---
title: Przy użyciu typów dopuszczających wartości zerowe — C# Programming Guide
ms.custom: seodec18
description: Dowiedz się, jak pracować z typami zerowalnymi C#
ms.date: 08/02/2018
helpviewer_keywords:
- nullable types [C#], about nullable types
ms.assetid: 0bacbe72-ce15-4b14-83e1-9c14e6380c28
ms.openlocfilehash: 5e468641efd4627c887d9a980fc4ed1129196e20
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54658250"
---
# <a name="using-nullable-types-c-programming-guide"></a><span data-ttu-id="a0b72-103">Przy użyciu typów dopuszczających wartości zerowe (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="a0b72-103">Using nullable types (C# Programming Guide)</span></span>

<span data-ttu-id="a0b72-104">Typy dopuszczające wartości zerowe są typami, które reprezentują wartości typu podstawowego wartość `T`wraz z dodatkowymi [null](../../language-reference/keywords/null.md) wartość.</span><span class="sxs-lookup"><span data-stu-id="a0b72-104">Nullable types are types that represent all the values of an underlying value type `T`, and an additional [null](../../language-reference/keywords/null.md) value.</span></span> <span data-ttu-id="a0b72-105">Aby uzyskać więcej informacji, zobacz [typów dopuszczających wartości zerowe](index.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="a0b72-105">For more information, see the [Nullable types](index.md) topic.</span></span>

<span data-ttu-id="a0b72-106">Możesz zapoznać się z typu dopuszczającego wartość null w dowolnej z następujących form: `Nullable<T>` lub `T?`.</span><span class="sxs-lookup"><span data-stu-id="a0b72-106">You can refer to a nullable type in any of the following forms: `Nullable<T>` or `T?`.</span></span> <span data-ttu-id="a0b72-107">Te dwa formularze są wymienne.</span><span class="sxs-lookup"><span data-stu-id="a0b72-107">These two forms are interchangeable.</span></span>  
  
## <a name="declaration-and-assignment"></a><span data-ttu-id="a0b72-108">Deklarację i przypisanie</span><span class="sxs-lookup"><span data-stu-id="a0b72-108">Declaration and assignment</span></span>

<span data-ttu-id="a0b72-109">Zgodnie z typem wartości mogą być niejawnie konwertowane na odpowiedni typ dopuszczający wartość null, podobnie jak w przypadku jej typ podstawowy wartość możesz przypisać wartości do typu dopuszczającego wartość null.</span><span class="sxs-lookup"><span data-stu-id="a0b72-109">As a value type can be implicitly converted to the corresponding nullable type, you assign a value to a nullable type as you would for its underlying value type.</span></span> <span data-ttu-id="a0b72-110">Możesz również przypisać `null` wartość.</span><span class="sxs-lookup"><span data-stu-id="a0b72-110">You also can assign the `null` value.</span></span>  <span data-ttu-id="a0b72-111">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="a0b72-111">For example:</span></span>
  
[!code-csharp[declare and assign](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#1)]

## <a name="examination-of-a-nullable-type-value"></a><span data-ttu-id="a0b72-112">Badanie wartości typu dopuszczającego wartość null</span><span class="sxs-lookup"><span data-stu-id="a0b72-112">Examination of a nullable type value</span></span>

<span data-ttu-id="a0b72-113">Użyj następujących właściwości tylko do odczytu do badania wystąpienie typu dopuszczającego wartość null w przypadku wartości null i pobierania wartości typu podstawowego:</span><span class="sxs-lookup"><span data-stu-id="a0b72-113">Use the following readonly properties to examine an instance of a nullable type for null and retrieve a value of an underlying type:</span></span>  
  
- <span data-ttu-id="a0b72-114"><xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> Wskazuje, czy wystąpienie typu dopuszczającego wartość null, ma wartość jego typ podstawowy.</span><span class="sxs-lookup"><span data-stu-id="a0b72-114"><xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> indicates whether an instance of a nullable type has a value of its underlying type.</span></span>
  
- <span data-ttu-id="a0b72-115"><xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> pobiera wartość typu podstawowego, jeśli <xref:System.Nullable%601.HasValue%2A> jest `true`.</span><span class="sxs-lookup"><span data-stu-id="a0b72-115"><xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> gets the value of an underlying type if <xref:System.Nullable%601.HasValue%2A> is `true`.</span></span> <span data-ttu-id="a0b72-116">Jeśli <xref:System.Nullable%601.HasValue%2A> jest `false`, <xref:System.Nullable%601.Value%2A> zgłasza właściwości <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="a0b72-116">If <xref:System.Nullable%601.HasValue%2A> is `false`, the <xref:System.Nullable%601.Value%2A> property throws an <xref:System.InvalidOperationException>.</span></span>
  
<span data-ttu-id="a0b72-117">W kodzie w poniższym przykładzie użyto `HasValue` właściwości, aby sprawdzić, czy zmienna zawiera wartość, przed wyświetleniem go:</span><span class="sxs-lookup"><span data-stu-id="a0b72-117">The code in the following example uses the `HasValue` property to test whether the variable contains a value before displaying it:</span></span>
  
[!code-csharp-interactive[use HasValue](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#2)]
  
<span data-ttu-id="a0b72-118">Można również porównać zmienną typu dopuszczającego wartość null z `null` zamiast `HasValue` właściwości, co ilustruje poniższy przykład:</span><span class="sxs-lookup"><span data-stu-id="a0b72-118">You also can compare a nullable type variable with `null` instead of using the `HasValue` property, as the following example shows:</span></span>  
  
[!code-csharp-interactive[use comparison with null](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#3)]

<span data-ttu-id="a0b72-119">Począwszy od języka C# 7.0, można użyć [dopasowywania do wzorca](../../pattern-matching.md) do zbadania i Pobierz wartość typu dopuszczającego wartość null:</span><span class="sxs-lookup"><span data-stu-id="a0b72-119">Beginning with C# 7.0, you can use [pattern matching](../../pattern-matching.md) to both examine and get a value of a nullable type:</span></span>

[!code-csharp-interactive[use pattern matching](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#4)]

## <a name="conversion-from-a-nullable-type-to-an-underlying-type"></a><span data-ttu-id="a0b72-120">Konwersja z typu dopuszczającego wartość null na typ podstawowy</span><span class="sxs-lookup"><span data-stu-id="a0b72-120">Conversion from a nullable type to an underlying type</span></span>

<span data-ttu-id="a0b72-121">Jeśli musisz przypisać do typów innych niż NULL wartość typu dopuszczającego wartość null, użyj [operatorem łączenia wartości null `??` ](../../language-reference/operators/null-coalescing-operator.md) określić wartość do przypisania, jeśli wartość typu dopuszczającego wartość null jest równa null (możesz też użyć <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> celu metodę który):</span><span class="sxs-lookup"><span data-stu-id="a0b72-121">If you need to assign a nullable type value to a non-nullable type, use the [null-coalescing operator `??`](../../language-reference/operators/null-coalescing-operator.md) to specify the value to be assigned if a nullable type value is null (you also can use the <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> method to do that):</span></span>
  
[!code-csharp-interactive[?? operator](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#5)]

<span data-ttu-id="a0b72-122">Użyj <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> metodę, jeśli wartość ma być używany, gdy wartość typu dopuszczającego wartość null jest równa null powinna być wartością domyślną typu wartości podstawowej.</span><span class="sxs-lookup"><span data-stu-id="a0b72-122">Use the <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> method if the value to be used when a nullable type value is null should be the default value of the underlying value type.</span></span>
  
<span data-ttu-id="a0b72-123">Można jawnie rzutowane typu dopuszczającego wartość null do niedopuszczającej typu.</span><span class="sxs-lookup"><span data-stu-id="a0b72-123">You can explicitly cast a nullable type to a non-nullable type.</span></span> <span data-ttu-id="a0b72-124">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="a0b72-124">For example:</span></span>  
  
[!code-csharp[explicit cast](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#6)]

<span data-ttu-id="a0b72-125">W czasie wykonywania, jeśli wartość typu dopuszczającego wartość null jest pusta, jawnego rzutowania zgłasza <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="a0b72-125">At run time, if the value of a nullable type is null, the explicit cast throws an <xref:System.InvalidOperationException>.</span></span>

<span data-ttu-id="a0b72-126">Typem wartościowym niebędącym jest niejawnie konwertowany na odpowiedni typ dopuszczający wartość null.</span><span class="sxs-lookup"><span data-stu-id="a0b72-126">A non-nullable value type is implicitly converted to the corresponding nullable type.</span></span>
  
## <a name="operators"></a><span data-ttu-id="a0b72-127">Operatory</span><span class="sxs-lookup"><span data-stu-id="a0b72-127">Operators</span></span>

<span data-ttu-id="a0b72-128">Jednoargumentowy wstępnie zdefiniowanych i operatory binarne i zdefiniowane przez użytkownika operatory, które istnieją w przypadku typów wartości może również używane przez typy dopuszczające wartości null.</span><span class="sxs-lookup"><span data-stu-id="a0b72-128">The predefined unary and binary operators and any user-defined operators that exist for value types may also be used by nullable types.</span></span> <span data-ttu-id="a0b72-129">Te operatory generuje wartość null, jeśli jeden lub oba operandy są null; w przeciwnym razie operator używa wartości zawartej do obliczania wyniku.</span><span class="sxs-lookup"><span data-stu-id="a0b72-129">These operators produce a null value if one or both operands are null; otherwise, the operator uses the contained values to calculate the result.</span></span> <span data-ttu-id="a0b72-130">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="a0b72-130">For example:</span></span>  
  
[!code-csharp[operators](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#7)]
  
<span data-ttu-id="a0b72-131">Dla operatorów relacyjnych (`<`, `>`, `<=`, `>=`), jeśli jeden lub oba argumenty mają wartość null, wynik jest `false`.</span><span class="sxs-lookup"><span data-stu-id="a0b72-131">For the relational operators (`<`, `>`, `<=`, `>=`), if one or both operands are null, the result is `false`.</span></span> <span data-ttu-id="a0b72-132">Nie przyjęto założenie, że ponieważ danym porównaniu (na przykład `<=`) zwraca `false`, przeciwne porównania (`>`) zwraca `true`.</span><span class="sxs-lookup"><span data-stu-id="a0b72-132">Do not assume that because a particular comparison (for example, `<=`) returns `false`, the opposite comparison (`>`) returns `true`.</span></span> <span data-ttu-id="a0b72-133">W poniższym przykładzie pokazano, że jest 10</span><span class="sxs-lookup"><span data-stu-id="a0b72-133">The following example shows that 10 is</span></span>

- <span data-ttu-id="a0b72-134">ani większa lub równa null,</span><span class="sxs-lookup"><span data-stu-id="a0b72-134">neither greater than or equal to null,</span></span>
- <span data-ttu-id="a0b72-135">ani mniejsza niż wartość null.</span><span class="sxs-lookup"><span data-stu-id="a0b72-135">nor less than null.</span></span>
  
[!code-csharp-interactive[relational and equality operators](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#8)]
  
<span data-ttu-id="a0b72-136">Powyższy przykład pokazuje, że porównanie równości dwa typy dopuszczające wartość null, które są zarówno null daje w wyniku `true`.</span><span class="sxs-lookup"><span data-stu-id="a0b72-136">The above example also shows that an equality comparison of two nullable types that are both null evaluates to `true`.</span></span>

## <a name="boxing-and-unboxing"></a><span data-ttu-id="a0b72-137">Konwersja boxing i konwersja unboxing</span><span class="sxs-lookup"><span data-stu-id="a0b72-137">Boxing and unboxing</span></span>

<span data-ttu-id="a0b72-138">Jest typem wartościowym [opakowany](../types/boxing-and-unboxing.md) przez następujące reguły:</span><span class="sxs-lookup"><span data-stu-id="a0b72-138">A nullable value type is [boxed](../types/boxing-and-unboxing.md) by the following rules:</span></span>

- <span data-ttu-id="a0b72-139">Jeśli <xref:System.Nullable%601.HasValue%2A> zwraca `false`, generowany jest odwołanie o wartości null.</span><span class="sxs-lookup"><span data-stu-id="a0b72-139">If <xref:System.Nullable%601.HasValue%2A> returns `false`, the null reference is produced.</span></span>  
- <span data-ttu-id="a0b72-140">Jeśli <xref:System.Nullable%601.HasValue%2A> zwraca `true`, wartość typu podstawowego wartość `T` jest spakowany, nie wystąpienie <xref:System.Nullable%601>.</span><span class="sxs-lookup"><span data-stu-id="a0b72-140">If <xref:System.Nullable%601.HasValue%2A> returns `true`, a value of the underlying value type `T` is boxed, not the instance of <xref:System.Nullable%601>.</span></span>

<span data-ttu-id="a0b72-141">Rozpakowywanie z opakowanym typem wartościowym do odpowiedniego typu dopuszczającego wartość null, co ilustruje poniższy przykład:</span><span class="sxs-lookup"><span data-stu-id="a0b72-141">You can unbox the boxed value type to the corresponding nullable type, as the following example shows:</span></span>

[!code-csharp-interactive[boxing and unboxing](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#9)]

## <a name="the-bool-type"></a><span data-ttu-id="a0b72-142">Wartość logiczna? Typ</span><span class="sxs-lookup"><span data-stu-id="a0b72-142">The bool? type</span></span>

<span data-ttu-id="a0b72-143">`bool?` Typu dopuszczającego wartość null może zawierać trzy różne wartości: [true](../../language-reference/keywords/true-literal.md), [false](../../language-reference/keywords/false-literal.md), i [null](../../language-reference/keywords/null.md).</span><span class="sxs-lookup"><span data-stu-id="a0b72-143">The `bool?` nullable type can contain three different values: [true](../../language-reference/keywords/true-literal.md), [false](../../language-reference/keywords/false-literal.md), and [null](../../language-reference/keywords/null.md).</span></span> <span data-ttu-id="a0b72-144">`bool?` Typu przypomina logiczna typ zmiennej, który jest używany w języku SQL.</span><span class="sxs-lookup"><span data-stu-id="a0b72-144">The `bool?` type is like the Boolean variable type that is used in SQL.</span></span> <span data-ttu-id="a0b72-145">Aby upewnij się, że wyniki generowane przez `&` i `|` operatory są zgodne z przechowywanymi w trzech typu Boolean w języku SQL, znajdują się następujące operatory wstępnie zdefiniowane:</span><span class="sxs-lookup"><span data-stu-id="a0b72-145">To ensure that the results produced by the `&` and `|` operators are consistent with the three-valued Boolean type in SQL, the following predefined operators are provided:</span></span>

- `bool? operator &(bool? x, bool? y)`  
- `bool? operator |(bool? x, bool? y)`  
  
<span data-ttu-id="a0b72-146">Semantyka te operatory jest zdefiniowane w poniższej tabeli:</span><span class="sxs-lookup"><span data-stu-id="a0b72-146">The semantics of these operators is defined by the following table:</span></span>  
  
|<span data-ttu-id="a0b72-147">x</span><span class="sxs-lookup"><span data-stu-id="a0b72-147">x</span></span>|<span data-ttu-id="a0b72-148">t</span><span class="sxs-lookup"><span data-stu-id="a0b72-148">y</span></span>|<span data-ttu-id="a0b72-149">x i y</span><span class="sxs-lookup"><span data-stu-id="a0b72-149">x&y</span></span>|<span data-ttu-id="a0b72-150">x&#124;y</span><span class="sxs-lookup"><span data-stu-id="a0b72-150">x&#124;y</span></span>|  
|-------|-------|---------|--------------|  
|<span data-ttu-id="a0b72-151">true</span><span class="sxs-lookup"><span data-stu-id="a0b72-151">true</span></span>|<span data-ttu-id="a0b72-152">true</span><span class="sxs-lookup"><span data-stu-id="a0b72-152">true</span></span>|<span data-ttu-id="a0b72-153">true</span><span class="sxs-lookup"><span data-stu-id="a0b72-153">true</span></span>|<span data-ttu-id="a0b72-154">true</span><span class="sxs-lookup"><span data-stu-id="a0b72-154">true</span></span>|  
|<span data-ttu-id="a0b72-155">true</span><span class="sxs-lookup"><span data-stu-id="a0b72-155">true</span></span>|<span data-ttu-id="a0b72-156">false</span><span class="sxs-lookup"><span data-stu-id="a0b72-156">false</span></span>|<span data-ttu-id="a0b72-157">false</span><span class="sxs-lookup"><span data-stu-id="a0b72-157">false</span></span>|<span data-ttu-id="a0b72-158">true</span><span class="sxs-lookup"><span data-stu-id="a0b72-158">true</span></span>|  
|<span data-ttu-id="a0b72-159">true</span><span class="sxs-lookup"><span data-stu-id="a0b72-159">true</span></span>|<span data-ttu-id="a0b72-160">null</span><span class="sxs-lookup"><span data-stu-id="a0b72-160">null</span></span>|<span data-ttu-id="a0b72-161">null</span><span class="sxs-lookup"><span data-stu-id="a0b72-161">null</span></span>|<span data-ttu-id="a0b72-162">true</span><span class="sxs-lookup"><span data-stu-id="a0b72-162">true</span></span>|  
|<span data-ttu-id="a0b72-163">false</span><span class="sxs-lookup"><span data-stu-id="a0b72-163">false</span></span>|<span data-ttu-id="a0b72-164">true</span><span class="sxs-lookup"><span data-stu-id="a0b72-164">true</span></span>|<span data-ttu-id="a0b72-165">false</span><span class="sxs-lookup"><span data-stu-id="a0b72-165">false</span></span>|<span data-ttu-id="a0b72-166">true</span><span class="sxs-lookup"><span data-stu-id="a0b72-166">true</span></span>|  
|<span data-ttu-id="a0b72-167">false</span><span class="sxs-lookup"><span data-stu-id="a0b72-167">false</span></span>|<span data-ttu-id="a0b72-168">false</span><span class="sxs-lookup"><span data-stu-id="a0b72-168">false</span></span>|<span data-ttu-id="a0b72-169">false</span><span class="sxs-lookup"><span data-stu-id="a0b72-169">false</span></span>|<span data-ttu-id="a0b72-170">false</span><span class="sxs-lookup"><span data-stu-id="a0b72-170">false</span></span>|  
|<span data-ttu-id="a0b72-171">false</span><span class="sxs-lookup"><span data-stu-id="a0b72-171">false</span></span>|<span data-ttu-id="a0b72-172">null</span><span class="sxs-lookup"><span data-stu-id="a0b72-172">null</span></span>|<span data-ttu-id="a0b72-173">false</span><span class="sxs-lookup"><span data-stu-id="a0b72-173">false</span></span>|<span data-ttu-id="a0b72-174">null</span><span class="sxs-lookup"><span data-stu-id="a0b72-174">null</span></span>|  
|<span data-ttu-id="a0b72-175">null</span><span class="sxs-lookup"><span data-stu-id="a0b72-175">null</span></span>|<span data-ttu-id="a0b72-176">true</span><span class="sxs-lookup"><span data-stu-id="a0b72-176">true</span></span>|<span data-ttu-id="a0b72-177">null</span><span class="sxs-lookup"><span data-stu-id="a0b72-177">null</span></span>|<span data-ttu-id="a0b72-178">true</span><span class="sxs-lookup"><span data-stu-id="a0b72-178">true</span></span>|  
|<span data-ttu-id="a0b72-179">null</span><span class="sxs-lookup"><span data-stu-id="a0b72-179">null</span></span>|<span data-ttu-id="a0b72-180">false</span><span class="sxs-lookup"><span data-stu-id="a0b72-180">false</span></span>|<span data-ttu-id="a0b72-181">false</span><span class="sxs-lookup"><span data-stu-id="a0b72-181">false</span></span>|<span data-ttu-id="a0b72-182">null</span><span class="sxs-lookup"><span data-stu-id="a0b72-182">null</span></span>|  
|<span data-ttu-id="a0b72-183">null</span><span class="sxs-lookup"><span data-stu-id="a0b72-183">null</span></span>|<span data-ttu-id="a0b72-184">null</span><span class="sxs-lookup"><span data-stu-id="a0b72-184">null</span></span>|<span data-ttu-id="a0b72-185">null</span><span class="sxs-lookup"><span data-stu-id="a0b72-185">null</span></span>|<span data-ttu-id="a0b72-186">null</span><span class="sxs-lookup"><span data-stu-id="a0b72-186">null</span></span>|  

<span data-ttu-id="a0b72-187">Należy pamiętać, że te dwa operatory nie są zgodne z zasadami opisanymi w [operatory](#operators) sekcji: wynik oceny — operator może być inna niż null, nawet, jeśli jeden z argumentów ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="a0b72-187">Note that these two operators don't follow the rules described in the [Operators](#operators) section: the result of an operator evaluation can be non-null even if one of the operands is null.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="a0b72-188">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a0b72-188">See also</span></span>

- [<span data-ttu-id="a0b72-189">Typy dopuszczające wartości zerowe</span><span class="sxs-lookup"><span data-stu-id="a0b72-189">Nullable types</span></span>](index.md)
- [<span data-ttu-id="a0b72-190">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="a0b72-190">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="a0b72-191">Co dokładnie "podniesiony" oznacza?</span><span class="sxs-lookup"><span data-stu-id="a0b72-191">What exactly does 'lifted' mean?</span></span>](https://blogs.msdn.microsoft.com/ericlippert/2007/06/27/what-exactly-does-lifted-mean/)
