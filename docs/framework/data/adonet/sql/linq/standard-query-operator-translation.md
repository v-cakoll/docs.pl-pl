---
title: Translacja standardowego operatora zapytania
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a60c30fa-1e68-45fe-b984-f6abb9ede40e
ms.openlocfilehash: 4df1653b7bd6865ad9f5d7d3fb9be6815dcfe018
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781013"
---
# <a name="standard-query-operator-translation"></a><span data-ttu-id="6a308-102">Translacja standardowego operatora zapytania</span><span class="sxs-lookup"><span data-stu-id="6a308-102">Standard Query Operator Translation</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="6a308-103">tłumaczy standardowe operatory zapytań na polecenia SQL.</span><span class="sxs-lookup"><span data-stu-id="6a308-103">translates Standard Query Operators to SQL commands.</span></span> <span data-ttu-id="6a308-104">Procesor zapytań bazy danych określa semantykę wykonywania translacji SQL.</span><span class="sxs-lookup"><span data-stu-id="6a308-104">The query processor of the database determines the execution semantics of SQL translation.</span></span>

<span data-ttu-id="6a308-105">Standardowe operatory zapytań są zdefiniowane dla *sekwencji*.</span><span class="sxs-lookup"><span data-stu-id="6a308-105">Standard Query Operators are defined against *sequences*.</span></span> <span data-ttu-id="6a308-106">Sekwencja jest *uporządkowana* i opiera się na tożsamości odwołania dla każdego elementu sekwencji.</span><span class="sxs-lookup"><span data-stu-id="6a308-106">A sequence is *ordered* and relies on reference identity for each element of the sequence.</span></span> <span data-ttu-id="6a308-107">Aby uzyskać więcej informacji, zobacz [standardowe operatory zapytań —C#omówienie ()](../../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) lub [standardowe operatory zapytań — Omówienie (Visual Basic)](../../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span><span class="sxs-lookup"><span data-stu-id="6a308-107">For more information, see [Standard Query Operators Overview (C#)](../../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) or [Standard Query Operators Overview (Visual Basic)](../../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>

<span data-ttu-id="6a308-108">Program SQL zajmuje się głównie *nieuporządkowanymi zestawami wartości*.</span><span class="sxs-lookup"><span data-stu-id="6a308-108">SQL deals primarily with *unordered sets of values*.</span></span> <span data-ttu-id="6a308-109">Kolejność jest zwykle jawnie określona, operacja po przetworzeniu, która jest stosowana do końcowego wyniku zapytania, a nie do wyników pośrednich.</span><span class="sxs-lookup"><span data-stu-id="6a308-109">Ordering is typically an explicitly stated, post-processing operation that is applied to the final result of a query rather than to intermediate results.</span></span> <span data-ttu-id="6a308-110">Tożsamość jest definiowana przez wartości.</span><span class="sxs-lookup"><span data-stu-id="6a308-110">Identity is defined by values.</span></span> <span data-ttu-id="6a308-111">Z tego powodu zapytania SQL są zrozumiałe do postępowania z wielozestawami *(* zbiorami), a nie *zestawami*.</span><span class="sxs-lookup"><span data-stu-id="6a308-111">For this reason, SQL queries are understood to deal with multisets (*bags*) instead of *sets*.</span></span>

<span data-ttu-id="6a308-112">Poniższe ustępy opisują różnice między standardowymi operatorami zapytań a ich tłumaczeniami SQL dla dostawcy [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]SQL Server.</span><span class="sxs-lookup"><span data-stu-id="6a308-112">The following paragraphs describe the differences between the Standard Query Operators and their SQL translation for the SQL Server provider for [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>

## <a name="operator-support"></a><span data-ttu-id="6a308-113">Obsługa operatorów</span><span class="sxs-lookup"><span data-stu-id="6a308-113">Operator Support</span></span>

### <a name="concat"></a><span data-ttu-id="6a308-114">Concat</span><span class="sxs-lookup"><span data-stu-id="6a308-114">Concat</span></span>

<span data-ttu-id="6a308-115"><xref:System.Linq.Enumerable.Concat%2A> Metoda jest definiowana dla uporządkowanych zestawów wielozbiorów, w których kolejność odbiornika i kolejność argumentu są takie same.</span><span class="sxs-lookup"><span data-stu-id="6a308-115">The <xref:System.Linq.Enumerable.Concat%2A> method is defined for ordered multisets where the order of the receiver and the order of the argument are the same.</span></span> <span data-ttu-id="6a308-116"><xref:System.Linq.Enumerable.Concat%2A>działa jak `UNION ALL` w przypadku zestawów wielozbiorowych, po których następuje typowa kolejność.</span><span class="sxs-lookup"><span data-stu-id="6a308-116"><xref:System.Linq.Enumerable.Concat%2A> works as `UNION ALL` over the multisets followed by the common order.</span></span>

<span data-ttu-id="6a308-117">Ostatnim krokiem jest porządkowanie w języku SQL, zanim zostaną wygenerowane wyniki.</span><span class="sxs-lookup"><span data-stu-id="6a308-117">The final step is ordering in SQL before results are produced.</span></span> <span data-ttu-id="6a308-118"><xref:System.Linq.Enumerable.Concat%2A>nie zachowuje kolejności argumentów.</span><span class="sxs-lookup"><span data-stu-id="6a308-118"><xref:System.Linq.Enumerable.Concat%2A> does not preserve the order of its arguments.</span></span> <span data-ttu-id="6a308-119">Aby zapewnić odpowiednią kolejność, należy jawnie zastanowić się nad <xref:System.Linq.Enumerable.Concat%2A>wynikami.</span><span class="sxs-lookup"><span data-stu-id="6a308-119">To ensure appropriate ordering, you must explicitly order the results of <xref:System.Linq.Enumerable.Concat%2A>.</span></span>

### <a name="intersect-except-union"></a><span data-ttu-id="6a308-120">Intersect, EXCEPT, Union</span><span class="sxs-lookup"><span data-stu-id="6a308-120">Intersect, Except, Union</span></span>

<span data-ttu-id="6a308-121">Metody <xref:System.Linq.Enumerable.Intersect%2A> i<xref:System.Linq.Enumerable.Except%2A> są dobrze zdefiniowane tylko w zestawach.</span><span class="sxs-lookup"><span data-stu-id="6a308-121">The <xref:System.Linq.Enumerable.Intersect%2A> and <xref:System.Linq.Enumerable.Except%2A> methods are well defined only on sets.</span></span> <span data-ttu-id="6a308-122">Semantyka dla wielozestawów jest niezdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="6a308-122">The semantics for multisets is undefined.</span></span>

<span data-ttu-id="6a308-123"><xref:System.Linq.Enumerable.Union%2A> Metoda jest definiowana dla wielozbiorów jako nieuporządkowane złączenie zestawów (w efekcie w wyniku klauzuli Union All w języku SQL).</span><span class="sxs-lookup"><span data-stu-id="6a308-123">The <xref:System.Linq.Enumerable.Union%2A> method is defined for multisets as the unordered concatenation of the multisets (effectively the result of the UNION ALL clause in SQL).</span></span>

### <a name="take-skip"></a><span data-ttu-id="6a308-124">Take, Skip</span><span class="sxs-lookup"><span data-stu-id="6a308-124">Take, Skip</span></span>

<span data-ttu-id="6a308-125"><xref:System.Linq.Enumerable.Take%2A>metody <xref:System.Linq.Enumerable.Skip%2A> i są dobrze zdefiniowane tylko względem *uporządkowanych zestawów*.</span><span class="sxs-lookup"><span data-stu-id="6a308-125"><xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> methods are well defined only against *ordered sets*.</span></span> <span data-ttu-id="6a308-126">Semantyka nieuporządkowanych zestawów lub zestawów wielozbiorówowych nie jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="6a308-126">The semantics for unordered sets or multisets are undefined.</span></span>

> [!NOTE]
> <span data-ttu-id="6a308-127"><xref:System.Linq.Enumerable.Take%2A>i <xref:System.Linq.Enumerable.Skip%2A> mają pewne ograniczenia, gdy są używane w zapytaniach do SQL Server 2000.</span><span class="sxs-lookup"><span data-stu-id="6a308-127"><xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> have certain limitations when they are used in queries against SQL Server 2000.</span></span> <span data-ttu-id="6a308-128">Aby uzyskać więcej informacji, zobacz wpis "Pomiń i przejmowanie wyjątków w SQL Server 2000" w [temacie Rozwiązywanie problemów](troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="6a308-128">For more information, see the "Skip and Take Exceptions in SQL Server 2000" entry in [Troubleshooting](troubleshooting.md).</span></span>

<span data-ttu-id="6a308-129">Ze względu na ograniczenia związane z kolejnością w programie SQL, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] program próbuje przenieść kolejność argumentów tych metod do wyniku metody.</span><span class="sxs-lookup"><span data-stu-id="6a308-129">Because of limitations on ordering in SQL, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tries to move the ordering of the argument of these methods to the result of the method.</span></span> <span data-ttu-id="6a308-130">Rozważmy na przykład następujące [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zapytanie:</span><span class="sxs-lookup"><span data-stu-id="6a308-130">For example, consider the following [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] query:</span></span>

[!code-csharp[DLinqSQOTranslation#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#1)]
[!code-vb[DLinqSQOTranslation#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#1)]

<span data-ttu-id="6a308-131">Wygenerowane SQL dla tego kodu przenosi kolejność do końca w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="6a308-131">The generated SQL for this code moves the ordering to the end, as follows:</span></span>

```sql
SELECT TOP 1 [t0].[CustomerID], [t0].[CompanyName],
FROM [Customers] AS [t0]
WHERE (NOT (EXISTS(
    SELECT NULL AS [EMPTY]
    FROM (
        SELECT TOP 1 [t1].[CustomerID]
        FROM [Customers] AS [t1]
        WHERE [t1].[City] = @p0
        ORDER BY [t1].[CustomerID]
        ) AS [t2]
    WHERE [t0].[CustomerID] = [t2].[CustomerID]
    ))) AND ([t0].[City] = @p1)
ORDER BY [t0].[CustomerID]
```

<span data-ttu-id="6a308-132">Jest to oczywiste, że wszystkie określone porządkowanie muszą być spójne, <xref:System.Linq.Enumerable.Take%2A> gdy <xref:System.Linq.Enumerable.Skip%2A> i są powiązane ze sobą.</span><span class="sxs-lookup"><span data-stu-id="6a308-132">It becomes obvious that all the specified ordering must be consistent when <xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> are chained together.</span></span> <span data-ttu-id="6a308-133">W przeciwnym razie wyniki są niezdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="6a308-133">Otherwise, the results are undefined.</span></span>

<span data-ttu-id="6a308-134">Oba <xref:System.Linq.Enumerable.Take%2A> i<xref:System.Linq.Enumerable.Skip%2A> są dobrze zdefiniowane dla nieujemnych, stałych argumentów całkowitych na podstawie specyfikacji standardowego operatora zapytań.</span><span class="sxs-lookup"><span data-stu-id="6a308-134">Both <xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> are well-defined for non-negative, constant integral arguments based on the Standard Query Operator specification.</span></span>

### <a name="operators-with-no-translation"></a><span data-ttu-id="6a308-135">Operatory bez tłumaczenia</span><span class="sxs-lookup"><span data-stu-id="6a308-135">Operators with No Translation</span></span>

<span data-ttu-id="6a308-136">Następujące metody nie są tłumaczone przez [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6a308-136">The following methods are not translated by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="6a308-137">Najbardziej typową przyczyną jest różnica między nieuporządkowanymi zestawami i sekwencjami.</span><span class="sxs-lookup"><span data-stu-id="6a308-137">The most common reason is the difference between unordered multisets and sequences.</span></span>

|<span data-ttu-id="6a308-138">Operatory</span><span class="sxs-lookup"><span data-stu-id="6a308-138">Operators</span></span>|<span data-ttu-id="6a308-139">Ich uzasadnienie</span><span class="sxs-lookup"><span data-stu-id="6a308-139">Rationale</span></span>|
|---------------|---------------|
|<span data-ttu-id="6a308-140"><xref:System.Linq.Enumerable.TakeWhile%2A>, <xref:System.Linq.Enumerable.SkipWhile%2A></span><span class="sxs-lookup"><span data-stu-id="6a308-140"><xref:System.Linq.Enumerable.TakeWhile%2A>, <xref:System.Linq.Enumerable.SkipWhile%2A></span></span>|<span data-ttu-id="6a308-141">Zapytania SQL działają na wielozestawach, a nie na sekwencjach.</span><span class="sxs-lookup"><span data-stu-id="6a308-141">SQL queries operate on multisets, not on sequences.</span></span> <span data-ttu-id="6a308-142">`ORDER BY`musi być ostatnią klauzulą zastosowana do wyników.</span><span class="sxs-lookup"><span data-stu-id="6a308-142">`ORDER BY` must be the last clause applied to the results.</span></span> <span data-ttu-id="6a308-143">Z tego powodu nie istnieje tłumaczenie ogólnego przeznaczenia dla tych dwóch metod.</span><span class="sxs-lookup"><span data-stu-id="6a308-143">For this reason, there is no general-purpose translation for these two methods.</span></span>|
|<xref:System.Linq.Enumerable.Reverse%2A>|<span data-ttu-id="6a308-144">Tłumaczenie tej metody jest możliwe dla uporządkowanego zestawu, ale nie jest obecnie przetłumaczone [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]przez.</span><span class="sxs-lookup"><span data-stu-id="6a308-144">Translation of this method is possible for an ordered set but is not currently translated by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>|
|<span data-ttu-id="6a308-145"><xref:System.Linq.Enumerable.Last%2A>, <xref:System.Linq.Enumerable.LastOrDefault%2A></span><span class="sxs-lookup"><span data-stu-id="6a308-145"><xref:System.Linq.Enumerable.Last%2A>, <xref:System.Linq.Enumerable.LastOrDefault%2A></span></span>|<span data-ttu-id="6a308-146">Tłumaczenie tych metod jest możliwe dla uporządkowanego zestawu, ale nie jest obecnie przetłumaczone [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]przez.</span><span class="sxs-lookup"><span data-stu-id="6a308-146">Translation of these methods is possible for an ordered set but is not currently translated by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>|
|<span data-ttu-id="6a308-147"><xref:System.Linq.Enumerable.ElementAt%2A>, <xref:System.Linq.Enumerable.ElementAtOrDefault%2A></span><span class="sxs-lookup"><span data-stu-id="6a308-147"><xref:System.Linq.Enumerable.ElementAt%2A>, <xref:System.Linq.Enumerable.ElementAtOrDefault%2A></span></span>|<span data-ttu-id="6a308-148">Zapytania SQL działają na wielozestawach, a nie w sekwencjach z indeksem.</span><span class="sxs-lookup"><span data-stu-id="6a308-148">SQL queries operate on multisets, not on indexable sequences.</span></span>|
|<span data-ttu-id="6a308-149"><xref:System.Linq.Enumerable.DefaultIfEmpty%2A>(przeciążenia z argumentem domyślnym)</span><span class="sxs-lookup"><span data-stu-id="6a308-149"><xref:System.Linq.Enumerable.DefaultIfEmpty%2A> (overload with default arg)</span></span>|<span data-ttu-id="6a308-150">Ogólnie rzecz biorąc nie można określić wartości domyślnej dla dowolnej krotki.</span><span class="sxs-lookup"><span data-stu-id="6a308-150">In general, a default value cannot be specified for an arbitrary tuple.</span></span> <span data-ttu-id="6a308-151">W niektórych przypadkach wartości null dla krotek są możliwe przez sprzężenia zewnętrzne.</span><span class="sxs-lookup"><span data-stu-id="6a308-151">Null values for tuples are possible in some cases through outer joins.</span></span>|

## <a name="expression-translation"></a><span data-ttu-id="6a308-152">Tłumaczenie wyrażeń</span><span class="sxs-lookup"><span data-stu-id="6a308-152">Expression Translation</span></span>

### <a name="null-semantics"></a><span data-ttu-id="6a308-153">Semantyka o wartości null</span><span class="sxs-lookup"><span data-stu-id="6a308-153">Null semantics</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="6a308-154">nie nakłada semantyki porównania o wartości null na serwerze SQL.</span><span class="sxs-lookup"><span data-stu-id="6a308-154">does not impose null comparison semantics on SQL.</span></span> <span data-ttu-id="6a308-155">Operatory porównania są syntaktycznie przetłumaczone na ich odpowiedniki języka SQL.</span><span class="sxs-lookup"><span data-stu-id="6a308-155">Comparison operators are syntactically translated to their SQL equivalents.</span></span> <span data-ttu-id="6a308-156">Z tego powodu semantyka odzwierciedla semantykę SQL, która jest zdefiniowana przez ustawienia serwera lub połączenia.</span><span class="sxs-lookup"><span data-stu-id="6a308-156">For this reason, the semantics reflect SQL semantics that are defined by server or connection settings.</span></span> <span data-ttu-id="6a308-157">Na przykład dwie wartości null są uznawane za nierówne w domyślnych ustawieniach SQL Server, ale można zmienić ustawienia, aby zmienić semantykę.</span><span class="sxs-lookup"><span data-stu-id="6a308-157">For example, two null values are considered unequal under default SQL Server settings, but you can change the settings to change the semantics.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="6a308-158">podczas translacji zapytań nie należy uwzględniać ustawień serwera.</span><span class="sxs-lookup"><span data-stu-id="6a308-158">does not consider server settings when it translates queries.</span></span>

<span data-ttu-id="6a308-159">Porównanie z literałem null jest tłumaczone na odpowiednią wersję SQL (`is null` lub `is not null`).</span><span class="sxs-lookup"><span data-stu-id="6a308-159">A comparison with the literal null is translated to the appropriate SQL version (`is null` or `is not null`).</span></span>

<span data-ttu-id="6a308-160">Wartość `null` sortowania jest definiowana przez SQL Server.</span><span class="sxs-lookup"><span data-stu-id="6a308-160">The value of `null` in collation is defined by SQL Server.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="6a308-161">nie zmienia sortowania.</span><span class="sxs-lookup"><span data-stu-id="6a308-161">does not change the collation.</span></span>

### <a name="aggregates"></a><span data-ttu-id="6a308-162">Agregaty</span><span class="sxs-lookup"><span data-stu-id="6a308-162">Aggregates</span></span>

<span data-ttu-id="6a308-163">Metoda <xref:System.Linq.Enumerable.Sum%2A> agregująca standardowego operatora zapytania daje w wyniku zero dla pustej sekwencji lub dla sekwencji zawierającej tylko wartości null.</span><span class="sxs-lookup"><span data-stu-id="6a308-163">The Standard Query Operator aggregate method <xref:System.Linq.Enumerable.Sum%2A> evaluates to zero for an empty sequence or for a sequence that contains only nulls.</span></span> <span data-ttu-id="6a308-164">W [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]programie semantyka SQL pozostaje niezmieniona i <xref:System.Linq.Enumerable.Sum%2A> szacuje się `null` zamiast zero dla pustej sekwencji lub dla sekwencji zawierającej tylko wartości null.</span><span class="sxs-lookup"><span data-stu-id="6a308-164">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the semantics of SQL are left unchanged, and <xref:System.Linq.Enumerable.Sum%2A> evaluates to `null` instead of zero for an empty sequence or for a sequence that contains only nulls.</span></span>

<span data-ttu-id="6a308-165">Ograniczenia SQL dotyczące wyników pośrednich stosują się [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]do agregacji w.</span><span class="sxs-lookup"><span data-stu-id="6a308-165">SQL limitations on intermediate results apply to aggregates in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="6a308-166"><xref:System.Linq.Enumerable.Sum%2A> 32-bitowe liczby całkowite nie są obliczane przy użyciu 64-bitowych wyników.</span><span class="sxs-lookup"><span data-stu-id="6a308-166">The <xref:System.Linq.Enumerable.Sum%2A> of 32-bit integer quantities is not computed by using 64-bit results.</span></span> <span data-ttu-id="6a308-167">Przepełnienie może wystąpić [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] w przypadku <xref:System.Linq.Enumerable.Sum%2A>tłumaczenia, nawet jeśli implementacja standardowego operatora zapytań nie powoduje przepełnienia odpowiedniej sekwencji w pamięci.</span><span class="sxs-lookup"><span data-stu-id="6a308-167">Overflow might occur for a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translation of <xref:System.Linq.Enumerable.Sum%2A>, even if the Standard Query Operator implementation does not cause an overflow for the corresponding in-memory sequence.</span></span>

<span data-ttu-id="6a308-168">Analogicznie, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Linq.Enumerable.Average%2A> tłumaczenie wartościcałkowitych`double`jest obliczane jako ,niejako.`integer`</span><span class="sxs-lookup"><span data-stu-id="6a308-168">Likewise, the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translation of <xref:System.Linq.Enumerable.Average%2A> of integer values is computed as an `integer`, not as a `double`.</span></span>

### <a name="entity-arguments"></a><span data-ttu-id="6a308-169">Argumenty jednostek</span><span class="sxs-lookup"><span data-stu-id="6a308-169">Entity Arguments</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="6a308-170">Włącza typy jednostek, które mają być używane <xref:System.Linq.Enumerable.GroupBy%2A> w <xref:System.Linq.Enumerable.OrderBy%2A> metodach i.</span><span class="sxs-lookup"><span data-stu-id="6a308-170">enables entity types to be used in the <xref:System.Linq.Enumerable.GroupBy%2A> and <xref:System.Linq.Enumerable.OrderBy%2A> methods.</span></span> <span data-ttu-id="6a308-171">W tłumaczeniu tych operatorów Użycie argumentu typu jest uznawane za równoważne do określenia wszystkich elementów członkowskich tego typu.</span><span class="sxs-lookup"><span data-stu-id="6a308-171">In the translation of these operators, the use of an argument of a type is considered to be the equivalent to specifying all members of that type.</span></span> <span data-ttu-id="6a308-172">Na przykład następujący kod jest równoważny:</span><span class="sxs-lookup"><span data-stu-id="6a308-172">For example, the following code is equivalent:</span></span>

[!code-csharp[DLinqSQOTranslation#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#2)]
[!code-vb[DLinqSQOTranslation#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#2)]

### <a name="equatable--comparable-arguments"></a><span data-ttu-id="6a308-173">Argumenty równe/porównywalne</span><span class="sxs-lookup"><span data-stu-id="6a308-173">Equatable / Comparable Arguments</span></span>

<span data-ttu-id="6a308-174">W implementacji następujących metod jest wymagana równość argumentów:</span><span class="sxs-lookup"><span data-stu-id="6a308-174">Equality of arguments is required in the implementation of the following methods:</span></span>

- <xref:System.Linq.Enumerable.Contains%2A>

- <xref:System.Linq.Enumerable.Skip%2A>

- <xref:System.Linq.Enumerable.Union%2A>

- <xref:System.Linq.Enumerable.Intersect%2A>

- <xref:System.Linq.Enumerable.Except%2A>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="6a308-175">obsługuje równość i porównanie dla *prostych* argumentów, ale nie dla argumentów, które są lub zawierają sekwencje.</span><span class="sxs-lookup"><span data-stu-id="6a308-175">supports equality and comparison for *flat* arguments, but not for arguments that are or contain sequences.</span></span> <span data-ttu-id="6a308-176">Prosty argument jest typem, który można zamapować na wiersz SQL.</span><span class="sxs-lookup"><span data-stu-id="6a308-176">A flat argument is a type that can be mapped to a SQL row.</span></span> <span data-ttu-id="6a308-177">Rzutowanie co najmniej jednego typu jednostki, które można statycznie określić, aby nie zawierało sekwencji jest traktowane jako argument prosty.</span><span class="sxs-lookup"><span data-stu-id="6a308-177">A projection of one or more entity types that can be statically determined not to contain a sequence is considered a flat argument.</span></span>

<span data-ttu-id="6a308-178">Poniżej przedstawiono przykłady prostych argumentów:</span><span class="sxs-lookup"><span data-stu-id="6a308-178">Following are examples of flat arguments:</span></span>

[!code-csharp[DLinqSQOTranslation#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#3)]
[!code-vb[DLinqSQOTranslation#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#3)]

<span data-ttu-id="6a308-179">Poniżej przedstawiono przykłady niepłaskich (hierarchicznych) argumentów.</span><span class="sxs-lookup"><span data-stu-id="6a308-179">The following are examples of non-flat (hierarchical) arguments.</span></span>

[!code-csharp[DLinqSQOTranslation#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#4)]
[!code-vb[DLinqSQOTranslation#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#4)]

### <a name="visual-basic-function-translation"></a><span data-ttu-id="6a308-180">Tłumaczenie funkcji Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6a308-180">Visual Basic Function Translation</span></span>

<span data-ttu-id="6a308-181">Następujące funkcje pomocnika, które są używane przez kompilator Visual Basic są tłumaczone na odpowiednie operatory i funkcje SQL:</span><span class="sxs-lookup"><span data-stu-id="6a308-181">The following helper functions that are used by the Visual Basic compiler are translated to corresponding SQL operators and functions:</span></span>

- `CompareString`

- `DateTime.Compare`

- `Decimal.Compare`

- `IIf (in Microsoft.VisualBasic.Interaction)`

<span data-ttu-id="6a308-182">Metody konwersji:</span><span class="sxs-lookup"><span data-stu-id="6a308-182">Conversion methods:</span></span>

|||||
|-|-|-|-|
|<span data-ttu-id="6a308-183">ToBoolean</span><span class="sxs-lookup"><span data-stu-id="6a308-183">ToBoolean</span></span>|<span data-ttu-id="6a308-184">ToSByte —</span><span class="sxs-lookup"><span data-stu-id="6a308-184">ToSByte</span></span>|<span data-ttu-id="6a308-185">ToByte —</span><span class="sxs-lookup"><span data-stu-id="6a308-185">ToByte</span></span>|<span data-ttu-id="6a308-186">ToChar</span><span class="sxs-lookup"><span data-stu-id="6a308-186">ToChar</span></span>|
|<span data-ttu-id="6a308-187">ToCharArrayRankOne</span><span class="sxs-lookup"><span data-stu-id="6a308-187">ToCharArrayRankOne</span></span>|<span data-ttu-id="6a308-188">ToDate</span><span class="sxs-lookup"><span data-stu-id="6a308-188">ToDate</span></span>|<span data-ttu-id="6a308-189">ToDecimal —</span><span class="sxs-lookup"><span data-stu-id="6a308-189">ToDecimal</span></span>|<span data-ttu-id="6a308-190">ToDouble —</span><span class="sxs-lookup"><span data-stu-id="6a308-190">ToDouble</span></span>|
|<span data-ttu-id="6a308-191">ToInteger</span><span class="sxs-lookup"><span data-stu-id="6a308-191">ToInteger</span></span>|<span data-ttu-id="6a308-192">ToUInteger</span><span class="sxs-lookup"><span data-stu-id="6a308-192">ToUInteger</span></span>|<span data-ttu-id="6a308-193">ToLong</span><span class="sxs-lookup"><span data-stu-id="6a308-193">ToLong</span></span>|<span data-ttu-id="6a308-194">ToULong</span><span class="sxs-lookup"><span data-stu-id="6a308-194">ToULong</span></span>|
|<span data-ttu-id="6a308-195">ToShort</span><span class="sxs-lookup"><span data-stu-id="6a308-195">ToShort</span></span>|<span data-ttu-id="6a308-196">ToUShort</span><span class="sxs-lookup"><span data-stu-id="6a308-196">ToUShort</span></span>|<span data-ttu-id="6a308-197">ToSingle —</span><span class="sxs-lookup"><span data-stu-id="6a308-197">ToSingle</span></span>|<span data-ttu-id="6a308-198">ToString</span><span class="sxs-lookup"><span data-stu-id="6a308-198">ToString</span></span>|

## <a name="inheritance-support"></a><span data-ttu-id="6a308-199">Obsługa dziedziczenia</span><span class="sxs-lookup"><span data-stu-id="6a308-199">Inheritance Support</span></span>

### <a name="inheritance-mapping-restrictions"></a><span data-ttu-id="6a308-200">Ograniczenia mapowania dziedziczenia</span><span class="sxs-lookup"><span data-stu-id="6a308-200">Inheritance Mapping Restrictions</span></span>

<span data-ttu-id="6a308-201">Aby uzyskać więcej informacji, zobacz [jak: Hierarchie](how-to-map-inheritance-hierarchies.md)dziedziczenia mapowania.</span><span class="sxs-lookup"><span data-stu-id="6a308-201">For more information, see [How to: Map Inheritance Hierarchies](how-to-map-inheritance-hierarchies.md).</span></span>

### <a name="inheritance-in-queries"></a><span data-ttu-id="6a308-202">Dziedziczenie w zapytaniach</span><span class="sxs-lookup"><span data-stu-id="6a308-202">Inheritance in Queries</span></span>

<span data-ttu-id="6a308-203">C#rzutowania są obsługiwane tylko w projekcji.</span><span class="sxs-lookup"><span data-stu-id="6a308-203">C# casts are supported only in projection.</span></span> <span data-ttu-id="6a308-204">Rzutowania, które są używane w innym miejscu, nie są tłumaczone i są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="6a308-204">Casts that are used elsewhere are not translated and are ignored.</span></span> <span data-ttu-id="6a308-205">Oprócz nazw funkcji SQL, SQL naprawdę wykonuje jedynie odpowiednik środowiska uruchomieniowego języka wspólnego (CLR) <xref:System.Convert>.</span><span class="sxs-lookup"><span data-stu-id="6a308-205">Aside from SQL function names, SQL really only performs the equivalent of the common language runtime (CLR) <xref:System.Convert>.</span></span> <span data-ttu-id="6a308-206">Oznacza to, że SQL może zmienić wartość jednego typu na inny.</span><span class="sxs-lookup"><span data-stu-id="6a308-206">That is, SQL can change the value of one type to another.</span></span> <span data-ttu-id="6a308-207">Nie istnieje odpowiednik rzutowania CLR, ponieważ nie ma koncepcji dotyczącej reinterpretacji tych samych bitów, co w przypadku innych typów.</span><span class="sxs-lookup"><span data-stu-id="6a308-207">There is no equivalent of CLR cast because there is no concept of reinterpreting the same bits as those of another type.</span></span> <span data-ttu-id="6a308-208">To dlatego, że C# rzutowanie działa tylko lokalnie.</span><span class="sxs-lookup"><span data-stu-id="6a308-208">That is why a C# cast works only locally.</span></span> <span data-ttu-id="6a308-209">Nie jest ona zdalna.</span><span class="sxs-lookup"><span data-stu-id="6a308-209">It is not remoted.</span></span>

<span data-ttu-id="6a308-210">Operatory, `is` `Select` i `as` i`GetType` Metoda nie są ograniczone do operatora.</span><span class="sxs-lookup"><span data-stu-id="6a308-210">The operators, `is` and `as`, and the `GetType` method are not restricted to the `Select` operator.</span></span> <span data-ttu-id="6a308-211">Mogą one być używane w innych operatorach zapytań.</span><span class="sxs-lookup"><span data-stu-id="6a308-211">They can be used in other query operators also.</span></span>

## <a name="sql-server-2008-support"></a><span data-ttu-id="6a308-212">SQL Server 2008 Support</span><span class="sxs-lookup"><span data-stu-id="6a308-212">SQL Server 2008 Support</span></span>

<span data-ttu-id="6a308-213">Począwszy od .NET Framework 3,5 z dodatkiem SP1, LINQ to SQL obsługuje mapowanie do nowych typów dat i godzin wprowadzonych w SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="6a308-213">Starting with the .NET Framework 3.5 SP1, LINQ to SQL supports mapping to new date and time types introduced with SQL Server 2008.</span></span> <span data-ttu-id="6a308-214">Istnieją jednak ograniczenia dotyczące LINQ to SQL operatorów zapytań, których można używać podczas pracy z wartościami mapowanymi na te nowe typy.</span><span class="sxs-lookup"><span data-stu-id="6a308-214">But, there are some limitations to the LINQ to SQL query operators that you can use when operating against values mapped to these new types.</span></span>

### <a name="unsupported-query-operators"></a><span data-ttu-id="6a308-215">Nieobsługiwane operatory zapytań</span><span class="sxs-lookup"><span data-stu-id="6a308-215">Unsupported Query Operators</span></span>

<span data-ttu-id="6a308-216">Następujące operatory zapytań nie są obsługiwane w przypadku wartości mapowanych na nowe SQL Server typy daty i godziny: `DATETIME2`, `DATE`, `TIME`i `DATETIMEOFFSET`.</span><span class="sxs-lookup"><span data-stu-id="6a308-216">The following query operators are not supported on values mapped to the new SQL Server date and time types: `DATETIME2`, `DATE`, `TIME`, and `DATETIMEOFFSET`.</span></span>

- `Aggregate`

- `Average`

- `LastOrDefault`

- `OfType`

- `Sum`

<span data-ttu-id="6a308-217">Aby uzyskać więcej informacji na temat mapowania na te SQL Server typy daty i godziny, zobacz [Mapowanie typu SQL-CLR](sql-clr-type-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="6a308-217">For more information about mapping to these SQL Server date and time types, see [SQL-CLR Type Mapping](sql-clr-type-mapping.md).</span></span>

## <a name="sql-server-2005-support"></a><span data-ttu-id="6a308-218">Obsługa SQL Server 2005</span><span class="sxs-lookup"><span data-stu-id="6a308-218">SQL Server 2005 Support</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="6a308-219">Program nie obsługuje następujących funkcji SQL Server 2005:</span><span class="sxs-lookup"><span data-stu-id="6a308-219">does not support the following SQL Server 2005 features:</span></span>

- <span data-ttu-id="6a308-220">Procedury składowane zapisane dla środowiska SQL CLR.</span><span class="sxs-lookup"><span data-stu-id="6a308-220">Stored procedures written for SQL CLR.</span></span>

- <span data-ttu-id="6a308-221">Typ zdefiniowany przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="6a308-221">User-defined type.</span></span>

- <span data-ttu-id="6a308-222">Funkcje zapytania XML.</span><span class="sxs-lookup"><span data-stu-id="6a308-222">XML query features.</span></span>

## <a name="sql-server-2000-support"></a><span data-ttu-id="6a308-223">SQL Server 2000 Support</span><span class="sxs-lookup"><span data-stu-id="6a308-223">SQL Server 2000 Support</span></span>

<span data-ttu-id="6a308-224">Następujące ograniczenia SQL Server 2000 (w porównaniu do Microsoft SQL Server 2005) wpływają [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] na pomoc techniczną.</span><span class="sxs-lookup"><span data-stu-id="6a308-224">The following SQL Server 2000 limitations (compared to Microsoft SQL Server 2005) affect [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] support.</span></span>

### <a name="cross-apply-and-outer-apply-operators"></a><span data-ttu-id="6a308-225">Cross Apply i OUTER APPLY — operatory</span><span class="sxs-lookup"><span data-stu-id="6a308-225">Cross Apply and Outer Apply Operators</span></span>

<span data-ttu-id="6a308-226">Te operatory nie są dostępne w SQL Server 2000.</span><span class="sxs-lookup"><span data-stu-id="6a308-226">These operators are not available in SQL Server 2000.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="6a308-227">podejmuje próbę przetworzenia serii, aby zamienić je na odpowiednie sprzężenia.</span><span class="sxs-lookup"><span data-stu-id="6a308-227">tries a series of rewrites to replace them with appropriate joins.</span></span>

<span data-ttu-id="6a308-228">`Cross Apply`i `Outer Apply` są generowane dla nawigacji relacji.</span><span class="sxs-lookup"><span data-stu-id="6a308-228">`Cross Apply` and `Outer Apply` are generated for relationship navigations.</span></span> <span data-ttu-id="6a308-229">Zestaw zapytań, dla których takie ponowne zapisywanie jest możliwe, nie jest dobrze zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="6a308-229">The set of queries for which such rewrites are possible is not well defined.</span></span> <span data-ttu-id="6a308-230">Z tego powodu minimalny zestaw zapytań, który jest obsługiwany przez SQL Server 2000, jest zestawem, który nie obejmuje nawigacji między relacjami.</span><span class="sxs-lookup"><span data-stu-id="6a308-230">For this reason, the minimal set of queries that is supported for SQL Server 2000 is the set that does not involve relationship navigation.</span></span>

### <a name="text--ntext"></a><span data-ttu-id="6a308-231">tekst/ntext</span><span class="sxs-lookup"><span data-stu-id="6a308-231">text / ntext</span></span>

<span data-ttu-id="6a308-232">Typów `text` `varchar(max)` `nvarchar(max)`  / danych nie można używać w niektórych operacjach zapytania względem, które są obsługiwane przez Microsoft SQL Server 2005.  /  `ntext`</span><span class="sxs-lookup"><span data-stu-id="6a308-232">Data types `text` / `ntext` cannot be used in certain query operations against `varchar(max)` / `nvarchar(max)`, which are supported by Microsoft SQL Server 2005.</span></span>

<span data-ttu-id="6a308-233">Dla tego ograniczenia nie jest dostępne żadne rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="6a308-233">No resolution is available for this limitation.</span></span> <span data-ttu-id="6a308-234">W związku z tym nie `Distinct()` można używać w żadnym wyniku, który zawiera elementy członkowskie `text` , `ntext` które są mapowane na kolumny lub.</span><span class="sxs-lookup"><span data-stu-id="6a308-234">Specifically, you cannot use `Distinct()` on any result that contains members that are mapped to `text` or `ntext` columns.</span></span>

### <a name="behavior-triggered-by-nested-queries"></a><span data-ttu-id="6a308-235">Zachowanie wyzwalane przez zapytania zagnieżdżone</span><span class="sxs-lookup"><span data-stu-id="6a308-235">Behavior Triggered by Nested Queries</span></span>

<span data-ttu-id="6a308-236">Spinacz SQL Server 2000 (do SP4) ma pewne idiosyncrasies, które są wyzwalane przez zagnieżdżone zapytania.</span><span class="sxs-lookup"><span data-stu-id="6a308-236">SQL Server 2000 (through SP4) binder has some idiosyncrasies that are triggered by nested queries.</span></span> <span data-ttu-id="6a308-237">Zbiór zapytań SQL, które wyzwalają te idiosyncrasies, nie jest dobrze zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="6a308-237">The set of SQL queries that triggers these idiosyncrasies is not well defined.</span></span> <span data-ttu-id="6a308-238">Z tego powodu nie można zdefiniować zestawu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zapytań, które mogą spowodować SQL Server wyjątków.</span><span class="sxs-lookup"><span data-stu-id="6a308-238">For this reason, you cannot define the set of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries that might cause SQL Server exceptions.</span></span>

### <a name="skip-and-take-operators"></a><span data-ttu-id="6a308-239">Pomiń i wykonaj operatory</span><span class="sxs-lookup"><span data-stu-id="6a308-239">Skip and Take Operators</span></span>

<span data-ttu-id="6a308-240"><xref:System.Linq.Enumerable.Take%2A>i <xref:System.Linq.Enumerable.Skip%2A> mają pewne ograniczenia, gdy są używane w zapytaniach do SQL Server 2000.</span><span class="sxs-lookup"><span data-stu-id="6a308-240"><xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> have certain limitations when they are used in queries against SQL Server 2000.</span></span> <span data-ttu-id="6a308-241">Aby uzyskać więcej informacji, zobacz wpis "Pomiń i przejmowanie wyjątków w SQL Server 2000" w [temacie Rozwiązywanie problemów](troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="6a308-241">For more information, see the "Skip and Take Exceptions in SQL Server 2000" entry in [Troubleshooting](troubleshooting.md).</span></span>

## <a name="object-materialization"></a><span data-ttu-id="6a308-242">Materializacja obiektu</span><span class="sxs-lookup"><span data-stu-id="6a308-242">Object Materialization</span></span>

<span data-ttu-id="6a308-243">Materializację tworzy obiekty CLR z wierszy, które są zwracane przez co najmniej jedno zapytanie SQL.</span><span class="sxs-lookup"><span data-stu-id="6a308-243">Materialization creates CLR objects from rows that are returned by one or more SQL queries.</span></span>

- <span data-ttu-id="6a308-244">Następujące wywołania są *wykonywane lokalnie* jako część materializację:</span><span class="sxs-lookup"><span data-stu-id="6a308-244">The following calls are *executed locally* as a part of materialization:</span></span>

  - <span data-ttu-id="6a308-245">Konstruktorów</span><span class="sxs-lookup"><span data-stu-id="6a308-245">Constructors</span></span>

  - <span data-ttu-id="6a308-246">`ToString`metody w projekcjach</span><span class="sxs-lookup"><span data-stu-id="6a308-246">`ToString` methods in projections</span></span>

  - <span data-ttu-id="6a308-247">Wpisz rzutowania w projekcjach</span><span class="sxs-lookup"><span data-stu-id="6a308-247">Type casts in projections</span></span>

- <span data-ttu-id="6a308-248">Metody, które po <xref:System.Linq.Enumerable.AsEnumerable%2A> metodzie są *wykonywane lokalnie*.</span><span class="sxs-lookup"><span data-stu-id="6a308-248">Methods that follow the <xref:System.Linq.Enumerable.AsEnumerable%2A> method are *executed locally*.</span></span> <span data-ttu-id="6a308-249">Ta metoda nie powoduje natychmiastowego wykonania.</span><span class="sxs-lookup"><span data-stu-id="6a308-249">This method does not cause immediate execution.</span></span>

- <span data-ttu-id="6a308-250">Można użyć `struct` jako typu zwracanego wyniku zapytania lub jako elementu członkowskiego typu wynik.</span><span class="sxs-lookup"><span data-stu-id="6a308-250">You can use a `struct` as the return type of a query result or as a member of the result type.</span></span> <span data-ttu-id="6a308-251">Jednostki muszą być klasami.</span><span class="sxs-lookup"><span data-stu-id="6a308-251">Entities are required to be classes.</span></span> <span data-ttu-id="6a308-252">Typy anonimowe są materiałowe jako wystąpienia klas, ale nazwanych struktur (niebędących jednostkami) można używać w projekcji.</span><span class="sxs-lookup"><span data-stu-id="6a308-252">Anonymous types are materialized as class instances, but named structs (non-entities) can be used in projection.</span></span>

- <span data-ttu-id="6a308-253">Element członkowski typu zwracanego wyniku zapytania może być typu <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="6a308-253">A member of the return type of a query result can be of type <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="6a308-254">Jest on materiałowy jako kolekcja lokalna.</span><span class="sxs-lookup"><span data-stu-id="6a308-254">It is materialized as a local collection.</span></span>

- <span data-ttu-id="6a308-255">Następujące metody powodują *natychmiastowe materializację* sekwencji, do której są stosowane metody:</span><span class="sxs-lookup"><span data-stu-id="6a308-255">The following methods cause the *immediate materialization* of the sequence that the methods are applied to:</span></span>

  - <xref:System.Linq.Enumerable.ToList%2A>

  - <xref:System.Linq.Enumerable.ToDictionary%2A>

  - <xref:System.Linq.Enumerable.ToArray%2A>

## <a name="see-also"></a><span data-ttu-id="6a308-256">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6a308-256">See also</span></span>

- [<span data-ttu-id="6a308-257">Dokumentacja</span><span class="sxs-lookup"><span data-stu-id="6a308-257">Reference</span></span>](reference.md)
- [<span data-ttu-id="6a308-258">Zwracanie lub pomijanie elementów w sekwencji</span><span class="sxs-lookup"><span data-stu-id="6a308-258">Return Or Skip Elements in a Sequence</span></span>](return-or-skip-elements-in-a-sequence.md)
- [<span data-ttu-id="6a308-259">Łączenie dwóch sekwencji</span><span class="sxs-lookup"><span data-stu-id="6a308-259">Concatenate Two Sequences</span></span>](concatenate-two-sequences.md)
- [<span data-ttu-id="6a308-260">Zwracanie zestawu różnic między dwoma sekwencjami</span><span class="sxs-lookup"><span data-stu-id="6a308-260">Return the Set Difference Between Two Sequences</span></span>](return-the-set-difference-between-two-sequences.md)
- [<span data-ttu-id="6a308-261">Zwracanie zestawu części wspólnych dwóch sekwencji</span><span class="sxs-lookup"><span data-stu-id="6a308-261">Return the Set Intersection of Two Sequences</span></span>](return-the-set-intersection-of-two-sequences.md)
- [<span data-ttu-id="6a308-262">Zwracanie sumy zbiorów dwóch sekwencji</span><span class="sxs-lookup"><span data-stu-id="6a308-262">Return the Set Union of Two Sequences</span></span>](return-the-set-union-of-two-sequences.md)
