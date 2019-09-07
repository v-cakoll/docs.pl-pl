---
title: <activityStateQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 9f8c3e4f-e2e3-4402-9760-03bf918ece7b
ms.openlocfilehash: 5d3c35589330ab5bed5f89c0dafac006b9e3af55
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398936"
---
# <a name="activitystatequery"></a><span data-ttu-id="d4a26-101">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="d4a26-101">\<activityStateQuery></span></span>
<span data-ttu-id="d4a26-102">Reprezentuje zapytanie, które jest używane do śledzenia zmian cyklem życia działań, które tworzą wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="d4a26-102">Represents a query that is used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="d4a26-103">Na przykład możesz chcieć śledzić każde działanie "Wyślij wiadomość E-Mail" w ramach wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="d4a26-103">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="d4a26-104">To zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania obiektów rekordu stanu działania.</span><span class="sxs-lookup"><span data-stu-id="d4a26-104">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="d4a26-105">Stany do subskrybowania są wyszczególnione w ActivityStates.</span><span class="sxs-lookup"><span data-stu-id="d4a26-105">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
 <span data-ttu-id="d4a26-106">Aby uzyskać więcej informacji na temat śledzenia kwerend profilu, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="d4a26-106">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="d4a26-107">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d4a26-107">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d4a26-108">&nbsp;&nbsp;[ **\<systemami. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="d4a26-108">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="d4a26-109">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Śledzenie >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="d4a26-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="d4a26-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="d4a26-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="d4a26-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<przepływ pracy >** ](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="d4a26-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="d4a26-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<activityStateQueries >** ](activitystatequeries.md)</span><span class="sxs-lookup"><span data-stu-id="d4a26-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQueries>**](activitystatequeries.md)</span></span>\
<span data-ttu-id="d4a26-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<activityStateQuery >**</span><span class="sxs-lookup"><span data-stu-id="d4a26-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityStateQuery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4a26-114">Składnia</span><span class="sxs-lookup"><span data-stu-id="d4a26-114">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d4a26-115">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d4a26-115">Attributes and Elements</span></span>  
 <span data-ttu-id="d4a26-116">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d4a26-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d4a26-117">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d4a26-117">Attributes</span></span>  
  
|<span data-ttu-id="d4a26-118">Atrybut</span><span class="sxs-lookup"><span data-stu-id="d4a26-118">Attribute</span></span>|<span data-ttu-id="d4a26-119">Opis</span><span class="sxs-lookup"><span data-stu-id="d4a26-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d4a26-120">activityName</span><span class="sxs-lookup"><span data-stu-id="d4a26-120">activityName</span></span>|<span data-ttu-id="d4a26-121">Ciąg określający nazwę czynności, aby filtrować <xref:System.Activities.Tracking.ActivityStateRecord> wystąpień.</span><span class="sxs-lookup"><span data-stu-id="d4a26-121">A string that specifies the name of the activity to filter <xref:System.Activities.Tracking.ActivityStateRecord> instances on.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d4a26-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d4a26-122">Child Elements</span></span>  
  
|<span data-ttu-id="d4a26-123">Element</span><span class="sxs-lookup"><span data-stu-id="d4a26-123">Element</span></span>|<span data-ttu-id="d4a26-124">Opis</span><span class="sxs-lookup"><span data-stu-id="d4a26-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d4a26-125">\<argumenty ></span><span class="sxs-lookup"><span data-stu-id="d4a26-125">\<arguments></span></span>](arguments.md)|<span data-ttu-id="d4a26-126">Kolekcja argumenty skojarzone z tej kwerendy działania.</span><span class="sxs-lookup"><span data-stu-id="d4a26-126">A collection of arguments associated with this activity query.</span></span>|  
|[<span data-ttu-id="d4a26-127">\<Stany ></span><span class="sxs-lookup"><span data-stu-id="d4a26-127">\<states></span></span>](states.md)|<span data-ttu-id="d4a26-128">Kolekcja elementów konfiguracji, które zawierają stany subskrybowanego działania, dla którego należy obliczanie rekord śledzenia.</span><span class="sxs-lookup"><span data-stu-id="d4a26-128">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
|[<span data-ttu-id="d4a26-129">\<Stany ></span><span class="sxs-lookup"><span data-stu-id="d4a26-129">\<states></span></span>](states.md)|<span data-ttu-id="d4a26-130">Kolekcja zmiennych skojarzoną z tym zapytaniem działania.</span><span class="sxs-lookup"><span data-stu-id="d4a26-130">A collection of variables associated with this activity query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d4a26-131">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d4a26-131">Parent Elements</span></span>  
  
|<span data-ttu-id="d4a26-132">Element</span><span class="sxs-lookup"><span data-stu-id="d4a26-132">Element</span></span>|<span data-ttu-id="d4a26-133">Opis</span><span class="sxs-lookup"><span data-stu-id="d4a26-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d4a26-134">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="d4a26-134">\<faultPropagationQuery></span></span>](faultpropagationquery.md)|<span data-ttu-id="d4a26-135">Reprezentuje listę elementów konfiguracji, które są używane do śledzenia żądań, aby anulować działanie podrzędne przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d4a26-135">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="d4a26-136">Zapytanie jest niezbędne do uczestnika śledzenia do subskrybowania Anuluj żądanie rekordu obiektów.</span><span class="sxs-lookup"><span data-stu-id="d4a26-136">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d4a26-137">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d4a26-137">Remarks</span></span>  
 <span data-ttu-id="d4a26-138">Jedno rozwiązanie ActivityStateQuery jest możliwość wyodrębniania danych podczas śledzenia wykonywania przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="d4a26-138">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="d4a26-139">Umożliwia to dodatkowy kontekst podczas uzyskiwania dostępu do śledzenia rekordów post wykonywania.</span><span class="sxs-lookup"><span data-stu-id="d4a26-139">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="d4a26-140">Można użyć [ \<argumentów >](arguments.md), [ \<Stany >](states.md) i [ \<Stany >](states.md) elementy, aby wyodrębnić dowolną zmienną lub argument z dowolnego działania w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="d4a26-140">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="d4a26-141">W poniższym przykładzie przedstawiono zapytanie o stan działania, które wyodrębnia zmienne i argumenty podczas emitowania `Closed` rekordu śledzenia działania.</span><span class="sxs-lookup"><span data-stu-id="d4a26-141">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="d4a26-142">Zmienne i argumenty mogą być wyodrębniane tylko za pomocą ActivityStateRecord i w ten sposób są subskrybowane w ramach profilu śledzenia przy użyciu [ \<ActivityStateQuery >](activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="d4a26-142">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d4a26-143">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d4a26-143">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="d4a26-144">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="d4a26-144">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="d4a26-145">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="d4a26-145">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
