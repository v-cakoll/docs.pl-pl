---
title: <argument>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a7144d53-8023-4e90-971f-895e016fd58a
ms.openlocfilehash: ed08f5533cd6b3839775d061452cb17110cc627e
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398907"
---
# <a name="argument"></a><span data-ttu-id="de0c4-101">\<> argumentu</span><span class="sxs-lookup"><span data-stu-id="de0c4-101">\<argument></span></span>
<span data-ttu-id="de0c4-102">Element konfiguracji, który reprezentuje argumentu skojarzonych z kwerendą stanu działania.</span><span class="sxs-lookup"><span data-stu-id="de0c4-102">A configuration element that represents an argument associated with an activity state query.</span></span>  
  
 <span data-ttu-id="de0c4-103">Aby uzyskać więcej informacji na temat śledzenia kwerend profilu, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="de0c4-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="de0c4-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="de0c4-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="de0c4-105">&nbsp;&nbsp;[ **\<systemami. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="de0c4-105">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="de0c4-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Śledzenie >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="de0c4-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="de0c4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="de0c4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="de0c4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<przepływ pracy >** ](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="de0c4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="de0c4-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<activityStateQueries >** ](activitystatequeries.md)</span><span class="sxs-lookup"><span data-stu-id="de0c4-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQueries>**](activitystatequeries.md)</span></span>\
<span data-ttu-id="de0c4-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<activityStateQuery >** ](activitystatequery.md)</span><span class="sxs-lookup"><span data-stu-id="de0c4-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQuery>**](activitystatequery.md)</span></span>\
<span data-ttu-id="de0c4-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<argumenty >** ](arguments.md)</span><span class="sxs-lookup"><span data-stu-id="de0c4-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<arguments>**](arguments.md)</span></span>\
<span data-ttu-id="de0c4-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> argumentu**</span><span class="sxs-lookup"><span data-stu-id="de0c4-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<argument>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de0c4-113">Składnia</span><span class="sxs-lookup"><span data-stu-id="de0c4-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="de0c4-114">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="de0c4-114">Attributes and Elements</span></span>  
 <span data-ttu-id="de0c4-115">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="de0c4-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="de0c4-116">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="de0c4-116">Attributes</span></span>  
  
|<span data-ttu-id="de0c4-117">Atrybut</span><span class="sxs-lookup"><span data-stu-id="de0c4-117">Attribute</span></span>|<span data-ttu-id="de0c4-118">Opis</span><span class="sxs-lookup"><span data-stu-id="de0c4-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="de0c4-119">nazwa</span><span class="sxs-lookup"><span data-stu-id="de0c4-119">name</span></span>|<span data-ttu-id="de0c4-120">Ciąg określający nazwę argumentu.</span><span class="sxs-lookup"><span data-stu-id="de0c4-120">A string that specifies the name of the argument.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="de0c4-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="de0c4-121">Child Elements</span></span>  
 <span data-ttu-id="de0c4-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="de0c4-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="de0c4-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="de0c4-123">Parent Elements</span></span>  
  
|<span data-ttu-id="de0c4-124">Element</span><span class="sxs-lookup"><span data-stu-id="de0c4-124">Element</span></span>|<span data-ttu-id="de0c4-125">Opis</span><span class="sxs-lookup"><span data-stu-id="de0c4-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="de0c4-126">\<argumenty ></span><span class="sxs-lookup"><span data-stu-id="de0c4-126">\<arguments></span></span>](arguments.md)|<span data-ttu-id="de0c4-127">Kolekcja argumenty skojarzone z tej kwerendy działania.</span><span class="sxs-lookup"><span data-stu-id="de0c4-127">A collection of arguments associated with this activity query.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="de0c4-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="de0c4-128">Remarks</span></span>  
 <span data-ttu-id="de0c4-129">Jedno rozwiązanie ActivityStateQuery jest możliwość wyodrębniania danych podczas śledzenia wykonywania przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="de0c4-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="de0c4-130">Umożliwia to dodatkowy kontekst podczas uzyskiwania dostępu do śledzenia rekordów post wykonywania.</span><span class="sxs-lookup"><span data-stu-id="de0c4-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="de0c4-131">Można użyć [ \<argumentów >](arguments.md), [ \<Stany >](states.md) i [ \<Stany >](states.md) elementy, aby wyodrębnić dowolną zmienną lub argument z dowolnego działania w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="de0c4-131">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="de0c4-132">W poniższym przykładzie przedstawiono zapytanie o stan działania, które wyodrębnia zmienne i argumenty podczas emitowania `Closed` rekordu śledzenia działania.</span><span class="sxs-lookup"><span data-stu-id="de0c4-132">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="de0c4-133">Zmienne i argumenty mogą być wyodrębniane tylko za pomocą ActivityStateRecord i w ten sposób są subskrybowane w ramach profilu śledzenia przy użyciu [ \<ActivityStateQuery >](activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="de0c4-133">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="de0c4-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="de0c4-134">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ArgumentElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="de0c4-135">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="de0c4-135">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="de0c4-136">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="de0c4-136">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
