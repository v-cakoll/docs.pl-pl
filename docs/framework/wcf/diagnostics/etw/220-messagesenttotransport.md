---
title: 220 — MessageSentToTransport
ms.date: 03/30/2017
ms.assetid: aef4e781-240b-45bc-bff8-400053037e71
ms.openlocfilehash: 92ec664aead15470fbed576bf157d64d984ddebf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="220---messagesenttotransport"></a><span data-ttu-id="5a6b6-102">220 — MessageSentToTransport</span><span class="sxs-lookup"><span data-stu-id="5a6b6-102">220 - MessageSentToTransport</span></span>
## <a name="properties"></a><span data-ttu-id="5a6b6-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="5a6b6-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5a6b6-104">Id</span><span class="sxs-lookup"><span data-stu-id="5a6b6-104">Id</span></span>|<span data-ttu-id="5a6b6-105">220</span><span class="sxs-lookup"><span data-stu-id="5a6b6-105">220</span></span>|  
|<span data-ttu-id="5a6b6-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="5a6b6-106">Keywords</span></span>|<span data-ttu-id="5a6b6-107">EndToEndMonitoring rozwiązywania problemów, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="5a6b6-107">EndToEndMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="5a6b6-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="5a6b6-108">Level</span></span>|<span data-ttu-id="5a6b6-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="5a6b6-109">Information</span></span>|  
|<span data-ttu-id="5a6b6-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="5a6b6-110">Channel</span></span>|<span data-ttu-id="5a6b6-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="5a6b6-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="5a6b6-112">Opis</span><span class="sxs-lookup"><span data-stu-id="5a6b6-112">Description</span></span>  
 <span data-ttu-id="5a6b6-113">To zdarzenie jest emitowany, gdy Model usługi wysyła wiadomość do transportu.</span><span class="sxs-lookup"><span data-stu-id="5a6b6-113">This event is emitted when the Service Model sends a message to the transport.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5a6b6-114">To zdarzenie nie będzie emitowany dla transportów jednokierunkowe.</span><span class="sxs-lookup"><span data-stu-id="5a6b6-114">This event will not be emitted for one-way transports.</span></span>  
  
## <a name="message"></a><span data-ttu-id="5a6b6-115">Komunikat</span><span class="sxs-lookup"><span data-stu-id="5a6b6-115">Message</span></span>  
 <span data-ttu-id="5a6b6-116">Dyspozytor wysłał wiadomość do transportu.</span><span class="sxs-lookup"><span data-stu-id="5a6b6-116">The Dispatcher sent a message to the transport.</span></span> <span data-ttu-id="5a6b6-117">Identyfikator korelacji == "%1".</span><span class="sxs-lookup"><span data-stu-id="5a6b6-117">Correlation ID == '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="5a6b6-118">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="5a6b6-118">Details</span></span>  
  
|<span data-ttu-id="5a6b6-119">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="5a6b6-119">Data Item Name</span></span>|<span data-ttu-id="5a6b6-120">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="5a6b6-120">Data Item Type</span></span>|<span data-ttu-id="5a6b6-121">Opis</span><span class="sxs-lookup"><span data-stu-id="5a6b6-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="5a6b6-122">Identyfikator korelacji</span><span class="sxs-lookup"><span data-stu-id="5a6b6-122">Correlation ID</span></span>|`xs:GUID`|<span data-ttu-id="5a6b6-123">Aktywności identyfikator używany do skorelowania `MessageSentToTransport` odpowiednie zdarzenia z usługi lub klienta `MessageReceivedFromTransport` w drugim zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="5a6b6-123">The activity ID used to correlate a `MessageSentToTransport` event from a service or client to its corresponding `MessageReceivedFromTransport` on the other end.</span></span>|  
|<span data-ttu-id="5a6b6-124">HostReference</span><span class="sxs-lookup"><span data-stu-id="5a6b6-124">HostReference</span></span>|`xs:string`|<span data-ttu-id="5a6b6-125">W przypadku usług hostowanych w sieci Web to pole unikatowo identyfikuje usługę w hierarchii sieci Web.</span><span class="sxs-lookup"><span data-stu-id="5a6b6-125">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="5a6b6-126">Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web&#124;ścieżki wirtualnej usługi&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="5a6b6-126">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="5a6b6-127">Przykład: "Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService".</span><span class="sxs-lookup"><span data-stu-id="5a6b6-127">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="5a6b6-128">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="5a6b6-128">AppDomain</span></span>|`xs:string`|<span data-ttu-id="5a6b6-129">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="5a6b6-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
