---
title: Funkcje matematyczne Canonical
ms.date: 03/30/2017
ms.assetid: 6f6cddc6-b561-4ebe-84b6-841ef5b4113b
ms.openlocfilehash: 9417ff9836912017c9d88bb24a18849aaac2836a
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250309"
---
# <a name="math-canonical-functions"></a><span data-ttu-id="1f92d-102">Funkcje matematyczne Canonical</span><span class="sxs-lookup"><span data-stu-id="1f92d-102">Math Canonical Functions</span></span>

<span data-ttu-id="1f92d-103">Entity SQL obejmuje następujące funkcje matematyczne w postaci kanonicznej:</span><span class="sxs-lookup"><span data-stu-id="1f92d-103">Entity SQL includes the following math canonical functions:</span></span>
  
## <a name="absvalue"></a><span data-ttu-id="1f92d-104">ABS (wartość)</span><span class="sxs-lookup"><span data-stu-id="1f92d-104">Abs(value)</span></span>

<span data-ttu-id="1f92d-105">Zwraca wartość `value`bezwzględną.</span><span class="sxs-lookup"><span data-stu-id="1f92d-105">Returns the absolute value of `value`.</span></span>

<span data-ttu-id="1f92d-106">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="1f92d-106">**Arguments**</span></span>

<span data-ttu-id="1f92d-107">`Int16` ,`Int32` ,,`Decimal`,, I. `Int64` `Byte` `Single` `Double`</span><span class="sxs-lookup"><span data-stu-id="1f92d-107">An `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="1f92d-108">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="1f92d-108">**Return Value**</span></span>

<span data-ttu-id="1f92d-109">Typ `value`.</span><span class="sxs-lookup"><span data-stu-id="1f92d-109">The type of `value`.</span></span>

<span data-ttu-id="1f92d-110">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="1f92d-110">**Example**</span></span>

`Abs(-2)`

## <a name="ceilingvalue"></a><span data-ttu-id="1f92d-111">Górny limit (wartość)</span><span class="sxs-lookup"><span data-stu-id="1f92d-111">Ceiling(value)</span></span>

<span data-ttu-id="1f92d-112">Zwraca najmniejszą liczbę całkowitą, która nie jest `value`mniejsza niż.</span><span class="sxs-lookup"><span data-stu-id="1f92d-112">Returns the smallest integer that is not less than `value`.</span></span>

<span data-ttu-id="1f92d-113">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="1f92d-113">**Arguments**</span></span>

<span data-ttu-id="1f92d-114">A `Single`, `Double`i .`Decimal`</span><span class="sxs-lookup"><span data-stu-id="1f92d-114">A `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="1f92d-115">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="1f92d-115">**Return Value**</span></span>

<span data-ttu-id="1f92d-116">Typ `value`.</span><span class="sxs-lookup"><span data-stu-id="1f92d-116">The type of `value`.</span></span>

