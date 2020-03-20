---
title: Funkcje matematyczne
ms.date: 03/30/2017
ms.assetid: b040c7cb-156d-40f2-9152-61065b18148c
ms.openlocfilehash: 4512aaa2eeb3e715a1d6f7a8655912eb15162124
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149768"
---
# <a name="mathematical-functions"></a><span data-ttu-id="1322f-102">Funkcje matematyczne</span><span class="sxs-lookup"><span data-stu-id="1322f-102">Mathematical Functions</span></span>

<span data-ttu-id="1322f-103">Dostawca danych programu .NET Framework dla programu SQL Server (SqlClient) udostępnia funkcje matematyczne, które wykonują obliczenia wartości wejściowych, które są dostarczane jako argumenty i zwracają wynik wartości liczbowej.</span><span class="sxs-lookup"><span data-stu-id="1322f-103">The .NET Framework Data Provider for SQL Server (SqlClient) provides math functions that perform calculations on input values that are provided as arguments, and return a numeric value result.</span></span> <span data-ttu-id="1322f-104">Te funkcje znajdują się w obszarze nazw SqlServer, który jest dostępny podczas korzystania z SqlClient.</span><span class="sxs-lookup"><span data-stu-id="1322f-104">These functions are in the SqlServer namespace, which is available when you use SqlClient.</span></span> <span data-ttu-id="1322f-105">Właściwość obszaru nazw dostawcy umożliwia entity framework, który prefiks jest używany przez tego dostawcę dla określonych konstrukcji, takich jak typy i funkcje.</span><span class="sxs-lookup"><span data-stu-id="1322f-105">A provider's namespace property allows the Entity Framework to discover which prefix is used by this provider for specific constructs, such as types and functions.</span></span> <span data-ttu-id="1322f-106">W poniższej tabeli opisano funkcje matematyczne SqlClient.</span><span class="sxs-lookup"><span data-stu-id="1322f-106">The following table describes the SqlClient math functions.</span></span>  
  
## <a name="absexpression"></a><span data-ttu-id="1322f-107">ABS(wyrażenie)</span><span class="sxs-lookup"><span data-stu-id="1322f-107">ABS(expression)</span></span>

<span data-ttu-id="1322f-108">Wykonuje funkcję wartości bezwzględnej.</span><span class="sxs-lookup"><span data-stu-id="1322f-108">Performs the absolute value function.</span></span>

<span data-ttu-id="1322f-109">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="1322f-109">**Arguments**</span></span>

<span data-ttu-id="1322f-110">`expression`: `Int32`An `Int64` `Double`, `Decimal`, , lub .</span><span class="sxs-lookup"><span data-stu-id="1322f-110">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="1322f-111">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="1322f-111">**Return Value**</span></span>

<span data-ttu-id="1322f-112">Wartość bezwzględna określonego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="1322f-112">The absolute value of the specified expression.</span></span>

<span data-ttu-id="1322f-113">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="1322f-113">**Example**</span></span>

`SqlServer.ABS(-2)`

## <a name="acosexpression"></a><span data-ttu-id="1322f-114">ACOS(wyrażenie)</span><span class="sxs-lookup"><span data-stu-id="1322f-114">ACOS(expression)</span></span>

<span data-ttu-id="1322f-115">Zwraca wartość arccosine określonego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="1322f-115">Returns the arccosine value of the specified expression.</span></span>

<span data-ttu-id="1322f-116">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="1322f-116">**Arguments**</span></span>

<span data-ttu-id="1322f-117">`expression`: `Double`A .</span><span class="sxs-lookup"><span data-stu-id="1322f-117">`expression`: A `Double`.</span></span>

<span data-ttu-id="1322f-118">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="1322f-118">**Return Value**</span></span>

<span data-ttu-id="1322f-119">Klasa `Double`.</span><span class="sxs-lookup"><span data-stu-id="1322f-119">A `Double`.</span></span>

<span data-ttu-id="1322f-120">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="1322f-120">**Example**</span></span>

`SqlServer.ACOS(.9)`

## <a name="asinexpression"></a><span data-ttu-id="1322f-121">ASIN(wyrażenie)</span><span class="sxs-lookup"><span data-stu-id="1322f-121">ASIN(expression)</span></span>

<span data-ttu-id="1322f-122">Zwraca wartość arcsine określonego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="1322f-122">Returns the arcsine value of the specified expression.</span></span>

