---
title: Funkcje matematyczne
ms.date: 03/30/2017
ms.assetid: b040c7cb-156d-40f2-9152-61065b18148c
ms.openlocfilehash: e6c58d781d7138f8295f2d0a2f0db110ad4b1dd6
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2018
ms.locfileid: "48837313"
---
# <a name="mathematical-functions"></a><span data-ttu-id="770ae-102">Funkcje matematyczne</span><span class="sxs-lookup"><span data-stu-id="770ae-102">Mathematical Functions</span></span>

<span data-ttu-id="770ae-103">.NET Framework Data Provider for SQL Server (SqlClient) zapewnia funkcje matematyczne, które wykonują obliczenia na wartości wejściowych, które są przekazywane jako argumenty i zwraca wynik wartość liczbową.</span><span class="sxs-lookup"><span data-stu-id="770ae-103">The .NET Framework Data Provider for SQL Server (SqlClient) provides math functions that perform calculations on input values that are provided as arguments, and return a numeric value result.</span></span> <span data-ttu-id="770ae-104">Te funkcje są w przestrzeni nazw SqlServer, który jest dostępny, gdy używasz SqlClient.</span><span class="sxs-lookup"><span data-stu-id="770ae-104">These functions are in the SqlServer namespace, which is available when you use SqlClient.</span></span> <span data-ttu-id="770ae-105">Właściwość przestrzeni nazw dostawcy umożliwia programu Entity Framework dowiedzieć się, który prefiks jest używany przez tego dostawcę dla określonego konstrukcji, takich jak typy i funkcje. W poniższej tabeli opisano funkcje matematyczne SqlClient.</span><span class="sxs-lookup"><span data-stu-id="770ae-105">A provider's namespace property allows the Entity Framework to discover which prefix is used by this provider for specific constructs, such as types and functions.The following table describes the SqlClient math functions.</span></span>  
  
## <a name="absexpression"></a><span data-ttu-id="770ae-106">ABS(Expression)</span><span class="sxs-lookup"><span data-stu-id="770ae-106">ABS(expression)</span></span>

<span data-ttu-id="770ae-107">Wykonuje funkcję wartości bezwzględnej.</span><span class="sxs-lookup"><span data-stu-id="770ae-107">Performs the absolute value function.</span></span>

<span data-ttu-id="770ae-108">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="770ae-108">**Arguments**</span></span>

