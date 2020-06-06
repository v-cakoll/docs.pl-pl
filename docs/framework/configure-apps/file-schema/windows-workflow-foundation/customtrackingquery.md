---
title: <customTrackingQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e108e89-1132-46b7-868a-c7f5c69dc89f
ms.openlocfilehash: a02d71811709b2c285ab7081b89ee3082ec5b43d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152212"
---
# \<customTrackingQuery>
<span data-ttu-id="4988e-101">Reprezentuje kolekcję zapytań, które są używane do śledzenia zdarzeń zdefiniowanych przez użytkownika w działaniach kodu.</span><span class="sxs-lookup"><span data-stu-id="4988e-101">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="4988e-102">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania śledzenia niestandardowe rekordów.</span><span class="sxs-lookup"><span data-stu-id="4988e-102">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="4988e-103">Aby uzyskać więcej informacji o śledzeniu zapytań profilowych, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="4988e-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customTrackingQueries>**](customtrackingqueries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="4988e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4988e-104">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <customTrackingQueries>
        <customTrackingQuery activityName="String"
                             name="String" />
      </customTrackingQueries>
    </workflow>
 </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4988e-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4988e-105">Attributes and Elements</span></span>  
 <span data-ttu-id="4988e-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4988e-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4988e-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4988e-107">Attributes</span></span>  
  
|<span data-ttu-id="4988e-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="4988e-108">Attribute</span></span>|<span data-ttu-id="4988e-109">Opis</span><span class="sxs-lookup"><span data-stu-id="4988e-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4988e-110">activityName</span><span class="sxs-lookup"><span data-stu-id="4988e-110">activityName</span></span>|<span data-ttu-id="4988e-111">Ciąg określający nazwę działania, który wygenerował rekord śledzenia.</span><span class="sxs-lookup"><span data-stu-id="4988e-111">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|<span data-ttu-id="4988e-112">name</span><span class="sxs-lookup"><span data-stu-id="4988e-112">name</span></span>|<span data-ttu-id="4988e-113">Ciąg, który określa nazwę rekord śledzenia niestandardowego, który jest emitowane.</span><span class="sxs-lookup"><span data-stu-id="4988e-113">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4988e-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4988e-114">Child Elements</span></span>  
 <span data-ttu-id="4988e-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="4988e-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4988e-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4988e-116">Parent Elements</span></span>  
  
|<span data-ttu-id="4988e-117">Element</span><span class="sxs-lookup"><span data-stu-id="4988e-117">Element</span></span>|<span data-ttu-id="4988e-118">Opis</span><span class="sxs-lookup"><span data-stu-id="4988e-118">Description</span></span>|  
|-------------|-----------------|  
|[\<customTrackingQuery>](customtrackingquery.md)|<span data-ttu-id="4988e-119">Zapytanie, które jest używane do śledzenia zdarzeń zdefiniowanych przez użytkownika w działaniach kodu.</span><span class="sxs-lookup"><span data-stu-id="4988e-119">A query that is used to track events that you define in your code activities.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4988e-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4988e-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="4988e-121">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="4988e-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="4988e-122">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="4988e-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
