---
title: <behavior><serviceBehaviors> przepływu pracy
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 6a4b718a-1b40-4957-935a-f6122819ab3c
ms.openlocfilehash: 65bde45ffdd4af166d5b44308162c23257659802
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398890"
---
# <a name="behavior-of-servicebehaviors-of-workflow"></a><span data-ttu-id="e8dff-102">\<> \<zachowania > przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="e8dff-102">\<behavior> of \<serviceBehaviors> of workflow</span></span>
<span data-ttu-id="e8dff-103">Element **Behavior** zawiera kolekcję ustawień zachowania usługi.</span><span class="sxs-lookup"><span data-stu-id="e8dff-103">The **behavior** element contains a collection of settings for the behavior of a service.</span></span> <span data-ttu-id="e8dff-104">Każde zachowanie jest indeksowane według jego **nazwy**.</span><span class="sxs-lookup"><span data-stu-id="e8dff-104">Each behavior is indexed by its **name**.</span></span> <span data-ttu-id="e8dff-105">Usługi mogą łączyć się z każdym zachowaniem za pomocą tej nazwy przy użyciu atrybutu [ \<behaviorConfiguration elementu Endpoint >](../wcf/endpoint-element.md) .</span><span class="sxs-lookup"><span data-stu-id="e8dff-105">Services can link to each behavior through this name using the **behaviorConfiguration** attribute of the [\<endpoint>](../wcf/endpoint-element.md) element.</span></span> <span data-ttu-id="e8dff-106">Dzięki temu punktów końcowych udostępnić typowych konfiguracji zachowanie bez ponownego definiowania ustawień.</span><span class="sxs-lookup"><span data-stu-id="e8dff-106">This allows endpoints to share common behavior configurations without redefining the settings.</span></span>  
  
