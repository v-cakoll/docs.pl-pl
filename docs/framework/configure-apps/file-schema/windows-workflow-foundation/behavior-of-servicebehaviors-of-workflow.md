---
title: "&lt;zachowanie&gt; z &lt;serviceBehaviors&gt; przepływu pracy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 6a4b718a-1b40-4957-935a-f6122819ab3c
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7ce452b97b31f1d552eda481d2f514857372e2d5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltbehaviorgt-of-ltservicebehaviorsgt-of-workflow"></a><span data-ttu-id="4d48b-102">&lt;zachowanie&gt; z &lt;serviceBehaviors&gt; przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="4d48b-102">&lt;behavior&gt; of &lt;serviceBehaviors&gt; of workflow</span></span>
<span data-ttu-id="4d48b-103">**Zachowanie** element zawiera kolekcję ustawień zachowania dla usługi.</span><span class="sxs-lookup"><span data-stu-id="4d48b-103">The **behavior** element contains a collection of settings for the behavior of a service.</span></span> <span data-ttu-id="4d48b-104">Każdy zachowanie jest indeksowany przez jego **nazwa**.</span><span class="sxs-lookup"><span data-stu-id="4d48b-104">Each behavior is indexed by its **name**.</span></span> <span data-ttu-id="4d48b-105">Usługi można połączyć z każdym zachowanie przy użyciu tej nazwy **behaviorConfiguration**atrybutu [ \<punktu końcowego >](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="4d48b-105">Services can link to each behavior through this name using the **behaviorConfiguration**attribute of the [\<endpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) element.</span></span> <span data-ttu-id="4d48b-106">Dzięki temu punktów końcowych udostępnić typowych konfiguracji zachowanie bez ponownego definiowania ustawień.</span><span class="sxs-lookup"><span data-stu-id="4d48b-106">This allows endpoints to share common behavior configurations without redefining the settings.</span></span>  
  
<span data-ttu-id="4d48b-107">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="4d48b-107">\<system.ServiceModel></span></span>  
<span data-ttu-id="4d48b-108">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="4d48b-108">\<behaviors></span></span>  
<span data-ttu-id="4d48b-109">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="4d48b-109">\<serviceBehaviors></span></span>  
<span data-ttu-id="4d48b-110">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="4d48b-110">\<behavior></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d48b-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="4d48b-111">Syntax</span></span>  
  
```xml  
<system.ServiceModel>  
  <behaviors>  
    <serviceBehaviors>  
      <behavior name="String">
        <bufferReceive maxPendingMessagesPerChannel="Integer" />
        <etwTracking profileName="String" />
        <sendMessageChannelCache allowUnsafeCaching="Boolean">
          <channelSettings idleTimeout="TimeSpan" 
                           leaseTimeout="TimeSpan" 
                           maxItemsInCache="Integer" />
          <factorySettings idleTimeout="TimeSpan" 
                           leaseTimeout="TimeSpan" 
                           maxItemsInCache="Integer" />
        </sendMessageChannelCache>
        <sqlWorkflowInstanceStore connectionStringName="String" 
                                  honstLockRenewalPeriod="TimeSpan" 
                                  instanceCompletionAction="DeleteNothing/DeleteAll" 
                                  instanceEncodingAction="None/GZip" 
                                  instanceLockedExceptionAction="NoRetry/BasicRetry/AggressiveRetry" 
                                  runnableInstancesDetectionPeriod="TimeSpan" />
        <workflowIdle timeToPersist="TimeSpan" 
                      timeToUnload="TimeSpan" />
        <workflowUnhandledException action="Abandon/AbandonAndSuspend/Cancel/Terminate" />
      </behavior>
    </serviceBehaviors>  
  </behaviors>  
</system.ServiceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4d48b-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4d48b-112">Attributes and Elements</span></span>  
 <span data-ttu-id="4d48b-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4d48b-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4d48b-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4d48b-114">Attributes</span></span>  
  
|<span data-ttu-id="4d48b-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="4d48b-115">Attribute</span></span>|<span data-ttu-id="4d48b-116">Opis</span><span class="sxs-lookup"><span data-stu-id="4d48b-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4d48b-117">nazwa</span><span class="sxs-lookup"><span data-stu-id="4d48b-117">name</span></span>|<span data-ttu-id="4d48b-118">Unikatowy ciąg, który zawiera nazwę konfiguracji zachowanie.</span><span class="sxs-lookup"><span data-stu-id="4d48b-118">A unique string that contains the configuration name of the behavior.</span></span> <span data-ttu-id="4d48b-119">Ta wartość jest ciągiem zdefiniowanej przez użytkownika, który musi być unikatowy, ponieważ działa jako ciąg identyfikacyjny dla elementu.</span><span class="sxs-lookup"><span data-stu-id="4d48b-119">This value is a user-defined string that must be unique, since it acts as the identification string for the element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4d48b-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4d48b-120">Child Elements</span></span>  
  
|<span data-ttu-id="4d48b-121">Element</span><span class="sxs-lookup"><span data-stu-id="4d48b-121">Element</span></span>|<span data-ttu-id="4d48b-122">Opis</span><span class="sxs-lookup"><span data-stu-id="4d48b-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4d48b-123">\<bufferReceive ></span><span class="sxs-lookup"><span data-stu-id="4d48b-123">\<bufferReceive></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bufferreceive.md)|<span data-ttu-id="4d48b-124">Zachowanie usługi, które umożliwia usługa do użycia buforowanego odbierać przetwarzania, co umożliwia usługi przepływu pracy w celu przetwarzania komunikatów poza kolejnością.</span><span class="sxs-lookup"><span data-stu-id="4d48b-124">A service behavior that enables a service to use buffered receive processing, which enables a workflow service to process out-of-order messages.</span></span>|  
|[<span data-ttu-id="4d48b-125">\<Routing ></span><span class="sxs-lookup"><span data-stu-id="4d48b-125">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md)|<span data-ttu-id="4d48b-126">Zachowanie usługi, która umożliwia korzystanie z funkcji ETW śledzenia przy użyciu usługi <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span><span class="sxs-lookup"><span data-stu-id="4d48b-126">A service behavior that allows a service to utilize ETW tracking using an <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span></span>|  
|[<span data-ttu-id="4d48b-127">\<sendMessageChannelCache ></span><span class="sxs-lookup"><span data-stu-id="4d48b-127">\<sendMessageChannelCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/sendmessagechannelcache.md)|<span data-ttu-id="4d48b-128">Zachowanie usługi umożliwiające dostosowywanie udostępnianie poziomy, ustawienia pamięci podręcznej fabryki kanału i ustawienia pamięci podręcznej kanału dla przepływów pracy, który wysyła wiadomości do punktów końcowych usługi przy użyciu działań dotyczących komunikatów wysyłania pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="4d48b-128">A service behavior that enables the customization of the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using Send messaging activities.</span></span>|  
|[<span data-ttu-id="4d48b-129">\<Obiekt sqlWorkflowInstanceStore ></span><span class="sxs-lookup"><span data-stu-id="4d48b-129">\<sqlWorkflowInstanceStore></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/sqlworkflowinstancestore.md)|<span data-ttu-id="4d48b-130">Zachowanie usługi, która pozwala na skonfigurowanie <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> funkcji, która obsługuje trwałych informacji o stanie dla wystąpienia usługi przepływu pracy w bazie danych programu SQL Server 2005 lub SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="4d48b-130">A service behavior that allows you to configure the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> feature, which supports persisting state information for workflow service instances into an SQL Server 2005 or SQL Server 2008 database.</span></span>|  
|[<span data-ttu-id="4d48b-131">\<workflowIdle ></span><span class="sxs-lookup"><span data-stu-id="4d48b-131">\<workflowIdle></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowidle.md)|<span data-ttu-id="4d48b-132">Zachowanie usługi sterująca po zwolnione wystąpienia bezczynności przepływu pracy i utrwalone.</span><span class="sxs-lookup"><span data-stu-id="4d48b-132">A service behavior that controls when idle workflow instances are unloaded and persisted.</span></span>|  
|[<span data-ttu-id="4d48b-133">\<workflowInstanceManagement ></span><span class="sxs-lookup"><span data-stu-id="4d48b-133">\<workflowInstanceManagement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancemanagement.md)|<span data-ttu-id="4d48b-134">Zachowanie usługi, które umożliwia określenie ustawień, które kontrolują, jak są uruchamiane wystąpienia przepływu pracy, łącznie z trwałości, nieobsługiwanych wyjątków zachowanie i zachowanie bezczynności.</span><span class="sxs-lookup"><span data-stu-id="4d48b-134">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>|  
|[<span data-ttu-id="4d48b-135">\<workflowUnhandledException ></span><span class="sxs-lookup"><span data-stu-id="4d48b-135">\<workflowUnhandledException></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowunhandledexception.md)|<span data-ttu-id="4d48b-136">Zachowanie usługi, który umożliwia określenie Akcja podejmowana po wystąpieniu nieobsługiwanego wyjątku w ramach usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="4d48b-136">A service behavior that enables you to specify the action to take when an unhandled exception occurs within a workflow service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4d48b-137">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4d48b-137">Parent Elements</span></span>  
  
|<span data-ttu-id="4d48b-138">Element</span><span class="sxs-lookup"><span data-stu-id="4d48b-138">Element</span></span>|<span data-ttu-id="4d48b-139">Opis</span><span class="sxs-lookup"><span data-stu-id="4d48b-139">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4d48b-140">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="4d48b-140">\<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/servicebehaviors-of-workflow.md)|<span data-ttu-id="4d48b-141">Kolekcja elementów zachowanie usługi.</span><span class="sxs-lookup"><span data-stu-id="4d48b-141">A collection of service behavior elements.</span></span>|
