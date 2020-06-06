---
title: <trackingProfile>programu WCF
ms.date: 10/08/2018
ms.assetid: 09b651c2-c0d2-4850-a101-b0e009a1dc3a
ms.openlocfilehash: c5df03d63653e658a23a36e8943c06f156d2ae00
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70854942"
---
# <a name="trackingprofile-of-wcf"></a><span data-ttu-id="1a30d-102">\<trackingProfile>programu WCF</span><span class="sxs-lookup"><span data-stu-id="1a30d-102">\<trackingProfile> of WCF</span></span>
<span data-ttu-id="1a30d-103">Reprezentuje sekcję konfiguracji służącą do tworzenia subskrypcji dla rekordów śledzenia przepływu pracy w uczestniku śledzenia.</span><span class="sxs-lookup"><span data-stu-id="1a30d-103">Represents a configuration section for creating a subscription to workflow tracking records in a tracking participant.</span></span> <span data-ttu-id="1a30d-104">Profil śledzenia zawiera śledzenia zapytań, pozwalające uczestnikiem śledzenia do subskrybowania zdarzenia przepływu pracy, które są emitowane po zmianie stanu wystąpienia przepływu pracy w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="1a30d-104">A tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="1a30d-105">Kwerendy zdefiniowane w profilu śledzenia sekcji zdefiniować rodzaje zdarzenia, które są zwracane w subskrypcji.</span><span class="sxs-lookup"><span data-stu-id="1a30d-105">The queries defined within the tracking profile section define the kinds of events that are returned by the subscription.</span></span>  
  
