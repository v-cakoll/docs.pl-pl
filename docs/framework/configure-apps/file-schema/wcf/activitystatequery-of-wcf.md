---
title: <activityStateQuery> w WCF
ms.date: 03/30/2017
ms.assetid: d6cdc04b-6f3a-4097-a623-ee4a1be3b5c4
ms.openlocfilehash: 97fce512415ad6ae165b29c7e8eff3394d5e675a
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55254798"
---
# <a name="activitystatequery-of-wcf"></a><span data-ttu-id="fbf81-102">\<activityStateQuery > w WCF</span><span class="sxs-lookup"><span data-stu-id="fbf81-102">\<activityStateQuery> of WCF</span></span>

<span data-ttu-id="fbf81-103">Reprezentuje zapytanie, które jest używane do śledzenia zmian cyklem życia działań, które tworzą wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="fbf81-103">Represents a query that is used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="fbf81-104">Na przykład chcesz do śledzenia za każdym razem, gdy kończy działanie "Wyślij wiadomość E-Mail", w ramach wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="fbf81-104">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="fbf81-105">To zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania obiektów rekordu stanu działania.</span><span class="sxs-lookup"><span data-stu-id="fbf81-105">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="fbf81-106">Stany do subskrybowania są wyszczególnione w ActivityStates.</span><span class="sxs-lookup"><span data-stu-id="fbf81-106">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
<span data-ttu-id="fbf81-107">Aby uzyskać więcej informacji na podstawie śledzenia zapytań profilu zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="fbf81-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>

<span data-ttu-id="fbf81-108">\<system.serviceModel> \<tracking></span><span class="sxs-lookup"><span data-stu-id="fbf81-108">\<system.serviceModel> \<tracking></span></span>  
<span data-ttu-id="fbf81-109">\<profiles> \<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="fbf81-109">\<profiles> \<trackingProfile></span></span>  
<span data-ttu-id="fbf81-110">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="fbf81-110">\<workflow></span></span>  
<span data-ttu-id="fbf81-111">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="fbf81-111">\<activityStateQueries></span></span>  
<span data-ttu-id="fbf81-112">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="fbf81-112">\<activityStateQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbf81-113">Składnia</span><span class="sxs-lookup"><span data-stu-id="fbf81-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fbf81-114">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="fbf81-114">Attributes and elements</span></span>  

<span data-ttu-id="fbf81-115">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="fbf81-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fbf81-116">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="fbf81-116">Attributes</span></span>  
  
|<span data-ttu-id="fbf81-117">Atrybut</span><span class="sxs-lookup"><span data-stu-id="fbf81-117">Attribute</span></span>|<span data-ttu-id="fbf81-118">Opis</span><span class="sxs-lookup"><span data-stu-id="fbf81-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fbf81-119">activityName</span><span class="sxs-lookup"><span data-stu-id="fbf81-119">activityName</span></span>|<span data-ttu-id="fbf81-120">Ciąg określający nazwę czynności, aby filtrować <xref:System.Activities.Tracking.ActivityStateRecord> wystąpień.</span><span class="sxs-lookup"><span data-stu-id="fbf81-120">A string that specifies the name of the activity to filter <xref:System.Activities.Tracking.ActivityStateRecord> instances on.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fbf81-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="fbf81-121">Child elements</span></span>  
  
|<span data-ttu-id="fbf81-122">Element</span><span class="sxs-lookup"><span data-stu-id="fbf81-122">Element</span></span>|<span data-ttu-id="fbf81-123">Opis</span><span class="sxs-lookup"><span data-stu-id="fbf81-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fbf81-124">\<arguments></span><span class="sxs-lookup"><span data-stu-id="fbf81-124">\<arguments></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md)|<span data-ttu-id="fbf81-125">Kolekcja argumenty skojarzone z tej kwerendy działania.</span><span class="sxs-lookup"><span data-stu-id="fbf81-125">A collection of arguments associated with this activity query.</span></span>|  
|[<span data-ttu-id="fbf81-126">\<Stany ></span><span class="sxs-lookup"><span data-stu-id="fbf81-126">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="fbf81-127">Kolekcja elementów konfiguracji, które zawierają stany subskrybowanego działania, dla którego należy obliczanie rekord śledzenia.</span><span class="sxs-lookup"><span data-stu-id="fbf81-127">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
|[<span data-ttu-id="fbf81-128">\<Stany ></span><span class="sxs-lookup"><span data-stu-id="fbf81-128">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="fbf81-129">Kolekcja zmiennych skojarzoną z tym zapytaniem działania.</span><span class="sxs-lookup"><span data-stu-id="fbf81-129">A collection of variables associated with this activity query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fbf81-130">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="fbf81-130">Parent elements</span></span>  
  
|<span data-ttu-id="fbf81-131">Element</span><span class="sxs-lookup"><span data-stu-id="fbf81-131">Element</span></span>|<span data-ttu-id="fbf81-132">Opis</span><span class="sxs-lookup"><span data-stu-id="fbf81-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fbf81-133">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="fbf81-133">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="fbf81-134">Reprezentuje listę elementów konfiguracji, które są używane do śledzenia żądań, aby anulować działanie podrzędne przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="fbf81-134">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="fbf81-135">Zapytanie jest niezbędne do uczestnika śledzenia do subskrybowania Anuluj żądanie rekordu obiektów.</span><span class="sxs-lookup"><span data-stu-id="fbf81-135">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fbf81-136">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fbf81-136">Remarks</span></span>

<span data-ttu-id="fbf81-137">Jedno rozwiązanie ActivityStateQuery jest możliwość wyodrębniania danych podczas śledzenia wykonywania przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="fbf81-137">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="fbf81-138">Umożliwia to dodatkowy kontekst podczas uzyskiwania dostępu do śledzenia rekordów post wykonywania.</span><span class="sxs-lookup"><span data-stu-id="fbf81-138">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="fbf81-139">Możesz użyć [ \<argumenty >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<stany >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) i [ \<stany >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elementy, aby wyodrębnić dowolnej zmiennej lub argumentu wszelkie działania w przepływie pracy. W poniższym przykładzie pokazano kwerendą stanu działania, który wyodrębnia zmienne i argumenty podczas działania `Closed` rekord śledzenia jest emitowane.</span><span class="sxs-lookup"><span data-stu-id="fbf81-139">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="fbf81-140">Zmienne i argumenty wyodrębniania tylko z ActivityStateRecord i w związku z tym subskrybują w ramach śledzenia profilu przy użyciu [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="fbf81-140">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fbf81-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fbf81-141">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElement>
- <xref:System.Activities.Tracking.ActivityStateQuery>
- [<span data-ttu-id="fbf81-142">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="fbf81-142">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="fbf81-143">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="fbf81-143">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
