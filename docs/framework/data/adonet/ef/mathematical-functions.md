---
title: Funkcje matematyczne
ms.date: 03/30/2017
ms.assetid: b040c7cb-156d-40f2-9152-61065b18148c
ms.openlocfilehash: d8d766cb1416a9a07476175364fe568d81fd9b25
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54652270"
---
# <a name="mathematical-functions"></a><span data-ttu-id="709ab-102">Funkcje matematyczne</span><span class="sxs-lookup"><span data-stu-id="709ab-102">Mathematical Functions</span></span>

<span data-ttu-id="709ab-103">.NET Framework Data Provider for SQL Server (SqlClient) zapewnia funkcje matematyczne, które wykonują obliczenia na wartości wejściowych, które są przekazywane jako argumenty i zwraca wynik wartość liczbową.</span><span class="sxs-lookup"><span data-stu-id="709ab-103">The .NET Framework Data Provider for SQL Server (SqlClient) provides math functions that perform calculations on input values that are provided as arguments, and return a numeric value result.</span></span> <span data-ttu-id="709ab-104">Te funkcje są w przestrzeni nazw SqlServer, który jest dostępny, gdy używasz SqlClient.</span><span class="sxs-lookup"><span data-stu-id="709ab-104">These functions are in the SqlServer namespace, which is available when you use SqlClient.</span></span> <span data-ttu-id="709ab-105">Właściwość przestrzeni nazw dostawcy umożliwia programu Entity Framework dowiedzieć się, który prefiks jest używany przez tego dostawcę dla określonego konstrukcji, takich jak typy i funkcje.</span><span class="sxs-lookup"><span data-stu-id="709ab-105">A provider's namespace property allows the Entity Framework to discover which prefix is used by this provider for specific constructs, such as types and functions.</span></span> <span data-ttu-id="709ab-106">W poniższej tabeli opisano funkcje matematyczne SqlClient.</span><span class="sxs-lookup"><span data-stu-id="709ab-106">The following table describes the SqlClient math functions.</span></span>  
  
## <a name="absexpression"></a><span data-ttu-id="709ab-107">ABS(Expression)</span><span class="sxs-lookup"><span data-stu-id="709ab-107">ABS(expression)</span></span>

<span data-ttu-id="709ab-108">Wykonuje funkcję wartości bezwzględnej.</span><span class="sxs-lookup"><span data-stu-id="709ab-108">Performs the absolute value function.</span></span>

<span data-ttu-id="709ab-109">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="709ab-109">**Arguments**</span></span>

