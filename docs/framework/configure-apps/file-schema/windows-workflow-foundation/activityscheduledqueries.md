---
title: <activityScheduledQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ca6e82f1-54f2-48d6-899c-9873065b5547
ms.openlocfilehash: e6891144d613623b199e7279aa091d4d7cbe4445
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55284560"
---
# <a name="activityscheduledqueries"></a><span data-ttu-id="72f28-101">\<activityScheduledQueries></span><span class="sxs-lookup"><span data-stu-id="72f28-101">\<activityScheduledQueries></span></span>
<span data-ttu-id="72f28-102">Reprezentuje kolekcję zapytań, które są używane do śledzenia działania zaPLanowane do wykonania przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="72f28-102">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="72f28-103">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania zaPLanowane rekordów.</span><span class="sxs-lookup"><span data-stu-id="72f28-103">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="72f28-104">Aby uzyskać więcej informacji na podstawie śledzenia zapytań profilu zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="72f28-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="72f28-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="72f28-105">\<system.serviceModel></span></span>  
<span data-ttu-id="72f28-106">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="72f28-106">\<tracking></span></span>  
<span data-ttu-id="72f28-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="72f28-107">\<trackingProfile></span></span>  
<span data-ttu-id="72f28-108">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="72f28-108">\<workflow></span></span>  
<span data-ttu-id="72f28-109">\<activityScheduledQueries></span><span class="sxs-lookup"><span data-stu-id="72f28-109">\<activityScheduledQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72f28-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="72f28-110">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityScheduledQueries>
        <activityScheduledQuery activityName="String" 
                                childActivityName="String" />
      </activityScheduledQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="72f28-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="72f28-111">Attributes and Elements</span></span>  
 <span data-ttu-id="72f28-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="72f28-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="72f28-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="72f28-113">Attributes</span></span>  
 <span data-ttu-id="72f28-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="72f28-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="72f28-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="72f28-115">Child Elements</span></span>  
  
|<span data-ttu-id="72f28-116">Element</span><span class="sxs-lookup"><span data-stu-id="72f28-116">Element</span></span>|<span data-ttu-id="72f28-117">Opis</span><span class="sxs-lookup"><span data-stu-id="72f28-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="72f28-118">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="72f28-118">\<activityScheduledQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledquery.md)|<span data-ttu-id="72f28-119">Zapytanie, które jest używane do śledzenia działania zaPLanowane do wykonania przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="72f28-119">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="72f28-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="72f28-120">Parent Elements</span></span>  
  
|<span data-ttu-id="72f28-121">Element</span><span class="sxs-lookup"><span data-stu-id="72f28-121">Element</span></span>|<span data-ttu-id="72f28-122">Opis</span><span class="sxs-lookup"><span data-stu-id="72f28-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="72f28-123">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="72f28-123">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="72f28-124">Element konfiguracji, który zawiera wszystkie zapytania dotyczące określonego przepływu pracy identyfikowane przez **activityDefinitionId** właściwości.</span><span class="sxs-lookup"><span data-stu-id="72f28-124">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="72f28-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="72f28-125">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>
- [<span data-ttu-id="72f28-126">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="72f28-126">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="72f28-127">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="72f28-127">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
