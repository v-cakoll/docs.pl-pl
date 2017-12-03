---
title: "214 — OperationCompleted"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a6287eef-023f-4816-813c-1802c82366df
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 09a8dc1994da30c0f0c180640e3f66c8806e4528
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="214---operationcompleted"></a><span data-ttu-id="a7b97-102">214 — OperationCompleted</span><span class="sxs-lookup"><span data-stu-id="a7b97-102">214 - OperationCompleted</span></span>
## <a name="properties"></a><span data-ttu-id="a7b97-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="a7b97-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a7b97-104">ID</span><span class="sxs-lookup"><span data-stu-id="a7b97-104">ID</span></span>|<span data-ttu-id="a7b97-105">214</span><span class="sxs-lookup"><span data-stu-id="a7b97-105">214</span></span>|  
|<span data-ttu-id="a7b97-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="a7b97-106">Keywords</span></span>|<span data-ttu-id="a7b97-107">HealthMonitoring EndToEndMonitoring, rozwiązywania problemów, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="a7b97-107">HealthMonitoring, EndToEndMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="a7b97-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="a7b97-108">Level</span></span>|<span data-ttu-id="a7b97-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="a7b97-109">Information</span></span>|  
|<span data-ttu-id="a7b97-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="a7b97-110">Channel</span></span>|<span data-ttu-id="a7b97-111">Microsoft-Windows aplikacji Server aplikacje/analityczne</span><span class="sxs-lookup"><span data-stu-id="a7b97-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a7b97-112">Opis</span><span class="sxs-lookup"><span data-stu-id="a7b97-112">Description</span></span>  
 <span data-ttu-id="a7b97-113">To zdarzenie jest emitowany gdy domyślny Model usługi `OperationInvoker` zostało zakończone wywołanie do metody bez tej metody generowania wyjątku.</span><span class="sxs-lookup"><span data-stu-id="a7b97-113">This event is emitted when the Service Model's default `OperationInvoker` has completed a call to a method without that method throwing an exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="a7b97-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="a7b97-114">Message</span></span>  
 <span data-ttu-id="a7b97-115">Obiekt OperationInvoker ukończył wywołanie metody '%1'.</span><span class="sxs-lookup"><span data-stu-id="a7b97-115">An OperationInvoker completed the call to the '%1' method.</span></span> <span data-ttu-id="a7b97-116">Wywołanie metody trwało "%2" ms.</span><span class="sxs-lookup"><span data-stu-id="a7b97-116">The method call duration was '%2' ms.</span></span>  
  
## <a name="details"></a><span data-ttu-id="a7b97-117">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="a7b97-117">Details</span></span>  
  
|<span data-ttu-id="a7b97-118">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="a7b97-118">Data Item Name</span></span>|<span data-ttu-id="a7b97-119">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="a7b97-119">Data Item Type</span></span>|<span data-ttu-id="a7b97-120">Opis</span><span class="sxs-lookup"><span data-stu-id="a7b97-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="a7b97-121">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="a7b97-121">Method Name</span></span>|`xs:string`|<span data-ttu-id="a7b97-122">Nazwa metody, która została wywołana przez CLR `OperationInvoker`.</span><span class="sxs-lookup"><span data-stu-id="a7b97-122">The CLR name of the method that was invoked by the `OperationInvoker`.</span></span>|  
|<span data-ttu-id="a7b97-123">Czas trwania</span><span class="sxs-lookup"><span data-stu-id="a7b97-123">Duration</span></span>|`xs:long`|<span data-ttu-id="a7b97-124">Czas (w milisekundach), jaką trwało `OperationInvoker` można wywołać metody.</span><span class="sxs-lookup"><span data-stu-id="a7b97-124">The time, in milliseconds, that it took the `OperationInvoker` to invoke the method.</span></span>|  
|<span data-ttu-id="a7b97-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="a7b97-125">HostReference</span></span>|`xs:string`|<span data-ttu-id="a7b97-126">W przypadku usług hostowanych w sieci web to pole unikatowo identyfikuje usługę w hierarchii sieci Web.</span><span class="sxs-lookup"><span data-stu-id="a7b97-126">For web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="a7b97-127">Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web &#124; Ścieżka wirtualna usługi &#124; ServiceName ".</span><span class="sxs-lookup"><span data-stu-id="a7b97-127">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="a7b97-128">Przykład: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService ".</span><span class="sxs-lookup"><span data-stu-id="a7b97-128">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="a7b97-129">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="a7b97-129">AppDomain</span></span>|`xs:string`|<span data-ttu-id="a7b97-130">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="a7b97-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