<span data-ttu-id="709ab-110">`expression`: `Int32`, `Int64`, `Double`, Lub `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="709ab-110">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="709ab-111">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="709ab-111">**Return Value**</span></span>

<span data-ttu-id="709ab-112">Wartość bezwzględna z określonego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="709ab-112">The absolute value of the specified expression.</span></span>

<span data-ttu-id="709ab-113">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="709ab-113">**Example**</span></span>

`SqlServer.ABS(-2)`

## <a name="acosexpression"></a><span data-ttu-id="709ab-114">ACOS(Expression)</span><span class="sxs-lookup"><span data-stu-id="709ab-114">ACOS(expression)</span></span>

<span data-ttu-id="709ab-115">Zwraca arcus cosinus wartości podanego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="709ab-115">Returns the arccosine value of the specified expression.</span></span>

<span data-ttu-id="709ab-116">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="709ab-116">**Arguments**</span></span>

<span data-ttu-id="709ab-117">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="709ab-117">`expression`: A `Double`.</span></span>

<span data-ttu-id="709ab-118">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="709ab-118">**Return Value**</span></span>

<span data-ttu-id="709ab-119">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="709ab-119">A `Double`.</span></span>

<span data-ttu-id="709ab-120">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="709ab-120">**Example**</span></span>

`SqlServer.ACOS(.9)`

## <a name="asinexpression"></a><span data-ttu-id="709ab-121">ASIN(Expression)</span><span class="sxs-lookup"><span data-stu-id="709ab-121">ASIN(expression)</span></span>

<span data-ttu-id="709ab-122">Zwraca arcus sinus wartości podanego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="709ab-122">Returns the arcsine value of the specified expression.</span></span>

<span data-ttu-id="709ab-123">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="709ab-123">**Arguments**</span></span>

<span data-ttu-id="709ab-124">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="709ab-124">`expression`: A `Double`.</span></span>

<span data-ttu-id="709ab-125">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="709ab-125">**Return Value**</span></span>

<span data-ttu-id="709ab-126">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="709ab-126">A `Double`.</span></span>

<span data-ttu-id="709ab-127">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="709ab-127">**Example**</span></span>

`SqlServer.ASIN(.9)`

## <a name="atanexpression"></a><span data-ttu-id="709ab-128">ATAN(Expression)</span><span class="sxs-lookup"><span data-stu-id="709ab-128">ATAN(expression)</span></span>

<span data-ttu-id="709ab-129">Zwraca arcus tangens wartości podanego wyrażenia liczbowego.</span><span class="sxs-lookup"><span data-stu-id="709ab-129">Returns the arctangent value of the specified numeric expression.</span></span>

<span data-ttu-id="709ab-130">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="709ab-130">**Arguments**</span></span>

<span data-ttu-id="709ab-131">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="709ab-131">`expression`: A `Double`.</span></span>

<span data-ttu-id="709ab-132">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="709ab-132">**Return Value**</span></span>

<span data-ttu-id="709ab-133">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="709ab-133">A `Double`.</span></span>

<span data-ttu-id="709ab-134">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="709ab-134">**Example**</span></span>

`SqlServer.ATAN(9)`

## <a name="atn2expression-expression"></a><span data-ttu-id="709ab-135">ATN2(Expression, Expression)</span><span class="sxs-lookup"><span data-stu-id="709ab-135">ATN2(expression, expression)</span></span>

<span data-ttu-id="709ab-136">Zwraca kąt w radianach, którego tangens jest między dwoma określonych wyrażeń liczbowych.</span><span class="sxs-lookup"><span data-stu-id="709ab-136">Returns the angle, in radians, whose tangent is between the two specified numeric expressions.</span></span>

<span data-ttu-id="709ab-137">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="709ab-137">**Arguments**</span></span>

<span data-ttu-id="709ab-138">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="709ab-138">`expression`: A `Double`.</span></span>

<span data-ttu-id="709ab-139">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="709ab-139">**Return Value**</span></span>

<span data-ttu-id="709ab-140">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="709ab-140">A `Double`.</span></span>

<span data-ttu-id="709ab-141">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="709ab-141">**Example**</span></span>

`SqlServer.ATN2(9, 8)`
 
## <a name="ceilingexpression"></a><span data-ttu-id="709ab-142">CEILING(Expression)</span><span class="sxs-lookup"><span data-stu-id="709ab-142">CEILING(expression)</span></span>

<span data-ttu-id="709ab-143">Konwertuje określony wyrażenie najmniejsza liczba całkowita, która jest większa niż lub równą jej.</span><span class="sxs-lookup"><span data-stu-id="709ab-143">Converts the specified expression to the smallest integer that is greater than or equal to it.</span></span>

<span data-ttu-id="709ab-144">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="709ab-144">**Arguments**</span></span>

<span data-ttu-id="709ab-145">`expression`: `Int32`, `Int64`, `Double`, Lub `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="709ab-145">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="709ab-146">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="709ab-146">**Return Value**</span></span>

