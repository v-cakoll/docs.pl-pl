---
title: <workflow>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 560aa9b6-9cf3-460e-b798-f87d14b1d2de
ms.openlocfilehash: 89f9d0e7c57f6e66b9fdffd148d9dcae5a189fba
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947234"
---
# <a name="workflow"></a><span data-ttu-id="ee8ad-101">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="ee8ad-101">\<workflow></span></span>
<span data-ttu-id="ee8ad-102">Element konfiguracji, który zawiera wszystkie zapytania dla określonego przepływu pracy identyfikowane przez <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="ee8ad-102">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="ee8ad-103">Aby uzyskać więcej informacji na temat śledzenia przepływu pracy i jego konfiguracji, zobacz [śledzenie przepływów pracy i](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) śledzenie i [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="ee8ad-103">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="ee8ad-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="ee8ad-104">\<system.serviceModel></span></span>  
<span data-ttu-id="ee8ad-105">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="ee8ad-105">\<tracking></span></span>  
<span data-ttu-id="ee8ad-106">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="ee8ad-106">\<trackingProfile></span></span>  
<span data-ttu-id="ee8ad-107">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="ee8ad-107">\<workflow></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee8ad-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="ee8ad-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ee8ad-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ee8ad-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ee8ad-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ee8ad-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ee8ad-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ee8ad-111">Attributes</span></span>  
  
|<span data-ttu-id="ee8ad-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="ee8ad-112">Attribute</span></span>|<span data-ttu-id="ee8ad-113">Opis</span><span class="sxs-lookup"><span data-stu-id="ee8ad-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ee8ad-114">activityDefinitionId</span><span class="sxs-lookup"><span data-stu-id="ee8ad-114">activityDefinitionId</span></span>|<span data-ttu-id="ee8ad-115">Ciąg, który określa identyfikator definicji działania przepływu pracy są śledzone.</span><span class="sxs-lookup"><span data-stu-id="ee8ad-115">A string that specifies the activity definition ID of the workflow being tracked.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ee8ad-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ee8ad-116">Child Elements</span></span>  
  
|<span data-ttu-id="ee8ad-117">Element</span><span class="sxs-lookup"><span data-stu-id="ee8ad-117">Element</span></span>|<span data-ttu-id="ee8ad-118">Opis</span><span class="sxs-lookup"><span data-stu-id="ee8ad-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ee8ad-119">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="ee8ad-119">\<activityScheduledQueries></span></span>](activityscheduledqueries.md)|<span data-ttu-id="ee8ad-120">Reprezentuje kolekcję zapytań, które są używane do śledzenia działania zaPLanowane do wykonania przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ee8ad-120">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="ee8ad-121">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania zaPLanowane rekordów.</span><span class="sxs-lookup"><span data-stu-id="ee8ad-121">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>|  
|[<span data-ttu-id="ee8ad-122">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="ee8ad-122">\<activityStateQueries></span></span>](activitystatequeries.md)|<span data-ttu-id="ee8ad-123">Reprezentuje kolekcję zapytań, które są używane do śledzenia zmian cyklem życia działań, które tworzą wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="ee8ad-123">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="ee8ad-124">Na przykład możesz chcieć śledzić każde działanie "Wyślij wiadomość E-Mail" w ramach wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="ee8ad-124">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="ee8ad-125">To zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania obiektów rekordu stanu działania.</span><span class="sxs-lookup"><span data-stu-id="ee8ad-125">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="ee8ad-126">Stany do subskrybowania są wyszczególnione w ActivityStates.</span><span class="sxs-lookup"><span data-stu-id="ee8ad-126">The available states to subscribe to are specified in ActivityStates.</span></span>|  
|[<span data-ttu-id="ee8ad-127">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="ee8ad-127">\<bookmarkResumptionQueries></span></span>](bookmarkresumptionqueries.md)|<span data-ttu-id="ee8ad-128">Reprezentuje kolekcję zapytań, które są używane do śledzenia wznowienie zakładki w ramach wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="ee8ad-128">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="ee8ad-129">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania zakładki wznowienie rekordów.</span><span class="sxs-lookup"><span data-stu-id="ee8ad-129">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
|[<span data-ttu-id="ee8ad-130">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="ee8ad-130">\<cancelRequestedQueries></span></span>](cancelrequestedqueries.md)|<span data-ttu-id="ee8ad-131">Reprezentuje kolekcję zapytań, które są używane do śledzenia żądań, aby anulować działanie podrzędne przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ee8ad-131">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="ee8ad-132">Zapytanie jest niezbędne do uczestnika śledzenia do subskrybowania Anuluj żądanie rekordu obiektów.</span><span class="sxs-lookup"><span data-stu-id="ee8ad-132">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
|[<span data-ttu-id="ee8ad-133">\<customTrackingQueries></span><span class="sxs-lookup"><span data-stu-id="ee8ad-133">\<customTrackingQueries></span></span>](customtrackingqueries.md)|<span data-ttu-id="ee8ad-134">Reprezentuje kolekcję zapytań, które są używane do śledzenia zdarzeń zdefiniowanych przez użytkownika w działaniach kodu.</span><span class="sxs-lookup"><span data-stu-id="ee8ad-134">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="ee8ad-135">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania śledzenia niestandardowe rekordów.</span><span class="sxs-lookup"><span data-stu-id="ee8ad-135">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>|  
|[<span data-ttu-id="ee8ad-136">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="ee8ad-136">\<faultPropagationQueries></span></span>](faultpropagationqueries.md)|<span data-ttu-id="ee8ad-137">Reprezentuje kolekcję zapytań, które są używane do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="ee8ad-137">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="ee8ad-138">To zdarzenie jest wykonywane za każdym razem, gdy FaultHandler przetwarza błąd.</span><span class="sxs-lookup"><span data-stu-id="ee8ad-138">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="ee8ad-139">Należy użyć takiej kwerendy do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="ee8ad-139">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="ee8ad-140">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania błędów propagacji rekordów.</span><span class="sxs-lookup"><span data-stu-id="ee8ad-140">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>|  
|[<span data-ttu-id="ee8ad-141">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="ee8ad-141">\<workflowInstanceQueries></span></span>](workflowinstancequeries.md)|<span data-ttu-id="ee8ad-142">Reprezentuje kolekcję elementów konfiguracji, które śledzą zmiany cyklu życia wystąpienia przepływu pracy, takie jak zdarzenie uruchomione lub ukończone.</span><span class="sxs-lookup"><span data-stu-id="ee8ad-142">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ee8ad-143">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ee8ad-143">Parent Elements</span></span>  
  
