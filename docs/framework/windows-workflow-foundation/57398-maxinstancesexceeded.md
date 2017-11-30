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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7417d2e0e850017e65910be32e7449255f0761c3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="57398---maxinstancesexceeded"></a><span data-ttu-id="069ff-102">57398 - MaxInstancesExceeded</span><span class="sxs-lookup"><span data-stu-id="069ff-102">57398 - MaxInstancesExceeded</span></span>
## <a name="properties"></a><span data-ttu-id="069ff-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="069ff-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="069ff-104">ID</span><span class="sxs-lookup"><span data-stu-id="069ff-104">ID</span></span>|<span data-ttu-id="069ff-105">57398</span><span class="sxs-lookup"><span data-stu-id="069ff-105">57398</span></span>|  
|<span data-ttu-id="069ff-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="069ff-106">Keywords</span></span>|<span data-ttu-id="069ff-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="069ff-107">WFServices</span></span>|  
|<span data-ttu-id="069ff-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="069ff-108">Level</span></span>|<span data-ttu-id="069ff-109">Ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="069ff-109">Warning</span></span>|  
|<span data-ttu-id="069ff-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="069ff-110">Channel</span></span>|<span data-ttu-id="069ff-111">Microsoft-Windows aplikacji Server aplikacje/analityczne</span><span class="sxs-lookup"><span data-stu-id="069ff-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="069ff-112">Opis</span><span class="sxs-lookup"><span data-stu-id="069ff-112">Description</span></span>  
 <span data-ttu-id="069ff-113">Wskazuje, że system osiągnął limit ustawiony dla przepustnicy "MaxConcurrentInstances".</span><span class="sxs-lookup"><span data-stu-id="069ff-113">Indicates the system hit the limit set for throttle 'MaxConcurrentInstances'.</span></span>  
  
## <a name="message"></a><span data-ttu-id="069ff-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="069ff-114">Message</span></span>  
 <span data-ttu-id="069ff-115">System osiągnął limit ustawiony dla przepustnicy "MaxConcurrentInstances".</span><span class="sxs-lookup"><span data-stu-id="069ff-115">The system hit the limit set for throttle 'MaxConcurrentInstances'.</span></span> <span data-ttu-id="069ff-116">Limit dla tej przepustnicy została ustawiona na %1.</span><span class="sxs-lookup"><span data-stu-id="069ff-116">Limit for this throttle was set to %1.</span></span> <span data-ttu-id="069ff-117">Wartość przepustnicy można zmienić, modyfikując atrybut "maxConcurrentInstances" elementu serviceThrottle lub modyfikując właściwość "MaxConcurrentInstances" zachowania ServiceThrottlingBehavior.</span><span class="sxs-lookup"><span data-stu-id="069ff-117">Throttle value can be changed by modifying attribute 'maxConcurrentInstances' in serviceThrottle element or by modifying 'MaxConcurrentInstances' property on behavior ServiceThrottlingBehavior.</span></span>  
  
## <a name="details"></a><span data-ttu-id="069ff-118">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="069ff-118">Details</span></span>  
  
|<span data-ttu-id="069ff-119">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="069ff-119">Data Item Name</span></span>|<span data-ttu-id="069ff-120">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="069ff-120">Data Item Type</span></span>|<span data-ttu-id="069ff-121">Opis</span><span class="sxs-lookup"><span data-stu-id="069ff-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="069ff-122">Nazwa</span><span class="sxs-lookup"><span data-stu-id="069ff-122">Name</span></span>|<span data-ttu-id="069ff-123">xs:String</span><span class="sxs-lookup"><span data-stu-id="069ff-123">xs:string</span></span>|<span data-ttu-id="069ff-124">Nazwa elementu.</span><span class="sxs-lookup"><span data-stu-id="069ff-124">The name of the item.</span></span>|  
|<span data-ttu-id="069ff-125">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="069ff-125">AppDomain</span></span>|<span data-ttu-id="069ff-126">xs:String</span><span class="sxs-lookup"><span data-stu-id="069ff-126">xs:string</span></span>|<span data-ttu-id="069ff-127">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="069ff-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
