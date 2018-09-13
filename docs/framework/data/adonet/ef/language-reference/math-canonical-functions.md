---
title: Funkcje matematyczne Canonical
ms.date: 03/30/2017
ms.assetid: 6f6cddc6-b561-4ebe-84b6-841ef5b4113b
ms.openlocfilehash: 0fc9f4942c3f76f139ab7e4400005f0bfe80204e
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44708091"
---
# <a name="math-canonical-functions"></a><span data-ttu-id="6004a-102">Funkcje matematyczne Canonical</span><span class="sxs-lookup"><span data-stu-id="6004a-102">Math Canonical Functions</span></span>

<span data-ttu-id="6004a-103">Jednostka SQL obejmuje następujące funkcje matematyczne canonical:</span><span class="sxs-lookup"><span data-stu-id="6004a-103">Entity SQL includes the following math canonical functions:</span></span>
  
## <a name="absvalue"></a><span data-ttu-id="6004a-104">ABS(Value)</span><span class="sxs-lookup"><span data-stu-id="6004a-104">Abs(value)</span></span>

<span data-ttu-id="6004a-105">Zwraca wartość bezwzględną liczby `value`.</span><span class="sxs-lookup"><span data-stu-id="6004a-105">Returns the absolute value of `value`.</span></span>

<span data-ttu-id="6004a-106">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="6004a-106">**Arguments**</span></span>

<span data-ttu-id="6004a-107">`Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, I `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="6004a-107">An `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="6004a-108">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="6004a-108">**Return Value**</span></span>

<span data-ttu-id="6004a-109">Typ `value`.</span><span class="sxs-lookup"><span data-stu-id="6004a-109">The type of `value`.</span></span>

<span data-ttu-id="6004a-110">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="6004a-110">**Example**</span></span>

`Abs(-2)`

## <a name="ceilingvalue"></a><span data-ttu-id="6004a-111">CEILING(Value)</span><span class="sxs-lookup"><span data-stu-id="6004a-111">Ceiling(value)</span></span>

<span data-ttu-id="6004a-112">Zwraca najmniejszą liczbę całkowitą, która nie jest mniejsza niż `value`.</span><span class="sxs-lookup"><span data-stu-id="6004a-112">Returns the smallest integer that is not less than `value`.</span></span>

<span data-ttu-id="6004a-113">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="6004a-113">**Arguments**</span></span>

<span data-ttu-id="6004a-114">A `Single`, `Double`, i `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="6004a-114">A `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="6004a-115">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="6004a-115">**Return Value**</span></span>

<span data-ttu-id="6004a-116">Typ `value`.</span><span class="sxs-lookup"><span data-stu-id="6004a-116">The type of `value`.</span></span>

<span data-ttu-id="6004a-117">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="6004a-117">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_CEILING](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_ceiling)]
[!code-sql[DP EntityServices Concepts#EDM_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_ceiling)]

## <a name="floorvalue"></a><span data-ttu-id="6004a-118">FLOOR(Value)</span><span class="sxs-lookup"><span data-stu-id="6004a-118">Floor(value)</span></span>

<span data-ttu-id="6004a-119">Zwraca największą liczbą całkowitą, która nie jest większa niż `value`.</span><span class="sxs-lookup"><span data-stu-id="6004a-119">Returns the largest integer that is not greater than `value`.</span></span>

<span data-ttu-id="6004a-120">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="6004a-120">**Arguments**</span></span>

<span data-ttu-id="6004a-121">A `Single`, `Double`, i `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="6004a-121">A `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="6004a-122">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="6004a-122">**Return Value**</span></span>

<span data-ttu-id="6004a-123">Typ `value`.</span><span class="sxs-lookup"><span data-stu-id="6004a-123">The type of `value`.</span></span>

<span data-ttu-id="6004a-124">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="6004a-124">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_FLOOR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_floor)]
[!code-sql[DP EntityServices Concepts#EDM_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_floor)]

## <a name="powervalue-exponent"></a><span data-ttu-id="6004a-125">Zasilania (wartość wykładnika)</span><span class="sxs-lookup"><span data-stu-id="6004a-125">Power(value, exponent)</span></span>

<span data-ttu-id="6004a-126">Zwraca wynik określony `value` określonej `exponent`.</span><span class="sxs-lookup"><span data-stu-id="6004a-126">Returns the result of the specified `value` to the specified `exponent`.</span></span>

<span data-ttu-id="6004a-127">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="6004a-127">**Arguments**</span></span>

|  |  |
|--|--|
|`value` | <span data-ttu-id="6004a-128">`Int32, Int64, Double`, Lub `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="6004a-128">An `Int32, Int64, Double`, or `Decimal`.</span></span> |
|`exponent` | <span data-ttu-id="6004a-129">`Int64`, `Double`, Lub `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="6004a-129">An `Int64`, `Double`, or `Decimal`.</span></span> |

<span data-ttu-id="6004a-130">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="6004a-130">**Return Value**</span></span>

<span data-ttu-id="6004a-131">Typ `value`.</span><span class="sxs-lookup"><span data-stu-id="6004a-131">The type of `value`.</span></span>

<span data-ttu-id="6004a-132">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="6004a-132">**Example**</span></span>

`Power(748.58,2)`

## <a name="roundvalue"></a><span data-ttu-id="6004a-133">ROUND(Value)</span><span class="sxs-lookup"><span data-stu-id="6004a-133">Round(value)</span></span>

<span data-ttu-id="6004a-134">Zwraca część całkowitą `value`, zaokrąglony do najbliższej liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="6004a-134">Returns the integer portion of `value`, rounded to the nearest integer.</span></span>

<span data-ttu-id="6004a-135">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="6004a-135">**Arguments**</span></span>

<span data-ttu-id="6004a-136">A `Single`, `Double`, i `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="6004a-136">A `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="6004a-137">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="6004a-137">**Return Value**</span></span>

<span data-ttu-id="6004a-138">Typ `value`.</span><span class="sxs-lookup"><span data-stu-id="6004a-138">The type of `value`.</span></span>

<span data-ttu-id="6004a-139">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="6004a-139">**Example**</span></span>

`Round(748.58)`

## <a name="roundvalue-digits"></a><span data-ttu-id="6004a-140">Zaokrąglij (wartość cyfr)</span><span class="sxs-lookup"><span data-stu-id="6004a-140">Round(value, digits)</span></span>

<span data-ttu-id="6004a-141">Zwraca `value`, zaokrąglona do najbliższej wartości określone `digits`.</span><span class="sxs-lookup"><span data-stu-id="6004a-141">Returns the `value`, rounded to the nearest specified `digits`.</span></span>

<span data-ttu-id="6004a-142">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="6004a-142">**Arguments**</span></span>

|  |  |
|--|--|
|`value`|<span data-ttu-id="6004a-143">`Double` lub `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="6004a-143">`Double` or `Decimal`.</span></span>|
|`digits`|<span data-ttu-id="6004a-144">`Int16` lub `Int32`.</span><span class="sxs-lookup"><span data-stu-id="6004a-144">`Int16` or `Int32`.</span></span>|