<span data-ttu-id="1322f-123">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="1322f-123">**Arguments**</span></span>

<span data-ttu-id="1322f-124">`expression`: `Double`A .</span><span class="sxs-lookup"><span data-stu-id="1322f-124">`expression`: A `Double`.</span></span>

<span data-ttu-id="1322f-125">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="1322f-125">**Return Value**</span></span>

<span data-ttu-id="1322f-126">Klasa `Double`.</span><span class="sxs-lookup"><span data-stu-id="1322f-126">A `Double`.</span></span>

<span data-ttu-id="1322f-127">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="1322f-127">**Example**</span></span>

`SqlServer.ASIN(.9)`

## <a name="atanexpression"></a><span data-ttu-id="1322f-128">ATAN(wyrażenie)</span><span class="sxs-lookup"><span data-stu-id="1322f-128">ATAN(expression)</span></span>

<span data-ttu-id="1322f-129">Zwraca wartość arctangent określonego wyrażenia liczbowego.</span><span class="sxs-lookup"><span data-stu-id="1322f-129">Returns the arctangent value of the specified numeric expression.</span></span>

<span data-ttu-id="1322f-130">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="1322f-130">**Arguments**</span></span>

<span data-ttu-id="1322f-131">`expression`: `Double`A .</span><span class="sxs-lookup"><span data-stu-id="1322f-131">`expression`: A `Double`.</span></span>

<span data-ttu-id="1322f-132">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="1322f-132">**Return Value**</span></span>

<span data-ttu-id="1322f-133">Klasa `Double`.</span><span class="sxs-lookup"><span data-stu-id="1322f-133">A `Double`.</span></span>

<span data-ttu-id="1322f-134">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="1322f-134">**Example**</span></span>

`SqlServer.ATAN(9)`

## <a name="atn2expression-expression"></a><span data-ttu-id="1322f-135">ATN2(wyrażenie, wyrażenie)</span><span class="sxs-lookup"><span data-stu-id="1322f-135">ATN2(expression, expression)</span></span>

<span data-ttu-id="1322f-136">Zwraca kąt w radianach, którego styczna znajduje się między dwoma określonymi wyrażeniami liczbowymi.</span><span class="sxs-lookup"><span data-stu-id="1322f-136">Returns the angle, in radians, whose tangent is between the two specified numeric expressions.</span></span>

<span data-ttu-id="1322f-137">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="1322f-137">**Arguments**</span></span>

<span data-ttu-id="1322f-138">`expression`: `Double`A .</span><span class="sxs-lookup"><span data-stu-id="1322f-138">`expression`: A `Double`.</span></span>

<span data-ttu-id="1322f-139">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="1322f-139">**Return Value**</span></span>

<span data-ttu-id="1322f-140">Klasa `Double`.</span><span class="sxs-lookup"><span data-stu-id="1322f-140">A `Double`.</span></span>

<span data-ttu-id="1322f-141">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="1322f-141">**Example**</span></span>

`SqlServer.ATN2(9, 8)`

## <a name="ceilingexpression"></a><span data-ttu-id="1322f-142">CEILING(wyrażenie)</span><span class="sxs-lookup"><span data-stu-id="1322f-142">CEILING(expression)</span></span>

<span data-ttu-id="1322f-143">Konwertuje określone wyrażenie na najmniejszą liczę całkowitą, która jest większa lub równa.</span><span class="sxs-lookup"><span data-stu-id="1322f-143">Converts the specified expression to the smallest integer that is greater than or equal to it.</span></span>

<span data-ttu-id="1322f-144">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="1322f-144">**Arguments**</span></span>

<span data-ttu-id="1322f-145">`expression`: `Int32`An `Int64` `Double`, `Decimal`, , lub .</span><span class="sxs-lookup"><span data-stu-id="1322f-145">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="1322f-146">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="1322f-146">**Return Value**</span></span>

<span data-ttu-id="1322f-147">An `Int32` `Int64`, `Double`, `Decimal`, lub .</span><span class="sxs-lookup"><span data-stu-id="1322f-147">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="1322f-148">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="1322f-148">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_ceiling)]

## <a name="cosexpression"></a><span data-ttu-id="1322f-149">COS(wyrażenie)</span><span class="sxs-lookup"><span data-stu-id="1322f-149">COS(expression)</span></span>

