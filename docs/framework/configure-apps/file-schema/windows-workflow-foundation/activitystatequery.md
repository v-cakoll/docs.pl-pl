---
title: '&lt;activityStateQuery&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 9f8c3e4f-e2e3-4402-9760-03bf918ece7b
ms.openlocfilehash: 7b872d933d07af329601063b3d769bc43a22007c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54568676"
---
# <a name="ltactivitystatequerygt"></a><span data-ttu-id="85859-102">&lt;activityStateQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="85859-102">&lt;activityStateQuery&gt;</span></span>
<span data-ttu-id="85859-103">Reprezentuje zapytanie, które jest używane do śledzenia zmian cyklem życia działań, które tworzą wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="85859-103">Represents a query that is used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="85859-104">Na przykład chcesz do śledzenia za każdym razem, gdy kończy działanie "Wyślij wiadomość E-Mail", w ramach wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="85859-104">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="85859-105">To zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania obiektów rekordu stanu działania.</span><span class="sxs-lookup"><span data-stu-id="85859-105">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="85859-106">Stany do subskrybowania są wyszczególnione w ActivityStates.</span><span class="sxs-lookup"><span data-stu-id="85859-106">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
 <span data-ttu-id="85859-107">Aby uzyskać więcej informacji na podstawie śledzenia zapytań profilu zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="85859-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="85859-108">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="85859-108">\<system.serviceModel></span></span>  
<span data-ttu-id="85859-109">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="85859-109">\<tracking></span></span>  
<span data-ttu-id="85859-110">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="85859-110">\<trackingProfile></span></span>  
<span data-ttu-id="85859-111">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="85859-111">\<workflow></span></span>  
<span data-ttu-id="85859-112">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="85859-112">\<activityStateQueries></span></span>  
<span data-ttu-id="85859-113">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="85859-113">\<activityStateQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85859-114">Składnia</span><span class="sxs-lookup"><span data-stu-id="85859-114">Syntax</span></span>  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <arguments>
          <argument name="String"/>
        </arguments>
        <states>
          <state name="String"/>
        </states>
        <variables>
          <variable name="String"/>
        </variables>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="85859-115">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="85859-115">Attributes and Elements</span></span>  
 <span data-ttu-id="85859-116">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="85859-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="85859-117">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="85859-117">Attributes</span></span>  
  
|<span data-ttu-id="85859-118">Atrybut</span><span class="sxs-lookup"><span data-stu-id="85859-118">Attribute</span></span>|<span data-ttu-id="85859-119">Opis</span><span class="sxs-lookup"><span data-stu-id="85859-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="85859-120">activityName</span><span class="sxs-lookup"><span data-stu-id="85859-120">activityName</span></span>|<span data-ttu-id="85859-121">Ciąg określający nazwę czynności, aby filtrować <xref:System.Activities.Tracking.ActivityStateRecord> wystąpień.</span><span class="sxs-lookup"><span data-stu-id="85859-121">A string that specifies the name of the activity to filter <xref:System.Activities.Tracking.ActivityStateRecord> instances on.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="85859-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="85859-122">Child Elements</span></span>  
  
|<span data-ttu-id="85859-123">Element</span><span class="sxs-lookup"><span data-stu-id="85859-123">Element</span></span>|<span data-ttu-id="85859-124">Opis</span><span class="sxs-lookup"><span data-stu-id="85859-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="85859-125">\<arguments></span><span class="sxs-lookup"><span data-stu-id="85859-125">\<arguments></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md)|<span data-ttu-id="85859-126">Kolekcja argumenty skojarzone z tej kwerendy działania.</span><span class="sxs-lookup"><span data-stu-id="85859-126">A collection of arguments associated with this activity query.</span></span>|  
|[<span data-ttu-id="85859-127">\<Stany ></span><span class="sxs-lookup"><span data-stu-id="85859-127">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="85859-128">Kolekcja elementów konfiguracji, które zawierają stany subskrybowanego działania, dla którego należy obliczanie rekord śledzenia.</span><span class="sxs-lookup"><span data-stu-id="85859-128">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
|[<span data-ttu-id="85859-129">\<Stany ></span><span class="sxs-lookup"><span data-stu-id="85859-129">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="85859-130">Kolekcja zmiennych skojarzoną z tym zapytaniem działania.</span><span class="sxs-lookup"><span data-stu-id="85859-130">A collection of variables associated with this activity query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="85859-131">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="85859-131">Parent Elements</span></span>  
  
|<span data-ttu-id="85859-132">Element</span><span class="sxs-lookup"><span data-stu-id="85859-132">Element</span></span>|<span data-ttu-id="85859-133">Opis</span><span class="sxs-lookup"><span data-stu-id="85859-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="85859-134">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="85859-134">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="85859-135">Reprezentuje listę elementów konfiguracji, które są używane do śledzenia żądań, aby anulować działanie podrzędne przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="85859-135">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="85859-136">Zapytanie jest niezbędne do uczestnika śledzenia do subskrybowania Anuluj żądanie rekordu obiektów.</span><span class="sxs-lookup"><span data-stu-id="85859-136">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="85859-137">Uwagi</span><span class="sxs-lookup"><span data-stu-id="85859-137">Remarks</span></span>  
 <span data-ttu-id="85859-138">Jedno rozwiązanie ActivityStateQuery jest możliwość wyodrębniania danych podczas śledzenia wykonywania przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="85859-138">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="85859-139">Umożliwia to dodatkowy kontekst podczas uzyskiwania dostępu do śledzenia rekordów post wykonywania.</span><span class="sxs-lookup"><span data-stu-id="85859-139">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="85859-140">Możesz użyć [ \<argumenty >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<stany >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) i [ \<stany >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elementy, aby wyodrębnić dowolnej zmiennej lub argumentu wszelkie działania w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="85859-140">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="85859-141">W poniższym przykładzie pokazano kwerendą stanu działania, który wyodrębnia zmienne i argumenty podczas działania `Closed` rekord śledzenia jest emitowane.</span><span class="sxs-lookup"><span data-stu-id="85859-141">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="85859-142">Zmienne i argumenty wyodrębniania tylko z ActivityStateRecord i w związku z tym subskrybują w ramach śledzenia profilu przy użyciu [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="85859-142">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="85859-143">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="85859-143">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="85859-144">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="85859-144">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="85859-145">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="85859-145">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
