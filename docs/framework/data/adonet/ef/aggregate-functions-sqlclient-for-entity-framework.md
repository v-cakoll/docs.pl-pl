---
title: Funkcje agregujące (SqlClient for Entity Framework)
ms.date: 03/30/2017
ms.assetid: 03303f01-b591-4efc-9875-f9c608edff0b
ms.openlocfilehash: 1fad25f2229b4fa810cf82a96dcb8c50a9de3070
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150652"
---
# <a name="aggregate-functions-sqlclient-for-entity-framework"></a><span data-ttu-id="7d394-102">Funkcje agregujące (SqlClient for Entity Framework)</span><span class="sxs-lookup"><span data-stu-id="7d394-102">Aggregate Functions (SqlClient for Entity Framework)</span></span>
<span data-ttu-id="7d394-103">Dostawca danych programu .NET Framework dla programu SQL Server (SqlClient) udostępnia funkcje agregujące.</span><span class="sxs-lookup"><span data-stu-id="7d394-103">The .NET Framework Data Provider for SQL Server (SqlClient) provides aggregate functions.</span></span> <span data-ttu-id="7d394-104">Funkcje agregowane wykonują obliczenia na zestawie wartości wejściowych i zwracają wartość.</span><span class="sxs-lookup"><span data-stu-id="7d394-104">Aggregate functions perform calculations on a set of input values and return a value.</span></span> <span data-ttu-id="7d394-105">Te funkcje znajdują się w obszarze nazw SqlServer, który jest dostępny podczas korzystania z SqlClient.</span><span class="sxs-lookup"><span data-stu-id="7d394-105">These functions are in the SqlServer namespace, which is available when you use SqlClient.</span></span> <span data-ttu-id="7d394-106">Właściwość obszaru nazw dostawcy umożliwia entity framework, który prefiks jest używany przez tego dostawcę dla określonych konstrukcji, takich jak typy i funkcje.</span><span class="sxs-lookup"><span data-stu-id="7d394-106">A provider's namespace property allows the Entity Framework to discover which prefix is used by this provider for specific constructs, such as types and functions.</span></span>  
  
 <span data-ttu-id="7d394-107">Poniżej przedstawiono funkcje agregujące SqlClient.</span><span class="sxs-lookup"><span data-stu-id="7d394-107">The following are the SqlClient aggregate functions.</span></span>  

## <a name="avgexpression"></a><span data-ttu-id="7d394-108">AVG(wyrażenie)</span><span class="sxs-lookup"><span data-stu-id="7d394-108">AVG(expression)</span></span>

<span data-ttu-id="7d394-109">Zwraca średnią wartości w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="7d394-109">Returns the average of the values in a collection.</span></span> <span data-ttu-id="7d394-110">Wartości null są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="7d394-110">Null values are ignored.</span></span>

<span data-ttu-id="7d394-111">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="7d394-111">**Arguments**</span></span>

<span data-ttu-id="7d394-112">An `Int32` `Int64`, `Double`, `Decimal`i .</span><span class="sxs-lookup"><span data-stu-id="7d394-112">An `Int32`, `Int64`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="7d394-113">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="7d394-113">**Return Value**</span></span>

<span data-ttu-id="7d394-114">Typ . `expression`</span><span class="sxs-lookup"><span data-stu-id="7d394-114">The type of `expression`.</span></span>

<span data-ttu-id="7d394-115">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="7d394-115">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_AVG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_avg)]

