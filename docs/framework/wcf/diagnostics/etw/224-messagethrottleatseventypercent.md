---
title: "224 — MessageThrottleAtSeventyPercent"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 82bbbfd7-10d2-41fd-805d-2443b0c1b96b
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0dd985e3986548938f06e86c1f49d23c43307d17
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="224---messagethrottleatseventypercent"></a><span data-ttu-id="79ac2-102">224 — MessageThrottleAtSeventyPercent</span><span class="sxs-lookup"><span data-stu-id="79ac2-102">224 - MessageThrottleAtSeventyPercent</span></span>
## <a name="properties"></a><span data-ttu-id="79ac2-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="79ac2-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="79ac2-104">ID</span><span class="sxs-lookup"><span data-stu-id="79ac2-104">ID</span></span>|<span data-ttu-id="79ac2-105">224</span><span class="sxs-lookup"><span data-stu-id="79ac2-105">224</span></span>|  
|<span data-ttu-id="79ac2-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="79ac2-106">Keywords</span></span>|<span data-ttu-id="79ac2-107">EndToEndMonitoring HealthMonitoring, rozwiązywania problemów, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="79ac2-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="79ac2-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="79ac2-108">Level</span></span>|<span data-ttu-id="79ac2-109">Ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="79ac2-109">Warning</span></span>|  
|<span data-ttu-id="79ac2-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="79ac2-110">Channel</span></span>|<span data-ttu-id="79ac2-111">Microsoft-Windows aplikacji Server aplikacje/analityczne</span><span class="sxs-lookup"><span data-stu-id="79ac2-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="79ac2-112">Opis</span><span class="sxs-lookup"><span data-stu-id="79ac2-112">Description</span></span>  
 <span data-ttu-id="79ac2-113">Gdy jeden z głównej usługi limity został przekroczony, `MessageThrottleExceeded` jest emitowany zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="79ac2-113">When one of the main service throttles has been exceeded, the `MessageThrottleExceeded` event is emitted.</span></span> <span data-ttu-id="79ac2-114">Gdy spowalnia kolekcji działania i bieżącą wartość przepustnicy wynosi 70 procent bieżący limit następnie to zdarzenie jest emitowany.</span><span class="sxs-lookup"><span data-stu-id="79ac2-114">When the spike of activity slows and the current value of the throttle is at 70 percent of the current limit then this event is emitted.</span></span> <span data-ttu-id="79ac2-115">Należy pamiętać, że to zdarzenie tylko wysyłanego po jako działanie spowalnia.</span><span class="sxs-lookup"><span data-stu-id="79ac2-115">Note that this event is only emitted once as the activity is slowing.</span></span> <span data-ttu-id="79ac2-116">Jeśli bieżąca wartość wskaźnika myszy na znak 70 procent, (na przykład 70,69,70,71,70,69), tylko pierwsze wystąpienie 70 procent powoduje zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="79ac2-116">If the current value hovers at the 70 percent mark, (for example, 70,69,70,71,70,69), only the first occurrence of 70 percent results in an event.</span></span> <span data-ttu-id="79ac2-117">Po to zdarzenie jest emitowany, przyszłych wystąpień przekroczenia ograniczania limit wyników w `MessageThrottleExceeded` zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="79ac2-117">After this event is emitted, future occurrences of exceeding the throttle's limit result in a `MessageThrottleExceeded` event.</span></span>  
  
## <a name="message"></a><span data-ttu-id="79ac2-118">Komunikat</span><span class="sxs-lookup"><span data-stu-id="79ac2-118">Message</span></span>  
 <span data-ttu-id="79ac2-119">Limit przepustnicy "%1" z "%2" ma wartość 70 %%.</span><span class="sxs-lookup"><span data-stu-id="79ac2-119">The '%1' throttle limit of '%2' is at 70%%.</span></span>  
  
## <a name="details"></a><span data-ttu-id="79ac2-120">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="79ac2-120">Details</span></span>  
  
|<span data-ttu-id="79ac2-121">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="79ac2-121">Data Item Name</span></span>|<span data-ttu-id="79ac2-122">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="79ac2-122">Data Item Type</span></span>|<span data-ttu-id="79ac2-123">Opis</span><span class="sxs-lookup"><span data-stu-id="79ac2-123">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="79ac2-124">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="79ac2-124">Throttle Name</span></span>|`xs:string`|<span data-ttu-id="79ac2-125">Nazwa ograniczenia, który został przekroczony.</span><span class="sxs-lookup"><span data-stu-id="79ac2-125">The name of the throttle that has been exceeded.</span></span> <span data-ttu-id="79ac2-126">Albo `MaxConcurrentCalls`, `MaxConcurrentInstances`, lub `MaxConcurrentSessions`,</span><span class="sxs-lookup"><span data-stu-id="79ac2-126">Either `MaxConcurrentCalls`, `MaxConcurrentInstances`, or `MaxConcurrentSessions`,</span></span>|  
|<span data-ttu-id="79ac2-127">Limit</span><span class="sxs-lookup"><span data-stu-id="79ac2-127">Limit</span></span>|`xs:long`|<span data-ttu-id="79ac2-128">Aktualnie skonfigurowany limit przepustnicy.</span><span class="sxs-lookup"><span data-stu-id="79ac2-128">The currently configured limit of the throttle.</span></span>|  
|<span data-ttu-id="79ac2-129">HostReference</span><span class="sxs-lookup"><span data-stu-id="79ac2-129">HostReference</span></span>|`xs:string`|<span data-ttu-id="79ac2-130">W przypadku usług hostowanych w sieci Web to pole unikatowo identyfikuje usługę w hierarchii sieci Web.</span><span class="sxs-lookup"><span data-stu-id="79ac2-130">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="79ac2-131">Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web &#124; Ścieżka wirtualna usługi &#124; ServiceName ".</span><span class="sxs-lookup"><span data-stu-id="79ac2-131">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="79ac2-132">Przykład: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService ".</span><span class="sxs-lookup"><span data-stu-id="79ac2-132">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="79ac2-133">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="79ac2-133">AppDomain</span></span>|`xs:string`|<span data-ttu-id="79ac2-134">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="79ac2-134">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
