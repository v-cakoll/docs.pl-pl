---
title: <customTrackingQuery> w WCF
ms.date: 03/30/2017
ms.assetid: 164446ae-8440-4b67-b217-6786cfae1e01
ms.openlocfilehash: 0a5e7c034ce1ef12a8d7d5b1753e2e441e48e293
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673176"
---
# <a name="customtrackingquery-of-wcf"></a><span data-ttu-id="10013-102">\<customTrackingQuery > w WCF</span><span class="sxs-lookup"><span data-stu-id="10013-102">\<customTrackingQuery> of WCF</span></span>

<span data-ttu-id="10013-103">Reprezentuje zapytanie, które jest używane do śledzenia zdarzeń zdefiniowanych przez użytkownika w działaniach kodu.</span><span class="sxs-lookup"><span data-stu-id="10013-103">Represents a query that is used to track events that you define in your code activities.</span></span> <span data-ttu-id="10013-104">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania śledzenia niestandardowe rekordów.</span><span class="sxs-lookup"><span data-stu-id="10013-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>

<span data-ttu-id="10013-105">Aby uzyskać więcej informacji na podstawie śledzenia zapytań profilu zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="10013-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="10013-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="10013-106">\<system.serviceModel></span></span>  
<span data-ttu-id="10013-107">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="10013-107">\<tracking></span></span>  
<span data-ttu-id="10013-108">\<profiles></span><span class="sxs-lookup"><span data-stu-id="10013-108">\<profiles></span></span>  
<span data-ttu-id="10013-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="10013-109">\<trackingProfile></span></span>  
<span data-ttu-id="10013-110">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="10013-110">\<workflow></span></span>  
<span data-ttu-id="10013-111">\<customTrackingQueries></span><span class="sxs-lookup"><span data-stu-id="10013-111">\<customTrackingQueries></span></span>  
<span data-ttu-id="10013-112">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="10013-112">\<customTrackingQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10013-113">Składnia</span><span class="sxs-lookup"><span data-stu-id="10013-113">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <customTrackingQueries>
          <customTrackingQuery activityName="String"
                               name="String"/>
        </customTrackingQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="10013-114">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="10013-114">Attributes and elements</span></span>  

<span data-ttu-id="10013-115">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="10013-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="10013-116">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="10013-116">Attributes</span></span>  
  
|<span data-ttu-id="10013-117">Atrybut</span><span class="sxs-lookup"><span data-stu-id="10013-117">Attribute</span></span>|<span data-ttu-id="10013-118">Opis</span><span class="sxs-lookup"><span data-stu-id="10013-118">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="10013-119">Ciąg określający nazwę działania, który wygenerował rekord śledzenia.</span><span class="sxs-lookup"><span data-stu-id="10013-119">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|`name`|<span data-ttu-id="10013-120">Ciąg, który określa nazwę rekord śledzenia niestandardowego, który jest emitowane.</span><span class="sxs-lookup"><span data-stu-id="10013-120">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="10013-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="10013-121">Child elements</span></span>

<span data-ttu-id="10013-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="10013-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="10013-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="10013-123">Parent elements</span></span>

|<span data-ttu-id="10013-124">Element</span><span class="sxs-lookup"><span data-stu-id="10013-124">Element</span></span>|<span data-ttu-id="10013-125">Opis</span><span class="sxs-lookup"><span data-stu-id="10013-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="10013-126">\<customTrackingQueries></span><span class="sxs-lookup"><span data-stu-id="10013-126">\<customTrackingQueries></span></span>](customtrackingqueries-of-wcf.md)|<span data-ttu-id="10013-127">Reprezentuje kolekcję zapytań, które są używane do śledzenia zdarzeń zdefiniowanych przez użytkownika w działaniach kodu.</span><span class="sxs-lookup"><span data-stu-id="10013-127">Represents a collection of queries that are used to track events that you define in your code activities.</span></span>|
  
## <a name="see-also"></a><span data-ttu-id="10013-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="10013-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="10013-129">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="10013-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="10013-130">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="10013-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
