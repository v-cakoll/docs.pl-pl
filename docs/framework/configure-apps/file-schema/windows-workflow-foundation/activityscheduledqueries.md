---
title: '&lt;activityScheduledQueries&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ca6e82f1-54f2-48d6-899c-9873065b5547
ms.openlocfilehash: 2285dfae84f078483c03d85801051e29b79e74c3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54561845"
---
# <a name="ltactivityscheduledqueriesgt"></a><span data-ttu-id="35beb-102">&lt;activityScheduledQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="35beb-102">&lt;activityScheduledQueries&gt;</span></span>
<span data-ttu-id="35beb-103">Reprezentuje kolekcję zapytań, które są używane do śledzenia działania zaPLanowane do wykonania przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="35beb-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="35beb-104">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania zaPLanowane rekordów.</span><span class="sxs-lookup"><span data-stu-id="35beb-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="35beb-105">Aby uzyskać więcej informacji na podstawie śledzenia zapytań profilu zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="35beb-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="35beb-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="35beb-106">\<system.serviceModel></span></span>  
<span data-ttu-id="35beb-107">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="35beb-107">\<tracking></span></span>  
<span data-ttu-id="35beb-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="35beb-108">\<trackingProfile></span></span>  
<span data-ttu-id="35beb-109">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="35beb-109">\<workflow></span></span>  
<span data-ttu-id="35beb-110">\<activityScheduledQueries></span><span class="sxs-lookup"><span data-stu-id="35beb-110">\<activityScheduledQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35beb-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="35beb-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="35beb-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="35beb-112">Attributes and Elements</span></span>  
 <span data-ttu-id="35beb-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="35beb-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="35beb-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="35beb-114">Attributes</span></span>  
 <span data-ttu-id="35beb-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="35beb-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="35beb-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="35beb-116">Child Elements</span></span>  
  
|<span data-ttu-id="35beb-117">Element</span><span class="sxs-lookup"><span data-stu-id="35beb-117">Element</span></span>|<span data-ttu-id="35beb-118">Opis</span><span class="sxs-lookup"><span data-stu-id="35beb-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="35beb-119">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="35beb-119">\<activityScheduledQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledquery.md)|<span data-ttu-id="35beb-120">Zapytanie, które jest używane do śledzenia działania zaPLanowane do wykonania przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="35beb-120">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="35beb-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="35beb-121">Parent Elements</span></span>  
  
|<span data-ttu-id="35beb-122">Element</span><span class="sxs-lookup"><span data-stu-id="35beb-122">Element</span></span>|<span data-ttu-id="35beb-123">Opis</span><span class="sxs-lookup"><span data-stu-id="35beb-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="35beb-124">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="35beb-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="35beb-125">Element konfiguracji, który zawiera wszystkie zapytania dotyczące określonego przepływu pracy identyfikowane przez **activityDefinitionId** właściwości.</span><span class="sxs-lookup"><span data-stu-id="35beb-125">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="35beb-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="35beb-126">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>
- [<span data-ttu-id="35beb-127">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="35beb-127">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="35beb-128">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="35beb-128">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
