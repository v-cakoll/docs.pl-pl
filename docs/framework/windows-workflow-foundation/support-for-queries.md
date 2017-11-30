---
title: "Obsługa zapytań"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 093c22f5-3294-4642-857a-5252233d6796
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d4f338f9ae5cc6967885d0518eb573d9f9535fc2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="support-for-queries"></a><span data-ttu-id="51f10-102">Obsługa zapytań</span><span class="sxs-lookup"><span data-stu-id="51f10-102">Support for Queries</span></span>
<span data-ttu-id="51f10-103">W magazynie wystąpień przepływu pracy SQL rejestruje zestaw dobrze znanych właściwości w magazynie.</span><span class="sxs-lookup"><span data-stu-id="51f10-103">The SQL Workflow Instance Store records a set of well-known properties in the store.</span></span> <span data-ttu-id="51f10-104">Użytkownicy mogą wykonywać kwerendę o wystąpień na podstawie tych właściwości.</span><span class="sxs-lookup"><span data-stu-id="51f10-104">Users can query for instances based on these properties.</span></span> <span data-ttu-id="51f10-105">Poniższa lista zawiera niektóre z tych znanych właściwości:</span><span class="sxs-lookup"><span data-stu-id="51f10-105">The following list contains some of these well-known properties:</span></span>  
  
-   <span data-ttu-id="51f10-106">**Nazwa witryny.**</span><span class="sxs-lookup"><span data-stu-id="51f10-106">**Site Name.**</span></span> <span data-ttu-id="51f10-107">Nazwa witryny sieci Web, który zawiera tę usługę.</span><span class="sxs-lookup"><span data-stu-id="51f10-107">Name of the Web site that contains the service.</span></span>  
  
-   <span data-ttu-id="51f10-108">**Ścieżka względna aplikacji.**</span><span class="sxs-lookup"><span data-stu-id="51f10-108">**Relative Application Path.**</span></span> <span data-ttu-id="51f10-109">Ścieżka aplikacji względem witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="51f10-109">Path of the application relative to the Web site.</span></span>  
  
-   <span data-ttu-id="51f10-110">**Ścieżka względna usługi.**</span><span class="sxs-lookup"><span data-stu-id="51f10-110">**Relative Service Path.**</span></span> <span data-ttu-id="51f10-111">Ścieżka usługi względem aplikacji.</span><span class="sxs-lookup"><span data-stu-id="51f10-111">Path of the service relative to the application.</span></span>  
  
-   <span data-ttu-id="51f10-112">**Nazwa usługi.**</span><span class="sxs-lookup"><span data-stu-id="51f10-112">**Service Name.**</span></span> <span data-ttu-id="51f10-113">Nazwa usługi.</span><span class="sxs-lookup"><span data-stu-id="51f10-113">Name of the service.</span></span>  
  
-   <span data-ttu-id="51f10-114">**Usługa Namespace.**</span><span class="sxs-lookup"><span data-stu-id="51f10-114">**Service Namespace.**</span></span> <span data-ttu-id="51f10-115">Nazwa przestrzeni nazw, która korzysta z usługi.</span><span class="sxs-lookup"><span data-stu-id="51f10-115">Name of the namespace that the service uses.</span></span>  
  
-   <span data-ttu-id="51f10-116">**Bieżącego komputera.**</span><span class="sxs-lookup"><span data-stu-id="51f10-116">**Current Machine.**</span></span>  
  
