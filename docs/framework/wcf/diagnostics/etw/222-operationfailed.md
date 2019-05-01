---
title: 222 — OperationFailed
ms.date: 03/30/2017
ms.assetid: 6b530ded-8f20-4d78-8bfe-1875276df6ba
ms.openlocfilehash: c49aad0f93ce47b66306d75741267530dc6d3fe5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781644"
---
# <a name="222---operationfailed"></a><span data-ttu-id="083e4-102">222 — OperationFailed</span><span class="sxs-lookup"><span data-stu-id="083e4-102">222 - OperationFailed</span></span>
## <a name="properties"></a><span data-ttu-id="083e4-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="083e4-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="083e4-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="083e4-104">ID</span></span>|<span data-ttu-id="083e4-105">222</span><span class="sxs-lookup"><span data-stu-id="083e4-105">222</span></span>|  
|<span data-ttu-id="083e4-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="083e4-106">Keywords</span></span>|<span data-ttu-id="083e4-107">EndToEndMonitoring HealthMonitoring, rozwiązywania problemów, modelu ServiceModel</span><span class="sxs-lookup"><span data-stu-id="083e4-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="083e4-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="083e4-108">Level</span></span>|<span data-ttu-id="083e4-109">Ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="083e4-109">Warning</span></span>|  
|<span data-ttu-id="083e4-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="083e4-110">Channel</span></span>|<span data-ttu-id="083e4-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="083e4-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="083e4-112">Opis</span><span class="sxs-lookup"><span data-stu-id="083e4-112">Description</span></span>  
 <span data-ttu-id="083e4-113">To zdarzenie jest emitowane przy domyślny Model usług `OperationInvoker` napotkał wyjątek podczas wywoływania jego metody.</span><span class="sxs-lookup"><span data-stu-id="083e4-113">This event is emitted when the Service Model's default `OperationInvoker` has encountered an exception while invoking its method.</span></span> <span data-ttu-id="083e4-114">Uwaga tego wyjątki, które wynikają z `FaultException` spowodować, że to zdarzenie nie jest emitowany.</span><span class="sxs-lookup"><span data-stu-id="083e4-114">Note that exceptions that derive from `FaultException` cause this event to not be emitted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="083e4-115">Komunikat</span><span class="sxs-lookup"><span data-stu-id="083e4-115">Message</span></span>  
 <span data-ttu-id="083e4-116">Metoda "%1" spowodowała nieobsługiwany wyjątek podczas wywoływania przez OperationInvoker.</span><span class="sxs-lookup"><span data-stu-id="083e4-116">The '%1' method threw an unhandled exception when invoked by the OperationInvoker.</span></span> <span data-ttu-id="083e4-117">Czas trwania wywołania metody wynosiła ms "%2".</span><span class="sxs-lookup"><span data-stu-id="083e4-117">The method call duration was '%2' ms.</span></span>  
  
## <a name="details"></a><span data-ttu-id="083e4-118">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="083e4-118">Details</span></span>  
  
|<span data-ttu-id="083e4-119">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="083e4-119">Data Item Name</span></span>|<span data-ttu-id="083e4-120">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="083e4-120">Data Item Type</span></span>|<span data-ttu-id="083e4-121">Opis</span><span class="sxs-lookup"><span data-stu-id="083e4-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="083e4-122">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="083e4-122">Method Name</span></span>|`xs:string`|<span data-ttu-id="083e4-123">Nazwa aparatu CLR metody, która została wywołana przez `OperationInvoker`.</span><span class="sxs-lookup"><span data-stu-id="083e4-123">The CLR name of the method that was invoked by the `OperationInvoker`.</span></span>|  
|<span data-ttu-id="083e4-124">Czas trwania</span><span class="sxs-lookup"><span data-stu-id="083e4-124">Duration</span></span>|`xs:long`|<span data-ttu-id="083e4-125">Czas w milisekundach, jaki zajęło `OperationInvoker` było wywołanie metody.</span><span class="sxs-lookup"><span data-stu-id="083e4-125">The time, in milliseconds, that it took the `OperationInvoker` to invoke the method.</span></span>|  
|<span data-ttu-id="083e4-126">HostReference</span><span class="sxs-lookup"><span data-stu-id="083e4-126">HostReference</span></span>|`xs:string`|<span data-ttu-id="083e4-127">W przypadku usług hostowanych w sieci Web to pole jednoznacznie identyfikuje usługę w hierarchii w sieci Web.</span><span class="sxs-lookup"><span data-stu-id="083e4-127">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="083e4-128">Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web&#124;ścieżka wirtualna usługi&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="083e4-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="083e4-129">Przykład: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="083e4-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="083e4-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="083e4-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="083e4-131">Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="083e4-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
