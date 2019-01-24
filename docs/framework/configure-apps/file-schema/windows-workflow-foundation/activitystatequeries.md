---
title: '&lt;activityStateQueries&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: bdd3c8ae-a13f-4df1-9b3c-a9d6c4bb1b5f
ms.openlocfilehash: bfd19e00e79a95eb717ca9131e92b5ff5c600d5b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54511985"
---
# <a name="ltactivitystatequeriesgt"></a><span data-ttu-id="68611-102">&lt;activityStateQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="68611-102">&lt;activityStateQueries&gt;</span></span>
<span data-ttu-id="68611-103">Reprezentuje kolekcję zapytań, które są używane do śledzenia zmian cyklem życia działań, które tworzą wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="68611-103">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="68611-104">Na przykład chcesz do śledzenia za każdym razem, gdy kończy działanie "Wyślij wiadomość E-Mail", w ramach wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="68611-104">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="68611-105">To zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania obiektów rekordu stanu działania.</span><span class="sxs-lookup"><span data-stu-id="68611-105">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="68611-106">Stany do subskrybowania są wyszczególnione w ActivityStates.</span><span class="sxs-lookup"><span data-stu-id="68611-106">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
 <span data-ttu-id="68611-107">Aby uzyskać więcej informacji na podstawie śledzenia zapytań profilu zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="68611-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="68611-108">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="68611-108">\<system.serviceModel></span></span>  
<span data-ttu-id="68611-109">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="68611-109">\<tracking></span></span>  
<span data-ttu-id="68611-110">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="68611-110">\<trackingProfile></span></span>  
<span data-ttu-id="68611-111">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="68611-111">\<workflow></span></span>  
<span data-ttu-id="68611-112">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="68611-112">\<activityStateQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68611-113">Składnia</span><span class="sxs-lookup"><span data-stu-id="68611-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="68611-114">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="68611-114">Attributes and Elements</span></span>  
 <span data-ttu-id="68611-115">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="68611-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="68611-116">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="68611-116">Attributes</span></span>  
 <span data-ttu-id="68611-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="68611-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="68611-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="68611-118">Child Elements</span></span>  
  
|<span data-ttu-id="68611-119">Element</span><span class="sxs-lookup"><span data-stu-id="68611-119">Element</span></span>|<span data-ttu-id="68611-120">Opis</span><span class="sxs-lookup"><span data-stu-id="68611-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="68611-121">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="68611-121">\<activityStateQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)|<span data-ttu-id="68611-122">Zapytanie, które jest używane do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="68611-122">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="68611-123">To zdarzenie występuje, każdym razem FaultHandler przetwarza błąd wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="68611-123">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="68611-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="68611-124">Parent Elements</span></span>  
  
|<span data-ttu-id="68611-125">Element</span><span class="sxs-lookup"><span data-stu-id="68611-125">Element</span></span>|<span data-ttu-id="68611-126">Opis</span><span class="sxs-lookup"><span data-stu-id="68611-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="68611-127">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="68611-127">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="68611-128">Element konfiguracji, który zawiera wszystkie zapytania dotyczące określonego przepływu pracy identyfikowane przez **activityDefinitionId** właściwości.</span><span class="sxs-lookup"><span data-stu-id="68611-128">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="68611-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="68611-129">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="68611-130">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="68611-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="68611-131">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="68611-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
