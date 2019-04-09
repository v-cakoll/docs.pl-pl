---
title: <states> z <activityStateQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a7cc2018-2b79-44f1-825a-bb7ca08690a3
ms.openlocfilehash: fa3736fc13f6f40f52d15b8257b7a79f4179d738
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59189602"
---
# <a name="states-of-activitystatequery"></a><span data-ttu-id="d074d-102">\<Stany > z \<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="d074d-102">\<states> of \<activityStateQuery></span></span>
<span data-ttu-id="d074d-103">Kolekcja elementów konfiguracji, które zawierają stany subskrybowanego działania, dla którego należy obliczanie rekord śledzenia.</span><span class="sxs-lookup"><span data-stu-id="d074d-103">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>  
  
 <span data-ttu-id="d074d-104">Aby uzyskać więcej informacji na podstawie śledzenia zapytań profilu zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="d074d-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="d074d-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="d074d-105">\<system.serviceModel></span></span>  
<span data-ttu-id="d074d-106">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="d074d-106">\<tracking></span></span>  
<span data-ttu-id="d074d-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="d074d-107">\<trackingProfile></span></span>  
<span data-ttu-id="d074d-108">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="d074d-108">\<workflow></span></span>  
<span data-ttu-id="d074d-109">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="d074d-109">\<activityStateQueries></span></span>  
<span data-ttu-id="d074d-110">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="d074d-110">\<activityStateQuery></span></span>  
<span data-ttu-id="d074d-111">\<Stany ></span><span class="sxs-lookup"><span data-stu-id="d074d-111">\<states></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d074d-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="d074d-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d074d-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d074d-113">Attributes and Elements</span></span>  
 <span data-ttu-id="d074d-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d074d-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d074d-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d074d-115">Attributes</span></span>  
 <span data-ttu-id="d074d-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="d074d-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d074d-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d074d-117">Child Elements</span></span>  
  
|<span data-ttu-id="d074d-118">Element</span><span class="sxs-lookup"><span data-stu-id="d074d-118">Element</span></span>|<span data-ttu-id="d074d-119">Opis</span><span class="sxs-lookup"><span data-stu-id="d074d-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d074d-120">\<state></span><span class="sxs-lookup"><span data-stu-id="d074d-120">\<state></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/state-of-states.md)|<span data-ttu-id="d074d-121">Element konfiguracji zawiera stany subskrybowanego działania, dla którego należy obliczanie rekord śledzenia.</span><span class="sxs-lookup"><span data-stu-id="d074d-121">A configuration element that contains the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d074d-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d074d-122">Parent Elements</span></span>  
  
|<span data-ttu-id="d074d-123">Element</span><span class="sxs-lookup"><span data-stu-id="d074d-123">Element</span></span>|<span data-ttu-id="d074d-124">Opis</span><span class="sxs-lookup"><span data-stu-id="d074d-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d074d-125">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="d074d-125">\<activityStateQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)|<span data-ttu-id="d074d-126">Reprezentuje element konfiguracji, które jest używane do śledzenia żądań, aby anulować działanie podrzędne przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d074d-126">Represents a configuration element that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="d074d-127">Zapytanie jest niezbędne do uczestnika śledzenia do subskrybowania Anuluj żądanie rekordu obiektów.</span><span class="sxs-lookup"><span data-stu-id="d074d-127">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d074d-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d074d-128">Remarks</span></span>  
 <span data-ttu-id="d074d-129">Jedno rozwiązanie ActivityStateQuery jest możliwość wyodrębniania danych podczas śledzenia wykonywania przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="d074d-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="d074d-130">Umożliwia to dodatkowy kontekst podczas uzyskiwania dostępu do śledzenia rekordów post wykonywania.</span><span class="sxs-lookup"><span data-stu-id="d074d-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="d074d-131">Możesz użyć [ \<argumenty >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<stany >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) i [ \<stany >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elementy, aby wyodrębnić dowolnej zmiennej lub argumentu wszelkie działania w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="d074d-131">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="d074d-132">W poniższym przykładzie pokazano kwerendą stanu działania, który wyodrębnia zmienne i argumenty podczas działania `Closed` rekord śledzenia jest emitowane.</span><span class="sxs-lookup"><span data-stu-id="d074d-132">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="d074d-133">Zmienne i argumenty wyodrębniania tylko z ActivityStateRecord i w związku z tym subskrybują w ramach śledzenia profilu przy użyciu [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="d074d-133">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d074d-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d074d-134">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="d074d-135">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="d074d-135">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="d074d-136">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="d074d-136">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
