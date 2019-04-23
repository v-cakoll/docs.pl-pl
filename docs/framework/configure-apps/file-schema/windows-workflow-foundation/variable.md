---
title: <variable>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 46cc8cbc-10ec-4625-8813-3f5cd6c6afde
ms.openlocfilehash: c85f3c57739c48566c97c8b1debfb7f2c3912bdf
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59196635"
---
# <a name="variable"></a><span data-ttu-id="39f91-101">\<Zmienna ></span><span class="sxs-lookup"><span data-stu-id="39f91-101">\<variable></span></span>
<span data-ttu-id="39f91-102">Reprezentuje kolekcję zmiennych skojarzoną z tym zapytaniem działania.</span><span class="sxs-lookup"><span data-stu-id="39f91-102">Represents a collection of variables associated with this activity query.</span></span>  
  
 <span data-ttu-id="39f91-103">Aby uzyskać więcej informacji na podstawie śledzenia zapytań profilu zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="39f91-103">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="39f91-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="39f91-104">\<system.serviceModel></span></span>  
<span data-ttu-id="39f91-105">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="39f91-105">\<tracking></span></span>  
<span data-ttu-id="39f91-106">\<profiles></span><span class="sxs-lookup"><span data-stu-id="39f91-106">\<profiles></span></span>  
<span data-ttu-id="39f91-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="39f91-107">\<trackingProfile></span></span>  
<span data-ttu-id="39f91-108">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="39f91-108">\<workflow></span></span>  
<span data-ttu-id="39f91-109">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="39f91-109">\<activityStateQueries></span></span>  
<span data-ttu-id="39f91-110">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="39f91-110">\<activityStateQuery></span></span>  
<span data-ttu-id="39f91-111">\<Zmienne ></span><span class="sxs-lookup"><span data-stu-id="39f91-111">\<variables></span></span>  
<span data-ttu-id="39f91-112">\<Zmienna ></span><span class="sxs-lookup"><span data-stu-id="39f91-112">\<variable></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39f91-113">Składnia</span><span class="sxs-lookup"><span data-stu-id="39f91-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="39f91-114">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="39f91-114">Attributes and Elements</span></span>  
 <span data-ttu-id="39f91-115">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="39f91-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="39f91-116">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="39f91-116">Attributes</span></span>  
  
|<span data-ttu-id="39f91-117">Atrybut</span><span class="sxs-lookup"><span data-stu-id="39f91-117">Attribute</span></span>|<span data-ttu-id="39f91-118">Opis</span><span class="sxs-lookup"><span data-stu-id="39f91-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="39f91-119">nazwa</span><span class="sxs-lookup"><span data-stu-id="39f91-119">name</span></span>|<span data-ttu-id="39f91-120">Ciąg określający nazwę zmiennej.</span><span class="sxs-lookup"><span data-stu-id="39f91-120">A string that specifies the name of the variable.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="39f91-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="39f91-121">Child Elements</span></span>  
 <span data-ttu-id="39f91-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="39f91-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="39f91-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="39f91-123">Parent Elements</span></span>  
  
|<span data-ttu-id="39f91-124">Element</span><span class="sxs-lookup"><span data-stu-id="39f91-124">Element</span></span>|<span data-ttu-id="39f91-125">Opis</span><span class="sxs-lookup"><span data-stu-id="39f91-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="39f91-126">\<Zmienna ></span><span class="sxs-lookup"><span data-stu-id="39f91-126">\<variable></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/variable.md)|<span data-ttu-id="39f91-127">Zmienna skojarzonych z kwerendą stanu działania.</span><span class="sxs-lookup"><span data-stu-id="39f91-127">A variable associated with an activity state query.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="39f91-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="39f91-128">Remarks</span></span>  
 <span data-ttu-id="39f91-129">Jedno rozwiązanie ActivityStateQuery jest możliwość wyodrębniania danych podczas śledzenia wykonywania przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="39f91-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="39f91-130">Umożliwia to dodatkowy kontekst podczas uzyskiwania dostępu do śledzenia rekordów post wykonywania.</span><span class="sxs-lookup"><span data-stu-id="39f91-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="39f91-131">Możesz użyć [ \<argumenty >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<stany >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) i [ \<stany >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elementy, aby wyodrębnić dowolnej zmiennej lub argumentu wszelkie działania w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="39f91-131">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="39f91-132">W poniższym przykładzie pokazano kwerendą stanu działania, który wyodrębnia zmienne i argumenty podczas działania `Closed` rekord śledzenia jest emitowane.</span><span class="sxs-lookup"><span data-stu-id="39f91-132">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="39f91-133">Zmienne i argumenty wyodrębniania tylko z ActivityStateRecord i w związku z tym subskrybują w ramach śledzenia profilu przy użyciu [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="39f91-133">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="39f91-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="39f91-134">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.VariableElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="39f91-135">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="39f91-135">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="39f91-136">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="39f91-136">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
