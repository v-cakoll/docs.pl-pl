---
title: Funkcje agregujące Canonical
ms.date: 03/30/2017
ms.assetid: 3bcff826-ca90-41b3-a791-04d6ff0e5085
ms.openlocfilehash: f5d3584c6e9d35c9eb69b4f54cad45187416ee59
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57372805"
---
# <a name="aggregate-canonical-functions"></a><span data-ttu-id="4779c-102">Funkcje agregujące Canonical</span><span class="sxs-lookup"><span data-stu-id="4779c-102">Aggregate Canonical Functions</span></span>

<span data-ttu-id="4779c-103">Agregacje są wyrażeniami, które zmniejszenie szereg wartości wejściowych do, na przykład pojedynczej wartości.</span><span class="sxs-lookup"><span data-stu-id="4779c-103">Aggregates are expressions that reduce a series of input values into, for example, a single value.</span></span> <span data-ttu-id="4779c-104">Agregacje są zwykle używane w połączeniu z klauzulą GROUP BY Wybierz wyrażenie, a istnieją ograniczenia, na którym mogą być używane.</span><span class="sxs-lookup"><span data-stu-id="4779c-104">Aggregates are normally used in conjunction with the GROUP BY clause of the SELECT expression, and there are constraints on where they can be used.</span></span>

## <a name="aggregate-entity-sql-canonical-functions"></a><span data-ttu-id="4779c-105">Funkcje agregujące canonical jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="4779c-105">Aggregate Entity SQL canonical functions</span></span>

<span data-ttu-id="4779c-106">Dostępne są następujące funkcje agregujące canonical jednostki SQL.</span><span class="sxs-lookup"><span data-stu-id="4779c-106">The following are the aggregate Entity SQL canonical functions.</span></span>

### <a name="avgexpression"></a><span data-ttu-id="4779c-107">AVG(Expression)</span><span class="sxs-lookup"><span data-stu-id="4779c-107">Avg(expression)</span></span>

<span data-ttu-id="4779c-108">Zwraca średnią wartości innych niż null.</span><span class="sxs-lookup"><span data-stu-id="4779c-108">Returns the average of the non-null values.</span></span>

<span data-ttu-id="4779c-109">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="4779c-109">**Arguments**</span></span>

