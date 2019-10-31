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
ms.openlocfilehash: 7eedf052b6f2285799940b394d9891975230cb72
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132930"
---
# <a name="ihosttaskmanagersleep-method"></a><span data-ttu-id="54407-102">IHostTaskManager::Sleep — Metoda</span><span class="sxs-lookup"><span data-stu-id="54407-102">IHostTaskManager::Sleep Method</span></span>
<span data-ttu-id="54407-103">Powiadamia hosta, że bieżące zadanie przechodzi w stan uśpienia.</span><span class="sxs-lookup"><span data-stu-id="54407-103">Notifies the host that the current task is going to sleep.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54407-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="54407-104">Syntax</span></span>  
  
```cpp  
HRESULT Sleep (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="54407-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="54407-105">Parameters</span></span>  
 `dwMilliseconds`  
 <span data-ttu-id="54407-106">podczas Przedział czasu (w milisekundach), przez który wątek będzie uśpiony.</span><span class="sxs-lookup"><span data-stu-id="54407-106">[in] The time interval, in milliseconds, that the thread will sleep.</span></span>  
  
 `option`  
 <span data-ttu-id="54407-107">podczas Jedna z wartości wyliczenia [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) wskazująca, jaka akcja powinna być wykonywana przez hosta, jeśli ta akcja jest blokowana.</span><span class="sxs-lookup"><span data-stu-id="54407-107">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) enumeration values, indicating what action the host should take if this action blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="54407-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="54407-108">Return Value</span></span>  
  
|<span data-ttu-id="54407-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="54407-109">HRESULT</span></span>|<span data-ttu-id="54407-110">Opis</span><span class="sxs-lookup"><span data-stu-id="54407-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="54407-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="54407-111">S_OK</span></span>|<span data-ttu-id="54407-112">`Sleep` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="54407-112">`Sleep` returned successfully.</span></span>|  
|<span data-ttu-id="54407-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="54407-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="54407-114">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="54407-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="54407-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="54407-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="54407-116">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="54407-116">The call timed out.</span></span>|  
|<span data-ttu-id="54407-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="54407-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="54407-118">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="54407-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="54407-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="54407-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="54407-120">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="54407-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="54407-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="54407-121">E_FAIL</span></span>|<span data-ttu-id="54407-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="54407-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="54407-123">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="54407-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="54407-124">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="54407-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="54407-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="54407-125">Remarks</span></span>  
 <span data-ttu-id="54407-126">Środowisko CLR zazwyczaj wywołuje `IHostTaskManager::Sleep`, gdy <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> jest wywoływana z kodu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="54407-126">The CLR typically calls `IHostTaskManager::Sleep` when <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> is called from user code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54407-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="54407-127">Requirements</span></span>  
 <span data-ttu-id="54407-128">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54407-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54407-129">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="54407-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="54407-130">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="54407-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="54407-131">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54407-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54407-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="54407-132">See also</span></span>

- [<span data-ttu-id="54407-133">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="54407-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="54407-134">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="54407-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="54407-135">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="54407-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="54407-136">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="54407-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
