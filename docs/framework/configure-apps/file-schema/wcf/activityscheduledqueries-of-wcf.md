---
title: <activityScheduledQueries>programu WCF
ms.date: 03/30/2017
ms.assetid: e351329f-9676-4f11-9b19-f4bac82f36fc
ms.openlocfilehash: 83e71e2038377ae4c1c3b17334eece3f30c919f6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920321"
---
# <a name="activityscheduledqueries-of-wcf"></a><span data-ttu-id="a5349-102">\<activityScheduledQueries > WCF</span><span class="sxs-lookup"><span data-stu-id="a5349-102">\<activityScheduledQueries> of WCF</span></span>
<span data-ttu-id="a5349-103">Reprezentuje kolekcję zapytań, które są używane do śledzenia działania zaPLanowane do wykonania przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a5349-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="a5349-104">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania zaPLanowane rekordów.</span><span class="sxs-lookup"><span data-stu-id="a5349-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
<span data-ttu-id="a5349-105">Aby uzyskać więcej informacji o śledzeniu zapytań profilowych, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="a5349-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="a5349-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="a5349-106">\<system.serviceModel></span></span>  
<span data-ttu-id="a5349-107">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="a5349-107">\<tracking></span></span>  
<span data-ttu-id="a5349-108">\<> profilów</span><span class="sxs-lookup"><span data-stu-id="a5349-108">\<profiles></span></span>  
<span data-ttu-id="a5349-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="a5349-109">\<trackingProfile></span></span>  
<span data-ttu-id="a5349-110">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="a5349-110">\<workflow></span></span>  
<span data-ttu-id="a5349-111">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="a5349-111">\<activityScheduledQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5349-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="a5349-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a5349-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a5349-113">Attributes and elements</span></span>  

<span data-ttu-id="a5349-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a5349-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a5349-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a5349-115">Attributes</span></span>  

<span data-ttu-id="a5349-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="a5349-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a5349-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a5349-117">Child elements</span></span>  
  
|<span data-ttu-id="a5349-118">Element</span><span class="sxs-lookup"><span data-stu-id="a5349-118">Element</span></span>|<span data-ttu-id="a5349-119">Opis</span><span class="sxs-lookup"><span data-stu-id="a5349-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a5349-120">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="a5349-120">\<activityScheduledQuery></span></span>](activityscheduledquery-of-wcf.md)|<span data-ttu-id="a5349-121">Zapytanie, które jest używane do śledzenia działania zaPLanowane do wykonania przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a5349-121">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a5349-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a5349-122">Parent elements</span></span>  
  
|<span data-ttu-id="a5349-123">Element</span><span class="sxs-lookup"><span data-stu-id="a5349-123">Element</span></span>|<span data-ttu-id="a5349-124">Opis</span><span class="sxs-lookup"><span data-stu-id="a5349-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a5349-125">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="a5349-125">\<workflow></span></span>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="a5349-126">Element konfiguracji, który zawiera wszystkie zapytania dla określonego przepływu pracy identyfikowane przez `activityDefinitionId` właściwości.</span><span class="sxs-lookup"><span data-stu-id="a5349-126">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a5349-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a5349-127">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection>
- <xref:System.Activities.Tracking.ActivityScheduledQuery>
- [<span data-ttu-id="a5349-128">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="a5349-128">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="a5349-129">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="a5349-129">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
