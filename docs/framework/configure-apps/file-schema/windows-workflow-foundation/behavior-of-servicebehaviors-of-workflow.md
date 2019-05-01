---
title: <behavior> z <serviceBehaviors> przepływu pracy
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 6a4b718a-1b40-4957-935a-f6122819ab3c
ms.openlocfilehash: 09bd54f4a7d56dc1215b1acd36ff131ba4cba12c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790315"
---
# <a name="behavior-of-servicebehaviors-of-workflow"></a><span data-ttu-id="034b9-102">\<zachowanie > z \<serviceBehaviors > przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="034b9-102">\<behavior> of \<serviceBehaviors> of workflow</span></span>
<span data-ttu-id="034b9-103">**Zachowanie** element zawiera zbiór ustawień dotyczących zachowania usługi.</span><span class="sxs-lookup"><span data-stu-id="034b9-103">The **behavior** element contains a collection of settings for the behavior of a service.</span></span> <span data-ttu-id="034b9-104">Każde działanie jest indeksowane według jego **nazwa**.</span><span class="sxs-lookup"><span data-stu-id="034b9-104">Each behavior is indexed by its **name**.</span></span> <span data-ttu-id="034b9-105">Usługi można połączyć każdego zachowanie za pomocą tej nazwy **behaviorConfiguration** atrybutu [ \<punktu końcowego >](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="034b9-105">Services can link to each behavior through this name using the **behaviorConfiguration** attribute of the [\<endpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) element.</span></span> <span data-ttu-id="034b9-106">Dzięki temu punktów końcowych udostępnić typowych konfiguracji zachowanie bez ponownego definiowania ustawień.</span><span class="sxs-lookup"><span data-stu-id="034b9-106">This allows endpoints to share common behavior configurations without redefining the settings.</span></span>  
  
<span data-ttu-id="034b9-107">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="034b9-107">\<system.ServiceModel></span></span>  
<span data-ttu-id="034b9-108">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="034b9-108">\<behaviors></span></span>  
<span data-ttu-id="034b9-109">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="034b9-109">\<serviceBehaviors></span></span>  
<span data-ttu-id="034b9-110">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="034b9-110">\<behavior></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="034b9-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="034b9-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="034b9-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="034b9-112">Attributes and Elements</span></span>  
 <span data-ttu-id="034b9-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="034b9-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="034b9-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="034b9-114">Attributes</span></span>  
  
|<span data-ttu-id="034b9-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="034b9-115">Attribute</span></span>|<span data-ttu-id="034b9-116">Opis</span><span class="sxs-lookup"><span data-stu-id="034b9-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="034b9-117">nazwa</span><span class="sxs-lookup"><span data-stu-id="034b9-117">name</span></span>|<span data-ttu-id="034b9-118">Unikatowy ciąg, który zawiera nazwę konfiguracji zachowanie.</span><span class="sxs-lookup"><span data-stu-id="034b9-118">A unique string that contains the configuration name of the behavior.</span></span> <span data-ttu-id="034b9-119">Ta wartość jest ciągiem zdefiniowanej przez użytkownika, który musi być unikatowy, ponieważ działa jako ciąg identyfikacyjny dla elementu.</span><span class="sxs-lookup"><span data-stu-id="034b9-119">This value is a user-defined string that must be unique, since it acts as the identification string for the element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="034b9-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="034b9-120">Child Elements</span></span>  
  
|<span data-ttu-id="034b9-121">Element</span><span class="sxs-lookup"><span data-stu-id="034b9-121">Element</span></span>|<span data-ttu-id="034b9-122">Opis</span><span class="sxs-lookup"><span data-stu-id="034b9-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="034b9-123">\<bufferReceive></span><span class="sxs-lookup"><span data-stu-id="034b9-123">\<bufferReceive></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bufferreceive.md)|<span data-ttu-id="034b9-124">Zachowanie usługi, które umożliwia usługa do użycia buforowanego odbierać przetwarzania, co umożliwia usługi przepływu pracy w celu przetwarzania komunikatów poza kolejnością.</span><span class="sxs-lookup"><span data-stu-id="034b9-124">A service behavior that enables a service to use buffered receive processing, which enables a workflow service to process out-of-order messages.</span></span>|  
|[<span data-ttu-id="034b9-125">\<routing></span><span class="sxs-lookup"><span data-stu-id="034b9-125">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md)|<span data-ttu-id="034b9-126">Zachowanie usługi, która umożliwia korzystanie z funkcji ETW śledzenia za pomocą <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span><span class="sxs-lookup"><span data-stu-id="034b9-126">A service behavior that allows a service to utilize ETW tracking using an <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span></span>|  
|[<span data-ttu-id="034b9-127">\<sendMessageChannelCache></span><span class="sxs-lookup"><span data-stu-id="034b9-127">\<sendMessageChannelCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/sendmessagechannelcache.md)|<span data-ttu-id="034b9-128">Zachowanie usługi, który umożliwia dostosowywania pamięci podręcznej udostępnianie poziomy, ustawienia pamięci podręcznej fabryki kanału i ustawienia pamięci podręcznej kanału do wysyłania wiadomości do punktów końcowych usługi za pomocą wysyłania wiadomości działania przepływami pracy.</span><span class="sxs-lookup"><span data-stu-id="034b9-128">A service behavior that enables the customization of the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using Send messaging activities.</span></span>|  
|[<span data-ttu-id="034b9-129">\<sqlWorkflowInstanceStore></span><span class="sxs-lookup"><span data-stu-id="034b9-129">\<sqlWorkflowInstanceStore></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/sqlworkflowinstancestore.md)|<span data-ttu-id="034b9-130">Zachowanie usługi, które pozwala na skonfigurowanie <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> funkcji, która obsługuje utrwalanie informacji o stanie dla wystąpień usługi przepływu pracy w bazie danych programu SQL Server 2005 lub SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="034b9-130">A service behavior that allows you to configure the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> feature, which supports persisting state information for workflow service instances into an SQL Server 2005 or SQL Server 2008 database.</span></span>|  
|[<span data-ttu-id="034b9-131">\<workflowIdle></span><span class="sxs-lookup"><span data-stu-id="034b9-131">\<workflowIdle></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowidle.md)|<span data-ttu-id="034b9-132">Zachowanie usługi sterująca po zwolnione wystąpienia bezczynności przepływu pracy i utrwalone.</span><span class="sxs-lookup"><span data-stu-id="034b9-132">A service behavior that controls when idle workflow instances are unloaded and persisted.</span></span>|  
|[<span data-ttu-id="034b9-133">\<workflowInstanceManagement></span><span class="sxs-lookup"><span data-stu-id="034b9-133">\<workflowInstanceManagement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancemanagement.md)|<span data-ttu-id="034b9-134">Zachowanie usługi, które umożliwia określenie ustawień, które kontrolują, jak są uruchamiane wystąpienia przepływu pracy, łącznie z trwałości, nieobsługiwanych wyjątków zachowanie i zachowanie bezczynności.</span><span class="sxs-lookup"><span data-stu-id="034b9-134">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>|  
|[<span data-ttu-id="034b9-135">\<workflowUnhandledException></span><span class="sxs-lookup"><span data-stu-id="034b9-135">\<workflowUnhandledException></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowunhandledexception.md)|<span data-ttu-id="034b9-136">Zachowanie usługi, który umożliwia określenie Akcja podejmowana po wystąpieniu nieobsługiwanego wyjątku w ramach usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="034b9-136">A service behavior that enables you to specify the action to take when an unhandled exception occurs within a workflow service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="034b9-137">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="034b9-137">Parent Elements</span></span>  
  
|<span data-ttu-id="034b9-138">Element</span><span class="sxs-lookup"><span data-stu-id="034b9-138">Element</span></span>|<span data-ttu-id="034b9-139">Opis</span><span class="sxs-lookup"><span data-stu-id="034b9-139">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="034b9-140">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="034b9-140">\<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/servicebehaviors-of-workflow.md)|<span data-ttu-id="034b9-141">Kolekcja elementów zachowanie usługi.</span><span class="sxs-lookup"><span data-stu-id="034b9-141">A collection of service behavior elements.</span></span>|
