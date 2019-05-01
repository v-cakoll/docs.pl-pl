---
title: 221 — MessageReceivedFromTransport
ms.date: 03/30/2017
ms.assetid: 4995f0d5-c182-4d97-981f-6951da6df1fb
ms.openlocfilehash: 98dbf2728242fa73b3e54b7cf32f9e227e5251b2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781722"
---
# <a name="221---messagereceivedfromtransport"></a><span data-ttu-id="263cd-102">221 — MessageReceivedFromTransport</span><span class="sxs-lookup"><span data-stu-id="263cd-102">221 - MessageReceivedFromTransport</span></span>
## <a name="properties"></a><span data-ttu-id="263cd-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="263cd-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="263cd-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="263cd-104">ID</span></span>|<span data-ttu-id="263cd-105">221</span><span class="sxs-lookup"><span data-stu-id="263cd-105">221</span></span>|  
|<span data-ttu-id="263cd-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="263cd-106">Keywords</span></span>|<span data-ttu-id="263cd-107">EndToEndMonitoring, rozwiązywania problemów, modelu ServiceModel</span><span class="sxs-lookup"><span data-stu-id="263cd-107">EndToEndMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="263cd-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="263cd-108">Level</span></span>|<span data-ttu-id="263cd-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="263cd-109">Information</span></span>|  
|<span data-ttu-id="263cd-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="263cd-110">Channel</span></span>|<span data-ttu-id="263cd-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="263cd-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="263cd-112">Opis</span><span class="sxs-lookup"><span data-stu-id="263cd-112">Description</span></span>  
 <span data-ttu-id="263cd-113">To zdarzenie jest emitowane, gdy Model usług otrzymuje komunikat z transportu.</span><span class="sxs-lookup"><span data-stu-id="263cd-113">This event is emitted when the Service Model receives a message from the transport.</span></span>  
  
## <a name="message"></a><span data-ttu-id="263cd-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="263cd-114">Message</span></span>  
 <span data-ttu-id="263cd-115">Dyspozytor otrzymał komunikat z transportu.</span><span class="sxs-lookup"><span data-stu-id="263cd-115">The Dispatcher received a message from the transport.</span></span> <span data-ttu-id="263cd-116">Identyfikator korelacji == "%1".</span><span class="sxs-lookup"><span data-stu-id="263cd-116">Correlation ID == '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="263cd-117">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="263cd-117">Details</span></span>  
  
|<span data-ttu-id="263cd-118">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="263cd-118">Data Item Name</span></span>|<span data-ttu-id="263cd-119">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="263cd-119">Data Item Type</span></span>|<span data-ttu-id="263cd-120">Opis</span><span class="sxs-lookup"><span data-stu-id="263cd-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="263cd-121">Identyfikator korelacji</span><span class="sxs-lookup"><span data-stu-id="263cd-121">Correlation ID</span></span>|`xs:GUID`|<span data-ttu-id="263cd-122">Działanie identyfikator używany do skorelowania `MessageSentToTransport` zdarzenie z usługi lub klienta, aby odpowiadającymi mu dostawcami `MessageReceivedFromTransport` po drugiej stronie.</span><span class="sxs-lookup"><span data-stu-id="263cd-122">The activity ID used to correlate a `MessageSentToTransport` event from a service or client to its corresponding `MessageReceivedFromTransport` on the other end.</span></span>|  
|<span data-ttu-id="263cd-123">HostReference</span><span class="sxs-lookup"><span data-stu-id="263cd-123">HostReference</span></span>|`xs:string`|<span data-ttu-id="263cd-124">W przypadku usług hostowanych w sieci Web to pole jednoznacznie identyfikuje usługę w hierarchii w sieci Web.</span><span class="sxs-lookup"><span data-stu-id="263cd-124">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="263cd-125">Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web&#124;ścieżka wirtualna usługi&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="263cd-125">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="263cd-126">Przykład: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="263cd-126">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="263cd-127">AppDomain</span><span class="sxs-lookup"><span data-stu-id="263cd-127">AppDomain</span></span>|`xs:string`|<span data-ttu-id="263cd-128">Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="263cd-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
