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
ms.openlocfilehash: 676a1d50202333203c13fcf916dbb14a6d91fb8f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121444"
---
# <a name="ihostsecuritymanagersetsecuritycontext-method"></a><span data-ttu-id="33ee9-102">IHostSecurityManager::SetSecurityContext — Metoda</span><span class="sxs-lookup"><span data-stu-id="33ee9-102">IHostSecurityManager::SetSecurityContext Method</span></span>
<span data-ttu-id="33ee9-103">Ustawia kontekst zabezpieczeń aktualnie wykonywanego wątku.</span><span class="sxs-lookup"><span data-stu-id="33ee9-103">Sets the security context of the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33ee9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="33ee9-104">Syntax</span></span>  
  
```cpp  
HRESULT SetSecurityContext (  
    [in]  EContextType eContextType,  
    [out] IHostSecurityContext** ppSecurityContext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="33ee9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="33ee9-105">Parameters</span></span>  
 `eContextType`  
 <span data-ttu-id="33ee9-106">podczas Jedna z wartości [EContextType —](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md) , wskazująca, jakiego typu kontekstu środowisko uruchomieniowe języka wspólnego (CLR) umieszcza na hoście.</span><span class="sxs-lookup"><span data-stu-id="33ee9-106">[in] One of the [EContextType](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md) values, indicating what type of context the common language runtime (CLR) is placing on the host.</span></span>  
  
 `ppSecurityContext`  
 <span data-ttu-id="33ee9-107">określoną Wskaźnik do adresu nowego obiektu [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="33ee9-107">[out] A pointer to the address of a new [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="33ee9-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="33ee9-108">Return Value</span></span>  
  
|<span data-ttu-id="33ee9-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="33ee9-109">HRESULT</span></span>|<span data-ttu-id="33ee9-110">Opis</span><span class="sxs-lookup"><span data-stu-id="33ee9-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="33ee9-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="33ee9-111">S_OK</span></span>|<span data-ttu-id="33ee9-112">`SetSecurityContext` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="33ee9-112">`SetSecurityContext` returned successfully.</span></span>|  
|<span data-ttu-id="33ee9-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="33ee9-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="33ee9-114">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="33ee9-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="33ee9-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="33ee9-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="33ee9-116">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="33ee9-116">The call timed out.</span></span>|  
|<span data-ttu-id="33ee9-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="33ee9-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="33ee9-118">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="33ee9-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="33ee9-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="33ee9-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="33ee9-120">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="33ee9-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="33ee9-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="33ee9-121">E_FAIL</span></span>|<span data-ttu-id="33ee9-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="33ee9-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="33ee9-123">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="33ee9-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="33ee9-124">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="33ee9-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="33ee9-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="33ee9-125">Remarks</span></span>  
 <span data-ttu-id="33ee9-126">Środowisko CLR wywołuje `SetSecurityContext` w kilku scenariuszach.</span><span class="sxs-lookup"><span data-stu-id="33ee9-126">The CLR calls `SetSecurityContext` in several scenarios.</span></span> <span data-ttu-id="33ee9-127">Przed wykonaniem konstruktorów klas i modułów oraz finalizatorów, wywołania CLR `SetSecurityContext` do ochrony hosta przed błędami wykonywania.</span><span class="sxs-lookup"><span data-stu-id="33ee9-127">Before it executes class and module constructors and finalizers, the CLR calls `SetSecurityContext` to protect the host from execution failures.</span></span> <span data-ttu-id="33ee9-128">Następnie resetuje kontekst zabezpieczeń do oryginalnego stanu po wykonaniu konstruktora lub finalizatora przy użyciu innego wywołania do `SetSecurityContext`.</span><span class="sxs-lookup"><span data-stu-id="33ee9-128">It then resets the security context to its original state after execution of the constructor or finalizer, by using another call to `SetSecurityContext`.</span></span> <span data-ttu-id="33ee9-129">Podobny wzorzec występuje po zakończeniu operacji we/wy.</span><span class="sxs-lookup"><span data-stu-id="33ee9-129">A similar pattern occurs with I/O completion.</span></span> <span data-ttu-id="33ee9-130">Jeśli Host implementuje [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md), aparat CLR wywołuje `SetSecurityContext` po wywołaniach hosta [ICLRIoCompletionManager:: OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md).</span><span class="sxs-lookup"><span data-stu-id="33ee9-130">If the host implements [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md), the CLR calls `SetSecurityContext` after the host calls [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md).</span></span>  
  
 <span data-ttu-id="33ee9-131">W przypadku asynchronicznych punktów w wątkach roboczych środowisko CLR wywołuje `SetSecurityContext` w <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> lub w [IHostThreadPoolManager:: QueueUserWorkItem](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md), w zależności od tego, czy host lub środowisko CLR implementuje pulę wątków.</span><span class="sxs-lookup"><span data-stu-id="33ee9-131">At asynchronous points in worker threads, the CLR calls `SetSecurityContext` within <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> or within [IHostThreadPoolManager::QueueUserWorkItem](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md), depending on whether the host or the CLR is implementing the thread pool.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33ee9-132">Wymagania</span><span class="sxs-lookup"><span data-stu-id="33ee9-132">Requirements</span></span>  
 <span data-ttu-id="33ee9-133">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="33ee9-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33ee9-134">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="33ee9-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="33ee9-135">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="33ee9-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="33ee9-136">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33ee9-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33ee9-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="33ee9-137">See also</span></span>

- <xref:System.Threading.ThreadPool?displayProperty=nameWithType>
- [<span data-ttu-id="33ee9-138">EContextType, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="33ee9-138">EContextType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md)
- [<span data-ttu-id="33ee9-139">ICLRIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="33ee9-139">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="33ee9-140">IHostIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="33ee9-140">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
- [<span data-ttu-id="33ee9-141">IHostSecurityContext, interfejs</span><span class="sxs-lookup"><span data-stu-id="33ee9-141">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="33ee9-142">IHostSecurityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="33ee9-142">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
- [<span data-ttu-id="33ee9-143">IHostThreadPoolManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="33ee9-143">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
