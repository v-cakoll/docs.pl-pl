---
title: IHostIoCompletionManager::SetCLRIoCompletionManager — Metoda
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.SetCLRIoCompletionManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::SetCLRIoCompletionManager
helpviewer_keywords:
- IHostIoCompletionManager::SetCLRIoCompletionManager method [.NET Framework hosting]
- SetCLRIoCompletionManager method [.NET Framework hosting]
ms.assetid: 4254bb01-3a14-4f34-a3be-60ff1f5072b5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 97d4561c34c03eefc7487f5f96b7a490a480ac19
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780763"
---
# <a name="ihostiocompletionmanagersetclriocompletionmanager-method"></a><span data-ttu-id="a5491-102">IHostIoCompletionManager::SetCLRIoCompletionManager — Metoda</span><span class="sxs-lookup"><span data-stu-id="a5491-102">IHostIoCompletionManager::SetCLRIoCompletionManager Method</span></span>
<span data-ttu-id="a5491-103">Udostępnia wskaźnik interfejsu do hosta [iclriocompletionmanager —](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) wystąpienia implementowany przez środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="a5491-103">Provides the host with an interface pointer to the [ICLRIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) instance implemented by the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5491-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a5491-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCLRIoCompletionManager (  
    [in] ICLRIoCompletionManager *pManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a5491-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a5491-105">Parameters</span></span>  
 `pManager`  
 <span data-ttu-id="a5491-106">[in] Wskaźnik interfejsu do `ICLRIoCompletionManager` wystąpienia dostarczane przez środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="a5491-106">[in] An interface pointer to an `ICLRIoCompletionManager` instance provided by the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a5491-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a5491-107">Return Value</span></span>  
  
|<span data-ttu-id="a5491-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a5491-108">HRESULT</span></span>|<span data-ttu-id="a5491-109">Opis</span><span class="sxs-lookup"><span data-stu-id="a5491-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a5491-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="a5491-110">S_OK</span></span>|<span data-ttu-id="a5491-111">`SetCLRIoCompletionManager` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="a5491-111">`SetCLRIoCompletionManager` returned successfully.</span></span>|  
|<span data-ttu-id="a5491-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a5491-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a5491-113">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="a5491-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a5491-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a5491-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a5491-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="a5491-115">The call timed out.</span></span>|  
|<span data-ttu-id="a5491-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a5491-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a5491-117">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="a5491-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a5491-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a5491-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a5491-119">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="a5491-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a5491-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a5491-120">E_FAIL</span></span>|<span data-ttu-id="a5491-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="a5491-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a5491-122">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="a5491-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a5491-123">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a5491-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a5491-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a5491-124">Remarks</span></span>  
 <span data-ttu-id="a5491-125">Po środowisko CLR jest określana mianem `SetCLRIoCompletionManager`, host musi wywołać [iclriocompletionmanager::onComplete —](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md) powiadomić środowiska CLR, po zakończeniu żądania We/Wy.</span><span class="sxs-lookup"><span data-stu-id="a5491-125">After the CLR has called `SetCLRIoCompletionManager`, the host must call [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md) to notify the CLR when an I/O request has been completed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5491-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a5491-126">Requirements</span></span>  
 <span data-ttu-id="a5491-127">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5491-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5491-128">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a5491-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a5491-129">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a5491-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a5491-130">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5491-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5491-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a5491-131">See also</span></span>

- [<span data-ttu-id="a5491-132">ICLRIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="a5491-132">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="a5491-133">IHostIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="a5491-133">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
