---
title: 57398 - MaxInstancesExceeded
ms.date: 03/30/2017
ms.assetid: f943d209-dfeb-43e5-b572-c9a06217936e
ms.openlocfilehash: d644c25ec2dee06eea4a5fb66c30792bb650f252
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="57398---maxinstancesexceeded"></a><span data-ttu-id="a4022-102">57398 - MaxInstancesExceeded</span><span class="sxs-lookup"><span data-stu-id="a4022-102">57398 - MaxInstancesExceeded</span></span>
## <a name="properties"></a><span data-ttu-id="a4022-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="a4022-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a4022-104">ID</span><span class="sxs-lookup"><span data-stu-id="a4022-104">ID</span></span>|<span data-ttu-id="a4022-105">57398</span><span class="sxs-lookup"><span data-stu-id="a4022-105">57398</span></span>|  
|<span data-ttu-id="a4022-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="a4022-106">Keywords</span></span>|<span data-ttu-id="a4022-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="a4022-107">WFServices</span></span>|  
|<span data-ttu-id="a4022-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="a4022-108">Level</span></span>|<span data-ttu-id="a4022-109">Ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="a4022-109">Warning</span></span>|  
|<span data-ttu-id="a4022-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="a4022-110">Channel</span></span>|<span data-ttu-id="a4022-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="a4022-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a4022-112">Opis</span><span class="sxs-lookup"><span data-stu-id="a4022-112">Description</span></span>  
 <span data-ttu-id="a4022-113">Wskazuje, że system osiągnął limit ustawiony dla przepustnicy "MaxConcurrentInstances".</span><span class="sxs-lookup"><span data-stu-id="a4022-113">Indicates the system hit the limit set for throttle 'MaxConcurrentInstances'.</span></span>  
  
## <a name="message"></a><span data-ttu-id="a4022-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="a4022-114">Message</span></span>  
 <span data-ttu-id="a4022-115">System osiągnął limit ustawiony dla przepustnicy "MaxConcurrentInstances".</span><span class="sxs-lookup"><span data-stu-id="a4022-115">The system hit the limit set for throttle 'MaxConcurrentInstances'.</span></span> <span data-ttu-id="a4022-116">Limit dla tej przepustnicy została ustawiona na %1.</span><span class="sxs-lookup"><span data-stu-id="a4022-116">Limit for this throttle was set to %1.</span></span> <span data-ttu-id="a4022-117">Wartość przepustnicy można zmienić, modyfikując atrybut "maxConcurrentInstances" elementu serviceThrottle lub modyfikując właściwość "MaxConcurrentInstances" zachowania ServiceThrottlingBehavior.</span><span class="sxs-lookup"><span data-stu-id="a4022-117">Throttle value can be changed by modifying attribute 'maxConcurrentInstances' in serviceThrottle element or by modifying 'MaxConcurrentInstances' property on behavior ServiceThrottlingBehavior.</span></span>  
  
## <a name="details"></a><span data-ttu-id="a4022-118">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="a4022-118">Details</span></span>  
  
|<span data-ttu-id="a4022-119">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="a4022-119">Data Item Name</span></span>|<span data-ttu-id="a4022-120">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="a4022-120">Data Item Type</span></span>|<span data-ttu-id="a4022-121">Opis</span><span class="sxs-lookup"><span data-stu-id="a4022-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="a4022-122">Nazwa</span><span class="sxs-lookup"><span data-stu-id="a4022-122">Name</span></span>|<span data-ttu-id="a4022-123">xs:String</span><span class="sxs-lookup"><span data-stu-id="a4022-123">xs:string</span></span>|<span data-ttu-id="a4022-124">Nazwa elementu.</span><span class="sxs-lookup"><span data-stu-id="a4022-124">The name of the item.</span></span>|  
|<span data-ttu-id="a4022-125">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="a4022-125">AppDomain</span></span>|<span data-ttu-id="a4022-126">xs:String</span><span class="sxs-lookup"><span data-stu-id="a4022-126">xs:string</span></span>|<span data-ttu-id="a4022-127">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="a4022-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