<span data-ttu-id="770ae-109">`expression`: `Int32`, `Int64`, `Double`, Lub `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="770ae-109">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="770ae-110">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="770ae-110">**Return Value**</span></span>

<span data-ttu-id="770ae-111">Wartość bezwzględna z określonego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="770ae-111">The absolute value of the specified expression.</span></span>

<span data-ttu-id="770ae-112">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="770ae-112">**Example**</span></span>

`SqlServer.ABS(-2)`

## <a name="acosexpression"></a><span data-ttu-id="770ae-113">ACOS(Expression)</span><span class="sxs-lookup"><span data-stu-id="770ae-113">ACOS(expression)</span></span>

<span data-ttu-id="770ae-114">Zwraca arcus cosinus wartości podanego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="770ae-114">Returns the arccosine value of the specified expression.</span></span>

<span data-ttu-id="770ae-115">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="770ae-115">**Arguments**</span></span>

<span data-ttu-id="770ae-116">`expression`: ELEMENT `Double`.</span><span class="sxs-lookup"><span data-stu-id="770ae-116">`expression`: A `Double`.</span></span>

<span data-ttu-id="770ae-117">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="770ae-117">**Return Value**</span></span>

<span data-ttu-id="770ae-118">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="770ae-118">A `Double`.</span></span>

<span data-ttu-id="770ae-119">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="770ae-119">**Example**</span></span>

`SqlServer.ACOS(.9)`

## <a name="asinexpression"></a><span data-ttu-id="770ae-120">ASIN(Expression)</span><span class="sxs-lookup"><span data-stu-id="770ae-120">ASIN(expression)</span></span>

<span data-ttu-id="770ae-121">Zwraca arcus sinus wartości podanego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="770ae-121">Returns the arcsine value of the specified expression.</span></span>

<span data-ttu-id="770ae-122">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="770ae-122">**Arguments**</span></span>

<span data-ttu-id="770ae-123">`expression`: ELEMENT `Double`.</span><span class="sxs-lookup"><span data-stu-id="770ae-123">`expression`: A `Double`.</span></span>

<span data-ttu-id="770ae-124">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="770ae-124">**Return Value**</span></span>

<span data-ttu-id="770ae-125">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="770ae-125">A `Double`.</span></span>

<span data-ttu-id="770ae-126">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="770ae-126">**Example**</span></span>

`SqlServer.ASIN(.9)`

## <a name="atanexpression"></a><span data-ttu-id="770ae-127">ATAN(Expression)</span><span class="sxs-lookup"><span data-stu-id="770ae-127">ATAN(expression)</span></span>

<span data-ttu-id="770ae-128">Zwraca arcus tangens wartości podanego wyrażenia liczbowego.</span><span class="sxs-lookup"><span data-stu-id="770ae-128">Returns the arctangent value of the specified numeric expression.</span></span>

<span data-ttu-id="770ae-129">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="770ae-129">**Arguments**</span></span>

<span data-ttu-id="770ae-130">`expression`: ELEMENT `Double`.</span><span class="sxs-lookup"><span data-stu-id="770ae-130">`expression`: A `Double`.</span></span>

<span data-ttu-id="770ae-131">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="770ae-131">**Return Value**</span></span>

<span data-ttu-id="770ae-132">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="770ae-132">A `Double`.</span></span>

<span data-ttu-id="770ae-133">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="770ae-133">**Example**</span></span>

`SqlServer.ATAN(9)`

## <a name="atn2expression-expression"></a><span data-ttu-id="770ae-134">ATN2(Expression, Expression)</span><span class="sxs-lookup"><span data-stu-id="770ae-134">ATN2(expression, expression)</span></span>

<span data-ttu-id="770ae-135">Zwraca kąt w radianach, którego tangens jest między dwoma określonych wyrażeń liczbowych.</span><span class="sxs-lookup"><span data-stu-id="770ae-135">Returns the angle, in radians, whose tangent is between the two specified numeric expressions.</span></span>

<span data-ttu-id="770ae-136">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="770ae-136">**Arguments**</span></span>

<span data-ttu-id="770ae-137">`expression`: ELEMENT `Double`.</span><span class="sxs-lookup"><span data-stu-id="770ae-137">`expression`: A `Double`.</span></span>

<span data-ttu-id="770ae-138">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="770ae-138">**Return Value**</span></span>

<span data-ttu-id="770ae-139">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="770ae-139">A `Double`.</span></span>

<span data-ttu-id="770ae-140">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="770ae-140">**Example**</span></span>

`SqlServer.ATN2(9, 8)`
 
## <a name="ceilingexpression"></a><span data-ttu-id="770ae-141">CEILING(Expression)</span><span class="sxs-lookup"><span data-stu-id="770ae-141">CEILING(expression)</span></span>

<span data-ttu-id="770ae-142">Konwertuje określony wyrażenie najmniejsza liczba całkowita, która jest większa niż lub równą jej.</span><span class="sxs-lookup"><span data-stu-id="770ae-142">Converts the specified expression to the smallest integer that is greater than or equal to it.</span></span>

<span data-ttu-id="770ae-143">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="770ae-143">**Arguments**</span></span>

<span data-ttu-id="770ae-144">`expression`: `Int32`, `Int64`, `Double`, Lub `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="770ae-144">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="770ae-145">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="770ae-145">**Return Value**</span></span>

