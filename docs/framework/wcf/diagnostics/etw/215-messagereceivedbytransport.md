---
title: 215 — MessageReceivedByTransport
ms.date: 03/30/2017
ms.assetid: bb32aa60-5207-4711-9f08-110e8ac327e5
ms.openlocfilehash: aa1ad30526aa65501e5d9875d3877631ca00879b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964184"
---
# <a name="215---messagereceivedbytransport"></a><span data-ttu-id="c8518-102">215 — MessageReceivedByTransport</span><span class="sxs-lookup"><span data-stu-id="c8518-102">215 - MessageReceivedByTransport</span></span>
## <a name="properties"></a><span data-ttu-id="c8518-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="c8518-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c8518-104">id</span><span class="sxs-lookup"><span data-stu-id="c8518-104">ID</span></span>|<span data-ttu-id="c8518-105">215</span><span class="sxs-lookup"><span data-stu-id="c8518-105">215</span></span>|  
|<span data-ttu-id="c8518-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="c8518-106">Keywords</span></span>|<span data-ttu-id="c8518-107">Rozwiązywanie problemów, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="c8518-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="c8518-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="c8518-108">Level</span></span>|<span data-ttu-id="c8518-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="c8518-109">Information</span></span>|  
|<span data-ttu-id="c8518-110">Ukierunkowan</span><span class="sxs-lookup"><span data-stu-id="c8518-110">Channel</span></span>|<span data-ttu-id="c8518-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="c8518-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c8518-112">Opis</span><span class="sxs-lookup"><span data-stu-id="c8518-112">Description</span></span>  
 <span data-ttu-id="c8518-113">To zdarzenie występuje, gdy transport oparty na protokole TCP odbierze komunikat.</span><span class="sxs-lookup"><span data-stu-id="c8518-113">This event occurs when a TCP-based transport receives a message.</span></span> <span data-ttu-id="c8518-114">Należy pamiętać, że na poziomie transportu wiele komunikatów może być wymienianych między klientami i usługami w ramach jednej operacji.</span><span class="sxs-lookup"><span data-stu-id="c8518-114">Note that at the transport level, multiple messages can be exchanged between clients and services for a single operation.</span></span> <span data-ttu-id="c8518-115">Może to być spowodowane zachowaniem infrastruktury, tym dobrym przykładem.</span><span class="sxs-lookup"><span data-stu-id="c8518-115">This can be due to infrastructure behavior, security is a good example.</span></span> <span data-ttu-id="c8518-116">W związku z tym liczba `MessageReceivedByTransport` wyemitowanych zdarzeń zależy od powiązania usługi i jego konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="c8518-116">Therefore, the number of `MessageReceivedByTransport` events that are emitted vary based on your service's binding and its configuration.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c8518-117">To zdarzenie nie jest emitowane w przypadku transportów jednokierunkowych.</span><span class="sxs-lookup"><span data-stu-id="c8518-117">This event is not emitted for one-way transports.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c8518-118">Message</span><span class="sxs-lookup"><span data-stu-id="c8518-118">Message</span></span>  
 <span data-ttu-id="c8518-119">Transport odebrał komunikat z '% 1 '.</span><span class="sxs-lookup"><span data-stu-id="c8518-119">The transport received a message from '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c8518-120">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="c8518-120">Details</span></span>  
  
|<span data-ttu-id="c8518-121">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="c8518-121">Data Item Name</span></span>|<span data-ttu-id="c8518-122">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="c8518-122">Data Item Type</span></span>|<span data-ttu-id="c8518-123">Opis</span><span class="sxs-lookup"><span data-stu-id="c8518-123">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c8518-124">Adres nasłuchiwania</span><span class="sxs-lookup"><span data-stu-id="c8518-124">Listen Address</span></span>|`xs:string`|<span data-ttu-id="c8518-125">Adres, który odebrał wiadomość.</span><span class="sxs-lookup"><span data-stu-id="c8518-125">The address that received the message.</span></span>|  
|<span data-ttu-id="c8518-126">HostReference</span><span class="sxs-lookup"><span data-stu-id="c8518-126">HostReference</span></span>|`xs:string`|<span data-ttu-id="c8518-127">W przypadku usług hostowanych w sieci Web to pole jednoznacznie identyfikuje usługę w hierarchii sieci Web.</span><span class="sxs-lookup"><span data-stu-id="c8518-127">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="c8518-128">Jego format jest zdefiniowany jako "Nazwa witryny sieci Web ścieżka wirtualna&#124;usługi ścieżki wirtualnej&#124;Service Path ServiceName".</span><span class="sxs-lookup"><span data-stu-id="c8518-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="c8518-129">Przykład: "Domyślna witryna sieci Web/&#124;CalculatorApplication&#124;/CalculatorService.svc CalculatorService".</span><span class="sxs-lookup"><span data-stu-id="c8518-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="c8518-130">Wywołując</span><span class="sxs-lookup"><span data-stu-id="c8518-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="c8518-131">Ciąg zwracany przez element AppDomain. CurrentDomain —. FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="c8518-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
