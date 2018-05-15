---
title: '&lt;serviceTimeouts&gt;'
ms.date: 03/30/2017
ms.assetid: ada536cf-97dc-4cd7-89ec-ed1466c1c557
ms.openlocfilehash: a0f0725bffe0c3c83e412348dea97b16736ef3a8
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltservicetimeoutsgt"></a><span data-ttu-id="7928d-102">&lt;serviceTimeouts&gt;</span><span class="sxs-lookup"><span data-stu-id="7928d-102">&lt;serviceTimeouts&gt;</span></span>
<span data-ttu-id="7928d-103">Określa limit czasu dla usługi.</span><span class="sxs-lookup"><span data-stu-id="7928d-103">Specifies the timeout for a service.</span></span>  
  
 <span data-ttu-id="7928d-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="7928d-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="7928d-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="7928d-105">\<behaviors></span></span>  
<span data-ttu-id="7928d-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="7928d-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="7928d-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="7928d-107">\<behavior></span></span>  
<span data-ttu-id="7928d-108">\<serviceTimeouts ></span><span class="sxs-lookup"><span data-stu-id="7928d-108">\<serviceTimeouts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7928d-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="7928d-109">Syntax</span></span>  
  
```xml  
<serviceTimeouts transactionTimeout="TimeSpan" />  
```  
  
## <a name="type"></a><span data-ttu-id="7928d-110">Typ</span><span class="sxs-lookup"><span data-stu-id="7928d-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7928d-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7928d-111">Attributes and Elements</span></span>  
 <span data-ttu-id="7928d-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="7928d-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7928d-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7928d-113">Attributes</span></span>  
  
|<span data-ttu-id="7928d-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="7928d-114">Attribute</span></span>|<span data-ttu-id="7928d-115">Opis</span><span class="sxs-lookup"><span data-stu-id="7928d-115">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="7928d-116">A <xref:System.TimeSpan> wartość, która określa przedział czasu transakcji musi przepływać z klienta do serwera.</span><span class="sxs-lookup"><span data-stu-id="7928d-116">A <xref:System.TimeSpan> value that specifies the interval of time a transaction must flow from client to server.</span></span> <span data-ttu-id="7928d-117">Wartość domyślna to "00: 00:00".</span><span class="sxs-lookup"><span data-stu-id="7928d-117">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7928d-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7928d-118">Child Elements</span></span>  
 <span data-ttu-id="7928d-119">Brak.</span><span class="sxs-lookup"><span data-stu-id="7928d-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7928d-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7928d-120">Parent Elements</span></span>  
  
|<span data-ttu-id="7928d-121">Element</span><span class="sxs-lookup"><span data-stu-id="7928d-121">Element</span></span>|<span data-ttu-id="7928d-122">Opis</span><span class="sxs-lookup"><span data-stu-id="7928d-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7928d-123">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="7928d-123">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="7928d-124">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="7928d-124">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7928d-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7928d-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>