<span data-ttu-id="770ae-146">`Int32`, `Int64`, `Double`, Lub `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="770ae-146">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="770ae-147">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="770ae-147">**Example**</span></span> 

[!code-csharp[DP EntityServices Concepts#SQLSERVER_CEILING](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_ceiling)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_ceiling)]

## <a name="cosexpression"></a><span data-ttu-id="770ae-148">COS(Expression)</span><span class="sxs-lookup"><span data-stu-id="770ae-148">COS(expression)</span></span>

<span data-ttu-id="770ae-149">Oblicza trygonometrycznych cosinus określonego kąta podany w radianach.</span><span class="sxs-lookup"><span data-stu-id="770ae-149">Calculates the trigonometric cosine of the specified angle in radians.</span></span> 

<span data-ttu-id="770ae-150">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="770ae-150">**Arguments**</span></span> 

<span data-ttu-id="770ae-151">`expression`: ELEMENT `Double`.</span><span class="sxs-lookup"><span data-stu-id="770ae-151">`expression`: A `Double`.</span></span> 

<span data-ttu-id="770ae-152">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="770ae-152">**Return Value**</span></span> 

<span data-ttu-id="770ae-153">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="770ae-153">A `Double`.</span></span> 

<span data-ttu-id="770ae-154">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="770ae-154">**Example**</span></span> 

`SqlServer.COS(45)`

## <a name="cotexpression"></a><span data-ttu-id="770ae-155">COT(Expression)</span><span class="sxs-lookup"><span data-stu-id="770ae-155">COT(expression)</span></span>

<span data-ttu-id="770ae-156">Oblicza trygonometrycznych cotangens kąta określonego w radianach.</span><span class="sxs-lookup"><span data-stu-id="770ae-156">Calculates the trigonometric cotangent of the specified angle in radians.</span></span> 

<span data-ttu-id="770ae-157">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="770ae-157">**Arguments**</span></span> 

<span data-ttu-id="770ae-158">`expression`: ELEMENT `Double`.</span><span class="sxs-lookup"><span data-stu-id="770ae-158">`expression`: A `Double`.</span></span> 

<span data-ttu-id="770ae-159">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="770ae-159">**Return Value**</span></span> 

<span data-ttu-id="770ae-160">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="770ae-160">A `Double`.</span></span> 

<span data-ttu-id="770ae-161">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="770ae-161">**Example**</span></span> 

`SqlServer.COT(60)`
  
## <a name="degreesradians"></a><span data-ttu-id="770ae-162">DEGREES(RADIANS)</span><span class="sxs-lookup"><span data-stu-id="770ae-162">DEGREES(radians)</span></span>

<span data-ttu-id="770ae-163">Zwraca odpowiedni kąt w stopniach.</span><span class="sxs-lookup"><span data-stu-id="770ae-163">Returns the corresponding angle in degrees.</span></span> 

<span data-ttu-id="770ae-164">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="770ae-164">**Arguments**</span></span> 

<span data-ttu-id="770ae-165">`expression`: `Int32`, `Int64`, `Double`, Lub `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="770ae-165">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="770ae-166">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="770ae-166">**Return Value**</span></span> 

