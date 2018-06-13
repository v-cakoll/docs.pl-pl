---
title: ICLRTask::SwitchIn — Metoda
ms.date: 03/30/2017
api_name:
- ICLRTask.SwitchIn
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::SwitchIn
helpviewer_keywords:
- ICLRTask::SwitchIn method [.NET Framework hosting]
- SwitchIn method [.NET Framework hosting]
ms.assetid: 3d37ce20-aa65-4043-8f13-7c728b5d8a52
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 13e4119da7af4c54387c24ee576ff9577da56ca9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33438044"
---
# <a name="iclrtaskswitchin-method"></a><span data-ttu-id="7f1d0-102">ICLRTask::SwitchIn — Metoda</span><span class="sxs-lookup"><span data-stu-id="7f1d0-102">ICLRTask::SwitchIn Method</span></span>
<span data-ttu-id="7f1d0-103">Powiadamia środowisko uruchomieniowe języka wspólnego (CLR) który zadania który bieżącego [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) reprezentuje wystąpienie jest teraz w stanie obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="7f1d0-103">Notifies the common language runtime (CLR) that the task that the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance represents is now in an operable state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f1d0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7f1d0-104">Syntax</span></span>  
  
```  
HRESULT SwitchIn (  
    [in] HANDLE threadHandle  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7f1d0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7f1d0-105">Parameters</span></span>  
 `threadHandle`  
 <span data-ttu-id="7f1d0-106">[in] Dojście do wątku fizycznym, w którym zadanie reprezentowany przez bieżący `ICLRTask` wystąpienia jest wykonywany.</span><span class="sxs-lookup"><span data-stu-id="7f1d0-106">[in] A handle to the physical thread on which the task represented by the current `ICLRTask` instance is executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7f1d0-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="7f1d0-107">Return Value</span></span>  
  
|<span data-ttu-id="7f1d0-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7f1d0-108">HRESULT</span></span>|<span data-ttu-id="7f1d0-109">Opis</span><span class="sxs-lookup"><span data-stu-id="7f1d0-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7f1d0-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="7f1d0-110">S_OK</span></span>|<span data-ttu-id="7f1d0-111">`SwitchIn` zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="7f1d0-111">`SwitchIn` returned successfully.</span></span>|  
|<span data-ttu-id="7f1d0-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7f1d0-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7f1d0-113">Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="7f1d0-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7f1d0-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7f1d0-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7f1d0-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="7f1d0-115">The call timed out.</span></span>|  
|<span data-ttu-id="7f1d0-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7f1d0-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7f1d0-117">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="7f1d0-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7f1d0-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7f1d0-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7f1d0-119">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="7f1d0-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7f1d0-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7f1d0-120">E_FAIL</span></span>|<span data-ttu-id="7f1d0-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="7f1d0-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7f1d0-122">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="7f1d0-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7f1d0-123">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="7f1d0-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="7f1d0-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="7f1d0-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="7f1d0-125">`SwitchIn` został wywołany bez wcześniejszej wywołanie [SwitchOut — metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchout-method.md).</span><span class="sxs-lookup"><span data-stu-id="7f1d0-125">`SwitchIn` was called without an earlier call to [SwitchOut Method](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchout-method.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7f1d0-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7f1d0-126">Remarks</span></span>  
 <span data-ttu-id="7f1d0-127">`threadHandle` Parametr reprezentuje dojścia do wątku systemu operacyjnego, na którym zadanie reprezentowany przez bieżący `ICLRTask` wystąpienie zostało zaplanowane.</span><span class="sxs-lookup"><span data-stu-id="7f1d0-127">The `threadHandle` parameter represents a handle to the operating system thread on which the task represented by the current `ICLRTask` instance has been scheduled.</span></span> <span data-ttu-id="7f1d0-128">W przypadku personifikacji dla tego wątku, należy wywołać [IHostSecurityManager::RevertToSelf](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md) przed przełączeniem w zadaniu.</span><span class="sxs-lookup"><span data-stu-id="7f1d0-128">If impersonation has occurred on this thread, you must call [IHostSecurityManager::RevertToSelf](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md) before switching in the task.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7f1d0-129">Wywołanie `SwitchIn` bez wcześniejszej wywołanie `SwitchOut` kończy się niepowodzeniem i wartość HRESULT HOST_E_INVALIDOPERATION.</span><span class="sxs-lookup"><span data-stu-id="7f1d0-129">A call to `SwitchIn` without an earlier call to `SwitchOut` fails with an HRESULT value of HOST_E_INVALIDOPERATION.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f1d0-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7f1d0-130">Requirements</span></span>  
 <span data-ttu-id="7f1d0-131">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f1d0-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f1d0-132">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7f1d0-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7f1d0-133">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7f1d0-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7f1d0-134">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f1d0-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f1d0-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7f1d0-135">See Also</span></span>  
 [<span data-ttu-id="7f1d0-136">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="7f1d0-136">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="7f1d0-137">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="7f1d0-137">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="7f1d0-138">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="7f1d0-138">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="7f1d0-139">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="7f1d0-139">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
