---
title: 216 — MessageSentByTransport
ms.date: 03/30/2017
ms.assetid: 150c3167-4154-4225-8d94-57cc94341233
ms.openlocfilehash: fa21568e4c8c38eefe359c417d47ec0a9d30a7c4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781813"
---
# <a name="216---messagesentbytransport"></a><span data-ttu-id="effd4-102">216 — MessageSentByTransport</span><span class="sxs-lookup"><span data-stu-id="effd4-102">216 - MessageSentByTransport</span></span>
## <a name="properties"></a><span data-ttu-id="effd4-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="effd4-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="effd4-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="effd4-104">ID</span></span>|<span data-ttu-id="effd4-105">216</span><span class="sxs-lookup"><span data-stu-id="effd4-105">216</span></span>|  
|<span data-ttu-id="effd4-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="effd4-106">Keywords</span></span>|<span data-ttu-id="effd4-107">Rozwiązywanie problemów, modelu ServiceModel</span><span class="sxs-lookup"><span data-stu-id="effd4-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="effd4-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="effd4-108">Level</span></span>|<span data-ttu-id="effd4-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="effd4-109">Information</span></span>|  
|<span data-ttu-id="effd4-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="effd4-110">Channel</span></span>|<span data-ttu-id="effd4-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="effd4-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="effd4-112">Opis</span><span class="sxs-lookup"><span data-stu-id="effd4-112">Description</span></span>  
 <span data-ttu-id="effd4-113">To zdarzenie występuje, gdy transport oparte na protokole TCP jest wysyłana wiadomość.</span><span class="sxs-lookup"><span data-stu-id="effd4-113">This event occurs when a TCP-based transport sends a message.</span></span> <span data-ttu-id="effd4-114">Należy pamiętać, że na poziomie transportu wiele wiadomości mogą być wymieniane między klientów i usług dla pojedynczej operacji.</span><span class="sxs-lookup"><span data-stu-id="effd4-114">Note that at the transport level multiple messages can be exchanged between clients and services for a single operation.</span></span> <span data-ttu-id="effd4-115">Może to być spowodowane zachowanie infrastruktury, zabezpieczeń, które są dobrym przykładem.</span><span class="sxs-lookup"><span data-stu-id="effd4-115">This may be due to infrastructure behavior, security being a good example.</span></span> <span data-ttu-id="effd4-116">W związku z tym, liczba **MessageSentByTransport** zdarzenia, które są emitowane różnią się zależnie od powiązania z usługą i jego konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="effd4-116">Therefore, the number of **MessageSentByTransport** events that are emitted vary based on your service's binding and its configuration.</span></span>  
  
## <a name="message"></a><span data-ttu-id="effd4-117">Komunikat</span><span class="sxs-lookup"><span data-stu-id="effd4-117">Message</span></span>  
 <span data-ttu-id="effd4-118">Transport wiadomości do "%1".</span><span class="sxs-lookup"><span data-stu-id="effd4-118">The transport sent a message to '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="effd4-119">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="effd4-119">Details</span></span>  
  
|<span data-ttu-id="effd4-120">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="effd4-120">Data Item Name</span></span>|<span data-ttu-id="effd4-121">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="effd4-121">Data Item Type</span></span>|<span data-ttu-id="effd4-122">Opis</span><span class="sxs-lookup"><span data-stu-id="effd4-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="effd4-123">DestinationAddress</span><span class="sxs-lookup"><span data-stu-id="effd4-123">DestinationAddress</span></span>|`xs:string`|<span data-ttu-id="effd4-124">Adres, na który wysłano komunikat żądania.</span><span class="sxs-lookup"><span data-stu-id="effd4-124">The address that the request message was sent to.</span></span>|  
|<span data-ttu-id="effd4-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="effd4-125">HostReference</span></span>|<span data-ttu-id="effd4-126">xs:String</span><span class="sxs-lookup"><span data-stu-id="effd4-126">xs:string</span></span>|<span data-ttu-id="effd4-127">W przypadku usług hostowanych w sieci Web to pole jednoznacznie identyfikuje usługę w hierarchii w sieci Web.</span><span class="sxs-lookup"><span data-stu-id="effd4-127">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="effd4-128">Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web&#124;ścieżka wirtualna usługi&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="effd4-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="effd4-129">Przykład: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="effd4-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="effd4-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="effd4-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="effd4-131">Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="effd4-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
