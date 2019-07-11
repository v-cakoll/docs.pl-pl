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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e9de2ad07efa1a9a8bb93aced600e687b2634111
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67758946"
---
# <a name="iclrtasklocksheld-method"></a><span data-ttu-id="759ab-102">ICLRTask::LocksHeld — Metoda</span><span class="sxs-lookup"><span data-stu-id="759ab-102">ICLRTask::LocksHeld Method</span></span>
<span data-ttu-id="759ab-103">Pobiera liczbę blokad znajdujących się obecnie w zadania.</span><span class="sxs-lookup"><span data-stu-id="759ab-103">Gets the number of locks currently held on the task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="759ab-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="759ab-104">Syntax</span></span>  
  
```cpp  
HRESULT LocksHeld (  
    [out] SIZE_T *pLockCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="759ab-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="759ab-105">Parameters</span></span>  
 `pLockCount`  
 <span data-ttu-id="759ab-106">[out] Liczba blokady utrzymywane w zadaniu w momencie wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="759ab-106">[out] The number of locks held on the task at the time of the method call.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="759ab-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="759ab-107">Return Value</span></span>  
  
|<span data-ttu-id="759ab-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="759ab-108">HRESULT</span></span>|<span data-ttu-id="759ab-109">Opis</span><span class="sxs-lookup"><span data-stu-id="759ab-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="759ab-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="759ab-110">S_OK</span></span>|<span data-ttu-id="759ab-111">`LocksHeld` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="759ab-111">`LocksHeld` returned successfully.</span></span>|  
|<span data-ttu-id="759ab-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="759ab-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="759ab-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="759ab-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="759ab-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="759ab-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="759ab-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="759ab-115">The call timed out.</span></span>|  
|<span data-ttu-id="759ab-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="759ab-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="759ab-117">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="759ab-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="759ab-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="759ab-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="759ab-119">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="759ab-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="759ab-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="759ab-120">E_FAIL</span></span>|<span data-ttu-id="759ab-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="759ab-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="759ab-122">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="759ab-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="759ab-123">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="759ab-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="759ab-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="759ab-124">Requirements</span></span>  
 <span data-ttu-id="759ab-125">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="759ab-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="759ab-126">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="759ab-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="759ab-127">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="759ab-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="759ab-128">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="759ab-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="759ab-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="759ab-129">See also</span></span>

- [<span data-ttu-id="759ab-130">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="759ab-130">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="759ab-131">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="759ab-131">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="759ab-132">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="759ab-132">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="759ab-133">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="759ab-133">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
