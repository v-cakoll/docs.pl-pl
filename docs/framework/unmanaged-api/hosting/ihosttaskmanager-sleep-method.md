---
title: IHostTaskManager::Sleep — Metoda
ms.date: 03/30/2017
api_name:
- IHostTaskManager.Sleep
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::Sleep
helpviewer_keywords:
- IHostTaskManager::Sleep method [.NET Framework hosting]
- Sleep method, IHostTaskManager interface [.NET Framework hosting]
ms.assetid: f67d25f3-9199-4c5f-b1e8-1c819243cfd5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5e9661d1cd6994acf2c622350593ede502929f3a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54510653"
---
# <a name="ihosttaskmanagersleep-method"></a><span data-ttu-id="65ed3-102">IHostTaskManager::Sleep — Metoda</span><span class="sxs-lookup"><span data-stu-id="65ed3-102">IHostTaskManager::Sleep Method</span></span>
<span data-ttu-id="65ed3-103">Powiadamia hosta, że bieżące zadanie przechodzi w stan uśpienia.</span><span class="sxs-lookup"><span data-stu-id="65ed3-103">Notifies the host that the current task is going to sleep.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65ed3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="65ed3-104">Syntax</span></span>  
  
```  
HRESULT Sleep (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="65ed3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="65ed3-105">Parameters</span></span>  
 `dwMilliseconds`  
 <span data-ttu-id="65ed3-106">[in] Interwał czasu w milisekundach wątek będzie uśpienia.</span><span class="sxs-lookup"><span data-stu-id="65ed3-106">[in] The time interval, in milliseconds, that the thread will sleep.</span></span>  
  
 `option`  
 <span data-ttu-id="65ed3-107">[in] Jedną z [wait_option —](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) wartości wyliczenia, wskazującą, jakie działania host powinien wykonać, jeśli akcja bloków.</span><span class="sxs-lookup"><span data-stu-id="65ed3-107">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) enumeration values, indicating what action the host should take if this action blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="65ed3-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="65ed3-108">Return Value</span></span>  
  
|<span data-ttu-id="65ed3-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="65ed3-109">HRESULT</span></span>|<span data-ttu-id="65ed3-110">Opis</span><span class="sxs-lookup"><span data-stu-id="65ed3-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="65ed3-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="65ed3-111">S_OK</span></span>|<span data-ttu-id="65ed3-112">`Sleep` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="65ed3-112">`Sleep` returned successfully.</span></span>|  
|<span data-ttu-id="65ed3-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="65ed3-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="65ed3-114">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="65ed3-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="65ed3-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="65ed3-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="65ed3-116">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="65ed3-116">The call timed out.</span></span>|  
|<span data-ttu-id="65ed3-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="65ed3-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="65ed3-118">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="65ed3-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="65ed3-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="65ed3-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="65ed3-120">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="65ed3-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="65ed3-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="65ed3-121">E_FAIL</span></span>|<span data-ttu-id="65ed3-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="65ed3-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="65ed3-123">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="65ed3-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="65ed3-124">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="65ed3-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="65ed3-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="65ed3-125">Remarks</span></span>  
 <span data-ttu-id="65ed3-126">Środowisko CLR jest zazwyczaj wywołuje `IHostTaskManager::Sleep` podczas <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> jest wywoływana z kodu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="65ed3-126">The CLR typically calls `IHostTaskManager::Sleep` when <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> is called from user code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65ed3-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="65ed3-127">Requirements</span></span>  
 <span data-ttu-id="65ed3-128">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65ed3-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65ed3-129">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="65ed3-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="65ed3-130">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="65ed3-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="65ed3-131">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65ed3-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65ed3-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="65ed3-132">See also</span></span>
- [<span data-ttu-id="65ed3-133">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="65ed3-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="65ed3-134">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="65ed3-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="65ed3-135">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="65ed3-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="65ed3-136">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="65ed3-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
