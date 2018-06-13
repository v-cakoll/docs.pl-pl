---
title: '&lt;activityScheduledQueries&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ca6e82f1-54f2-48d6-899c-9873065b5547
ms.openlocfilehash: 6192fea9a520a3f453593e5efac964a5d32a492f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32756296"
---
# <a name="ltactivityscheduledqueriesgt"></a><span data-ttu-id="d0775-102">&lt;activityScheduledQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="d0775-102">&lt;activityScheduledQueries&gt;</span></span>
<span data-ttu-id="d0775-103">Reprezentuje kolekcję zapytań, które są używane do śledzenia działania zaPLanowane do wykonania przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d0775-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="d0775-104">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania zaPLanowane rekordów.</span><span class="sxs-lookup"><span data-stu-id="d0775-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="d0775-105">Aby uzyskać więcej informacji na zapytania dotyczące profilu śledzenia, zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="d0775-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="d0775-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="d0775-106">\<system.serviceModel></span></span>  
<span data-ttu-id="d0775-107">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="d0775-107">\<tracking></span></span>  
<span data-ttu-id="d0775-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="d0775-108">\<trackingProfile></span></span>  
<span data-ttu-id="d0775-109">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="d0775-109">\<workflow></span></span>  
<span data-ttu-id="d0775-110">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="d0775-110">\<activityScheduledQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0775-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="d0775-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d0775-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d0775-112">Attributes and Elements</span></span>  
 <span data-ttu-id="d0775-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d0775-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d0775-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d0775-114">Attributes</span></span>  
 <span data-ttu-id="d0775-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="d0775-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d0775-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d0775-116">Child Elements</span></span>  
  
|<span data-ttu-id="d0775-117">Element</span><span class="sxs-lookup"><span data-stu-id="d0775-117">Element</span></span>|<span data-ttu-id="d0775-118">Opis</span><span class="sxs-lookup"><span data-stu-id="d0775-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d0775-119">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="d0775-119">\<activityScheduledQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledquery.md)|<span data-ttu-id="d0775-120">Zapytanie, które jest używane do śledzenia działania zaPLanowane do wykonania przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d0775-120">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d0775-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d0775-121">Parent Elements</span></span>  
  
|<span data-ttu-id="d0775-122">Element</span><span class="sxs-lookup"><span data-stu-id="d0775-122">Element</span></span>|<span data-ttu-id="d0775-123">Opis</span><span class="sxs-lookup"><span data-stu-id="d0775-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d0775-124">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="d0775-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="d0775-125">Element konfiguracji, który zawiera wszystkie zapytania dotyczące określonego przepływu pracy, identyfikowane przez **obiektu activityDefinitionId** właściwości.</span><span class="sxs-lookup"><span data-stu-id="d0775-125">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d0775-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d0775-126">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="d0775-127">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="d0775-127">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="d0775-128">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="d0775-128">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