<span data-ttu-id="1322f-150">Oblicza cosine trygonometryczne określonego kąta w radianach.</span><span class="sxs-lookup"><span data-stu-id="1322f-150">Calculates the trigonometric cosine of the specified angle in radians.</span></span>

<span data-ttu-id="1322f-151">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="1322f-151">**Arguments**</span></span>

<span data-ttu-id="1322f-152">`expression`: `Double`A .</span><span class="sxs-lookup"><span data-stu-id="1322f-152">`expression`: A `Double`.</span></span>

<span data-ttu-id="1322f-153">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="1322f-153">**Return Value**</span></span>

<span data-ttu-id="1322f-154">Klasa `Double`.</span><span class="sxs-lookup"><span data-stu-id="1322f-154">A `Double`.</span></span>

<span data-ttu-id="1322f-155">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="1322f-155">**Example**</span></span>

`SqlServer.COS(45)`

## <a name="cotexpression"></a><span data-ttu-id="1322f-156">COT(wyrażenie)</span><span class="sxs-lookup"><span data-stu-id="1322f-156">COT(expression)</span></span>

<span data-ttu-id="1322f-157">Oblicza tryb trygonometryczny określonego kąta w radianach.</span><span class="sxs-lookup"><span data-stu-id="1322f-157">Calculates the trigonometric cotangent of the specified angle in radians.</span></span>

<span data-ttu-id="1322f-158">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="1322f-158">**Arguments**</span></span>

<span data-ttu-id="1322f-159">`expression`: `Double`A .</span><span class="sxs-lookup"><span data-stu-id="1322f-159">`expression`: A `Double`.</span></span>

<span data-ttu-id="1322f-160">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="1322f-160">**Return Value**</span></span>

<span data-ttu-id="1322f-161">Klasa `Double`.</span><span class="sxs-lookup"><span data-stu-id="1322f-161">A `Double`.</span></span>

<span data-ttu-id="1322f-162">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="1322f-162">**Example**</span></span>

`SqlServer.COT(60)`
  
## <a name="degreesradians"></a><span data-ttu-id="1322f-163">STOPNIE(radiany)</span><span class="sxs-lookup"><span data-stu-id="1322f-163">DEGREES(radians)</span></span>

<span data-ttu-id="1322f-164">Zwraca odpowiedni kąt w stopniach.</span><span class="sxs-lookup"><span data-stu-id="1322f-164">Returns the corresponding angle in degrees.</span></span>

<span data-ttu-id="1322f-165">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="1322f-165">**Arguments**</span></span>

<span data-ttu-id="1322f-166">`expression`: `Int32`An `Int64` `Double`, `Decimal`, , lub .</span><span class="sxs-lookup"><span data-stu-id="1322f-166">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="1322f-167">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="1322f-167">**Return Value**</span></span>

<span data-ttu-id="1322f-168">An `Int32` `Int64`, `Double`, `Decimal`, lub .</span><span class="sxs-lookup"><span data-stu-id="1322f-168">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="1322f-169">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="1322f-169">**Example**</span></span>

`SqlServer.DEGREES(3.1)`

## <a name="expexpression"></a><span data-ttu-id="1322f-170">EXP(wyrażenie)</span><span class="sxs-lookup"><span data-stu-id="1322f-170">EXP(expression)</span></span>

<span data-ttu-id="1322f-171">Oblicza wykładniczą wartość określonego wyrażenia liczbowego.</span><span class="sxs-lookup"><span data-stu-id="1322f-171">Calculates the exponential value of a specified numeric expression.</span></span>

<span data-ttu-id="1322f-172">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="1322f-172">**Arguments**</span></span>

<span data-ttu-id="1322f-173">`expression`: `Double`A .</span><span class="sxs-lookup"><span data-stu-id="1322f-173">`expression`: A `Double`.</span></span>

<span data-ttu-id="1322f-174">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="1322f-174">**Return Value**</span></span>

<span data-ttu-id="1322f-175">Klasa `Double`.</span><span class="sxs-lookup"><span data-stu-id="1322f-175">A `Double`.</span></span>

<span data-ttu-id="1322f-176">**Przykład**`SqlServer.EXP(1)`</span><span class="sxs-lookup"><span data-stu-id="1322f-176">**Example** `SqlServer.EXP(1)`</span></span>

## <a name="floorexpression"></a><span data-ttu-id="1322f-177">FLOOR(wyrażenie)</span><span class="sxs-lookup"><span data-stu-id="1322f-177">FLOOR(expression)</span></span>

