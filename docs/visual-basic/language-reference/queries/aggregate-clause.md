---
title: Aggregate — Klauzula (Visual Basic)
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
ms.openlocfilehash: a26ea220a807d3158d6874e2127db9a2f280a10c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54547095"
---
# <a name="aggregate-clause-visual-basic"></a><span data-ttu-id="b6f40-102">Aggregate — Klauzula (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b6f40-102">Aggregate Clause (Visual Basic)</span></span>
<span data-ttu-id="b6f40-103">Stosuje jedną lub więcej funkcji agregujących do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="b6f40-103">Applies one or more aggregate functions to a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6f40-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b6f40-104">Syntax</span></span>  
  
```  
Aggregate element [As type] In collection _  
  [, element2 [As type2] In collection2, [...]]  
  [ clause ]  
  Into expressionList  
```  
  
## <a name="parts"></a><span data-ttu-id="b6f40-105">Części</span><span class="sxs-lookup"><span data-stu-id="b6f40-105">Parts</span></span>  
  
|<span data-ttu-id="b6f40-106">Termin</span><span class="sxs-lookup"><span data-stu-id="b6f40-106">Term</span></span>|<span data-ttu-id="b6f40-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="b6f40-107">Definition</span></span>|  
|---|---|  
|`element`|<span data-ttu-id="b6f40-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="b6f40-108">Required.</span></span> <span data-ttu-id="b6f40-109">Zmienna jest używana do iteracji przez elementy kolekcji.</span><span class="sxs-lookup"><span data-stu-id="b6f40-109">Variable used to iterate through the elements of the collection.</span></span>|  
|`type`|<span data-ttu-id="b6f40-110">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="b6f40-110">Optional.</span></span> <span data-ttu-id="b6f40-111">Typ `element`.</span><span class="sxs-lookup"><span data-stu-id="b6f40-111">The type of `element`.</span></span> <span data-ttu-id="b6f40-112">Jeśli nie określono typu, typu `element` wynika z `collection`.</span><span class="sxs-lookup"><span data-stu-id="b6f40-112">If no type is specified, the type of `element` is inferred from `collection`.</span></span>|  
|`collection`|<span data-ttu-id="b6f40-113">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="b6f40-113">Required.</span></span> <span data-ttu-id="b6f40-114">Odnosi się do kolekcji do wykonywania operacji.</span><span class="sxs-lookup"><span data-stu-id="b6f40-114">Refers to the collection to operate on.</span></span>|  
|`clause`|<span data-ttu-id="b6f40-115">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="b6f40-115">Optional.</span></span> <span data-ttu-id="b6f40-116">Jeden lub więcej klauzul zapytania, takie jak `Where` klauzulę, aby udoskonalić wynik zapytania, aby zastosować aggregate — klauzula lub klauzule.</span><span class="sxs-lookup"><span data-stu-id="b6f40-116">One or more query clauses, such as a `Where` clause, to refine the query result to apply the aggregate clause or clauses to.</span></span>|  
|`expressionList`|<span data-ttu-id="b6f40-117">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="b6f40-117">Required.</span></span> <span data-ttu-id="b6f40-118">Co najmniej jednego rozdzielonych przecinkami wyrażenia, które identyfikują funkcję agregacji, aby zastosować do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="b6f40-118">One or more comma-delimited expressions that identify an aggregate function to apply to the collection.</span></span> <span data-ttu-id="b6f40-119">Alias można zastosować do funkcji agregującej, aby określić nazwę elementu członkowskiego dla wyniku kwerendy.</span><span class="sxs-lookup"><span data-stu-id="b6f40-119">You can apply an alias to an aggregate function to specify a member name for the query result.</span></span> <span data-ttu-id="b6f40-120">Jeśli nie dostarczono Brak aliasu, nazwa funkcji agregującej jest używana.</span><span class="sxs-lookup"><span data-stu-id="b6f40-120">If no alias is supplied, the name of the aggregate function is used.</span></span> <span data-ttu-id="b6f40-121">Aby uzyskać przykłady zobacz sekcję dotyczącą funkcji agregujących w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="b6f40-121">For examples, see the section about aggregate functions later in this topic.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b6f40-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b6f40-122">Remarks</span></span>  
 <span data-ttu-id="b6f40-123">`Aggregate` Klauzuli może służyć do uwzględnienia funkcji agregujących w zapytaniach.</span><span class="sxs-lookup"><span data-stu-id="b6f40-123">The `Aggregate` clause can be used to include aggregate functions in your queries.</span></span> <span data-ttu-id="b6f40-124">Funkcje agregujące wykonują zbiór wartości kontroli i obliczeń i zwracać pojedynczą wartość.</span><span class="sxs-lookup"><span data-stu-id="b6f40-124">Aggregate functions perform checks and computations over a set of values and return a single value.</span></span> <span data-ttu-id="b6f40-125">Obliczona wartość dostęp przy użyciu członka typu wyniku zapytania.</span><span class="sxs-lookup"><span data-stu-id="b6f40-125">You can access the computed value by using a member of the query result type.</span></span> <span data-ttu-id="b6f40-126">Standardowe funkcje agregujące, których można użyć są `All`, `Any`, `Average`, `Count`, `LongCount`, `Max`, `Min`, i `Sum` funkcji.</span><span class="sxs-lookup"><span data-stu-id="b6f40-126">The standard aggregate functions that you can use are the `All`, `Any`, `Average`, `Count`, `LongCount`, `Max`, `Min`, and `Sum` functions.</span></span> <span data-ttu-id="b6f40-127">Te funkcje są znane deweloperom, którzy są zaznajomieni z wartości zagregowanych w języku SQL.</span><span class="sxs-lookup"><span data-stu-id="b6f40-127">These functions are familiar to developers who are familiar with aggregates in SQL.</span></span> <span data-ttu-id="b6f40-128">Zostały one opisane w poniższej sekcji tego tematu.</span><span class="sxs-lookup"><span data-stu-id="b6f40-128">They are described in the following section of this topic.</span></span>  
  
 <span data-ttu-id="b6f40-129">Wynik funkcji agregującej znajduje się w wyniku kwerendy jako pole typu wyniku zapytania.</span><span class="sxs-lookup"><span data-stu-id="b6f40-129">The result of an aggregate function is included in the query result as a field of the query result type.</span></span> <span data-ttu-id="b6f40-130">Możesz podać alias wyniku funkcji agregującej do określenia nazwy elementu członkowskiego typu wyniku zapytania, który będzie przechowywać wartości zagregowanej.</span><span class="sxs-lookup"><span data-stu-id="b6f40-130">You can supply an alias for the aggregate function result to specify the name of the member of the query result type that will hold the aggregate value.</span></span> <span data-ttu-id="b6f40-131">Jeśli nie dostarczono Brak aliasu, nazwa funkcji agregującej jest używana.</span><span class="sxs-lookup"><span data-stu-id="b6f40-131">If no alias is supplied, the name of the aggregate function is used.</span></span>  
  
 <span data-ttu-id="b6f40-132">`Aggregate` Klauzuli można rozpocząć zapytania lub może być uwzględniany jako dodatkową klauzulę w zapytaniu.</span><span class="sxs-lookup"><span data-stu-id="b6f40-132">The `Aggregate` clause can begin a query, or it can be included as an additional clause in a query.</span></span> <span data-ttu-id="b6f40-133">Jeśli `Aggregate` klauzuli rozpoczyna się zapytanie, wynik jest pojedynczą wartość, która jest wynikiem funkcji agregującej, określone w `Into` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="b6f40-133">If the `Aggregate` clause begins a query, the result is a single value that is the result of the aggregate function specified in the `Into` clause.</span></span> <span data-ttu-id="b6f40-134">Jeśli określono więcej niż jedną funkcję agregacji w `Into` klauzuli zapytanie zwraca jeden typ z właściwością oddzielne k odkazu wynik każdego w funkcji agregującej `Into` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="b6f40-134">If more than one aggregate function is specified in the `Into` clause, the query returns a single type with a separate property to reference the result of each aggregate function in the `Into` clause.</span></span> <span data-ttu-id="b6f40-135">Jeśli `Aggregate` klauzula jest dołączony jako dodatkową klauzulę w zapytaniu, typ zwracany w kolekcji zapytanie będzie miał oddzielny właściwości, aby odwoływać się do wyniku każdej funkcji agregującej w `Into` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="b6f40-135">If the `Aggregate` clause is included as an additional clause in a query, the type returned in the query collection will have a separate property to reference the result of each aggregate function in the `Into` clause.</span></span>  
  
