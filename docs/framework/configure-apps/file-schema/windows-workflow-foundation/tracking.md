---
title: <tracking>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: fd9b50ed-98a1-4518-836d-e4e02c670822
ms.openlocfilehash: 31490c7425572909cc30fe4237af9309754b68e4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59072248"
---
# <a name="tracking"></a><span data-ttu-id="e4135-101">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="e4135-101">\<tracking></span></span>
<span data-ttu-id="e4135-102">Reprezentuje sekcję konfiguracji do definiowania ustawień śledzenia dla usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="e4135-102">Represents a configuration section for defining tracking settings for a workflow service.</span></span>  
  
 <span data-ttu-id="e4135-103">Aby uzyskać więcej informacji śledzenia przepływu pracy i jego konfiguracji, zobacz [przepływu pracy i śledzenie](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) i [Konfigurowanie śledzenia przepływu pracy](../../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="e4135-103">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Configuring Tracking for a Workflow](../../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>  
  
<span data-ttu-id="e4135-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="e4135-104">\<system.serviceModel></span></span>  
<span data-ttu-id="e4135-105">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="e4135-105">\<tracking></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4135-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="e4135-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e4135-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e4135-107">Attributes and Elements</span></span>  
 <span data-ttu-id="e4135-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e4135-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e4135-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e4135-109">Attributes</span></span>  
 <span data-ttu-id="e4135-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="e4135-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e4135-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e4135-111">Child Elements</span></span>  
  
|<span data-ttu-id="e4135-112">Element</span><span class="sxs-lookup"><span data-stu-id="e4135-112">Element</span></span>|<span data-ttu-id="e4135-113">Opis</span><span class="sxs-lookup"><span data-stu-id="e4135-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e4135-114">\<Uczestnicy ></span><span class="sxs-lookup"><span data-stu-id="e4135-114">\<participants></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md)|<span data-ttu-id="e4135-115">Kolekcja elementów konfiguracji definiowania uczestników subskrybowania śledzenie rekordów.</span><span class="sxs-lookup"><span data-stu-id="e4135-115">A collection of configuration elements defining participants that subscribe to tracking records.</span></span> <span data-ttu-id="e4135-116">Uczestnicy śledzenia zawiera logikę do przetwarzania ładunku z rekordów śledzenia (na przykład ich można wybrać do zapisu do pliku).</span><span class="sxs-lookup"><span data-stu-id="e4135-116">The tracking participants contain the logic to process the payload from the tracking records (for example, they could choose to write to a file).</span></span>|  
|[<span data-ttu-id="e4135-117">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="e4135-117">\<trackingProfile></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/trackingprofile.md)|<span data-ttu-id="e4135-118">Profil śledzenia do filtrowania rekordów śledzenia emitowane z wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="e4135-118">A tracking profile to filter tracking records emitted from a workflow instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e4135-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e4135-119">Parent Elements</span></span>  
  
|<span data-ttu-id="e4135-120">Element</span><span class="sxs-lookup"><span data-stu-id="e4135-120">Element</span></span>|<span data-ttu-id="e4135-121">Opis</span><span class="sxs-lookup"><span data-stu-id="e4135-121">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e4135-122">System.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="e4135-122">system.ServiceModel</span></span>|<span data-ttu-id="e4135-123">Element główny wszystkich elementów konfiguracji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="e4135-123">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e4135-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e4135-124">Remarks</span></span>  
 <span data-ttu-id="e4135-125">Śledzenie umożliwia należy sprawdzić, czy wykonywania przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="e4135-125">Tracking provides you with the ability to examine the execution of a workflow.</span></span> <span data-ttu-id="e4135-126">Infrastruktura śledzenia przepływu pracy instruments przepływu pracy, aby emitować rekordów odzwierciedlający kluczy zdarzeń podczas wykonywania.</span><span class="sxs-lookup"><span data-stu-id="e4135-126">The workflow tracking infrastructure instruments a workflow to emit records reflecting key events during the execution.</span></span> <span data-ttu-id="e4135-127">Na przykład gdy wystąpienie przepływu pracy rozpoczyna się lub kończy są emitowane rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="e4135-127">For example, when a workflow instance starts or completes tracking records are emitted.</span></span> <span data-ttu-id="e4135-128">Śledzenie również można wyodrębnić business odpowiednie dane skojarzone z zmienne przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="e4135-128">Tracking can also extract business relevant data associated with the workflow variables.</span></span> <span data-ttu-id="e4135-129">Na przykład jeśli przepływ pracy reprezentuje kolejność przetwarzania systemu identyfikator zamówienia wyodrębniania wraz z rekordem śledzenia.</span><span class="sxs-lookup"><span data-stu-id="e4135-129">For example, if the workflow represents an order processing system the order id can be extracted along with the tracking record.</span></span> <span data-ttu-id="e4135-130">Ogólnie rzecz biorąc włączania WF śledzenia umożliwia wykonywanie operacji diagnostyki lub analiz biznesowych za wykonywanie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="e4135-130">In general, enabling WF tracking facilitates diagnostics or business analytics over a workflow execution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4135-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e4135-131">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection?displayProperty=nameWithType>
- [<span data-ttu-id="e4135-132">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="e4135-132">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