<span data-ttu-id="770ae-167">`Int32`, `Int64`, `Double`, Lub `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="770ae-167">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="770ae-168">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="770ae-168">**Example**</span></span> 

`SqlServer.DEGREES(3.1)`

## <a name="expexpression"></a><span data-ttu-id="770ae-169">EXP(Expression)</span><span class="sxs-lookup"><span data-stu-id="770ae-169">EXP(expression)</span></span>

<span data-ttu-id="770ae-170">Oblicza wartość wykładniczą określonego wyrażenia liczbowego.</span><span class="sxs-lookup"><span data-stu-id="770ae-170">Calculates the exponential value of a specified numeric expression.</span></span> 

<span data-ttu-id="770ae-171">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="770ae-171">**Arguments**</span></span> 

<span data-ttu-id="770ae-172">`expression`: ELEMENT `Double`.</span><span class="sxs-lookup"><span data-stu-id="770ae-172">`expression`: A `Double`.</span></span> 

<span data-ttu-id="770ae-173">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="770ae-173">**Return Value**</span></span> 

<span data-ttu-id="770ae-174">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="770ae-174">A `Double`.</span></span> 

<span data-ttu-id="770ae-175">**Przykład** `SqlServer.EXP(1)`</span><span class="sxs-lookup"><span data-stu-id="770ae-175">**Example** `SqlServer.EXP(1)`</span></span>

## <a name="floorexpression"></a><span data-ttu-id="770ae-176">FLOOR(Expression)</span><span class="sxs-lookup"><span data-stu-id="770ae-176">FLOOR(expression)</span></span>

<span data-ttu-id="770ae-177">Konwertuje określony wyrażenie największą liczbą całkowitą mniejszą lub równą jej.</span><span class="sxs-lookup"><span data-stu-id="770ae-177">Converts the specified expression to the largest integer less than or equal to it.</span></span> 

<span data-ttu-id="770ae-178">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="770ae-178">**Arguments**</span></span> 

<span data-ttu-id="770ae-179">`expression`: ELEMENT `Double`.</span><span class="sxs-lookup"><span data-stu-id="770ae-179">`expression`: A `Double`.</span></span> 

<span data-ttu-id="770ae-180">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="770ae-180">**Return Value**</span></span> 

<span data-ttu-id="770ae-181">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="770ae-181">A `Double`.</span></span> 

<span data-ttu-id="770ae-182">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="770ae-182">**Example**</span></span> 

[!code-csharp[DP EntityServices Concepts#SQLSERVER_FLOOR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_floor)] 
[!code-sql[DP EntityServices Concepts#SQLSERVER_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_floor)]

## <a name="logexpression"></a><span data-ttu-id="770ae-183">LOG(Expression)</span><span class="sxs-lookup"><span data-stu-id="770ae-183">LOG(expression)</span></span>

<span data-ttu-id="770ae-184">Oblicza logarytm naturalny z określonym `float` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="770ae-184">Calculates the natural logarithm of the specified `float` expression.</span></span> 

<span data-ttu-id="770ae-185">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="770ae-185">**Arguments**</span></span> 

<span data-ttu-id="770ae-186">`expression`: ELEMENT `Double`.</span><span class="sxs-lookup"><span data-stu-id="770ae-186">`expression`: A `Double`.</span></span> 

<span data-ttu-id="770ae-187">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="770ae-187">**Return Value**</span></span> 

<span data-ttu-id="770ae-188">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="770ae-188">A `Double`.</span></span> 

<span data-ttu-id="770ae-189">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="770ae-189">**Example**</span></span> 

`SqlServer.LOG(100)`

## <a name="log10expression"></a><span data-ttu-id="770ae-190">LOG10(Expression)</span><span class="sxs-lookup"><span data-stu-id="770ae-190">LOG10(expression)</span></span>

<span data-ttu-id="770ae-191">Zwraca logarytm o podstawie base 10 określonego `Double` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="770ae-191">Returns the base-10 logarithm of the specified `Double` expression.</span></span> 

<span data-ttu-id="770ae-192">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="770ae-192">**Arguments**</span></span> 

<span data-ttu-id="770ae-193">`expression`: ELEMENT `Double`.</span><span class="sxs-lookup"><span data-stu-id="770ae-193">`expression`: A `Double`.</span></span> 

<span data-ttu-id="770ae-194">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="770ae-194">**Return Value**</span></span> 

<span data-ttu-id="770ae-195">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="770ae-195">A `Double`.</span></span> 

<span data-ttu-id="770ae-196">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="770ae-196">**Example**</span></span> 

`SqlServer.LOG10(100)`

## <a name="pi"></a><span data-ttu-id="770ae-197">PI()</span><span class="sxs-lookup"><span data-stu-id="770ae-197">PI()</span></span>

<span data-ttu-id="770ae-198">Zwraca wartość stała pi jako `Double`.</span><span class="sxs-lookup"><span data-stu-id="770ae-198">Returns the constant value of pi as a `Double`.</span></span> 

<span data-ttu-id="770ae-199">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="770ae-199">**Return Value**</span></span> 

<span data-ttu-id="770ae-200">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="770ae-200">A `Double`.</span></span> 

<span data-ttu-id="770ae-201">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="770ae-201">**Example**</span></span> 

`SqlServer.PI()`

## <a name="powernumericexpression-powerexpression"></a><span data-ttu-id="770ae-202">ZASILANIA (numeric_expression, power_expression)</span><span class="sxs-lookup"><span data-stu-id="770ae-202">POWER(numeric_expression, power_expression)</span></span>

<span data-ttu-id="770ae-203">Oblicza wartość określone wyrażenie do określonej potęgi.</span><span class="sxs-lookup"><span data-stu-id="770ae-203">Calculates the value of a specified expression to a specified power.</span></span>

<span data-ttu-id="770ae-204">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="770ae-204">**Arguments**</span></span> 

|  |  |
|--|--|
|`numeric_expression`| <span data-ttu-id="770ae-205">`Int32`, `Int64`, `Double`, Lub `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="770ae-205">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>|
|`power_expression`| <span data-ttu-id="770ae-206">A `Double` reprezentujący zasilania, do którego zostanie wywołane `numeric_expression`.</span><span class="sxs-lookup"><span data-stu-id="770ae-206">A `Double` that represents the power to which to raise the `numeric_expression`.</span></span>| 

<span data-ttu-id="770ae-207">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="770ae-207">**Return Value**</span></span> 

<span data-ttu-id="770ae-208">Wartość określonego `numeric_expression` określonej `power_expression`.</span><span class="sxs-lookup"><span data-stu-id="770ae-208">The value of the specified `numeric_expression` to the specified `power_expression`.</span></span> 

