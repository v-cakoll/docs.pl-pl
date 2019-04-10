---
title: Obsługa zapytań
ms.date: 03/30/2017
ms.assetid: 093c22f5-3294-4642-857a-5252233d6796
ms.openlocfilehash: 30695fcd791a0d69c31a897068d69838c80c3957
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59307954"
---
# <a name="support-for-queries"></a><span data-ttu-id="101bc-102">Obsługa zapytań</span><span class="sxs-lookup"><span data-stu-id="101bc-102">Support for Queries</span></span>
<span data-ttu-id="101bc-103">Store wystąpienia przepływu pracy SQL rejestruje zestaw właściwości dobrze znane w magazynie.</span><span class="sxs-lookup"><span data-stu-id="101bc-103">The SQL Workflow Instance Store records a set of well-known properties in the store.</span></span> <span data-ttu-id="101bc-104">Użytkownicy mogą wyszukiwać wystąpień na podstawie tych właściwości.</span><span class="sxs-lookup"><span data-stu-id="101bc-104">Users can query for instances based on these properties.</span></span> <span data-ttu-id="101bc-105">Poniższa lista zawiera niektóre z tych znanych właściwości:</span><span class="sxs-lookup"><span data-stu-id="101bc-105">The following list contains some of these well-known properties:</span></span>  
  
-   **<span data-ttu-id="101bc-106">Nazwa witryny.</span><span class="sxs-lookup"><span data-stu-id="101bc-106">Site Name.</span></span>** <span data-ttu-id="101bc-107">Nazwa witryny sieci Web, które zawiera tę usługę.</span><span class="sxs-lookup"><span data-stu-id="101bc-107">Name of the Web site that contains the service.</span></span>  
  
-   **<span data-ttu-id="101bc-108">Ścieżka względna aplikacji.</span><span class="sxs-lookup"><span data-stu-id="101bc-108">Relative Application Path.</span></span>** <span data-ttu-id="101bc-109">Ścieżka aplikacji względem witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="101bc-109">Path of the application relative to the Web site.</span></span>  
  
-   **<span data-ttu-id="101bc-110">Relative Service Path.</span><span class="sxs-lookup"><span data-stu-id="101bc-110">Relative Service Path.</span></span>** <span data-ttu-id="101bc-111">Ścieżka usługi względem aplikacji.</span><span class="sxs-lookup"><span data-stu-id="101bc-111">Path of the service relative to the application.</span></span>  
  
-   **<span data-ttu-id="101bc-112">Nazwa usługi.</span><span class="sxs-lookup"><span data-stu-id="101bc-112">Service Name.</span></span>** <span data-ttu-id="101bc-113">Nazwa usługi.</span><span class="sxs-lookup"><span data-stu-id="101bc-113">Name of the service.</span></span>  
  
-   **<span data-ttu-id="101bc-114">Usługa Namespace.</span><span class="sxs-lookup"><span data-stu-id="101bc-114">Service Namespace.</span></span>** <span data-ttu-id="101bc-115">Nazwa przestrzeni nazw, używanymi przez usługę.</span><span class="sxs-lookup"><span data-stu-id="101bc-115">Name of the namespace that the service uses.</span></span>  
  
-   **<span data-ttu-id="101bc-116">Bieżąca maszyna.</span><span class="sxs-lookup"><span data-stu-id="101bc-116">Current Machine.</span></span>**  
  
