---
title: '&lt;activityStateQueries&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: bdd3c8ae-a13f-4df1-9b3c-a9d6c4bb1b5f
ms.openlocfilehash: c215380530acef630ff99dc24e2fc9cf35bbd3d4
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltactivitystatequeriesgt"></a><span data-ttu-id="9bfbb-102">&lt;activityStateQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="9bfbb-102">&lt;activityStateQueries&gt;</span></span>
<span data-ttu-id="9bfbb-103">Reprezentuje kolekcję zapytań, które są używane do śledzenia zmian cyklem życia działań, które tworzą wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="9bfbb-103">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="9bfbb-104">Na przykład może być do śledzenia każdorazowo po ukończeniu działania "Wyślij wiadomość E-Mail" w ramach wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="9bfbb-104">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="9bfbb-105">To zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania obiektów rekordu stanu działania.</span><span class="sxs-lookup"><span data-stu-id="9bfbb-105">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="9bfbb-106">Stany do subskrybowania są wyszczególnione w ActivityStates.</span><span class="sxs-lookup"><span data-stu-id="9bfbb-106">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
 <span data-ttu-id="9bfbb-107">Aby uzyskać więcej informacji na zapytania dotyczące profilu śledzenia, zobacz [śledzenia profile](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="9bfbb-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="9bfbb-108">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="9bfbb-108">\<system.serviceModel></span></span>  
<span data-ttu-id="9bfbb-109">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="9bfbb-109">\<tracking></span></span>  
<span data-ttu-id="9bfbb-110">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="9bfbb-110">\<trackingProfile></span></span>  
<span data-ttu-id="9bfbb-111">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="9bfbb-111">\<workflow></span></span>  
<span data-ttu-id="9bfbb-112">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="9bfbb-112">\<activityStateQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9bfbb-113">Składnia</span><span class="sxs-lookup"><span data-stu-id="9bfbb-113">Syntax</span></span>  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <arguments>
          <argument name="String" />
        </arguments>
        <states>
          <state name="String" />
        </states>
        <variables>
         <variable name="String" />
        </variables>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9bfbb-114">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9bfbb-114">Attributes and Elements</span></span>  
 <span data-ttu-id="9bfbb-115">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9bfbb-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9bfbb-116">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9bfbb-116">Attributes</span></span>  
 <span data-ttu-id="9bfbb-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="9bfbb-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9bfbb-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9bfbb-118">Child Elements</span></span>  
  
|<span data-ttu-id="9bfbb-119">Element</span><span class="sxs-lookup"><span data-stu-id="9bfbb-119">Element</span></span>|<span data-ttu-id="9bfbb-120">Opis</span><span class="sxs-lookup"><span data-stu-id="9bfbb-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9bfbb-121">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="9bfbb-121">\<activityStateQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)|<span data-ttu-id="9bfbb-122">Kwerenda, która służy do śledzenia Obsługa błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="9bfbb-122">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="9bfbb-123">To zdarzenie występuje zawsze FaultHandler przetwarza błąd.</span><span class="sxs-lookup"><span data-stu-id="9bfbb-123">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9bfbb-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9bfbb-124">Parent Elements</span></span>  
  
|<span data-ttu-id="9bfbb-125">Element</span><span class="sxs-lookup"><span data-stu-id="9bfbb-125">Element</span></span>|<span data-ttu-id="9bfbb-126">Opis</span><span class="sxs-lookup"><span data-stu-id="9bfbb-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9bfbb-127">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="9bfbb-127">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="9bfbb-128">Element konfiguracji, który zawiera wszystkie zapytania dotyczące określonego przepływu pracy, identyfikowane przez **obiektu activityDefinitionId** właściwości.</span><span class="sxs-lookup"><span data-stu-id="9bfbb-128">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9bfbb-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9bfbb-129">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="9bfbb-130">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="9bfbb-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="9bfbb-131">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="9bfbb-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
