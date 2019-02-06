---
title: Funkcje matematyczne
ms.date: 03/30/2017
ms.assetid: b040c7cb-156d-40f2-9152-61065b18148c
ms.openlocfilehash: b6f248382f069df59a55e85e9a764b0df700fb26
ms.sourcegitcommit: 01ea420eaa4bf76d5fc47673294c8881379b3369
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/06/2019
ms.locfileid: "55759382"
---
# <a name="mathematical-functions"></a><span data-ttu-id="97a43-102">Funkcje matematyczne</span><span class="sxs-lookup"><span data-stu-id="97a43-102">Mathematical Functions</span></span>

<span data-ttu-id="97a43-103">.NET Framework Data Provider for SQL Server (SqlClient) zapewnia funkcje matematyczne, które wykonują obliczenia na wartości wejściowych, które są przekazywane jako argumenty i zwraca wynik wartość liczbową.</span><span class="sxs-lookup"><span data-stu-id="97a43-103">The .NET Framework Data Provider for SQL Server (SqlClient) provides math functions that perform calculations on input values that are provided as arguments, and return a numeric value result.</span></span> <span data-ttu-id="97a43-104">Te funkcje są w przestrzeni nazw SqlServer, który jest dostępny, gdy używasz SqlClient.</span><span class="sxs-lookup"><span data-stu-id="97a43-104">These functions are in the SqlServer namespace, which is available when you use SqlClient.</span></span> <span data-ttu-id="97a43-105">Właściwość przestrzeni nazw dostawcy umożliwia programu Entity Framework dowiedzieć się, który prefiks jest używany przez tego dostawcę dla określonego konstrukcji, takich jak typy i funkcje.</span><span class="sxs-lookup"><span data-stu-id="97a43-105">A provider's namespace property allows the Entity Framework to discover which prefix is used by this provider for specific constructs, such as types and functions.</span></span> <span data-ttu-id="97a43-106">W poniższej tabeli opisano funkcje matematyczne SqlClient.</span><span class="sxs-lookup"><span data-stu-id="97a43-106">The following table describes the SqlClient math functions.</span></span>  
  
## <a name="absexpression"></a><span data-ttu-id="97a43-107">ABS(Expression)</span><span class="sxs-lookup"><span data-stu-id="97a43-107">ABS(expression)</span></span>

<span data-ttu-id="97a43-108">Wykonuje funkcję wartości bezwzględnej.</span><span class="sxs-lookup"><span data-stu-id="97a43-108">Performs the absolute value function.</span></span>

<span data-ttu-id="97a43-109">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="97a43-109">**Arguments**</span></span>

