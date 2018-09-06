---
title: Funkcje agregujące (SqlClient programu Entity Framework)
ms.date: 03/30/2017
ms.assetid: 03303f01-b591-4efc-9875-f9c608edff0b
ms.openlocfilehash: 8ed9a58da9914724fe312876d6594cb526f2e0e9
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43856520"
---
# <a name="aggregate-functions-sqlclient-for-entity-framework"></a><span data-ttu-id="cdb0a-102">Funkcje agregujące (SqlClient programu Entity Framework)</span><span class="sxs-lookup"><span data-stu-id="cdb0a-102">Aggregate Functions (SqlClient for Entity Framework)</span></span>
<span data-ttu-id="cdb0a-103">.NET Framework Data Provider for SQL Server (SqlClient) zapewnia funkcje agregujące.</span><span class="sxs-lookup"><span data-stu-id="cdb0a-103">The .NET Framework Data Provider for SQL Server (SqlClient) provides aggregate functions.</span></span> <span data-ttu-id="cdb0a-104">Funkcje agregujące wykonywanie obliczeń na zestaw wartości wejściowych i zwracają wartość.</span><span class="sxs-lookup"><span data-stu-id="cdb0a-104">Aggregate functions perform calculations on a set of input values and return a value.</span></span> <span data-ttu-id="cdb0a-105">Te funkcje są w przestrzeni nazw SqlServer, który jest dostępny, gdy używasz SqlClient.</span><span class="sxs-lookup"><span data-stu-id="cdb0a-105">These functions are in the SqlServer namespace, which is available when you use SqlClient.</span></span> <span data-ttu-id="cdb0a-106">Właściwość przestrzeni nazw dostawcy umożliwia programu Entity Framework dowiedzieć się, który prefiks jest używany przez tego dostawcę dla określonego konstrukcji, takich jak typy i funkcje.</span><span class="sxs-lookup"><span data-stu-id="cdb0a-106">A provider's namespace property allows the Entity Framework to discover which prefix is used by this provider for specific constructs, such as types and functions.</span></span>  
  
 <span data-ttu-id="cdb0a-107">Dostępne są następujące funkcje agregujące SqlClient.</span><span class="sxs-lookup"><span data-stu-id="cdb0a-107">The following are the SqlClient aggregate functions.</span></span>  

## <a name="avgexpression"></a><span data-ttu-id="cdb0a-108">AVG(Expression)</span><span class="sxs-lookup"><span data-stu-id="cdb0a-108">AVG(expression)</span></span>

<span data-ttu-id="cdb0a-109">Zwraca średnią z wartości w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="cdb0a-109">Returns the average of the values in a collection.</span></span> <span data-ttu-id="cdb0a-110">Wartości null są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="cdb0a-110">Null values are ignored.</span></span>

<span data-ttu-id="cdb0a-111">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="cdb0a-111">**Arguments**</span></span>

