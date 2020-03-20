---
title: <behavior>przepływu <serviceBehaviors> pracy
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 6a4b718a-1b40-4957-935a-f6122819ab3c
ms.openlocfilehash: 071cff8e9f6ec3fa0546a07d19160869d8b43f60
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152323"
---
# <a name="behavior-of-servicebehaviors-of-workflow"></a><span data-ttu-id="f1f28-102">\<zachowanie> \<usługZachowatości> przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="f1f28-102">\<behavior> of \<serviceBehaviors> of workflow</span></span>
<span data-ttu-id="f1f28-103">Element **zachowania** zawiera zbiór ustawień zachowania usługi.</span><span class="sxs-lookup"><span data-stu-id="f1f28-103">The **behavior** element contains a collection of settings for the behavior of a service.</span></span> <span data-ttu-id="f1f28-104">Każde zachowanie jest indeksowane według jego **nazwy**.</span><span class="sxs-lookup"><span data-stu-id="f1f28-104">Each behavior is indexed by its **name**.</span></span> <span data-ttu-id="f1f28-105">Usługi można połączyć się z każdego zachowania za pomocą tego atrybutu **behaviorConfiguration** [ \<elementu>.](../wcf/endpoint-element.md)</span><span class="sxs-lookup"><span data-stu-id="f1f28-105">Services can link to each behavior through this name using the **behaviorConfiguration** attribute of the [\<endpoint>](../wcf/endpoint-element.md) element.</span></span> <span data-ttu-id="f1f28-106">Dzięki temu punktów końcowych udostępnić typowych konfiguracji zachowanie bez ponownego definiowania ustawień.</span><span class="sxs-lookup"><span data-stu-id="f1f28-106">This allows endpoints to share common behavior configurations without redefining the settings.</span></span>  
  
