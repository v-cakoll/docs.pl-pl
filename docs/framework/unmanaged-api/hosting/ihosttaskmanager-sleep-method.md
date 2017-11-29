---
title: "IHostTaskManager::Sleep — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTaskManager.Sleep
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTaskManager::Sleep
helpviewer_keywords:
- IHostTaskManager::Sleep method [.NET Framework hosting]
- Sleep method, IHostTaskManager interface [.NET Framework hosting]
ms.assetid: f67d25f3-9199-4c5f-b1e8-1c819243cfd5
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cc26ca7d226c4529b0bc702567e774f2f98b085d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ihosttaskmanagersleep-method"></a><span data-ttu-id="894a6-102">IHostTaskManager::Sleep — Metoda</span><span class="sxs-lookup"><span data-stu-id="894a6-102">IHostTaskManager::Sleep Method</span></span>
<span data-ttu-id="894a6-103">Powiadamia hosta, że bieżące zadanie przechodzi w stan uśpienia.</span><span class="sxs-lookup"><span data-stu-id="894a6-103">Notifies the host that the current task is going to sleep.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="894a6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="894a6-104">Syntax</span></span>  
  
```  
HRESULT Sleep (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="894a6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="894a6-105">Parameters</span></span>  
 `dwMilliseconds`  
 <span data-ttu-id="894a6-106">[in] Przedział czasu (w milisekundach), które zostaną wprowadzone w tryb uśpienia wątku.</span><span class="sxs-lookup"><span data-stu-id="894a6-106">[in] The time interval, in milliseconds, that the thread will sleep.</span></span>  
  
 `option`  
 <span data-ttu-id="894a6-107">[in] Jeden z [wait_option —](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) wartości wyliczenia, wskazujący akcję hosta powinien wykonać, jeśli ta akcja bloków.</span><span class="sxs-lookup"><span data-stu-id="894a6-107">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) enumeration values, indicating what action the host should take if this action blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="894a6-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="894a6-108">Return Value</span></span>  
  
|<span data-ttu-id="894a6-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="894a6-109">HRESULT</span></span>|<span data-ttu-id="894a6-110">Opis</span><span class="sxs-lookup"><span data-stu-id="894a6-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="894a6-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="894a6-111">S_OK</span></span>|<span data-ttu-id="894a6-112">`Sleep`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="894a6-112">`Sleep` returned successfully.</span></span>|  
|<span data-ttu-id="894a6-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="894a6-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="894a6-114">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="894a6-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="894a6-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="894a6-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="894a6-116">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="894a6-116">The call timed out.</span></span>|  
|<span data-ttu-id="894a6-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="894a6-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="894a6-118">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="894a6-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="894a6-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="894a6-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="894a6-120">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="894a6-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="894a6-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="894a6-121">E_FAIL</span></span>|<span data-ttu-id="894a6-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="894a6-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="894a6-123">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="894a6-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="894a6-124">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="894a6-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="894a6-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="894a6-125">Remarks</span></span>  
 <span data-ttu-id="894a6-126">Zazwyczaj wymaga środowiska CLR `IHostTaskManager::Sleep` podczas <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> jest wywoływana z kodu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="894a6-126">The CLR typically calls `IHostTaskManager::Sleep` when <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> is called from user code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="894a6-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="894a6-127">Requirements</span></span>  
 <span data-ttu-id="894a6-128">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="894a6-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="894a6-129">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="894a6-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="894a6-130">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="894a6-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="894a6-131">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="894a6-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="894a6-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="894a6-132">See Also</span></span>  
 [<span data-ttu-id="894a6-133">ICLRTask — interfejs</span><span class="sxs-lookup"><span data-stu-id="894a6-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="894a6-134">ICLRTaskManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="894a6-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="894a6-135">IHostTask — interfejs</span><span class="sxs-lookup"><span data-stu-id="894a6-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="894a6-136">IHostTaskManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="894a6-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
