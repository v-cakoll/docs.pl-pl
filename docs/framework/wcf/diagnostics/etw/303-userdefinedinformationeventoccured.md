---
title: 303 — UserDefinedInformationEventOccured
ms.date: 03/30/2017
ms.assetid: 5ed5acaf-3755-4417-92c4-4ebc8e854ca1
ms.openlocfilehash: 0b782b5ac0527b5acb3ebf0bf11c117563042495
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61595782"
---
# <a name="303---userdefinedinformationeventoccured"></a><span data-ttu-id="ad776-102">303 — UserDefinedInformationEventOccured</span><span class="sxs-lookup"><span data-stu-id="ad776-102">303 - UserDefinedInformationEventOccured</span></span>
## <a name="properties"></a><span data-ttu-id="ad776-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="ad776-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ad776-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="ad776-104">ID</span></span>|<span data-ttu-id="ad776-105">303</span><span class="sxs-lookup"><span data-stu-id="ad776-105">303</span></span>|  
|<span data-ttu-id="ad776-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="ad776-106">Keywords</span></span>|<span data-ttu-id="ad776-107">Rozwiązywanie problemów, HealthMonitoring UserEvents, ServiceModel, EndToEndMonitoring</span><span class="sxs-lookup"><span data-stu-id="ad776-107">Troubleshooting, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring</span></span>|  
|<span data-ttu-id="ad776-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="ad776-108">Level</span></span>|<span data-ttu-id="ad776-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="ad776-109">Information</span></span>|  
|<span data-ttu-id="ad776-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="ad776-110">Channel</span></span>|<span data-ttu-id="ad776-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="ad776-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ad776-112">Opis</span><span class="sxs-lookup"><span data-stu-id="ad776-112">Description</span></span>  
 <span data-ttu-id="ad776-113">To zdarzenie jest emitowane przez kod użytkownika.</span><span class="sxs-lookup"><span data-stu-id="ad776-113">This event is emitted from user code.</span></span> <span data-ttu-id="ad776-114">Deweloperzy może emitować to zdarzenie, gdy wystąpi zdarzenie informacyjne niestandardowy w ich usługi.</span><span class="sxs-lookup"><span data-stu-id="ad776-114">Developers can emit this event when a custom-defined informational event occurs in their service.</span></span> <span data-ttu-id="ad776-115">Można to zrobić za pomocą <xref:System.Diagnostics.Eventing> interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="ad776-115">This can be done using the <xref:System.Diagnostics.Eventing> APIs.</span></span> <span data-ttu-id="ad776-116">Ponadto jest przykładowy WCF, otacza tego interfejsu API, który pokazuje, jak prawidłowo emisji to zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="ad776-116">Additionally, there is a WCF sample that wraps that API and demonstrates how to properly emit this event.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ad776-117">Komunikat</span><span class="sxs-lookup"><span data-stu-id="ad776-117">Message</span></span>  
 <span data-ttu-id="ad776-118">Nazwa: "%1" dla odwołania: "%2", ładunek: %3</span><span class="sxs-lookup"><span data-stu-id="ad776-118">Name:'%1', Reference:'%2', Payload:%3</span></span>  
  
## <a name="details"></a><span data-ttu-id="ad776-119">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="ad776-119">Details</span></span>  
  
|<span data-ttu-id="ad776-120">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="ad776-120">Data Item Name</span></span>|<span data-ttu-id="ad776-121">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="ad776-121">Data Item Type</span></span>|<span data-ttu-id="ad776-122">Opis</span><span class="sxs-lookup"><span data-stu-id="ad776-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ad776-123">Nazwa</span><span class="sxs-lookup"><span data-stu-id="ad776-123">Name</span></span>|`xs:string`|<span data-ttu-id="ad776-124">Zdefiniowana przez użytkownika nazwa zdarzenia</span><span class="sxs-lookup"><span data-stu-id="ad776-124">The user-defined name of the event</span></span>|  
|<span data-ttu-id="ad776-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="ad776-125">HostReference</span></span>|`xs:string`|<span data-ttu-id="ad776-126">Dla usług sieci Web hostowanych w tym polu jednoznacznie identyfikuje usługę w hierarchii w sieci Web.</span><span class="sxs-lookup"><span data-stu-id="ad776-126">For Web hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="ad776-127">Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web&#124;ścieżka wirtualna usługi&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="ad776-127">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="ad776-128">Przykład: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="ad776-128">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="ad776-129">ładunek</span><span class="sxs-lookup"><span data-stu-id="ad776-129">Payload</span></span>|`xs:string`|<span data-ttu-id="ad776-130">Zdefiniowane przez użytkownika ładunek zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="ad776-130">The user-defined payload of the event.</span></span>|
