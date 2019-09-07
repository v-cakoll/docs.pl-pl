---
title: <tracking>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: fd9b50ed-98a1-4518-836d-e4e02c670822
ms.openlocfilehash: 28d73bb74c4a49052589040adc26194b1300668c
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397603"
---
# <a name="tracking"></a><span data-ttu-id="a3153-101">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="a3153-101">\<tracking></span></span>
<span data-ttu-id="a3153-102">Reprezentuje sekcję konfiguracji do definiowania ustawień śledzenia dla usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="a3153-102">Represents a configuration section for defining tracking settings for a workflow service.</span></span>  
  
 <span data-ttu-id="a3153-103">Aby uzyskać więcej informacji na temat śledzenia przepływu pracy i jego konfiguracji, zobacz [śledzenie i śledzenie przepływów pracy](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) oraz [Konfigurowanie śledzenia dla przepływu pracy](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="a3153-103">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Configuring Tracking for a Workflow](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>  
  
<span data-ttu-id="a3153-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a3153-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a3153-105">&nbsp;&nbsp;[ **\<systemami. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="a3153-105">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="a3153-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<Śledzenie >**</span><span class="sxs-lookup"><span data-stu-id="a3153-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<tracking>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3153-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="a3153-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a3153-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a3153-108">Attributes and Elements</span></span>  
 <span data-ttu-id="a3153-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a3153-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a3153-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a3153-110">Attributes</span></span>  
 <span data-ttu-id="a3153-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="a3153-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a3153-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a3153-112">Child Elements</span></span>  
  
|<span data-ttu-id="a3153-113">Element</span><span class="sxs-lookup"><span data-stu-id="a3153-113">Element</span></span>|<span data-ttu-id="a3153-114">Opis</span><span class="sxs-lookup"><span data-stu-id="a3153-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a3153-115">\<Uczestnicy ></span><span class="sxs-lookup"><span data-stu-id="a3153-115">\<participants></span></span>](participants.md)|<span data-ttu-id="a3153-116">Kolekcja elementów konfiguracji definiujących uczestników, którzy subskrybują śledzenie rekordów.</span><span class="sxs-lookup"><span data-stu-id="a3153-116">A collection of configuration elements defining participants that subscribe to tracking records.</span></span> <span data-ttu-id="a3153-117">Uczestnicy śledzenia zawierają logikę do przetwarzania ładunku z rekordów śledzenia (na przykład mogą wybrać zapis w pliku).</span><span class="sxs-lookup"><span data-stu-id="a3153-117">The tracking participants contain the logic to process the payload from the tracking records (for example, they could choose to write to a file).</span></span>|  
|[<span data-ttu-id="a3153-118">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="a3153-118">\<trackingProfile></span></span>](trackingprofile.md)|<span data-ttu-id="a3153-119">Profil śledzenia do filtrowania rekordów śledzenia emitowane z wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="a3153-119">A tracking profile to filter tracking records emitted from a workflow instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a3153-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a3153-120">Parent Elements</span></span>  
  
|<span data-ttu-id="a3153-121">Element</span><span class="sxs-lookup"><span data-stu-id="a3153-121">Element</span></span>|<span data-ttu-id="a3153-122">Opis</span><span class="sxs-lookup"><span data-stu-id="a3153-122">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a3153-123">System.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="a3153-123">system.ServiceModel</span></span>|<span data-ttu-id="a3153-124">Element główny wszystkich elementów konfiguracji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="a3153-124">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a3153-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a3153-125">Remarks</span></span>  
 <span data-ttu-id="a3153-126">Śledzenie umożliwia należy sprawdzić, czy wykonywania przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="a3153-126">Tracking provides you with the ability to examine the execution of a workflow.</span></span> <span data-ttu-id="a3153-127">Infrastruktura śledzenia przepływu pracy instruments przepływu pracy, aby emitować rekordów odzwierciedlający kluczy zdarzeń podczas wykonywania.</span><span class="sxs-lookup"><span data-stu-id="a3153-127">The workflow tracking infrastructure instruments a workflow to emit records reflecting key events during the execution.</span></span> <span data-ttu-id="a3153-128">Na przykład po uruchomieniu wystąpienia przepływu pracy lub zakończeniu śledzenia rekordy są emitowane.</span><span class="sxs-lookup"><span data-stu-id="a3153-128">For example, when a workflow instance starts or completes tracking records are emitted.</span></span> <span data-ttu-id="a3153-129">Śledzenie również można wyodrębnić business odpowiednie dane skojarzone z zmienne przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="a3153-129">Tracking can also extract business relevant data associated with the workflow variables.</span></span> <span data-ttu-id="a3153-130">Na przykład, jeśli przepływ pracy reprezentuje system przetwarzania zamówień, można wyodrębnić identyfikator zamówienia wraz z rekordem śledzenia.</span><span class="sxs-lookup"><span data-stu-id="a3153-130">For example, if the workflow represents an order processing system the order id can be extracted along with the tracking record.</span></span> <span data-ttu-id="a3153-131">Ogólnie rzecz biorąc włączania WF śledzenia umożliwia wykonywanie operacji diagnostyki lub analiz biznesowych za wykonywanie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="a3153-131">In general, enabling WF tracking facilitates diagnostics or business analytics over a workflow execution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3153-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a3153-132">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection?displayProperty=nameWithType>
- [<span data-ttu-id="a3153-133">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="a3153-133">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
