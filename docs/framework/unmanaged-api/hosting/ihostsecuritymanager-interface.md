---
title: IHostSecurityManager — Interfejs
ms.date: 03/30/2017
api_name:
- IHostSecurityManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager
helpviewer_keywords:
- IHostSecurityManager interface [.NET Framework hosting]
ms.assetid: c3be2cbd-2d93-438b-9888-9a0251b63c03
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f45379fe8640ef7e7b3917bac8d10ca956d75ffb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59223761"
---
# <a name="ihostsecuritymanager-interface"></a><span data-ttu-id="78129-102">IHostSecurityManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="78129-102">IHostSecurityManager Interface</span></span>
<span data-ttu-id="78129-103">Udostępnia metody, które umożliwiają dostęp do i kontrolę nad kontekstu zabezpieczeń aktualnie wykonywany wątek.</span><span class="sxs-lookup"><span data-stu-id="78129-103">Provides methods that allow access to and control over the security context of the currently executing thread.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="78129-104">Metody</span><span class="sxs-lookup"><span data-stu-id="78129-104">Methods</span></span>  
  
|<span data-ttu-id="78129-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="78129-105">Method</span></span>|<span data-ttu-id="78129-106">Opis</span><span class="sxs-lookup"><span data-stu-id="78129-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="78129-107">GetSecurityContext, metoda</span><span class="sxs-lookup"><span data-stu-id="78129-107">GetSecurityContext Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md)|<span data-ttu-id="78129-108">Pobiera żądany [ihostsecuritycontext —](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) z hosta.</span><span class="sxs-lookup"><span data-stu-id="78129-108">Gets the requested [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) from the host.</span></span>|  
|[<span data-ttu-id="78129-109">ImpersonateLoggedOnUser, metoda</span><span class="sxs-lookup"><span data-stu-id="78129-109">ImpersonateLoggedOnUser Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md)|<span data-ttu-id="78129-110">Żądania, kod można wykonać przy użyciu poświadczeń bieżącej tożsamości użytkownika.</span><span class="sxs-lookup"><span data-stu-id="78129-110">Requests that code be executed using the credentials of the current user identity.</span></span>|  
|[<span data-ttu-id="78129-111">OpenThreadToken, metoda</span><span class="sxs-lookup"><span data-stu-id="78129-111">OpenThreadToken Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-openthreadtoken-method.md)|<span data-ttu-id="78129-112">Zostanie otwarty token dostępu skojarzone z bieżącym wątkiem.</span><span class="sxs-lookup"><span data-stu-id="78129-112">Opens the discretionary access token associated with the current thread.</span></span>|  
|[<span data-ttu-id="78129-113">RevertToSelf, metoda</span><span class="sxs-lookup"><span data-stu-id="78129-113">RevertToSelf Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md)|<span data-ttu-id="78129-114">Kończy działanie personifikacji bieżącej tożsamości użytkownika, a następnie zwraca oryginalny tokenu wątku.</span><span class="sxs-lookup"><span data-stu-id="78129-114">Terminates impersonation of the current user identity and returns the original thread token.</span></span>|  
|[<span data-ttu-id="78129-115">SetSecurityContext, metoda</span><span class="sxs-lookup"><span data-stu-id="78129-115">SetSecurityContext Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setsecuritycontext-method.md)|<span data-ttu-id="78129-116">Ustawia kontekst zabezpieczeń dla aktualnie wykonywany wątek.</span><span class="sxs-lookup"><span data-stu-id="78129-116">Sets the security context for the currently executing thread.</span></span>|  
|[<span data-ttu-id="78129-117">SetThreadToken, metoda</span><span class="sxs-lookup"><span data-stu-id="78129-117">SetThreadToken Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setthreadtoken-method.md)|<span data-ttu-id="78129-118">Ustawia obsługi do aktualnie wykonywany wątek.</span><span class="sxs-lookup"><span data-stu-id="78129-118">Sets a handle for the currently executing thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="78129-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="78129-119">Remarks</span></span>  
 <span data-ttu-id="78129-120">Hosta można kontrolować wszelki dostęp kodu do tokenów wątku przez środowisko uruchomieniowe języka wspólnego (CLR) i kod użytkownika.</span><span class="sxs-lookup"><span data-stu-id="78129-120">A host can control all code access to thread tokens by both the common language runtime (CLR) and user code.</span></span> <span data-ttu-id="78129-121">Można to także zapewnić pełne zabezpieczenia informacji kontekstowych jest przekazywany w operacji asynchronicznych lub punkty kodowe dostęp ograniczony kod.</span><span class="sxs-lookup"><span data-stu-id="78129-121">It can also ensure that complete security context information is passed across asynchronous operations or code points with restricted code access.</span></span> `IHostSecurityContext` <span data-ttu-id="78129-122">hermetyzuje informacje kontekstu zabezpieczeń, która jest nieprzezroczysta dla środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="78129-122">encapsulates this security context information, which is opaque to the CLR.</span></span>  
  
 <span data-ttu-id="78129-123">Środowisko CLR obsługuje kontekstu wątków zarządzanych wewnętrznie.</span><span class="sxs-lookup"><span data-stu-id="78129-123">The CLR handles managed thread context internally.</span></span> <span data-ttu-id="78129-124">Wysyła zapytanie dotyczące procesu `IHostSecurityManager` w następujących sytuacjach:</span><span class="sxs-lookup"><span data-stu-id="78129-124">It queries the process-specific `IHostSecurityManager` in the following situations:</span></span>  
  
-   <span data-ttu-id="78129-125">W wątku finalizatora podczas wykonywania finalizatora.</span><span class="sxs-lookup"><span data-stu-id="78129-125">On the finalizer thread, during finalizer execution.</span></span>  
  
-   <span data-ttu-id="78129-126">Podczas wykonywania konstruktora klasy i moduł.</span><span class="sxs-lookup"><span data-stu-id="78129-126">During class and module constructor execution.</span></span>  
  
-   <span data-ttu-id="78129-127">W punktach asynchroniczne w wątku roboczego, w wywołaniach [ihostthreadpoolmanager::QueueUserWorkItem —](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="78129-127">At asynchronous points on the worker thread, in calls to the [IHostThreadPoolManager::QueueUserWorkItem](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md) method.</span></span>  
  
-   <span data-ttu-id="78129-128">Obsługę portów zakończenia operacji We/Wy.</span><span class="sxs-lookup"><span data-stu-id="78129-128">In servicing of I/O completion ports.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78129-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="78129-129">Requirements</span></span>  
 <span data-ttu-id="78129-130">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78129-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78129-131">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="78129-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="78129-132">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="78129-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="78129-133">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="78129-133">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="78129-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="78129-134">See also</span></span>

- [<span data-ttu-id="78129-135">IHostSecurityContext — Interfejs</span><span class="sxs-lookup"><span data-stu-id="78129-135">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="78129-136">Hosting — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="78129-136">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
