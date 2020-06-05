---
title: Aggregate, klauzula
ms.date: 08/28/2018
f1_keywords:
- vb.QueryAggregateIn
- vb.QueryAggregate
- vb.QueryAggregateInto
helpviewer_keywords:
- Aggregate clause [Visual Basic]
- Aggregate statement [Visual Basic]
- queries [Visual Basic], Aggregate
ms.assetid: 1315a814-5db6-4077-b34b-b141e11cc0eb
ms.openlocfilehash: 326c3306368ceca2122e912556efd84e4bfef1f1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413004"
---
# <a name="aggregate-clause-visual-basic"></a><span data-ttu-id="25677-102">Aggregate — Klauzula (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="25677-102">Aggregate Clause (Visual Basic)</span></span>
<span data-ttu-id="25677-103">Stosuje co najmniej jedną funkcję agregującą do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="25677-103">Applies one or more aggregate functions to a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25677-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="25677-104">Syntax</span></span>  
  
```vb  
Aggregate element [As type] In collection _  
  [, element2 [As type2] In collection2, [...]]  
  [ clause ]  
  Into expressionList  
```  
  
## <a name="parts"></a><span data-ttu-id="25677-105">Części</span><span class="sxs-lookup"><span data-stu-id="25677-105">Parts</span></span>  
  
