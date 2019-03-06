---
title: <argument>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a7144d53-8023-4e90-971f-895e016fd58a
ms.openlocfilehash: e386ad261422904d3f33385bb80bdb8c1ac029b9
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57371188"
---
# <a name="argument"></a><span data-ttu-id="adb38-101">\<argument ></span><span class="sxs-lookup"><span data-stu-id="adb38-101">\<argument></span></span>
<span data-ttu-id="adb38-102">Element konfiguracji, który reprezentuje argumentu skojarzonych z kwerendą stanu działania.</span><span class="sxs-lookup"><span data-stu-id="adb38-102">A configuration element that represents an argument associated with an activity state query.</span></span>  
  
 <span data-ttu-id="adb38-103">Aby uzyskać więcej informacji na podstawie śledzenia zapytań profilu zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="adb38-103">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="adb38-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="adb38-104">\<system.serviceModel></span></span>  
<span data-ttu-id="adb38-105">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="adb38-105">\<tracking></span></span>  
<span data-ttu-id="adb38-106">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="adb38-106">\<trackingProfile></span></span>  
<span data-ttu-id="adb38-107">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="adb38-107">\<workflow></span></span>  
<span data-ttu-id="adb38-108">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="adb38-108">\<activityStateQueries></span></span>  
<span data-ttu-id="adb38-109">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="adb38-109">\<activityStateQuery></span></span>  
<span data-ttu-id="adb38-110">\<arguments></span><span class="sxs-lookup"><span data-stu-id="adb38-110">\<arguments></span></span>  
<span data-ttu-id="adb38-111">\<argument ></span><span class="sxs-lookup"><span data-stu-id="adb38-111">\<argument></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="adb38-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="adb38-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="adb38-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="adb38-113">Attributes and Elements</span></span>  
 <span data-ttu-id="adb38-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="adb38-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="adb38-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="adb38-115">Attributes</span></span>  
  
|<span data-ttu-id="adb38-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="adb38-116">Attribute</span></span>|<span data-ttu-id="adb38-117">Opis</span><span class="sxs-lookup"><span data-stu-id="adb38-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="adb38-118">nazwa</span><span class="sxs-lookup"><span data-stu-id="adb38-118">name</span></span>|<span data-ttu-id="adb38-119">Ciąg określający nazwę argumentu.</span><span class="sxs-lookup"><span data-stu-id="adb38-119">A string that specifies the name of the argument.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="adb38-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="adb38-120">Child Elements</span></span>  
 <span data-ttu-id="adb38-121">Brak.</span><span class="sxs-lookup"><span data-stu-id="adb38-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="adb38-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="adb38-122">Parent Elements</span></span>  
  
|<span data-ttu-id="adb38-123">Element</span><span class="sxs-lookup"><span data-stu-id="adb38-123">Element</span></span>|<span data-ttu-id="adb38-124">Opis</span><span class="sxs-lookup"><span data-stu-id="adb38-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="adb38-125">\<arguments></span><span class="sxs-lookup"><span data-stu-id="adb38-125">\<arguments></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md)|<span data-ttu-id="adb38-126">Kolekcja argumenty skojarzone z tej kwerendy działania.</span><span class="sxs-lookup"><span data-stu-id="adb38-126">A collection of arguments associated with this activity query.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="adb38-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="adb38-127">Remarks</span></span>  
 <span data-ttu-id="adb38-128">Jedno rozwiązanie ActivityStateQuery jest możliwość wyodrębniania danych podczas śledzenia wykonywania przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="adb38-128">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="adb38-129">Umożliwia to dodatkowy kontekst podczas uzyskiwania dostępu do śledzenia rekordów post wykonywania.</span><span class="sxs-lookup"><span data-stu-id="adb38-129">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="adb38-130">Możesz użyć [ \<argumenty >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<stany >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) i [ \<stany >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elementy, aby wyodrębnić dowolnej zmiennej lub argumentu wszelkie działania w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="adb38-130">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="adb38-131">W poniższym przykładzie pokazano kwerendą stanu działania, który wyodrębnia zmienne i argumenty podczas działania `Closed` rekord śledzenia jest emitowane.</span><span class="sxs-lookup"><span data-stu-id="adb38-131">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="adb38-132">Zmienne i argumenty wyodrębniania tylko z ActivityStateRecord i w związku z tym subskrybują w ramach śledzenia profilu przy użyciu [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="adb38-132">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="adb38-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="adb38-133">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.ArgumentElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="adb38-134">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="adb38-134">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="adb38-135">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="adb38-135">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