<span data-ttu-id="97a43-110">`expression`: `Int32`, `Int64`, `Double`, Lub `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="97a43-110">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="97a43-111">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="97a43-111">**Return Value**</span></span>

<span data-ttu-id="97a43-112">Wartość bezwzględna z określonego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="97a43-112">The absolute value of the specified expression.</span></span>

<span data-ttu-id="97a43-113">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="97a43-113">**Example**</span></span>

`SqlServer.ABS(-2)`

## <a name="acosexpression"></a><span data-ttu-id="97a43-114">ACOS(Expression)</span><span class="sxs-lookup"><span data-stu-id="97a43-114">ACOS(expression)</span></span>

<span data-ttu-id="97a43-115">Zwraca arcus cosinus wartości podanego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="97a43-115">Returns the arccosine value of the specified expression.</span></span>

<span data-ttu-id="97a43-116">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="97a43-116">**Arguments**</span></span>

<span data-ttu-id="97a43-117">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="97a43-117">`expression`: A `Double`.</span></span>

<span data-ttu-id="97a43-118">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="97a43-118">**Return Value**</span></span>

<span data-ttu-id="97a43-119">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="97a43-119">A `Double`.</span></span>

<span data-ttu-id="97a43-120">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="97a43-120">**Example**</span></span>

`SqlServer.ACOS(.9)`

## <a name="asinexpression"></a><span data-ttu-id="97a43-121">ASIN(Expression)</span><span class="sxs-lookup"><span data-stu-id="97a43-121">ASIN(expression)</span></span>

<span data-ttu-id="97a43-122">Zwraca arcus sinus wartości podanego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="97a43-122">Returns the arcsine value of the specified expression.</span></span>

<span data-ttu-id="97a43-123">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="97a43-123">**Arguments**</span></span>

<span data-ttu-id="97a43-124">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="97a43-124">`expression`: A `Double`.</span></span>

<span data-ttu-id="97a43-125">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="97a43-125">**Return Value**</span></span>

<span data-ttu-id="97a43-126">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="97a43-126">A `Double`.</span></span>

<span data-ttu-id="97a43-127">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="97a43-127">**Example**</span></span>

`SqlServer.ASIN(.9)`

## <a name="atanexpression"></a><span data-ttu-id="97a43-128">ATAN(Expression)</span><span class="sxs-lookup"><span data-stu-id="97a43-128">ATAN(expression)</span></span>

<span data-ttu-id="97a43-129">Zwraca arcus tangens wartości podanego wyrażenia liczbowego.</span><span class="sxs-lookup"><span data-stu-id="97a43-129">Returns the arctangent value of the specified numeric expression.</span></span>

<span data-ttu-id="97a43-130">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="97a43-130">**Arguments**</span></span>

<span data-ttu-id="97a43-131">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="97a43-131">`expression`: A `Double`.</span></span>

<span data-ttu-id="97a43-132">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="97a43-132">**Return Value**</span></span>

<span data-ttu-id="97a43-133">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="97a43-133">A `Double`.</span></span>

<span data-ttu-id="97a43-134">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="97a43-134">**Example**</span></span>

`SqlServer.ATAN(9)`

## <a name="atn2expression-expression"></a><span data-ttu-id="97a43-135">ATN2(Expression, Expression)</span><span class="sxs-lookup"><span data-stu-id="97a43-135">ATN2(expression, expression)</span></span>

<span data-ttu-id="97a43-136">Zwraca kąt w radianach, którego tangens jest między dwoma określonych wyrażeń liczbowych.</span><span class="sxs-lookup"><span data-stu-id="97a43-136">Returns the angle, in radians, whose tangent is between the two specified numeric expressions.</span></span>

<span data-ttu-id="97a43-137">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="97a43-137">**Arguments**</span></span>

<span data-ttu-id="97a43-138">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="97a43-138">`expression`: A `Double`.</span></span>

<span data-ttu-id="97a43-139">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="97a43-139">**Return Value**</span></span>

<span data-ttu-id="97a43-140">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="97a43-140">A `Double`.</span></span>

<span data-ttu-id="97a43-141">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="97a43-141">**Example**</span></span>

`SqlServer.ATN2(9, 8)`
 
## <a name="ceilingexpression"></a><span data-ttu-id="97a43-142">CEILING(Expression)</span><span class="sxs-lookup"><span data-stu-id="97a43-142">CEILING(expression)</span></span>

<span data-ttu-id="97a43-143">Konwertuje określony wyrażenie najmniejsza liczba całkowita, która jest większa niż lub równą jej.</span><span class="sxs-lookup"><span data-stu-id="97a43-143">Converts the specified expression to the smallest integer that is greater than or equal to it.</span></span>

<span data-ttu-id="97a43-144">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="97a43-144">**Arguments**</span></span>

<span data-ttu-id="97a43-145">`expression`: `Int32`, `Int64`, `Double`, Lub `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="97a43-145">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="97a43-146">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="97a43-146">**Return Value**</span></span>

