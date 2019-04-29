---
title: <variable>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 46cc8cbc-10ec-4625-8813-3f5cd6c6afde
ms.openlocfilehash: c85f3c57739c48566c97c8b1debfb7f2c3912bdf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61613524"
---
# <a name="variable"></a><span data-ttu-id="dc10b-101">\<Zmienna ></span><span class="sxs-lookup"><span data-stu-id="dc10b-101">\<variable></span></span>
<span data-ttu-id="dc10b-102">Reprezentuje kolekcję zmiennych skojarzoną z tym zapytaniem działania.</span><span class="sxs-lookup"><span data-stu-id="dc10b-102">Represents a collection of variables associated with this activity query.</span></span>  
  
 <span data-ttu-id="dc10b-103">Aby uzyskać więcej informacji na podstawie śledzenia zapytań profilu zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="dc10b-103">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="dc10b-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="dc10b-104">\<system.serviceModel></span></span>  
<span data-ttu-id="dc10b-105">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="dc10b-105">\<tracking></span></span>  
<span data-ttu-id="dc10b-106">\<profiles></span><span class="sxs-lookup"><span data-stu-id="dc10b-106">\<profiles></span></span>  
<span data-ttu-id="dc10b-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="dc10b-107">\<trackingProfile></span></span>  
<span data-ttu-id="dc10b-108">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="dc10b-108">\<workflow></span></span>  
<span data-ttu-id="dc10b-109">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="dc10b-109">\<activityStateQueries></span></span>  
<span data-ttu-id="dc10b-110">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="dc10b-110">\<activityStateQuery></span></span>  
<span data-ttu-id="dc10b-111">\<Zmienne ></span><span class="sxs-lookup"><span data-stu-id="dc10b-111">\<variables></span></span>  
<span data-ttu-id="dc10b-112">\<Zmienna ></span><span class="sxs-lookup"><span data-stu-id="dc10b-112">\<variable></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc10b-113">Składnia</span><span class="sxs-lookup"><span data-stu-id="dc10b-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dc10b-114">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="dc10b-114">Attributes and Elements</span></span>  
 <span data-ttu-id="dc10b-115">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="dc10b-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dc10b-116">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="dc10b-116">Attributes</span></span>  
  
|<span data-ttu-id="dc10b-117">Atrybut</span><span class="sxs-lookup"><span data-stu-id="dc10b-117">Attribute</span></span>|<span data-ttu-id="dc10b-118">Opis</span><span class="sxs-lookup"><span data-stu-id="dc10b-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dc10b-119">nazwa</span><span class="sxs-lookup"><span data-stu-id="dc10b-119">name</span></span>|<span data-ttu-id="dc10b-120">Ciąg określający nazwę zmiennej.</span><span class="sxs-lookup"><span data-stu-id="dc10b-120">A string that specifies the name of the variable.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dc10b-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="dc10b-121">Child Elements</span></span>  
 <span data-ttu-id="dc10b-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="dc10b-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dc10b-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="dc10b-123">Parent Elements</span></span>  
  
|<span data-ttu-id="dc10b-124">Element</span><span class="sxs-lookup"><span data-stu-id="dc10b-124">Element</span></span>|<span data-ttu-id="dc10b-125">Opis</span><span class="sxs-lookup"><span data-stu-id="dc10b-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dc10b-126">\<Zmienna ></span><span class="sxs-lookup"><span data-stu-id="dc10b-126">\<variable></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/variable.md)|<span data-ttu-id="dc10b-127">Zmienna skojarzonych z kwerendą stanu działania.</span><span class="sxs-lookup"><span data-stu-id="dc10b-127">A variable associated with an activity state query.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dc10b-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dc10b-128">Remarks</span></span>  
 <span data-ttu-id="dc10b-129">Jedno rozwiązanie ActivityStateQuery jest możliwość wyodrębniania danych podczas śledzenia wykonywania przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="dc10b-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="dc10b-130">Umożliwia to dodatkowy kontekst podczas uzyskiwania dostępu do śledzenia rekordów post wykonywania.</span><span class="sxs-lookup"><span data-stu-id="dc10b-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="dc10b-131">Możesz użyć [ \<argumenty >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<stany >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) i [ \<stany >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elementy, aby wyodrębnić dowolnej zmiennej lub argumentu wszelkie działania w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="dc10b-131">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="dc10b-132">W poniższym przykładzie pokazano kwerendą stanu działania, który wyodrębnia zmienne i argumenty podczas działania `Closed` rekord śledzenia jest emitowane.</span><span class="sxs-lookup"><span data-stu-id="dc10b-132">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="dc10b-133">Zmienne i argumenty wyodrębniania tylko z ActivityStateRecord i w związku z tym subskrybują w ramach śledzenia profilu przy użyciu [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="dc10b-133">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="dc10b-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dc10b-134">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.VariableElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="dc10b-135">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="dc10b-135">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="dc10b-136">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="dc10b-136">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
