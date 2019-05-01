---
title: 214 — OperationCompleted
ms.date: 03/30/2017
ms.assetid: a6287eef-023f-4816-813c-1802c82366df
ms.openlocfilehash: da1021b674b555b683f8f745f5a2a0073c9567e8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61968002"
---
# <a name="214---operationcompleted"></a><span data-ttu-id="7ddf9-102">214 — OperationCompleted</span><span class="sxs-lookup"><span data-stu-id="7ddf9-102">214 - OperationCompleted</span></span>
## <a name="properties"></a><span data-ttu-id="7ddf9-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="7ddf9-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7ddf9-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="7ddf9-104">ID</span></span>|<span data-ttu-id="7ddf9-105">214</span><span class="sxs-lookup"><span data-stu-id="7ddf9-105">214</span></span>|  
|<span data-ttu-id="7ddf9-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="7ddf9-106">Keywords</span></span>|<span data-ttu-id="7ddf9-107">HealthMonitoring EndToEndMonitoring, rozwiązywania problemów, modelu ServiceModel</span><span class="sxs-lookup"><span data-stu-id="7ddf9-107">HealthMonitoring, EndToEndMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="7ddf9-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="7ddf9-108">Level</span></span>|<span data-ttu-id="7ddf9-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="7ddf9-109">Information</span></span>|  
|<span data-ttu-id="7ddf9-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="7ddf9-110">Channel</span></span>|<span data-ttu-id="7ddf9-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="7ddf9-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="7ddf9-112">Opis</span><span class="sxs-lookup"><span data-stu-id="7ddf9-112">Description</span></span>  
 <span data-ttu-id="7ddf9-113">To zdarzenie jest emitowane przy domyślny Model usług `OperationInvoker` zakończone wywołanie do metody bez tej metody, zostanie zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="7ddf9-113">This event is emitted when the Service Model's default `OperationInvoker` has completed a call to a method without that method throwing an exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="7ddf9-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="7ddf9-114">Message</span></span>  
 <span data-ttu-id="7ddf9-115">OperationInvoker wykonać wywołanie metody "%1".</span><span class="sxs-lookup"><span data-stu-id="7ddf9-115">An OperationInvoker completed the call to the '%1' method.</span></span> <span data-ttu-id="7ddf9-116">Czas trwania wywołania metody wynosiła ms "%2".</span><span class="sxs-lookup"><span data-stu-id="7ddf9-116">The method call duration was '%2' ms.</span></span>  
  
## <a name="details"></a><span data-ttu-id="7ddf9-117">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="7ddf9-117">Details</span></span>  
  
|<span data-ttu-id="7ddf9-118">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="7ddf9-118">Data Item Name</span></span>|<span data-ttu-id="7ddf9-119">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="7ddf9-119">Data Item Type</span></span>|<span data-ttu-id="7ddf9-120">Opis</span><span class="sxs-lookup"><span data-stu-id="7ddf9-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="7ddf9-121">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="7ddf9-121">Method Name</span></span>|`xs:string`|<span data-ttu-id="7ddf9-122">Nazwa aparatu CLR metody, która została wywołana przez `OperationInvoker`.</span><span class="sxs-lookup"><span data-stu-id="7ddf9-122">The CLR name of the method that was invoked by the `OperationInvoker`.</span></span>|  
|<span data-ttu-id="7ddf9-123">Czas trwania</span><span class="sxs-lookup"><span data-stu-id="7ddf9-123">Duration</span></span>|`xs:long`|<span data-ttu-id="7ddf9-124">Czas w milisekundach, jaki zajęło `OperationInvoker` było wywołanie metody.</span><span class="sxs-lookup"><span data-stu-id="7ddf9-124">The time, in milliseconds, that it took the `OperationInvoker` to invoke the method.</span></span>|  
|<span data-ttu-id="7ddf9-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="7ddf9-125">HostReference</span></span>|`xs:string`|<span data-ttu-id="7ddf9-126">W przypadku usług hostowanych w sieci web to pole jednoznacznie identyfikuje usługę w hierarchii w sieci Web.</span><span class="sxs-lookup"><span data-stu-id="7ddf9-126">For web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="7ddf9-127">Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web&#124;ścieżka wirtualna usługi&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="7ddf9-127">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="7ddf9-128">Przykład: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="7ddf9-128">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="7ddf9-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="7ddf9-129">AppDomain</span></span>|`xs:string`|<span data-ttu-id="7ddf9-130">Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="7ddf9-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
