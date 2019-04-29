---
title: 223 — OperationFaulted
ms.date: 03/30/2017
ms.assetid: 2f7d89d7-3a6a-40fe-9610-5424eb6bbf61
ms.openlocfilehash: cf4a455d80a1a0ac09e99bad967c1feba3653842
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61596540"
---
# <a name="223---operationfaulted"></a><span data-ttu-id="d245b-102">223 — OperationFaulted</span><span class="sxs-lookup"><span data-stu-id="d245b-102">223 - OperationFaulted</span></span>
## <a name="properties"></a><span data-ttu-id="d245b-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="d245b-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d245b-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="d245b-104">ID</span></span>|<span data-ttu-id="d245b-105">223</span><span class="sxs-lookup"><span data-stu-id="d245b-105">223</span></span>|  
|<span data-ttu-id="d245b-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="d245b-106">Keywords</span></span>|<span data-ttu-id="d245b-107">EndToEndMonitoring HealthMonitoring, rozwiązywania problemów, modelu ServiceModel</span><span class="sxs-lookup"><span data-stu-id="d245b-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="d245b-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="d245b-108">Level</span></span>|<span data-ttu-id="d245b-109">Ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="d245b-109">Warning</span></span>|  
|<span data-ttu-id="d245b-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="d245b-110">Channel</span></span>|<span data-ttu-id="d245b-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="d245b-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="d245b-112">Opis</span><span class="sxs-lookup"><span data-stu-id="d245b-112">Description</span></span>  
 <span data-ttu-id="d245b-113">To zdarzenie jest emitowane przy domyślny Model usług `OperationInvoker` napotkała wyjątek pochodząca od `FaultException` podczas wywoływania metody.</span><span class="sxs-lookup"><span data-stu-id="d245b-113">This event is emitted when the Service Model's default `OperationInvoker` has encountered an exception deriving from `FaultException` while invoking its method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="d245b-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="d245b-114">Message</span></span>  
 <span data-ttu-id="d245b-115">Metoda "%1" zwróciła wyjątek FaultException —, po wywołaniu przez OperationInvoker.</span><span class="sxs-lookup"><span data-stu-id="d245b-115">The '%1' method threw a FaultException when invoked by the OperationInvoker.</span></span> <span data-ttu-id="d245b-116">Czas trwania wywołania metody wynosiła ms "%2".</span><span class="sxs-lookup"><span data-stu-id="d245b-116">The method call duration was '%2' ms.</span></span>  
  
## <a name="details"></a><span data-ttu-id="d245b-117">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="d245b-117">Details</span></span>  
  
|<span data-ttu-id="d245b-118">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="d245b-118">Data Item Name</span></span>|<span data-ttu-id="d245b-119">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="d245b-119">Data Item Type</span></span>|<span data-ttu-id="d245b-120">Opis</span><span class="sxs-lookup"><span data-stu-id="d245b-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="d245b-121">MethodName</span><span class="sxs-lookup"><span data-stu-id="d245b-121">MethodName</span></span>|`xs:string`|<span data-ttu-id="d245b-122">Nazwa aparatu CLR metody, która została wywołana przez `OperationInvoker`.</span><span class="sxs-lookup"><span data-stu-id="d245b-122">The CLR name of the method that was invoked by the `OperationInvoker`.</span></span>|  
|<span data-ttu-id="d245b-123">Czas trwania</span><span class="sxs-lookup"><span data-stu-id="d245b-123">Duration</span></span>|`xs:long`|<span data-ttu-id="d245b-124">Czas w milisekundach, jaki zajęło `OperationInvoker` było wywołanie metody.</span><span class="sxs-lookup"><span data-stu-id="d245b-124">The time, in milliseconds, that it took the `OperationInvoker` to invoke the method.</span></span>|  
|<span data-ttu-id="d245b-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="d245b-125">HostReference</span></span>|`xs:string`|<span data-ttu-id="d245b-126">W przypadku usług hostowanych w sieci Web to pole jednoznacznie identyfikuje usługę w hierarchii w sieci Web.</span><span class="sxs-lookup"><span data-stu-id="d245b-126">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="d245b-127">Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web&#124;ścieżka wirtualna usługi&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="d245b-127">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="d245b-128">Przykład: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="d245b-128">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="d245b-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="d245b-129">AppDomain</span></span>|`xs:string`|<span data-ttu-id="d245b-130">Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="d245b-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
