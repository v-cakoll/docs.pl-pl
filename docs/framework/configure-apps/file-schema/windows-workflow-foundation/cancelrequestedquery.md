---
title: <cancelRequestedQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8da9b1c4-338a-4f23-9830-6d257772d340
ms.openlocfilehash: 5de459717fdc0dbf946f12dceda18dce79ca4b06
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398816"
---
# <a name="cancelrequestedquery"></a><span data-ttu-id="5b2c2-101">\<cancelRequestedQuery></span><span class="sxs-lookup"><span data-stu-id="5b2c2-101">\<cancelRequestedQuery></span></span>
<span data-ttu-id="5b2c2-102">Reprezentuje zapytanie, które jest używane do śledzenia żądań, aby anulować działanie podrzędne przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="5b2c2-102">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="5b2c2-103">Zapytanie jest niezbędne do uczestnika śledzenia do subskrybowania Anuluj żądanie rekordu obiektów.</span><span class="sxs-lookup"><span data-stu-id="5b2c2-103">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="5b2c2-104">Aby uzyskać więcej informacji na temat śledzenia kwerend profilu, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="5b2c2-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="5b2c2-105">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5b2c2-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5b2c2-106">&nbsp;&nbsp;[ **\<systemami. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="5b2c2-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="5b2c2-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Śledzenie >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="5b2c2-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="5b2c2-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="5b2c2-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="5b2c2-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<przepływ pracy >** ](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="5b2c2-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="5b2c2-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<cancelRequestedQueries >** ](cancelrequestedqueries.md)</span><span class="sxs-lookup"><span data-stu-id="5b2c2-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cancelRequestedQueries>**](cancelrequestedqueries.md)</span></span>\
<span data-ttu-id="5b2c2-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<cancelRequestedQuery >**</span><span class="sxs-lookup"><span data-stu-id="5b2c2-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQuery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b2c2-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="5b2c2-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5b2c2-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="5b2c2-113">Attributes and Elements</span></span>  
 <span data-ttu-id="5b2c2-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="5b2c2-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5b2c2-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="5b2c2-115">Attributes</span></span>  
  
|<span data-ttu-id="5b2c2-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="5b2c2-116">Attribute</span></span>|<span data-ttu-id="5b2c2-117">Opis</span><span class="sxs-lookup"><span data-stu-id="5b2c2-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5b2c2-118">activityName</span><span class="sxs-lookup"><span data-stu-id="5b2c2-118">activityName</span></span>|<span data-ttu-id="5b2c2-119">Ciąg określający nazwę działania, który żąda anulowania.</span><span class="sxs-lookup"><span data-stu-id="5b2c2-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="5b2c2-120">childActivityName</span><span class="sxs-lookup"><span data-stu-id="5b2c2-120">childActivityName</span></span>|<span data-ttu-id="5b2c2-121">Ciąg, który określa nazwę działania podrzędnego, dla której zażądano anulowania.</span><span class="sxs-lookup"><span data-stu-id="5b2c2-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5b2c2-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="5b2c2-122">Child Elements</span></span>  
 <span data-ttu-id="5b2c2-123">Brak.</span><span class="sxs-lookup"><span data-stu-id="5b2c2-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5b2c2-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="5b2c2-124">Parent Elements</span></span>  
  
|<span data-ttu-id="5b2c2-125">Element</span><span class="sxs-lookup"><span data-stu-id="5b2c2-125">Element</span></span>|<span data-ttu-id="5b2c2-126">Opis</span><span class="sxs-lookup"><span data-stu-id="5b2c2-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5b2c2-127">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="5b2c2-127">\<faultPropagationQuery></span></span>](faultpropagationquery.md)|<span data-ttu-id="5b2c2-128">Reprezentuje listę elementów konfiguracji, które są używane do śledzenia żądań, aby anulować działanie podrzędne przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="5b2c2-128">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="5b2c2-129">Zapytanie jest niezbędne do uczestnika śledzenia do subskrybowania Anuluj żądanie rekordu obiektów.</span><span class="sxs-lookup"><span data-stu-id="5b2c2-129">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5b2c2-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5b2c2-130">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>
- [<span data-ttu-id="5b2c2-131">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="5b2c2-131">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="5b2c2-132">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="5b2c2-132">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
