---
title: 302 — UserDefinedWarningOccurred
ms.date: 03/30/2017
ms.assetid: 8d1f0bf1-0151-45e6-be92-573d397b54de
ms.openlocfilehash: c70857951309ef54ba460e96e948c9320269d30f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61596755"
---
# <a name="302---userdefinedwarningoccurred"></a><span data-ttu-id="feb1f-102">302 — UserDefinedWarningOccurred</span><span class="sxs-lookup"><span data-stu-id="feb1f-102">302 - UserDefinedWarningOccurred</span></span>
## <a name="properties"></a><span data-ttu-id="feb1f-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="feb1f-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="feb1f-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="feb1f-104">ID</span></span>|<span data-ttu-id="feb1f-105">302</span><span class="sxs-lookup"><span data-stu-id="feb1f-105">302</span></span>|  
|<span data-ttu-id="feb1f-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="feb1f-106">Keywords</span></span>|<span data-ttu-id="feb1f-107">Rozwiązywanie problemów, HealthMonitoring UserEvents, ServiceModel, EndToEndMonitoring</span><span class="sxs-lookup"><span data-stu-id="feb1f-107">Troubleshooting, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring</span></span>|  
|<span data-ttu-id="feb1f-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="feb1f-108">Level</span></span>|<span data-ttu-id="feb1f-109">Ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="feb1f-109">Warning</span></span>|  
|<span data-ttu-id="feb1f-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="feb1f-110">Channel</span></span>|<span data-ttu-id="feb1f-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="feb1f-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="feb1f-112">Opis</span><span class="sxs-lookup"><span data-stu-id="feb1f-112">Description</span></span>  
 <span data-ttu-id="feb1f-113">To zdarzenie jest emitowane przez kod użytkownika.</span><span class="sxs-lookup"><span data-stu-id="feb1f-113">This event is emitted from user code.</span></span> <span data-ttu-id="feb1f-114">Deweloperzy może emitować to zdarzenie, gdy wystąpi zdarzenie ostrzeżenia niestandardowy w ich usługi.</span><span class="sxs-lookup"><span data-stu-id="feb1f-114">Developers can emit this event when a custom-defined warning event occurs in their service.</span></span> <span data-ttu-id="feb1f-115">Można to zrobić za pomocą <xref:System.Diagnostics.Eventing> interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="feb1f-115">This can be done using the <xref:System.Diagnostics.Eventing> APIs.</span></span> <span data-ttu-id="feb1f-116">Ponadto jest przykładowy WCF, otacza tego interfejsu API, który pokazuje, jak prawidłowo emisji to zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="feb1f-116">Additionally, there is a WCF sample that wraps that API and demonstrates how to properly emit this event.</span></span>  
  
## <a name="message"></a><span data-ttu-id="feb1f-117">Komunikat</span><span class="sxs-lookup"><span data-stu-id="feb1f-117">Message</span></span>  
 <span data-ttu-id="feb1f-118">Nazwa: "%1" dla odwołania: "%2", ładunek: %3</span><span class="sxs-lookup"><span data-stu-id="feb1f-118">Name:'%1', Reference:'%2', Payload:%3</span></span>  
  
## <a name="details"></a><span data-ttu-id="feb1f-119">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="feb1f-119">Details</span></span>  
  
|<span data-ttu-id="feb1f-120">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="feb1f-120">Data Item Name</span></span>|<span data-ttu-id="feb1f-121">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="feb1f-121">Data Item Type</span></span>|<span data-ttu-id="feb1f-122">Opis</span><span class="sxs-lookup"><span data-stu-id="feb1f-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="feb1f-123">Nazwa</span><span class="sxs-lookup"><span data-stu-id="feb1f-123">Name</span></span>|`xs:string`|<span data-ttu-id="feb1f-124">Zdefiniowana przez użytkownika nazwa zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="feb1f-124">The user-defined name of the event.</span></span>|  
|<span data-ttu-id="feb1f-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="feb1f-125">HostReference</span></span>|`xs:string`|<span data-ttu-id="feb1f-126">W przypadku usług hostowanych w sieci Web to pole jednoznacznie identyfikuje usługę w hierarchii w sieci Web.</span><span class="sxs-lookup"><span data-stu-id="feb1f-126">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="feb1f-127">Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web&#124;ścieżka wirtualna usługi&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="feb1f-127">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="feb1f-128">Przykład: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="feb1f-128">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="feb1f-129">ładunek</span><span class="sxs-lookup"><span data-stu-id="feb1f-129">Payload</span></span>|`xs:string`|<span data-ttu-id="feb1f-130">Zdefiniowane przez użytkownika ładunek zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="feb1f-130">The user-defined payload of the event.</span></span>|
