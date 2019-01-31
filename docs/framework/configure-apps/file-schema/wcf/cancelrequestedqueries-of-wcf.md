---
title: <cancelRequestedQueries> w WCF
ms.date: 03/30/2017
ms.assetid: a7cc7125-9ea3-4d3f-99c0-878cdeb1258a
ms.openlocfilehash: a9364fc53c7eb62a240206f6c81bd434b25c3f40
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55289474"
---
# <a name="cancelrequestedqueries-of-wcf"></a><span data-ttu-id="80e08-102">\<cancelRequestedQueries > w WCF</span><span class="sxs-lookup"><span data-stu-id="80e08-102">\<cancelRequestedQueries> of WCF</span></span>
<span data-ttu-id="80e08-103">Reprezentuje kolekcję zapytań, które są używane do śledzenia żądań, aby anulować działanie podrzędne przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="80e08-103">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="80e08-104">Zapytanie jest niezbędne do uczestnika śledzenia do subskrybowania Anuluj żądanie rekordu obiektów.</span><span class="sxs-lookup"><span data-stu-id="80e08-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
<span data-ttu-id="80e08-105">Aby uzyskać więcej informacji na podstawie śledzenia zapytań profilu zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="80e08-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="80e08-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="80e08-106">\<system.serviceModel></span></span>  
<span data-ttu-id="80e08-107">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="80e08-107">\<tracking></span></span>  
<span data-ttu-id="80e08-108">\<profiles> \<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="80e08-108">\<profiles> \<trackingProfile></span></span>  
<span data-ttu-id="80e08-109">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="80e08-109">\<workflow></span></span>  
<span data-ttu-id="80e08-110">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="80e08-110">\<cancelRequestedQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80e08-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="80e08-111">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <cancelRequestQueries>
          <cancelRequestQuery activityName="String"
                              childActivityName="String" />
        </cancelRequestQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="80e08-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="80e08-112">Attributes and elements</span></span>  

<span data-ttu-id="80e08-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="80e08-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="80e08-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="80e08-114">Attributes</span></span>

<span data-ttu-id="80e08-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="80e08-115">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="80e08-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="80e08-116">Child elements</span></span>
  
|<span data-ttu-id="80e08-117">Element</span><span class="sxs-lookup"><span data-stu-id="80e08-117">Element</span></span>|<span data-ttu-id="80e08-118">Opis</span><span class="sxs-lookup"><span data-stu-id="80e08-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="80e08-119">\<cancelRequestedQuery></span><span class="sxs-lookup"><span data-stu-id="80e08-119">\<cancelRequestedQuery></span></span>](cancelrequestedquery-of-wcf.md)|<span data-ttu-id="80e08-120">Zapytanie, które jest używane do śledzenia żądań, aby anulować działanie podrzędne przez działanie nadrzędne</span><span class="sxs-lookup"><span data-stu-id="80e08-120">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="80e08-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="80e08-121">Parent elements</span></span>  
  
|<span data-ttu-id="80e08-122">Element</span><span class="sxs-lookup"><span data-stu-id="80e08-122">Element</span></span>|<span data-ttu-id="80e08-123">Opis</span><span class="sxs-lookup"><span data-stu-id="80e08-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="80e08-124">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="80e08-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="80e08-125">Element konfiguracji, który zawiera wszystkie zapytania dla określonego przepływu pracy identyfikowane przez <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId> właściwości.</span><span class="sxs-lookup"><span data-stu-id="80e08-125">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId> property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="80e08-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="80e08-126">See also</span></span>

- <xref:System.Activities.Tracking.CancelRequestedQuery>
- [<span data-ttu-id="80e08-127">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="80e08-127">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="80e08-128">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="80e08-128">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
