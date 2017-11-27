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
ms.openlocfilehash: f1fd1c21fc4f156bfe7a5abf9f76bd341e2d0f10
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="comparison-semantics-entity-sql"></a><span data-ttu-id="13502-102">Semantykę porównania (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="13502-102">Comparison Semantics (Entity SQL)</span></span>
<span data-ttu-id="13502-103">Wykonywanie następujących [!INCLUDE[esql](../../../../../../includes/esql-md.md)] porównania wystąpienia typu obejmuje operatory:</span><span class="sxs-lookup"><span data-stu-id="13502-103">Performing any of the following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operators involves comparison of type instances:</span></span>  
  
## <a name="explicit-comparison"></a><span data-ttu-id="13502-104">Jawne porównanie</span><span class="sxs-lookup"><span data-stu-id="13502-104">Explicit comparison</span></span>  
 <span data-ttu-id="13502-105">Operacje równości:</span><span class="sxs-lookup"><span data-stu-id="13502-105">Equality operations:</span></span>  
  
-   =  
  
-   <span data-ttu-id="13502-106">!=</span><span class="sxs-lookup"><span data-stu-id="13502-106">!=</span></span>  
  
 <span data-ttu-id="13502-107">Kolejność operacji:</span><span class="sxs-lookup"><span data-stu-id="13502-107">Ordering operations:</span></span>  
  
-   <  
  
-   \<=  
  
-   >  
  
-   \>=  
  
 <span data-ttu-id="13502-108">Operacje dopuszczania wartości null:</span><span class="sxs-lookup"><span data-stu-id="13502-108">Nullability operations:</span></span>  
  
-   <span data-ttu-id="13502-109">MA WARTOŚĆ NULL</span><span class="sxs-lookup"><span data-stu-id="13502-109">IS NULL</span></span>  
  
-   <span data-ttu-id="13502-110">NIE MA WARTOŚCI NULL</span><span class="sxs-lookup"><span data-stu-id="13502-110">IS NOT NULL</span></span>  
  
## <a name="explicit-distinction"></a><span data-ttu-id="13502-111">Jawne różnicy</span><span class="sxs-lookup"><span data-stu-id="13502-111">Explicit distinction</span></span>  
 <span data-ttu-id="13502-112">Równość różnicy:</span><span class="sxs-lookup"><span data-stu-id="13502-112">Equality distinction:</span></span>  
  
-   <span data-ttu-id="13502-113">RÓŻNE</span><span class="sxs-lookup"><span data-stu-id="13502-113">DISTINCT</span></span>  
  
-   <span data-ttu-id="13502-114">GRUPUJ WEDŁUG</span><span class="sxs-lookup"><span data-stu-id="13502-114">GROUP BY</span></span>  
  
 <span data-ttu-id="13502-115">Porządkowanie różnicy:</span><span class="sxs-lookup"><span data-stu-id="13502-115">Ordering distinction:</span></span>  
  
-   <span data-ttu-id="13502-116">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="13502-116">ORDER BY</span></span>  
  
## <a name="implicit-distinction"></a><span data-ttu-id="13502-117">Niejawne różnicy</span><span class="sxs-lookup"><span data-stu-id="13502-117">Implicit distinction</span></span>  
 <span data-ttu-id="13502-118">Ustaw operacje i predykatów (równości):</span><span class="sxs-lookup"><span data-stu-id="13502-118">Set operations and predicates (equality):</span></span>  
  
-   <span data-ttu-id="13502-119">UNION</span><span class="sxs-lookup"><span data-stu-id="13502-119">UNION</span></span>  
  
-   <span data-ttu-id="13502-120">INTERSECT</span><span class="sxs-lookup"><span data-stu-id="13502-120">INTERSECT</span></span>  
  
-   <span data-ttu-id="13502-121">Z WYJĄTKIEM</span><span class="sxs-lookup"><span data-stu-id="13502-121">EXCEPT</span></span>  
  
-   <span data-ttu-id="13502-122">ZESTAW</span><span class="sxs-lookup"><span data-stu-id="13502-122">SET</span></span>  
  
-   <span data-ttu-id="13502-123">POKRYWA SIĘ</span><span class="sxs-lookup"><span data-stu-id="13502-123">OVERLAPS</span></span>  
  
 <span data-ttu-id="13502-124">Predykaty elementu (równości):</span><span class="sxs-lookup"><span data-stu-id="13502-124">Item predicates (equality):</span></span>  
  
-   <span data-ttu-id="13502-125">W</span><span class="sxs-lookup"><span data-stu-id="13502-125">IN</span></span>  
  
## <a name="supported-combinations"></a><span data-ttu-id="13502-126">Obsługiwane kombinacje</span><span class="sxs-lookup"><span data-stu-id="13502-126">Supported Combinations</span></span>  
 <span data-ttu-id="13502-127">W poniższej tabeli przedstawiono obsługiwane kombinacje operatory porównania dla każdego rodzaju:</span><span class="sxs-lookup"><span data-stu-id="13502-127">The following table shows all the supported combinations of comparison operators for each kind of type:</span></span>  
  
|<span data-ttu-id="13502-128">**Typ**</span><span class="sxs-lookup"><span data-stu-id="13502-128">**Type**</span></span>|**=**<br /><br /> <span data-ttu-id="13502-129">**!=**</span><span class="sxs-lookup"><span data-stu-id="13502-129">**!=**</span></span>|<span data-ttu-id="13502-130">**GRUPUJ WEDŁUG**</span><span class="sxs-lookup"><span data-stu-id="13502-130">**GROUP BY**</span></span><br /><br /> <span data-ttu-id="13502-131">**RÓŻNE**</span><span class="sxs-lookup"><span data-stu-id="13502-131">**DISTINCT**</span></span>|<span data-ttu-id="13502-132">**UNII**</span><span class="sxs-lookup"><span data-stu-id="13502-132">**UNION**</span></span><br /><br /> <span data-ttu-id="13502-133">**INTERSECT**</span><span class="sxs-lookup"><span data-stu-id="13502-133">**INTERSECT**</span></span><br /><br /> <span data-ttu-id="13502-134">**Z WYJĄTKIEM**</span><span class="sxs-lookup"><span data-stu-id="13502-134">**EXCEPT**</span></span><br /><br /> <span data-ttu-id="13502-135">**ZESTAW**</span><span class="sxs-lookup"><span data-stu-id="13502-135">**SET**</span></span><br /><br /> <span data-ttu-id="13502-136">**POKRYWA SIĘ**</span><span class="sxs-lookup"><span data-stu-id="13502-136">**OVERLAPS**</span></span>|<span data-ttu-id="13502-137">**W**</span><span class="sxs-lookup"><span data-stu-id="13502-137">**IN**</span></span>|<span data-ttu-id="13502-138">**<   <=**</span><span class="sxs-lookup"><span data-stu-id="13502-138">**<   <=**</span></span><br /><br /> <span data-ttu-id="13502-139">**>   >=**</span><span class="sxs-lookup"><span data-stu-id="13502-139">**>   >=**</span></span>|<span data-ttu-id="13502-140">**ORDER BY**</span><span class="sxs-lookup"><span data-stu-id="13502-140">**ORDER BY**</span></span>|<span data-ttu-id="13502-141">**MA WARTOŚĆ NULL**</span><span class="sxs-lookup"><span data-stu-id="13502-141">**IS NULL**</span></span><br /><br /> <span data-ttu-id="13502-142">**NIE MA WARTOŚCI NULL**</span><span class="sxs-lookup"><span data-stu-id="13502-142">**IS NOT NULL**</span></span>|  
|-|-|-|-|-|-|-|-|  
|<span data-ttu-id="13502-143">Typ jednostki</span><span class="sxs-lookup"><span data-stu-id="13502-143">Entity type</span></span>|<span data-ttu-id="13502-144">REF<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="13502-144">Ref<sup>1</sup></span></span>|<span data-ttu-id="13502-145">Wszystkie właściwości<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="13502-145">All properties<sup>2</sup></span></span>|<span data-ttu-id="13502-146">Wszystkie właściwości<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="13502-146">All properties<sup>2</sup></span></span>|<span data-ttu-id="13502-147">Wszystkie właściwości<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="13502-147">All properties<sup>2</sup></span></span>|<span data-ttu-id="13502-148">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="13502-148">Throw<sup>3</sup></span></span>|<span data-ttu-id="13502-149">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="13502-149">Throw<sup>3</sup></span></span>|<span data-ttu-id="13502-150">REF<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="13502-150">Ref<sup>1</sup></span></span>|  
|<span data-ttu-id="13502-151">Typ złożony</span><span class="sxs-lookup"><span data-stu-id="13502-151">Complex type</span></span>|<span data-ttu-id="13502-152">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="13502-152">Throw<sup>3</sup></span></span>|<span data-ttu-id="13502-153">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="13502-153">Throw<sup>3</sup></span></span>|<span data-ttu-id="13502-154">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="13502-154">Throw<sup>3</sup></span></span>|<span data-ttu-id="13502-155">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="13502-155">Throw<sup>3</sup></span></span>|<span data-ttu-id="13502-156">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="13502-156">Throw<sup>3</sup></span></span>|<span data-ttu-id="13502-157">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="13502-157">Throw<sup>3</sup></span></span>|<span data-ttu-id="13502-158">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="13502-158">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="13502-159">Wiersz</span><span class="sxs-lookup"><span data-stu-id="13502-159">Row</span></span>|<span data-ttu-id="13502-160">Wszystkie właściwości<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="13502-160">All properties<sup>4</sup></span></span>|<span data-ttu-id="13502-161">Wszystkie właściwości<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="13502-161">All properties<sup>4</sup></span></span>|<span data-ttu-id="13502-162">Wszystkie właściwości<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="13502-162">All properties<sup>4</sup></span></span>|<span data-ttu-id="13502-163">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="13502-163">Throw<sup>3</sup></span></span>|<span data-ttu-id="13502-164">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="13502-164">Throw<sup>3</sup></span></span>|<span data-ttu-id="13502-165">Wszystkie właściwości<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="13502-165">All properties<sup>4</sup></span></span>|<span data-ttu-id="13502-166">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="13502-166">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="13502-167">Typ pierwotny</span><span class="sxs-lookup"><span data-stu-id="13502-167">Primitive type</span></span>|<span data-ttu-id="13502-168">Specyficznych dla dostawcy</span><span class="sxs-lookup"><span data-stu-id="13502-168">Provider-specific</span></span>|<span data-ttu-id="13502-169">Specyficznych dla dostawcy</span><span class="sxs-lookup"><span data-stu-id="13502-169">Provider-specific</span></span>|<span data-ttu-id="13502-170">Specyficznych dla dostawcy</span><span class="sxs-lookup"><span data-stu-id="13502-170">Provider-specific</span></span>|<span data-ttu-id="13502-171">Specyficznych dla dostawcy</span><span class="sxs-lookup"><span data-stu-id="13502-171">Provider-specific</span></span>|<span data-ttu-id="13502-172">Specyficznych dla dostawcy</span><span class="sxs-lookup"><span data-stu-id="13502-172">Provider-specific</span></span>|<span data-ttu-id="13502-173">Specyficznych dla dostawcy</span><span class="sxs-lookup"><span data-stu-id="13502-173">Provider-specific</span></span>|<span data-ttu-id="13502-174">Specyficznych dla dostawcy</span><span class="sxs-lookup"><span data-stu-id="13502-174">Provider-specific</span></span>|  
|<span data-ttu-id="13502-175">Zestaw wielokrotny</span><span class="sxs-lookup"><span data-stu-id="13502-175">Multiset</span></span>|<span data-ttu-id="13502-176">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="13502-176">Throw<sup>3</sup></span></span>|<span data-ttu-id="13502-177">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="13502-177">Throw<sup>3</sup></span></span>|<span data-ttu-id="13502-178">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="13502-178">Throw<sup>3</sup></span></span>|<span data-ttu-id="13502-179">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="13502-179">Throw<sup>3</sup></span></span>|<span data-ttu-id="13502-180">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="13502-180">Throw<sup>3</sup></span></span>|<span data-ttu-id="13502-181">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="13502-181">Throw<sup>3</sup></span></span>|<span data-ttu-id="13502-182">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="13502-182">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="13502-183">REF</span><span class="sxs-lookup"><span data-stu-id="13502-183">Ref</span></span>|<span data-ttu-id="13502-184">Tak<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="13502-184">Yes<sup>5</sup></span></span>|<span data-ttu-id="13502-185">Tak<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="13502-185">Yes<sup>5</sup></span></span>|<span data-ttu-id="13502-186">Tak<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="13502-186">Yes<sup>5</sup></span></span>|<span data-ttu-id="13502-187">Tak<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="13502-187">Yes<sup>5</sup></span></span>|<span data-ttu-id="13502-188">Throw</span><span class="sxs-lookup"><span data-stu-id="13502-188">Throw</span></span>|<span data-ttu-id="13502-189">Throw</span><span class="sxs-lookup"><span data-stu-id="13502-189">Throw</span></span>|<span data-ttu-id="13502-190">Tak<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="13502-190">Yes<sup>5</sup></span></span>|  
|<span data-ttu-id="13502-191">Skojarzenie</span><span class="sxs-lookup"><span data-stu-id="13502-191">Association</span></span><br /><br /> <span data-ttu-id="13502-192">— typ</span><span class="sxs-lookup"><span data-stu-id="13502-192">type</span></span>|<span data-ttu-id="13502-193">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="13502-193">Throw<sup>3</sup></span></span>|<span data-ttu-id="13502-194">Throw</span><span class="sxs-lookup"><span data-stu-id="13502-194">Throw</span></span>|<span data-ttu-id="13502-195">Throw</span><span class="sxs-lookup"><span data-stu-id="13502-195">Throw</span></span>|<span data-ttu-id="13502-196">Throw</span><span class="sxs-lookup"><span data-stu-id="13502-196">Throw</span></span>|<span data-ttu-id="13502-197">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="13502-197">Throw<sup>3</sup></span></span>|<span data-ttu-id="13502-198">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="13502-198">Throw<sup>3</sup></span></span>|<span data-ttu-id="13502-199">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="13502-199">Throw<sup>3</sup></span></span>|  
  
 <span data-ttu-id="13502-200"><sup>1</sup>odwołania do danej jednostki wystąpień typu są porównywane niejawnie, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="13502-200"><sup>1</sup>The references of the given entity type instances are implicitly compared, as shown in the following example:</span></span>  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != p2 OR p1 IS NULL  
```  
  
 <span data-ttu-id="13502-201">Wystąpienie jednostki nie można porównać do jawnego odwołania.</span><span class="sxs-lookup"><span data-stu-id="13502-201">An entity instance cannot be compared to an explicit reference.</span></span> <span data-ttu-id="13502-202">Jeśli ta próba zostanie podjęta, jest zwracany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="13502-202">If this is attempted, an exception is thrown.</span></span> <span data-ttu-id="13502-203">Na przykład poniższe zapytanie spowoduje zgłoszenie wyjątku:</span><span class="sxs-lookup"><span data-stu-id="13502-203">For example, the following query will throw an exception:</span></span>  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != REF(p2)  
```  
  
 <span data-ttu-id="13502-204"><sup>2</sup>właściwości złożonych typów są spłaszczane przed wysłaniem do magazynu, więc stają się one porównywalne (o ile ich właściwości mogą być porównywane).</span><span class="sxs-lookup"><span data-stu-id="13502-204"><sup>2</sup>Properties of complex types are flattened out before being sent to the store, so they become comparable (as long as all their properties are comparable).</span></span> <span data-ttu-id="13502-205">Zobacz też <sup>4.</sup></span><span class="sxs-lookup"><span data-stu-id="13502-205">Also see <sup>4.</sup></span></span>  
  
 <span data-ttu-id="13502-206"><sup>3</sup>środowiska uruchomieniowego programu Entity Framework wykrywa nieobsługiwane przypadku i zgłasza wyjątek znaczące bez zaangażowania dostawcy/magazynu.</span><span class="sxs-lookup"><span data-stu-id="13502-206"><sup>3</sup>The Entity Framework runtime detects the unsupported case and throws a meaningful exception without engaging the provider/store.</span></span>  
  
 <span data-ttu-id="13502-207"><sup>4</sup>próby porównania wszystkich właściwości.</span><span class="sxs-lookup"><span data-stu-id="13502-207"><sup>4</sup>An attempt is made to compare all properties.</span></span> <span data-ttu-id="13502-208">Jeśli istnieje we właściwości nie można porównywać pod względem typu, takie jak text, ntext lub image, może być zgłoszony wyjątek serwera.</span><span class="sxs-lookup"><span data-stu-id="13502-208">If there is a property that is of a non-comparable type, such as text, ntext, or image, a server exception might be thrown.</span></span>  
  
 <span data-ttu-id="13502-209"><sup>5</sup>wszystkie poszczególne elementy odwołań są porównywane (dotyczy to również nazwa zestawu jednostek i wszystkich właściwości klucza typu jednostek).</span><span class="sxs-lookup"><span data-stu-id="13502-209"><sup>5</sup>All individual elements of the references are compared (this includes the entity set name and all the key properties of the entity type).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13502-210">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="13502-210">See Also</span></span>  
 [<span data-ttu-id="13502-211">Omówienie SQL jednostki</span><span class="sxs-lookup"><span data-stu-id="13502-211">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
