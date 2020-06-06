---
title: <trackingProfile>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 154830ff-ddd3-4397-a3b5-5b334907777f
ms.openlocfilehash: 8985da7e1223ac117cf1b68227140634f9c85d3a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79151892"
---
# \<trackingProfile>
<span data-ttu-id="addba-101">Reprezentuje sekcję konfiguracji służącą do tworzenia subskrypcji dla rekordów śledzenia przepływu pracy w uczestniku śledzenia.</span><span class="sxs-lookup"><span data-stu-id="addba-101">Represents a configuration section for creating a subscription to workflow tracking records in a tracking participant.</span></span> <span data-ttu-id="addba-102">Profil śledzenia zawiera śledzenia zapytań, pozwalające uczestnikiem śledzenia do subskrybowania zdarzenia przepływu pracy, które są emitowane po zmianie stanu wystąpienia przepływu pracy w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="addba-102">A tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="addba-103">Kwerendy zdefiniowane w profilu śledzenia sekcji zdefiniować rodzaje zdarzenia, które są zwracane w subskrypcji.</span><span class="sxs-lookup"><span data-stu-id="addba-103">The queries defined within the tracking profile section define the kinds of events that are returned by the subscription.</span></span>  
  
 <span data-ttu-id="addba-104">Aby uzyskać więcej informacji na temat śledzenia przepływu pracy i jego konfiguracji, zobacz [śledzenie przepływów pracy i](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) śledzenie i [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="addba-104">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<trackingProfile>**  
  
## <a name="syntax"></a><span data-ttu-id="addba-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="addba-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="addba-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="addba-106">Attributes and Elements</span></span>  
 <span data-ttu-id="addba-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="addba-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="addba-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="addba-108">Attributes</span></span>  
  
|<span data-ttu-id="addba-109">Atrybut</span><span class="sxs-lookup"><span data-stu-id="addba-109">Attribute</span></span>|<span data-ttu-id="addba-110">Opis</span><span class="sxs-lookup"><span data-stu-id="addba-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="addba-111">name</span><span class="sxs-lookup"><span data-stu-id="addba-111">name</span></span>|<span data-ttu-id="addba-112">Ciąg określający nazwę profilu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="addba-112">A string that specifies the name of the tracking profile.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="addba-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="addba-113">Child Elements</span></span>  
  
|<span data-ttu-id="addba-114">Element</span><span class="sxs-lookup"><span data-stu-id="addba-114">Element</span></span>|<span data-ttu-id="addba-115">Opis</span><span class="sxs-lookup"><span data-stu-id="addba-115">Description</span></span>|  
|-------------|-----------------|  
|[\<participants>](participants.md)|<span data-ttu-id="addba-116">Element konfiguracji, który zawiera wszystkie zapytania dla określonego przepływu pracy identyfikowane przez <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="addba-116">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId%2A?displayProperty=nameWithType> property.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="addba-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="addba-117">Parent Elements</span></span>  
  
|<span data-ttu-id="addba-118">Element</span><span class="sxs-lookup"><span data-stu-id="addba-118">Element</span></span>|<span data-ttu-id="addba-119">Opis</span><span class="sxs-lookup"><span data-stu-id="addba-119">Description</span></span>|  
|-------------|-----------------|  
|[\<tracking>](tracking.md)|<span data-ttu-id="addba-120">Reprezentuje sekcję konfiguracji do definiowania ustawień śledzenia dla usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="addba-120">Represents a configuration section for defining tracking settings for a workflow service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="addba-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="addba-121">Remarks</span></span>  
 <span data-ttu-id="addba-122">Śledzenie profile zawiera śledzenia zapytań, pozwalające uczestnikiem śledzenia do subskrybowania zdarzenia przepływu pracy, które są emitowane po zmianie stanu wystąpienia przepływu pracy w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="addba-122">Tracking profiles contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="addba-123">W zależności od potrzeb może zapisu profil przybliżonego, które subskrybuje niewielkiego zestawu zmian stanu wysokiego poziomu przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="addba-123">Depending on your monitoring requirements you may write a profile that is very coarse, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="addba-124">Z drugiej strony można utworzyć bardzo określony profil którego wynikowego zdarzenia są rozbudowanych, odtworzenie przepływ wykonania szczegółowe później.</span><span class="sxs-lookup"><span data-stu-id="addba-124">Conversely, you may create a very specific profile whose resulting events are rich enough to reconstruct a detailed execution flow later.</span></span>  
  
 <span data-ttu-id="addba-125">Profile śledzenia mają strukturę jako deklaratywne subskrypcji dla śledzenia rekordy, które umożliwiają zapytania dla rekordów śledzenie wersję wykonawczą przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="addba-125">Tracking profiles are structured as declarative subscriptions for tracking records that allow you to query the workflow runtime for specific tracking records.</span></span> <span data-ttu-id="addba-126">Istnieje kilku typów zapytań, które umożliwiają subskrybowanie różnych klas <xref:System.Activities.Tracking.TrackingRecord> obiektów.</span><span class="sxs-lookup"><span data-stu-id="addba-126">There are a handful of query types that allow you subscribe to different classes of <xref:System.Activities.Tracking.TrackingRecord> objects.</span></span> <span data-ttu-id="addba-127">Aby uzyskać pełną listę zapytań, zobacz [\<participants>](participants.md) i [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md)..</span><span class="sxs-lookup"><span data-stu-id="addba-127">For a complete list of queries, see [\<participants>](participants.md) and [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)..</span></span>  
  
 <span data-ttu-id="addba-128">Poniższy przykład przedstawia profil śledzenia w pliku konfiguracji, który umożliwia śledzenie uczestnika subskrybowanie `Started` `Completed` zdarzeń przepływu pracy i.</span><span class="sxs-lookup"><span data-stu-id="addba-128">The following example shows a tracking profile in a configuration file that allows a tracking participant to subscribe to the `Started` and `Completed` workflow events.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="addba-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="addba-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileElement>
- <xref:System.Activities.Tracking.TrackingProfile>
- [<span data-ttu-id="addba-130">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="addba-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="addba-131">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="addba-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
