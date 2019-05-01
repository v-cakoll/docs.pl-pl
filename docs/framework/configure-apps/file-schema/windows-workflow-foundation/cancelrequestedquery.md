---
title: <cancelRequestedQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8da9b1c4-338a-4f23-9830-6d257772d340
ms.openlocfilehash: 5f2e46d5e4cdd64c37219476790b9ff92c606b6b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790237"
---
# <a name="cancelrequestedquery"></a><span data-ttu-id="5fec4-101">\<cancelRequestedQuery></span><span class="sxs-lookup"><span data-stu-id="5fec4-101">\<cancelRequestedQuery></span></span>
<span data-ttu-id="5fec4-102">Reprezentuje zapytanie, które jest używane do śledzenia żądań, aby anulować działanie podrzędne przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="5fec4-102">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="5fec4-103">Zapytanie jest niezbędne do uczestnika śledzenia do subskrybowania Anuluj żądanie rekordu obiektów.</span><span class="sxs-lookup"><span data-stu-id="5fec4-103">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="5fec4-104">Aby uzyskać więcej informacji na podstawie śledzenia zapytań profilu zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="5fec4-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="5fec4-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="5fec4-105">\<system.serviceModel></span></span>  
<span data-ttu-id="5fec4-106">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="5fec4-106">\<tracking></span></span>  
<span data-ttu-id="5fec4-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="5fec4-107">\<trackingProfile></span></span>  
<span data-ttu-id="5fec4-108">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="5fec4-108">\<workflow></span></span>  
<span data-ttu-id="5fec4-109">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="5fec4-109">\<cancelRequestedQueries></span></span>  
<span data-ttu-id="5fec4-110">\<cancelRequestedQuery></span><span class="sxs-lookup"><span data-stu-id="5fec4-110">\<cancelRequestedQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fec4-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="5fec4-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5fec4-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="5fec4-112">Attributes and Elements</span></span>  
 <span data-ttu-id="5fec4-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="5fec4-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5fec4-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="5fec4-114">Attributes</span></span>  
  
|<span data-ttu-id="5fec4-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="5fec4-115">Attribute</span></span>|<span data-ttu-id="5fec4-116">Opis</span><span class="sxs-lookup"><span data-stu-id="5fec4-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5fec4-117">activityName</span><span class="sxs-lookup"><span data-stu-id="5fec4-117">activityName</span></span>|<span data-ttu-id="5fec4-118">Ciąg określający nazwę działania, który żąda anulowania.</span><span class="sxs-lookup"><span data-stu-id="5fec4-118">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="5fec4-119">childActivityName</span><span class="sxs-lookup"><span data-stu-id="5fec4-119">childActivityName</span></span>|<span data-ttu-id="5fec4-120">Ciąg, który określa nazwę działania podrzędnego, dla której zażądano anulowania.</span><span class="sxs-lookup"><span data-stu-id="5fec4-120">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5fec4-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="5fec4-121">Child Elements</span></span>  
 <span data-ttu-id="5fec4-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="5fec4-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5fec4-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="5fec4-123">Parent Elements</span></span>  
  
|<span data-ttu-id="5fec4-124">Element</span><span class="sxs-lookup"><span data-stu-id="5fec4-124">Element</span></span>|<span data-ttu-id="5fec4-125">Opis</span><span class="sxs-lookup"><span data-stu-id="5fec4-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5fec4-126">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="5fec4-126">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="5fec4-127">Reprezentuje listę elementów konfiguracji, które są używane do śledzenia żądań, aby anulować działanie podrzędne przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="5fec4-127">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="5fec4-128">Zapytanie jest niezbędne do uczestnika śledzenia do subskrybowania Anuluj żądanie rekordu obiektów.</span><span class="sxs-lookup"><span data-stu-id="5fec4-128">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5fec4-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5fec4-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>
- [<span data-ttu-id="5fec4-130">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="5fec4-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="5fec4-131">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="5fec4-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
