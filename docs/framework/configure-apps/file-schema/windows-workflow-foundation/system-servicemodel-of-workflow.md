---
title: < System. serviceModel > przepływu pracy
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 6a8eb2bf-f925-40e1-ba5c-a49b1d3a3ac6
ms.openlocfilehash: faa8154c4d7ac5c6aa2f9f1707cf8f0d39eefad5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947367"
---
# <a name="systemservicemodel-of-workflow"></a><span data-ttu-id="ba749-102">\<> System. serviceModel przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="ba749-102">\<system.serviceModel> of workflow</span></span>
<span data-ttu-id="ba749-103">Ta sekcja konfiguracji zawiera wszystkie elementy konfiguracji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="ba749-103">This configuration section contains all the workflow configuration elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba749-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ba749-104">Syntax</span></span>  
  
```xml  
<system.ServiceModel>  
  <behaviors>  
    <serviceBehaviors>  
    <behavior name="String">  
      <bufferReceive maxPendingMessagesPerChannel="Integer" />  
      <etwTracking profileName="String" />  
     <sendMessageChannelCache allowUnsafeCaching="Boolean" >          
        <channelSettings idleTimeout="TimeSpan" leaseTimeout="TimeSpan" maxItemsInCache="Integer" />  
        <factorySettings idleTimeout="TimeSpan" leaseTimeout="TimeSpan" maxItemsInCache="Integer" />  
     </sendMessageChannelCache>  
      <sqlWorkflowInstanceStore   
          connectionStringName="String"   
          hostLockRenewalPeriod="TimeSpan"  
          instanceCompletionAction="DeleteNothing/DeleteAll"  
          instanceEncodingAction="None/GZip"  
          instanceLockedExceptionAction="NoRetry/BasicRetry/AggressiveRetry"  
          runnableInstancesDetectionPeriod="TimeSpan" />  
      <workflowIdle timeToPersist="TimeSpan"  
          timeToUnload="TimeSpan" />  
      <workflowUnhandledExceptionAction="Abandon/AbandonAndSuspend/Cancel/Terminate" />  
    </behavior>  
    </serviceBehaviors>  
  </behaviors>  
  <tracking>    
     <participants>   
      <add name="String"   
           profileName="String"  
           type="String" />   
     </participants>   
    <trackingProfile name="String">  
      <workflow activityDefinitionId="String">  
          <activityScheduledQueries>  
             <activityScheduledQuery activityName="String"  
                 childActivityName="String"/>  
          </activityScheduledQueries>  
             <activityStateQuery activityName="String" />  
                <arguments>  
                   <argument name="String"/>  
                </arguments>  
                <states>  
                   <state name="String"/>  
                </states>  
                <variables>  
                   <variable name="String"/>  
                </variables>  
          </activityStateQueries>  
          <bookmarkResumptionQueries>  
             <bookmarkResumptionQuery name="String" />  
          </bookmarkResumptionQueries>  
          <cancelRequestQueries>  
             <cancelRequestQuery activityName="String"  
                 childActivityName="String"/>  
          </cancelRequestQueries>  
          <customTrackingQueries>  
             <customTrackingQuery activityName="String"  
                 name="String"/>  
          </customTrackingQueries>  
          <faultPropagationQueries>  
             <faultPropagationQuery activityName="String"  
                 faultHandlerActivityName="String"/>  
          </faultPropagationQueries>  
         <workflowInstanceQueries>  
            <workflowInstanceQuery>  
              <states>  
                 <state name="String"/>  
              </states>  
          </workflowInstanceQuery>  
        </workflowInstanceQueries>  
      </workflow>  
    </trackingProfile>          
   </profiles>  
  </tracking>  
</system.ServiceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ba749-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ba749-105">Attributes and Elements</span></span>  
 <span data-ttu-id="ba749-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ba749-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ba749-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ba749-107">Attributes</span></span>  
 <span data-ttu-id="ba749-108">Brak</span><span class="sxs-lookup"><span data-stu-id="ba749-108">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ba749-109">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ba749-109">Child Elements</span></span>  
  
|<span data-ttu-id="ba749-110">Element</span><span class="sxs-lookup"><span data-stu-id="ba749-110">Element</span></span>|<span data-ttu-id="ba749-111">Opis</span><span class="sxs-lookup"><span data-stu-id="ba749-111">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ba749-112">\<> zachowań</span><span class="sxs-lookup"><span data-stu-id="ba749-112">\<behaviors></span></span>](behaviors-of-workflow.md)|<span data-ttu-id="ba749-113">Ta sekcja definiuje kolekcję serviceBehaviors.</span><span class="sxs-lookup"><span data-stu-id="ba749-113">This section defines the **serviceBehaviors** collection.</span></span>  <span data-ttu-id="ba749-114">Każdy element w kolekcji definiuje zachowanie elementy używane przez usługi.</span><span class="sxs-lookup"><span data-stu-id="ba749-114">Each element in the collection defines behavior elements consumed by services.</span></span> <span data-ttu-id="ba749-115">Każdy element zachowania jest identyfikowany przez jego unikatowy atrybut **nazwy** .</span><span class="sxs-lookup"><span data-stu-id="ba749-115">Each behavior element is identified by its unique **name** attribute.</span></span>|  
|[<span data-ttu-id="ba749-116">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="ba749-116">\<tracking></span></span>](tracking.md)|<span data-ttu-id="ba749-117">Reprezentuje sekcję konfiguracji do definiowania ustawień śledzenia dla usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="ba749-117">Represents a configuration section for defining tracking settings for a workflow service.</span></span><br /><br /> <span data-ttu-id="ba749-118">Aby uzyskać więcej informacji na temat śledzenia przepływu pracy i jego konfiguracji, zobacz [śledzenie i śledzenie przepływów pracy](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) oraz [Konfigurowanie śledzenia dla przepływu pracy](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="ba749-118">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Configuring Tracking for a Workflow](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ba749-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ba749-119">Parent Elements</span></span>  
  
|<span data-ttu-id="ba749-120">Element</span><span class="sxs-lookup"><span data-stu-id="ba749-120">Element</span></span>|<span data-ttu-id="ba749-121">Opis</span><span class="sxs-lookup"><span data-stu-id="ba749-121">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ba749-122">\<> konfiguracji</span><span class="sxs-lookup"><span data-stu-id="ba749-122">\<configuration></span></span>|<span data-ttu-id="ba749-123">Element główny dla wszystkich elementów konfiguracji w PLiku konfiguracji PLatformy .NET.</span><span class="sxs-lookup"><span data-stu-id="ba749-123">The root element for all configuration elements in a .NET configuration file.</span></span>|
