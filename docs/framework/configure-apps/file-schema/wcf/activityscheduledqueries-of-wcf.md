---
title: '&lt;activityScheduledQueries&gt; w WCF'
ms.date: 03/30/2017
ms.assetid: e351329f-9676-4f11-9b19-f4bac82f36fc
ms.openlocfilehash: 35bcb0dc0c33d30eee566869579edb32f131f495
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2018
ms.locfileid: "49452699"
---
# <a name="ltactivityscheduledqueriesgt-of-wcf"></a><span data-ttu-id="87b50-102">&lt;activityScheduledQueries&gt; w WCF</span><span class="sxs-lookup"><span data-stu-id="87b50-102">&lt;activityScheduledQueries&gt; of WCF</span></span>
<span data-ttu-id="87b50-103">Reprezentuje kolekcję zapytań, które są używane do śledzenia działania zaPLanowane do wykonania przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="87b50-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="87b50-104">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania zaPLanowane rekordów.</span><span class="sxs-lookup"><span data-stu-id="87b50-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
<span data-ttu-id="87b50-105">Aby uzyskać więcej informacji na podstawie śledzenia zapytań profilu zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="87b50-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="87b50-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="87b50-106">\<system.serviceModel></span></span>  
<span data-ttu-id="87b50-107">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="87b50-107">\<tracking></span></span>  
<span data-ttu-id="87b50-108">\<profile ></span><span class="sxs-lookup"><span data-stu-id="87b50-108">\<profiles></span></span>  
<span data-ttu-id="87b50-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="87b50-109">\<trackingProfile></span></span>  
<span data-ttu-id="87b50-110">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="87b50-110">\<workflow></span></span>  
<span data-ttu-id="87b50-111">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="87b50-111">\<activityScheduledQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87b50-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="87b50-112">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <activityScheduledQueries>
          <activityScheduledQuery activityName="String"   
                                  childActivityName="String"/>
        </activityScheduledQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="87b50-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="87b50-113">Attributes and elements</span></span>  

<span data-ttu-id="87b50-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="87b50-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="87b50-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="87b50-115">Attributes</span></span>  

<span data-ttu-id="87b50-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="87b50-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="87b50-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="87b50-117">Child elements</span></span>  
  
|<span data-ttu-id="87b50-118">Element</span><span class="sxs-lookup"><span data-stu-id="87b50-118">Element</span></span>|<span data-ttu-id="87b50-119">Opis</span><span class="sxs-lookup"><span data-stu-id="87b50-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="87b50-120">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="87b50-120">\<activityScheduledQuery></span></span>](activityscheduledquery-of-wcf.md)|<span data-ttu-id="87b50-121">Zapytanie, które jest używane do śledzenia działania zaPLanowane do wykonania przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="87b50-121">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="87b50-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="87b50-122">Parent elements</span></span>  
  
|<span data-ttu-id="87b50-123">Element</span><span class="sxs-lookup"><span data-stu-id="87b50-123">Element</span></span>|<span data-ttu-id="87b50-124">Opis</span><span class="sxs-lookup"><span data-stu-id="87b50-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="87b50-125">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="87b50-125">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="87b50-126">Element konfiguracji, który zawiera wszystkie zapytania dla określonego przepływu pracy identyfikowane przez `activityDefinitionId` właściwości.</span><span class="sxs-lookup"><span data-stu-id="87b50-126">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="87b50-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="87b50-127">See also</span></span>  

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection>
- <xref:System.Activities.Tracking.ActivityScheduledQuery>
- [<span data-ttu-id="87b50-128">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="87b50-128">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="87b50-129">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="87b50-129">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
