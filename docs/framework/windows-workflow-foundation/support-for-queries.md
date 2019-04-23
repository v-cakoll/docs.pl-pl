---
title: Obsługa zapytań
ms.date: 03/30/2017
ms.assetid: 093c22f5-3294-4642-857a-5252233d6796
ms.openlocfilehash: 30695fcd791a0d69c31a897068d69838c80c3957
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59307954"
---
# <a name="support-for-queries"></a><span data-ttu-id="66f58-102">Obsługa zapytań</span><span class="sxs-lookup"><span data-stu-id="66f58-102">Support for Queries</span></span>
<span data-ttu-id="66f58-103">Store wystąpienia przepływu pracy SQL rejestruje zestaw właściwości dobrze znane w magazynie.</span><span class="sxs-lookup"><span data-stu-id="66f58-103">The SQL Workflow Instance Store records a set of well-known properties in the store.</span></span> <span data-ttu-id="66f58-104">Użytkownicy mogą wyszukiwać wystąpień na podstawie tych właściwości.</span><span class="sxs-lookup"><span data-stu-id="66f58-104">Users can query for instances based on these properties.</span></span> <span data-ttu-id="66f58-105">Poniższa lista zawiera niektóre z tych znanych właściwości:</span><span class="sxs-lookup"><span data-stu-id="66f58-105">The following list contains some of these well-known properties:</span></span>  
  
-   <span data-ttu-id="66f58-106">**Nazwa witryny.**</span><span class="sxs-lookup"><span data-stu-id="66f58-106">**Site Name.**</span></span> <span data-ttu-id="66f58-107">Nazwa witryny sieci Web, które zawiera tę usługę.</span><span class="sxs-lookup"><span data-stu-id="66f58-107">Name of the Web site that contains the service.</span></span>  
  
-   <span data-ttu-id="66f58-108">**Ścieżka względna aplikacji.**</span><span class="sxs-lookup"><span data-stu-id="66f58-108">**Relative Application Path.**</span></span> <span data-ttu-id="66f58-109">Ścieżka aplikacji względem witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="66f58-109">Path of the application relative to the Web site.</span></span>  
  
-   <span data-ttu-id="66f58-110">**Relative Service Path.**</span><span class="sxs-lookup"><span data-stu-id="66f58-110">**Relative Service Path.**</span></span> <span data-ttu-id="66f58-111">Ścieżka usługi względem aplikacji.</span><span class="sxs-lookup"><span data-stu-id="66f58-111">Path of the service relative to the application.</span></span>  
  
-   <span data-ttu-id="66f58-112">**Nazwa usługi.**</span><span class="sxs-lookup"><span data-stu-id="66f58-112">**Service Name.**</span></span> <span data-ttu-id="66f58-113">Nazwa usługi.</span><span class="sxs-lookup"><span data-stu-id="66f58-113">Name of the service.</span></span>  
  
-   <span data-ttu-id="66f58-114">**Usługa Namespace.**</span><span class="sxs-lookup"><span data-stu-id="66f58-114">**Service Namespace.**</span></span> <span data-ttu-id="66f58-115">Nazwa przestrzeni nazw, używanymi przez usługę.</span><span class="sxs-lookup"><span data-stu-id="66f58-115">Name of the namespace that the service uses.</span></span>  
  
-   <span data-ttu-id="66f58-116">**Bieżąca maszyna.**</span><span class="sxs-lookup"><span data-stu-id="66f58-116">**Current Machine.**</span></span>  
  