|<span data-ttu-id="25677-106">Termin</span><span class="sxs-lookup"><span data-stu-id="25677-106">Term</span></span>|<span data-ttu-id="25677-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="25677-107">Definition</span></span>|  
|---|---|  
|`element`|<span data-ttu-id="25677-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="25677-108">Required.</span></span> <span data-ttu-id="25677-109">Zmienna używana do iteracji elementów kolekcji.</span><span class="sxs-lookup"><span data-stu-id="25677-109">Variable used to iterate through the elements of the collection.</span></span>|  
|`type`|<span data-ttu-id="25677-110">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="25677-110">Optional.</span></span> <span data-ttu-id="25677-111">Typ `element` .</span><span class="sxs-lookup"><span data-stu-id="25677-111">The type of `element`.</span></span> <span data-ttu-id="25677-112">Jeśli typ nie zostanie określony, typ `element` jest wnioskowany z `collection` .</span><span class="sxs-lookup"><span data-stu-id="25677-112">If no type is specified, the type of `element` is inferred from `collection`.</span></span>|  
|`collection`|<span data-ttu-id="25677-113">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="25677-113">Required.</span></span> <span data-ttu-id="25677-114">Odwołuje się do kolekcji, w której ma działać.</span><span class="sxs-lookup"><span data-stu-id="25677-114">Refers to the collection to operate on.</span></span>|  
|`clause`|<span data-ttu-id="25677-115">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="25677-115">Optional.</span></span> <span data-ttu-id="25677-116">Co najmniej jedna klauzula zapytania, taka jak `Where` klauzula, do uściślenia wyniku zapytania, aby zastosować klauzulę agregującą lub klauzulę do.</span><span class="sxs-lookup"><span data-stu-id="25677-116">One or more query clauses, such as a `Where` clause, to refine the query result to apply the aggregate clause or clauses to.</span></span>|  
|`expressionList`|<span data-ttu-id="25677-117">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="25677-117">Required.</span></span> <span data-ttu-id="25677-118">Jedno lub więcej wyrażeń rozdzielanych przecinkami, które identyfikują funkcję agregującą, która ma zostać zastosowana do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="25677-118">One or more comma-delimited expressions that identify an aggregate function to apply to the collection.</span></span> <span data-ttu-id="25677-119">Można zastosować alias do funkcji agregującej, aby określić nazwę elementu członkowskiego dla wyniku zapytania.</span><span class="sxs-lookup"><span data-stu-id="25677-119">You can apply an alias to an aggregate function to specify a member name for the query result.</span></span> <span data-ttu-id="25677-120">Jeśli nie podano aliasu, używana jest nazwa funkcji agregującej.</span><span class="sxs-lookup"><span data-stu-id="25677-120">If no alias is supplied, the name of the aggregate function is used.</span></span> <span data-ttu-id="25677-121">Przykłady zawiera sekcja dotycząca funkcji agregujących w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="25677-121">For examples, see the section about aggregate functions later in this topic.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="25677-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="25677-122">Remarks</span></span>  
 <span data-ttu-id="25677-123">`Aggregate`Klauzula może służyć do uwzględnienia funkcji agregujących w zapytaniach.</span><span class="sxs-lookup"><span data-stu-id="25677-123">The `Aggregate` clause can be used to include aggregate functions in your queries.</span></span> <span data-ttu-id="25677-124">Funkcje agregujące wykonują operacje sprawdzania i obliczeń na zestawie wartości i zwracają pojedynczą wartość.</span><span class="sxs-lookup"><span data-stu-id="25677-124">Aggregate functions perform checks and computations over a set of values and return a single value.</span></span> <span data-ttu-id="25677-125">Możesz uzyskać dostęp do obliczonej wartości przy użyciu elementu członkowskiego typu wyników zapytania.</span><span class="sxs-lookup"><span data-stu-id="25677-125">You can access the computed value by using a member of the query result type.</span></span> <span data-ttu-id="25677-126">Standardowe funkcje agregujące, których można użyć, to funkcje,,,,,, `All` `Any` `Average` `Count` `LongCount` `Max` `Min` i `Sum` .</span><span class="sxs-lookup"><span data-stu-id="25677-126">The standard aggregate functions that you can use are the `All`, `Any`, `Average`, `Count`, `LongCount`, `Max`, `Min`, and `Sum` functions.</span></span> <span data-ttu-id="25677-127">Te funkcje są znane dla deweloperów, którzy znają agregacje w programie SQL Server.</span><span class="sxs-lookup"><span data-stu-id="25677-127">These functions are familiar to developers who are familiar with aggregates in SQL.</span></span> <span data-ttu-id="25677-128">Opisano je w poniższej sekcji tego tematu.</span><span class="sxs-lookup"><span data-stu-id="25677-128">They are described in the following section of this topic.</span></span>  
  
 <span data-ttu-id="25677-129">Wynik funkcji agregującej jest uwzględniany w wyniku zapytania jako pole typu wyniku zapytania.</span><span class="sxs-lookup"><span data-stu-id="25677-129">The result of an aggregate function is included in the query result as a field of the query result type.</span></span> <span data-ttu-id="25677-130">Można podać alias dla wyniku funkcji agregującej, aby określić nazwę elementu członkowskiego typu wyników zapytania, który będzie przechowywać wartość zagregowaną.</span><span class="sxs-lookup"><span data-stu-id="25677-130">You can supply an alias for the aggregate function result to specify the name of the member of the query result type that will hold the aggregate value.</span></span> <span data-ttu-id="25677-131">Jeśli nie podano aliasu, używana jest nazwa funkcji agregującej.</span><span class="sxs-lookup"><span data-stu-id="25677-131">If no alias is supplied, the name of the aggregate function is used.</span></span>  
  
 <span data-ttu-id="25677-132">`Aggregate`Klauzula może rozpoczynać zapytanie lub może być dołączana jako dodatkowa klauzula w zapytaniu.</span><span class="sxs-lookup"><span data-stu-id="25677-132">The `Aggregate` clause can begin a query, or it can be included as an additional clause in a query.</span></span> <span data-ttu-id="25677-133">Jeśli `Aggregate` klauzula rozpoczyna kwerendę, wynikiem jest pojedyncza wartość, która jest wynikiem funkcji agregującej określonej w `Into` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="25677-133">If the `Aggregate` clause begins a query, the result is a single value that is the result of the aggregate function specified in the `Into` clause.</span></span> <span data-ttu-id="25677-134">Jeśli w klauzuli określono więcej niż jedną funkcję agregującą `Into` , zapytanie zwraca pojedynczy typ z oddzielną właściwością, aby odwołać wynik każdej funkcji agregującej w `Into` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="25677-134">If more than one aggregate function is specified in the `Into` clause, the query returns a single type with a separate property to reference the result of each aggregate function in the `Into` clause.</span></span> <span data-ttu-id="25677-135">Jeśli `Aggregate` klauzula jest uwzględniona jako dodatkowa klauzula w zapytaniu, typ zwracany w kolekcji zapytań będzie miał osobną właściwość, aby odwołać się do wyniku każdej funkcji agregującej w `Into` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="25677-135">If the `Aggregate` clause is included as an additional clause in a query, the type returned in the query collection will have a separate property to reference the result of each aggregate function in the `Into` clause.</span></span>  
  
## <a name="aggregate-functions"></a><span data-ttu-id="25677-136">Funkcje agregujące</span><span class="sxs-lookup"><span data-stu-id="25677-136">Aggregate Functions</span></span>