<span data-ttu-id="4779c-110">`Int32`, `Int64`, `Double`, I `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="4779c-110">An `Int32`, `Int64`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="4779c-111">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="4779c-111">**Return Value**</span></span>

<span data-ttu-id="4779c-112">Typ `expression`, lub `null` Jeśli wszystkie wartości wejściowe są `null` wartości.</span><span class="sxs-lookup"><span data-stu-id="4779c-112">The type of `expression`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="4779c-113">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="4779c-113">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_AVG](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_avg)]
[!code-sql[DP EntityServices Concepts#EDM_AVG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_avg)]

### <a name="bigcountexpression"></a><span data-ttu-id="4779c-114">BigCount(expression)</span><span class="sxs-lookup"><span data-stu-id="4779c-114">BigCount(expression)</span></span>

<span data-ttu-id="4779c-115">Zwraca rozmiar agregacji, łącznie z wartościami null i zduplikowane.</span><span class="sxs-lookup"><span data-stu-id="4779c-115">Returns the size of the aggregate including null and duplicate values.</span></span>

<span data-ttu-id="4779c-116">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="4779c-116">**Arguments**</span></span>

<span data-ttu-id="4779c-117">Dowolnego typu.</span><span class="sxs-lookup"><span data-stu-id="4779c-117">Any type.</span></span>

<span data-ttu-id="4779c-118">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="4779c-118">**Return Value**</span></span>

<span data-ttu-id="4779c-119">`Int64`.</span><span class="sxs-lookup"><span data-stu-id="4779c-119">An `Int64`.</span></span>

<span data-ttu-id="4779c-120">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="4779c-120">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_BIGCOUNT](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_bigcount)]
[!code-sql[DP EntityServices Concepts#EDM_BIGCOUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_bigcount)]

### <a name="countexpression"></a><span data-ttu-id="4779c-121">Count(Expression)</span><span class="sxs-lookup"><span data-stu-id="4779c-121">Count(expression)</span></span>

<span data-ttu-id="4779c-122">Zwraca rozmiar agregacji, łącznie z wartościami null i zduplikowane.</span><span class="sxs-lookup"><span data-stu-id="4779c-122">Returns the size of the aggregate including null and duplicate values.</span></span>

<span data-ttu-id="4779c-123">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="4779c-123">**Arguments**</span></span>

<span data-ttu-id="4779c-124">Dowolnego typu.</span><span class="sxs-lookup"><span data-stu-id="4779c-124">Any type.</span></span>

<span data-ttu-id="4779c-125">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="4779c-125">**Return Value**</span></span>

<span data-ttu-id="4779c-126">`Int32`.</span><span class="sxs-lookup"><span data-stu-id="4779c-126">An `Int32`.</span></span>

<span data-ttu-id="4779c-127">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="4779c-127">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_COUNT](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_count)]
[!code-sql[DP EntityServices Concepts#EDM_COUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_count)]

### <a name="maxexpression"></a><span data-ttu-id="4779c-128">MAX(Expression)</span><span class="sxs-lookup"><span data-stu-id="4779c-128">Max(expression)</span></span>

<span data-ttu-id="4779c-129">Zwraca maksymalną liczbę wartości innych niż null.</span><span class="sxs-lookup"><span data-stu-id="4779c-129">Returns the maximum of the non-null values.</span></span>

<span data-ttu-id="4779c-130">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="4779c-130">**Arguments**</span></span>

<span data-ttu-id="4779c-131">A `Byte`, `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, `Decimal`, `DateTime`, `DateTimeOffset`, `Time`, `String`, `Binary`.</span><span class="sxs-lookup"><span data-stu-id="4779c-131">A `Byte`, `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, `Decimal`, `DateTime`, `DateTimeOffset`, `Time`, `String`, `Binary`.</span></span>

<span data-ttu-id="4779c-132">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="4779c-132">**Return Value**</span></span>

<span data-ttu-id="4779c-133">Typ `expression`, lub `null` Jeśli wszystkie wartości wejściowe są `null` wartości.</span><span class="sxs-lookup"><span data-stu-id="4779c-133">The type of `expression`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="4779c-134">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="4779c-134">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_MAX](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_max)]
[!code-sql[DP EntityServices Concepts#EDM_MAX](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_max)]

### <a name="minexpression"></a><span data-ttu-id="4779c-135">Min(Expression)</span><span class="sxs-lookup"><span data-stu-id="4779c-135">Min(expression)</span></span>

<span data-ttu-id="4779c-136">Zwraca wartość minimalną wartość inną niż null.</span><span class="sxs-lookup"><span data-stu-id="4779c-136">Returns the minimum of the non-null values.</span></span>

<span data-ttu-id="4779c-137">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="4779c-137">**Arguments**</span></span>

<span data-ttu-id="4779c-138">A `Byte`, `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, `Decimal`, `DateTime`, `DateTimeOffset`, `Time`, `String`, `Binary`.</span><span class="sxs-lookup"><span data-stu-id="4779c-138">A `Byte`, `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, `Decimal`, `DateTime`, `DateTimeOffset`, `Time`, `String`, `Binary`.</span></span>

<span data-ttu-id="4779c-139">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="4779c-139">**Return Value**</span></span>

<span data-ttu-id="4779c-140">Typ `expression`, lub `null` Jeśli wszystkie wartości wejściowe są `null` wartości.</span><span class="sxs-lookup"><span data-stu-id="4779c-140">The type of `expression`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="4779c-141">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="4779c-141">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_MIN](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_min)]
[!code-sql[DP EntityServices Concepts#EDM_MIN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_min)]

### <a name="stdevexpression"></a><span data-ttu-id="4779c-142">StDev(expression)</span><span class="sxs-lookup"><span data-stu-id="4779c-142">StDev(expression)</span></span>

<span data-ttu-id="4779c-143">Zwraca odchylenie standardowe wartości innych niż null.</span><span class="sxs-lookup"><span data-stu-id="4779c-143">Returns the standard deviation of the non-null values.</span></span>

<span data-ttu-id="4779c-144">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="4779c-144">**Arguments**</span></span>

<span data-ttu-id="4779c-145">`Int32`, `Int64`, `Double`, `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="4779c-145">An `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="4779c-146">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="4779c-146">**Return Value**</span></span>

<span data-ttu-id="4779c-147">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="4779c-147">A `Double`.</span></span> <span data-ttu-id="4779c-148">`Null`, jeśli wszystkie wartości wejściowe są `null` wartości.</span><span class="sxs-lookup"><span data-stu-id="4779c-148">`Null`, if all input values are `null` values.</span></span>

<span data-ttu-id="4779c-149">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="4779c-149">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_STDEV](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_stdev)]
[!code-sql[DP EntityServices Concepts#EDM_STDEV](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_stdev)]

### <a name="stdevpexpression"></a><span data-ttu-id="4779c-150">StDevP(expression)</span><span class="sxs-lookup"><span data-stu-id="4779c-150">StDevP(expression)</span></span>

<span data-ttu-id="4779c-151">Zwraca odchylenie standardowe populacji dla wszystkich wartości.</span><span class="sxs-lookup"><span data-stu-id="4779c-151">Returns the standard deviation for the population of all values.</span></span>

<span data-ttu-id="4779c-152">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="4779c-152">**Arguments**</span></span>

<span data-ttu-id="4779c-153">`Int32`, `Int64`, `Double`, `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="4779c-153">An `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="4779c-154">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="4779c-154">**Return Value**</span></span>

<span data-ttu-id="4779c-155">A `Double`, lub `null` Jeśli wszystkie wartości wejściowe są `null` wartości.</span><span class="sxs-lookup"><span data-stu-id="4779c-155">A `Double`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="4779c-156">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="4779c-156">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_STDEVP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_stdevp)]
[!code-sql[DP EntityServices Concepts#EDM_STDEVP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_stdevp)]

### <a name="sumexpression"></a><span data-ttu-id="4779c-157">Sum(Expression)</span><span class="sxs-lookup"><span data-stu-id="4779c-157">Sum(expression)</span></span>

<span data-ttu-id="4779c-158">Zwraca sumę wartości innych niż null.</span><span class="sxs-lookup"><span data-stu-id="4779c-158">Returns the sum of the non-null values.</span></span>

<span data-ttu-id="4779c-159">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="4779c-159">**Arguments**</span></span>

<span data-ttu-id="4779c-160">`Int32`, `Int64`, `Double`, `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="4779c-160">An `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="4779c-161">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="4779c-161">**Return Value**</span></span>

<span data-ttu-id="4779c-162">A `Double`, lub `null` Jeśli wszystkie wartości wejściowe są `null` wartości.</span><span class="sxs-lookup"><span data-stu-id="4779c-162">A `Double`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="4779c-163">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="4779c-163">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_SUM](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_sum)]
[!code-sql[DP EntityServices Concepts#EDM_SUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_sum)]

### <a name="varexpression"></a><span data-ttu-id="4779c-164">Var(Expression)</span><span class="sxs-lookup"><span data-stu-id="4779c-164">Var(expression)</span></span>

<span data-ttu-id="4779c-165">Zwraca wariancję wszystkich wartości innych niż null.</span><span class="sxs-lookup"><span data-stu-id="4779c-165">Returns the variance of all non-null values.</span></span>

<span data-ttu-id="4779c-166">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="4779c-166">**Arguments**</span></span>

<span data-ttu-id="4779c-167">`Int32`, `Int64`, `Double`, `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="4779c-167">An `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="4779c-168">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="4779c-168">**Return Value**</span></span>

<span data-ttu-id="4779c-169">A `Double`, lub `null` Jeśli wszystkie wartości wejściowe są `null` wartości.</span><span class="sxs-lookup"><span data-stu-id="4779c-169">A `Double`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="4779c-170">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="4779c-170">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_VAR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_var)]
[!code-sql[DP EntityServices Concepts#EDM_VAR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_var)]

### <a name="varpexpression"></a><span data-ttu-id="4779c-171">VarP(expression)</span><span class="sxs-lookup"><span data-stu-id="4779c-171">VarP(expression)</span></span>

<span data-ttu-id="4779c-172">Zwraca wariancję populacji dla wszystkich wartości innych niż null.</span><span class="sxs-lookup"><span data-stu-id="4779c-172">Returns the variance for the population of all non-null values.</span></span>

<span data-ttu-id="4779c-173">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="4779c-173">**Arguments**</span></span>

<span data-ttu-id="4779c-174">`Int32`, `Int64`, `Double`, `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="4779c-174">An `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="4779c-175">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="4779c-175">**Return Value**</span></span>

<span data-ttu-id="4779c-176">A `Double`, lub `null` Jeśli wszystkie wartości wejściowe są `null` wartości.</span><span class="sxs-lookup"><span data-stu-id="4779c-176">A `Double`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="4779c-177">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="4779c-177">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_VARP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_varp)]
[!code-sql[DP EntityServices Concepts#EDM_VARP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_varp)]

<span data-ttu-id="4779c-178">Równoważne funkcje są dostępne w Microsoft SQL klienta zarządzanego dostawcy.</span><span class="sxs-lookup"><span data-stu-id="4779c-178">Equivalent functionality is available in the Microsoft SQL Client Managed Provider.</span></span> <span data-ttu-id="4779c-179">Aby uzyskać więcej informacji, zobacz [Klient SQL dla funkcji programu Entity Framework](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span><span class="sxs-lookup"><span data-stu-id="4779c-179">For more information, see [SqlClient for Entity Framework Functions](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span></span>

## <a name="collection-based-aggregates"></a><span data-ttu-id="4779c-180">Wartości zagregowane z kolekcji</span><span class="sxs-lookup"><span data-stu-id="4779c-180">Collection-based aggregates</span></span>

<span data-ttu-id="4779c-181">Opartego na kolekcji wartości zagregowanych (kolekcji funkcji) działają na kolekcji i zwracają wartość.</span><span class="sxs-lookup"><span data-stu-id="4779c-181">Collection-based aggregates (collection functions) operate on collections and return a value.</span></span> <span data-ttu-id="4779c-182">Na przykład jeśli zamówienia to zbiór wszystkich zamówień, można obliczyć Najwcześniejsza data wysyłki za pomocą następującego wyrażenia:</span><span class="sxs-lookup"><span data-stu-id="4779c-182">For example if ORDERS is a collection of all orders, you can calculate the earliest ship date with the following expression:</span></span>

```sql
min(select value o.ShipDate from LOB.Orders as o)
```

<span data-ttu-id="4779c-183">Wyrażenia wewnątrz opartego na kolekcji wartości zagregowane są obliczane w bieżącym zakresie rozpoznawania nazw otoczenia.</span><span class="sxs-lookup"><span data-stu-id="4779c-183">Expressions inside collection-based aggregates are evaluated within the current ambient name-resolution scope.</span></span>

## <a name="group-based-aggregates"></a><span data-ttu-id="4779c-184">Agregacje oparte na grupach</span><span class="sxs-lookup"><span data-stu-id="4779c-184">Group-based aggregates</span></span>

<span data-ttu-id="4779c-185">Oparte na grupach agregacje są obliczane przez grupę, zgodnie z definicją w klauzuli GROUP BY.</span><span class="sxs-lookup"><span data-stu-id="4779c-185">Group-based aggregates are calculated over a group as defined by the GROUP BY clause.</span></span> <span data-ttu-id="4779c-186">Dla każdej grupy w wyniku oddzielne agregacji jest obliczana przy użyciu elementów w każdej grupie jako dane wejściowe do obliczania agregacji.</span><span class="sxs-lookup"><span data-stu-id="4779c-186">For each group in the result, a separate aggregate is calculated by using the elements in each group as input to the aggregate calculation.</span></span> <span data-ttu-id="4779c-187">Użycie klauzuli group by w wyrażeniu wybierz tylko grupowanie nazwy wyrażeń, agregacje lub wyrażenia stałe mogą być obecne w projekcji lub klauzuli order by.</span><span class="sxs-lookup"><span data-stu-id="4779c-187">When a group-by clause is used in a select expression, only grouping expression names, aggregates, or constant expressions can be present in the projection or order-by clause.</span></span>

<span data-ttu-id="4779c-188">W poniższym przykładzie oblicza średnią ilość uporządkowane dla każdego produktu:</span><span class="sxs-lookup"><span data-stu-id="4779c-188">The following example calculates the average quantity ordered for each product:</span></span>

```sql
select p, avg(ol.Quantity) from LOB.OrderLines as ol
  group by ol.Product as p