-   <span data-ttu-id="66f58-117">**Ostatnie maszyny**.</span><span class="sxs-lookup"><span data-stu-id="66f58-117">**Last Machine**.</span></span> <span data-ttu-id="66f58-118">Komputer, na którym został uruchomiony ostatniego wystąpienia usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="66f58-118">The computer on which the workflow service instance ran the last time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="66f58-119">W przypadku scenariuszy samodzielnie hostowany przy użyciu hosta usługi przepływu pracy są wypełniane tylko cztery ostatnie właściwości.</span><span class="sxs-lookup"><span data-stu-id="66f58-119">For self-hosted scenarios using Workflow Service Host, only the last four properties are populated.</span></span> <span data-ttu-id="66f58-120">W przypadku scenariuszy aplikacji przepływu pracy jest wypełniana tylko ostatnie właściwości.</span><span class="sxs-lookup"><span data-stu-id="66f58-120">For Workflow Application scenarios, only the last property is populated.</span></span>  
  
 <span data-ttu-id="66f58-121">Środowisko wykonawcze przepływów pracy dostarcza wartości dla pierwszych trzech właściwości.</span><span class="sxs-lookup"><span data-stu-id="66f58-121">The workflow runtime supplies values for the first three properties.</span></span> <span data-ttu-id="66f58-122">Hosta usługi przepływu pracy dostarcza wartość **zawiesić Przyczyna** właściwości.</span><span class="sxs-lookup"><span data-stu-id="66f58-122">The workflow service host supplies the value for the **Suspend Reason** property.</span></span> <span data-ttu-id="66f58-123">Store wystąpienia przepływu pracy SQL, sama dostarcza wartości dla **ostatnia maszyna zaktualizowane** właściwości.</span><span class="sxs-lookup"><span data-stu-id="66f58-123">The SQL Workflow Instance Store itself supplies values for the **Last Updated Machine** property.</span></span>  
  
 <span data-ttu-id="66f58-124">Funkcja Store wystąpienia przepływu pracy SQL umożliwia także określić właściwości niestandardowe, dla których mają być przechowywane wartości w bazie danych trwałości i chcesz używać w zapytaniach.</span><span class="sxs-lookup"><span data-stu-id="66f58-124">The SQL Workflow Instance Store feature also lets you specify the custom properties for which you want to store the values in the persistence database and that you want to use in queries.</span></span> <span data-ttu-id="66f58-125">Aby uzyskać więcej informacji na temat niestandardowych promocji zobacz [rozszerzalności Store](store-extensibility.md).</span><span class="sxs-lookup"><span data-stu-id="66f58-125">For more information about custom promotions, see [Store Extensibility](store-extensibility.md).</span></span>  
  
## <a name="views"></a><span data-ttu-id="66f58-126">Widoki</span><span class="sxs-lookup"><span data-stu-id="66f58-126">Views</span></span>  
 <span data-ttu-id="66f58-127">Magazyn wystąpienie zawiera następujące widoki.</span><span class="sxs-lookup"><span data-stu-id="66f58-127">The instance store contains the following views.</span></span> <span data-ttu-id="66f58-128">Zobacz [schemat bazy danych trwałości](persistence-database-schema.md) więcej szczegółowych informacji.</span><span class="sxs-lookup"><span data-stu-id="66f58-128">See [Persistence Database Schema](persistence-database-schema.md) for further details.</span></span>  
  
### <a name="the-instances-view"></a><span data-ttu-id="66f58-129">Wyświetl wystąpienia</span><span class="sxs-lookup"><span data-stu-id="66f58-129">The Instances View</span></span>  
 <span data-ttu-id="66f58-130">Widok wystąpień zawiera następujące pola:</span><span class="sxs-lookup"><span data-stu-id="66f58-130">The Instances view contains the following fields:</span></span>  
  
1. <span data-ttu-id="66f58-131">**Identyfikator**</span><span class="sxs-lookup"><span data-stu-id="66f58-131">**Id**</span></span>  
  
2. <span data-ttu-id="66f58-132">**PendingTimer**</span><span class="sxs-lookup"><span data-stu-id="66f58-132">**PendingTimer**</span></span>  
  
3. <span data-ttu-id="66f58-133">**CreationTime**</span><span class="sxs-lookup"><span data-stu-id="66f58-133">**CreationTime**</span></span>  
  
4. <span data-ttu-id="66f58-134">**LastUpdatedTime**</span><span class="sxs-lookup"><span data-stu-id="66f58-134">**LastUpdatedTime**</span></span>  
  
5. <span data-ttu-id="66f58-135">**ServiceDeploymentId**</span><span class="sxs-lookup"><span data-stu-id="66f58-135">**ServiceDeploymentId**</span></span>  
  
6. <span data-ttu-id="66f58-136">**SuspensionExceptionName**</span><span class="sxs-lookup"><span data-stu-id="66f58-136">**SuspensionExceptionName**</span></span>  
  
7. <span data-ttu-id="66f58-137">**SuspensionReason**</span><span class="sxs-lookup"><span data-stu-id="66f58-137">**SuspensionReason**</span></span>  
  
8. <span data-ttu-id="66f58-138">**ActiveBookmarks**</span><span class="sxs-lookup"><span data-stu-id="66f58-138">**ActiveBookmarks**</span></span>  
  
9. <span data-ttu-id="66f58-139">**CurrentMachine**</span><span class="sxs-lookup"><span data-stu-id="66f58-139">**CurrentMachine**</span></span>  
  
10. <span data-ttu-id="66f58-140">**LastMachine**</span><span class="sxs-lookup"><span data-stu-id="66f58-140">**LastMachine**</span></span>  
  
11. <span data-ttu-id="66f58-141">**ExecutionStatus**</span><span class="sxs-lookup"><span data-stu-id="66f58-141">**ExecutionStatus**</span></span>  
  
