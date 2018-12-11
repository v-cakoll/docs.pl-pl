---
title: Funkcje matematyczne
ms.date: 03/30/2017
ms.assetid: b040c7cb-156d-40f2-9152-61065b18148c
ms.openlocfilehash: 63f83532c399f77e268913da3198327345b9c2ee
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53143678"
---
# <a name="mathematical-functions"></a><span data-ttu-id="c4644-102">Funkcje matematyczne</span><span class="sxs-lookup"><span data-stu-id="c4644-102">Mathematical Functions</span></span>

<span data-ttu-id="c4644-103">.NET Framework Data Provider for SQL Server (SqlClient) zapewnia funkcje matematyczne, które wykonują obliczenia na wartości wejściowych, które są przekazywane jako argumenty i zwraca wynik wartość liczbową.</span><span class="sxs-lookup"><span data-stu-id="c4644-103">The .NET Framework Data Provider for SQL Server (SqlClient) provides math functions that perform calculations on input values that are provided as arguments, and return a numeric value result.</span></span> <span data-ttu-id="c4644-104">Te funkcje są w przestrzeni nazw SqlServer, który jest dostępny, gdy używasz SqlClient.</span><span class="sxs-lookup"><span data-stu-id="c4644-104">These functions are in the SqlServer namespace, which is available when you use SqlClient.</span></span> <span data-ttu-id="c4644-105">Właściwość przestrzeni nazw dostawcy umożliwia programu Entity Framework dowiedzieć się, który prefiks jest używany przez tego dostawcę dla określonego konstrukcji, takich jak typy i funkcje.</span><span class="sxs-lookup"><span data-stu-id="c4644-105">A provider's namespace property allows the Entity Framework to discover which prefix is used by this provider for specific constructs, such as types and functions.</span></span> <span data-ttu-id="c4644-106">W poniższej tabeli opisano funkcje matematyczne SqlClient.</span><span class="sxs-lookup"><span data-stu-id="c4644-106">The following table describes the SqlClient math functions.</span></span>  
  
## <a name="absexpression"></a><span data-ttu-id="c4644-107">ABS(Expression)</span><span class="sxs-lookup"><span data-stu-id="c4644-107">ABS(expression)</span></span>

<span data-ttu-id="c4644-108">Wykonuje funkcję wartości bezwzględnej.</span><span class="sxs-lookup"><span data-stu-id="c4644-108">Performs the absolute value function.</span></span>

<span data-ttu-id="c4644-109">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="c4644-109">**Arguments**</span></span>

