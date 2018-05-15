---
title: Semantykę porównania (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: b36ce28a-2fe4-4236-b782-e5f7c054deae
ms.openlocfilehash: 2184f86ee43f88b0c4cfc1b96e42e2486c17fe5f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="comparison-semantics-entity-sql"></a><span data-ttu-id="33e12-102">Semantykę porównania (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="33e12-102">Comparison Semantics (Entity SQL)</span></span>
<span data-ttu-id="33e12-103">Wykonywanie następujących [!INCLUDE[esql](../../../../../../includes/esql-md.md)] porównania wystąpienia typu obejmuje operatory:</span><span class="sxs-lookup"><span data-stu-id="33e12-103">Performing any of the following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operators involves comparison of type instances:</span></span>  
  
## <a name="explicit-comparison"></a><span data-ttu-id="33e12-104">Jawne porównanie</span><span class="sxs-lookup"><span data-stu-id="33e12-104">Explicit comparison</span></span>  
 <span data-ttu-id="33e12-105">Operacje równości:</span><span class="sxs-lookup"><span data-stu-id="33e12-105">Equality operations:</span></span>  
  
-   =  
  
-   <span data-ttu-id="33e12-106">!=</span><span class="sxs-lookup"><span data-stu-id="33e12-106">!=</span></span>  
  
 <span data-ttu-id="33e12-107">Kolejność operacji:</span><span class="sxs-lookup"><span data-stu-id="33e12-107">Ordering operations:</span></span>  
  
-   <  
  
-   \<=  
  
-   \>  
  
-   \>=  
  
 <span data-ttu-id="33e12-108">Operacje dopuszczania wartości null:</span><span class="sxs-lookup"><span data-stu-id="33e12-108">Nullability operations:</span></span>  
  
-   <span data-ttu-id="33e12-109">MA WARTOŚĆ NULL</span><span class="sxs-lookup"><span data-stu-id="33e12-109">IS NULL</span></span>  
  
-   <span data-ttu-id="33e12-110">NIE MA WARTOŚCI NULL</span><span class="sxs-lookup"><span data-stu-id="33e12-110">IS NOT NULL</span></span>  
  
## <a name="explicit-distinction"></a><span data-ttu-id="33e12-111">Jawne różnicy</span><span class="sxs-lookup"><span data-stu-id="33e12-111">Explicit distinction</span></span>  
 <span data-ttu-id="33e12-112">Równość różnicy:</span><span class="sxs-lookup"><span data-stu-id="33e12-112">Equality distinction:</span></span>  
  
-   <span data-ttu-id="33e12-113">RÓŻNE</span><span class="sxs-lookup"><span data-stu-id="33e12-113">DISTINCT</span></span>  
  
-   <span data-ttu-id="33e12-114">GRUPUJ WEDŁUG</span><span class="sxs-lookup"><span data-stu-id="33e12-114">GROUP BY</span></span>  
  
 <span data-ttu-id="33e12-115">Porządkowanie różnicy:</span><span class="sxs-lookup"><span data-stu-id="33e12-115">Ordering distinction:</span></span>  
  
-   <span data-ttu-id="33e12-116">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="33e12-116">ORDER BY</span></span>  
  
## <a name="implicit-distinction"></a><span data-ttu-id="33e12-117">Niejawne różnicy</span><span class="sxs-lookup"><span data-stu-id="33e12-117">Implicit distinction</span></span>  
 <span data-ttu-id="33e12-118">Ustaw operacje i predykatów (równości):</span><span class="sxs-lookup"><span data-stu-id="33e12-118">Set operations and predicates (equality):</span></span>  
  
-   <span data-ttu-id="33e12-119">UNION</span><span class="sxs-lookup"><span data-stu-id="33e12-119">UNION</span></span>  
  
-   <span data-ttu-id="33e12-120">INTERSECT</span><span class="sxs-lookup"><span data-stu-id="33e12-120">INTERSECT</span></span>  
  
-   <span data-ttu-id="33e12-121">EXCEPT</span><span class="sxs-lookup"><span data-stu-id="33e12-121">EXCEPT</span></span>  
  
-   <span data-ttu-id="33e12-122">SET</span><span class="sxs-lookup"><span data-stu-id="33e12-122">SET</span></span>  
  
-   <span data-ttu-id="33e12-123">POKRYWA SIĘ</span><span class="sxs-lookup"><span data-stu-id="33e12-123">OVERLAPS</span></span>  
  
 <span data-ttu-id="33e12-124">Predykaty elementu (równości):</span><span class="sxs-lookup"><span data-stu-id="33e12-124">Item predicates (equality):</span></span>  
  
-   <span data-ttu-id="33e12-125">W</span><span class="sxs-lookup"><span data-stu-id="33e12-125">IN</span></span>  
  
## <a name="supported-combinations"></a><span data-ttu-id="33e12-126">Obsługiwane kombinacje</span><span class="sxs-lookup"><span data-stu-id="33e12-126">Supported Combinations</span></span>  
 <span data-ttu-id="33e12-127">W poniższej tabeli przedstawiono obsługiwane kombinacje operatory porównania dla każdego rodzaju:</span><span class="sxs-lookup"><span data-stu-id="33e12-127">The following table shows all the supported combinations of comparison operators for each kind of type:</span></span>  
  
|<span data-ttu-id="33e12-128">**Typ**</span><span class="sxs-lookup"><span data-stu-id="33e12-128">**Type**</span></span>|**=**<br /><br /> <span data-ttu-id="33e12-129">**!=**</span><span class="sxs-lookup"><span data-stu-id="33e12-129">**!=**</span></span>|<span data-ttu-id="33e12-130">**GROUP BY**</span><span class="sxs-lookup"><span data-stu-id="33e12-130">**GROUP BY**</span></span><br /><br /> <span data-ttu-id="33e12-131">**RÓŻNE**</span><span class="sxs-lookup"><span data-stu-id="33e12-131">**DISTINCT**</span></span>|<span data-ttu-id="33e12-132">**UNION**</span><span class="sxs-lookup"><span data-stu-id="33e12-132">**UNION**</span></span><br /><br /> <span data-ttu-id="33e12-133">**INTERSECT**</span><span class="sxs-lookup"><span data-stu-id="33e12-133">**INTERSECT**</span></span><br /><br /> <span data-ttu-id="33e12-134">**EXCEPT**</span><span class="sxs-lookup"><span data-stu-id="33e12-134">**EXCEPT**</span></span><br /><br /> <span data-ttu-id="33e12-135">**SET**</span><span class="sxs-lookup"><span data-stu-id="33e12-135">**SET**</span></span><br /><br /> <span data-ttu-id="33e12-136">**OVERLAPS**</span><span class="sxs-lookup"><span data-stu-id="33e12-136">**OVERLAPS**</span></span>|<span data-ttu-id="33e12-137">**IN**</span><span class="sxs-lookup"><span data-stu-id="33e12-137">**IN**</span></span>|<span data-ttu-id="33e12-138">**<   <=**</span><span class="sxs-lookup"><span data-stu-id="33e12-138">**<   <=**</span></span><br /><br /> <span data-ttu-id="33e12-139">**>   >=**</span><span class="sxs-lookup"><span data-stu-id="33e12-139">**>   >=**</span></span>|<span data-ttu-id="33e12-140">**ORDER BY**</span><span class="sxs-lookup"><span data-stu-id="33e12-140">**ORDER BY**</span></span>|<span data-ttu-id="33e12-141">**MA WARTOŚĆ NULL**</span><span class="sxs-lookup"><span data-stu-id="33e12-141">**IS NULL**</span></span><br /><br /> <span data-ttu-id="33e12-142">**NIE MA WARTOŚCI NULL**</span><span class="sxs-lookup"><span data-stu-id="33e12-142">**IS NOT NULL**</span></span>|  
|-|-|-|-|-|-|-|-|  
|<span data-ttu-id="33e12-143">Typ jednostki</span><span class="sxs-lookup"><span data-stu-id="33e12-143">Entity type</span></span>|<span data-ttu-id="33e12-144">REF<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="33e12-144">Ref<sup>1</sup></span></span>|<span data-ttu-id="33e12-145">Wszystkie właściwości<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="33e12-145">All properties<sup>2</sup></span></span>|<span data-ttu-id="33e12-146">Wszystkie właściwości<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="33e12-146">All properties<sup>2</sup></span></span>|<span data-ttu-id="33e12-147">Wszystkie właściwości<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="33e12-147">All properties<sup>2</sup></span></span>|<span data-ttu-id="33e12-148">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="33e12-148">Throw<sup>3</sup></span></span>|<span data-ttu-id="33e12-149">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="33e12-149">Throw<sup>3</sup></span></span>|<span data-ttu-id="33e12-150">REF<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="33e12-150">Ref<sup>1</sup></span></span>|  
|<span data-ttu-id="33e12-151">Typ złożony</span><span class="sxs-lookup"><span data-stu-id="33e12-151">Complex type</span></span>|<span data-ttu-id="33e12-152">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="33e12-152">Throw<sup>3</sup></span></span>|<span data-ttu-id="33e12-153">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="33e12-153">Throw<sup>3</sup></span></span>|<span data-ttu-id="33e12-154">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="33e12-154">Throw<sup>3</sup></span></span>|<span data-ttu-id="33e12-155">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="33e12-155">Throw<sup>3</sup></span></span>|<span data-ttu-id="33e12-156">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="33e12-156">Throw<sup>3</sup></span></span>|<span data-ttu-id="33e12-157">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="33e12-157">Throw<sup>3</sup></span></span>|<span data-ttu-id="33e12-158">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="33e12-158">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="33e12-159">Wiersz</span><span class="sxs-lookup"><span data-stu-id="33e12-159">Row</span></span>|<span data-ttu-id="33e12-160">Wszystkie właściwości<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="33e12-160">All properties<sup>4</sup></span></span>|<span data-ttu-id="33e12-161">Wszystkie właściwości<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="33e12-161">All properties<sup>4</sup></span></span>|<span data-ttu-id="33e12-162">Wszystkie właściwości<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="33e12-162">All properties<sup>4</sup></span></span>|<span data-ttu-id="33e12-163">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="33e12-163">Throw<sup>3</sup></span></span>|<span data-ttu-id="33e12-164">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="33e12-164">Throw<sup>3</sup></span></span>|<span data-ttu-id="33e12-165">Wszystkie właściwości<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="33e12-165">All properties<sup>4</sup></span></span>|<span data-ttu-id="33e12-166">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="33e12-166">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="33e12-167">Typ pierwotny</span><span class="sxs-lookup"><span data-stu-id="33e12-167">Primitive type</span></span>|<span data-ttu-id="33e12-168">Specyficznych dla dostawcy</span><span class="sxs-lookup"><span data-stu-id="33e12-168">Provider-specific</span></span>|<span data-ttu-id="33e12-169">Specyficznych dla dostawcy</span><span class="sxs-lookup"><span data-stu-id="33e12-169">Provider-specific</span></span>|<span data-ttu-id="33e12-170">Specyficznych dla dostawcy</span><span class="sxs-lookup"><span data-stu-id="33e12-170">Provider-specific</span></span>|<span data-ttu-id="33e12-171">Specyficznych dla dostawcy</span><span class="sxs-lookup"><span data-stu-id="33e12-171">Provider-specific</span></span>|<span data-ttu-id="33e12-172">Specyficznych dla dostawcy</span><span class="sxs-lookup"><span data-stu-id="33e12-172">Provider-specific</span></span>|<span data-ttu-id="33e12-173">Specyficznych dla dostawcy</span><span class="sxs-lookup"><span data-stu-id="33e12-173">Provider-specific</span></span>|<span data-ttu-id="33e12-174">Specyficznych dla dostawcy</span><span class="sxs-lookup"><span data-stu-id="33e12-174">Provider-specific</span></span>|  
|<span data-ttu-id="33e12-175">Zestaw wielokrotny</span><span class="sxs-lookup"><span data-stu-id="33e12-175">Multiset</span></span>|<span data-ttu-id="33e12-176">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="33e12-176">Throw<sup>3</sup></span></span>|<span data-ttu-id="33e12-177">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="33e12-177">Throw<sup>3</sup></span></span>|<span data-ttu-id="33e12-178">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="33e12-178">Throw<sup>3</sup></span></span>|<span data-ttu-id="33e12-179">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="33e12-179">Throw<sup>3</sup></span></span>|<span data-ttu-id="33e12-180">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="33e12-180">Throw<sup>3</sup></span></span>|<span data-ttu-id="33e12-181">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="33e12-181">Throw<sup>3</sup></span></span>|<span data-ttu-id="33e12-182">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="33e12-182">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="33e12-183">REF</span><span class="sxs-lookup"><span data-stu-id="33e12-183">Ref</span></span>|<span data-ttu-id="33e12-184">Tak<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="33e12-184">Yes<sup>5</sup></span></span>|<span data-ttu-id="33e12-185">Tak<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="33e12-185">Yes<sup>5</sup></span></span>|<span data-ttu-id="33e12-186">Tak<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="33e12-186">Yes<sup>5</sup></span></span>|<span data-ttu-id="33e12-187">Tak<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="33e12-187">Yes<sup>5</sup></span></span>|<span data-ttu-id="33e12-188">Throw</span><span class="sxs-lookup"><span data-stu-id="33e12-188">Throw</span></span>|<span data-ttu-id="33e12-189">Throw</span><span class="sxs-lookup"><span data-stu-id="33e12-189">Throw</span></span>|<span data-ttu-id="33e12-190">Tak<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="33e12-190">Yes<sup>5</sup></span></span>|  
|<span data-ttu-id="33e12-191">Skojarzenie</span><span class="sxs-lookup"><span data-stu-id="33e12-191">Association</span></span><br /><br /> <span data-ttu-id="33e12-192">— typ</span><span class="sxs-lookup"><span data-stu-id="33e12-192">type</span></span>|<span data-ttu-id="33e12-193">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="33e12-193">Throw<sup>3</sup></span></span>|<span data-ttu-id="33e12-194">Throw</span><span class="sxs-lookup"><span data-stu-id="33e12-194">Throw</span></span>|<span data-ttu-id="33e12-195">Throw</span><span class="sxs-lookup"><span data-stu-id="33e12-195">Throw</span></span>|<span data-ttu-id="33e12-196">Throw</span><span class="sxs-lookup"><span data-stu-id="33e12-196">Throw</span></span>|<span data-ttu-id="33e12-197">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="33e12-197">Throw<sup>3</sup></span></span>|<span data-ttu-id="33e12-198">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="33e12-198">Throw<sup>3</sup></span></span>|<span data-ttu-id="33e12-199">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="33e12-199">Throw<sup>3</sup></span></span>|  
  
 <span data-ttu-id="33e12-200"><sup>1</sup>odwołania do danej jednostki wystąpień typu są porównywane niejawnie, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="33e12-200"><sup>1</sup>The references of the given entity type instances are implicitly compared, as shown in the following example:</span></span>  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != p2 OR p1 IS NULL  
```  
  
 <span data-ttu-id="33e12-201">Wystąpienie jednostki nie można porównać do jawnego odwołania.</span><span class="sxs-lookup"><span data-stu-id="33e12-201">An entity instance cannot be compared to an explicit reference.</span></span> <span data-ttu-id="33e12-202">Jeśli ta próba zostanie podjęta, jest zwracany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="33e12-202">If this is attempted, an exception is thrown.</span></span> <span data-ttu-id="33e12-203">Na przykład poniższe zapytanie spowoduje zgłoszenie wyjątku:</span><span class="sxs-lookup"><span data-stu-id="33e12-203">For example, the following query will throw an exception:</span></span>  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != REF(p2)  
```  
  
 <span data-ttu-id="33e12-204"><sup>2</sup>właściwości złożonych typów są spłaszczane przed wysłaniem do magazynu, więc stają się one porównywalne (o ile ich właściwości mogą być porównywane).</span><span class="sxs-lookup"><span data-stu-id="33e12-204"><sup>2</sup>Properties of complex types are flattened out before being sent to the store, so they become comparable (as long as all their properties are comparable).</span></span> <span data-ttu-id="33e12-205">Zobacz też <sup>4.</sup></span><span class="sxs-lookup"><span data-stu-id="33e12-205">Also see <sup>4.</sup></span></span>  
  
 <span data-ttu-id="33e12-206"><sup>3</sup>środowiska uruchomieniowego programu Entity Framework wykrywa nieobsługiwane przypadku i zgłasza wyjątek znaczące bez zaangażowania dostawcy/magazynu.</span><span class="sxs-lookup"><span data-stu-id="33e12-206"><sup>3</sup>The Entity Framework runtime detects the unsupported case and throws a meaningful exception without engaging the provider/store.</span></span>  
  
 <span data-ttu-id="33e12-207"><sup>4</sup>próby porównania wszystkich właściwości.</span><span class="sxs-lookup"><span data-stu-id="33e12-207"><sup>4</sup>An attempt is made to compare all properties.</span></span> <span data-ttu-id="33e12-208">Jeśli istnieje we właściwości nie można porównywać pod względem typu, takie jak text, ntext lub image, może być zgłoszony wyjątek serwera.</span><span class="sxs-lookup"><span data-stu-id="33e12-208">If there is a property that is of a non-comparable type, such as text, ntext, or image, a server exception might be thrown.</span></span>  
  
 <span data-ttu-id="33e12-209"><sup>5</sup>wszystkie poszczególne elementy odwołań są porównywane (dotyczy to również nazwa zestawu jednostek i wszystkich właściwości klucza typu jednostek).</span><span class="sxs-lookup"><span data-stu-id="33e12-209"><sup>5</sup>All individual elements of the references are compared (this includes the entity set name and all the key properties of the entity type).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33e12-210">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="33e12-210">See Also</span></span>  
 [<span data-ttu-id="33e12-211">Omówienie jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="33e12-211">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
