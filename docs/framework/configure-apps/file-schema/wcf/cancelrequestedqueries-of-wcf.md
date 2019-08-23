---
title: <cancelRequestedQueries>programu WCF
ms.date: 03/30/2017
ms.assetid: a7cc7125-9ea3-4d3f-99c0-878cdeb1258a
ms.openlocfilehash: 0f04fc928358c96ca3112422f1a6ccd039269e47
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926247"
---
# <a name="cancelrequestedqueries-of-wcf"></a><span data-ttu-id="82a07-102">\<cancelRequestedQueries > WCF</span><span class="sxs-lookup"><span data-stu-id="82a07-102">\<cancelRequestedQueries> of WCF</span></span>
<span data-ttu-id="82a07-103">Reprezentuje kolekcję zapytań, które są używane do śledzenia żądań, aby anulować działanie podrzędne przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="82a07-103">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="82a07-104">Zapytanie jest niezbędne do uczestnika śledzenia do subskrybowania Anuluj żądanie rekordu obiektów.</span><span class="sxs-lookup"><span data-stu-id="82a07-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
<span data-ttu-id="82a07-105">Aby uzyskać więcej informacji o śledzeniu zapytań profilowych, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="82a07-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="82a07-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="82a07-106">\<system.serviceModel></span></span>  
<span data-ttu-id="82a07-107">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="82a07-107">\<tracking></span></span>  
<span data-ttu-id="82a07-108">\<profiles> \<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="82a07-108">\<profiles> \<trackingProfile></span></span>  
<span data-ttu-id="82a07-109">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="82a07-109">\<workflow></span></span>  
<span data-ttu-id="82a07-110">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="82a07-110">\<cancelRequestedQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82a07-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="82a07-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="82a07-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="82a07-112">Attributes and elements</span></span>  

<span data-ttu-id="82a07-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="82a07-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="82a07-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="82a07-114">Attributes</span></span>

<span data-ttu-id="82a07-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="82a07-115">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="82a07-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="82a07-116">Child elements</span></span>
  
|<span data-ttu-id="82a07-117">Element</span><span class="sxs-lookup"><span data-stu-id="82a07-117">Element</span></span>|<span data-ttu-id="82a07-118">Opis</span><span class="sxs-lookup"><span data-stu-id="82a07-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="82a07-119">\<cancelRequestedQuery></span><span class="sxs-lookup"><span data-stu-id="82a07-119">\<cancelRequestedQuery></span></span>](cancelrequestedquery-of-wcf.md)|<span data-ttu-id="82a07-120">Zapytanie, które jest używane do śledzenia żądań, aby anulować działanie podrzędne przez działanie nadrzędne</span><span class="sxs-lookup"><span data-stu-id="82a07-120">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="82a07-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="82a07-121">Parent elements</span></span>  
  
|<span data-ttu-id="82a07-122">Element</span><span class="sxs-lookup"><span data-stu-id="82a07-122">Element</span></span>|<span data-ttu-id="82a07-123">Opis</span><span class="sxs-lookup"><span data-stu-id="82a07-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="82a07-124">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="82a07-124">\<workflow></span></span>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="82a07-125">Element konfiguracji, który zawiera wszystkie zapytania dla określonego przepływu pracy identyfikowane przez <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId> właściwości.</span><span class="sxs-lookup"><span data-stu-id="82a07-125">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId> property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="82a07-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="82a07-126">See also</span></span>

- <xref:System.Activities.Tracking.CancelRequestedQuery>
- [<span data-ttu-id="82a07-127">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="82a07-127">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="82a07-128">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="82a07-128">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
