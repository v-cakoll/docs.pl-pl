---
title: IHostTaskManager::SwitchToTask — Metoda
ms.date: 03/30/2017
api_name:
- IHostTaskManager.SwitchToTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::SwitchToTask
helpviewer_keywords:
- IHostTaskManager::SwitchToTask method [.NET Framework hosting]
- SwitchToTask method [.NET Framework hosting]
ms.assetid: 35d0c27e-4b14-49ce-810d-7ab2120177e8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a50c9f7fc5921d3e5c21dd3566de81ac2249f3dd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61796607"
---
# <a name="ihosttaskmanagerswitchtotask-method"></a><span data-ttu-id="b2431-102">IHostTaskManager::SwitchToTask — Metoda</span><span class="sxs-lookup"><span data-stu-id="b2431-102">IHostTaskManager::SwitchToTask Method</span></span>
<span data-ttu-id="b2431-103">Powiadamia hosta, że powinni przełączyć się do bieżącego zadania.</span><span class="sxs-lookup"><span data-stu-id="b2431-103">Notifies the host that it should switch out the current task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2431-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b2431-104">Syntax</span></span>  
  
```  
HRESULT SwitchToTask (  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b2431-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b2431-105">Parameters</span></span>  
 `option`  
 <span data-ttu-id="b2431-106">[in] Jedną z [wait_option —](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) wartości wyliczenia, wskazujący akcję host powinien wykonać, jeśli bloki żądanej operacji.</span><span class="sxs-lookup"><span data-stu-id="b2431-106">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) enumeration values, indicating the action the host should take if the requested operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b2431-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b2431-107">Return Value</span></span>  
  
|<span data-ttu-id="b2431-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b2431-108">HRESULT</span></span>|<span data-ttu-id="b2431-109">Opis</span><span class="sxs-lookup"><span data-stu-id="b2431-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b2431-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="b2431-110">S_OK</span></span>|<span data-ttu-id="b2431-111">`SwitchToTask` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="b2431-111">`SwitchToTask` returned successfully.</span></span>|  
|<span data-ttu-id="b2431-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b2431-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b2431-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="b2431-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b2431-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b2431-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b2431-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="b2431-115">The call timed out.</span></span>|  
|<span data-ttu-id="b2431-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b2431-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b2431-117">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="b2431-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b2431-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b2431-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b2431-119">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="b2431-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b2431-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b2431-120">E_FAIL</span></span>|<span data-ttu-id="b2431-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="b2431-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b2431-122">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="b2431-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b2431-123">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b2431-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b2431-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b2431-124">Remarks</span></span>  
 <span data-ttu-id="b2431-125">Hosta można przełączyć w innym zadaniu jako żądane ani potrzebne.</span><span class="sxs-lookup"><span data-stu-id="b2431-125">The host can switch in another task as desired or needed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b2431-126">`SwitchToTask` nie określa zadania, które hosta powinni przełączyć się na; Określa tylko zadania, które należy zmienić.</span><span class="sxs-lookup"><span data-stu-id="b2431-126">`SwitchToTask` does not specify which task the host should switch to; it specifies only the task that it should switch from.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2431-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b2431-127">Requirements</span></span>  
 <span data-ttu-id="b2431-128">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2431-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2431-129">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b2431-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b2431-130">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b2431-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b2431-131">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2431-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2431-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b2431-132">See also</span></span>

- [<span data-ttu-id="b2431-133">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="b2431-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="b2431-134">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="b2431-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="b2431-135">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="b2431-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="b2431-136">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="b2431-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
