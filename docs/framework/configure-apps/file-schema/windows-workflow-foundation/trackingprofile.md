---
title: <trackingProfile>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 154830ff-ddd3-4397-a3b5-5b334907777f
ms.openlocfilehash: 3120d6f5d1bb5a5cf452567e96766231534f3f41
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398594"
---
# <a name="trackingprofile"></a><span data-ttu-id="a7b3a-101">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="a7b3a-101">\<trackingProfile></span></span>
<span data-ttu-id="a7b3a-102">Reprezentuje sekcję konfiguracji służącą do tworzenia subskrypcji dla rekordów śledzenia przepływu pracy w uczestniku śledzenia.</span><span class="sxs-lookup"><span data-stu-id="a7b3a-102">Represents a configuration section for creating a subscription to workflow tracking records in a tracking participant.</span></span> <span data-ttu-id="a7b3a-103">Profil śledzenia zawiera śledzenia zapytań, pozwalające uczestnikiem śledzenia do subskrybowania zdarzenia przepływu pracy, które są emitowane po zmianie stanu wystąpienia przepływu pracy w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="a7b3a-103">A tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="a7b3a-104">Kwerendy zdefiniowane w profilu śledzenia sekcji zdefiniować rodzaje zdarzenia, które są zwracane w subskrypcji.</span><span class="sxs-lookup"><span data-stu-id="a7b3a-104">The queries defined within the tracking profile section define the kinds of events that are returned by the subscription.</span></span>  
  
 <span data-ttu-id="a7b3a-105">Aby uzyskać więcej informacji na temat śledzenia przepływu pracy i jego konfiguracji, zobacz [śledzenie przepływów pracy i](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) śledzenie i [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="a7b3a-105">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="a7b3a-106">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a7b3a-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a7b3a-107">&nbsp;&nbsp;[ **\<systemami. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="a7b3a-107">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="a7b3a-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Śledzenie >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="a7b3a-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="a7b3a-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<trackingProfile >**</span><span class="sxs-lookup"><span data-stu-id="a7b3a-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<trackingProfile>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7b3a-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="a7b3a-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a7b3a-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a7b3a-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a7b3a-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a7b3a-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a7b3a-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a7b3a-113">Attributes</span></span>  
  
|<span data-ttu-id="a7b3a-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="a7b3a-114">Attribute</span></span>|<span data-ttu-id="a7b3a-115">Opis</span><span class="sxs-lookup"><span data-stu-id="a7b3a-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a7b3a-116">nazwa</span><span class="sxs-lookup"><span data-stu-id="a7b3a-116">name</span></span>|<span data-ttu-id="a7b3a-117">Ciąg określający nazwę profilu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="a7b3a-117">A string that specifies the name of the tracking profile.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a7b3a-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a7b3a-118">Child Elements</span></span>  
  
|<span data-ttu-id="a7b3a-119">Element</span><span class="sxs-lookup"><span data-stu-id="a7b3a-119">Element</span></span>|<span data-ttu-id="a7b3a-120">Opis</span><span class="sxs-lookup"><span data-stu-id="a7b3a-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a7b3a-121">\<Uczestnicy ></span><span class="sxs-lookup"><span data-stu-id="a7b3a-121">\<participants></span></span>](participants.md)|<span data-ttu-id="a7b3a-122">Element konfiguracji, który zawiera wszystkie zapytania dla określonego przepływu pracy identyfikowane przez <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="a7b3a-122">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId%2A?displayProperty=nameWithType> property.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a7b3a-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a7b3a-123">Parent Elements</span></span>  
  
|<span data-ttu-id="a7b3a-124">Element</span><span class="sxs-lookup"><span data-stu-id="a7b3a-124">Element</span></span>|<span data-ttu-id="a7b3a-125">Opis</span><span class="sxs-lookup"><span data-stu-id="a7b3a-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a7b3a-126">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="a7b3a-126">\<tracking></span></span>](tracking.md)|<span data-ttu-id="a7b3a-127">Reprezentuje sekcję konfiguracji do definiowania ustawień śledzenia dla usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="a7b3a-127">Represents a configuration section for defining tracking settings for a workflow service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a7b3a-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a7b3a-128">Remarks</span></span>  
 <span data-ttu-id="a7b3a-129">Śledzenie profile zawiera śledzenia zapytań, pozwalające uczestnikiem śledzenia do subskrybowania zdarzenia przepływu pracy, które są emitowane po zmianie stanu wystąpienia przepływu pracy w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="a7b3a-129">Tracking profiles contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="a7b3a-130">W zależności od potrzeb może zapisu profil przybliżonego, które subskrybuje niewielkiego zestawu zmian stanu wysokiego poziomu przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="a7b3a-130">Depending on your monitoring requirements you may write a profile that is very coarse, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="a7b3a-131">Z drugiej strony można utworzyć bardzo określony profil którego wynikowego zdarzenia są rozbudowanych, odtworzenie przepływ wykonania szczegółowe później.</span><span class="sxs-lookup"><span data-stu-id="a7b3a-131">Conversely, you may create a very specific profile whose resulting events are rich enough to reconstruct a detailed execution flow later.</span></span>  
  
 <span data-ttu-id="a7b3a-132">Profile śledzenia mają strukturę jako deklaratywne subskrypcji dla śledzenia rekordy, które umożliwiają zapytania dla rekordów śledzenie wersję wykonawczą przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="a7b3a-132">Tracking profiles are structured as declarative subscriptions for tracking records that allow you to query the workflow runtime for specific tracking records.</span></span> <span data-ttu-id="a7b3a-133">Istnieje kilku typów zapytań, które umożliwiają subskrybowanie różnych klas <xref:System.Activities.Tracking.TrackingRecord> obiektów.</span><span class="sxs-lookup"><span data-stu-id="a7b3a-133">There are a handful of query types that allow you subscribe to different classes of <xref:System.Activities.Tracking.TrackingRecord> objects.</span></span> <span data-ttu-id="a7b3a-134">Aby uzyskać pełną listę zapytań, zobacz [ \<uczestników >](participants.md) i [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md)..</span><span class="sxs-lookup"><span data-stu-id="a7b3a-134">For a complete list of queries, see [\<participants>](participants.md) and [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)..</span></span>  
  
 <span data-ttu-id="a7b3a-135">Poniższy przykład przedstawia profil śledzenia w pliku konfiguracji, który umożliwia śledzenie uczestnika subskrybowanie `Started` zdarzeń przepływu pracy i. `Completed`</span><span class="sxs-lookup"><span data-stu-id="a7b3a-135">The following example shows a tracking profile in a configuration file that allows a tracking participant to subscribe to the `Started` and `Completed` workflow events.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a7b3a-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a7b3a-136">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileElement>
- <xref:System.Activities.Tracking.TrackingProfile>
- [<span data-ttu-id="a7b3a-137">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="a7b3a-137">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="a7b3a-138">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="a7b3a-138">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
