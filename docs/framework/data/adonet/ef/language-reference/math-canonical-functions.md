---
title: Funkcje matematyczne Canonical
ms.date: 03/30/2017
ms.assetid: 6f6cddc6-b561-4ebe-84b6-841ef5b4113b
ms.openlocfilehash: 0fc9f4942c3f76f139ab7e4400005f0bfe80204e
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43564808"
---
# <a name="math-canonical-functions"></a><span data-ttu-id="0d0b4-102">Funkcje matematyczne Canonical</span><span class="sxs-lookup"><span data-stu-id="0d0b4-102">Math Canonical Functions</span></span>

<span data-ttu-id="0d0b4-103">Jednostka SQL obejmuje następujące funkcje matematyczne canonical:</span><span class="sxs-lookup"><span data-stu-id="0d0b4-103">Entity SQL includes the following math canonical functions:</span></span>
  
## <a name="absvalue"></a><span data-ttu-id="0d0b4-104">ABS(Value)</span><span class="sxs-lookup"><span data-stu-id="0d0b4-104">Abs(value)</span></span>

<span data-ttu-id="0d0b4-105">Zwraca wartość bezwzględną liczby `value`.</span><span class="sxs-lookup"><span data-stu-id="0d0b4-105">Returns the absolute value of `value`.</span></span>

<span data-ttu-id="0d0b4-106">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="0d0b4-106">**Arguments**</span></span>

<span data-ttu-id="0d0b4-107">`Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, I `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="0d0b4-107">An `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="0d0b4-108">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="0d0b4-108">**Return Value**</span></span>

<span data-ttu-id="0d0b4-109">Typ `value`.</span><span class="sxs-lookup"><span data-stu-id="0d0b4-109">The type of `value`.</span></span>

<span data-ttu-id="0d0b4-110">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="0d0b4-110">**Example**</span></span>

`Abs(-2)`

## <a name="ceilingvalue"></a><span data-ttu-id="0d0b4-111">CEILING(Value)</span><span class="sxs-lookup"><span data-stu-id="0d0b4-111">Ceiling(value)</span></span>

<span data-ttu-id="0d0b4-112">Zwraca najmniejszą liczbę całkowitą, która nie jest mniejsza niż `value`.</span><span class="sxs-lookup"><span data-stu-id="0d0b4-112">Returns the smallest integer that is not less than `value`.</span></span>

<span data-ttu-id="0d0b4-113">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="0d0b4-113">**Arguments**</span></span>

<span data-ttu-id="0d0b4-114">A `Single`, `Double`, i `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="0d0b4-114">A `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="0d0b4-115">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="0d0b4-115">**Return Value**</span></span>

<span data-ttu-id="0d0b4-116">Typ `value`.</span><span class="sxs-lookup"><span data-stu-id="0d0b4-116">The type of `value`.</span></span>

<span data-ttu-id="0d0b4-117">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="0d0b4-117">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_CEILING](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_ceiling)]
[!code-sql[DP EntityServices Concepts#EDM_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_ceiling)]

## <a name="floorvalue"></a><span data-ttu-id="0d0b4-118">FLOOR(Value)</span><span class="sxs-lookup"><span data-stu-id="0d0b4-118">Floor(value)</span></span>

<span data-ttu-id="0d0b4-119">Zwraca największą liczbą całkowitą, która nie jest większa niż `value`.</span><span class="sxs-lookup"><span data-stu-id="0d0b4-119">Returns the largest integer that is not greater than `value`.</span></span>

<span data-ttu-id="0d0b4-120">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="0d0b4-120">**Arguments**</span></span>

<span data-ttu-id="0d0b4-121">A `Single`, `Double`, i `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="0d0b4-121">A `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="0d0b4-122">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="0d0b4-122">**Return Value**</span></span>

<span data-ttu-id="0d0b4-123">Typ `value`.</span><span class="sxs-lookup"><span data-stu-id="0d0b4-123">The type of `value`.</span></span>

<span data-ttu-id="0d0b4-124">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="0d0b4-124">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_FLOOR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_floor)]
[!code-sql[DP EntityServices Concepts#EDM_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_floor)]

## <a name="powervalue-exponent"></a><span data-ttu-id="0d0b4-125">Zasilania (wartość wykładnika)</span><span class="sxs-lookup"><span data-stu-id="0d0b4-125">Power(value, exponent)</span></span>

<span data-ttu-id="0d0b4-126">Zwraca wynik określony `value` określonej `exponent`.</span><span class="sxs-lookup"><span data-stu-id="0d0b4-126">Returns the result of the specified `value` to the specified `exponent`.</span></span>

<span data-ttu-id="0d0b4-127">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="0d0b4-127">**Arguments**</span></span>

|  |  |
|--|--|
|`value` | <span data-ttu-id="0d0b4-128">`Int32, Int64, Double`, Lub `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="0d0b4-128">An `Int32, Int64, Double`, or `Decimal`.</span></span> |
|`exponent` | <span data-ttu-id="0d0b4-129">`Int64`, `Double`, Lub `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="0d0b4-129">An `Int64`, `Double`, or `Decimal`.</span></span> |

<span data-ttu-id="0d0b4-130">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="0d0b4-130">**Return Value**</span></span>

<span data-ttu-id="0d0b4-131">Typ `value`.</span><span class="sxs-lookup"><span data-stu-id="0d0b4-131">The type of `value`.</span></span>

<span data-ttu-id="0d0b4-132">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="0d0b4-132">**Example**</span></span>

`Power(748.58,2)`

## <a name="roundvalue"></a><span data-ttu-id="0d0b4-133">ROUND(Value)</span><span class="sxs-lookup"><span data-stu-id="0d0b4-133">Round(value)</span></span>

<span data-ttu-id="0d0b4-134">Zwraca część całkowitą `value`, zaokrąglony do najbliższej liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="0d0b4-134">Returns the integer portion of `value`, rounded to the nearest integer.</span></span>

<span data-ttu-id="0d0b4-135">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="0d0b4-135">**Arguments**</span></span>

<span data-ttu-id="0d0b4-136">A `Single`, `Double`, i `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="0d0b4-136">A `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="0d0b4-137">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="0d0b4-137">**Return Value**</span></span>

<span data-ttu-id="0d0b4-138">Typ `value`.</span><span class="sxs-lookup"><span data-stu-id="0d0b4-138">The type of `value`.</span></span>

<span data-ttu-id="0d0b4-139">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="0d0b4-139">**Example**</span></span>

`Round(748.58)`

## <a name="roundvalue-digits"></a><span data-ttu-id="0d0b4-140">Zaokrąglij (wartość cyfr)</span><span class="sxs-lookup"><span data-stu-id="0d0b4-140">Round(value, digits)</span></span>

<span data-ttu-id="0d0b4-141">Zwraca `value`, zaokrąglona do najbliższej wartości określone `digits`.</span><span class="sxs-lookup"><span data-stu-id="0d0b4-141">Returns the `value`, rounded to the nearest specified `digits`.</span></span>

<span data-ttu-id="0d0b4-142">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="0d0b4-142">**Arguments**</span></span>

|  |  |
|--|--|
|`value`|<span data-ttu-id="0d0b4-143">`Double` lub `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="0d0b4-143">`Double` or `Decimal`.</span></span>|
|`digits`|<span data-ttu-id="0d0b4-144">`Int16` lub `Int32`.</span><span class="sxs-lookup"><span data-stu-id="0d0b4-144">`Int16` or `Int32`.</span></span>|

