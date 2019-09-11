---
title: <cancelRequestedQuery>programu WCF
ms.date: 03/30/2017
ms.assetid: b690d870-02eb-4c56-8bc3-e5ca99d7097b
ms.openlocfilehash: 0ac8b87afc44927ab6653dd6fcdc09cd61436a9b
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850049"
---
# <a name="cancelrequestedquery-of-wcf"></a><span data-ttu-id="8656f-102">\<cancelRequestedQuery > WCF</span><span class="sxs-lookup"><span data-stu-id="8656f-102">\<cancelRequestedQuery> of WCF</span></span>

<span data-ttu-id="8656f-103">Reprezentuje zapytanie, które jest używane do śledzenia żądań, aby anulować działanie podrzędne przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="8656f-103">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="8656f-104">Zapytanie jest niezbędne do uczestnika śledzenia do subskrybowania Anuluj żądanie rekordu obiektów.</span><span class="sxs-lookup"><span data-stu-id="8656f-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
<span data-ttu-id="8656f-105">Aby uzyskać więcej informacji na temat śledzenia kwerend profilu, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="8656f-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="8656f-106">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="8656f-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="8656f-107">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="8656f-107">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="8656f-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Śledzenie >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="8656f-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="8656f-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> profilów**</span><span class="sxs-lookup"><span data-stu-id="8656f-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="8656f-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="8656f-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="8656f-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<przepływ pracy >** ](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="8656f-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="8656f-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<cancelRequestedQueries >** ](cancelrequestedqueries-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="8656f-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cancelRequestedQueries>**](cancelrequestedqueries-of-wcf.md)</span></span>\
<span data-ttu-id="8656f-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<cancelRequestedQuery >**</span><span class="sxs-lookup"><span data-stu-id="8656f-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQuery>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="8656f-114">Składnia</span><span class="sxs-lookup"><span data-stu-id="8656f-114">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8656f-115">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="8656f-115">Attributes and elements</span></span>

<span data-ttu-id="8656f-116">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="8656f-116">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="8656f-117">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="8656f-117">Attributes</span></span>  
  
|<span data-ttu-id="8656f-118">Atrybut</span><span class="sxs-lookup"><span data-stu-id="8656f-118">Attribute</span></span>|<span data-ttu-id="8656f-119">Opis</span><span class="sxs-lookup"><span data-stu-id="8656f-119">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="8656f-120">Ciąg określający nazwę działania, który żąda anulowania.</span><span class="sxs-lookup"><span data-stu-id="8656f-120">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|`childActivityName`|<span data-ttu-id="8656f-121">Ciąg, który określa nazwę działania podrzędnego, dla której zażądano anulowania.</span><span class="sxs-lookup"><span data-stu-id="8656f-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8656f-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="8656f-122">Child elements</span></span>

<span data-ttu-id="8656f-123">Brak.</span><span class="sxs-lookup"><span data-stu-id="8656f-123">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="8656f-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="8656f-124">Parent elements</span></span>
  
|<span data-ttu-id="8656f-125">Element</span><span class="sxs-lookup"><span data-stu-id="8656f-125">Element</span></span>|<span data-ttu-id="8656f-126">Opis</span><span class="sxs-lookup"><span data-stu-id="8656f-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8656f-127">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="8656f-127">\<cancelRequestedQueries></span></span>](cancelrequestedqueries-of-wcf.md)|<span data-ttu-id="8656f-128">Reprezentuje kolekcję zapytań, które są używane do śledzenia żądań, aby anulować działanie podrzędne przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="8656f-128">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8656f-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8656f-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>
- [<span data-ttu-id="8656f-130">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="8656f-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="8656f-131">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="8656f-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
