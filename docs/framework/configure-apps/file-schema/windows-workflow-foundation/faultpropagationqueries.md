---
title: <faultPropagationQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 00ff90ae-ebe0-4c85-a93f-61557288d0a3
ms.openlocfilehash: 3d6d03638ec5806448a16cc32b37e630d6198624
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152134"
---
# <a name="faultpropagationqueries"></a><span data-ttu-id="e67be-101">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="e67be-101">\<faultPropagationQueries></span></span>
<span data-ttu-id="e67be-102">Reprezentuje kolekcję zapytań, które są używane do śledzenia obsługi błędów, które występują w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="e67be-102">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="e67be-103">To zdarzenie występuje za każdym razem, gdy FaultHandler przetwarza usterkę.</span><span class="sxs-lookup"><span data-stu-id="e67be-103">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="e67be-104">Należy użyć takiej kwerendy do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="e67be-104">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="e67be-105">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania błędów propagacji rekordów.</span><span class="sxs-lookup"><span data-stu-id="e67be-105">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="e67be-106">Aby uzyskać więcej informacji na temat śledzenia zapytań profilowych, zobacz [Śledzenie profili](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="e67be-106">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="e67be-107">[**\<>konfiguracyjne**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e67be-107">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e67be-108">&nbsp;&nbsp;[**\<System.>z>**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="e67be-108">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="e67be-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<>śledzenia**](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="e67be-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="e67be-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="e67be-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="e67be-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>przepływu pracy**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="e67be-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="e67be-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<faultPropagationQueries>**</span><span class="sxs-lookup"><span data-stu-id="e67be-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<faultPropagationQueries>**</span></span>
  
## <a name="syntax"></a><span data-ttu-id="e67be-113">Składnia</span><span class="sxs-lookup"><span data-stu-id="e67be-113">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <faultPropagationQueries>
        <faultPropagationQuery activityName="String"
                               faultHandlerActivityName="String" />
      </faultPropagationQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e67be-114">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e67be-114">Attributes and Elements</span></span>  
 <span data-ttu-id="e67be-115">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e67be-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e67be-116">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e67be-116">Attributes</span></span>  
 <span data-ttu-id="e67be-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="e67be-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e67be-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e67be-118">Child Elements</span></span>  
  
|<span data-ttu-id="e67be-119">Element</span><span class="sxs-lookup"><span data-stu-id="e67be-119">Element</span></span>|<span data-ttu-id="e67be-120">Opis</span><span class="sxs-lookup"><span data-stu-id="e67be-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e67be-121">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="e67be-121">\<faultPropagationQuery></span></span>](faultpropagationquery.md)|<span data-ttu-id="e67be-122">Kwerenda, która jest używana do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="e67be-122">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="e67be-123">To zdarzenie występuje za każdym razem, gdy FaultHandler przetwarza usterkę.</span><span class="sxs-lookup"><span data-stu-id="e67be-123">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e67be-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e67be-124">Parent Elements</span></span>  
  
|<span data-ttu-id="e67be-125">Element</span><span class="sxs-lookup"><span data-stu-id="e67be-125">Element</span></span>|<span data-ttu-id="e67be-126">Opis</span><span class="sxs-lookup"><span data-stu-id="e67be-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e67be-127">\<>przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="e67be-127">\<workflow></span></span>](workflow.md)|<span data-ttu-id="e67be-128">Element konfiguracji, który zawiera wszystkie kwerendy dla określonego przepływu pracy identyfikowane przez **activityDefinitionId** właściwości.</span><span class="sxs-lookup"><span data-stu-id="e67be-128">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e67be-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e67be-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="e67be-130">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="e67be-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="e67be-131">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="e67be-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
