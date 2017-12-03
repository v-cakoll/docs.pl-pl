---
title: '&lt;customTrackingQueries&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 4e9e732d-911d-45a3-a569-4b5e9cd1ffbe
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 241684a3a2344d6eb7f3b34c81c581b0ec5130f1
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltcustomtrackingqueriesgt"></a><span data-ttu-id="9f221-102">&lt;customTrackingQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="9f221-102">&lt;customTrackingQueries&gt;</span></span>
<span data-ttu-id="9f221-103">Reprezentuje kolekcję zapytań, które są używane do śledzenia zdarzeń zdefiniowanych przez użytkownika w działaniach kodu.</span><span class="sxs-lookup"><span data-stu-id="9f221-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="9f221-104">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania śledzenia niestandardowe rekordów.</span><span class="sxs-lookup"><span data-stu-id="9f221-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="9f221-105">Aby uzyskać więcej informacji na zapytania dotyczące profilu śledzenia, zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="9f221-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="9f221-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="9f221-106">\<system.serviceModel></span></span>  
<span data-ttu-id="9f221-107">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="9f221-107">\<tracking></span></span>  
<span data-ttu-id="9f221-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="9f221-108">\<trackingProfile></span></span>  
<span data-ttu-id="9f221-109">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="9f221-109">\<workflow></span></span>  
<span data-ttu-id="9f221-110">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="9f221-110">\<customTrackingQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f221-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="9f221-111">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <customTrackingQueries>
        <customTrackingQuery activityName="String" 
                             name="String" />
      </customTrackingQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9f221-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9f221-112">Attributes and Elements</span></span>  
 <span data-ttu-id="9f221-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9f221-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9f221-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9f221-114">Attributes</span></span>  
 <span data-ttu-id="9f221-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="9f221-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9f221-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9f221-116">Child Elements</span></span>  
  
|<span data-ttu-id="9f221-117">Element</span><span class="sxs-lookup"><span data-stu-id="9f221-117">Element</span></span>|<span data-ttu-id="9f221-118">Opis</span><span class="sxs-lookup"><span data-stu-id="9f221-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9f221-119">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="9f221-119">\<customTrackingQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingquery.md)|<span data-ttu-id="9f221-120">Zapytanie, które jest używane do śledzenia zdarzeń zdefiniowanych przez użytkownika w działaniach kodu.</span><span class="sxs-lookup"><span data-stu-id="9f221-120">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9f221-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9f221-121">Parent Elements</span></span>  
  
|<span data-ttu-id="9f221-122">Element</span><span class="sxs-lookup"><span data-stu-id="9f221-122">Element</span></span>|<span data-ttu-id="9f221-123">Opis</span><span class="sxs-lookup"><span data-stu-id="9f221-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9f221-124">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="9f221-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="9f221-125">Element konfiguracji, który zawiera wszystkie zapytania dotyczące określonego przepływu pracy, identyfikowane przez **obiektu activityDefinitionId** właściwości.</span><span class="sxs-lookup"><span data-stu-id="9f221-125">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9f221-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9f221-126">See Also</span></span>  
 <span data-ttu-id="9f221-127"><xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="9f221-127"><xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="9f221-128"><xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="9f221-128"><xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="9f221-129">Przepływ pracy, kontrola i śledzenie</span><span class="sxs-lookup"><span data-stu-id="9f221-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="9f221-130">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="9f221-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
