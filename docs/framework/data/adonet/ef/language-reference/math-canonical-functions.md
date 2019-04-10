---
title: Funkcje matematyczne Canonical
ms.date: 03/30/2017
ms.assetid: 6f6cddc6-b561-4ebe-84b6-841ef5b4113b
ms.openlocfilehash: f575785bb198251ef50ba3563e736946253c9526
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59228773"
---
# <a name="math-canonical-functions"></a><span data-ttu-id="1c500-102">Funkcje matematyczne Canonical</span><span class="sxs-lookup"><span data-stu-id="1c500-102">Math Canonical Functions</span></span>

<span data-ttu-id="1c500-103">Jednostka SQL obejmuje następujące funkcje matematyczne canonical:</span><span class="sxs-lookup"><span data-stu-id="1c500-103">Entity SQL includes the following math canonical functions:</span></span>
  
## <a name="absvalue"></a><span data-ttu-id="1c500-104">ABS(Value)</span><span class="sxs-lookup"><span data-stu-id="1c500-104">Abs(value)</span></span>

<span data-ttu-id="1c500-105">Zwraca wartość bezwzględną liczby `value`.</span><span class="sxs-lookup"><span data-stu-id="1c500-105">Returns the absolute value of `value`.</span></span>

**<span data-ttu-id="1c500-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="1c500-106">Arguments</span></span>**

<span data-ttu-id="1c500-107">`Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, I `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="1c500-107">An `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, and `Decimal`.</span></span>

**<span data-ttu-id="1c500-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1c500-108">Return Value</span></span>**

<span data-ttu-id="1c500-109">Typ `value`.</span><span class="sxs-lookup"><span data-stu-id="1c500-109">The type of `value`.</span></span>

**<span data-ttu-id="1c500-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="1c500-110">Example</span></span>**

`Abs(-2)`

## <a name="ceilingvalue"></a><span data-ttu-id="1c500-111">CEILING(Value)</span><span class="sxs-lookup"><span data-stu-id="1c500-111">Ceiling(value)</span></span>

<span data-ttu-id="1c500-112">Zwraca najmniejszą liczbę całkowitą, która nie jest mniejsza niż `value`.</span><span class="sxs-lookup"><span data-stu-id="1c500-112">Returns the smallest integer that is not less than `value`.</span></span>

**<span data-ttu-id="1c500-113">Argumenty</span><span class="sxs-lookup"><span data-stu-id="1c500-113">Arguments</span></span>**

<span data-ttu-id="1c500-114">A `Single`, `Double`, i `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="1c500-114">A `Single`, `Double`, and `Decimal`.</span></span>

**<span data-ttu-id="1c500-115">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1c500-115">Return Value</span></span>**

<span data-ttu-id="1c500-116">Typ `value`.</span><span class="sxs-lookup"><span data-stu-id="1c500-116">The type of `value`.</span></span>

**<span data-ttu-id="1c500-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="1c500-117">Example</span></span>**

