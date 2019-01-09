---
title: '&lt;cancelRequestedQuery&gt; w WCF'
ms.date: 03/30/2017
ms.assetid: b690d870-02eb-4c56-8bc3-e5ca99d7097b
ms.openlocfilehash: 6b41721dcc0c489377c59bfccdd0b1a617f551b0
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54149075"
---
# <a name="ltcancelrequestedquerygt-of-wcf"></a><span data-ttu-id="04b1a-102">&lt;cancelRequestedQuery&gt; w WCF</span><span class="sxs-lookup"><span data-stu-id="04b1a-102">&lt;cancelRequestedQuery&gt; of WCF</span></span>

<span data-ttu-id="04b1a-103">Reprezentuje zapytanie, które jest używane do śledzenia żądań, aby anulować działanie podrzędne przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="04b1a-103">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="04b1a-104">Zapytanie jest niezbędne do uczestnika śledzenia do subskrybowania Anuluj żądanie rekordu obiektów.</span><span class="sxs-lookup"><span data-stu-id="04b1a-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
<span data-ttu-id="04b1a-105">Aby uzyskać więcej informacji na podstawie śledzenia zapytań profilu zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="04b1a-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="04b1a-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="04b1a-106">\<system.serviceModel></span></span>  
<span data-ttu-id="04b1a-107">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="04b1a-107">\<tracking></span></span>  
<span data-ttu-id="04b1a-108">\<profile ></span><span class="sxs-lookup"><span data-stu-id="04b1a-108">\<profiles></span></span>  
<span data-ttu-id="04b1a-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="04b1a-109">\<trackingProfile></span></span>  
<span data-ttu-id="04b1a-110">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="04b1a-110">\<workflow></span></span>  
<span data-ttu-id="04b1a-111">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="04b1a-111">\<cancelRequestedQueries></span></span>  
<span data-ttu-id="04b1a-112">\<cancelRequestedQuery ></span><span class="sxs-lookup"><span data-stu-id="04b1a-112">\<cancelRequestedQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04b1a-113">Składnia</span><span class="sxs-lookup"><span data-stu-id="04b1a-113">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <cancelRequestedQueries>
          <cancelRequestedQuery activityName="String"
                                childActivityName="String" />
        </cancelRequestedQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="04b1a-114">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="04b1a-114">Attributes and elements</span></span>

<span data-ttu-id="04b1a-115">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="04b1a-115">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="04b1a-116">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="04b1a-116">Attributes</span></span>  
  
|<span data-ttu-id="04b1a-117">Atrybut</span><span class="sxs-lookup"><span data-stu-id="04b1a-117">Attribute</span></span>|<span data-ttu-id="04b1a-118">Opis</span><span class="sxs-lookup"><span data-stu-id="04b1a-118">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="04b1a-119">Ciąg określający nazwę działania, który żąda anulowania.</span><span class="sxs-lookup"><span data-stu-id="04b1a-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|`childActivityName`|<span data-ttu-id="04b1a-120">Ciąg, który określa nazwę działania podrzędnego, dla której zażądano anulowania.</span><span class="sxs-lookup"><span data-stu-id="04b1a-120">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="04b1a-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="04b1a-121">Child elements</span></span>

<span data-ttu-id="04b1a-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="04b1a-122">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="04b1a-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="04b1a-123">Parent elements</span></span>
  
|<span data-ttu-id="04b1a-124">Element</span><span class="sxs-lookup"><span data-stu-id="04b1a-124">Element</span></span>|<span data-ttu-id="04b1a-125">Opis</span><span class="sxs-lookup"><span data-stu-id="04b1a-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="04b1a-126">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="04b1a-126">\<cancelRequestedQueries></span></span>](cancelrequestedqueries-of-wcf.md)|<span data-ttu-id="04b1a-127">Reprezentuje kolekcję zapytań, które są używane do śledzenia żądań, aby anulować działanie podrzędne przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="04b1a-127">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="04b1a-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="04b1a-128">See also</span></span>  

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>
- [<span data-ttu-id="04b1a-129">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="04b1a-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="04b1a-130">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="04b1a-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
