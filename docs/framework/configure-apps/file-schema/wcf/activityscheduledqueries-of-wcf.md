---
title: <activityScheduledQueries> w WCF
ms.date: 03/30/2017
ms.assetid: e351329f-9676-4f11-9b19-f4bac82f36fc
ms.openlocfilehash: 1c9c292080016d7a2d0014ed07be371c0e247621
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55285782"
---
# <a name="activityscheduledqueries-of-wcf"></a><span data-ttu-id="7da92-102">\<activityScheduledQueries > w WCF</span><span class="sxs-lookup"><span data-stu-id="7da92-102">\<activityScheduledQueries> of WCF</span></span>
<span data-ttu-id="7da92-103">Reprezentuje kolekcję zapytań, które są używane do śledzenia działania zaPLanowane do wykonania przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="7da92-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="7da92-104">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania zaPLanowane rekordów.</span><span class="sxs-lookup"><span data-stu-id="7da92-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
<span data-ttu-id="7da92-105">Aby uzyskać więcej informacji na podstawie śledzenia zapytań profilu zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="7da92-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="7da92-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="7da92-106">\<system.serviceModel></span></span>  
<span data-ttu-id="7da92-107">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="7da92-107">\<tracking></span></span>  
<span data-ttu-id="7da92-108">\<profiles></span><span class="sxs-lookup"><span data-stu-id="7da92-108">\<profiles></span></span>  
<span data-ttu-id="7da92-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="7da92-109">\<trackingProfile></span></span>  
<span data-ttu-id="7da92-110">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="7da92-110">\<workflow></span></span>  
<span data-ttu-id="7da92-111">\<activityScheduledQueries></span><span class="sxs-lookup"><span data-stu-id="7da92-111">\<activityScheduledQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7da92-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="7da92-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7da92-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7da92-113">Attributes and elements</span></span>  

<span data-ttu-id="7da92-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="7da92-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7da92-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7da92-115">Attributes</span></span>  

<span data-ttu-id="7da92-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="7da92-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7da92-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7da92-117">Child elements</span></span>  
  
|<span data-ttu-id="7da92-118">Element</span><span class="sxs-lookup"><span data-stu-id="7da92-118">Element</span></span>|<span data-ttu-id="7da92-119">Opis</span><span class="sxs-lookup"><span data-stu-id="7da92-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7da92-120">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="7da92-120">\<activityScheduledQuery></span></span>](activityscheduledquery-of-wcf.md)|<span data-ttu-id="7da92-121">Zapytanie, które jest używane do śledzenia działania zaPLanowane do wykonania przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="7da92-121">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7da92-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7da92-122">Parent elements</span></span>  
  
|<span data-ttu-id="7da92-123">Element</span><span class="sxs-lookup"><span data-stu-id="7da92-123">Element</span></span>|<span data-ttu-id="7da92-124">Opis</span><span class="sxs-lookup"><span data-stu-id="7da92-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7da92-125">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="7da92-125">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="7da92-126">Element konfiguracji, który zawiera wszystkie zapytania dla określonego przepływu pracy identyfikowane przez `activityDefinitionId` właściwości.</span><span class="sxs-lookup"><span data-stu-id="7da92-126">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7da92-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7da92-127">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection>
- <xref:System.Activities.Tracking.ActivityScheduledQuery>
- [<span data-ttu-id="7da92-128">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="7da92-128">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="7da92-129">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="7da92-129">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