[!code-csharp[DP EntityServices Concepts#EDM_CEILING](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_ceiling)]
[!code-sql[DP EntityServices Concepts#EDM_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_ceiling)]

## <a name="floorvalue"></a><span data-ttu-id="1c500-118">FLOOR(Value)</span><span class="sxs-lookup"><span data-stu-id="1c500-118">Floor(value)</span></span>

<span data-ttu-id="1c500-119">Zwraca największą liczbą całkowitą, która nie jest większa niż `value`.</span><span class="sxs-lookup"><span data-stu-id="1c500-119">Returns the largest integer that is not greater than `value`.</span></span>

**<span data-ttu-id="1c500-120">Argumenty</span><span class="sxs-lookup"><span data-stu-id="1c500-120">Arguments</span></span>**

<span data-ttu-id="1c500-121">A `Single`, `Double`, i `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="1c500-121">A `Single`, `Double`, and `Decimal`.</span></span>

**<span data-ttu-id="1c500-122">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1c500-122">Return Value</span></span>**

<span data-ttu-id="1c500-123">Typ `value`.</span><span class="sxs-lookup"><span data-stu-id="1c500-123">The type of `value`.</span></span>

**<span data-ttu-id="1c500-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="1c500-124">Example</span></span>**

[!code-csharp[DP EntityServices Concepts#EDM_FLOOR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_floor)]
[!code-sql[DP EntityServices Concepts#EDM_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_floor)]

## <a name="powervalue-exponent"></a><span data-ttu-id="1c500-125">Zasilania (wartość wykładnika)</span><span class="sxs-lookup"><span data-stu-id="1c500-125">Power(value, exponent)</span></span>

<span data-ttu-id="1c500-126">Zwraca wynik określony `value` określonej `exponent`.</span><span class="sxs-lookup"><span data-stu-id="1c500-126">Returns the result of the specified `value` to the specified `exponent`.</span></span>

**<span data-ttu-id="1c500-127">Argumenty</span><span class="sxs-lookup"><span data-stu-id="1c500-127">Arguments</span></span>**

|  |  |
|--|--|
|`value` | <span data-ttu-id="1c500-128">`Int32, Int64, Double`, Lub `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="1c500-128">An `Int32, Int64, Double`, or `Decimal`.</span></span> |
|`exponent` | <span data-ttu-id="1c500-129">`Int64`, `Double`, Lub `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="1c500-129">An `Int64`, `Double`, or `Decimal`.</span></span> |

**<span data-ttu-id="1c500-130">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1c500-130">Return Value</span></span>**

<span data-ttu-id="1c500-131">Typ `value`.</span><span class="sxs-lookup"><span data-stu-id="1c500-131">The type of `value`.</span></span>

**<span data-ttu-id="1c500-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="1c500-132">Example</span></span>**

`Power(748.58,2)`

## <a name="roundvalue"></a><span data-ttu-id="1c500-133">ROUND(Value)</span><span class="sxs-lookup"><span data-stu-id="1c500-133">Round(value)</span></span>

<span data-ttu-id="1c500-134">Zwraca część całkowitą `value`, zaokrąglony do najbliższej liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="1c500-134">Returns the integer portion of `value`, rounded to the nearest integer.</span></span>

**<span data-ttu-id="1c500-135">Argumenty</span><span class="sxs-lookup"><span data-stu-id="1c500-135">Arguments</span></span>**

<span data-ttu-id="1c500-136">A `Single`, `Double`, i `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="1c500-136">A `Single`, `Double`, and `Decimal`.</span></span>

**<span data-ttu-id="1c500-137">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1c500-137">Return Value</span></span>**

<span data-ttu-id="1c500-138">Typ `value`.</span><span class="sxs-lookup"><span data-stu-id="1c500-138">The type of `value`.</span></span>

**<span data-ttu-id="1c500-139">Przykład</span><span class="sxs-lookup"><span data-stu-id="1c500-139">Example</span></span>**

`Round(748.58)`

## <a name="roundvalue-digits"></a><span data-ttu-id="1c500-140">Zaokrąglij (wartość cyfr)</span><span class="sxs-lookup"><span data-stu-id="1c500-140">Round(value, digits)</span></span>

<span data-ttu-id="1c500-141">Zwraca `value`, zaokrąglona do najbliższej wartości określone `digits`.</span><span class="sxs-lookup"><span data-stu-id="1c500-141">Returns the `value`, rounded to the nearest specified `digits`.</span></span>

**<span data-ttu-id="1c500-142">Argumenty</span><span class="sxs-lookup"><span data-stu-id="1c500-142">Arguments</span></span>**

|  |  |
|--|--|
|`value`|`Double` <span data-ttu-id="1c500-143">lub `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="1c500-143">or `Decimal`.</span></span>|
|`digits`|`Int16` <span data-ttu-id="1c500-144">lub `Int32`.</span><span class="sxs-lookup"><span data-stu-id="1c500-144">or `Int32`.</span></span>|

**<span data-ttu-id="1c500-145">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1c500-145">Return Value</span></span>**

<span data-ttu-id="1c500-146">Typ `value`.</span><span class="sxs-lookup"><span data-stu-id="1c500-146">The type of `value`.</span></span>

**<span data-ttu-id="1c500-147">Przykład</span><span class="sxs-lookup"><span data-stu-id="1c500-147">Example</span></span>**

`Round(748.58,1)`

## <a name="truncatevalue-digits"></a><span data-ttu-id="1c500-148">Obetnij (wartość cyfr)</span><span class="sxs-lookup"><span data-stu-id="1c500-148">Truncate(value, digits)</span></span>

<span data-ttu-id="1c500-149">Zwraca `value`, obcięty do najbliższej wartości określone `digits`.</span><span class="sxs-lookup"><span data-stu-id="1c500-149">Returns the `value`, truncated to the nearest specified `digits`.</span></span>

**<span data-ttu-id="1c500-150">Argumenty</span><span class="sxs-lookup"><span data-stu-id="1c500-150">Arguments</span></span>**

|  |  |
|--|--|
|`value`|`Double` <span data-ttu-id="1c500-151">lub `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="1c500-151">or `Decimal`.</span></span>|
|`digits`|`Int16` <span data-ttu-id="1c500-152">lub `Int32`.</span><span class="sxs-lookup"><span data-stu-id="1c500-152">or `Int32`.</span></span>|

**<span data-ttu-id="1c500-153">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1c500-153">Return Value</span></span>**

<span data-ttu-id="1c500-154">Typ `value`.</span><span class="sxs-lookup"><span data-stu-id="1c500-154">The type of `value`.</span></span>

**<span data-ttu-id="1c500-155">Przykład</span><span class="sxs-lookup"><span data-stu-id="1c500-155">Example</span></span>**

`Truncate(748.58,1)`  
  
 <span data-ttu-id="1c500-156">Te funkcje zwrócą `null` Jeśli `null` danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="1c500-156">These functions will return `null` if given `null` input.</span></span>  
  
 <span data-ttu-id="1c500-157">Równoważne funkcje są dostępne w Microsoft SQL klienta zarządzanego dostawcy.</span><span class="sxs-lookup"><span data-stu-id="1c500-157">Equivalent functionality is available in the Microsoft SQL Client Managed Provider.</span></span> <span data-ttu-id="1c500-158">Aby uzyskać więcej informacji, zobacz [Klient SQL dla funkcji programu Entity Framework](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span><span class="sxs-lookup"><span data-stu-id="1c500-158">For more information, see [SqlClient for Entity Framework Functions](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c500-159">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1c500-159">See also</span></span>

- [<span data-ttu-id="1c500-160">Funkcje Canonical</span><span class="sxs-lookup"><span data-stu-id="1c500-160">Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
