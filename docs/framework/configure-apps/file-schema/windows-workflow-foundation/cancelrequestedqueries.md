---
title: <cancelRequestedQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: eab5af7e-76fa-434d-9d36-873e995cee05
ms.openlocfilehash: 0d08612ce5d74f4f7f505c538187ddecea610132
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398827"
---
# <a name="cancelrequestedqueries"></a><span data-ttu-id="12590-101">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="12590-101">\<cancelRequestedQueries></span></span>
<span data-ttu-id="12590-102">Reprezentuje kolekcję zapytań, które są używane do śledzenia żądań, aby anulować działanie podrzędne przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="12590-102">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="12590-103">Zapytanie jest niezbędne do uczestnika śledzenia do subskrybowania Anuluj żądanie rekordu obiektów.</span><span class="sxs-lookup"><span data-stu-id="12590-103">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="12590-104">Aby uzyskać więcej informacji o śledzeniu zapytań profilowych, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="12590-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="12590-105">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="12590-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="12590-106">&nbsp;&nbsp;[ **\<systemami. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="12590-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="12590-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Śledzenie >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="12590-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="12590-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="12590-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="12590-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<przepływ pracy >** ](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="12590-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="12590-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<cancelRequestedQueries >**</span><span class="sxs-lookup"><span data-stu-id="12590-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQueries>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12590-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="12590-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="12590-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="12590-112">Attributes and Elements</span></span>  
 <span data-ttu-id="12590-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="12590-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="12590-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="12590-114">Attributes</span></span>  
 <span data-ttu-id="12590-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="12590-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="12590-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="12590-116">Child Elements</span></span>  
  
|<span data-ttu-id="12590-117">Element</span><span class="sxs-lookup"><span data-stu-id="12590-117">Element</span></span>|<span data-ttu-id="12590-118">Opis</span><span class="sxs-lookup"><span data-stu-id="12590-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="12590-119">\<cancelRequestedQuery></span><span class="sxs-lookup"><span data-stu-id="12590-119">\<cancelRequestedQuery></span></span>](cancelrequestedquery.md)|<span data-ttu-id="12590-120">Zapytanie, które jest używane do śledzenia żądań, aby anulować działanie podrzędne przez działanie nadrzędne</span><span class="sxs-lookup"><span data-stu-id="12590-120">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="12590-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="12590-121">Parent Elements</span></span>  
  
|<span data-ttu-id="12590-122">Element</span><span class="sxs-lookup"><span data-stu-id="12590-122">Element</span></span>|<span data-ttu-id="12590-123">Opis</span><span class="sxs-lookup"><span data-stu-id="12590-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="12590-124">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="12590-124">\<workflow></span></span>](workflow.md)|<span data-ttu-id="12590-125">Element konfiguracji, który zawiera wszystkie zapytania dla określonego przepływu pracy identyfikowanego przez właściwość **activityDefinitionId** .</span><span class="sxs-lookup"><span data-stu-id="12590-125">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="12590-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="12590-126">See also</span></span>

- [<span data-ttu-id="12590-127">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="12590-127">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="12590-128">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="12590-128">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
