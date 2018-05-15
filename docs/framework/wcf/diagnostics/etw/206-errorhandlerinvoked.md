---
title: 206 — ErrorHandlerInvoked
ms.date: 03/30/2017
ms.assetid: 97340f4d-4e09-4e42-a17a-982b3868dbcf
ms.openlocfilehash: 40a92d77c57728249569a854eab8767ff371bca2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="206---errorhandlerinvoked"></a><span data-ttu-id="396ef-102">206 — ErrorHandlerInvoked</span><span class="sxs-lookup"><span data-stu-id="396ef-102">206 - ErrorHandlerInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="396ef-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="396ef-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="396ef-104">ID</span><span class="sxs-lookup"><span data-stu-id="396ef-104">ID</span></span>|<span data-ttu-id="396ef-105">206</span><span class="sxs-lookup"><span data-stu-id="396ef-105">206</span></span>|  
|<span data-ttu-id="396ef-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="396ef-106">Keywords</span></span>|<span data-ttu-id="396ef-107">Rozwiązywanie problemów, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="396ef-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="396ef-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="396ef-108">Level</span></span>|<span data-ttu-id="396ef-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="396ef-109">Information</span></span>|  
|<span data-ttu-id="396ef-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="396ef-110">Channel</span></span>|<span data-ttu-id="396ef-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="396ef-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="396ef-112">Opis</span><span class="sxs-lookup"><span data-stu-id="396ef-112">Description</span></span>  
 <span data-ttu-id="396ef-113">To zdarzenie jest emitowany po `ErrorHandler` umożliwieniu do obsługi wyjątku, który wystąpił podczas operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="396ef-113">This event is emitted after an `ErrorHandler` has had an opportunity to handle an exception that occurred in a service operation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="396ef-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="396ef-114">Message</span></span>  
 <span data-ttu-id="396ef-115">Dyspozytor wywołał obiekt ErrorHandler typu "%1" za pomocą wyjątku typu '%3'.</span><span class="sxs-lookup"><span data-stu-id="396ef-115">The Dispatcher invoked an ErrorHandler of type '%1' with an exception of type '%3'.</span></span> <span data-ttu-id="396ef-116">Obsłużony błąd == "%2".</span><span class="sxs-lookup"><span data-stu-id="396ef-116">ErrorHandled == '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="396ef-117">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="396ef-117">Details</span></span>  
  
|<span data-ttu-id="396ef-118">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="396ef-118">Data Item Name</span></span>|<span data-ttu-id="396ef-119">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="396ef-119">Data Item Type</span></span>|<span data-ttu-id="396ef-120">Opis</span><span class="sxs-lookup"><span data-stu-id="396ef-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="396ef-121">TypeName</span><span class="sxs-lookup"><span data-stu-id="396ef-121">TypeName</span></span>|`xs:string`|<span data-ttu-id="396ef-122">Imię i nazwisko CLR typu wywołanej `ErrorHandler`.</span><span class="sxs-lookup"><span data-stu-id="396ef-122">The CLR FullName of the type of the invoked `ErrorHandler`.</span></span>|  
|<span data-ttu-id="396ef-123">Obsługiwane</span><span class="sxs-lookup"><span data-stu-id="396ef-123">Handled</span></span>|`xs:unsignedByte`|<span data-ttu-id="396ef-124">`true` Jeśli program obsługi błędów obsługi błędu, w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="396ef-124">`true` if the error handler handled the error, otherwise `false`.</span></span>|  
|<span data-ttu-id="396ef-125">ExceptionTypeName</span><span class="sxs-lookup"><span data-stu-id="396ef-125">ExceptionTypeName</span></span>|`xs:string`|<span data-ttu-id="396ef-126">Element FullName CLR wyjątku, który został już obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="396ef-126">The CLR FullName of the exception that was being handled.</span></span>|  
|<span data-ttu-id="396ef-127">HostReference</span><span class="sxs-lookup"><span data-stu-id="396ef-127">HostReference</span></span>|`xs:string`|<span data-ttu-id="396ef-128">W przypadku usług hostowanych w sieci Web to pole unikatowo identyfikuje usługę w hierarchii sieci Web.</span><span class="sxs-lookup"><span data-stu-id="396ef-128">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="396ef-129">Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web&#124;ścieżki wirtualnej usługi&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="396ef-129">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="396ef-130">Przykład: "Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService".</span><span class="sxs-lookup"><span data-stu-id="396ef-130">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="396ef-131">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="396ef-131">AppDomain</span></span>|`xs:string`|<span data-ttu-id="396ef-132">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="396ef-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