<span data-ttu-id="25677-137">Poniżej znajdują się standardowe funkcje agregujące, które mogą być używane z `Aggregate` klauzulą.</span><span class="sxs-lookup"><span data-stu-id="25677-137">The following are the standard aggregate functions that can be used with the `Aggregate` clause.</span></span>  
  
### <a name="all"></a><span data-ttu-id="25677-138">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="25677-138">All</span></span>

<span data-ttu-id="25677-139">Zwraca `true` czy wszystkie elementy w kolekcji spełniają określony warunek; w przeciwnym razie zwraca `false` .</span><span class="sxs-lookup"><span data-stu-id="25677-139">Returns `true` if all elements in the collection satisfy a specified condition; otherwise returns `false`.</span></span> <span data-ttu-id="25677-140">Poniżej przedstawiono przykład:</span><span class="sxs-lookup"><span data-stu-id="25677-140">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#5)]

### <a name="any"></a><span data-ttu-id="25677-141">Dowolne</span><span class="sxs-lookup"><span data-stu-id="25677-141">Any</span></span>

<span data-ttu-id="25677-142">Zwraca `true` czy dowolny element w kolekcji spełnia określony warunek; w przeciwnym razie zwraca `false` .</span><span class="sxs-lookup"><span data-stu-id="25677-142">Returns `true` if any element in the collection satisfies a specified condition; otherwise returns `false`.</span></span> <span data-ttu-id="25677-143">Poniżej przedstawiono przykład:</span><span class="sxs-lookup"><span data-stu-id="25677-143">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#6)]

### <a name="average"></a><span data-ttu-id="25677-144">Średnia</span><span class="sxs-lookup"><span data-stu-id="25677-144">Average</span></span>

<span data-ttu-id="25677-145">Oblicza średnią wszystkich elementów w kolekcji lub oblicza dostarczone wyrażenie dla wszystkich elementów w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="25677-145">Computes the average of all elements in the collection, or computes a supplied expression for all elements in the collection.</span></span> <span data-ttu-id="25677-146">Poniżej przedstawiono przykład:</span><span class="sxs-lookup"><span data-stu-id="25677-146">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#7)]

### <a name="count"></a><span data-ttu-id="25677-147">Liczba</span><span class="sxs-lookup"><span data-stu-id="25677-147">Count</span></span>

<span data-ttu-id="25677-148">Zlicza elementy w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="25677-148">Counts the number of elements in the collection.</span></span> <span data-ttu-id="25677-149">Można podać opcjonalne `Boolean` wyrażenie, aby obliczyć tylko liczbę elementów w kolekcji, które spełniają warunek.</span><span class="sxs-lookup"><span data-stu-id="25677-149">You can supply an optional `Boolean` expression to count only the number of elements in the collection that satisfy a condition.</span></span> <span data-ttu-id="25677-150">Poniżej przedstawiono przykład:</span><span class="sxs-lookup"><span data-stu-id="25677-150">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#8)]

### <a name="group"></a><span data-ttu-id="25677-151">Grupa</span><span class="sxs-lookup"><span data-stu-id="25677-151">Group</span></span>

