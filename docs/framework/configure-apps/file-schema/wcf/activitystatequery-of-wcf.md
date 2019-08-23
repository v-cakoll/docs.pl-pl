---
title: <activityStateQuery>programu WCF
ms.date: 03/30/2017
ms.assetid: d6cdc04b-6f3a-4097-a623-ee4a1be3b5c4
ms.openlocfilehash: ce7505896b9c5bb605bb0f67d735cb324f4fd493
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926895"
---
# <a name="activitystatequery-of-wcf"></a><span data-ttu-id="897f5-102">\<activityStateQuery > WCF</span><span class="sxs-lookup"><span data-stu-id="897f5-102">\<activityStateQuery> of WCF</span></span>

<span data-ttu-id="897f5-103">Reprezentuje zapytanie, które jest używane do śledzenia zmian cyklem życia działań, które tworzą wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="897f5-103">Represents a query that is used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="897f5-104">Na przykład możesz chcieć śledzić każde działanie "Wyślij wiadomość E-Mail" w ramach wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="897f5-104">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="897f5-105">To zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania obiektów rekordu stanu działania.</span><span class="sxs-lookup"><span data-stu-id="897f5-105">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="897f5-106">Stany do subskrybowania są wyszczególnione w ActivityStates.</span><span class="sxs-lookup"><span data-stu-id="897f5-106">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
<span data-ttu-id="897f5-107">Aby uzyskać więcej informacji na temat śledzenia kwerend profilu, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="897f5-107">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>

<span data-ttu-id="897f5-108">\<system.serviceModel> \<tracking></span><span class="sxs-lookup"><span data-stu-id="897f5-108">\<system.serviceModel> \<tracking></span></span>  
<span data-ttu-id="897f5-109">\<profiles> \<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="897f5-109">\<profiles> \<trackingProfile></span></span>  
<span data-ttu-id="897f5-110">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="897f5-110">\<workflow></span></span>  
<span data-ttu-id="897f5-111">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="897f5-111">\<activityStateQueries></span></span>  
<span data-ttu-id="897f5-112">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="897f5-112">\<activityStateQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="897f5-113">Składnia</span><span class="sxs-lookup"><span data-stu-id="897f5-113">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <activityStateQueries>
          <activityStateQuery activityName="String">
            <arguments>
              <argument name="String" />
            </arguments>
            <states>
              <state name="String" />
            </states>
            <variables>
              <variable name="String" />
            </variables>
          </activityStateQuery>
        </activityStateQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="897f5-114">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="897f5-114">Attributes and elements</span></span>  

<span data-ttu-id="897f5-115">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="897f5-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="897f5-116">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="897f5-116">Attributes</span></span>  
  
|<span data-ttu-id="897f5-117">Atrybut</span><span class="sxs-lookup"><span data-stu-id="897f5-117">Attribute</span></span>|<span data-ttu-id="897f5-118">Opis</span><span class="sxs-lookup"><span data-stu-id="897f5-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="897f5-119">activityName</span><span class="sxs-lookup"><span data-stu-id="897f5-119">activityName</span></span>|<span data-ttu-id="897f5-120">Ciąg określający nazwę czynności, aby filtrować <xref:System.Activities.Tracking.ActivityStateRecord> wystąpień.</span><span class="sxs-lookup"><span data-stu-id="897f5-120">A string that specifies the name of the activity to filter <xref:System.Activities.Tracking.ActivityStateRecord> instances on.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="897f5-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="897f5-121">Child elements</span></span>  
  
