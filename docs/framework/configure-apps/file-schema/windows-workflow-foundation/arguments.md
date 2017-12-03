---
title: '&lt;argumenty&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 0f327196-f468-4be3-b6c4-68ba981a1bd6
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 58e5f9ede15edfbc6627ba8f4e9055fb673db806
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltargumentsgt"></a><span data-ttu-id="e003b-102">&lt;argumenty&gt;</span><span class="sxs-lookup"><span data-stu-id="e003b-102">&lt;arguments&gt;</span></span>
<span data-ttu-id="e003b-103">Reprezentuje kolekcję argumentów skojarzonych z kwerendą stanu działania.</span><span class="sxs-lookup"><span data-stu-id="e003b-103">Represents a collection of arguments associated with an activity state query.</span></span>  
  
 <span data-ttu-id="e003b-104">Aby uzyskać więcej informacji na zapytania dotyczące profilu śledzenia, zobacz [śledzenia profile](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="e003b-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="e003b-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="e003b-105">\<system.serviceModel></span></span>  
<span data-ttu-id="e003b-106">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="e003b-106">\<tracking></span></span>  
<span data-ttu-id="e003b-107">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="e003b-107">\<trackingProfile></span></span>  
<span data-ttu-id="e003b-108">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="e003b-108">\<workflow></span></span>  
<span data-ttu-id="e003b-109">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="e003b-109">\<activityStateQueries></span></span>  
<span data-ttu-id="e003b-110">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="e003b-110">\<activityStateQuery></span></span>  
<span data-ttu-id="e003b-111">\<argumenty ></span><span class="sxs-lookup"><span data-stu-id="e003b-111">\<arguments></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e003b-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="e003b-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e003b-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e003b-113">Attributes and Elements</span></span>  
 <span data-ttu-id="e003b-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e003b-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e003b-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e003b-115">Attributes</span></span>  
 <span data-ttu-id="e003b-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="e003b-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e003b-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e003b-117">Child Elements</span></span>  
  
|<span data-ttu-id="e003b-118">Element</span><span class="sxs-lookup"><span data-stu-id="e003b-118">Element</span></span>|<span data-ttu-id="e003b-119">Opis</span><span class="sxs-lookup"><span data-stu-id="e003b-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e003b-120">\<argument ></span><span class="sxs-lookup"><span data-stu-id="e003b-120">\<argument></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/argument.md)|<span data-ttu-id="e003b-121">Argument skojarzonych z kwerendą stanu działania.</span><span class="sxs-lookup"><span data-stu-id="e003b-121">An argument associated with an activity state query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e003b-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e003b-122">Parent Elements</span></span>  
  
|<span data-ttu-id="e003b-123">Element</span><span class="sxs-lookup"><span data-stu-id="e003b-123">Element</span></span>|<span data-ttu-id="e003b-124">Opis</span><span class="sxs-lookup"><span data-stu-id="e003b-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e003b-125">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="e003b-125">\<activityStateQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)|<span data-ttu-id="e003b-126">Reprezentuje element konfiguracji, które jest używane do śledzenia żądań, aby anulować działanie podrzędne przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e003b-126">Represents a configuration element that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="e003b-127">Zapytanie jest niezbędne do uczestnika śledzenia do subskrybowania Anuluj żądanie rekordu obiektów.</span><span class="sxs-lookup"><span data-stu-id="e003b-127">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e003b-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e003b-128">Remarks</span></span>  
 <span data-ttu-id="e003b-129">Jedno rozwiązanie ActivityStateQuery jest możliwość wyodrębniania danych podczas śledzenia wykonywania przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="e003b-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="e003b-130">Umożliwia to dodatkowy kontekst podczas uzyskiwania dostępu do śledzenia rekordów post wykonywania.</span><span class="sxs-lookup"><span data-stu-id="e003b-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="e003b-131">Można użyć [ \<argumentów >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<stanów >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) i [ \<stanów >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elementy, aby wyodrębnić żadnych zmiennej lub argumentu wszystkie działania w przepływie pracy. W poniższym przykładzie przedstawiono kwerendy stanu działania, która wyodrębnia zmiennych i argumenty podczas działania `Closed` śledzenia rekord jest emitowany.</span><span class="sxs-lookup"><span data-stu-id="e003b-131">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="e003b-132">Argumenty i zmienne można wyodrębnić tylko z ActivityStateRecord i w związku z tym jest subskrybowana w ramach śledzenia profilowania za pomocą [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="e003b-132">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e003b-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e003b-133">See Also</span></span>  
 <span data-ttu-id="e003b-134"><xref:System.ServiceModel.Activities.Tracking.Configuration.ArgumentElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="e003b-134"><xref:System.ServiceModel.Activities.Tracking.Configuration.ArgumentElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="e003b-135"><xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="e003b-135"><xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="e003b-136">Przepływ pracy, kontrola i śledzenie</span><span class="sxs-lookup"><span data-stu-id="e003b-136">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="e003b-137">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="e003b-137">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
