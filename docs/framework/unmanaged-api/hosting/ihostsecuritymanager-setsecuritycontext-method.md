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
ms.openlocfilehash: 6a6b4d0351e22026dc873aad8281d0259d871a14
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501485"
---
# <a name="ihostsecuritymanagersetsecuritycontext-method"></a><span data-ttu-id="0ec0d-102">IHostSecurityManager::SetSecurityContext — Metoda</span><span class="sxs-lookup"><span data-stu-id="0ec0d-102">IHostSecurityManager::SetSecurityContext Method</span></span>
<span data-ttu-id="0ec0d-103">Ustawia kontekst zabezpieczeń aktualnie wykonywanego wątku.</span><span class="sxs-lookup"><span data-stu-id="0ec0d-103">Sets the security context of the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ec0d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0ec0d-104">Syntax</span></span>  
  
```cpp  
HRESULT SetSecurityContext (  
    [in]  EContextType eContextType,  
    [out] IHostSecurityContext** ppSecurityContext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0ec0d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0ec0d-105">Parameters</span></span>  
 `eContextType`  
 <span data-ttu-id="0ec0d-106">podczas Jedna z wartości [EContextType —](econtexttype-enumeration.md) , wskazująca, jakiego typu kontekstu środowisko uruchomieniowe języka wspólnego (CLR) umieszcza na hoście.</span><span class="sxs-lookup"><span data-stu-id="0ec0d-106">[in] One of the [EContextType](econtexttype-enumeration.md) values, indicating what type of context the common language runtime (CLR) is placing on the host.</span></span>  
  
 `ppSecurityContext`  
 <span data-ttu-id="0ec0d-107">określoną Wskaźnik do adresu nowego obiektu [IHostSecurityContext](ihostsecuritycontext-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="0ec0d-107">[out] A pointer to the address of a new [IHostSecurityContext](ihostsecuritycontext-interface.md) object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0ec0d-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="0ec0d-108">Return Value</span></span>  
  
|<span data-ttu-id="0ec0d-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0ec0d-109">HRESULT</span></span>|<span data-ttu-id="0ec0d-110">Opis</span><span class="sxs-lookup"><span data-stu-id="0ec0d-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0ec0d-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="0ec0d-111">S_OK</span></span>|<span data-ttu-id="0ec0d-112">`SetSecurityContext`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="0ec0d-112">`SetSecurityContext` returned successfully.</span></span>|  
|<span data-ttu-id="0ec0d-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0ec0d-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0ec0d-114">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="0ec0d-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0ec0d-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0ec0d-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0ec0d-116">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="0ec0d-116">The call timed out.</span></span>|  
|<span data-ttu-id="0ec0d-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0ec0d-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0ec0d-118">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="0ec0d-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0ec0d-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0ec0d-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0ec0d-120">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="0ec0d-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0ec0d-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0ec0d-121">E_FAIL</span></span>|<span data-ttu-id="0ec0d-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="0ec0d-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0ec0d-123">Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="0ec0d-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0ec0d-124">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0ec0d-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0ec0d-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0ec0d-125">Remarks</span></span>  
 <span data-ttu-id="0ec0d-126">Środowisko CLR wywołuje `SetSecurityContext` kilka scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="0ec0d-126">The CLR calls `SetSecurityContext` in several scenarios.</span></span> <span data-ttu-id="0ec0d-127">Przed wykonaniem konstruktorów klas i modułów oraz finalizatorów, środowisko CLR wywołuje `SetSecurityContext` w celu ochrony hosta przed błędami wykonania.</span><span class="sxs-lookup"><span data-stu-id="0ec0d-127">Before it executes class and module constructors and finalizers, the CLR calls `SetSecurityContext` to protect the host from execution failures.</span></span> <span data-ttu-id="0ec0d-128">Następnie resetuje kontekst zabezpieczeń do oryginalnego stanu po wykonaniu konstruktora lub finalizatora przy użyciu innego wywołania do `SetSecurityContext` .</span><span class="sxs-lookup"><span data-stu-id="0ec0d-128">It then resets the security context to its original state after execution of the constructor or finalizer, by using another call to `SetSecurityContext`.</span></span> <span data-ttu-id="0ec0d-129">Podobny wzorzec występuje po zakończeniu operacji we/wy.</span><span class="sxs-lookup"><span data-stu-id="0ec0d-129">A similar pattern occurs with I/O completion.</span></span> <span data-ttu-id="0ec0d-130">Jeśli Host implementuje [IHostIoCompletionManager](ihostiocompletionmanager-interface.md), środowisko CLR wywołuje się `SetSecurityContext` po wywołaniach hosta [ICLRIoCompletionManager:: OnComplete](iclriocompletionmanager-oncomplete-method.md).</span><span class="sxs-lookup"><span data-stu-id="0ec0d-130">If the host implements [IHostIoCompletionManager](ihostiocompletionmanager-interface.md), the CLR calls `SetSecurityContext` after the host calls [ICLRIoCompletionManager::OnComplete](iclriocompletionmanager-oncomplete-method.md).</span></span>  
  
 <span data-ttu-id="0ec0d-131">W przypadku asynchronicznych punktów w wątkach roboczych, środowisko CLR wywołuje `SetSecurityContext` wewnątrz <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> lub w [IHostThreadPoolManager:: QueueUserWorkItem](ihostthreadpoolmanager-queueuserworkitem-method.md), w zależności od tego, czy host lub środowisko CLR implementuje pulę wątków.</span><span class="sxs-lookup"><span data-stu-id="0ec0d-131">At asynchronous points in worker threads, the CLR calls `SetSecurityContext` within <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> or within [IHostThreadPoolManager::QueueUserWorkItem](ihostthreadpoolmanager-queueuserworkitem-method.md), depending on whether the host or the CLR is implementing the thread pool.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ec0d-132">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0ec0d-132">Requirements</span></span>  
 <span data-ttu-id="0ec0d-133">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0ec0d-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ec0d-134">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0ec0d-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0ec0d-135">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="0ec0d-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0ec0d-136">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ec0d-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ec0d-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0ec0d-137">See also</span></span>

- <xref:System.Threading.ThreadPool?displayProperty=nameWithType>
- [<span data-ttu-id="0ec0d-138">EContextType, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="0ec0d-138">EContextType Enumeration</span></span>](econtexttype-enumeration.md)
- [<span data-ttu-id="0ec0d-139">ICLRIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="0ec0d-139">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="0ec0d-140">IHostIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="0ec0d-140">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
- [<span data-ttu-id="0ec0d-141">IHostSecurityContext — Interfejs</span><span class="sxs-lookup"><span data-stu-id="0ec0d-141">IHostSecurityContext Interface</span></span>](ihostsecuritycontext-interface.md)
- [<span data-ttu-id="0ec0d-142">IHostSecurityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="0ec0d-142">IHostSecurityManager Interface</span></span>](ihostsecuritymanager-interface.md)
- [<span data-ttu-id="0ec0d-143">IHostThreadPoolManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="0ec0d-143">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)
