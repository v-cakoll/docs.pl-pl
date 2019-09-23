---
title: Funkcje matematyczne
ms.date: 03/30/2017
ms.assetid: b040c7cb-156d-40f2-9152-61065b18148c
ms.openlocfilehash: 5e5658e28c7d806f7fd38f941bfa7254e7806e11
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182484"
---
# <a name="mathematical-functions"></a><span data-ttu-id="62ba7-102">Funkcje matematyczne</span><span class="sxs-lookup"><span data-stu-id="62ba7-102">Mathematical Functions</span></span>

<span data-ttu-id="62ba7-103">.NET Framework Dostawca danych for SQL Server (SqlClient) oferuje funkcje matematyczne, które wykonują obliczenia na wartościach wejściowych, które są podawane jako argumenty, i zwracają wynik wartości liczbowej.</span><span class="sxs-lookup"><span data-stu-id="62ba7-103">The .NET Framework Data Provider for SQL Server (SqlClient) provides math functions that perform calculations on input values that are provided as arguments, and return a numeric value result.</span></span> <span data-ttu-id="62ba7-104">Te funkcje znajdują się w przestrzeni nazw SqlServer, która jest dostępna w przypadku korzystania z programu SqlClient.</span><span class="sxs-lookup"><span data-stu-id="62ba7-104">These functions are in the SqlServer namespace, which is available when you use SqlClient.</span></span> <span data-ttu-id="62ba7-105">Właściwość przestrzeni nazw dostawcy umożliwia Entity Framework odnajdywania prefiksu używanego przez tego dostawcę dla określonych konstrukcji, takich jak typy i funkcje.</span><span class="sxs-lookup"><span data-stu-id="62ba7-105">A provider's namespace property allows the Entity Framework to discover which prefix is used by this provider for specific constructs, such as types and functions.</span></span> <span data-ttu-id="62ba7-106">W poniższej tabeli opisano funkcje matematyczne SqlClient.</span><span class="sxs-lookup"><span data-stu-id="62ba7-106">The following table describes the SqlClient math functions.</span></span>  
  
## <a name="absexpression"></a><span data-ttu-id="62ba7-107">ABS (wyrażenie)</span><span class="sxs-lookup"><span data-stu-id="62ba7-107">ABS(expression)</span></span>

<span data-ttu-id="62ba7-108">Wykonuje funkcję wartość bezwzględną.</span><span class="sxs-lookup"><span data-stu-id="62ba7-108">Performs the absolute value function.</span></span>

<span data-ttu-id="62ba7-109">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="62ba7-109">**Arguments**</span></span>

<span data-ttu-id="62ba7-110">`expression`: `Int32`, ,,`Double`Lub .`Decimal` `Int64`</span><span class="sxs-lookup"><span data-stu-id="62ba7-110">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="62ba7-111">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="62ba7-111">**Return Value**</span></span>

<span data-ttu-id="62ba7-112">Wartość bezwzględna określonego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="62ba7-112">The absolute value of the specified expression.</span></span>

<span data-ttu-id="62ba7-113">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="62ba7-113">**Example**</span></span>

`SqlServer.ABS(-2)`

## <a name="acosexpression"></a><span data-ttu-id="62ba7-114">ACOS (wyrażenie)</span><span class="sxs-lookup"><span data-stu-id="62ba7-114">ACOS(expression)</span></span>

<span data-ttu-id="62ba7-115">Zwraca wartość arcus cosinus określonego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="62ba7-115">Returns the arccosine value of the specified expression.</span></span>

<span data-ttu-id="62ba7-116">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="62ba7-116">**Arguments**</span></span>

<span data-ttu-id="62ba7-117">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="62ba7-117">`expression`: A `Double`.</span></span>

<span data-ttu-id="62ba7-118">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="62ba7-118">**Return Value**</span></span>

<span data-ttu-id="62ba7-119">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="62ba7-119">A `Double`.</span></span>

