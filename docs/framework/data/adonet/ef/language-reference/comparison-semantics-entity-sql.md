---
title: Semantyka porównania (entity SQL)
ms.date: 03/30/2017
ms.assetid: b36ce28a-2fe4-4236-b782-e5f7c054deae
ms.openlocfilehash: 57d81d4b581df76a4382ad5e1d72fe8250b10d43
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150457"
---
# <a name="comparison-semantics-entity-sql"></a><span data-ttu-id="6e7bc-102">Semantyka porównania (entity SQL)</span><span class="sxs-lookup"><span data-stu-id="6e7bc-102">Comparison Semantics (Entity SQL)</span></span>
<span data-ttu-id="6e7bc-103">Wykonywanie dowolnego z [!INCLUDE[esql](../../../../../../includes/esql-md.md)] następujących operatorów obejmuje porównanie wystąpień typu:</span><span class="sxs-lookup"><span data-stu-id="6e7bc-103">Performing any of the following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operators involves comparison of type instances:</span></span>  
  
## <a name="explicit-comparison"></a><span data-ttu-id="6e7bc-104">Jawne porównanie</span><span class="sxs-lookup"><span data-stu-id="6e7bc-104">Explicit comparison</span></span>  
 <span data-ttu-id="6e7bc-105">Operacje równości:</span><span class="sxs-lookup"><span data-stu-id="6e7bc-105">Equality operations:</span></span>  
  
- =  
  
- <span data-ttu-id="6e7bc-106">!=</span><span class="sxs-lookup"><span data-stu-id="6e7bc-106">!=</span></span>  
  
 <span data-ttu-id="6e7bc-107">Operacje zamawiania:</span><span class="sxs-lookup"><span data-stu-id="6e7bc-107">Ordering operations:</span></span>  
  
- <  
  
- \<=  
  
- \>  
  
- \>=  
  
 <span data-ttu-id="6e7bc-108">Operacje anulowania:</span><span class="sxs-lookup"><span data-stu-id="6e7bc-108">Nullability operations:</span></span>  
  
- <span data-ttu-id="6e7bc-109">MA WARTOŚĆ NULL</span><span class="sxs-lookup"><span data-stu-id="6e7bc-109">IS NULL</span></span>  
  
- <span data-ttu-id="6e7bc-110">NIE MA WARTOŚCI NULL</span><span class="sxs-lookup"><span data-stu-id="6e7bc-110">IS NOT NULL</span></span>  
  
## <a name="explicit-distinction"></a><span data-ttu-id="6e7bc-111">Wyraźne rozróżnienie</span><span class="sxs-lookup"><span data-stu-id="6e7bc-111">Explicit distinction</span></span>  
 <span data-ttu-id="6e7bc-112">Rozróżnienie równości:</span><span class="sxs-lookup"><span data-stu-id="6e7bc-112">Equality distinction:</span></span>  
  
- <span data-ttu-id="6e7bc-113">DISTINCT</span><span class="sxs-lookup"><span data-stu-id="6e7bc-113">DISTINCT</span></span>  
  
- <span data-ttu-id="6e7bc-114">GROUP BY</span><span class="sxs-lookup"><span data-stu-id="6e7bc-114">GROUP BY</span></span>  
  
 <span data-ttu-id="6e7bc-115">Wyróżnienie zamawiania:</span><span class="sxs-lookup"><span data-stu-id="6e7bc-115">Ordering distinction:</span></span>  
  
- <span data-ttu-id="6e7bc-116">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="6e7bc-116">ORDER BY</span></span>  
  
## <a name="implicit-distinction"></a><span data-ttu-id="6e7bc-117">Niejawne rozróżnienie</span><span class="sxs-lookup"><span data-stu-id="6e7bc-117">Implicit distinction</span></span>  
 <span data-ttu-id="6e7bc-118">Ustaw operacje i predykaty (równość):</span><span class="sxs-lookup"><span data-stu-id="6e7bc-118">Set operations and predicates (equality):</span></span>  
  
