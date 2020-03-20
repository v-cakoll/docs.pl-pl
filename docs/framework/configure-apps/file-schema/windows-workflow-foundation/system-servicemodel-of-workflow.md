---
title: <system.serviceModel> przepływu pracy
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 6a8eb2bf-f925-40e1-ba5c-a49b1d3a3ac6
ms.openlocfilehash: 9aa2bf0fdfd6fe4528a3fda4d05b3ba8f23637d3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151952"
---
# <a name="systemservicemodel-of-workflow"></a><span data-ttu-id="79d57-102">\<system.serviceModel> przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="79d57-102">\<system.serviceModel> of workflow</span></span>
<span data-ttu-id="79d57-103">Ta sekcja konfiguracji zawiera wszystkie elementy konfiguracji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="79d57-103">This configuration section contains all the workflow configuration elements.</span></span>  

<span data-ttu-id="79d57-104">[**\<>konfiguracyjne**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="79d57-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="79d57-105">&nbsp;&nbsp;**\<System.>z>**</span><span class="sxs-lookup"><span data-stu-id="79d57-105">&nbsp;&nbsp;**\<system.ServiceModel>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79d57-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="79d57-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="79d57-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="79d57-107">Attributes and Elements</span></span>  
 <span data-ttu-id="79d57-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="79d57-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="79d57-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="79d57-109">Attributes</span></span>  
 <span data-ttu-id="79d57-110">Brak</span><span class="sxs-lookup"><span data-stu-id="79d57-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="79d57-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="79d57-111">Child Elements</span></span>  
  
|<span data-ttu-id="79d57-112">Element</span><span class="sxs-lookup"><span data-stu-id="79d57-112">Element</span></span>|<span data-ttu-id="79d57-113">Opis</span><span class="sxs-lookup"><span data-stu-id="79d57-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="79d57-114">\<zachowania></span><span class="sxs-lookup"><span data-stu-id="79d57-114">\<behaviors></span></span>](behaviors-of-workflow.md)|<span data-ttu-id="79d57-115">W tej sekcji definiuje **serviceBehaviors kolekcji.**</span><span class="sxs-lookup"><span data-stu-id="79d57-115">This section defines the **serviceBehaviors** collection.</span></span>  <span data-ttu-id="79d57-116">Każdy element w kolekcji definiuje zachowanie elementy używane przez usługi.</span><span class="sxs-lookup"><span data-stu-id="79d57-116">Each element in the collection defines behavior elements consumed by services.</span></span> <span data-ttu-id="79d57-117">Każdy element zachowania jest identyfikowany przez jego unikatowy atrybut **nazwy.**</span><span class="sxs-lookup"><span data-stu-id="79d57-117">Each behavior element is identified by its unique **name** attribute.</span></span>|  
|[<span data-ttu-id="79d57-118">\<>śledzenia</span><span class="sxs-lookup"><span data-stu-id="79d57-118">\<tracking></span></span>](tracking.md)|<span data-ttu-id="79d57-119">Reprezentuje sekcję konfiguracji do definiowania ustawień śledzenia dla usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="79d57-119">Represents a configuration section for defining tracking settings for a workflow service.</span></span><br /><br /> <span data-ttu-id="79d57-120">Aby uzyskać więcej informacji dotyczących śledzenia przepływu pracy i jego konfiguracji, zobacz [Śledzenie przepływu pracy i śledzenie](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) i [konfigurowanie śledzenia dla przepływu pracy](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="79d57-120">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Configuring Tracking for a Workflow](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="79d57-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="79d57-121">Parent Elements</span></span>  
  
|<span data-ttu-id="79d57-122">Element</span><span class="sxs-lookup"><span data-stu-id="79d57-122">Element</span></span>|<span data-ttu-id="79d57-123">Opis</span><span class="sxs-lookup"><span data-stu-id="79d57-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="79d57-124">\<>konfiguracyjne</span><span class="sxs-lookup"><span data-stu-id="79d57-124">\<configuration></span></span>](../configuration-element.md)|<span data-ttu-id="79d57-125">Element główny dla wszystkich elementów konfiguracji w PLiku konfiguracji PLatformy .NET.</span><span class="sxs-lookup"><span data-stu-id="79d57-125">The root element for all configuration elements in a .NET configuration file.</span></span>|