<span data-ttu-id="770ae-209">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="770ae-209">**Example**</span></span> 

`SqlServer.POWER(2,7)`

## <a name="radiansexpression"></a><span data-ttu-id="770ae-210">RADIANS(Expression)</span><span class="sxs-lookup"><span data-stu-id="770ae-210">RADIANS(expression)</span></span>

<span data-ttu-id="770ae-211">Konwertuje stopnie na radiany.</span><span class="sxs-lookup"><span data-stu-id="770ae-211">Converts degrees to radians.</span></span> 

<span data-ttu-id="770ae-212">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="770ae-212">**Arguments**</span></span> 

<span data-ttu-id="770ae-213">`expression`: `Int32`, `Int64`, `Double`, Lub `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="770ae-213">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="770ae-214">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="770ae-214">**Return Value**</span></span> 

<span data-ttu-id="770ae-215">`Int32`, `Int64`, `Double`, Lub `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="770ae-215">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="770ae-216">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="770ae-216">**Example**</span></span> 

`SqlServer.RADIANS(360.0)`

## <a name="randseed"></a><span data-ttu-id="770ae-217">RAND([seed])</span><span class="sxs-lookup"><span data-stu-id="770ae-217">RAND([seed])</span></span>

<span data-ttu-id="770ae-218">Zwraca wartość losową z zakresu od 0 do 1.</span><span class="sxs-lookup"><span data-stu-id="770ae-218">Returns a random value from 0 through 1.</span></span> 

<span data-ttu-id="770ae-219">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="770ae-219">**Arguments**</span></span> 

<span data-ttu-id="770ae-220">Wartość początkową jako `Int32`.</span><span class="sxs-lookup"><span data-stu-id="770ae-220">The seed value as an `Int32`.</span></span> <span data-ttu-id="770ae-221">Jeśli zalążek nie zostanie określony, aparatu bazy danych programu SQL Server w losowo wybranym momencie przypisuje wartość inicjatora.</span><span class="sxs-lookup"><span data-stu-id="770ae-221">If the seed is not specified, the SQL Server Database Engine assigns a seed value at random.</span></span> <span data-ttu-id="770ae-222">Wartości inicjatora określona zwracana jest zawsze taki sam.</span><span class="sxs-lookup"><span data-stu-id="770ae-222">For a specified seed value, the result returned is always the same.</span></span>

<span data-ttu-id="770ae-223">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="770ae-223">**Return Value**</span></span> 

<span data-ttu-id="770ae-224">Losowe `Double` wartość od 0 do 1.</span><span class="sxs-lookup"><span data-stu-id="770ae-224">A random `Double` value from 0 through 1.</span></span> 

<span data-ttu-id="770ae-225">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="770ae-225">**Example**</span></span> 

`SqlServer.RAND()`
  
## <a name="roundnumericexpression-lengthfunction"></a><span data-ttu-id="770ae-226">ROUND(Numeric_Expression, length[,Function])</span><span class="sxs-lookup"><span data-stu-id="770ae-226">ROUND(numeric_expression, length[,function])</span></span>

<span data-ttu-id="770ae-227">Zwraca wartość wyrażenia liczbowego zaokrąglone do określonej długości lub dokładności.</span><span class="sxs-lookup"><span data-stu-id="770ae-227">Returns a numeric expression, rounded to the specified length or precision.</span></span> 

<span data-ttu-id="770ae-228">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="770ae-228">**Arguments**</span></span> 