-   <span data-ttu-id="101bc-117">**Ostatnie maszyny**.</span><span class="sxs-lookup"><span data-stu-id="101bc-117">**Last Machine**.</span></span> <span data-ttu-id="101bc-118">Komputer, na którym został uruchomiony ostatniego wystąpienia usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="101bc-118">The computer on which the workflow service instance ran the last time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="101bc-119">W przypadku scenariuszy samodzielnie hostowany przy użyciu hosta usługi przepływu pracy są wypełniane tylko cztery ostatnie właściwości.</span><span class="sxs-lookup"><span data-stu-id="101bc-119">For self-hosted scenarios using Workflow Service Host, only the last four properties are populated.</span></span> <span data-ttu-id="101bc-120">W przypadku scenariuszy aplikacji przepływu pracy jest wypełniana tylko ostatnie właściwości.</span><span class="sxs-lookup"><span data-stu-id="101bc-120">For Workflow Application scenarios, only the last property is populated.</span></span>  
  
 <span data-ttu-id="101bc-121">Środowisko wykonawcze przepływów pracy dostarcza wartości dla pierwszych trzech właściwości.</span><span class="sxs-lookup"><span data-stu-id="101bc-121">The workflow runtime supplies values for the first three properties.</span></span> <span data-ttu-id="101bc-122">Hosta usługi przepływu pracy dostarcza wartość **zawiesić Przyczyna** właściwości.</span><span class="sxs-lookup"><span data-stu-id="101bc-122">The workflow service host supplies the value for the **Suspend Reason** property.</span></span> <span data-ttu-id="101bc-123">Store wystąpienia przepływu pracy SQL, sama dostarcza wartości dla **ostatnia maszyna zaktualizowane** właściwości.</span><span class="sxs-lookup"><span data-stu-id="101bc-123">The SQL Workflow Instance Store itself supplies values for the **Last Updated Machine** property.</span></span>  
  
 <span data-ttu-id="101bc-124">Funkcja Store wystąpienia przepływu pracy SQL umożliwia także określić właściwości niestandardowe, dla których mają być przechowywane wartości w bazie danych trwałości i chcesz używać w zapytaniach.</span><span class="sxs-lookup"><span data-stu-id="101bc-124">The SQL Workflow Instance Store feature also lets you specify the custom properties for which you want to store the values in the persistence database and that you want to use in queries.</span></span> <span data-ttu-id="101bc-125">Aby uzyskać więcej informacji na temat niestandardowych promocji zobacz [rozszerzalności Store](store-extensibility.md).</span><span class="sxs-lookup"><span data-stu-id="101bc-125">For more information about custom promotions, see [Store Extensibility](store-extensibility.md).</span></span>  
  
## <a name="views"></a><span data-ttu-id="101bc-126">Widoki</span><span class="sxs-lookup"><span data-stu-id="101bc-126">Views</span></span>  
 <span data-ttu-id="101bc-127">Magazyn wystąpienie zawiera następujące widoki.</span><span class="sxs-lookup"><span data-stu-id="101bc-127">The instance store contains the following views.</span></span> <span data-ttu-id="101bc-128">Zobacz [schemat bazy danych trwałości](persistence-database-schema.md) więcej szczegółowych informacji.</span><span class="sxs-lookup"><span data-stu-id="101bc-128">See [Persistence Database Schema](persistence-database-schema.md) for further details.</span></span>  
  
### <a name="the-instances-view"></a><span data-ttu-id="101bc-129">Wyświetl wystąpienia</span><span class="sxs-lookup"><span data-stu-id="101bc-129">The Instances View</span></span>  
 <span data-ttu-id="101bc-130">Widok wystąpień zawiera następujące pola:</span><span class="sxs-lookup"><span data-stu-id="101bc-130">The Instances view contains the following fields:</span></span>  
  
1. **<span data-ttu-id="101bc-131">Id</span><span class="sxs-lookup"><span data-stu-id="101bc-131">Id</span></span>**  
  
2. **<span data-ttu-id="101bc-132">PendingTimer</span><span class="sxs-lookup"><span data-stu-id="101bc-132">PendingTimer</span></span>**  
  
3. **<span data-ttu-id="101bc-133">CreationTime</span><span class="sxs-lookup"><span data-stu-id="101bc-133">CreationTime</span></span>**  
  
4. **<span data-ttu-id="101bc-134">LastUpdatedTime</span><span class="sxs-lookup"><span data-stu-id="101bc-134">LastUpdatedTime</span></span>**  
  
5. **<span data-ttu-id="101bc-135">ServiceDeploymentId</span><span class="sxs-lookup"><span data-stu-id="101bc-135">ServiceDeploymentId</span></span>**  
  
6. **<span data-ttu-id="101bc-136">SuspensionExceptionName</span><span class="sxs-lookup"><span data-stu-id="101bc-136">SuspensionExceptionName</span></span>**  
  
7. **<span data-ttu-id="101bc-137">SuspensionReason</span><span class="sxs-lookup"><span data-stu-id="101bc-137">SuspensionReason</span></span>**  
  
8. **<span data-ttu-id="101bc-138">ActiveBookmarks</span><span class="sxs-lookup"><span data-stu-id="101bc-138">ActiveBookmarks</span></span>**  
  
9. **<span data-ttu-id="101bc-139">CurrentMachine</span><span class="sxs-lookup"><span data-stu-id="101bc-139">CurrentMachine</span></span>**  
  
10. **<span data-ttu-id="101bc-140">LastMachine</span><span class="sxs-lookup"><span data-stu-id="101bc-140">LastMachine</span></span>**  
  
11. **<span data-ttu-id="101bc-141">ExecutionStatus</span><span class="sxs-lookup"><span data-stu-id="101bc-141">ExecutionStatus</span></span>**  
  
