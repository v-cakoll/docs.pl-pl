---
title: <arguments>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 0f327196-f468-4be3-b6c4-68ba981a1bd6
ms.openlocfilehash: 3e9fc4f286e7aba6406ce61910da9e614e13ffca
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55276573"
---
# <a name="arguments"></a><span data-ttu-id="ddd18-101">\<arguments></span><span class="sxs-lookup"><span data-stu-id="ddd18-101">\<arguments></span></span>
<span data-ttu-id="ddd18-102">Reprezentuje kolekcję argumentów skojarzonych z kwerendą stanu działania.</span><span class="sxs-lookup"><span data-stu-id="ddd18-102">Represents a collection of arguments associated with an activity state query.</span></span>  
  
 <span data-ttu-id="ddd18-103">Aby uzyskać więcej informacji na podstawie śledzenia zapytań profilu zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="ddd18-103">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="ddd18-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="ddd18-104">\<system.serviceModel></span></span>  
<span data-ttu-id="ddd18-105">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="ddd18-105">\<tracking></span></span>  
<span data-ttu-id="ddd18-106">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="ddd18-106">\<trackingProfile></span></span>  
<span data-ttu-id="ddd18-107">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="ddd18-107">\<workflow></span></span>  
<span data-ttu-id="ddd18-108">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="ddd18-108">\<activityStateQueries></span></span>  
<span data-ttu-id="ddd18-109">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="ddd18-109">\<activityStateQuery></span></span>  
<span data-ttu-id="ddd18-110">\<arguments></span><span class="sxs-lookup"><span data-stu-id="ddd18-110">\<arguments></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ddd18-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="ddd18-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ddd18-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ddd18-112">Attributes and Elements</span></span>  
 <span data-ttu-id="ddd18-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ddd18-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ddd18-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ddd18-114">Attributes</span></span>  
 <span data-ttu-id="ddd18-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="ddd18-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ddd18-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ddd18-116">Child Elements</span></span>  
  
|<span data-ttu-id="ddd18-117">Element</span><span class="sxs-lookup"><span data-stu-id="ddd18-117">Element</span></span>|<span data-ttu-id="ddd18-118">Opis</span><span class="sxs-lookup"><span data-stu-id="ddd18-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ddd18-119">\<argument ></span><span class="sxs-lookup"><span data-stu-id="ddd18-119">\<argument></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/argument.md)|<span data-ttu-id="ddd18-120">Argument skojarzonych z kwerendą stanu działania.</span><span class="sxs-lookup"><span data-stu-id="ddd18-120">An argument associated with an activity state query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ddd18-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ddd18-121">Parent Elements</span></span>  
  
|<span data-ttu-id="ddd18-122">Element</span><span class="sxs-lookup"><span data-stu-id="ddd18-122">Element</span></span>|<span data-ttu-id="ddd18-123">Opis</span><span class="sxs-lookup"><span data-stu-id="ddd18-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ddd18-124">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="ddd18-124">\<activityStateQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)|<span data-ttu-id="ddd18-125">Reprezentuje element konfiguracji, które jest używane do śledzenia żądań, aby anulować działanie podrzędne przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ddd18-125">Represents a configuration element that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="ddd18-126">Zapytanie jest niezbędne do uczestnika śledzenia do subskrybowania Anuluj żądanie rekordu obiektów.</span><span class="sxs-lookup"><span data-stu-id="ddd18-126">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ddd18-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ddd18-127">Remarks</span></span>  
 <span data-ttu-id="ddd18-128">Jedno rozwiązanie ActivityStateQuery jest możliwość wyodrębniania danych podczas śledzenia wykonywania przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="ddd18-128">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="ddd18-129">Umożliwia to dodatkowy kontekst podczas uzyskiwania dostępu do śledzenia rekordów post wykonywania.</span><span class="sxs-lookup"><span data-stu-id="ddd18-129">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="ddd18-130">Możesz użyć [ \<argumenty >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<stany >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) i [ \<stany >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elementy, aby wyodrębnić dowolnej zmiennej lub argumentu wszelkie działania w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="ddd18-130">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="ddd18-131">W poniższym przykładzie pokazano kwerendą stanu działania, który wyodrębnia zmienne i argumenty podczas działania `Closed` rekord śledzenia jest emitowane.</span><span class="sxs-lookup"><span data-stu-id="ddd18-131">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="ddd18-132">Zmienne i argumenty wyodrębniania tylko z ActivityStateRecord i w związku z tym subskrybują w ramach śledzenia profilu przy użyciu [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="ddd18-132">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ddd18-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ddd18-133">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.ArgumentElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="ddd18-134">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="ddd18-134">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="ddd18-135">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="ddd18-135">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