<span data-ttu-id="c4644-110">`expression`: `Int32`, `Int64`, `Double`, Lub `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="c4644-110">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="c4644-111">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="c4644-111">**Return Value**</span></span>

<span data-ttu-id="c4644-112">Wartość bezwzględna z określonego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="c4644-112">The absolute value of the specified expression.</span></span>

<span data-ttu-id="c4644-113">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="c4644-113">**Example**</span></span>

`SqlServer.ABS(-2)`

## <a name="acosexpression"></a><span data-ttu-id="c4644-114">ACOS(Expression)</span><span class="sxs-lookup"><span data-stu-id="c4644-114">ACOS(expression)</span></span>

<span data-ttu-id="c4644-115">Zwraca arcus cosinus wartości podanego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="c4644-115">Returns the arccosine value of the specified expression.</span></span>

<span data-ttu-id="c4644-116">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="c4644-116">**Arguments**</span></span>

<span data-ttu-id="c4644-117">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="c4644-117">`expression`: A `Double`.</span></span>

<span data-ttu-id="c4644-118">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="c4644-118">**Return Value**</span></span>

<span data-ttu-id="c4644-119">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="c4644-119">A `Double`.</span></span>

<span data-ttu-id="c4644-120">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="c4644-120">**Example**</span></span>

`SqlServer.ACOS(.9)`

## <a name="asinexpression"></a><span data-ttu-id="c4644-121">ASIN(Expression)</span><span class="sxs-lookup"><span data-stu-id="c4644-121">ASIN(expression)</span></span>

<span data-ttu-id="c4644-122">Zwraca arcus sinus wartości podanego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="c4644-122">Returns the arcsine value of the specified expression.</span></span>

<span data-ttu-id="c4644-123">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="c4644-123">**Arguments**</span></span>

<span data-ttu-id="c4644-124">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="c4644-124">`expression`: A `Double`.</span></span>

<span data-ttu-id="c4644-125">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="c4644-125">**Return Value**</span></span>

<span data-ttu-id="c4644-126">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="c4644-126">A `Double`.</span></span>

<span data-ttu-id="c4644-127">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="c4644-127">**Example**</span></span>

`SqlServer.ASIN(.9)`

## <a name="atanexpression"></a><span data-ttu-id="c4644-128">ATAN(Expression)</span><span class="sxs-lookup"><span data-stu-id="c4644-128">ATAN(expression)</span></span>

<span data-ttu-id="c4644-129">Zwraca arcus tangens wartości podanego wyrażenia liczbowego.</span><span class="sxs-lookup"><span data-stu-id="c4644-129">Returns the arctangent value of the specified numeric expression.</span></span>

<span data-ttu-id="c4644-130">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="c4644-130">**Arguments**</span></span>

<span data-ttu-id="c4644-131">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="c4644-131">`expression`: A `Double`.</span></span>

<span data-ttu-id="c4644-132">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="c4644-132">**Return Value**</span></span>

<span data-ttu-id="c4644-133">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="c4644-133">A `Double`.</span></span>

<span data-ttu-id="c4644-134">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="c4644-134">**Example**</span></span>

`SqlServer.ATAN(9)`

## <a name="atn2expression-expression"></a><span data-ttu-id="c4644-135">ATN2(Expression, Expression)</span><span class="sxs-lookup"><span data-stu-id="c4644-135">ATN2(expression, expression)</span></span>

<span data-ttu-id="c4644-136">Zwraca kąt w radianach, którego tangens jest między dwoma określonych wyrażeń liczbowych.</span><span class="sxs-lookup"><span data-stu-id="c4644-136">Returns the angle, in radians, whose tangent is between the two specified numeric expressions.</span></span>

<span data-ttu-id="c4644-137">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="c4644-137">**Arguments**</span></span>

<span data-ttu-id="c4644-138">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="c4644-138">`expression`: A `Double`.</span></span>

<span data-ttu-id="c4644-139">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="c4644-139">**Return Value**</span></span>

<span data-ttu-id="c4644-140">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="c4644-140">A `Double`.</span></span>

<span data-ttu-id="c4644-141">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="c4644-141">**Example**</span></span>

`SqlServer.ATN2(9, 8)`
 
## <a name="ceilingexpression"></a><span data-ttu-id="c4644-142">CEILING(Expression)</span><span class="sxs-lookup"><span data-stu-id="c4644-142">CEILING(expression)</span></span>

<span data-ttu-id="c4644-143">Konwertuje określony wyrażenie najmniejsza liczba całkowita, która jest większa niż lub równą jej.</span><span class="sxs-lookup"><span data-stu-id="c4644-143">Converts the specified expression to the smallest integer that is greater than or equal to it.</span></span>

<span data-ttu-id="c4644-144">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="c4644-144">**Arguments**</span></span>

<span data-ttu-id="c4644-145">`expression`: `Int32`, `Int64`, `Double`, Lub `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="c4644-145">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="c4644-146">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="c4644-146">**Return Value**</span></span>

