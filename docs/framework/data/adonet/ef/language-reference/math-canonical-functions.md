---
title: Funkcje matematyczne Canonical
ms.date: 03/30/2017
ms.assetid: 6f6cddc6-b561-4ebe-84b6-841ef5b4113b
ms.openlocfilehash: 0fc9f4942c3f76f139ab7e4400005f0bfe80204e
ms.sourcegitcommit: 2eb5ca4956231c1a0efd34b6a9cab6153a5438af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/11/2018
ms.locfileid: "49087612"
---
# <a name="math-canonical-functions"></a><span data-ttu-id="158e7-102">Funkcje matematyczne Canonical</span><span class="sxs-lookup"><span data-stu-id="158e7-102">Math Canonical Functions</span></span>

<span data-ttu-id="158e7-103">Jednostka SQL obejmuje następujące funkcje matematyczne canonical:</span><span class="sxs-lookup"><span data-stu-id="158e7-103">Entity SQL includes the following math canonical functions:</span></span>
  
## <a name="absvalue"></a><span data-ttu-id="158e7-104">ABS(Value)</span><span class="sxs-lookup"><span data-stu-id="158e7-104">Abs(value)</span></span>

<span data-ttu-id="158e7-105">Zwraca wartość bezwzględną liczby `value`.</span><span class="sxs-lookup"><span data-stu-id="158e7-105">Returns the absolute value of `value`.</span></span>

<span data-ttu-id="158e7-106">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="158e7-106">**Arguments**</span></span>

<span data-ttu-id="158e7-107">`Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, I `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="158e7-107">An `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="158e7-108">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="158e7-108">**Return Value**</span></span>

<span data-ttu-id="158e7-109">Typ `value`.</span><span class="sxs-lookup"><span data-stu-id="158e7-109">The type of `value`.</span></span>

<span data-ttu-id="158e7-110">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="158e7-110">**Example**</span></span>

`Abs(-2)`

## <a name="ceilingvalue"></a><span data-ttu-id="158e7-111">CEILING(Value)</span><span class="sxs-lookup"><span data-stu-id="158e7-111">Ceiling(value)</span></span>

<span data-ttu-id="158e7-112">Zwraca najmniejszą liczbę całkowitą, która nie jest mniejsza niż `value`.</span><span class="sxs-lookup"><span data-stu-id="158e7-112">Returns the smallest integer that is not less than `value`.</span></span>

<span data-ttu-id="158e7-113">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="158e7-113">**Arguments**</span></span>

<span data-ttu-id="158e7-114">A `Single`, `Double`, i `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="158e7-114">A `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="158e7-115">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="158e7-115">**Return Value**</span></span>

<span data-ttu-id="158e7-116">Typ `value`.</span><span class="sxs-lookup"><span data-stu-id="158e7-116">The type of `value`.</span></span>

<span data-ttu-id="158e7-117">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="158e7-117">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_CEILING](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_ceiling)]
[!code-sql[DP EntityServices Concepts#EDM_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_ceiling)]

## <a name="floorvalue"></a><span data-ttu-id="158e7-118">FLOOR(Value)</span><span class="sxs-lookup"><span data-stu-id="158e7-118">Floor(value)</span></span>

<span data-ttu-id="158e7-119">Zwraca największą liczbą całkowitą, która nie jest większa niż `value`.</span><span class="sxs-lookup"><span data-stu-id="158e7-119">Returns the largest integer that is not greater than `value`.</span></span>

<span data-ttu-id="158e7-120">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="158e7-120">**Arguments**</span></span>

<span data-ttu-id="158e7-121">A `Single`, `Double`, i `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="158e7-121">A `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="158e7-122">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="158e7-122">**Return Value**</span></span>

<span data-ttu-id="158e7-123">Typ `value`.</span><span class="sxs-lookup"><span data-stu-id="158e7-123">The type of `value`.</span></span>

<span data-ttu-id="158e7-124">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="158e7-124">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_FLOOR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_floor)]
[!code-sql[DP EntityServices Concepts#EDM_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_floor)]

## <a name="powervalue-exponent"></a><span data-ttu-id="158e7-125">Zasilania (wartość wykładnika)</span><span class="sxs-lookup"><span data-stu-id="158e7-125">Power(value, exponent)</span></span>

<span data-ttu-id="158e7-126">Zwraca wynik określony `value` określonej `exponent`.</span><span class="sxs-lookup"><span data-stu-id="158e7-126">Returns the result of the specified `value` to the specified `exponent`.</span></span>

<span data-ttu-id="158e7-127">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="158e7-127">**Arguments**</span></span>

|  |  |
|--|--|
|`value` | <span data-ttu-id="158e7-128">`Int32, Int64, Double`, Lub `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="158e7-128">An `Int32, Int64, Double`, or `Decimal`.</span></span> |
|`exponent` | <span data-ttu-id="158e7-129">`Int64`, `Double`, Lub `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="158e7-129">An `Int64`, `Double`, or `Decimal`.</span></span> |

<span data-ttu-id="158e7-130">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="158e7-130">**Return Value**</span></span>

<span data-ttu-id="158e7-131">Typ `value`.</span><span class="sxs-lookup"><span data-stu-id="158e7-131">The type of `value`.</span></span>

<span data-ttu-id="158e7-132">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="158e7-132">**Example**</span></span>

`Power(748.58,2)`

## <a name="roundvalue"></a><span data-ttu-id="158e7-133">ROUND(Value)</span><span class="sxs-lookup"><span data-stu-id="158e7-133">Round(value)</span></span>

<span data-ttu-id="158e7-134">Zwraca część całkowitą `value`, zaokrąglony do najbliższej liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="158e7-134">Returns the integer portion of `value`, rounded to the nearest integer.</span></span>

<span data-ttu-id="158e7-135">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="158e7-135">**Arguments**</span></span>

<span data-ttu-id="158e7-136">A `Single`, `Double`, i `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="158e7-136">A `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="158e7-137">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="158e7-137">**Return Value**</span></span>

<span data-ttu-id="158e7-138">Typ `value`.</span><span class="sxs-lookup"><span data-stu-id="158e7-138">The type of `value`.</span></span>

<span data-ttu-id="158e7-139">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="158e7-139">**Example**</span></span>

`Round(748.58)`

## <a name="roundvalue-digits"></a><span data-ttu-id="158e7-140">Zaokrąglij (wartość cyfr)</span><span class="sxs-lookup"><span data-stu-id="158e7-140">Round(value, digits)</span></span>

<span data-ttu-id="158e7-141">Zwraca `value`, zaokrąglona do najbliższej wartości określone `digits`.</span><span class="sxs-lookup"><span data-stu-id="158e7-141">Returns the `value`, rounded to the nearest specified `digits`.</span></span>

<span data-ttu-id="158e7-142">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="158e7-142">**Arguments**</span></span>

|  |  |
|--|--|
|`value`|<span data-ttu-id="158e7-143">`Double` lub `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="158e7-143">`Double` or `Decimal`.</span></span>|
|`digits`|<span data-ttu-id="158e7-144">`Int16` lub `Int32`.</span><span class="sxs-lookup"><span data-stu-id="158e7-144">`Int16` or `Int32`.</span></span>|