|<span data-ttu-id="897f5-122">Element</span><span class="sxs-lookup"><span data-stu-id="897f5-122">Element</span></span>|<span data-ttu-id="897f5-123">Opis</span><span class="sxs-lookup"><span data-stu-id="897f5-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="897f5-124">\<argumenty ></span><span class="sxs-lookup"><span data-stu-id="897f5-124">\<arguments></span></span>](../windows-workflow-foundation/arguments.md)|<span data-ttu-id="897f5-125">Kolekcja argumenty skojarzone z tej kwerendy działania.</span><span class="sxs-lookup"><span data-stu-id="897f5-125">A collection of arguments associated with this activity query.</span></span>|  
|[<span data-ttu-id="897f5-126">\<Stany ></span><span class="sxs-lookup"><span data-stu-id="897f5-126">\<states></span></span>](../windows-workflow-foundation/states.md)|<span data-ttu-id="897f5-127">Kolekcja elementów konfiguracji, które zawierają stany subskrybowanego działania, dla którego należy obliczanie rekord śledzenia.</span><span class="sxs-lookup"><span data-stu-id="897f5-127">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
|[<span data-ttu-id="897f5-128">\<Stany ></span><span class="sxs-lookup"><span data-stu-id="897f5-128">\<states></span></span>](../windows-workflow-foundation/states.md)|<span data-ttu-id="897f5-129">Kolekcja zmiennych skojarzoną z tym zapytaniem działania.</span><span class="sxs-lookup"><span data-stu-id="897f5-129">A collection of variables associated with this activity query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="897f5-130">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="897f5-130">Parent elements</span></span>  
  
|<span data-ttu-id="897f5-131">Element</span><span class="sxs-lookup"><span data-stu-id="897f5-131">Element</span></span>|<span data-ttu-id="897f5-132">Opis</span><span class="sxs-lookup"><span data-stu-id="897f5-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="897f5-133">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="897f5-133">\<faultPropagationQuery></span></span>](../windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="897f5-134">Reprezentuje listę elementów konfiguracji, które są używane do śledzenia żądań, aby anulować działanie podrzędne przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="897f5-134">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="897f5-135">Zapytanie jest niezbędne do uczestnika śledzenia do subskrybowania Anuluj żądanie rekordu obiektów.</span><span class="sxs-lookup"><span data-stu-id="897f5-135">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="897f5-136">Uwagi</span><span class="sxs-lookup"><span data-stu-id="897f5-136">Remarks</span></span>

<span data-ttu-id="897f5-137">Jedno rozwiązanie ActivityStateQuery jest możliwość wyodrębniania danych podczas śledzenia wykonywania przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="897f5-137">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="897f5-138">Umożliwia to dodatkowy kontekst podczas uzyskiwania dostępu do śledzenia rekordów post wykonywania.</span><span class="sxs-lookup"><span data-stu-id="897f5-138">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="897f5-139">Można użyć [ \<argumentów >](../windows-workflow-foundation/arguments.md), [ \<Stany >](../windows-workflow-foundation/states.md) i [ \<Stany >](../windows-workflow-foundation/states.md) elementy, aby wyodrębnić dowolną zmienną lub argument z dowolnego działania w przepływie pracy. W poniższym przykładzie przedstawiono zapytanie o stan działania, które wyodrębnia zmienne i argumenty podczas emitowania `Closed` rekordu śledzenia działania.</span><span class="sxs-lookup"><span data-stu-id="897f5-139">You can use the [\<arguments>](../windows-workflow-foundation/arguments.md), [\<states>](../windows-workflow-foundation/states.md) and [\<states>](../windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="897f5-140">Zmienne i argumenty mogą być wyodrębniane tylko za pomocą ActivityStateRecord i w ten sposób są subskrybowane w ramach profilu śledzenia przy użyciu [ \<ActivityStateQuery >](../windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="897f5-140">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../windows-workflow-foundation/activitystatequery.md).</span></span>  
  
```xml  
<activityStateQuery activityName="SendEmailActivity">
  <states>
    <state name="Closed" />
  </states>
  <variables>
    <variable name="FromAddress" />
  </variables>
  <arguments>
    <argument name="Result" />
  </arguments>
</activityStateQuery>
```  
  
## <a name="see-also"></a><span data-ttu-id="897f5-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="897f5-141">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElement>
- <xref:System.Activities.Tracking.ActivityStateQuery>
- [<span data-ttu-id="897f5-142">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="897f5-142">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="897f5-143">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="897f5-143">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
