---
title: Obsługa zapytań
ms.date: 03/30/2017
ms.assetid: 093c22f5-3294-4642-857a-5252233d6796
ms.openlocfilehash: e281b5ae7a41bd282f8e7c7eb9db6f99ef5487f3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69948937"
---
# <a name="support-for-queries"></a><span data-ttu-id="b1d1f-102">Obsługa zapytań</span><span class="sxs-lookup"><span data-stu-id="b1d1f-102">Support for Queries</span></span>
<span data-ttu-id="b1d1f-103">Magazyn wystąpień przepływu pracy SQL rejestruje zestaw dobrze znanych właściwości w sklepie.</span><span class="sxs-lookup"><span data-stu-id="b1d1f-103">The SQL Workflow Instance Store records a set of well-known properties in the store.</span></span> <span data-ttu-id="b1d1f-104">Użytkownicy mogą wykonywać zapytania o wystąpienia na podstawie tych właściwości.</span><span class="sxs-lookup"><span data-stu-id="b1d1f-104">Users can query for instances based on these properties.</span></span> <span data-ttu-id="b1d1f-105">Poniższa lista zawiera niektóre z tych dobrze znanych właściwości:</span><span class="sxs-lookup"><span data-stu-id="b1d1f-105">The following list contains some of these well-known properties:</span></span>  
  
- <span data-ttu-id="b1d1f-106">**Nazwa witryny.**</span><span class="sxs-lookup"><span data-stu-id="b1d1f-106">**Site Name.**</span></span> <span data-ttu-id="b1d1f-107">Nazwa witryny sieci Web zawierającej usługę.</span><span class="sxs-lookup"><span data-stu-id="b1d1f-107">Name of the Web site that contains the service.</span></span>  
  
- <span data-ttu-id="b1d1f-108">**Względna ścieżka aplikacji.**</span><span class="sxs-lookup"><span data-stu-id="b1d1f-108">**Relative Application Path.**</span></span> <span data-ttu-id="b1d1f-109">Ścieżka aplikacji względem witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="b1d1f-109">Path of the application relative to the Web site.</span></span>  
  
- <span data-ttu-id="b1d1f-110">**Względna ścieżka do usługi.**</span><span class="sxs-lookup"><span data-stu-id="b1d1f-110">**Relative Service Path.**</span></span> <span data-ttu-id="b1d1f-111">Ścieżka usługi względem aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b1d1f-111">Path of the service relative to the application.</span></span>  
  
- <span data-ttu-id="b1d1f-112">**Nazwa usługi.**</span><span class="sxs-lookup"><span data-stu-id="b1d1f-112">**Service Name.**</span></span> <span data-ttu-id="b1d1f-113">Nazwa usługi.</span><span class="sxs-lookup"><span data-stu-id="b1d1f-113">Name of the service.</span></span>  
  
- <span data-ttu-id="b1d1f-114">**Przestrzeń nazw usługi.**</span><span class="sxs-lookup"><span data-stu-id="b1d1f-114">**Service Namespace.**</span></span> <span data-ttu-id="b1d1f-115">Nazwa przestrzeni nazw używanej przez usługę.</span><span class="sxs-lookup"><span data-stu-id="b1d1f-115">Name of the namespace that the service uses.</span></span>  
  
- <span data-ttu-id="b1d1f-116">**Bieżąca maszyna.**</span><span class="sxs-lookup"><span data-stu-id="b1d1f-116">**Current Machine.**</span></span>  
  
