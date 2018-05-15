---
title: '&lt;Stan&gt; z &lt;stanów&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ab483c7f-a091-4933-ba6b-708d96846d38
ms.openlocfilehash: 8893f6acfc7ec4d6989be2c647b0584093a534a1
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltstategt-of-ltstatesgt"></a><span data-ttu-id="5cbc8-102">&lt;Stan&gt; z &lt;stanów&gt;</span><span class="sxs-lookup"><span data-stu-id="5cbc8-102">&lt;state&gt; of &lt;states&gt;</span></span>
<span data-ttu-id="5cbc8-103">Element konfiguracji, który zawiera stan subskrybowanego działania, dla którego należy obliczanie rekord śledzenia.</span><span class="sxs-lookup"><span data-stu-id="5cbc8-103">A configuration element that contains the state of the subscribed activity for which a tracking record should be emitted.</span></span>  
  
 <span data-ttu-id="5cbc8-104">Aby uzyskać więcej informacji na zapytania dotyczące profilu śledzenia, zobacz [śledzenia profile](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="5cbc8-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="5cbc8-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="5cbc8-105">\<system.serviceModel></span></span>  
<span data-ttu-id="5cbc8-106">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="5cbc8-106">\<tracking></span></span>  
<span data-ttu-id="5cbc8-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="5cbc8-107">\<trackingProfile></span></span>  
<span data-ttu-id="5cbc8-108">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="5cbc8-108">\<workflow></span></span>  
<span data-ttu-id="5cbc8-109">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="5cbc8-109">\<activityStateQueries></span></span>  
<span data-ttu-id="5cbc8-110">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="5cbc8-110">\<activityStateQuery></span></span>  
<span data-ttu-id="5cbc8-111">\<Stany ></span><span class="sxs-lookup"><span data-stu-id="5cbc8-111">\<states></span></span>  
<span data-ttu-id="5cbc8-112">\<Stan ></span><span class="sxs-lookup"><span data-stu-id="5cbc8-112">\<state></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5cbc8-113">Składnia</span><span class="sxs-lookup"><span data-stu-id="5cbc8-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5cbc8-114">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="5cbc8-114">Attributes and Elements</span></span>  
 <span data-ttu-id="5cbc8-115">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="5cbc8-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5cbc8-116">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="5cbc8-116">Attributes</span></span>  
  
|<span data-ttu-id="5cbc8-117">Atrybut</span><span class="sxs-lookup"><span data-stu-id="5cbc8-117">Attribute</span></span>|<span data-ttu-id="5cbc8-118">Opis</span><span class="sxs-lookup"><span data-stu-id="5cbc8-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5cbc8-119">nazwa</span><span class="sxs-lookup"><span data-stu-id="5cbc8-119">name</span></span>|<span data-ttu-id="5cbc8-120">Ciąg, który określa stan subskrybowanego działania, dla którego należy obliczanie rekord śledzenia.</span><span class="sxs-lookup"><span data-stu-id="5cbc8-120">A string that specifies the state of the subscribed activity for which a tracking record should be emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5cbc8-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="5cbc8-121">Child Elements</span></span>  
 <span data-ttu-id="5cbc8-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="5cbc8-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5cbc8-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="5cbc8-123">Parent Elements</span></span>  
  
|<span data-ttu-id="5cbc8-124">Element</span><span class="sxs-lookup"><span data-stu-id="5cbc8-124">Element</span></span>|<span data-ttu-id="5cbc8-125">Opis</span><span class="sxs-lookup"><span data-stu-id="5cbc8-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5cbc8-126">\<Stany ></span><span class="sxs-lookup"><span data-stu-id="5cbc8-126">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states-of-activitystatequery.md)|<span data-ttu-id="5cbc8-127">Kolekcja elementów konfiguracji, które zawierają stany subskrybowanego działania, dla którego należy obliczanie rekord śledzenia.</span><span class="sxs-lookup"><span data-stu-id="5cbc8-127">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5cbc8-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5cbc8-128">Remarks</span></span>  
 <span data-ttu-id="5cbc8-129">Jedno rozwiązanie ActivityStateQuery jest możliwość wyodrębniania danych podczas śledzenia wykonywania przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="5cbc8-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="5cbc8-130">Umożliwia to dodatkowy kontekst podczas uzyskiwania dostępu do śledzenia rekordów post wykonywania.</span><span class="sxs-lookup"><span data-stu-id="5cbc8-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="5cbc8-131">Można użyć [ \<argumentów >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<stanów >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) i [ \<stanów >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elementy, aby wyodrębnić żadnych zmiennej lub argumentu wszystkie działania w przepływie pracy. W poniższym przykładzie przedstawiono kwerendy stanu działania, która wyodrębnia zmiennych i argumenty podczas działania `Closed` śledzenia rekord jest emitowany.</span><span class="sxs-lookup"><span data-stu-id="5cbc8-131">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="5cbc8-132">Argumenty i zmienne można wyodrębnić tylko z ActivityStateRecord i w związku z tym jest subskrybowana w ramach śledzenia profilowania za pomocą [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="5cbc8-132">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5cbc8-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5cbc8-133">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="5cbc8-134">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="5cbc8-134">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="5cbc8-135">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="5cbc8-135">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
