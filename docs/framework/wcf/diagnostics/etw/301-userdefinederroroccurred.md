---
title: "301 — UserDefinedErrorOccurred"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a0285d1c-550f-4c14-9c36-a96e97f1c4e4
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b24d54930a29a24dab97ce403c2808fb74b8cbfe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="301---userdefinederroroccurred"></a><span data-ttu-id="c3e4b-102">301 — UserDefinedErrorOccurred</span><span class="sxs-lookup"><span data-stu-id="c3e4b-102">301 - UserDefinedErrorOccurred</span></span>
## <a name="properties"></a><span data-ttu-id="c3e4b-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="c3e4b-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c3e4b-104">ID</span><span class="sxs-lookup"><span data-stu-id="c3e4b-104">ID</span></span>|<span data-ttu-id="c3e4b-105">301</span><span class="sxs-lookup"><span data-stu-id="c3e4b-105">301</span></span>|  
|<span data-ttu-id="c3e4b-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="c3e4b-106">Keywords</span></span>|<span data-ttu-id="c3e4b-107">Rozwiązywanie problemów, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring</span><span class="sxs-lookup"><span data-stu-id="c3e4b-107">Troubleshooting, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring</span></span>|  
|<span data-ttu-id="c3e4b-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="c3e4b-108">Level</span></span>|<span data-ttu-id="c3e4b-109">Błąd</span><span class="sxs-lookup"><span data-stu-id="c3e4b-109">Error</span></span>|  
|<span data-ttu-id="c3e4b-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="c3e4b-110">Channel</span></span>|<span data-ttu-id="c3e4b-111">Microsoft-Windows aplikacji Server aplikacje/analityczne</span><span class="sxs-lookup"><span data-stu-id="c3e4b-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c3e4b-112">Opis</span><span class="sxs-lookup"><span data-stu-id="c3e4b-112">Description</span></span>  
 <span data-ttu-id="c3e4b-113">To zdarzenie jest emitowany z kodu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="c3e4b-113">This event is emitted from user code.</span></span> <span data-ttu-id="c3e4b-114">Deweloperzy mogą emituje to zdarzenie, gdy wystąpi błąd niestandardowy w usłudze ich.</span><span class="sxs-lookup"><span data-stu-id="c3e4b-114">Developers can emit this event when a custom-defined error occurs in their service.</span></span> <span data-ttu-id="c3e4b-115">Można to zrobić przy użyciu <xref:System.Diagnostics.Eventing> interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="c3e4b-115">This can be done using the <xref:System.Diagnostics.Eventing> APIs.</span></span> <span data-ttu-id="c3e4b-116">Ponadto jest przykład WCF, który opakowuje tego interfejsu API i pokazuje, jak poprawnie Emituj to zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="c3e4b-116">Additionally, there is a WCF sample that wraps that API and demonstrates how to properly emit this event.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c3e4b-117">Komunikat</span><span class="sxs-lookup"><span data-stu-id="c3e4b-117">Message</span></span>  
 <span data-ttu-id="c3e4b-118">Nazwa: '%1' dla odwołania: "%2", ładunku: %3</span><span class="sxs-lookup"><span data-stu-id="c3e4b-118">Name:'%1', Reference:'%2', Payload:%3</span></span>  
  
## <a name="details"></a><span data-ttu-id="c3e4b-119">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="c3e4b-119">Details</span></span>  
  
|<span data-ttu-id="c3e4b-120">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="c3e4b-120">Data Item Name</span></span>|<span data-ttu-id="c3e4b-121">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="c3e4b-121">Data Item Type</span></span>|<span data-ttu-id="c3e4b-122">Opis</span><span class="sxs-lookup"><span data-stu-id="c3e4b-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c3e4b-123">Nazwa</span><span class="sxs-lookup"><span data-stu-id="c3e4b-123">Name</span></span>|`xs:string`|<span data-ttu-id="c3e4b-124">Zdefiniowane przez użytkownika nazwa zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="c3e4b-124">The user-defined name of the event.</span></span>|  
|<span data-ttu-id="c3e4b-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="c3e4b-125">HostReference</span></span>|`xs:string`|<span data-ttu-id="c3e4b-126">W przypadku usług hostowanych w sieci Web to pole unikatowo identyfikuje usługę w hierarchii sieci Web.</span><span class="sxs-lookup"><span data-stu-id="c3e4b-126">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="c3e4b-127">Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web &#124; Ścieżka wirtualna usługi &#124; ServiceName ".</span><span class="sxs-lookup"><span data-stu-id="c3e4b-127">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="c3e4b-128">Przykład: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService ".</span><span class="sxs-lookup"><span data-stu-id="c3e4b-128">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="c3e4b-129">ładunek</span><span class="sxs-lookup"><span data-stu-id="c3e4b-129">Payload</span></span>|`xs:string`|<span data-ttu-id="c3e4b-130">Zdefiniowane przez użytkownika ładunek zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="c3e4b-130">The user-defined payload of the event.</span></span>|