- <span data-ttu-id="6e7bc-119">UNION</span><span class="sxs-lookup"><span data-stu-id="6e7bc-119">UNION</span></span>  
  
- <span data-ttu-id="6e7bc-120">INTERSECT</span><span class="sxs-lookup"><span data-stu-id="6e7bc-120">INTERSECT</span></span>  
  
- <span data-ttu-id="6e7bc-121">EXCEPT</span><span class="sxs-lookup"><span data-stu-id="6e7bc-121">EXCEPT</span></span>  
  
- <span data-ttu-id="6e7bc-122">SET</span><span class="sxs-lookup"><span data-stu-id="6e7bc-122">SET</span></span>  
  
- <span data-ttu-id="6e7bc-123">OVERLAPS</span><span class="sxs-lookup"><span data-stu-id="6e7bc-123">OVERLAPS</span></span>  
  
 <span data-ttu-id="6e7bc-124">Predykaty pozycji (równość):</span><span class="sxs-lookup"><span data-stu-id="6e7bc-124">Item predicates (equality):</span></span>  
  
- <span data-ttu-id="6e7bc-125">IN</span><span class="sxs-lookup"><span data-stu-id="6e7bc-125">IN</span></span>  
  
## <a name="supported-combinations"></a><span data-ttu-id="6e7bc-126">Obsługiwane kombinacje</span><span class="sxs-lookup"><span data-stu-id="6e7bc-126">Supported Combinations</span></span>  
 <span data-ttu-id="6e7bc-127">W poniższej tabeli przedstawiono wszystkie obsługiwane kombinacje operatorów porównania dla każdego rodzaju typu:</span><span class="sxs-lookup"><span data-stu-id="6e7bc-127">The following table shows all the supported combinations of comparison operators for each kind of type:</span></span>  
  