<span data-ttu-id="97a43-147">`Int32`, `Int64`, `Double`, Lub `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="97a43-147">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="97a43-148">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="97a43-148">**Example**</span></span> 

[!code-csharp[DP EntityServices Concepts#SQLSERVER_CEILING](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_ceiling)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_ceiling)]

## <a name="cosexpression"></a><span data-ttu-id="97a43-149">COS(Expression)</span><span class="sxs-lookup"><span data-stu-id="97a43-149">COS(expression)</span></span>

<span data-ttu-id="97a43-150">Oblicza trygonometrycznych cosinus określonego kąta podany w radianach.</span><span class="sxs-lookup"><span data-stu-id="97a43-150">Calculates the trigonometric cosine of the specified angle in radians.</span></span> 

<span data-ttu-id="97a43-151">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="97a43-151">**Arguments**</span></span> 

<span data-ttu-id="97a43-152">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="97a43-152">`expression`: A `Double`.</span></span> 

<span data-ttu-id="97a43-153">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="97a43-153">**Return Value**</span></span> 

<span data-ttu-id="97a43-154">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="97a43-154">A `Double`.</span></span> 

<span data-ttu-id="97a43-155">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="97a43-155">**Example**</span></span> 

`SqlServer.COS(45)`

## <a name="cotexpression"></a><span data-ttu-id="97a43-156">COT(Expression)</span><span class="sxs-lookup"><span data-stu-id="97a43-156">COT(expression)</span></span>

<span data-ttu-id="97a43-157">Oblicza trygonometrycznych cotangens kąta określonego w radianach.</span><span class="sxs-lookup"><span data-stu-id="97a43-157">Calculates the trigonometric cotangent of the specified angle in radians.</span></span> 

<span data-ttu-id="97a43-158">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="97a43-158">**Arguments**</span></span> 

<span data-ttu-id="97a43-159">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="97a43-159">`expression`: A `Double`.</span></span> 

<span data-ttu-id="97a43-160">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="97a43-160">**Return Value**</span></span> 

<span data-ttu-id="97a43-161">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="97a43-161">A `Double`.</span></span> 

<span data-ttu-id="97a43-162">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="97a43-162">**Example**</span></span> 

`SqlServer.COT(60)`
  
## <a name="degreesradians"></a><span data-ttu-id="97a43-163">DEGREES(RADIANS)</span><span class="sxs-lookup"><span data-stu-id="97a43-163">DEGREES(radians)</span></span>

<span data-ttu-id="97a43-164">Zwraca odpowiedni kąt w stopniach.</span><span class="sxs-lookup"><span data-stu-id="97a43-164">Returns the corresponding angle in degrees.</span></span> 

<span data-ttu-id="97a43-165">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="97a43-165">**Arguments**</span></span> 

<span data-ttu-id="97a43-166">`expression`: `Int32`, `Int64`, `Double`, Lub `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="97a43-166">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="97a43-167">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="97a43-167">**Return Value**</span></span> 

