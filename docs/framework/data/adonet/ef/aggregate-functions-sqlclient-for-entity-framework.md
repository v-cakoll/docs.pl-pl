---
title: Funkcje agregujące (SqlClient dla Entity Framework)
ms.date: 03/30/2017
ms.assetid: 03303f01-b591-4efc-9875-f9c608edff0b
ms.openlocfilehash: 3dbd4c0a24a5fc41153ea16747325e824669b0e5
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700057"
---
# <a name="aggregate-functions-sqlclient-for-entity-framework"></a><span data-ttu-id="75b20-102">Funkcje agregujące (SqlClient dla Entity Framework)</span><span class="sxs-lookup"><span data-stu-id="75b20-102">Aggregate Functions (SqlClient for Entity Framework)</span></span>
<span data-ttu-id="75b20-103">Dostawca danych .NET Framework dla SQL Server (SqlClient) udostępnia funkcje agregujące.</span><span class="sxs-lookup"><span data-stu-id="75b20-103">The .NET Framework Data Provider for SQL Server (SqlClient) provides aggregate functions.</span></span> <span data-ttu-id="75b20-104">Funkcje agregujące wykonują obliczenia na zestawie wartości wejściowych i zwracają wartość.</span><span class="sxs-lookup"><span data-stu-id="75b20-104">Aggregate functions perform calculations on a set of input values and return a value.</span></span> <span data-ttu-id="75b20-105">Te funkcje znajdują się w przestrzeni nazw SqlServer, która jest dostępna w przypadku korzystania z programu SqlClient.</span><span class="sxs-lookup"><span data-stu-id="75b20-105">These functions are in the SqlServer namespace, which is available when you use SqlClient.</span></span> <span data-ttu-id="75b20-106">Właściwość przestrzeni nazw dostawcy umożliwia Entity Framework odnajdywania prefiksu używanego przez tego dostawcę dla określonych konstrukcji, takich jak typy i funkcje.</span><span class="sxs-lookup"><span data-stu-id="75b20-106">A provider's namespace property allows the Entity Framework to discover which prefix is used by this provider for specific constructs, such as types and functions.</span></span>  
  
 <span data-ttu-id="75b20-107">Poniżej przedstawiono funkcje agregujące SqlClient.</span><span class="sxs-lookup"><span data-stu-id="75b20-107">The following are the SqlClient aggregate functions.</span></span>  

## <a name="avgexpression"></a><span data-ttu-id="75b20-108">Średnia (wyrażenie)</span><span class="sxs-lookup"><span data-stu-id="75b20-108">AVG(expression)</span></span>

<span data-ttu-id="75b20-109">Zwraca średnią wartości w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="75b20-109">Returns the average of the values in a collection.</span></span> <span data-ttu-id="75b20-110">Wartości null są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="75b20-110">Null values are ignored.</span></span>

<span data-ttu-id="75b20-111">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="75b20-111">**Arguments**</span></span>

