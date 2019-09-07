---
title: <variable>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 46cc8cbc-10ec-4625-8813-3f5cd6c6afde
ms.openlocfilehash: 5878720f51f4b5cfe3163abf316a867ccda31342
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397769"
---
# <a name="variable"></a><span data-ttu-id="61b56-101">\<Zmienna ></span><span class="sxs-lookup"><span data-stu-id="61b56-101">\<variable></span></span>
<span data-ttu-id="61b56-102">Reprezentuje kolekcję zmiennych skojarzoną z tym zapytaniem działania.</span><span class="sxs-lookup"><span data-stu-id="61b56-102">Represents a collection of variables associated with this activity query.</span></span>  
  
 <span data-ttu-id="61b56-103">Aby uzyskać więcej informacji na temat śledzenia kwerend profilu, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="61b56-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="61b56-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="61b56-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="61b56-105">&nbsp;&nbsp;[ **\<systemami. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="61b56-105">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="61b56-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Śledzenie >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="61b56-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="61b56-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="61b56-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="61b56-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<przepływ pracy >** ](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="61b56-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="61b56-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<activityStateQueries >** ](activitystatequeries.md)</span><span class="sxs-lookup"><span data-stu-id="61b56-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQueries>**](activitystatequeries.md)</span></span>\
<span data-ttu-id="61b56-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<activityStateQuery >** ](activitystatequery.md)</span><span class="sxs-lookup"><span data-stu-id="61b56-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQuery>**](activitystatequery.md)</span></span>\
<span data-ttu-id="61b56-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Zmienne >** ](variables.md)</span><span class="sxs-lookup"><span data-stu-id="61b56-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<variables>**](variables.md)</span></span>\
<span data-ttu-id="61b56-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Zmienna >**</span><span class="sxs-lookup"><span data-stu-id="61b56-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<variable>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61b56-113">Składnia</span><span class="sxs-lookup"><span data-stu-id="61b56-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="61b56-114">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="61b56-114">Attributes and Elements</span></span>  
 <span data-ttu-id="61b56-115">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="61b56-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="61b56-116">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="61b56-116">Attributes</span></span>  
  
|<span data-ttu-id="61b56-117">Atrybut</span><span class="sxs-lookup"><span data-stu-id="61b56-117">Attribute</span></span>|<span data-ttu-id="61b56-118">Opis</span><span class="sxs-lookup"><span data-stu-id="61b56-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="61b56-119">nazwa</span><span class="sxs-lookup"><span data-stu-id="61b56-119">name</span></span>|<span data-ttu-id="61b56-120">Ciąg określający nazwę zmiennej.</span><span class="sxs-lookup"><span data-stu-id="61b56-120">A string that specifies the name of the variable.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="61b56-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="61b56-121">Child Elements</span></span>  
 <span data-ttu-id="61b56-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="61b56-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="61b56-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="61b56-123">Parent Elements</span></span>  
  
|<span data-ttu-id="61b56-124">Element</span><span class="sxs-lookup"><span data-stu-id="61b56-124">Element</span></span>|<span data-ttu-id="61b56-125">Opis</span><span class="sxs-lookup"><span data-stu-id="61b56-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="61b56-126">\<Zmienna ></span><span class="sxs-lookup"><span data-stu-id="61b56-126">\<variable></span></span>](variable.md)|<span data-ttu-id="61b56-127">Zmienna skojarzonych z kwerendą stanu działania.</span><span class="sxs-lookup"><span data-stu-id="61b56-127">A variable associated with an activity state query.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="61b56-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="61b56-128">Remarks</span></span>  
 <span data-ttu-id="61b56-129">Jedno rozwiązanie ActivityStateQuery jest możliwość wyodrębniania danych podczas śledzenia wykonywania przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="61b56-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="61b56-130">Umożliwia to dodatkowy kontekst podczas uzyskiwania dostępu do śledzenia rekordów post wykonywania.</span><span class="sxs-lookup"><span data-stu-id="61b56-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="61b56-131">Można użyć [ \<argumentów >](arguments.md), [ \<Stany >](states.md) i [ \<Stany >](states.md) elementy, aby wyodrębnić dowolną zmienną lub argument z dowolnego działania w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="61b56-131">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="61b56-132">W poniższym przykładzie przedstawiono zapytanie o stan działania, które wyodrębnia zmienne i argumenty podczas emitowania `Closed` rekordu śledzenia działania.</span><span class="sxs-lookup"><span data-stu-id="61b56-132">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="61b56-133">Zmienne i argumenty mogą być wyodrębniane tylko za pomocą ActivityStateRecord i w ten sposób są subskrybowane w ramach profilu śledzenia przy użyciu [ \<ActivityStateQuery >](activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="61b56-133">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="61b56-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="61b56-134">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.VariableElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="61b56-135">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="61b56-135">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="61b56-136">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="61b56-136">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
