---
title: <cancelRequestedQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8da9b1c4-338a-4f23-9830-6d257772d340
ms.openlocfilehash: d9c3f91edb41bd034bcd978b075d62f74b6e308d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945883"
---
# <a name="cancelrequestedquery"></a><span data-ttu-id="aba82-101">\<cancelRequestedQuery></span><span class="sxs-lookup"><span data-stu-id="aba82-101">\<cancelRequestedQuery></span></span>
<span data-ttu-id="aba82-102">Reprezentuje zapytanie, które jest używane do śledzenia żądań, aby anulować działanie podrzędne przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="aba82-102">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="aba82-103">Zapytanie jest niezbędne do uczestnika śledzenia do subskrybowania Anuluj żądanie rekordu obiektów.</span><span class="sxs-lookup"><span data-stu-id="aba82-103">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="aba82-104">Aby uzyskać więcej informacji na temat śledzenia kwerend profilu, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="aba82-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="aba82-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="aba82-105">\<system.serviceModel></span></span>  
<span data-ttu-id="aba82-106">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="aba82-106">\<tracking></span></span>  
<span data-ttu-id="aba82-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="aba82-107">\<trackingProfile></span></span>  
<span data-ttu-id="aba82-108">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="aba82-108">\<workflow></span></span>  
<span data-ttu-id="aba82-109">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="aba82-109">\<cancelRequestedQueries></span></span>  
<span data-ttu-id="aba82-110">\<cancelRequestedQuery></span><span class="sxs-lookup"><span data-stu-id="aba82-110">\<cancelRequestedQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aba82-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="aba82-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aba82-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="aba82-112">Attributes and Elements</span></span>  
 <span data-ttu-id="aba82-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="aba82-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aba82-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="aba82-114">Attributes</span></span>  
  
|<span data-ttu-id="aba82-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="aba82-115">Attribute</span></span>|<span data-ttu-id="aba82-116">Opis</span><span class="sxs-lookup"><span data-stu-id="aba82-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="aba82-117">activityName</span><span class="sxs-lookup"><span data-stu-id="aba82-117">activityName</span></span>|<span data-ttu-id="aba82-118">Ciąg określający nazwę działania, który żąda anulowania.</span><span class="sxs-lookup"><span data-stu-id="aba82-118">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="aba82-119">childActivityName</span><span class="sxs-lookup"><span data-stu-id="aba82-119">childActivityName</span></span>|<span data-ttu-id="aba82-120">Ciąg, który określa nazwę działania podrzędnego, dla której zażądano anulowania.</span><span class="sxs-lookup"><span data-stu-id="aba82-120">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="aba82-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="aba82-121">Child Elements</span></span>  
 <span data-ttu-id="aba82-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="aba82-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="aba82-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="aba82-123">Parent Elements</span></span>  
  
|<span data-ttu-id="aba82-124">Element</span><span class="sxs-lookup"><span data-stu-id="aba82-124">Element</span></span>|<span data-ttu-id="aba82-125">Opis</span><span class="sxs-lookup"><span data-stu-id="aba82-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="aba82-126">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="aba82-126">\<faultPropagationQuery></span></span>](faultpropagationquery.md)|<span data-ttu-id="aba82-127">Reprezentuje listę elementów konfiguracji, które są używane do śledzenia żądań, aby anulować działanie podrzędne przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="aba82-127">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="aba82-128">Zapytanie jest niezbędne do uczestnika śledzenia do subskrybowania Anuluj żądanie rekordu obiektów.</span><span class="sxs-lookup"><span data-stu-id="aba82-128">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="aba82-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="aba82-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>
- [<span data-ttu-id="aba82-130">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="aba82-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="aba82-131">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="aba82-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
