---
title: Funkcje agregujące (SqlClient dla Entity Framework)
ms.date: 03/30/2017
ms.assetid: 03303f01-b591-4efc-9875-f9c608edff0b
ms.openlocfilehash: cf476192cf049f230c1956e390d215ad4abaa821
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251705"
---
# <a name="aggregate-functions-sqlclient-for-entity-framework"></a><span data-ttu-id="74f9c-102">Funkcje agregujące (SqlClient dla Entity Framework)</span><span class="sxs-lookup"><span data-stu-id="74f9c-102">Aggregate Functions (SqlClient for Entity Framework)</span></span>
<span data-ttu-id="74f9c-103">Dostawca danych .NET Framework dla SQL Server (SqlClient) udostępnia funkcje agregujące.</span><span class="sxs-lookup"><span data-stu-id="74f9c-103">The .NET Framework Data Provider for SQL Server (SqlClient) provides aggregate functions.</span></span> <span data-ttu-id="74f9c-104">Funkcje agregujące wykonują obliczenia na zestawie wartości wejściowych i zwracają wartość.</span><span class="sxs-lookup"><span data-stu-id="74f9c-104">Aggregate functions perform calculations on a set of input values and return a value.</span></span> <span data-ttu-id="74f9c-105">Te funkcje znajdują się w przestrzeni nazw SqlServer, która jest dostępna w przypadku korzystania z programu SqlClient.</span><span class="sxs-lookup"><span data-stu-id="74f9c-105">These functions are in the SqlServer namespace, which is available when you use SqlClient.</span></span> <span data-ttu-id="74f9c-106">Właściwość przestrzeni nazw dostawcy umożliwia Entity Framework odnajdywania prefiksu używanego przez tego dostawcę dla określonych konstrukcji, takich jak typy i funkcje.</span><span class="sxs-lookup"><span data-stu-id="74f9c-106">A provider's namespace property allows the Entity Framework to discover which prefix is used by this provider for specific constructs, such as types and functions.</span></span>  
  
 <span data-ttu-id="74f9c-107">Poniżej przedstawiono funkcje agregujące SqlClient.</span><span class="sxs-lookup"><span data-stu-id="74f9c-107">The following are the SqlClient aggregate functions.</span></span>  

## <a name="avgexpression"></a><span data-ttu-id="74f9c-108">Średnia (wyrażenie)</span><span class="sxs-lookup"><span data-stu-id="74f9c-108">AVG(expression)</span></span>

<span data-ttu-id="74f9c-109">Zwraca średnią wartości w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="74f9c-109">Returns the average of the values in a collection.</span></span> <span data-ttu-id="74f9c-110">Wartości null są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="74f9c-110">Null values are ignored.</span></span>

<span data-ttu-id="74f9c-111">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="74f9c-111">**Arguments**</span></span>

<span data-ttu-id="74f9c-112">`Int32`, ,,`Double`I .`Decimal` `Int64`</span><span class="sxs-lookup"><span data-stu-id="74f9c-112">An `Int32`, `Int64`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="74f9c-113">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="74f9c-113">**Return Value**</span></span>

<span data-ttu-id="74f9c-114">Typ `expression`.</span><span class="sxs-lookup"><span data-stu-id="74f9c-114">The type of `expression`.</span></span>

<span data-ttu-id="74f9c-115">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="74f9c-115">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_AVG](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_avg)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_AVG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_avg)]