<span data-ttu-id="75b20-112">`Int32`, `Int64`, `Double`i `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="75b20-112">An `Int32`, `Int64`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="75b20-113">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="75b20-113">**Return Value**</span></span>

<span data-ttu-id="75b20-114">Typ elementu `expression`.</span><span class="sxs-lookup"><span data-stu-id="75b20-114">The type of `expression`.</span></span>

<span data-ttu-id="75b20-115">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="75b20-115">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_AVG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_avg)]

## <a name="checksum_aggcollection"></a><span data-ttu-id="75b20-116">CHECKSUM_AGG (kolekcja)</span><span class="sxs-lookup"><span data-stu-id="75b20-116">CHECKSUM_AGG(collection)</span></span>
 
 <span data-ttu-id="75b20-117">Zwraca sumę kontrolną wartości w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="75b20-117">Returns the checksum of the values in a collection.</span></span> <span data-ttu-id="75b20-118">Wartości null są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="75b20-118">Null values are ignored.</span></span>
 
 <span data-ttu-id="75b20-119">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="75b20-119">**Arguments**</span></span>
 
 <span data-ttu-id="75b20-120">Kolekcja (`Int32`).</span><span class="sxs-lookup"><span data-stu-id="75b20-120">A Collection(`Int32`).</span></span>
 
 <span data-ttu-id="75b20-121">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="75b20-121">**Return Value**</span></span>
 
 <span data-ttu-id="75b20-122">`Int32`.</span><span class="sxs-lookup"><span data-stu-id="75b20-122">An `Int32`.</span></span>
 
 <span data-ttu-id="75b20-123">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="75b20-123">**Example**</span></span>
 
[!code-sql[DP EntityServices Concepts#SQLSERVER_CHECKSUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_checksum)]
   
## <a name="countexpression"></a><span data-ttu-id="75b20-124">COUNT (wyrażenie)</span><span class="sxs-lookup"><span data-stu-id="75b20-124">COUNT(expression)</span></span>

<span data-ttu-id="75b20-125">Zwraca liczbę elementów w kolekcji jako `Int32`.</span><span class="sxs-lookup"><span data-stu-id="75b20-125">Returns the number of items in a collection as an `Int32`.</span></span>

<span data-ttu-id="75b20-126">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="75b20-126">**Arguments**</span></span>

<span data-ttu-id="75b20-127">Kolekcja\<T >, gdzie T jest jednym z następujących typów:</span><span class="sxs-lookup"><span data-stu-id="75b20-127">A Collection\<T>, where T is one of the following types:</span></span>

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|<span data-ttu-id="75b20-128">`Guid` (niezwrócone w SQL Server 2000)</span><span class="sxs-lookup"><span data-stu-id="75b20-128">`Guid` (not returned in SQL Server 2000)</span></span>|

<span data-ttu-id="75b20-129">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="75b20-129">**Return Value**</span></span>

<span data-ttu-id="75b20-130">`Int32`.</span><span class="sxs-lookup"><span data-stu-id="75b20-130">An `Int32`.</span></span>

<span data-ttu-id="75b20-131">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="75b20-131">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_count)]
 
## <a name="count_bigexpression"></a><span data-ttu-id="75b20-132">COUNT_BIG (wyrażenie)</span><span class="sxs-lookup"><span data-stu-id="75b20-132">COUNT_BIG(expression)</span></span>
 
<span data-ttu-id="75b20-133">Zwraca liczbę elementów w kolekcji jako `bigint`.</span><span class="sxs-lookup"><span data-stu-id="75b20-133">Returns the number of items in a collection as a `bigint`.</span></span>
 
 <span data-ttu-id="75b20-134">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="75b20-134">**Arguments**</span></span>
 
 <span data-ttu-id="75b20-135">Kolekcja (T), gdzie T jest jednym z następujących typów:</span><span class="sxs-lookup"><span data-stu-id="75b20-135">A Collection(T), where T is one of the following types:</span></span>
 
 |   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|<span data-ttu-id="75b20-136">`Guid` (niezwrócone w SQL Server 2000)</span><span class="sxs-lookup"><span data-stu-id="75b20-136">`Guid` (not returned in SQL Server 2000)</span></span>|

<span data-ttu-id="75b20-137">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="75b20-137">**Return Value**</span></span>

<span data-ttu-id="75b20-138">`Int64`.</span><span class="sxs-lookup"><span data-stu-id="75b20-138">An `Int64`.</span></span>

<span data-ttu-id="75b20-139">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="75b20-139">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNTBIG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_countbig)]

## <a name="maxexpression"></a><span data-ttu-id="75b20-140">MAX (wyrażenie)</span><span class="sxs-lookup"><span data-stu-id="75b20-140">MAX(expression)</span></span>

<span data-ttu-id="75b20-141">Zwraca maksymalną wartość kolekcji.</span><span class="sxs-lookup"><span data-stu-id="75b20-141">Returns the maximum value the collection.</span></span>

<span data-ttu-id="75b20-142">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="75b20-142">**Arguments**</span></span>

<span data-ttu-id="75b20-143">Kolekcja (T), gdzie T jest jednym z następujących typów:</span><span class="sxs-lookup"><span data-stu-id="75b20-143">A Collection(T), where T is one of the following types:</span></span> 

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

<span data-ttu-id="75b20-144">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="75b20-144">**Return Value**</span></span>

<span data-ttu-id="75b20-145">Typ elementu `expression`.</span><span class="sxs-lookup"><span data-stu-id="75b20-145">The type of `expression`.</span></span>

<span data-ttu-id="75b20-146">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="75b20-146">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_MAX](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_max)]

## <a name="minexpression"></a><span data-ttu-id="75b20-147">MIN (wyrażenie)</span><span class="sxs-lookup"><span data-stu-id="75b20-147">MIN(expression)</span></span>

<span data-ttu-id="75b20-148">Zwraca minimalną wartość w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="75b20-148">Returns the minimum value in a collection.</span></span>

<span data-ttu-id="75b20-149">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="75b20-149">**Arguments**</span></span>

<span data-ttu-id="75b20-150">Kolekcja (T), gdzie T jest jednym z następujących typów:</span><span class="sxs-lookup"><span data-stu-id="75b20-150">A Collection(T), where T is one of the following types:</span></span> 

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

<span data-ttu-id="75b20-151">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="75b20-151">**Return Value**</span></span>

<span data-ttu-id="75b20-152">Typ elementu `expression`.</span><span class="sxs-lookup"><span data-stu-id="75b20-152">The type of `expression`.</span></span>

<span data-ttu-id="75b20-153">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="75b20-153">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_MIN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_min)]

## <a name="stdevexpression"></a><span data-ttu-id="75b20-154">STDEV (wyrażenie)</span><span class="sxs-lookup"><span data-stu-id="75b20-154">STDEV(expression)</span></span>

<span data-ttu-id="75b20-155">Zwraca statystyczne odchylenie standardowe wszystkich wartości w określonym wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="75b20-155">Returns the statistical standard deviation of all values in the specified expression.</span></span>

<span data-ttu-id="75b20-156">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="75b20-156">**Arguments**</span></span>

<span data-ttu-id="75b20-157">Kolekcja (`Double`).</span><span class="sxs-lookup"><span data-stu-id="75b20-157">A Collection(`Double`).</span></span>

<span data-ttu-id="75b20-158">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="75b20-158">**Return Value**</span></span>

<span data-ttu-id="75b20-159">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="75b20-159">A `Double`.</span></span>

<span data-ttu-id="75b20-160">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="75b20-160">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEV](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdev)]

## <a name="stdevpexpression"></a><span data-ttu-id="75b20-161">STDEVP (wyrażenie)</span><span class="sxs-lookup"><span data-stu-id="75b20-161">STDEVP(expression)</span></span>

<span data-ttu-id="75b20-162">Zwraca statystyczne odchylenie standardowe populacji dla wszystkich wartości w określonym wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="75b20-162">Returns the statistical standard deviation for the population for all values in the specified expression.</span></span>

<span data-ttu-id="75b20-163">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="75b20-163">**Arguments**</span></span>

<span data-ttu-id="75b20-164">Kolekcja (`Double`).</span><span class="sxs-lookup"><span data-stu-id="75b20-164">A Collection(`Double`).</span></span>

<span data-ttu-id="75b20-165">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="75b20-165">**Return Value**</span></span>

<span data-ttu-id="75b20-166">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="75b20-166">A `Double`.</span></span>

<span data-ttu-id="75b20-167">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="75b20-167">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEVP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdevp)]

## <a name="sumexpression"></a><span data-ttu-id="75b20-168">SUM (wyrażenie)</span><span class="sxs-lookup"><span data-stu-id="75b20-168">SUM(expression)</span></span>

<span data-ttu-id="75b20-169">Zwraca sumę wszystkich wartości w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="75b20-169">Returns the sum of all the values in the collection.</span></span>

<span data-ttu-id="75b20-170">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="75b20-170">**Arguments**</span></span>

<span data-ttu-id="75b20-171">Kolekcja (T), gdzie T jest jednym z następujących typów: `Int32`, `Int64`, `Double``Decimal`.</span><span class="sxs-lookup"><span data-stu-id="75b20-171">A Collection(T) where T is one of the following types: `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="75b20-172">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="75b20-172">**Return Value**</span></span>