|<span data-ttu-id="6e7bc-128">**Typ**</span><span class="sxs-lookup"><span data-stu-id="6e7bc-128">**Type**</span></span>|**=**<br /><br /> <span data-ttu-id="6e7bc-129">**!=**</span><span class="sxs-lookup"><span data-stu-id="6e7bc-129">**!=**</span></span>|<span data-ttu-id="6e7bc-130">**GROUP BY**</span><span class="sxs-lookup"><span data-stu-id="6e7bc-130">**GROUP BY**</span></span><br /><br /> <span data-ttu-id="6e7bc-131">**Odrębne**</span><span class="sxs-lookup"><span data-stu-id="6e7bc-131">**DISTINCT**</span></span>|<span data-ttu-id="6e7bc-132">**Unii**</span><span class="sxs-lookup"><span data-stu-id="6e7bc-132">**UNION**</span></span><br /><br /> <span data-ttu-id="6e7bc-133">**INTERSECT**</span><span class="sxs-lookup"><span data-stu-id="6e7bc-133">**INTERSECT**</span></span><br /><br /> <span data-ttu-id="6e7bc-134">**EXCEPT**</span><span class="sxs-lookup"><span data-stu-id="6e7bc-134">**EXCEPT**</span></span><br /><br /> <span data-ttu-id="6e7bc-135">**Ustawić**</span><span class="sxs-lookup"><span data-stu-id="6e7bc-135">**SET**</span></span><br /><br /> <span data-ttu-id="6e7bc-136">**OVERLAPS**</span><span class="sxs-lookup"><span data-stu-id="6e7bc-136">**OVERLAPS**</span></span>|<span data-ttu-id="6e7bc-137">**IN**</span><span class="sxs-lookup"><span data-stu-id="6e7bc-137">**IN**</span></span>|<span data-ttu-id="6e7bc-138">**< <=**</span><span class="sxs-lookup"><span data-stu-id="6e7bc-138">**<   <=**</span></span><br /><br /> <span data-ttu-id="6e7bc-139">**> >=**</span><span class="sxs-lookup"><span data-stu-id="6e7bc-139">**>   >=**</span></span>|<span data-ttu-id="6e7bc-140">**ORDER BY**</span><span class="sxs-lookup"><span data-stu-id="6e7bc-140">**ORDER BY**</span></span>|<span data-ttu-id="6e7bc-141">**MA WARTOŚĆ NULL**</span><span class="sxs-lookup"><span data-stu-id="6e7bc-141">**IS NULL**</span></span><br /><br /> <span data-ttu-id="6e7bc-142">**NIE MA WARTOŚCI NULL**</span><span class="sxs-lookup"><span data-stu-id="6e7bc-142">**IS NOT NULL**</span></span>|  
|-|-|-|-|-|-|-|-|  
|<span data-ttu-id="6e7bc-143">Typ jednostki</span><span class="sxs-lookup"><span data-stu-id="6e7bc-143">Entity type</span></span>|<span data-ttu-id="6e7bc-144">Ref<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="6e7bc-144">Ref<sup>1</sup></span></span>|<span data-ttu-id="6e7bc-145">Wszystkie właściwości<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="6e7bc-145">All properties<sup>2</sup></span></span>|<span data-ttu-id="6e7bc-146">Wszystkie właściwości<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="6e7bc-146">All properties<sup>2</sup></span></span>|<span data-ttu-id="6e7bc-147">Wszystkie właściwości<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="6e7bc-147">All properties<sup>2</sup></span></span>|<span data-ttu-id="6e7bc-148">Rzut<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="6e7bc-148">Throw<sup>3</sup></span></span>|<span data-ttu-id="6e7bc-149">Rzut<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="6e7bc-149">Throw<sup>3</sup></span></span>|<span data-ttu-id="6e7bc-150">Ref<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="6e7bc-150">Ref<sup>1</sup></span></span>|  
|<span data-ttu-id="6e7bc-151">Typ złożony</span><span class="sxs-lookup"><span data-stu-id="6e7bc-151">Complex type</span></span>|<span data-ttu-id="6e7bc-152">Rzut<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="6e7bc-152">Throw<sup>3</sup></span></span>|<span data-ttu-id="6e7bc-153">Rzut<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="6e7bc-153">Throw<sup>3</sup></span></span>|<span data-ttu-id="6e7bc-154">Rzut<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="6e7bc-154">Throw<sup>3</sup></span></span>|<span data-ttu-id="6e7bc-155">Rzut<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="6e7bc-155">Throw<sup>3</sup></span></span>|<span data-ttu-id="6e7bc-156">Rzut<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="6e7bc-156">Throw<sup>3</sup></span></span>|<span data-ttu-id="6e7bc-157">Rzut<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="6e7bc-157">Throw<sup>3</sup></span></span>|<span data-ttu-id="6e7bc-158">Rzut<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="6e7bc-158">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="6e7bc-159">Wiersz</span><span class="sxs-lookup"><span data-stu-id="6e7bc-159">Row</span></span>|<span data-ttu-id="6e7bc-160">Wszystkie właściwości<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="6e7bc-160">All properties<sup>4</sup></span></span>|<span data-ttu-id="6e7bc-161">Wszystkie właściwości<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="6e7bc-161">All properties<sup>4</sup></span></span>|<span data-ttu-id="6e7bc-162">Wszystkie właściwości<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="6e7bc-162">All properties<sup>4</sup></span></span>|<span data-ttu-id="6e7bc-163">Rzut<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="6e7bc-163">Throw<sup>3</sup></span></span>|<span data-ttu-id="6e7bc-164">Rzut<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="6e7bc-164">Throw<sup>3</sup></span></span>|<span data-ttu-id="6e7bc-165">Wszystkie właściwości<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="6e7bc-165">All properties<sup>4</sup></span></span>|<span data-ttu-id="6e7bc-166">Rzut<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="6e7bc-166">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="6e7bc-167">Typ pierwotny</span><span class="sxs-lookup"><span data-stu-id="6e7bc-167">Primitive type</span></span>|<span data-ttu-id="6e7bc-168">Specyficzne dla dostawcy</span><span class="sxs-lookup"><span data-stu-id="6e7bc-168">Provider-specific</span></span>|<span data-ttu-id="6e7bc-169">Specyficzne dla dostawcy</span><span class="sxs-lookup"><span data-stu-id="6e7bc-169">Provider-specific</span></span>|<span data-ttu-id="6e7bc-170">Specyficzne dla dostawcy</span><span class="sxs-lookup"><span data-stu-id="6e7bc-170">Provider-specific</span></span>|<span data-ttu-id="6e7bc-171">Specyficzne dla dostawcy</span><span class="sxs-lookup"><span data-stu-id="6e7bc-171">Provider-specific</span></span>|<span data-ttu-id="6e7bc-172">Specyficzne dla dostawcy</span><span class="sxs-lookup"><span data-stu-id="6e7bc-172">Provider-specific</span></span>|<span data-ttu-id="6e7bc-173">Specyficzne dla dostawcy</span><span class="sxs-lookup"><span data-stu-id="6e7bc-173">Provider-specific</span></span>|<span data-ttu-id="6e7bc-174">Specyficzne dla dostawcy</span><span class="sxs-lookup"><span data-stu-id="6e7bc-174">Provider-specific</span></span>|  
|<span data-ttu-id="6e7bc-175">Zestaw wielokrotny</span><span class="sxs-lookup"><span data-stu-id="6e7bc-175">Multiset</span></span>|<span data-ttu-id="6e7bc-176">Rzut<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="6e7bc-176">Throw<sup>3</sup></span></span>|<span data-ttu-id="6e7bc-177">Rzut<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="6e7bc-177">Throw<sup>3</sup></span></span>|<span data-ttu-id="6e7bc-178">Rzut<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="6e7bc-178">Throw<sup>3</sup></span></span>|<span data-ttu-id="6e7bc-179">Rzut<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="6e7bc-179">Throw<sup>3</sup></span></span>|<span data-ttu-id="6e7bc-180">Rzut<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="6e7bc-180">Throw<sup>3</sup></span></span>|<span data-ttu-id="6e7bc-181">Rzut<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="6e7bc-181">Throw<sup>3</sup></span></span>|<span data-ttu-id="6e7bc-182">Rzut<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="6e7bc-182">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="6e7bc-183">Ref</span><span class="sxs-lookup"><span data-stu-id="6e7bc-183">Ref</span></span>|<span data-ttu-id="6e7bc-184">Tak<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="6e7bc-184">Yes<sup>5</sup></span></span>|<span data-ttu-id="6e7bc-185">Tak<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="6e7bc-185">Yes<sup>5</sup></span></span>|<span data-ttu-id="6e7bc-186">Tak<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="6e7bc-186">Yes<sup>5</sup></span></span>|<span data-ttu-id="6e7bc-187">Tak<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="6e7bc-187">Yes<sup>5</sup></span></span>|<span data-ttu-id="6e7bc-188">Throw</span><span class="sxs-lookup"><span data-stu-id="6e7bc-188">Throw</span></span>|<span data-ttu-id="6e7bc-189">Throw</span><span class="sxs-lookup"><span data-stu-id="6e7bc-189">Throw</span></span>|<span data-ttu-id="6e7bc-190">Tak<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="6e7bc-190">Yes<sup>5</sup></span></span>|  
|<span data-ttu-id="6e7bc-191">Stowarzyszenia</span><span class="sxs-lookup"><span data-stu-id="6e7bc-191">Association</span></span><br /><br /> <span data-ttu-id="6e7bc-192">type</span><span class="sxs-lookup"><span data-stu-id="6e7bc-192">type</span></span>|<span data-ttu-id="6e7bc-193">Rzut<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="6e7bc-193">Throw<sup>3</sup></span></span>|<span data-ttu-id="6e7bc-194">Throw</span><span class="sxs-lookup"><span data-stu-id="6e7bc-194">Throw</span></span>|<span data-ttu-id="6e7bc-195">Throw</span><span class="sxs-lookup"><span data-stu-id="6e7bc-195">Throw</span></span>|<span data-ttu-id="6e7bc-196">Throw</span><span class="sxs-lookup"><span data-stu-id="6e7bc-196">Throw</span></span>|<span data-ttu-id="6e7bc-197">Rzut<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="6e7bc-197">Throw<sup>3</sup></span></span>|<span data-ttu-id="6e7bc-198">Rzut<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="6e7bc-198">Throw<sup>3</sup></span></span>|<span data-ttu-id="6e7bc-199">Rzut<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="6e7bc-199">Throw<sup>3</sup></span></span>|  
  
 <span data-ttu-id="6e7bc-200"><sup>1.</sup> Odwołania do wystąpienia danego typu jednostki są niejawnie porównywane, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="6e7bc-200"><sup>1</sup>The references of the given entity type instances are implicitly compared, as shown in the following example:</span></span>  
  
