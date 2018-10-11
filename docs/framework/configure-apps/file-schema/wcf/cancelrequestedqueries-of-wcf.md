---
title: '&lt;cancelRequestedQueries&gt; w WCF'
ms.date: 03/30/2017
ms.assetid: a7cc7125-9ea3-4d3f-99c0-878cdeb1258a
ms.openlocfilehash: 4d746290f01e702979d1dd0165ad3fc5299e1b75
ms.sourcegitcommit: 2eb5ca4956231c1a0efd34b6a9cab6153a5438af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/11/2018
ms.locfileid: "49087755"
---
# <a name="ltcancelrequestedqueriesgt-of-wcf"></a><span data-ttu-id="8527e-102">&lt;cancelRequestedQueries&gt; w WCF</span><span class="sxs-lookup"><span data-stu-id="8527e-102">&lt;cancelRequestedQueries&gt; of WCF</span></span>
<span data-ttu-id="8527e-103">Reprezentuje kolekcję zapytań, które są używane do śledzenia żądań, aby anulować działanie podrzędne przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="8527e-103">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="8527e-104">Zapytanie jest niezbędne do uczestnika śledzenia do subskrybowania Anuluj żądanie rekordu obiektów.</span><span class="sxs-lookup"><span data-stu-id="8527e-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="8527e-105">Aby uzyskać więcej informacji na podstawie śledzenia zapytań profilu zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="8527e-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="8527e-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="8527e-106">\<system.serviceModel></span></span>  
<span data-ttu-id="8527e-107">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="8527e-107">\<tracking></span></span>  
<span data-ttu-id="8527e-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="8527e-108">\<trackingProfile></span></span>  
<span data-ttu-id="8527e-109">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="8527e-109">\<workflow></span></span>  
<span data-ttu-id="8527e-110">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="8527e-110">\<cancelRequestedQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8527e-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="8527e-111">Syntax</span></span>  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <cancelRequestQueries>
        <cancelRequestQuery activityName="String"
                            childActivityName="String"/>
      </cancelRequestQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8527e-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="8527e-112">Attributes and Elements</span></span>  
 <span data-ttu-id="8527e-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="8527e-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8527e-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="8527e-114">Attributes</span></span>  
 <span data-ttu-id="8527e-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="8527e-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8527e-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="8527e-116">Child Elements</span></span>  
  
|<span data-ttu-id="8527e-117">Element</span><span class="sxs-lookup"><span data-stu-id="8527e-117">Element</span></span>|<span data-ttu-id="8527e-118">Opis</span><span class="sxs-lookup"><span data-stu-id="8527e-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8527e-119">\<cancelRequestedQuery></span><span class="sxs-lookup"><span data-stu-id="8527e-119">\<cancelRequestedQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/cancelrequestedquery.md)|<span data-ttu-id="8527e-120">Zapytanie, które jest używane do śledzenia żądań, aby anulować działanie podrzędne przez działanie nadrzędne</span><span class="sxs-lookup"><span data-stu-id="8527e-120">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8527e-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="8527e-121">Parent Elements</span></span>  
  
|<span data-ttu-id="8527e-122">Element</span><span class="sxs-lookup"><span data-stu-id="8527e-122">Element</span></span>|<span data-ttu-id="8527e-123">Opis</span><span class="sxs-lookup"><span data-stu-id="8527e-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8527e-124">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="8527e-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="8527e-125">Element konfiguracji, który zawiera wszystkie zapytania dla określonego przepływu pracy identyfikowane przez <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId> właściwości.</span><span class="sxs-lookup"><span data-stu-id="8527e-125">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId> property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8527e-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8527e-126">See Also</span></span>  
 <xref:System.Activities.Tracking.CancelRequestedQuery>  
 [<span data-ttu-id="8527e-127">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="8527e-127">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="8527e-128">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="8527e-128">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
