---
title: <tracking>programu WCF
ms.date: 03/30/2017
ms.assetid: 70cfaf24-a91c-4e56-ac47-d2ed87a963b3
ms.openlocfilehash: e8f74d635299a965b754536234e6be28e4e7a104
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399419"
---
# <a name="tracking-of-wcf"></a><span data-ttu-id="24b4a-102">\<Śledzenie > WCF</span><span class="sxs-lookup"><span data-stu-id="24b4a-102">\<tracking> of WCF</span></span>
<span data-ttu-id="24b4a-103">Reprezentuje sekcję konfiguracji do definiowania ustawień śledzenia dla usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="24b4a-103">Represents a configuration section for defining tracking settings for a workflow service.</span></span>  
  
 <span data-ttu-id="24b4a-104">Aby uzyskać więcej informacji na temat śledzenia przepływu pracy i jego konfiguracji, zobacz [śledzenie i śledzenie przepływów pracy](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) oraz [Konfigurowanie śledzenia dla przepływu pracy](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="24b4a-104">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Configuring Tracking for a Workflow](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>  
  
<span data-ttu-id="24b4a-105">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="24b4a-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="24b4a-106">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="24b4a-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="24b4a-107">&nbsp;&nbsp;&nbsp;&nbsp; **\<Śledzenie >**</span><span class="sxs-lookup"><span data-stu-id="24b4a-107">&nbsp;&nbsp;&nbsp;&nbsp;**\<tracking>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24b4a-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="24b4a-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="24b4a-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="24b4a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="24b4a-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="24b4a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="24b4a-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="24b4a-111">Attributes</span></span>  
 <span data-ttu-id="24b4a-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="24b4a-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="24b4a-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="24b4a-113">Child Elements</span></span>  
  
|<span data-ttu-id="24b4a-114">Element</span><span class="sxs-lookup"><span data-stu-id="24b4a-114">Element</span></span>|<span data-ttu-id="24b4a-115">Opis</span><span class="sxs-lookup"><span data-stu-id="24b4a-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="24b4a-116">\<Uczestnicy ></span><span class="sxs-lookup"><span data-stu-id="24b4a-116">\<participants></span></span>](../windows-workflow-foundation/participants.md)|<span data-ttu-id="24b4a-117">Kolekcja elementów konfiguracji definiujących uczestników, którzy subskrybują śledzenie rekordów.</span><span class="sxs-lookup"><span data-stu-id="24b4a-117">A collection of configuration elements defining participants that subscribe to tracking records.</span></span> <span data-ttu-id="24b4a-118">Uczestnicy śledzenia zawierają logikę do przetwarzania ładunku z rekordów śledzenia (na przykład mogą wybrać zapis w pliku).</span><span class="sxs-lookup"><span data-stu-id="24b4a-118">The tracking participants contain the logic to process the payload from the tracking records (for example, they could choose to write to a file).</span></span>|  
|[<span data-ttu-id="24b4a-119">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="24b4a-119">\<trackingProfile></span></span>](../windows-workflow-foundation/trackingprofile.md)|<span data-ttu-id="24b4a-120">Profil śledzenia do filtrowania rekordów śledzenia emitowane z wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="24b4a-120">A tracking profile to filter tracking records emitted from a workflow instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="24b4a-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="24b4a-121">Parent Elements</span></span>  
  
|<span data-ttu-id="24b4a-122">Element</span><span class="sxs-lookup"><span data-stu-id="24b4a-122">Element</span></span>|<span data-ttu-id="24b4a-123">Opis</span><span class="sxs-lookup"><span data-stu-id="24b4a-123">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="24b4a-124">System.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="24b4a-124">system.ServiceModel</span></span>|<span data-ttu-id="24b4a-125">Element główny wszystkich elementów konfiguracji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="24b4a-125">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="24b4a-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="24b4a-126">Remarks</span></span>  
 <span data-ttu-id="24b4a-127">Śledzenie umożliwia należy sprawdzić, czy wykonywania przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="24b4a-127">Tracking provides you with the ability to examine the execution of a workflow.</span></span> <span data-ttu-id="24b4a-128">Infrastruktura śledzenia przepływu pracy instruments przepływu pracy, aby emitować rekordów odzwierciedlający kluczy zdarzeń podczas wykonywania.</span><span class="sxs-lookup"><span data-stu-id="24b4a-128">The workflow tracking infrastructure instruments a workflow to emit records reflecting key events during the execution.</span></span> <span data-ttu-id="24b4a-129">Na przykład po uruchomieniu wystąpienia przepływu pracy lub zakończeniu śledzenia rekordy są emitowane.</span><span class="sxs-lookup"><span data-stu-id="24b4a-129">For example, when a workflow instance starts or completes tracking records are emitted.</span></span> <span data-ttu-id="24b4a-130">Śledzenie również można wyodrębnić business odpowiednie dane skojarzone z zmienne przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="24b4a-130">Tracking can also extract business relevant data associated with the workflow variables.</span></span> <span data-ttu-id="24b4a-131">Na przykład, jeśli przepływ pracy reprezentuje system przetwarzania zamówień, można wyodrębnić identyfikator zamówienia wraz z rekordem śledzenia.</span><span class="sxs-lookup"><span data-stu-id="24b4a-131">For example, if the workflow represents an order processing system the order id can be extracted along with the tracking record.</span></span> <span data-ttu-id="24b4a-132">Ogólnie rzecz biorąc włączania WF śledzenia umożliwia wykonywanie operacji diagnostyki lub analiz biznesowych za wykonywanie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="24b4a-132">In general, enabling WF tracking facilitates diagnostics or business analytics over a workflow execution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24b4a-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="24b4a-133">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection?displayProperty=nameWithType>
- [<span data-ttu-id="24b4a-134">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="24b4a-134">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