<span data-ttu-id="709ab-147">`Int32`, `Int64`, `Double`, Lub `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="709ab-147">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="709ab-148">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="709ab-148">**Example**</span></span> 

[!code-csharp[DP EntityServices Concepts#SQLSERVER_CEILING](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_ceiling)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_ceiling)]

## <a name="cosexpression"></a><span data-ttu-id="709ab-149">COS(Expression)</span><span class="sxs-lookup"><span data-stu-id="709ab-149">COS(expression)</span></span>

<span data-ttu-id="709ab-150">Oblicza trygonometrycznych cosinus określonego kąta podany w radianach.</span><span class="sxs-lookup"><span data-stu-id="709ab-150">Calculates the trigonometric cosine of the specified angle in radians.</span></span> 

<span data-ttu-id="709ab-151">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="709ab-151">**Arguments**</span></span> 

<span data-ttu-id="709ab-152">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="709ab-152">`expression`: A `Double`.</span></span> 

<span data-ttu-id="709ab-153">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="709ab-153">**Return Value**</span></span> 

<span data-ttu-id="709ab-154">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="709ab-154">A `Double`.</span></span> 

<span data-ttu-id="709ab-155">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="709ab-155">**Example**</span></span> 

`SqlServer.COS(45)`

## <a name="cotexpression"></a><span data-ttu-id="709ab-156">COT(Expression)</span><span class="sxs-lookup"><span data-stu-id="709ab-156">COT(expression)</span></span>

<span data-ttu-id="709ab-157">Oblicza trygonometrycznych cotangens kąta określonego w radianach.</span><span class="sxs-lookup"><span data-stu-id="709ab-157">Calculates the trigonometric cotangent of the specified angle in radians.</span></span> 

<span data-ttu-id="709ab-158">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="709ab-158">**Arguments**</span></span> 

<span data-ttu-id="709ab-159">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="709ab-159">`expression`: A `Double`.</span></span> 

<span data-ttu-id="709ab-160">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="709ab-160">**Return Value**</span></span> 

<span data-ttu-id="709ab-161">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="709ab-161">A `Double`.</span></span> 

<span data-ttu-id="709ab-162">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="709ab-162">**Example**</span></span> 

`SqlServer.COT(60)`
  
## <a name="degreesradians"></a><span data-ttu-id="709ab-163">DEGREES(RADIANS)</span><span class="sxs-lookup"><span data-stu-id="709ab-163">DEGREES(radians)</span></span>

<span data-ttu-id="709ab-164">Zwraca odpowiedni kąt w stopniach.</span><span class="sxs-lookup"><span data-stu-id="709ab-164">Returns the corresponding angle in degrees.</span></span> 

<span data-ttu-id="709ab-165">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="709ab-165">**Arguments**</span></span> 

<span data-ttu-id="709ab-166">`expression`: `Int32`, `Int64`, `Double`, Lub `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="709ab-166">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="709ab-167">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="709ab-167">**Return Value**</span></span> 

