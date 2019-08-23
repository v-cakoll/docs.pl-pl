---
title: 220 — MessageSentToTransport
ms.date: 03/30/2017
ms.assetid: aef4e781-240b-45bc-bff8-400053037e71
ms.openlocfilehash: 9f95edf42e0b1ec19d2019773def282fc279871b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69948280"
---
# <a name="220---messagesenttotransport"></a><span data-ttu-id="662d0-102">220 — MessageSentToTransport</span><span class="sxs-lookup"><span data-stu-id="662d0-102">220 - MessageSentToTransport</span></span>
## <a name="properties"></a><span data-ttu-id="662d0-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="662d0-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="662d0-104">Id</span><span class="sxs-lookup"><span data-stu-id="662d0-104">Id</span></span>|<span data-ttu-id="662d0-105">220</span><span class="sxs-lookup"><span data-stu-id="662d0-105">220</span></span>|  
|<span data-ttu-id="662d0-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="662d0-106">Keywords</span></span>|<span data-ttu-id="662d0-107">EndToEndMonitoring, rozwiązywanie problemów, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="662d0-107">EndToEndMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="662d0-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="662d0-108">Level</span></span>|<span data-ttu-id="662d0-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="662d0-109">Information</span></span>|  
|<span data-ttu-id="662d0-110">Ukierunkowan</span><span class="sxs-lookup"><span data-stu-id="662d0-110">Channel</span></span>|<span data-ttu-id="662d0-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="662d0-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="662d0-112">Opis</span><span class="sxs-lookup"><span data-stu-id="662d0-112">Description</span></span>  
 <span data-ttu-id="662d0-113">To zdarzenie jest emitowane, gdy model usługi wysyła komunikat do transportu.</span><span class="sxs-lookup"><span data-stu-id="662d0-113">This event is emitted when the Service Model sends a message to the transport.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="662d0-114">To zdarzenie nie będzie emitowane w przypadku transportów jednokierunkowych.</span><span class="sxs-lookup"><span data-stu-id="662d0-114">This event will not be emitted for one-way transports.</span></span>  
  
## <a name="message"></a><span data-ttu-id="662d0-115">Message</span><span class="sxs-lookup"><span data-stu-id="662d0-115">Message</span></span>  
 <span data-ttu-id="662d0-116">Dyspozytor wysłał komunikat do transportu.</span><span class="sxs-lookup"><span data-stu-id="662d0-116">The Dispatcher sent a message to the transport.</span></span> <span data-ttu-id="662d0-117">Identyfikator korelacji = = '% 1 '.</span><span class="sxs-lookup"><span data-stu-id="662d0-117">Correlation ID == '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="662d0-118">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="662d0-118">Details</span></span>  
  
|<span data-ttu-id="662d0-119">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="662d0-119">Data Item Name</span></span>|<span data-ttu-id="662d0-120">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="662d0-120">Data Item Type</span></span>|<span data-ttu-id="662d0-121">Opis</span><span class="sxs-lookup"><span data-stu-id="662d0-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="662d0-122">Identyfikator korelacji</span><span class="sxs-lookup"><span data-stu-id="662d0-122">Correlation ID</span></span>|`xs:GUID`|<span data-ttu-id="662d0-123">Identyfikator działania służący do skorelowania `MessageSentToTransport` zdarzenia z usługi lub klienta do jego odpowiadającego `MessageReceivedFromTransport` na drugim końcu.</span><span class="sxs-lookup"><span data-stu-id="662d0-123">The activity ID used to correlate a `MessageSentToTransport` event from a service or client to its corresponding `MessageReceivedFromTransport` on the other end.</span></span>|  
|<span data-ttu-id="662d0-124">HostReference</span><span class="sxs-lookup"><span data-stu-id="662d0-124">HostReference</span></span>|`xs:string`|<span data-ttu-id="662d0-125">W przypadku usług hostowanych w sieci Web to pole jednoznacznie identyfikuje usługę w hierarchii sieci Web.</span><span class="sxs-lookup"><span data-stu-id="662d0-125">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="662d0-126">Jego format jest zdefiniowany jako "Nazwa witryny sieci Web ścieżka wirtualna&#124;usługi ścieżki wirtualnej&#124;Service Path ServiceName".</span><span class="sxs-lookup"><span data-stu-id="662d0-126">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="662d0-127">Przykład: "Domyślna witryna sieci Web/&#124;CalculatorApplication&#124;/CalculatorService.svc CalculatorService".</span><span class="sxs-lookup"><span data-stu-id="662d0-127">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="662d0-128">Wywołując</span><span class="sxs-lookup"><span data-stu-id="662d0-128">AppDomain</span></span>|`xs:string`|<span data-ttu-id="662d0-129">Ciąg zwracany przez element AppDomain. CurrentDomain —. FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="662d0-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
