---
title: 303 — UserDefinedInformationEventOccured
ms.date: 03/30/2017
ms.assetid: 5ed5acaf-3755-4417-92c4-4ebc8e854ca1
ms.openlocfilehash: 0b782b5ac0527b5acb3ebf0bf11c117563042495
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="303---userdefinedinformationeventoccured"></a><span data-ttu-id="21263-102">303 — UserDefinedInformationEventOccured</span><span class="sxs-lookup"><span data-stu-id="21263-102">303 - UserDefinedInformationEventOccured</span></span>
## <a name="properties"></a><span data-ttu-id="21263-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="21263-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="21263-104">ID</span><span class="sxs-lookup"><span data-stu-id="21263-104">ID</span></span>|<span data-ttu-id="21263-105">303</span><span class="sxs-lookup"><span data-stu-id="21263-105">303</span></span>|  
|<span data-ttu-id="21263-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="21263-106">Keywords</span></span>|<span data-ttu-id="21263-107">Rozwiązywanie problemów, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring</span><span class="sxs-lookup"><span data-stu-id="21263-107">Troubleshooting, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring</span></span>|  
|<span data-ttu-id="21263-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="21263-108">Level</span></span>|<span data-ttu-id="21263-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="21263-109">Information</span></span>|  
|<span data-ttu-id="21263-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="21263-110">Channel</span></span>|<span data-ttu-id="21263-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="21263-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="21263-112">Opis</span><span class="sxs-lookup"><span data-stu-id="21263-112">Description</span></span>  
 <span data-ttu-id="21263-113">To zdarzenie jest emitowany z kodu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="21263-113">This event is emitted from user code.</span></span> <span data-ttu-id="21263-114">Deweloperzy mogą emituje to zdarzenie po wystąpieniu zdarzenia informacyjną niestandardowy w usłudze ich.</span><span class="sxs-lookup"><span data-stu-id="21263-114">Developers can emit this event when a custom-defined informational event occurs in their service.</span></span> <span data-ttu-id="21263-115">Można to zrobić przy użyciu <xref:System.Diagnostics.Eventing> interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="21263-115">This can be done using the <xref:System.Diagnostics.Eventing> APIs.</span></span> <span data-ttu-id="21263-116">Ponadto jest przykład WCF, który opakowuje tego interfejsu API i pokazuje, jak poprawnie Emituj to zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="21263-116">Additionally, there is a WCF sample that wraps that API and demonstrates how to properly emit this event.</span></span>  
  
## <a name="message"></a><span data-ttu-id="21263-117">Komunikat</span><span class="sxs-lookup"><span data-stu-id="21263-117">Message</span></span>  
 <span data-ttu-id="21263-118">Nazwa: '%1' dla odwołania: "%2", ładunku: %3</span><span class="sxs-lookup"><span data-stu-id="21263-118">Name:'%1', Reference:'%2', Payload:%3</span></span>  
  
## <a name="details"></a><span data-ttu-id="21263-119">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="21263-119">Details</span></span>  
  
|<span data-ttu-id="21263-120">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="21263-120">Data Item Name</span></span>|<span data-ttu-id="21263-121">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="21263-121">Data Item Type</span></span>|<span data-ttu-id="21263-122">Opis</span><span class="sxs-lookup"><span data-stu-id="21263-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="21263-123">Nazwa</span><span class="sxs-lookup"><span data-stu-id="21263-123">Name</span></span>|`xs:string`|<span data-ttu-id="21263-124">Nazwa użytkownika zdarzenia</span><span class="sxs-lookup"><span data-stu-id="21263-124">The user-defined name of the event</span></span>|  
|<span data-ttu-id="21263-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="21263-125">HostReference</span></span>|`xs:string`|<span data-ttu-id="21263-126">Dla usług sieci Web hostowanych w tym polu unikatowo identyfikuje usługę w hierarchii sieci Web.</span><span class="sxs-lookup"><span data-stu-id="21263-126">For Web hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="21263-127">Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web&#124;ścieżki wirtualnej usługi&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="21263-127">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="21263-128">Przykład: "Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService".</span><span class="sxs-lookup"><span data-stu-id="21263-128">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="21263-129">ładunek</span><span class="sxs-lookup"><span data-stu-id="21263-129">Payload</span></span>|`xs:string`|<span data-ttu-id="21263-130">Zdefiniowane przez użytkownika ładunek zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="21263-130">The user-defined payload of the event.</span></span>|
