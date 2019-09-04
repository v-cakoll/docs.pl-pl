---
title: Semantyka porównania (Entity SQL)
ms.date: 03/30/2017
ms.assetid: b36ce28a-2fe4-4236-b782-e5f7c054deae
ms.openlocfilehash: da7b8f662d10376abd649e674701b43b7b740a6f
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251179"
---
# <a name="comparison-semantics-entity-sql"></a><span data-ttu-id="f054e-102">Semantyka porównania (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="f054e-102">Comparison Semantics (Entity SQL)</span></span>
<span data-ttu-id="f054e-103">Wykonywanie któregokolwiek z następujących [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatorów obejmuje porównanie wystąpień typu:</span><span class="sxs-lookup"><span data-stu-id="f054e-103">Performing any of the following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operators involves comparison of type instances:</span></span>  
  
## <a name="explicit-comparison"></a><span data-ttu-id="f054e-104">Jawne porównanie</span><span class="sxs-lookup"><span data-stu-id="f054e-104">Explicit comparison</span></span>  
 <span data-ttu-id="f054e-105">Operacje równości:</span><span class="sxs-lookup"><span data-stu-id="f054e-105">Equality operations:</span></span>  
  
- =  
  
- <span data-ttu-id="f054e-106">!=</span><span class="sxs-lookup"><span data-stu-id="f054e-106">!=</span></span>  
  
 <span data-ttu-id="f054e-107">Operacje porządkowania:</span><span class="sxs-lookup"><span data-stu-id="f054e-107">Ordering operations:</span></span>  
  
- <  
  
- \<=  
  
- \>  
  
- \>=  
  
 <span data-ttu-id="f054e-108">Operacje dopuszczania wartości null:</span><span class="sxs-lookup"><span data-stu-id="f054e-108">Nullability operations:</span></span>  
  
- <span data-ttu-id="f054e-109">MA WARTOŚĆ NULL</span><span class="sxs-lookup"><span data-stu-id="f054e-109">IS NULL</span></span>  
  
- <span data-ttu-id="f054e-110">NIE MA WARTOŚCI NULL</span><span class="sxs-lookup"><span data-stu-id="f054e-110">IS NOT NULL</span></span>  
  
## <a name="explicit-distinction"></a><span data-ttu-id="f054e-111">Jawne rozróżnienie</span><span class="sxs-lookup"><span data-stu-id="f054e-111">Explicit distinction</span></span>  
 <span data-ttu-id="f054e-112">Rozróżnienie równości:</span><span class="sxs-lookup"><span data-stu-id="f054e-112">Equality distinction:</span></span>  
  
- <span data-ttu-id="f054e-113">ITP</span><span class="sxs-lookup"><span data-stu-id="f054e-113">DISTINCT</span></span>  
  
- <span data-ttu-id="f054e-114">GROUP BY</span><span class="sxs-lookup"><span data-stu-id="f054e-114">GROUP BY</span></span>  
  
 <span data-ttu-id="f054e-115">Kolejność rozróżniania:</span><span class="sxs-lookup"><span data-stu-id="f054e-115">Ordering distinction:</span></span>  
  
- <span data-ttu-id="f054e-116">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="f054e-116">ORDER BY</span></span>  
  
## <a name="implicit-distinction"></a><span data-ttu-id="f054e-117">Niejawne rozróżnienie</span><span class="sxs-lookup"><span data-stu-id="f054e-117">Implicit distinction</span></span>  
 <span data-ttu-id="f054e-118">Ustaw operacje i predykaty (równość):</span><span class="sxs-lookup"><span data-stu-id="f054e-118">Set operations and predicates (equality):</span></span>  
  
- <span data-ttu-id="f054e-119">UNION</span><span class="sxs-lookup"><span data-stu-id="f054e-119">UNION</span></span>  
  
- <span data-ttu-id="f054e-120">INTERSECT</span><span class="sxs-lookup"><span data-stu-id="f054e-120">INTERSECT</span></span>  
  
- <span data-ttu-id="f054e-121">EXCEPT</span><span class="sxs-lookup"><span data-stu-id="f054e-121">EXCEPT</span></span>  
  
- <span data-ttu-id="f054e-122">SET</span><span class="sxs-lookup"><span data-stu-id="f054e-122">SET</span></span>  
  
- <span data-ttu-id="f054e-123">OVERLAPS</span><span class="sxs-lookup"><span data-stu-id="f054e-123">OVERLAPS</span></span>  
  
 <span data-ttu-id="f054e-124">Predykaty elementów (równość):</span><span class="sxs-lookup"><span data-stu-id="f054e-124">Item predicates (equality):</span></span>  
  
- <span data-ttu-id="f054e-125">IN</span><span class="sxs-lookup"><span data-stu-id="f054e-125">IN</span></span>  
  
## <a name="supported-combinations"></a><span data-ttu-id="f054e-126">Obsługiwane kombinacje</span><span class="sxs-lookup"><span data-stu-id="f054e-126">Supported Combinations</span></span>  
 <span data-ttu-id="f054e-127">W poniższej tabeli przedstawiono wszystkie obsługiwane kombinacje operatorów porównania dla każdego rodzaju typu:</span><span class="sxs-lookup"><span data-stu-id="f054e-127">The following table shows all the supported combinations of comparison operators for each kind of type:</span></span>  
  
|<span data-ttu-id="f054e-128">**Typ**</span><span class="sxs-lookup"><span data-stu-id="f054e-128">**Type**</span></span>|**=**<br /><br /> <span data-ttu-id="f054e-129">**\!=**</span><span class="sxs-lookup"><span data-stu-id="f054e-129">**!=**</span></span>|<span data-ttu-id="f054e-130">**GROUP BY**</span><span class="sxs-lookup"><span data-stu-id="f054e-130">**GROUP BY**</span></span><br /><br /> <span data-ttu-id="f054e-131">**ITP**</span><span class="sxs-lookup"><span data-stu-id="f054e-131">**DISTINCT**</span></span>|<span data-ttu-id="f054e-132">**UNION**</span><span class="sxs-lookup"><span data-stu-id="f054e-132">**UNION**</span></span><br /><br /> <span data-ttu-id="f054e-133">**INTERSECT**</span><span class="sxs-lookup"><span data-stu-id="f054e-133">**INTERSECT**</span></span><br /><br /> <span data-ttu-id="f054e-134">**EXCEPT**</span><span class="sxs-lookup"><span data-stu-id="f054e-134">**EXCEPT**</span></span><br /><br /> <span data-ttu-id="f054e-135">**SET**</span><span class="sxs-lookup"><span data-stu-id="f054e-135">**SET**</span></span><br /><br /> <span data-ttu-id="f054e-136">**OVERLAPS**</span><span class="sxs-lookup"><span data-stu-id="f054e-136">**OVERLAPS**</span></span>|<span data-ttu-id="f054e-137">**IN**</span><span class="sxs-lookup"><span data-stu-id="f054e-137">**IN**</span></span>|<span data-ttu-id="f054e-138">**<   <=**</span><span class="sxs-lookup"><span data-stu-id="f054e-138">**<   <=**</span></span><br /><br /> <span data-ttu-id="f054e-139">**>   >=**</span><span class="sxs-lookup"><span data-stu-id="f054e-139">**>   >=**</span></span>|<span data-ttu-id="f054e-140">**ORDER BY**</span><span class="sxs-lookup"><span data-stu-id="f054e-140">**ORDER BY**</span></span>|<span data-ttu-id="f054e-141">**MA WARTOŚĆ NULL**</span><span class="sxs-lookup"><span data-stu-id="f054e-141">**IS NULL**</span></span><br /><br /> <span data-ttu-id="f054e-142">**NIE MA WARTOŚCI NULL**</span><span class="sxs-lookup"><span data-stu-id="f054e-142">**IS NOT NULL**</span></span>|  
|-|-|-|-|-|-|-|-|  
|<span data-ttu-id="f054e-143">Typ jednostki</span><span class="sxs-lookup"><span data-stu-id="f054e-143">Entity type</span></span>|<span data-ttu-id="f054e-144">Odwołanie<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="f054e-144">Ref<sup>1</sup></span></span>|<span data-ttu-id="f054e-145">Wszystkie właściwości<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="f054e-145">All properties<sup>2</sup></span></span>|<span data-ttu-id="f054e-146">Wszystkie właściwości<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="f054e-146">All properties<sup>2</sup></span></span>|<span data-ttu-id="f054e-147">Wszystkie właściwości<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="f054e-147">All properties<sup>2</sup></span></span>|<span data-ttu-id="f054e-148">Zgłoś<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="f054e-148">Throw<sup>3</sup></span></span>|<span data-ttu-id="f054e-149">Zgłoś<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="f054e-149">Throw<sup>3</sup></span></span>|<span data-ttu-id="f054e-150">Odwołanie<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="f054e-150">Ref<sup>1</sup></span></span>|  
|<span data-ttu-id="f054e-151">Typ złożony</span><span class="sxs-lookup"><span data-stu-id="f054e-151">Complex type</span></span>|<span data-ttu-id="f054e-152">Zgłoś<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="f054e-152">Throw<sup>3</sup></span></span>|<span data-ttu-id="f054e-153">Zgłoś<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="f054e-153">Throw<sup>3</sup></span></span>|<span data-ttu-id="f054e-154">Zgłoś<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="f054e-154">Throw<sup>3</sup></span></span>|<span data-ttu-id="f054e-155">Zgłoś<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="f054e-155">Throw<sup>3</sup></span></span>|<span data-ttu-id="f054e-156">Zgłoś<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="f054e-156">Throw<sup>3</sup></span></span>|<span data-ttu-id="f054e-157">Zgłoś<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="f054e-157">Throw<sup>3</sup></span></span>|<span data-ttu-id="f054e-158">Zgłoś<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="f054e-158">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="f054e-159">Wiersz</span><span class="sxs-lookup"><span data-stu-id="f054e-159">Row</span></span>|<span data-ttu-id="f054e-160">Wszystkie właściwości<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="f054e-160">All properties<sup>4</sup></span></span>|<span data-ttu-id="f054e-161">Wszystkie właściwości<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="f054e-161">All properties<sup>4</sup></span></span>|<span data-ttu-id="f054e-162">Wszystkie właściwości<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="f054e-162">All properties<sup>4</sup></span></span>|<span data-ttu-id="f054e-163">Zgłoś<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="f054e-163">Throw<sup>3</sup></span></span>|<span data-ttu-id="f054e-164">Zgłoś<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="f054e-164">Throw<sup>3</sup></span></span>|<span data-ttu-id="f054e-165">Wszystkie właściwości<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="f054e-165">All properties<sup>4</sup></span></span>|<span data-ttu-id="f054e-166">Zgłoś<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="f054e-166">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="f054e-167">Typ pierwotny</span><span class="sxs-lookup"><span data-stu-id="f054e-167">Primitive type</span></span>|<span data-ttu-id="f054e-168">Specyficzne dla dostawcy</span><span class="sxs-lookup"><span data-stu-id="f054e-168">Provider-specific</span></span>|<span data-ttu-id="f054e-169">Specyficzne dla dostawcy</span><span class="sxs-lookup"><span data-stu-id="f054e-169">Provider-specific</span></span>|<span data-ttu-id="f054e-170">Specyficzne dla dostawcy</span><span class="sxs-lookup"><span data-stu-id="f054e-170">Provider-specific</span></span>|<span data-ttu-id="f054e-171">Specyficzne dla dostawcy</span><span class="sxs-lookup"><span data-stu-id="f054e-171">Provider-specific</span></span>|<span data-ttu-id="f054e-172">Specyficzne dla dostawcy</span><span class="sxs-lookup"><span data-stu-id="f054e-172">Provider-specific</span></span>|<span data-ttu-id="f054e-173">Specyficzne dla dostawcy</span><span class="sxs-lookup"><span data-stu-id="f054e-173">Provider-specific</span></span>|<span data-ttu-id="f054e-174">Specyficzne dla dostawcy</span><span class="sxs-lookup"><span data-stu-id="f054e-174">Provider-specific</span></span>|  
|<span data-ttu-id="f054e-175">Multiset</span><span class="sxs-lookup"><span data-stu-id="f054e-175">Multiset</span></span>|<span data-ttu-id="f054e-176">Zgłoś<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="f054e-176">Throw<sup>3</sup></span></span>|<span data-ttu-id="f054e-177">Zgłoś<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="f054e-177">Throw<sup>3</sup></span></span>|<span data-ttu-id="f054e-178">Zgłoś<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="f054e-178">Throw<sup>3</sup></span></span>|<span data-ttu-id="f054e-179">Zgłoś<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="f054e-179">Throw<sup>3</sup></span></span>|<span data-ttu-id="f054e-180">Zgłoś<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="f054e-180">Throw<sup>3</sup></span></span>|<span data-ttu-id="f054e-181">Zgłoś<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="f054e-181">Throw<sup>3</sup></span></span>|<span data-ttu-id="f054e-182">Zgłoś<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="f054e-182">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="f054e-183">Umieszczone</span><span class="sxs-lookup"><span data-stu-id="f054e-183">Ref</span></span>|<span data-ttu-id="f054e-184">Tak<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="f054e-184">Yes<sup>5</sup></span></span>|<span data-ttu-id="f054e-185">Tak<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="f054e-185">Yes<sup>5</sup></span></span>|<span data-ttu-id="f054e-186">Tak<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="f054e-186">Yes<sup>5</sup></span></span>|<span data-ttu-id="f054e-187">Tak<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="f054e-187">Yes<sup>5</sup></span></span>|<span data-ttu-id="f054e-188">Throw</span><span class="sxs-lookup"><span data-stu-id="f054e-188">Throw</span></span>|<span data-ttu-id="f054e-189">Throw</span><span class="sxs-lookup"><span data-stu-id="f054e-189">Throw</span></span>|<span data-ttu-id="f054e-190">Tak<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="f054e-190">Yes<sup>5</sup></span></span>|  
|<span data-ttu-id="f054e-191">Skojarzenie</span><span class="sxs-lookup"><span data-stu-id="f054e-191">Association</span></span><br /><br /> <span data-ttu-id="f054e-192">— typ</span><span class="sxs-lookup"><span data-stu-id="f054e-192">type</span></span>|<span data-ttu-id="f054e-193">Zgłoś<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="f054e-193">Throw<sup>3</sup></span></span>|<span data-ttu-id="f054e-194">Throw</span><span class="sxs-lookup"><span data-stu-id="f054e-194">Throw</span></span>|<span data-ttu-id="f054e-195">Throw</span><span class="sxs-lookup"><span data-stu-id="f054e-195">Throw</span></span>|<span data-ttu-id="f054e-196">Throw</span><span class="sxs-lookup"><span data-stu-id="f054e-196">Throw</span></span>|<span data-ttu-id="f054e-197">Zgłoś<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="f054e-197">Throw<sup>3</sup></span></span>|<span data-ttu-id="f054e-198">Zgłoś<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="f054e-198">Throw<sup>3</sup></span></span>|<span data-ttu-id="f054e-199">Zgłoś<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="f054e-199">Throw<sup>3</sup></span></span>|  
  
 <span data-ttu-id="f054e-200"><sup>1</sup> Odwołania do danego wystąpienia typu jednostki są niejawnie porównywane, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="f054e-200"><sup>1</sup>The references of the given entity type instances are implicitly compared, as shown in the following example:</span></span>  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != p2 OR p1 IS NULL  
```  
  
 <span data-ttu-id="f054e-201">Nie można porównać wystąpienia jednostki z jawnym odwołaniem.</span><span class="sxs-lookup"><span data-stu-id="f054e-201">An entity instance cannot be compared to an explicit reference.</span></span> <span data-ttu-id="f054e-202">Jeśli zostanie podjęta taka próba, zostanie zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="f054e-202">If this is attempted, an exception is thrown.</span></span> <span data-ttu-id="f054e-203">Na przykład następujące zapytanie spowoduje zgłoszenie wyjątku:</span><span class="sxs-lookup"><span data-stu-id="f054e-203">For example, the following query will throw an exception:</span></span>  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != REF(p2)  
```  
  
 <span data-ttu-id="f054e-204"><sup>2</sup> Właściwości typów złożonych są spłaszczane przed wysłaniem do magazynu, dzięki czemu stają się one porównywalne (o ile wszystkie ich właściwości są porównywalne).</span><span class="sxs-lookup"><span data-stu-id="f054e-204"><sup>2</sup>Properties of complex types are flattened out before being sent to the store, so they become comparable (as long as all their properties are comparable).</span></span> <span data-ttu-id="f054e-205">Zobacz też <sup>4.</sup></span><span class="sxs-lookup"><span data-stu-id="f054e-205">Also see <sup>4.</sup></span></span>  
  
 <span data-ttu-id="f054e-206"><sup>3</sup> Środowisko uruchomieniowe Entity Framework wykrywa nieobsługiwany przypadek i zgłasza znaczący wyjątek bez angażowania dostawcy/magazynu.</span><span class="sxs-lookup"><span data-stu-id="f054e-206"><sup>3</sup>The Entity Framework runtime detects the unsupported case and throws a meaningful exception without engaging the provider/store.</span></span>  
  
 <span data-ttu-id="f054e-207"><sup>4</sup> Podjęto próbę porównania wszystkich właściwości.</span><span class="sxs-lookup"><span data-stu-id="f054e-207"><sup>4</sup>An attempt is made to compare all properties.</span></span> <span data-ttu-id="f054e-208">Jeśli istnieje właściwość, której typ nie jest porównywalny, taki jak text, ntext lub Image, może zostać zgłoszony wyjątek serwera.</span><span class="sxs-lookup"><span data-stu-id="f054e-208">If there is a property that is of a non-comparable type, such as text, ntext, or image, a server exception might be thrown.</span></span>  
  
 <span data-ttu-id="f054e-209"><sup>5</sup> Wszystkie poszczególne elementy odwołań są porównywane (obejmuje to nazwę zestawu jednostek i wszystkie właściwości klucza typu jednostki).</span><span class="sxs-lookup"><span data-stu-id="f054e-209"><sup>5</sup>All individual elements of the references are compared (this includes the entity set name and all the key properties of the entity type).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f054e-210">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f054e-210">See also</span></span>

- [<span data-ttu-id="f054e-211">Omówienie jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="f054e-211">Entity SQL Overview</span></span>](entity-sql-overview.md)
