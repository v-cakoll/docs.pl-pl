---
title: '&lt;activityScheduledQueries&gt; w WCF'
ms.date: 03/30/2017
ms.assetid: e351329f-9676-4f11-9b19-f4bac82f36fc
ms.openlocfilehash: 5430058049e8a09c1e2a289e1f997338c23b9d94
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54492159"
---
# <a name="ltactivityscheduledqueriesgt-of-wcf"></a><span data-ttu-id="f847a-102">&lt;activityScheduledQueries&gt; w WCF</span><span class="sxs-lookup"><span data-stu-id="f847a-102">&lt;activityScheduledQueries&gt; of WCF</span></span>
<span data-ttu-id="f847a-103">Reprezentuje kolekcję zapytań, które są używane do śledzenia działania zaPLanowane do wykonania przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f847a-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="f847a-104">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania zaPLanowane rekordów.</span><span class="sxs-lookup"><span data-stu-id="f847a-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
<span data-ttu-id="f847a-105">Aby uzyskać więcej informacji na podstawie śledzenia zapytań profilu zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="f847a-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="f847a-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="f847a-106">\<system.serviceModel></span></span>  
<span data-ttu-id="f847a-107">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="f847a-107">\<tracking></span></span>  
<span data-ttu-id="f847a-108">\<profiles></span><span class="sxs-lookup"><span data-stu-id="f847a-108">\<profiles></span></span>  
<span data-ttu-id="f847a-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="f847a-109">\<trackingProfile></span></span>  
<span data-ttu-id="f847a-110">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="f847a-110">\<workflow></span></span>  
<span data-ttu-id="f847a-111">\<activityScheduledQueries></span><span class="sxs-lookup"><span data-stu-id="f847a-111">\<activityScheduledQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f847a-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="f847a-112">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <activityScheduledQueries>
          <activityScheduledQuery activityName="String"
                                  childActivityName="String" />
        </activityScheduledQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f847a-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f847a-113">Attributes and elements</span></span>  

<span data-ttu-id="f847a-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f847a-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f847a-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f847a-115">Attributes</span></span>  

<span data-ttu-id="f847a-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="f847a-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f847a-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f847a-117">Child elements</span></span>  
  
|<span data-ttu-id="f847a-118">Element</span><span class="sxs-lookup"><span data-stu-id="f847a-118">Element</span></span>|<span data-ttu-id="f847a-119">Opis</span><span class="sxs-lookup"><span data-stu-id="f847a-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f847a-120">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="f847a-120">\<activityScheduledQuery></span></span>](activityscheduledquery-of-wcf.md)|<span data-ttu-id="f847a-121">Zapytanie, które jest używane do śledzenia działania zaPLanowane do wykonania przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f847a-121">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f847a-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f847a-122">Parent elements</span></span>  
  
|<span data-ttu-id="f847a-123">Element</span><span class="sxs-lookup"><span data-stu-id="f847a-123">Element</span></span>|<span data-ttu-id="f847a-124">Opis</span><span class="sxs-lookup"><span data-stu-id="f847a-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f847a-125">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="f847a-125">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="f847a-126">Element konfiguracji, który zawiera wszystkie zapytania dla określonego przepływu pracy identyfikowane przez `activityDefinitionId` właściwości.</span><span class="sxs-lookup"><span data-stu-id="f847a-126">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f847a-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f847a-127">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection>
- <xref:System.Activities.Tracking.ActivityScheduledQuery>
- [<span data-ttu-id="f847a-128">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="f847a-128">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="f847a-129">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="f847a-129">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
