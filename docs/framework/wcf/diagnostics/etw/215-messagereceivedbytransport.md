---
title: "215 — MessageReceivedByTransport"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bb32aa60-5207-4711-9f08-110e8ac327e5
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8bf2336d1b5c9dda1dac2b38305d944a822bd253
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="215---messagereceivedbytransport"></a><span data-ttu-id="4c752-102">215 — MessageReceivedByTransport</span><span class="sxs-lookup"><span data-stu-id="4c752-102">215 - MessageReceivedByTransport</span></span>
## <a name="properties"></a><span data-ttu-id="4c752-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="4c752-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4c752-104">ID</span><span class="sxs-lookup"><span data-stu-id="4c752-104">ID</span></span>|<span data-ttu-id="4c752-105">215</span><span class="sxs-lookup"><span data-stu-id="4c752-105">215</span></span>|  
|<span data-ttu-id="4c752-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="4c752-106">Keywords</span></span>|<span data-ttu-id="4c752-107">Rozwiązywanie problemów, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="4c752-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="4c752-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="4c752-108">Level</span></span>|<span data-ttu-id="4c752-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="4c752-109">Information</span></span>|  
|<span data-ttu-id="4c752-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="4c752-110">Channel</span></span>|<span data-ttu-id="4c752-111">Microsoft-Windows aplikacji Server aplikacje/analityczne</span><span class="sxs-lookup"><span data-stu-id="4c752-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="4c752-112">Opis</span><span class="sxs-lookup"><span data-stu-id="4c752-112">Description</span></span>  
 <span data-ttu-id="4c752-113">To zdarzenie występuje, gdy transport opartych na protokole TCP odbiera komunikat.</span><span class="sxs-lookup"><span data-stu-id="4c752-113">This event occurs when a TCP-based transport receives a message.</span></span> <span data-ttu-id="4c752-114">Należy pamiętać, że na poziomie transportu, wiele komunikatów mogą być wymieniane między klienci i usługi dla jednej operacji.</span><span class="sxs-lookup"><span data-stu-id="4c752-114">Note that at the transport level, multiple messages can be exchanged between clients and services for a single operation.</span></span> <span data-ttu-id="4c752-115">Może to być spowodowane zachowanie infrastruktury, zabezpieczeń jest dobrym przykładem.</span><span class="sxs-lookup"><span data-stu-id="4c752-115">This can be due to infrastructure behavior, security is a good example.</span></span> <span data-ttu-id="4c752-116">W związku z tym numerem `MessageReceivedByTransport` zdarzenia, które są emitowane różnić w zależności od powiązanie z usługą i jego konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="4c752-116">Therefore, the number of `MessageReceivedByTransport` events that are emitted vary based on your service's binding and its configuration.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4c752-117">To zdarzenie nie jest emitowany dla transportów jednokierunkowe.</span><span class="sxs-lookup"><span data-stu-id="4c752-117">This event is not emitted for one-way transports.</span></span>  
  
## <a name="message"></a><span data-ttu-id="4c752-118">Komunikat</span><span class="sxs-lookup"><span data-stu-id="4c752-118">Message</span></span>  
 <span data-ttu-id="4c752-119">Transportu odebrała wiadomość od "%1".</span><span class="sxs-lookup"><span data-stu-id="4c752-119">The transport received a message from '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="4c752-120">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="4c752-120">Details</span></span>  
  
|<span data-ttu-id="4c752-121">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="4c752-121">Data Item Name</span></span>|<span data-ttu-id="4c752-122">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="4c752-122">Data Item Type</span></span>|<span data-ttu-id="4c752-123">Opis</span><span class="sxs-lookup"><span data-stu-id="4c752-123">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="4c752-124">Adres nasłuchiwania</span><span class="sxs-lookup"><span data-stu-id="4c752-124">Listen Address</span></span>|`xs:string`|<span data-ttu-id="4c752-125">Adres, który odebrał wiadomość.</span><span class="sxs-lookup"><span data-stu-id="4c752-125">The address that received the message.</span></span>|  
|<span data-ttu-id="4c752-126">HostReference</span><span class="sxs-lookup"><span data-stu-id="4c752-126">HostReference</span></span>|`xs:string`|<span data-ttu-id="4c752-127">W przypadku usług hostowanych w sieci Web to pole unikatowo identyfikuje usługę w hierarchii sieci Web.</span><span class="sxs-lookup"><span data-stu-id="4c752-127">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="4c752-128">Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web &#124; Ścieżka wirtualna usługi &#124; ServiceName ".</span><span class="sxs-lookup"><span data-stu-id="4c752-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="4c752-129">Przykład: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService ".</span><span class="sxs-lookup"><span data-stu-id="4c752-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="4c752-130">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="4c752-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="4c752-131">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="4c752-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