12. **<span data-ttu-id="101bc-142">IsInitialized</span><span class="sxs-lookup"><span data-stu-id="101bc-142">IsInitialized</span></span>**  
  
13. **<span data-ttu-id="101bc-143">IsSuspended</span><span class="sxs-lookup"><span data-stu-id="101bc-143">IsSuspended</span></span>**  
  
14. **<span data-ttu-id="101bc-144">IsCompleted</span><span class="sxs-lookup"><span data-stu-id="101bc-144">IsCompleted</span></span>**  
  
15. **<span data-ttu-id="101bc-145">EncodingOption</span><span class="sxs-lookup"><span data-stu-id="101bc-145">EncodingOption</span></span>**  
  
16. **<span data-ttu-id="101bc-146">ReadWritePrimitiveDataProperties</span><span class="sxs-lookup"><span data-stu-id="101bc-146">ReadWritePrimitiveDataProperties</span></span>**  
  
17. **<span data-ttu-id="101bc-147">WriteOnlyPrimitiveDataProperties</span><span class="sxs-lookup"><span data-stu-id="101bc-147">WriteOnlyPrimitiveDataProperties</span></span>**  
  
18. **<span data-ttu-id="101bc-148">ReadWriteComplexDataProperties</span><span class="sxs-lookup"><span data-stu-id="101bc-148">ReadWriteComplexDataProperties</span></span>**  
  
19. **<span data-ttu-id="101bc-149">WriteOnlyComplexDataProperties</span><span class="sxs-lookup"><span data-stu-id="101bc-149">WriteOnlyComplexDataProperties</span></span>**  
  
### <a name="the-servicedeployments-view"></a><span data-ttu-id="101bc-150">Widok ServiceDeployments</span><span class="sxs-lookup"><span data-stu-id="101bc-150">The ServiceDeployments view</span></span>  
 <span data-ttu-id="101bc-151">Widok ServiceDeployments zawiera następujące pola:</span><span class="sxs-lookup"><span data-stu-id="101bc-151">The ServiceDeployments view contains the following fields:</span></span>  
  
1. **<span data-ttu-id="101bc-152">SiteName</span><span class="sxs-lookup"><span data-stu-id="101bc-152">SiteName</span></span>**  
  
2. **<span data-ttu-id="101bc-153">RelativeServicePath</span><span class="sxs-lookup"><span data-stu-id="101bc-153">RelativeServicePath</span></span>**  
  
3. **<span data-ttu-id="101bc-154">RelativeApplicationPath</span><span class="sxs-lookup"><span data-stu-id="101bc-154">RelativeApplicationPath</span></span>**  
  
4. **<span data-ttu-id="101bc-155">ServiceName</span><span class="sxs-lookup"><span data-stu-id="101bc-155">ServiceName</span></span>**  
  
5. **<span data-ttu-id="101bc-156">ServiceNamespace</span><span class="sxs-lookup"><span data-stu-id="101bc-156">ServiceNamespace</span></span>**  
  
### <a name="the-instancepromotedproperties-view"></a><span data-ttu-id="101bc-157">Widok InstancePromotedProperties</span><span class="sxs-lookup"><span data-stu-id="101bc-157">The InstancePromotedProperties view</span></span>  
 <span data-ttu-id="101bc-158">Widok InstancePromotedProperties zawiera następujące pola.</span><span class="sxs-lookup"><span data-stu-id="101bc-158">The InstancePromotedProperties view contains the following fields.</span></span> <span data-ttu-id="101bc-159">Aby uzyskać więcej informacji na temat właściwości o podwyższonym poziomie, zobacz [rozszerzalności Store](store-extensibility.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="101bc-159">For details on promoted properties, see the [Store Extensibility](store-extensibility.md) topic.</span></span>  
  
1. **<span data-ttu-id="101bc-160">InstanceId</span><span class="sxs-lookup"><span data-stu-id="101bc-160">InstanceId</span></span>**  
  
2. **<span data-ttu-id="101bc-161">EncodingOption</span><span class="sxs-lookup"><span data-stu-id="101bc-161">EncodingOption</span></span>**  
  
3. **<span data-ttu-id="101bc-162">PromotionName</span><span class="sxs-lookup"><span data-stu-id="101bc-162">PromotionName</span></span>**  
  
4. <span data-ttu-id="101bc-163">**Wartość #** (zakres pola z **wartość1** do **Value64**).</span><span class="sxs-lookup"><span data-stu-id="101bc-163">**Value#** (a range of fields from **Value1** to **Value64**).</span></span>
