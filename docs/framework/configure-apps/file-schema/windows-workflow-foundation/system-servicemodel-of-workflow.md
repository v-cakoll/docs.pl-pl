---
title: "&lt;system.serviceModel&gt; przepływu pracy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 6a8eb2bf-f925-40e1-ba5c-a49b1d3a3ac6
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 650cc0850b76cd6c855ea1f20b639752d7bef8cf
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltsystemservicemodelgt-of-workflow"></a><span data-ttu-id="af6b8-102">&lt;system.serviceModel&gt; przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="af6b8-102">&lt;system.serviceModel&gt; of workflow</span></span>
<span data-ttu-id="af6b8-103">Ta sekcja konfiguracji zawiera wszystkie elementy konfiguracji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="af6b8-103">This configuration section contains all the workflow configuration elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af6b8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="af6b8-104">Syntax</span></span>  
  
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
          honstLockRenewalPeriod="TimeSpan"  
          instanceCompletionAction="DeleteNothing/DeleteAll"  
          instanceEncodingAction="None/GZip"  
          instanceLockedExceptionAction="NoRetry/BasicRetry/AggressiveRetry"  
          runnableInstancesDetectionPeriod="TimeSpan" />  
      <workflowIdle timeToPersist="TimeSpan"  
          timeToUnload="TimeSpan" />  
      <workflowUnhandledExceptionaction="Abandon/AbandonAndSuspend/Cancel/Terminate" />  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="af6b8-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="af6b8-105">Attributes and Elements</span></span>  
 <span data-ttu-id="af6b8-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="af6b8-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="af6b8-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="af6b8-107">Attributes</span></span>  
 <span data-ttu-id="af6b8-108">Brak</span><span class="sxs-lookup"><span data-stu-id="af6b8-108">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="af6b8-109">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="af6b8-109">Child Elements</span></span>  
  
|<span data-ttu-id="af6b8-110">Element</span><span class="sxs-lookup"><span data-stu-id="af6b8-110">Element</span></span>|<span data-ttu-id="af6b8-111">Opis</span><span class="sxs-lookup"><span data-stu-id="af6b8-111">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="af6b8-112">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="af6b8-112">\<behaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behaviors-of-workflow.md)|<span data-ttu-id="af6b8-113">Ta sekcja definiuje **serviceBehaviors** kolekcji.</span><span class="sxs-lookup"><span data-stu-id="af6b8-113">This section defines the **serviceBehaviors** collection.</span></span>  <span data-ttu-id="af6b8-114">Każdy element w kolekcji definiuje zachowanie elementy używane przez usługi.</span><span class="sxs-lookup"><span data-stu-id="af6b8-114">Each element in the collection defines behavior elements consumed by services.</span></span> <span data-ttu-id="af6b8-115">Każdy element zachowanie jest identyfikowany przez jego unikatowy **nazwa** atrybutu.</span><span class="sxs-lookup"><span data-stu-id="af6b8-115">Each behavior element is identified by its unique **name** attribute.</span></span>|  
|[<span data-ttu-id="af6b8-116">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="af6b8-116">\<tracking></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/tracking.md)|<span data-ttu-id="af6b8-117">Reprezentuje sekcję konfiguracji do definiowania ustawień śledzenia dla usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="af6b8-117">Represents a configuration section for defining tracking settings for a workflow service.</span></span><br /><br /> <span data-ttu-id="af6b8-118">Aby uzyskać więcej informacji w śledzenia przepływu pracy i jego konfiguracja, zobacz [przepływu pracy śledzenia i śledzenia](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) i [Konfigurowanie śledzenia przepływu pracy](../../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="af6b8-118">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Configuring Tracking for a Workflow](../../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="af6b8-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="af6b8-119">Parent Elements</span></span>  
  
|<span data-ttu-id="af6b8-120">Element</span><span class="sxs-lookup"><span data-stu-id="af6b8-120">Element</span></span>|<span data-ttu-id="af6b8-121">Opis</span><span class="sxs-lookup"><span data-stu-id="af6b8-121">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="af6b8-122">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="af6b8-122">\<configuration></span></span>|<span data-ttu-id="af6b8-123">Element główny dla wszystkich elementów konfiguracji w PLiku konfiguracji PLatformy .NET.</span><span class="sxs-lookup"><span data-stu-id="af6b8-123">The root element for all configuration elements in a .NET configuration file.</span></span>|
