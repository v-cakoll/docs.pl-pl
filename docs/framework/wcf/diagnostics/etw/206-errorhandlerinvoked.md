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
ms.workload: dotnet
ms.openlocfilehash: 43acd7ae7bbfc84e1d1ffb1bf4fa49a3dd3f191a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="206---errorhandlerinvoked"></a><span data-ttu-id="7a6b1-102">206 — ErrorHandlerInvoked</span><span class="sxs-lookup"><span data-stu-id="7a6b1-102">206 - ErrorHandlerInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="7a6b1-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="7a6b1-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7a6b1-104">ID</span><span class="sxs-lookup"><span data-stu-id="7a6b1-104">ID</span></span>|<span data-ttu-id="7a6b1-105">206</span><span class="sxs-lookup"><span data-stu-id="7a6b1-105">206</span></span>|  
|<span data-ttu-id="7a6b1-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="7a6b1-106">Keywords</span></span>|<span data-ttu-id="7a6b1-107">Rozwiązywanie problemów, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="7a6b1-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="7a6b1-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="7a6b1-108">Level</span></span>|<span data-ttu-id="7a6b1-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="7a6b1-109">Information</span></span>|  
|<span data-ttu-id="7a6b1-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="7a6b1-110">Channel</span></span>|<span data-ttu-id="7a6b1-111">Microsoft-Windows aplikacji Server aplikacje/analityczne</span><span class="sxs-lookup"><span data-stu-id="7a6b1-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="7a6b1-112">Opis</span><span class="sxs-lookup"><span data-stu-id="7a6b1-112">Description</span></span>  
 <span data-ttu-id="7a6b1-113">To zdarzenie jest emitowany po `ErrorHandler` umożliwieniu do obsługi wyjątku, który wystąpił podczas operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="7a6b1-113">This event is emitted after an `ErrorHandler` has had an opportunity to handle an exception that occurred in a service operation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="7a6b1-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="7a6b1-114">Message</span></span>  
 <span data-ttu-id="7a6b1-115">Dyspozytor wywołał obiekt ErrorHandler typu "%1" za pomocą wyjątku typu '%3'.</span><span class="sxs-lookup"><span data-stu-id="7a6b1-115">The Dispatcher invoked an ErrorHandler of type '%1' with an exception of type '%3'.</span></span> <span data-ttu-id="7a6b1-116">Obsłużony błąd == "%2".</span><span class="sxs-lookup"><span data-stu-id="7a6b1-116">ErrorHandled == '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="7a6b1-117">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="7a6b1-117">Details</span></span>  
  
|<span data-ttu-id="7a6b1-118">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="7a6b1-118">Data Item Name</span></span>|<span data-ttu-id="7a6b1-119">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="7a6b1-119">Data Item Type</span></span>|<span data-ttu-id="7a6b1-120">Opis</span><span class="sxs-lookup"><span data-stu-id="7a6b1-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="7a6b1-121">TypeName</span><span class="sxs-lookup"><span data-stu-id="7a6b1-121">TypeName</span></span>|`xs:string`|<span data-ttu-id="7a6b1-122">Imię i nazwisko CLR typu wywołanej `ErrorHandler`.</span><span class="sxs-lookup"><span data-stu-id="7a6b1-122">The CLR FullName of the type of the invoked `ErrorHandler`.</span></span>|  
|<span data-ttu-id="7a6b1-123">Obsługiwane</span><span class="sxs-lookup"><span data-stu-id="7a6b1-123">Handled</span></span>|`xs:unsignedByte`|<span data-ttu-id="7a6b1-124">`true`Jeśli program obsługi błędów obsługi błędu, w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="7a6b1-124">`true` if the error handler handled the error, otherwise `false`.</span></span>|  
|<span data-ttu-id="7a6b1-125">ExceptionTypeName</span><span class="sxs-lookup"><span data-stu-id="7a6b1-125">ExceptionTypeName</span></span>|`xs:string`|<span data-ttu-id="7a6b1-126">Element FullName CLR wyjątku, który został już obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="7a6b1-126">The CLR FullName of the exception that was being handled.</span></span>|  
|<span data-ttu-id="7a6b1-127">HostReference</span><span class="sxs-lookup"><span data-stu-id="7a6b1-127">HostReference</span></span>|`xs:string`|<span data-ttu-id="7a6b1-128">W przypadku usług hostowanych w sieci Web to pole unikatowo identyfikuje usługę w hierarchii sieci Web.</span><span class="sxs-lookup"><span data-stu-id="7a6b1-128">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="7a6b1-129">Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web &#124; Ścieżka wirtualna usługi &#124; ServiceName ".</span><span class="sxs-lookup"><span data-stu-id="7a6b1-129">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="7a6b1-130">Przykład: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService ".</span><span class="sxs-lookup"><span data-stu-id="7a6b1-130">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="7a6b1-131">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="7a6b1-131">AppDomain</span></span>|`xs:string`|<span data-ttu-id="7a6b1-132">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="7a6b1-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
