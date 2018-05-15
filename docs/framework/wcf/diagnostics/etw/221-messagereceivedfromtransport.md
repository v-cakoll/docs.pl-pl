---
title: 221 — MessageReceivedFromTransport
ms.date: 03/30/2017
ms.assetid: 4995f0d5-c182-4d97-981f-6951da6df1fb
ms.openlocfilehash: 98dbf2728242fa73b3e54b7cf32f9e227e5251b2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="221---messagereceivedfromtransport"></a><span data-ttu-id="ae96d-102">221 — MessageReceivedFromTransport</span><span class="sxs-lookup"><span data-stu-id="ae96d-102">221 - MessageReceivedFromTransport</span></span>
## <a name="properties"></a><span data-ttu-id="ae96d-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="ae96d-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ae96d-104">ID</span><span class="sxs-lookup"><span data-stu-id="ae96d-104">ID</span></span>|<span data-ttu-id="ae96d-105">221</span><span class="sxs-lookup"><span data-stu-id="ae96d-105">221</span></span>|  
|<span data-ttu-id="ae96d-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="ae96d-106">Keywords</span></span>|<span data-ttu-id="ae96d-107">EndToEndMonitoring rozwiązywania problemów, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="ae96d-107">EndToEndMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="ae96d-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="ae96d-108">Level</span></span>|<span data-ttu-id="ae96d-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="ae96d-109">Information</span></span>|  
|<span data-ttu-id="ae96d-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="ae96d-110">Channel</span></span>|<span data-ttu-id="ae96d-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="ae96d-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ae96d-112">Opis</span><span class="sxs-lookup"><span data-stu-id="ae96d-112">Description</span></span>  
 <span data-ttu-id="ae96d-113">To zdarzenie jest emitowany, gdy Model usługi otrzyma komunikat z transportu.</span><span class="sxs-lookup"><span data-stu-id="ae96d-113">This event is emitted when the Service Model receives a message from the transport.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ae96d-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="ae96d-114">Message</span></span>  
 <span data-ttu-id="ae96d-115">Dyspozytor odebrał wiadomość od transportu.</span><span class="sxs-lookup"><span data-stu-id="ae96d-115">The Dispatcher received a message from the transport.</span></span> <span data-ttu-id="ae96d-116">Identyfikator korelacji == "%1".</span><span class="sxs-lookup"><span data-stu-id="ae96d-116">Correlation ID == '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="ae96d-117">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="ae96d-117">Details</span></span>  
  
|<span data-ttu-id="ae96d-118">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="ae96d-118">Data Item Name</span></span>|<span data-ttu-id="ae96d-119">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="ae96d-119">Data Item Type</span></span>|<span data-ttu-id="ae96d-120">Opis</span><span class="sxs-lookup"><span data-stu-id="ae96d-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ae96d-121">Identyfikator korelacji</span><span class="sxs-lookup"><span data-stu-id="ae96d-121">Correlation ID</span></span>|`xs:GUID`|<span data-ttu-id="ae96d-122">Aktywności identyfikator używany do skorelowania `MessageSentToTransport` odpowiednie zdarzenia z usługi lub klienta `MessageReceivedFromTransport` w drugim zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="ae96d-122">The activity ID used to correlate a `MessageSentToTransport` event from a service or client to its corresponding `MessageReceivedFromTransport` on the other end.</span></span>|  
|<span data-ttu-id="ae96d-123">HostReference</span><span class="sxs-lookup"><span data-stu-id="ae96d-123">HostReference</span></span>|`xs:string`|<span data-ttu-id="ae96d-124">W przypadku usług hostowanych w sieci Web to pole unikatowo identyfikuje usługę w hierarchii sieci Web.</span><span class="sxs-lookup"><span data-stu-id="ae96d-124">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="ae96d-125">Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web&#124;ścieżki wirtualnej usługi&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="ae96d-125">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="ae96d-126">Przykład: "Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService".</span><span class="sxs-lookup"><span data-stu-id="ae96d-126">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="ae96d-127">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="ae96d-127">AppDomain</span></span>|`xs:string`|<span data-ttu-id="ae96d-128">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="ae96d-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