<span data-ttu-id="c4644-147">`Int32`, `Int64`, `Double`, Lub `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="c4644-147">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="c4644-148">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="c4644-148">**Example**</span></span> 

[!code-csharp[DP EntityServices Concepts#SQLSERVER_CEILING](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_ceiling)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_ceiling)]

## <a name="cosexpression"></a><span data-ttu-id="c4644-149">COS(Expression)</span><span class="sxs-lookup"><span data-stu-id="c4644-149">COS(expression)</span></span>

<span data-ttu-id="c4644-150">Oblicza trygonometrycznych cosinus określonego kąta podany w radianach.</span><span class="sxs-lookup"><span data-stu-id="c4644-150">Calculates the trigonometric cosine of the specified angle in radians.</span></span> 

<span data-ttu-id="c4644-151">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="c4644-151">**Arguments**</span></span> 

<span data-ttu-id="c4644-152">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="c4644-152">`expression`: A `Double`.</span></span> 

<span data-ttu-id="c4644-153">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="c4644-153">**Return Value**</span></span> 

<span data-ttu-id="c4644-154">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="c4644-154">A `Double`.</span></span> 

<span data-ttu-id="c4644-155">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="c4644-155">**Example**</span></span> 

`SqlServer.COS(45)`

## <a name="cotexpression"></a><span data-ttu-id="c4644-156">COT(Expression)</span><span class="sxs-lookup"><span data-stu-id="c4644-156">COT(expression)</span></span>

<span data-ttu-id="c4644-157">Oblicza trygonometrycznych cotangens kąta określonego w radianach.</span><span class="sxs-lookup"><span data-stu-id="c4644-157">Calculates the trigonometric cotangent of the specified angle in radians.</span></span> 

<span data-ttu-id="c4644-158">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="c4644-158">**Arguments**</span></span> 

<span data-ttu-id="c4644-159">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="c4644-159">`expression`: A `Double`.</span></span> 

<span data-ttu-id="c4644-160">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="c4644-160">**Return Value**</span></span> 

<span data-ttu-id="c4644-161">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="c4644-161">A `Double`.</span></span> 

<span data-ttu-id="c4644-162">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="c4644-162">**Example**</span></span> 

`SqlServer.COT(60)`
  
## <a name="degreesradians"></a><span data-ttu-id="c4644-163">DEGREES(RADIANS)</span><span class="sxs-lookup"><span data-stu-id="c4644-163">DEGREES(radians)</span></span>

<span data-ttu-id="c4644-164">Zwraca odpowiedni kąt w stopniach.</span><span class="sxs-lookup"><span data-stu-id="c4644-164">Returns the corresponding angle in degrees.</span></span> 

<span data-ttu-id="c4644-165">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="c4644-165">**Arguments**</span></span> 

<span data-ttu-id="c4644-166">`expression`: `Int32`, `Int64`, `Double`, Lub `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="c4644-166">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="c4644-167">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="c4644-167">**Return Value**</span></span> 