## <a name="aggregate-functions"></a><span data-ttu-id="b6f40-136">Funkcje agregujące</span><span class="sxs-lookup"><span data-stu-id="b6f40-136">Aggregate Functions</span></span>

<span data-ttu-id="b6f40-137">Poniżej przedstawiono standardowe funkcje agregujące, które mogą być używane z `Aggregate` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="b6f40-137">The following are the standard aggregate functions that can be used with the `Aggregate` clause.</span></span>  
  
### <a name="all"></a><span data-ttu-id="b6f40-138">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="b6f40-138">All</span></span>

<span data-ttu-id="b6f40-139">Zwraca `true` , gdy wszystkie elementy w kolekcji spełniają określony warunek; w przeciwnym razie zwraca `false`.</span><span class="sxs-lookup"><span data-stu-id="b6f40-139">Returns `true` if all elements in the collection satisfy a specified condition; otherwise returns `false`.</span></span> <span data-ttu-id="b6f40-140">Oto przykład:</span><span class="sxs-lookup"><span data-stu-id="b6f40-140">The following is an example:</span></span>

[!code-vb[VbSimpleQuerySamples#5](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_1.vb)]

### <a name="any"></a><span data-ttu-id="b6f40-141">Dowolne</span><span class="sxs-lookup"><span data-stu-id="b6f40-141">Any</span></span>

<span data-ttu-id="b6f40-142">Zwraca `true` , jeżeli dowolny element w kolekcji spełnia określony warunek; w przeciwnym razie zwraca `false`.</span><span class="sxs-lookup"><span data-stu-id="b6f40-142">Returns `true` if any element in the collection satisfies a specified condition; otherwise returns `false`.</span></span> <span data-ttu-id="b6f40-143">Oto przykład:</span><span class="sxs-lookup"><span data-stu-id="b6f40-143">The following is an example:</span></span>

[!code-vb[VbSimpleQuerySamples#6](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_2.vb)]

### <a name="average"></a><span data-ttu-id="b6f40-144">Średnia</span><span class="sxs-lookup"><span data-stu-id="b6f40-144">Average</span></span>

<span data-ttu-id="b6f40-145">Oblicza średnią wszystkich elementów w kolekcji, lub oblicza wyrażenie podane dla wszystkich elementów w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="b6f40-145">Computes the average of all elements in the collection, or computes a supplied expression for all elements in the collection.</span></span> <span data-ttu-id="b6f40-146">Oto przykład:</span><span class="sxs-lookup"><span data-stu-id="b6f40-146">The following is an example:</span></span>

[!code-vb[VbSimpleQuerySamples#7](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_3.vb)]

### <a name="count"></a><span data-ttu-id="b6f40-147">Licznik</span><span class="sxs-lookup"><span data-stu-id="b6f40-147">Count</span></span>

<span data-ttu-id="b6f40-148">Zlicza liczbę elementów w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="b6f40-148">Counts the number of elements in the collection.</span></span> <span data-ttu-id="b6f40-149">Można podać opcjonalny `Boolean` wyrażenia do obliczania tylko liczby elementów w kolekcji, które spełniają warunek.</span><span class="sxs-lookup"><span data-stu-id="b6f40-149">You can supply an optional `Boolean` expression to count only the number of elements in the collection that satisfy a condition.</span></span> <span data-ttu-id="b6f40-150">Oto przykład:</span><span class="sxs-lookup"><span data-stu-id="b6f40-150">The following is an example:</span></span>

[!code-vb[VbSimpleQuerySamples#8](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_4.vb)]

### <a name="group"></a><span data-ttu-id="b6f40-151">Grupa</span><span class="sxs-lookup"><span data-stu-id="b6f40-151">Group</span></span>

<span data-ttu-id="b6f40-152">Odwołuje się do wyników zapytania, które są grupowane w `Group By` lub `Group Join` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="b6f40-152">Refers to query results that are grouped as a result of a `Group By` or `Group Join` clause.</span></span> <span data-ttu-id="b6f40-153">`Group` Funkcja jest prawidłowa tylko w `Into` klauzuli `Group By` lub `Group Join` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="b6f40-153">The `Group` function is valid only in the `Into` clause of a `Group By` or `Group Join` clause.</span></span> <span data-ttu-id="b6f40-154">Aby uzyskać więcej informacji i przykładów, zobacz [grupy przez klauzulę](../../../visual-basic/language-reference/queries/group-by-clause.md) i [Group Join — klauzula](../../../visual-basic/language-reference/queries/group-join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="b6f40-154">For more information and examples, see [Group By Clause](../../../visual-basic/language-reference/queries/group-by-clause.md) and [Group Join Clause](../../../visual-basic/language-reference/queries/group-join-clause.md).</span></span>

### <a name="longcount"></a><span data-ttu-id="b6f40-155">LongCount</span><span class="sxs-lookup"><span data-stu-id="b6f40-155">LongCount</span></span>

<span data-ttu-id="b6f40-156">Zlicza liczbę elementów w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="b6f40-156">Counts the number of elements in the collection.</span></span> <span data-ttu-id="b6f40-157">Można podać opcjonalny `Boolean` wyrażenia do obliczania tylko liczby elementów w kolekcji, które spełniają warunek.</span><span class="sxs-lookup"><span data-stu-id="b6f40-157">You can supply an optional `Boolean` expression to count only the number of elements in the collection that satisfy a condition.</span></span> <span data-ttu-id="b6f40-158">Zwraca wynik w postaci `Long`.</span><span class="sxs-lookup"><span data-stu-id="b6f40-158">Returns the result as a `Long`.</span></span> <span data-ttu-id="b6f40-159">Aby uzyskać przykład, zobacz `Count` funkcję agregacji.</span><span class="sxs-lookup"><span data-stu-id="b6f40-159">For an example, see the `Count` aggregate function.</span></span>

### <a name="max"></a><span data-ttu-id="b6f40-160">Maks.</span><span class="sxs-lookup"><span data-stu-id="b6f40-160">Max</span></span>

<span data-ttu-id="b6f40-161">Oblicza maksymalną wartość z kolekcji, lub oblicza wyrażenie podane dla wszystkich elementów w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="b6f40-161">Computes the maximum value from the collection, or computes a supplied expression for all elements in the collection.</span></span> <span data-ttu-id="b6f40-162">Oto przykład:</span><span class="sxs-lookup"><span data-stu-id="b6f40-162">The following is an example:</span></span>

[!code-vb[VbSimpleQuerySamples#9](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_5.vb)]

### <a name="min"></a><span data-ttu-id="b6f40-163">Min.</span><span class="sxs-lookup"><span data-stu-id="b6f40-163">Min</span></span>

<span data-ttu-id="b6f40-164">Oblicza minimalną wartość z kolekcji, lub oblicza wyrażenie podane dla wszystkich elementów w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="b6f40-164">Computes the minimum value from the collection, or computes a supplied expression for all elements in the collection.</span></span> <span data-ttu-id="b6f40-165">Oto przykład:</span><span class="sxs-lookup"><span data-stu-id="b6f40-165">The following is an example:</span></span>

[!code-vb[VbSimpleQuerySamples#10](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_6.vb)]

### <a name="sum"></a><span data-ttu-id="b6f40-166">Suma</span><span class="sxs-lookup"><span data-stu-id="b6f40-166">Sum</span></span>

<span data-ttu-id="b6f40-167">Oblicza sumę wszystkich elementów w kolekcji, lub oblicza wyrażenie podane dla wszystkich elementów w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="b6f40-167">Computes the sum of all elements in the collection, or computes a supplied expression for all elements in the collection.</span></span> <span data-ttu-id="b6f40-168">Oto przykład:</span><span class="sxs-lookup"><span data-stu-id="b6f40-168">The following is an example:</span></span>

[!code-vb[VbSimpleQuerySamples#15](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_7.vb)]

## <a name="example"></a><span data-ttu-id="b6f40-169">Przykład</span><span class="sxs-lookup"><span data-stu-id="b6f40-169">Example</span></span>  

<span data-ttu-id="b6f40-170">Poniższy przykład pokazuje, jak używać `Aggregate` klauzuli w celu zastosowanie funkcji agregujących do wyniku zapytania.</span><span class="sxs-lookup"><span data-stu-id="b6f40-170">The following example shows how to use the `Aggregate` clause to apply aggregate functions to a query result.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#4](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_8.vb)]  
  
## <a name="creating-user-defined-aggregate-functions"></a><span data-ttu-id="b6f40-171">Tworzenie funkcji agregujących zdefiniowanych przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="b6f40-171">Creating User-Defined Aggregate Functions</span></span>

 <span data-ttu-id="b6f40-172">W wyrażeniu zapytania może zawierać własne niestandardowe funkcje agregujące, dodając metody rozszerzenia umożliwiające <xref:System.Collections.Generic.IEnumerable%601> typu.</span><span class="sxs-lookup"><span data-stu-id="b6f40-172">You can include your own custom aggregate functions in a query expression by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> type.</span></span> <span data-ttu-id="b6f40-173">Metoda niestandardowych można wykonywać obliczenia lub operacja wyliczalny kolekcję, do której istnieje odwołanie do funkcji agregującej.</span><span class="sxs-lookup"><span data-stu-id="b6f40-173">Your custom method can then perform a calculation or operation on the enumerable collection that has referenced your aggregate function.</span></span> <span data-ttu-id="b6f40-174">Aby uzyskać więcej informacji dotyczących metod rozszerzających, zobacz [metody rozszerzenia](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="b6f40-174">For more information about extension methods, see [Extension Methods](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).</span></span>  
  
 <span data-ttu-id="b6f40-175">Na przykład poniższy kod przedstawia niestandardowych funkcji agregującej, który oblicza wartość mediany zbioru liczb.</span><span class="sxs-lookup"><span data-stu-id="b6f40-175">For example, the following example shows a custom aggregate function that calculates the median value of a collection of numbers.</span></span> <span data-ttu-id="b6f40-176">Istnieją dwa przeciążenia `Median` — metoda rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="b6f40-176">There are two overloads of the `Median` extension method.</span></span> <span data-ttu-id="b6f40-177">Pierwsze przeciążenie przyjmuje jako dane wejściowe, Kolekcja typu `IEnumerable(Of Double)`.</span><span class="sxs-lookup"><span data-stu-id="b6f40-177">The first overload accepts, as input, a collection of type `IEnumerable(Of Double)`.</span></span> <span data-ttu-id="b6f40-178">Jeśli `Median` funkcji agregującej jest wywoływana dla pola zapytania typu `Double`, ta metoda zostanie wywołana.</span><span class="sxs-lookup"><span data-stu-id="b6f40-178">If the `Median` aggregate function is called for a query field of type `Double`, this method will be called.</span></span> <span data-ttu-id="b6f40-179">Drugie przeciążenie `Median` metody mogą być przekazywane do dowolnego typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="b6f40-179">The second overload of the `Median` method can be passed any generic type.</span></span> <span data-ttu-id="b6f40-180">Przeciążenie ogólne `Median` metoda przyjmuje drugi parametr, który odwołuje się do `Func(Of T, Double)` wyrażenia lambda do projektu wartość dla typu (z kolekcji) jako wartość odpowiedniego typu `Double`.</span><span class="sxs-lookup"><span data-stu-id="b6f40-180">The generic overload of the `Median` method takes a second parameter that references the `Func(Of T, Double)` lambda expression to project a value for a type (from a collection) as the corresponding value of type `Double`.</span></span> <span data-ttu-id="b6f40-181">Następnie deleguje ona obliczenia wartość mediany, aby inne przeciążenia `Median` metody.</span><span class="sxs-lookup"><span data-stu-id="b6f40-181">It then delegates the calculation of the median value to the other overload of the `Median` method.</span></span> <span data-ttu-id="b6f40-182">Aby uzyskać więcej informacji na temat wyrażeń lambda, zobacz [wyrażeń Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="b6f40-182">For more information about lambda expressions, see [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#18](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_9.vb)]  
  
 <span data-ttu-id="b6f40-183">W poniższym przykładzie przedstawiono przykładowe zapytania, które wywołują `Median` funkcję zbierania typu agregacji `Integer`, a kolekcja typu `Double`.</span><span class="sxs-lookup"><span data-stu-id="b6f40-183">The following example shows sample queries that call the `Median` aggregate function on a collection of type `Integer`, and a collection of type `Double`.</span></span> <span data-ttu-id="b6f40-184">Zapytanie, które wywołuje `Median` funkcję na kolekcję typu agregacji `Double` wywołuje przeciążenia `Median` metodę, która przyjmuje jako dane wejściowe, Kolekcja typu `Double`.</span><span class="sxs-lookup"><span data-stu-id="b6f40-184">The query that calls the `Median` aggregate function on the collection of type `Double` calls the overload of the `Median` method that accepts, as input, a collection of type `Double`.</span></span> <span data-ttu-id="b6f40-185">Zapytanie, które wywołuje `Median` funkcję na kolekcję typu agregacji `Integer` wywołuje przeciążenia ogólne `Median` metody.</span><span class="sxs-lookup"><span data-stu-id="b6f40-185">The query that calls the `Median` aggregate function on the collection of type `Integer` calls the generic overload of the `Median` method.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#19](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_10.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="b6f40-186">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b6f40-186">See also</span></span>

- [<span data-ttu-id="b6f40-187">Wprowadzenie do LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b6f40-187">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="b6f40-188">Zapytania</span><span class="sxs-lookup"><span data-stu-id="b6f40-188">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="b6f40-189">Select, klauzula</span><span class="sxs-lookup"><span data-stu-id="b6f40-189">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="b6f40-190">From, klauzula</span><span class="sxs-lookup"><span data-stu-id="b6f40-190">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="b6f40-191">Where, klauzula</span><span class="sxs-lookup"><span data-stu-id="b6f40-191">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
- [<span data-ttu-id="b6f40-192">Klauzula Group By</span><span class="sxs-lookup"><span data-stu-id="b6f40-192">Group By Clause</span></span>](../../../visual-basic/language-reference/queries/group-by-clause.md)