- <span data-ttu-id="b1d1f-117">**Ostatnia maszyna**.</span><span class="sxs-lookup"><span data-stu-id="b1d1f-117">**Last Machine**.</span></span> <span data-ttu-id="b1d1f-118">Komputer, na którym uruchomiono wystąpienie usługi przepływu pracy po raz ostatni.</span><span class="sxs-lookup"><span data-stu-id="b1d1f-118">The computer on which the workflow service instance ran the last time.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b1d1f-119">W przypadku scenariuszy samodzielnych przy użyciu hosta usługi przepływu pracy są wypełniane tylko ostatnie cztery właściwości.</span><span class="sxs-lookup"><span data-stu-id="b1d1f-119">For self-hosted scenarios using Workflow Service Host, only the last four properties are populated.</span></span> <span data-ttu-id="b1d1f-120">W przypadku scenariuszy aplikacji przepływu pracy tylko Ostatnia właściwość jest wypełniana.</span><span class="sxs-lookup"><span data-stu-id="b1d1f-120">For Workflow Application scenarios, only the last property is populated.</span></span>  
  
 <span data-ttu-id="b1d1f-121">Środowisko uruchomieniowe przepływu pracy dostarcza wartości dla pierwszych trzech właściwości.</span><span class="sxs-lookup"><span data-stu-id="b1d1f-121">The workflow runtime supplies values for the first three properties.</span></span> <span data-ttu-id="b1d1f-122">Host usługi przepływu pracy dostarcza wartość właściwości **Przyczyna wstrzymania** .</span><span class="sxs-lookup"><span data-stu-id="b1d1f-122">The workflow service host supplies the value for the **Suspend Reason** property.</span></span> <span data-ttu-id="b1d1f-123">W przypadku wystąpienia przepływu pracy SQL są przechowywane wartości dla **ostatniej zaktualizowanej właściwości maszyny** .</span><span class="sxs-lookup"><span data-stu-id="b1d1f-123">The SQL Workflow Instance Store itself supplies values for the **Last Updated Machine** property.</span></span>  
  
 <span data-ttu-id="b1d1f-124">Funkcja magazynu wystąpień przepływu pracy SQL umożliwia również określenie właściwości niestandardowych, dla których mają być przechowywane wartości w bazie danych trwałości i które mają być używane w zapytaniach.</span><span class="sxs-lookup"><span data-stu-id="b1d1f-124">The SQL Workflow Instance Store feature also lets you specify the custom properties for which you want to store the values in the persistence database and that you want to use in queries.</span></span> <span data-ttu-id="b1d1f-125">Aby uzyskać więcej informacji na temat promocji niestandardowych, zobacz [rozszerzanie magazynu](store-extensibility.md).</span><span class="sxs-lookup"><span data-stu-id="b1d1f-125">For more information about custom promotions, see [Store Extensibility](store-extensibility.md).</span></span>  
  
## <a name="views"></a><span data-ttu-id="b1d1f-126">Widoki</span><span class="sxs-lookup"><span data-stu-id="b1d1f-126">Views</span></span>  
 <span data-ttu-id="b1d1f-127">Magazyn wystąpień zawiera następujące widoki:</span><span class="sxs-lookup"><span data-stu-id="b1d1f-127">The instance store contains the following views.</span></span> <span data-ttu-id="b1d1f-128">Aby uzyskać więcej informacji, zobacz [schemat bazy danych trwałości](persistence-database-schema.md) .</span><span class="sxs-lookup"><span data-stu-id="b1d1f-128">See [Persistence Database Schema](persistence-database-schema.md) for further details.</span></span>  
  
### <a name="the-instances-view"></a><span data-ttu-id="b1d1f-129">Widok wystąpień</span><span class="sxs-lookup"><span data-stu-id="b1d1f-129">The Instances View</span></span>  
 <span data-ttu-id="b1d1f-130">Widok wystąpienia zawiera następujące pola:</span><span class="sxs-lookup"><span data-stu-id="b1d1f-130">The Instances view contains the following fields:</span></span>  
  
1. <span data-ttu-id="b1d1f-131">**Identyfikator**</span><span class="sxs-lookup"><span data-stu-id="b1d1f-131">**Id**</span></span>  
  
2. <span data-ttu-id="b1d1f-132">**PendingTimer**</span><span class="sxs-lookup"><span data-stu-id="b1d1f-132">**PendingTimer**</span></span>  
  
3. <span data-ttu-id="b1d1f-133">**CreationTime**</span><span class="sxs-lookup"><span data-stu-id="b1d1f-133">**CreationTime**</span></span>  
  
4. <span data-ttu-id="b1d1f-134">**LastUpdatedTime**</span><span class="sxs-lookup"><span data-stu-id="b1d1f-134">**LastUpdatedTime**</span></span>  
  
5. <span data-ttu-id="b1d1f-135">**ServiceDeploymentId**</span><span class="sxs-lookup"><span data-stu-id="b1d1f-135">**ServiceDeploymentId**</span></span>  
  
6. <span data-ttu-id="b1d1f-136">**SuspensionExceptionName**</span><span class="sxs-lookup"><span data-stu-id="b1d1f-136">**SuspensionExceptionName**</span></span>  
  
7. <span data-ttu-id="b1d1f-137">**SuspensionReason**</span><span class="sxs-lookup"><span data-stu-id="b1d1f-137">**SuspensionReason**</span></span>  
  
8. <span data-ttu-id="b1d1f-138">**ActiveBookmarks**</span><span class="sxs-lookup"><span data-stu-id="b1d1f-138">**ActiveBookmarks**</span></span>  
  
9. <span data-ttu-id="b1d1f-139">**CurrentMachine**</span><span class="sxs-lookup"><span data-stu-id="b1d1f-139">**CurrentMachine**</span></span>  
  
10. <span data-ttu-id="b1d1f-140">**LastMachine**</span><span class="sxs-lookup"><span data-stu-id="b1d1f-140">**LastMachine**</span></span>  
  
11. <span data-ttu-id="b1d1f-141">**ExecutionStatus**</span><span class="sxs-lookup"><span data-stu-id="b1d1f-141">**ExecutionStatus**</span></span>  
  
