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
ms.openlocfilehash: 803616fdd287491afa27d3ac23dfce99c5db08ca
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="57398---maxinstancesexceeded"></a><span data-ttu-id="0bc95-102">57398 - MaxInstancesExceeded</span><span class="sxs-lookup"><span data-stu-id="0bc95-102">57398 - MaxInstancesExceeded</span></span>
## <a name="properties"></a><span data-ttu-id="0bc95-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="0bc95-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0bc95-104">ID</span><span class="sxs-lookup"><span data-stu-id="0bc95-104">ID</span></span>|<span data-ttu-id="0bc95-105">57398</span><span class="sxs-lookup"><span data-stu-id="0bc95-105">57398</span></span>|  
|<span data-ttu-id="0bc95-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="0bc95-106">Keywords</span></span>|<span data-ttu-id="0bc95-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="0bc95-107">WFServices</span></span>|  
|<span data-ttu-id="0bc95-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="0bc95-108">Level</span></span>|<span data-ttu-id="0bc95-109">Ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="0bc95-109">Warning</span></span>|  
|<span data-ttu-id="0bc95-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="0bc95-110">Channel</span></span>|<span data-ttu-id="0bc95-111">Microsoft-Windows aplikacji Server aplikacje/analityczne</span><span class="sxs-lookup"><span data-stu-id="0bc95-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="0bc95-112">Opis</span><span class="sxs-lookup"><span data-stu-id="0bc95-112">Description</span></span>  
 <span data-ttu-id="0bc95-113">Wskazuje, że system osiągnął limit ustawiony dla przepustnicy "MaxConcurrentInstances".</span><span class="sxs-lookup"><span data-stu-id="0bc95-113">Indicates the system hit the limit set for throttle 'MaxConcurrentInstances'.</span></span>  
  
## <a name="message"></a><span data-ttu-id="0bc95-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="0bc95-114">Message</span></span>  
 <span data-ttu-id="0bc95-115">System osiągnął limit ustawiony dla przepustnicy "MaxConcurrentInstances".</span><span class="sxs-lookup"><span data-stu-id="0bc95-115">The system hit the limit set for throttle 'MaxConcurrentInstances'.</span></span> <span data-ttu-id="0bc95-116">Limit dla tej przepustnicy została ustawiona na %1.</span><span class="sxs-lookup"><span data-stu-id="0bc95-116">Limit for this throttle was set to %1.</span></span> <span data-ttu-id="0bc95-117">Wartość przepustnicy można zmienić, modyfikując atrybut "maxConcurrentInstances" elementu serviceThrottle lub modyfikując właściwość "MaxConcurrentInstances" zachowania ServiceThrottlingBehavior.</span><span class="sxs-lookup"><span data-stu-id="0bc95-117">Throttle value can be changed by modifying attribute 'maxConcurrentInstances' in serviceThrottle element or by modifying 'MaxConcurrentInstances' property on behavior ServiceThrottlingBehavior.</span></span>  
  
## <a name="details"></a><span data-ttu-id="0bc95-118">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="0bc95-118">Details</span></span>  
  
|<span data-ttu-id="0bc95-119">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="0bc95-119">Data Item Name</span></span>|<span data-ttu-id="0bc95-120">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="0bc95-120">Data Item Type</span></span>|<span data-ttu-id="0bc95-121">Opis</span><span class="sxs-lookup"><span data-stu-id="0bc95-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="0bc95-122">Nazwa</span><span class="sxs-lookup"><span data-stu-id="0bc95-122">Name</span></span>|<span data-ttu-id="0bc95-123">xs:String</span><span class="sxs-lookup"><span data-stu-id="0bc95-123">xs:string</span></span>|<span data-ttu-id="0bc95-124">Nazwa elementu.</span><span class="sxs-lookup"><span data-stu-id="0bc95-124">The name of the item.</span></span>|  
|<span data-ttu-id="0bc95-125">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="0bc95-125">AppDomain</span></span>|<span data-ttu-id="0bc95-126">xs:String</span><span class="sxs-lookup"><span data-stu-id="0bc95-126">xs:string</span></span>|<span data-ttu-id="0bc95-127">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="0bc95-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
