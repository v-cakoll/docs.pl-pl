---
title: Semantyka porównania (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: b36ce28a-2fe4-4236-b782-e5f7c054deae
ms.openlocfilehash: 6b4c4177ebd6c45e00a1ac7774e40a43e0c14a74
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61605974"
---
# <a name="comparison-semantics-entity-sql"></a><span data-ttu-id="cae4f-102">Semantyka porównania (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="cae4f-102">Comparison Semantics (Entity SQL)</span></span>
<span data-ttu-id="cae4f-103">Wykonanie dowolnego z następujących [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatory obejmuje porównanie wystąpień typu:</span><span class="sxs-lookup"><span data-stu-id="cae4f-103">Performing any of the following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operators involves comparison of type instances:</span></span>  
  
## <a name="explicit-comparison"></a><span data-ttu-id="cae4f-104">Porównanie jawne</span><span class="sxs-lookup"><span data-stu-id="cae4f-104">Explicit comparison</span></span>  
 <span data-ttu-id="cae4f-105">Operacje równości:</span><span class="sxs-lookup"><span data-stu-id="cae4f-105">Equality operations:</span></span>  
  
- =  
  
- <span data-ttu-id="cae4f-106">!=</span><span class="sxs-lookup"><span data-stu-id="cae4f-106">!=</span></span>  
  
 <span data-ttu-id="cae4f-107">Kolejność operacji:</span><span class="sxs-lookup"><span data-stu-id="cae4f-107">Ordering operations:</span></span>  
  
- <  
  
- \<=  
  
- \>  
  
- \>=  
  
 <span data-ttu-id="cae4f-108">Operacje dopuszczania wartości null:</span><span class="sxs-lookup"><span data-stu-id="cae4f-108">Nullability operations:</span></span>  
  
- <span data-ttu-id="cae4f-109">MA WARTOŚĆ NULL</span><span class="sxs-lookup"><span data-stu-id="cae4f-109">IS NULL</span></span>  
  
- <span data-ttu-id="cae4f-110">NIE MA WARTOŚCI NULL</span><span class="sxs-lookup"><span data-stu-id="cae4f-110">IS NOT NULL</span></span>  
  
## <a name="explicit-distinction"></a><span data-ttu-id="cae4f-111">Jawne różnicy</span><span class="sxs-lookup"><span data-stu-id="cae4f-111">Explicit distinction</span></span>  
 <span data-ttu-id="cae4f-112">Rozróżnienie równości:</span><span class="sxs-lookup"><span data-stu-id="cae4f-112">Equality distinction:</span></span>  
  
- <span data-ttu-id="cae4f-113">DISTINCT</span><span class="sxs-lookup"><span data-stu-id="cae4f-113">DISTINCT</span></span>  
  
- <span data-ttu-id="cae4f-114">GROUP BY</span><span class="sxs-lookup"><span data-stu-id="cae4f-114">GROUP BY</span></span>  
  
 <span data-ttu-id="cae4f-115">Kolejność różnicy:</span><span class="sxs-lookup"><span data-stu-id="cae4f-115">Ordering distinction:</span></span>  
  
- <span data-ttu-id="cae4f-116">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="cae4f-116">ORDER BY</span></span>  
  
## <a name="implicit-distinction"></a><span data-ttu-id="cae4f-117">Niejawna różnicy</span><span class="sxs-lookup"><span data-stu-id="cae4f-117">Implicit distinction</span></span>  
 <span data-ttu-id="cae4f-118">Ustaw operacje i predykatów (równości):</span><span class="sxs-lookup"><span data-stu-id="cae4f-118">Set operations and predicates (equality):</span></span>  
  
- <span data-ttu-id="cae4f-119">UNION</span><span class="sxs-lookup"><span data-stu-id="cae4f-119">UNION</span></span>  
  
- <span data-ttu-id="cae4f-120">INTERSECT</span><span class="sxs-lookup"><span data-stu-id="cae4f-120">INTERSECT</span></span>  
  
- <span data-ttu-id="cae4f-121">EXCEPT</span><span class="sxs-lookup"><span data-stu-id="cae4f-121">EXCEPT</span></span>  
  
- <span data-ttu-id="cae4f-122">SET</span><span class="sxs-lookup"><span data-stu-id="cae4f-122">SET</span></span>  
  
- <span data-ttu-id="cae4f-123">OVERLAPS</span><span class="sxs-lookup"><span data-stu-id="cae4f-123">OVERLAPS</span></span>  
  
 <span data-ttu-id="cae4f-124">Element predykatów (równości):</span><span class="sxs-lookup"><span data-stu-id="cae4f-124">Item predicates (equality):</span></span>  
  
- <span data-ttu-id="cae4f-125">IN</span><span class="sxs-lookup"><span data-stu-id="cae4f-125">IN</span></span>  
  
## <a name="supported-combinations"></a><span data-ttu-id="cae4f-126">Obsługiwane kombinacje</span><span class="sxs-lookup"><span data-stu-id="cae4f-126">Supported Combinations</span></span>  
 <span data-ttu-id="cae4f-127">W poniższej tabeli przedstawiono obsługiwane kombinacje operatorów porównania dla każdego rodzaju typu:</span><span class="sxs-lookup"><span data-stu-id="cae4f-127">The following table shows all the supported combinations of comparison operators for each kind of type:</span></span>  
  
|<span data-ttu-id="cae4f-128">**Typ**</span><span class="sxs-lookup"><span data-stu-id="cae4f-128">**Type**</span></span>|**=**<br /><br /> <span data-ttu-id="cae4f-129">**\!=**</span><span class="sxs-lookup"><span data-stu-id="cae4f-129">**!=**</span></span>|<span data-ttu-id="cae4f-130">**GROUP BY**</span><span class="sxs-lookup"><span data-stu-id="cae4f-130">**GROUP BY**</span></span><br /><br /> <span data-ttu-id="cae4f-131">**DISTINCT**</span><span class="sxs-lookup"><span data-stu-id="cae4f-131">**DISTINCT**</span></span>|<span data-ttu-id="cae4f-132">**UNION**</span><span class="sxs-lookup"><span data-stu-id="cae4f-132">**UNION**</span></span><br /><br /> <span data-ttu-id="cae4f-133">**INTERSECT**</span><span class="sxs-lookup"><span data-stu-id="cae4f-133">**INTERSECT**</span></span><br /><br /> <span data-ttu-id="cae4f-134">**EXCEPT**</span><span class="sxs-lookup"><span data-stu-id="cae4f-134">**EXCEPT**</span></span><br /><br /> <span data-ttu-id="cae4f-135">**SET**</span><span class="sxs-lookup"><span data-stu-id="cae4f-135">**SET**</span></span><br /><br /> <span data-ttu-id="cae4f-136">**OVERLAPS**</span><span class="sxs-lookup"><span data-stu-id="cae4f-136">**OVERLAPS**</span></span>|<span data-ttu-id="cae4f-137">**IN**</span><span class="sxs-lookup"><span data-stu-id="cae4f-137">**IN**</span></span>|<span data-ttu-id="cae4f-138">**<   <=**</span><span class="sxs-lookup"><span data-stu-id="cae4f-138">**<   <=**</span></span><br /><br /> <span data-ttu-id="cae4f-139">**>   >=**</span><span class="sxs-lookup"><span data-stu-id="cae4f-139">**>   >=**</span></span>|<span data-ttu-id="cae4f-140">**ORDER BY**</span><span class="sxs-lookup"><span data-stu-id="cae4f-140">**ORDER BY**</span></span>|<span data-ttu-id="cae4f-141">**MA WARTOŚĆ NULL**</span><span class="sxs-lookup"><span data-stu-id="cae4f-141">**IS NULL**</span></span><br /><br /> <span data-ttu-id="cae4f-142">**NIE MA WARTOŚCI NULL**</span><span class="sxs-lookup"><span data-stu-id="cae4f-142">**IS NOT NULL**</span></span>|  
|-|-|-|-|-|-|-|-|  
|<span data-ttu-id="cae4f-143">Typ jednostki</span><span class="sxs-lookup"><span data-stu-id="cae4f-143">Entity type</span></span>|<span data-ttu-id="cae4f-144">REF<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="cae4f-144">Ref<sup>1</sup></span></span>|<span data-ttu-id="cae4f-145">Wszystkie właściwości<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="cae4f-145">All properties<sup>2</sup></span></span>|<span data-ttu-id="cae4f-146">Wszystkie właściwości<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="cae4f-146">All properties<sup>2</sup></span></span>|<span data-ttu-id="cae4f-147">Wszystkie właściwości<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="cae4f-147">All properties<sup>2</sup></span></span>|<span data-ttu-id="cae4f-148">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="cae4f-148">Throw<sup>3</sup></span></span>|<span data-ttu-id="cae4f-149">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="cae4f-149">Throw<sup>3</sup></span></span>|<span data-ttu-id="cae4f-150">REF<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="cae4f-150">Ref<sup>1</sup></span></span>|  
|<span data-ttu-id="cae4f-151">Typ złożony</span><span class="sxs-lookup"><span data-stu-id="cae4f-151">Complex type</span></span>|<span data-ttu-id="cae4f-152">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="cae4f-152">Throw<sup>3</sup></span></span>|<span data-ttu-id="cae4f-153">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="cae4f-153">Throw<sup>3</sup></span></span>|<span data-ttu-id="cae4f-154">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="cae4f-154">Throw<sup>3</sup></span></span>|<span data-ttu-id="cae4f-155">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="cae4f-155">Throw<sup>3</sup></span></span>|<span data-ttu-id="cae4f-156">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="cae4f-156">Throw<sup>3</sup></span></span>|<span data-ttu-id="cae4f-157">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="cae4f-157">Throw<sup>3</sup></span></span>|<span data-ttu-id="cae4f-158">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="cae4f-158">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="cae4f-159">Wiersz</span><span class="sxs-lookup"><span data-stu-id="cae4f-159">Row</span></span>|<span data-ttu-id="cae4f-160">Wszystkie właściwości<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="cae4f-160">All properties<sup>4</sup></span></span>|<span data-ttu-id="cae4f-161">Wszystkie właściwości<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="cae4f-161">All properties<sup>4</sup></span></span>|<span data-ttu-id="cae4f-162">Wszystkie właściwości<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="cae4f-162">All properties<sup>4</sup></span></span>|<span data-ttu-id="cae4f-163">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="cae4f-163">Throw<sup>3</sup></span></span>|<span data-ttu-id="cae4f-164">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="cae4f-164">Throw<sup>3</sup></span></span>|<span data-ttu-id="cae4f-165">Wszystkie właściwości<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="cae4f-165">All properties<sup>4</sup></span></span>|<span data-ttu-id="cae4f-166">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="cae4f-166">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="cae4f-167">typ pierwotny</span><span class="sxs-lookup"><span data-stu-id="cae4f-167">Primitive type</span></span>|<span data-ttu-id="cae4f-168">Właściwe dla dostawcy</span><span class="sxs-lookup"><span data-stu-id="cae4f-168">Provider-specific</span></span>|<span data-ttu-id="cae4f-169">Właściwe dla dostawcy</span><span class="sxs-lookup"><span data-stu-id="cae4f-169">Provider-specific</span></span>|<span data-ttu-id="cae4f-170">Właściwe dla dostawcy</span><span class="sxs-lookup"><span data-stu-id="cae4f-170">Provider-specific</span></span>|<span data-ttu-id="cae4f-171">Właściwe dla dostawcy</span><span class="sxs-lookup"><span data-stu-id="cae4f-171">Provider-specific</span></span>|<span data-ttu-id="cae4f-172">Właściwe dla dostawcy</span><span class="sxs-lookup"><span data-stu-id="cae4f-172">Provider-specific</span></span>|<span data-ttu-id="cae4f-173">Właściwe dla dostawcy</span><span class="sxs-lookup"><span data-stu-id="cae4f-173">Provider-specific</span></span>|<span data-ttu-id="cae4f-174">Właściwe dla dostawcy</span><span class="sxs-lookup"><span data-stu-id="cae4f-174">Provider-specific</span></span>|  
|<span data-ttu-id="cae4f-175">multiset</span><span class="sxs-lookup"><span data-stu-id="cae4f-175">Multiset</span></span>|<span data-ttu-id="cae4f-176">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="cae4f-176">Throw<sup>3</sup></span></span>|<span data-ttu-id="cae4f-177">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="cae4f-177">Throw<sup>3</sup></span></span>|<span data-ttu-id="cae4f-178">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="cae4f-178">Throw<sup>3</sup></span></span>|<span data-ttu-id="cae4f-179">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="cae4f-179">Throw<sup>3</sup></span></span>|<span data-ttu-id="cae4f-180">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="cae4f-180">Throw<sup>3</sup></span></span>|<span data-ttu-id="cae4f-181">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="cae4f-181">Throw<sup>3</sup></span></span>|<span data-ttu-id="cae4f-182">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="cae4f-182">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="cae4f-183">REF</span><span class="sxs-lookup"><span data-stu-id="cae4f-183">Ref</span></span>|<span data-ttu-id="cae4f-184">Tak<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="cae4f-184">Yes<sup>5</sup></span></span>|<span data-ttu-id="cae4f-185">Tak<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="cae4f-185">Yes<sup>5</sup></span></span>|<span data-ttu-id="cae4f-186">Tak<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="cae4f-186">Yes<sup>5</sup></span></span>|<span data-ttu-id="cae4f-187">Tak<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="cae4f-187">Yes<sup>5</sup></span></span>|<span data-ttu-id="cae4f-188">throw</span><span class="sxs-lookup"><span data-stu-id="cae4f-188">Throw</span></span>|<span data-ttu-id="cae4f-189">throw</span><span class="sxs-lookup"><span data-stu-id="cae4f-189">Throw</span></span>|<span data-ttu-id="cae4f-190">Tak<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="cae4f-190">Yes<sup>5</sup></span></span>|  
|<span data-ttu-id="cae4f-191">Skojarzenie</span><span class="sxs-lookup"><span data-stu-id="cae4f-191">Association</span></span><br /><br /> <span data-ttu-id="cae4f-192">— typ</span><span class="sxs-lookup"><span data-stu-id="cae4f-192">type</span></span>|<span data-ttu-id="cae4f-193">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="cae4f-193">Throw<sup>3</sup></span></span>|<span data-ttu-id="cae4f-194">throw</span><span class="sxs-lookup"><span data-stu-id="cae4f-194">Throw</span></span>|<span data-ttu-id="cae4f-195">throw</span><span class="sxs-lookup"><span data-stu-id="cae4f-195">Throw</span></span>|<span data-ttu-id="cae4f-196">throw</span><span class="sxs-lookup"><span data-stu-id="cae4f-196">Throw</span></span>|<span data-ttu-id="cae4f-197">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="cae4f-197">Throw<sup>3</sup></span></span>|<span data-ttu-id="cae4f-198">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="cae4f-198">Throw<sup>3</sup></span></span>|<span data-ttu-id="cae4f-199">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="cae4f-199">Throw<sup>3</sup></span></span>|  
  
 <span data-ttu-id="cae4f-200"><sup>1</sup>odwołania do danej jednostki wystąpień typu są porównywane niejawnie, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="cae4f-200"><sup>1</sup>The references of the given entity type instances are implicitly compared, as shown in the following example:</span></span>  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != p2 OR p1 IS NULL  
```  
  
 <span data-ttu-id="cae4f-201">Wystąpienie jednostki nie można porównać do jawnego odwołania.</span><span class="sxs-lookup"><span data-stu-id="cae4f-201">An entity instance cannot be compared to an explicit reference.</span></span> <span data-ttu-id="cae4f-202">Jeśli to jest podejmowana próba jest zgłaszany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="cae4f-202">If this is attempted, an exception is thrown.</span></span> <span data-ttu-id="cae4f-203">Na przykład następujące zapytanie spowoduje zgłoszenie wyjątku:</span><span class="sxs-lookup"><span data-stu-id="cae4f-203">For example, the following query will throw an exception:</span></span>  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != REF(p2)  
```  
  
 <span data-ttu-id="cae4f-204"><sup>2</sup>właściwości typy złożone są spłaszczone przed wysłaniem do magazynu, dzięki czemu staną się porównywalne (tak długo, jak ich właściwości są porównywalne).</span><span class="sxs-lookup"><span data-stu-id="cae4f-204"><sup>2</sup>Properties of complex types are flattened out before being sent to the store, so they become comparable (as long as all their properties are comparable).</span></span> <span data-ttu-id="cae4f-205">Zobacz też <sup>4.</sup></span><span class="sxs-lookup"><span data-stu-id="cae4f-205">Also see <sup>4.</sup></span></span>  
  
 <span data-ttu-id="cae4f-206"><sup>3</sup>środowisko uruchomieniowe programu Entity Framework wykrywa nieobsługiwane przypadku i istotnych wyjątek bez angażowania dostawcy/magazynowania.</span><span class="sxs-lookup"><span data-stu-id="cae4f-206"><sup>3</sup>The Entity Framework runtime detects the unsupported case and throws a meaningful exception without engaging the provider/store.</span></span>  
  
 <span data-ttu-id="cae4f-207"><sup>4</sup>zostanie podjęta próba, aby porównać wszystkie właściwości.</span><span class="sxs-lookup"><span data-stu-id="cae4f-207"><sup>4</sup>An attempt is made to compare all properties.</span></span> <span data-ttu-id="cae4f-208">Jeśli jest właściwością, która jest typu innego niż porównywalne, takich jak text, ntext lub image, może zostać wygenerowany wyjątek serwera.</span><span class="sxs-lookup"><span data-stu-id="cae4f-208">If there is a property that is of a non-comparable type, such as text, ntext, or image, a server exception might be thrown.</span></span>  
  
 <span data-ttu-id="cae4f-209"><sup>5</sup>wszystkie poszczególne elementy odniesienia są porównywane (obejmuje to nazwa zestawu jednostek i wszystkich właściwości klucza typu jednostki).</span><span class="sxs-lookup"><span data-stu-id="cae4f-209"><sup>5</sup>All individual elements of the references are compared (this includes the entity set name and all the key properties of the entity type).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cae4f-210">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cae4f-210">See also</span></span>

- [<span data-ttu-id="cae4f-211">Omówienie jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="cae4f-211">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