```sql  
SELECT p1, p2
FROM AdventureWorksEntities.Product AS p1
     JOIN AdventureWorksEntities.Product AS p2
WHERE p1 != p2 OR p1 IS NULL  
```  
  
 <span data-ttu-id="6e7bc-201">Nie można porównać wystąpienia jednostki z jawnym odwołaniem.</span><span class="sxs-lookup"><span data-stu-id="6e7bc-201">An entity instance cannot be compared to an explicit reference.</span></span> <span data-ttu-id="6e7bc-202">W przypadku podjęcia tej próby zostanie zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="6e7bc-202">If this is attempted, an exception is thrown.</span></span> <span data-ttu-id="6e7bc-203">Na przykład następująca kwerenda zda wyjątek:</span><span class="sxs-lookup"><span data-stu-id="6e7bc-203">For example, the following query will throw an exception:</span></span>  
  
```sql  
SELECT p1, p2
FROM AdventureWorksEntities.Product AS p1
     JOIN AdventureWorksEntities.Product AS p2
WHERE p1 != REF(p2)  
```  
  
 <span data-ttu-id="6e7bc-204"><sup>2.</sup> Właściwości typów złożonych są spłaszczane przed wysłaniem do magazynu, więc stają się porównywalne (o ile wszystkie ich właściwości są porównywalne).</span><span class="sxs-lookup"><span data-stu-id="6e7bc-204"><sup>2</sup>Properties of complex types are flattened out before being sent to the store, so they become comparable (as long as all their properties are comparable).</span></span> <span data-ttu-id="6e7bc-205">Zobacz także <sup>4.</sup></span><span class="sxs-lookup"><span data-stu-id="6e7bc-205">Also see <sup>4.</sup></span></span>  
  
 <span data-ttu-id="6e7bc-206"><sup>3</sup> Środowisko uruchomieniowe entity framework wykrywa nieobsługiwał przypadek i zgłasza znaczący wyjątek bez angażowania dostawcy/magazynu.</span><span class="sxs-lookup"><span data-stu-id="6e7bc-206"><sup>3</sup>The Entity Framework runtime detects the unsupported case and throws a meaningful exception without engaging the provider/store.</span></span>  
  
 <span data-ttu-id="6e7bc-207"><sup>4</sup> Podejmowana jest próba porównania wszystkich właściwości.</span><span class="sxs-lookup"><span data-stu-id="6e7bc-207"><sup>4</sup>An attempt is made to compare all properties.</span></span> <span data-ttu-id="6e7bc-208">Jeśli istnieje właściwość, która jest typu niesymady, takich jak tekst, ntext lub obraz, może zostać zgłoszony wyjątek serwera.</span><span class="sxs-lookup"><span data-stu-id="6e7bc-208">If there is a property that is of a non-comparable type, such as text, ntext, or image, a server exception might be thrown.</span></span>  
  
 <span data-ttu-id="6e7bc-209"><sup>5</sup> Wszystkie poszczególne elementy odwołań są porównywane (obejmuje to nazwę zestawu jednostek i wszystkie kluczowe właściwości typu jednostki).</span><span class="sxs-lookup"><span data-stu-id="6e7bc-209"><sup>5</sup>All individual elements of the references are compared (this includes the entity set name and all the key properties of the entity type).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e7bc-210">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6e7bc-210">See also</span></span>

- [<span data-ttu-id="6e7bc-211">Omówienie jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="6e7bc-211">Entity SQL Overview</span></span>](entity-sql-overview.md)