## <a name="checksum_aggcollection"></a><span data-ttu-id="7d394-116">CHECKSUM_AGG(kolekcja)</span><span class="sxs-lookup"><span data-stu-id="7d394-116">CHECKSUM_AGG(collection)</span></span>

 <span data-ttu-id="7d394-117">Zwraca sumę kontrolną wartości w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="7d394-117">Returns the checksum of the values in a collection.</span></span> <span data-ttu-id="7d394-118">Wartości null są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="7d394-118">Null values are ignored.</span></span>

 <span data-ttu-id="7d394-119">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="7d394-119">**Arguments**</span></span>

 <span data-ttu-id="7d394-120">Kolekcja(`Int32`).</span><span class="sxs-lookup"><span data-stu-id="7d394-120">A Collection(`Int32`).</span></span>

 <span data-ttu-id="7d394-121">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="7d394-121">**Return Value**</span></span>

 <span data-ttu-id="7d394-122">An `Int32`.</span><span class="sxs-lookup"><span data-stu-id="7d394-122">An `Int32`.</span></span>

 <span data-ttu-id="7d394-123">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="7d394-123">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_CHECKSUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_checksum)]

## <a name="countexpression"></a><span data-ttu-id="7d394-124">COUNT(wyrażenie)</span><span class="sxs-lookup"><span data-stu-id="7d394-124">COUNT(expression)</span></span>

<span data-ttu-id="7d394-125">Zwraca liczbę elementów w kolekcji jako plik `Int32`.</span><span class="sxs-lookup"><span data-stu-id="7d394-125">Returns the number of items in a collection as an `Int32`.</span></span>

<span data-ttu-id="7d394-126">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="7d394-126">**Arguments**</span></span>

<span data-ttu-id="7d394-127">Kolekcja\<T>, gdzie T jest jednym z następujących typów:</span><span class="sxs-lookup"><span data-stu-id="7d394-127">A Collection\<T>, where T is one of the following types:</span></span>

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|<span data-ttu-id="7d394-128">`Guid`(nie zwrócono w programie SQL Server 2000)</span><span class="sxs-lookup"><span data-stu-id="7d394-128">`Guid` (not returned in SQL Server 2000)</span></span>|

<span data-ttu-id="7d394-129">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="7d394-129">**Return Value**</span></span>

<span data-ttu-id="7d394-130">An `Int32`.</span><span class="sxs-lookup"><span data-stu-id="7d394-130">An `Int32`.</span></span>

<span data-ttu-id="7d394-131">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="7d394-131">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_count)]

## <a name="count_bigexpression"></a><span data-ttu-id="7d394-132">COUNT_BIG(wyrażenie)</span><span class="sxs-lookup"><span data-stu-id="7d394-132">COUNT_BIG(expression)</span></span>

<span data-ttu-id="7d394-133">Zwraca liczbę elementów w kolekcji jako `bigint`.</span><span class="sxs-lookup"><span data-stu-id="7d394-133">Returns the number of items in a collection as a `bigint`.</span></span>

 <span data-ttu-id="7d394-134">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="7d394-134">**Arguments**</span></span>

 <span data-ttu-id="7d394-135">Kolekcja(T), gdzie T jest jednym z następujących typów:</span><span class="sxs-lookup"><span data-stu-id="7d394-135">A Collection(T), where T is one of the following types:</span></span>

 |   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|<span data-ttu-id="7d394-136">`Guid`(nie zwrócono w programie SQL Server 2000)</span><span class="sxs-lookup"><span data-stu-id="7d394-136">`Guid` (not returned in SQL Server 2000)</span></span>|

<span data-ttu-id="7d394-137">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="7d394-137">**Return Value**</span></span>

<span data-ttu-id="7d394-138">An `Int64`.</span><span class="sxs-lookup"><span data-stu-id="7d394-138">An `Int64`.</span></span>

<span data-ttu-id="7d394-139">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="7d394-139">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNTBIG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_countbig)]

## <a name="maxexpression"></a><span data-ttu-id="7d394-140">MAX(wyrażenie)</span><span class="sxs-lookup"><span data-stu-id="7d394-140">MAX(expression)</span></span>

<span data-ttu-id="7d394-141">Zwraca maksymalną wartość kolekcji.</span><span class="sxs-lookup"><span data-stu-id="7d394-141">Returns the maximum value the collection.</span></span>

