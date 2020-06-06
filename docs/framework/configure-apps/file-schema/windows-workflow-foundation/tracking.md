---
title: <tracking>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: fd9b50ed-98a1-4518-836d-e4e02c670822
ms.openlocfilehash: 968cfa8e5402458afd6f13545ed999a472adf2e0
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79151913"
---
# \<tracking>
<span data-ttu-id="c6cb1-101">Reprezentuje sekcję konfiguracji do definiowania ustawień śledzenia dla usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="c6cb1-101">Represents a configuration section for defining tracking settings for a workflow service.</span></span>  
  
 <span data-ttu-id="c6cb1-102">Aby uzyskać więcej informacji na temat śledzenia przepływu pracy i jego konfiguracji, zobacz [śledzenie i śledzenie przepływów pracy](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) oraz [Konfigurowanie śledzenia dla przepływu pracy](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="c6cb1-102">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Configuring Tracking for a Workflow](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<tracking>**  
  
## <a name="syntax"></a><span data-ttu-id="c6cb1-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="c6cb1-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c6cb1-104">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c6cb1-104">Attributes and Elements</span></span>  
 <span data-ttu-id="c6cb1-105">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c6cb1-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c6cb1-106">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c6cb1-106">Attributes</span></span>  
 <span data-ttu-id="c6cb1-107">Brak.</span><span class="sxs-lookup"><span data-stu-id="c6cb1-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c6cb1-108">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c6cb1-108">Child Elements</span></span>  
  
|<span data-ttu-id="c6cb1-109">Element</span><span class="sxs-lookup"><span data-stu-id="c6cb1-109">Element</span></span>|<span data-ttu-id="c6cb1-110">Opis</span><span class="sxs-lookup"><span data-stu-id="c6cb1-110">Description</span></span>|  
|-------------|-----------------|  
|[\<participants>](participants.md)|<span data-ttu-id="c6cb1-111">Kolekcja elementów konfiguracji definiujących uczestników, którzy subskrybują śledzenie rekordów.</span><span class="sxs-lookup"><span data-stu-id="c6cb1-111">A collection of configuration elements defining participants that subscribe to tracking records.</span></span> <span data-ttu-id="c6cb1-112">Uczestnicy śledzenia zawierają logikę do przetwarzania ładunku z rekordów śledzenia (na przykład mogą wybrać zapis w pliku).</span><span class="sxs-lookup"><span data-stu-id="c6cb1-112">The tracking participants contain the logic to process the payload from the tracking records (for example, they could choose to write to a file).</span></span>|  
|[\<trackingProfile>](trackingprofile.md)|<span data-ttu-id="c6cb1-113">Profil śledzenia do filtrowania rekordów śledzenia emitowane z wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="c6cb1-113">A tracking profile to filter tracking records emitted from a workflow instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c6cb1-114">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c6cb1-114">Parent Elements</span></span>  
  
|<span data-ttu-id="c6cb1-115">Element</span><span class="sxs-lookup"><span data-stu-id="c6cb1-115">Element</span></span>|<span data-ttu-id="c6cb1-116">Opis</span><span class="sxs-lookup"><span data-stu-id="c6cb1-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c6cb1-117">System.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="c6cb1-117">system.ServiceModel</span></span>|<span data-ttu-id="c6cb1-118">Element główny wszystkich elementów konfiguracji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="c6cb1-118">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c6cb1-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c6cb1-119">Remarks</span></span>  
 <span data-ttu-id="c6cb1-120">Śledzenie umożliwia należy sprawdzić, czy wykonywania przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="c6cb1-120">Tracking provides you with the ability to examine the execution of a workflow.</span></span> <span data-ttu-id="c6cb1-121">Infrastruktura śledzenia przepływu pracy instruments przepływu pracy, aby emitować rekordów odzwierciedlający kluczy zdarzeń podczas wykonywania.</span><span class="sxs-lookup"><span data-stu-id="c6cb1-121">The workflow tracking infrastructure instruments a workflow to emit records reflecting key events during the execution.</span></span> <span data-ttu-id="c6cb1-122">Na przykład po uruchomieniu wystąpienia przepływu pracy lub zakończeniu śledzenia rekordy są emitowane.</span><span class="sxs-lookup"><span data-stu-id="c6cb1-122">For example, when a workflow instance starts or completes tracking records are emitted.</span></span> <span data-ttu-id="c6cb1-123">Śledzenie również można wyodrębnić business odpowiednie dane skojarzone z zmienne przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="c6cb1-123">Tracking can also extract business relevant data associated with the workflow variables.</span></span> <span data-ttu-id="c6cb1-124">Na przykład, jeśli przepływ pracy reprezentuje system przetwarzania zamówień, można wyodrębnić identyfikator zamówienia wraz z rekordem śledzenia.</span><span class="sxs-lookup"><span data-stu-id="c6cb1-124">For example, if the workflow represents an order processing system the order id can be extracted along with the tracking record.</span></span> <span data-ttu-id="c6cb1-125">Ogólnie rzecz biorąc włączania WF śledzenia umożliwia wykonywanie operacji diagnostyki lub analiz biznesowych za wykonywanie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="c6cb1-125">In general, enabling WF tracking facilitates diagnostics or business analytics over a workflow execution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6cb1-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c6cb1-126">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection?displayProperty=nameWithType>
- [<span data-ttu-id="c6cb1-127">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="c6cb1-127">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
