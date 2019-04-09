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
ms.openlocfilehash: cd48664c78e3f5772cdfa655ebbc7cfa716f4950
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59107207"
---
# <a name="ihostiocompletionmanagersetclriocompletionmanager-method"></a><span data-ttu-id="76c1c-102">IHostIoCompletionManager::SetCLRIoCompletionManager — Metoda</span><span class="sxs-lookup"><span data-stu-id="76c1c-102">IHostIoCompletionManager::SetCLRIoCompletionManager Method</span></span>
<span data-ttu-id="76c1c-103">Udostępnia wskaźnik interfejsu do hosta [iclriocompletionmanager —](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) wystąpienia implementowany przez środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="76c1c-103">Provides the host with an interface pointer to the [ICLRIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) instance implemented by the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76c1c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="76c1c-104">Syntax</span></span>  
  
```  
HRESULT SetCLRIoCompletionManager (  
    [in] ICLRIoCompletionManager *pManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="76c1c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="76c1c-105">Parameters</span></span>  
 `pManager`  
 <span data-ttu-id="76c1c-106">[in] Wskaźnik interfejsu do `ICLRIoCompletionManager` wystąpienia dostarczane przez środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="76c1c-106">[in] An interface pointer to an `ICLRIoCompletionManager` instance provided by the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="76c1c-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="76c1c-107">Return Value</span></span>  
  
|<span data-ttu-id="76c1c-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="76c1c-108">HRESULT</span></span>|<span data-ttu-id="76c1c-109">Opis</span><span class="sxs-lookup"><span data-stu-id="76c1c-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="76c1c-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="76c1c-110">S_OK</span></span>|`SetCLRIoCompletionManager` <span data-ttu-id="76c1c-111">pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="76c1c-111">returned successfully.</span></span>|  
|<span data-ttu-id="76c1c-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="76c1c-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="76c1c-113">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="76c1c-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="76c1c-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="76c1c-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="76c1c-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="76c1c-115">The call timed out.</span></span>|  
|<span data-ttu-id="76c1c-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="76c1c-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="76c1c-117">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="76c1c-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="76c1c-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="76c1c-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="76c1c-119">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="76c1c-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="76c1c-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="76c1c-120">E_FAIL</span></span>|<span data-ttu-id="76c1c-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="76c1c-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="76c1c-122">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="76c1c-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="76c1c-123">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="76c1c-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="76c1c-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="76c1c-124">Remarks</span></span>  
 <span data-ttu-id="76c1c-125">Po środowisko CLR jest określana mianem `SetCLRIoCompletionManager`, host musi wywołać [iclriocompletionmanager::onComplete —](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md) powiadomić środowiska CLR, po zakończeniu żądania We/Wy.</span><span class="sxs-lookup"><span data-stu-id="76c1c-125">After the CLR has called `SetCLRIoCompletionManager`, the host must call [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md) to notify the CLR when an I/O request has been completed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76c1c-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="76c1c-126">Requirements</span></span>  
 <span data-ttu-id="76c1c-127">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="76c1c-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76c1c-128">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="76c1c-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="76c1c-129">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="76c1c-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="76c1c-130">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="76c1c-130">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="76c1c-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="76c1c-131">See also</span></span>

- [<span data-ttu-id="76c1c-132">ICLRIoCompletionManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="76c1c-132">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="76c1c-133">IHostIoCompletionManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="76c1c-133">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
