---
title: <trackingProfile>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 154830ff-ddd3-4397-a3b5-5b334907777f
ms.openlocfilehash: 8b8cfe95a646563642e7425fdb4b5257cafa466f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947301"
---
# <a name="trackingprofile"></a><span data-ttu-id="1afc7-101">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="1afc7-101">\<trackingProfile></span></span>
<span data-ttu-id="1afc7-102">Reprezentuje sekcję konfiguracji służącą do tworzenia subskrypcji dla rekordów śledzenia przepływu pracy w uczestniku śledzenia.</span><span class="sxs-lookup"><span data-stu-id="1afc7-102">Represents a configuration section for creating a subscription to workflow tracking records in a tracking participant.</span></span> <span data-ttu-id="1afc7-103">Profil śledzenia zawiera śledzenia zapytań, pozwalające uczestnikiem śledzenia do subskrybowania zdarzenia przepływu pracy, które są emitowane po zmianie stanu wystąpienia przepływu pracy w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="1afc7-103">A tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="1afc7-104">Kwerendy zdefiniowane w profilu śledzenia sekcji zdefiniować rodzaje zdarzenia, które są zwracane w subskrypcji.</span><span class="sxs-lookup"><span data-stu-id="1afc7-104">The queries defined within the tracking profile section define the kinds of events that are returned by the subscription.</span></span>  
  
 <span data-ttu-id="1afc7-105">Aby uzyskać więcej informacji na temat śledzenia przepływu pracy i jego konfiguracji, zobacz [śledzenie przepływów pracy i](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) śledzenie i [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="1afc7-105">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="1afc7-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="1afc7-106">\<system.serviceModel></span></span>  
<span data-ttu-id="1afc7-107">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="1afc7-107">\<tracking></span></span>  
<span data-ttu-id="1afc7-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="1afc7-108">\<trackingProfile></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1afc7-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="1afc7-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1afc7-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1afc7-110">Attributes and Elements</span></span>  
 <span data-ttu-id="1afc7-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="1afc7-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1afc7-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1afc7-112">Attributes</span></span>  
  
|<span data-ttu-id="1afc7-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="1afc7-113">Attribute</span></span>|<span data-ttu-id="1afc7-114">Opis</span><span class="sxs-lookup"><span data-stu-id="1afc7-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1afc7-115">nazwa</span><span class="sxs-lookup"><span data-stu-id="1afc7-115">name</span></span>|<span data-ttu-id="1afc7-116">Ciąg określający nazwę profilu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="1afc7-116">A string that specifies the name of the tracking profile.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1afc7-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1afc7-117">Child Elements</span></span>  
  
|<span data-ttu-id="1afc7-118">Element</span><span class="sxs-lookup"><span data-stu-id="1afc7-118">Element</span></span>|<span data-ttu-id="1afc7-119">Opis</span><span class="sxs-lookup"><span data-stu-id="1afc7-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1afc7-120">\<Uczestnicy ></span><span class="sxs-lookup"><span data-stu-id="1afc7-120">\<participants></span></span>](participants.md)|<span data-ttu-id="1afc7-121">Element konfiguracji, który zawiera wszystkie zapytania dla określonego przepływu pracy identyfikowane przez <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="1afc7-121">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId%2A?displayProperty=nameWithType> property.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1afc7-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1afc7-122">Parent Elements</span></span>  
  
|<span data-ttu-id="1afc7-123">Element</span><span class="sxs-lookup"><span data-stu-id="1afc7-123">Element</span></span>|<span data-ttu-id="1afc7-124">Opis</span><span class="sxs-lookup"><span data-stu-id="1afc7-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1afc7-125">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="1afc7-125">\<tracking></span></span>](tracking.md)|<span data-ttu-id="1afc7-126">Reprezentuje sekcję konfiguracji do definiowania ustawień śledzenia dla usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="1afc7-126">Represents a configuration section for defining tracking settings for a workflow service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1afc7-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1afc7-127">Remarks</span></span>  
 <span data-ttu-id="1afc7-128">Śledzenie profile zawiera śledzenia zapytań, pozwalające uczestnikiem śledzenia do subskrybowania zdarzenia przepływu pracy, które są emitowane po zmianie stanu wystąpienia przepływu pracy w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="1afc7-128">Tracking profiles contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="1afc7-129">W zależności od potrzeb może zapisu profil przybliżonego, które subskrybuje niewielkiego zestawu zmian stanu wysokiego poziomu przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="1afc7-129">Depending on your monitoring requirements you may write a profile that is very coarse, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="1afc7-130">Z drugiej strony można utworzyć bardzo określony profil którego wynikowego zdarzenia są rozbudowanych, odtworzenie przepływ wykonania szczegółowe później.</span><span class="sxs-lookup"><span data-stu-id="1afc7-130">Conversely, you may create a very specific profile whose resulting events are rich enough to reconstruct a detailed execution flow later.</span></span>  
  
 <span data-ttu-id="1afc7-131">Profile śledzenia mają strukturę jako deklaratywne subskrypcji dla śledzenia rekordy, które umożliwiają zapytania dla rekordów śledzenie wersję wykonawczą przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="1afc7-131">Tracking profiles are structured as declarative subscriptions for tracking records that allow you to query the workflow runtime for specific tracking records.</span></span> <span data-ttu-id="1afc7-132">Istnieje kilku typów zapytań, które umożliwiają subskrybowanie różnych klas <xref:System.Activities.Tracking.TrackingRecord> obiektów.</span><span class="sxs-lookup"><span data-stu-id="1afc7-132">There are a handful of query types that allow you subscribe to different classes of <xref:System.Activities.Tracking.TrackingRecord> objects.</span></span> <span data-ttu-id="1afc7-133">Aby uzyskać pełną listę zapytań, zobacz [ \<uczestników >](participants.md) i [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md)..</span><span class="sxs-lookup"><span data-stu-id="1afc7-133">For a complete list of queries, see [\<participants>](participants.md) and [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)..</span></span>  
  
 <span data-ttu-id="1afc7-134">Poniższy przykład przedstawia profil śledzenia w pliku konfiguracji, który umożliwia śledzenie uczestnika subskrybowanie `Started` zdarzeń przepływu pracy i. `Completed`</span><span class="sxs-lookup"><span data-stu-id="1afc7-134">The following example shows a tracking profile in a configuration file that allows a tracking participant to subscribe to the `Started` and `Completed` workflow events.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1afc7-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1afc7-135">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileElement>
- <xref:System.Activities.Tracking.TrackingProfile>
- [<span data-ttu-id="1afc7-136">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="1afc7-136">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="1afc7-137">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="1afc7-137">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