<span data-ttu-id="e8dff-107">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e8dff-107">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e8dff-108">&nbsp;&nbsp;[ **\<systemami. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="e8dff-108">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="e8dff-109">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowań**](behaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="e8dff-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)</span></span>\
<span data-ttu-id="e8dff-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> serviceBehaviors**](servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="e8dff-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="e8dff-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> zachowania**</span><span class="sxs-lookup"><span data-stu-id="e8dff-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<behavior>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8dff-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="e8dff-112">Syntax</span></span>  
  
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
                                  hostLockRenewalPeriod="TimeSpan" 
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e8dff-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e8dff-113">Attributes and Elements</span></span>  
 <span data-ttu-id="e8dff-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e8dff-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e8dff-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e8dff-115">Attributes</span></span>  
  
|<span data-ttu-id="e8dff-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="e8dff-116">Attribute</span></span>|<span data-ttu-id="e8dff-117">Opis</span><span class="sxs-lookup"><span data-stu-id="e8dff-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e8dff-118">nazwa</span><span class="sxs-lookup"><span data-stu-id="e8dff-118">name</span></span>|<span data-ttu-id="e8dff-119">Unikatowy ciąg, który zawiera nazwę konfiguracji zachowanie.</span><span class="sxs-lookup"><span data-stu-id="e8dff-119">A unique string that contains the configuration name of the behavior.</span></span> <span data-ttu-id="e8dff-120">Ta wartość jest ciągiem zdefiniowanej przez użytkownika, który musi być unikatowy, ponieważ działa jako ciąg identyfikacyjny dla elementu.</span><span class="sxs-lookup"><span data-stu-id="e8dff-120">This value is a user-defined string that must be unique, since it acts as the identification string for the element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e8dff-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e8dff-121">Child Elements</span></span>  
  
|<span data-ttu-id="e8dff-122">Element</span><span class="sxs-lookup"><span data-stu-id="e8dff-122">Element</span></span>|<span data-ttu-id="e8dff-123">Opis</span><span class="sxs-lookup"><span data-stu-id="e8dff-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e8dff-124">\<bufferReceive ></span><span class="sxs-lookup"><span data-stu-id="e8dff-124">\<bufferReceive></span></span>](bufferreceive.md)|<span data-ttu-id="e8dff-125">Zachowanie usługi, które umożliwia usługa do użycia buforowanego odbierać przetwarzania, co umożliwia usługi przepływu pracy w celu przetwarzania komunikatów poza kolejnością.</span><span class="sxs-lookup"><span data-stu-id="e8dff-125">A service behavior that enables a service to use buffered receive processing, which enables a workflow service to process out-of-order messages.</span></span>|  
|[<span data-ttu-id="e8dff-126">\<> routingu</span><span class="sxs-lookup"><span data-stu-id="e8dff-126">\<routing></span></span>](../wcf/routing-of-servicebehavior.md)|<span data-ttu-id="e8dff-127">Zachowanie usługi, które umożliwia usłudze korzystanie z funkcji śledzenia ETW przy użyciu <xref:System.Activities.Tracking.EtwTrackingParticipant>programu.</span><span class="sxs-lookup"><span data-stu-id="e8dff-127">A service behavior that allows a service to utilize ETW tracking using an <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span></span>|  
|[<span data-ttu-id="e8dff-128">\<sendMessageChannelCache></span><span class="sxs-lookup"><span data-stu-id="e8dff-128">\<sendMessageChannelCache></span></span>](sendmessagechannelcache.md)|<span data-ttu-id="e8dff-129">Zachowanie usługi, które umożliwia dostosowanie poziomów udostępniania pamięci podręcznej, ustawień pamięci podręcznej fabryki kanałów oraz ustawień pamięci podręcznej kanału dla przepływów pracy, które wysyłają komunikaty do punktów końcowych usługi przy użyciu działań wysyłania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="e8dff-129">A service behavior that enables the customization of the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using Send messaging activities.</span></span>|  
|[<span data-ttu-id="e8dff-130">\<sqlWorkflowInstanceStore></span><span class="sxs-lookup"><span data-stu-id="e8dff-130">\<sqlWorkflowInstanceStore></span></span>](sqlworkflowinstancestore.md)|<span data-ttu-id="e8dff-131">Zachowanie usługi, które umożliwia skonfigurowanie <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> funkcji, która obsługuje utrwalanie informacji o stanie dla wystąpień usługi przepływu pracy w bazie danych SQL Server 2005 lub SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="e8dff-131">A service behavior that allows you to configure the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> feature, which supports persisting state information for workflow service instances into an SQL Server 2005 or SQL Server 2008 database.</span></span>|  
|[<span data-ttu-id="e8dff-132">\<workflowIdle></span><span class="sxs-lookup"><span data-stu-id="e8dff-132">\<workflowIdle></span></span>](workflowidle.md)|<span data-ttu-id="e8dff-133">Zachowanie usługi sterująca po zwolnione wystąpienia bezczynności przepływu pracy i utrwalone.</span><span class="sxs-lookup"><span data-stu-id="e8dff-133">A service behavior that controls when idle workflow instances are unloaded and persisted.</span></span>|  
|[<span data-ttu-id="e8dff-134">\<workflowInstanceManagement ></span><span class="sxs-lookup"><span data-stu-id="e8dff-134">\<workflowInstanceManagement></span></span>](workflowinstancemanagement.md)|<span data-ttu-id="e8dff-135">Zachowanie usługi, które umożliwia określenie ustawień, które kontrolują, jak są uruchamiane wystąpienia przepływu pracy, łącznie z trwałości, nieobsługiwanych wyjątków zachowanie i zachowanie bezczynności.</span><span class="sxs-lookup"><span data-stu-id="e8dff-135">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>|  
|[<span data-ttu-id="e8dff-136">\<workflowUnhandledException></span><span class="sxs-lookup"><span data-stu-id="e8dff-136">\<workflowUnhandledException></span></span>](workflowunhandledexception.md)|<span data-ttu-id="e8dff-137">Zachowanie usługi, który umożliwia określenie Akcja podejmowana po wystąpieniu nieobsługiwanego wyjątku w ramach usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="e8dff-137">A service behavior that enables you to specify the action to take when an unhandled exception occurs within a workflow service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e8dff-138">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e8dff-138">Parent Elements</span></span>  
  
|<span data-ttu-id="e8dff-139">Element</span><span class="sxs-lookup"><span data-stu-id="e8dff-139">Element</span></span>|<span data-ttu-id="e8dff-140">Opis</span><span class="sxs-lookup"><span data-stu-id="e8dff-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e8dff-141">\<> serviceBehaviors</span><span class="sxs-lookup"><span data-stu-id="e8dff-141">\<serviceBehaviors></span></span>](servicebehaviors-of-workflow.md)|<span data-ttu-id="e8dff-142">Kolekcja elementów zachowanie usługi.</span><span class="sxs-lookup"><span data-stu-id="e8dff-142">A collection of service behavior elements.</span></span>|
