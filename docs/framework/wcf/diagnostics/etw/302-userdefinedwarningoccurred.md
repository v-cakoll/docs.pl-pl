---
title: 302 — UserDefinedWarningOccurred
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8d1f0bf1-0151-45e6-be92-573d397b54de
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ae455c9eec2335fcf6eb5473932bd8d9e5d2db95
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/23/2018
---
# <a name="302---userdefinedwarningoccurred"></a><span data-ttu-id="9ed33-102">302 — UserDefinedWarningOccurred</span><span class="sxs-lookup"><span data-stu-id="9ed33-102">302 - UserDefinedWarningOccurred</span></span>
## <a name="properties"></a><span data-ttu-id="9ed33-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="9ed33-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9ed33-104">ID</span><span class="sxs-lookup"><span data-stu-id="9ed33-104">ID</span></span>|<span data-ttu-id="9ed33-105">302</span><span class="sxs-lookup"><span data-stu-id="9ed33-105">302</span></span>|  
|<span data-ttu-id="9ed33-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="9ed33-106">Keywords</span></span>|<span data-ttu-id="9ed33-107">Rozwiązywanie problemów, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring</span><span class="sxs-lookup"><span data-stu-id="9ed33-107">Troubleshooting, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring</span></span>|  
|<span data-ttu-id="9ed33-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="9ed33-108">Level</span></span>|<span data-ttu-id="9ed33-109">Ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="9ed33-109">Warning</span></span>|  
|<span data-ttu-id="9ed33-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="9ed33-110">Channel</span></span>|<span data-ttu-id="9ed33-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="9ed33-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9ed33-112">Opis</span><span class="sxs-lookup"><span data-stu-id="9ed33-112">Description</span></span>  
 <span data-ttu-id="9ed33-113">To zdarzenie jest emitowany z kodu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="9ed33-113">This event is emitted from user code.</span></span> <span data-ttu-id="9ed33-114">Deweloperzy mogą emituje to zdarzenie, gdy wystąpi zdarzenie ostrzeżenia niestandardowy w usłudze ich.</span><span class="sxs-lookup"><span data-stu-id="9ed33-114">Developers can emit this event when a custom-defined warning event occurs in their service.</span></span> <span data-ttu-id="9ed33-115">Można to zrobić przy użyciu <xref:System.Diagnostics.Eventing> interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="9ed33-115">This can be done using the <xref:System.Diagnostics.Eventing> APIs.</span></span> <span data-ttu-id="9ed33-116">Ponadto jest przykład WCF, który opakowuje tego interfejsu API i pokazuje, jak poprawnie Emituj to zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="9ed33-116">Additionally, there is a WCF sample that wraps that API and demonstrates how to properly emit this event.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9ed33-117">Komunikat</span><span class="sxs-lookup"><span data-stu-id="9ed33-117">Message</span></span>  
 <span data-ttu-id="9ed33-118">Nazwa: '%1' dla odwołania: "%2", ładunku: %3</span><span class="sxs-lookup"><span data-stu-id="9ed33-118">Name:'%1', Reference:'%2', Payload:%3</span></span>  
  
## <a name="details"></a><span data-ttu-id="9ed33-119">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="9ed33-119">Details</span></span>  
  
|<span data-ttu-id="9ed33-120">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="9ed33-120">Data Item Name</span></span>|<span data-ttu-id="9ed33-121">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="9ed33-121">Data Item Type</span></span>|<span data-ttu-id="9ed33-122">Opis</span><span class="sxs-lookup"><span data-stu-id="9ed33-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="9ed33-123">Nazwa</span><span class="sxs-lookup"><span data-stu-id="9ed33-123">Name</span></span>|`xs:string`|<span data-ttu-id="9ed33-124">Zdefiniowane przez użytkownika nazwa zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="9ed33-124">The user-defined name of the event.</span></span>|  
|<span data-ttu-id="9ed33-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="9ed33-125">HostReference</span></span>|`xs:string`|<span data-ttu-id="9ed33-126">W przypadku usług hostowanych w sieci Web to pole unikatowo identyfikuje usługę w hierarchii sieci Web.</span><span class="sxs-lookup"><span data-stu-id="9ed33-126">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="9ed33-127">Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web&#124;ścieżki wirtualnej usługi&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="9ed33-127">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="9ed33-128">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="9ed33-128">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="9ed33-129">ładunek</span><span class="sxs-lookup"><span data-stu-id="9ed33-129">Payload</span></span>|`xs:string`|<span data-ttu-id="9ed33-130">Zdefiniowane przez użytkownika ładunek zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="9ed33-130">The user-defined payload of the event.</span></span>|