<span data-ttu-id="97a43-168">`Int32`, `Int64`, `Double`, Lub `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="97a43-168">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="97a43-169">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="97a43-169">**Example**</span></span> 

`SqlServer.DEGREES(3.1)`

## <a name="expexpression"></a><span data-ttu-id="97a43-170">EXP(Expression)</span><span class="sxs-lookup"><span data-stu-id="97a43-170">EXP(expression)</span></span>

<span data-ttu-id="97a43-171">Oblicza wartość wykładniczą określonego wyrażenia liczbowego.</span><span class="sxs-lookup"><span data-stu-id="97a43-171">Calculates the exponential value of a specified numeric expression.</span></span> 

<span data-ttu-id="97a43-172">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="97a43-172">**Arguments**</span></span> 

<span data-ttu-id="97a43-173">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="97a43-173">`expression`: A `Double`.</span></span> 

<span data-ttu-id="97a43-174">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="97a43-174">**Return Value**</span></span> 

<span data-ttu-id="97a43-175">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="97a43-175">A `Double`.</span></span> 

<span data-ttu-id="97a43-176">**Przykład** `SqlServer.EXP(1)`</span><span class="sxs-lookup"><span data-stu-id="97a43-176">**Example** `SqlServer.EXP(1)`</span></span>

## <a name="floorexpression"></a><span data-ttu-id="97a43-177">FLOOR(Expression)</span><span class="sxs-lookup"><span data-stu-id="97a43-177">FLOOR(expression)</span></span>

<span data-ttu-id="97a43-178">Konwertuje określony wyrażenie największą liczbą całkowitą mniejszą lub równą jej.</span><span class="sxs-lookup"><span data-stu-id="97a43-178">Converts the specified expression to the largest integer less than or equal to it.</span></span> 

<span data-ttu-id="97a43-179">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="97a43-179">**Arguments**</span></span> 

<span data-ttu-id="97a43-180">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="97a43-180">`expression`: A `Double`.</span></span> 

<span data-ttu-id="97a43-181">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="97a43-181">**Return Value**</span></span> 

<span data-ttu-id="97a43-182">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="97a43-182">A `Double`.</span></span> 

<span data-ttu-id="97a43-183">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="97a43-183">**Example**</span></span> 

[!code-csharp[DP EntityServices Concepts#SQLSERVER_FLOOR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_floor)] 
[!code-sql[DP EntityServices Concepts#SQLSERVER_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_floor)]

## <a name="logexpression"></a><span data-ttu-id="97a43-184">LOG(Expression)</span><span class="sxs-lookup"><span data-stu-id="97a43-184">LOG(expression)</span></span>

<span data-ttu-id="97a43-185">Oblicza logarytm naturalny z określonym `float` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="97a43-185">Calculates the natural logarithm of the specified `float` expression.</span></span> 

<span data-ttu-id="97a43-186">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="97a43-186">**Arguments**</span></span> 

<span data-ttu-id="97a43-187">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="97a43-187">`expression`: A `Double`.</span></span> 

<span data-ttu-id="97a43-188">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="97a43-188">**Return Value**</span></span> 

<span data-ttu-id="97a43-189">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="97a43-189">A `Double`.</span></span> 

<span data-ttu-id="97a43-190">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="97a43-190">**Example**</span></span> 

`SqlServer.LOG(100)`

## <a name="log10expression"></a><span data-ttu-id="97a43-191">LOG10(Expression)</span><span class="sxs-lookup"><span data-stu-id="97a43-191">LOG10(expression)</span></span>

<span data-ttu-id="97a43-192">Zwraca logarytm o podstawie base 10 określonego `Double` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="97a43-192">Returns the base-10 logarithm of the specified `Double` expression.</span></span> 

<span data-ttu-id="97a43-193">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="97a43-193">**Arguments**</span></span> 

<span data-ttu-id="97a43-194">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="97a43-194">`expression`: A `Double`.</span></span> 

<span data-ttu-id="97a43-195">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="97a43-195">**Return Value**</span></span> 

<span data-ttu-id="97a43-196">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="97a43-196">A `Double`.</span></span> 

<span data-ttu-id="97a43-197">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="97a43-197">**Example**</span></span> 

`SqlServer.LOG10(100)`

## <a name="pi"></a><span data-ttu-id="97a43-198">PI()</span><span class="sxs-lookup"><span data-stu-id="97a43-198">PI()</span></span>

<span data-ttu-id="97a43-199">Zwraca wartość stała pi jako `Double`.</span><span class="sxs-lookup"><span data-stu-id="97a43-199">Returns the constant value of pi as a `Double`.</span></span> 

<span data-ttu-id="97a43-200">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="97a43-200">**Return Value**</span></span> 

<span data-ttu-id="97a43-201">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="97a43-201">A `Double`.</span></span> 

<span data-ttu-id="97a43-202">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="97a43-202">**Example**</span></span> 

`SqlServer.PI()`

## <a name="powernumericexpression-powerexpression"></a><span data-ttu-id="97a43-203">ZASILANIA (numeric_expression, power_expression)</span><span class="sxs-lookup"><span data-stu-id="97a43-203">POWER(numeric_expression, power_expression)</span></span>

<span data-ttu-id="97a43-204">Oblicza wartość określone wyrażenie do określonej potęgi.</span><span class="sxs-lookup"><span data-stu-id="97a43-204">Calculates the value of a specified expression to a specified power.</span></span>

<span data-ttu-id="97a43-205">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="97a43-205">**Arguments**</span></span> 

|  |  |
|--|--|
|`numeric_expression`| <span data-ttu-id="97a43-206">`Int32`, `Int64`, `Double`, Lub `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="97a43-206">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>|
|`power_expression`| <span data-ttu-id="97a43-207">A `Double` reprezentujący zasilania, do którego zostanie wywołane `numeric_expression`.</span><span class="sxs-lookup"><span data-stu-id="97a43-207">A `Double` that represents the power to which to raise the `numeric_expression`.</span></span>| 

<span data-ttu-id="97a43-208">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="97a43-208">**Return Value**</span></span> 

<span data-ttu-id="97a43-209">Wartość określonego `numeric_expression` określonej `power_expression`.</span><span class="sxs-lookup"><span data-stu-id="97a43-209">The value of the specified `numeric_expression` to the specified `power_expression`.</span></span> 

<span data-ttu-id="97a43-210">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="97a43-210">**Example**</span></span> 

`SqlServer.POWER(2,7)`

