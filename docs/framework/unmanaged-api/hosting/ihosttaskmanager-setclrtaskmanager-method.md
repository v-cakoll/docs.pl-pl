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
ms.openlocfilehash: bc5008461acc3b0653c53cee70cbfe89c90a440b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67749398"
---
# <a name="ihosttaskmanagersetclrtaskmanager-method"></a><span data-ttu-id="bd654-102">IHostTaskManager::SetCLRTaskManager — Metoda</span><span class="sxs-lookup"><span data-stu-id="bd654-102">IHostTaskManager::SetCLRTaskManager Method</span></span>
<span data-ttu-id="bd654-103">Udostępnia wskaźnik interfejsu do hosta [iclrtaskmanager —](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md) wystąpienia implementowany przez środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="bd654-103">Provides the host with an interface pointer to an [ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md) instance implemented by the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd654-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bd654-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCLRTaskManager (  
    [in] ICLRTaskManager *pManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bd654-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bd654-105">Parameters</span></span>  
 `pManager`  
 <span data-ttu-id="bd654-106">[in] Wskaźnik do `ICLRTaskManager` wystąpienia implementowany przez środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="bd654-106">[in] A pointer to an `ICLRTaskManager` instance implemented by the common language runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bd654-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="bd654-107">Return Value</span></span>  
  
|<span data-ttu-id="bd654-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bd654-108">HRESULT</span></span>|<span data-ttu-id="bd654-109">Opis</span><span class="sxs-lookup"><span data-stu-id="bd654-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bd654-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="bd654-110">S_OK</span></span>|<span data-ttu-id="bd654-111">`SetCLRTaskManager` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="bd654-111">`SetCLRTaskManager` returned successfully.</span></span>|  
|<span data-ttu-id="bd654-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="bd654-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="bd654-113">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="bd654-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="bd654-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="bd654-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="bd654-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="bd654-115">The call timed out.</span></span>|  
|<span data-ttu-id="bd654-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="bd654-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="bd654-117">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="bd654-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="bd654-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="bd654-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="bd654-119">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="bd654-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="bd654-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bd654-120">E_FAIL</span></span>|<span data-ttu-id="bd654-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="bd654-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="bd654-122">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="bd654-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="bd654-123">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="bd654-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bd654-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bd654-124">Remarks</span></span>  
 <span data-ttu-id="bd654-125">Środowisko uruchomieniowe wywołuje `SetCLRTaskManager` zapewnienie hosta za pomocą wskaźnika interfejsu do `ICLRTaskManager` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="bd654-125">The runtime calls `SetCLRTaskManager` to provide the host with an interface pointer to an `ICLRTaskManager` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd654-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bd654-126">Requirements</span></span>  
 <span data-ttu-id="bd654-127">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd654-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd654-128">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="bd654-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bd654-129">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bd654-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bd654-130">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd654-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd654-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bd654-131">See also</span></span>

- [<span data-ttu-id="bd654-132">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="bd654-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="bd654-133">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="bd654-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="bd654-134">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="bd654-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="bd654-135">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="bd654-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
