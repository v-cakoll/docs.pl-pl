---
title: IHostSecurityManager::SetSecurityContext — Metoda
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.SetSecurityContext
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::SetSecurityContext
helpviewer_keywords:
- SetSecurityContext method [.NET Framework hosting]
- IHostSecurityManager::SetSecurityContext method [.NET Framework hosting]
ms.assetid: e4372384-ee69-48d7-97e0-8fab7866597a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d31aa0dfad70bed31bd72be5029c7bdff0925ba2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59088562"
---
# <a name="ihostsecuritymanagersetsecuritycontext-method"></a><span data-ttu-id="5c657-102">IHostSecurityManager::SetSecurityContext — Metoda</span><span class="sxs-lookup"><span data-stu-id="5c657-102">IHostSecurityManager::SetSecurityContext Method</span></span>
<span data-ttu-id="5c657-103">Ustawia kontekst zabezpieczeń aktualnie wykonywany wątek.</span><span class="sxs-lookup"><span data-stu-id="5c657-103">Sets the security context of the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c657-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5c657-104">Syntax</span></span>  
  
```  
HRESULT SetSecurityContext (  
    [in]  EContextType eContextType,  
    [out] IHostSecurityContext** ppSecurityContext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5c657-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5c657-105">Parameters</span></span>  
 `eContextType`  
 <span data-ttu-id="5c657-106">[in] Jedną z [econtexttype —](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md) wartości, wskazujący typ kontekstu, które środowisko uruchomieniowe języka wspólnego (CLR) jest umieszczenie na hoście.</span><span class="sxs-lookup"><span data-stu-id="5c657-106">[in] One of the [EContextType](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md) values, indicating what type of context the common language runtime (CLR) is placing on the host.</span></span>  
  
 `ppSecurityContext`  
 <span data-ttu-id="5c657-107">[out] Wskaźnik do adresów nowej [ihostsecuritycontext —](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) obiektu.</span><span class="sxs-lookup"><span data-stu-id="5c657-107">[out] A pointer to the address of a new [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5c657-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="5c657-108">Return Value</span></span>  
  
|<span data-ttu-id="5c657-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5c657-109">HRESULT</span></span>|<span data-ttu-id="5c657-110">Opis</span><span class="sxs-lookup"><span data-stu-id="5c657-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5c657-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="5c657-111">S_OK</span></span>|`SetSecurityContext` <span data-ttu-id="5c657-112">pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="5c657-112">returned successfully.</span></span>|  
|<span data-ttu-id="5c657-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5c657-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5c657-114">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="5c657-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5c657-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5c657-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5c657-116">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="5c657-116">The call timed out.</span></span>|  
|<span data-ttu-id="5c657-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5c657-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5c657-118">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="5c657-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5c657-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5c657-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5c657-120">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="5c657-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5c657-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5c657-121">E_FAIL</span></span>|<span data-ttu-id="5c657-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="5c657-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5c657-123">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="5c657-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5c657-124">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="5c657-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5c657-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5c657-125">Remarks</span></span>  
 <span data-ttu-id="5c657-126">CLR wywołuje `SetSecurityContext` w kilku scenariuszach.</span><span class="sxs-lookup"><span data-stu-id="5c657-126">The CLR calls `SetSecurityContext` in several scenarios.</span></span> <span data-ttu-id="5c657-127">Przed rozpoczęciem wykonywania klasy i konstruktory modułu i finalizatorów, środowisko CLR wywołuje `SetSecurityContext` ochrony hosta przed awariami wykonywania.</span><span class="sxs-lookup"><span data-stu-id="5c657-127">Before it executes class and module constructors and finalizers, the CLR calls `SetSecurityContext` to protect the host from execution failures.</span></span> <span data-ttu-id="5c657-128">Następnie resetuje kontekstu zabezpieczeń do pierwotnego stanu po wykonaniu konstruktora lub finalizatora, przy użyciu innego wywołania `SetSecurityContext`.</span><span class="sxs-lookup"><span data-stu-id="5c657-128">It then resets the security context to its original state after execution of the constructor or finalizer, by using another call to `SetSecurityContext`.</span></span> <span data-ttu-id="5c657-129">Podobny wzorzec występuje po ukończeniu operacji We/Wy.</span><span class="sxs-lookup"><span data-stu-id="5c657-129">A similar pattern occurs with I/O completion.</span></span> <span data-ttu-id="5c657-130">Jeśli host implementuje [ihostiocompletionmanager —](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md), CLR wywołuje `SetSecurityContext` po wywołania hosta [iclriocompletionmanager::onComplete —](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md).</span><span class="sxs-lookup"><span data-stu-id="5c657-130">If the host implements [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md), the CLR calls `SetSecurityContext` after the host calls [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md).</span></span>  
  
 <span data-ttu-id="5c657-131">Asynchroniczne momentach wątków roboczych, środowisko CLR wywołuje `SetSecurityContext` w ramach <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> lub w ramach [ihostthreadpoolmanager::QueueUserWorkItem —](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md), w zależności od tego, czy host lub środowiska CLR jest implementacja puli wątków.</span><span class="sxs-lookup"><span data-stu-id="5c657-131">At asynchronous points in worker threads, the CLR calls `SetSecurityContext` within <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> or within [IHostThreadPoolManager::QueueUserWorkItem](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md), depending on whether the host or the CLR is implementing the thread pool.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c657-132">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5c657-132">Requirements</span></span>  
 <span data-ttu-id="5c657-133">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c657-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c657-134">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5c657-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5c657-135">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5c657-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="5c657-136">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="5c657-136">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5c657-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5c657-137">See also</span></span>

- <xref:System.Threading.ThreadPool?displayProperty=nameWithType>
- [<span data-ttu-id="5c657-138">EContextType — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="5c657-138">EContextType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md)
- [<span data-ttu-id="5c657-139">ICLRIoCompletionManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="5c657-139">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="5c657-140">IHostIoCompletionManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="5c657-140">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
- [<span data-ttu-id="5c657-141">IHostSecurityContext — Interfejs</span><span class="sxs-lookup"><span data-stu-id="5c657-141">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="5c657-142">IHostSecurityManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="5c657-142">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
- [<span data-ttu-id="5c657-143">IHostThreadPoolManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="5c657-143">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
