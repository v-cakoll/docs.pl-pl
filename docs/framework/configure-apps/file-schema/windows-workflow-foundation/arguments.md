---
title: <arguments>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 0f327196-f468-4be3-b6c4-68ba981a1bd6
ms.openlocfilehash: bb7ae702209df3c0297ec2cfac6b09ee47ad9558
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946129"
---
# <a name="arguments"></a><span data-ttu-id="ec6c0-101">\<argumenty ></span><span class="sxs-lookup"><span data-stu-id="ec6c0-101">\<arguments></span></span>
<span data-ttu-id="ec6c0-102">Reprezentuje kolekcję argumentów skojarzonych z kwerendą stanu działania.</span><span class="sxs-lookup"><span data-stu-id="ec6c0-102">Represents a collection of arguments associated with an activity state query.</span></span>  
  
 <span data-ttu-id="ec6c0-103">Aby uzyskać więcej informacji na temat śledzenia kwerend profilu, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="ec6c0-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="ec6c0-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="ec6c0-104">\<system.serviceModel></span></span>  
<span data-ttu-id="ec6c0-105">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="ec6c0-105">\<tracking></span></span>  
<span data-ttu-id="ec6c0-106">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="ec6c0-106">\<trackingProfile></span></span>  
<span data-ttu-id="ec6c0-107">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="ec6c0-107">\<workflow></span></span>  
<span data-ttu-id="ec6c0-108">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="ec6c0-108">\<activityStateQueries></span></span>  
<span data-ttu-id="ec6c0-109">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="ec6c0-109">\<activityStateQuery></span></span>  
<span data-ttu-id="ec6c0-110">\<argumenty ></span><span class="sxs-lookup"><span data-stu-id="ec6c0-110">\<arguments></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec6c0-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="ec6c0-111">Syntax</span></span>  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <arguments>
          <argument name="String" />
        </arguments>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ec6c0-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ec6c0-112">Attributes and Elements</span></span>  
 <span data-ttu-id="ec6c0-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ec6c0-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ec6c0-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ec6c0-114">Attributes</span></span>  
 <span data-ttu-id="ec6c0-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="ec6c0-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ec6c0-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ec6c0-116">Child Elements</span></span>  
  
|<span data-ttu-id="ec6c0-117">Element</span><span class="sxs-lookup"><span data-stu-id="ec6c0-117">Element</span></span>|<span data-ttu-id="ec6c0-118">Opis</span><span class="sxs-lookup"><span data-stu-id="ec6c0-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ec6c0-119">\<> argumentu</span><span class="sxs-lookup"><span data-stu-id="ec6c0-119">\<argument></span></span>](argument.md)|<span data-ttu-id="ec6c0-120">Argument skojarzonych z kwerendą stanu działania.</span><span class="sxs-lookup"><span data-stu-id="ec6c0-120">An argument associated with an activity state query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ec6c0-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ec6c0-121">Parent Elements</span></span>  
  
|<span data-ttu-id="ec6c0-122">Element</span><span class="sxs-lookup"><span data-stu-id="ec6c0-122">Element</span></span>|<span data-ttu-id="ec6c0-123">Opis</span><span class="sxs-lookup"><span data-stu-id="ec6c0-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ec6c0-124">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="ec6c0-124">\<activityStateQuery></span></span>](activitystatequery.md)|<span data-ttu-id="ec6c0-125">Reprezentuje element konfiguracji, które jest używane do śledzenia żądań, aby anulować działanie podrzędne przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ec6c0-125">Represents a configuration element that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="ec6c0-126">Zapytanie jest niezbędne do uczestnika śledzenia do subskrybowania Anuluj żądanie rekordu obiektów.</span><span class="sxs-lookup"><span data-stu-id="ec6c0-126">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ec6c0-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ec6c0-127">Remarks</span></span>  
 <span data-ttu-id="ec6c0-128">Jedno rozwiązanie ActivityStateQuery jest możliwość wyodrębniania danych podczas śledzenia wykonywania przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="ec6c0-128">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="ec6c0-129">Umożliwia to dodatkowy kontekst podczas uzyskiwania dostępu do śledzenia rekordów post wykonywania.</span><span class="sxs-lookup"><span data-stu-id="ec6c0-129">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="ec6c0-130">Można użyć [ \<argumentów >](arguments.md), [ \<Stany >](states.md) i [ \<Stany >](states.md) elementy, aby wyodrębnić dowolną zmienną lub argument z dowolnego działania w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="ec6c0-130">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="ec6c0-131">W poniższym przykładzie przedstawiono zapytanie o stan działania, które wyodrębnia zmienne i argumenty podczas emitowania `Closed` rekordu śledzenia działania.</span><span class="sxs-lookup"><span data-stu-id="ec6c0-131">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="ec6c0-132">Zmienne i argumenty mogą być wyodrębniane tylko za pomocą ActivityStateRecord i w ten sposób są subskrybowane w ramach profilu śledzenia przy użyciu [ \<ActivityStateQuery >](activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="ec6c0-132">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ec6c0-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ec6c0-133">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ArgumentElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="ec6c0-134">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="ec6c0-134">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="ec6c0-135">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="ec6c0-135">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
