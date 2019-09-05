---
title: Funkcje agregujące Canonical
ms.date: 03/30/2017
ms.assetid: 3bcff826-ca90-41b3-a791-04d6ff0e5085
ms.openlocfilehash: 3f4bb84c45e503fc0018e7869f3b41ddab4581a6
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251354"
---
# <a name="aggregate-canonical-functions"></a><span data-ttu-id="3e44e-102">Funkcje agregujące Canonical</span><span class="sxs-lookup"><span data-stu-id="3e44e-102">Aggregate Canonical Functions</span></span>

<span data-ttu-id="3e44e-103">Agregaty są wyrażeniami, które redukują serię wartości wejściowych, na przykład pojedynczą wartość.</span><span class="sxs-lookup"><span data-stu-id="3e44e-103">Aggregates are expressions that reduce a series of input values into, for example, a single value.</span></span> <span data-ttu-id="3e44e-104">Agregaty są zwykle używane w połączeniu z klauzulą GROUP BY wyrażenia SELECT, a istnieją ograniczenia dotyczące miejsca, w którym można ich używać.</span><span class="sxs-lookup"><span data-stu-id="3e44e-104">Aggregates are normally used in conjunction with the GROUP BY clause of the SELECT expression, and there are constraints on where they can be used.</span></span>

## <a name="aggregate-entity-sql-canonical-functions"></a><span data-ttu-id="3e44e-105">Agreguj Entity SQL funkcje kanoniczne</span><span class="sxs-lookup"><span data-stu-id="3e44e-105">Aggregate Entity SQL canonical functions</span></span>

<span data-ttu-id="3e44e-106">Poniżej znajdują się wartości zagregowane Entity SQL funkcje kanoniczne.</span><span class="sxs-lookup"><span data-stu-id="3e44e-106">The following are the aggregate Entity SQL canonical functions.</span></span>

### <a name="avgexpression"></a><span data-ttu-id="3e44e-107">Średnia (wyrażenie)</span><span class="sxs-lookup"><span data-stu-id="3e44e-107">Avg(expression)</span></span>

<span data-ttu-id="3e44e-108">Zwraca średnią wartości innych niż null.</span><span class="sxs-lookup"><span data-stu-id="3e44e-108">Returns the average of the non-null values.</span></span>

<span data-ttu-id="3e44e-109">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="3e44e-109">**Arguments**</span></span>

<span data-ttu-id="3e44e-110">`Int32`, ,,`Double`I .`Decimal` `Int64`</span><span class="sxs-lookup"><span data-stu-id="3e44e-110">An `Int32`, `Int64`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="3e44e-111">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="3e44e-111">**Return Value**</span></span>

