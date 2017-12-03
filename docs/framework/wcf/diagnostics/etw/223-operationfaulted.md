---
title: "223 — OperationFaulted"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2f7d89d7-3a6a-40fe-9610-5424eb6bbf61
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b0428d90135823761e7b8a12f560786e34e12734
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="223---operationfaulted"></a><span data-ttu-id="79c12-102">223 — OperationFaulted</span><span class="sxs-lookup"><span data-stu-id="79c12-102">223 - OperationFaulted</span></span>
## <a name="properties"></a><span data-ttu-id="79c12-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="79c12-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="79c12-104">ID</span><span class="sxs-lookup"><span data-stu-id="79c12-104">ID</span></span>|<span data-ttu-id="79c12-105">223</span><span class="sxs-lookup"><span data-stu-id="79c12-105">223</span></span>|  
|<span data-ttu-id="79c12-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="79c12-106">Keywords</span></span>|<span data-ttu-id="79c12-107">EndToEndMonitoring HealthMonitoring, rozwiązywania problemów, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="79c12-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="79c12-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="79c12-108">Level</span></span>|<span data-ttu-id="79c12-109">Ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="79c12-109">Warning</span></span>|  
|<span data-ttu-id="79c12-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="79c12-110">Channel</span></span>|<span data-ttu-id="79c12-111">Microsoft-Windows aplikacji Server aplikacje/analityczne</span><span class="sxs-lookup"><span data-stu-id="79c12-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="79c12-112">Opis</span><span class="sxs-lookup"><span data-stu-id="79c12-112">Description</span></span>  
 <span data-ttu-id="79c12-113">To zdarzenie jest emitowany gdy domyślny Model usługi `OperationInvoker` napotkał wyjątek pochodny `FaultException` podczas wywoływania metody.</span><span class="sxs-lookup"><span data-stu-id="79c12-113">This event is emitted when the Service Model's default `OperationInvoker` has encountered an exception deriving from `FaultException` while invoking its method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="79c12-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="79c12-114">Message</span></span>  
 <span data-ttu-id="79c12-115">Metoda "%1" spowodowała zgłoszenie wyjątku FaultException, gdy została wywołana przez obiekt OperationInvoker.</span><span class="sxs-lookup"><span data-stu-id="79c12-115">The '%1' method threw a FaultException when invoked by the OperationInvoker.</span></span> <span data-ttu-id="79c12-116">Wywołanie metody trwało "%2" ms.</span><span class="sxs-lookup"><span data-stu-id="79c12-116">The method call duration was '%2' ms.</span></span>  
  
## <a name="details"></a><span data-ttu-id="79c12-117">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="79c12-117">Details</span></span>  
  
|<span data-ttu-id="79c12-118">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="79c12-118">Data Item Name</span></span>|<span data-ttu-id="79c12-119">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="79c12-119">Data Item Type</span></span>|<span data-ttu-id="79c12-120">Opis</span><span class="sxs-lookup"><span data-stu-id="79c12-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="79c12-121">MethodName</span><span class="sxs-lookup"><span data-stu-id="79c12-121">MethodName</span></span>|`xs:string`|<span data-ttu-id="79c12-122">Nazwa metody, która została wywołana przez CLR `OperationInvoker`.</span><span class="sxs-lookup"><span data-stu-id="79c12-122">The CLR name of the method that was invoked by the `OperationInvoker`.</span></span>|  
|<span data-ttu-id="79c12-123">Czas trwania</span><span class="sxs-lookup"><span data-stu-id="79c12-123">Duration</span></span>|`xs:long`|<span data-ttu-id="79c12-124">Czas (w milisekundach), jaką trwało `OperationInvoker` można wywołać metody.</span><span class="sxs-lookup"><span data-stu-id="79c12-124">The time, in milliseconds, that it took the `OperationInvoker` to invoke the method.</span></span>|  
|<span data-ttu-id="79c12-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="79c12-125">HostReference</span></span>|`xs:string`|<span data-ttu-id="79c12-126">W przypadku usług hostowanych w sieci Web to pole unikatowo identyfikuje usługę w hierarchii sieci Web.</span><span class="sxs-lookup"><span data-stu-id="79c12-126">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="79c12-127">Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web &#124; Ścieżka wirtualna usługi &#124; ServiceName ".</span><span class="sxs-lookup"><span data-stu-id="79c12-127">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="79c12-128">Przykład: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService ".</span><span class="sxs-lookup"><span data-stu-id="79c12-128">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="79c12-129">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="79c12-129">AppDomain</span></span>|`xs:string`|<span data-ttu-id="79c12-130">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="79c12-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