<span data-ttu-id="709ab-168">`Int32`, `Int64`, `Double`, Lub `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="709ab-168">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="709ab-169">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="709ab-169">**Example**</span></span> 

`SqlServer.DEGREES(3.1)`

## <a name="expexpression"></a><span data-ttu-id="709ab-170">EXP(Expression)</span><span class="sxs-lookup"><span data-stu-id="709ab-170">EXP(expression)</span></span>

<span data-ttu-id="709ab-171">Oblicza wartość wykładniczą określonego wyrażenia liczbowego.</span><span class="sxs-lookup"><span data-stu-id="709ab-171">Calculates the exponential value of a specified numeric expression.</span></span> 

<span data-ttu-id="709ab-172">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="709ab-172">**Arguments**</span></span> 

<span data-ttu-id="709ab-173">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="709ab-173">`expression`: A `Double`.</span></span> 

<span data-ttu-id="709ab-174">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="709ab-174">**Return Value**</span></span> 

<span data-ttu-id="709ab-175">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="709ab-175">A `Double`.</span></span> 

<span data-ttu-id="709ab-176">**Przykład** `SqlServer.EXP(1)`</span><span class="sxs-lookup"><span data-stu-id="709ab-176">**Example** `SqlServer.EXP(1)`</span></span>

## <a name="floorexpression"></a><span data-ttu-id="709ab-177">FLOOR(Expression)</span><span class="sxs-lookup"><span data-stu-id="709ab-177">FLOOR(expression)</span></span>

<span data-ttu-id="709ab-178">Konwertuje określony wyrażenie największą liczbą całkowitą mniejszą lub równą jej.</span><span class="sxs-lookup"><span data-stu-id="709ab-178">Converts the specified expression to the largest integer less than or equal to it.</span></span> 

<span data-ttu-id="709ab-179">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="709ab-179">**Arguments**</span></span> 

<span data-ttu-id="709ab-180">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="709ab-180">`expression`: A `Double`.</span></span> 

<span data-ttu-id="709ab-181">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="709ab-181">**Return Value**</span></span> 

<span data-ttu-id="709ab-182">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="709ab-182">A `Double`.</span></span> 

<span data-ttu-id="709ab-183">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="709ab-183">**Example**</span></span> 

[!code-csharp[DP EntityServices Concepts#SQLSERVER_FLOOR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_floor)] 
[!code-sql[DP EntityServices Concepts#SQLSERVER_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_floor)]

## <a name="logexpression"></a><span data-ttu-id="709ab-184">LOG(Expression)</span><span class="sxs-lookup"><span data-stu-id="709ab-184">LOG(expression)</span></span>

<span data-ttu-id="709ab-185">Oblicza logarytm naturalny z określonym `float` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="709ab-185">Calculates the natural logarithm of the specified `float` expression.</span></span> 

<span data-ttu-id="709ab-186">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="709ab-186">**Arguments**</span></span> 

<span data-ttu-id="709ab-187">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="709ab-187">`expression`: A `Double`.</span></span> 

<span data-ttu-id="709ab-188">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="709ab-188">**Return Value**</span></span> 

<span data-ttu-id="709ab-189">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="709ab-189">A `Double`.</span></span> 

<span data-ttu-id="709ab-190">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="709ab-190">**Example**</span></span> 

`SqlServer.LOG(100)`

## <a name="log10expression"></a><span data-ttu-id="709ab-191">LOG10(Expression)</span><span class="sxs-lookup"><span data-stu-id="709ab-191">LOG10(expression)</span></span>

<span data-ttu-id="709ab-192">Zwraca logarytm o podstawie base 10 określonego `Double` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="709ab-192">Returns the base-10 logarithm of the specified `Double` expression.</span></span> 

<span data-ttu-id="709ab-193">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="709ab-193">**Arguments**</span></span> 

<span data-ttu-id="709ab-194">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="709ab-194">`expression`: A `Double`.</span></span> 

<span data-ttu-id="709ab-195">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="709ab-195">**Return Value**</span></span> 

<span data-ttu-id="709ab-196">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="709ab-196">A `Double`.</span></span> 

<span data-ttu-id="709ab-197">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="709ab-197">**Example**</span></span> 

`SqlServer.LOG10(100)`

## <a name="pi"></a><span data-ttu-id="709ab-198">PI()</span><span class="sxs-lookup"><span data-stu-id="709ab-198">PI()</span></span>

<span data-ttu-id="709ab-199">Zwraca wartość stała pi jako `Double`.</span><span class="sxs-lookup"><span data-stu-id="709ab-199">Returns the constant value of pi as a `Double`.</span></span> 

<span data-ttu-id="709ab-200">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="709ab-200">**Return Value**</span></span> 

<span data-ttu-id="709ab-201">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="709ab-201">A `Double`.</span></span> 

<span data-ttu-id="709ab-202">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="709ab-202">**Example**</span></span> 

`SqlServer.PI()`

## <a name="powernumericexpression-powerexpression"></a><span data-ttu-id="709ab-203">ZASILANIA (numeric_expression, power_expression)</span><span class="sxs-lookup"><span data-stu-id="709ab-203">POWER(numeric_expression, power_expression)</span></span>

<span data-ttu-id="709ab-204">Oblicza wartość określone wyrażenie do określonej potęgi.</span><span class="sxs-lookup"><span data-stu-id="709ab-204">Calculates the value of a specified expression to a specified power.</span></span>

<span data-ttu-id="709ab-205">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="709ab-205">**Arguments**</span></span> 

|  |  |
|--|--|
|`numeric_expression`| <span data-ttu-id="709ab-206">`Int32`, `Int64`, `Double`, Lub `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="709ab-206">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>|
|`power_expression`| <span data-ttu-id="709ab-207">A `Double` reprezentujący zasilania, do którego zostanie wywołane `numeric_expression`.</span><span class="sxs-lookup"><span data-stu-id="709ab-207">A `Double` that represents the power to which to raise the `numeric_expression`.</span></span>| 

<span data-ttu-id="709ab-208">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="709ab-208">**Return Value**</span></span> 

<span data-ttu-id="709ab-209">Wartość określonego `numeric_expression` określonej `power_expression`.</span><span class="sxs-lookup"><span data-stu-id="709ab-209">The value of the specified `numeric_expression` to the specified `power_expression`.</span></span> 

<span data-ttu-id="709ab-210">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="709ab-210">**Example**</span></span> 

`SqlServer.POWER(2,7)`

