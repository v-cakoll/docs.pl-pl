---
title: <faultPropagationQueries>programu WCF
ms.date: 03/30/2017
ms.assetid: d85f66a7-e7b0-4dbb-83cc-89fa06fc9161
ms.openlocfilehash: 709c2c6907b4d0d28118f9de12edb047aa16d741
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855263"
---
# <a name="faultpropagationqueries-of-wcf"></a><span data-ttu-id="34c74-102">\<faultPropagationQueries > WCF</span><span class="sxs-lookup"><span data-stu-id="34c74-102">\<faultPropagationQueries> of WCF</span></span>

<span data-ttu-id="34c74-103">Reprezentuje kolekcję zapytań, które są używane do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="34c74-103">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="34c74-104">To zdarzenie jest wykonywane za każdym razem, gdy FaultHandler przetwarza błąd.</span><span class="sxs-lookup"><span data-stu-id="34c74-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="34c74-105">Należy użyć takiej kwerendy do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="34c74-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="34c74-106">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania błędów propagacji rekordów.</span><span class="sxs-lookup"><span data-stu-id="34c74-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
<span data-ttu-id="34c74-107">Aby uzyskać więcej informacji na temat śledzenia kwerend profilu, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="34c74-107">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="34c74-108">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="34c74-108">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="34c74-109">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="34c74-109">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="34c74-110">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Śledzenie >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="34c74-110">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="34c74-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> profilów**</span><span class="sxs-lookup"><span data-stu-id="34c74-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="34c74-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="34c74-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="34c74-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<przepływ pracy >** ](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="34c74-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="34c74-114">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<faultPropagationQueries >**</span><span class="sxs-lookup"><span data-stu-id="34c74-114">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<faultPropagationQueries>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34c74-115">Składnia</span><span class="sxs-lookup"><span data-stu-id="34c74-115">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <faultPropagationQueries>
          <faultPropagationQuery faultSourceActivityName="String"
                                 faultHandlerActivityName="String"/>
        </faultPropagationQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="34c74-116">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="34c74-116">Attributes and elements</span></span>

<span data-ttu-id="34c74-117">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="34c74-117">The following sections describe attributes, child elements, and parent elements.</span></span>
  
### <a name="attributes"></a><span data-ttu-id="34c74-118">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="34c74-118">Attributes</span></span>

<span data-ttu-id="34c74-119">Brak.</span><span class="sxs-lookup"><span data-stu-id="34c74-119">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="34c74-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="34c74-120">Child elements</span></span>

|<span data-ttu-id="34c74-121">Element</span><span class="sxs-lookup"><span data-stu-id="34c74-121">Element</span></span>|<span data-ttu-id="34c74-122">Opis</span><span class="sxs-lookup"><span data-stu-id="34c74-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="34c74-123">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="34c74-123">\<faultPropagationQuery></span></span>](faultpropagationquery-of-wcf.md)|<span data-ttu-id="34c74-124">Zapytanie, które jest używane do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="34c74-124">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="34c74-125">To zdarzenie jest wykonywane za każdym razem, gdy FaultHandler przetwarza błąd.</span><span class="sxs-lookup"><span data-stu-id="34c74-125">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="34c74-126">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="34c74-126">Parent elements</span></span>  
  
|<span data-ttu-id="34c74-127">Element</span><span class="sxs-lookup"><span data-stu-id="34c74-127">Element</span></span>|<span data-ttu-id="34c74-128">Opis</span><span class="sxs-lookup"><span data-stu-id="34c74-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="34c74-129">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="34c74-129">\<workflow></span></span>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="34c74-130">Element konfiguracji, który zawiera wszystkie zapytania dla określonego przepływu pracy identyfikowane przez `activityDefinitionId` właściwości.</span><span class="sxs-lookup"><span data-stu-id="34c74-130">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="34c74-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="34c74-131">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="34c74-132">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="34c74-132">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="34c74-133">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="34c74-133">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
