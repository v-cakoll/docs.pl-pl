---
title: <state> z <states>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ab483c7f-a091-4933-ba6b-708d96846d38
ms.openlocfilehash: ff75895949c50cd369e4297ea77dc21106994067
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59073939"
---
# <a name="state-of-states"></a><span data-ttu-id="acb5f-102">\<Stan > z \<stany ></span><span class="sxs-lookup"><span data-stu-id="acb5f-102">\<state> of \<states></span></span>
<span data-ttu-id="acb5f-103">Element konfiguracji, który zawiera stan subskrybowanego działania, dla którego należy obliczanie rekord śledzenia.</span><span class="sxs-lookup"><span data-stu-id="acb5f-103">A configuration element that contains the state of the subscribed activity for which a tracking record should be emitted.</span></span>  
  
 <span data-ttu-id="acb5f-104">Aby uzyskać więcej informacji na podstawie śledzenia zapytań profilu zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="acb5f-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="acb5f-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="acb5f-105">\<system.serviceModel></span></span>  
<span data-ttu-id="acb5f-106">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="acb5f-106">\<tracking></span></span>  
<span data-ttu-id="acb5f-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="acb5f-107">\<trackingProfile></span></span>  
<span data-ttu-id="acb5f-108">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="acb5f-108">\<workflow></span></span>  
<span data-ttu-id="acb5f-109">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="acb5f-109">\<activityStateQueries></span></span>  
<span data-ttu-id="acb5f-110">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="acb5f-110">\<activityStateQuery></span></span>  
<span data-ttu-id="acb5f-111">\<Stany ></span><span class="sxs-lookup"><span data-stu-id="acb5f-111">\<states></span></span>  
<span data-ttu-id="acb5f-112">\<state></span><span class="sxs-lookup"><span data-stu-id="acb5f-112">\<state></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="acb5f-113">Składnia</span><span class="sxs-lookup"><span data-stu-id="acb5f-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="acb5f-114">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="acb5f-114">Attributes and Elements</span></span>  
 <span data-ttu-id="acb5f-115">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="acb5f-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="acb5f-116">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="acb5f-116">Attributes</span></span>  
  
|<span data-ttu-id="acb5f-117">Atrybut</span><span class="sxs-lookup"><span data-stu-id="acb5f-117">Attribute</span></span>|<span data-ttu-id="acb5f-118">Opis</span><span class="sxs-lookup"><span data-stu-id="acb5f-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="acb5f-119">nazwa</span><span class="sxs-lookup"><span data-stu-id="acb5f-119">name</span></span>|<span data-ttu-id="acb5f-120">Ciąg, który określa stan subskrybowanego działania, dla którego należy obliczanie rekord śledzenia.</span><span class="sxs-lookup"><span data-stu-id="acb5f-120">A string that specifies the state of the subscribed activity for which a tracking record should be emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="acb5f-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="acb5f-121">Child Elements</span></span>  
 <span data-ttu-id="acb5f-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="acb5f-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="acb5f-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="acb5f-123">Parent Elements</span></span>  
  
|<span data-ttu-id="acb5f-124">Element</span><span class="sxs-lookup"><span data-stu-id="acb5f-124">Element</span></span>|<span data-ttu-id="acb5f-125">Opis</span><span class="sxs-lookup"><span data-stu-id="acb5f-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="acb5f-126">\<Stany ></span><span class="sxs-lookup"><span data-stu-id="acb5f-126">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states-of-activitystatequery.md)|<span data-ttu-id="acb5f-127">Kolekcja elementów konfiguracji, które zawierają stany subskrybowanego działania, dla którego należy obliczanie rekord śledzenia.</span><span class="sxs-lookup"><span data-stu-id="acb5f-127">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="acb5f-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="acb5f-128">Remarks</span></span>  
 <span data-ttu-id="acb5f-129">Jedno rozwiązanie ActivityStateQuery jest możliwość wyodrębniania danych podczas śledzenia wykonywania przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="acb5f-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="acb5f-130">Umożliwia to dodatkowy kontekst podczas uzyskiwania dostępu do śledzenia rekordów post wykonywania.</span><span class="sxs-lookup"><span data-stu-id="acb5f-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="acb5f-131">Możesz użyć [ \<argumenty >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<stany >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) i [ \<stany >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elementy, aby wyodrębnić dowolnej zmiennej lub argumentu wszelkie działania w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="acb5f-131">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="acb5f-132">W poniższym przykładzie pokazano kwerendą stanu działania, który wyodrębnia zmienne i argumenty podczas działania `Closed` rekord śledzenia jest emitowane.</span><span class="sxs-lookup"><span data-stu-id="acb5f-132">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="acb5f-133">Zmienne i argumenty wyodrębniania tylko z ActivityStateRecord i w związku z tym subskrybują w ramach śledzenia profilu przy użyciu [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="acb5f-133">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="acb5f-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="acb5f-134">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="acb5f-135">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="acb5f-135">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="acb5f-136">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="acb5f-136">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
