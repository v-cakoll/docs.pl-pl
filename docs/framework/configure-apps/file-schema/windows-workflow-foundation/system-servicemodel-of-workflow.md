---
title: < system.serviceModel > przepływu pracy
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 6a8eb2bf-f925-40e1-ba5c-a49b1d3a3ac6
ms.openlocfilehash: 005a274df9e9ab99227a3748b7a25c9d465d020f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61768878"
---
# <a name="systemservicemodel-of-workflow"></a><span data-ttu-id="bf5f4-102">\<system.serviceModel > przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="bf5f4-102">\<system.serviceModel> of workflow</span></span>
<span data-ttu-id="bf5f4-103">Ta sekcja konfiguracji zawiera wszystkie elementy konfiguracji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="bf5f4-103">This configuration section contains all the workflow configuration elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf5f4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bf5f4-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bf5f4-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="bf5f4-105">Attributes and Elements</span></span>  
 <span data-ttu-id="bf5f4-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="bf5f4-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bf5f4-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="bf5f4-107">Attributes</span></span>  
 <span data-ttu-id="bf5f4-108">Brak</span><span class="sxs-lookup"><span data-stu-id="bf5f4-108">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="bf5f4-109">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="bf5f4-109">Child Elements</span></span>  
  
|<span data-ttu-id="bf5f4-110">Element</span><span class="sxs-lookup"><span data-stu-id="bf5f4-110">Element</span></span>|<span data-ttu-id="bf5f4-111">Opis</span><span class="sxs-lookup"><span data-stu-id="bf5f4-111">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bf5f4-112">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="bf5f4-112">\<behaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behaviors-of-workflow.md)|<span data-ttu-id="bf5f4-113">Ta sekcja definiuje **serviceBehaviors** kolekcji.</span><span class="sxs-lookup"><span data-stu-id="bf5f4-113">This section defines the **serviceBehaviors** collection.</span></span>  <span data-ttu-id="bf5f4-114">Każdy element w kolekcji definiuje zachowanie elementy używane przez usługi.</span><span class="sxs-lookup"><span data-stu-id="bf5f4-114">Each element in the collection defines behavior elements consumed by services.</span></span> <span data-ttu-id="bf5f4-115">Każdy element zachowanie jest określony przez jego unikatowy **nazwa** atrybutu.</span><span class="sxs-lookup"><span data-stu-id="bf5f4-115">Each behavior element is identified by its unique **name** attribute.</span></span>|  
|[<span data-ttu-id="bf5f4-116">\<tracking></span><span class="sxs-lookup"><span data-stu-id="bf5f4-116">\<tracking></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/tracking.md)|<span data-ttu-id="bf5f4-117">Reprezentuje sekcję konfiguracji do definiowania ustawień śledzenia dla usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="bf5f4-117">Represents a configuration section for defining tracking settings for a workflow service.</span></span><br /><br /> <span data-ttu-id="bf5f4-118">Aby uzyskać więcej informacji śledzenia przepływu pracy i jego konfiguracji, zobacz [przepływu pracy i śledzenie](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) i [Konfigurowanie śledzenia przepływu pracy](../../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="bf5f4-118">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Configuring Tracking for a Workflow](../../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bf5f4-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="bf5f4-119">Parent Elements</span></span>  
  
|<span data-ttu-id="bf5f4-120">Element</span><span class="sxs-lookup"><span data-stu-id="bf5f4-120">Element</span></span>|<span data-ttu-id="bf5f4-121">Opis</span><span class="sxs-lookup"><span data-stu-id="bf5f4-121">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bf5f4-122">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="bf5f4-122">\<configuration></span></span>|<span data-ttu-id="bf5f4-123">Element główny dla wszystkich elementów konfiguracji w PLiku konfiguracji PLatformy .NET.</span><span class="sxs-lookup"><span data-stu-id="bf5f4-123">The root element for all configuration elements in a .NET configuration file.</span></span>|
