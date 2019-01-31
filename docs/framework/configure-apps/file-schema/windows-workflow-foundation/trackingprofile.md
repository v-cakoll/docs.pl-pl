---
title: <trackingProfile>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 154830ff-ddd3-4397-a3b5-5b334907777f
ms.openlocfilehash: ff5bf2b4140665e7af8f8ec0103c32fe2e8a3142
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55267862"
---
# <a name="trackingprofile"></a><span data-ttu-id="59226-101">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="59226-101">\<trackingProfile></span></span>
<span data-ttu-id="59226-102">Reprezentuje sekcję konfiguracji do tworzenia subskrypcji do śledzenia rekordów w uczestnikiem śledzenia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="59226-102">Represents a configuration section for creating a subscription to workflow tracking records in a tracking participant.</span></span> <span data-ttu-id="59226-103">Profil śledzenia zawiera śledzenia zapytań, pozwalające uczestnikiem śledzenia do subskrybowania zdarzenia przepływu pracy, które są emitowane po zmianie stanu wystąpienia przepływu pracy w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="59226-103">A tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="59226-104">Kwerendy zdefiniowane w profilu śledzenia sekcji zdefiniować rodzaje zdarzenia, które są zwracane w subskrypcji.</span><span class="sxs-lookup"><span data-stu-id="59226-104">The queries defined within the tracking profile section define the kinds of events that are returned by the subscription.</span></span>  
  
 <span data-ttu-id="59226-105">Aby uzyskać więcej informacji śledzenia przepływu pracy i jego konfiguracji, zobacz [przepływu pracy i śledzenie](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) i [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="59226-105">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="59226-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="59226-106">\<system.serviceModel></span></span>  
<span data-ttu-id="59226-107">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="59226-107">\<tracking></span></span>  
<span data-ttu-id="59226-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="59226-108">\<trackingProfile></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59226-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="59226-109">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <tracking>
    <profiles>
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
          <activityStateQueries>
            <activityStateQuery activityName="String" />
            <arguments>
              <argument name="String" />
            </arguments>
            <states>
              <state name="String"  />
            </states>
            <variables>
              <variable name="String" />
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
                                   faultHandlerActivityName="String" />
          </faultPropagationQueries>
          <workflowInstanceQueries>
            <workflowInstanceQuery>
              <states>
                <state name="String" />
              </states>
            </workflowInstanceQuery>
          </workflowInstanceQueries>
        </workflow>
      </trackingProfile>
    </profiles>
  </tracking>
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="59226-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="59226-110">Attributes and Elements</span></span>  
 <span data-ttu-id="59226-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="59226-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="59226-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="59226-112">Attributes</span></span>  
  
|<span data-ttu-id="59226-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="59226-113">Attribute</span></span>|<span data-ttu-id="59226-114">Opis</span><span class="sxs-lookup"><span data-stu-id="59226-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="59226-115">nazwa</span><span class="sxs-lookup"><span data-stu-id="59226-115">name</span></span>|<span data-ttu-id="59226-116">Ciąg określający nazwę profilu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="59226-116">A string that specifies the name of the tracking profile.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="59226-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="59226-117">Child Elements</span></span>  
  
|<span data-ttu-id="59226-118">Element</span><span class="sxs-lookup"><span data-stu-id="59226-118">Element</span></span>|<span data-ttu-id="59226-119">Opis</span><span class="sxs-lookup"><span data-stu-id="59226-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="59226-120">\<Uczestnicy ></span><span class="sxs-lookup"><span data-stu-id="59226-120">\<participants></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md)|<span data-ttu-id="59226-121">Element konfiguracji, który zawiera wszystkie zapytania dla określonego przepływu pracy identyfikowane przez <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="59226-121">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId%2A?displayProperty=nameWithType> property.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="59226-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="59226-122">Parent Elements</span></span>  
  
|<span data-ttu-id="59226-123">Element</span><span class="sxs-lookup"><span data-stu-id="59226-123">Element</span></span>|<span data-ttu-id="59226-124">Opis</span><span class="sxs-lookup"><span data-stu-id="59226-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="59226-125">\<tracking></span><span class="sxs-lookup"><span data-stu-id="59226-125">\<tracking></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/tracking.md)|<span data-ttu-id="59226-126">Reprezentuje sekcję konfiguracji do definiowania ustawień śledzenia dla usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="59226-126">Represents a configuration section for defining tracking settings for a workflow service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="59226-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="59226-127">Remarks</span></span>  
 <span data-ttu-id="59226-128">Śledzenie profile zawiera śledzenia zapytań, pozwalające uczestnikiem śledzenia do subskrybowania zdarzenia przepływu pracy, które są emitowane po zmianie stanu wystąpienia przepływu pracy w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="59226-128">Tracking profiles contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="59226-129">W zależności od potrzeb może zapisu profil przybliżonego, które subskrybuje niewielkiego zestawu zmian stanu wysokiego poziomu przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="59226-129">Depending on your monitoring requirements you may write a profile that is very coarse, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="59226-130">Z drugiej strony można utworzyć bardzo określony profil którego wynikowego zdarzenia są rozbudowanych, odtworzenie przepływ wykonania szczegółowe później.</span><span class="sxs-lookup"><span data-stu-id="59226-130">Conversely, you may create a very specific profile whose resulting events are rich enough to reconstruct a detailed execution flow later.</span></span>  
  
 <span data-ttu-id="59226-131">Profile śledzenia mają strukturę jako deklaratywne subskrypcji dla śledzenia rekordy, które umożliwiają zapytania dla rekordów śledzenie wersję wykonawczą przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="59226-131">Tracking profiles are structured as declarative subscriptions for tracking records that allow you to query the workflow runtime for specific tracking records.</span></span> <span data-ttu-id="59226-132">Istnieje kilka typów zapytania, które umożliwiają subskrybować różnymi klasami <xref:System.Activities.Tracking.TrackingRecord> obiektów.</span><span class="sxs-lookup"><span data-stu-id="59226-132">There are a handful of query types that allow you subscribe to different classes of <xref:System.Activities.Tracking.TrackingRecord> objects.</span></span> <span data-ttu-id="59226-133">Aby uzyskać pełną listę zapytań, zobacz [ \<uczestników >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md) i [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)...</span><span class="sxs-lookup"><span data-stu-id="59226-133">For a complete list of queries, see [\<participants>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md) and [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)..</span></span>  
  
 <span data-ttu-id="59226-134">W poniższym przykładzie pokazano profil śledzenia w pliku konfiguracji, który umożliwia śledzenia uczestnika do subskrybowania `Started` i `Completed` zdarzenia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="59226-134">The following example shows a tracking profile in a configuration file that allows a tracking participant to subscribe to the `Started` and `Completed` workflow events.</span></span>  
  
```xml  
<system.serviceModel>  
  <tracking>    
    <trackingProfile name="Sample Tracking Profile">  
      <workflow activityDefinitionId="*">  
         <workflowInstanceQueries>  
            <workflowInstanceQuery>  
            <states>  
              <state name="Started"/>  
              <state name="Completed"/>  
            </states>  
          </workflowInstanceQuery>  
        </workflowInstanceQueries>  
      </workflow>  
    </trackingProfile>          
   </profiles>  
  </tracking>  
</system.serviceModel>  
```  
  
## <a name="see-also"></a><span data-ttu-id="59226-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="59226-135">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileElement>
- <xref:System.Activities.Tracking.TrackingProfile>
- [<span data-ttu-id="59226-136">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="59226-136">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="59226-137">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="59226-137">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