<span data-ttu-id="1322f-178">Konwertuje określone wyrażenie na największą całkowitą mniejszą lub równą.</span><span class="sxs-lookup"><span data-stu-id="1322f-178">Converts the specified expression to the largest integer less than or equal to it.</span></span>

<span data-ttu-id="1322f-179">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="1322f-179">**Arguments**</span></span>

<span data-ttu-id="1322f-180">`expression`: `Double`A .</span><span class="sxs-lookup"><span data-stu-id="1322f-180">`expression`: A `Double`.</span></span>

<span data-ttu-id="1322f-181">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="1322f-181">**Return Value**</span></span>

<span data-ttu-id="1322f-182">Klasa `Double`.</span><span class="sxs-lookup"><span data-stu-id="1322f-182">A `Double`.</span></span>

<span data-ttu-id="1322f-183">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="1322f-183">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_floor)]

## <a name="logexpression"></a><span data-ttu-id="1322f-184">LOG(wyrażenie)</span><span class="sxs-lookup"><span data-stu-id="1322f-184">LOG(expression)</span></span>

<span data-ttu-id="1322f-185">Oblicza logarytm naturalny określonego `float` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="1322f-185">Calculates the natural logarithm of the specified `float` expression.</span></span>

<span data-ttu-id="1322f-186">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="1322f-186">**Arguments**</span></span>

<span data-ttu-id="1322f-187">`expression`: `Double`A .</span><span class="sxs-lookup"><span data-stu-id="1322f-187">`expression`: A `Double`.</span></span>

<span data-ttu-id="1322f-188">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="1322f-188">**Return Value**</span></span>

<span data-ttu-id="1322f-189">Klasa `Double`.</span><span class="sxs-lookup"><span data-stu-id="1322f-189">A `Double`.</span></span>

<span data-ttu-id="1322f-190">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="1322f-190">**Example**</span></span>

`SqlServer.LOG(100)`

## <a name="log10expression"></a><span data-ttu-id="1322f-191">LOG10(wyrażenie)</span><span class="sxs-lookup"><span data-stu-id="1322f-191">LOG10(expression)</span></span>

<span data-ttu-id="1322f-192">Zwraca logarytm base-10 określonego `Double` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="1322f-192">Returns the base-10 logarithm of the specified `Double` expression.</span></span>

<span data-ttu-id="1322f-193">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="1322f-193">**Arguments**</span></span>

<span data-ttu-id="1322f-194">`expression`: `Double`A .</span><span class="sxs-lookup"><span data-stu-id="1322f-194">`expression`: A `Double`.</span></span>

<span data-ttu-id="1322f-195">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="1322f-195">**Return Value**</span></span>

<span data-ttu-id="1322f-196">Klasa `Double`.</span><span class="sxs-lookup"><span data-stu-id="1322f-196">A `Double`.</span></span>

<span data-ttu-id="1322f-197">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="1322f-197">**Example**</span></span>

`SqlServer.LOG10(100)`

## <a name="pi"></a><span data-ttu-id="1322f-198">PI()</span><span class="sxs-lookup"><span data-stu-id="1322f-198">PI()</span></span>

<span data-ttu-id="1322f-199">Zwraca stałą wartość pi `Double`jako .</span><span class="sxs-lookup"><span data-stu-id="1322f-199">Returns the constant value of pi as a `Double`.</span></span>

<span data-ttu-id="1322f-200">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="1322f-200">**Return Value**</span></span>

<span data-ttu-id="1322f-201">Klasa `Double`.</span><span class="sxs-lookup"><span data-stu-id="1322f-201">A `Double`.</span></span>

<span data-ttu-id="1322f-202">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="1322f-202">**Example**</span></span>

`SqlServer.PI()`

## <a name="powernumeric_expression-power_expression"></a><span data-ttu-id="1322f-203">MOC (numeric_expression, power_expression)</span><span class="sxs-lookup"><span data-stu-id="1322f-203">POWER(numeric_expression, power_expression)</span></span>

<span data-ttu-id="1322f-204">Oblicza wartość określonego wyrażenia do określonej mocy.</span><span class="sxs-lookup"><span data-stu-id="1322f-204">Calculates the value of a specified expression to a specified power.</span></span>

<span data-ttu-id="1322f-205">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="1322f-205">**Arguments**</span></span>

