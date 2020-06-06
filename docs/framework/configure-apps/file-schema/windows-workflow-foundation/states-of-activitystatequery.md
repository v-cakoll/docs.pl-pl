---
title: <states> dla <activityStateQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a7cc2018-2b79-44f1-825a-bb7ca08690a3
ms.openlocfilehash: 0c8bf5b793684d3e6076114ce9eda7ffe1ef7a81
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398630"
---
# <a name="states-of-activitystatequery"></a><span data-ttu-id="4c490-102">\<states> dla \<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="4c490-102">\<states> of \<activityStateQuery></span></span>
<span data-ttu-id="4c490-103">Kolekcja elementów konfiguracji, które zawierają stany subskrybowanego działania, dla którego należy obliczanie rekord śledzenia.</span><span class="sxs-lookup"><span data-stu-id="4c490-103">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>  
  
 <span data-ttu-id="4c490-104">Aby uzyskać więcej informacji na temat śledzenia kwerend profilu, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="4c490-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQueries>**](activitystatequeries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQuery>**](activitystatequery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<states>**  
  
## <a name="syntax"></a><span data-ttu-id="4c490-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="4c490-105">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <states>
          <state name="String" />
        </states>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4c490-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4c490-106">Attributes and Elements</span></span>  
 <span data-ttu-id="4c490-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4c490-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4c490-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4c490-108">Attributes</span></span>  
 <span data-ttu-id="4c490-109">Brak.</span><span class="sxs-lookup"><span data-stu-id="4c490-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4c490-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4c490-110">Child Elements</span></span>  
  
|<span data-ttu-id="4c490-111">Element</span><span class="sxs-lookup"><span data-stu-id="4c490-111">Element</span></span>|<span data-ttu-id="4c490-112">Opis</span><span class="sxs-lookup"><span data-stu-id="4c490-112">Description</span></span>|  
|-------------|-----------------|  
|[\<state>](state-of-states.md)|<span data-ttu-id="4c490-113">Element konfiguracji zawiera stany subskrybowanego działania, dla którego należy obliczanie rekord śledzenia.</span><span class="sxs-lookup"><span data-stu-id="4c490-113">A configuration element that contains the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4c490-114">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4c490-114">Parent Elements</span></span>  
  
|<span data-ttu-id="4c490-115">Element</span><span class="sxs-lookup"><span data-stu-id="4c490-115">Element</span></span>|<span data-ttu-id="4c490-116">Opis</span><span class="sxs-lookup"><span data-stu-id="4c490-116">Description</span></span>|  
|-------------|-----------------|  
|[\<activityStateQuery>](activitystatequery.md)|<span data-ttu-id="4c490-117">Reprezentuje element konfiguracji, które jest używane do śledzenia żądań, aby anulować działanie podrzędne przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4c490-117">Represents a configuration element that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="4c490-118">Zapytanie jest niezbędne do uczestnika śledzenia do subskrybowania Anuluj żądanie rekordu obiektów.</span><span class="sxs-lookup"><span data-stu-id="4c490-118">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4c490-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4c490-119">Remarks</span></span>  
 <span data-ttu-id="4c490-120">Jedno rozwiązanie ActivityStateQuery jest możliwość wyodrębniania danych podczas śledzenia wykonywania przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="4c490-120">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="4c490-121">Umożliwia to dodatkowy kontekst podczas uzyskiwania dostępu do śledzenia rekordów post wykonywania.</span><span class="sxs-lookup"><span data-stu-id="4c490-121">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="4c490-122">Można użyć [\<arguments>](arguments.md) [\<states>](states.md) elementów i, [\<states>](states.md) Aby wyodrębnić dowolną zmienną lub argument z dowolnego działania w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="4c490-122">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="4c490-123">W poniższym przykładzie przedstawiono zapytanie o stan działania, które wyodrębnia zmienne i argumenty podczas `Closed` emitowania rekordu śledzenia działania.</span><span class="sxs-lookup"><span data-stu-id="4c490-123">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="4c490-124">Zmienne i argumenty mogą być wyodrębniane tylko za pomocą ActivityStateRecord i w ten sposób są subskrybowane w ramach profilu śledzenia przy użyciu [\<activityStateQuery>](activitystatequery.md) .</span><span class="sxs-lookup"><span data-stu-id="4c490-124">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4c490-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4c490-125">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="4c490-126">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="4c490-126">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="4c490-127">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="4c490-127">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