|<span data-ttu-id="ee8ad-144">Element</span><span class="sxs-lookup"><span data-stu-id="ee8ad-144">Element</span></span>|<span data-ttu-id="ee8ad-145">Opis</span><span class="sxs-lookup"><span data-stu-id="ee8ad-145">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ee8ad-146">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="ee8ad-146">\<trackingProfile></span></span>](trackingprofile.md)|<span data-ttu-id="ee8ad-147">Reprezentuje sekcję konfiguracji służącą do tworzenia subskrypcji dla rekordów śledzenia przepływu pracy w uczestniku śledzenia.</span><span class="sxs-lookup"><span data-stu-id="ee8ad-147">Represents a configuration section for creating a subscription to workflow tracking records in a tracking participant.</span></span> <span data-ttu-id="ee8ad-148">Profil śledzenia zawiera śledzenia zapytań, pozwalające uczestnikiem śledzenia do subskrybowania zdarzenia przepływu pracy, które są emitowane po zmianie stanu wystąpienia przepływu pracy w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="ee8ad-148">A tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="ee8ad-149">Kwerendy zdefiniowane w profilu śledzenia sekcji zdefiniować rodzaje zdarzenia, które są zwracane w subskrypcji.</span><span class="sxs-lookup"><span data-stu-id="ee8ad-149">The queries defined within the tracking profile section define the kinds of events that are returned by the subscription.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ee8ad-150">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ee8ad-150">Remarks</span></span>  
 <span data-ttu-id="ee8ad-151">Śledzenie profile zawiera śledzenia zapytań, pozwalające uczestnikiem śledzenia do subskrybowania zdarzenia przepływu pracy, które są emitowane po zmianie stanu wystąpienia określonego przepływu pracy w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="ee8ad-151">Tracking profiles contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a particular workflow instance changes at runtime.</span></span> <span data-ttu-id="ee8ad-152">Wystąpienie przepływu pracy śledzone identyfikowane przez ten element konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ee8ad-152">The workflow instance being tracked is identified by this configuration element.</span></span>  
  
 <span data-ttu-id="ee8ad-153">W zależności od potrzeb może zapisu profil przybliżonego, które subskrybuje niewielkiego zestawu zmian stanu wysokiego poziomu przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="ee8ad-153">Depending on your monitoring requirements you may write a profile that is very coarse, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="ee8ad-154">Z drugiej strony można utworzyć bardzo określony profil którego wynikowego zdarzenia są rozbudowanych, odtworzenie przepływ wykonania szczegółowe później.</span><span class="sxs-lookup"><span data-stu-id="ee8ad-154">Conversely, you may create a very specific profile whose resulting events are rich enough to reconstruct a detailed execution flow later.</span></span>  
  
 <span data-ttu-id="ee8ad-155">Profile śledzenia mają strukturę jako deklaratywne subskrypcji dla śledzenia rekordy, które umożliwiają zapytania dla rekordów śledzenie wersję wykonawczą przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="ee8ad-155">Tracking profiles are structured as declarative subscriptions for tracking records that allow you to query the workflow runtime for specific tracking records.</span></span> <span data-ttu-id="ee8ad-156">Istnieje kilku typów zapytań, które umożliwiają subskrybowanie różnych klas rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="ee8ad-156">There are a handful of query types that allow you subscribe to different classes of tracking records.</span></span> <span data-ttu-id="ee8ad-157">Aby uzyskać pełną listę zapytań, zobacz listę elementów podrzędnych tego tematu oraz [Profile śledzenia](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="ee8ad-157">For a complete list of queries, see the child element list of this topic and [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
 <span data-ttu-id="ee8ad-158">Poniższy przykład przedstawia profil śledzenia w pliku konfiguracji, który umożliwia śledzenie uczestnika subskrybowanie `Started` zdarzeń przepływu pracy i. `Completed`</span><span class="sxs-lookup"><span data-stu-id="ee8ad-158">The following example shows a tracking profile in a configuration file that allows a tracking participant to subscribe to the `Started` and `Completed` workflow events.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ee8ad-159">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ee8ad-159">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement>
- <xref:System.Activities.Tracking.TrackingProfile>
- [<span data-ttu-id="ee8ad-160">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="ee8ad-160">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="ee8ad-161">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="ee8ad-161">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