|  |  |
|--|--|
|`numeric_expression`| <span data-ttu-id="1322f-206">An `Int32` `Int64`, `Double`, `Decimal`, lub .</span><span class="sxs-lookup"><span data-stu-id="1322f-206">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>|
|`power_expression`| <span data-ttu-id="1322f-207">A, `Double` który reprezentuje moc, `numeric_expression`do której podnieść .</span><span class="sxs-lookup"><span data-stu-id="1322f-207">A `Double` that represents the power to which to raise the `numeric_expression`.</span></span>|

<span data-ttu-id="1322f-208">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="1322f-208">**Return Value**</span></span>

<span data-ttu-id="1322f-209">Wartość określona `numeric_expression` do określonego `power_expression`.</span><span class="sxs-lookup"><span data-stu-id="1322f-209">The value of the specified `numeric_expression` to the specified `power_expression`.</span></span>

<span data-ttu-id="1322f-210">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="1322f-210">**Example**</span></span>

`SqlServer.POWER(2,7)`

## <a name="radiansexpression"></a><span data-ttu-id="1322f-211">RADIAIANS(wyrażenie)</span><span class="sxs-lookup"><span data-stu-id="1322f-211">RADIANS(expression)</span></span>

<span data-ttu-id="1322f-212">Konwertuje stopnie na radiany.</span><span class="sxs-lookup"><span data-stu-id="1322f-212">Converts degrees to radians.</span></span>

<span data-ttu-id="1322f-213">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="1322f-213">**Arguments**</span></span>

<span data-ttu-id="1322f-214">`expression`: `Int32`An `Int64` `Double`, `Decimal`, , lub .</span><span class="sxs-lookup"><span data-stu-id="1322f-214">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="1322f-215">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="1322f-215">**Return Value**</span></span>

<span data-ttu-id="1322f-216">An `Int32` `Int64`, `Double`, `Decimal`, lub .</span><span class="sxs-lookup"><span data-stu-id="1322f-216">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="1322f-217">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="1322f-217">**Example**</span></span>

`SqlServer.RADIANS(360.0)`

## <a name="randseed"></a><span data-ttu-id="1322f-218">RAND([materiał siewny])</span><span class="sxs-lookup"><span data-stu-id="1322f-218">RAND([seed])</span></span>

<span data-ttu-id="1322f-219">Zwraca wartość losową od 0 do 1.</span><span class="sxs-lookup"><span data-stu-id="1322f-219">Returns a random value from 0 through 1.</span></span>

<span data-ttu-id="1322f-220">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="1322f-220">**Arguments**</span></span>

<span data-ttu-id="1322f-221">Wartość materiału siewnego jako wartość `Int32`.</span><span class="sxs-lookup"><span data-stu-id="1322f-221">The seed value as an `Int32`.</span></span> <span data-ttu-id="1322f-222">Jeśli materiał siewny nie jest określony, aparat bazy danych programu SQL Server przypisuje wartość źródłową losowo.</span><span class="sxs-lookup"><span data-stu-id="1322f-222">If the seed is not specified, the SQL Server Database Engine assigns a seed value at random.</span></span> <span data-ttu-id="1322f-223">Dla określonej wartości źródłowej zwracany wynik jest zawsze taki sam.</span><span class="sxs-lookup"><span data-stu-id="1322f-223">For a specified seed value, the result returned is always the same.</span></span>

<span data-ttu-id="1322f-224">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="1322f-224">**Return Value**</span></span>

<span data-ttu-id="1322f-225">Wartość `Double` losowa od 0 do 1.</span><span class="sxs-lookup"><span data-stu-id="1322f-225">A random `Double` value from 0 through 1.</span></span>

<span data-ttu-id="1322f-226">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="1322f-226">**Example**</span></span>

`SqlServer.RAND()`
  
## <a name="roundnumeric_expression-lengthfunction"></a><span data-ttu-id="1322f-227">ROUND(numeric_expression, długość[,funkcja])</span><span class="sxs-lookup"><span data-stu-id="1322f-227">ROUND(numeric_expression, length[,function])</span></span>

<span data-ttu-id="1322f-228">Zwraca wyrażenie liczbowe, zaokrąglone do określonej długości lub precyzji.</span><span class="sxs-lookup"><span data-stu-id="1322f-228">Returns a numeric expression, rounded to the specified length or precision.</span></span>

<span data-ttu-id="1322f-229">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="1322f-229">**Arguments**</span></span>

