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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e2f96aea0df629c24eb9d795a4409cae6a9c9aa9
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="224---messagethrottleatseventypercent"></a><span data-ttu-id="185a0-102">224 — MessageThrottleAtSeventyPercent</span><span class="sxs-lookup"><span data-stu-id="185a0-102">224 - MessageThrottleAtSeventyPercent</span></span>
## <a name="properties"></a><span data-ttu-id="185a0-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="185a0-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="185a0-104">ID</span><span class="sxs-lookup"><span data-stu-id="185a0-104">ID</span></span>|<span data-ttu-id="185a0-105">224</span><span class="sxs-lookup"><span data-stu-id="185a0-105">224</span></span>|  
|<span data-ttu-id="185a0-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="185a0-106">Keywords</span></span>|<span data-ttu-id="185a0-107">EndToEndMonitoring HealthMonitoring, rozwiązywania problemów, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="185a0-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="185a0-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="185a0-108">Level</span></span>|<span data-ttu-id="185a0-109">Ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="185a0-109">Warning</span></span>|  
|<span data-ttu-id="185a0-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="185a0-110">Channel</span></span>|<span data-ttu-id="185a0-111">Microsoft-Windows aplikacji Server aplikacje/analityczne</span><span class="sxs-lookup"><span data-stu-id="185a0-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="185a0-112">Opis</span><span class="sxs-lookup"><span data-stu-id="185a0-112">Description</span></span>  
 <span data-ttu-id="185a0-113">Gdy jeden z głównej usługi limity został przekroczony, `MessageThrottleExceeded` jest emitowany zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="185a0-113">When one of the main service throttles has been exceeded, the `MessageThrottleExceeded` event is emitted.</span></span> <span data-ttu-id="185a0-114">Gdy spowalnia kolekcji działania i bieżącą wartość przepustnicy wynosi 70 procent bieżący limit następnie to zdarzenie jest emitowany.</span><span class="sxs-lookup"><span data-stu-id="185a0-114">When the spike of activity slows and the current value of the throttle is at 70 percent of the current limit then this event is emitted.</span></span> <span data-ttu-id="185a0-115">Należy pamiętać, że to zdarzenie tylko wysyłanego po jako działanie spowalnia.</span><span class="sxs-lookup"><span data-stu-id="185a0-115">Note that this event is only emitted once as the activity is slowing.</span></span> <span data-ttu-id="185a0-116">Jeśli bieżąca wartość wskaźnika myszy na znak 70 procent, (na przykład 70,69,70,71,70,69), tylko pierwsze wystąpienie 70 procent powoduje zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="185a0-116">If the current value hovers at the 70 percent mark, (for example, 70,69,70,71,70,69), only the first occurrence of 70 percent results in an event.</span></span> <span data-ttu-id="185a0-117">Po to zdarzenie jest emitowany, przyszłych wystąpień przekroczenia ograniczania limit wyników w `MessageThrottleExceeded` zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="185a0-117">After this event is emitted, future occurrences of exceeding the throttle's limit result in a `MessageThrottleExceeded` event.</span></span>  
  
## <a name="message"></a><span data-ttu-id="185a0-118">Komunikat</span><span class="sxs-lookup"><span data-stu-id="185a0-118">Message</span></span>  
 <span data-ttu-id="185a0-119">Limit przepustnicy "%1" z "%2" ma wartość 70 %%.</span><span class="sxs-lookup"><span data-stu-id="185a0-119">The '%1' throttle limit of '%2' is at 70%%.</span></span>  
  
## <a name="details"></a><span data-ttu-id="185a0-120">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="185a0-120">Details</span></span>  
  
|<span data-ttu-id="185a0-121">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="185a0-121">Data Item Name</span></span>|<span data-ttu-id="185a0-122">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="185a0-122">Data Item Type</span></span>|<span data-ttu-id="185a0-123">Opis</span><span class="sxs-lookup"><span data-stu-id="185a0-123">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="185a0-124">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="185a0-124">Throttle Name</span></span>|`xs:string`|<span data-ttu-id="185a0-125">Nazwa ograniczenia, który został przekroczony.</span><span class="sxs-lookup"><span data-stu-id="185a0-125">The name of the throttle that has been exceeded.</span></span> <span data-ttu-id="185a0-126">Albo `MaxConcurrentCalls`, `MaxConcurrentInstances`, lub `MaxConcurrentSessions`,</span><span class="sxs-lookup"><span data-stu-id="185a0-126">Either `MaxConcurrentCalls`, `MaxConcurrentInstances`, or `MaxConcurrentSessions`,</span></span>|  
|<span data-ttu-id="185a0-127">Limit</span><span class="sxs-lookup"><span data-stu-id="185a0-127">Limit</span></span>|`xs:long`|<span data-ttu-id="185a0-128">Aktualnie skonfigurowany limit przepustnicy.</span><span class="sxs-lookup"><span data-stu-id="185a0-128">The currently configured limit of the throttle.</span></span>|  
|<span data-ttu-id="185a0-129">HostReference</span><span class="sxs-lookup"><span data-stu-id="185a0-129">HostReference</span></span>|`xs:string`|<span data-ttu-id="185a0-130">W przypadku usług hostowanych w sieci Web to pole unikatowo identyfikuje usługę w hierarchii sieci Web.</span><span class="sxs-lookup"><span data-stu-id="185a0-130">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="185a0-131">Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web &#124; Ścieżka wirtualna usługi &#124; ServiceName ".</span><span class="sxs-lookup"><span data-stu-id="185a0-131">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="185a0-132">Przykład: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService ".</span><span class="sxs-lookup"><span data-stu-id="185a0-132">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="185a0-133">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="185a0-133">AppDomain</span></span>|`xs:string`|<span data-ttu-id="185a0-134">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="185a0-134">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
