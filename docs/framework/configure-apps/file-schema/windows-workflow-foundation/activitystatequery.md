---
title: '&lt;activityStateQuery&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 9f8c3e4f-e2e3-4402-9760-03bf918ece7b
ms.openlocfilehash: 3c6243e6b8e1d2b32dc830609a5d4df474f48e61
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53151177"
---
# <a name="ltactivitystatequerygt"></a><span data-ttu-id="12bf1-102">&lt;activityStateQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="12bf1-102">&lt;activityStateQuery&gt;</span></span>
<span data-ttu-id="12bf1-103">Reprezentuje zapytanie, które jest używane do śledzenia zmian cyklem życia działań, które tworzą wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="12bf1-103">Represents a query that is used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="12bf1-104">Na przykład chcesz do śledzenia za każdym razem, gdy kończy działanie "Wyślij wiadomość E-Mail", w ramach wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="12bf1-104">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="12bf1-105">To zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania obiektów rekordu stanu działania.</span><span class="sxs-lookup"><span data-stu-id="12bf1-105">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="12bf1-106">Stany do subskrybowania są wyszczególnione w ActivityStates.</span><span class="sxs-lookup"><span data-stu-id="12bf1-106">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
 <span data-ttu-id="12bf1-107">Aby uzyskać więcej informacji na podstawie śledzenia zapytań profilu zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="12bf1-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="12bf1-108">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="12bf1-108">\<system.serviceModel></span></span>  
<span data-ttu-id="12bf1-109">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="12bf1-109">\<tracking></span></span>  
<span data-ttu-id="12bf1-110">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="12bf1-110">\<trackingProfile></span></span>  
<span data-ttu-id="12bf1-111">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="12bf1-111">\<workflow></span></span>  
<span data-ttu-id="12bf1-112">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="12bf1-112">\<activityStateQueries></span></span>  
<span data-ttu-id="12bf1-113">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="12bf1-113">\<activityStateQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12bf1-114">Składnia</span><span class="sxs-lookup"><span data-stu-id="12bf1-114">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="12bf1-115">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="12bf1-115">Attributes and Elements</span></span>  
 <span data-ttu-id="12bf1-116">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="12bf1-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="12bf1-117">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="12bf1-117">Attributes</span></span>  
  
|<span data-ttu-id="12bf1-118">Atrybut</span><span class="sxs-lookup"><span data-stu-id="12bf1-118">Attribute</span></span>|<span data-ttu-id="12bf1-119">Opis</span><span class="sxs-lookup"><span data-stu-id="12bf1-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="12bf1-120">activityName</span><span class="sxs-lookup"><span data-stu-id="12bf1-120">activityName</span></span>|<span data-ttu-id="12bf1-121">Ciąg określający nazwę czynności, aby filtrować <xref:System.Activities.Tracking.ActivityStateRecord> wystąpień.</span><span class="sxs-lookup"><span data-stu-id="12bf1-121">A string that specifies the name of the activity to filter <xref:System.Activities.Tracking.ActivityStateRecord> instances on.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="12bf1-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="12bf1-122">Child Elements</span></span>  
  
|<span data-ttu-id="12bf1-123">Element</span><span class="sxs-lookup"><span data-stu-id="12bf1-123">Element</span></span>|<span data-ttu-id="12bf1-124">Opis</span><span class="sxs-lookup"><span data-stu-id="12bf1-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="12bf1-125">\<argumenty ></span><span class="sxs-lookup"><span data-stu-id="12bf1-125">\<arguments></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md)|<span data-ttu-id="12bf1-126">Kolekcja argumenty skojarzone z tej kwerendy działania.</span><span class="sxs-lookup"><span data-stu-id="12bf1-126">A collection of arguments associated with this activity query.</span></span>|  
|[<span data-ttu-id="12bf1-127">\<Stany ></span><span class="sxs-lookup"><span data-stu-id="12bf1-127">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="12bf1-128">Kolekcja elementów konfiguracji, które zawierają stany subskrybowanego działania, dla którego należy obliczanie rekord śledzenia.</span><span class="sxs-lookup"><span data-stu-id="12bf1-128">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
|[<span data-ttu-id="12bf1-129">\<Stany ></span><span class="sxs-lookup"><span data-stu-id="12bf1-129">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="12bf1-130">Kolekcja zmiennych skojarzoną z tym zapytaniem działania.</span><span class="sxs-lookup"><span data-stu-id="12bf1-130">A collection of variables associated with this activity query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="12bf1-131">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="12bf1-131">Parent Elements</span></span>  
  
|<span data-ttu-id="12bf1-132">Element</span><span class="sxs-lookup"><span data-stu-id="12bf1-132">Element</span></span>|<span data-ttu-id="12bf1-133">Opis</span><span class="sxs-lookup"><span data-stu-id="12bf1-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="12bf1-134">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="12bf1-134">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="12bf1-135">Reprezentuje listę elementów konfiguracji, które są używane do śledzenia żądań, aby anulować działanie podrzędne przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="12bf1-135">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="12bf1-136">Zapytanie jest niezbędne do uczestnika śledzenia do subskrybowania Anuluj żądanie rekordu obiektów.</span><span class="sxs-lookup"><span data-stu-id="12bf1-136">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="12bf1-137">Uwagi</span><span class="sxs-lookup"><span data-stu-id="12bf1-137">Remarks</span></span>  
 <span data-ttu-id="12bf1-138">Jedno rozwiązanie ActivityStateQuery jest możliwość wyodrębniania danych podczas śledzenia wykonywania przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="12bf1-138">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="12bf1-139">Umożliwia to dodatkowy kontekst podczas uzyskiwania dostępu do śledzenia rekordów post wykonywania.</span><span class="sxs-lookup"><span data-stu-id="12bf1-139">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="12bf1-140">Możesz użyć [ \<argumenty >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<stany >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) i [ \<stany >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elementy, aby wyodrębnić dowolnej zmiennej lub argumentu wszelkie działania w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="12bf1-140">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="12bf1-141">W poniższym przykładzie pokazano kwerendą stanu działania, który wyodrębnia zmienne i argumenty podczas działania `Closed` rekord śledzenia jest emitowane.</span><span class="sxs-lookup"><span data-stu-id="12bf1-141">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="12bf1-142">Zmienne i argumenty wyodrębniania tylko z ActivityStateRecord i w związku z tym subskrybują w ramach śledzenia profilu przy użyciu [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="12bf1-142">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="12bf1-143">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="12bf1-143">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElement?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="12bf1-144">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="12bf1-144">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="12bf1-145">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="12bf1-145">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
