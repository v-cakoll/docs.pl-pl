---
title: "210 — MessageThrottleExceeded"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 24ca08ea-c11c-4753-946e-98aa820f8711
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 299cc11dc4f6794b65761ad7da71bcf062c318db
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="210---messagethrottleexceeded"></a><span data-ttu-id="b818e-102">210 — MessageThrottleExceeded</span><span class="sxs-lookup"><span data-stu-id="b818e-102">210 - MessageThrottleExceeded</span></span>
## <a name="properties"></a><span data-ttu-id="b818e-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="b818e-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b818e-104">ID</span><span class="sxs-lookup"><span data-stu-id="b818e-104">ID</span></span>|<span data-ttu-id="b818e-105">210</span><span class="sxs-lookup"><span data-stu-id="b818e-105">210</span></span>|  
|<span data-ttu-id="b818e-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="b818e-106">Keywords</span></span>|<span data-ttu-id="b818e-107">EndToEndMonitoring HealthMonitoring, rozwiązywania problemów, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="b818e-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="b818e-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="b818e-108">Level</span></span>|<span data-ttu-id="b818e-109">Ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="b818e-109">Warning</span></span>|  
|<span data-ttu-id="b818e-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="b818e-110">Channel</span></span>|<span data-ttu-id="b818e-111">Microsoft-Windows aplikacji Server aplikacje/analityczne</span><span class="sxs-lookup"><span data-stu-id="b818e-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b818e-112">Opis</span><span class="sxs-lookup"><span data-stu-id="b818e-112">Description</span></span>  
 <span data-ttu-id="b818e-113">To zdarzenie jest emitowany, gdy dla jednego z trzech głównych usługi zostały przekroczone limity.</span><span class="sxs-lookup"><span data-stu-id="b818e-113">This event is emitted when one of the three main service throttles have been exceeded.</span></span> <span data-ttu-id="b818e-114">Należy pamiętać, że to zdarzenie tylko wysyłanego początkowo przekroczenia limitu ograniczania przepustowości.</span><span class="sxs-lookup"><span data-stu-id="b818e-114">Note that this event is only emitted when the throttle limit is initially exceeded.</span></span> <span data-ttu-id="b818e-115">Na przykład, jeśli limit przepustnicy dla jednoczesnych wywołań jest 10, 11 równoczesnych wyniki wywołania `MessageThrottleExceeded` zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="b818e-115">For example, if the throttle limit for concurrent calls is 10, the 11th concurrent call results in a `MessageThrottleExceeded` event.</span></span> <span data-ttu-id="b818e-116">W innym przypadku nie powoduje wywołanie 12.</span><span class="sxs-lookup"><span data-stu-id="b818e-116">The 12th call does not result in another event.</span></span> <span data-ttu-id="b818e-117">Ponadto aby uniknąć strumienia zdarzeń zakłócenia, działanie, które znajduje się wokół limit nie powoduje inne zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="b818e-117">Additionally, to avoid a noisy event stream, activity that hovers around the limit does not result in another event.</span></span> <span data-ttu-id="b818e-118">W tym przykładzie Jeśli kilka wywołania zakończone następnie jest 9 współbieżnych wywołań.</span><span class="sxs-lookup"><span data-stu-id="b818e-118">In this example, if a couple of calls complete then there are 9 concurrent calls.</span></span> <span data-ttu-id="b818e-119">Jeśli następnie dwóch kolejnych wywołań wejść, bieżąca wartość jest ponownie 11.</span><span class="sxs-lookup"><span data-stu-id="b818e-119">If subsequently two more calls come in, the current value is again 11.</span></span> <span data-ttu-id="b818e-120">Nie powoduje to inne zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="b818e-120">This does not result in another event.</span></span> <span data-ttu-id="b818e-121">Gdy bieżąca wartość znajduje się do 70 procent limit przepustnicy zdarzenia jest emitowany wskazujący, że ma spowolnić działanie.</span><span class="sxs-lookup"><span data-stu-id="b818e-121">When the current value falls to 70 percent of the throttle limit a different event is emitted that indicates that the activity has slowed.</span></span> <span data-ttu-id="b818e-122">Przyszłe działania, która przekracza limit wyników w innym `MessageThrottleExceeded` zdarzenia, które są emitowane.</span><span class="sxs-lookup"><span data-stu-id="b818e-122">Future activity that exceeds the limit results in another `MessageThrottleExceeded` event being emitted.</span></span> <span data-ttu-id="b818e-123">W tym przykładzie, jeśli liczba równoczesnych wywołań spadnie do 7, a następnie ponownie osiągnie 11 i innego `MessageThrottleExceeded` jest emitowany zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="b818e-123">In this example, if the amount of concurrent calls falls to 7 and then again reaches 11 and another `MessageThrottleExceeded` event is emitted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b818e-124">Komunikat</span><span class="sxs-lookup"><span data-stu-id="b818e-124">Message</span></span>  
 <span data-ttu-id="b818e-125">Osiągnięto limit przepustnicy "%1" z "%2".</span><span class="sxs-lookup"><span data-stu-id="b818e-125">The '%1' throttle limit of '%2' was hit.</span></span>  
  
## <a name="details"></a><span data-ttu-id="b818e-126">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="b818e-126">Details</span></span>  
  
|<span data-ttu-id="b818e-127">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="b818e-127">Data Item Name</span></span>|<span data-ttu-id="b818e-128">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="b818e-128">Data Item Type</span></span>|<span data-ttu-id="b818e-129">Opis</span><span class="sxs-lookup"><span data-stu-id="b818e-129">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b818e-130">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="b818e-130">Throttle Name</span></span>|`xs:string`|<span data-ttu-id="b818e-131">Nazwa ograniczenia, który został przekroczony.</span><span class="sxs-lookup"><span data-stu-id="b818e-131">The name of the throttle that has been exceeded.</span></span> <span data-ttu-id="b818e-132">Albo `MaxConcurrentCalls`, `MaxConcurrentInstances`, lub `MaxConcurrentSessions`,</span><span class="sxs-lookup"><span data-stu-id="b818e-132">Either `MaxConcurrentCalls`, `MaxConcurrentInstances`, or `MaxConcurrentSessions`,</span></span>|  
|<span data-ttu-id="b818e-133">Limit</span><span class="sxs-lookup"><span data-stu-id="b818e-133">Limit</span></span>|`xs:long`|<span data-ttu-id="b818e-134">Aktualnie skonfigurowany limit przepustnicy.</span><span class="sxs-lookup"><span data-stu-id="b818e-134">The currently configured limit of the throttle.</span></span>|  
|<span data-ttu-id="b818e-135">HostReference</span><span class="sxs-lookup"><span data-stu-id="b818e-135">HostReference</span></span>|`xs:string`|<span data-ttu-id="b818e-136">W przypadku usług hostowanych w sieci Web to pole unikatowo identyfikuje usługę w hierarchii sieci Web.</span><span class="sxs-lookup"><span data-stu-id="b818e-136">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="b818e-137">Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web &#124; Ścieżka wirtualna usługi &#124; ServiceName ".</span><span class="sxs-lookup"><span data-stu-id="b818e-137">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="b818e-138">Przykład: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService ".</span><span class="sxs-lookup"><span data-stu-id="b818e-138">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="b818e-139">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="b818e-139">AppDomain</span></span>|`xs:string`|<span data-ttu-id="b818e-140">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="b818e-140">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