<span data-ttu-id="1f92d-117">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="1f92d-117">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_CEILING](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_ceiling)]
[!code-sql[DP EntityServices Concepts#EDM_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_ceiling)]

## <a name="floorvalue"></a><span data-ttu-id="1f92d-118">Piętro (wartość)</span><span class="sxs-lookup"><span data-stu-id="1f92d-118">Floor(value)</span></span>

<span data-ttu-id="1f92d-119">Zwraca największą liczbę całkowitą, która nie jest większa `value`niż.</span><span class="sxs-lookup"><span data-stu-id="1f92d-119">Returns the largest integer that is not greater than `value`.</span></span>

<span data-ttu-id="1f92d-120">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="1f92d-120">**Arguments**</span></span>

<span data-ttu-id="1f92d-121">A `Single`, `Double`i .`Decimal`</span><span class="sxs-lookup"><span data-stu-id="1f92d-121">A `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="1f92d-122">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="1f92d-122">**Return Value**</span></span>

<span data-ttu-id="1f92d-123">Typ `value`.</span><span class="sxs-lookup"><span data-stu-id="1f92d-123">The type of `value`.</span></span>

<span data-ttu-id="1f92d-124">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="1f92d-124">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_FLOOR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_floor)]
[!code-sql[DP EntityServices Concepts#EDM_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_floor)]

## <a name="powervalue-exponent"></a><span data-ttu-id="1f92d-125">Potęga (wartość, wykładnik)</span><span class="sxs-lookup"><span data-stu-id="1f92d-125">Power(value, exponent)</span></span>

<span data-ttu-id="1f92d-126">Zwraca wynik określonego `value` do określonego `exponent`.</span><span class="sxs-lookup"><span data-stu-id="1f92d-126">Returns the result of the specified `value` to the specified `exponent`.</span></span>

<span data-ttu-id="1f92d-127">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="1f92d-127">**Arguments**</span></span>

|  |  |
|--|--|
|`value` | <span data-ttu-id="1f92d-128">`Int32, Int64, Double`Lub .`Decimal`</span><span class="sxs-lookup"><span data-stu-id="1f92d-128">An `Int32, Int64, Double`, or `Decimal`.</span></span> |
|`exponent` | <span data-ttu-id="1f92d-129">`Int64`, ,`Double`Lub .`Decimal`</span><span class="sxs-lookup"><span data-stu-id="1f92d-129">An `Int64`, `Double`, or `Decimal`.</span></span> |

<span data-ttu-id="1f92d-130">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="1f92d-130">**Return Value**</span></span>

<span data-ttu-id="1f92d-131">Typ `value`.</span><span class="sxs-lookup"><span data-stu-id="1f92d-131">The type of `value`.</span></span>

<span data-ttu-id="1f92d-132">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="1f92d-132">**Example**</span></span>

`Power(748.58,2)`

## <a name="roundvalue"></a><span data-ttu-id="1f92d-133">Round (wartość)</span><span class="sxs-lookup"><span data-stu-id="1f92d-133">Round(value)</span></span>

<span data-ttu-id="1f92d-134">Zwraca część całkowitą z `value`zaokrągloną do najbliższej liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="1f92d-134">Returns the integer portion of `value`, rounded to the nearest integer.</span></span>

<span data-ttu-id="1f92d-135">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="1f92d-135">**Arguments**</span></span>

<span data-ttu-id="1f92d-136">A `Single`, `Double`i .`Decimal`</span><span class="sxs-lookup"><span data-stu-id="1f92d-136">A `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="1f92d-137">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="1f92d-137">**Return Value**</span></span>

<span data-ttu-id="1f92d-138">Typ `value`.</span><span class="sxs-lookup"><span data-stu-id="1f92d-138">The type of `value`.</span></span>

<span data-ttu-id="1f92d-139">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="1f92d-139">**Example**</span></span>

`Round(748.58)`

## <a name="roundvalue-digits"></a><span data-ttu-id="1f92d-140">Round (wartość, cyfry)</span><span class="sxs-lookup"><span data-stu-id="1f92d-140">Round(value, digits)</span></span>

<span data-ttu-id="1f92d-141">Zwraca zaokrąglony do najbliższego określonego `digits`. `value`</span><span class="sxs-lookup"><span data-stu-id="1f92d-141">Returns the `value`, rounded to the nearest specified `digits`.</span></span>

<span data-ttu-id="1f92d-142">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="1f92d-142">**Arguments**</span></span>

|  |  |
|--|--|
|`value`|<span data-ttu-id="1f92d-143">`Double`lub `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="1f92d-143">`Double` or `Decimal`.</span></span>|
|`digits`|<span data-ttu-id="1f92d-144">`Int16`lub `Int32`.</span><span class="sxs-lookup"><span data-stu-id="1f92d-144">`Int16` or `Int32`.</span></span>|

<span data-ttu-id="1f92d-145">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="1f92d-145">**Return Value**</span></span>

<span data-ttu-id="1f92d-146">Typ `value`.</span><span class="sxs-lookup"><span data-stu-id="1f92d-146">The type of `value`.</span></span>

<span data-ttu-id="1f92d-147">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="1f92d-147">**Example**</span></span>

`Round(748.58,1)`

## <a name="truncatevalue-digits"></a><span data-ttu-id="1f92d-148">TRUNCATE (wartość, cyfry)</span><span class="sxs-lookup"><span data-stu-id="1f92d-148">Truncate(value, digits)</span></span>

<span data-ttu-id="1f92d-149">Zwraca wartość `value`, która jest obcinana do `digits`najbliższego określonego.</span><span class="sxs-lookup"><span data-stu-id="1f92d-149">Returns the `value`, truncated to the nearest specified `digits`.</span></span>

<span data-ttu-id="1f92d-150">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="1f92d-150">**Arguments**</span></span>

|  |  |
|--|--|
|`value`|<span data-ttu-id="1f92d-151">`Double`lub `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="1f92d-151">`Double` or `Decimal`.</span></span>|
|`digits`|<span data-ttu-id="1f92d-152">`Int16`lub `Int32`.</span><span class="sxs-lookup"><span data-stu-id="1f92d-152">`Int16` or `Int32`.</span></span>|

<span data-ttu-id="1f92d-153">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="1f92d-153">**Return Value**</span></span>

<span data-ttu-id="1f92d-154">Typ `value`.</span><span class="sxs-lookup"><span data-stu-id="1f92d-154">The type of `value`.</span></span>

<span data-ttu-id="1f92d-155">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="1f92d-155">**Example**</span></span>

`Truncate(748.58,1)`  
  
 <span data-ttu-id="1f92d-156">Te funkcje zostaną zwrócone `null` , jeśli `null` dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="1f92d-156">These functions will return `null` if given `null` input.</span></span>  
  
 <span data-ttu-id="1f92d-157">Równoważne funkcje są dostępne w dostawcy zarządzanym przez klienta programu Microsoft SQL.</span><span class="sxs-lookup"><span data-stu-id="1f92d-157">Equivalent functionality is available in the Microsoft SQL Client Managed Provider.</span></span> <span data-ttu-id="1f92d-158">Aby uzyskać więcej informacji, zobacz temat [SqlClient for Entity Framework Functions](../sqlclient-for-ef-functions.md).</span><span class="sxs-lookup"><span data-stu-id="1f92d-158">For more information, see [SqlClient for Entity Framework Functions](../sqlclient-for-ef-functions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f92d-159">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1f92d-159">See also</span></span>

- [<span data-ttu-id="1f92d-160">Funkcje Canonical</span><span class="sxs-lookup"><span data-stu-id="1f92d-160">Canonical Functions</span></span>](canonical-functions.md)
