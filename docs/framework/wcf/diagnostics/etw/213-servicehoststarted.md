---
title: 213 — ServiceHostStarted
ms.date: 03/30/2017
ms.assetid: a6f7facc-342f-46bb-9d52-a470178ba6bb
ms.openlocfilehash: 819efa2e13c94e2c7a16c24f6ba9c7ef2b87ef8c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781826"
---
# <a name="213---servicehoststarted"></a><span data-ttu-id="25dbc-102">213 — ServiceHostStarted</span><span class="sxs-lookup"><span data-stu-id="25dbc-102">213 - ServiceHostStarted</span></span>
## <a name="properties"></a><span data-ttu-id="25dbc-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="25dbc-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="25dbc-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="25dbc-104">ID</span></span>|<span data-ttu-id="25dbc-105">213</span><span class="sxs-lookup"><span data-stu-id="25dbc-105">213</span></span>|  
|<span data-ttu-id="25dbc-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="25dbc-106">Keywords</span></span>|<span data-ttu-id="25dbc-107">EndToEndMonitoring HealthMonitoring, rozwiązywania problemów, ServiceHost</span><span class="sxs-lookup"><span data-stu-id="25dbc-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceHost</span></span>|  
|<span data-ttu-id="25dbc-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="25dbc-108">Level</span></span>|<span data-ttu-id="25dbc-109">LogAlways</span><span class="sxs-lookup"><span data-stu-id="25dbc-109">LogAlways</span></span>|  
|<span data-ttu-id="25dbc-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="25dbc-110">Channel</span></span>|<span data-ttu-id="25dbc-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="25dbc-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="25dbc-112">Opis</span><span class="sxs-lookup"><span data-stu-id="25dbc-112">Description</span></span>  
 <span data-ttu-id="25dbc-113">To zdarzenie jest emitowane, podczas uruchamiania hosta usługi hostowanej w sieci Web.</span><span class="sxs-lookup"><span data-stu-id="25dbc-113">This event is emitted when a Web-hosted service host is started.</span></span> <span data-ttu-id="25dbc-114">Dzieje się tak zazwyczaj, gdy usługa została aktywowana przez komunikat.</span><span class="sxs-lookup"><span data-stu-id="25dbc-114">This typically happens when the service is activated by a message.</span></span> <span data-ttu-id="25dbc-115">Również zdarzyć, gdy usługa jest skonfigurowana do automatycznego uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="25dbc-115">It may also happen if the service is configured to be automatically started.</span></span>  
  
## <a name="message"></a><span data-ttu-id="25dbc-116">Komunikat</span><span class="sxs-lookup"><span data-stu-id="25dbc-116">Message</span></span>  
 <span data-ttu-id="25dbc-117">ServiceHost pracy: "%1".</span><span class="sxs-lookup"><span data-stu-id="25dbc-117">ServiceHost started: '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="25dbc-118">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="25dbc-118">Details</span></span>  
  
|<span data-ttu-id="25dbc-119">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="25dbc-119">Data Item Name</span></span>|<span data-ttu-id="25dbc-120">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="25dbc-120">Data Item Type</span></span>|<span data-ttu-id="25dbc-121">Opis</span><span class="sxs-lookup"><span data-stu-id="25dbc-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="25dbc-122">Nazwa typu usługi</span><span class="sxs-lookup"><span data-stu-id="25dbc-122">Service Type Name</span></span>|`xs:string`|<span data-ttu-id="25dbc-123">Pełna nazwa CLR typu implementacji usługi.</span><span class="sxs-lookup"><span data-stu-id="25dbc-123">The CLR FullName of the type of the service implementation.</span></span>|  
|<span data-ttu-id="25dbc-124">HostReference</span><span class="sxs-lookup"><span data-stu-id="25dbc-124">HostReference</span></span>|`xs:string`|<span data-ttu-id="25dbc-125">Dla usług sieci Web hostowanych w tym polu jednoznacznie identyfikuje usługę w hierarchii w sieci Web.</span><span class="sxs-lookup"><span data-stu-id="25dbc-125">For Web hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="25dbc-126">Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web&#124;ścieżka wirtualna usługi&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="25dbc-126">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="25dbc-127">Przykład: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="25dbc-127">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="25dbc-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="25dbc-128">AppDomain</span></span>|`xs:string`|<span data-ttu-id="25dbc-129">Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="25dbc-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
