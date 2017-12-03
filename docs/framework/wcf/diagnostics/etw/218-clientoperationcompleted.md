---
title: "218 — ClientOperationCompleted"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b069bced-7bb2-4e01-8227-e5dbda17af09
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7d5b6fcc1c7ec4dd2f2c008e9d8bcfb58b2b4991
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="218---clientoperationcompleted"></a><span data-ttu-id="d6f56-102">218 — ClientOperationCompleted</span><span class="sxs-lookup"><span data-stu-id="d6f56-102">218 - ClientOperationCompleted</span></span>
## <a name="properties"></a><span data-ttu-id="d6f56-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="d6f56-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d6f56-104">ID</span><span class="sxs-lookup"><span data-stu-id="d6f56-104">ID</span></span>|<span data-ttu-id="d6f56-105">218</span><span class="sxs-lookup"><span data-stu-id="d6f56-105">218</span></span>|  
|<span data-ttu-id="d6f56-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="d6f56-106">Keywords</span></span>|<span data-ttu-id="d6f56-107">Rozwiązywanie problemów, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="d6f56-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="d6f56-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="d6f56-108">Level</span></span>|<span data-ttu-id="d6f56-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="d6f56-109">Information</span></span>|  
|<span data-ttu-id="d6f56-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="d6f56-110">Channel</span></span>|<span data-ttu-id="d6f56-111">Microsoft-Windows aplikacji Server aplikacje/analityczne</span><span class="sxs-lookup"><span data-stu-id="d6f56-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="d6f56-112">Opis</span><span class="sxs-lookup"><span data-stu-id="d6f56-112">Description</span></span>  
 <span data-ttu-id="d6f56-113">To zdarzenie jest emitowane przez klientów zaraz po zakończeniu operacji.</span><span class="sxs-lookup"><span data-stu-id="d6f56-113">This event is emitted by clients just after an operation completes.</span></span> <span data-ttu-id="d6f56-114">W przypadku operacji jednokierunkowych jest tuż po wiadomość zostanie wysłana pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="d6f56-114">For one-way operations, this is just after the message is sent successfully.</span></span> <span data-ttu-id="d6f56-115">Dla operacji żądanie odpowiedź jest po odebraniu odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="d6f56-115">For request-response operations this is after the response is received.</span></span>  
  
## <a name="message"></a><span data-ttu-id="d6f56-116">Komunikat</span><span class="sxs-lookup"><span data-stu-id="d6f56-116">Message</span></span>  
 <span data-ttu-id="d6f56-117">Klient ukończył wykonywanie akcji "%1" skojarzoną z kontraktem "%2".</span><span class="sxs-lookup"><span data-stu-id="d6f56-117">The Client completed executing Action '%1' associated with the '%2' contract.</span></span> <span data-ttu-id="d6f56-118">Wiadomość została wysłana do "%3".</span><span class="sxs-lookup"><span data-stu-id="d6f56-118">The message was sent to '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="d6f56-119">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="d6f56-119">Details</span></span>  
  
|<span data-ttu-id="d6f56-120">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="d6f56-120">Data Item Name</span></span>|<span data-ttu-id="d6f56-121">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="d6f56-121">Data Item Type</span></span>|<span data-ttu-id="d6f56-122">Opis</span><span class="sxs-lookup"><span data-stu-id="d6f56-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="d6f56-123">Akcja</span><span class="sxs-lookup"><span data-stu-id="d6f56-123">Action</span></span>|<span data-ttu-id="d6f56-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="d6f56-124">xs:string</span></span>|<span data-ttu-id="d6f56-125">Akcja SOAP nagłówka komunikatu wychodzącego.</span><span class="sxs-lookup"><span data-stu-id="d6f56-125">The SOAP action header of the outgoing message.</span></span>|  
|<span data-ttu-id="d6f56-126">Nazwa umowy</span><span class="sxs-lookup"><span data-stu-id="d6f56-126">Contract Name</span></span>|`xs:string`|<span data-ttu-id="d6f56-127">Nazwa kontraktu.</span><span class="sxs-lookup"><span data-stu-id="d6f56-127">The name of the contract.</span></span> <span data-ttu-id="d6f56-128">Przykład: ICalculator.</span><span class="sxs-lookup"><span data-stu-id="d6f56-128">Example: ICalculator.</span></span>|  
|<span data-ttu-id="d6f56-129">Miejsce docelowe</span><span class="sxs-lookup"><span data-stu-id="d6f56-129">Destination</span></span>|`xs:string`|<span data-ttu-id="d6f56-130">Adres punktu końcowego usługi, z którego wysłano wiadomość.</span><span class="sxs-lookup"><span data-stu-id="d6f56-130">The address of the service endpoint that the message was sent to.</span></span>|  
|<span data-ttu-id="d6f56-131">HostReference</span><span class="sxs-lookup"><span data-stu-id="d6f56-131">HostReference</span></span>|`xs:string`|<span data-ttu-id="d6f56-132">W przypadku usług hostowanych w sieci Web to pole unikatowo identyfikuje usługę w hierarchii sieci Web.</span><span class="sxs-lookup"><span data-stu-id="d6f56-132">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="d6f56-133">Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web &#124; Ścieżka wirtualna usługi &#124; ServiceName ".</span><span class="sxs-lookup"><span data-stu-id="d6f56-133">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="d6f56-134">Przykład: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService ".</span><span class="sxs-lookup"><span data-stu-id="d6f56-134">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="d6f56-135">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="d6f56-135">AppDomain</span></span>|`xs:string`|<span data-ttu-id="d6f56-136">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="d6f56-136">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