## <a name="radiansexpression"></a><span data-ttu-id="709ab-211">RADIANS(Expression)</span><span class="sxs-lookup"><span data-stu-id="709ab-211">RADIANS(expression)</span></span>

<span data-ttu-id="709ab-212">Konwertuje stopnie na radiany.</span><span class="sxs-lookup"><span data-stu-id="709ab-212">Converts degrees to radians.</span></span> 

<span data-ttu-id="709ab-213">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="709ab-213">**Arguments**</span></span> 

<span data-ttu-id="709ab-214">`expression`: `Int32`, `Int64`, `Double`, Lub `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="709ab-214">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="709ab-215">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="709ab-215">**Return Value**</span></span> 

<span data-ttu-id="709ab-216">`Int32`, `Int64`, `Double`, Lub `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="709ab-216">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="709ab-217">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="709ab-217">**Example**</span></span> 

`SqlServer.RADIANS(360.0)`

## <a name="randseed"></a><span data-ttu-id="709ab-218">RAND([seed])</span><span class="sxs-lookup"><span data-stu-id="709ab-218">RAND([seed])</span></span>

<span data-ttu-id="709ab-219">Zwraca wartość losową z zakresu od 0 do 1.</span><span class="sxs-lookup"><span data-stu-id="709ab-219">Returns a random value from 0 through 1.</span></span> 

<span data-ttu-id="709ab-220">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="709ab-220">**Arguments**</span></span> 

<span data-ttu-id="709ab-221">Wartość początkową jako `Int32`.</span><span class="sxs-lookup"><span data-stu-id="709ab-221">The seed value as an `Int32`.</span></span> <span data-ttu-id="709ab-222">Jeśli zalążek nie zostanie określony, aparatu bazy danych programu SQL Server w losowo wybranym momencie przypisuje wartość inicjatora.</span><span class="sxs-lookup"><span data-stu-id="709ab-222">If the seed is not specified, the SQL Server Database Engine assigns a seed value at random.</span></span> <span data-ttu-id="709ab-223">Wartości inicjatora określona zwracana jest zawsze taki sam.</span><span class="sxs-lookup"><span data-stu-id="709ab-223">For a specified seed value, the result returned is always the same.</span></span>

<span data-ttu-id="709ab-224">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="709ab-224">**Return Value**</span></span> 

<span data-ttu-id="709ab-225">Losowe `Double` wartość od 0 do 1.</span><span class="sxs-lookup"><span data-stu-id="709ab-225">A random `Double` value from 0 through 1.</span></span> 

<span data-ttu-id="709ab-226">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="709ab-226">**Example**</span></span> 

`SqlServer.RAND()`
  
## <a name="roundnumericexpression-lengthfunction"></a><span data-ttu-id="709ab-227">ROUND(Numeric_Expression, length[,Function])</span><span class="sxs-lookup"><span data-stu-id="709ab-227">ROUND(numeric_expression, length[,function])</span></span>

<span data-ttu-id="709ab-228">Zwraca wartość wyrażenia liczbowego zaokrąglone do określonej długości lub dokładności.</span><span class="sxs-lookup"><span data-stu-id="709ab-228">Returns a numeric expression, rounded to the specified length or precision.</span></span> 

<span data-ttu-id="709ab-229">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="709ab-229">**Arguments**</span></span> 

