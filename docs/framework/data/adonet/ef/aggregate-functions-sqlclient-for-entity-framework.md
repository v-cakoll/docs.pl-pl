---
title: Funkcje agregujące (SqlClient programu Entity Framework)
ms.date: 03/30/2017
ms.assetid: 03303f01-b591-4efc-9875-f9c608edff0b
ms.openlocfilehash: f2f2b557cd9f126ddd513a0f42d3ac95114c3822
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61606783"
---
# <a name="aggregate-functions-sqlclient-for-entity-framework"></a><span data-ttu-id="fa32f-102">Funkcje agregujące (SqlClient programu Entity Framework)</span><span class="sxs-lookup"><span data-stu-id="fa32f-102">Aggregate Functions (SqlClient for Entity Framework)</span></span>
<span data-ttu-id="fa32f-103">.NET Framework Data Provider for SQL Server (SqlClient) zapewnia funkcje agregujące.</span><span class="sxs-lookup"><span data-stu-id="fa32f-103">The .NET Framework Data Provider for SQL Server (SqlClient) provides aggregate functions.</span></span> <span data-ttu-id="fa32f-104">Funkcje agregujące wykonywanie obliczeń na zestaw wartości wejściowych i zwracają wartość.</span><span class="sxs-lookup"><span data-stu-id="fa32f-104">Aggregate functions perform calculations on a set of input values and return a value.</span></span> <span data-ttu-id="fa32f-105">Te funkcje są w przestrzeni nazw SqlServer, który jest dostępny, gdy używasz SqlClient.</span><span class="sxs-lookup"><span data-stu-id="fa32f-105">These functions are in the SqlServer namespace, which is available when you use SqlClient.</span></span> <span data-ttu-id="fa32f-106">Właściwość przestrzeni nazw dostawcy umożliwia programu Entity Framework dowiedzieć się, który prefiks jest używany przez tego dostawcę dla określonego konstrukcji, takich jak typy i funkcje.</span><span class="sxs-lookup"><span data-stu-id="fa32f-106">A provider's namespace property allows the Entity Framework to discover which prefix is used by this provider for specific constructs, such as types and functions.</span></span>  
  
 <span data-ttu-id="fa32f-107">Dostępne są następujące funkcje agregujące SqlClient.</span><span class="sxs-lookup"><span data-stu-id="fa32f-107">The following are the SqlClient aggregate functions.</span></span>  

## <a name="avgexpression"></a><span data-ttu-id="fa32f-108">AVG(Expression)</span><span class="sxs-lookup"><span data-stu-id="fa32f-108">AVG(expression)</span></span>

<span data-ttu-id="fa32f-109">Zwraca średnią z wartości w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="fa32f-109">Returns the average of the values in a collection.</span></span> <span data-ttu-id="fa32f-110">Wartości null są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="fa32f-110">Null values are ignored.</span></span>

<span data-ttu-id="fa32f-111">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="fa32f-111">**Arguments**</span></span>

