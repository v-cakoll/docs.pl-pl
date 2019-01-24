---
title: '&lt;serviceTimeouts&gt;'
ms.date: 03/30/2017
ms.assetid: ada536cf-97dc-4cd7-89ec-ed1466c1c557
ms.openlocfilehash: f7aa623ee387f67f3bbff32249d3695049359cde
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54524471"
---
# <a name="ltservicetimeoutsgt"></a><span data-ttu-id="d2581-102">&lt;serviceTimeouts&gt;</span><span class="sxs-lookup"><span data-stu-id="d2581-102">&lt;serviceTimeouts&gt;</span></span>
<span data-ttu-id="d2581-103">Określa limit czasu usługi.</span><span class="sxs-lookup"><span data-stu-id="d2581-103">Specifies the timeout for a service.</span></span>  
  
 <span data-ttu-id="d2581-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d2581-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d2581-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="d2581-105">\<behaviors></span></span>  
<span data-ttu-id="d2581-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="d2581-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="d2581-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="d2581-107">\<behavior></span></span>  
<span data-ttu-id="d2581-108">\<serviceTimeouts></span><span class="sxs-lookup"><span data-stu-id="d2581-108">\<serviceTimeouts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2581-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="d2581-109">Syntax</span></span>  
  
```xml  
<serviceTimeouts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="d2581-110">Typ</span><span class="sxs-lookup"><span data-stu-id="d2581-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d2581-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d2581-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d2581-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d2581-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d2581-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d2581-113">Attributes</span></span>  
  
|<span data-ttu-id="d2581-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="d2581-114">Attribute</span></span>|<span data-ttu-id="d2581-115">Opis</span><span class="sxs-lookup"><span data-stu-id="d2581-115">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="d2581-116">A <xref:System.TimeSpan> wartość, która określa przedział czasu transakcji musi przepływać od klienta do serwera.</span><span class="sxs-lookup"><span data-stu-id="d2581-116">A <xref:System.TimeSpan> value that specifies the interval of time a transaction must flow from client to server.</span></span> <span data-ttu-id="d2581-117">Wartość domyślna to "00: 00:00".</span><span class="sxs-lookup"><span data-stu-id="d2581-117">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d2581-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d2581-118">Child Elements</span></span>  
 <span data-ttu-id="d2581-119">Brak.</span><span class="sxs-lookup"><span data-stu-id="d2581-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d2581-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d2581-120">Parent Elements</span></span>  
  
|<span data-ttu-id="d2581-121">Element</span><span class="sxs-lookup"><span data-stu-id="d2581-121">Element</span></span>|<span data-ttu-id="d2581-122">Opis</span><span class="sxs-lookup"><span data-stu-id="d2581-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d2581-123">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="d2581-123">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="d2581-124">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="d2581-124">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d2581-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d2581-125">See also</span></span>
- <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>