-   <span data-ttu-id="51f10-117">**Ostatni maszyny**.</span><span class="sxs-lookup"><span data-stu-id="51f10-117">**Last Machine**.</span></span> <span data-ttu-id="51f10-118">Komputer, na którym został uruchomiony podczas ostatniego wystąpienia usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="51f10-118">The computer on which the workflow service instance ran the last time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="51f10-119">W przypadku scenariuszy hostowania samoobsługowego przy użyciu hosta usługi przepływu pracy są wypełniane tylko cztery ostatnie właściwości.</span><span class="sxs-lookup"><span data-stu-id="51f10-119">For self-hosted scenarios using Workflow Service Host, only the last four properties are populated.</span></span> <span data-ttu-id="51f10-120">W przypadku scenariuszy aplikacji przepływu pracy jest wypełniana tylko ostatnich właściwości.</span><span class="sxs-lookup"><span data-stu-id="51f10-120">For Workflow Application scenarios, only the last property is populated.</span></span>  
  
 <span data-ttu-id="51f10-121">Środowiska uruchomieniowego przepływu pracy, dostarcza wartości dla właściwości pierwsze trzy.</span><span class="sxs-lookup"><span data-stu-id="51f10-121">The workflow runtime supplies values for the first three properties.</span></span> <span data-ttu-id="51f10-122">Hosta usługi przepływu pracy, dostarcza wartość **zawiesić Przyczyna** właściwości.</span><span class="sxs-lookup"><span data-stu-id="51f10-122">The workflow service host supplies the value for the **Suspend Reason** property.</span></span> <span data-ttu-id="51f10-123">Samego magazynu wystąpienia przepływu pracy SQL dostarcza wartości dla **ostatnia maszyna zaktualizowane** właściwości.</span><span class="sxs-lookup"><span data-stu-id="51f10-123">The SQL Workflow Instance Store itself supplies values for the **Last Updated Machine** property.</span></span>  
  
 <span data-ttu-id="51f10-124">Funkcja magazynu wystąpienia przepływu pracy SQL umożliwia także określić, czy właściwości niestandardowe, dla których mają być przechowywane w bazie danych trwałości i wartości mają być używane w zapytaniach.</span><span class="sxs-lookup"><span data-stu-id="51f10-124">The SQL Workflow Instance Store feature also lets you specify the custom properties for which you want to store the values in the persistence database and that you want to use in queries.</span></span> <span data-ttu-id="51f10-125">Aby uzyskać więcej informacji o promocjach niestandardowych, zobacz [rozszerzalności magazynu](../../../docs/framework/windows-workflow-foundation/store-extensibility.md).</span><span class="sxs-lookup"><span data-stu-id="51f10-125">For more information about custom promotions, see [Store Extensibility](../../../docs/framework/windows-workflow-foundation/store-extensibility.md).</span></span>  
  
## <a name="views"></a><span data-ttu-id="51f10-126">Widoki</span><span class="sxs-lookup"><span data-stu-id="51f10-126">Views</span></span>  
 <span data-ttu-id="51f10-127">W magazynie wystąpień zawiera następujące widoki.</span><span class="sxs-lookup"><span data-stu-id="51f10-127">The instance store contains the following views.</span></span> <span data-ttu-id="51f10-128">Zobacz [schematu bazy danych trwałości](../../../docs/framework/windows-workflow-foundation/persistence-database-schema.md) uzyskać więcej szczegółowych informacji.</span><span class="sxs-lookup"><span data-stu-id="51f10-128">See [Persistence Database Schema](../../../docs/framework/windows-workflow-foundation/persistence-database-schema.md) for further details.</span></span>  
  
### <a name="the-instances-view"></a><span data-ttu-id="51f10-129">Widok wystąpień</span><span class="sxs-lookup"><span data-stu-id="51f10-129">The Instances View</span></span>  
 <span data-ttu-id="51f10-130">Widok wystąpień zawiera następujące pola:</span><span class="sxs-lookup"><span data-stu-id="51f10-130">The Instances view contains the following fields:</span></span>  
  
1.  <span data-ttu-id="51f10-131">**Identyfikator**</span><span class="sxs-lookup"><span data-stu-id="51f10-131">**Id**</span></span>  
  
2.  <span data-ttu-id="51f10-132">**PendingTimer**</span><span class="sxs-lookup"><span data-stu-id="51f10-132">**PendingTimer**</span></span>  
  
3.  <span data-ttu-id="51f10-133">**CreationTime**</span><span class="sxs-lookup"><span data-stu-id="51f10-133">**CreationTime**</span></span>  
  
4.  <span data-ttu-id="51f10-134">**LastUpdatedTime**</span><span class="sxs-lookup"><span data-stu-id="51f10-134">**LastUpdatedTime**</span></span>  
  
5.  <span data-ttu-id="51f10-135">**ServiceDeploymentId**</span><span class="sxs-lookup"><span data-stu-id="51f10-135">**ServiceDeploymentId**</span></span>  
  
6.  <span data-ttu-id="51f10-136">**SuspensionExceptionName**</span><span class="sxs-lookup"><span data-stu-id="51f10-136">**SuspensionExceptionName**</span></span>  
  
7.  <span data-ttu-id="51f10-137">**SuspensionReason**</span><span class="sxs-lookup"><span data-stu-id="51f10-137">**SuspensionReason**</span></span>  
  
8.  <span data-ttu-id="51f10-138">**ActiveBookmarks**</span><span class="sxs-lookup"><span data-stu-id="51f10-138">**ActiveBookmarks**</span></span>  
  
9. <span data-ttu-id="51f10-139">**CurrentMachine**</span><span class="sxs-lookup"><span data-stu-id="51f10-139">**CurrentMachine**</span></span>  
  
10. <span data-ttu-id="51f10-140">**LastMachine**</span><span class="sxs-lookup"><span data-stu-id="51f10-140">**LastMachine**</span></span>  
  
11. <span data-ttu-id="51f10-141">**ExecutionStatus**</span><span class="sxs-lookup"><span data-stu-id="51f10-141">**ExecutionStatus**</span></span>  
  
