---
title: <faultPropagationQueries>programu WCF
ms.date: 03/30/2017
ms.assetid: d85f66a7-e7b0-4dbb-83cc-89fa06fc9161
ms.openlocfilehash: 709c2c6907b4d0d28118f9de12edb047aa16d741
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855263"
---
# <a name="faultpropagationqueries-of-wcf"></a><span data-ttu-id="61625-102">\<faultPropagationQueries>programu WCF</span><span class="sxs-lookup"><span data-stu-id="61625-102">\<faultPropagationQueries> of WCF</span></span>

<span data-ttu-id="61625-103">Reprezentuje kolekcję zapytań, które są używane do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="61625-103">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="61625-104">To zdarzenie jest wykonywane za każdym razem, gdy FaultHandler przetwarza błąd.</span><span class="sxs-lookup"><span data-stu-id="61625-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="61625-105">Należy użyć takiej kwerendy do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="61625-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="61625-106">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania błędów propagacji rekordów.</span><span class="sxs-lookup"><span data-stu-id="61625-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
<span data-ttu-id="61625-107">Aby uzyskać więcej informacji na temat śledzenia kwerend profilu, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="61625-107">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<faultPropagationQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="61625-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="61625-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="61625-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="61625-109">Attributes and elements</span></span>

<span data-ttu-id="61625-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="61625-110">The following sections describe attributes, child elements, and parent elements.</span></span>
  
### <a name="attributes"></a><span data-ttu-id="61625-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="61625-111">Attributes</span></span>

<span data-ttu-id="61625-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="61625-112">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="61625-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="61625-113">Child elements</span></span>

|<span data-ttu-id="61625-114">Element</span><span class="sxs-lookup"><span data-stu-id="61625-114">Element</span></span>|<span data-ttu-id="61625-115">Opis</span><span class="sxs-lookup"><span data-stu-id="61625-115">Description</span></span>|  
|-------------|-----------------|  
|[\<faultPropagationQuery>](faultpropagationquery-of-wcf.md)|<span data-ttu-id="61625-116">Zapytanie, które jest używane do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="61625-116">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="61625-117">To zdarzenie jest wykonywane za każdym razem, gdy FaultHandler przetwarza błąd.</span><span class="sxs-lookup"><span data-stu-id="61625-117">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="61625-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="61625-118">Parent elements</span></span>  
  
|<span data-ttu-id="61625-119">Element</span><span class="sxs-lookup"><span data-stu-id="61625-119">Element</span></span>|<span data-ttu-id="61625-120">Opis</span><span class="sxs-lookup"><span data-stu-id="61625-120">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="61625-121">Element konfiguracji, który zawiera wszystkie zapytania dla określonego przepływu pracy identyfikowane przez `activityDefinitionId` właściwości.</span><span class="sxs-lookup"><span data-stu-id="61625-121">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="61625-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="61625-122">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="61625-123">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="61625-123">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="61625-124">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="61625-124">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
