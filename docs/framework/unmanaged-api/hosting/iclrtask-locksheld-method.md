---
title: ICLRTask::LocksHeld — Metoda
ms.date: 03/30/2017
api_name:
- ICLRTask.LocksHeld
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::LocksHeld
helpviewer_keywords:
- LocksHeld method [.NET Framework hosting]
- ICLRTask::LocksHeld method [.NET Framework hosting]
ms.assetid: e88a4dc3-02cc-4703-a474-292b71c40657
topic_type:
- apiref
ms.openlocfilehash: 3a3c42e2877957e3bbf5031e6ba650e4c9e0364e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73195945"
---
# <a name="iclrtasklocksheld-method"></a><span data-ttu-id="f17fb-102">ICLRTask::LocksHeld — Metoda</span><span class="sxs-lookup"><span data-stu-id="f17fb-102">ICLRTask::LocksHeld Method</span></span>
<span data-ttu-id="f17fb-103">Pobiera liczbę blokad aktualnie przechowywanych w zadaniu.</span><span class="sxs-lookup"><span data-stu-id="f17fb-103">Gets the number of locks currently held on the task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f17fb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f17fb-104">Syntax</span></span>  
  
```cpp  
HRESULT LocksHeld (  
    [out] SIZE_T *pLockCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f17fb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f17fb-105">Parameters</span></span>  
 `pLockCount`  
 <span data-ttu-id="f17fb-106">określoną Liczba blokad przechowywanych w zadaniu w momencie wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="f17fb-106">[out] The number of locks held on the task at the time of the method call.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f17fb-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f17fb-107">Return Value</span></span>  
  
|<span data-ttu-id="f17fb-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f17fb-108">HRESULT</span></span>|<span data-ttu-id="f17fb-109">Opis</span><span class="sxs-lookup"><span data-stu-id="f17fb-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f17fb-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="f17fb-110">S_OK</span></span>|<span data-ttu-id="f17fb-111">`LocksHeld` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="f17fb-111">`LocksHeld` returned successfully.</span></span>|  
|<span data-ttu-id="f17fb-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f17fb-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f17fb-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f17fb-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f17fb-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f17fb-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f17fb-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="f17fb-115">The call timed out.</span></span>|  
|<span data-ttu-id="f17fb-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f17fb-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f17fb-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="f17fb-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f17fb-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f17fb-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f17fb-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="f17fb-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f17fb-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f17fb-120">E_FAIL</span></span>|<span data-ttu-id="f17fb-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="f17fb-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f17fb-122">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="f17fb-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f17fb-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f17fb-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f17fb-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f17fb-124">Requirements</span></span>  
 <span data-ttu-id="f17fb-125">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f17fb-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f17fb-126">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f17fb-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f17fb-127">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f17fb-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f17fb-128">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f17fb-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f17fb-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f17fb-129">See also</span></span>

- [<span data-ttu-id="f17fb-130">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="f17fb-130">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="f17fb-131">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="f17fb-131">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="f17fb-132">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="f17fb-132">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="f17fb-133">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="f17fb-133">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
