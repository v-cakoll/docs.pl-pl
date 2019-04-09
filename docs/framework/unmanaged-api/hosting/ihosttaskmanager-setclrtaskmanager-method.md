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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59173553"
---
# <a name="ihosttaskmanagersetclrtaskmanager-method"></a><span data-ttu-id="637ff-102">IHostTaskManager::SetCLRTaskManager — Metoda</span><span class="sxs-lookup"><span data-stu-id="637ff-102">IHostTaskManager::SetCLRTaskManager Method</span></span>
<span data-ttu-id="637ff-103">Udostępnia wskaźnik interfejsu do hosta [iclrtaskmanager —](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md) wystąpienia implementowany przez środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="637ff-103">Provides the host with an interface pointer to an [ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md) instance implemented by the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="637ff-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="637ff-104">Syntax</span></span>  
  
```  
HRESULT SetCLRTaskManager (  
    [in] ICLRTaskManager *pManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="637ff-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="637ff-105">Parameters</span></span>  
 `pManager`  
 <span data-ttu-id="637ff-106">[in] Wskaźnik do `ICLRTaskManager` wystąpienia implementowany przez środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="637ff-106">[in] A pointer to an `ICLRTaskManager` instance implemented by the common language runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="637ff-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="637ff-107">Return Value</span></span>  
  
|<span data-ttu-id="637ff-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="637ff-108">HRESULT</span></span>|<span data-ttu-id="637ff-109">Opis</span><span class="sxs-lookup"><span data-stu-id="637ff-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="637ff-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="637ff-110">S_OK</span></span>|`SetCLRTaskManager` <span data-ttu-id="637ff-111">pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="637ff-111">returned successfully.</span></span>|  
|<span data-ttu-id="637ff-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="637ff-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="637ff-113">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="637ff-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="637ff-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="637ff-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="637ff-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="637ff-115">The call timed out.</span></span>|  
|<span data-ttu-id="637ff-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="637ff-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="637ff-117">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="637ff-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="637ff-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="637ff-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="637ff-119">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="637ff-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="637ff-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="637ff-120">E_FAIL</span></span>|<span data-ttu-id="637ff-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="637ff-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="637ff-122">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="637ff-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="637ff-123">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="637ff-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="637ff-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="637ff-124">Remarks</span></span>  
 <span data-ttu-id="637ff-125">Środowisko uruchomieniowe wywołuje `SetCLRTaskManager` zapewnienie hosta za pomocą wskaźnika interfejsu do `ICLRTaskManager` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="637ff-125">The runtime calls `SetCLRTaskManager` to provide the host with an interface pointer to an `ICLRTaskManager` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="637ff-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="637ff-126">Requirements</span></span>  
 <span data-ttu-id="637ff-127">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="637ff-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="637ff-128">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="637ff-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="637ff-129">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="637ff-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="637ff-130">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="637ff-130">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="637ff-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="637ff-131">See also</span></span>

- [<span data-ttu-id="637ff-132">ICLRTask — Interfejs</span><span class="sxs-lookup"><span data-stu-id="637ff-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="637ff-133">ICLRTaskManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="637ff-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="637ff-134">IHostTask — Interfejs</span><span class="sxs-lookup"><span data-stu-id="637ff-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="637ff-135">IHostTaskManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="637ff-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
