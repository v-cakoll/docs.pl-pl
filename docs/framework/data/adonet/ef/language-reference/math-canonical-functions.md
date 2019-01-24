---
title: Funkcje matematyczne Canonical
ms.date: 03/30/2017
ms.assetid: 6f6cddc6-b561-4ebe-84b6-841ef5b4113b
ms.openlocfilehash: 3e8122806e31fc72b3d390e5e8671fada7f3a47d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54492706"
---
# <a name="math-canonical-functions"></a><span data-ttu-id="f7a7f-102">Funkcje matematyczne Canonical</span><span class="sxs-lookup"><span data-stu-id="f7a7f-102">Math Canonical Functions</span></span>

<span data-ttu-id="f7a7f-103">Jednostka SQL obejmuje następujące funkcje matematyczne canonical:</span><span class="sxs-lookup"><span data-stu-id="f7a7f-103">Entity SQL includes the following math canonical functions:</span></span>
  
## <a name="absvalue"></a><span data-ttu-id="f7a7f-104">ABS(Value)</span><span class="sxs-lookup"><span data-stu-id="f7a7f-104">Abs(value)</span></span>

<span data-ttu-id="f7a7f-105">Zwraca wartość bezwzględną liczby `value`.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-105">Returns the absolute value of `value`.</span></span>

<span data-ttu-id="f7a7f-106">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="f7a7f-106">**Arguments**</span></span>

<span data-ttu-id="f7a7f-107">`Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, I `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-107">An `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="f7a7f-108">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="f7a7f-108">**Return Value**</span></span>

<span data-ttu-id="f7a7f-109">Typ `value`.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-109">The type of `value`.</span></span>

<span data-ttu-id="f7a7f-110">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="f7a7f-110">**Example**</span></span>

`Abs(-2)`

## <a name="ceilingvalue"></a><span data-ttu-id="f7a7f-111">CEILING(Value)</span><span class="sxs-lookup"><span data-stu-id="f7a7f-111">Ceiling(value)</span></span>

<span data-ttu-id="f7a7f-112">Zwraca najmniejszą liczbę całkowitą, która nie jest mniejsza niż `value`.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-112">Returns the smallest integer that is not less than `value`.</span></span>

<span data-ttu-id="f7a7f-113">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="f7a7f-113">**Arguments**</span></span>

<span data-ttu-id="f7a7f-114">A `Single`, `Double`, i `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-114">A `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="f7a7f-115">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="f7a7f-115">**Return Value**</span></span>

<span data-ttu-id="f7a7f-116">Typ `value`.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-116">The type of `value`.</span></span>

