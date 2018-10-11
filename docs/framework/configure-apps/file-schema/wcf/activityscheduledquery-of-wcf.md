---
title: '&lt;activityScheduledQuery&gt; w WCF'
ms.date: 03/30/2017
ms.assetid: 25f6eee1-3d98-4c39-b517-c0813f03f106
ms.openlocfilehash: 9a53d72316dad0178f24e05656a4fb4531b88aec
ms.sourcegitcommit: 2eb5ca4956231c1a0efd34b6a9cab6153a5438af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/11/2018
ms.locfileid: "49087768"
---
# <a name="ltactivityscheduledquerygt-of-wcf"></a><span data-ttu-id="2df38-102">&lt;activityScheduledQuery&gt; w WCF</span><span class="sxs-lookup"><span data-stu-id="2df38-102">&lt;activityScheduledQuery&gt; of WCF</span></span>
<span data-ttu-id="2df38-103">Reprezentuje kolekcję zapytań, które są używane do śledzenia działania zaPLanowane do wykonania przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="2df38-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="2df38-104">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania zaPLanowane rekordów.</span><span class="sxs-lookup"><span data-stu-id="2df38-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="2df38-105">Aby uzyskać więcej informacji na podstawie śledzenia zapytań profilu zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="2df38-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="2df38-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="2df38-106">\<system.serviceModel></span></span>  
<span data-ttu-id="2df38-107">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="2df38-107">\<tracking></span></span>  
<span data-ttu-id="2df38-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="2df38-108">\<trackingProfile></span></span>  
<span data-ttu-id="2df38-109">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="2df38-109">\<workflow></span></span>  
<span data-ttu-id="2df38-110">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="2df38-110">\<activityScheduledQueries></span></span>  
<span data-ttu-id="2df38-111">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="2df38-111">\<activityScheduledQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2df38-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="2df38-112">Syntax</span></span>  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityScheduledQueries>
        <activityScheduledQuery activityName="String"   
                                childActivityName="String"/>
      </activityScheduledQueries>
    </workflow>
  </trackingProfile>
</tracking> 
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2df38-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="2df38-113">Attributes and Elements</span></span>  
 <span data-ttu-id="2df38-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="2df38-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2df38-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="2df38-115">Attributes</span></span>  
  
|<span data-ttu-id="2df38-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="2df38-116">Attribute</span></span>|<span data-ttu-id="2df38-117">Opis</span><span class="sxs-lookup"><span data-stu-id="2df38-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2df38-118">activityName</span><span class="sxs-lookup"><span data-stu-id="2df38-118">activityName</span></span>|<span data-ttu-id="2df38-119">Ciąg określający nazwę działania, który żąda anulowania.</span><span class="sxs-lookup"><span data-stu-id="2df38-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="2df38-120">childActivityName</span><span class="sxs-lookup"><span data-stu-id="2df38-120">childActivityName</span></span>|<span data-ttu-id="2df38-121">Ciąg, który określa nazwę działania podrzędnego, dla której zażądano anulowania.</span><span class="sxs-lookup"><span data-stu-id="2df38-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2df38-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="2df38-122">Child Elements</span></span>  
 <span data-ttu-id="2df38-123">Brak.</span><span class="sxs-lookup"><span data-stu-id="2df38-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2df38-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="2df38-124">Parent Elements</span></span>  
  
|<span data-ttu-id="2df38-125">Element</span><span class="sxs-lookup"><span data-stu-id="2df38-125">Element</span></span>|<span data-ttu-id="2df38-126">Opis</span><span class="sxs-lookup"><span data-stu-id="2df38-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2df38-127">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="2df38-127">\<activityScheduledQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledquery.md)|<span data-ttu-id="2df38-128">Zapytanie, które jest używane do śledzenia działania zaPLanowane do wykonania przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="2df38-128">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2df38-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2df38-129">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement>     
 <xref:System.Activities.Tracking.ActivityScheduledQuery>     
 [<span data-ttu-id="2df38-130">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="2df38-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="2df38-131">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="2df38-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