<span data-ttu-id="3e44e-112">Typ `expression` `null` lub `null` , jeśli wszystkie wartości wejściowe są wartościami.</span><span class="sxs-lookup"><span data-stu-id="3e44e-112">The type of `expression`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="3e44e-113">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="3e44e-113">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_AVG](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_avg)]
[!code-sql[DP EntityServices Concepts#EDM_AVG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_avg)]

### <a name="bigcountexpression"></a><span data-ttu-id="3e44e-114">BigCount (wyrażenie)</span><span class="sxs-lookup"><span data-stu-id="3e44e-114">BigCount(expression)</span></span>

<span data-ttu-id="3e44e-115">Zwraca rozmiar zagregowany, w tym wartość null i zduplikowane wartości.</span><span class="sxs-lookup"><span data-stu-id="3e44e-115">Returns the size of the aggregate including null and duplicate values.</span></span>

<span data-ttu-id="3e44e-116">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="3e44e-116">**Arguments**</span></span>

<span data-ttu-id="3e44e-117">Dowolny typ.</span><span class="sxs-lookup"><span data-stu-id="3e44e-117">Any type.</span></span>

<span data-ttu-id="3e44e-118">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="3e44e-118">**Return Value**</span></span>

<span data-ttu-id="3e44e-119">A `Int64`.</span><span class="sxs-lookup"><span data-stu-id="3e44e-119">An `Int64`.</span></span>

<span data-ttu-id="3e44e-120">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="3e44e-120">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_BIGCOUNT](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_bigcount)]
[!code-sql[DP EntityServices Concepts#EDM_BIGCOUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_bigcount)]

### <a name="countexpression"></a><span data-ttu-id="3e44e-121">Count (wyrażenie)</span><span class="sxs-lookup"><span data-stu-id="3e44e-121">Count(expression)</span></span>

<span data-ttu-id="3e44e-122">Zwraca rozmiar zagregowany, w tym wartość null i zduplikowane wartości.</span><span class="sxs-lookup"><span data-stu-id="3e44e-122">Returns the size of the aggregate including null and duplicate values.</span></span>

<span data-ttu-id="3e44e-123">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="3e44e-123">**Arguments**</span></span>

<span data-ttu-id="3e44e-124">Dowolny typ.</span><span class="sxs-lookup"><span data-stu-id="3e44e-124">Any type.</span></span>

<span data-ttu-id="3e44e-125">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="3e44e-125">**Return Value**</span></span>

<span data-ttu-id="3e44e-126">A `Int32`.</span><span class="sxs-lookup"><span data-stu-id="3e44e-126">An `Int32`.</span></span>

<span data-ttu-id="3e44e-127">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="3e44e-127">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_COUNT](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_count)]
[!code-sql[DP EntityServices Concepts#EDM_COUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_count)]

### <a name="maxexpression"></a><span data-ttu-id="3e44e-128">Max (wyrażenie)</span><span class="sxs-lookup"><span data-stu-id="3e44e-128">Max(expression)</span></span>

<span data-ttu-id="3e44e-129">Zwraca wartość maksymalną wartości różną od null.</span><span class="sxs-lookup"><span data-stu-id="3e44e-129">Returns the maximum of the non-null values.</span></span>

<span data-ttu-id="3e44e-130">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="3e44e-130">**Arguments**</span></span>

<span data-ttu-id="3e44e-131">A `Byte`, `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, `Decimal`, `DateTime`, `DateTimeOffset`, `Time`, `String`, `Binary`.</span><span class="sxs-lookup"><span data-stu-id="3e44e-131">A `Byte`, `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, `Decimal`, `DateTime`, `DateTimeOffset`, `Time`, `String`, `Binary`.</span></span>

<span data-ttu-id="3e44e-132">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="3e44e-132">**Return Value**</span></span>

<span data-ttu-id="3e44e-133">Typ `expression` `null` lub `null` , jeśli wszystkie wartości wejściowe są wartościami.</span><span class="sxs-lookup"><span data-stu-id="3e44e-133">The type of `expression`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="3e44e-134">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="3e44e-134">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_MAX](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_max)]
[!code-sql[DP EntityServices Concepts#EDM_MAX](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_max)]

### <a name="minexpression"></a><span data-ttu-id="3e44e-135">Min (wyrażenie)</span><span class="sxs-lookup"><span data-stu-id="3e44e-135">Min(expression)</span></span>

<span data-ttu-id="3e44e-136">Zwraca wartość minimalną wartości innych niż null.</span><span class="sxs-lookup"><span data-stu-id="3e44e-136">Returns the minimum of the non-null values.</span></span>

<span data-ttu-id="3e44e-137">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="3e44e-137">**Arguments**</span></span>

<span data-ttu-id="3e44e-138">A `Byte`, `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, `Decimal`, `DateTime`, `DateTimeOffset`, `Time`, `String`, `Binary`.</span><span class="sxs-lookup"><span data-stu-id="3e44e-138">A `Byte`, `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, `Decimal`, `DateTime`, `DateTimeOffset`, `Time`, `String`, `Binary`.</span></span>

<span data-ttu-id="3e44e-139">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="3e44e-139">**Return Value**</span></span>

<span data-ttu-id="3e44e-140">Typ `expression` `null` lub `null` , jeśli wszystkie wartości wejściowe są wartościami.</span><span class="sxs-lookup"><span data-stu-id="3e44e-140">The type of `expression`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="3e44e-141">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="3e44e-141">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_MIN](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_min)]
[!code-sql[DP EntityServices Concepts#EDM_MIN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_min)]

### <a name="stdevexpression"></a><span data-ttu-id="3e44e-142">StDev (wyrażenie)</span><span class="sxs-lookup"><span data-stu-id="3e44e-142">StDev(expression)</span></span>

<span data-ttu-id="3e44e-143">Zwraca odchylenie standardowe wartości innych niż null.</span><span class="sxs-lookup"><span data-stu-id="3e44e-143">Returns the standard deviation of the non-null values.</span></span>

<span data-ttu-id="3e44e-144">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="3e44e-144">**Arguments**</span></span>

<span data-ttu-id="3e44e-145">`Int32` ,`Int64` ,`Decimal`, .`Double`</span><span class="sxs-lookup"><span data-stu-id="3e44e-145">An `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="3e44e-146">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="3e44e-146">**Return Value**</span></span>

<span data-ttu-id="3e44e-147">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="3e44e-147">A `Double`.</span></span> <span data-ttu-id="3e44e-148">`Null`, jeśli wszystkie wartości wejściowe są `null` wartościami.</span><span class="sxs-lookup"><span data-stu-id="3e44e-148">`Null`, if all input values are `null` values.</span></span>

<span data-ttu-id="3e44e-149">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="3e44e-149">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_STDEV](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_stdev)]
[!code-sql[DP EntityServices Concepts#EDM_STDEV](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_stdev)]

### <a name="stdevpexpression"></a><span data-ttu-id="3e44e-150">StDevP (wyrażenie)</span><span class="sxs-lookup"><span data-stu-id="3e44e-150">StDevP(expression)</span></span>

<span data-ttu-id="3e44e-151">Zwraca odchylenie standardowe dla populacji wszystkich wartości.</span><span class="sxs-lookup"><span data-stu-id="3e44e-151">Returns the standard deviation for the population of all values.</span></span>

<span data-ttu-id="3e44e-152">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="3e44e-152">**Arguments**</span></span>

<span data-ttu-id="3e44e-153">`Int32` ,`Int64` ,`Decimal`, .`Double`</span><span class="sxs-lookup"><span data-stu-id="3e44e-153">An `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="3e44e-154">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="3e44e-154">**Return Value**</span></span>

<span data-ttu-id="3e44e-155">A `Double`, lub `null` Jeśli wszystkie wartości wejściowe są `null` wartościami.</span><span class="sxs-lookup"><span data-stu-id="3e44e-155">A `Double`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="3e44e-156">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="3e44e-156">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_STDEVP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_stdevp)]
[!code-sql[DP EntityServices Concepts#EDM_STDEVP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_stdevp)]

### <a name="sumexpression"></a><span data-ttu-id="3e44e-157">Sum (wyrażenie)</span><span class="sxs-lookup"><span data-stu-id="3e44e-157">Sum(expression)</span></span>

<span data-ttu-id="3e44e-158">Zwraca sumę wartości innych niż null.</span><span class="sxs-lookup"><span data-stu-id="3e44e-158">Returns the sum of the non-null values.</span></span>

<span data-ttu-id="3e44e-159">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="3e44e-159">**Arguments**</span></span>

<span data-ttu-id="3e44e-160">`Int32` ,`Int64` ,`Decimal`, .`Double`</span><span class="sxs-lookup"><span data-stu-id="3e44e-160">An `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="3e44e-161">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="3e44e-161">**Return Value**</span></span>

<span data-ttu-id="3e44e-162">A `Double`, lub `null` Jeśli wszystkie wartości wejściowe są `null` wartościami.</span><span class="sxs-lookup"><span data-stu-id="3e44e-162">A `Double`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="3e44e-163">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="3e44e-163">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_SUM](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_sum)]
[!code-sql[DP EntityServices Concepts#EDM_SUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_sum)]

### <a name="varexpression"></a><span data-ttu-id="3e44e-164">Var (wyrażenie)</span><span class="sxs-lookup"><span data-stu-id="3e44e-164">Var(expression)</span></span>

<span data-ttu-id="3e44e-165">Zwraca wariancję wszystkich wartości innych niż null.</span><span class="sxs-lookup"><span data-stu-id="3e44e-165">Returns the variance of all non-null values.</span></span>

<span data-ttu-id="3e44e-166">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="3e44e-166">**Arguments**</span></span>

<span data-ttu-id="3e44e-167">`Int32` ,`Int64` ,`Decimal`, .`Double`</span><span class="sxs-lookup"><span data-stu-id="3e44e-167">An `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="3e44e-168">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="3e44e-168">**Return Value**</span></span>

<span data-ttu-id="3e44e-169">A `Double`, lub `null` Jeśli wszystkie wartości wejściowe są `null` wartościami.</span><span class="sxs-lookup"><span data-stu-id="3e44e-169">A `Double`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="3e44e-170">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="3e44e-170">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_VAR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_var)]
[!code-sql[DP EntityServices Concepts#EDM_VAR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_var)]

### <a name="varpexpression"></a><span data-ttu-id="3e44e-171">VarP (wyrażenie)</span><span class="sxs-lookup"><span data-stu-id="3e44e-171">VarP(expression)</span></span>

<span data-ttu-id="3e44e-172">Zwraca wariancję populacji dla wszystkich wartości innych niż null.</span><span class="sxs-lookup"><span data-stu-id="3e44e-172">Returns the variance for the population of all non-null values.</span></span>

<span data-ttu-id="3e44e-173">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="3e44e-173">**Arguments**</span></span>

<span data-ttu-id="3e44e-174">`Int32` ,`Int64` ,`Decimal`, .`Double`</span><span class="sxs-lookup"><span data-stu-id="3e44e-174">An `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="3e44e-175">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="3e44e-175">**Return Value**</span></span>

<span data-ttu-id="3e44e-176">A `Double`, lub `null` Jeśli wszystkie wartości wejściowe są `null` wartościami.</span><span class="sxs-lookup"><span data-stu-id="3e44e-176">A `Double`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="3e44e-177">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="3e44e-177">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_VARP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_varp)]
[!code-sql[DP EntityServices Concepts#EDM_VARP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_varp)]

<span data-ttu-id="3e44e-178">Równoważne funkcje są dostępne w dostawcy zarządzanym przez klienta programu Microsoft SQL.</span><span class="sxs-lookup"><span data-stu-id="3e44e-178">Equivalent functionality is available in the Microsoft SQL Client Managed Provider.</span></span> <span data-ttu-id="3e44e-179">Aby uzyskać więcej informacji, zobacz temat [SqlClient for Entity Framework Functions](../sqlclient-for-ef-functions.md).</span><span class="sxs-lookup"><span data-stu-id="3e44e-179">For more information, see [SqlClient for Entity Framework Functions](../sqlclient-for-ef-functions.md).</span></span>

## <a name="collection-based-aggregates"></a><span data-ttu-id="3e44e-180">Agregacje oparte na kolekcjach</span><span class="sxs-lookup"><span data-stu-id="3e44e-180">Collection-based aggregates</span></span>

<span data-ttu-id="3e44e-181">Agregacje oparte na kolekcjach (funkcje kolekcji) działają na kolekcjach i zwracają wartość.</span><span class="sxs-lookup"><span data-stu-id="3e44e-181">Collection-based aggregates (collection functions) operate on collections and return a value.</span></span> <span data-ttu-id="3e44e-182">Na przykład jeśli zamówienia są kolekcją wszystkich zamówień, można obliczyć najwcześniejszą datę wysyłki przy użyciu następującego wyrażenia:</span><span class="sxs-lookup"><span data-stu-id="3e44e-182">For example if ORDERS is a collection of all orders, you can calculate the earliest ship date with the following expression:</span></span>

```sql
min(select value o.ShipDate from LOB.Orders as o)
```

<span data-ttu-id="3e44e-183">Wyrażenia wewnątrz agregacji opartych na kolekcjach są oceniane w ramach bieżącego zakresu rozpoznawania nazw otoczenia.</span><span class="sxs-lookup"><span data-stu-id="3e44e-183">Expressions inside collection-based aggregates are evaluated within the current ambient name-resolution scope.</span></span>

## <a name="group-based-aggregates"></a><span data-ttu-id="3e44e-184">Agregacje oparte na grupach</span><span class="sxs-lookup"><span data-stu-id="3e44e-184">Group-based aggregates</span></span>

<span data-ttu-id="3e44e-185">Agregacje oparte na grupach są obliczane na podstawie grupy zgodnie z definicją w klauzuli GROUP BY.</span><span class="sxs-lookup"><span data-stu-id="3e44e-185">Group-based aggregates are calculated over a group as defined by the GROUP BY clause.</span></span> <span data-ttu-id="3e44e-186">Dla każdej grupy w wyniku oddzielna wartość zagregowana jest obliczana przy użyciu elementów w każdej grupie jako dane wejściowe do obliczenia agregacji.</span><span class="sxs-lookup"><span data-stu-id="3e44e-186">For each group in the result, a separate aggregate is calculated by using the elements in each group as input to the aggregate calculation.</span></span> <span data-ttu-id="3e44e-187">Gdy klauzula GROUP by jest używana w wyrażeniu SELECT, w klauzuli projekcji lub order by może występować tylko nazwa wyrażenia grupującego, agregacje lub wyrażenia stałe.</span><span class="sxs-lookup"><span data-stu-id="3e44e-187">When a group-by clause is used in a select expression, only grouping expression names, aggregates, or constant expressions can be present in the projection or order-by clause.</span></span>

<span data-ttu-id="3e44e-188">Poniższy przykład oblicza średnią ilość zamówioną dla każdego produktu:</span><span class="sxs-lookup"><span data-stu-id="3e44e-188">The following example calculates the average quantity ordered for each product:</span></span>

```sql
select p, avg(ol.Quantity) from LOB.OrderLines as ol
  group by ol.Product as p
```

<span data-ttu-id="3e44e-189">Możliwe jest posiadanie agregacji opartej na grupach bez jawnej klauzuli Group by w wyrażeniu SELECT.</span><span class="sxs-lookup"><span data-stu-id="3e44e-189">It's possible to have a group-based aggregate without an explicit group-by clause in the SELECT expression.</span></span> <span data-ttu-id="3e44e-190">W takim przypadku wszystkie elementy są traktowane jako pojedyncze grupy.</span><span class="sxs-lookup"><span data-stu-id="3e44e-190">In this case, all elements are treated as a single group.</span></span> <span data-ttu-id="3e44e-191">Jest to równoważne określeniu grupowania na podstawie stałej.</span><span class="sxs-lookup"><span data-stu-id="3e44e-191">This is equivalent of specifying a grouping based on a constant.</span></span> <span data-ttu-id="3e44e-192">Zrób to na przykład następujące wyrażenie:</span><span class="sxs-lookup"><span data-stu-id="3e44e-192">Take, for example, the following expression:</span></span>

```sql
select avg(ol.Quantity) from LOB.OrderLines as ol
```

<span data-ttu-id="3e44e-193">Jest to równoważne z następującymi:</span><span class="sxs-lookup"><span data-stu-id="3e44e-193">This is equivalent to the following:</span></span>

```sql
select avg(ol.Quantity) from LOB.OrderLines as ol group by 1
```

<span data-ttu-id="3e44e-194">Wyrażenia wewnątrz agregacji opartej na grupach są oceniane w zakresie rozpoznawania nazw, który byłby widoczny dla wyrażenia klauzuli WHERE.</span><span class="sxs-lookup"><span data-stu-id="3e44e-194">Expressions inside the group-based aggregate are evaluated within the name-resolution scope that would be visible to the WHERE clause expression.</span></span>

<span data-ttu-id="3e44e-195">Podobnie jak w języku Transact-SQL, agregacje oparte na grupach mogą również określać Modyfikatory ALL lub DISTINCT.</span><span class="sxs-lookup"><span data-stu-id="3e44e-195">As in Transact-SQL, group-based aggregates can also specify an ALL or DISTINCT modifier.</span></span> <span data-ttu-id="3e44e-196">Jeśli określono modyfikator DISTINCT, duplikaty są eliminowane z kolekcji agregacji danych wejściowych przed obliczaniem agregacji.</span><span class="sxs-lookup"><span data-stu-id="3e44e-196">If the DISTINCT modifier is specified, duplicates are eliminated from the aggregate input collection, before the aggregate is computed.</span></span> <span data-ttu-id="3e44e-197">Jeśli modyfikator ALL jest określony (lub jeśli nie określono modyfikatora), nie jest wykonywane żadne duplikowanie eliminacji.</span><span class="sxs-lookup"><span data-stu-id="3e44e-197">If the ALL modifier is specified (or if no modifier is specified), no duplicate elimination is performed.</span></span>

## <a name="see-also"></a><span data-ttu-id="3e44e-198">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3e44e-198">See also</span></span>

- [<span data-ttu-id="3e44e-199">Funkcje Canonical</span><span class="sxs-lookup"><span data-stu-id="3e44e-199">Canonical Functions</span></span>](canonical-functions.md)