<span data-ttu-id="6004a-145">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="6004a-145">**Return Value**</span></span>

<span data-ttu-id="6004a-146">Typ `value`.</span><span class="sxs-lookup"><span data-stu-id="6004a-146">The type of `value`.</span></span>

<span data-ttu-id="6004a-147">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="6004a-147">**Example**</span></span>

`Round(748.58,1)`

## <a name="truncatevalue-digits"></a><span data-ttu-id="6004a-148">Obetnij (wartość cyfr)</span><span class="sxs-lookup"><span data-stu-id="6004a-148">Truncate(value, digits)</span></span>

<span data-ttu-id="6004a-149">Zwraca `value`, obcięty do najbliższej wartości określone `digits`.</span><span class="sxs-lookup"><span data-stu-id="6004a-149">Returns the `value`, truncated to the nearest specified `digits`.</span></span>

<span data-ttu-id="6004a-150">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="6004a-150">**Arguments**</span></span>

|  |  |
|--|--|
|`value`|<span data-ttu-id="6004a-151">`Double` lub `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="6004a-151">`Double` or `Decimal`.</span></span>|
|`digits`|<span data-ttu-id="6004a-152">`Int16` lub `Int32`.</span><span class="sxs-lookup"><span data-stu-id="6004a-152">`Int16` or `Int32`.</span></span>|

<span data-ttu-id="6004a-153">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="6004a-153">**Return Value**</span></span>

<span data-ttu-id="6004a-154">Typ `value`.</span><span class="sxs-lookup"><span data-stu-id="6004a-154">The type of `value`.</span></span>

<span data-ttu-id="6004a-155">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="6004a-155">**Example**</span></span>

`Truncate(748.58,1)`  
  
 <span data-ttu-id="6004a-156">Te funkcje zwrócą `null` Jeśli `null` danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="6004a-156">These functions will return `null` if given `null` input.</span></span>  
  
 <span data-ttu-id="6004a-157">Równoważne funkcje są dostępne w Microsoft SQL klienta zarządzanego dostawcy.</span><span class="sxs-lookup"><span data-stu-id="6004a-157">Equivalent functionality is available in the Microsoft SQL Client Managed Provider.</span></span> <span data-ttu-id="6004a-158">Aby uzyskać więcej informacji, zobacz [Klient SQL dla funkcji programu Entity Framework](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span><span class="sxs-lookup"><span data-stu-id="6004a-158">For more information, see [SqlClient for Entity Framework Functions](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6004a-159">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6004a-159">See Also</span></span>  
 [<span data-ttu-id="6004a-160">Funkcje Canonical</span><span class="sxs-lookup"><span data-stu-id="6004a-160">Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
