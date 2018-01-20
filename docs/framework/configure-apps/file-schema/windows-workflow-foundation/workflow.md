---
title: "&lt;przepływ pracy&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 560aa9b6-9cf3-460e-b798-f87d14b1d2de
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7130a918f5a0d879fa07e0d6c055aa600e1635c6
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="ltworkflowgt"></a><span data-ttu-id="83a99-102">&lt;przepływ pracy&gt;</span><span class="sxs-lookup"><span data-stu-id="83a99-102">&lt;workflow&gt;</span></span>
<span data-ttu-id="83a99-103">Element konfiguracji, który zawiera wszystkie zapytania dotyczące określonego przepływu pracy, identyfikowane przez **HYPERLINK "http://msdn.microsoft.com/library/ ctivityDefinitionId system.ServiceModel.Activities.Tracking.Configuration.profileworkflowelement.activitydefinitionid (VS.100) .aspx"** właściwości.</span><span class="sxs-lookup"><span data-stu-id="83a99-103">A configuration element that contains all queries for a specific workflow identified by the **a HYPERLINK "http://msdn.microsoft.com/library/system.servicemodel.activities.tracking.configuration.profileworkflowelement.activitydefinitionid(VS.100).aspx" ctivityDefinitionId** property.</span></span>  
  
 <span data-ttu-id="83a99-104">Aby uzyskać więcej informacji w śledzenia przepływu pracy i jego konfiguracja, zobacz [przepływu pracy śledzenia i śledzenia](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) i [śledzenia profile](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="83a99-104">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="83a99-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="83a99-105">\<system.serviceModel></span></span>  
<span data-ttu-id="83a99-106">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="83a99-106">\<tracking></span></span>  
<span data-ttu-id="83a99-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="83a99-107">\<trackingProfile></span></span>  
<span data-ttu-id="83a99-108">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="83a99-108">\<workflow></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83a99-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="83a99-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="83a99-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="83a99-110">Attributes and Elements</span></span>  
 <span data-ttu-id="83a99-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="83a99-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="83a99-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="83a99-112">Attributes</span></span>  
  
|<span data-ttu-id="83a99-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="83a99-113">Attribute</span></span>|<span data-ttu-id="83a99-114">Opis</span><span class="sxs-lookup"><span data-stu-id="83a99-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="83a99-115">activityDefinitionId</span><span class="sxs-lookup"><span data-stu-id="83a99-115">activityDefinitionId</span></span>|<span data-ttu-id="83a99-116">Ciąg, który określa identyfikator definicji działania przepływu pracy są śledzone.</span><span class="sxs-lookup"><span data-stu-id="83a99-116">A string that specifies the activity definition ID of the workflow being tracked.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="83a99-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="83a99-117">Child Elements</span></span>  
  
|<span data-ttu-id="83a99-118">Element</span><span class="sxs-lookup"><span data-stu-id="83a99-118">Element</span></span>|<span data-ttu-id="83a99-119">Opis</span><span class="sxs-lookup"><span data-stu-id="83a99-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="83a99-120">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="83a99-120">\<activityScheduledQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledqueries.md)|<span data-ttu-id="83a99-121">Reprezentuje kolekcję zapytań, które są używane do śledzenia działania zaPLanowane do wykonania przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="83a99-121">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="83a99-122">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania zaPLanowane rekordów.</span><span class="sxs-lookup"><span data-stu-id="83a99-122">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>|  
|[<span data-ttu-id="83a99-123">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="83a99-123">\<activityStateQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequeries.md)|<span data-ttu-id="83a99-124">Reprezentuje kolekcję zapytań, które są używane do śledzenia zmian cyklem życia działań, które tworzą wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="83a99-124">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="83a99-125">Na przykład może być do śledzenia każdorazowo po ukończeniu działania "Wyślij wiadomość E-Mail" w ramach wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="83a99-125">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="83a99-126">To zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania obiektów rekordu stanu działania.</span><span class="sxs-lookup"><span data-stu-id="83a99-126">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="83a99-127">Stany do subskrybowania są wyszczególnione w ActivityStates.</span><span class="sxs-lookup"><span data-stu-id="83a99-127">The available states to subscribe to are specified in ActivityStates.</span></span>|  
|[<span data-ttu-id="83a99-128">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="83a99-128">\<bookmarkResumptionQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionqueries.md)|<span data-ttu-id="83a99-129">Reprezentuje kolekcję zapytań, które są używane do śledzenia wznowienie zakładki w ramach wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="83a99-129">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="83a99-130">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania zakładki wznowienie rekordów.</span><span class="sxs-lookup"><span data-stu-id="83a99-130">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
|[<span data-ttu-id="83a99-131">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="83a99-131">\<cancelRequestedQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/cancelrequestedqueries.md)|<span data-ttu-id="83a99-132">Reprezentuje kolekcję zapytań, które są używane do śledzenia żądań, aby anulować działanie podrzędne przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="83a99-132">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="83a99-133">Zapytanie jest niezbędne do uczestnika śledzenia do subskrybowania Anuluj żądanie rekordu obiektów.</span><span class="sxs-lookup"><span data-stu-id="83a99-133">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
|[<span data-ttu-id="83a99-134">\<customTrackingQueries></span><span class="sxs-lookup"><span data-stu-id="83a99-134">\<customTrackingQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingqueries.md)|<span data-ttu-id="83a99-135">Reprezentuje kolekcję zapytań, które są używane do śledzenia zdarzeń zdefiniowanych przez użytkownika w działaniach kodu.</span><span class="sxs-lookup"><span data-stu-id="83a99-135">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="83a99-136">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania śledzenia niestandardowe rekordów.</span><span class="sxs-lookup"><span data-stu-id="83a99-136">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>|  
|[<span data-ttu-id="83a99-137">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="83a99-137">\<faultPropagationQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationqueries.md)|<span data-ttu-id="83a99-138">Reprezentuje kolekcję zapytań, które są używane do śledzenia Obsługa błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="83a99-138">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="83a99-139">To zdarzenie występuje zawsze FaultHandler przetwarza błąd.</span><span class="sxs-lookup"><span data-stu-id="83a99-139">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="83a99-140">Należy użyć takiej kwerendy do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="83a99-140">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="83a99-141">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania błędów propagacji rekordów.</span><span class="sxs-lookup"><span data-stu-id="83a99-141">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>|  
|[<span data-ttu-id="83a99-142">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="83a99-142">\<workflowInstanceQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequeries.md)|<span data-ttu-id="83a99-143">Reprezentuje kolekcję elementów konfiguracji, które śledzą zmiany cyklu życia wystąpienia przepływu pracy, takich jak zdarzenia rozpoczęte lub zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="83a99-143">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="83a99-144">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="83a99-144">Parent Elements</span></span>  
  
|<span data-ttu-id="83a99-145">Element</span><span class="sxs-lookup"><span data-stu-id="83a99-145">Element</span></span>|<span data-ttu-id="83a99-146">Opis</span><span class="sxs-lookup"><span data-stu-id="83a99-146">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="83a99-147">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="83a99-147">\<trackingProfile></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/trackingprofile.md)|<span data-ttu-id="83a99-148">Reprezentuje sekcję konfiguracji do tworzenia subskrypcji do śledzenia rekordów w uczestnika śledzenia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="83a99-148">Represents a configuration section for creating a subscription to workflow tracking records in a tracking participant.</span></span> <span data-ttu-id="83a99-149">Profil śledzenia zawiera śledzenia zapytań, pozwalające uczestnikiem śledzenia do subskrybowania zdarzenia przepływu pracy, które są emitowane po zmianie stanu wystąpienia przepływu pracy w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="83a99-149">A tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="83a99-150">Kwerendy zdefiniowane w profilu śledzenia sekcji zdefiniować rodzaje zdarzenia, które są zwracane w subskrypcji.</span><span class="sxs-lookup"><span data-stu-id="83a99-150">The queries defined within the tracking profile section define the kinds of events that are returned by the subscription.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="83a99-151">Uwagi</span><span class="sxs-lookup"><span data-stu-id="83a99-151">Remarks</span></span>  
 <span data-ttu-id="83a99-152">Śledzenie profile zawiera śledzenia zapytań, pozwalające uczestnikiem śledzenia do subskrybowania zdarzenia przepływu pracy, które są emitowane po zmianie stanu wystąpienia określonego przepływu pracy w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="83a99-152">Tracking profiles contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a particular workflow instance changes at runtime.</span></span> <span data-ttu-id="83a99-153">Wystąpienie przepływu pracy śledzone identyfikowane przez ten element konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="83a99-153">The workflow instance being tracked is identified by this configuration element.</span></span>  
  
 <span data-ttu-id="83a99-154">W zależności od potrzeb może zapisu profil przybliżonego, które subskrybuje niewielkiego zestawu zmian stanu wysokiego poziomu przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="83a99-154">Depending on your monitoring requirements you may write a profile that is very coarse, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="83a99-155">Z drugiej strony można utworzyć bardzo określony profil którego wynikowego zdarzenia są rozbudowanych, odtworzenie przepływ wykonania szczegółowe później.</span><span class="sxs-lookup"><span data-stu-id="83a99-155">Conversely, you may create a very specific profile whose resulting events are rich enough to reconstruct a detailed execution flow later.</span></span>  
  
 <span data-ttu-id="83a99-156">Profile śledzenia mają strukturę jako deklaratywne subskrypcji dla śledzenia rekordy, które umożliwiają zapytania dla rekordów śledzenie wersję wykonawczą przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="83a99-156">Tracking profiles are structured as declarative subscriptions for tracking records that allow you to query the workflow runtime for specific tracking records.</span></span> <span data-ttu-id="83a99-157">Istnieje kilka typów zapytania, które zezwala na subskrybować śledzenie rekordów różnych klas.</span><span class="sxs-lookup"><span data-stu-id="83a99-157">There are a handful of query types that allow you subscribe to different classes of tracking records.</span></span> <span data-ttu-id="83a99-158">Aby uzyskać pełną listę zapytań, zobacz liście elementów podrzędnych tego tematu i [śledzenia profile](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="83a99-158">For a complete list of queries, see the child element list of this topic and [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
 <span data-ttu-id="83a99-159">W poniższym przykładzie przedstawiono profilu śledzenia w pliku konfiguracji, który umożliwia śledzenie uczestnika do subskrybowania `Started` i `Completed` zdarzeń przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="83a99-159">The following example shows a tracking profile in a configuration file that allows a tracking participant to subscribe to the `Started` and `Completed` workflow events.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="83a99-160">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="83a99-160">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement>  
 <xref:System.Activities.Tracking.TrackingProfile>  
 [<span data-ttu-id="83a99-161">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="83a99-161">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="83a99-162">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="83a99-162">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
