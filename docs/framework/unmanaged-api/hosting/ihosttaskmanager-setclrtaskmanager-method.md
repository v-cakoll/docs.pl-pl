---
title: IHostTaskManager::SetCLRTaskManager — Metoda
ms.date: 03/30/2017
api_name:
- IHostTaskManager.SetCLRTaskManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::SetCLRTaskManager
helpviewer_keywords:
- IHostTaskManager::SetCLRTaskManager method [.NET Framework hosting]
- SetCLRTaskManager method [.NET Framework hosting]
ms.assetid: ec90ee83-bd4b-408b-9274-62a923ab86a1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 283e390b024fd1d0d6a51659b67eff82477fc64d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59173553"
---
# <a name="ihosttaskmanagersetclrtaskmanager-method"></a><span data-ttu-id="587f6-102">IHostTaskManager::SetCLRTaskManager — Metoda</span><span class="sxs-lookup"><span data-stu-id="587f6-102">IHostTaskManager::SetCLRTaskManager Method</span></span>
<span data-ttu-id="587f6-103">Udostępnia wskaźnik interfejsu do hosta [iclrtaskmanager —](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md) wystąpienia implementowany przez środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="587f6-103">Provides the host with an interface pointer to an [ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md) instance implemented by the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="587f6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="587f6-104">Syntax</span></span>  
  
```  
HRESULT SetCLRTaskManager (  
    [in] ICLRTaskManager *pManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="587f6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="587f6-105">Parameters</span></span>  
 `pManager`  
 <span data-ttu-id="587f6-106">[in] Wskaźnik do `ICLRTaskManager` wystąpienia implementowany przez środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="587f6-106">[in] A pointer to an `ICLRTaskManager` instance implemented by the common language runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="587f6-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="587f6-107">Return Value</span></span>  
  
|<span data-ttu-id="587f6-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="587f6-108">HRESULT</span></span>|<span data-ttu-id="587f6-109">Opis</span><span class="sxs-lookup"><span data-stu-id="587f6-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="587f6-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="587f6-110">S_OK</span></span>|<span data-ttu-id="587f6-111">`SetCLRTaskManager` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="587f6-111">`SetCLRTaskManager` returned successfully.</span></span>|  
|<span data-ttu-id="587f6-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="587f6-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="587f6-113">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="587f6-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="587f6-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="587f6-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="587f6-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="587f6-115">The call timed out.</span></span>|  
|<span data-ttu-id="587f6-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="587f6-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="587f6-117">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="587f6-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="587f6-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="587f6-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="587f6-119">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="587f6-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="587f6-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="587f6-120">E_FAIL</span></span>|<span data-ttu-id="587f6-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="587f6-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="587f6-122">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="587f6-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="587f6-123">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="587f6-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="587f6-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="587f6-124">Remarks</span></span>  
 <span data-ttu-id="587f6-125">Środowisko uruchomieniowe wywołuje `SetCLRTaskManager` zapewnienie hosta za pomocą wskaźnika interfejsu do `ICLRTaskManager` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="587f6-125">The runtime calls `SetCLRTaskManager` to provide the host with an interface pointer to an `ICLRTaskManager` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="587f6-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="587f6-126">Requirements</span></span>  
 <span data-ttu-id="587f6-127">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="587f6-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="587f6-128">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="587f6-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="587f6-129">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="587f6-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="587f6-130">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="587f6-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="587f6-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="587f6-131">See also</span></span>

- [<span data-ttu-id="587f6-132">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="587f6-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="587f6-133">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="587f6-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="587f6-134">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="587f6-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="587f6-135">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="587f6-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
