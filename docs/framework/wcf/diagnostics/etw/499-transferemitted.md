---
title: 499 — TransferEmitted
ms.date: 03/30/2017
ms.assetid: 07a26434-a7a0-40fc-b5d0-3520a04328ae
ms.openlocfilehash: b1ade828ee6519288165e272e7d9f36fd6aca9ff
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33469511"
---
# <a name="499---transferemitted"></a><span data-ttu-id="6eae7-102">499 — TransferEmitted</span><span class="sxs-lookup"><span data-stu-id="6eae7-102">499 - TransferEmitted</span></span>
## <a name="properties"></a><span data-ttu-id="6eae7-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="6eae7-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6eae7-104">ID</span><span class="sxs-lookup"><span data-stu-id="6eae7-104">ID</span></span>|<span data-ttu-id="6eae7-105">499</span><span class="sxs-lookup"><span data-stu-id="6eae7-105">499</span></span>|  
|<span data-ttu-id="6eae7-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="6eae7-106">Keywords</span></span>|<span data-ttu-id="6eae7-107">Rozwiązywanie problemów, UserEvents, EndToEndMonitoring, ServiceModel, WFTracking ServiceHost, WCFMessageLogging</span><span class="sxs-lookup"><span data-stu-id="6eae7-107">Troubleshooting, UserEvents, EndToEndMonitoring, ServiceModel, WFTracking, ServiceHost, WCFMessageLogging</span></span>|  
|<span data-ttu-id="6eae7-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="6eae7-108">Level</span></span>|<span data-ttu-id="6eae7-109">LogAlways</span><span class="sxs-lookup"><span data-stu-id="6eae7-109">LogAlways</span></span>|  
|<span data-ttu-id="6eae7-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="6eae7-110">Channel</span></span>|<span data-ttu-id="6eae7-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="6eae7-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="6eae7-112">Opis</span><span class="sxs-lookup"><span data-stu-id="6eae7-112">Description</span></span>  
 <span data-ttu-id="6eae7-113">To zdarzenie jest emitowany po wystąpieniu zdarzenia transferu.</span><span class="sxs-lookup"><span data-stu-id="6eae7-113">This event is emitted when the transfer event takes place.</span></span>  
  
## <a name="message"></a><span data-ttu-id="6eae7-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="6eae7-114">Message</span></span>  
 <span data-ttu-id="6eae7-115">Zdarzenia transferu wysyłanego.</span><span class="sxs-lookup"><span data-stu-id="6eae7-115">Transfer event emitted.</span></span>  
  
## <a name="details"></a><span data-ttu-id="6eae7-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="6eae7-116">Details</span></span>  
  
|<span data-ttu-id="6eae7-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="6eae7-117">Data Item Name</span></span>|<span data-ttu-id="6eae7-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="6eae7-118">Data Item Type</span></span>|<span data-ttu-id="6eae7-119">Opis</span><span class="sxs-lookup"><span data-stu-id="6eae7-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="6eae7-120">HostReference</span><span class="sxs-lookup"><span data-stu-id="6eae7-120">HostReference</span></span>|`xs:string`|<span data-ttu-id="6eae7-121">W przypadku usług hostowanych w sieci Web to pole unikatowo identyfikuje usługę w hierarchii sieci Web.</span><span class="sxs-lookup"><span data-stu-id="6eae7-121">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="6eae7-122">Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web&#124;ścieżki wirtualnej usługi&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="6eae7-122">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="6eae7-123">Przykład: "Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService".</span><span class="sxs-lookup"><span data-stu-id="6eae7-123">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="6eae7-124">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="6eae7-124">AppDomain</span></span>|`xs:string`|<span data-ttu-id="6eae7-125">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="6eae7-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
