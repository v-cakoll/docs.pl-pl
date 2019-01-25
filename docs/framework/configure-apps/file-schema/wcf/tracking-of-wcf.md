---
title: '&lt;tracking&gt; w WCF'
ms.date: 03/30/2017
ms.assetid: 70cfaf24-a91c-4e56-ac47-d2ed87a963b3
ms.openlocfilehash: 52efc1b5284c2a64eae30ea18995e5ee761dc2e7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54582607"
---
# <a name="lttrackinggt-of-wcf"></a><span data-ttu-id="8e83d-102">&lt;tracking&gt; w WCF</span><span class="sxs-lookup"><span data-stu-id="8e83d-102">&lt;tracking&gt; of WCF</span></span>
<span data-ttu-id="8e83d-103">Reprezentuje sekcję konfiguracji do definiowania ustawień śledzenia dla usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="8e83d-103">Represents a configuration section for defining tracking settings for a workflow service.</span></span>  
  
 <span data-ttu-id="8e83d-104">Aby uzyskać więcej informacji śledzenia przepływu pracy i jego konfiguracji, zobacz [przepływu pracy i śledzenie](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) i [Konfigurowanie śledzenia przepływu pracy](../../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="8e83d-104">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Configuring Tracking for a Workflow](../../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>  
  
 <span data-ttu-id="8e83d-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="8e83d-105">\<system.serviceModel></span></span>  
<span data-ttu-id="8e83d-106">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="8e83d-106">\<tracking></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e83d-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="8e83d-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <tracking>
    <participants>
      <add name="String"
           profileName="String"
           type="String" />
    </participants>
    <profiles>
      <trackingProfile name="String">
        <workflow activityDefinitionId="String">
          <activityScheduledQueries>
            <activityScheduledQuery activityName="String"
                                    childActivityName="String"/>
          </activityScheduledQueries>
          <activityStateQueries>
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
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8e83d-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="8e83d-108">Attributes and Elements</span></span>  
 <span data-ttu-id="8e83d-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="8e83d-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8e83d-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="8e83d-110">Attributes</span></span>  
 <span data-ttu-id="8e83d-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="8e83d-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8e83d-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="8e83d-112">Child Elements</span></span>  
  
|<span data-ttu-id="8e83d-113">Element</span><span class="sxs-lookup"><span data-stu-id="8e83d-113">Element</span></span>|<span data-ttu-id="8e83d-114">Opis</span><span class="sxs-lookup"><span data-stu-id="8e83d-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8e83d-115">\<Uczestnicy ></span><span class="sxs-lookup"><span data-stu-id="8e83d-115">\<participants></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md)|<span data-ttu-id="8e83d-116">Kolekcja elementów konfiguracji definiowania uczestników subskrybowania śledzenie rekordów.</span><span class="sxs-lookup"><span data-stu-id="8e83d-116">A collection of configuration elements defining participants that subscribe to tracking records.</span></span> <span data-ttu-id="8e83d-117">Uczestnicy śledzenia zawiera logikę do przetwarzania ładunku z rekordów śledzenia (na przykład ich można wybrać do zapisu do pliku).</span><span class="sxs-lookup"><span data-stu-id="8e83d-117">The tracking participants contain the logic to process the payload from the tracking records (for example, they could choose to write to a file).</span></span>|  
|[<span data-ttu-id="8e83d-118">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="8e83d-118">\<trackingProfile></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/trackingprofile.md)|<span data-ttu-id="8e83d-119">Profil śledzenia do filtrowania rekordów śledzenia emitowane z wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="8e83d-119">A tracking profile to filter tracking records emitted from a workflow instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8e83d-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="8e83d-120">Parent Elements</span></span>  
  
|<span data-ttu-id="8e83d-121">Element</span><span class="sxs-lookup"><span data-stu-id="8e83d-121">Element</span></span>|<span data-ttu-id="8e83d-122">Opis</span><span class="sxs-lookup"><span data-stu-id="8e83d-122">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8e83d-123">System.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="8e83d-123">system.ServiceModel</span></span>|<span data-ttu-id="8e83d-124">Element główny wszystkich elementów konfiguracji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="8e83d-124">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8e83d-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8e83d-125">Remarks</span></span>  
 <span data-ttu-id="8e83d-126">Śledzenie umożliwia należy sprawdzić, czy wykonywania przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="8e83d-126">Tracking provides you with the ability to examine the execution of a workflow.</span></span> <span data-ttu-id="8e83d-127">Infrastruktura śledzenia przepływu pracy instruments przepływu pracy, aby emitować rekordów odzwierciedlający kluczy zdarzeń podczas wykonywania.</span><span class="sxs-lookup"><span data-stu-id="8e83d-127">The workflow tracking infrastructure instruments a workflow to emit records reflecting key events during the execution.</span></span> <span data-ttu-id="8e83d-128">Na przykład gdy wystąpienie przepływu pracy rozpoczyna się lub kończy są emitowane rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="8e83d-128">For example, when a workflow instance starts or completes tracking records are emitted.</span></span> <span data-ttu-id="8e83d-129">Śledzenie również można wyodrębnić business odpowiednie dane skojarzone z zmienne przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="8e83d-129">Tracking can also extract business relevant data associated with the workflow variables.</span></span> <span data-ttu-id="8e83d-130">Na przykład jeśli przepływ pracy reprezentuje kolejność przetwarzania systemu identyfikator zamówienia wyodrębniania wraz z rekordem śledzenia.</span><span class="sxs-lookup"><span data-stu-id="8e83d-130">For example, if the workflow represents an order processing system the order id can be extracted along with the tracking record.</span></span> <span data-ttu-id="8e83d-131">Ogólnie rzecz biorąc włączania WF śledzenia umożliwia wykonywanie operacji diagnostyki lub analiz biznesowych za wykonywanie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="8e83d-131">In general, enabling WF tracking facilitates diagnostics or business analytics over a workflow execution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e83d-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8e83d-132">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection?displayProperty=nameWithType>
- [<span data-ttu-id="8e83d-133">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="8e83d-133">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