<span data-ttu-id="62ba7-120">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="62ba7-120">**Example**</span></span>

`SqlServer.ACOS(.9)`

## <a name="asinexpression"></a><span data-ttu-id="62ba7-121">ASIN (wyrażenie)</span><span class="sxs-lookup"><span data-stu-id="62ba7-121">ASIN(expression)</span></span>

<span data-ttu-id="62ba7-122">Zwraca wartość arcus sinus określonego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="62ba7-122">Returns the arcsine value of the specified expression.</span></span>

<span data-ttu-id="62ba7-123">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="62ba7-123">**Arguments**</span></span>

<span data-ttu-id="62ba7-124">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="62ba7-124">`expression`: A `Double`.</span></span>

<span data-ttu-id="62ba7-125">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="62ba7-125">**Return Value**</span></span>

<span data-ttu-id="62ba7-126">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="62ba7-126">A `Double`.</span></span>

<span data-ttu-id="62ba7-127">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="62ba7-127">**Example**</span></span>

`SqlServer.ASIN(.9)`

## <a name="atanexpression"></a><span data-ttu-id="62ba7-128">ATAN (wyrażenie)</span><span class="sxs-lookup"><span data-stu-id="62ba7-128">ATAN(expression)</span></span>

<span data-ttu-id="62ba7-129">Zwraca wartość arcus tangens określonego wyrażenia liczbowego.</span><span class="sxs-lookup"><span data-stu-id="62ba7-129">Returns the arctangent value of the specified numeric expression.</span></span>

<span data-ttu-id="62ba7-130">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="62ba7-130">**Arguments**</span></span>

<span data-ttu-id="62ba7-131">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="62ba7-131">`expression`: A `Double`.</span></span>

<span data-ttu-id="62ba7-132">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="62ba7-132">**Return Value**</span></span>

<span data-ttu-id="62ba7-133">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="62ba7-133">A `Double`.</span></span>

<span data-ttu-id="62ba7-134">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="62ba7-134">**Example**</span></span>

`SqlServer.ATAN(9)`

## <a name="atn2expression-expression"></a><span data-ttu-id="62ba7-135">ATN2 (wyrażenie, wyrażenie)</span><span class="sxs-lookup"><span data-stu-id="62ba7-135">ATN2(expression, expression)</span></span>

<span data-ttu-id="62ba7-136">Zwraca kąt w radianach, którego tangens jest między dwoma określonymi wyrażeniami liczbowymi.</span><span class="sxs-lookup"><span data-stu-id="62ba7-136">Returns the angle, in radians, whose tangent is between the two specified numeric expressions.</span></span>

<span data-ttu-id="62ba7-137">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="62ba7-137">**Arguments**</span></span>

<span data-ttu-id="62ba7-138">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="62ba7-138">`expression`: A `Double`.</span></span>

<span data-ttu-id="62ba7-139">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="62ba7-139">**Return Value**</span></span>

<span data-ttu-id="62ba7-140">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="62ba7-140">A `Double`.</span></span>

<span data-ttu-id="62ba7-141">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="62ba7-141">**Example**</span></span>

`SqlServer.ATN2(9, 8)`
 
## <a name="ceilingexpression"></a><span data-ttu-id="62ba7-142">GÓRNy limit (wyrażenie)</span><span class="sxs-lookup"><span data-stu-id="62ba7-142">CEILING(expression)</span></span>

<span data-ttu-id="62ba7-143">Konwertuje określone wyrażenie na najmniejszą liczbę całkowitą, która jest większa lub równa.</span><span class="sxs-lookup"><span data-stu-id="62ba7-143">Converts the specified expression to the smallest integer that is greater than or equal to it.</span></span>

<span data-ttu-id="62ba7-144">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="62ba7-144">**Arguments**</span></span>

<span data-ttu-id="62ba7-145">`expression`: `Int32`, ,,`Double`Lub .`Decimal` `Int64`</span><span class="sxs-lookup"><span data-stu-id="62ba7-145">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="62ba7-146">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="62ba7-146">**Return Value**</span></span>

