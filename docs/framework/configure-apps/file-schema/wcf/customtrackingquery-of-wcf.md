---
title: <customTrackingQuery>programu WCF
ms.date: 03/30/2017
ms.assetid: 164446ae-8440-4b67-b217-6786cfae1e01
ms.openlocfilehash: 204bbb6cf5ebcb30bf92b697885ecbbbd94385e0
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855420"
---
# <a name="customtrackingquery-of-wcf"></a><span data-ttu-id="16dff-102">\<customTrackingQuery>programu WCF</span><span class="sxs-lookup"><span data-stu-id="16dff-102">\<customTrackingQuery> of WCF</span></span>

<span data-ttu-id="16dff-103">Reprezentuje zapytanie, które jest używane do śledzenia zdarzeń zdefiniowanych w działaniach kodu.</span><span class="sxs-lookup"><span data-stu-id="16dff-103">Represents a query that is used to track events that you define in your code activities.</span></span> <span data-ttu-id="16dff-104">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania śledzenia niestandardowe rekordów.</span><span class="sxs-lookup"><span data-stu-id="16dff-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>

<span data-ttu-id="16dff-105">Aby uzyskać więcej informacji o śledzeniu zapytań profilowych, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="16dff-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customTrackingQueries>**](customtrackingqueries-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="16dff-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="16dff-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="16dff-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="16dff-107">Attributes and elements</span></span>  

<span data-ttu-id="16dff-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="16dff-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="16dff-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="16dff-109">Attributes</span></span>  
  
|<span data-ttu-id="16dff-110">Atrybut</span><span class="sxs-lookup"><span data-stu-id="16dff-110">Attribute</span></span>|<span data-ttu-id="16dff-111">Opis</span><span class="sxs-lookup"><span data-stu-id="16dff-111">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="16dff-112">Ciąg określający nazwę działania, który wygenerował rekord śledzenia.</span><span class="sxs-lookup"><span data-stu-id="16dff-112">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|`name`|<span data-ttu-id="16dff-113">Ciąg, który określa nazwę rekord śledzenia niestandardowego, który jest emitowane.</span><span class="sxs-lookup"><span data-stu-id="16dff-113">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="16dff-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="16dff-114">Child elements</span></span>

<span data-ttu-id="16dff-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="16dff-115">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="16dff-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="16dff-116">Parent elements</span></span>

|<span data-ttu-id="16dff-117">Element</span><span class="sxs-lookup"><span data-stu-id="16dff-117">Element</span></span>|<span data-ttu-id="16dff-118">Opis</span><span class="sxs-lookup"><span data-stu-id="16dff-118">Description</span></span>|  
|-------------|-----------------|  
|[\<customTrackingQueries>](customtrackingqueries-of-wcf.md)|<span data-ttu-id="16dff-119">Reprezentuje kolekcję zapytań, które są używane do śledzenia zdarzeń zdefiniowanych przez użytkownika w działaniach kodu.</span><span class="sxs-lookup"><span data-stu-id="16dff-119">Represents a collection of queries that are used to track events that you define in your code activities.</span></span>|
  
## <a name="see-also"></a><span data-ttu-id="16dff-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="16dff-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="16dff-121">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="16dff-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="16dff-122">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="16dff-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
