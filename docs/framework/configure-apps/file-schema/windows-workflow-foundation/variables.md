---
title: '&lt;zmienne&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: da0fd144-dda9-4613-b650-fe6325076513
ms.openlocfilehash: d0dc83951bdf894d0061971ae4b79854a7c8bcd8
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltvariablesgt"></a><span data-ttu-id="59d7f-102">&lt;zmienne&gt;</span><span class="sxs-lookup"><span data-stu-id="59d7f-102">&lt;variables&gt;</span></span>
<span data-ttu-id="59d7f-103">Reprezentuje kolekcję zmiennych skojarzoną z tym zapytaniem działania.</span><span class="sxs-lookup"><span data-stu-id="59d7f-103">Represents a collection of variables associated with this activity query.</span></span>  
  
 <span data-ttu-id="59d7f-104">Aby uzyskać więcej informacji na zapytania dotyczące profilu śledzenia, zobacz [śledzenia profile](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="59d7f-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="59d7f-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="59d7f-105">\<system.serviceModel></span></span>  
<span data-ttu-id="59d7f-106">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="59d7f-106">\<tracking></span></span>  
<span data-ttu-id="59d7f-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="59d7f-107">\<trackingProfile></span></span>  
<span data-ttu-id="59d7f-108">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="59d7f-108">\<workflow></span></span>  
<span data-ttu-id="59d7f-109">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="59d7f-109">\<activityStateQueries></span></span>  
<span data-ttu-id="59d7f-110">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="59d7f-110">\<activityStateQuery></span></span>  
<span data-ttu-id="59d7f-111">\<Zmienne ></span><span class="sxs-lookup"><span data-stu-id="59d7f-111">\<variables></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59d7f-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="59d7f-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="59d7f-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="59d7f-113">Attributes and Elements</span></span>  
 <span data-ttu-id="59d7f-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="59d7f-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="59d7f-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="59d7f-115">Attributes</span></span>  
 <span data-ttu-id="59d7f-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="59d7f-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="59d7f-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="59d7f-117">Child Elements</span></span>  
  
|<span data-ttu-id="59d7f-118">Element</span><span class="sxs-lookup"><span data-stu-id="59d7f-118">Element</span></span>|<span data-ttu-id="59d7f-119">Opis</span><span class="sxs-lookup"><span data-stu-id="59d7f-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="59d7f-120">\<Zmienna ></span><span class="sxs-lookup"><span data-stu-id="59d7f-120">\<variable></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/variable.md)|<span data-ttu-id="59d7f-121">Zmienna skojarzonych z kwerendą stanu działania.</span><span class="sxs-lookup"><span data-stu-id="59d7f-121">A variable associated with an activity state query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="59d7f-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="59d7f-122">Parent Elements</span></span>  
  
|<span data-ttu-id="59d7f-123">Element</span><span class="sxs-lookup"><span data-stu-id="59d7f-123">Element</span></span>|<span data-ttu-id="59d7f-124">Opis</span><span class="sxs-lookup"><span data-stu-id="59d7f-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="59d7f-125">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="59d7f-125">\<activityStateQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)|<span data-ttu-id="59d7f-126">Reprezentuje element konfiguracji, które jest używane do śledzenia żądań, aby anulować działanie podrzędne przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="59d7f-126">Represents a configuration element that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="59d7f-127">Zapytanie jest niezbędne do uczestnika śledzenia do subskrybowania Anuluj żądanie rekordu obiektów.</span><span class="sxs-lookup"><span data-stu-id="59d7f-127">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="59d7f-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="59d7f-128">Remarks</span></span>  
 <span data-ttu-id="59d7f-129">Jedno rozwiązanie ActivityStateQuery jest możliwość wyodrębniania danych podczas śledzenia wykonywania przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="59d7f-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="59d7f-130">Umożliwia to dodatkowy kontekst podczas uzyskiwania dostępu do śledzenia rekordów post wykonywania.</span><span class="sxs-lookup"><span data-stu-id="59d7f-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="59d7f-131">Można użyć [ \<argumentów >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<stanów >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) i [ \<stanów >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elementy, aby wyodrębnić żadnych zmiennej lub argumentu wszystkie działania w przepływie pracy. W poniższym przykładzie przedstawiono kwerendy stanu działania, która wyodrębnia zmiennych i argumenty podczas działania `Closed` śledzenia rekord jest emitowany.</span><span class="sxs-lookup"><span data-stu-id="59d7f-131">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="59d7f-132">Argumenty i zmienne można wyodrębnić tylko z ActivityStateRecord i w związku z tym jest subskrybowana w ramach śledzenia profilowania za pomocą [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="59d7f-132">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="59d7f-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="59d7f-133">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.VariableElementCollection?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="59d7f-134">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="59d7f-134">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="59d7f-135">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="59d7f-135">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
