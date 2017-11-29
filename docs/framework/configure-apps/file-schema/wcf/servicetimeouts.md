---
title: '&lt;serviceTimeouts&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ada536cf-97dc-4cd7-89ec-ed1466c1c557
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ecefda0a3447aa029079fbb3633b05054f42195a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ltservicetimeoutsgt"></a><span data-ttu-id="a2659-102">&lt;serviceTimeouts&gt;</span><span class="sxs-lookup"><span data-stu-id="a2659-102">&lt;serviceTimeouts&gt;</span></span>
<span data-ttu-id="a2659-103">Określa limit czasu dla usługi.</span><span class="sxs-lookup"><span data-stu-id="a2659-103">Specifies the timeout for a service.</span></span>  
  
 <span data-ttu-id="a2659-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="a2659-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="a2659-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="a2659-105">\<behaviors></span></span>  
<span data-ttu-id="a2659-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="a2659-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="a2659-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="a2659-107">\<behavior></span></span>  
<span data-ttu-id="a2659-108">\<serviceTimeouts ></span><span class="sxs-lookup"><span data-stu-id="a2659-108">\<serviceTimeouts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2659-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="a2659-109">Syntax</span></span>  
  
```xml  
<serviceTimeouts transactionTimeout="TimeSpan" />  
```  
  
## <a name="type"></a><span data-ttu-id="a2659-110">Typ</span><span class="sxs-lookup"><span data-stu-id="a2659-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a2659-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a2659-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a2659-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a2659-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a2659-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a2659-113">Attributes</span></span>  
  
|<span data-ttu-id="a2659-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="a2659-114">Attribute</span></span>|<span data-ttu-id="a2659-115">Opis</span><span class="sxs-lookup"><span data-stu-id="a2659-115">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="a2659-116">A <xref:System.TimeSpan> wartość, która określa przedział czasu transakcji musi przepływać z klienta do serwera.</span><span class="sxs-lookup"><span data-stu-id="a2659-116">A <xref:System.TimeSpan> value that specifies the interval of time a transaction must flow from client to server.</span></span> <span data-ttu-id="a2659-117">Wartość domyślna to "00: 00:00".</span><span class="sxs-lookup"><span data-stu-id="a2659-117">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a2659-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a2659-118">Child Elements</span></span>  
 <span data-ttu-id="a2659-119">Brak.</span><span class="sxs-lookup"><span data-stu-id="a2659-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a2659-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a2659-120">Parent Elements</span></span>  
  
|<span data-ttu-id="a2659-121">Element</span><span class="sxs-lookup"><span data-stu-id="a2659-121">Element</span></span>|<span data-ttu-id="a2659-122">Opis</span><span class="sxs-lookup"><span data-stu-id="a2659-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a2659-123">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="a2659-123">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="a2659-124">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="a2659-124">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a2659-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a2659-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>
