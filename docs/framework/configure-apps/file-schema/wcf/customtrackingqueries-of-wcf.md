---
title: '&lt;customTrackingQueries&gt; w WCF'
ms.date: 03/30/2017
ms.assetid: 14cfe47e-9935-4120-84f1-8f38de8ca4c1
ms.openlocfilehash: 11ad4281d2925a48508c6a3e8258b0b1cd49a326
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltcustomtrackingqueriesgt-of-wcf"></a><span data-ttu-id="67be6-102">&lt;customTrackingQueries&gt; w WCF</span><span class="sxs-lookup"><span data-stu-id="67be6-102">&lt;customTrackingQueries&gt; of WCF</span></span>
<span data-ttu-id="67be6-103">Reprezentuje kolekcję zapytań, które są używane do śledzenia zdarzeń zdefiniowanych przez użytkownika w działaniach kodu.</span><span class="sxs-lookup"><span data-stu-id="67be6-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="67be6-104">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania śledzenia niestandardowe rekordów.</span><span class="sxs-lookup"><span data-stu-id="67be6-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="67be6-105">Aby uzyskać więcej informacji na zapytania dotyczące profilu śledzenia, zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="67be6-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="67be6-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="67be6-106">\<system.serviceModel></span></span>  
<span data-ttu-id="67be6-107">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="67be6-107">\<tracking></span></span>  
<span data-ttu-id="67be6-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="67be6-108">\<trackingProfile></span></span>  
<span data-ttu-id="67be6-109">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="67be6-109">\<workflow></span></span>  
<span data-ttu-id="67be6-110">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="67be6-110">\<customTrackingQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67be6-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="67be6-111">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <customTrackingQueries>             <customTrackingQuery activityName="String"                 name="String"/>          </customTrackingQueries>       </workflow>   </trackingProfile></tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="67be6-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="67be6-112">Attributes and Elements</span></span>  
 <span data-ttu-id="67be6-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="67be6-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="67be6-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="67be6-114">Attributes</span></span>  
 <span data-ttu-id="67be6-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="67be6-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="67be6-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="67be6-116">Child Elements</span></span>  
  
|<span data-ttu-id="67be6-117">Element</span><span class="sxs-lookup"><span data-stu-id="67be6-117">Element</span></span>|<span data-ttu-id="67be6-118">Opis</span><span class="sxs-lookup"><span data-stu-id="67be6-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="67be6-119">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="67be6-119">\<customTrackingQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingquery.md)|<span data-ttu-id="67be6-120">Zapytanie, które jest używane do śledzenia zdarzeń zdefiniowanych przez użytkownika w działaniach kodu.</span><span class="sxs-lookup"><span data-stu-id="67be6-120">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="67be6-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="67be6-121">Parent Elements</span></span>  
  
|<span data-ttu-id="67be6-122">Element</span><span class="sxs-lookup"><span data-stu-id="67be6-122">Element</span></span>|<span data-ttu-id="67be6-123">Opis</span><span class="sxs-lookup"><span data-stu-id="67be6-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="67be6-124">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="67be6-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="67be6-125">Element konfiguracji, który zawiera wszystkie zapytania dla określonego przepływu pracy identyfikowane przez `activityDefinitionId` właściwości.</span><span class="sxs-lookup"><span data-stu-id="67be6-125">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="67be6-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="67be6-126">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="67be6-127">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="67be6-127">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="67be6-128">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="67be6-128">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
