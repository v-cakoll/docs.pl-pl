---
title: 57398 - MaxInstancesExceeded
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f943d209-dfeb-43e5-b572-c9a06217936e
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ba48f19de1be3cfd2461e159b91fa365e24ee750
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="57398---maxinstancesexceeded"></a><span data-ttu-id="6411d-102">57398 - MaxInstancesExceeded</span><span class="sxs-lookup"><span data-stu-id="6411d-102">57398 - MaxInstancesExceeded</span></span>
## <a name="properties"></a><span data-ttu-id="6411d-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="6411d-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6411d-104">ID</span><span class="sxs-lookup"><span data-stu-id="6411d-104">ID</span></span>|<span data-ttu-id="6411d-105">57398</span><span class="sxs-lookup"><span data-stu-id="6411d-105">57398</span></span>|  
|<span data-ttu-id="6411d-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="6411d-106">Keywords</span></span>|<span data-ttu-id="6411d-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="6411d-107">WFServices</span></span>|  
|<span data-ttu-id="6411d-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="6411d-108">Level</span></span>|<span data-ttu-id="6411d-109">Ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="6411d-109">Warning</span></span>|  
|<span data-ttu-id="6411d-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="6411d-110">Channel</span></span>|<span data-ttu-id="6411d-111">Microsoft-Windows aplikacji Server aplikacje/analityczne</span><span class="sxs-lookup"><span data-stu-id="6411d-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="6411d-112">Opis</span><span class="sxs-lookup"><span data-stu-id="6411d-112">Description</span></span>  
 <span data-ttu-id="6411d-113">Wskazuje, że system osiągnął limit ustawiony dla przepustnicy "MaxConcurrentInstances".</span><span class="sxs-lookup"><span data-stu-id="6411d-113">Indicates the system hit the limit set for throttle 'MaxConcurrentInstances'.</span></span>  
  
## <a name="message"></a><span data-ttu-id="6411d-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="6411d-114">Message</span></span>  
 <span data-ttu-id="6411d-115">System osiągnął limit ustawiony dla przepustnicy "MaxConcurrentInstances".</span><span class="sxs-lookup"><span data-stu-id="6411d-115">The system hit the limit set for throttle 'MaxConcurrentInstances'.</span></span> <span data-ttu-id="6411d-116">Limit dla tej przepustnicy została ustawiona na %1.</span><span class="sxs-lookup"><span data-stu-id="6411d-116">Limit for this throttle was set to %1.</span></span> <span data-ttu-id="6411d-117">Wartość przepustnicy można zmienić, modyfikując atrybut "maxConcurrentInstances" elementu serviceThrottle lub modyfikując właściwość "MaxConcurrentInstances" zachowania ServiceThrottlingBehavior.</span><span class="sxs-lookup"><span data-stu-id="6411d-117">Throttle value can be changed by modifying attribute 'maxConcurrentInstances' in serviceThrottle element or by modifying 'MaxConcurrentInstances' property on behavior ServiceThrottlingBehavior.</span></span>  
  
## <a name="details"></a><span data-ttu-id="6411d-118">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="6411d-118">Details</span></span>  
  
|<span data-ttu-id="6411d-119">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="6411d-119">Data Item Name</span></span>|<span data-ttu-id="6411d-120">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="6411d-120">Data Item Type</span></span>|<span data-ttu-id="6411d-121">Opis</span><span class="sxs-lookup"><span data-stu-id="6411d-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="6411d-122">Nazwa</span><span class="sxs-lookup"><span data-stu-id="6411d-122">Name</span></span>|<span data-ttu-id="6411d-123">xs:String</span><span class="sxs-lookup"><span data-stu-id="6411d-123">xs:string</span></span>|<span data-ttu-id="6411d-124">Nazwa elementu.</span><span class="sxs-lookup"><span data-stu-id="6411d-124">The name of the item.</span></span>|  
|<span data-ttu-id="6411d-125">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="6411d-125">AppDomain</span></span>|<span data-ttu-id="6411d-126">xs:String</span><span class="sxs-lookup"><span data-stu-id="6411d-126">xs:string</span></span>|<span data-ttu-id="6411d-127">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="6411d-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
