---
title: "499 — TransferEmitted"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 07a26434-a7a0-40fc-b5d0-3520a04328ae
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b1034ae6bd6072a3849d72fafcad55c61e500439
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="499---transferemitted"></a><span data-ttu-id="248ca-102">499 — TransferEmitted</span><span class="sxs-lookup"><span data-stu-id="248ca-102">499 - TransferEmitted</span></span>
## <a name="properties"></a><span data-ttu-id="248ca-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="248ca-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="248ca-104">ID</span><span class="sxs-lookup"><span data-stu-id="248ca-104">ID</span></span>|<span data-ttu-id="248ca-105">499</span><span class="sxs-lookup"><span data-stu-id="248ca-105">499</span></span>|  
|<span data-ttu-id="248ca-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="248ca-106">Keywords</span></span>|<span data-ttu-id="248ca-107">Rozwiązywanie problemów, UserEvents, EndToEndMonitoring, ServiceModel, WFTracking ServiceHost, WCFMessageLogging</span><span class="sxs-lookup"><span data-stu-id="248ca-107">Troubleshooting, UserEvents, EndToEndMonitoring, ServiceModel, WFTracking, ServiceHost, WCFMessageLogging</span></span>|  
|<span data-ttu-id="248ca-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="248ca-108">Level</span></span>|<span data-ttu-id="248ca-109">LogAlways</span><span class="sxs-lookup"><span data-stu-id="248ca-109">LogAlways</span></span>|  
|<span data-ttu-id="248ca-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="248ca-110">Channel</span></span>|<span data-ttu-id="248ca-111">Microsoft-Windows aplikacji Server aplikacje/analityczne</span><span class="sxs-lookup"><span data-stu-id="248ca-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="248ca-112">Opis</span><span class="sxs-lookup"><span data-stu-id="248ca-112">Description</span></span>  
 <span data-ttu-id="248ca-113">To zdarzenie jest emitowany po wystąpieniu zdarzenia transferu.</span><span class="sxs-lookup"><span data-stu-id="248ca-113">This event is emitted when the transfer event takes place.</span></span>  
  
## <a name="message"></a><span data-ttu-id="248ca-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="248ca-114">Message</span></span>  
 <span data-ttu-id="248ca-115">Zdarzenia transferu wysyłanego.</span><span class="sxs-lookup"><span data-stu-id="248ca-115">Transfer event emitted.</span></span>  
  
## <a name="details"></a><span data-ttu-id="248ca-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="248ca-116">Details</span></span>  
  
|<span data-ttu-id="248ca-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="248ca-117">Data Item Name</span></span>|<span data-ttu-id="248ca-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="248ca-118">Data Item Type</span></span>|<span data-ttu-id="248ca-119">Opis</span><span class="sxs-lookup"><span data-stu-id="248ca-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="248ca-120">HostReference</span><span class="sxs-lookup"><span data-stu-id="248ca-120">HostReference</span></span>|`xs:string`|<span data-ttu-id="248ca-121">W przypadku usług hostowanych w sieci Web to pole unikatowo identyfikuje usługę w hierarchii sieci Web.</span><span class="sxs-lookup"><span data-stu-id="248ca-121">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="248ca-122">Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web &#124; Ścieżka wirtualna usługi &#124; ServiceName ".</span><span class="sxs-lookup"><span data-stu-id="248ca-122">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="248ca-123">Przykład: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService ".</span><span class="sxs-lookup"><span data-stu-id="248ca-123">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="248ca-124">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="248ca-124">AppDomain</span></span>|`xs:string`|<span data-ttu-id="248ca-125">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="248ca-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