## <a name="checksum_aggcollection"></a><span data-ttu-id="74f9c-116">CHECKSUM_AGG (kolekcja)</span><span class="sxs-lookup"><span data-stu-id="74f9c-116">CHECKSUM_AGG(collection)</span></span>
 
 <span data-ttu-id="74f9c-117">Zwraca sumę kontrolną wartości w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="74f9c-117">Returns the checksum of the values in a collection.</span></span> <span data-ttu-id="74f9c-118">Wartości null są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="74f9c-118">Null values are ignored.</span></span>
 
 <span data-ttu-id="74f9c-119">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="74f9c-119">**Arguments**</span></span>
 
 <span data-ttu-id="74f9c-120">Kolekcja (`Int32`).</span><span class="sxs-lookup"><span data-stu-id="74f9c-120">A Collection(`Int32`).</span></span>
 
 <span data-ttu-id="74f9c-121">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="74f9c-121">**Return Value**</span></span>
 
 <span data-ttu-id="74f9c-122">A `Int32`.</span><span class="sxs-lookup"><span data-stu-id="74f9c-122">An `Int32`.</span></span>
 
 <span data-ttu-id="74f9c-123">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="74f9c-123">**Example**</span></span>
 
 [!code-csharp[DP EntityServices Concepts#SQLSERVER_CHECKSUM](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_checksum)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_CHECKSUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_checksum)]
   
## <a name="countexpression"></a><span data-ttu-id="74f9c-124">COUNT (wyrażenie)</span><span class="sxs-lookup"><span data-stu-id="74f9c-124">COUNT(expression)</span></span>

<span data-ttu-id="74f9c-125">Zwraca liczbę elementów w kolekcji jako `Int32`.</span><span class="sxs-lookup"><span data-stu-id="74f9c-125">Returns the number of items in a collection as an `Int32`.</span></span>

<span data-ttu-id="74f9c-126">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="74f9c-126">**Arguments**</span></span>

<span data-ttu-id="74f9c-127">Kolekcja\<t >, gdzie t jest jednym z następujących typów:</span><span class="sxs-lookup"><span data-stu-id="74f9c-127">A Collection\<T>, where T is one of the following types:</span></span>

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|<span data-ttu-id="74f9c-128">`Guid`(niezwrócone w SQL Server 2000)</span><span class="sxs-lookup"><span data-stu-id="74f9c-128">`Guid` (not returned in SQL Server 2000)</span></span>|

<span data-ttu-id="74f9c-129">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="74f9c-129">**Return Value**</span></span>

<span data-ttu-id="74f9c-130">A `Int32`.</span><span class="sxs-lookup"><span data-stu-id="74f9c-130">An `Int32`.</span></span>

<span data-ttu-id="74f9c-131">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="74f9c-131">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_COUNT](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_count)]
<span data-ttu-id="74f9c-132">[! code-SQL[DP EntityServices koncepcje # SQLSERVER_COUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_count)</span><span class="sxs-lookup"><span data-stu-id="74f9c-132">[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_count)</span></span>
 
## <a name="count_bigexpression"></a><span data-ttu-id="74f9c-133">COUNT_BIG (wyrażenie)</span><span class="sxs-lookup"><span data-stu-id="74f9c-133">COUNT_BIG(expression)</span></span>
 
 <span data-ttu-id="74f9c-134">Zwraca liczbę elementów w kolekcji jako `bigint`.</span><span class="sxs-lookup"><span data-stu-id="74f9c-134">Returns the number of items in a collection as a `bigint`.</span></span>
 
 <span data-ttu-id="74f9c-135">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="74f9c-135">**Arguments**</span></span>
 
 <span data-ttu-id="74f9c-136">Kolekcja (T), gdzie T jest jednym z następujących typów:</span><span class="sxs-lookup"><span data-stu-id="74f9c-136">A Collection(T), where T is one of the following types:</span></span>
 
 |   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|<span data-ttu-id="74f9c-137">`Guid`(niezwrócone w SQL Server 2000)</span><span class="sxs-lookup"><span data-stu-id="74f9c-137">`Guid` (not returned in SQL Server 2000)</span></span>|

<span data-ttu-id="74f9c-138">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="74f9c-138">**Return Value**</span></span>

<span data-ttu-id="74f9c-139">A `Int64`.</span><span class="sxs-lookup"><span data-stu-id="74f9c-139">An `Int64`.</span></span>

<span data-ttu-id="74f9c-140">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="74f9c-140">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_COUNTBIG](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_countbig)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNTBIG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_countbig)]

## <a name="maxexpression"></a><span data-ttu-id="74f9c-141">MAX (wyrażenie)</span><span class="sxs-lookup"><span data-stu-id="74f9c-141">MAX(expression)</span></span>

<span data-ttu-id="74f9c-142">Zwraca maksymalną wartość kolekcji.</span><span class="sxs-lookup"><span data-stu-id="74f9c-142">Returns the maximum value the collection.</span></span>

<span data-ttu-id="74f9c-143">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="74f9c-143">**Arguments**</span></span>