<span data-ttu-id="75b20-173">Typ elementu `expression`.</span><span class="sxs-lookup"><span data-stu-id="75b20-173">The type of `expression`.</span></span>

<span data-ttu-id="75b20-174">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="75b20-174">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_SUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_sum)]

## <a name="varexpression"></a><span data-ttu-id="75b20-175">VAR (wyrażenie)</span><span class="sxs-lookup"><span data-stu-id="75b20-175">VAR(expression)</span></span>

<span data-ttu-id="75b20-176">Zwraca wariancję statystyczną wszystkich wartości w określonym wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="75b20-176">Returns the statistical variance of all values in the specified expression.</span></span>

<span data-ttu-id="75b20-177">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="75b20-177">**Arguments**</span></span>

<span data-ttu-id="75b20-178">Kolekcja (`Double`).</span><span class="sxs-lookup"><span data-stu-id="75b20-178">A Collection(`Double`).</span></span>

<span data-ttu-id="75b20-179">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="75b20-179">**Return Value**</span></span>

<span data-ttu-id="75b20-180">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="75b20-180">A `Double`.</span></span>

<span data-ttu-id="75b20-181">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="75b20-181">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_VAR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_var)]

## <a name="varpexpression"></a><span data-ttu-id="75b20-182">VARP (wyrażenie)</span><span class="sxs-lookup"><span data-stu-id="75b20-182">VARP(expression)</span></span>

<span data-ttu-id="75b20-183">Zwraca wariancję statystyczną dla populacji dla wszystkich wartości w określonym wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="75b20-183">Returns the statistical variance for the population for all values in the specified expression.</span></span>

<span data-ttu-id="75b20-184">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="75b20-184">**Arguments**</span></span>

<span data-ttu-id="75b20-185">Kolekcja (`Double`).</span><span class="sxs-lookup"><span data-stu-id="75b20-185">A Collection(`Double`).</span></span>

<span data-ttu-id="75b20-186">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="75b20-186">**Return Value**</span></span>

<span data-ttu-id="75b20-187">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="75b20-187">A `Double`.</span></span>

<span data-ttu-id="75b20-188">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="75b20-188">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_VARP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_varp)] 
  
## <a name="see-also"></a><span data-ttu-id="75b20-189">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="75b20-189">See also</span></span>

- [<span data-ttu-id="75b20-190">Aggregate Functions (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="75b20-190">Aggregate Functions (Transact-SQL)</span></span>](/sql/t-sql/functions/aggregate-functions-transact-sql)
- [<span data-ttu-id="75b20-191">Jednostki języka SQL</span><span class="sxs-lookup"><span data-stu-id="75b20-191">Entity SQL Language</span></span>](./language-reference/entity-sql-language.md)
- [<span data-ttu-id="75b20-192">Funkcje agregujące Canonical</span><span class="sxs-lookup"><span data-stu-id="75b20-192">Aggregate Canonical Functions</span></span>](./language-reference/aggregate-canonical-functions.md)