<span data-ttu-id="7d394-142">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="7d394-142">**Arguments**</span></span>

<span data-ttu-id="7d394-143">Kolekcja(T), gdzie T jest jednym z następujących typów:</span><span class="sxs-lookup"><span data-stu-id="7d394-143">A Collection(T), where T is one of the following types:</span></span>

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

<span data-ttu-id="7d394-144">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="7d394-144">**Return Value**</span></span>

<span data-ttu-id="7d394-145">Typ . `expression`</span><span class="sxs-lookup"><span data-stu-id="7d394-145">The type of `expression`.</span></span>

<span data-ttu-id="7d394-146">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="7d394-146">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_MAX](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_max)]

## <a name="minexpression"></a><span data-ttu-id="7d394-147">MIN(wyrażenie)</span><span class="sxs-lookup"><span data-stu-id="7d394-147">MIN(expression)</span></span>

<span data-ttu-id="7d394-148">Zwraca minimalną wartość w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="7d394-148">Returns the minimum value in a collection.</span></span>

<span data-ttu-id="7d394-149">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="7d394-149">**Arguments**</span></span>

<span data-ttu-id="7d394-150">Kolekcja(T), gdzie T jest jednym z następujących typów:</span><span class="sxs-lookup"><span data-stu-id="7d394-150">A Collection(T), where T is one of the following types:</span></span>

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

<span data-ttu-id="7d394-151">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="7d394-151">**Return Value**</span></span>

<span data-ttu-id="7d394-152">Typ . `expression`</span><span class="sxs-lookup"><span data-stu-id="7d394-152">The type of `expression`.</span></span>

<span data-ttu-id="7d394-153">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="7d394-153">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_MIN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_min)]

## <a name="stdevexpression"></a><span data-ttu-id="7d394-154">STDEV(wyrażenie)</span><span class="sxs-lookup"><span data-stu-id="7d394-154">STDEV(expression)</span></span>

<span data-ttu-id="7d394-155">Zwraca statystyczne odchylenie standardowe wszystkich wartości w określonym wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="7d394-155">Returns the statistical standard deviation of all values in the specified expression.</span></span>

<span data-ttu-id="7d394-156">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="7d394-156">**Arguments**</span></span>

<span data-ttu-id="7d394-157">Kolekcja(`Double`).</span><span class="sxs-lookup"><span data-stu-id="7d394-157">A Collection(`Double`).</span></span>

<span data-ttu-id="7d394-158">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="7d394-158">**Return Value**</span></span>

<span data-ttu-id="7d394-159">Klasa `Double`.</span><span class="sxs-lookup"><span data-stu-id="7d394-159">A `Double`.</span></span>

<span data-ttu-id="7d394-160">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="7d394-160">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEV](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdev)]

## <a name="stdevpexpression"></a><span data-ttu-id="7d394-161">STDEVP(wyrażenie)</span><span class="sxs-lookup"><span data-stu-id="7d394-161">STDEVP(expression)</span></span>

<span data-ttu-id="7d394-162">Zwraca statystyczne odchylenie standardowe dla populacji dla wszystkich wartości w określonym wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="7d394-162">Returns the statistical standard deviation for the population for all values in the specified expression.</span></span>

<span data-ttu-id="7d394-163">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="7d394-163">**Arguments**</span></span>

<span data-ttu-id="7d394-164">Kolekcja(`Double`).</span><span class="sxs-lookup"><span data-stu-id="7d394-164">A Collection(`Double`).</span></span>

<span data-ttu-id="7d394-165">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="7d394-165">**Return Value**</span></span>

<span data-ttu-id="7d394-166">Klasa `Double`.</span><span class="sxs-lookup"><span data-stu-id="7d394-166">A `Double`.</span></span>

<span data-ttu-id="7d394-167">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="7d394-167">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEVP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdevp)]

