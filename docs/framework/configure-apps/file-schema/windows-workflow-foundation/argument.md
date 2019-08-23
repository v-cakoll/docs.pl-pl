---
title: <argument>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a7144d53-8023-4e90-971f-895e016fd58a
ms.openlocfilehash: f2aeb61e2e72f5bd6a696c031279f2c57907166b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946142"
---
# <a name="argument"></a><span data-ttu-id="b3520-101">\<> argumentu</span><span class="sxs-lookup"><span data-stu-id="b3520-101">\<argument></span></span>
<span data-ttu-id="b3520-102">Element konfiguracji, który reprezentuje argumentu skojarzonych z kwerendą stanu działania.</span><span class="sxs-lookup"><span data-stu-id="b3520-102">A configuration element that represents an argument associated with an activity state query.</span></span>  
  
 <span data-ttu-id="b3520-103">Aby uzyskać więcej informacji na temat śledzenia kwerend profilu, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="b3520-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="b3520-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="b3520-104">\<system.serviceModel></span></span>  
<span data-ttu-id="b3520-105">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="b3520-105">\<tracking></span></span>  
<span data-ttu-id="b3520-106">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="b3520-106">\<trackingProfile></span></span>  
<span data-ttu-id="b3520-107">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="b3520-107">\<workflow></span></span>  
<span data-ttu-id="b3520-108">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="b3520-108">\<activityStateQueries></span></span>  
<span data-ttu-id="b3520-109">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="b3520-109">\<activityStateQuery></span></span>  
<span data-ttu-id="b3520-110">\<argumenty ></span><span class="sxs-lookup"><span data-stu-id="b3520-110">\<arguments></span></span>  
<span data-ttu-id="b3520-111">\<> argumentu</span><span class="sxs-lookup"><span data-stu-id="b3520-111">\<argument></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3520-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="b3520-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b3520-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b3520-113">Attributes and Elements</span></span>  
 <span data-ttu-id="b3520-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b3520-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b3520-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b3520-115">Attributes</span></span>  
  
|<span data-ttu-id="b3520-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="b3520-116">Attribute</span></span>|<span data-ttu-id="b3520-117">Opis</span><span class="sxs-lookup"><span data-stu-id="b3520-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b3520-118">nazwa</span><span class="sxs-lookup"><span data-stu-id="b3520-118">name</span></span>|<span data-ttu-id="b3520-119">Ciąg określający nazwę argumentu.</span><span class="sxs-lookup"><span data-stu-id="b3520-119">A string that specifies the name of the argument.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b3520-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b3520-120">Child Elements</span></span>  
 <span data-ttu-id="b3520-121">Brak.</span><span class="sxs-lookup"><span data-stu-id="b3520-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b3520-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b3520-122">Parent Elements</span></span>  
  
|<span data-ttu-id="b3520-123">Element</span><span class="sxs-lookup"><span data-stu-id="b3520-123">Element</span></span>|<span data-ttu-id="b3520-124">Opis</span><span class="sxs-lookup"><span data-stu-id="b3520-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b3520-125">\<argumenty ></span><span class="sxs-lookup"><span data-stu-id="b3520-125">\<arguments></span></span>](arguments.md)|<span data-ttu-id="b3520-126">Kolekcja argumenty skojarzone z tej kwerendy działania.</span><span class="sxs-lookup"><span data-stu-id="b3520-126">A collection of arguments associated with this activity query.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b3520-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b3520-127">Remarks</span></span>  
 <span data-ttu-id="b3520-128">Jedno rozwiązanie ActivityStateQuery jest możliwość wyodrębniania danych podczas śledzenia wykonywania przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="b3520-128">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="b3520-129">Umożliwia to dodatkowy kontekst podczas uzyskiwania dostępu do śledzenia rekordów post wykonywania.</span><span class="sxs-lookup"><span data-stu-id="b3520-129">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="b3520-130">Można użyć [ \<argumentów >](arguments.md), [ \<Stany >](states.md) i [ \<Stany >](states.md) elementy, aby wyodrębnić dowolną zmienną lub argument z dowolnego działania w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="b3520-130">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="b3520-131">W poniższym przykładzie przedstawiono zapytanie o stan działania, które wyodrębnia zmienne i argumenty podczas emitowania `Closed` rekordu śledzenia działania.</span><span class="sxs-lookup"><span data-stu-id="b3520-131">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="b3520-132">Zmienne i argumenty mogą być wyodrębniane tylko za pomocą ActivityStateRecord i w ten sposób są subskrybowane w ramach profilu śledzenia przy użyciu [ \<ActivityStateQuery >](activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="b3520-132">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b3520-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b3520-133">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ArgumentElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="b3520-134">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="b3520-134">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="b3520-135">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="b3520-135">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
