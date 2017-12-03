---
title: "206 — ErrorHandlerInvoked"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 97340f4d-4e09-4e42-a17a-982b3868dbcf
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4ff48217b1430002e1590ec3fdb1707d65075ffe
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="206---errorhandlerinvoked"></a><span data-ttu-id="1ab96-102">206 — ErrorHandlerInvoked</span><span class="sxs-lookup"><span data-stu-id="1ab96-102">206 - ErrorHandlerInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="1ab96-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="1ab96-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1ab96-104">ID</span><span class="sxs-lookup"><span data-stu-id="1ab96-104">ID</span></span>|<span data-ttu-id="1ab96-105">206</span><span class="sxs-lookup"><span data-stu-id="1ab96-105">206</span></span>|  
|<span data-ttu-id="1ab96-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="1ab96-106">Keywords</span></span>|<span data-ttu-id="1ab96-107">Rozwiązywanie problemów, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="1ab96-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="1ab96-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="1ab96-108">Level</span></span>|<span data-ttu-id="1ab96-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="1ab96-109">Information</span></span>|  
|<span data-ttu-id="1ab96-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="1ab96-110">Channel</span></span>|<span data-ttu-id="1ab96-111">Microsoft-Windows aplikacji Server aplikacje/analityczne</span><span class="sxs-lookup"><span data-stu-id="1ab96-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="1ab96-112">Opis</span><span class="sxs-lookup"><span data-stu-id="1ab96-112">Description</span></span>  
 <span data-ttu-id="1ab96-113">To zdarzenie jest emitowany po `ErrorHandler` umożliwieniu do obsługi wyjątku, który wystąpił podczas operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="1ab96-113">This event is emitted after an `ErrorHandler` has had an opportunity to handle an exception that occurred in a service operation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="1ab96-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="1ab96-114">Message</span></span>  
 <span data-ttu-id="1ab96-115">Dyspozytor wywołał obiekt ErrorHandler typu "%1" za pomocą wyjątku typu '%3'.</span><span class="sxs-lookup"><span data-stu-id="1ab96-115">The Dispatcher invoked an ErrorHandler of type '%1' with an exception of type '%3'.</span></span> <span data-ttu-id="1ab96-116">Obsłużony błąd == "%2".</span><span class="sxs-lookup"><span data-stu-id="1ab96-116">ErrorHandled == '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="1ab96-117">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="1ab96-117">Details</span></span>  
  
|<span data-ttu-id="1ab96-118">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="1ab96-118">Data Item Name</span></span>|<span data-ttu-id="1ab96-119">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="1ab96-119">Data Item Type</span></span>|<span data-ttu-id="1ab96-120">Opis</span><span class="sxs-lookup"><span data-stu-id="1ab96-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="1ab96-121">TypeName</span><span class="sxs-lookup"><span data-stu-id="1ab96-121">TypeName</span></span>|`xs:string`|<span data-ttu-id="1ab96-122">Imię i nazwisko CLR typu wywołanej `ErrorHandler`.</span><span class="sxs-lookup"><span data-stu-id="1ab96-122">The CLR FullName of the type of the invoked `ErrorHandler`.</span></span>|  
|<span data-ttu-id="1ab96-123">Obsługiwane</span><span class="sxs-lookup"><span data-stu-id="1ab96-123">Handled</span></span>|`xs:unsignedByte`|<span data-ttu-id="1ab96-124">`true`Jeśli program obsługi błędów obsługi błędu, w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="1ab96-124">`true` if the error handler handled the error, otherwise `false`.</span></span>|  
|<span data-ttu-id="1ab96-125">ExceptionTypeName</span><span class="sxs-lookup"><span data-stu-id="1ab96-125">ExceptionTypeName</span></span>|`xs:string`|<span data-ttu-id="1ab96-126">Element FullName CLR wyjątku, który został już obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="1ab96-126">The CLR FullName of the exception that was being handled.</span></span>|  
|<span data-ttu-id="1ab96-127">HostReference</span><span class="sxs-lookup"><span data-stu-id="1ab96-127">HostReference</span></span>|`xs:string`|<span data-ttu-id="1ab96-128">W przypadku usług hostowanych w sieci Web to pole unikatowo identyfikuje usługę w hierarchii sieci Web.</span><span class="sxs-lookup"><span data-stu-id="1ab96-128">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="1ab96-129">Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web &#124; Ścieżka wirtualna usługi &#124; ServiceName ".</span><span class="sxs-lookup"><span data-stu-id="1ab96-129">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="1ab96-130">Przykład: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService ".</span><span class="sxs-lookup"><span data-stu-id="1ab96-130">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="1ab96-131">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="1ab96-131">AppDomain</span></span>|`xs:string`|<span data-ttu-id="1ab96-132">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="1ab96-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
