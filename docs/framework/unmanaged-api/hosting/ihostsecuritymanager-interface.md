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
ms.openlocfilehash: a2c71f32dfd190e188bb28aad5d51c72160eb4bc
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64603239"
---
# <a name="ihostsecuritymanager-interface"></a><span data-ttu-id="25bbc-102">IHostSecurityManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="25bbc-102">IHostSecurityManager Interface</span></span>
<span data-ttu-id="25bbc-103">Udostępnia metody, które umożliwiają dostęp do i kontrolę nad kontekstu zabezpieczeń aktualnie wykonywany wątek.</span><span class="sxs-lookup"><span data-stu-id="25bbc-103">Provides methods that allow access to and control over the security context of the currently executing thread.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="25bbc-104">Metody</span><span class="sxs-lookup"><span data-stu-id="25bbc-104">Methods</span></span>  
  
|<span data-ttu-id="25bbc-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="25bbc-105">Method</span></span>|<span data-ttu-id="25bbc-106">Opis</span><span class="sxs-lookup"><span data-stu-id="25bbc-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="25bbc-107">GetSecurityContext, metoda</span><span class="sxs-lookup"><span data-stu-id="25bbc-107">GetSecurityContext Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md)|<span data-ttu-id="25bbc-108">Pobiera żądany [ihostsecuritycontext —](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) z hosta.</span><span class="sxs-lookup"><span data-stu-id="25bbc-108">Gets the requested [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) from the host.</span></span>|  
|[<span data-ttu-id="25bbc-109">ImpersonateLoggedOnUser, metoda</span><span class="sxs-lookup"><span data-stu-id="25bbc-109">ImpersonateLoggedOnUser Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md)|<span data-ttu-id="25bbc-110">Żądania, kod można wykonać przy użyciu poświadczeń bieżącej tożsamości użytkownika.</span><span class="sxs-lookup"><span data-stu-id="25bbc-110">Requests that code be executed using the credentials of the current user identity.</span></span>|  
|[<span data-ttu-id="25bbc-111">OpenThreadToken, metoda</span><span class="sxs-lookup"><span data-stu-id="25bbc-111">OpenThreadToken Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-openthreadtoken-method.md)|<span data-ttu-id="25bbc-112">Zostanie otwarty token dostępu skojarzone z bieżącym wątkiem.</span><span class="sxs-lookup"><span data-stu-id="25bbc-112">Opens the discretionary access token associated with the current thread.</span></span>|  
|[<span data-ttu-id="25bbc-113">RevertToSelf, metoda</span><span class="sxs-lookup"><span data-stu-id="25bbc-113">RevertToSelf Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md)|<span data-ttu-id="25bbc-114">Kończy działanie personifikacji bieżącej tożsamości użytkownika, a następnie zwraca oryginalny tokenu wątku.</span><span class="sxs-lookup"><span data-stu-id="25bbc-114">Terminates impersonation of the current user identity and returns the original thread token.</span></span>|  
|[<span data-ttu-id="25bbc-115">SetSecurityContext, metoda</span><span class="sxs-lookup"><span data-stu-id="25bbc-115">SetSecurityContext Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setsecuritycontext-method.md)|<span data-ttu-id="25bbc-116">Ustawia kontekst zabezpieczeń dla aktualnie wykonywany wątek.</span><span class="sxs-lookup"><span data-stu-id="25bbc-116">Sets the security context for the currently executing thread.</span></span>|  
|[<span data-ttu-id="25bbc-117">SetThreadToken, metoda</span><span class="sxs-lookup"><span data-stu-id="25bbc-117">SetThreadToken Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setthreadtoken-method.md)|<span data-ttu-id="25bbc-118">Ustawia obsługi do aktualnie wykonywany wątek.</span><span class="sxs-lookup"><span data-stu-id="25bbc-118">Sets a handle for the currently executing thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="25bbc-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="25bbc-119">Remarks</span></span>  
 <span data-ttu-id="25bbc-120">Hosta można kontrolować wszelki dostęp kodu do tokenów wątku przez środowisko uruchomieniowe języka wspólnego (CLR) i kod użytkownika.</span><span class="sxs-lookup"><span data-stu-id="25bbc-120">A host can control all code access to thread tokens by both the common language runtime (CLR) and user code.</span></span> <span data-ttu-id="25bbc-121">Można to także zapewnić pełne zabezpieczenia informacji kontekstowych jest przekazywany w operacji asynchronicznych lub punkty kodowe dostęp ograniczony kod.</span><span class="sxs-lookup"><span data-stu-id="25bbc-121">It can also ensure that complete security context information is passed across asynchronous operations or code points with restricted code access.</span></span> <span data-ttu-id="25bbc-122">`IHostSecurityContext` hermetyzuje informacje kontekstu zabezpieczeń, która jest nieprzezroczysta dla środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="25bbc-122">`IHostSecurityContext` encapsulates this security context information, which is opaque to the CLR.</span></span>  
  
 <span data-ttu-id="25bbc-123">Środowisko CLR obsługuje kontekstu wątków zarządzanych wewnętrznie.</span><span class="sxs-lookup"><span data-stu-id="25bbc-123">The CLR handles managed thread context internally.</span></span> <span data-ttu-id="25bbc-124">Wysyła zapytanie dotyczące procesu `IHostSecurityManager` w następujących sytuacjach:</span><span class="sxs-lookup"><span data-stu-id="25bbc-124">It queries the process-specific `IHostSecurityManager` in the following situations:</span></span>  
  
- <span data-ttu-id="25bbc-125">W wątku finalizatora podczas wykonywania finalizatora.</span><span class="sxs-lookup"><span data-stu-id="25bbc-125">On the finalizer thread, during finalizer execution.</span></span>  
  
- <span data-ttu-id="25bbc-126">Podczas wykonywania konstruktora klasy i moduł.</span><span class="sxs-lookup"><span data-stu-id="25bbc-126">During class and module constructor execution.</span></span>  
  
- <span data-ttu-id="25bbc-127">W punktach asynchroniczne w wątku roboczego, w wywołaniach [ihostthreadpoolmanager::QueueUserWorkItem —](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="25bbc-127">At asynchronous points on the worker thread, in calls to the [IHostThreadPoolManager::QueueUserWorkItem](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md) method.</span></span>  
  
- <span data-ttu-id="25bbc-128">Obsługę portów zakończenia operacji We/Wy.</span><span class="sxs-lookup"><span data-stu-id="25bbc-128">In servicing of I/O completion ports.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25bbc-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="25bbc-129">Requirements</span></span>  
 <span data-ttu-id="25bbc-130">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25bbc-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25bbc-131">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="25bbc-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="25bbc-132">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="25bbc-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="25bbc-133">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25bbc-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25bbc-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="25bbc-134">See also</span></span>

- [<span data-ttu-id="25bbc-135">IHostSecurityContext, interfejs</span><span class="sxs-lookup"><span data-stu-id="25bbc-135">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="25bbc-136">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="25bbc-136">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