|  |  |
|--|--|
|`numeric_expression`| <span data-ttu-id="770ae-229">`Int32`, `Int64`, `Double`, Lub `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="770ae-229">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 
|`length`| <span data-ttu-id="770ae-230">`Int32` Reprezentujący dokładność, do którego `numeric_expression` ma zostać zaokrąglona.</span><span class="sxs-lookup"><span data-stu-id="770ae-230">An `Int32` that represents the precision to which `numeric_expression` is to be rounded.</span></span> <span data-ttu-id="770ae-231">Gdy `length` jest liczbą dodatnią `numeric_expression` jest zaokrąglana do liczby miejsc dziesiętnych określonej przez `length`.</span><span class="sxs-lookup"><span data-stu-id="770ae-231">When `length` is a positive number, `numeric_expression` is rounded to the number of decimal positions specified by `length`.</span></span> <span data-ttu-id="770ae-232">Gdy `length` jest liczbą ujemną `numeric_expression` jest zaokrąglana po lewej stronie przecinka dziesiętnego, określony przez `length`.</span><span class="sxs-lookup"><span data-stu-id="770ae-232">When `length` is a negative number, `numeric_expression` is rounded on the left side of the decimal point, as specified by `length`.</span></span>|
|`function` | <span data-ttu-id="770ae-233">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="770ae-233">Optional.</span></span> <span data-ttu-id="770ae-234">`Int32` Reprezentujący typ operacji do wykonania.</span><span class="sxs-lookup"><span data-stu-id="770ae-234">An `Int32` that represents the type of operation to perform.</span></span> <span data-ttu-id="770ae-235">Gdy funkcja zostanie pominięty lub ma wartość 0 (domyślnie), `numeric_expression` jest zaokrąglana.</span><span class="sxs-lookup"><span data-stu-id="770ae-235">When function is omitted or has a value of 0 (default), `numeric_expression` is rounded.</span></span> <span data-ttu-id="770ae-236">Gdy wartość inną niż określono wartość 0, `numeric_expression` zostały obcięte.</span><span class="sxs-lookup"><span data-stu-id="770ae-236">When a value other than 0 is specified, `numeric_expression` is truncated.</span></span> |

<span data-ttu-id="770ae-237">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="770ae-237">**Return Value**</span></span> 

<span data-ttu-id="770ae-238">Wartość określonego `numeric_expression` określonej `power_expression`.</span><span class="sxs-lookup"><span data-stu-id="770ae-238">The value of the specified `numeric_expression` to the specified `power_expression`.</span></span>

<span data-ttu-id="770ae-239">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="770ae-239">**Example**</span></span> 

`SqlServer.ROUND(748.58, -3)`

## <a name="signexpression"></a><span data-ttu-id="770ae-240">SIGN(Expression)</span><span class="sxs-lookup"><span data-stu-id="770ae-240">SIGN(expression)</span></span> 

<span data-ttu-id="770ae-241">Zwraca wynik dodatni (+ 1), wartość zero (0) lub minus (-1) z określonego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="770ae-241">Returns the positive (+1), zero (0), or negative (-1) sign of the specified expression.</span></span> 

<span data-ttu-id="770ae-242">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="770ae-242">**Arguments**</span></span> 

<span data-ttu-id="770ae-243">`expression`: `Int32`, `Int64`, `Double`, lub `Decimal`</span><span class="sxs-lookup"><span data-stu-id="770ae-243">`expression`: `Int32`, `Int64`, `Double`, or `Decimal`</span></span> 

<span data-ttu-id="770ae-244">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="770ae-244">**Return Value**</span></span> 

<span data-ttu-id="770ae-245">`Int32`, `Int64`, `Double`, Lub `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="770ae-245">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="770ae-246">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="770ae-246">**Example**</span></span> 

`SqlServer.SIGN(-10)`

## <a name="sinexpression"></a><span data-ttu-id="770ae-247">SIN(Expression)</span><span class="sxs-lookup"><span data-stu-id="770ae-247">SIN(expression)</span></span>

<span data-ttu-id="770ae-248">Oblicza trygonometrycznych sinus określonego kąta podany w radianach, a następnie zwraca `Double` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="770ae-248">Calculates the trigonometric sine of the specified angle in radians, and returns a `Double` expression.</span></span> 

<span data-ttu-id="770ae-249">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="770ae-249">**Arguments**</span></span> 

<span data-ttu-id="770ae-250">`expression`: ELEMENT `Double`.</span><span class="sxs-lookup"><span data-stu-id="770ae-250">`expression`: A `Double`.</span></span> 

<span data-ttu-id="770ae-251">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="770ae-251">**Return Value**</span></span> 

<span data-ttu-id="770ae-252">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="770ae-252">A `Double`.</span></span> 

<span data-ttu-id="770ae-253">**Przykład** `SqlServer.SIN(20)`</span><span class="sxs-lookup"><span data-stu-id="770ae-253">**Example** `SqlServer.SIN(20)`</span></span>

## <a name="sqrtexpression"></a><span data-ttu-id="770ae-254">SQRT(Expression)</span><span class="sxs-lookup"><span data-stu-id="770ae-254">SQRT(expression)</span></span>

<span data-ttu-id="770ae-255">Zwraca pierwiastek kwadratowy z określonego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="770ae-255">Returns the square root of the specified expression.</span></span> 

<span data-ttu-id="770ae-256">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="770ae-256">**Arguments**</span></span> 