<span data-ttu-id="74f9c-144">Kolekcja (T), gdzie T jest jednym z następujących typów:</span><span class="sxs-lookup"><span data-stu-id="74f9c-144">A Collection(T), where T is one of the following types:</span></span> 

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

<span data-ttu-id="74f9c-145">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="74f9c-145">**Return Value**</span></span>

<span data-ttu-id="74f9c-146">Typ `expression`.</span><span class="sxs-lookup"><span data-stu-id="74f9c-146">The type of `expression`.</span></span>

<span data-ttu-id="74f9c-147">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="74f9c-147">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_MAX](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_max)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_MAX](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_max)]

## <a name="minexpression"></a><span data-ttu-id="74f9c-148">MIN (wyrażenie)</span><span class="sxs-lookup"><span data-stu-id="74f9c-148">MIN(expression)</span></span>

<span data-ttu-id="74f9c-149">Zwraca minimalną wartość w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="74f9c-149">Returns the minimum value in a collection.</span></span>

<span data-ttu-id="74f9c-150">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="74f9c-150">**Arguments**</span></span>

<span data-ttu-id="74f9c-151">Kolekcja (T), gdzie T jest jednym z następujących typów:</span><span class="sxs-lookup"><span data-stu-id="74f9c-151">A Collection(T), where T is one of the following types:</span></span> 

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

<span data-ttu-id="74f9c-152">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="74f9c-152">**Return Value**</span></span>

<span data-ttu-id="74f9c-153">Typ `expression`.</span><span class="sxs-lookup"><span data-stu-id="74f9c-153">The type of `expression`.</span></span>

<span data-ttu-id="74f9c-154">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="74f9c-154">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_MIN](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_min)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_MIN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_min)]

## <a name="stdevexpression"></a><span data-ttu-id="74f9c-155">STDEV (wyrażenie)</span><span class="sxs-lookup"><span data-stu-id="74f9c-155">STDEV(expression)</span></span>

<span data-ttu-id="74f9c-156">Zwraca statystyczne odchylenie standardowe wszystkich wartości w określonym wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="74f9c-156">Returns the statistical standard deviation of all values in the specified expression.</span></span>

<span data-ttu-id="74f9c-157">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="74f9c-157">**Arguments**</span></span>

<span data-ttu-id="74f9c-158">Kolekcja (`Double`).</span><span class="sxs-lookup"><span data-stu-id="74f9c-158">A Collection(`Double`).</span></span>

<span data-ttu-id="74f9c-159">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="74f9c-159">**Return Value**</span></span>

<span data-ttu-id="74f9c-160">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="74f9c-160">A `Double`.</span></span>

<span data-ttu-id="74f9c-161">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="74f9c-161">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_STDEV](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_stdev)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEV](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdev)]

## <a name="stdevpexpression"></a><span data-ttu-id="74f9c-162">STDEVP (wyrażenie)</span><span class="sxs-lookup"><span data-stu-id="74f9c-162">STDEVP(expression)</span></span>

<span data-ttu-id="74f9c-163">Zwraca statystyczne odchylenie standardowe populacji dla wszystkich wartości w określonym wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="74f9c-163">Returns the statistical standard deviation for the population for all values in the specified expression.</span></span>

<span data-ttu-id="74f9c-164">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="74f9c-164">**Arguments**</span></span>

<span data-ttu-id="74f9c-165">Kolekcja (`Double`).</span><span class="sxs-lookup"><span data-stu-id="74f9c-165">A Collection(`Double`).</span></span>

<span data-ttu-id="74f9c-166">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="74f9c-166">**Return Value**</span></span>

<span data-ttu-id="74f9c-167">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="74f9c-167">A `Double`.</span></span>

<span data-ttu-id="74f9c-168">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="74f9c-168">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_STDEVP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_stdevp)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEVP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdevp)]

## <a name="sumexpression"></a><span data-ttu-id="74f9c-169">SUM (wyrażenie)</span><span class="sxs-lookup"><span data-stu-id="74f9c-169">SUM(expression)</span></span>

<span data-ttu-id="74f9c-170">Zwraca sumę wszystkich wartości w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="74f9c-170">Returns the sum of all the values in the collection.</span></span>

<span data-ttu-id="74f9c-171">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="74f9c-171">**Arguments**</span></span>