<span data-ttu-id="62ba7-147">`Int32`, ,,`Double`Lub .`Decimal` `Int64`</span><span class="sxs-lookup"><span data-stu-id="62ba7-147">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="62ba7-148">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="62ba7-148">**Example**</span></span> 

[!code-csharp[DP EntityServices Concepts#SQLSERVER_CEILING](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_ceiling)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_ceiling)]

## <a name="cosexpression"></a><span data-ttu-id="62ba7-149">COS (wyrażenie)</span><span class="sxs-lookup"><span data-stu-id="62ba7-149">COS(expression)</span></span>

<span data-ttu-id="62ba7-150">Oblicza cosinus kąta określony kąt w radianach.</span><span class="sxs-lookup"><span data-stu-id="62ba7-150">Calculates the trigonometric cosine of the specified angle in radians.</span></span> 

<span data-ttu-id="62ba7-151">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="62ba7-151">**Arguments**</span></span> 

<span data-ttu-id="62ba7-152">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="62ba7-152">`expression`: A `Double`.</span></span> 

<span data-ttu-id="62ba7-153">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="62ba7-153">**Return Value**</span></span> 

<span data-ttu-id="62ba7-154">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="62ba7-154">A `Double`.</span></span> 

<span data-ttu-id="62ba7-155">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="62ba7-155">**Example**</span></span> 

`SqlServer.COS(45)`

## <a name="cotexpression"></a><span data-ttu-id="62ba7-156">COT (wyrażenie)</span><span class="sxs-lookup"><span data-stu-id="62ba7-156">COT(expression)</span></span>

<span data-ttu-id="62ba7-157">Oblicza cotangens w postaci wartości kąta w radianach.</span><span class="sxs-lookup"><span data-stu-id="62ba7-157">Calculates the trigonometric cotangent of the specified angle in radians.</span></span> 

<span data-ttu-id="62ba7-158">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="62ba7-158">**Arguments**</span></span> 

<span data-ttu-id="62ba7-159">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="62ba7-159">`expression`: A `Double`.</span></span> 

<span data-ttu-id="62ba7-160">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="62ba7-160">**Return Value**</span></span> 

<span data-ttu-id="62ba7-161">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="62ba7-161">A `Double`.</span></span> 

<span data-ttu-id="62ba7-162">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="62ba7-162">**Example**</span></span> 

`SqlServer.COT(60)`
  
## <a name="degreesradians"></a><span data-ttu-id="62ba7-163">STOPnie (radiany)</span><span class="sxs-lookup"><span data-stu-id="62ba7-163">DEGREES(radians)</span></span>

<span data-ttu-id="62ba7-164">Zwraca odpowiedni kąt w stopniach.</span><span class="sxs-lookup"><span data-stu-id="62ba7-164">Returns the corresponding angle in degrees.</span></span> 

<span data-ttu-id="62ba7-165">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="62ba7-165">**Arguments**</span></span> 

<span data-ttu-id="62ba7-166">`expression`: `Int32`, ,,`Double`Lub .`Decimal` `Int64`</span><span class="sxs-lookup"><span data-stu-id="62ba7-166">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="62ba7-167">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="62ba7-167">**Return Value**</span></span> 

<span data-ttu-id="62ba7-168">`Int32`, ,,`Double`Lub .`Decimal` `Int64`</span><span class="sxs-lookup"><span data-stu-id="62ba7-168">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="62ba7-169">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="62ba7-169">**Example**</span></span> 

`SqlServer.DEGREES(3.1)`

## <a name="expexpression"></a><span data-ttu-id="62ba7-170">EXP (wyrażenie)</span><span class="sxs-lookup"><span data-stu-id="62ba7-170">EXP(expression)</span></span>

<span data-ttu-id="62ba7-171">Oblicza wartość wykładniczą określonego wyrażenia liczbowego.</span><span class="sxs-lookup"><span data-stu-id="62ba7-171">Calculates the exponential value of a specified numeric expression.</span></span> 

<span data-ttu-id="62ba7-172">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="62ba7-172">**Arguments**</span></span> 

<span data-ttu-id="62ba7-173">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="62ba7-173">`expression`: A `Double`.</span></span> 

<span data-ttu-id="62ba7-174">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="62ba7-174">**Return Value**</span></span> 

<span data-ttu-id="62ba7-175">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="62ba7-175">A `Double`.</span></span> 

<span data-ttu-id="62ba7-176">**Przykład**`SqlServer.EXP(1)`</span><span class="sxs-lookup"><span data-stu-id="62ba7-176">**Example** `SqlServer.EXP(1)`</span></span>

## <a name="floorexpression"></a><span data-ttu-id="62ba7-177">FLOOR (wyrażenie)</span><span class="sxs-lookup"><span data-stu-id="62ba7-177">FLOOR(expression)</span></span>

<span data-ttu-id="62ba7-178">Konwertuje określone wyrażenie na największą liczbę całkowitą mniejszą lub równą.</span><span class="sxs-lookup"><span data-stu-id="62ba7-178">Converts the specified expression to the largest integer less than or equal to it.</span></span> 

<span data-ttu-id="62ba7-179">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="62ba7-179">**Arguments**</span></span> 

<span data-ttu-id="62ba7-180">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="62ba7-180">`expression`: A `Double`.</span></span> 

<span data-ttu-id="62ba7-181">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="62ba7-181">**Return Value**</span></span> 

<span data-ttu-id="62ba7-182">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="62ba7-182">A `Double`.</span></span> 

<span data-ttu-id="62ba7-183">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="62ba7-183">**Example**</span></span> 

[!code-csharp[DP EntityServices Concepts#SQLSERVER_FLOOR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_floor)] 
[!code-sql[DP EntityServices Concepts#SQLSERVER_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_floor)]

## <a name="logexpression"></a><span data-ttu-id="62ba7-184">Dziennik (wyrażenie)</span><span class="sxs-lookup"><span data-stu-id="62ba7-184">LOG(expression)</span></span>

<span data-ttu-id="62ba7-185">Oblicza logarytm naturalny określonego `float` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="62ba7-185">Calculates the natural logarithm of the specified `float` expression.</span></span> 

<span data-ttu-id="62ba7-186">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="62ba7-186">**Arguments**</span></span> 

<span data-ttu-id="62ba7-187">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="62ba7-187">`expression`: A `Double`.</span></span> 

<span data-ttu-id="62ba7-188">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="62ba7-188">**Return Value**</span></span> 

<span data-ttu-id="62ba7-189">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="62ba7-189">A `Double`.</span></span> 

<span data-ttu-id="62ba7-190">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="62ba7-190">**Example**</span></span> 

`SqlServer.LOG(100)`

## <a name="log10expression"></a><span data-ttu-id="62ba7-191">LOG10 — (wyrażenie)</span><span class="sxs-lookup"><span data-stu-id="62ba7-191">LOG10(expression)</span></span>

<span data-ttu-id="62ba7-192">Zwraca logarytm dziesiętny dla podanego `Double` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="62ba7-192">Returns the base-10 logarithm of the specified `Double` expression.</span></span> 

<span data-ttu-id="62ba7-193">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="62ba7-193">**Arguments**</span></span> 

<span data-ttu-id="62ba7-194">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="62ba7-194">`expression`: A `Double`.</span></span> 

<span data-ttu-id="62ba7-195">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="62ba7-195">**Return Value**</span></span> 

<span data-ttu-id="62ba7-196">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="62ba7-196">A `Double`.</span></span> 

<span data-ttu-id="62ba7-197">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="62ba7-197">**Example**</span></span> 

`SqlServer.LOG10(100)`

## <a name="pi"></a><span data-ttu-id="62ba7-198">PI()</span><span class="sxs-lookup"><span data-stu-id="62ba7-198">PI()</span></span>

<span data-ttu-id="62ba7-199">Zwraca wartość stałą liczby pi jako `Double`.</span><span class="sxs-lookup"><span data-stu-id="62ba7-199">Returns the constant value of pi as a `Double`.</span></span> 

<span data-ttu-id="62ba7-200">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="62ba7-200">**Return Value**</span></span> 

<span data-ttu-id="62ba7-201">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="62ba7-201">A `Double`.</span></span> 

<span data-ttu-id="62ba7-202">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="62ba7-202">**Example**</span></span> 

`SqlServer.PI()`

## <a name="powernumeric_expression-power_expression"></a><span data-ttu-id="62ba7-203">Energia (numeric_expression, power_expression)</span><span class="sxs-lookup"><span data-stu-id="62ba7-203">POWER(numeric_expression, power_expression)</span></span>

<span data-ttu-id="62ba7-204">Oblicza wartość określonego wyrażenia do określonej potęgi.</span><span class="sxs-lookup"><span data-stu-id="62ba7-204">Calculates the value of a specified expression to a specified power.</span></span>

<span data-ttu-id="62ba7-205">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="62ba7-205">**Arguments**</span></span> 

|  |  |
|--|--|
|`numeric_expression`| <span data-ttu-id="62ba7-206">`Int32`, ,,`Double`Lub .`Decimal` `Int64`</span><span class="sxs-lookup"><span data-stu-id="62ba7-206">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>|
|`power_expression`| <span data-ttu-id="62ba7-207">Reprezentuje moc, do której należy `numeric_expression`podnieść. `Double`</span><span class="sxs-lookup"><span data-stu-id="62ba7-207">A `Double` that represents the power to which to raise the `numeric_expression`.</span></span>| 

<span data-ttu-id="62ba7-208">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="62ba7-208">**Return Value**</span></span> 

<span data-ttu-id="62ba7-209">Wartość określonego `numeric_expression` `power_expression`elementu.</span><span class="sxs-lookup"><span data-stu-id="62ba7-209">The value of the specified `numeric_expression` to the specified `power_expression`.</span></span> 

<span data-ttu-id="62ba7-210">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="62ba7-210">**Example**</span></span> 

`SqlServer.POWER(2,7)`

## <a name="radiansexpression"></a><span data-ttu-id="62ba7-211">RADIANy (wyrażenie)</span><span class="sxs-lookup"><span data-stu-id="62ba7-211">RADIANS(expression)</span></span>

<span data-ttu-id="62ba7-212">Konwertuje stopnie na radiany.</span><span class="sxs-lookup"><span data-stu-id="62ba7-212">Converts degrees to radians.</span></span> 

<span data-ttu-id="62ba7-213">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="62ba7-213">**Arguments**</span></span> 

<span data-ttu-id="62ba7-214">`expression`: `Int32`, ,,`Double`Lub .`Decimal` `Int64`</span><span class="sxs-lookup"><span data-stu-id="62ba7-214">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="62ba7-215">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="62ba7-215">**Return Value**</span></span> 

<span data-ttu-id="62ba7-216">`Int32`, ,,`Double`Lub .`Decimal` `Int64`</span><span class="sxs-lookup"><span data-stu-id="62ba7-216">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="62ba7-217">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="62ba7-217">**Example**</span></span> 

`SqlServer.RADIANS(360.0)`

## <a name="randseed"></a><span data-ttu-id="62ba7-218">RAND ([inicjator])</span><span class="sxs-lookup"><span data-stu-id="62ba7-218">RAND([seed])</span></span>

<span data-ttu-id="62ba7-219">Zwraca losową wartość z przewartości od 0 do 1.</span><span class="sxs-lookup"><span data-stu-id="62ba7-219">Returns a random value from 0 through 1.</span></span> 

<span data-ttu-id="62ba7-220">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="62ba7-220">**Arguments**</span></span> 

<span data-ttu-id="62ba7-221">Wartość inicjatora jako `Int32`.</span><span class="sxs-lookup"><span data-stu-id="62ba7-221">The seed value as an `Int32`.</span></span> <span data-ttu-id="62ba7-222">Jeśli inicjator nie zostanie określony, aparat bazy danych SQL Server w losowo przypisze wartość inicjatora.</span><span class="sxs-lookup"><span data-stu-id="62ba7-222">If the seed is not specified, the SQL Server Database Engine assigns a seed value at random.</span></span> <span data-ttu-id="62ba7-223">W przypadku określonej wartości inicjatora zwrócony wynik jest zawsze taki sam.</span><span class="sxs-lookup"><span data-stu-id="62ba7-223">For a specified seed value, the result returned is always the same.</span></span>

<span data-ttu-id="62ba7-224">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="62ba7-224">**Return Value**</span></span> 

<span data-ttu-id="62ba7-225">Wartość losowa `Double` od 0 do 1.</span><span class="sxs-lookup"><span data-stu-id="62ba7-225">A random `Double` value from 0 through 1.</span></span> 

<span data-ttu-id="62ba7-226">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="62ba7-226">**Example**</span></span> 

`SqlServer.RAND()`
  
## <a name="roundnumeric_expression-lengthfunction"></a><span data-ttu-id="62ba7-227">ROUND (numeric_expression, Length [, funkcja])</span><span class="sxs-lookup"><span data-stu-id="62ba7-227">ROUND(numeric_expression, length[,function])</span></span>

<span data-ttu-id="62ba7-228">Zwraca wyrażenie liczbowe zaokrąglone do określonej długości lub dokładności.</span><span class="sxs-lookup"><span data-stu-id="62ba7-228">Returns a numeric expression, rounded to the specified length or precision.</span></span> 

<span data-ttu-id="62ba7-229">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="62ba7-229">**Arguments**</span></span> 

|  |  |
|--|--|
|`numeric_expression`| <span data-ttu-id="62ba7-230">`Int32`, ,,`Double`Lub .`Decimal` `Int64`</span><span class="sxs-lookup"><span data-stu-id="62ba7-230">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 
|`length`| <span data-ttu-id="62ba7-231">Reprezentuje precyzję, do której `numeric_expression` ma zostać zaokrąglona wartość. `Int32`</span><span class="sxs-lookup"><span data-stu-id="62ba7-231">An `Int32` that represents the precision to which `numeric_expression` is to be rounded.</span></span> <span data-ttu-id="62ba7-232">Gdy `length` jest liczbą dodatnią, `numeric_expression` jest zaokrąglana do liczby pozycji dziesiętnych określonych przez `length`.</span><span class="sxs-lookup"><span data-stu-id="62ba7-232">When `length` is a positive number, `numeric_expression` is rounded to the number of decimal positions specified by `length`.</span></span> <span data-ttu-id="62ba7-233">Gdy `length` jest liczbą ujemną, `numeric_expression` jest zaokrąglana po lewej stronie przecinka dziesiętnego, zgodnie z opisem w `length`.</span><span class="sxs-lookup"><span data-stu-id="62ba7-233">When `length` is a negative number, `numeric_expression` is rounded on the left side of the decimal point, as specified by `length`.</span></span>|
|`function` | <span data-ttu-id="62ba7-234">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="62ba7-234">Optional.</span></span> <span data-ttu-id="62ba7-235">`Int32` Reprezentuje typ operacji do wykonania.</span><span class="sxs-lookup"><span data-stu-id="62ba7-235">An `Int32` that represents the type of operation to perform.</span></span> <span data-ttu-id="62ba7-236">Gdy funkcja jest pomijana lub ma wartość 0 (domyślnie), `numeric_expression` jest zaokrąglana.</span><span class="sxs-lookup"><span data-stu-id="62ba7-236">When function is omitted or has a value of 0 (default), `numeric_expression` is rounded.</span></span> <span data-ttu-id="62ba7-237">Gdy określona jest wartość inna niż 0, `numeric_expression` zostanie obcięta.</span><span class="sxs-lookup"><span data-stu-id="62ba7-237">When a value other than 0 is specified, `numeric_expression` is truncated.</span></span> |

<span data-ttu-id="62ba7-238">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="62ba7-238">**Return Value**</span></span> 

<span data-ttu-id="62ba7-239">Wartość określonego `numeric_expression` `power_expression`elementu.</span><span class="sxs-lookup"><span data-stu-id="62ba7-239">The value of the specified `numeric_expression` to the specified `power_expression`.</span></span>

<span data-ttu-id="62ba7-240">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="62ba7-240">**Example**</span></span> 

`SqlServer.ROUND(748.58, -3)`

## <a name="signexpression"></a><span data-ttu-id="62ba7-241">SIGN (wyrażenie)</span><span class="sxs-lookup"><span data-stu-id="62ba7-241">SIGN(expression)</span></span> 

<span data-ttu-id="62ba7-242">Zwraca wartość dodatnią (+ 1), zero (0) lub ujemną (-1) znak podanego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="62ba7-242">Returns the positive (+1), zero (0), or negative (-1) sign of the specified expression.</span></span> 

<span data-ttu-id="62ba7-243">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="62ba7-243">**Arguments**</span></span> 

<span data-ttu-id="62ba7-244">`expression`: `Int32`, `Int64`, lub`Double``Decimal`</span><span class="sxs-lookup"><span data-stu-id="62ba7-244">`expression`: `Int32`, `Int64`, `Double`, or `Decimal`</span></span> 

<span data-ttu-id="62ba7-245">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="62ba7-245">**Return Value**</span></span> 

<span data-ttu-id="62ba7-246">`Int32`, ,,`Double`Lub .`Decimal` `Int64`</span><span class="sxs-lookup"><span data-stu-id="62ba7-246">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="62ba7-247">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="62ba7-247">**Example**</span></span> 

`SqlServer.SIGN(-10)`

## <a name="sinexpression"></a><span data-ttu-id="62ba7-248">SIN (wyrażenie)</span><span class="sxs-lookup"><span data-stu-id="62ba7-248">SIN(expression)</span></span>

<span data-ttu-id="62ba7-249">Oblicza sinus kątów o określonym kącie w radianach i zwraca `Double` wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="62ba7-249">Calculates the trigonometric sine of the specified angle in radians, and returns a `Double` expression.</span></span> 

<span data-ttu-id="62ba7-250">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="62ba7-250">**Arguments**</span></span> 

<span data-ttu-id="62ba7-251">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="62ba7-251">`expression`: A `Double`.</span></span> 

<span data-ttu-id="62ba7-252">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="62ba7-252">**Return Value**</span></span> 

<span data-ttu-id="62ba7-253">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="62ba7-253">A `Double`.</span></span> 

<span data-ttu-id="62ba7-254">**Przykład**`SqlServer.SIN(20)`</span><span class="sxs-lookup"><span data-stu-id="62ba7-254">**Example** `SqlServer.SIN(20)`</span></span>

## <a name="sqrtexpression"></a><span data-ttu-id="62ba7-255">SQRT (wyrażenie)</span><span class="sxs-lookup"><span data-stu-id="62ba7-255">SQRT(expression)</span></span>

<span data-ttu-id="62ba7-256">Zwraca pierwiastek kwadratowy z podanego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="62ba7-256">Returns the square root of the specified expression.</span></span> 

<span data-ttu-id="62ba7-257">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="62ba7-257">**Arguments**</span></span> 

<span data-ttu-id="62ba7-258">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="62ba7-258">`expression`: A `Double`.</span></span> 

<span data-ttu-id="62ba7-259">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="62ba7-259">**Return Value**</span></span> 

<span data-ttu-id="62ba7-260">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="62ba7-260">A `Double`.</span></span> 

<span data-ttu-id="62ba7-261">**Przykład**`SqlServer.SQRT(3600)`</span><span class="sxs-lookup"><span data-stu-id="62ba7-261">**Example** `SqlServer.SQRT(3600)`</span></span>

## <a name="squareexpression"></a><span data-ttu-id="62ba7-262">KWADRAT (wyrażenie)</span><span class="sxs-lookup"><span data-stu-id="62ba7-262">SQUARE(expression)</span></span>

<span data-ttu-id="62ba7-263">Zwraca kwadrat z podanego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="62ba7-263">Returns the square of the specified expression.</span></span> 

<span data-ttu-id="62ba7-264">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="62ba7-264">**Arguments**</span></span> 

<span data-ttu-id="62ba7-265">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="62ba7-265">`expression`: A `Double`.</span></span> 

<span data-ttu-id="62ba7-266">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="62ba7-266">**Return Value**</span></span> 

<span data-ttu-id="62ba7-267">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="62ba7-267">A `Double`.</span></span> 

<span data-ttu-id="62ba7-268">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="62ba7-268">**Example**</span></span> 

`SqlServer.SQUARE(25)`

## <a name="tanexpression"></a><span data-ttu-id="62ba7-269">TAN (wyrażenie)</span><span class="sxs-lookup"><span data-stu-id="62ba7-269">TAN(expression)</span></span>

<span data-ttu-id="62ba7-270">Oblicza tangens podanego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="62ba7-270">Calculates the tangent of a specified expression.</span></span>

<span data-ttu-id="62ba7-271">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="62ba7-271">**Arguments**</span></span> 

<span data-ttu-id="62ba7-272">`expression`: `Double`</span><span class="sxs-lookup"><span data-stu-id="62ba7-272">`expression`: `Double`</span></span> 

<span data-ttu-id="62ba7-273">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="62ba7-273">**Return Value**</span></span> 

`Double` 

<span data-ttu-id="62ba7-274">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="62ba7-274">**Example**</span></span> 

`SqlServer.TAN(45.0)`
  
## <a name="see-also"></a><span data-ttu-id="62ba7-275">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="62ba7-275">See also</span></span>

<span data-ttu-id="62ba7-276">Aby uzyskać więcej informacji na temat funkcji matematycznych obsługiwanych przez program SqlClient, zapoznaj się z dokumentacją dla SQL Server wersji określonej w manifeście dostawcy SqlClient:</span><span class="sxs-lookup"><span data-stu-id="62ba7-276">For more information about the mathematical functions that SqlClient supports, see the documentation for the SQL Server version that you specified in the SqlClient provider manifest:</span></span>

- <span data-ttu-id="62ba7-277">**SQL Server 2005:** [Funkcje matematyczne (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms177516(v=sql.90))</span><span class="sxs-lookup"><span data-stu-id="62ba7-277">**SQL Server 2005:** [Mathematical Functions (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms177516(v=sql.90))</span></span>
- <span data-ttu-id="62ba7-278">**SQL Server 2008:** [Funkcje matematyczne (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms177516(v=sql.100))</span><span class="sxs-lookup"><span data-stu-id="62ba7-278">**SQL Server 2008:** [Mathematical Functions (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms177516(v=sql.100))</span></span>
- <span data-ttu-id="62ba7-279">**SQL Server 2012 i nowsze:** [Funkcje matematyczne (Transact-SQL)](/sql/t-sql/functions/mathematical-functions-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="62ba7-279">**SQL Server 2012 and later:** [Mathematical Functions (Transact-SQL)](/sql/t-sql/functions/mathematical-functions-transact-sql)</span></span>

- [<span data-ttu-id="62ba7-280">Klient SQL dla funkcji programu Entity Framework</span><span class="sxs-lookup"><span data-stu-id="62ba7-280">SqlClient for Entity Framework Functions</span></span>](sqlclient-for-ef-functions.md)
