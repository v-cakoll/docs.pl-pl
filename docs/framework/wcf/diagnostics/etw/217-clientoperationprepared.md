---
title: "217 — ClientOperationPrepared"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ad207f04-b038-4f33-95e9-27a361df8ecd
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5062d2c2146dae8b22165cfbea0c6a78241d17b8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="217---clientoperationprepared"></a><span data-ttu-id="41a94-102">217 — ClientOperationPrepared</span><span class="sxs-lookup"><span data-stu-id="41a94-102">217 - ClientOperationPrepared</span></span>
## <a name="properties"></a><span data-ttu-id="41a94-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="41a94-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="41a94-104">ID</span><span class="sxs-lookup"><span data-stu-id="41a94-104">ID</span></span>|<span data-ttu-id="41a94-105">217</span><span class="sxs-lookup"><span data-stu-id="41a94-105">217</span></span>|  
|<span data-ttu-id="41a94-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="41a94-106">Keywords</span></span>|<span data-ttu-id="41a94-107">Rozwiązywanie problemów, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="41a94-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="41a94-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="41a94-108">Level</span></span>|<span data-ttu-id="41a94-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="41a94-109">Information</span></span>|  
|<span data-ttu-id="41a94-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="41a94-110">Channel</span></span>|<span data-ttu-id="41a94-111">Microsoft-Windows aplikacji Server aplikacje/analityczne</span><span class="sxs-lookup"><span data-stu-id="41a94-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="41a94-112">Opis</span><span class="sxs-lookup"><span data-stu-id="41a94-112">Description</span></span>  
 <span data-ttu-id="41a94-113">To zdarzenie jest emitowane przez klientów tuż przed operacją jest wysyłane do usługi.</span><span class="sxs-lookup"><span data-stu-id="41a94-113">This event is emitted by clients just before an operation is sent to the service.</span></span>  
  
## <a name="message"></a><span data-ttu-id="41a94-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="41a94-114">Message</span></span>  
 <span data-ttu-id="41a94-115">Klient wykonuje akcję "%1" skojarzoną z kontraktem "%2".</span><span class="sxs-lookup"><span data-stu-id="41a94-115">The Client is executing Action '%1' associated with the '%2' contract.</span></span> <span data-ttu-id="41a94-116">Wiadomość zostanie wysłana do "%3".</span><span class="sxs-lookup"><span data-stu-id="41a94-116">The message will be sent to '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="41a94-117">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="41a94-117">Details</span></span>  
  
|<span data-ttu-id="41a94-118">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="41a94-118">Data Item Name</span></span>|<span data-ttu-id="41a94-119">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="41a94-119">Data Item Type</span></span>|<span data-ttu-id="41a94-120">Opis</span><span class="sxs-lookup"><span data-stu-id="41a94-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="41a94-121">Akcja</span><span class="sxs-lookup"><span data-stu-id="41a94-121">Action</span></span>|`xs:string`|<span data-ttu-id="41a94-122">Akcja SOAP nagłówka komunikatu wychodzącego.</span><span class="sxs-lookup"><span data-stu-id="41a94-122">The SOAP action header of the outgoing message.</span></span>|  
|<span data-ttu-id="41a94-123">Nazwa umowy</span><span class="sxs-lookup"><span data-stu-id="41a94-123">Contract Name</span></span>|`xs:string`|<span data-ttu-id="41a94-124">Nazwa kontraktu.</span><span class="sxs-lookup"><span data-stu-id="41a94-124">The name of the contract.</span></span> <span data-ttu-id="41a94-125">Przykład: ICalculator.</span><span class="sxs-lookup"><span data-stu-id="41a94-125">Example: ICalculator.</span></span>|  
|<span data-ttu-id="41a94-126">Miejsce docelowe</span><span class="sxs-lookup"><span data-stu-id="41a94-126">Destination</span></span>|`xs:string`|<span data-ttu-id="41a94-127">Adres punktu końcowego usługi, który komunikat jest wysyłany do.</span><span class="sxs-lookup"><span data-stu-id="41a94-127">The address of the service endpoint that the message is sent to.</span></span>|  
|<span data-ttu-id="41a94-128">HostReference</span><span class="sxs-lookup"><span data-stu-id="41a94-128">HostReference</span></span>|`xs:string`|<span data-ttu-id="41a94-129">W przypadku usług hostowanych w sieci Web to pole unikatowo identyfikuje usługę w hierarchii sieci Web.</span><span class="sxs-lookup"><span data-stu-id="41a94-129">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="41a94-130">Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web &#124; Ścieżka wirtualna usługi &#124; ServiceName ".</span><span class="sxs-lookup"><span data-stu-id="41a94-130">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="41a94-131">Przykład: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService ".</span><span class="sxs-lookup"><span data-stu-id="41a94-131">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="41a94-132">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="41a94-132">AppDomain</span></span>|`xs:string`|<span data-ttu-id="41a94-133">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="41a94-133">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
