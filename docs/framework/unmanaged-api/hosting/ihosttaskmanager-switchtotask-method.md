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
ms.openlocfilehash: a55b43f3629cebb0ba1d3a7ac1802126874418d8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122121"
---
# <a name="ihosttaskmanagerswitchtotask-method"></a><span data-ttu-id="a5647-102">IHostTaskManager::SwitchToTask — Metoda</span><span class="sxs-lookup"><span data-stu-id="a5647-102">IHostTaskManager::SwitchToTask Method</span></span>
<span data-ttu-id="a5647-103">Powiadamia hosta o konieczności przełączenia bieżącego zadania.</span><span class="sxs-lookup"><span data-stu-id="a5647-103">Notifies the host that it should switch out the current task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5647-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a5647-104">Syntax</span></span>  
  
```cpp  
HRESULT SwitchToTask (  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a5647-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a5647-105">Parameters</span></span>  
 `option`  
 <span data-ttu-id="a5647-106">podczas Jedna z wartości wyliczenia [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) wskazująca akcję, którą powinien wykonać host, jeśli żądane bloki operacji.</span><span class="sxs-lookup"><span data-stu-id="a5647-106">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) enumeration values, indicating the action the host should take if the requested operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a5647-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a5647-107">Return Value</span></span>  
  
|<span data-ttu-id="a5647-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a5647-108">HRESULT</span></span>|<span data-ttu-id="a5647-109">Opis</span><span class="sxs-lookup"><span data-stu-id="a5647-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a5647-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="a5647-110">S_OK</span></span>|<span data-ttu-id="a5647-111">`SwitchToTask` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="a5647-111">`SwitchToTask` returned successfully.</span></span>|  
|<span data-ttu-id="a5647-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a5647-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a5647-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="a5647-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a5647-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a5647-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a5647-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="a5647-115">The call timed out.</span></span>|  
|<span data-ttu-id="a5647-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a5647-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a5647-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="a5647-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a5647-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a5647-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a5647-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="a5647-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a5647-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a5647-120">E_FAIL</span></span>|<span data-ttu-id="a5647-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="a5647-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a5647-122">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="a5647-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a5647-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a5647-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a5647-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a5647-124">Remarks</span></span>  
 <span data-ttu-id="a5647-125">Host może przełączać się w innym zadaniu odpowiednio do potrzeb lub w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="a5647-125">The host can switch in another task as desired or needed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a5647-126">`SwitchToTask` nie określa, do którego zadania należy przełączyć hosta; określa tylko zadanie, z którego ma zostać przełączone.</span><span class="sxs-lookup"><span data-stu-id="a5647-126">`SwitchToTask` does not specify which task the host should switch to; it specifies only the task that it should switch from.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5647-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a5647-127">Requirements</span></span>  
 <span data-ttu-id="a5647-128">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5647-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5647-129">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a5647-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a5647-130">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a5647-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a5647-131">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5647-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5647-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a5647-132">See also</span></span>

- [<span data-ttu-id="a5647-133">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="a5647-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="a5647-134">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="a5647-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="a5647-135">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="a5647-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="a5647-136">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="a5647-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