<span data-ttu-id="c4644-168">`Int32`, `Int64`, `Double`, Lub `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="c4644-168">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="c4644-169">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="c4644-169">**Example**</span></span> 

`SqlServer.DEGREES(3.1)`

## <a name="expexpression"></a><span data-ttu-id="c4644-170">EXP(Expression)</span><span class="sxs-lookup"><span data-stu-id="c4644-170">EXP(expression)</span></span>

<span data-ttu-id="c4644-171">Oblicza wartość wykładniczą określonego wyrażenia liczbowego.</span><span class="sxs-lookup"><span data-stu-id="c4644-171">Calculates the exponential value of a specified numeric expression.</span></span> 

<span data-ttu-id="c4644-172">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="c4644-172">**Arguments**</span></span> 

<span data-ttu-id="c4644-173">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="c4644-173">`expression`: A `Double`.</span></span> 

<span data-ttu-id="c4644-174">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="c4644-174">**Return Value**</span></span> 

<span data-ttu-id="c4644-175">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="c4644-175">A `Double`.</span></span> 

<span data-ttu-id="c4644-176">**Przykład** `SqlServer.EXP(1)`</span><span class="sxs-lookup"><span data-stu-id="c4644-176">**Example** `SqlServer.EXP(1)`</span></span>

## <a name="floorexpression"></a><span data-ttu-id="c4644-177">FLOOR(Expression)</span><span class="sxs-lookup"><span data-stu-id="c4644-177">FLOOR(expression)</span></span>

<span data-ttu-id="c4644-178">Konwertuje określony wyrażenie największą liczbą całkowitą mniejszą lub równą jej.</span><span class="sxs-lookup"><span data-stu-id="c4644-178">Converts the specified expression to the largest integer less than or equal to it.</span></span> 

<span data-ttu-id="c4644-179">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="c4644-179">**Arguments**</span></span> 

<span data-ttu-id="c4644-180">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="c4644-180">`expression`: A `Double`.</span></span> 

<span data-ttu-id="c4644-181">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="c4644-181">**Return Value**</span></span> 

<span data-ttu-id="c4644-182">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="c4644-182">A `Double`.</span></span> 

<span data-ttu-id="c4644-183">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="c4644-183">**Example**</span></span> 

[!code-csharp[DP EntityServices Concepts#SQLSERVER_FLOOR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_floor)] 
[!code-sql[DP EntityServices Concepts#SQLSERVER_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_floor)]

## <a name="logexpression"></a><span data-ttu-id="c4644-184">LOG(Expression)</span><span class="sxs-lookup"><span data-stu-id="c4644-184">LOG(expression)</span></span>

<span data-ttu-id="c4644-185">Oblicza logarytm naturalny z określonym `float` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="c4644-185">Calculates the natural logarithm of the specified `float` expression.</span></span> 

<span data-ttu-id="c4644-186">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="c4644-186">**Arguments**</span></span> 

<span data-ttu-id="c4644-187">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="c4644-187">`expression`: A `Double`.</span></span> 

<span data-ttu-id="c4644-188">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="c4644-188">**Return Value**</span></span> 

<span data-ttu-id="c4644-189">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="c4644-189">A `Double`.</span></span> 

<span data-ttu-id="c4644-190">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="c4644-190">**Example**</span></span> 

`SqlServer.LOG(100)`

## <a name="log10expression"></a><span data-ttu-id="c4644-191">LOG10(Expression)</span><span class="sxs-lookup"><span data-stu-id="c4644-191">LOG10(expression)</span></span>

<span data-ttu-id="c4644-192">Zwraca logarytm o podstawie base 10 określonego `Double` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="c4644-192">Returns the base-10 logarithm of the specified `Double` expression.</span></span> 

<span data-ttu-id="c4644-193">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="c4644-193">**Arguments**</span></span> 

<span data-ttu-id="c4644-194">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="c4644-194">`expression`: A `Double`.</span></span> 

<span data-ttu-id="c4644-195">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="c4644-195">**Return Value**</span></span> 

<span data-ttu-id="c4644-196">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="c4644-196">A `Double`.</span></span> 

<span data-ttu-id="c4644-197">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="c4644-197">**Example**</span></span> 

`SqlServer.LOG10(100)`

## <a name="pi"></a><span data-ttu-id="c4644-198">PI()</span><span class="sxs-lookup"><span data-stu-id="c4644-198">PI()</span></span>

<span data-ttu-id="c4644-199">Zwraca wartość stała pi jako `Double`.</span><span class="sxs-lookup"><span data-stu-id="c4644-199">Returns the constant value of pi as a `Double`.</span></span> 

<span data-ttu-id="c4644-200">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="c4644-200">**Return Value**</span></span> 

<span data-ttu-id="c4644-201">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="c4644-201">A `Double`.</span></span> 

<span data-ttu-id="c4644-202">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="c4644-202">**Example**</span></span> 

`SqlServer.PI()`

## <a name="powernumericexpression-powerexpression"></a><span data-ttu-id="c4644-203">ZASILANIA (numeric_expression, power_expression)</span><span class="sxs-lookup"><span data-stu-id="c4644-203">POWER(numeric_expression, power_expression)</span></span>

<span data-ttu-id="c4644-204">Oblicza wartość określone wyrażenie do określonej potęgi.</span><span class="sxs-lookup"><span data-stu-id="c4644-204">Calculates the value of a specified expression to a specified power.</span></span>

<span data-ttu-id="c4644-205">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="c4644-205">**Arguments**</span></span> 

|  |  |
|--|--|
|`numeric_expression`| <span data-ttu-id="c4644-206">`Int32`, `Int64`, `Double`, Lub `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="c4644-206">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>|
|`power_expression`| <span data-ttu-id="c4644-207">A `Double` reprezentujący zasilania, do którego zostanie wywołane `numeric_expression`.</span><span class="sxs-lookup"><span data-stu-id="c4644-207">A `Double` that represents the power to which to raise the `numeric_expression`.</span></span>| 

<span data-ttu-id="c4644-208">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="c4644-208">**Return Value**</span></span> 

<span data-ttu-id="c4644-209">Wartość określonego `numeric_expression` określonej `power_expression`.</span><span class="sxs-lookup"><span data-stu-id="c4644-209">The value of the specified `numeric_expression` to the specified `power_expression`.</span></span> 

<span data-ttu-id="c4644-210">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="c4644-210">**Example**</span></span> 

`SqlServer.POWER(2,7)`

