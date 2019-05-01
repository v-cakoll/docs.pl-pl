---
title: 215 — MessageReceivedByTransport
ms.date: 03/30/2017
ms.assetid: bb32aa60-5207-4711-9f08-110e8ac327e5
ms.openlocfilehash: a8ba90b88ef8dbe3c8651bc565da61aae16a0a4a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781839"
---
# <a name="215---messagereceivedbytransport"></a><span data-ttu-id="0c814-102">215 — MessageReceivedByTransport</span><span class="sxs-lookup"><span data-stu-id="0c814-102">215 - MessageReceivedByTransport</span></span>
## <a name="properties"></a><span data-ttu-id="0c814-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="0c814-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0c814-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="0c814-104">ID</span></span>|<span data-ttu-id="0c814-105">215</span><span class="sxs-lookup"><span data-stu-id="0c814-105">215</span></span>|  
|<span data-ttu-id="0c814-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="0c814-106">Keywords</span></span>|<span data-ttu-id="0c814-107">Rozwiązywanie problemów, modelu ServiceModel</span><span class="sxs-lookup"><span data-stu-id="0c814-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="0c814-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="0c814-108">Level</span></span>|<span data-ttu-id="0c814-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="0c814-109">Information</span></span>|  
|<span data-ttu-id="0c814-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="0c814-110">Channel</span></span>|<span data-ttu-id="0c814-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="0c814-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="0c814-112">Opis</span><span class="sxs-lookup"><span data-stu-id="0c814-112">Description</span></span>  
 <span data-ttu-id="0c814-113">To zdarzenie występuje, gdy transport oparte na protokole TCP odbiera komunikat.</span><span class="sxs-lookup"><span data-stu-id="0c814-113">This event occurs when a TCP-based transport receives a message.</span></span> <span data-ttu-id="0c814-114">Należy pamiętać, że na poziomie transportu, wiele wiadomości mogą być wymieniane między klientów i usług dla pojedynczej operacji.</span><span class="sxs-lookup"><span data-stu-id="0c814-114">Note that at the transport level, multiple messages can be exchanged between clients and services for a single operation.</span></span> <span data-ttu-id="0c814-115">Może to być spowodowane zachowanie infrastruktury, zabezpieczenia są dobrym przykładem.</span><span class="sxs-lookup"><span data-stu-id="0c814-115">This can be due to infrastructure behavior, security is a good example.</span></span> <span data-ttu-id="0c814-116">W związku z tym, liczba `MessageReceivedByTransport` zdarzenia, które są emitowane różnią się zależnie od powiązania z usługą i jego konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="0c814-116">Therefore, the number of `MessageReceivedByTransport` events that are emitted vary based on your service's binding and its configuration.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0c814-117">To zdarzenie nie jest emitowane dla transportów jednokierunkowe.</span><span class="sxs-lookup"><span data-stu-id="0c814-117">This event is not emitted for one-way transports.</span></span>  
  
## <a name="message"></a><span data-ttu-id="0c814-118">Komunikat</span><span class="sxs-lookup"><span data-stu-id="0c814-118">Message</span></span>  
 <span data-ttu-id="0c814-119">Transport otrzymał komunikat z "%1".</span><span class="sxs-lookup"><span data-stu-id="0c814-119">The transport received a message from '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="0c814-120">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="0c814-120">Details</span></span>  
  
|<span data-ttu-id="0c814-121">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="0c814-121">Data Item Name</span></span>|<span data-ttu-id="0c814-122">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="0c814-122">Data Item Type</span></span>|<span data-ttu-id="0c814-123">Opis</span><span class="sxs-lookup"><span data-stu-id="0c814-123">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="0c814-124">Adresu nasłuchiwania</span><span class="sxs-lookup"><span data-stu-id="0c814-124">Listen Address</span></span>|`xs:string`|<span data-ttu-id="0c814-125">Adres, który otrzymał komunikat.</span><span class="sxs-lookup"><span data-stu-id="0c814-125">The address that received the message.</span></span>|  
|<span data-ttu-id="0c814-126">HostReference</span><span class="sxs-lookup"><span data-stu-id="0c814-126">HostReference</span></span>|`xs:string`|<span data-ttu-id="0c814-127">W przypadku usług hostowanych w sieci Web to pole jednoznacznie identyfikuje usługę w hierarchii w sieci Web.</span><span class="sxs-lookup"><span data-stu-id="0c814-127">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="0c814-128">Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web&#124;ścieżka wirtualna usługi&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="0c814-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="0c814-129">Przykład: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="0c814-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="0c814-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="0c814-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="0c814-131">Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="0c814-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