## <a name="sumexpression"></a><span data-ttu-id="7d394-168">SUMA(wyrażenie)</span><span class="sxs-lookup"><span data-stu-id="7d394-168">SUM(expression)</span></span>

<span data-ttu-id="7d394-169">Zwraca sumę wszystkich wartości w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="7d394-169">Returns the sum of all the values in the collection.</span></span>

<span data-ttu-id="7d394-170">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="7d394-170">**Arguments**</span></span>

<span data-ttu-id="7d394-171">Kolekcja(T), gdzie T jest jednym z `Int32` `Int64`następujących `Double` `Decimal`typów: , , .</span><span class="sxs-lookup"><span data-stu-id="7d394-171">A Collection(T) where T is one of the following types: `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="7d394-172">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="7d394-172">**Return Value**</span></span>

<span data-ttu-id="7d394-173">Typ . `expression`</span><span class="sxs-lookup"><span data-stu-id="7d394-173">The type of `expression`.</span></span>

<span data-ttu-id="7d394-174">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="7d394-174">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_SUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_sum)]

## <a name="varexpression"></a><span data-ttu-id="7d394-175">VAR(wyrażenie)</span><span class="sxs-lookup"><span data-stu-id="7d394-175">VAR(expression)</span></span>

<span data-ttu-id="7d394-176">Zwraca wariancję statystyczną wszystkich wartości w określonym wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="7d394-176">Returns the statistical variance of all values in the specified expression.</span></span>

<span data-ttu-id="7d394-177">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="7d394-177">**Arguments**</span></span>

<span data-ttu-id="7d394-178">Kolekcja(`Double`).</span><span class="sxs-lookup"><span data-stu-id="7d394-178">A Collection(`Double`).</span></span>

<span data-ttu-id="7d394-179">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="7d394-179">**Return Value**</span></span>

<span data-ttu-id="7d394-180">Klasa `Double`.</span><span class="sxs-lookup"><span data-stu-id="7d394-180">A `Double`.</span></span>

<span data-ttu-id="7d394-181">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="7d394-181">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_VAR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_var)]

## <a name="varpexpression"></a><span data-ttu-id="7d394-182">WARIANCJA(wyrażenie)</span><span class="sxs-lookup"><span data-stu-id="7d394-182">VARP(expression)</span></span>

<span data-ttu-id="7d394-183">Zwraca wariancję statystyczną dla populacji dla wszystkich wartości w określonym wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="7d394-183">Returns the statistical variance for the population for all values in the specified expression.</span></span>

<span data-ttu-id="7d394-184">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="7d394-184">**Arguments**</span></span>

<span data-ttu-id="7d394-185">Kolekcja(`Double`).</span><span class="sxs-lookup"><span data-stu-id="7d394-185">A Collection(`Double`).</span></span>

<span data-ttu-id="7d394-186">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="7d394-186">**Return Value**</span></span>

<span data-ttu-id="7d394-187">Klasa `Double`.</span><span class="sxs-lookup"><span data-stu-id="7d394-187">A `Double`.</span></span>

<span data-ttu-id="7d394-188">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="7d394-188">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_VARP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_varp)]
  
## <a name="see-also"></a><span data-ttu-id="7d394-189">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7d394-189">See also</span></span>

- [<span data-ttu-id="7d394-190">Funkcje agregowane (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="7d394-190">Aggregate Functions (Transact-SQL)</span></span>](/sql/t-sql/functions/aggregate-functions-transact-sql)
- [<span data-ttu-id="7d394-191">Jednostki języka SQL</span><span class="sxs-lookup"><span data-stu-id="7d394-191">Entity SQL Language</span></span>](./language-reference/entity-sql-language.md)
- [<span data-ttu-id="7d394-192">Funkcje agregujące Canonical</span><span class="sxs-lookup"><span data-stu-id="7d394-192">Aggregate Canonical Functions</span></span>](./language-reference/aggregate-canonical-functions.md)