<span data-ttu-id="1a30d-106">Aby uzyskać więcej informacji na temat śledzenia przepływu pracy i jego konfiguracji, zobacz [śledzenie przepływów pracy i](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) śledzenie i [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="1a30d-106">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<trackingProfile>**  
  
## <a name="syntax"></a><span data-ttu-id="1a30d-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="1a30d-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <tracking>
    <profiles>
      <trackingProfile name="String">
        <workflow activityDefinitionId="String">
          <activityScheduledQueries>
            <activityScheduledQuery activityName="String"
                                    childActivityName="String" />
          </activityScheduledQueries>
          <activityStateQueries>
            <activityStateQuery activityName="String">
              <arguments>
                <argument name="String" />
              </arguments>
              <states>
                <state name="String" />
              </states>
              <variables>
                <variable name="String" />
              </variables>
            </activityStateQuery>
          </activityStateQueries>
          <bookmarkResumptionQueries>
            <bookmarkResumptionQuery name="String" />
          </bookmarkResumptionQueries>
          <cancelRequestedQueries>
            <cancelRequestedQuery activityName="String"
                                  childActivityName="String" />
          </cancelRequestedQueries>
          <customTrackingQueries>
            <customTrackingQuery activityName="String"
                                 name="String" />
          </customTrackingQueries>
          <faultPropagationQueries>
            <faultPropagationQuery faultSourceActivityName="String"
                                   faultHandlerActivityName="String" />
          </faultPropagationQueries>
          <stateMachineStateQueries>
            <stateMachineStateQuery activityName="String" />
          </stateMachineStateQueries>
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1a30d-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1a30d-108">Attributes and Elements</span></span>  

<span data-ttu-id="1a30d-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="1a30d-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1a30d-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1a30d-110">Attributes</span></span>  
  
|<span data-ttu-id="1a30d-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="1a30d-111">Attribute</span></span>|<span data-ttu-id="1a30d-112">Opis</span><span class="sxs-lookup"><span data-stu-id="1a30d-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1a30d-113">name</span><span class="sxs-lookup"><span data-stu-id="1a30d-113">name</span></span>|<span data-ttu-id="1a30d-114">Ciąg określający nazwę profilu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="1a30d-114">A string that specifies the name of the tracking profile.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1a30d-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1a30d-115">Child Elements</span></span>  
  
|<span data-ttu-id="1a30d-116">Element</span><span class="sxs-lookup"><span data-stu-id="1a30d-116">Element</span></span>|<span data-ttu-id="1a30d-117">Opis</span><span class="sxs-lookup"><span data-stu-id="1a30d-117">Description</span></span>|  
|-------------|-----------------|  
|[\<participants>](../windows-workflow-foundation/participants.md)|<span data-ttu-id="1a30d-118">Element konfiguracji, który zawiera wszystkie zapytania dla określonego przepływu pracy identyfikowane przez <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="1a30d-118">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId?displayProperty=nameWithType> property.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1a30d-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1a30d-119">Parent Elements</span></span>  
  
|<span data-ttu-id="1a30d-120">Element</span><span class="sxs-lookup"><span data-stu-id="1a30d-120">Element</span></span>|<span data-ttu-id="1a30d-121">Opis</span><span class="sxs-lookup"><span data-stu-id="1a30d-121">Description</span></span>|  
|-------------|-----------------|  
|[\<tracking>](../windows-workflow-foundation/tracking.md)|<span data-ttu-id="1a30d-122">Reprezentuje sekcję konfiguracji do definiowania ustawień śledzenia dla usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="1a30d-122">Represents a configuration section for defining tracking settings for a workflow service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1a30d-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1a30d-123">Remarks</span></span>  
 <span data-ttu-id="1a30d-124">Śledzenie profile zawiera śledzenia zapytań, pozwalające uczestnikiem śledzenia do subskrybowania zdarzenia przepływu pracy, które są emitowane po zmianie stanu wystąpienia przepływu pracy w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="1a30d-124">Tracking profiles contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="1a30d-125">W zależności od potrzeb może zapisu profil przybliżonego, które subskrybuje niewielkiego zestawu zmian stanu wysokiego poziomu przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="1a30d-125">Depending on your monitoring requirements you may write a profile that is very coarse, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="1a30d-126">Z drugiej strony można utworzyć bardzo określony profil którego wynikowego zdarzenia są rozbudowanych, odtworzenie przepływ wykonania szczegółowe później.</span><span class="sxs-lookup"><span data-stu-id="1a30d-126">Conversely, you may create a very specific profile whose resulting events are rich enough to reconstruct a detailed execution flow later.</span></span>  
  
 <span data-ttu-id="1a30d-127">Profile śledzenia mają strukturę jako deklaratywne subskrypcji dla śledzenia rekordy, które umożliwiają zapytania dla rekordów śledzenie wersję wykonawczą przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="1a30d-127">Tracking profiles are structured as declarative subscriptions for tracking records that allow you to query the workflow runtime for specific tracking records.</span></span> <span data-ttu-id="1a30d-128">Istnieje kilku typów zapytań, które umożliwiają subskrybowanie różnych klas <xref:System.Activities.Tracking.TrackingRecord> obiektów.</span><span class="sxs-lookup"><span data-stu-id="1a30d-128">There are a handful of query types that allow you subscribe to different classes of <xref:System.Activities.Tracking.TrackingRecord> objects.</span></span> <span data-ttu-id="1a30d-129">Aby uzyskać pełną listę zapytań, zobacz [\<participants>](../windows-workflow-foundation/participants.md) i [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="1a30d-129">For a complete list of queries, see [\<participants>](../windows-workflow-foundation/participants.md) and [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="1a30d-130">Poniższy przykład przedstawia profil śledzenia w pliku konfiguracji, który umożliwia śledzenie uczestnika subskrybowanie `Started` `Completed` zdarzeń przepływu pracy i.</span><span class="sxs-lookup"><span data-stu-id="1a30d-130">The following example shows a tracking profile in a configuration file that allows a tracking participant to subscribe to the `Started` and `Completed` workflow events.</span></span>  
  
```xml  
<system.serviceModel>
  <tracking>
    <profiles>
      <trackingProfile name="Sample Tracking Profile">
        <workflow activityDefinitionId="*">
          <workflowInstanceQueries>
            <workflowInstanceQuery>
              <states>
                <state name="Started" />
                <state name="Completed" />
              </states>
            </workflowInstanceQuery>
          </workflowInstanceQueries>
        </workflow>
      </trackingProfile>
    </profiles>
  </tracking>
</system.serviceModel>
```  
  
## <a name="see-also"></a><span data-ttu-id="1a30d-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1a30d-131">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileElement>
- <xref:System.Activities.Tracking.TrackingProfile>
- [<span data-ttu-id="1a30d-132">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="1a30d-132">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="1a30d-133">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="1a30d-133">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
