---
title: "IHostSecurityManager::SetSecurityContext — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSecurityManager.SetSecurityContext
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSecurityManager::SetSecurityContext
helpviewer_keywords:
- SetSecurityContext method [.NET Framework hosting]
- IHostSecurityManager::SetSecurityContext method [.NET Framework hosting]
ms.assetid: e4372384-ee69-48d7-97e0-8fab7866597a
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 29a7652e20c08b9de584a9e11ac343ad92f40653
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ihostsecuritymanagersetsecuritycontext-method"></a><span data-ttu-id="8549f-102">IHostSecurityManager::SetSecurityContext — Metoda</span><span class="sxs-lookup"><span data-stu-id="8549f-102">IHostSecurityManager::SetSecurityContext Method</span></span>
<span data-ttu-id="8549f-103">Ustawia kontekst zabezpieczeń aktualnie wykonywane wątku.</span><span class="sxs-lookup"><span data-stu-id="8549f-103">Sets the security context of the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8549f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8549f-104">Syntax</span></span>  
  
```  
HRESULT SetSecurityContext (  
    [in]  EContextType eContextType,  
    [out] IHostSecurityContext** ppSecurityContext  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8549f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8549f-105">Parameters</span></span>  
 `eContextType`  
 <span data-ttu-id="8549f-106">[in] Jeden z [EContextType](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md) wartości, wskazujący, jaki typ kontekstu środowisko uruchomieniowe języka wspólnego (CLR) jest umieszczenie na hoście.</span><span class="sxs-lookup"><span data-stu-id="8549f-106">[in] One of the [EContextType](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md) values, indicating what type of context the common language runtime (CLR) is placing on the host.</span></span>  
  
 `ppSecurityContext`  
 <span data-ttu-id="8549f-107">[out] Wskaźnik do nowego adresu [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) obiektu.</span><span class="sxs-lookup"><span data-stu-id="8549f-107">[out] A pointer to the address of a new [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8549f-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="8549f-108">Return Value</span></span>  
  
|<span data-ttu-id="8549f-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8549f-109">HRESULT</span></span>|<span data-ttu-id="8549f-110">Opis</span><span class="sxs-lookup"><span data-stu-id="8549f-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8549f-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="8549f-111">S_OK</span></span>|<span data-ttu-id="8549f-112">`SetSecurityContext`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="8549f-112">`SetSecurityContext` returned successfully.</span></span>|  
|<span data-ttu-id="8549f-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8549f-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8549f-114">Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="8549f-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8549f-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8549f-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8549f-116">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="8549f-116">The call timed out.</span></span>|  
|<span data-ttu-id="8549f-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8549f-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8549f-118">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="8549f-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8549f-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8549f-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8549f-120">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="8549f-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8549f-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8549f-121">E_FAIL</span></span>|<span data-ttu-id="8549f-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="8549f-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8549f-123">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="8549f-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8549f-124">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8549f-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8549f-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8549f-125">Remarks</span></span>  
 <span data-ttu-id="8549f-126">Wywołania CLR `SetSecurityContext` w kilku scenariuszach.</span><span class="sxs-lookup"><span data-stu-id="8549f-126">The CLR calls `SetSecurityContext` in several scenarios.</span></span> <span data-ttu-id="8549f-127">Przed rozpoczęciem wykonywania klasy i konstruktory modułu i finalizatory, wywołuje CLR `SetSecurityContext` ochrony hosta przed awariami wykonywania.</span><span class="sxs-lookup"><span data-stu-id="8549f-127">Before it executes class and module constructors and finalizers, the CLR calls `SetSecurityContext` to protect the host from execution failures.</span></span> <span data-ttu-id="8549f-128">Następnie resetuje ono kontekstu zabezpieczeń do stanu pierwotnego po wykonaniu konstruktora lub finalizatora, za pomocą innego wywołania `SetSecurityContext`.</span><span class="sxs-lookup"><span data-stu-id="8549f-128">It then resets the security context to its original state after execution of the constructor or finalizer, by using another call to `SetSecurityContext`.</span></span> <span data-ttu-id="8549f-129">Podobnego wzorca występuje zakończenia We/Wy.</span><span class="sxs-lookup"><span data-stu-id="8549f-129">A similar pattern occurs with I/O completion.</span></span> <span data-ttu-id="8549f-130">Jeśli host implementuje [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md), wywołania CLR `SetSecurityContext` po wywołania hosta [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md).</span><span class="sxs-lookup"><span data-stu-id="8549f-130">If the host implements [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md), the CLR calls `SetSecurityContext` after the host calls [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md).</span></span>  
  
 <span data-ttu-id="8549f-131">W punktach asynchronicznych wątków roboczych, wywołuje CLR `SetSecurityContext` w <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> lub poziomu [IHostThreadPoolManager::QueueUserWorkItem](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md)w zależności od tego, czy host lub CLR implementuje puli wątków.</span><span class="sxs-lookup"><span data-stu-id="8549f-131">At asynchronous points in worker threads, the CLR calls `SetSecurityContext` within <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> or within [IHostThreadPoolManager::QueueUserWorkItem](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md), depending on whether the host or the CLR is implementing the thread pool.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8549f-132">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8549f-132">Requirements</span></span>  
 <span data-ttu-id="8549f-133">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8549f-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8549f-134">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8549f-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8549f-135">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8549f-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8549f-136">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8549f-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8549f-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8549f-137">See Also</span></span>  
 <xref:System.Threading.ThreadPool?displayProperty=nameWithType>  
 [<span data-ttu-id="8549f-138">EContextType, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="8549f-138">EContextType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md)  
 [<span data-ttu-id="8549f-139">ICLRIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="8549f-139">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="8549f-140">IHostIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="8549f-140">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)  
 [<span data-ttu-id="8549f-141">IHostSecurityContext, interfejs</span><span class="sxs-lookup"><span data-stu-id="8549f-141">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 [<span data-ttu-id="8549f-142">IHostSecurityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="8549f-142">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
 [<span data-ttu-id="8549f-143">IHostThreadPoolManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="8549f-143">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
