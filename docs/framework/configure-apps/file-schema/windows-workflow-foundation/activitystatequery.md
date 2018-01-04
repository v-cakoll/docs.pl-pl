---
title: '&lt;activityStateQuery&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 9f8c3e4f-e2e3-4402-9760-03bf918ece7b
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 00ed194606fa6f6abda81de0d6fa76857826e6fa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltactivitystatequerygt"></a><span data-ttu-id="cd7d7-102">&lt;activityStateQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="cd7d7-102">&lt;activityStateQuery&gt;</span></span>
<span data-ttu-id="cd7d7-103">Reprezentuje zapytanie, które jest używane do śledzenia zmian cyklem życia działań, które tworzą wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="cd7d7-103">Represents a query that is used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="cd7d7-104">Na przykład może być do śledzenia każdorazowo po ukończeniu działania "Wyślij wiadomość E-Mail" w ramach wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="cd7d7-104">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="cd7d7-105">To zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania obiektów rekordu stanu działania.</span><span class="sxs-lookup"><span data-stu-id="cd7d7-105">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="cd7d7-106">Stany do subskrybowania są wyszczególnione w ActivityStates.</span><span class="sxs-lookup"><span data-stu-id="cd7d7-106">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
 <span data-ttu-id="cd7d7-107">Aby uzyskać więcej informacji na zapytania dotyczące profilu śledzenia, zobacz [śledzenia profile](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="cd7d7-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="cd7d7-108">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="cd7d7-108">\<system.serviceModel></span></span>  
<span data-ttu-id="cd7d7-109">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="cd7d7-109">\<tracking></span></span>  
<span data-ttu-id="cd7d7-110">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="cd7d7-110">\<trackingProfile></span></span>  
<span data-ttu-id="cd7d7-111">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="cd7d7-111">\<workflow></span></span>  
<span data-ttu-id="cd7d7-112">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="cd7d7-112">\<activityStateQueries></span></span>  
<span data-ttu-id="cd7d7-113">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="cd7d7-113">\<activityStateQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd7d7-114">Składnia</span><span class="sxs-lookup"><span data-stu-id="cd7d7-114">Syntax</span></span>  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <arguments>
          <argument name="String"/>
        </arguments>
        <states>
          <state name="String"/>
        </states>
        <variables>
          <variable name="String"/>
        </variables>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cd7d7-115">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="cd7d7-115">Attributes and Elements</span></span>  
 <span data-ttu-id="cd7d7-116">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="cd7d7-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cd7d7-117">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="cd7d7-117">Attributes</span></span>  
  
|<span data-ttu-id="cd7d7-118">Atrybut</span><span class="sxs-lookup"><span data-stu-id="cd7d7-118">Attribute</span></span>|<span data-ttu-id="cd7d7-119">Opis</span><span class="sxs-lookup"><span data-stu-id="cd7d7-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cd7d7-120">activityName</span><span class="sxs-lookup"><span data-stu-id="cd7d7-120">activityName</span></span>|<span data-ttu-id="cd7d7-121">Ciąg określający nazwę czynności, aby filtrować <xref:System.Activities.Tracking.ActivityStateRecord> wystąpień.</span><span class="sxs-lookup"><span data-stu-id="cd7d7-121">A string that specifies the name of the activity to filter <xref:System.Activities.Tracking.ActivityStateRecord> instances on.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cd7d7-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="cd7d7-122">Child Elements</span></span>  
  
|<span data-ttu-id="cd7d7-123">Element</span><span class="sxs-lookup"><span data-stu-id="cd7d7-123">Element</span></span>|<span data-ttu-id="cd7d7-124">Opis</span><span class="sxs-lookup"><span data-stu-id="cd7d7-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cd7d7-125">\<argumenty ></span><span class="sxs-lookup"><span data-stu-id="cd7d7-125">\<arguments></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md)|<span data-ttu-id="cd7d7-126">Kolekcja argumenty skojarzone z tej kwerendy działania.</span><span class="sxs-lookup"><span data-stu-id="cd7d7-126">A collection of arguments associated with this activity query.</span></span>|  
|[<span data-ttu-id="cd7d7-127">\<Stany ></span><span class="sxs-lookup"><span data-stu-id="cd7d7-127">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="cd7d7-128">Kolekcja elementów konfiguracji, które zawierają stany subskrybowanego działania, dla którego należy obliczanie rekord śledzenia.</span><span class="sxs-lookup"><span data-stu-id="cd7d7-128">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
|[<span data-ttu-id="cd7d7-129">\<Stany ></span><span class="sxs-lookup"><span data-stu-id="cd7d7-129">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="cd7d7-130">Kolekcja zmiennych skojarzoną z tym zapytaniem działania.</span><span class="sxs-lookup"><span data-stu-id="cd7d7-130">A collection of variables associated with this activity query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cd7d7-131">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="cd7d7-131">Parent Elements</span></span>  
  
|<span data-ttu-id="cd7d7-132">Element</span><span class="sxs-lookup"><span data-stu-id="cd7d7-132">Element</span></span>|<span data-ttu-id="cd7d7-133">Opis</span><span class="sxs-lookup"><span data-stu-id="cd7d7-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cd7d7-134">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="cd7d7-134">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="cd7d7-135">Reprezentuje listę elementów konfiguracji, które są używane do śledzenia żądań, aby anulować działanie podrzędne przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="cd7d7-135">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="cd7d7-136">Zapytanie jest niezbędne do uczestnika śledzenia do subskrybowania Anuluj żądanie rekordu obiektów.</span><span class="sxs-lookup"><span data-stu-id="cd7d7-136">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cd7d7-137">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cd7d7-137">Remarks</span></span>  
 <span data-ttu-id="cd7d7-138">Jedno rozwiązanie ActivityStateQuery jest możliwość wyodrębniania danych podczas śledzenia wykonywania przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="cd7d7-138">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="cd7d7-139">Umożliwia to dodatkowy kontekst podczas uzyskiwania dostępu do śledzenia rekordów post wykonywania.</span><span class="sxs-lookup"><span data-stu-id="cd7d7-139">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="cd7d7-140">Można użyć [ \<argumentów >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<stanów >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) i [ \<stanów >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elementy, aby wyodrębnić żadnych zmiennej lub argumentu wszystkie działania w przepływie pracy. W poniższym przykładzie przedstawiono kwerendy stanu działania, która wyodrębnia zmiennych i argumenty podczas działania `Closed` śledzenia rekord jest emitowany.</span><span class="sxs-lookup"><span data-stu-id="cd7d7-140">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="cd7d7-141">Argumenty i zmienne można wyodrębnić tylko z ActivityStateRecord i w związku z tym jest subskrybowana w ramach śledzenia profilowania za pomocą [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="cd7d7-141">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cd7d7-142">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cd7d7-142">See Also</span></span>  
 <span data-ttu-id="cd7d7-143"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="cd7d7-143"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="cd7d7-144"><xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="cd7d7-144"><xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="cd7d7-145">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="cd7d7-145">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="cd7d7-146">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="cd7d7-146">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