<span data-ttu-id="25677-152">Odwołuje się do wyników zapytania, które są pogrupowane w `Group By` wyniku `Group Join` klauzuli OR.</span><span class="sxs-lookup"><span data-stu-id="25677-152">Refers to query results that are grouped as a result of a `Group By` or `Group Join` clause.</span></span> <span data-ttu-id="25677-153">`Group`Funkcja jest prawidłowa tylko w `Into` klauzuli `Group By` `Group Join` klauzuli OR.</span><span class="sxs-lookup"><span data-stu-id="25677-153">The `Group` function is valid only in the `Into` clause of a `Group By` or `Group Join` clause.</span></span> <span data-ttu-id="25677-154">Aby uzyskać więcej informacji i przykładów, zobacz klauzule Group [by](group-by-clause.md) i Group [Join](group-join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="25677-154">For more information and examples, see [Group By Clause](group-by-clause.md) and [Group Join Clause](group-join-clause.md).</span></span>

### <a name="longcount"></a><span data-ttu-id="25677-155">LongCount</span><span class="sxs-lookup"><span data-stu-id="25677-155">LongCount</span></span>

<span data-ttu-id="25677-156">Zlicza elementy w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="25677-156">Counts the number of elements in the collection.</span></span> <span data-ttu-id="25677-157">Można podać opcjonalne `Boolean` wyrażenie, aby obliczyć tylko liczbę elementów w kolekcji, które spełniają warunek.</span><span class="sxs-lookup"><span data-stu-id="25677-157">You can supply an optional `Boolean` expression to count only the number of elements in the collection that satisfy a condition.</span></span> <span data-ttu-id="25677-158">Zwraca wynik w postaci `Long` .</span><span class="sxs-lookup"><span data-stu-id="25677-158">Returns the result as a `Long`.</span></span> <span data-ttu-id="25677-159">Aby zapoznać się z przykładem, zobacz `Count` Funkcja agregująca.</span><span class="sxs-lookup"><span data-stu-id="25677-159">For an example, see the `Count` aggregate function.</span></span>

### <a name="max"></a><span data-ttu-id="25677-160">Maks.</span><span class="sxs-lookup"><span data-stu-id="25677-160">Max</span></span>

<span data-ttu-id="25677-161">Oblicza wartość maksymalną z kolekcji lub oblicza dostarczone wyrażenie dla wszystkich elementów w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="25677-161">Computes the maximum value from the collection, or computes a supplied expression for all elements in the collection.</span></span> <span data-ttu-id="25677-162">Poniżej przedstawiono przykład:</span><span class="sxs-lookup"><span data-stu-id="25677-162">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#9)]

### <a name="min"></a><span data-ttu-id="25677-163">Min.</span><span class="sxs-lookup"><span data-stu-id="25677-163">Min</span></span>

<span data-ttu-id="25677-164">Oblicza wartość minimalną kolekcji lub oblicza dostarczone wyrażenie dla wszystkich elementów w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="25677-164">Computes the minimum value from the collection, or computes a supplied expression for all elements in the collection.</span></span> <span data-ttu-id="25677-165">Poniżej przedstawiono przykład:</span><span class="sxs-lookup"><span data-stu-id="25677-165">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#10)]

### <a name="sum"></a><span data-ttu-id="25677-166">Suma</span><span class="sxs-lookup"><span data-stu-id="25677-166">Sum</span></span>

<span data-ttu-id="25677-167">Oblicza sumę wszystkich elementów w kolekcji lub oblicza dostarczone wyrażenie dla wszystkich elementów w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="25677-167">Computes the sum of all elements in the collection, or computes a supplied expression for all elements in the collection.</span></span> <span data-ttu-id="25677-168">Poniżej przedstawiono przykład:</span><span class="sxs-lookup"><span data-stu-id="25677-168">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#15)]

## <a name="example"></a><span data-ttu-id="25677-169">Przykład</span><span class="sxs-lookup"><span data-stu-id="25677-169">Example</span></span>  

<span data-ttu-id="25677-170">Poniższy przykład pokazuje, jak używać `Aggregate` klauzuli do stosowania funkcji agregujących do wyniku zapytania.</span><span class="sxs-lookup"><span data-stu-id="25677-170">The following example shows how to use the `Aggregate` clause to apply aggregate functions to a query result.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#4)]  
  
## <a name="creating-user-defined-aggregate-functions"></a><span data-ttu-id="25677-171">Tworzenie funkcji agregujących zdefiniowanych przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="25677-171">Creating User-Defined Aggregate Functions</span></span>

 <span data-ttu-id="25677-172">W wyrażeniu zapytania można uwzględnić własne niestandardowe funkcje agregujące, dodając metody rozszerzające do <xref:System.Collections.Generic.IEnumerable%601> typu.</span><span class="sxs-lookup"><span data-stu-id="25677-172">You can include your own custom aggregate functions in a query expression by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> type.</span></span> <span data-ttu-id="25677-173">Metoda niestandardowa może następnie wykonać obliczenia lub operacje na wyliczalnej kolekcji, która przywołuje funkcję agregującą.</span><span class="sxs-lookup"><span data-stu-id="25677-173">Your custom method can then perform a calculation or operation on the enumerable collection that has referenced your aggregate function.</span></span> <span data-ttu-id="25677-174">Aby uzyskać więcej informacji na temat metod rozszerzających, zobacz [metody rozszerzenia](../../programming-guide/language-features/procedures/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="25677-174">For more information about extension methods, see [Extension Methods](../../programming-guide/language-features/procedures/extension-methods.md).</span></span>  
  
 <span data-ttu-id="25677-175">Na przykład poniższy przykład pokazuje niestandardową funkcję agregującą, która oblicza wartość mediany kolekcji liczb.</span><span class="sxs-lookup"><span data-stu-id="25677-175">For example, the following example shows a custom aggregate function that calculates the median value of a collection of numbers.</span></span> <span data-ttu-id="25677-176">Istnieją dwa przeciążenia `Median` metody rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="25677-176">There are two overloads of the `Median` extension method.</span></span> <span data-ttu-id="25677-177">Pierwsze przeciążenie przyjmuje jako dane wejściowe, Kolekcja typu `IEnumerable(Of Double)` .</span><span class="sxs-lookup"><span data-stu-id="25677-177">The first overload accepts, as input, a collection of type `IEnumerable(Of Double)`.</span></span> <span data-ttu-id="25677-178">Jeśli `Median` Funkcja agregująca jest wywoływana dla pola zapytania typu `Double` , ta metoda zostanie wywołana.</span><span class="sxs-lookup"><span data-stu-id="25677-178">If the `Median` aggregate function is called for a query field of type `Double`, this method will be called.</span></span> <span data-ttu-id="25677-179">Drugie Przeciążenie `Median` metody może być przekazanie dowolnego typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="25677-179">The second overload of the `Median` method can be passed any generic type.</span></span> <span data-ttu-id="25677-180">Ogólne Przeciążenie `Median` metody przyjmuje drugi parametr, który odwołuje się do `Func(Of T, Double)` wyrażenia lambda, aby zaprojektować wartość dla typu (z kolekcji) jako odpowiadającą wartość typu `Double` .</span><span class="sxs-lookup"><span data-stu-id="25677-180">The generic overload of the `Median` method takes a second parameter that references the `Func(Of T, Double)` lambda expression to project a value for a type (from a collection) as the corresponding value of type `Double`.</span></span> <span data-ttu-id="25677-181">Następnie przydeleguje obliczenie wartości mediany do innego przeciążenia `Median` metody.</span><span class="sxs-lookup"><span data-stu-id="25677-181">It then delegates the calculation of the median value to the other overload of the `Median` method.</span></span> <span data-ttu-id="25677-182">Aby uzyskać więcej informacji na temat wyrażeń lambda, zobacz [lambda Expressions](../../programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="25677-182">For more information about lambda expressions, see [Lambda Expressions](../../programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/UserDefinedAggregates.vb#18)]  
  
 <span data-ttu-id="25677-183">Poniższy przykład pokazuje przykładowe zapytania, które wywołują `Median` funkcję agregującą w kolekcji typu `Integer` , i kolekcję typu `Double` .</span><span class="sxs-lookup"><span data-stu-id="25677-183">The following example shows sample queries that call the `Median` aggregate function on a collection of type `Integer`, and a collection of type `Double`.</span></span> <span data-ttu-id="25677-184">Zapytanie, które wywołuje `Median` funkcję agregującą w kolekcji typu `Double` wywołuje Przeciążenie `Median` metody, która akceptuje, jako dane wejściowe, Kolekcja typu `Double` .</span><span class="sxs-lookup"><span data-stu-id="25677-184">The query that calls the `Median` aggregate function on the collection of type `Double` calls the overload of the `Median` method that accepts, as input, a collection of type `Double`.</span></span> <span data-ttu-id="25677-185">Zapytanie, które wywołuje `Median` funkcję agregującą w kolekcji typu `Integer` wywołuje ogólne Przeciążenie `Median` metody.</span><span class="sxs-lookup"><span data-stu-id="25677-185">The query that calls the `Median` aggregate function on the collection of type `Integer` calls the generic overload of the `Median` method.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/UserDefinedAggregates.vb#19)]  
  
## <a name="see-also"></a><span data-ttu-id="25677-186">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="25677-186">See also</span></span>

- [<span data-ttu-id="25677-187">Wprowadzenie do LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="25677-187">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="25677-188">Zapytania</span><span class="sxs-lookup"><span data-stu-id="25677-188">Queries</span></span>](index.md)
- [<span data-ttu-id="25677-189">SELECT — klauzula</span><span class="sxs-lookup"><span data-stu-id="25677-189">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="25677-190">Klauzula from</span><span class="sxs-lookup"><span data-stu-id="25677-190">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="25677-191">Klauzula WHERE</span><span class="sxs-lookup"><span data-stu-id="25677-191">Where Clause</span></span>](where-clause.md)
- [<span data-ttu-id="25677-192">Group By, klauzula</span><span class="sxs-lookup"><span data-stu-id="25677-192">Group By Clause</span></span>](group-by-clause.md)