<span data-ttu-id="f1f28-107">[**\<>konfiguracyjne**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f1f28-107">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f1f28-108">&nbsp;&nbsp;[**\<System.>z>**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="f1f28-108">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="f1f28-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<zachowania>**](behaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="f1f28-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)</span></span>\
<span data-ttu-id="f1f28-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<usługiZachowady>**](servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="f1f28-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="f1f28-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>zachowania**</span><span class="sxs-lookup"><span data-stu-id="f1f28-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<behavior>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1f28-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="f1f28-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f1f28-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f1f28-113">Attributes and Elements</span></span>  
 <span data-ttu-id="f1f28-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f1f28-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f1f28-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f1f28-115">Attributes</span></span>  
  
|<span data-ttu-id="f1f28-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="f1f28-116">Attribute</span></span>|<span data-ttu-id="f1f28-117">Opis</span><span class="sxs-lookup"><span data-stu-id="f1f28-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f1f28-118">name</span><span class="sxs-lookup"><span data-stu-id="f1f28-118">name</span></span>|<span data-ttu-id="f1f28-119">Unikatowy ciąg, który zawiera nazwę konfiguracji zachowanie.</span><span class="sxs-lookup"><span data-stu-id="f1f28-119">A unique string that contains the configuration name of the behavior.</span></span> <span data-ttu-id="f1f28-120">Ta wartość jest ciągiem zdefiniowanej przez użytkownika, który musi być unikatowy, ponieważ działa jako ciąg identyfikacyjny dla elementu.</span><span class="sxs-lookup"><span data-stu-id="f1f28-120">This value is a user-defined string that must be unique, since it acts as the identification string for the element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f1f28-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f1f28-121">Child Elements</span></span>  
  
|<span data-ttu-id="f1f28-122">Element</span><span class="sxs-lookup"><span data-stu-id="f1f28-122">Element</span></span>|<span data-ttu-id="f1f28-123">Opis</span><span class="sxs-lookup"><span data-stu-id="f1f28-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f1f28-124">\<buforRecetywne></span><span class="sxs-lookup"><span data-stu-id="f1f28-124">\<bufferReceive></span></span>](bufferreceive.md)|<span data-ttu-id="f1f28-125">Zachowanie usługi, które umożliwia usługa do użycia buforowanego odbierać przetwarzania, co umożliwia usługi przepływu pracy w celu przetwarzania komunikatów poza kolejnością.</span><span class="sxs-lookup"><span data-stu-id="f1f28-125">A service behavior that enables a service to use buffered receive processing, which enables a workflow service to process out-of-order messages.</span></span>|  
|[<span data-ttu-id="f1f28-126">\<>routingu</span><span class="sxs-lookup"><span data-stu-id="f1f28-126">\<routing></span></span>](../wcf/routing-of-servicebehavior.md)|<span data-ttu-id="f1f28-127">Zachowanie usługi, które pozwala usłudze korzystać <xref:System.Activities.Tracking.EtwTrackingParticipant>ze śledzenia ETW za pomocą pliku .</span><span class="sxs-lookup"><span data-stu-id="f1f28-127">A service behavior that allows a service to utilize ETW tracking using an <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span></span>|  
|[<span data-ttu-id="f1f28-128">\<>sendMessageChannelCache</span><span class="sxs-lookup"><span data-stu-id="f1f28-128">\<sendMessageChannelCache></span></span>](sendmessagechannelcache.md)|<span data-ttu-id="f1f28-129">Zachowanie usługi, która umożliwia dostosowanie poziomów udostępniania pamięci podręcznej, ustawienia pamięci podręcznej fabryki kanału i ustawienia pamięci podręcznej kanału dla przepływów pracy, które wysyłają wiadomości do punktów końcowych usługi przy użyciu wysyłania działań obsługi wiadomości.</span><span class="sxs-lookup"><span data-stu-id="f1f28-129">A service behavior that enables the customization of the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using Send messaging activities.</span></span>|  
|[<span data-ttu-id="f1f28-130">\<sqlWorkflowInstanceStore></span><span class="sxs-lookup"><span data-stu-id="f1f28-130">\<sqlWorkflowInstanceStore></span></span>](sqlworkflowinstancestore.md)|<span data-ttu-id="f1f28-131">Zachowanie usługi, które umożliwia skonfigurowanie <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> funkcji, która obsługuje utrwalanie informacji o stanie wystąpień usługi przepływu pracy w bazie danych PROGRAMU SQL Server 2005 lub SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="f1f28-131">A service behavior that allows you to configure the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> feature, which supports persisting state information for workflow service instances into an SQL Server 2005 or SQL Server 2008 database.</span></span>|  
|[<span data-ttu-id="f1f28-132">\<>przepływu pracyIdle</span><span class="sxs-lookup"><span data-stu-id="f1f28-132">\<workflowIdle></span></span>](workflowidle.md)|<span data-ttu-id="f1f28-133">Zachowanie usługi sterująca po zwolnione wystąpienia bezczynności przepływu pracy i utrwalone.</span><span class="sxs-lookup"><span data-stu-id="f1f28-133">A service behavior that controls when idle workflow instances are unloaded and persisted.</span></span>|  
|[<span data-ttu-id="f1f28-134">\<>zarządzanie przepływem pracy</span><span class="sxs-lookup"><span data-stu-id="f1f28-134">\<workflowInstanceManagement></span></span>](workflowinstancemanagement.md)|<span data-ttu-id="f1f28-135">Zachowanie usługi, które umożliwia określenie ustawień, które kontrolują, jak są uruchamiane wystąpienia przepływu pracy, łącznie z trwałości, nieobsługiwanych wyjątków zachowanie i zachowanie bezczynności.</span><span class="sxs-lookup"><span data-stu-id="f1f28-135">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>|  
|[<span data-ttu-id="f1f28-136">\<workflowUnhandledException></span><span class="sxs-lookup"><span data-stu-id="f1f28-136">\<workflowUnhandledException></span></span>](workflowunhandledexception.md)|<span data-ttu-id="f1f28-137">Zachowanie usługi, który umożliwia określenie Akcja podejmowana po wystąpieniu nieobsługiwanego wyjątku w ramach usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="f1f28-137">A service behavior that enables you to specify the action to take when an unhandled exception occurs within a workflow service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f1f28-138">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f1f28-138">Parent Elements</span></span>  
  
|<span data-ttu-id="f1f28-139">Element</span><span class="sxs-lookup"><span data-stu-id="f1f28-139">Element</span></span>|<span data-ttu-id="f1f28-140">Opis</span><span class="sxs-lookup"><span data-stu-id="f1f28-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f1f28-141">\<usługiZachowady></span><span class="sxs-lookup"><span data-stu-id="f1f28-141">\<serviceBehaviors></span></span>](servicebehaviors-of-workflow.md)|<span data-ttu-id="f1f28-142">Kolekcja elementów zachowanie usługi.</span><span class="sxs-lookup"><span data-stu-id="f1f28-142">A collection of service behavior elements.</span></span>|
