---
title: <customTrackingQueries>programu WCF
ms.date: 03/30/2017
ms.assetid: 14cfe47e-9935-4120-84f1-8f38de8ca4c1
ms.openlocfilehash: 2c4bd74ae346c536e8bc0ae454e638b7c76a40fc
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855431"
---
# <a name="customtrackingqueries-of-wcf"></a><span data-ttu-id="4a32b-102">\<customTrackingQueries>programu WCF</span><span class="sxs-lookup"><span data-stu-id="4a32b-102">\<customTrackingQueries> of WCF</span></span>

<span data-ttu-id="4a32b-103">Reprezentuje kolekcję zapytań, które są używane do śledzenia zdarzeń zdefiniowanych przez użytkownika w działaniach kodu.</span><span class="sxs-lookup"><span data-stu-id="4a32b-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="4a32b-104">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania śledzenia niestandardowe rekordów.</span><span class="sxs-lookup"><span data-stu-id="4a32b-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
<span data-ttu-id="4a32b-105">Aby uzyskać więcej informacji na temat śledzenia kwerend profilu, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="4a32b-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQueries>**  

## <a name="syntax"></a><span data-ttu-id="4a32b-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="4a32b-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4a32b-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4a32b-107">Attributes and elements</span></span>

<span data-ttu-id="4a32b-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4a32b-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4a32b-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4a32b-109">Attributes</span></span>

<span data-ttu-id="4a32b-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="4a32b-110">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="4a32b-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4a32b-111">Child elements</span></span>
  
|<span data-ttu-id="4a32b-112">Element</span><span class="sxs-lookup"><span data-stu-id="4a32b-112">Element</span></span>|<span data-ttu-id="4a32b-113">Opis</span><span class="sxs-lookup"><span data-stu-id="4a32b-113">Description</span></span>|  
|-------------|-----------------|  
|[\<customTrackingQuery>](customtrackingquery-of-wcf.md)|<span data-ttu-id="4a32b-114">Zapytanie, które jest używane do śledzenia zdarzeń zdefiniowanych przez użytkownika w działaniach kodu.</span><span class="sxs-lookup"><span data-stu-id="4a32b-114">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4a32b-115">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4a32b-115">Parent elements</span></span>  
  
|<span data-ttu-id="4a32b-116">Element</span><span class="sxs-lookup"><span data-stu-id="4a32b-116">Element</span></span>|<span data-ttu-id="4a32b-117">Opis</span><span class="sxs-lookup"><span data-stu-id="4a32b-117">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="4a32b-118">Element konfiguracji, który zawiera wszystkie zapytania dla określonego przepływu pracy identyfikowane przez `activityDefinitionId` właściwości.</span><span class="sxs-lookup"><span data-stu-id="4a32b-118">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4a32b-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4a32b-119">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="4a32b-120">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="4a32b-120">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="4a32b-121">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="4a32b-121">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
