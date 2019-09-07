---
title: <arguments>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 0f327196-f468-4be3-b6c4-68ba981a1bd6
ms.openlocfilehash: f06a2188ea3561437c1453d3a1cb23d42d767f53
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398912"
---
# <a name="arguments"></a><span data-ttu-id="2edae-101">\<argumenty ></span><span class="sxs-lookup"><span data-stu-id="2edae-101">\<arguments></span></span>
<span data-ttu-id="2edae-102">Reprezentuje kolekcję argumentów skojarzonych z kwerendą stanu działania.</span><span class="sxs-lookup"><span data-stu-id="2edae-102">Represents a collection of arguments associated with an activity state query.</span></span>  
  
 <span data-ttu-id="2edae-103">Aby uzyskać więcej informacji na temat śledzenia kwerend profilu, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="2edae-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="2edae-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="2edae-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2edae-105">&nbsp;&nbsp;[ **\<systemami. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="2edae-105">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="2edae-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Śledzenie >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="2edae-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="2edae-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="2edae-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="2edae-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<przepływ pracy >** ](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="2edae-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="2edae-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<activityStateQueries >** ](activitystatequeries.md)</span><span class="sxs-lookup"><span data-stu-id="2edae-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQueries>**](activitystatequeries.md)</span></span>\
<span data-ttu-id="2edae-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<activityStateQuery >** ](activitystatequery.md)</span><span class="sxs-lookup"><span data-stu-id="2edae-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQuery>**](activitystatequery.md)</span></span>\
<span data-ttu-id="2edae-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<argumenty >**</span><span class="sxs-lookup"><span data-stu-id="2edae-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<arguments>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2edae-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="2edae-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2edae-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="2edae-113">Attributes and Elements</span></span>  
 <span data-ttu-id="2edae-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="2edae-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2edae-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="2edae-115">Attributes</span></span>  
 <span data-ttu-id="2edae-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="2edae-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2edae-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="2edae-117">Child Elements</span></span>  
  
|<span data-ttu-id="2edae-118">Element</span><span class="sxs-lookup"><span data-stu-id="2edae-118">Element</span></span>|<span data-ttu-id="2edae-119">Opis</span><span class="sxs-lookup"><span data-stu-id="2edae-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2edae-120">\<> argumentu</span><span class="sxs-lookup"><span data-stu-id="2edae-120">\<argument></span></span>](argument.md)|<span data-ttu-id="2edae-121">Argument skojarzonych z kwerendą stanu działania.</span><span class="sxs-lookup"><span data-stu-id="2edae-121">An argument associated with an activity state query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2edae-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="2edae-122">Parent Elements</span></span>  
  
|<span data-ttu-id="2edae-123">Element</span><span class="sxs-lookup"><span data-stu-id="2edae-123">Element</span></span>|<span data-ttu-id="2edae-124">Opis</span><span class="sxs-lookup"><span data-stu-id="2edae-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2edae-125">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="2edae-125">\<activityStateQuery></span></span>](activitystatequery.md)|<span data-ttu-id="2edae-126">Reprezentuje element konfiguracji, które jest używane do śledzenia żądań, aby anulować działanie podrzędne przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="2edae-126">Represents a configuration element that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="2edae-127">Zapytanie jest niezbędne do uczestnika śledzenia do subskrybowania Anuluj żądanie rekordu obiektów.</span><span class="sxs-lookup"><span data-stu-id="2edae-127">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2edae-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2edae-128">Remarks</span></span>  
 <span data-ttu-id="2edae-129">Jedno rozwiązanie ActivityStateQuery jest możliwość wyodrębniania danych podczas śledzenia wykonywania przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="2edae-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="2edae-130">Umożliwia to dodatkowy kontekst podczas uzyskiwania dostępu do śledzenia rekordów post wykonywania.</span><span class="sxs-lookup"><span data-stu-id="2edae-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="2edae-131">Można użyć [ \<argumentów >](arguments.md), [ \<Stany >](states.md) i [ \<Stany >](states.md) elementy, aby wyodrębnić dowolną zmienną lub argument z dowolnego działania w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="2edae-131">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="2edae-132">W poniższym przykładzie przedstawiono zapytanie o stan działania, które wyodrębnia zmienne i argumenty podczas emitowania `Closed` rekordu śledzenia działania.</span><span class="sxs-lookup"><span data-stu-id="2edae-132">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="2edae-133">Zmienne i argumenty mogą być wyodrębniane tylko za pomocą ActivityStateRecord i w ten sposób są subskrybowane w ramach profilu śledzenia przy użyciu [ \<ActivityStateQuery >](activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="2edae-133">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2edae-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2edae-134">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ArgumentElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="2edae-135">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="2edae-135">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="2edae-136">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="2edae-136">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
