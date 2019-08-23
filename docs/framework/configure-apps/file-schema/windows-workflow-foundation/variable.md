---
title: <variable>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 46cc8cbc-10ec-4625-8813-3f5cd6c6afde
ms.openlocfilehash: a8f66f950db1edf8cd6ec21400785fb7e01b878e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947276"
---
# <a name="variable"></a><span data-ttu-id="e5eb2-101">\<Zmienna ></span><span class="sxs-lookup"><span data-stu-id="e5eb2-101">\<variable></span></span>
<span data-ttu-id="e5eb2-102">Reprezentuje kolekcję zmiennych skojarzoną z tym zapytaniem działania.</span><span class="sxs-lookup"><span data-stu-id="e5eb2-102">Represents a collection of variables associated with this activity query.</span></span>  
  
 <span data-ttu-id="e5eb2-103">Aby uzyskać więcej informacji na temat śledzenia kwerend profilu, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="e5eb2-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="e5eb2-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="e5eb2-104">\<system.serviceModel></span></span>  
<span data-ttu-id="e5eb2-105">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="e5eb2-105">\<tracking></span></span>  
<span data-ttu-id="e5eb2-106">\<> profilów</span><span class="sxs-lookup"><span data-stu-id="e5eb2-106">\<profiles></span></span>  
<span data-ttu-id="e5eb2-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="e5eb2-107">\<trackingProfile></span></span>  
<span data-ttu-id="e5eb2-108">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="e5eb2-108">\<workflow></span></span>  
<span data-ttu-id="e5eb2-109">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="e5eb2-109">\<activityStateQueries></span></span>  
<span data-ttu-id="e5eb2-110">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="e5eb2-110">\<activityStateQuery></span></span>  
<span data-ttu-id="e5eb2-111">\<Zmienne ></span><span class="sxs-lookup"><span data-stu-id="e5eb2-111">\<variables></span></span>  
<span data-ttu-id="e5eb2-112">\<Zmienna ></span><span class="sxs-lookup"><span data-stu-id="e5eb2-112">\<variable></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5eb2-113">Składnia</span><span class="sxs-lookup"><span data-stu-id="e5eb2-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e5eb2-114">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e5eb2-114">Attributes and Elements</span></span>  
 <span data-ttu-id="e5eb2-115">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e5eb2-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e5eb2-116">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e5eb2-116">Attributes</span></span>  
  
|<span data-ttu-id="e5eb2-117">Atrybut</span><span class="sxs-lookup"><span data-stu-id="e5eb2-117">Attribute</span></span>|<span data-ttu-id="e5eb2-118">Opis</span><span class="sxs-lookup"><span data-stu-id="e5eb2-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e5eb2-119">nazwa</span><span class="sxs-lookup"><span data-stu-id="e5eb2-119">name</span></span>|<span data-ttu-id="e5eb2-120">Ciąg określający nazwę zmiennej.</span><span class="sxs-lookup"><span data-stu-id="e5eb2-120">A string that specifies the name of the variable.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e5eb2-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e5eb2-121">Child Elements</span></span>  
 <span data-ttu-id="e5eb2-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="e5eb2-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e5eb2-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e5eb2-123">Parent Elements</span></span>  
  
|<span data-ttu-id="e5eb2-124">Element</span><span class="sxs-lookup"><span data-stu-id="e5eb2-124">Element</span></span>|<span data-ttu-id="e5eb2-125">Opis</span><span class="sxs-lookup"><span data-stu-id="e5eb2-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e5eb2-126">\<Zmienna ></span><span class="sxs-lookup"><span data-stu-id="e5eb2-126">\<variable></span></span>](variable.md)|<span data-ttu-id="e5eb2-127">Zmienna skojarzonych z kwerendą stanu działania.</span><span class="sxs-lookup"><span data-stu-id="e5eb2-127">A variable associated with an activity state query.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e5eb2-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e5eb2-128">Remarks</span></span>  
 <span data-ttu-id="e5eb2-129">Jedno rozwiązanie ActivityStateQuery jest możliwość wyodrębniania danych podczas śledzenia wykonywania przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="e5eb2-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="e5eb2-130">Umożliwia to dodatkowy kontekst podczas uzyskiwania dostępu do śledzenia rekordów post wykonywania.</span><span class="sxs-lookup"><span data-stu-id="e5eb2-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="e5eb2-131">Można użyć [ \<argumentów >](arguments.md), [ \<Stany >](states.md) i [ \<Stany >](states.md) elementy, aby wyodrębnić dowolną zmienną lub argument z dowolnego działania w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="e5eb2-131">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="e5eb2-132">W poniższym przykładzie przedstawiono zapytanie o stan działania, które wyodrębnia zmienne i argumenty podczas emitowania `Closed` rekordu śledzenia działania.</span><span class="sxs-lookup"><span data-stu-id="e5eb2-132">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="e5eb2-133">Zmienne i argumenty mogą być wyodrębniane tylko za pomocą ActivityStateRecord i w ten sposób są subskrybowane w ramach profilu śledzenia przy użyciu [ \<ActivityStateQuery >](activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="e5eb2-133">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e5eb2-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e5eb2-134">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.VariableElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="e5eb2-135">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="e5eb2-135">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="e5eb2-136">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="e5eb2-136">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
