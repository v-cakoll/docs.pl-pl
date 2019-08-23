---
title: <serviceTimeouts>
ms.date: 03/30/2017
ms.assetid: ada536cf-97dc-4cd7-89ec-ed1466c1c557
ms.openlocfilehash: a1792fec4f86c9ac31107c043b976cfafcfa4c13
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937094"
---
# <a name="servicetimeouts"></a><span data-ttu-id="507b3-101">\<serviceTimeouts></span><span class="sxs-lookup"><span data-stu-id="507b3-101">\<serviceTimeouts></span></span>
<span data-ttu-id="507b3-102">Określa limit czasu dla usługi.</span><span class="sxs-lookup"><span data-stu-id="507b3-102">Specifies the timeout for a service.</span></span>  
  
 <span data-ttu-id="507b3-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="507b3-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="507b3-104">\<> zachowań</span><span class="sxs-lookup"><span data-stu-id="507b3-104">\<behaviors></span></span>  
<span data-ttu-id="507b3-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="507b3-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="507b3-106">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="507b3-106">\<behavior></span></span>  
<span data-ttu-id="507b3-107">\<serviceTimeouts></span><span class="sxs-lookup"><span data-stu-id="507b3-107">\<serviceTimeouts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="507b3-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="507b3-108">Syntax</span></span>  
  
```xml  
<serviceTimeouts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="507b3-109">Typ</span><span class="sxs-lookup"><span data-stu-id="507b3-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="507b3-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="507b3-110">Attributes and Elements</span></span>  
 <span data-ttu-id="507b3-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="507b3-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="507b3-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="507b3-112">Attributes</span></span>  
  
|<span data-ttu-id="507b3-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="507b3-113">Attribute</span></span>|<span data-ttu-id="507b3-114">Opis</span><span class="sxs-lookup"><span data-stu-id="507b3-114">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="507b3-115"><xref:System.TimeSpan> Wartość, która określa przedział czasu, przez który transakcja musi przepływać z klienta do serwera.</span><span class="sxs-lookup"><span data-stu-id="507b3-115">A <xref:System.TimeSpan> value that specifies the interval of time a transaction must flow from client to server.</span></span> <span data-ttu-id="507b3-116">Wartość domyślna to "00:00:00".</span><span class="sxs-lookup"><span data-stu-id="507b3-116">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="507b3-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="507b3-117">Child Elements</span></span>  
 <span data-ttu-id="507b3-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="507b3-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="507b3-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="507b3-119">Parent Elements</span></span>  
  
|<span data-ttu-id="507b3-120">Element</span><span class="sxs-lookup"><span data-stu-id="507b3-120">Element</span></span>|<span data-ttu-id="507b3-121">Opis</span><span class="sxs-lookup"><span data-stu-id="507b3-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="507b3-122">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="507b3-122">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="507b3-123">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="507b3-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="507b3-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="507b3-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>
