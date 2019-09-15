---
title: <activityStateQuery>programu WCF
ms.date: 03/30/2017
ms.assetid: d6cdc04b-6f3a-4097-a623-ee4a1be3b5c4
ms.openlocfilehash: 49c507424e813067e1dad9b08167d9661acef36f
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991218"
---
# <a name="activitystatequery-of-wcf"></a><span data-ttu-id="0e719-102">\<activityStateQuery > WCF</span><span class="sxs-lookup"><span data-stu-id="0e719-102">\<activityStateQuery> of WCF</span></span>

<span data-ttu-id="0e719-103">Reprezentuje zapytanie, które jest używane do śledzenia zmian cyklem życia działań, które tworzą wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="0e719-103">Represents a query that is used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="0e719-104">Na przykład możesz chcieć śledzić każde działanie "Wyślij wiadomość E-Mail" w ramach wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="0e719-104">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="0e719-105">To zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania obiektów rekordu stanu działania.</span><span class="sxs-lookup"><span data-stu-id="0e719-105">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="0e719-106">Stany do subskrybowania są wyszczególnione w ActivityStates.</span><span class="sxs-lookup"><span data-stu-id="0e719-106">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
<span data-ttu-id="0e719-107">Aby uzyskać więcej informacji na temat śledzenia kwerend profilu, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="0e719-107">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>

<span data-ttu-id="0e719-108">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="0e719-108">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="0e719-109">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="0e719-109">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="0e719-110">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Śledzenie >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="0e719-110">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="0e719-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> profilów**</span><span class="sxs-lookup"><span data-stu-id="0e719-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="0e719-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="0e719-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="0e719-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<przepływ pracy >** ](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="0e719-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="0e719-114">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<activityStateQueries >** ](activitystatequeries-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="0e719-114">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQueries>**](activitystatequeries-of-wcf.md)</span></span>\
<span data-ttu-id="0e719-115">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<activityStateQuery >**</span><span class="sxs-lookup"><span data-stu-id="0e719-115">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityStateQuery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e719-116">Składnia</span><span class="sxs-lookup"><span data-stu-id="0e719-116">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0e719-117">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="0e719-117">Attributes and elements</span></span>  

<span data-ttu-id="0e719-118">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="0e719-118">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0e719-119">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="0e719-119">Attributes</span></span>  
  
|<span data-ttu-id="0e719-120">Atrybut</span><span class="sxs-lookup"><span data-stu-id="0e719-120">Attribute</span></span>|<span data-ttu-id="0e719-121">Opis</span><span class="sxs-lookup"><span data-stu-id="0e719-121">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0e719-122">activityName</span><span class="sxs-lookup"><span data-stu-id="0e719-122">activityName</span></span>|<span data-ttu-id="0e719-123">Ciąg określający nazwę czynności, aby filtrować <xref:System.Activities.Tracking.ActivityStateRecord> wystąpień.</span><span class="sxs-lookup"><span data-stu-id="0e719-123">A string that specifies the name of the activity to filter <xref:System.Activities.Tracking.ActivityStateRecord> instances on.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0e719-124">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="0e719-124">Child elements</span></span>  
  
|<span data-ttu-id="0e719-125">Element</span><span class="sxs-lookup"><span data-stu-id="0e719-125">Element</span></span>|<span data-ttu-id="0e719-126">Opis</span><span class="sxs-lookup"><span data-stu-id="0e719-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0e719-127">\<argumenty ></span><span class="sxs-lookup"><span data-stu-id="0e719-127">\<arguments></span></span>](../windows-workflow-foundation/arguments.md)|<span data-ttu-id="0e719-128">Kolekcja argumenty skojarzone z tej kwerendy działania.</span><span class="sxs-lookup"><span data-stu-id="0e719-128">A collection of arguments associated with this activity query.</span></span>|  
|[<span data-ttu-id="0e719-129">\<Stany ></span><span class="sxs-lookup"><span data-stu-id="0e719-129">\<states></span></span>](../windows-workflow-foundation/states.md)|<span data-ttu-id="0e719-130">Kolekcja elementów konfiguracji, które zawierają stany subskrybowanego działania, dla którego należy obliczanie rekord śledzenia.</span><span class="sxs-lookup"><span data-stu-id="0e719-130">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
|[<span data-ttu-id="0e719-131">\<Stany ></span><span class="sxs-lookup"><span data-stu-id="0e719-131">\<states></span></span>](../windows-workflow-foundation/states.md)|<span data-ttu-id="0e719-132">Kolekcja zmiennych skojarzoną z tym zapytaniem działania.</span><span class="sxs-lookup"><span data-stu-id="0e719-132">A collection of variables associated with this activity query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0e719-133">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="0e719-133">Parent elements</span></span>  
  
|<span data-ttu-id="0e719-134">Element</span><span class="sxs-lookup"><span data-stu-id="0e719-134">Element</span></span>|<span data-ttu-id="0e719-135">Opis</span><span class="sxs-lookup"><span data-stu-id="0e719-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0e719-136">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="0e719-136">\<faultPropagationQuery></span></span>](../windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="0e719-137">Reprezentuje listę elementów konfiguracji, które są używane do śledzenia żądań, aby anulować działanie podrzędne przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="0e719-137">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="0e719-138">Zapytanie jest niezbędne do uczestnika śledzenia do subskrybowania Anuluj żądanie rekordu obiektów.</span><span class="sxs-lookup"><span data-stu-id="0e719-138">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0e719-139">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0e719-139">Remarks</span></span>

<span data-ttu-id="0e719-140">Jedno rozwiązanie ActivityStateQuery jest możliwość wyodrębniania danych podczas śledzenia wykonywania przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="0e719-140">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="0e719-141">Umożliwia to dodatkowy kontekst podczas uzyskiwania dostępu do śledzenia rekordów post wykonywania.</span><span class="sxs-lookup"><span data-stu-id="0e719-141">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="0e719-142">Można użyć [ \<argumentów >](../windows-workflow-foundation/arguments.md), [ \<Stany >](../windows-workflow-foundation/states.md) i [ \<Stany >](../windows-workflow-foundation/states.md) elementy, aby wyodrębnić dowolną zmienną lub argument z dowolnego działania w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="0e719-142">You can use the [\<arguments>](../windows-workflow-foundation/arguments.md), [\<states>](../windows-workflow-foundation/states.md) and [\<states>](../windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="0e719-143">W poniższym przykładzie przedstawiono zapytanie o stan działania, które wyodrębnia zmienne i argumenty podczas emitowania `Closed` rekordu śledzenia działania.</span><span class="sxs-lookup"><span data-stu-id="0e719-143">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="0e719-144">Zmienne i argumenty mogą być wyodrębniane tylko za pomocą ActivityStateRecord i w ten sposób są subskrybowane w ramach profilu śledzenia przy użyciu [ \<ActivityStateQuery >](../windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="0e719-144">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0e719-145">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0e719-145">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElement>
- <xref:System.Activities.Tracking.ActivityStateQuery>
- [<span data-ttu-id="0e719-146">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="0e719-146">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="0e719-147">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="0e719-147">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