<span data-ttu-id="cdb0a-112">`Int32`, `Int64`, `Double`, I `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="cdb0a-112">An `Int32`, `Int64`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="cdb0a-113">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="cdb0a-113">**Return Value**</span></span>

<span data-ttu-id="cdb0a-114">Typ `expression`.</span><span class="sxs-lookup"><span data-stu-id="cdb0a-114">The type of `expression`.</span></span>

<span data-ttu-id="cdb0a-115">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="cdb0a-115">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_AVG](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_avg)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_AVG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_avg)]

## <a name="checksumaggcollection"></a><span data-ttu-id="cdb0a-116">CHECKSUM_AGG(Collection)</span><span class="sxs-lookup"><span data-stu-id="cdb0a-116">CHECKSUM_AGG(collection)</span></span>
 
 <span data-ttu-id="cdb0a-117">Zwraca sumę kontrolną wartości w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="cdb0a-117">Returns the checksum of the values in a collection.</span></span> <span data-ttu-id="cdb0a-118">Wartości null są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="cdb0a-118">Null values are ignored.</span></span>
 
 <span data-ttu-id="cdb0a-119">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="cdb0a-119">**Arguments**</span></span>
 
 <span data-ttu-id="cdb0a-120">Kolekcja (`Int32`).</span><span class="sxs-lookup"><span data-stu-id="cdb0a-120">A Collection(`Int32`).</span></span>
 
 <span data-ttu-id="cdb0a-121">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="cdb0a-121">**Return Value**</span></span>
 
 <span data-ttu-id="cdb0a-122">`Int32`.</span><span class="sxs-lookup"><span data-stu-id="cdb0a-122">An `Int32`.</span></span>
 
 <span data-ttu-id="cdb0a-123">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="cdb0a-123">**Example**</span></span>
 
 [!code-csharp[DP EntityServices Concepts#SQLSERVER_CHECKSUM](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_checksum)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_CHECKSUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_checksum)]
   
## <a name="countexpression"></a><span data-ttu-id="cdb0a-124">Count(Expression)</span><span class="sxs-lookup"><span data-stu-id="cdb0a-124">COUNT(expression)</span></span>

<span data-ttu-id="cdb0a-125">Zwraca liczbę elementów w kolekcji jako `Int32`.</span><span class="sxs-lookup"><span data-stu-id="cdb0a-125">Returns the number of items in a collection as an `Int32`.</span></span>

<span data-ttu-id="cdb0a-126">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="cdb0a-126">**Arguments**</span></span>

<span data-ttu-id="cdb0a-127">Kolekcja\<T >, gdzie T jest jednym z następujących typów:</span><span class="sxs-lookup"><span data-stu-id="cdb0a-127">A Collection\<T>, where T is one of the following types:</span></span>

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|<span data-ttu-id="cdb0a-128">`Guid` (nie jest zwracana w programie SQL Server 2000)</span><span class="sxs-lookup"><span data-stu-id="cdb0a-128">`Guid` (not returned in SQL Server 2000)</span></span>|

<span data-ttu-id="cdb0a-129">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="cdb0a-129">**Return Value**</span></span>

<span data-ttu-id="cdb0a-130">`Int32`.</span><span class="sxs-lookup"><span data-stu-id="cdb0a-130">An `Int32`.</span></span>

<span data-ttu-id="cdb0a-131">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="cdb0a-131">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_COUNT](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_count)]
<span data-ttu-id="cdb0a-132">[! code-sql[SQLSERVER_COUNT # pojęcia EntityServices punktu dystrybucji](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_count)</span><span class="sxs-lookup"><span data-stu-id="cdb0a-132">[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_count)</span></span>
 
## <a name="countbigexpression"></a><span data-ttu-id="cdb0a-133">COUNT_BIG(Expression)</span><span class="sxs-lookup"><span data-stu-id="cdb0a-133">COUNT_BIG(expression)</span></span>
 
 <span data-ttu-id="cdb0a-134">Zwraca liczbę elementów w kolekcji jako `bigint`.</span><span class="sxs-lookup"><span data-stu-id="cdb0a-134">Returns the number of items in a collection as a `bigint`.</span></span>
 
 <span data-ttu-id="cdb0a-135">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="cdb0a-135">**Arguments**</span></span>
 
 <span data-ttu-id="cdb0a-136">Collection(T), gdzie T jest jednym z następujących typów:</span><span class="sxs-lookup"><span data-stu-id="cdb0a-136">A Collection(T), where T is one of the following types:</span></span>
 
 |   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|<span data-ttu-id="cdb0a-137">`Guid` (nie jest zwracana w programie SQL Server 2000)</span><span class="sxs-lookup"><span data-stu-id="cdb0a-137">`Guid` (not returned in SQL Server 2000)</span></span>|

<span data-ttu-id="cdb0a-138">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="cdb0a-138">**Return Value**</span></span>

<span data-ttu-id="cdb0a-139">`Int64`.</span><span class="sxs-lookup"><span data-stu-id="cdb0a-139">An `Int64`.</span></span>

<span data-ttu-id="cdb0a-140">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="cdb0a-140">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_COUNTBIG](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_countbig)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNTBIG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_countbig)]

## <a name="maxexpression"></a><span data-ttu-id="cdb0a-141">MAX(Expression)</span><span class="sxs-lookup"><span data-stu-id="cdb0a-141">MAX(expression)</span></span>

<span data-ttu-id="cdb0a-142">Zwraca maksymalną wartość w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="cdb0a-142">Returns the maximum value the collection.</span></span>

<span data-ttu-id="cdb0a-143">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="cdb0a-143">**Arguments**</span></span>

<span data-ttu-id="cdb0a-144">Collection(T), gdzie T jest jednym z następujących typów:</span><span class="sxs-lookup"><span data-stu-id="cdb0a-144">A Collection(T), where T is one of the following types:</span></span> 

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

<span data-ttu-id="cdb0a-145">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="cdb0a-145">**Return Value**</span></span>

<span data-ttu-id="cdb0a-146">Typ `expression`.</span><span class="sxs-lookup"><span data-stu-id="cdb0a-146">The type of `expression`.</span></span>

<span data-ttu-id="cdb0a-147">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="cdb0a-147">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_MAX](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_max)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_MAX](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_max)]

## <a name="minexpression"></a><span data-ttu-id="cdb0a-148">MIN(Expression)</span><span class="sxs-lookup"><span data-stu-id="cdb0a-148">MIN(expression)</span></span>

<span data-ttu-id="cdb0a-149">Zwraca minimalną wartość w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="cdb0a-149">Returns the minimum value in a collection.</span></span>

<span data-ttu-id="cdb0a-150">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="cdb0a-150">**Arguments**</span></span>

<span data-ttu-id="cdb0a-151">Collection(T), gdzie T jest jednym z następujących typów:</span><span class="sxs-lookup"><span data-stu-id="cdb0a-151">A Collection(T), where T is one of the following types:</span></span> 

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

<span data-ttu-id="cdb0a-152">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="cdb0a-152">**Return Value**</span></span>

<span data-ttu-id="cdb0a-153">Typ `expression`.</span><span class="sxs-lookup"><span data-stu-id="cdb0a-153">The type of `expression`.</span></span>

<span data-ttu-id="cdb0a-154">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="cdb0a-154">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_MIN](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_min)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_MIN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_min)]

## <a name="stdevexpression"></a><span data-ttu-id="cdb0a-155">StDev(Expression)</span><span class="sxs-lookup"><span data-stu-id="cdb0a-155">STDEV(expression)</span></span>

<span data-ttu-id="cdb0a-156">Zwraca statystyczne odchylenie standardowe wszystkich wartości określonego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="cdb0a-156">Returns the statistical standard deviation of all values in the specified expression.</span></span>

<span data-ttu-id="cdb0a-157">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="cdb0a-157">**Arguments**</span></span>

<span data-ttu-id="cdb0a-158">Kolekcja (`Double`).</span><span class="sxs-lookup"><span data-stu-id="cdb0a-158">A Collection(`Double`).</span></span>

<span data-ttu-id="cdb0a-159">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="cdb0a-159">**Return Value**</span></span>

<span data-ttu-id="cdb0a-160">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="cdb0a-160">A `Double`.</span></span>

<span data-ttu-id="cdb0a-161">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="cdb0a-161">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_STDEV](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_stdev)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEV](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdev)]

## <a name="stdevpexpression"></a><span data-ttu-id="cdb0a-162">STDEVP(Expression)</span><span class="sxs-lookup"><span data-stu-id="cdb0a-162">STDEVP(expression)</span></span>

<span data-ttu-id="cdb0a-163">Zwraca statystyczne odchylenie standardowe populacji dla wszystkich wartości określonego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="cdb0a-163">Returns the statistical standard deviation for the population for all values in the specified expression.</span></span>

<span data-ttu-id="cdb0a-164">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="cdb0a-164">**Arguments**</span></span>

<span data-ttu-id="cdb0a-165">Kolekcja (`Double`).</span><span class="sxs-lookup"><span data-stu-id="cdb0a-165">A Collection(`Double`).</span></span>

<span data-ttu-id="cdb0a-166">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="cdb0a-166">**Return Value**</span></span>

<span data-ttu-id="cdb0a-167">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="cdb0a-167">A `Double`.</span></span>

<span data-ttu-id="cdb0a-168">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="cdb0a-168">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_STDEVP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_stdevp)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEVP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdevp)]

## <a name="sumexpression"></a><span data-ttu-id="cdb0a-169">SUM(Expression)</span><span class="sxs-lookup"><span data-stu-id="cdb0a-169">SUM(expression)</span></span>

<span data-ttu-id="cdb0a-170">Zwraca sumę wszystkich wartości w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="cdb0a-170">Returns the sum of all the values in the collection.</span></span>

<span data-ttu-id="cdb0a-171">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="cdb0a-171">**Arguments**</span></span>

<span data-ttu-id="cdb0a-172">Collection(T), gdzie T jest jednym z następujących typów: `Int32`, `Int64`, `Double`, `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="cdb0a-172">A Collection(T) where T is one of the following types: `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="cdb0a-173">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="cdb0a-173">**Return Value**</span></span>

<span data-ttu-id="cdb0a-174">Typ `expression`.</span><span class="sxs-lookup"><span data-stu-id="cdb0a-174">The type of `expression`.</span></span>

<span data-ttu-id="cdb0a-175">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="cdb0a-175">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_SUM](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_sum)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_SUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_sum)]

## <a name="varexpression"></a><span data-ttu-id="cdb0a-176">VAR(Expression)</span><span class="sxs-lookup"><span data-stu-id="cdb0a-176">VAR(expression)</span></span>

<span data-ttu-id="cdb0a-177">Zwraca statystyczną wariancję wszystkich wartości określonego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="cdb0a-177">Returns the statistical variance of all values in the specified expression.</span></span>

<span data-ttu-id="cdb0a-178">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="cdb0a-178">**Arguments**</span></span>

<span data-ttu-id="cdb0a-179">Kolekcja (`Double`).</span><span class="sxs-lookup"><span data-stu-id="cdb0a-179">A Collection(`Double`).</span></span>

<span data-ttu-id="cdb0a-180">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="cdb0a-180">**Return Value**</span></span>

<span data-ttu-id="cdb0a-181">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="cdb0a-181">A `Double`.</span></span>

<span data-ttu-id="cdb0a-182">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="cdb0a-182">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_VAR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_var)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_VAR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_var)]

## <a name="varpexpression"></a><span data-ttu-id="cdb0a-183">VARP(Expression)</span><span class="sxs-lookup"><span data-stu-id="cdb0a-183">VARP(expression)</span></span>

<span data-ttu-id="cdb0a-184">Zwraca statystyczne wariancję populacji dla wszystkich wartości podanego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="cdb0a-184">Returns the statistical variance for the population for all values in the specified expression.</span></span>

<span data-ttu-id="cdb0a-185">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="cdb0a-185">**Arguments**</span></span>

<span data-ttu-id="cdb0a-186">Kolekcja (`Double`).</span><span class="sxs-lookup"><span data-stu-id="cdb0a-186">A Collection(`Double`).</span></span>

<span data-ttu-id="cdb0a-187">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="cdb0a-187">**Return Value**</span></span>

<span data-ttu-id="cdb0a-188">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="cdb0a-188">A `Double`.</span></span>

<span data-ttu-id="cdb0a-189">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="cdb0a-189">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_VARP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_varp)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_VARP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_varp)] 
  
## <a name="see-also"></a><span data-ttu-id="cdb0a-190">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cdb0a-190">See also</span></span>

<span data-ttu-id="cdb0a-191">Aby uzyskać więcej informacji na temat funkcji agregujących, które obsługuje klient SQL zobacz dokumentację dla używanej wersji programu SQL Server określonego w manifeście dostawcy SqlClient:</span><span class="sxs-lookup"><span data-stu-id="cdb0a-191">For more information about the aggregate functions that SqlClient supports, see the documentation for the SQL Server version that you specified in the SqlClient provider manifest:</span></span>  
  
<span data-ttu-id="cdb0a-192">**SQL Server 2005**: [funkcje (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms173454(v=sql.90))</span><span class="sxs-lookup"><span data-stu-id="cdb0a-192">**SQL Server 2005**: [Aggregate Functions (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms173454(v=sql.90))</span></span>  
<span data-ttu-id="cdb0a-193">**Program SQL Server 2008 i nowsze wersje**: [funkcje agregujące (Transact-SQL)](/sql/t-sql/functions/aggregate-functions-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="cdb0a-193">**SQL Server 2008 and later**:  [Aggregate Functions (Transact-SQL)](/sql/t-sql/functions/aggregate-functions-transact-sql)</span></span>  
[<span data-ttu-id="cdb0a-194">Jednostki języka SQL</span><span class="sxs-lookup"><span data-stu-id="cdb0a-194">Entity SQL Language</span></span>](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)  
[<span data-ttu-id="cdb0a-195">Funkcje agregujące Canonical</span><span class="sxs-lookup"><span data-stu-id="cdb0a-195">Aggregate Canonical Functions</span></span>](../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)