## <a name="radiansexpression"></a><span data-ttu-id="97a43-211">RADIANS(Expression)</span><span class="sxs-lookup"><span data-stu-id="97a43-211">RADIANS(expression)</span></span>

<span data-ttu-id="97a43-212">Konwertuje stopnie na radiany.</span><span class="sxs-lookup"><span data-stu-id="97a43-212">Converts degrees to radians.</span></span> 

<span data-ttu-id="97a43-213">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="97a43-213">**Arguments**</span></span> 

<span data-ttu-id="97a43-214">`expression`: `Int32`, `Int64`, `Double`, Lub `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="97a43-214">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="97a43-215">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="97a43-215">**Return Value**</span></span> 

<span data-ttu-id="97a43-216">`Int32`, `Int64`, `Double`, Lub `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="97a43-216">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="97a43-217">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="97a43-217">**Example**</span></span> 

`SqlServer.RADIANS(360.0)`

## <a name="randseed"></a><span data-ttu-id="97a43-218">RAND([seed])</span><span class="sxs-lookup"><span data-stu-id="97a43-218">RAND([seed])</span></span>

<span data-ttu-id="97a43-219">Zwraca wartość losową z zakresu od 0 do 1.</span><span class="sxs-lookup"><span data-stu-id="97a43-219">Returns a random value from 0 through 1.</span></span> 

<span data-ttu-id="97a43-220">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="97a43-220">**Arguments**</span></span> 

<span data-ttu-id="97a43-221">Wartość początkową jako `Int32`.</span><span class="sxs-lookup"><span data-stu-id="97a43-221">The seed value as an `Int32`.</span></span> <span data-ttu-id="97a43-222">Jeśli zalążek nie zostanie określony, aparatu bazy danych programu SQL Server w losowo wybranym momencie przypisuje wartość inicjatora.</span><span class="sxs-lookup"><span data-stu-id="97a43-222">If the seed is not specified, the SQL Server Database Engine assigns a seed value at random.</span></span> <span data-ttu-id="97a43-223">Wartości inicjatora określona zwracana jest zawsze taki sam.</span><span class="sxs-lookup"><span data-stu-id="97a43-223">For a specified seed value, the result returned is always the same.</span></span>

<span data-ttu-id="97a43-224">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="97a43-224">**Return Value**</span></span> 

<span data-ttu-id="97a43-225">Losowe `Double` wartość od 0 do 1.</span><span class="sxs-lookup"><span data-stu-id="97a43-225">A random `Double` value from 0 through 1.</span></span> 

<span data-ttu-id="97a43-226">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="97a43-226">**Example**</span></span> 

`SqlServer.RAND()`
  
## <a name="roundnumericexpression-lengthfunction"></a><span data-ttu-id="97a43-227">ROUND(Numeric_Expression, length[,Function])</span><span class="sxs-lookup"><span data-stu-id="97a43-227">ROUND(numeric_expression, length[,function])</span></span>

<span data-ttu-id="97a43-228">Zwraca wartość wyrażenia liczbowego zaokrąglone do określonej długości lub dokładności.</span><span class="sxs-lookup"><span data-stu-id="97a43-228">Returns a numeric expression, rounded to the specified length or precision.</span></span> 

<span data-ttu-id="97a43-229">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="97a43-229">**Arguments**</span></span> 

