---
title: <activityStateQueries>programu WCF
ms.date: 10/08/2018
ms.assetid: 9e45db49-ed85-4fdf-bd65-0d5477e31823
ms.openlocfilehash: 415cd4a75ecab725f91bcd298f8a7966ea6079d1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920298"
---
# <a name="activitystatequeries-of-wcf"></a><span data-ttu-id="6a65f-102">\<activityStateQueries > WCF</span><span class="sxs-lookup"><span data-stu-id="6a65f-102">\<activityStateQueries> of WCF</span></span>

<span data-ttu-id="6a65f-103">Reprezentuje kolekcję zapytań, które są używane do śledzenia zmian cyklem życia działań, które tworzą wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="6a65f-103">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="6a65f-104">Na przykład możesz chcieć śledzić każde działanie "Wyślij wiadomość E-Mail" w ramach wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="6a65f-104">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="6a65f-105">To zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania obiektów rekordu stanu działania.</span><span class="sxs-lookup"><span data-stu-id="6a65f-105">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="6a65f-106">Stany do subskrybowania są wyszczególnione w ActivityStates.</span><span class="sxs-lookup"><span data-stu-id="6a65f-106">The available states to subscribe to are specified in ActivityStates.</span></span>

<span data-ttu-id="6a65f-107">Aby uzyskać więcej informacji na temat śledzenia kwerend profilu, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="6a65f-107">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>

<span data-ttu-id="6a65f-108">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="6a65f-108">\<system.serviceModel></span></span>  
<span data-ttu-id="6a65f-109">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="6a65f-109">\<tracking></span></span>  
<span data-ttu-id="6a65f-110">\<> profilów</span><span class="sxs-lookup"><span data-stu-id="6a65f-110">\<profiles></span></span>  
<span data-ttu-id="6a65f-111">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="6a65f-111">\<trackingProfile></span></span>  
<span data-ttu-id="6a65f-112">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="6a65f-112">\<workflow></span></span>  
<span data-ttu-id="6a65f-113">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="6a65f-113">\<activityStateQueries></span></span>  

## <a name="syntax"></a><span data-ttu-id="6a65f-114">Składnia</span><span class="sxs-lookup"><span data-stu-id="6a65f-114">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
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
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  

## <a name="attributes-and-elements"></a><span data-ttu-id="6a65f-115">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="6a65f-115">Attributes and elements</span></span>

<span data-ttu-id="6a65f-116">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="6a65f-116">The following sections describe attributes, child elements, and parent elements.</span></span>
  
### <a name="attributes"></a><span data-ttu-id="6a65f-117">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="6a65f-117">Attributes</span></span>  

<span data-ttu-id="6a65f-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="6a65f-118">None.</span></span>  

### <a name="child-elements"></a><span data-ttu-id="6a65f-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="6a65f-119">Child elements</span></span>

|<span data-ttu-id="6a65f-120">Element</span><span class="sxs-lookup"><span data-stu-id="6a65f-120">Element</span></span>|<span data-ttu-id="6a65f-121">Opis</span><span class="sxs-lookup"><span data-stu-id="6a65f-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6a65f-122">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="6a65f-122">\<activityStateQuery></span></span>](activitystatequery-of-wcf.md)|<span data-ttu-id="6a65f-123">Zapytanie, które jest używane do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="6a65f-123">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="6a65f-124">To zdarzenie jest wykonywane za każdym razem, gdy FaultHandler przetwarza błąd.</span><span class="sxs-lookup"><span data-stu-id="6a65f-124">This event occurs each time a FaultHandler processes a fault.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="6a65f-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="6a65f-125">Parent elements</span></span>

|<span data-ttu-id="6a65f-126">Element</span><span class="sxs-lookup"><span data-stu-id="6a65f-126">Element</span></span>|<span data-ttu-id="6a65f-127">Opis</span><span class="sxs-lookup"><span data-stu-id="6a65f-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6a65f-128">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="6a65f-128">\<workflow></span></span>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="6a65f-129">Element konfiguracji, który zawiera wszystkie zapytania dla określonego przepływu pracy identyfikowane przez `activityDefinitionId` właściwości.</span><span class="sxs-lookup"><span data-stu-id="6a65f-129">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|

## <a name="see-also"></a><span data-ttu-id="6a65f-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6a65f-130">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection>
- <xref:System.Activities.Tracking.ActivityStateQuery>
- [<span data-ttu-id="6a65f-131">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="6a65f-131">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="6a65f-132">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="6a65f-132">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
