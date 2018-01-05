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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0d8bfde535eb417614eee4ec6a2db7985152be33
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltservicetimeoutsgt"></a><span data-ttu-id="34a68-102">&lt;serviceTimeouts&gt;</span><span class="sxs-lookup"><span data-stu-id="34a68-102">&lt;serviceTimeouts&gt;</span></span>
<span data-ttu-id="34a68-103">Określa limit czasu dla usługi.</span><span class="sxs-lookup"><span data-stu-id="34a68-103">Specifies the timeout for a service.</span></span>  
  
 <span data-ttu-id="34a68-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="34a68-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="34a68-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="34a68-105">\<behaviors></span></span>  
<span data-ttu-id="34a68-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="34a68-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="34a68-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="34a68-107">\<behavior></span></span>  
<span data-ttu-id="34a68-108">\<serviceTimeouts ></span><span class="sxs-lookup"><span data-stu-id="34a68-108">\<serviceTimeouts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34a68-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="34a68-109">Syntax</span></span>  
  
```xml  
<serviceTimeouts transactionTimeout="TimeSpan" />  
```  
  
## <a name="type"></a><span data-ttu-id="34a68-110">Typ</span><span class="sxs-lookup"><span data-stu-id="34a68-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="34a68-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="34a68-111">Attributes and Elements</span></span>  
 <span data-ttu-id="34a68-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="34a68-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="34a68-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="34a68-113">Attributes</span></span>  
  
|<span data-ttu-id="34a68-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="34a68-114">Attribute</span></span>|<span data-ttu-id="34a68-115">Opis</span><span class="sxs-lookup"><span data-stu-id="34a68-115">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="34a68-116">A <xref:System.TimeSpan> wartość, która określa przedział czasu transakcji musi przepływać z klienta do serwera.</span><span class="sxs-lookup"><span data-stu-id="34a68-116">A <xref:System.TimeSpan> value that specifies the interval of time a transaction must flow from client to server.</span></span> <span data-ttu-id="34a68-117">Wartość domyślna to "00: 00:00".</span><span class="sxs-lookup"><span data-stu-id="34a68-117">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="34a68-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="34a68-118">Child Elements</span></span>  
 <span data-ttu-id="34a68-119">Brak.</span><span class="sxs-lookup"><span data-stu-id="34a68-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="34a68-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="34a68-120">Parent Elements</span></span>  
  
|<span data-ttu-id="34a68-121">Element</span><span class="sxs-lookup"><span data-stu-id="34a68-121">Element</span></span>|<span data-ttu-id="34a68-122">Opis</span><span class="sxs-lookup"><span data-stu-id="34a68-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="34a68-123">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="34a68-123">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="34a68-124">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="34a68-124">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="34a68-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="34a68-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>