## <a name="radiansexpression"></a><span data-ttu-id="c4644-211">RADIANS(Expression)</span><span class="sxs-lookup"><span data-stu-id="c4644-211">RADIANS(expression)</span></span>

<span data-ttu-id="c4644-212">Konwertuje stopnie na radiany.</span><span class="sxs-lookup"><span data-stu-id="c4644-212">Converts degrees to radians.</span></span> 

<span data-ttu-id="c4644-213">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="c4644-213">**Arguments**</span></span> 

<span data-ttu-id="c4644-214">`expression`: `Int32`, `Int64`, `Double`, Lub `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="c4644-214">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="c4644-215">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="c4644-215">**Return Value**</span></span> 

<span data-ttu-id="c4644-216">`Int32`, `Int64`, `Double`, Lub `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="c4644-216">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="c4644-217">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="c4644-217">**Example**</span></span> 

`SqlServer.RADIANS(360.0)`

## <a name="randseed"></a><span data-ttu-id="c4644-218">RAND([seed])</span><span class="sxs-lookup"><span data-stu-id="c4644-218">RAND([seed])</span></span>

<span data-ttu-id="c4644-219">Zwraca wartość losową z zakresu od 0 do 1.</span><span class="sxs-lookup"><span data-stu-id="c4644-219">Returns a random value from 0 through 1.</span></span> 

<span data-ttu-id="c4644-220">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="c4644-220">**Arguments**</span></span> 

<span data-ttu-id="c4644-221">Wartość początkową jako `Int32`.</span><span class="sxs-lookup"><span data-stu-id="c4644-221">The seed value as an `Int32`.</span></span> <span data-ttu-id="c4644-222">Jeśli zalążek nie zostanie określony, aparatu bazy danych programu SQL Server w losowo wybranym momencie przypisuje wartość inicjatora.</span><span class="sxs-lookup"><span data-stu-id="c4644-222">If the seed is not specified, the SQL Server Database Engine assigns a seed value at random.</span></span> <span data-ttu-id="c4644-223">Wartości inicjatora określona zwracana jest zawsze taki sam.</span><span class="sxs-lookup"><span data-stu-id="c4644-223">For a specified seed value, the result returned is always the same.</span></span>

<span data-ttu-id="c4644-224">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="c4644-224">**Return Value**</span></span> 

<span data-ttu-id="c4644-225">Losowe `Double` wartość od 0 do 1.</span><span class="sxs-lookup"><span data-stu-id="c4644-225">A random `Double` value from 0 through 1.</span></span> 

<span data-ttu-id="c4644-226">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="c4644-226">**Example**</span></span> 

`SqlServer.RAND()`
  
## <a name="roundnumericexpression-lengthfunction"></a><span data-ttu-id="c4644-227">ROUND(Numeric_Expression, length[,Function])</span><span class="sxs-lookup"><span data-stu-id="c4644-227">ROUND(numeric_expression, length[,function])</span></span>

<span data-ttu-id="c4644-228">Zwraca wartość wyrażenia liczbowego zaokrąglone do określonej długości lub dokładności.</span><span class="sxs-lookup"><span data-stu-id="c4644-228">Returns a numeric expression, rounded to the specified length or precision.</span></span> 

<span data-ttu-id="c4644-229">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="c4644-229">**Arguments**</span></span> 