<span data-ttu-id="f7a7f-117">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="f7a7f-117">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_CEILING](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_ceiling)]
[!code-sql[DP EntityServices Concepts#EDM_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_ceiling)]

## <a name="floorvalue"></a><span data-ttu-id="f7a7f-118">FLOOR(Value)</span><span class="sxs-lookup"><span data-stu-id="f7a7f-118">Floor(value)</span></span>

<span data-ttu-id="f7a7f-119">Zwraca największą liczbą całkowitą, która nie jest większa niż `value`.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-119">Returns the largest integer that is not greater than `value`.</span></span>

<span data-ttu-id="f7a7f-120">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="f7a7f-120">**Arguments**</span></span>

<span data-ttu-id="f7a7f-121">A `Single`, `Double`, i `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-121">A `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="f7a7f-122">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="f7a7f-122">**Return Value**</span></span>

<span data-ttu-id="f7a7f-123">Typ `value`.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-123">The type of `value`.</span></span>

<span data-ttu-id="f7a7f-124">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="f7a7f-124">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_FLOOR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_floor)]
[!code-sql[DP EntityServices Concepts#EDM_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_floor)]

## <a name="powervalue-exponent"></a><span data-ttu-id="f7a7f-125">Zasilania (wartość wykładnika)</span><span class="sxs-lookup"><span data-stu-id="f7a7f-125">Power(value, exponent)</span></span>

<span data-ttu-id="f7a7f-126">Zwraca wynik określony `value` określonej `exponent`.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-126">Returns the result of the specified `value` to the specified `exponent`.</span></span>

<span data-ttu-id="f7a7f-127">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="f7a7f-127">**Arguments**</span></span>

|  |  |
|--|--|
|`value` | <span data-ttu-id="f7a7f-128">`Int32, Int64, Double`, Lub `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-128">An `Int32, Int64, Double`, or `Decimal`.</span></span> |
|`exponent` | <span data-ttu-id="f7a7f-129">`Int64`, `Double`, Lub `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-129">An `Int64`, `Double`, or `Decimal`.</span></span> |

<span data-ttu-id="f7a7f-130">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="f7a7f-130">**Return Value**</span></span>

<span data-ttu-id="f7a7f-131">Typ `value`.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-131">The type of `value`.</span></span>

<span data-ttu-id="f7a7f-132">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="f7a7f-132">**Example**</span></span>

`Power(748.58,2)`

## <a name="roundvalue"></a><span data-ttu-id="f7a7f-133">ROUND(Value)</span><span class="sxs-lookup"><span data-stu-id="f7a7f-133">Round(value)</span></span>

<span data-ttu-id="f7a7f-134">Zwraca część całkowitą `value`, zaokrąglony do najbliższej liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-134">Returns the integer portion of `value`, rounded to the nearest integer.</span></span>

<span data-ttu-id="f7a7f-135">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="f7a7f-135">**Arguments**</span></span>

<span data-ttu-id="f7a7f-136">A `Single`, `Double`, i `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-136">A `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="f7a7f-137">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="f7a7f-137">**Return Value**</span></span>

<span data-ttu-id="f7a7f-138">Typ `value`.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-138">The type of `value`.</span></span>

<span data-ttu-id="f7a7f-139">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="f7a7f-139">**Example**</span></span>

`Round(748.58)`

## <a name="roundvalue-digits"></a><span data-ttu-id="f7a7f-140">Zaokrąglij (wartość cyfr)</span><span class="sxs-lookup"><span data-stu-id="f7a7f-140">Round(value, digits)</span></span>

<span data-ttu-id="f7a7f-141">Zwraca `value`, zaokrąglona do najbliższej wartości określone `digits`.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-141">Returns the `value`, rounded to the nearest specified `digits`.</span></span>

<span data-ttu-id="f7a7f-142">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="f7a7f-142">**Arguments**</span></span>

|  |  |
|--|--|
|`value`|<span data-ttu-id="f7a7f-143">`Double` lub `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-143">`Double` or `Decimal`.</span></span>|
|`digits`|<span data-ttu-id="f7a7f-144">`Int16` lub `Int32`.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-144">`Int16` or `Int32`.</span></span>|

<span data-ttu-id="f7a7f-145">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="f7a7f-145">**Return Value**</span></span>

<span data-ttu-id="f7a7f-146">Typ `value`.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-146">The type of `value`.</span></span>

<span data-ttu-id="f7a7f-147">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="f7a7f-147">**Example**</span></span>

`Round(748.58,1)`

## <a name="truncatevalue-digits"></a><span data-ttu-id="f7a7f-148">Obetnij (wartość cyfr)</span><span class="sxs-lookup"><span data-stu-id="f7a7f-148">Truncate(value, digits)</span></span>

<span data-ttu-id="f7a7f-149">Zwraca `value`, obcięty do najbliższej wartości określone `digits`.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-149">Returns the `value`, truncated to the nearest specified `digits`.</span></span>

<span data-ttu-id="f7a7f-150">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="f7a7f-150">**Arguments**</span></span>

|  |  |
|--|--|
|`value`|<span data-ttu-id="f7a7f-151">`Double` lub `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-151">`Double` or `Decimal`.</span></span>|
|`digits`|<span data-ttu-id="f7a7f-152">`Int16` lub `Int32`.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-152">`Int16` or `Int32`.</span></span>|

<span data-ttu-id="f7a7f-153">**Wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="f7a7f-153">**Return Value**</span></span>

<span data-ttu-id="f7a7f-154">Typ `value`.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-154">The type of `value`.</span></span>

<span data-ttu-id="f7a7f-155">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="f7a7f-155">**Example**</span></span>

`Truncate(748.58,1)`  
  
 <span data-ttu-id="f7a7f-156">Te funkcje zwrócą `null` Jeśli `null` danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-156">These functions will return `null` if given `null` input.</span></span>  
  
 <span data-ttu-id="f7a7f-157">Równoważne funkcje są dostępne w Microsoft SQL klienta zarządzanego dostawcy.</span><span class="sxs-lookup"><span data-stu-id="f7a7f-157">Equivalent functionality is available in the Microsoft SQL Client Managed Provider.</span></span> <span data-ttu-id="f7a7f-158">Aby uzyskać więcej informacji, zobacz [Klient SQL dla funkcji programu Entity Framework](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span><span class="sxs-lookup"><span data-stu-id="f7a7f-158">For more information, see [SqlClient for Entity Framework Functions](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7a7f-159">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f7a7f-159">See also</span></span>
- [<span data-ttu-id="f7a7f-160">Funkcje Canonical</span><span class="sxs-lookup"><span data-stu-id="f7a7f-160">Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
