---
title: Semantyka porównania (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: b36ce28a-2fe4-4236-b782-e5f7c054deae
ms.openlocfilehash: 371999df0fb3177ecc90f9b1fa43d457a51bfd7a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54492497"
---
# <a name="comparison-semantics-entity-sql"></a><span data-ttu-id="2080b-102">Semantyka porównania (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="2080b-102">Comparison Semantics (Entity SQL)</span></span>
<span data-ttu-id="2080b-103">Wykonanie dowolnego z następujących [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatory obejmuje porównanie wystąpień typu:</span><span class="sxs-lookup"><span data-stu-id="2080b-103">Performing any of the following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operators involves comparison of type instances:</span></span>  
  
## <a name="explicit-comparison"></a><span data-ttu-id="2080b-104">Porównanie jawne</span><span class="sxs-lookup"><span data-stu-id="2080b-104">Explicit comparison</span></span>  
 <span data-ttu-id="2080b-105">Operacje równości:</span><span class="sxs-lookup"><span data-stu-id="2080b-105">Equality operations:</span></span>  
  
-   =  
  
-   <span data-ttu-id="2080b-106">!=</span><span class="sxs-lookup"><span data-stu-id="2080b-106">!=</span></span>  
  
 <span data-ttu-id="2080b-107">Kolejność operacji:</span><span class="sxs-lookup"><span data-stu-id="2080b-107">Ordering operations:</span></span>  
  
-   <  
  
-   \<=  
  
-   \>  
  
-   \>=  
  
 <span data-ttu-id="2080b-108">Operacje dopuszczania wartości null:</span><span class="sxs-lookup"><span data-stu-id="2080b-108">Nullability operations:</span></span>  
  
-   <span data-ttu-id="2080b-109">MA WARTOŚĆ NULL</span><span class="sxs-lookup"><span data-stu-id="2080b-109">IS NULL</span></span>  
  
-   <span data-ttu-id="2080b-110">NIE MA WARTOŚCI NULL</span><span class="sxs-lookup"><span data-stu-id="2080b-110">IS NOT NULL</span></span>  
  
## <a name="explicit-distinction"></a><span data-ttu-id="2080b-111">Jawne różnicy</span><span class="sxs-lookup"><span data-stu-id="2080b-111">Explicit distinction</span></span>  
 <span data-ttu-id="2080b-112">Rozróżnienie równości:</span><span class="sxs-lookup"><span data-stu-id="2080b-112">Equality distinction:</span></span>  
  
-   <span data-ttu-id="2080b-113">DISTINCT</span><span class="sxs-lookup"><span data-stu-id="2080b-113">DISTINCT</span></span>  
  
-   <span data-ttu-id="2080b-114">GRUPUJ WEDŁUG</span><span class="sxs-lookup"><span data-stu-id="2080b-114">GROUP BY</span></span>  
  
 <span data-ttu-id="2080b-115">Kolejność różnicy:</span><span class="sxs-lookup"><span data-stu-id="2080b-115">Ordering distinction:</span></span>  
  
-   <span data-ttu-id="2080b-116">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="2080b-116">ORDER BY</span></span>  
  
## <a name="implicit-distinction"></a><span data-ttu-id="2080b-117">Niejawna różnicy</span><span class="sxs-lookup"><span data-stu-id="2080b-117">Implicit distinction</span></span>  
 <span data-ttu-id="2080b-118">Ustaw operacje i predykatów (równości):</span><span class="sxs-lookup"><span data-stu-id="2080b-118">Set operations and predicates (equality):</span></span>  
  
-   <span data-ttu-id="2080b-119">UNION</span><span class="sxs-lookup"><span data-stu-id="2080b-119">UNION</span></span>  
  
-   <span data-ttu-id="2080b-120">INTERSECT</span><span class="sxs-lookup"><span data-stu-id="2080b-120">INTERSECT</span></span>  
  
-   <span data-ttu-id="2080b-121">EXCEPT</span><span class="sxs-lookup"><span data-stu-id="2080b-121">EXCEPT</span></span>  
  
-   <span data-ttu-id="2080b-122">SET</span><span class="sxs-lookup"><span data-stu-id="2080b-122">SET</span></span>  
  
-   <span data-ttu-id="2080b-123">NAKŁADA SIĘ NA</span><span class="sxs-lookup"><span data-stu-id="2080b-123">OVERLAPS</span></span>  
  
 <span data-ttu-id="2080b-124">Element predykatów (równości):</span><span class="sxs-lookup"><span data-stu-id="2080b-124">Item predicates (equality):</span></span>  
  
-   <span data-ttu-id="2080b-125">INDIE</span><span class="sxs-lookup"><span data-stu-id="2080b-125">IN</span></span>  
  
## <a name="supported-combinations"></a><span data-ttu-id="2080b-126">Obsługiwane kombinacje</span><span class="sxs-lookup"><span data-stu-id="2080b-126">Supported Combinations</span></span>  
 <span data-ttu-id="2080b-127">W poniższej tabeli przedstawiono obsługiwane kombinacje operatorów porównania dla każdego rodzaju typu:</span><span class="sxs-lookup"><span data-stu-id="2080b-127">The following table shows all the supported combinations of comparison operators for each kind of type:</span></span>  
  
|<span data-ttu-id="2080b-128">**Typ**</span><span class="sxs-lookup"><span data-stu-id="2080b-128">**Type**</span></span>|**=**<br /><br /> <span data-ttu-id="2080b-129">**\!=**</span><span class="sxs-lookup"><span data-stu-id="2080b-129">**!=**</span></span>|<span data-ttu-id="2080b-130">**GROUP BY**</span><span class="sxs-lookup"><span data-stu-id="2080b-130">**GROUP BY**</span></span><br /><br /> <span data-ttu-id="2080b-131">**DISTINCT**</span><span class="sxs-lookup"><span data-stu-id="2080b-131">**DISTINCT**</span></span>|<span data-ttu-id="2080b-132">**UNION**</span><span class="sxs-lookup"><span data-stu-id="2080b-132">**UNION**</span></span><br /><br /> <span data-ttu-id="2080b-133">**INTERSECT**</span><span class="sxs-lookup"><span data-stu-id="2080b-133">**INTERSECT**</span></span><br /><br /> <span data-ttu-id="2080b-134">**EXCEPT**</span><span class="sxs-lookup"><span data-stu-id="2080b-134">**EXCEPT**</span></span><br /><br /> <span data-ttu-id="2080b-135">**SET**</span><span class="sxs-lookup"><span data-stu-id="2080b-135">**SET**</span></span><br /><br /> <span data-ttu-id="2080b-136">**OVERLAPS**</span><span class="sxs-lookup"><span data-stu-id="2080b-136">**OVERLAPS**</span></span>|<span data-ttu-id="2080b-137">**IN**</span><span class="sxs-lookup"><span data-stu-id="2080b-137">**IN**</span></span>|<span data-ttu-id="2080b-138">**<   <=**</span><span class="sxs-lookup"><span data-stu-id="2080b-138">**<   <=**</span></span><br /><br /> <span data-ttu-id="2080b-139">**>   >=**</span><span class="sxs-lookup"><span data-stu-id="2080b-139">**>   >=**</span></span>|<span data-ttu-id="2080b-140">**ORDER BY**</span><span class="sxs-lookup"><span data-stu-id="2080b-140">**ORDER BY**</span></span>|<span data-ttu-id="2080b-141">**MA WARTOŚĆ NULL**</span><span class="sxs-lookup"><span data-stu-id="2080b-141">**IS NULL**</span></span><br /><br /> <span data-ttu-id="2080b-142">**NIE MA WARTOŚCI NULL**</span><span class="sxs-lookup"><span data-stu-id="2080b-142">**IS NOT NULL**</span></span>|  
|-|-|-|-|-|-|-|-|  
|<span data-ttu-id="2080b-143">Typ jednostki</span><span class="sxs-lookup"><span data-stu-id="2080b-143">Entity type</span></span>|<span data-ttu-id="2080b-144">REF<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="2080b-144">Ref<sup>1</sup></span></span>|<span data-ttu-id="2080b-145">Wszystkie właściwości<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="2080b-145">All properties<sup>2</sup></span></span>|<span data-ttu-id="2080b-146">Wszystkie właściwości<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="2080b-146">All properties<sup>2</sup></span></span>|<span data-ttu-id="2080b-147">Wszystkie właściwości<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="2080b-147">All properties<sup>2</sup></span></span>|<span data-ttu-id="2080b-148">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2080b-148">Throw<sup>3</sup></span></span>|<span data-ttu-id="2080b-149">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2080b-149">Throw<sup>3</sup></span></span>|<span data-ttu-id="2080b-150">REF<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="2080b-150">Ref<sup>1</sup></span></span>|  
|<span data-ttu-id="2080b-151">Typ złożony</span><span class="sxs-lookup"><span data-stu-id="2080b-151">Complex type</span></span>|<span data-ttu-id="2080b-152">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2080b-152">Throw<sup>3</sup></span></span>|<span data-ttu-id="2080b-153">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2080b-153">Throw<sup>3</sup></span></span>|<span data-ttu-id="2080b-154">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2080b-154">Throw<sup>3</sup></span></span>|<span data-ttu-id="2080b-155">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2080b-155">Throw<sup>3</sup></span></span>|<span data-ttu-id="2080b-156">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2080b-156">Throw<sup>3</sup></span></span>|<span data-ttu-id="2080b-157">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2080b-157">Throw<sup>3</sup></span></span>|<span data-ttu-id="2080b-158">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2080b-158">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="2080b-159">Wiersz</span><span class="sxs-lookup"><span data-stu-id="2080b-159">Row</span></span>|<span data-ttu-id="2080b-160">Wszystkie właściwości<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="2080b-160">All properties<sup>4</sup></span></span>|<span data-ttu-id="2080b-161">Wszystkie właściwości<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="2080b-161">All properties<sup>4</sup></span></span>|<span data-ttu-id="2080b-162">Wszystkie właściwości<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="2080b-162">All properties<sup>4</sup></span></span>|<span data-ttu-id="2080b-163">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2080b-163">Throw<sup>3</sup></span></span>|<span data-ttu-id="2080b-164">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2080b-164">Throw<sup>3</sup></span></span>|<span data-ttu-id="2080b-165">Wszystkie właściwości<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="2080b-165">All properties<sup>4</sup></span></span>|<span data-ttu-id="2080b-166">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2080b-166">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="2080b-167">typ pierwotny</span><span class="sxs-lookup"><span data-stu-id="2080b-167">Primitive type</span></span>|<span data-ttu-id="2080b-168">Właściwe dla dostawcy</span><span class="sxs-lookup"><span data-stu-id="2080b-168">Provider-specific</span></span>|<span data-ttu-id="2080b-169">Właściwe dla dostawcy</span><span class="sxs-lookup"><span data-stu-id="2080b-169">Provider-specific</span></span>|<span data-ttu-id="2080b-170">Właściwe dla dostawcy</span><span class="sxs-lookup"><span data-stu-id="2080b-170">Provider-specific</span></span>|<span data-ttu-id="2080b-171">Właściwe dla dostawcy</span><span class="sxs-lookup"><span data-stu-id="2080b-171">Provider-specific</span></span>|<span data-ttu-id="2080b-172">Właściwe dla dostawcy</span><span class="sxs-lookup"><span data-stu-id="2080b-172">Provider-specific</span></span>|<span data-ttu-id="2080b-173">Właściwe dla dostawcy</span><span class="sxs-lookup"><span data-stu-id="2080b-173">Provider-specific</span></span>|<span data-ttu-id="2080b-174">Właściwe dla dostawcy</span><span class="sxs-lookup"><span data-stu-id="2080b-174">Provider-specific</span></span>|  
|<span data-ttu-id="2080b-175">multiset</span><span class="sxs-lookup"><span data-stu-id="2080b-175">Multiset</span></span>|<span data-ttu-id="2080b-176">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2080b-176">Throw<sup>3</sup></span></span>|<span data-ttu-id="2080b-177">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2080b-177">Throw<sup>3</sup></span></span>|<span data-ttu-id="2080b-178">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2080b-178">Throw<sup>3</sup></span></span>|<span data-ttu-id="2080b-179">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2080b-179">Throw<sup>3</sup></span></span>|<span data-ttu-id="2080b-180">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2080b-180">Throw<sup>3</sup></span></span>|<span data-ttu-id="2080b-181">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2080b-181">Throw<sup>3</sup></span></span>|<span data-ttu-id="2080b-182">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2080b-182">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="2080b-183">REF</span><span class="sxs-lookup"><span data-stu-id="2080b-183">Ref</span></span>|<span data-ttu-id="2080b-184">Tak<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="2080b-184">Yes<sup>5</sup></span></span>|<span data-ttu-id="2080b-185">Tak<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="2080b-185">Yes<sup>5</sup></span></span>|<span data-ttu-id="2080b-186">Tak<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="2080b-186">Yes<sup>5</sup></span></span>|<span data-ttu-id="2080b-187">Tak<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="2080b-187">Yes<sup>5</sup></span></span>|<span data-ttu-id="2080b-188">throw</span><span class="sxs-lookup"><span data-stu-id="2080b-188">Throw</span></span>|<span data-ttu-id="2080b-189">throw</span><span class="sxs-lookup"><span data-stu-id="2080b-189">Throw</span></span>|<span data-ttu-id="2080b-190">Tak<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="2080b-190">Yes<sup>5</sup></span></span>|  
|<span data-ttu-id="2080b-191">Skojarzenie</span><span class="sxs-lookup"><span data-stu-id="2080b-191">Association</span></span><br /><br /> <span data-ttu-id="2080b-192">— typ</span><span class="sxs-lookup"><span data-stu-id="2080b-192">type</span></span>|<span data-ttu-id="2080b-193">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2080b-193">Throw<sup>3</sup></span></span>|<span data-ttu-id="2080b-194">throw</span><span class="sxs-lookup"><span data-stu-id="2080b-194">Throw</span></span>|<span data-ttu-id="2080b-195">throw</span><span class="sxs-lookup"><span data-stu-id="2080b-195">Throw</span></span>|<span data-ttu-id="2080b-196">throw</span><span class="sxs-lookup"><span data-stu-id="2080b-196">Throw</span></span>|<span data-ttu-id="2080b-197">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2080b-197">Throw<sup>3</sup></span></span>|<span data-ttu-id="2080b-198">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2080b-198">Throw<sup>3</sup></span></span>|<span data-ttu-id="2080b-199">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2080b-199">Throw<sup>3</sup></span></span>|  
  
 <span data-ttu-id="2080b-200"><sup>1</sup>odwołania do danej jednostki wystąpień typu są porównywane niejawnie, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="2080b-200"><sup>1</sup>The references of the given entity type instances are implicitly compared, as shown in the following example:</span></span>  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != p2 OR p1 IS NULL  
```  
  
 <span data-ttu-id="2080b-201">Wystąpienie jednostki nie można porównać do jawnego odwołania.</span><span class="sxs-lookup"><span data-stu-id="2080b-201">An entity instance cannot be compared to an explicit reference.</span></span> <span data-ttu-id="2080b-202">Jeśli to jest podejmowana próba jest zgłaszany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="2080b-202">If this is attempted, an exception is thrown.</span></span> <span data-ttu-id="2080b-203">Na przykład następujące zapytanie spowoduje zgłoszenie wyjątku:</span><span class="sxs-lookup"><span data-stu-id="2080b-203">For example, the following query will throw an exception:</span></span>  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != REF(p2)  
```  
  
 <span data-ttu-id="2080b-204"><sup>2</sup>właściwości typy złożone są spłaszczone przed wysłaniem do magazynu, dzięki czemu staną się porównywalne (tak długo, jak ich właściwości są porównywalne).</span><span class="sxs-lookup"><span data-stu-id="2080b-204"><sup>2</sup>Properties of complex types are flattened out before being sent to the store, so they become comparable (as long as all their properties are comparable).</span></span> <span data-ttu-id="2080b-205">Zobacz też <sup>4.</sup></span><span class="sxs-lookup"><span data-stu-id="2080b-205">Also see <sup>4.</sup></span></span>  
  
 <span data-ttu-id="2080b-206"><sup>3</sup>środowisko uruchomieniowe programu Entity Framework wykrywa nieobsługiwane przypadku i istotnych wyjątek bez angażowania dostawcy/magazynowania.</span><span class="sxs-lookup"><span data-stu-id="2080b-206"><sup>3</sup>The Entity Framework runtime detects the unsupported case and throws a meaningful exception without engaging the provider/store.</span></span>  
  
 <span data-ttu-id="2080b-207"><sup>4</sup>zostanie podjęta próba, aby porównać wszystkie właściwości.</span><span class="sxs-lookup"><span data-stu-id="2080b-207"><sup>4</sup>An attempt is made to compare all properties.</span></span> <span data-ttu-id="2080b-208">Jeśli jest właściwością, która jest typu innego niż porównywalne, takich jak text, ntext lub image, może zostać wygenerowany wyjątek serwera.</span><span class="sxs-lookup"><span data-stu-id="2080b-208">If there is a property that is of a non-comparable type, such as text, ntext, or image, a server exception might be thrown.</span></span>  
  
 <span data-ttu-id="2080b-209"><sup>5</sup>wszystkie poszczególne elementy odniesienia są porównywane (obejmuje to nazwa zestawu jednostek i wszystkich właściwości klucza typu jednostki).</span><span class="sxs-lookup"><span data-stu-id="2080b-209"><sup>5</sup>All individual elements of the references are compared (this includes the entity set name and all the key properties of the entity type).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2080b-210">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2080b-210">See also</span></span>
- [<span data-ttu-id="2080b-211">Omówienie jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="2080b-211">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
