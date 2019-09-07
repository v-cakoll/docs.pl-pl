---
title: <faultPropagationQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 00ff90ae-ebe0-4c85-a93f-61557288d0a3
ms.openlocfilehash: bc0cc5fd027da45994269b149b72496fa03becef
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398735"
---
# <a name="faultpropagationqueries"></a><span data-ttu-id="44d1a-101">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="44d1a-101">\<faultPropagationQueries></span></span>
<span data-ttu-id="44d1a-102">Reprezentuje kolekcję zapytań, które są używane do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="44d1a-102">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="44d1a-103">To zdarzenie jest wykonywane za każdym razem, gdy FaultHandler przetwarza błąd.</span><span class="sxs-lookup"><span data-stu-id="44d1a-103">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="44d1a-104">Należy użyć takiej kwerendy do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="44d1a-104">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="44d1a-105">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania błędów propagacji rekordów.</span><span class="sxs-lookup"><span data-stu-id="44d1a-105">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="44d1a-106">Aby uzyskać więcej informacji na temat śledzenia kwerend profilu, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="44d1a-106">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="44d1a-107">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="44d1a-107">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="44d1a-108">&nbsp;&nbsp;[ **\<systemami. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="44d1a-108">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="44d1a-109">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Śledzenie >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="44d1a-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="44d1a-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="44d1a-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="44d1a-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<przepływ pracy >** ](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="44d1a-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="44d1a-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<faultPropagationQueries >**</span><span class="sxs-lookup"><span data-stu-id="44d1a-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<faultPropagationQueries>**</span></span> 
  
## <a name="syntax"></a><span data-ttu-id="44d1a-113">Składnia</span><span class="sxs-lookup"><span data-stu-id="44d1a-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="44d1a-114">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="44d1a-114">Attributes and Elements</span></span>  
 <span data-ttu-id="44d1a-115">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="44d1a-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="44d1a-116">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="44d1a-116">Attributes</span></span>  
 <span data-ttu-id="44d1a-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="44d1a-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="44d1a-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="44d1a-118">Child Elements</span></span>  
  
|<span data-ttu-id="44d1a-119">Element</span><span class="sxs-lookup"><span data-stu-id="44d1a-119">Element</span></span>|<span data-ttu-id="44d1a-120">Opis</span><span class="sxs-lookup"><span data-stu-id="44d1a-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="44d1a-121">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="44d1a-121">\<faultPropagationQuery></span></span>](faultpropagationquery.md)|<span data-ttu-id="44d1a-122">Zapytanie, które jest używane do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="44d1a-122">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="44d1a-123">To zdarzenie jest wykonywane za każdym razem, gdy FaultHandler przetwarza błąd.</span><span class="sxs-lookup"><span data-stu-id="44d1a-123">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="44d1a-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="44d1a-124">Parent Elements</span></span>  
  
|<span data-ttu-id="44d1a-125">Element</span><span class="sxs-lookup"><span data-stu-id="44d1a-125">Element</span></span>|<span data-ttu-id="44d1a-126">Opis</span><span class="sxs-lookup"><span data-stu-id="44d1a-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="44d1a-127">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="44d1a-127">\<workflow></span></span>](workflow.md)|<span data-ttu-id="44d1a-128">Element konfiguracji, który zawiera wszystkie zapytania dla określonego przepływu pracy identyfikowanego przez właściwość **activityDefinitionId** .</span><span class="sxs-lookup"><span data-stu-id="44d1a-128">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="44d1a-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="44d1a-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="44d1a-130">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="44d1a-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="44d1a-131">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="44d1a-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
