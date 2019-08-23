---
title: <cancelRequestedQuery>programu WCF
ms.date: 03/30/2017
ms.assetid: b690d870-02eb-4c56-8bc3-e5ca99d7097b
ms.openlocfilehash: 7952520edbf799e5fab6864e50962c6ec2860928
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919646"
---
# <a name="cancelrequestedquery-of-wcf"></a><span data-ttu-id="b53fb-102">\<cancelRequestedQuery > WCF</span><span class="sxs-lookup"><span data-stu-id="b53fb-102">\<cancelRequestedQuery> of WCF</span></span>

<span data-ttu-id="b53fb-103">Reprezentuje zapytanie, które jest używane do śledzenia żądań, aby anulować działanie podrzędne przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b53fb-103">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="b53fb-104">Zapytanie jest niezbędne do uczestnika śledzenia do subskrybowania Anuluj żądanie rekordu obiektów.</span><span class="sxs-lookup"><span data-stu-id="b53fb-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
<span data-ttu-id="b53fb-105">Aby uzyskać więcej informacji na temat śledzenia kwerend profilu, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="b53fb-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="b53fb-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="b53fb-106">\<system.serviceModel></span></span>  
<span data-ttu-id="b53fb-107">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="b53fb-107">\<tracking></span></span>  
<span data-ttu-id="b53fb-108">\<> profilów</span><span class="sxs-lookup"><span data-stu-id="b53fb-108">\<profiles></span></span>  
<span data-ttu-id="b53fb-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="b53fb-109">\<trackingProfile></span></span>  
<span data-ttu-id="b53fb-110">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="b53fb-110">\<workflow></span></span>  
<span data-ttu-id="b53fb-111">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="b53fb-111">\<cancelRequestedQueries></span></span>  
<span data-ttu-id="b53fb-112">\<cancelRequestedQuery></span><span class="sxs-lookup"><span data-stu-id="b53fb-112">\<cancelRequestedQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b53fb-113">Składnia</span><span class="sxs-lookup"><span data-stu-id="b53fb-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b53fb-114">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b53fb-114">Attributes and elements</span></span>

<span data-ttu-id="b53fb-115">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b53fb-115">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="b53fb-116">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b53fb-116">Attributes</span></span>  
  
|<span data-ttu-id="b53fb-117">Atrybut</span><span class="sxs-lookup"><span data-stu-id="b53fb-117">Attribute</span></span>|<span data-ttu-id="b53fb-118">Opis</span><span class="sxs-lookup"><span data-stu-id="b53fb-118">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="b53fb-119">Ciąg określający nazwę działania, który żąda anulowania.</span><span class="sxs-lookup"><span data-stu-id="b53fb-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|`childActivityName`|<span data-ttu-id="b53fb-120">Ciąg, który określa nazwę działania podrzędnego, dla której zażądano anulowania.</span><span class="sxs-lookup"><span data-stu-id="b53fb-120">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b53fb-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b53fb-121">Child elements</span></span>

<span data-ttu-id="b53fb-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="b53fb-122">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="b53fb-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b53fb-123">Parent elements</span></span>
  
|<span data-ttu-id="b53fb-124">Element</span><span class="sxs-lookup"><span data-stu-id="b53fb-124">Element</span></span>|<span data-ttu-id="b53fb-125">Opis</span><span class="sxs-lookup"><span data-stu-id="b53fb-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b53fb-126">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="b53fb-126">\<cancelRequestedQueries></span></span>](cancelrequestedqueries-of-wcf.md)|<span data-ttu-id="b53fb-127">Reprezentuje kolekcję zapytań, które są używane do śledzenia żądań, aby anulować działanie podrzędne przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b53fb-127">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b53fb-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b53fb-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>
- [<span data-ttu-id="b53fb-129">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="b53fb-129">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="b53fb-130">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="b53fb-130">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
