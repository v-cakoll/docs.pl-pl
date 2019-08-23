---
title: <activityStateQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: bdd3c8ae-a13f-4df1-9b3c-a9d6c4bb1b5f
ms.openlocfilehash: 6e91078a24a950c6de027d57e3883e38f19447d5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945458"
---
# <a name="activitystatequeries"></a><span data-ttu-id="db724-101">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="db724-101">\<activityStateQueries></span></span>
<span data-ttu-id="db724-102">Reprezentuje kolekcję zapytań, które są używane do śledzenia zmian cyklem życia działań, które tworzą wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="db724-102">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="db724-103">Na przykład możesz chcieć śledzić każde działanie "Wyślij wiadomość E-Mail" w ramach wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="db724-103">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="db724-104">To zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania obiektów rekordu stanu działania.</span><span class="sxs-lookup"><span data-stu-id="db724-104">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="db724-105">Stany do subskrybowania są wyszczególnione w ActivityStates.</span><span class="sxs-lookup"><span data-stu-id="db724-105">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
 <span data-ttu-id="db724-106">Aby uzyskać więcej informacji na temat śledzenia kwerend profilu, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="db724-106">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="db724-107">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="db724-107">\<system.serviceModel></span></span>  
<span data-ttu-id="db724-108">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="db724-108">\<tracking></span></span>  
<span data-ttu-id="db724-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="db724-109">\<trackingProfile></span></span>  
<span data-ttu-id="db724-110">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="db724-110">\<workflow></span></span>  
<span data-ttu-id="db724-111">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="db724-111">\<activityStateQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db724-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="db724-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="db724-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="db724-113">Attributes and Elements</span></span>  
 <span data-ttu-id="db724-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="db724-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="db724-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="db724-115">Attributes</span></span>  
 <span data-ttu-id="db724-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="db724-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="db724-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="db724-117">Child Elements</span></span>  
  
|<span data-ttu-id="db724-118">Element</span><span class="sxs-lookup"><span data-stu-id="db724-118">Element</span></span>|<span data-ttu-id="db724-119">Opis</span><span class="sxs-lookup"><span data-stu-id="db724-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="db724-120">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="db724-120">\<activityStateQuery></span></span>](activitystatequery.md)|<span data-ttu-id="db724-121">Zapytanie, które jest używane do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="db724-121">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="db724-122">To zdarzenie jest wykonywane za każdym razem, gdy FaultHandler przetwarza błąd.</span><span class="sxs-lookup"><span data-stu-id="db724-122">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="db724-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="db724-123">Parent Elements</span></span>  
  
|<span data-ttu-id="db724-124">Element</span><span class="sxs-lookup"><span data-stu-id="db724-124">Element</span></span>|<span data-ttu-id="db724-125">Opis</span><span class="sxs-lookup"><span data-stu-id="db724-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="db724-126">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="db724-126">\<workflow></span></span>](workflow.md)|<span data-ttu-id="db724-127">Element konfiguracji, który zawiera wszystkie zapytania dla określonego przepływu pracy identyfikowanego przez właściwość **activityDefinitionId** .</span><span class="sxs-lookup"><span data-stu-id="db724-127">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="db724-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="db724-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="db724-129">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="db724-129">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="db724-130">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="db724-130">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