|  |  |
|--|--|
|`numeric_expression`| <span data-ttu-id="c4644-230">`Int32`, `Int64`, `Double`, Lub `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="c4644-230">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 
|`length`| <span data-ttu-id="c4644-231">`Int32` Reprezentujący dokładność, do którego `numeric_expression` ma zostać zaokrąglona.</span><span class="sxs-lookup"><span data-stu-id="c4644-231">An `Int32` that represents the precision to which `numeric_expression` is to be rounded.</span></span> <span data-ttu-id="c4644-232">Gdy `length` jest liczbą dodatnią `numeric_expression` jest zaokrąglana do liczby miejsc dziesiętnych określonej przez `length`.</span><span class="sxs-lookup"><span data-stu-id="c4644-232">When `length` is a positive number, `numeric_expression` is rounded to the number of decimal positions specified by `length`.</span></span> <span data-ttu-id="c4644-233">Gdy `length` jest liczbą ujemną `numeric_expression` jest zaokrąglana po lewej stronie przecinka dziesiętnego, określony przez `length`.</span><span class="sxs-lookup"><span data-stu-id="c4644-233">When `length` is a negative number, `numeric_expression` is rounded on the left side of the decimal point, as specified by `length`.</span></span>|
|`function` | <span data-ttu-id="c4644-234">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="c4644-234">Optional.</span></span> <span data-ttu-id="c4644-235">`Int32` Reprezentujący typ operacji do wykonania.</span><span class="sxs-lookup"><span data-stu-id="c4644-235">An `Int32` that represents the type of operation to perform.</span></span> <span data-ttu-id="c4644-236">Gdy funkcja zostanie pominięty lub ma wartość 0 (domyślnie), `numeric_expression` jest zaokrąglana.</span><span class="sxs-lookup"><span data-stu-id="c4644-236">When function is omitted or has a value of 0 (default), `numeric_expression` is rounded.</span></span> <span data-ttu-id="c4644-237">Gdy wartość inną niż określono wartość 0, `numeric_expression` zostały obcięte.</span><span class="sxs-lookup"><span data-stu-id="c4644-237">When a value other than 0 is specified, `numeric_expression` is truncated.</span></span> |

<span data-ttu-id="c4644-238">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="c4644-238">**Return Value**</span></span> 

<span data-ttu-id="c4644-239">Wartość określonego `numeric_expression` określonej `power_expression`.</span><span class="sxs-lookup"><span data-stu-id="c4644-239">The value of the specified `numeric_expression` to the specified `power_expression`.</span></span>

<span data-ttu-id="c4644-240">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="c4644-240">**Example**</span></span> 

`SqlServer.ROUND(748.58, -3)`

## <a name="signexpression"></a><span data-ttu-id="c4644-241">SIGN(Expression)</span><span class="sxs-lookup"><span data-stu-id="c4644-241">SIGN(expression)</span></span> 

<span data-ttu-id="c4644-242">Zwraca wynik dodatni (+ 1), wartość zero (0) lub minus (-1) z określonego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="c4644-242">Returns the positive (+1), zero (0), or negative (-1) sign of the specified expression.</span></span> 

<span data-ttu-id="c4644-243">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="c4644-243">**Arguments**</span></span> 

<span data-ttu-id="c4644-244">`expression`: `Int32`, `Int64`, `Double`, lub `Decimal`</span><span class="sxs-lookup"><span data-stu-id="c4644-244">`expression`: `Int32`, `Int64`, `Double`, or `Decimal`</span></span> 

<span data-ttu-id="c4644-245">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="c4644-245">**Return Value**</span></span> 

<span data-ttu-id="c4644-246">`Int32`, `Int64`, `Double`, Lub `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="c4644-246">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="c4644-247">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="c4644-247">**Example**</span></span> 

`SqlServer.SIGN(-10)`

## <a name="sinexpression"></a><span data-ttu-id="c4644-248">SIN(Expression)</span><span class="sxs-lookup"><span data-stu-id="c4644-248">SIN(expression)</span></span>

<span data-ttu-id="c4644-249">Oblicza trygonometrycznych sinus określonego kąta podany w radianach, a następnie zwraca `Double` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="c4644-249">Calculates the trigonometric sine of the specified angle in radians, and returns a `Double` expression.</span></span> 

<span data-ttu-id="c4644-250">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="c4644-250">**Arguments**</span></span> 

<span data-ttu-id="c4644-251">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="c4644-251">`expression`: A `Double`.</span></span> 

<span data-ttu-id="c4644-252">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="c4644-252">**Return Value**</span></span> 

<span data-ttu-id="c4644-253">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="c4644-253">A `Double`.</span></span> 

<span data-ttu-id="c4644-254">**Przykład** `SqlServer.SIN(20)`</span><span class="sxs-lookup"><span data-stu-id="c4644-254">**Example** `SqlServer.SIN(20)`</span></span>

## <a name="sqrtexpression"></a><span data-ttu-id="c4644-255">SQRT(Expression)</span><span class="sxs-lookup"><span data-stu-id="c4644-255">SQRT(expression)</span></span>

<span data-ttu-id="c4644-256">Zwraca pierwiastek kwadratowy z określonego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="c4644-256">Returns the square root of the specified expression.</span></span> 