|  |  |
|--|--|
|`numeric_expression`| <span data-ttu-id="709ab-230">`Int32`, `Int64`, `Double`, Lub `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="709ab-230">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 
|`length`| <span data-ttu-id="709ab-231">`Int32` Reprezentujący dokładność, do którego `numeric_expression` ma zostać zaokrąglona.</span><span class="sxs-lookup"><span data-stu-id="709ab-231">An `Int32` that represents the precision to which `numeric_expression` is to be rounded.</span></span> <span data-ttu-id="709ab-232">Gdy `length` jest liczbą dodatnią `numeric_expression` jest zaokrąglana do liczby miejsc dziesiętnych określonej przez `length`.</span><span class="sxs-lookup"><span data-stu-id="709ab-232">When `length` is a positive number, `numeric_expression` is rounded to the number of decimal positions specified by `length`.</span></span> <span data-ttu-id="709ab-233">Gdy `length` jest liczbą ujemną `numeric_expression` jest zaokrąglana po lewej stronie przecinka dziesiętnego, określony przez `length`.</span><span class="sxs-lookup"><span data-stu-id="709ab-233">When `length` is a negative number, `numeric_expression` is rounded on the left side of the decimal point, as specified by `length`.</span></span>|
|`function` | <span data-ttu-id="709ab-234">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="709ab-234">Optional.</span></span> <span data-ttu-id="709ab-235">`Int32` Reprezentujący typ operacji do wykonania.</span><span class="sxs-lookup"><span data-stu-id="709ab-235">An `Int32` that represents the type of operation to perform.</span></span> <span data-ttu-id="709ab-236">Gdy funkcja zostanie pominięty lub ma wartość 0 (domyślnie), `numeric_expression` jest zaokrąglana.</span><span class="sxs-lookup"><span data-stu-id="709ab-236">When function is omitted or has a value of 0 (default), `numeric_expression` is rounded.</span></span> <span data-ttu-id="709ab-237">Gdy wartość inną niż określono wartość 0, `numeric_expression` zostały obcięte.</span><span class="sxs-lookup"><span data-stu-id="709ab-237">When a value other than 0 is specified, `numeric_expression` is truncated.</span></span> |

<span data-ttu-id="709ab-238">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="709ab-238">**Return Value**</span></span> 

<span data-ttu-id="709ab-239">Wartość określonego `numeric_expression` określonej `power_expression`.</span><span class="sxs-lookup"><span data-stu-id="709ab-239">The value of the specified `numeric_expression` to the specified `power_expression`.</span></span>

<span data-ttu-id="709ab-240">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="709ab-240">**Example**</span></span> 

`SqlServer.ROUND(748.58, -3)`

## <a name="signexpression"></a><span data-ttu-id="709ab-241">SIGN(Expression)</span><span class="sxs-lookup"><span data-stu-id="709ab-241">SIGN(expression)</span></span> 

<span data-ttu-id="709ab-242">Zwraca wynik dodatni (+ 1), wartość zero (0) lub minus (-1) z określonego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="709ab-242">Returns the positive (+1), zero (0), or negative (-1) sign of the specified expression.</span></span> 

<span data-ttu-id="709ab-243">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="709ab-243">**Arguments**</span></span> 

<span data-ttu-id="709ab-244">`expression`: `Int32`, `Int64`, `Double`, lub `Decimal`</span><span class="sxs-lookup"><span data-stu-id="709ab-244">`expression`: `Int32`, `Int64`, `Double`, or `Decimal`</span></span> 

<span data-ttu-id="709ab-245">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="709ab-245">**Return Value**</span></span> 

<span data-ttu-id="709ab-246">`Int32`, `Int64`, `Double`, Lub `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="709ab-246">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="709ab-247">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="709ab-247">**Example**</span></span> 

`SqlServer.SIGN(-10)`

## <a name="sinexpression"></a><span data-ttu-id="709ab-248">SIN(Expression)</span><span class="sxs-lookup"><span data-stu-id="709ab-248">SIN(expression)</span></span>

<span data-ttu-id="709ab-249">Oblicza trygonometrycznych sinus określonego kąta podany w radianach, a następnie zwraca `Double` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="709ab-249">Calculates the trigonometric sine of the specified angle in radians, and returns a `Double` expression.</span></span> 

<span data-ttu-id="709ab-250">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="709ab-250">**Arguments**</span></span> 

<span data-ttu-id="709ab-251">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="709ab-251">`expression`: A `Double`.</span></span> 

<span data-ttu-id="709ab-252">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="709ab-252">**Return Value**</span></span> 

<span data-ttu-id="709ab-253">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="709ab-253">A `Double`.</span></span> 

<span data-ttu-id="709ab-254">**Przykład** `SqlServer.SIN(20)`</span><span class="sxs-lookup"><span data-stu-id="709ab-254">**Example** `SqlServer.SIN(20)`</span></span>

## <a name="sqrtexpression"></a><span data-ttu-id="709ab-255">SQRT(Expression)</span><span class="sxs-lookup"><span data-stu-id="709ab-255">SQRT(expression)</span></span>

<span data-ttu-id="709ab-256">Zwraca pierwiastek kwadratowy z określonego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="709ab-256">Returns the square root of the specified expression.</span></span> 