12. <span data-ttu-id="b1d1f-142">**IsInitialized**</span><span class="sxs-lookup"><span data-stu-id="b1d1f-142">**IsInitialized**</span></span>  
  
13. <span data-ttu-id="b1d1f-143">**Issuspended**</span><span class="sxs-lookup"><span data-stu-id="b1d1f-143">**IsSuspended**</span></span>  
  
14. <span data-ttu-id="b1d1f-144">**IsCompleted**</span><span class="sxs-lookup"><span data-stu-id="b1d1f-144">**IsCompleted**</span></span>  
  
15. <span data-ttu-id="b1d1f-145">**EncodingOption**</span><span class="sxs-lookup"><span data-stu-id="b1d1f-145">**EncodingOption**</span></span>  
  
16. <span data-ttu-id="b1d1f-146">**ReadWritePrimitiveDataProperties**</span><span class="sxs-lookup"><span data-stu-id="b1d1f-146">**ReadWritePrimitiveDataProperties**</span></span>  
  
17. <span data-ttu-id="b1d1f-147">**WriteOnlyPrimitiveDataProperties**</span><span class="sxs-lookup"><span data-stu-id="b1d1f-147">**WriteOnlyPrimitiveDataProperties**</span></span>  
  
18. <span data-ttu-id="b1d1f-148">**ReadWriteComplexDataProperties**</span><span class="sxs-lookup"><span data-stu-id="b1d1f-148">**ReadWriteComplexDataProperties**</span></span>  
  
19. <span data-ttu-id="b1d1f-149">**WriteOnlyComplexDataProperties**</span><span class="sxs-lookup"><span data-stu-id="b1d1f-149">**WriteOnlyComplexDataProperties**</span></span>  
  
### <a name="the-servicedeployments-view"></a><span data-ttu-id="b1d1f-150">Widok ServiceDeployments</span><span class="sxs-lookup"><span data-stu-id="b1d1f-150">The ServiceDeployments view</span></span>  
 <span data-ttu-id="b1d1f-151">Widok ServiceDeployments zawiera następujące pola:</span><span class="sxs-lookup"><span data-stu-id="b1d1f-151">The ServiceDeployments view contains the following fields:</span></span>  
  
1. <span data-ttu-id="b1d1f-152">**SiteName**</span><span class="sxs-lookup"><span data-stu-id="b1d1f-152">**SiteName**</span></span>  
  
2. <span data-ttu-id="b1d1f-153">**RelativeServicePath**</span><span class="sxs-lookup"><span data-stu-id="b1d1f-153">**RelativeServicePath**</span></span>  
  
3. <span data-ttu-id="b1d1f-154">**RelativeApplicationPath**</span><span class="sxs-lookup"><span data-stu-id="b1d1f-154">**RelativeApplicationPath**</span></span>  
  
4. <span data-ttu-id="b1d1f-155">**ServiceName**</span><span class="sxs-lookup"><span data-stu-id="b1d1f-155">**ServiceName**</span></span>  
  
5. <span data-ttu-id="b1d1f-156">**Przestrzeń nazw**</span><span class="sxs-lookup"><span data-stu-id="b1d1f-156">**ServiceNamespace**</span></span>  
  
### <a name="the-instancepromotedproperties-view"></a><span data-ttu-id="b1d1f-157">Widok InstancePromotedProperties</span><span class="sxs-lookup"><span data-stu-id="b1d1f-157">The InstancePromotedProperties view</span></span>  
 <span data-ttu-id="b1d1f-158">Widok InstancePromotedProperties zawiera następujące pola.</span><span class="sxs-lookup"><span data-stu-id="b1d1f-158">The InstancePromotedProperties view contains the following fields.</span></span> <span data-ttu-id="b1d1f-159">Aby uzyskać szczegółowe informacje na temat podwyższonych właściwości, zobacz temat [rozszerzalność magazynu](store-extensibility.md) .</span><span class="sxs-lookup"><span data-stu-id="b1d1f-159">For details on promoted properties, see the [Store Extensibility](store-extensibility.md) topic.</span></span>  
  
1. <span data-ttu-id="b1d1f-160">**Identyfikator wystąpienia**</span><span class="sxs-lookup"><span data-stu-id="b1d1f-160">**InstanceId**</span></span>  
  
2. <span data-ttu-id="b1d1f-161">**EncodingOption**</span><span class="sxs-lookup"><span data-stu-id="b1d1f-161">**EncodingOption**</span></span>  
  
3. <span data-ttu-id="b1d1f-162">**Podwyższanie poziomu**</span><span class="sxs-lookup"><span data-stu-id="b1d1f-162">**PromotionName**</span></span>  
  
4. <span data-ttu-id="b1d1f-163">**Wartość #** (zakres pól od **wartość1** do **Value64**).</span><span class="sxs-lookup"><span data-stu-id="b1d1f-163">**Value#** (a range of fields from **Value1** to **Value64**).</span></span>