|  |  |
|--|--|
|`numeric_expression`| <span data-ttu-id="97a43-230">`Int32`, `Int64`, `Double`, Lub `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="97a43-230">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 
|`length`| <span data-ttu-id="97a43-231">`Int32` Reprezentujący dokładność, do którego `numeric_expression` ma zostać zaokrąglona.</span><span class="sxs-lookup"><span data-stu-id="97a43-231">An `Int32` that represents the precision to which `numeric_expression` is to be rounded.</span></span> <span data-ttu-id="97a43-232">Gdy `length` jest liczbą dodatnią `numeric_expression` jest zaokrąglana do liczby miejsc dziesiętnych określonej przez `length`.</span><span class="sxs-lookup"><span data-stu-id="97a43-232">When `length` is a positive number, `numeric_expression` is rounded to the number of decimal positions specified by `length`.</span></span> <span data-ttu-id="97a43-233">Gdy `length` jest liczbą ujemną `numeric_expression` jest zaokrąglana po lewej stronie przecinka dziesiętnego, określony przez `length`.</span><span class="sxs-lookup"><span data-stu-id="97a43-233">When `length` is a negative number, `numeric_expression` is rounded on the left side of the decimal point, as specified by `length`.</span></span>|
|`function` | <span data-ttu-id="97a43-234">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="97a43-234">Optional.</span></span> <span data-ttu-id="97a43-235">`Int32` Reprezentujący typ operacji do wykonania.</span><span class="sxs-lookup"><span data-stu-id="97a43-235">An `Int32` that represents the type of operation to perform.</span></span> <span data-ttu-id="97a43-236">Gdy funkcja zostanie pominięty lub ma wartość 0 (domyślnie), `numeric_expression` jest zaokrąglana.</span><span class="sxs-lookup"><span data-stu-id="97a43-236">When function is omitted or has a value of 0 (default), `numeric_expression` is rounded.</span></span> <span data-ttu-id="97a43-237">Gdy wartość inną niż określono wartość 0, `numeric_expression` zostały obcięte.</span><span class="sxs-lookup"><span data-stu-id="97a43-237">When a value other than 0 is specified, `numeric_expression` is truncated.</span></span> |

<span data-ttu-id="97a43-238">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="97a43-238">**Return Value**</span></span> 

<span data-ttu-id="97a43-239">Wartość określonego `numeric_expression` określonej `power_expression`.</span><span class="sxs-lookup"><span data-stu-id="97a43-239">The value of the specified `numeric_expression` to the specified `power_expression`.</span></span>

<span data-ttu-id="97a43-240">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="97a43-240">**Example**</span></span> 

`SqlServer.ROUND(748.58, -3)`

## <a name="signexpression"></a><span data-ttu-id="97a43-241">SIGN(Expression)</span><span class="sxs-lookup"><span data-stu-id="97a43-241">SIGN(expression)</span></span> 

<span data-ttu-id="97a43-242">Zwraca wynik dodatni (+ 1), wartość zero (0) lub minus (-1) z określonego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="97a43-242">Returns the positive (+1), zero (0), or negative (-1) sign of the specified expression.</span></span> 

<span data-ttu-id="97a43-243">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="97a43-243">**Arguments**</span></span> 

<span data-ttu-id="97a43-244">`expression`: `Int32`, `Int64`, `Double`, lub `Decimal`</span><span class="sxs-lookup"><span data-stu-id="97a43-244">`expression`: `Int32`, `Int64`, `Double`, or `Decimal`</span></span> 

<span data-ttu-id="97a43-245">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="97a43-245">**Return Value**</span></span> 

<span data-ttu-id="97a43-246">`Int32`, `Int64`, `Double`, Lub `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="97a43-246">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="97a43-247">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="97a43-247">**Example**</span></span> 

`SqlServer.SIGN(-10)`

## <a name="sinexpression"></a><span data-ttu-id="97a43-248">SIN(Expression)</span><span class="sxs-lookup"><span data-stu-id="97a43-248">SIN(expression)</span></span>

<span data-ttu-id="97a43-249">Oblicza trygonometrycznych sinus określonego kąta podany w radianach, a następnie zwraca `Double` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="97a43-249">Calculates the trigonometric sine of the specified angle in radians, and returns a `Double` expression.</span></span> 

<span data-ttu-id="97a43-250">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="97a43-250">**Arguments**</span></span> 

<span data-ttu-id="97a43-251">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="97a43-251">`expression`: A `Double`.</span></span> 

<span data-ttu-id="97a43-252">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="97a43-252">**Return Value**</span></span> 

<span data-ttu-id="97a43-253">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="97a43-253">A `Double`.</span></span> 

<span data-ttu-id="97a43-254">**Przykład** `SqlServer.SIN(20)`</span><span class="sxs-lookup"><span data-stu-id="97a43-254">**Example** `SqlServer.SIN(20)`</span></span>

## <a name="sqrtexpression"></a><span data-ttu-id="97a43-255">SQRT(Expression)</span><span class="sxs-lookup"><span data-stu-id="97a43-255">SQRT(expression)</span></span>

<span data-ttu-id="97a43-256">Zwraca pierwiastek kwadratowy z określonego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="97a43-256">Returns the square root of the specified expression.</span></span> 

