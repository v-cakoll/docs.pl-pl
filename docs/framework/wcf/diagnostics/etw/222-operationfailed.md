---
title: 222 — OperationFailed
ms.date: 03/30/2017
ms.assetid: 6b530ded-8f20-4d78-8bfe-1875276df6ba
ms.openlocfilehash: c49aad0f93ce47b66306d75741267530dc6d3fe5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="222---operationfailed"></a><span data-ttu-id="3aa3e-102">222 — OperationFailed</span><span class="sxs-lookup"><span data-stu-id="3aa3e-102">222 - OperationFailed</span></span>
## <a name="properties"></a><span data-ttu-id="3aa3e-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="3aa3e-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3aa3e-104">ID</span><span class="sxs-lookup"><span data-stu-id="3aa3e-104">ID</span></span>|<span data-ttu-id="3aa3e-105">222</span><span class="sxs-lookup"><span data-stu-id="3aa3e-105">222</span></span>|  
|<span data-ttu-id="3aa3e-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="3aa3e-106">Keywords</span></span>|<span data-ttu-id="3aa3e-107">EndToEndMonitoring HealthMonitoring, rozwiązywania problemów, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="3aa3e-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="3aa3e-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="3aa3e-108">Level</span></span>|<span data-ttu-id="3aa3e-109">Ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="3aa3e-109">Warning</span></span>|  
|<span data-ttu-id="3aa3e-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="3aa3e-110">Channel</span></span>|<span data-ttu-id="3aa3e-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="3aa3e-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="3aa3e-112">Opis</span><span class="sxs-lookup"><span data-stu-id="3aa3e-112">Description</span></span>  
 <span data-ttu-id="3aa3e-113">To zdarzenie jest emitowany gdy domyślny Model usługi `OperationInvoker` napotkał wyjątek podczas wywoływania metody.</span><span class="sxs-lookup"><span data-stu-id="3aa3e-113">This event is emitted when the Service Model's default `OperationInvoker` has encountered an exception while invoking its method.</span></span> <span data-ttu-id="3aa3e-114">Uwaga tego wyjątki pochodzące z `FaultException` spowodować to zdarzenie nie być emitowane.</span><span class="sxs-lookup"><span data-stu-id="3aa3e-114">Note that exceptions that derive from `FaultException` cause this event to not be emitted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="3aa3e-115">Komunikat</span><span class="sxs-lookup"><span data-stu-id="3aa3e-115">Message</span></span>  
 <span data-ttu-id="3aa3e-116">Metoda "%1" spowodowała zgłoszenie nieobsługiwanego wyjątku, gdy została wywołana przez obiekt OperationInvoker.</span><span class="sxs-lookup"><span data-stu-id="3aa3e-116">The '%1' method threw an unhandled exception when invoked by the OperationInvoker.</span></span> <span data-ttu-id="3aa3e-117">Wywołanie metody trwało "%2" ms.</span><span class="sxs-lookup"><span data-stu-id="3aa3e-117">The method call duration was '%2' ms.</span></span>  
  
## <a name="details"></a><span data-ttu-id="3aa3e-118">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="3aa3e-118">Details</span></span>  
  
|<span data-ttu-id="3aa3e-119">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="3aa3e-119">Data Item Name</span></span>|<span data-ttu-id="3aa3e-120">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="3aa3e-120">Data Item Type</span></span>|<span data-ttu-id="3aa3e-121">Opis</span><span class="sxs-lookup"><span data-stu-id="3aa3e-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="3aa3e-122">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="3aa3e-122">Method Name</span></span>|`xs:string`|<span data-ttu-id="3aa3e-123">Nazwa metody, która została wywołana przez CLR `OperationInvoker`.</span><span class="sxs-lookup"><span data-stu-id="3aa3e-123">The CLR name of the method that was invoked by the `OperationInvoker`.</span></span>|  
|<span data-ttu-id="3aa3e-124">Czas trwania</span><span class="sxs-lookup"><span data-stu-id="3aa3e-124">Duration</span></span>|`xs:long`|<span data-ttu-id="3aa3e-125">Czas (w milisekundach), jaką trwało `OperationInvoker` można wywołać metody.</span><span class="sxs-lookup"><span data-stu-id="3aa3e-125">The time, in milliseconds, that it took the `OperationInvoker` to invoke the method.</span></span>|  
|<span data-ttu-id="3aa3e-126">HostReference</span><span class="sxs-lookup"><span data-stu-id="3aa3e-126">HostReference</span></span>|`xs:string`|<span data-ttu-id="3aa3e-127">W przypadku usług hostowanych w sieci Web to pole unikatowo identyfikuje usługę w hierarchii sieci Web.</span><span class="sxs-lookup"><span data-stu-id="3aa3e-127">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="3aa3e-128">Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web&#124;ścieżki wirtualnej usługi&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="3aa3e-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="3aa3e-129">Przykład: "Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService".</span><span class="sxs-lookup"><span data-stu-id="3aa3e-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="3aa3e-130">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="3aa3e-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="3aa3e-131">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="3aa3e-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
