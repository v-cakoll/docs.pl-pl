---
title: "Semantykę porównania (jednostka SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b36ce28a-2fe4-4236-b782-e5f7c054deae
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 2835d2064f1845b55dd3a33abb086c5af0fb9e6c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="comparison-semantics-entity-sql"></a><span data-ttu-id="e75fc-102">Semantykę porównania (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="e75fc-102">Comparison Semantics (Entity SQL)</span></span>
<span data-ttu-id="e75fc-103">Wykonywanie następujących [!INCLUDE[esql](../../../../../../includes/esql-md.md)] porównania wystąpienia typu obejmuje operatory:</span><span class="sxs-lookup"><span data-stu-id="e75fc-103">Performing any of the following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operators involves comparison of type instances:</span></span>  
  
## <a name="explicit-comparison"></a><span data-ttu-id="e75fc-104">Jawne porównanie</span><span class="sxs-lookup"><span data-stu-id="e75fc-104">Explicit comparison</span></span>  
 <span data-ttu-id="e75fc-105">Operacje równości:</span><span class="sxs-lookup"><span data-stu-id="e75fc-105">Equality operations:</span></span>  
  
-   =  
  
-   <span data-ttu-id="e75fc-106">!=</span><span class="sxs-lookup"><span data-stu-id="e75fc-106">!=</span></span>  
  
 <span data-ttu-id="e75fc-107">Kolejność operacji:</span><span class="sxs-lookup"><span data-stu-id="e75fc-107">Ordering operations:</span></span>  
  
-   <  
  
-   \<=  
  
-   >  
  
-   \>=  
  
 <span data-ttu-id="e75fc-108">Operacje dopuszczania wartości null:</span><span class="sxs-lookup"><span data-stu-id="e75fc-108">Nullability operations:</span></span>  
  
-   <span data-ttu-id="e75fc-109">MA WARTOŚĆ NULL</span><span class="sxs-lookup"><span data-stu-id="e75fc-109">IS NULL</span></span>  
  
-   <span data-ttu-id="e75fc-110">NIE MA WARTOŚCI NULL</span><span class="sxs-lookup"><span data-stu-id="e75fc-110">IS NOT NULL</span></span>  
  
## <a name="explicit-distinction"></a><span data-ttu-id="e75fc-111">Jawne różnicy</span><span class="sxs-lookup"><span data-stu-id="e75fc-111">Explicit distinction</span></span>  
 <span data-ttu-id="e75fc-112">Równość różnicy:</span><span class="sxs-lookup"><span data-stu-id="e75fc-112">Equality distinction:</span></span>  
  
-   <span data-ttu-id="e75fc-113">RÓŻNE</span><span class="sxs-lookup"><span data-stu-id="e75fc-113">DISTINCT</span></span>  
  
-   <span data-ttu-id="e75fc-114">GRUPUJ WEDŁUG</span><span class="sxs-lookup"><span data-stu-id="e75fc-114">GROUP BY</span></span>  
  
 <span data-ttu-id="e75fc-115">Porządkowanie różnicy:</span><span class="sxs-lookup"><span data-stu-id="e75fc-115">Ordering distinction:</span></span>  
  
-   <span data-ttu-id="e75fc-116">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="e75fc-116">ORDER BY</span></span>  
  
## <a name="implicit-distinction"></a><span data-ttu-id="e75fc-117">Niejawne różnicy</span><span class="sxs-lookup"><span data-stu-id="e75fc-117">Implicit distinction</span></span>  
 <span data-ttu-id="e75fc-118">Ustaw operacje i predykatów (równości):</span><span class="sxs-lookup"><span data-stu-id="e75fc-118">Set operations and predicates (equality):</span></span>  
  
-   <span data-ttu-id="e75fc-119">UNION</span><span class="sxs-lookup"><span data-stu-id="e75fc-119">UNION</span></span>  
  
-   <span data-ttu-id="e75fc-120">INTERSECT</span><span class="sxs-lookup"><span data-stu-id="e75fc-120">INTERSECT</span></span>  
  
-   <span data-ttu-id="e75fc-121">Z WYJĄTKIEM</span><span class="sxs-lookup"><span data-stu-id="e75fc-121">EXCEPT</span></span>  
  
-   <span data-ttu-id="e75fc-122">ZESTAW</span><span class="sxs-lookup"><span data-stu-id="e75fc-122">SET</span></span>  
  
-   <span data-ttu-id="e75fc-123">POKRYWA SIĘ</span><span class="sxs-lookup"><span data-stu-id="e75fc-123">OVERLAPS</span></span>  
  
 <span data-ttu-id="e75fc-124">Predykaty elementu (równości):</span><span class="sxs-lookup"><span data-stu-id="e75fc-124">Item predicates (equality):</span></span>  
  
-   <span data-ttu-id="e75fc-125">W</span><span class="sxs-lookup"><span data-stu-id="e75fc-125">IN</span></span>  
  
## <a name="supported-combinations"></a><span data-ttu-id="e75fc-126">Obsługiwane kombinacje</span><span class="sxs-lookup"><span data-stu-id="e75fc-126">Supported Combinations</span></span>  
 <span data-ttu-id="e75fc-127">W poniższej tabeli przedstawiono obsługiwane kombinacje operatory porównania dla każdego rodzaju:</span><span class="sxs-lookup"><span data-stu-id="e75fc-127">The following table shows all the supported combinations of comparison operators for each kind of type:</span></span>  
  
|<span data-ttu-id="e75fc-128">**Typ**</span><span class="sxs-lookup"><span data-stu-id="e75fc-128">**Type**</span></span>|**=**<br /><br /> <span data-ttu-id="e75fc-129">**!=**</span><span class="sxs-lookup"><span data-stu-id="e75fc-129">**!=**</span></span>|<span data-ttu-id="e75fc-130">**GROUP BY**</span><span class="sxs-lookup"><span data-stu-id="e75fc-130">**GROUP BY**</span></span><br /><br /> <span data-ttu-id="e75fc-131">**RÓŻNE**</span><span class="sxs-lookup"><span data-stu-id="e75fc-131">**DISTINCT**</span></span>|<span data-ttu-id="e75fc-132">**UNION**</span><span class="sxs-lookup"><span data-stu-id="e75fc-132">**UNION**</span></span><br /><br /> <span data-ttu-id="e75fc-133">**INTERSECT**</span><span class="sxs-lookup"><span data-stu-id="e75fc-133">**INTERSECT**</span></span><br /><br /> <span data-ttu-id="e75fc-134">**EXCEPT**</span><span class="sxs-lookup"><span data-stu-id="e75fc-134">**EXCEPT**</span></span><br /><br /> <span data-ttu-id="e75fc-135">**SET**</span><span class="sxs-lookup"><span data-stu-id="e75fc-135">**SET**</span></span><br /><br /> <span data-ttu-id="e75fc-136">**OVERLAPS**</span><span class="sxs-lookup"><span data-stu-id="e75fc-136">**OVERLAPS**</span></span>|<span data-ttu-id="e75fc-137">**IN**</span><span class="sxs-lookup"><span data-stu-id="e75fc-137">**IN**</span></span>|<span data-ttu-id="e75fc-138">**<   <=**</span><span class="sxs-lookup"><span data-stu-id="e75fc-138">**<   <=**</span></span><br /><br /> <span data-ttu-id="e75fc-139">**>   >=**</span><span class="sxs-lookup"><span data-stu-id="e75fc-139">**>   >=**</span></span>|<span data-ttu-id="e75fc-140">**ORDER BY**</span><span class="sxs-lookup"><span data-stu-id="e75fc-140">**ORDER BY**</span></span>|<span data-ttu-id="e75fc-141">**MA WARTOŚĆ NULL**</span><span class="sxs-lookup"><span data-stu-id="e75fc-141">**IS NULL**</span></span><br /><br /> <span data-ttu-id="e75fc-142">**NIE MA WARTOŚCI NULL**</span><span class="sxs-lookup"><span data-stu-id="e75fc-142">**IS NOT NULL**</span></span>|  
|-|-|-|-|-|-|-|-|  
|<span data-ttu-id="e75fc-143">Typ jednostki</span><span class="sxs-lookup"><span data-stu-id="e75fc-143">Entity type</span></span>|<span data-ttu-id="e75fc-144">REF<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="e75fc-144">Ref<sup>1</sup></span></span>|<span data-ttu-id="e75fc-145">Wszystkie właściwości<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="e75fc-145">All properties<sup>2</sup></span></span>|<span data-ttu-id="e75fc-146">Wszystkie właściwości<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="e75fc-146">All properties<sup>2</sup></span></span>|<span data-ttu-id="e75fc-147">Wszystkie właściwości<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="e75fc-147">All properties<sup>2</sup></span></span>|<span data-ttu-id="e75fc-148">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="e75fc-148">Throw<sup>3</sup></span></span>|<span data-ttu-id="e75fc-149">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="e75fc-149">Throw<sup>3</sup></span></span>|<span data-ttu-id="e75fc-150">REF<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="e75fc-150">Ref<sup>1</sup></span></span>|  
|<span data-ttu-id="e75fc-151">Typ złożony</span><span class="sxs-lookup"><span data-stu-id="e75fc-151">Complex type</span></span>|<span data-ttu-id="e75fc-152">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="e75fc-152">Throw<sup>3</sup></span></span>|<span data-ttu-id="e75fc-153">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="e75fc-153">Throw<sup>3</sup></span></span>|<span data-ttu-id="e75fc-154">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="e75fc-154">Throw<sup>3</sup></span></span>|<span data-ttu-id="e75fc-155">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="e75fc-155">Throw<sup>3</sup></span></span>|<span data-ttu-id="e75fc-156">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="e75fc-156">Throw<sup>3</sup></span></span>|<span data-ttu-id="e75fc-157">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="e75fc-157">Throw<sup>3</sup></span></span>|<span data-ttu-id="e75fc-158">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="e75fc-158">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="e75fc-159">Wiersz</span><span class="sxs-lookup"><span data-stu-id="e75fc-159">Row</span></span>|<span data-ttu-id="e75fc-160">Wszystkie właściwości<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="e75fc-160">All properties<sup>4</sup></span></span>|<span data-ttu-id="e75fc-161">Wszystkie właściwości<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="e75fc-161">All properties<sup>4</sup></span></span>|<span data-ttu-id="e75fc-162">Wszystkie właściwości<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="e75fc-162">All properties<sup>4</sup></span></span>|<span data-ttu-id="e75fc-163">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="e75fc-163">Throw<sup>3</sup></span></span>|<span data-ttu-id="e75fc-164">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="e75fc-164">Throw<sup>3</sup></span></span>|<span data-ttu-id="e75fc-165">Wszystkie właściwości<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="e75fc-165">All properties<sup>4</sup></span></span>|<span data-ttu-id="e75fc-166">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="e75fc-166">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="e75fc-167">Typ pierwotny</span><span class="sxs-lookup"><span data-stu-id="e75fc-167">Primitive type</span></span>|<span data-ttu-id="e75fc-168">Specyficznych dla dostawcy</span><span class="sxs-lookup"><span data-stu-id="e75fc-168">Provider-specific</span></span>|<span data-ttu-id="e75fc-169">Specyficznych dla dostawcy</span><span class="sxs-lookup"><span data-stu-id="e75fc-169">Provider-specific</span></span>|<span data-ttu-id="e75fc-170">Specyficznych dla dostawcy</span><span class="sxs-lookup"><span data-stu-id="e75fc-170">Provider-specific</span></span>|<span data-ttu-id="e75fc-171">Specyficznych dla dostawcy</span><span class="sxs-lookup"><span data-stu-id="e75fc-171">Provider-specific</span></span>|<span data-ttu-id="e75fc-172">Specyficznych dla dostawcy</span><span class="sxs-lookup"><span data-stu-id="e75fc-172">Provider-specific</span></span>|<span data-ttu-id="e75fc-173">Specyficznych dla dostawcy</span><span class="sxs-lookup"><span data-stu-id="e75fc-173">Provider-specific</span></span>|<span data-ttu-id="e75fc-174">Specyficznych dla dostawcy</span><span class="sxs-lookup"><span data-stu-id="e75fc-174">Provider-specific</span></span>|  
|<span data-ttu-id="e75fc-175">Zestaw wielokrotny</span><span class="sxs-lookup"><span data-stu-id="e75fc-175">Multiset</span></span>|<span data-ttu-id="e75fc-176">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="e75fc-176">Throw<sup>3</sup></span></span>|<span data-ttu-id="e75fc-177">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="e75fc-177">Throw<sup>3</sup></span></span>|<span data-ttu-id="e75fc-178">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="e75fc-178">Throw<sup>3</sup></span></span>|<span data-ttu-id="e75fc-179">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="e75fc-179">Throw<sup>3</sup></span></span>|<span data-ttu-id="e75fc-180">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="e75fc-180">Throw<sup>3</sup></span></span>|<span data-ttu-id="e75fc-181">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="e75fc-181">Throw<sup>3</sup></span></span>|<span data-ttu-id="e75fc-182">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="e75fc-182">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="e75fc-183">REF</span><span class="sxs-lookup"><span data-stu-id="e75fc-183">Ref</span></span>|<span data-ttu-id="e75fc-184">Tak<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="e75fc-184">Yes<sup>5</sup></span></span>|<span data-ttu-id="e75fc-185">Tak<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="e75fc-185">Yes<sup>5</sup></span></span>|<span data-ttu-id="e75fc-186">Tak<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="e75fc-186">Yes<sup>5</sup></span></span>|<span data-ttu-id="e75fc-187">Tak<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="e75fc-187">Yes<sup>5</sup></span></span>|<span data-ttu-id="e75fc-188">Throw</span><span class="sxs-lookup"><span data-stu-id="e75fc-188">Throw</span></span>|<span data-ttu-id="e75fc-189">Throw</span><span class="sxs-lookup"><span data-stu-id="e75fc-189">Throw</span></span>|<span data-ttu-id="e75fc-190">Tak<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="e75fc-190">Yes<sup>5</sup></span></span>|  
|<span data-ttu-id="e75fc-191">Skojarzenie</span><span class="sxs-lookup"><span data-stu-id="e75fc-191">Association</span></span><br /><br /> <span data-ttu-id="e75fc-192">— typ</span><span class="sxs-lookup"><span data-stu-id="e75fc-192">type</span></span>|<span data-ttu-id="e75fc-193">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="e75fc-193">Throw<sup>3</sup></span></span>|<span data-ttu-id="e75fc-194">Throw</span><span class="sxs-lookup"><span data-stu-id="e75fc-194">Throw</span></span>|<span data-ttu-id="e75fc-195">Throw</span><span class="sxs-lookup"><span data-stu-id="e75fc-195">Throw</span></span>|<span data-ttu-id="e75fc-196">Throw</span><span class="sxs-lookup"><span data-stu-id="e75fc-196">Throw</span></span>|<span data-ttu-id="e75fc-197">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="e75fc-197">Throw<sup>3</sup></span></span>|<span data-ttu-id="e75fc-198">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="e75fc-198">Throw<sup>3</sup></span></span>|<span data-ttu-id="e75fc-199">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="e75fc-199">Throw<sup>3</sup></span></span>|  
  
 <span data-ttu-id="e75fc-200"><sup>1</sup>odwołania do danej jednostki wystąpień typu są porównywane niejawnie, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="e75fc-200"><sup>1</sup>The references of the given entity type instances are implicitly compared, as shown in the following example:</span></span>  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != p2 OR p1 IS NULL  
```  
  
 <span data-ttu-id="e75fc-201">Wystąpienie jednostki nie można porównać do jawnego odwołania.</span><span class="sxs-lookup"><span data-stu-id="e75fc-201">An entity instance cannot be compared to an explicit reference.</span></span> <span data-ttu-id="e75fc-202">Jeśli ta próba zostanie podjęta, jest zwracany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="e75fc-202">If this is attempted, an exception is thrown.</span></span> <span data-ttu-id="e75fc-203">Na przykład poniższe zapytanie spowoduje zgłoszenie wyjątku:</span><span class="sxs-lookup"><span data-stu-id="e75fc-203">For example, the following query will throw an exception:</span></span>  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != REF(p2)  
```  
  
 <span data-ttu-id="e75fc-204"><sup>2</sup>właściwości złożonych typów są spłaszczane przed wysłaniem do magazynu, więc stają się one porównywalne (o ile ich właściwości mogą być porównywane).</span><span class="sxs-lookup"><span data-stu-id="e75fc-204"><sup>2</sup>Properties of complex types are flattened out before being sent to the store, so they become comparable (as long as all their properties are comparable).</span></span> <span data-ttu-id="e75fc-205">Zobacz też <sup>4.</sup></span><span class="sxs-lookup"><span data-stu-id="e75fc-205">Also see <sup>4.</sup></span></span>  
  
 <span data-ttu-id="e75fc-206"><sup>3</sup>środowiska uruchomieniowego programu Entity Framework wykrywa nieobsługiwane przypadku i zgłasza wyjątek znaczące bez zaangażowania dostawcy/magazynu.</span><span class="sxs-lookup"><span data-stu-id="e75fc-206"><sup>3</sup>The Entity Framework runtime detects the unsupported case and throws a meaningful exception without engaging the provider/store.</span></span>  
  
 <span data-ttu-id="e75fc-207"><sup>4</sup>próby porównania wszystkich właściwości.</span><span class="sxs-lookup"><span data-stu-id="e75fc-207"><sup>4</sup>An attempt is made to compare all properties.</span></span> <span data-ttu-id="e75fc-208">Jeśli istnieje we właściwości nie można porównywać pod względem typu, takie jak text, ntext lub image, może być zgłoszony wyjątek serwera.</span><span class="sxs-lookup"><span data-stu-id="e75fc-208">If there is a property that is of a non-comparable type, such as text, ntext, or image, a server exception might be thrown.</span></span>  
  
 <span data-ttu-id="e75fc-209"><sup>5</sup>wszystkie poszczególne elementy odwołań są porównywane (dotyczy to również nazwa zestawu jednostek i wszystkich właściwości klucza typu jednostek).</span><span class="sxs-lookup"><span data-stu-id="e75fc-209"><sup>5</sup>All individual elements of the references are compared (this includes the entity set name and all the key properties of the entity type).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e75fc-210">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e75fc-210">See Also</span></span>  
 [<span data-ttu-id="e75fc-211">Omówienie jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="e75fc-211">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