<span data-ttu-id="c4644-257">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="c4644-257">**Arguments**</span></span> 

<span data-ttu-id="c4644-258">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="c4644-258">`expression`: A `Double`.</span></span> 

<span data-ttu-id="c4644-259">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="c4644-259">**Return Value**</span></span> 

<span data-ttu-id="c4644-260">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="c4644-260">A `Double`.</span></span> 

<span data-ttu-id="c4644-261">**Przykład** `SqlServer.SQRT(3600)`</span><span class="sxs-lookup"><span data-stu-id="c4644-261">**Example** `SqlServer.SQRT(3600)`</span></span>

## <a name="squareexpression"></a><span data-ttu-id="c4644-262">SQUARE(Expression)</span><span class="sxs-lookup"><span data-stu-id="c4644-262">SQUARE(expression)</span></span>

<span data-ttu-id="c4644-263">Zwraca kwadrat określone wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="c4644-263">Returns the square of the specified expression.</span></span> 

<span data-ttu-id="c4644-264">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="c4644-264">**Arguments**</span></span> 

<span data-ttu-id="c4644-265">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="c4644-265">`expression`: A `Double`.</span></span> 

<span data-ttu-id="c4644-266">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="c4644-266">**Return Value**</span></span> 

<span data-ttu-id="c4644-267">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="c4644-267">A `Double`.</span></span> 

<span data-ttu-id="c4644-268">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="c4644-268">**Example**</span></span> 

`SqlServer.SQUARE(25)`

## <a name="tanexpression"></a><span data-ttu-id="c4644-269">Tan(Expression)</span><span class="sxs-lookup"><span data-stu-id="c4644-269">TAN(expression)</span></span>

<span data-ttu-id="c4644-270">Oblicza tangens określonego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="c4644-270">Calculates the tangent of a specified expression.</span></span>

<span data-ttu-id="c4644-271">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="c4644-271">**Arguments**</span></span> 

<span data-ttu-id="c4644-272">`expression`: `Double`</span><span class="sxs-lookup"><span data-stu-id="c4644-272">`expression`: `Double`</span></span> 

<span data-ttu-id="c4644-273">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="c4644-273">**Return Value**</span></span> 

`Double` 

<span data-ttu-id="c4644-274">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="c4644-274">**Example**</span></span> 

`SqlServer.TAN(45.0)`
  
## <a name="see-also"></a><span data-ttu-id="c4644-275">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c4644-275">See also</span></span>

<span data-ttu-id="c4644-276">Aby uzyskać więcej informacji na temat funkcji matematycznych, które obsługuje klient SQL zobacz dokumentację dla używanej wersji programu SQL Server określonego w manifeście dostawcy SqlClient:</span><span class="sxs-lookup"><span data-stu-id="c4644-276">For more information about the mathematical functions that SqlClient supports, see the documentation for the SQL Server version that you specified in the SqlClient provider manifest:</span></span>  
  
<span data-ttu-id="c4644-277">**Program SQL Server 2005:** [Funkcje matematyczne (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms177516(v=sql.90))</span><span class="sxs-lookup"><span data-stu-id="c4644-277">**SQL Server 2005:** [Mathematical Functions (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms177516(v=sql.90))</span></span>  
<span data-ttu-id="c4644-278">**Program SQL Server 2008:** [Funkcje matematyczne (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms177516(v=sql.100))</span><span class="sxs-lookup"><span data-stu-id="c4644-278">**SQL Server 2008:** [Mathematical Functions (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms177516(v=sql.100))</span></span>  
<span data-ttu-id="c4644-279">**Program SQL Server 2012 lub nowszy:** [Funkcje matematyczne (Transact-SQL)](/sql/t-sql/functions/mathematical-functions-transact-sql?view=sql-server-2017)</span><span class="sxs-lookup"><span data-stu-id="c4644-279">**SQL Server 2012 and later:** [Mathematical Functions (Transact-SQL)](/sql/t-sql/functions/mathematical-functions-transact-sql?view=sql-server-2017)</span></span>   

 [<span data-ttu-id="c4644-280">Klient SQL dla funkcji programu Entity Framework</span><span class="sxs-lookup"><span data-stu-id="c4644-280">SqlClient for Entity Framework Functions</span></span>](sqlclient-for-ef-functions.md)
