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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 92880fd01f8f61a06c9b2c7d51ecc4a1671c6c85
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="215---messagereceivedbytransport"></a><span data-ttu-id="468a0-102">215 — MessageReceivedByTransport</span><span class="sxs-lookup"><span data-stu-id="468a0-102">215 - MessageReceivedByTransport</span></span>
## <a name="properties"></a><span data-ttu-id="468a0-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="468a0-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="468a0-104">ID</span><span class="sxs-lookup"><span data-stu-id="468a0-104">ID</span></span>|<span data-ttu-id="468a0-105">215</span><span class="sxs-lookup"><span data-stu-id="468a0-105">215</span></span>|  
|<span data-ttu-id="468a0-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="468a0-106">Keywords</span></span>|<span data-ttu-id="468a0-107">Rozwiązywanie problemów, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="468a0-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="468a0-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="468a0-108">Level</span></span>|<span data-ttu-id="468a0-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="468a0-109">Information</span></span>|  
|<span data-ttu-id="468a0-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="468a0-110">Channel</span></span>|<span data-ttu-id="468a0-111">Microsoft-Windows aplikacji Server aplikacje/analityczne</span><span class="sxs-lookup"><span data-stu-id="468a0-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="468a0-112">Opis</span><span class="sxs-lookup"><span data-stu-id="468a0-112">Description</span></span>  
 <span data-ttu-id="468a0-113">To zdarzenie występuje, gdy transport opartych na protokole TCP odbiera komunikat.</span><span class="sxs-lookup"><span data-stu-id="468a0-113">This event occurs when a TCP-based transport receives a message.</span></span> <span data-ttu-id="468a0-114">Należy pamiętać, że na poziomie transportu, wiele komunikatów mogą być wymieniane między klienci i usługi dla jednej operacji.</span><span class="sxs-lookup"><span data-stu-id="468a0-114">Note that at the transport level, multiple messages can be exchanged between clients and services for a single operation.</span></span> <span data-ttu-id="468a0-115">Może to być spowodowane zachowanie infrastruktury, zabezpieczeń jest dobrym przykładem.</span><span class="sxs-lookup"><span data-stu-id="468a0-115">This can be due to infrastructure behavior, security is a good example.</span></span> <span data-ttu-id="468a0-116">W związku z tym numerem `MessageReceivedByTransport` zdarzenia, które są emitowane różnić w zależności od powiązanie z usługą i jego konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="468a0-116">Therefore, the number of `MessageReceivedByTransport` events that are emitted vary based on your service's binding and its configuration.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="468a0-117">To zdarzenie nie jest emitowany dla transportów jednokierunkowe.</span><span class="sxs-lookup"><span data-stu-id="468a0-117">This event is not emitted for one-way transports.</span></span>  
  
## <a name="message"></a><span data-ttu-id="468a0-118">Komunikat</span><span class="sxs-lookup"><span data-stu-id="468a0-118">Message</span></span>  
 <span data-ttu-id="468a0-119">Transportu odebrała wiadomość od "%1".</span><span class="sxs-lookup"><span data-stu-id="468a0-119">The transport received a message from '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="468a0-120">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="468a0-120">Details</span></span>  
  
|<span data-ttu-id="468a0-121">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="468a0-121">Data Item Name</span></span>|<span data-ttu-id="468a0-122">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="468a0-122">Data Item Type</span></span>|<span data-ttu-id="468a0-123">Opis</span><span class="sxs-lookup"><span data-stu-id="468a0-123">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="468a0-124">Adres nasłuchiwania</span><span class="sxs-lookup"><span data-stu-id="468a0-124">Listen Address</span></span>|`xs:string`|<span data-ttu-id="468a0-125">Adres, który odebrał wiadomość.</span><span class="sxs-lookup"><span data-stu-id="468a0-125">The address that received the message.</span></span>|  
|<span data-ttu-id="468a0-126">HostReference</span><span class="sxs-lookup"><span data-stu-id="468a0-126">HostReference</span></span>|`xs:string`|<span data-ttu-id="468a0-127">W przypadku usług hostowanych w sieci Web to pole unikatowo identyfikuje usługę w hierarchii sieci Web.</span><span class="sxs-lookup"><span data-stu-id="468a0-127">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="468a0-128">Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web &#124; Ścieżka wirtualna usługi &#124; ServiceName ".</span><span class="sxs-lookup"><span data-stu-id="468a0-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="468a0-129">Przykład: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService ".</span><span class="sxs-lookup"><span data-stu-id="468a0-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="468a0-130">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="468a0-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="468a0-131">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="468a0-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