<span data-ttu-id="74f9c-172">Kolekcja (T), gdzie T jest jednym z następujących typów `Int32`:, `Int64`, `Double`, `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="74f9c-172">A Collection(T) where T is one of the following types: `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="74f9c-173">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="74f9c-173">**Return Value**</span></span>

<span data-ttu-id="74f9c-174">Typ `expression`.</span><span class="sxs-lookup"><span data-stu-id="74f9c-174">The type of `expression`.</span></span>

<span data-ttu-id="74f9c-175">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="74f9c-175">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_SUM](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_sum)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_SUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_sum)]

## <a name="varexpression"></a><span data-ttu-id="74f9c-176">VAR (wyrażenie)</span><span class="sxs-lookup"><span data-stu-id="74f9c-176">VAR(expression)</span></span>

<span data-ttu-id="74f9c-177">Zwraca wariancję statystyczną wszystkich wartości w określonym wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="74f9c-177">Returns the statistical variance of all values in the specified expression.</span></span>

<span data-ttu-id="74f9c-178">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="74f9c-178">**Arguments**</span></span>

<span data-ttu-id="74f9c-179">Kolekcja (`Double`).</span><span class="sxs-lookup"><span data-stu-id="74f9c-179">A Collection(`Double`).</span></span>

<span data-ttu-id="74f9c-180">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="74f9c-180">**Return Value**</span></span>

<span data-ttu-id="74f9c-181">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="74f9c-181">A `Double`.</span></span>

<span data-ttu-id="74f9c-182">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="74f9c-182">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_VAR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_var)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_VAR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_var)]

## <a name="varpexpression"></a><span data-ttu-id="74f9c-183">VARP (wyrażenie)</span><span class="sxs-lookup"><span data-stu-id="74f9c-183">VARP(expression)</span></span>

<span data-ttu-id="74f9c-184">Zwraca wariancję statystyczną dla populacji dla wszystkich wartości w określonym wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="74f9c-184">Returns the statistical variance for the population for all values in the specified expression.</span></span>

<span data-ttu-id="74f9c-185">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="74f9c-185">**Arguments**</span></span>

<span data-ttu-id="74f9c-186">Kolekcja (`Double`).</span><span class="sxs-lookup"><span data-stu-id="74f9c-186">A Collection(`Double`).</span></span>

<span data-ttu-id="74f9c-187">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="74f9c-187">**Return Value**</span></span>

<span data-ttu-id="74f9c-188">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="74f9c-188">A `Double`.</span></span>

<span data-ttu-id="74f9c-189">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="74f9c-189">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_VARP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_varp)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_VARP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_varp)] 
  
## <a name="see-also"></a><span data-ttu-id="74f9c-190">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="74f9c-190">See also</span></span>

<span data-ttu-id="74f9c-191">Aby uzyskać więcej informacji na temat funkcji agregujących obsługiwanych przez program SqlClient, zapoznaj się z dokumentacją dla SQL Server wersji określonej w manifeście dostawcy SqlClient:</span><span class="sxs-lookup"><span data-stu-id="74f9c-191">For more information about the aggregate functions that SqlClient supports, see the documentation for the SQL Server version that you specified in the SqlClient provider manifest:</span></span>

- <span data-ttu-id="74f9c-192">**SQL Server 2005:** [Aggregate Functions (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms173454(v=sql.90))</span><span class="sxs-lookup"><span data-stu-id="74f9c-192">**SQL Server 2005:** [Aggregate Functions (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms173454(v=sql.90))</span></span>
- <span data-ttu-id="74f9c-193">**SQL Server 2008 i nowsze:** [Aggregate Functions (Transact-SQL)](/sql/t-sql/functions/aggregate-functions-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="74f9c-193">**SQL Server 2008 and later:** [Aggregate Functions (Transact-SQL)](/sql/t-sql/functions/aggregate-functions-transact-sql)</span></span>

- [<span data-ttu-id="74f9c-194">Jednostki języka SQL</span><span class="sxs-lookup"><span data-stu-id="74f9c-194">Entity SQL Language</span></span>](./language-reference/entity-sql-language.md)
- [<span data-ttu-id="74f9c-195">Funkcje agregujące Canonical</span><span class="sxs-lookup"><span data-stu-id="74f9c-195">Aggregate Canonical Functions</span></span>](./language-reference/aggregate-canonical-functions.md)
