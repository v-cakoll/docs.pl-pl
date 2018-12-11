---
title: '&lt;Argument&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a7144d53-8023-4e90-971f-895e016fd58a
ms.openlocfilehash: 8172093f36bd09ea33b1a447ee61dc36afb1b358
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53154232"
---
# <a name="ltargumentgt"></a><span data-ttu-id="58d08-102">&lt;Argument&gt;</span><span class="sxs-lookup"><span data-stu-id="58d08-102">&lt;argument&gt;</span></span>
<span data-ttu-id="58d08-103">Element konfiguracji, który reprezentuje argumentu skojarzonych z kwerendą stanu działania.</span><span class="sxs-lookup"><span data-stu-id="58d08-103">A configuration element that represents an argument associated with an activity state query.</span></span>  
  
 <span data-ttu-id="58d08-104">Aby uzyskać więcej informacji na podstawie śledzenia zapytań profilu zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="58d08-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="58d08-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="58d08-105">\<system.serviceModel></span></span>  
<span data-ttu-id="58d08-106">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="58d08-106">\<tracking></span></span>  
<span data-ttu-id="58d08-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="58d08-107">\<trackingProfile></span></span>  
<span data-ttu-id="58d08-108">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="58d08-108">\<workflow></span></span>  
<span data-ttu-id="58d08-109">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="58d08-109">\<activityStateQueries></span></span>  
<span data-ttu-id="58d08-110">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="58d08-110">\<activityStateQuery></span></span>  
<span data-ttu-id="58d08-111">\<argumenty ></span><span class="sxs-lookup"><span data-stu-id="58d08-111">\<arguments></span></span>  
<span data-ttu-id="58d08-112">\<argument ></span><span class="sxs-lookup"><span data-stu-id="58d08-112">\<argument></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58d08-113">Składnia</span><span class="sxs-lookup"><span data-stu-id="58d08-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="58d08-114">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="58d08-114">Attributes and Elements</span></span>  
 <span data-ttu-id="58d08-115">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="58d08-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="58d08-116">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="58d08-116">Attributes</span></span>  
  
|<span data-ttu-id="58d08-117">Atrybut</span><span class="sxs-lookup"><span data-stu-id="58d08-117">Attribute</span></span>|<span data-ttu-id="58d08-118">Opis</span><span class="sxs-lookup"><span data-stu-id="58d08-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="58d08-119">nazwa</span><span class="sxs-lookup"><span data-stu-id="58d08-119">name</span></span>|<span data-ttu-id="58d08-120">Ciąg określający nazwę argumentu.</span><span class="sxs-lookup"><span data-stu-id="58d08-120">A string that specifies the name of the argument.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="58d08-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="58d08-121">Child Elements</span></span>  
 <span data-ttu-id="58d08-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="58d08-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="58d08-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="58d08-123">Parent Elements</span></span>  
  
|<span data-ttu-id="58d08-124">Element</span><span class="sxs-lookup"><span data-stu-id="58d08-124">Element</span></span>|<span data-ttu-id="58d08-125">Opis</span><span class="sxs-lookup"><span data-stu-id="58d08-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="58d08-126">\<argumenty ></span><span class="sxs-lookup"><span data-stu-id="58d08-126">\<arguments></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md)|<span data-ttu-id="58d08-127">Kolekcja argumenty skojarzone z tej kwerendy działania.</span><span class="sxs-lookup"><span data-stu-id="58d08-127">A collection of arguments associated with this activity query.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="58d08-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="58d08-128">Remarks</span></span>  
 <span data-ttu-id="58d08-129">Jedno rozwiązanie ActivityStateQuery jest możliwość wyodrębniania danych podczas śledzenia wykonywania przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="58d08-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="58d08-130">Umożliwia to dodatkowy kontekst podczas uzyskiwania dostępu do śledzenia rekordów post wykonywania.</span><span class="sxs-lookup"><span data-stu-id="58d08-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="58d08-131">Możesz użyć [ \<argumenty >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<stany >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) i [ \<stany >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elementy, aby wyodrębnić dowolnej zmiennej lub argumentu wszelkie działania w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="58d08-131">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="58d08-132">W poniższym przykładzie pokazano kwerendą stanu działania, który wyodrębnia zmienne i argumenty podczas działania `Closed` rekord śledzenia jest emitowane.</span><span class="sxs-lookup"><span data-stu-id="58d08-132">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="58d08-133">Zmienne i argumenty wyodrębniania tylko z ActivityStateRecord i w związku z tym subskrybują w ramach śledzenia profilu przy użyciu [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="58d08-133">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="58d08-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="58d08-134">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.ArgumentElement?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="58d08-135">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="58d08-135">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="58d08-136">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="58d08-136">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
