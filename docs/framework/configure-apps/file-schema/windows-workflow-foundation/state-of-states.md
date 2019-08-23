---
title: <state> dla <states>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ab483c7f-a091-4933-ba6b-708d96846d38
ms.openlocfilehash: 7c7326b2fd5ae39ca4c0f39fac05444802fa3d49
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947495"
---
# <a name="state-of-states"></a><span data-ttu-id="90c40-102">\<Stan > \<Stanów ></span><span class="sxs-lookup"><span data-stu-id="90c40-102">\<state> of \<states></span></span>
<span data-ttu-id="90c40-103">Element konfiguracji, który zawiera stan subskrybowanego działania, dla którego należy obliczanie rekord śledzenia.</span><span class="sxs-lookup"><span data-stu-id="90c40-103">A configuration element that contains the state of the subscribed activity for which a tracking record should be emitted.</span></span>  
  
 <span data-ttu-id="90c40-104">Aby uzyskać więcej informacji na temat śledzenia kwerend profilu, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="90c40-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="90c40-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="90c40-105">\<system.serviceModel></span></span>  
<span data-ttu-id="90c40-106">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="90c40-106">\<tracking></span></span>  
<span data-ttu-id="90c40-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="90c40-107">\<trackingProfile></span></span>  
<span data-ttu-id="90c40-108">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="90c40-108">\<workflow></span></span>  
<span data-ttu-id="90c40-109">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="90c40-109">\<activityStateQueries></span></span>  
<span data-ttu-id="90c40-110">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="90c40-110">\<activityStateQuery></span></span>  
<span data-ttu-id="90c40-111">\<Stany ></span><span class="sxs-lookup"><span data-stu-id="90c40-111">\<states></span></span>  
<span data-ttu-id="90c40-112">\<> stanu</span><span class="sxs-lookup"><span data-stu-id="90c40-112">\<state></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90c40-113">Składnia</span><span class="sxs-lookup"><span data-stu-id="90c40-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="90c40-114">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="90c40-114">Attributes and Elements</span></span>  
 <span data-ttu-id="90c40-115">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="90c40-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="90c40-116">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="90c40-116">Attributes</span></span>  
  
|<span data-ttu-id="90c40-117">Atrybut</span><span class="sxs-lookup"><span data-stu-id="90c40-117">Attribute</span></span>|<span data-ttu-id="90c40-118">Opis</span><span class="sxs-lookup"><span data-stu-id="90c40-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="90c40-119">nazwa</span><span class="sxs-lookup"><span data-stu-id="90c40-119">name</span></span>|<span data-ttu-id="90c40-120">Ciąg, który określa stan subskrybowanego działania, dla którego należy obliczanie rekord śledzenia.</span><span class="sxs-lookup"><span data-stu-id="90c40-120">A string that specifies the state of the subscribed activity for which a tracking record should be emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="90c40-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="90c40-121">Child Elements</span></span>  
 <span data-ttu-id="90c40-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="90c40-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="90c40-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="90c40-123">Parent Elements</span></span>  
  
|<span data-ttu-id="90c40-124">Element</span><span class="sxs-lookup"><span data-stu-id="90c40-124">Element</span></span>|<span data-ttu-id="90c40-125">Opis</span><span class="sxs-lookup"><span data-stu-id="90c40-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="90c40-126">\<Stany ></span><span class="sxs-lookup"><span data-stu-id="90c40-126">\<states></span></span>](states-of-activitystatequery.md)|<span data-ttu-id="90c40-127">Kolekcja elementów konfiguracji, które zawierają stany subskrybowanego działania, dla którego należy obliczanie rekord śledzenia.</span><span class="sxs-lookup"><span data-stu-id="90c40-127">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="90c40-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="90c40-128">Remarks</span></span>  
 <span data-ttu-id="90c40-129">Jedno rozwiązanie ActivityStateQuery jest możliwość wyodrębniania danych podczas śledzenia wykonywania przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="90c40-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="90c40-130">Umożliwia to dodatkowy kontekst podczas uzyskiwania dostępu do śledzenia rekordów post wykonywania.</span><span class="sxs-lookup"><span data-stu-id="90c40-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="90c40-131">Można użyć [ \<argumentów >](arguments.md), [ \<Stany >](states.md) i [ \<Stany >](states.md) elementy, aby wyodrębnić dowolną zmienną lub argument z dowolnego działania w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="90c40-131">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="90c40-132">W poniższym przykładzie przedstawiono zapytanie o stan działania, które wyodrębnia zmienne i argumenty podczas emitowania `Closed` rekordu śledzenia działania.</span><span class="sxs-lookup"><span data-stu-id="90c40-132">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="90c40-133">Zmienne i argumenty mogą być wyodrębniane tylko za pomocą ActivityStateRecord i w ten sposób są subskrybowane w ramach profilu śledzenia przy użyciu [ \<ActivityStateQuery >](activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="90c40-133">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="90c40-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="90c40-134">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="90c40-135">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="90c40-135">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="90c40-136">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="90c40-136">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
