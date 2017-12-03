---
title: '&lt;argument&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: a7144d53-8023-4e90-971f-895e016fd58a
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b3625d3bf6aa415c34b9c05bebdec390bcb51f69
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltargumentgt"></a><span data-ttu-id="1ec58-102">&lt;argument&gt;</span><span class="sxs-lookup"><span data-stu-id="1ec58-102">&lt;argument&gt;</span></span>
<span data-ttu-id="1ec58-103">Element konfiguracji, który reprezentuje argumentu skojarzonych z kwerendą stanu działania.</span><span class="sxs-lookup"><span data-stu-id="1ec58-103">A configuration element that represents an argument associated with an activity state query.</span></span>  
  
 <span data-ttu-id="1ec58-104">Aby uzyskać więcej informacji na zapytania dotyczące profilu śledzenia, zobacz [śledzenia profile](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="1ec58-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="1ec58-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="1ec58-105">\<system.serviceModel></span></span>  
<span data-ttu-id="1ec58-106">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="1ec58-106">\<tracking></span></span>  
<span data-ttu-id="1ec58-107">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="1ec58-107">\<trackingProfile></span></span>  
<span data-ttu-id="1ec58-108">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="1ec58-108">\<workflow></span></span>  
<span data-ttu-id="1ec58-109">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="1ec58-109">\<activityStateQueries></span></span>  
<span data-ttu-id="1ec58-110">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="1ec58-110">\<activityStateQuery></span></span>  
<span data-ttu-id="1ec58-111">\<argumenty ></span><span class="sxs-lookup"><span data-stu-id="1ec58-111">\<arguments></span></span>  
<span data-ttu-id="1ec58-112">\<argument ></span><span class="sxs-lookup"><span data-stu-id="1ec58-112">\<argument></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ec58-113">Składnia</span><span class="sxs-lookup"><span data-stu-id="1ec58-113">Syntax</span></span>  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <arguments>
          <argument name="String"/>
        </arguments>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1ec58-114">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1ec58-114">Attributes and Elements</span></span>  
 <span data-ttu-id="1ec58-115">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="1ec58-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1ec58-116">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1ec58-116">Attributes</span></span>  
  
|<span data-ttu-id="1ec58-117">Atrybut</span><span class="sxs-lookup"><span data-stu-id="1ec58-117">Attribute</span></span>|<span data-ttu-id="1ec58-118">Opis</span><span class="sxs-lookup"><span data-stu-id="1ec58-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1ec58-119">nazwa</span><span class="sxs-lookup"><span data-stu-id="1ec58-119">name</span></span>|<span data-ttu-id="1ec58-120">Ciąg określający nazwę argumentu.</span><span class="sxs-lookup"><span data-stu-id="1ec58-120">A string that specifies the name of the argument.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1ec58-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1ec58-121">Child Elements</span></span>  
 <span data-ttu-id="1ec58-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="1ec58-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1ec58-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1ec58-123">Parent Elements</span></span>  
  
|<span data-ttu-id="1ec58-124">Element</span><span class="sxs-lookup"><span data-stu-id="1ec58-124">Element</span></span>|<span data-ttu-id="1ec58-125">Opis</span><span class="sxs-lookup"><span data-stu-id="1ec58-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1ec58-126">\<argumenty ></span><span class="sxs-lookup"><span data-stu-id="1ec58-126">\<arguments></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md)|<span data-ttu-id="1ec58-127">Kolekcja argumenty skojarzone z tej kwerendy działania.</span><span class="sxs-lookup"><span data-stu-id="1ec58-127">A collection of arguments associated with this activity query.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1ec58-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1ec58-128">Remarks</span></span>  
 <span data-ttu-id="1ec58-129">Jedno rozwiązanie ActivityStateQuery jest możliwość wyodrębniania danych podczas śledzenia wykonywania przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="1ec58-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="1ec58-130">Umożliwia to dodatkowy kontekst podczas uzyskiwania dostępu do śledzenia rekordów post wykonywania.</span><span class="sxs-lookup"><span data-stu-id="1ec58-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="1ec58-131">Można użyć [ \<argumentów >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<stanów >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) i [ \<stanów >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elementy, aby wyodrębnić żadnych zmiennej lub argumentu wszystkie działania w przepływie pracy. W poniższym przykładzie przedstawiono kwerendy stanu działania, która wyodrębnia zmiennych i argumenty podczas działania `Closed` śledzenia rekord jest emitowany.</span><span class="sxs-lookup"><span data-stu-id="1ec58-131">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="1ec58-132">Argumenty i zmienne można wyodrębnić tylko z ActivityStateRecord i w związku z tym jest subskrybowana w ramach śledzenia profilowania za pomocą [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="1ec58-132">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1ec58-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1ec58-133">See Also</span></span>  
 <span data-ttu-id="1ec58-134"><xref:System.ServiceModel.Activities.Tracking.Configuration.ArgumentElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="1ec58-134"><xref:System.ServiceModel.Activities.Tracking.Configuration.ArgumentElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="1ec58-135"><xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="1ec58-135"><xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="1ec58-136">Przepływ pracy, kontrola i śledzenie</span><span class="sxs-lookup"><span data-stu-id="1ec58-136">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="1ec58-137">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="1ec58-137">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
