---
title: <variables>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: da0fd144-dda9-4613-b650-fe6325076513
ms.openlocfilehash: 3e48256ab1127d45e95c557aa9c2434419d9ea59
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397593"
---
# <a name="variables"></a><span data-ttu-id="5f7e5-101">\<Zmienne ></span><span class="sxs-lookup"><span data-stu-id="5f7e5-101">\<variables></span></span>
<span data-ttu-id="5f7e5-102">Reprezentuje kolekcję zmiennych skojarzoną z tym zapytaniem działania.</span><span class="sxs-lookup"><span data-stu-id="5f7e5-102">Represents a collection of variables associated with this activity query.</span></span>  
  
 <span data-ttu-id="5f7e5-103">Aby uzyskać więcej informacji na temat śledzenia kwerend profilu, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="5f7e5-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="5f7e5-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5f7e5-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5f7e5-105">&nbsp;&nbsp;[ **\<systemami. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="5f7e5-105">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="5f7e5-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Śledzenie >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="5f7e5-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="5f7e5-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="5f7e5-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="5f7e5-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<przepływ pracy >** ](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="5f7e5-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="5f7e5-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<activityStateQueries >** ](activitystatequeries.md)</span><span class="sxs-lookup"><span data-stu-id="5f7e5-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQueries>**](activitystatequeries.md)</span></span>\
<span data-ttu-id="5f7e5-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<activityStateQuery >** ](activitystatequery.md)</span><span class="sxs-lookup"><span data-stu-id="5f7e5-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQuery>**](activitystatequery.md)</span></span>\
<span data-ttu-id="5f7e5-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Zmienne >**</span><span class="sxs-lookup"><span data-stu-id="5f7e5-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<variables>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f7e5-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="5f7e5-112">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <variables>
          <variable name="String" />
        </variables>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5f7e5-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="5f7e5-113">Attributes and Elements</span></span>  
 <span data-ttu-id="5f7e5-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="5f7e5-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5f7e5-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="5f7e5-115">Attributes</span></span>  
 <span data-ttu-id="5f7e5-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="5f7e5-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5f7e5-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="5f7e5-117">Child Elements</span></span>  
  
|<span data-ttu-id="5f7e5-118">Element</span><span class="sxs-lookup"><span data-stu-id="5f7e5-118">Element</span></span>|<span data-ttu-id="5f7e5-119">Opis</span><span class="sxs-lookup"><span data-stu-id="5f7e5-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5f7e5-120">\<Zmienna ></span><span class="sxs-lookup"><span data-stu-id="5f7e5-120">\<variable></span></span>](variable.md)|<span data-ttu-id="5f7e5-121">Zmienna skojarzonych z kwerendą stanu działania.</span><span class="sxs-lookup"><span data-stu-id="5f7e5-121">A variable associated with an activity state query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5f7e5-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="5f7e5-122">Parent Elements</span></span>  
  
|<span data-ttu-id="5f7e5-123">Element</span><span class="sxs-lookup"><span data-stu-id="5f7e5-123">Element</span></span>|<span data-ttu-id="5f7e5-124">Opis</span><span class="sxs-lookup"><span data-stu-id="5f7e5-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5f7e5-125">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="5f7e5-125">\<activityStateQuery></span></span>](activitystatequery.md)|<span data-ttu-id="5f7e5-126">Reprezentuje element konfiguracji, które jest używane do śledzenia żądań, aby anulować działanie podrzędne przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="5f7e5-126">Represents a configuration element that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="5f7e5-127">Zapytanie jest niezbędne do uczestnika śledzenia do subskrybowania Anuluj żądanie rekordu obiektów.</span><span class="sxs-lookup"><span data-stu-id="5f7e5-127">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5f7e5-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5f7e5-128">Remarks</span></span>  
 <span data-ttu-id="5f7e5-129">Jedno rozwiązanie ActivityStateQuery jest możliwość wyodrębniania danych podczas śledzenia wykonywania przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="5f7e5-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="5f7e5-130">Umożliwia to dodatkowy kontekst podczas uzyskiwania dostępu do śledzenia rekordów post wykonywania.</span><span class="sxs-lookup"><span data-stu-id="5f7e5-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="5f7e5-131">Można użyć [ \<argumentów >](arguments.md), [ \<Stany >](states.md) i [ \<Stany >](states.md) elementy, aby wyodrębnić dowolną zmienną lub argument z dowolnego działania w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="5f7e5-131">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="5f7e5-132">W poniższym przykładzie przedstawiono zapytanie o stan działania, które wyodrębnia zmienne i argumenty podczas emitowania `Closed` rekordu śledzenia działania.</span><span class="sxs-lookup"><span data-stu-id="5f7e5-132">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="5f7e5-133">Zmienne i argumenty mogą być wyodrębniane tylko za pomocą ActivityStateRecord i w ten sposób są subskrybowane w ramach profilu śledzenia przy użyciu [ \<ActivityStateQuery >](activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="5f7e5-133">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5f7e5-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5f7e5-134">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.VariableElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="5f7e5-135">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="5f7e5-135">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="5f7e5-136">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="5f7e5-136">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
