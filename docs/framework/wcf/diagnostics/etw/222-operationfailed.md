---
title: "222 — OperationFailed"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6b530ded-8f20-4d78-8bfe-1875276df6ba
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5d56766dd32acf1ef71f7c06a5c3c94cc7510070
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="222---operationfailed"></a><span data-ttu-id="362d0-102">222 — OperationFailed</span><span class="sxs-lookup"><span data-stu-id="362d0-102">222 - OperationFailed</span></span>
## <a name="properties"></a><span data-ttu-id="362d0-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="362d0-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="362d0-104">ID</span><span class="sxs-lookup"><span data-stu-id="362d0-104">ID</span></span>|<span data-ttu-id="362d0-105">222</span><span class="sxs-lookup"><span data-stu-id="362d0-105">222</span></span>|  
|<span data-ttu-id="362d0-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="362d0-106">Keywords</span></span>|<span data-ttu-id="362d0-107">EndToEndMonitoring HealthMonitoring, rozwiązywania problemów, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="362d0-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="362d0-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="362d0-108">Level</span></span>|<span data-ttu-id="362d0-109">Ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="362d0-109">Warning</span></span>|  
|<span data-ttu-id="362d0-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="362d0-110">Channel</span></span>|<span data-ttu-id="362d0-111">Microsoft-Windows aplikacji Server aplikacje/analityczne</span><span class="sxs-lookup"><span data-stu-id="362d0-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="362d0-112">Opis</span><span class="sxs-lookup"><span data-stu-id="362d0-112">Description</span></span>  
 <span data-ttu-id="362d0-113">To zdarzenie jest emitowany gdy domyślny Model usługi `OperationInvoker` napotkał wyjątek podczas wywoływania metody.</span><span class="sxs-lookup"><span data-stu-id="362d0-113">This event is emitted when the Service Model's default `OperationInvoker` has encountered an exception while invoking its method.</span></span> <span data-ttu-id="362d0-114">Uwaga tego wyjątki pochodzące z `FaultException` spowodować to zdarzenie nie być emitowane.</span><span class="sxs-lookup"><span data-stu-id="362d0-114">Note that exceptions that derive from `FaultException` cause this event to not be emitted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="362d0-115">Komunikat</span><span class="sxs-lookup"><span data-stu-id="362d0-115">Message</span></span>  
 <span data-ttu-id="362d0-116">Metoda "%1" spowodowała zgłoszenie nieobsługiwanego wyjątku, gdy została wywołana przez obiekt OperationInvoker.</span><span class="sxs-lookup"><span data-stu-id="362d0-116">The '%1' method threw an unhandled exception when invoked by the OperationInvoker.</span></span> <span data-ttu-id="362d0-117">Wywołanie metody trwało "%2" ms.</span><span class="sxs-lookup"><span data-stu-id="362d0-117">The method call duration was '%2' ms.</span></span>  
  
## <a name="details"></a><span data-ttu-id="362d0-118">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="362d0-118">Details</span></span>  
  
|<span data-ttu-id="362d0-119">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="362d0-119">Data Item Name</span></span>|<span data-ttu-id="362d0-120">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="362d0-120">Data Item Type</span></span>|<span data-ttu-id="362d0-121">Opis</span><span class="sxs-lookup"><span data-stu-id="362d0-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="362d0-122">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="362d0-122">Method Name</span></span>|`xs:string`|<span data-ttu-id="362d0-123">Nazwa metody, która została wywołana przez CLR `OperationInvoker`.</span><span class="sxs-lookup"><span data-stu-id="362d0-123">The CLR name of the method that was invoked by the `OperationInvoker`.</span></span>|  
|<span data-ttu-id="362d0-124">Czas trwania</span><span class="sxs-lookup"><span data-stu-id="362d0-124">Duration</span></span>|`xs:long`|<span data-ttu-id="362d0-125">Czas (w milisekundach), jaką trwało `OperationInvoker` można wywołać metody.</span><span class="sxs-lookup"><span data-stu-id="362d0-125">The time, in milliseconds, that it took the `OperationInvoker` to invoke the method.</span></span>|  
|<span data-ttu-id="362d0-126">HostReference</span><span class="sxs-lookup"><span data-stu-id="362d0-126">HostReference</span></span>|`xs:string`|<span data-ttu-id="362d0-127">W przypadku usług hostowanych w sieci Web to pole unikatowo identyfikuje usługę w hierarchii sieci Web.</span><span class="sxs-lookup"><span data-stu-id="362d0-127">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="362d0-128">Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web &#124; Ścieżka wirtualna usługi &#124; ServiceName ".</span><span class="sxs-lookup"><span data-stu-id="362d0-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="362d0-129">Przykład: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService ".</span><span class="sxs-lookup"><span data-stu-id="362d0-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="362d0-130">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="362d0-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="362d0-131">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="362d0-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