|  |  |
|--|--|
|`numeric_expression`| <span data-ttu-id="1322f-230">An `Int32` `Int64`, `Double`, `Decimal`, lub .</span><span class="sxs-lookup"><span data-stu-id="1322f-230">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>
|`length`| <span data-ttu-id="1322f-231">Który `Int32` reprezentuje dokładność, `numeric_expression` do której ma być zaokrąglona.</span><span class="sxs-lookup"><span data-stu-id="1322f-231">An `Int32` that represents the precision to which `numeric_expression` is to be rounded.</span></span> <span data-ttu-id="1322f-232">Gdy `length` jest to `numeric_expression` liczba dodatnia, jest zaokrąglana `length`do liczby pozycji dziesiętnych określonych przez .</span><span class="sxs-lookup"><span data-stu-id="1322f-232">When `length` is a positive number, `numeric_expression` is rounded to the number of decimal positions specified by `length`.</span></span> <span data-ttu-id="1322f-233">Gdy `length` jest to `numeric_expression` liczba ujemna, jest zaokrąglana po `length`lewej stronie przecinka dziesiętnego, jak określono w programie .</span><span class="sxs-lookup"><span data-stu-id="1322f-233">When `length` is a negative number, `numeric_expression` is rounded on the left side of the decimal point, as specified by `length`.</span></span>|
|`function` | <span data-ttu-id="1322f-234">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="1322f-234">Optional.</span></span> <span data-ttu-id="1322f-235">Który `Int32` reprezentuje typ operacji do wykonania.</span><span class="sxs-lookup"><span data-stu-id="1322f-235">An `Int32` that represents the type of operation to perform.</span></span> <span data-ttu-id="1322f-236">Gdy funkcja jest pominięta lub ma wartość `numeric_expression` 0 (domyślnie), jest zaokrąglana.</span><span class="sxs-lookup"><span data-stu-id="1322f-236">When function is omitted or has a value of 0 (default), `numeric_expression` is rounded.</span></span> <span data-ttu-id="1322f-237">Gdy określono wartość inną niż `numeric_expression` 0, jest obcinana.</span><span class="sxs-lookup"><span data-stu-id="1322f-237">When a value other than 0 is specified, `numeric_expression` is truncated.</span></span> |

<span data-ttu-id="1322f-238">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="1322f-238">**Return Value**</span></span>

<span data-ttu-id="1322f-239">Wartość określona `numeric_expression` do określonego `power_expression`.</span><span class="sxs-lookup"><span data-stu-id="1322f-239">The value of the specified `numeric_expression` to the specified `power_expression`.</span></span>

<span data-ttu-id="1322f-240">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="1322f-240">**Example**</span></span>

`SqlServer.ROUND(748.58, -3)`

## <a name="signexpression"></a><span data-ttu-id="1322f-241">ZNAK(wyrażenie)</span><span class="sxs-lookup"><span data-stu-id="1322f-241">SIGN(expression)</span></span>

<span data-ttu-id="1322f-242">Zwraca znak dodatni (+1), zero (0) lub ujemny (-1) określonego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="1322f-242">Returns the positive (+1), zero (0), or negative (-1) sign of the specified expression.</span></span>

<span data-ttu-id="1322f-243">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="1322f-243">**Arguments**</span></span>

<span data-ttu-id="1322f-244">`expression`: `Int32` `Int64`, `Double`, , lub`Decimal`</span><span class="sxs-lookup"><span data-stu-id="1322f-244">`expression`: `Int32`, `Int64`, `Double`, or `Decimal`</span></span>

<span data-ttu-id="1322f-245">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="1322f-245">**Return Value**</span></span>

<span data-ttu-id="1322f-246">An `Int32` `Int64`, `Double`, `Decimal`, lub .</span><span class="sxs-lookup"><span data-stu-id="1322f-246">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="1322f-247">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="1322f-247">**Example**</span></span>

`SqlServer.SIGN(-10)`

## <a name="sinexpression"></a><span data-ttu-id="1322f-248">SIN(wyrażenie)</span><span class="sxs-lookup"><span data-stu-id="1322f-248">SIN(expression)</span></span>

<span data-ttu-id="1322f-249">Oblicza sinus trygonometryczny określonego kąta w radianach i zwraca `Double` wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="1322f-249">Calculates the trigonometric sine of the specified angle in radians, and returns a `Double` expression.</span></span>

