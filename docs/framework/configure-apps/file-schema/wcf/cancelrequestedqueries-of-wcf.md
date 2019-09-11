---
title: <cancelRequestedQueries>programu WCF
ms.date: 03/30/2017
ms.assetid: a7cc7125-9ea3-4d3f-99c0-878cdeb1258a
ms.openlocfilehash: 63cfc835ac7ce88bde56fd9243a2cf6652cbce6e
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850097"
---
# <a name="cancelrequestedqueries-of-wcf"></a><span data-ttu-id="66c14-102">\<cancelRequestedQueries > WCF</span><span class="sxs-lookup"><span data-stu-id="66c14-102">\<cancelRequestedQueries> of WCF</span></span>
<span data-ttu-id="66c14-103">Reprezentuje kolekcję zapytań, które są używane do śledzenia żądań, aby anulować działanie podrzędne przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="66c14-103">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="66c14-104">Zapytanie jest niezbędne do uczestnika śledzenia do subskrybowania Anuluj żądanie rekordu obiektów.</span><span class="sxs-lookup"><span data-stu-id="66c14-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
<span data-ttu-id="66c14-105">Aby uzyskać więcej informacji o śledzeniu zapytań profilowych, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="66c14-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="66c14-106">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="66c14-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="66c14-107">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="66c14-107">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="66c14-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Śledzenie >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="66c14-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="66c14-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> profilów**</span><span class="sxs-lookup"><span data-stu-id="66c14-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="66c14-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="66c14-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="66c14-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<przepływ pracy >** ](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="66c14-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="66c14-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<cancelRequestedQueries >**</span><span class="sxs-lookup"><span data-stu-id="66c14-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQueries>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66c14-113">Składnia</span><span class="sxs-lookup"><span data-stu-id="66c14-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="66c14-114">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="66c14-114">Attributes and elements</span></span>  

<span data-ttu-id="66c14-115">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="66c14-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="66c14-116">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="66c14-116">Attributes</span></span>

<span data-ttu-id="66c14-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="66c14-117">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="66c14-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="66c14-118">Child elements</span></span>
  
|<span data-ttu-id="66c14-119">Element</span><span class="sxs-lookup"><span data-stu-id="66c14-119">Element</span></span>|<span data-ttu-id="66c14-120">Opis</span><span class="sxs-lookup"><span data-stu-id="66c14-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="66c14-121">\<cancelRequestedQuery></span><span class="sxs-lookup"><span data-stu-id="66c14-121">\<cancelRequestedQuery></span></span>](cancelrequestedquery-of-wcf.md)|<span data-ttu-id="66c14-122">Zapytanie, które jest używane do śledzenia żądań, aby anulować działanie podrzędne przez działanie nadrzędne</span><span class="sxs-lookup"><span data-stu-id="66c14-122">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="66c14-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="66c14-123">Parent elements</span></span>  
  
|<span data-ttu-id="66c14-124">Element</span><span class="sxs-lookup"><span data-stu-id="66c14-124">Element</span></span>|<span data-ttu-id="66c14-125">Opis</span><span class="sxs-lookup"><span data-stu-id="66c14-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="66c14-126">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="66c14-126">\<workflow></span></span>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="66c14-127">Element konfiguracji, który zawiera wszystkie zapytania dla określonego przepływu pracy identyfikowane przez <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId> właściwości.</span><span class="sxs-lookup"><span data-stu-id="66c14-127">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId> property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="66c14-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="66c14-128">See also</span></span>

- <xref:System.Activities.Tracking.CancelRequestedQuery>
- [<span data-ttu-id="66c14-129">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="66c14-129">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="66c14-130">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="66c14-130">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