<span data-ttu-id="709ab-257">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="709ab-257">**Arguments**</span></span> 

<span data-ttu-id="709ab-258">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="709ab-258">`expression`: A `Double`.</span></span> 

<span data-ttu-id="709ab-259">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="709ab-259">**Return Value**</span></span> 

<span data-ttu-id="709ab-260">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="709ab-260">A `Double`.</span></span> 

<span data-ttu-id="709ab-261">**Przykład** `SqlServer.SQRT(3600)`</span><span class="sxs-lookup"><span data-stu-id="709ab-261">**Example** `SqlServer.SQRT(3600)`</span></span>

## <a name="squareexpression"></a><span data-ttu-id="709ab-262">SQUARE(Expression)</span><span class="sxs-lookup"><span data-stu-id="709ab-262">SQUARE(expression)</span></span>

<span data-ttu-id="709ab-263">Zwraca kwadrat określone wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="709ab-263">Returns the square of the specified expression.</span></span> 

<span data-ttu-id="709ab-264">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="709ab-264">**Arguments**</span></span> 

<span data-ttu-id="709ab-265">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="709ab-265">`expression`: A `Double`.</span></span> 

<span data-ttu-id="709ab-266">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="709ab-266">**Return Value**</span></span> 

<span data-ttu-id="709ab-267">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="709ab-267">A `Double`.</span></span> 

<span data-ttu-id="709ab-268">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="709ab-268">**Example**</span></span> 

`SqlServer.SQUARE(25)`

## <a name="tanexpression"></a><span data-ttu-id="709ab-269">Tan(Expression)</span><span class="sxs-lookup"><span data-stu-id="709ab-269">TAN(expression)</span></span>

<span data-ttu-id="709ab-270">Oblicza tangens określonego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="709ab-270">Calculates the tangent of a specified expression.</span></span>

<span data-ttu-id="709ab-271">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="709ab-271">**Arguments**</span></span> 

<span data-ttu-id="709ab-272">`expression`: `Double`</span><span class="sxs-lookup"><span data-stu-id="709ab-272">`expression`: `Double`</span></span> 

<span data-ttu-id="709ab-273">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="709ab-273">**Return Value**</span></span> 

`Double` 

<span data-ttu-id="709ab-274">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="709ab-274">**Example**</span></span> 

`SqlServer.TAN(45.0)`
  
## <a name="see-also"></a><span data-ttu-id="709ab-275">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="709ab-275">See also</span></span>

<span data-ttu-id="709ab-276">Aby uzyskać więcej informacji na temat funkcji matematycznych, które obsługuje klient SQL zobacz dokumentację dla używanej wersji programu SQL Server określonego w manifeście dostawcy SqlClient:</span><span class="sxs-lookup"><span data-stu-id="709ab-276">For more information about the mathematical functions that SqlClient supports, see the documentation for the SQL Server version that you specified in the SqlClient provider manifest:</span></span>  

<span data-ttu-id="709ab-277">**SQL Server 2005:** [Mathematical Functions (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms177516(v=sql.90))</span><span class="sxs-lookup"><span data-stu-id="709ab-277">**SQL Server 2005:** [Mathematical Functions (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms177516(v=sql.90))</span></span>  
<span data-ttu-id="709ab-278">**SQL Server 2008:** [Mathematical Functions (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms177516(v=sql.100))</span><span class="sxs-lookup"><span data-stu-id="709ab-278">**SQL Server 2008:** [Mathematical Functions (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms177516(v=sql.100))</span></span>  
<span data-ttu-id="709ab-279">**Program SQL Server 2012 lub nowszy:** [Mathematical Functions (Transact-SQL)](/sql/t-sql/functions/mathematical-functions-transact-sql?view=sql-server-2017)</span><span class="sxs-lookup"><span data-stu-id="709ab-279">**SQL Server 2012 and later:** [Mathematical Functions (Transact-SQL)](/sql/t-sql/functions/mathematical-functions-transact-sql?view=sql-server-2017)</span></span>   

- [<span data-ttu-id="709ab-280">Klient SQL dla funkcji programu Entity Framework</span><span class="sxs-lookup"><span data-stu-id="709ab-280">SqlClient for Entity Framework Functions</span></span>](sqlclient-for-ef-functions.md)
