---
title: '&lt;Zmienna&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 46cc8cbc-10ec-4625-8813-3f5cd6c6afde
ms.openlocfilehash: 7d41d80bfe83cfafca01509d50709e21730bcb97
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32756790"
---
# <a name="ltvariablegt"></a><span data-ttu-id="dd142-102">&lt;Zmienna&gt;</span><span class="sxs-lookup"><span data-stu-id="dd142-102">&lt;variable&gt;</span></span>
<span data-ttu-id="dd142-103">Reprezentuje kolekcję zmiennych skojarzoną z tym zapytaniem działania.</span><span class="sxs-lookup"><span data-stu-id="dd142-103">Represents a collection of variables associated with this activity query.</span></span>  
  
 <span data-ttu-id="dd142-104">Aby uzyskać więcej informacji na zapytania dotyczące profilu śledzenia, zobacz [śledzenia profile](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="dd142-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="dd142-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="dd142-105">\<system.serviceModel></span></span>  
<span data-ttu-id="dd142-106">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="dd142-106">\<tracking></span></span>  
<span data-ttu-id="dd142-107">\<profile ></span><span class="sxs-lookup"><span data-stu-id="dd142-107">\<profiles></span></span>  
<span data-ttu-id="dd142-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="dd142-108">\<trackingProfile></span></span>  
<span data-ttu-id="dd142-109">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="dd142-109">\<workflow></span></span>  
<span data-ttu-id="dd142-110">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="dd142-110">\<activityStateQueries></span></span>  
<span data-ttu-id="dd142-111">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="dd142-111">\<activityStateQuery></span></span>  
<span data-ttu-id="dd142-112">\<Zmienne ></span><span class="sxs-lookup"><span data-stu-id="dd142-112">\<variables></span></span>  
<span data-ttu-id="dd142-113">\<Zmienna ></span><span class="sxs-lookup"><span data-stu-id="dd142-113">\<variable></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd142-114">Składnia</span><span class="sxs-lookup"><span data-stu-id="dd142-114">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dd142-115">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="dd142-115">Attributes and Elements</span></span>  
 <span data-ttu-id="dd142-116">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="dd142-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dd142-117">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="dd142-117">Attributes</span></span>  
  
|<span data-ttu-id="dd142-118">Atrybut</span><span class="sxs-lookup"><span data-stu-id="dd142-118">Attribute</span></span>|<span data-ttu-id="dd142-119">Opis</span><span class="sxs-lookup"><span data-stu-id="dd142-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dd142-120">nazwa</span><span class="sxs-lookup"><span data-stu-id="dd142-120">name</span></span>|<span data-ttu-id="dd142-121">Ciąg określający nazwę zmiennej.</span><span class="sxs-lookup"><span data-stu-id="dd142-121">A string that specifies the name of the variable.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dd142-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="dd142-122">Child Elements</span></span>  
 <span data-ttu-id="dd142-123">Brak.</span><span class="sxs-lookup"><span data-stu-id="dd142-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dd142-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="dd142-124">Parent Elements</span></span>  
  
|<span data-ttu-id="dd142-125">Element</span><span class="sxs-lookup"><span data-stu-id="dd142-125">Element</span></span>|<span data-ttu-id="dd142-126">Opis</span><span class="sxs-lookup"><span data-stu-id="dd142-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dd142-127">\<Zmienna ></span><span class="sxs-lookup"><span data-stu-id="dd142-127">\<variable></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/variable.md)|<span data-ttu-id="dd142-128">Zmienna skojarzonych z kwerendą stanu działania.</span><span class="sxs-lookup"><span data-stu-id="dd142-128">A variable associated with an activity state query.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dd142-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dd142-129">Remarks</span></span>  
 <span data-ttu-id="dd142-130">Jedno rozwiązanie ActivityStateQuery jest możliwość wyodrębniania danych podczas śledzenia wykonywania przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="dd142-130">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="dd142-131">Umożliwia to dodatkowy kontekst podczas uzyskiwania dostępu do śledzenia rekordów post wykonywania.</span><span class="sxs-lookup"><span data-stu-id="dd142-131">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="dd142-132">Można użyć [ \<argumentów >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<stanów >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) i [ \<stanów >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elementy, aby wyodrębnić żadnych zmiennej lub argumentu wszystkie działania w przepływie pracy. W poniższym przykładzie przedstawiono kwerendy stanu działania, która wyodrębnia zmiennych i argumenty podczas działania `Closed` śledzenia rekord jest emitowany.</span><span class="sxs-lookup"><span data-stu-id="dd142-132">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="dd142-133">Argumenty i zmienne można wyodrębnić tylko z ActivityStateRecord i w związku z tym jest subskrybowana w ramach śledzenia profilowania za pomocą [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="dd142-133">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="dd142-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dd142-134">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.VariableElement?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="dd142-135">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="dd142-135">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="dd142-136">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="dd142-136">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
