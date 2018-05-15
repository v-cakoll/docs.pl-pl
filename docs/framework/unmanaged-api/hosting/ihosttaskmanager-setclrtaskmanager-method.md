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
ms.openlocfilehash: 84501ae5e96a2eab4c5da4d4cb211fc60822e339
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="ihosttaskmanagersetclrtaskmanager-method"></a><span data-ttu-id="f2125-102">IHostTaskManager::SetCLRTaskManager — Metoda</span><span class="sxs-lookup"><span data-stu-id="f2125-102">IHostTaskManager::SetCLRTaskManager Method</span></span>
<span data-ttu-id="f2125-103">Udostępnia wskaźnik interfejsu do hosta [ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md) wystąpienia implementowany przez środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="f2125-103">Provides the host with an interface pointer to an [ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md) instance implemented by the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2125-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f2125-104">Syntax</span></span>  
  
```  
HRESULT SetCLRTaskManager (  
    [in] ICLRTaskManager *pManager  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f2125-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f2125-105">Parameters</span></span>  
 `pManager`  
 <span data-ttu-id="f2125-106">[in] Wskaźnik do `ICLRTaskManager` wystąpienia implementowany przez środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="f2125-106">[in] A pointer to an `ICLRTaskManager` instance implemented by the common language runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f2125-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f2125-107">Return Value</span></span>  
  
|<span data-ttu-id="f2125-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f2125-108">HRESULT</span></span>|<span data-ttu-id="f2125-109">Opis</span><span class="sxs-lookup"><span data-stu-id="f2125-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f2125-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="f2125-110">S_OK</span></span>|<span data-ttu-id="f2125-111">`SetCLRTaskManager` zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f2125-111">`SetCLRTaskManager` returned successfully.</span></span>|  
|<span data-ttu-id="f2125-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f2125-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f2125-113">Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="f2125-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f2125-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f2125-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f2125-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="f2125-115">The call timed out.</span></span>|  
|<span data-ttu-id="f2125-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f2125-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f2125-117">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="f2125-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f2125-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f2125-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f2125-119">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="f2125-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f2125-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f2125-120">E_FAIL</span></span>|<span data-ttu-id="f2125-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="f2125-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f2125-122">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="f2125-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f2125-123">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f2125-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f2125-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f2125-124">Remarks</span></span>  
 <span data-ttu-id="f2125-125">Wywołania środowiska uruchomieniowego `SetCLRTaskManager` do Zapewnij hostowi wskaźnika interfejsu do `ICLRTaskManager` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="f2125-125">The runtime calls `SetCLRTaskManager` to provide the host with an interface pointer to an `ICLRTaskManager` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2125-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f2125-126">Requirements</span></span>  
 <span data-ttu-id="f2125-127">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2125-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2125-128">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f2125-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f2125-129">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f2125-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f2125-130">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2125-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2125-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f2125-131">See Also</span></span>  
 [<span data-ttu-id="f2125-132">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="f2125-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="f2125-133">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="f2125-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="f2125-134">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="f2125-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="f2125-135">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="f2125-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