```

<span data-ttu-id="4779c-189">Istnieje możliwość mają oparte na grupach agregacji bez jawnego-klauzuli group by w wyrażeniu SELECT.</span><span class="sxs-lookup"><span data-stu-id="4779c-189">It's possible to have a group-based aggregate without an explicit group-by clause in the SELECT expression.</span></span> <span data-ttu-id="4779c-190">W takim przypadku wszystkie elementy są traktowane jako pojedynczej grupy.</span><span class="sxs-lookup"><span data-stu-id="4779c-190">In this case, all elements are treated as a single group.</span></span> <span data-ttu-id="4779c-191">Jest to równoważne określania grupowanie oparte na stałą.</span><span class="sxs-lookup"><span data-stu-id="4779c-191">This is equivalent of specifying a grouping based on a constant.</span></span> <span data-ttu-id="4779c-192">Weźmy na przykład, następujące wyrażenie:</span><span class="sxs-lookup"><span data-stu-id="4779c-192">Take, for example, the following expression:</span></span>

```sql
select avg(ol.Quantity) from LOB.OrderLines as ol
```

<span data-ttu-id="4779c-193">To jest odpowiednikiem następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="4779c-193">This is equivalent to the following:</span></span>

```sql
select avg(ol.Quantity) from LOB.OrderLines as ol group by 1
```

<span data-ttu-id="4779c-194">Wyrażenia wewnątrz agregacji oparte na grupach są obliczane w zakresie rozpoznawania nazw, które będą widoczne dla wyrażenie klauzuli WHERE.</span><span class="sxs-lookup"><span data-stu-id="4779c-194">Expressions inside the group-based aggregate are evaluated within the name-resolution scope that would be visible to the WHERE clause expression.</span></span>

<span data-ttu-id="4779c-195">Podobnie jak w [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], oparte na grupach agregacji można również określić wszystkie lub modyfikator DISTINCT.</span><span class="sxs-lookup"><span data-stu-id="4779c-195">As in [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], group-based aggregates can also specify an ALL or DISTINCT modifier.</span></span> <span data-ttu-id="4779c-196">Jeśli modyfikator DISTINCT jest określony, duplikaty są eliminowane z agregacji kolekcja wejściowa przed agregacji jest kolumną obliczaną.</span><span class="sxs-lookup"><span data-stu-id="4779c-196">If the DISTINCT modifier is specified, duplicates are eliminated from the aggregate input collection, before the aggregate is computed.</span></span> <span data-ttu-id="4779c-197">Jeśli określono wszystkie modyfikator (lub jeśli określono nie modyfikator), jest wykonywane nie wyeliminowania zduplikowanych.</span><span class="sxs-lookup"><span data-stu-id="4779c-197">If the ALL modifier is specified (or if no modifier is specified), no duplicate elimination is performed.</span></span>

## <a name="see-also"></a><span data-ttu-id="4779c-198">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4779c-198">See also</span></span>

- [<span data-ttu-id="4779c-199">Funkcje Canonical</span><span class="sxs-lookup"><span data-stu-id="4779c-199">Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