12. <span data-ttu-id="51f10-142">**IsInitialized**</span><span class="sxs-lookup"><span data-stu-id="51f10-142">**IsInitialized**</span></span>  
  
13. <span data-ttu-id="51f10-143">**IsSuspended**</span><span class="sxs-lookup"><span data-stu-id="51f10-143">**IsSuspended**</span></span>  
  
14. <span data-ttu-id="51f10-144">**IsCompleted**</span><span class="sxs-lookup"><span data-stu-id="51f10-144">**IsCompleted**</span></span>  
  
15. <span data-ttu-id="51f10-145">**EncodingOption**</span><span class="sxs-lookup"><span data-stu-id="51f10-145">**EncodingOption**</span></span>  
  
16. <span data-ttu-id="51f10-146">**ReadWritePrimitiveDataProperties**</span><span class="sxs-lookup"><span data-stu-id="51f10-146">**ReadWritePrimitiveDataProperties**</span></span>  
  
17. <span data-ttu-id="51f10-147">**WriteOnlyPrimitiveDataProperties**</span><span class="sxs-lookup"><span data-stu-id="51f10-147">**WriteOnlyPrimitiveDataProperties**</span></span>  
  
18. <span data-ttu-id="51f10-148">**ReadWriteComplexDataProperties**</span><span class="sxs-lookup"><span data-stu-id="51f10-148">**ReadWriteComplexDataProperties**</span></span>  
  
19. <span data-ttu-id="51f10-149">**WriteOnlyComplexDataProperties**</span><span class="sxs-lookup"><span data-stu-id="51f10-149">**WriteOnlyComplexDataProperties**</span></span>  
  
### <a name="the-servicedeployments-view"></a><span data-ttu-id="51f10-150">Widok ServiceDeployments</span><span class="sxs-lookup"><span data-stu-id="51f10-150">The ServiceDeployments view</span></span>  
 <span data-ttu-id="51f10-151">Widok ServiceDeployments zawiera następujące pola:</span><span class="sxs-lookup"><span data-stu-id="51f10-151">The ServiceDeployments view contains the following fields:</span></span>  
  
1.  <span data-ttu-id="51f10-152">**Nazwa witryny**</span><span class="sxs-lookup"><span data-stu-id="51f10-152">**SiteName**</span></span>  
  
2.  <span data-ttu-id="51f10-153">**RelativeServicePath**</span><span class="sxs-lookup"><span data-stu-id="51f10-153">**RelativeServicePath**</span></span>  
  
3.  <span data-ttu-id="51f10-154">**RelativeApplicationPath**</span><span class="sxs-lookup"><span data-stu-id="51f10-154">**RelativeApplicationPath**</span></span>  
  
4.  <span data-ttu-id="51f10-155">**ServiceName**</span><span class="sxs-lookup"><span data-stu-id="51f10-155">**ServiceName**</span></span>  
  
5.  <span data-ttu-id="51f10-156">**ServiceNamespace**</span><span class="sxs-lookup"><span data-stu-id="51f10-156">**ServiceNamespace**</span></span>  
  
### <a name="the-instancepromotedproperties-view"></a><span data-ttu-id="51f10-157">Widok InstancePromotedProperties</span><span class="sxs-lookup"><span data-stu-id="51f10-157">The InstancePromotedProperties view</span></span>  
 <span data-ttu-id="51f10-158">Widok InstancePromotedProperties zawiera następujące pola.</span><span class="sxs-lookup"><span data-stu-id="51f10-158">The InstancePromotedProperties view contains the following fields.</span></span> <span data-ttu-id="51f10-159">Aby uzyskać więcej informacji na temat awansowanej właściwości, zobacz [rozszerzalności magazynu](../../../docs/framework/windows-workflow-foundation/store-extensibility.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="51f10-159">For details on promoted properties, see the [Store Extensibility](../../../docs/framework/windows-workflow-foundation/store-extensibility.md) topic.</span></span>  
  
1.  <span data-ttu-id="51f10-160">**Identyfikator wystąpienia**</span><span class="sxs-lookup"><span data-stu-id="51f10-160">**InstanceId**</span></span>  
  
2.  <span data-ttu-id="51f10-161">**EncodingOption**</span><span class="sxs-lookup"><span data-stu-id="51f10-161">**EncodingOption**</span></span>  
  
3.  <span data-ttu-id="51f10-162">**PromotionName**</span><span class="sxs-lookup"><span data-stu-id="51f10-162">**PromotionName**</span></span>  
  
4.  <span data-ttu-id="51f10-163">**Wartość #** (zakresu pola z **wartość1** do **Value64**).</span><span class="sxs-lookup"><span data-stu-id="51f10-163">**Value#** (a range of fields from **Value1** to **Value64**).</span></span>
