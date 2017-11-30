---
title: "216 — MessageSentByTransport"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 150c3167-4154-4225-8d94-57cc94341233
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7b35f46ae7a214ab45e4062928de82c4da6541a1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="216---messagesentbytransport"></a><span data-ttu-id="27214-102">216 — MessageSentByTransport</span><span class="sxs-lookup"><span data-stu-id="27214-102">216 - MessageSentByTransport</span></span>
## <a name="properties"></a><span data-ttu-id="27214-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="27214-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="27214-104">ID</span><span class="sxs-lookup"><span data-stu-id="27214-104">ID</span></span>|<span data-ttu-id="27214-105">216</span><span class="sxs-lookup"><span data-stu-id="27214-105">216</span></span>|  
|<span data-ttu-id="27214-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="27214-106">Keywords</span></span>|<span data-ttu-id="27214-107">Rozwiązywanie problemów, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="27214-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="27214-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="27214-108">Level</span></span>|<span data-ttu-id="27214-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="27214-109">Information</span></span>|  
|<span data-ttu-id="27214-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="27214-110">Channel</span></span>|<span data-ttu-id="27214-111">Microsoft-Windows aplikacji Server aplikacje/analityczne</span><span class="sxs-lookup"><span data-stu-id="27214-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="27214-112">Opis</span><span class="sxs-lookup"><span data-stu-id="27214-112">Description</span></span>  
 <span data-ttu-id="27214-113">To zdarzenie występuje, gdy transport opartych na protokole TCP wysyła komunikat.</span><span class="sxs-lookup"><span data-stu-id="27214-113">This event occurs when a TCP-based transport sends a message.</span></span> <span data-ttu-id="27214-114">Należy pamiętać, że na poziomie transportu wiele komunikatów mogą być wymieniane między klienci i usługi dla jednej operacji.</span><span class="sxs-lookup"><span data-stu-id="27214-114">Note that at the transport level multiple messages can be exchanged between clients and services for a single operation.</span></span> <span data-ttu-id="27214-115">Może to być spowodowane zachowanie infrastruktury, zabezpieczeń są dobrym przykładem.</span><span class="sxs-lookup"><span data-stu-id="27214-115">This may be due to infrastructure behavior, security being a good example.</span></span> <span data-ttu-id="27214-116">W związku z tym numerem **MessageSentByTransport** zdarzenia, które są emitowane różnić w zależności od powiązanie z usługą i jego konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="27214-116">Therefore, the number of **MessageSentByTransport** events that are emitted vary based on your service's binding and its configuration.</span></span>  
  
## <a name="message"></a><span data-ttu-id="27214-117">Komunikat</span><span class="sxs-lookup"><span data-stu-id="27214-117">Message</span></span>  
 <span data-ttu-id="27214-118">Transportu wysłała wiadomość do "%1".</span><span class="sxs-lookup"><span data-stu-id="27214-118">The transport sent a message to '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="27214-119">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="27214-119">Details</span></span>  
  
|<span data-ttu-id="27214-120">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="27214-120">Data Item Name</span></span>|<span data-ttu-id="27214-121">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="27214-121">Data Item Type</span></span>|<span data-ttu-id="27214-122">Opis</span><span class="sxs-lookup"><span data-stu-id="27214-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="27214-123">DestinationAddress</span><span class="sxs-lookup"><span data-stu-id="27214-123">DestinationAddress</span></span>|`xs:string`|<span data-ttu-id="27214-124">Adres, którego wysłano komunikat żądania.</span><span class="sxs-lookup"><span data-stu-id="27214-124">The address that the request message was sent to.</span></span>|  
|<span data-ttu-id="27214-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="27214-125">HostReference</span></span>|<span data-ttu-id="27214-126">xs:String</span><span class="sxs-lookup"><span data-stu-id="27214-126">xs:string</span></span>|<span data-ttu-id="27214-127">W przypadku usług hostowanych w sieci Web to pole unikatowo identyfikuje usługę w hierarchii sieci Web.</span><span class="sxs-lookup"><span data-stu-id="27214-127">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="27214-128">Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web &#124; Ścieżka wirtualna usługi &#124; ServiceName ".</span><span class="sxs-lookup"><span data-stu-id="27214-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="27214-129">Przykład: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService ".</span><span class="sxs-lookup"><span data-stu-id="27214-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="27214-130">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="27214-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="27214-131">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="27214-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
