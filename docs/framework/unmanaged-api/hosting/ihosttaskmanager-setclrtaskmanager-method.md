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
ms.openlocfilehash: 0d18ccc18afa3bb3b7079139886c308882b2efc8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54616657"
---
# <a name="ihosttaskmanagersetclrtaskmanager-method"></a><span data-ttu-id="e08bb-102">IHostTaskManager::SetCLRTaskManager — Metoda</span><span class="sxs-lookup"><span data-stu-id="e08bb-102">IHostTaskManager::SetCLRTaskManager Method</span></span>
<span data-ttu-id="e08bb-103">Udostępnia wskaźnik interfejsu do hosta [iclrtaskmanager —](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md) wystąpienia implementowany przez środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="e08bb-103">Provides the host with an interface pointer to an [ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md) instance implemented by the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e08bb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e08bb-104">Syntax</span></span>  
  
```  
HRESULT SetCLRTaskManager (  
    [in] ICLRTaskManager *pManager  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e08bb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e08bb-105">Parameters</span></span>  
 `pManager`  
 <span data-ttu-id="e08bb-106">[in] Wskaźnik do `ICLRTaskManager` wystąpienia implementowany przez środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="e08bb-106">[in] A pointer to an `ICLRTaskManager` instance implemented by the common language runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e08bb-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e08bb-107">Return Value</span></span>  
  
|<span data-ttu-id="e08bb-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e08bb-108">HRESULT</span></span>|<span data-ttu-id="e08bb-109">Opis</span><span class="sxs-lookup"><span data-stu-id="e08bb-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e08bb-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="e08bb-110">S_OK</span></span>|<span data-ttu-id="e08bb-111">`SetCLRTaskManager` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="e08bb-111">`SetCLRTaskManager` returned successfully.</span></span>|  
|<span data-ttu-id="e08bb-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e08bb-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e08bb-113">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="e08bb-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e08bb-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e08bb-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e08bb-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="e08bb-115">The call timed out.</span></span>|  
|<span data-ttu-id="e08bb-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e08bb-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e08bb-117">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="e08bb-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e08bb-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e08bb-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e08bb-119">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="e08bb-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e08bb-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e08bb-120">E_FAIL</span></span>|<span data-ttu-id="e08bb-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="e08bb-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e08bb-122">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="e08bb-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e08bb-123">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e08bb-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e08bb-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e08bb-124">Remarks</span></span>  
 <span data-ttu-id="e08bb-125">Środowisko uruchomieniowe wywołuje `SetCLRTaskManager` zapewnienie hosta za pomocą wskaźnika interfejsu do `ICLRTaskManager` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="e08bb-125">The runtime calls `SetCLRTaskManager` to provide the host with an interface pointer to an `ICLRTaskManager` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e08bb-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e08bb-126">Requirements</span></span>  
 <span data-ttu-id="e08bb-127">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e08bb-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e08bb-128">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e08bb-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e08bb-129">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e08bb-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e08bb-130">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e08bb-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e08bb-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e08bb-131">See also</span></span>
- [<span data-ttu-id="e08bb-132">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="e08bb-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="e08bb-133">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="e08bb-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="e08bb-134">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="e08bb-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="e08bb-135">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="e08bb-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