<span data-ttu-id="0d0b4-145">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="0d0b4-145">**Return Value**</span></span>

<span data-ttu-id="0d0b4-146">Typ `value`.</span><span class="sxs-lookup"><span data-stu-id="0d0b4-146">The type of `value`.</span></span>

<span data-ttu-id="0d0b4-147">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="0d0b4-147">**Example**</span></span>

`Round(748.58,1)`

## <a name="truncatevalue-digits"></a><span data-ttu-id="0d0b4-148">Obetnij (wartość cyfr)</span><span class="sxs-lookup"><span data-stu-id="0d0b4-148">Truncate(value, digits)</span></span>

<span data-ttu-id="0d0b4-149">Zwraca `value`, obcięty do najbliższej wartości określone `digits`.</span><span class="sxs-lookup"><span data-stu-id="0d0b4-149">Returns the `value`, truncated to the nearest specified `digits`.</span></span>

<span data-ttu-id="0d0b4-150">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="0d0b4-150">**Arguments**</span></span>

|  |  |
|--|--|
|`value`|<span data-ttu-id="0d0b4-151">`Double` lub `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="0d0b4-151">`Double` or `Decimal`.</span></span>|
|`digits`|<span data-ttu-id="0d0b4-152">`Int16` lub `Int32`.</span><span class="sxs-lookup"><span data-stu-id="0d0b4-152">`Int16` or `Int32`.</span></span>|

<span data-ttu-id="0d0b4-153">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="0d0b4-153">**Return Value**</span></span>

<span data-ttu-id="0d0b4-154">Typ `value`.</span><span class="sxs-lookup"><span data-stu-id="0d0b4-154">The type of `value`.</span></span>

<span data-ttu-id="0d0b4-155">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="0d0b4-155">**Example**</span></span>

`Truncate(748.58,1)`  
  
 <span data-ttu-id="0d0b4-156">Te funkcje zwrócą `null` Jeśli `null` danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="0d0b4-156">These functions will return `null` if given `null` input.</span></span>  
  
 <span data-ttu-id="0d0b4-157">Równoważne funkcje są dostępne w Microsoft SQL klienta zarządzanego dostawcy.</span><span class="sxs-lookup"><span data-stu-id="0d0b4-157">Equivalent functionality is available in the Microsoft SQL Client Managed Provider.</span></span> <span data-ttu-id="0d0b4-158">Aby uzyskać więcej informacji, zobacz [Klient SQL dla funkcji programu Entity Framework](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span><span class="sxs-lookup"><span data-stu-id="0d0b4-158">For more information, see [SqlClient for Entity Framework Functions](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d0b4-159">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0d0b4-159">See Also</span></span>  
 [<span data-ttu-id="0d0b4-160">Funkcje Canonical</span><span class="sxs-lookup"><span data-stu-id="0d0b4-160">Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