<span data-ttu-id="1322f-250">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="1322f-250">**Arguments**</span></span>

<span data-ttu-id="1322f-251">`expression`: `Double`A .</span><span class="sxs-lookup"><span data-stu-id="1322f-251">`expression`: A `Double`.</span></span>

<span data-ttu-id="1322f-252">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="1322f-252">**Return Value**</span></span>

<span data-ttu-id="1322f-253">Klasa `Double`.</span><span class="sxs-lookup"><span data-stu-id="1322f-253">A `Double`.</span></span>

<span data-ttu-id="1322f-254">**Przykład**`SqlServer.SIN(20)`</span><span class="sxs-lookup"><span data-stu-id="1322f-254">**Example** `SqlServer.SIN(20)`</span></span>

## <a name="sqrtexpression"></a><span data-ttu-id="1322f-255">SQRT(wyrażenie)</span><span class="sxs-lookup"><span data-stu-id="1322f-255">SQRT(expression)</span></span>

<span data-ttu-id="1322f-256">Zwraca pierwiastek kwadratowy określonego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="1322f-256">Returns the square root of the specified expression.</span></span>

<span data-ttu-id="1322f-257">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="1322f-257">**Arguments**</span></span>

<span data-ttu-id="1322f-258">`expression`: `Double`A .</span><span class="sxs-lookup"><span data-stu-id="1322f-258">`expression`: A `Double`.</span></span>

<span data-ttu-id="1322f-259">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="1322f-259">**Return Value**</span></span>

<span data-ttu-id="1322f-260">Klasa `Double`.</span><span class="sxs-lookup"><span data-stu-id="1322f-260">A `Double`.</span></span>

<span data-ttu-id="1322f-261">**Przykład**`SqlServer.SQRT(3600)`</span><span class="sxs-lookup"><span data-stu-id="1322f-261">**Example** `SqlServer.SQRT(3600)`</span></span>

## <a name="squareexpression"></a><span data-ttu-id="1322f-262">KWADRAT(wyrażenie)</span><span class="sxs-lookup"><span data-stu-id="1322f-262">SQUARE(expression)</span></span>

<span data-ttu-id="1322f-263">Zwraca kwadrat określonego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="1322f-263">Returns the square of the specified expression.</span></span>

<span data-ttu-id="1322f-264">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="1322f-264">**Arguments**</span></span>

<span data-ttu-id="1322f-265">`expression`: `Double`A .</span><span class="sxs-lookup"><span data-stu-id="1322f-265">`expression`: A `Double`.</span></span>

<span data-ttu-id="1322f-266">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="1322f-266">**Return Value**</span></span>

<span data-ttu-id="1322f-267">Klasa `Double`.</span><span class="sxs-lookup"><span data-stu-id="1322f-267">A `Double`.</span></span>

<span data-ttu-id="1322f-268">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="1322f-268">**Example**</span></span>

`SqlServer.SQUARE(25)`

## <a name="tanexpression"></a><span data-ttu-id="1322f-269">TAN(wyrażenie)</span><span class="sxs-lookup"><span data-stu-id="1322f-269">TAN(expression)</span></span>

<span data-ttu-id="1322f-270">Oblicza styczną określonego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="1322f-270">Calculates the tangent of a specified expression.</span></span>

<span data-ttu-id="1322f-271">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="1322f-271">**Arguments**</span></span>

<span data-ttu-id="1322f-272">`expression`: `Double`</span><span class="sxs-lookup"><span data-stu-id="1322f-272">`expression`: `Double`</span></span>

<span data-ttu-id="1322f-273">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="1322f-273">**Return Value**</span></span>

`Double`

<span data-ttu-id="1322f-274">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="1322f-274">**Example**</span></span>

`SqlServer.TAN(45.0)`
  
## <a name="see-also"></a><span data-ttu-id="1322f-275">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1322f-275">See also</span></span>

- [<span data-ttu-id="1322f-276">Funkcje matematyczne (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="1322f-276">Mathematical Functions (Transact-SQL)</span></span>](/sql/t-sql/functions/mathematical-functions-transact-sql)
- [<span data-ttu-id="1322f-277">Klient SQL dla funkcji programu Entity Framework</span><span class="sxs-lookup"><span data-stu-id="1322f-277">SqlClient for Entity Framework Functions</span></span>](sqlclient-for-ef-functions.md)
