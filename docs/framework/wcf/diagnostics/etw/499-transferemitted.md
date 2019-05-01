---
title: 499 — TransferEmitted
ms.date: 03/30/2017
ms.assetid: 07a26434-a7a0-40fc-b5d0-3520a04328ae
ms.openlocfilehash: b1ade828ee6519288165e272e7d9f36fd6aca9ff
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774936"
---
# <a name="499---transferemitted"></a><span data-ttu-id="8e3c5-102">499 — TransferEmitted</span><span class="sxs-lookup"><span data-stu-id="8e3c5-102">499 - TransferEmitted</span></span>
## <a name="properties"></a><span data-ttu-id="8e3c5-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="8e3c5-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8e3c5-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="8e3c5-104">ID</span></span>|<span data-ttu-id="8e3c5-105">499</span><span class="sxs-lookup"><span data-stu-id="8e3c5-105">499</span></span>|  
|<span data-ttu-id="8e3c5-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="8e3c5-106">Keywords</span></span>|<span data-ttu-id="8e3c5-107">Troubleshooting, UserEvents, EndToEndMonitoring, ServiceModel, WFTracking, ServiceHost, WCFMessageLogging</span><span class="sxs-lookup"><span data-stu-id="8e3c5-107">Troubleshooting, UserEvents, EndToEndMonitoring, ServiceModel, WFTracking, ServiceHost, WCFMessageLogging</span></span>|  
|<span data-ttu-id="8e3c5-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="8e3c5-108">Level</span></span>|<span data-ttu-id="8e3c5-109">LogAlways</span><span class="sxs-lookup"><span data-stu-id="8e3c5-109">LogAlways</span></span>|  
|<span data-ttu-id="8e3c5-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="8e3c5-110">Channel</span></span>|<span data-ttu-id="8e3c5-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="8e3c5-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="8e3c5-112">Opis</span><span class="sxs-lookup"><span data-stu-id="8e3c5-112">Description</span></span>  
 <span data-ttu-id="8e3c5-113">To zdarzenie jest emitowane po wystąpieniu zdarzenia transferu.</span><span class="sxs-lookup"><span data-stu-id="8e3c5-113">This event is emitted when the transfer event takes place.</span></span>  
  
## <a name="message"></a><span data-ttu-id="8e3c5-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="8e3c5-114">Message</span></span>  
 <span data-ttu-id="8e3c5-115">Transferuje zdarzenie emitowane.</span><span class="sxs-lookup"><span data-stu-id="8e3c5-115">Transfer event emitted.</span></span>  
  
## <a name="details"></a><span data-ttu-id="8e3c5-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="8e3c5-116">Details</span></span>  
  
|<span data-ttu-id="8e3c5-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="8e3c5-117">Data Item Name</span></span>|<span data-ttu-id="8e3c5-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="8e3c5-118">Data Item Type</span></span>|<span data-ttu-id="8e3c5-119">Opis</span><span class="sxs-lookup"><span data-stu-id="8e3c5-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="8e3c5-120">HostReference</span><span class="sxs-lookup"><span data-stu-id="8e3c5-120">HostReference</span></span>|`xs:string`|<span data-ttu-id="8e3c5-121">W przypadku usług hostowanych w sieci Web to pole jednoznacznie identyfikuje usługę w hierarchii w sieci Web.</span><span class="sxs-lookup"><span data-stu-id="8e3c5-121">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="8e3c5-122">Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web&#124;ścieżka wirtualna usługi&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="8e3c5-122">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="8e3c5-123">Przykład: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="8e3c5-123">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="8e3c5-124">AppDomain</span><span class="sxs-lookup"><span data-stu-id="8e3c5-124">AppDomain</span></span>|`xs:string`|<span data-ttu-id="8e3c5-125">Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="8e3c5-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
