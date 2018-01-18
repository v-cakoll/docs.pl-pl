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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: c6d22b72e05e6293a7fd3bcf7ddfba6e116e441f
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="comparison-semantics-entity-sql"></a><span data-ttu-id="5b229-102">Semantykę porównania (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="5b229-102">Comparison Semantics (Entity SQL)</span></span>
<span data-ttu-id="5b229-103">Wykonywanie następujących [!INCLUDE[esql](../../../../../../includes/esql-md.md)] porównania wystąpienia typu obejmuje operatory:</span><span class="sxs-lookup"><span data-stu-id="5b229-103">Performing any of the following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operators involves comparison of type instances:</span></span>  
  
## <a name="explicit-comparison"></a><span data-ttu-id="5b229-104">Jawne porównanie</span><span class="sxs-lookup"><span data-stu-id="5b229-104">Explicit comparison</span></span>  
 <span data-ttu-id="5b229-105">Operacje równości:</span><span class="sxs-lookup"><span data-stu-id="5b229-105">Equality operations:</span></span>  
  
-   =  
  
-   <span data-ttu-id="5b229-106">!=</span><span class="sxs-lookup"><span data-stu-id="5b229-106">!=</span></span>  
  
 <span data-ttu-id="5b229-107">Kolejność operacji:</span><span class="sxs-lookup"><span data-stu-id="5b229-107">Ordering operations:</span></span>  
  
-   <  
  
-   \<=  
  
-   >  
  
-   \>=  
  
 <span data-ttu-id="5b229-108">Operacje dopuszczania wartości null:</span><span class="sxs-lookup"><span data-stu-id="5b229-108">Nullability operations:</span></span>  
  
-   <span data-ttu-id="5b229-109">MA WARTOŚĆ NULL</span><span class="sxs-lookup"><span data-stu-id="5b229-109">IS NULL</span></span>  
  
-   <span data-ttu-id="5b229-110">NIE MA WARTOŚCI NULL</span><span class="sxs-lookup"><span data-stu-id="5b229-110">IS NOT NULL</span></span>  
  
## <a name="explicit-distinction"></a><span data-ttu-id="5b229-111">Jawne różnicy</span><span class="sxs-lookup"><span data-stu-id="5b229-111">Explicit distinction</span></span>  
 <span data-ttu-id="5b229-112">Równość różnicy:</span><span class="sxs-lookup"><span data-stu-id="5b229-112">Equality distinction:</span></span>  
  
-   <span data-ttu-id="5b229-113">RÓŻNE</span><span class="sxs-lookup"><span data-stu-id="5b229-113">DISTINCT</span></span>  
  
-   <span data-ttu-id="5b229-114">GRUPUJ WEDŁUG</span><span class="sxs-lookup"><span data-stu-id="5b229-114">GROUP BY</span></span>  
  
 <span data-ttu-id="5b229-115">Porządkowanie różnicy:</span><span class="sxs-lookup"><span data-stu-id="5b229-115">Ordering distinction:</span></span>  
  
-   <span data-ttu-id="5b229-116">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="5b229-116">ORDER BY</span></span>  
  
## <a name="implicit-distinction"></a><span data-ttu-id="5b229-117">Niejawne różnicy</span><span class="sxs-lookup"><span data-stu-id="5b229-117">Implicit distinction</span></span>  
 <span data-ttu-id="5b229-118">Ustaw operacje i predykatów (równości):</span><span class="sxs-lookup"><span data-stu-id="5b229-118">Set operations and predicates (equality):</span></span>  
  
-   <span data-ttu-id="5b229-119">UNION</span><span class="sxs-lookup"><span data-stu-id="5b229-119">UNION</span></span>  
  
-   <span data-ttu-id="5b229-120">INTERSECT</span><span class="sxs-lookup"><span data-stu-id="5b229-120">INTERSECT</span></span>  
  
-   <span data-ttu-id="5b229-121">EXCEPT</span><span class="sxs-lookup"><span data-stu-id="5b229-121">EXCEPT</span></span>  
  
-   <span data-ttu-id="5b229-122">SET</span><span class="sxs-lookup"><span data-stu-id="5b229-122">SET</span></span>  
  
-   <span data-ttu-id="5b229-123">POKRYWA SIĘ</span><span class="sxs-lookup"><span data-stu-id="5b229-123">OVERLAPS</span></span>  
  
 <span data-ttu-id="5b229-124">Predykaty elementu (równości):</span><span class="sxs-lookup"><span data-stu-id="5b229-124">Item predicates (equality):</span></span>  
  
-   <span data-ttu-id="5b229-125">W</span><span class="sxs-lookup"><span data-stu-id="5b229-125">IN</span></span>  
  
## <a name="supported-combinations"></a><span data-ttu-id="5b229-126">Obsługiwane kombinacje</span><span class="sxs-lookup"><span data-stu-id="5b229-126">Supported Combinations</span></span>  
 <span data-ttu-id="5b229-127">W poniższej tabeli przedstawiono obsługiwane kombinacje operatory porównania dla każdego rodzaju:</span><span class="sxs-lookup"><span data-stu-id="5b229-127">The following table shows all the supported combinations of comparison operators for each kind of type:</span></span>  
  
|<span data-ttu-id="5b229-128">**Typ**</span><span class="sxs-lookup"><span data-stu-id="5b229-128">**Type**</span></span>|**=**<br /><br /> <span data-ttu-id="5b229-129">**!=**</span><span class="sxs-lookup"><span data-stu-id="5b229-129">**!=**</span></span>|<span data-ttu-id="5b229-130">**GROUP BY**</span><span class="sxs-lookup"><span data-stu-id="5b229-130">**GROUP BY**</span></span><br /><br /> <span data-ttu-id="5b229-131">**RÓŻNE**</span><span class="sxs-lookup"><span data-stu-id="5b229-131">**DISTINCT**</span></span>|<span data-ttu-id="5b229-132">**UNION**</span><span class="sxs-lookup"><span data-stu-id="5b229-132">**UNION**</span></span><br /><br /> <span data-ttu-id="5b229-133">**INTERSECT**</span><span class="sxs-lookup"><span data-stu-id="5b229-133">**INTERSECT**</span></span><br /><br /> <span data-ttu-id="5b229-134">**EXCEPT**</span><span class="sxs-lookup"><span data-stu-id="5b229-134">**EXCEPT**</span></span><br /><br /> <span data-ttu-id="5b229-135">**SET**</span><span class="sxs-lookup"><span data-stu-id="5b229-135">**SET**</span></span><br /><br /> <span data-ttu-id="5b229-136">**OVERLAPS**</span><span class="sxs-lookup"><span data-stu-id="5b229-136">**OVERLAPS**</span></span>|<span data-ttu-id="5b229-137">**IN**</span><span class="sxs-lookup"><span data-stu-id="5b229-137">**IN**</span></span>|<span data-ttu-id="5b229-138">**<   <=**</span><span class="sxs-lookup"><span data-stu-id="5b229-138">**<   <=**</span></span><br /><br /> <span data-ttu-id="5b229-139">**>   >=**</span><span class="sxs-lookup"><span data-stu-id="5b229-139">**>   >=**</span></span>|<span data-ttu-id="5b229-140">**ORDER BY**</span><span class="sxs-lookup"><span data-stu-id="5b229-140">**ORDER BY**</span></span>|<span data-ttu-id="5b229-141">**MA WARTOŚĆ NULL**</span><span class="sxs-lookup"><span data-stu-id="5b229-141">**IS NULL**</span></span><br /><br /> <span data-ttu-id="5b229-142">**NIE MA WARTOŚCI NULL**</span><span class="sxs-lookup"><span data-stu-id="5b229-142">**IS NOT NULL**</span></span>|  
|-|-|-|-|-|-|-|-|  
|<span data-ttu-id="5b229-143">Typ jednostki</span><span class="sxs-lookup"><span data-stu-id="5b229-143">Entity type</span></span>|<span data-ttu-id="5b229-144">Ref<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="5b229-144">Ref<sup>1</sup></span></span>|<span data-ttu-id="5b229-145">Wszystkie właściwości<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="5b229-145">All properties<sup>2</sup></span></span>|<span data-ttu-id="5b229-146">Wszystkie właściwości<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="5b229-146">All properties<sup>2</sup></span></span>|<span data-ttu-id="5b229-147">Wszystkie właściwości<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="5b229-147">All properties<sup>2</sup></span></span>|<span data-ttu-id="5b229-148">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="5b229-148">Throw<sup>3</sup></span></span>|<span data-ttu-id="5b229-149">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="5b229-149">Throw<sup>3</sup></span></span>|<span data-ttu-id="5b229-150">Ref<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="5b229-150">Ref<sup>1</sup></span></span>|  
|<span data-ttu-id="5b229-151">Typ złożony</span><span class="sxs-lookup"><span data-stu-id="5b229-151">Complex type</span></span>|<span data-ttu-id="5b229-152">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="5b229-152">Throw<sup>3</sup></span></span>|<span data-ttu-id="5b229-153">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="5b229-153">Throw<sup>3</sup></span></span>|<span data-ttu-id="5b229-154">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="5b229-154">Throw<sup>3</sup></span></span>|<span data-ttu-id="5b229-155">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="5b229-155">Throw<sup>3</sup></span></span>|<span data-ttu-id="5b229-156">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="5b229-156">Throw<sup>3</sup></span></span>|<span data-ttu-id="5b229-157">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="5b229-157">Throw<sup>3</sup></span></span>|<span data-ttu-id="5b229-158">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="5b229-158">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="5b229-159">Wiersz</span><span class="sxs-lookup"><span data-stu-id="5b229-159">Row</span></span>|<span data-ttu-id="5b229-160">Wszystkie właściwości<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="5b229-160">All properties<sup>4</sup></span></span>|<span data-ttu-id="5b229-161">Wszystkie właściwości<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="5b229-161">All properties<sup>4</sup></span></span>|<span data-ttu-id="5b229-162">Wszystkie właściwości<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="5b229-162">All properties<sup>4</sup></span></span>|<span data-ttu-id="5b229-163">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="5b229-163">Throw<sup>3</sup></span></span>|<span data-ttu-id="5b229-164">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="5b229-164">Throw<sup>3</sup></span></span>|<span data-ttu-id="5b229-165">Wszystkie właściwości<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="5b229-165">All properties<sup>4</sup></span></span>|<span data-ttu-id="5b229-166">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="5b229-166">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="5b229-167">Typ pierwotny</span><span class="sxs-lookup"><span data-stu-id="5b229-167">Primitive type</span></span>|<span data-ttu-id="5b229-168">Provider-specific</span><span class="sxs-lookup"><span data-stu-id="5b229-168">Provider-specific</span></span>|<span data-ttu-id="5b229-169">Provider-specific</span><span class="sxs-lookup"><span data-stu-id="5b229-169">Provider-specific</span></span>|<span data-ttu-id="5b229-170">Provider-specific</span><span class="sxs-lookup"><span data-stu-id="5b229-170">Provider-specific</span></span>|<span data-ttu-id="5b229-171">Provider-specific</span><span class="sxs-lookup"><span data-stu-id="5b229-171">Provider-specific</span></span>|<span data-ttu-id="5b229-172">Provider-specific</span><span class="sxs-lookup"><span data-stu-id="5b229-172">Provider-specific</span></span>|<span data-ttu-id="5b229-173">Provider-specific</span><span class="sxs-lookup"><span data-stu-id="5b229-173">Provider-specific</span></span>|<span data-ttu-id="5b229-174">Provider-specific</span><span class="sxs-lookup"><span data-stu-id="5b229-174">Provider-specific</span></span>|  
|<span data-ttu-id="5b229-175">Zestaw wielokrotny</span><span class="sxs-lookup"><span data-stu-id="5b229-175">Multiset</span></span>|<span data-ttu-id="5b229-176">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="5b229-176">Throw<sup>3</sup></span></span>|<span data-ttu-id="5b229-177">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="5b229-177">Throw<sup>3</sup></span></span>|<span data-ttu-id="5b229-178">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="5b229-178">Throw<sup>3</sup></span></span>|<span data-ttu-id="5b229-179">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="5b229-179">Throw<sup>3</sup></span></span>|<span data-ttu-id="5b229-180">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="5b229-180">Throw<sup>3</sup></span></span>|<span data-ttu-id="5b229-181">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="5b229-181">Throw<sup>3</sup></span></span>|<span data-ttu-id="5b229-182">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="5b229-182">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="5b229-183">REF</span><span class="sxs-lookup"><span data-stu-id="5b229-183">Ref</span></span>|<span data-ttu-id="5b229-184">Tak<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="5b229-184">Yes<sup>5</sup></span></span>|<span data-ttu-id="5b229-185">Tak<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="5b229-185">Yes<sup>5</sup></span></span>|<span data-ttu-id="5b229-186">Tak<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="5b229-186">Yes<sup>5</sup></span></span>|<span data-ttu-id="5b229-187">Tak<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="5b229-187">Yes<sup>5</sup></span></span>|<span data-ttu-id="5b229-188">Throw</span><span class="sxs-lookup"><span data-stu-id="5b229-188">Throw</span></span>|<span data-ttu-id="5b229-189">Throw</span><span class="sxs-lookup"><span data-stu-id="5b229-189">Throw</span></span>|<span data-ttu-id="5b229-190">Tak<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="5b229-190">Yes<sup>5</sup></span></span>|  
|<span data-ttu-id="5b229-191">Skojarzenie</span><span class="sxs-lookup"><span data-stu-id="5b229-191">Association</span></span><br /><br /> <span data-ttu-id="5b229-192">— typ</span><span class="sxs-lookup"><span data-stu-id="5b229-192">type</span></span>|<span data-ttu-id="5b229-193">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="5b229-193">Throw<sup>3</sup></span></span>|<span data-ttu-id="5b229-194">Throw</span><span class="sxs-lookup"><span data-stu-id="5b229-194">Throw</span></span>|<span data-ttu-id="5b229-195">Throw</span><span class="sxs-lookup"><span data-stu-id="5b229-195">Throw</span></span>|<span data-ttu-id="5b229-196">Throw</span><span class="sxs-lookup"><span data-stu-id="5b229-196">Throw</span></span>|<span data-ttu-id="5b229-197">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="5b229-197">Throw<sup>3</sup></span></span>|<span data-ttu-id="5b229-198">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="5b229-198">Throw<sup>3</sup></span></span>|<span data-ttu-id="5b229-199">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="5b229-199">Throw<sup>3</sup></span></span>|  
  
 <span data-ttu-id="5b229-200"><sup>1</sup>odwołania do danej jednostki wystąpień typu są porównywane niejawnie, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="5b229-200"><sup>1</sup>The references of the given entity type instances are implicitly compared, as shown in the following example:</span></span>  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != p2 OR p1 IS NULL  
```  
  
 <span data-ttu-id="5b229-201">Wystąpienie jednostki nie można porównać do jawnego odwołania.</span><span class="sxs-lookup"><span data-stu-id="5b229-201">An entity instance cannot be compared to an explicit reference.</span></span> <span data-ttu-id="5b229-202">Jeśli ta próba zostanie podjęta, jest zwracany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="5b229-202">If this is attempted, an exception is thrown.</span></span> <span data-ttu-id="5b229-203">Na przykład poniższe zapytanie spowoduje zgłoszenie wyjątku:</span><span class="sxs-lookup"><span data-stu-id="5b229-203">For example, the following query will throw an exception:</span></span>  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != REF(p2)  
```  
  
 <span data-ttu-id="5b229-204"><sup>2</sup>właściwości złożonych typów są spłaszczane przed wysłaniem do magazynu, więc stają się one porównywalne (o ile ich właściwości mogą być porównywane).</span><span class="sxs-lookup"><span data-stu-id="5b229-204"><sup>2</sup>Properties of complex types are flattened out before being sent to the store, so they become comparable (as long as all their properties are comparable).</span></span> <span data-ttu-id="5b229-205">Zobacz też <sup>4.</sup></span><span class="sxs-lookup"><span data-stu-id="5b229-205">Also see <sup>4.</sup></span></span>  
  
 <span data-ttu-id="5b229-206"><sup>3</sup>środowiska uruchomieniowego programu Entity Framework wykrywa nieobsługiwane przypadku i zgłasza wyjątek znaczące bez zaangażowania dostawcy/magazynu.</span><span class="sxs-lookup"><span data-stu-id="5b229-206"><sup>3</sup>The Entity Framework runtime detects the unsupported case and throws a meaningful exception without engaging the provider/store.</span></span>  
  
 <span data-ttu-id="5b229-207"><sup>4</sup>próby porównania wszystkich właściwości.</span><span class="sxs-lookup"><span data-stu-id="5b229-207"><sup>4</sup>An attempt is made to compare all properties.</span></span> <span data-ttu-id="5b229-208">Jeśli istnieje we właściwości nie można porównywać pod względem typu, takie jak text, ntext lub image, może być zgłoszony wyjątek serwera.</span><span class="sxs-lookup"><span data-stu-id="5b229-208">If there is a property that is of a non-comparable type, such as text, ntext, or image, a server exception might be thrown.</span></span>  
  
 <span data-ttu-id="5b229-209"><sup>5</sup>wszystkie poszczególne elementy odwołań są porównywane (dotyczy to również nazwa zestawu jednostek i wszystkich właściwości klucza typu jednostek).</span><span class="sxs-lookup"><span data-stu-id="5b229-209"><sup>5</sup>All individual elements of the references are compared (this includes the entity set name and all the key properties of the entity type).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b229-210">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5b229-210">See Also</span></span>  
 [<span data-ttu-id="5b229-211">Omówienie jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="5b229-211">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
