---
title: <states> dla <activityStateQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a7cc2018-2b79-44f1-825a-bb7ca08690a3
ms.openlocfilehash: 50827577374859133e6c673e8850e145b4ccab73
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947431"
---
# <a name="states-of-activitystatequery"></a><span data-ttu-id="01a78-102">\<Stany > \<ActivityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="01a78-102">\<states> of \<activityStateQuery></span></span>
<span data-ttu-id="01a78-103">Kolekcja elementów konfiguracji, które zawierają stany subskrybowanego działania, dla którego należy obliczanie rekord śledzenia.</span><span class="sxs-lookup"><span data-stu-id="01a78-103">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>  
  
 <span data-ttu-id="01a78-104">Aby uzyskać więcej informacji na temat śledzenia kwerend profilu, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="01a78-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="01a78-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="01a78-105">\<system.serviceModel></span></span>  
<span data-ttu-id="01a78-106">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="01a78-106">\<tracking></span></span>  
<span data-ttu-id="01a78-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="01a78-107">\<trackingProfile></span></span>  
<span data-ttu-id="01a78-108">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="01a78-108">\<workflow></span></span>  
<span data-ttu-id="01a78-109">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="01a78-109">\<activityStateQueries></span></span>  
<span data-ttu-id="01a78-110">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="01a78-110">\<activityStateQuery></span></span>  
<span data-ttu-id="01a78-111">\<Stany ></span><span class="sxs-lookup"><span data-stu-id="01a78-111">\<states></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01a78-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="01a78-112">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <states>
          <state name="String" />
        </states>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="01a78-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="01a78-113">Attributes and Elements</span></span>  
 <span data-ttu-id="01a78-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="01a78-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="01a78-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="01a78-115">Attributes</span></span>  
 <span data-ttu-id="01a78-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="01a78-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="01a78-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="01a78-117">Child Elements</span></span>  
  
|<span data-ttu-id="01a78-118">Element</span><span class="sxs-lookup"><span data-stu-id="01a78-118">Element</span></span>|<span data-ttu-id="01a78-119">Opis</span><span class="sxs-lookup"><span data-stu-id="01a78-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="01a78-120">\<> stanu</span><span class="sxs-lookup"><span data-stu-id="01a78-120">\<state></span></span>](state-of-states.md)|<span data-ttu-id="01a78-121">Element konfiguracji zawiera stany subskrybowanego działania, dla którego należy obliczanie rekord śledzenia.</span><span class="sxs-lookup"><span data-stu-id="01a78-121">A configuration element that contains the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="01a78-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="01a78-122">Parent Elements</span></span>  
  
|<span data-ttu-id="01a78-123">Element</span><span class="sxs-lookup"><span data-stu-id="01a78-123">Element</span></span>|<span data-ttu-id="01a78-124">Opis</span><span class="sxs-lookup"><span data-stu-id="01a78-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="01a78-125">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="01a78-125">\<activityStateQuery></span></span>](activitystatequery.md)|<span data-ttu-id="01a78-126">Reprezentuje element konfiguracji, które jest używane do śledzenia żądań, aby anulować działanie podrzędne przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="01a78-126">Represents a configuration element that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="01a78-127">Zapytanie jest niezbędne do uczestnika śledzenia do subskrybowania Anuluj żądanie rekordu obiektów.</span><span class="sxs-lookup"><span data-stu-id="01a78-127">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="01a78-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="01a78-128">Remarks</span></span>  
 <span data-ttu-id="01a78-129">Jedno rozwiązanie ActivityStateQuery jest możliwość wyodrębniania danych podczas śledzenia wykonywania przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="01a78-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="01a78-130">Umożliwia to dodatkowy kontekst podczas uzyskiwania dostępu do śledzenia rekordów post wykonywania.</span><span class="sxs-lookup"><span data-stu-id="01a78-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="01a78-131">Można użyć [ \<argumentów >](arguments.md), [ \<Stany >](states.md) i [ \<Stany >](states.md) elementy, aby wyodrębnić dowolną zmienną lub argument z dowolnego działania w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="01a78-131">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="01a78-132">W poniższym przykładzie przedstawiono zapytanie o stan działania, które wyodrębnia zmienne i argumenty podczas emitowania `Closed` rekordu śledzenia działania.</span><span class="sxs-lookup"><span data-stu-id="01a78-132">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="01a78-133">Zmienne i argumenty mogą być wyodrębniane tylko za pomocą ActivityStateRecord i w ten sposób są subskrybowane w ramach profilu śledzenia przy użyciu [ \<ActivityStateQuery >](activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="01a78-133">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
```xml  
<activityStateQuery activityName="SendEmailActivity">  
  <states>  
    <state name="Closed"/>  
  </states>  
  <variables>  
    <variable name="FromAddress"/>  
  </variables>  
  <arguments>  
    <argument name="Result"/>  
  </arguments>  
</activityStateQuery>  
```  
  
## <a name="see-also"></a><span data-ttu-id="01a78-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="01a78-134">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="01a78-135">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="01a78-135">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="01a78-136">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="01a78-136">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
