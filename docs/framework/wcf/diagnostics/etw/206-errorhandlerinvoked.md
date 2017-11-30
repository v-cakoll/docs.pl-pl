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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 84470cbaf7ba7951ef59b130c696462079216cde
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="206---errorhandlerinvoked"></a><span data-ttu-id="b73a0-102">206 — ErrorHandlerInvoked</span><span class="sxs-lookup"><span data-stu-id="b73a0-102">206 - ErrorHandlerInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="b73a0-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="b73a0-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b73a0-104">ID</span><span class="sxs-lookup"><span data-stu-id="b73a0-104">ID</span></span>|<span data-ttu-id="b73a0-105">206</span><span class="sxs-lookup"><span data-stu-id="b73a0-105">206</span></span>|  
|<span data-ttu-id="b73a0-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="b73a0-106">Keywords</span></span>|<span data-ttu-id="b73a0-107">Rozwiązywanie problemów, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="b73a0-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="b73a0-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="b73a0-108">Level</span></span>|<span data-ttu-id="b73a0-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="b73a0-109">Information</span></span>|  
|<span data-ttu-id="b73a0-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="b73a0-110">Channel</span></span>|<span data-ttu-id="b73a0-111">Microsoft-Windows aplikacji Server aplikacje/analityczne</span><span class="sxs-lookup"><span data-stu-id="b73a0-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b73a0-112">Opis</span><span class="sxs-lookup"><span data-stu-id="b73a0-112">Description</span></span>  
 <span data-ttu-id="b73a0-113">To zdarzenie jest emitowany po `ErrorHandler` umożliwieniu do obsługi wyjątku, który wystąpił podczas operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="b73a0-113">This event is emitted after an `ErrorHandler` has had an opportunity to handle an exception that occurred in a service operation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b73a0-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="b73a0-114">Message</span></span>  
 <span data-ttu-id="b73a0-115">Dyspozytor wywołał obiekt ErrorHandler typu "%1" za pomocą wyjątku typu '%3'.</span><span class="sxs-lookup"><span data-stu-id="b73a0-115">The Dispatcher invoked an ErrorHandler of type '%1' with an exception of type '%3'.</span></span> <span data-ttu-id="b73a0-116">Obsłużony błąd == "%2".</span><span class="sxs-lookup"><span data-stu-id="b73a0-116">ErrorHandled == '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="b73a0-117">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="b73a0-117">Details</span></span>  
  
|<span data-ttu-id="b73a0-118">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="b73a0-118">Data Item Name</span></span>|<span data-ttu-id="b73a0-119">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="b73a0-119">Data Item Type</span></span>|<span data-ttu-id="b73a0-120">Opis</span><span class="sxs-lookup"><span data-stu-id="b73a0-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b73a0-121">TypeName</span><span class="sxs-lookup"><span data-stu-id="b73a0-121">TypeName</span></span>|`xs:string`|<span data-ttu-id="b73a0-122">Imię i nazwisko CLR typu wywołanej `ErrorHandler`.</span><span class="sxs-lookup"><span data-stu-id="b73a0-122">The CLR FullName of the type of the invoked `ErrorHandler`.</span></span>|  
|<span data-ttu-id="b73a0-123">Obsługiwane</span><span class="sxs-lookup"><span data-stu-id="b73a0-123">Handled</span></span>|`xs:unsignedByte`|<span data-ttu-id="b73a0-124">`true`Jeśli program obsługi błędów obsługi błędu, w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="b73a0-124">`true` if the error handler handled the error, otherwise `false`.</span></span>|  
|<span data-ttu-id="b73a0-125">ExceptionTypeName</span><span class="sxs-lookup"><span data-stu-id="b73a0-125">ExceptionTypeName</span></span>|`xs:string`|<span data-ttu-id="b73a0-126">Element FullName CLR wyjątku, który został już obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="b73a0-126">The CLR FullName of the exception that was being handled.</span></span>|  
|<span data-ttu-id="b73a0-127">HostReference</span><span class="sxs-lookup"><span data-stu-id="b73a0-127">HostReference</span></span>|`xs:string`|<span data-ttu-id="b73a0-128">W przypadku usług hostowanych w sieci Web to pole unikatowo identyfikuje usługę w hierarchii sieci Web.</span><span class="sxs-lookup"><span data-stu-id="b73a0-128">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="b73a0-129">Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web &#124; Ścieżka wirtualna usługi &#124; ServiceName ".</span><span class="sxs-lookup"><span data-stu-id="b73a0-129">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="b73a0-130">Przykład: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService ".</span><span class="sxs-lookup"><span data-stu-id="b73a0-130">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="b73a0-131">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="b73a0-131">AppDomain</span></span>|`xs:string`|<span data-ttu-id="b73a0-132">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="b73a0-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
