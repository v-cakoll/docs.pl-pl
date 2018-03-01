---
title: "Używanie typów dopuszczających wartości zerowe (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- nullable types [C#], about nullable types
ms.assetid: 0bacbe72-ce15-4b14-83e1-9c14e6380c28
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c8a42392bbcd2e53c54ff4c13bf98c048262ae4d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="using-nullable-types-c-programming-guide"></a><span data-ttu-id="ccff6-102">Używanie typów dopuszczających wartości zerowe (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="ccff6-102">Using Nullable Types (C# Programming Guide)</span></span>
<span data-ttu-id="ccff6-103">Typy dopuszczające wartości zerowe może reprezentować wszystkich wartości typu podstawowego i dodatkowego [null](../../../csharp/language-reference/keywords/null.md) wartość.</span><span class="sxs-lookup"><span data-stu-id="ccff6-103">Nullable types can represent all the values of an underlying type, and an additional [null](../../../csharp/language-reference/keywords/null.md) value.</span></span> <span data-ttu-id="ccff6-104">Typy dopuszczające wartości null są zadeklarowane w jeden z dwóch sposobów:</span><span class="sxs-lookup"><span data-stu-id="ccff6-104">Nullable types are declared in one of two ways:</span></span>  
  
 `System.Nullable<T> variable`  
  
 <span data-ttu-id="ccff6-105">—lub—</span><span class="sxs-lookup"><span data-stu-id="ccff6-105">-or-</span></span>  
  
 `T? variable`  
  
 <span data-ttu-id="ccff6-106">`T`jest typem podstawowym typu dopuszczającego wartość null.</span><span class="sxs-lookup"><span data-stu-id="ccff6-106">`T` is the underlying type of the nullable type.</span></span> <span data-ttu-id="ccff6-107">`T`mogą być dowolnego typu wartości w tym `struct`; nie może być typem referencyjnym.</span><span class="sxs-lookup"><span data-stu-id="ccff6-107">`T` can be any value type including `struct`; it cannot be a reference type.</span></span>  
  
 <span data-ttu-id="ccff6-108">Na przykład kiedy może używać typu dopuszczającego wartość null, należy wziąć pod uwagę sposób zwykłej wartość logiczna może mieć dwie wartości: true i false.</span><span class="sxs-lookup"><span data-stu-id="ccff6-108">For an example of when you might use a nullable type, consider how an ordinary Boolean variable can have two values: true and false.</span></span> <span data-ttu-id="ccff6-109">Nie istnieje wartość, która oznacza, że "undefined".</span><span class="sxs-lookup"><span data-stu-id="ccff6-109">There is no value that signifies "undefined".</span></span> <span data-ttu-id="ccff6-110">W wielu aplikacjach programowania głównie bazy danych interakcji, zmienne może wystąpić w stanie niezdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="ccff6-110">In many programming applications, most notably database interactions, variables can occur in an undefined state.</span></span> <span data-ttu-id="ccff6-111">Na przykład pole w bazie danych może zawierać wartości PRAWDA lub FAŁSZ, ale może również zawierać żadnej wartości w ogóle.</span><span class="sxs-lookup"><span data-stu-id="ccff6-111">For example, a field in a database may contain the values true or false, but it may also contain no value at all.</span></span> <span data-ttu-id="ccff6-112">Podobnie można ustawić typy referencyjne `null` aby wskazać, że nie jest inicjowany.</span><span class="sxs-lookup"><span data-stu-id="ccff6-112">Similarly, reference types can be set to `null` to indicate that they are not initialized.</span></span>  
  
 <span data-ttu-id="ccff6-113">Tej różnicy można utworzyć bardzo programowania pracy z dodatkowe zmienne używane do przechowywania informacji o stanie, użyj wartości specjalnych i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="ccff6-113">This disparity can create extra programming work, with additional variables used to store state information, the use of special values, and so on.</span></span> <span data-ttu-id="ccff6-114">Modyfikator typ dopuszczający wartość null umożliwia C# do tworzenia zmiennych Typ wartości, które wskazuje niezdefiniowaną wartość.</span><span class="sxs-lookup"><span data-stu-id="ccff6-114">The nullable type modifier enables C# to create value-type variables that indicate an undefined value.</span></span>  
  
## <a name="examples-of-nullable-types"></a><span data-ttu-id="ccff6-115">Przykłady typów dopuszczających wartości zerowe</span><span class="sxs-lookup"><span data-stu-id="ccff6-115">Examples of Nullable Types</span></span>  
 <span data-ttu-id="ccff6-116">Dowolny typ wartości może służyć jako podstawa dla typu dopuszczającego wartość null.</span><span class="sxs-lookup"><span data-stu-id="ccff6-116">Any value type may be used as the basis for a nullable type.</span></span> <span data-ttu-id="ccff6-117">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="ccff6-117">For example:</span></span>  
  
 [!code-csharp[csProgGuideTypes#4](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_1.cs)]  
  
## <a name="the-members-of-nullable-types"></a><span data-ttu-id="ccff6-118">Elementów członkowskich typów dopuszczających wartości zerowe</span><span class="sxs-lookup"><span data-stu-id="ccff6-118">The Members of Nullable Types</span></span>  
 <span data-ttu-id="ccff6-119">Każde wystąpienie typu dopuszczającego wartości null ma dwie właściwości publiczne tylko do odczytu:</span><span class="sxs-lookup"><span data-stu-id="ccff6-119">Each instance of a nullable type has two public read-only properties:</span></span>  
  
-   `HasValue`  
  
     <span data-ttu-id="ccff6-120">`HasValue`jest typu `bool`.</span><span class="sxs-lookup"><span data-stu-id="ccff6-120">`HasValue` is of type `bool`.</span></span> <span data-ttu-id="ccff6-121">Ma ustawioną wartość `true` Jeśli zmienna zawiera wartość inną niż null.</span><span class="sxs-lookup"><span data-stu-id="ccff6-121">It is set to `true` when the variable contains a non-null value.</span></span>  
  
-   `Value`  
  
     <span data-ttu-id="ccff6-122">`Value`jest tego samego typu jako typu bazowego.</span><span class="sxs-lookup"><span data-stu-id="ccff6-122">`Value` is of the same type as the underlying type.</span></span> <span data-ttu-id="ccff6-123">Jeśli `HasValue` jest `true`, `Value` zawiera odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="ccff6-123">If `HasValue` is `true`, `Value` contains a meaningful value.</span></span> <span data-ttu-id="ccff6-124">Jeśli `HasValue` jest `false`, podczas uzyskiwania dostępu do `Value` zgłosi <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="ccff6-124">If `HasValue` is `false`, accessing `Value` will throw a <xref:System.InvalidOperationException>.</span></span>  
  
 <span data-ttu-id="ccff6-125">W tym przykładzie `HasValue` element członkowski jest używany do sprawdzenia, czy zmienna zawiera wartość, przed ponowną próbą go wyświetlić.</span><span class="sxs-lookup"><span data-stu-id="ccff6-125">In this example, the `HasValue` member is used to test whether the variable contains a value before it tries to display it.</span></span>  
  
 [!code-csharp[csProgGuideTypes#5](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_2.cs)]  
  
 <span data-ttu-id="ccff6-126">Testowanie wartości można również wykonać jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="ccff6-126">Testing for a value can also be done as in the following example:</span></span>  
  
 [!code-csharp[csProgGuideTypes#6](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_3.cs)]  
  
## <a name="explicit-conversions"></a><span data-ttu-id="ccff6-127">Jawne konwersje</span><span class="sxs-lookup"><span data-stu-id="ccff6-127">Explicit Conversions</span></span>  
 <span data-ttu-id="ccff6-128">Typ dopuszczający wartość null mogą być rzutowane na typu regularne jawnie z rzutowanie lub za pomocą `Value` właściwości.</span><span class="sxs-lookup"><span data-stu-id="ccff6-128">A nullable type can be cast to a regular type, either explicitly with a cast, or by using the `Value` property.</span></span> <span data-ttu-id="ccff6-129">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="ccff6-129">For example:</span></span>  
  
 [!code-csharp[csProgGuideTypes#7](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_4.cs)]  
  
 <span data-ttu-id="ccff6-130">Jeśli konwersja zdefiniowana przez użytkownika jest zdefiniowany między dwoma typami, tym samym konwersji można również używać razem nullable wersje tych typów danych.</span><span class="sxs-lookup"><span data-stu-id="ccff6-130">If a user-defined conversion is defined between two data types, the same conversion can also be used with the nullable versions of these data types.</span></span>  
  
## <a name="implicit-conversions"></a><span data-ttu-id="ccff6-131">Niejawne konwersje</span><span class="sxs-lookup"><span data-stu-id="ccff6-131">Implicit Conversions</span></span>  
 <span data-ttu-id="ccff6-132">Zmienna typu dopuszczającego wartość NULL można ustawić na wartość null z `null` — słowo kluczowe, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="ccff6-132">A variable of nullable type can be set to null with the `null` keyword, as shown in the following example:</span></span>  
  
 [!code-csharp[csProgGuideTypes#8](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_5.cs)]  
  
 <span data-ttu-id="ccff6-133">Konwersja z typu zwykłego na typ dopuszczający wartość null, jest niejawnie.</span><span class="sxs-lookup"><span data-stu-id="ccff6-133">The conversion from an ordinary type to a nullable type, is implicit.</span></span>  
  
 [!code-csharp[csProgGuideTypes#9](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_6.cs)]  
  
## <a name="operators"></a><span data-ttu-id="ccff6-134">Operatory</span><span class="sxs-lookup"><span data-stu-id="ccff6-134">Operators</span></span>  
 <span data-ttu-id="ccff6-135">Wstępnie zdefiniowane jednoargumentowy i operatorów binarnych oraz wszystkie operatory zdefiniowane przez użytkownika, które istnieją dla typów wartości mogą również wykorzystywane przez typy dopuszczające wartości zerowe.</span><span class="sxs-lookup"><span data-stu-id="ccff6-135">The predefined unary and binary operators and any user-defined operators that exist for value types may also be used by nullable types.</span></span> <span data-ttu-id="ccff6-136">Te operatorów daje wartość null, jeśli argumenty mają wartość null; w przeciwnym razie operator używa wartości zawartych w niej do obliczania wyniku.</span><span class="sxs-lookup"><span data-stu-id="ccff6-136">These operators produce a null value if the operands are null; otherwise, the operator uses the contained value to calculate the result.</span></span> <span data-ttu-id="ccff6-137">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="ccff6-137">For example:</span></span>  
  
 [!code-csharp[csProgGuideTypes#10](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_7.cs)]  
  
 <span data-ttu-id="ccff6-138">W przypadku wykonywania porównania z typy dopuszczające wartości null, jeśli wartość jednego z typów dopuszczających wartości zerowe ma wartość null, a drugi nie wszystkie porównania obliczać `false` z wyjątkiem `!=` (nie ma wartości).</span><span class="sxs-lookup"><span data-stu-id="ccff6-138">When you perform comparisons with nullable types, if the value of one of the nullable types is null and the other is not, all comparisons evaluate to `false` except for `!=` (not equal).</span></span> <span data-ttu-id="ccff6-139">Ważne jest, aby nie zakłada, że ponieważ zwraca określonego porównanie `false`, w przeciwnym wypadku zwraca `true`.</span><span class="sxs-lookup"><span data-stu-id="ccff6-139">It is important not to assume that because a particular comparison returns `false`, the opposite case returns `true`.</span></span> <span data-ttu-id="ccff6-140">W poniższym przykładzie 10 nie jest większa, mniejsza ani równa null.</span><span class="sxs-lookup"><span data-stu-id="ccff6-140">In the following example, 10 is not greater than, less than, nor equal to null.</span></span> <span data-ttu-id="ccff6-141">Tylko `num1 != num2` daje w wyniku `true`.</span><span class="sxs-lookup"><span data-stu-id="ccff6-141">Only `num1 != num2` evaluates to `true`.</span></span>  
  
 [!code-csharp[csProgGuideTypes#11](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_8.cs)]  
  
 <span data-ttu-id="ccff6-142">Daje w wyniku porównania równości dwóch typów wartości null, które są obie wartości null `true`.</span><span class="sxs-lookup"><span data-stu-id="ccff6-142">An equality comparison of two nullable types that are both null evaluates to `true`.</span></span>  
  
## <a name="the--operator"></a><span data-ttu-id="ccff6-143">?</span><span class="sxs-lookup"><span data-stu-id="ccff6-143">The ??</span></span> <span data-ttu-id="ccff6-144">Operator</span><span class="sxs-lookup"><span data-stu-id="ccff6-144">Operator</span></span>  
 <span data-ttu-id="ccff6-145">`??` Operator określa wartość domyślną, który jest zwracany, gdy typ dopuszczający wartość null jest przypisany do typu wartości null.</span><span class="sxs-lookup"><span data-stu-id="ccff6-145">The `??` operator defines a default value that is returned when a nullable type is assigned to a non-nullable type.</span></span>  
  
 [!code-csharp[csProgGuideTypes#12](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_9.cs)]  
  
 <span data-ttu-id="ccff6-146">Ten operator może również z wieloma typami wartości null.</span><span class="sxs-lookup"><span data-stu-id="ccff6-146">This operator can also be used with multiple nullable types.</span></span> <span data-ttu-id="ccff6-147">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="ccff6-147">For example:</span></span>  
  
 [!code-csharp[csProgGuideTypes#13](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_10.cs)]  
  
## <a name="the-bool-type"></a><span data-ttu-id="ccff6-148">Bool? Typ</span><span class="sxs-lookup"><span data-stu-id="ccff6-148">The bool? type</span></span>  
 <span data-ttu-id="ccff6-149">`bool?` Typ dopuszczający wartość null, mogą zawierać trzy różne wartości: [true](../../../csharp/language-reference/keywords/true.md), [false](../../../csharp/language-reference/keywords/false.md) i [null](../../../csharp/language-reference/keywords/null.md).</span><span class="sxs-lookup"><span data-stu-id="ccff6-149">The `bool?` nullable type can contain three different values: [true](../../../csharp/language-reference/keywords/true.md), [false](../../../csharp/language-reference/keywords/false.md) and [null](../../../csharp/language-reference/keywords/null.md).</span></span> <span data-ttu-id="ccff6-150">Aby uzyskać informacje na temat rzutowania z typu wartość logiczna? Aby bool, zobacz [porady: bezpieczne rzutowanie z bool? na bool](../../../csharp/programming-guide/nullable-types/how-to-safely-cast-from-bool-to-bool.md).</span><span class="sxs-lookup"><span data-stu-id="ccff6-150">For information about how to cast from a bool? to a bool, see [How to: Safely Cast from bool? to bool](../../../csharp/programming-guide/nullable-types/how-to-safely-cast-from-bool-to-bool.md).</span></span>  
  
 <span data-ttu-id="ccff6-151">Dopuszczające wartości zerowe wartości logiczne są podobne do logiczna typ zmiennej używanej w programie SQL.</span><span class="sxs-lookup"><span data-stu-id="ccff6-151">Nullable Booleans are like the Boolean variable type that is used in SQL.</span></span> <span data-ttu-id="ccff6-152">Do zapewnienia, że wyniki utworzonego przez `&` i `|` operatory są zgodne z przechowywanymi w trzech typu Boolean w programie SQL znajdują się następujące wstępnie zdefiniowane operatory:</span><span class="sxs-lookup"><span data-stu-id="ccff6-152">To ensure that the results produced by the `&` and `|` operators are consistent with the three-valued Boolean type in SQL, the following predefined operators are provided:</span></span>  
  
 `bool? operator &(bool? x, bool? y)`  
  
 `bool? operator |(bool? x, bool? y)`  
  
 <span data-ttu-id="ccff6-153">W poniższej tabeli przedstawiono wyniki tych operatorów:</span><span class="sxs-lookup"><span data-stu-id="ccff6-153">The results of these operators are listed in the following table:</span></span>  
  
|<span data-ttu-id="ccff6-154">X</span><span class="sxs-lookup"><span data-stu-id="ccff6-154">X</span></span>|<span data-ttu-id="ccff6-155">t</span><span class="sxs-lookup"><span data-stu-id="ccff6-155">y</span></span>|<span data-ttu-id="ccff6-156">x & y</span><span class="sxs-lookup"><span data-stu-id="ccff6-156">x&y</span></span>|<span data-ttu-id="ccff6-157">x &#124; y</span><span class="sxs-lookup"><span data-stu-id="ccff6-157">x&#124;y</span></span>|  
|-------|-------|---------|--------------|  
|<span data-ttu-id="ccff6-158">true</span><span class="sxs-lookup"><span data-stu-id="ccff6-158">true</span></span>|<span data-ttu-id="ccff6-159">true</span><span class="sxs-lookup"><span data-stu-id="ccff6-159">true</span></span>|<span data-ttu-id="ccff6-160">true</span><span class="sxs-lookup"><span data-stu-id="ccff6-160">true</span></span>|<span data-ttu-id="ccff6-161">true</span><span class="sxs-lookup"><span data-stu-id="ccff6-161">true</span></span>|  
|<span data-ttu-id="ccff6-162">true</span><span class="sxs-lookup"><span data-stu-id="ccff6-162">true</span></span>|<span data-ttu-id="ccff6-163">false</span><span class="sxs-lookup"><span data-stu-id="ccff6-163">false</span></span>|<span data-ttu-id="ccff6-164">false</span><span class="sxs-lookup"><span data-stu-id="ccff6-164">false</span></span>|<span data-ttu-id="ccff6-165">true</span><span class="sxs-lookup"><span data-stu-id="ccff6-165">true</span></span>|  
|<span data-ttu-id="ccff6-166">true</span><span class="sxs-lookup"><span data-stu-id="ccff6-166">true</span></span>|<span data-ttu-id="ccff6-167">null</span><span class="sxs-lookup"><span data-stu-id="ccff6-167">null</span></span>|<span data-ttu-id="ccff6-168">null</span><span class="sxs-lookup"><span data-stu-id="ccff6-168">null</span></span>|<span data-ttu-id="ccff6-169">true</span><span class="sxs-lookup"><span data-stu-id="ccff6-169">true</span></span>|  
|<span data-ttu-id="ccff6-170">false</span><span class="sxs-lookup"><span data-stu-id="ccff6-170">false</span></span>|<span data-ttu-id="ccff6-171">true</span><span class="sxs-lookup"><span data-stu-id="ccff6-171">true</span></span>|<span data-ttu-id="ccff6-172">false</span><span class="sxs-lookup"><span data-stu-id="ccff6-172">false</span></span>|<span data-ttu-id="ccff6-173">true</span><span class="sxs-lookup"><span data-stu-id="ccff6-173">true</span></span>|  
|<span data-ttu-id="ccff6-174">false</span><span class="sxs-lookup"><span data-stu-id="ccff6-174">false</span></span>|<span data-ttu-id="ccff6-175">false</span><span class="sxs-lookup"><span data-stu-id="ccff6-175">false</span></span>|<span data-ttu-id="ccff6-176">false</span><span class="sxs-lookup"><span data-stu-id="ccff6-176">false</span></span>|<span data-ttu-id="ccff6-177">false</span><span class="sxs-lookup"><span data-stu-id="ccff6-177">false</span></span>|  
|<span data-ttu-id="ccff6-178">false</span><span class="sxs-lookup"><span data-stu-id="ccff6-178">false</span></span>|<span data-ttu-id="ccff6-179">null</span><span class="sxs-lookup"><span data-stu-id="ccff6-179">null</span></span>|<span data-ttu-id="ccff6-180">false</span><span class="sxs-lookup"><span data-stu-id="ccff6-180">false</span></span>|<span data-ttu-id="ccff6-181">null</span><span class="sxs-lookup"><span data-stu-id="ccff6-181">null</span></span>|  
|<span data-ttu-id="ccff6-182">null</span><span class="sxs-lookup"><span data-stu-id="ccff6-182">null</span></span>|<span data-ttu-id="ccff6-183">true</span><span class="sxs-lookup"><span data-stu-id="ccff6-183">true</span></span>|<span data-ttu-id="ccff6-184">null</span><span class="sxs-lookup"><span data-stu-id="ccff6-184">null</span></span>|<span data-ttu-id="ccff6-185">true</span><span class="sxs-lookup"><span data-stu-id="ccff6-185">true</span></span>|  
|<span data-ttu-id="ccff6-186">null</span><span class="sxs-lookup"><span data-stu-id="ccff6-186">null</span></span>|<span data-ttu-id="ccff6-187">false</span><span class="sxs-lookup"><span data-stu-id="ccff6-187">false</span></span>|<span data-ttu-id="ccff6-188">false</span><span class="sxs-lookup"><span data-stu-id="ccff6-188">false</span></span>|<span data-ttu-id="ccff6-189">null</span><span class="sxs-lookup"><span data-stu-id="ccff6-189">null</span></span>|  
|<span data-ttu-id="ccff6-190">null</span><span class="sxs-lookup"><span data-stu-id="ccff6-190">null</span></span>|<span data-ttu-id="ccff6-191">null</span><span class="sxs-lookup"><span data-stu-id="ccff6-191">null</span></span>|<span data-ttu-id="ccff6-192">null</span><span class="sxs-lookup"><span data-stu-id="ccff6-192">null</span></span>|<span data-ttu-id="ccff6-193">null</span><span class="sxs-lookup"><span data-stu-id="ccff6-193">null</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ccff6-194">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ccff6-194">See Also</span></span>  
 [<span data-ttu-id="ccff6-195">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="ccff6-195">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="ccff6-196">Typy dopuszczające wartości zerowe</span><span class="sxs-lookup"><span data-stu-id="ccff6-196">Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/index.md)  
 [<span data-ttu-id="ccff6-197">Konwersja boxing typów dopuszczających wartości zerowe</span><span class="sxs-lookup"><span data-stu-id="ccff6-197">Boxing Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/boxing-nullable-types.md)  
 [<span data-ttu-id="ccff6-198">Typy dopuszczające wartości zerowe wartości</span><span class="sxs-lookup"><span data-stu-id="ccff6-198">Nullable Value Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