<span data-ttu-id="158e7-145">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="158e7-145">**Return Value**</span></span>

<span data-ttu-id="158e7-146">Typ `value`.</span><span class="sxs-lookup"><span data-stu-id="158e7-146">The type of `value`.</span></span>

<span data-ttu-id="158e7-147">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="158e7-147">**Example**</span></span>

`Round(748.58,1)`

## <a name="truncatevalue-digits"></a><span data-ttu-id="158e7-148">Obetnij (wartość cyfr)</span><span class="sxs-lookup"><span data-stu-id="158e7-148">Truncate(value, digits)</span></span>

<span data-ttu-id="158e7-149">Zwraca `value`, obcięty do najbliższej wartości określone `digits`.</span><span class="sxs-lookup"><span data-stu-id="158e7-149">Returns the `value`, truncated to the nearest specified `digits`.</span></span>

<span data-ttu-id="158e7-150">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="158e7-150">**Arguments**</span></span>

|  |  |
|--|--|
|`value`|<span data-ttu-id="158e7-151">`Double` lub `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="158e7-151">`Double` or `Decimal`.</span></span>|
|`digits`|<span data-ttu-id="158e7-152">`Int16` lub `Int32`.</span><span class="sxs-lookup"><span data-stu-id="158e7-152">`Int16` or `Int32`.</span></span>|

<span data-ttu-id="158e7-153">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="158e7-153">**Return Value**</span></span>

<span data-ttu-id="158e7-154">Typ `value`.</span><span class="sxs-lookup"><span data-stu-id="158e7-154">The type of `value`.</span></span>

<span data-ttu-id="158e7-155">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="158e7-155">**Example**</span></span>

`Truncate(748.58,1)`  
  
 <span data-ttu-id="158e7-156">Te funkcje zwrócą `null` Jeśli `null` danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="158e7-156">These functions will return `null` if given `null` input.</span></span>  
  
 <span data-ttu-id="158e7-157">Równoważne funkcje są dostępne w Microsoft SQL klienta zarządzanego dostawcy.</span><span class="sxs-lookup"><span data-stu-id="158e7-157">Equivalent functionality is available in the Microsoft SQL Client Managed Provider.</span></span> <span data-ttu-id="158e7-158">Aby uzyskać więcej informacji, zobacz [Klient SQL dla funkcji programu Entity Framework](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span><span class="sxs-lookup"><span data-stu-id="158e7-158">For more information, see [SqlClient for Entity Framework Functions](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="158e7-159">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="158e7-159">See Also</span></span>  
 [<span data-ttu-id="158e7-160">Funkcje Canonical</span><span class="sxs-lookup"><span data-stu-id="158e7-160">Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
