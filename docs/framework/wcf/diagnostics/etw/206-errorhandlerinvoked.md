---
title: 206 — ErrorHandlerInvoked
ms.date: 03/30/2017
ms.assetid: 97340f4d-4e09-4e42-a17a-982b3868dbcf
ms.openlocfilehash: 40a92d77c57728249569a854eab8767ff371bca2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781930"
---
# <a name="206---errorhandlerinvoked"></a><span data-ttu-id="210e2-102">206 — ErrorHandlerInvoked</span><span class="sxs-lookup"><span data-stu-id="210e2-102">206 - ErrorHandlerInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="210e2-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="210e2-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="210e2-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="210e2-104">ID</span></span>|<span data-ttu-id="210e2-105">206</span><span class="sxs-lookup"><span data-stu-id="210e2-105">206</span></span>|  
|<span data-ttu-id="210e2-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="210e2-106">Keywords</span></span>|<span data-ttu-id="210e2-107">Rozwiązywanie problemów, modelu ServiceModel</span><span class="sxs-lookup"><span data-stu-id="210e2-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="210e2-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="210e2-108">Level</span></span>|<span data-ttu-id="210e2-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="210e2-109">Information</span></span>|  
|<span data-ttu-id="210e2-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="210e2-110">Channel</span></span>|<span data-ttu-id="210e2-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="210e2-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="210e2-112">Opis</span><span class="sxs-lookup"><span data-stu-id="210e2-112">Description</span></span>  
 <span data-ttu-id="210e2-113">To zdarzenie jest emitowane po `ErrorHandler` umożliwieniu może obsłużyć wyjątek, który wystąpił podczas operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="210e2-113">This event is emitted after an `ErrorHandler` has had an opportunity to handle an exception that occurred in a service operation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="210e2-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="210e2-114">Message</span></span>  
 <span data-ttu-id="210e2-115">Dyspozytor wywoływane ErrorHandler typu "%1" z powodu wyjątku typu "%3".</span><span class="sxs-lookup"><span data-stu-id="210e2-115">The Dispatcher invoked an ErrorHandler of type '%1' with an exception of type '%3'.</span></span> <span data-ttu-id="210e2-116">ErrorHandled == "%2".</span><span class="sxs-lookup"><span data-stu-id="210e2-116">ErrorHandled == '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="210e2-117">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="210e2-117">Details</span></span>  
  
|<span data-ttu-id="210e2-118">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="210e2-118">Data Item Name</span></span>|<span data-ttu-id="210e2-119">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="210e2-119">Data Item Type</span></span>|<span data-ttu-id="210e2-120">Opis</span><span class="sxs-lookup"><span data-stu-id="210e2-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="210e2-121">TypeName</span><span class="sxs-lookup"><span data-stu-id="210e2-121">TypeName</span></span>|`xs:string`|<span data-ttu-id="210e2-122">Imię i nazwisko CLR typu wywołanej `ErrorHandler`.</span><span class="sxs-lookup"><span data-stu-id="210e2-122">The CLR FullName of the type of the invoked `ErrorHandler`.</span></span>|  
|<span data-ttu-id="210e2-123">Obsługiwane</span><span class="sxs-lookup"><span data-stu-id="210e2-123">Handled</span></span>|`xs:unsignedByte`|<span data-ttu-id="210e2-124">`true` Jeśli program obsługi błędów obsługi błędu, w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="210e2-124">`true` if the error handler handled the error, otherwise `false`.</span></span>|  
|<span data-ttu-id="210e2-125">ExceptionTypeName</span><span class="sxs-lookup"><span data-stu-id="210e2-125">ExceptionTypeName</span></span>|`xs:string`|<span data-ttu-id="210e2-126">Pełna nazwa CLR wyjątku, który został jest obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="210e2-126">The CLR FullName of the exception that was being handled.</span></span>|  
|<span data-ttu-id="210e2-127">HostReference</span><span class="sxs-lookup"><span data-stu-id="210e2-127">HostReference</span></span>|`xs:string`|<span data-ttu-id="210e2-128">W przypadku usług hostowanych w sieci Web to pole jednoznacznie identyfikuje usługę w hierarchii w sieci Web.</span><span class="sxs-lookup"><span data-stu-id="210e2-128">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="210e2-129">Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web&#124;ścieżka wirtualna usługi&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="210e2-129">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="210e2-130">Przykład: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="210e2-130">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="210e2-131">AppDomain</span><span class="sxs-lookup"><span data-stu-id="210e2-131">AppDomain</span></span>|`xs:string`|<span data-ttu-id="210e2-132">Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="210e2-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
