---
title: <activityScheduledQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ca6e82f1-54f2-48d6-899c-9873065b5547
ms.openlocfilehash: 89de9ef10449fbae78a8c5b558101a2cf6477b07
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945532"
---
# <a name="activityscheduledqueries"></a><span data-ttu-id="d41ca-101">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="d41ca-101">\<activityScheduledQueries></span></span>
<span data-ttu-id="d41ca-102">Reprezentuje kolekcję zapytań, które są używane do śledzenia działania zaPLanowane do wykonania przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d41ca-102">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="d41ca-103">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania zaPLanowane rekordów.</span><span class="sxs-lookup"><span data-stu-id="d41ca-103">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="d41ca-104">Aby uzyskać więcej informacji o śledzeniu zapytań profilowych, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="d41ca-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="d41ca-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="d41ca-105">\<system.serviceModel></span></span>  
<span data-ttu-id="d41ca-106">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="d41ca-106">\<tracking></span></span>  
<span data-ttu-id="d41ca-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="d41ca-107">\<trackingProfile></span></span>  
<span data-ttu-id="d41ca-108">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="d41ca-108">\<workflow></span></span>  
<span data-ttu-id="d41ca-109">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="d41ca-109">\<activityScheduledQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d41ca-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="d41ca-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d41ca-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d41ca-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d41ca-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d41ca-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d41ca-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d41ca-113">Attributes</span></span>  
 <span data-ttu-id="d41ca-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="d41ca-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d41ca-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d41ca-115">Child Elements</span></span>  
  
|<span data-ttu-id="d41ca-116">Element</span><span class="sxs-lookup"><span data-stu-id="d41ca-116">Element</span></span>|<span data-ttu-id="d41ca-117">Opis</span><span class="sxs-lookup"><span data-stu-id="d41ca-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d41ca-118">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="d41ca-118">\<activityScheduledQuery></span></span>](activityscheduledquery.md)|<span data-ttu-id="d41ca-119">Zapytanie, które jest używane do śledzenia działania zaPLanowane do wykonania przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d41ca-119">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d41ca-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d41ca-120">Parent Elements</span></span>  
  
|<span data-ttu-id="d41ca-121">Element</span><span class="sxs-lookup"><span data-stu-id="d41ca-121">Element</span></span>|<span data-ttu-id="d41ca-122">Opis</span><span class="sxs-lookup"><span data-stu-id="d41ca-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d41ca-123">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="d41ca-123">\<workflow></span></span>](workflow.md)|<span data-ttu-id="d41ca-124">Element konfiguracji, który zawiera wszystkie zapytania dla określonego przepływu pracy identyfikowanego przez właściwość **activityDefinitionId** .</span><span class="sxs-lookup"><span data-stu-id="d41ca-124">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d41ca-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d41ca-125">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>
- [<span data-ttu-id="d41ca-126">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="d41ca-126">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="d41ca-127">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="d41ca-127">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
