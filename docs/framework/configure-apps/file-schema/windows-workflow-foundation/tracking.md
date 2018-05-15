---
title: '&lt;Śledzenie&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: fd9b50ed-98a1-4518-836d-e4e02c670822
ms.openlocfilehash: 38c765c52a7578ed9972cd6fdd8e01440a4d9594
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="lttrackinggt"></a><span data-ttu-id="67818-102">&lt;Śledzenie&gt;</span><span class="sxs-lookup"><span data-stu-id="67818-102">&lt;tracking&gt;</span></span>
<span data-ttu-id="67818-103">Reprezentuje sekcję konfiguracji do definiowania ustawień śledzenia dla usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="67818-103">Represents a configuration section for defining tracking settings for a workflow service.</span></span>  
  
 <span data-ttu-id="67818-104">Aby uzyskać więcej informacji w śledzenia przepływu pracy i jego konfiguracja, zobacz [przepływu pracy śledzenia i śledzenia](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) i [Konfigurowanie śledzenia przepływu pracy](../../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="67818-104">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Configuring Tracking for a Workflow](../../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>  
  
<span data-ttu-id="67818-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="67818-105">\<system.serviceModel></span></span>  
<span data-ttu-id="67818-106">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="67818-106">\<tracking></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67818-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="67818-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="67818-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="67818-108">Attributes and Elements</span></span>  
 <span data-ttu-id="67818-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="67818-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="67818-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="67818-110">Attributes</span></span>  
 <span data-ttu-id="67818-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="67818-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="67818-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="67818-112">Child Elements</span></span>  
  
|<span data-ttu-id="67818-113">Element</span><span class="sxs-lookup"><span data-stu-id="67818-113">Element</span></span>|<span data-ttu-id="67818-114">Opis</span><span class="sxs-lookup"><span data-stu-id="67818-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="67818-115">\<Uczestnicy ></span><span class="sxs-lookup"><span data-stu-id="67818-115">\<participants></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md)|<span data-ttu-id="67818-116">Kolekcję elementów konfiguracji Definiowanie uczestników subskrybować śledzenie rekordów.</span><span class="sxs-lookup"><span data-stu-id="67818-116">A collection of configuration elements defining participants that subscribe to tracking records.</span></span> <span data-ttu-id="67818-117">Uczestników śledzenia zawierają logikę przetwarzania ładunku z rekordów śledzenia (na przykład ich można zapisać do pliku).</span><span class="sxs-lookup"><span data-stu-id="67818-117">The tracking participants contain the logic to process the payload from the tracking records (for example, they could choose to write to a file).</span></span>|  
|[<span data-ttu-id="67818-118">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="67818-118">\<trackingProfile></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/trackingprofile.md)|<span data-ttu-id="67818-119">Profil śledzenia do filtrowania rekordów śledzenia emitowane z wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="67818-119">A tracking profile to filter tracking records emitted from a workflow instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="67818-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="67818-120">Parent Elements</span></span>  
  
|<span data-ttu-id="67818-121">Element</span><span class="sxs-lookup"><span data-stu-id="67818-121">Element</span></span>|<span data-ttu-id="67818-122">Opis</span><span class="sxs-lookup"><span data-stu-id="67818-122">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="67818-123">System.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="67818-123">system.ServiceModel</span></span>|<span data-ttu-id="67818-124">Element główny wszystkich elementów konfiguracji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="67818-124">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="67818-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="67818-125">Remarks</span></span>  
 <span data-ttu-id="67818-126">Śledzenie umożliwia należy sprawdzić, czy wykonywania przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="67818-126">Tracking provides you with the ability to examine the execution of a workflow.</span></span> <span data-ttu-id="67818-127">Infrastruktura śledzenia przepływu pracy instruments przepływu pracy, aby emitować rekordów odzwierciedlający kluczy zdarzeń podczas wykonywania.</span><span class="sxs-lookup"><span data-stu-id="67818-127">The workflow tracking infrastructure instruments a workflow to emit records reflecting key events during the execution.</span></span> <span data-ttu-id="67818-128">Na przykład podczas uruchamiania wystąpienia przepływu pracy, lub zakończeniu są emitowane rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="67818-128">For example, when a workflow instance starts or completes tracking records are emitted.</span></span> <span data-ttu-id="67818-129">Śledzenie również można wyodrębnić business odpowiednie dane skojarzone z zmienne przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="67818-129">Tracking can also extract business relevant data associated with the workflow variables.</span></span> <span data-ttu-id="67818-130">Na przykład jeśli przepływ pracy reprezentuje kolejność przetwarzania systemu identyfikator zamówienia można wyodrębnić wraz z rekordem śledzenia.</span><span class="sxs-lookup"><span data-stu-id="67818-130">For example, if the workflow represents an order processing system the order id can be extracted along with the tracking record.</span></span> <span data-ttu-id="67818-131">Ogólnie rzecz biorąc włączania WF śledzenia umożliwia wykonywanie operacji diagnostyki lub analiz biznesowych za wykonywanie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="67818-131">In general, enabling WF tracking facilitates diagnostics or business analytics over a workflow execution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67818-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="67818-132">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection?displayProperty=nameWithType>       
 [<span data-ttu-id="67818-133">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="67818-133">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