<span data-ttu-id="97a43-257">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="97a43-257">**Arguments**</span></span> 

<span data-ttu-id="97a43-258">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="97a43-258">`expression`: A `Double`.</span></span> 

<span data-ttu-id="97a43-259">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="97a43-259">**Return Value**</span></span> 

<span data-ttu-id="97a43-260">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="97a43-260">A `Double`.</span></span> 

<span data-ttu-id="97a43-261">**Przykład** `SqlServer.SQRT(3600)`</span><span class="sxs-lookup"><span data-stu-id="97a43-261">**Example** `SqlServer.SQRT(3600)`</span></span>

## <a name="squareexpression"></a><span data-ttu-id="97a43-262">SQUARE(Expression)</span><span class="sxs-lookup"><span data-stu-id="97a43-262">SQUARE(expression)</span></span>

<span data-ttu-id="97a43-263">Zwraca kwadrat określone wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="97a43-263">Returns the square of the specified expression.</span></span> 

<span data-ttu-id="97a43-264">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="97a43-264">**Arguments**</span></span> 

<span data-ttu-id="97a43-265">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="97a43-265">`expression`: A `Double`.</span></span> 

<span data-ttu-id="97a43-266">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="97a43-266">**Return Value**</span></span> 

<span data-ttu-id="97a43-267">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="97a43-267">A `Double`.</span></span> 

<span data-ttu-id="97a43-268">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="97a43-268">**Example**</span></span> 

`SqlServer.SQUARE(25)`

## <a name="tanexpression"></a><span data-ttu-id="97a43-269">Tan(Expression)</span><span class="sxs-lookup"><span data-stu-id="97a43-269">TAN(expression)</span></span>

<span data-ttu-id="97a43-270">Oblicza tangens określonego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="97a43-270">Calculates the tangent of a specified expression.</span></span>

<span data-ttu-id="97a43-271">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="97a43-271">**Arguments**</span></span> 

<span data-ttu-id="97a43-272">`expression`: `Double`</span><span class="sxs-lookup"><span data-stu-id="97a43-272">`expression`: `Double`</span></span> 

<span data-ttu-id="97a43-273">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="97a43-273">**Return Value**</span></span> 

`Double` 

<span data-ttu-id="97a43-274">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="97a43-274">**Example**</span></span> 

`SqlServer.TAN(45.0)`
  
## <a name="see-also"></a><span data-ttu-id="97a43-275">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="97a43-275">See also</span></span>

<span data-ttu-id="97a43-276">Aby uzyskać więcej informacji na temat funkcji matematycznych, które obsługuje klient SQL zobacz dokumentację dla używanej wersji programu SQL Server określonego w manifeście dostawcy SqlClient:</span><span class="sxs-lookup"><span data-stu-id="97a43-276">For more information about the mathematical functions that SqlClient supports, see the documentation for the SQL Server version that you specified in the SqlClient provider manifest:</span></span>

- <span data-ttu-id="97a43-277">**SQL Server 2005:** [Mathematical Functions (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms177516(v=sql.90))</span><span class="sxs-lookup"><span data-stu-id="97a43-277">**SQL Server 2005:** [Mathematical Functions (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms177516(v=sql.90))</span></span>
- <span data-ttu-id="97a43-278">**SQL Server 2008:** [Mathematical Functions (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms177516(v=sql.100))</span><span class="sxs-lookup"><span data-stu-id="97a43-278">**SQL Server 2008:** [Mathematical Functions (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms177516(v=sql.100))</span></span>
- <span data-ttu-id="97a43-279">**Program SQL Server 2012 lub nowszy:** [Mathematical Functions (Transact-SQL)](/sql/t-sql/functions/mathematical-functions-transact-sql?view=sql-server-2017)</span><span class="sxs-lookup"><span data-stu-id="97a43-279">**SQL Server 2012 and later:** [Mathematical Functions (Transact-SQL)](/sql/t-sql/functions/mathematical-functions-transact-sql?view=sql-server-2017)</span></span>

- [<span data-ttu-id="97a43-280">Klient SQL dla funkcji programu Entity Framework</span><span class="sxs-lookup"><span data-stu-id="97a43-280">SqlClient for Entity Framework Functions</span></span>](sqlclient-for-ef-functions.md)
