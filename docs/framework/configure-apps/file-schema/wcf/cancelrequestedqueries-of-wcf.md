---
title: <cancelRequestedQueries> w WCF
ms.date: 03/30/2017
ms.assetid: a7cc7125-9ea3-4d3f-99c0-878cdeb1258a
ms.openlocfilehash: a9364fc53c7eb62a240206f6c81bd434b25c3f40
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704378"
---
# <a name="cancelrequestedqueries-of-wcf"></a><span data-ttu-id="ff909-102">\<cancelRequestedQueries > w WCF</span><span class="sxs-lookup"><span data-stu-id="ff909-102">\<cancelRequestedQueries> of WCF</span></span>
<span data-ttu-id="ff909-103">Reprezentuje kolekcję zapytań, które są używane do śledzenia żądań, aby anulować działanie podrzędne przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ff909-103">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="ff909-104">Zapytanie jest niezbędne do uczestnika śledzenia do subskrybowania Anuluj żądanie rekordu obiektów.</span><span class="sxs-lookup"><span data-stu-id="ff909-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
<span data-ttu-id="ff909-105">Aby uzyskać więcej informacji na podstawie śledzenia zapytań profilu zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="ff909-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="ff909-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="ff909-106">\<system.serviceModel></span></span>  
<span data-ttu-id="ff909-107">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="ff909-107">\<tracking></span></span>  
<span data-ttu-id="ff909-108">\<profiles> \<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="ff909-108">\<profiles> \<trackingProfile></span></span>  
<span data-ttu-id="ff909-109">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="ff909-109">\<workflow></span></span>  
<span data-ttu-id="ff909-110">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="ff909-110">\<cancelRequestedQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff909-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="ff909-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ff909-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ff909-112">Attributes and elements</span></span>  

<span data-ttu-id="ff909-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ff909-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ff909-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ff909-114">Attributes</span></span>

<span data-ttu-id="ff909-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="ff909-115">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="ff909-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ff909-116">Child elements</span></span>
  
|<span data-ttu-id="ff909-117">Element</span><span class="sxs-lookup"><span data-stu-id="ff909-117">Element</span></span>|<span data-ttu-id="ff909-118">Opis</span><span class="sxs-lookup"><span data-stu-id="ff909-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ff909-119">\<cancelRequestedQuery></span><span class="sxs-lookup"><span data-stu-id="ff909-119">\<cancelRequestedQuery></span></span>](cancelrequestedquery-of-wcf.md)|<span data-ttu-id="ff909-120">Zapytanie, które jest używane do śledzenia żądań, aby anulować działanie podrzędne przez działanie nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ff909-120">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ff909-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ff909-121">Parent elements</span></span>  
  
|<span data-ttu-id="ff909-122">Element</span><span class="sxs-lookup"><span data-stu-id="ff909-122">Element</span></span>|<span data-ttu-id="ff909-123">Opis</span><span class="sxs-lookup"><span data-stu-id="ff909-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ff909-124">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="ff909-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="ff909-125">Element konfiguracji, który zawiera wszystkie zapytania dla określonego przepływu pracy identyfikowane przez <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId> właściwości.</span><span class="sxs-lookup"><span data-stu-id="ff909-125">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId> property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ff909-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ff909-126">See also</span></span>

- <xref:System.Activities.Tracking.CancelRequestedQuery>
- [<span data-ttu-id="ff909-127">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="ff909-127">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="ff909-128">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="ff909-128">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