<span data-ttu-id="770ae-257">`expression`: ELEMENT `Double`.</span><span class="sxs-lookup"><span data-stu-id="770ae-257">`expression`: A `Double`.</span></span> 

<span data-ttu-id="770ae-258">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="770ae-258">**Return Value**</span></span> 

<span data-ttu-id="770ae-259">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="770ae-259">A `Double`.</span></span> 

<span data-ttu-id="770ae-260">**Przykład** `SqlServer.SQRT(3600)`</span><span class="sxs-lookup"><span data-stu-id="770ae-260">**Example** `SqlServer.SQRT(3600)`</span></span>

## <a name="squareexpression"></a><span data-ttu-id="770ae-261">SQUARE(Expression)</span><span class="sxs-lookup"><span data-stu-id="770ae-261">SQUARE(expression)</span></span>

<span data-ttu-id="770ae-262">Zwraca kwadrat określone wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="770ae-262">Returns the square of the specified expression.</span></span> 

<span data-ttu-id="770ae-263">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="770ae-263">**Arguments**</span></span> 

<span data-ttu-id="770ae-264">`expression`: ELEMENT `Double`.</span><span class="sxs-lookup"><span data-stu-id="770ae-264">`expression`: A `Double`.</span></span> 

<span data-ttu-id="770ae-265">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="770ae-265">**Return Value**</span></span> 

<span data-ttu-id="770ae-266">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="770ae-266">A `Double`.</span></span> 

<span data-ttu-id="770ae-267">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="770ae-267">**Example**</span></span> 

`SqlServer.SQUARE(25)`

## <a name="tanexpression"></a><span data-ttu-id="770ae-268">Tan(Expression)</span><span class="sxs-lookup"><span data-stu-id="770ae-268">TAN(expression)</span></span>

<span data-ttu-id="770ae-269">Oblicza tangens określonego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="770ae-269">Calculates the tangent of a specified expression.</span></span>

<span data-ttu-id="770ae-270">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="770ae-270">**Arguments**</span></span> 

<span data-ttu-id="770ae-271">`expression`: `Double`</span><span class="sxs-lookup"><span data-stu-id="770ae-271">`expression`: `Double`</span></span> 

<span data-ttu-id="770ae-272">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="770ae-272">**Return Value**</span></span> 

`Double` 

<span data-ttu-id="770ae-273">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="770ae-273">**Example**</span></span> 

`SqlServer.TAN(45.0)`
  
## <a name="see-also"></a><span data-ttu-id="770ae-274">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="770ae-274">See also</span></span>

<span data-ttu-id="770ae-275">Aby uzyskać więcej informacji na temat funkcji matematycznych, które obsługuje klient SQL zobacz dokumentację dla używanej wersji programu SQL Server określonego w manifeście dostawcy SqlClient:</span><span class="sxs-lookup"><span data-stu-id="770ae-275">For more information about the mathematical functions that SqlClient supports, see the documentation for the SQL Server version that you specified in the SqlClient provider manifest:</span></span>  
  
<span data-ttu-id="770ae-276">**Program SQL Server 2005:** [funkcje matematyczne (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms177516(v=sql.90))</span><span class="sxs-lookup"><span data-stu-id="770ae-276">**SQL Server 2005:** [Mathematical Functions (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms177516(v=sql.90))</span></span>  
<span data-ttu-id="770ae-277">**Program SQL Server 2008:** [funkcje matematyczne (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms177516(v=sql.100))</span><span class="sxs-lookup"><span data-stu-id="770ae-277">**SQL Server 2008:** [Mathematical Functions (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms177516(v=sql.100))</span></span>  
<span data-ttu-id="770ae-278">**Program SQL Server 2012 lub nowszy:** [funkcje matematyczne (Transact-SQL)](/sql/t-sql/functions/mathematical-functions-transact-sql?view=sql-server-2017)</span><span class="sxs-lookup"><span data-stu-id="770ae-278">**SQL Server 2012 and later:** [Mathematical Functions (Transact-SQL)](/sql/t-sql/functions/mathematical-functions-transact-sql?view=sql-server-2017)</span></span>   

 [<span data-ttu-id="770ae-279">Klient SQL dla funkcji programu Entity Framework</span><span class="sxs-lookup"><span data-stu-id="770ae-279">SqlClient for Entity Framework Functions</span></span>](sqlclient-for-ef-functions.md)