12. <span data-ttu-id="66f58-142">**IsInitialized**</span><span class="sxs-lookup"><span data-stu-id="66f58-142">**IsInitialized**</span></span>  
  
13. <span data-ttu-id="66f58-143">**IsSuspended**</span><span class="sxs-lookup"><span data-stu-id="66f58-143">**IsSuspended**</span></span>  
  
14. <span data-ttu-id="66f58-144">**IsCompleted**</span><span class="sxs-lookup"><span data-stu-id="66f58-144">**IsCompleted**</span></span>  
  
15. <span data-ttu-id="66f58-145">**EncodingOption**</span><span class="sxs-lookup"><span data-stu-id="66f58-145">**EncodingOption**</span></span>  
  
16. <span data-ttu-id="66f58-146">**ReadWritePrimitiveDataProperties**</span><span class="sxs-lookup"><span data-stu-id="66f58-146">**ReadWritePrimitiveDataProperties**</span></span>  
  
17. <span data-ttu-id="66f58-147">**WriteOnlyPrimitiveDataProperties**</span><span class="sxs-lookup"><span data-stu-id="66f58-147">**WriteOnlyPrimitiveDataProperties**</span></span>  
  
18. <span data-ttu-id="66f58-148">**ReadWriteComplexDataProperties**</span><span class="sxs-lookup"><span data-stu-id="66f58-148">**ReadWriteComplexDataProperties**</span></span>  
  
19. <span data-ttu-id="66f58-149">**WriteOnlyComplexDataProperties**</span><span class="sxs-lookup"><span data-stu-id="66f58-149">**WriteOnlyComplexDataProperties**</span></span>  
  
### <a name="the-servicedeployments-view"></a><span data-ttu-id="66f58-150">Widok ServiceDeployments</span><span class="sxs-lookup"><span data-stu-id="66f58-150">The ServiceDeployments view</span></span>  
 <span data-ttu-id="66f58-151">Widok ServiceDeployments zawiera następujące pola:</span><span class="sxs-lookup"><span data-stu-id="66f58-151">The ServiceDeployments view contains the following fields:</span></span>  
  
1. <span data-ttu-id="66f58-152">**SiteName**</span><span class="sxs-lookup"><span data-stu-id="66f58-152">**SiteName**</span></span>  
  
2. <span data-ttu-id="66f58-153">**RelativeServicePath**</span><span class="sxs-lookup"><span data-stu-id="66f58-153">**RelativeServicePath**</span></span>  
  
3. <span data-ttu-id="66f58-154">**RelativeApplicationPath**</span><span class="sxs-lookup"><span data-stu-id="66f58-154">**RelativeApplicationPath**</span></span>  
  
4. <span data-ttu-id="66f58-155">**ServiceName**</span><span class="sxs-lookup"><span data-stu-id="66f58-155">**ServiceName**</span></span>  
  
5. <span data-ttu-id="66f58-156">**ServiceNamespace**</span><span class="sxs-lookup"><span data-stu-id="66f58-156">**ServiceNamespace**</span></span>  
  
### <a name="the-instancepromotedproperties-view"></a><span data-ttu-id="66f58-157">Widok InstancePromotedProperties</span><span class="sxs-lookup"><span data-stu-id="66f58-157">The InstancePromotedProperties view</span></span>  
 <span data-ttu-id="66f58-158">Widok InstancePromotedProperties zawiera następujące pola.</span><span class="sxs-lookup"><span data-stu-id="66f58-158">The InstancePromotedProperties view contains the following fields.</span></span> <span data-ttu-id="66f58-159">Aby uzyskać więcej informacji na temat właściwości o podwyższonym poziomie, zobacz [rozszerzalności Store](store-extensibility.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="66f58-159">For details on promoted properties, see the [Store Extensibility](store-extensibility.md) topic.</span></span>  
  
1. <span data-ttu-id="66f58-160">**InstanceId**</span><span class="sxs-lookup"><span data-stu-id="66f58-160">**InstanceId**</span></span>  
  
2. <span data-ttu-id="66f58-161">**EncodingOption**</span><span class="sxs-lookup"><span data-stu-id="66f58-161">**EncodingOption**</span></span>  
  
3. <span data-ttu-id="66f58-162">**PromotionName**</span><span class="sxs-lookup"><span data-stu-id="66f58-162">**PromotionName**</span></span>  
  
4. <span data-ttu-id="66f58-163">**Wartość #** (zakres pola z **wartość1** do **Value64**).</span><span class="sxs-lookup"><span data-stu-id="66f58-163">**Value#** (a range of fields from **Value1** to **Value64**).</span></span>
