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
ms.openlocfilehash: 9b7cc41848e41976f388e38bf22c9ea0f90abbae
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121479"
---
# <a name="ihostsecuritymanager-interface"></a><span data-ttu-id="25ec4-102">IHostSecurityManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="25ec4-102">IHostSecurityManager Interface</span></span>
<span data-ttu-id="25ec4-103">Zapewnia metody, które umożliwiają dostęp do i kontrolę nad kontekstem zabezpieczeń aktualnie wykonywanego wątku.</span><span class="sxs-lookup"><span data-stu-id="25ec4-103">Provides methods that allow access to and control over the security context of the currently executing thread.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="25ec4-104">Metody</span><span class="sxs-lookup"><span data-stu-id="25ec4-104">Methods</span></span>  
  
|<span data-ttu-id="25ec4-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="25ec4-105">Method</span></span>|<span data-ttu-id="25ec4-106">Opis</span><span class="sxs-lookup"><span data-stu-id="25ec4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="25ec4-107">GetSecurityContext, metoda</span><span class="sxs-lookup"><span data-stu-id="25ec4-107">GetSecurityContext Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md)|<span data-ttu-id="25ec4-108">Pobiera żądany [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) z hosta.</span><span class="sxs-lookup"><span data-stu-id="25ec4-108">Gets the requested [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) from the host.</span></span>|  
|[<span data-ttu-id="25ec4-109">ImpersonateLoggedOnUser, metoda</span><span class="sxs-lookup"><span data-stu-id="25ec4-109">ImpersonateLoggedOnUser Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md)|<span data-ttu-id="25ec4-110">Żąda wykonania kodu przy użyciu poświadczeń bieżącego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="25ec4-110">Requests that code be executed using the credentials of the current user identity.</span></span>|  
|[<span data-ttu-id="25ec4-111">OpenThreadToken, metoda</span><span class="sxs-lookup"><span data-stu-id="25ec4-111">OpenThreadToken Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-openthreadtoken-method.md)|<span data-ttu-id="25ec4-112">Otwiera token dostępu swobodnego skojarzony z bieżącym wątkiem.</span><span class="sxs-lookup"><span data-stu-id="25ec4-112">Opens the discretionary access token associated with the current thread.</span></span>|  
|[<span data-ttu-id="25ec4-113">RevertToSelf, metoda</span><span class="sxs-lookup"><span data-stu-id="25ec4-113">RevertToSelf Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md)|<span data-ttu-id="25ec4-114">Kończy personifikację bieżącej tożsamości użytkownika i zwraca oryginalny token wątku.</span><span class="sxs-lookup"><span data-stu-id="25ec4-114">Terminates impersonation of the current user identity and returns the original thread token.</span></span>|  
|[<span data-ttu-id="25ec4-115">SetSecurityContext, metoda</span><span class="sxs-lookup"><span data-stu-id="25ec4-115">SetSecurityContext Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setsecuritycontext-method.md)|<span data-ttu-id="25ec4-116">Ustawia kontekst zabezpieczeń aktualnie wykonywanego wątku.</span><span class="sxs-lookup"><span data-stu-id="25ec4-116">Sets the security context for the currently executing thread.</span></span>|  
|[<span data-ttu-id="25ec4-117">SetThreadToken, metoda</span><span class="sxs-lookup"><span data-stu-id="25ec4-117">SetThreadToken Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setthreadtoken-method.md)|<span data-ttu-id="25ec4-118">Ustawia dojście dla aktualnie wykonywanego wątku.</span><span class="sxs-lookup"><span data-stu-id="25ec4-118">Sets a handle for the currently executing thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="25ec4-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="25ec4-119">Remarks</span></span>  
 <span data-ttu-id="25ec4-120">Host może kontrolować cały dostęp kodu do tokenów wątków przez środowisko uruchomieniowe języka wspólnego (CLR) i kod użytkownika.</span><span class="sxs-lookup"><span data-stu-id="25ec4-120">A host can control all code access to thread tokens by both the common language runtime (CLR) and user code.</span></span> <span data-ttu-id="25ec4-121">Może także zapewnić, że pełne informacje kontekstu zabezpieczeń są przesyłane przez operacje asynchroniczne lub punkty kodowe z ograniczonym dostępem do kodu.</span><span class="sxs-lookup"><span data-stu-id="25ec4-121">It can also ensure that complete security context information is passed across asynchronous operations or code points with restricted code access.</span></span> <span data-ttu-id="25ec4-122">`IHostSecurityContext` hermetyzuje informacje kontekstu zabezpieczeń, nieprzezroczyste dla środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="25ec4-122">`IHostSecurityContext` encapsulates this security context information, which is opaque to the CLR.</span></span>  
  
 <span data-ttu-id="25ec4-123">Środowisko CLR obsługuje wewnętrznie zarządzane kontekstu wątku.</span><span class="sxs-lookup"><span data-stu-id="25ec4-123">The CLR handles managed thread context internally.</span></span> <span data-ttu-id="25ec4-124">Wysyła zapytanie do `IHostSecurityManager` specyficznych dla procesu w następujących sytuacjach:</span><span class="sxs-lookup"><span data-stu-id="25ec4-124">It queries the process-specific `IHostSecurityManager` in the following situations:</span></span>  
  
- <span data-ttu-id="25ec4-125">W wątku finalizatora podczas wykonywania finalizatora.</span><span class="sxs-lookup"><span data-stu-id="25ec4-125">On the finalizer thread, during finalizer execution.</span></span>  
  
- <span data-ttu-id="25ec4-126">Podczas wykonywania konstruktora klasy i modułu.</span><span class="sxs-lookup"><span data-stu-id="25ec4-126">During class and module constructor execution.</span></span>  
  
- <span data-ttu-id="25ec4-127">W przypadku asynchronicznych punktów w wątku roboczym w wywołaniach metody [IHostThreadPoolManager:: QueueUserWorkItem](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md) .</span><span class="sxs-lookup"><span data-stu-id="25ec4-127">At asynchronous points on the worker thread, in calls to the [IHostThreadPoolManager::QueueUserWorkItem](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md) method.</span></span>  
  
- <span data-ttu-id="25ec4-128">W trakcie obsługi portów zakończenia we/wy.</span><span class="sxs-lookup"><span data-stu-id="25ec4-128">In servicing of I/O completion ports.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25ec4-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="25ec4-129">Requirements</span></span>  
 <span data-ttu-id="25ec4-130">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25ec4-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25ec4-131">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="25ec4-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="25ec4-132">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="25ec4-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="25ec4-133">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25ec4-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25ec4-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="25ec4-134">See also</span></span>

- [<span data-ttu-id="25ec4-135">IHostSecurityContext, interfejs</span><span class="sxs-lookup"><span data-stu-id="25ec4-135">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="25ec4-136">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="25ec4-136">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
