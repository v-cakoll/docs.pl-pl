---
title: "205 — OperationInvoked"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9c8d6c90-dfa5-4ae0-a589-96679a8fb3ba
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2b0a96f1e3ba72a226d9b1a871382a27db61c57e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="205---operationinvoked"></a><span data-ttu-id="148d3-102">205 — OperationInvoked</span><span class="sxs-lookup"><span data-stu-id="148d3-102">205 - OperationInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="148d3-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="148d3-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="148d3-104">ID</span><span class="sxs-lookup"><span data-stu-id="148d3-104">ID</span></span>|<span data-ttu-id="148d3-105">205</span><span class="sxs-lookup"><span data-stu-id="148d3-105">205</span></span>|  
|<span data-ttu-id="148d3-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="148d3-106">Keywords</span></span>|<span data-ttu-id="148d3-107">Rozwiązywanie problemów, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="148d3-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="148d3-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="148d3-108">Level</span></span>|<span data-ttu-id="148d3-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="148d3-109">Information</span></span>|  
|<span data-ttu-id="148d3-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="148d3-110">Channel</span></span>|<span data-ttu-id="148d3-111">Microsoft-Windows aplikacji Server aplikacje/analityczne</span><span class="sxs-lookup"><span data-stu-id="148d3-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="148d3-112">Opis</span><span class="sxs-lookup"><span data-stu-id="148d3-112">Description</span></span>  
 <span data-ttu-id="148d3-113">To zdarzenie jest emitowany tuż przed domyślny Model usługi `OperationInvoker` rozpoczyna wywołanie do metody.</span><span class="sxs-lookup"><span data-stu-id="148d3-113">This event is emitted just before the Service Model's default `OperationInvoker` begins a call to a method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="148d3-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="148d3-114">Message</span></span>  
 <span data-ttu-id="148d3-115">Obiekt OperationInvoker wywołał metodę "%1".</span><span class="sxs-lookup"><span data-stu-id="148d3-115">An OperationInvoker invoked the '%1' method.</span></span> <span data-ttu-id="148d3-116">Informacje o obiekcie wywołującym: "%2".</span><span class="sxs-lookup"><span data-stu-id="148d3-116">Caller information: '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="148d3-117">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="148d3-117">Details</span></span>  
  
|<span data-ttu-id="148d3-118">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="148d3-118">Data Item Name</span></span>|<span data-ttu-id="148d3-119">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="148d3-119">Data Item Type</span></span>|<span data-ttu-id="148d3-120">Opis</span><span class="sxs-lookup"><span data-stu-id="148d3-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="148d3-121">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="148d3-121">Method Name</span></span>|`xs:string`|<span data-ttu-id="148d3-122">Nazwa metody, która została wywołana przez CLR `OperationInvoker`.</span><span class="sxs-lookup"><span data-stu-id="148d3-122">The CLR name of the method that was invoked by the `OperationInvoker`.</span></span>|  
|<span data-ttu-id="148d3-123">Informacje o wywołującym</span><span class="sxs-lookup"><span data-stu-id="148d3-123">Caller Information</span></span>|`xs:string`|<span data-ttu-id="148d3-124">IP adres i port numer klienta w formacie "IPAddress:PortNumber".</span><span class="sxs-lookup"><span data-stu-id="148d3-124">The IP address and port number of the client in the format 'IPAddress:PortNumber'.</span></span> <span data-ttu-id="148d3-125">Te dwie wartości są pobierane z właściwości komunikatu "System.ServiceModel.Channels.RemoteEndpointMessageProperty" w ramach operacji.</span><span class="sxs-lookup"><span data-stu-id="148d3-125">The two values are retrieved from the 'System.ServiceModel.Channels.RemoteEndpointMessageProperty' message property within the operation context.</span></span> <span data-ttu-id="148d3-126">Należy pamiętać, że dla powiązania z systemem innym niż TCP tej wartości `null`.</span><span class="sxs-lookup"><span data-stu-id="148d3-126">Note that for non-TCP bindings this value `null`.</span></span>|  
|<span data-ttu-id="148d3-127">HostReference</span><span class="sxs-lookup"><span data-stu-id="148d3-127">HostReference</span></span>|`xs:string`|<span data-ttu-id="148d3-128">W przypadku usług hostowanych w sieci Web to pole unikatowo identyfikuje usługę w hierarchii sieci Web.</span><span class="sxs-lookup"><span data-stu-id="148d3-128">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="148d3-129">Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web &#124; Ścieżka wirtualna usługi &#124; ServiceName ".</span><span class="sxs-lookup"><span data-stu-id="148d3-129">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="148d3-130">Przykład: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService ".</span><span class="sxs-lookup"><span data-stu-id="148d3-130">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="148d3-131">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="148d3-131">AppDomain</span></span>|`xs:string`|<span data-ttu-id="148d3-132">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="148d3-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
