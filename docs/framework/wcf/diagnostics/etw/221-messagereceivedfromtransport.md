---
title: "221 — MessageReceivedFromTransport"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4995f0d5-c182-4d97-981f-6951da6df1fb
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 139ca9e0fbe4d3f59d3d593f7785d5fb65e64702
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="221---messagereceivedfromtransport"></a><span data-ttu-id="fcfc0-102">221 — MessageReceivedFromTransport</span><span class="sxs-lookup"><span data-stu-id="fcfc0-102">221 - MessageReceivedFromTransport</span></span>
## <a name="properties"></a><span data-ttu-id="fcfc0-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="fcfc0-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="fcfc0-104">ID</span><span class="sxs-lookup"><span data-stu-id="fcfc0-104">ID</span></span>|<span data-ttu-id="fcfc0-105">221</span><span class="sxs-lookup"><span data-stu-id="fcfc0-105">221</span></span>|  
|<span data-ttu-id="fcfc0-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="fcfc0-106">Keywords</span></span>|<span data-ttu-id="fcfc0-107">EndToEndMonitoring rozwiązywania problemów, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="fcfc0-107">EndToEndMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="fcfc0-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="fcfc0-108">Level</span></span>|<span data-ttu-id="fcfc0-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="fcfc0-109">Information</span></span>|  
|<span data-ttu-id="fcfc0-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="fcfc0-110">Channel</span></span>|<span data-ttu-id="fcfc0-111">Microsoft-Windows aplikacji Server aplikacje/analityczne</span><span class="sxs-lookup"><span data-stu-id="fcfc0-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="fcfc0-112">Opis</span><span class="sxs-lookup"><span data-stu-id="fcfc0-112">Description</span></span>  
 <span data-ttu-id="fcfc0-113">To zdarzenie jest emitowany, gdy Model usługi otrzyma komunikat z transportu.</span><span class="sxs-lookup"><span data-stu-id="fcfc0-113">This event is emitted when the Service Model receives a message from the transport.</span></span>  
  
## <a name="message"></a><span data-ttu-id="fcfc0-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="fcfc0-114">Message</span></span>  
 <span data-ttu-id="fcfc0-115">Dyspozytor odebrał wiadomość od transportu.</span><span class="sxs-lookup"><span data-stu-id="fcfc0-115">The Dispatcher received a message from the transport.</span></span> <span data-ttu-id="fcfc0-116">Identyfikator korelacji == "%1".</span><span class="sxs-lookup"><span data-stu-id="fcfc0-116">Correlation ID == '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="fcfc0-117">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="fcfc0-117">Details</span></span>  
  
|<span data-ttu-id="fcfc0-118">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="fcfc0-118">Data Item Name</span></span>|<span data-ttu-id="fcfc0-119">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="fcfc0-119">Data Item Type</span></span>|<span data-ttu-id="fcfc0-120">Opis</span><span class="sxs-lookup"><span data-stu-id="fcfc0-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="fcfc0-121">Identyfikator korelacji</span><span class="sxs-lookup"><span data-stu-id="fcfc0-121">Correlation ID</span></span>|`xs:GUID`|<span data-ttu-id="fcfc0-122">Aktywności identyfikator używany do skorelowania `MessageSentToTransport` odpowiednie zdarzenia z usługi lub klienta `MessageReceivedFromTransport` w drugim zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="fcfc0-122">The activity ID used to correlate a `MessageSentToTransport` event from a service or client to its corresponding `MessageReceivedFromTransport` on the other end.</span></span>|  
|<span data-ttu-id="fcfc0-123">HostReference</span><span class="sxs-lookup"><span data-stu-id="fcfc0-123">HostReference</span></span>|`xs:string`|<span data-ttu-id="fcfc0-124">W przypadku usług hostowanych w sieci Web to pole unikatowo identyfikuje usługę w hierarchii sieci Web.</span><span class="sxs-lookup"><span data-stu-id="fcfc0-124">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="fcfc0-125">Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web &#124; Ścieżka wirtualna usługi &#124; ServiceName ".</span><span class="sxs-lookup"><span data-stu-id="fcfc0-125">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="fcfc0-126">Przykład: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService ".</span><span class="sxs-lookup"><span data-stu-id="fcfc0-126">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="fcfc0-127">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="fcfc0-127">AppDomain</span></span>|`xs:string`|<span data-ttu-id="fcfc0-128">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="fcfc0-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