<span data-ttu-id="fa32f-112">`Int32`, `Int64`, `Double`, I `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="fa32f-112">An `Int32`, `Int64`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="fa32f-113">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="fa32f-113">**Return Value**</span></span>

<span data-ttu-id="fa32f-114">Typ `expression`.</span><span class="sxs-lookup"><span data-stu-id="fa32f-114">The type of `expression`.</span></span>

<span data-ttu-id="fa32f-115">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="fa32f-115">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_AVG](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_avg)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_AVG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_avg)]

## <a name="checksumaggcollection"></a><span data-ttu-id="fa32f-116">CHECKSUM_AGG(Collection)</span><span class="sxs-lookup"><span data-stu-id="fa32f-116">CHECKSUM_AGG(collection)</span></span>
 
 <span data-ttu-id="fa32f-117">Zwraca sumę kontrolną wartości w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="fa32f-117">Returns the checksum of the values in a collection.</span></span> <span data-ttu-id="fa32f-118">Wartości null są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="fa32f-118">Null values are ignored.</span></span>
 
 <span data-ttu-id="fa32f-119">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="fa32f-119">**Arguments**</span></span>
 
 <span data-ttu-id="fa32f-120">Kolekcja (`Int32`).</span><span class="sxs-lookup"><span data-stu-id="fa32f-120">A Collection(`Int32`).</span></span>
 
 <span data-ttu-id="fa32f-121">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="fa32f-121">**Return Value**</span></span>
 
 <span data-ttu-id="fa32f-122">`Int32`.</span><span class="sxs-lookup"><span data-stu-id="fa32f-122">An `Int32`.</span></span>
 
 <span data-ttu-id="fa32f-123">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="fa32f-123">**Example**</span></span>
 
 [!code-csharp[DP EntityServices Concepts#SQLSERVER_CHECKSUM](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_checksum)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_CHECKSUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_checksum)]
   
## <a name="countexpression"></a><span data-ttu-id="fa32f-124">Count(Expression)</span><span class="sxs-lookup"><span data-stu-id="fa32f-124">COUNT(expression)</span></span>

<span data-ttu-id="fa32f-125">Zwraca liczbę elementów w kolekcji jako `Int32`.</span><span class="sxs-lookup"><span data-stu-id="fa32f-125">Returns the number of items in a collection as an `Int32`.</span></span>

<span data-ttu-id="fa32f-126">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="fa32f-126">**Arguments**</span></span>

<span data-ttu-id="fa32f-127">Kolekcja\<T >, gdzie T jest jednym z następujących typów:</span><span class="sxs-lookup"><span data-stu-id="fa32f-127">A Collection\<T>, where T is one of the following types:</span></span>

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|<span data-ttu-id="fa32f-128">`Guid` (nie jest zwracana w programie SQL Server 2000)</span><span class="sxs-lookup"><span data-stu-id="fa32f-128">`Guid` (not returned in SQL Server 2000)</span></span>|

<span data-ttu-id="fa32f-129">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="fa32f-129">**Return Value**</span></span>

<span data-ttu-id="fa32f-130">`Int32`.</span><span class="sxs-lookup"><span data-stu-id="fa32f-130">An `Int32`.</span></span>

<span data-ttu-id="fa32f-131">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="fa32f-131">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_COUNT](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_count)]
<span data-ttu-id="fa32f-132">[! code-sql[SQLSERVER_COUNT # pojęcia EntityServices punktu dystrybucji](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_count)</span><span class="sxs-lookup"><span data-stu-id="fa32f-132">[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_count)</span></span>
 
## <a name="countbigexpression"></a><span data-ttu-id="fa32f-133">COUNT_BIG(Expression)</span><span class="sxs-lookup"><span data-stu-id="fa32f-133">COUNT_BIG(expression)</span></span>
 
 <span data-ttu-id="fa32f-134">Zwraca liczbę elementów w kolekcji jako `bigint`.</span><span class="sxs-lookup"><span data-stu-id="fa32f-134">Returns the number of items in a collection as a `bigint`.</span></span>
 
 <span data-ttu-id="fa32f-135">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="fa32f-135">**Arguments**</span></span>
 
 <span data-ttu-id="fa32f-136">Collection(T), gdzie T jest jednym z następujących typów:</span><span class="sxs-lookup"><span data-stu-id="fa32f-136">A Collection(T), where T is one of the following types:</span></span>
 
 |   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|<span data-ttu-id="fa32f-137">`Guid` (nie jest zwracana w programie SQL Server 2000)</span><span class="sxs-lookup"><span data-stu-id="fa32f-137">`Guid` (not returned in SQL Server 2000)</span></span>|

<span data-ttu-id="fa32f-138">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="fa32f-138">**Return Value**</span></span>

<span data-ttu-id="fa32f-139">`Int64`.</span><span class="sxs-lookup"><span data-stu-id="fa32f-139">An `Int64`.</span></span>

<span data-ttu-id="fa32f-140">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="fa32f-140">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_COUNTBIG](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_countbig)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNTBIG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_countbig)]

## <a name="maxexpression"></a><span data-ttu-id="fa32f-141">MAX(Expression)</span><span class="sxs-lookup"><span data-stu-id="fa32f-141">MAX(expression)</span></span>

<span data-ttu-id="fa32f-142">Zwraca maksymalną wartość w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="fa32f-142">Returns the maximum value the collection.</span></span>

<span data-ttu-id="fa32f-143">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="fa32f-143">**Arguments**</span></span>

<span data-ttu-id="fa32f-144">Collection(T), gdzie T jest jednym z następujących typów:</span><span class="sxs-lookup"><span data-stu-id="fa32f-144">A Collection(T), where T is one of the following types:</span></span> 

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

<span data-ttu-id="fa32f-145">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="fa32f-145">**Return Value**</span></span>

<span data-ttu-id="fa32f-146">Typ `expression`.</span><span class="sxs-lookup"><span data-stu-id="fa32f-146">The type of `expression`.</span></span>

<span data-ttu-id="fa32f-147">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="fa32f-147">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_MAX](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_max)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_MAX](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_max)]

## <a name="minexpression"></a><span data-ttu-id="fa32f-148">MIN(Expression)</span><span class="sxs-lookup"><span data-stu-id="fa32f-148">MIN(expression)</span></span>

<span data-ttu-id="fa32f-149">Zwraca minimalną wartość w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="fa32f-149">Returns the minimum value in a collection.</span></span>

<span data-ttu-id="fa32f-150">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="fa32f-150">**Arguments**</span></span>

<span data-ttu-id="fa32f-151">Collection(T), gdzie T jest jednym z następujących typów:</span><span class="sxs-lookup"><span data-stu-id="fa32f-151">A Collection(T), where T is one of the following types:</span></span> 

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

<span data-ttu-id="fa32f-152">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="fa32f-152">**Return Value**</span></span>

<span data-ttu-id="fa32f-153">Typ `expression`.</span><span class="sxs-lookup"><span data-stu-id="fa32f-153">The type of `expression`.</span></span>

<span data-ttu-id="fa32f-154">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="fa32f-154">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_MIN](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_min)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_MIN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_min)]

## <a name="stdevexpression"></a><span data-ttu-id="fa32f-155">StDev(Expression)</span><span class="sxs-lookup"><span data-stu-id="fa32f-155">STDEV(expression)</span></span>

<span data-ttu-id="fa32f-156">Zwraca statystyczne odchylenie standardowe wszystkich wartości określonego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="fa32f-156">Returns the statistical standard deviation of all values in the specified expression.</span></span>

<span data-ttu-id="fa32f-157">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="fa32f-157">**Arguments**</span></span>

<span data-ttu-id="fa32f-158">Kolekcja (`Double`).</span><span class="sxs-lookup"><span data-stu-id="fa32f-158">A Collection(`Double`).</span></span>

<span data-ttu-id="fa32f-159">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="fa32f-159">**Return Value**</span></span>

<span data-ttu-id="fa32f-160">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="fa32f-160">A `Double`.</span></span>

<span data-ttu-id="fa32f-161">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="fa32f-161">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_STDEV](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_stdev)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEV](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdev)]

## <a name="stdevpexpression"></a><span data-ttu-id="fa32f-162">STDEVP(Expression)</span><span class="sxs-lookup"><span data-stu-id="fa32f-162">STDEVP(expression)</span></span>

<span data-ttu-id="fa32f-163">Zwraca statystyczne odchylenie standardowe populacji dla wszystkich wartości określonego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="fa32f-163">Returns the statistical standard deviation for the population for all values in the specified expression.</span></span>

<span data-ttu-id="fa32f-164">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="fa32f-164">**Arguments**</span></span>

<span data-ttu-id="fa32f-165">Kolekcja (`Double`).</span><span class="sxs-lookup"><span data-stu-id="fa32f-165">A Collection(`Double`).</span></span>

<span data-ttu-id="fa32f-166">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="fa32f-166">**Return Value**</span></span>

<span data-ttu-id="fa32f-167">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="fa32f-167">A `Double`.</span></span>

<span data-ttu-id="fa32f-168">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="fa32f-168">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_STDEVP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_stdevp)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEVP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdevp)]

## <a name="sumexpression"></a><span data-ttu-id="fa32f-169">SUM(Expression)</span><span class="sxs-lookup"><span data-stu-id="fa32f-169">SUM(expression)</span></span>

<span data-ttu-id="fa32f-170">Zwraca sumę wszystkich wartości w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="fa32f-170">Returns the sum of all the values in the collection.</span></span>

<span data-ttu-id="fa32f-171">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="fa32f-171">**Arguments**</span></span>

<span data-ttu-id="fa32f-172">Collection(T), gdzie T jest jednym z następujących typów: `Int32`, `Int64`, `Double`, `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="fa32f-172">A Collection(T) where T is one of the following types: `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="fa32f-173">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="fa32f-173">**Return Value**</span></span>

<span data-ttu-id="fa32f-174">Typ `expression`.</span><span class="sxs-lookup"><span data-stu-id="fa32f-174">The type of `expression`.</span></span>

<span data-ttu-id="fa32f-175">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="fa32f-175">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_SUM](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_sum)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_SUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_sum)]

## <a name="varexpression"></a><span data-ttu-id="fa32f-176">VAR(Expression)</span><span class="sxs-lookup"><span data-stu-id="fa32f-176">VAR(expression)</span></span>

<span data-ttu-id="fa32f-177">Zwraca statystyczną wariancję wszystkich wartości określonego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="fa32f-177">Returns the statistical variance of all values in the specified expression.</span></span>

<span data-ttu-id="fa32f-178">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="fa32f-178">**Arguments**</span></span>

<span data-ttu-id="fa32f-179">Kolekcja (`Double`).</span><span class="sxs-lookup"><span data-stu-id="fa32f-179">A Collection(`Double`).</span></span>

<span data-ttu-id="fa32f-180">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="fa32f-180">**Return Value**</span></span>

<span data-ttu-id="fa32f-181">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="fa32f-181">A `Double`.</span></span>

<span data-ttu-id="fa32f-182">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="fa32f-182">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_VAR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_var)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_VAR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_var)]

## <a name="varpexpression"></a><span data-ttu-id="fa32f-183">VARP(Expression)</span><span class="sxs-lookup"><span data-stu-id="fa32f-183">VARP(expression)</span></span>

<span data-ttu-id="fa32f-184">Zwraca statystyczne wariancję populacji dla wszystkich wartości podanego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="fa32f-184">Returns the statistical variance for the population for all values in the specified expression.</span></span>

<span data-ttu-id="fa32f-185">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="fa32f-185">**Arguments**</span></span>

<span data-ttu-id="fa32f-186">Kolekcja (`Double`).</span><span class="sxs-lookup"><span data-stu-id="fa32f-186">A Collection(`Double`).</span></span>

<span data-ttu-id="fa32f-187">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="fa32f-187">**Return Value**</span></span>

<span data-ttu-id="fa32f-188">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="fa32f-188">A `Double`.</span></span>

<span data-ttu-id="fa32f-189">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="fa32f-189">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_VARP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_varp)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_VARP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_varp)] 
  
## <a name="see-also"></a><span data-ttu-id="fa32f-190">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fa32f-190">See also</span></span>

<span data-ttu-id="fa32f-191">Aby uzyskać więcej informacji na temat funkcji agregujących, które obsługuje klient SQL zobacz dokumentację dla używanej wersji programu SQL Server określonego w manifeście dostawcy SqlClient:</span><span class="sxs-lookup"><span data-stu-id="fa32f-191">For more information about the aggregate functions that SqlClient supports, see the documentation for the SQL Server version that you specified in the SqlClient provider manifest:</span></span>

- <span data-ttu-id="fa32f-192">**SQL Server 2005:** [Aggregate Functions (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms173454(v=sql.90))</span><span class="sxs-lookup"><span data-stu-id="fa32f-192">**SQL Server 2005:** [Aggregate Functions (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms173454(v=sql.90))</span></span>
- <span data-ttu-id="fa32f-193">**Program SQL Server 2008 lub nowszy:** [Aggregate Functions (Transact-SQL)](/sql/t-sql/functions/aggregate-functions-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="fa32f-193">**SQL Server 2008 and later:** [Aggregate Functions (Transact-SQL)](/sql/t-sql/functions/aggregate-functions-transact-sql)</span></span>

- [<span data-ttu-id="fa32f-194">Jednostki języka SQL</span><span class="sxs-lookup"><span data-stu-id="fa32f-194">Entity SQL Language</span></span>](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)
- [<span data-ttu-id="fa32f-195">Funkcje agregujące Canonical</span><span class="sxs-lookup"><span data-stu-id="fa32f-195">Aggregate Canonical Functions</span></span>](../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)
