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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c6ef1eb398a0146e619cbcb85fe2761306aba4fc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="214---operationcompleted"></a><span data-ttu-id="e9c95-102">214 — OperationCompleted</span><span class="sxs-lookup"><span data-stu-id="e9c95-102">214 - OperationCompleted</span></span>
## <a name="properties"></a><span data-ttu-id="e9c95-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="e9c95-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e9c95-104">ID</span><span class="sxs-lookup"><span data-stu-id="e9c95-104">ID</span></span>|<span data-ttu-id="e9c95-105">214</span><span class="sxs-lookup"><span data-stu-id="e9c95-105">214</span></span>|  
|<span data-ttu-id="e9c95-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="e9c95-106">Keywords</span></span>|<span data-ttu-id="e9c95-107">HealthMonitoring EndToEndMonitoring, rozwiązywania problemów, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="e9c95-107">HealthMonitoring, EndToEndMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="e9c95-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="e9c95-108">Level</span></span>|<span data-ttu-id="e9c95-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="e9c95-109">Information</span></span>|  
|<span data-ttu-id="e9c95-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="e9c95-110">Channel</span></span>|<span data-ttu-id="e9c95-111">Microsoft-Windows aplikacji Server aplikacje/analityczne</span><span class="sxs-lookup"><span data-stu-id="e9c95-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e9c95-112">Opis</span><span class="sxs-lookup"><span data-stu-id="e9c95-112">Description</span></span>  
 <span data-ttu-id="e9c95-113">To zdarzenie jest emitowany gdy domyślny Model usługi `OperationInvoker` zostało zakończone wywołanie do metody bez tej metody generowania wyjątku.</span><span class="sxs-lookup"><span data-stu-id="e9c95-113">This event is emitted when the Service Model's default `OperationInvoker` has completed a call to a method without that method throwing an exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e9c95-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="e9c95-114">Message</span></span>  
 <span data-ttu-id="e9c95-115">Obiekt OperationInvoker ukończył wywołanie metody '%1'.</span><span class="sxs-lookup"><span data-stu-id="e9c95-115">An OperationInvoker completed the call to the '%1' method.</span></span> <span data-ttu-id="e9c95-116">Wywołanie metody trwało "%2" ms.</span><span class="sxs-lookup"><span data-stu-id="e9c95-116">The method call duration was '%2' ms.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e9c95-117">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="e9c95-117">Details</span></span>  
  
|<span data-ttu-id="e9c95-118">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="e9c95-118">Data Item Name</span></span>|<span data-ttu-id="e9c95-119">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="e9c95-119">Data Item Type</span></span>|<span data-ttu-id="e9c95-120">Opis</span><span class="sxs-lookup"><span data-stu-id="e9c95-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e9c95-121">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="e9c95-121">Method Name</span></span>|`xs:string`|<span data-ttu-id="e9c95-122">Nazwa metody, która została wywołana przez CLR `OperationInvoker`.</span><span class="sxs-lookup"><span data-stu-id="e9c95-122">The CLR name of the method that was invoked by the `OperationInvoker`.</span></span>|  
|<span data-ttu-id="e9c95-123">Czas trwania</span><span class="sxs-lookup"><span data-stu-id="e9c95-123">Duration</span></span>|`xs:long`|<span data-ttu-id="e9c95-124">Czas (w milisekundach), jaką trwało `OperationInvoker` można wywołać metody.</span><span class="sxs-lookup"><span data-stu-id="e9c95-124">The time, in milliseconds, that it took the `OperationInvoker` to invoke the method.</span></span>|  
|<span data-ttu-id="e9c95-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="e9c95-125">HostReference</span></span>|`xs:string`|<span data-ttu-id="e9c95-126">W przypadku usług hostowanych w sieci web to pole unikatowo identyfikuje usługę w hierarchii sieci Web.</span><span class="sxs-lookup"><span data-stu-id="e9c95-126">For web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="e9c95-127">Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web &#124; Ścieżka wirtualna usługi &#124; ServiceName ".</span><span class="sxs-lookup"><span data-stu-id="e9c95-127">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="e9c95-128">Przykład: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService ".</span><span class="sxs-lookup"><span data-stu-id="e9c95-128">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="e9c95-129">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="e9c95-129">AppDomain</span></span>|`xs:string`|<span data-ttu-id="e9c95-130">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="e9c95-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
