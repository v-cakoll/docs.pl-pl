---
title: IHostTask::GetPriority — Metoda
ms.date: 03/30/2017
api_name:
- IHostTask.GetPriority
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::GetPriority
helpviewer_keywords:
- GetPriority method [.NET Framework hosting]
- IHostTask::GetPriority method [.NET Framework hosting]
ms.assetid: 4b463cd6-77c1-4f9a-8518-346ad8fc4b70
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 702992ab4edfea3f0b699efefedb195cd87586ea
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789574"
---
# <a name="ihosttaskgetpriority-method"></a><span data-ttu-id="9ff45-102">IHostTask::GetPriority — Metoda</span><span class="sxs-lookup"><span data-stu-id="9ff45-102">IHostTask::GetPriority Method</span></span>
<span data-ttu-id="9ff45-103">Pobiera poziom priorytetu wątku zadania, reprezentowane przez bieżącą [ihosttask —](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="9ff45-103">Gets the thread priority level of the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ff45-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9ff45-104">Syntax</span></span>  
  
```  
HRESULT GetPriority (  
    [out] int *pPriority  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9ff45-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9ff45-105">Parameters</span></span>  
 `pPriority`  
 <span data-ttu-id="9ff45-106">[out] Wskaźnik do liczby całkowitej, który wskazuje poziom priorytetu wątku zadania, reprezentowane przez bieżącą `IHostTask` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="9ff45-106">[out] A pointer to an integer that indicates the thread priority level of the task represented by the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9ff45-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="9ff45-107">Return Value</span></span>  
  
|<span data-ttu-id="9ff45-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9ff45-108">HRESULT</span></span>|<span data-ttu-id="9ff45-109">Opis</span><span class="sxs-lookup"><span data-stu-id="9ff45-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9ff45-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="9ff45-110">S_OK</span></span>|<span data-ttu-id="9ff45-111">`GetPriority` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="9ff45-111">`GetPriority` returned successfully.</span></span>|  
|<span data-ttu-id="9ff45-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9ff45-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9ff45-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="9ff45-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9ff45-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9ff45-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9ff45-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="9ff45-115">The call timed out.</span></span>|  
|<span data-ttu-id="9ff45-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9ff45-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9ff45-117">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="9ff45-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9ff45-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9ff45-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9ff45-119">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="9ff45-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9ff45-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9ff45-120">E_FAIL</span></span>|<span data-ttu-id="9ff45-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="9ff45-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9ff45-122">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="9ff45-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9ff45-123">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9ff45-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9ff45-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9ff45-124">Remarks</span></span>  
 <span data-ttu-id="9ff45-125">Wartości poziomu priorytetu wątku są definiowane przez Win32 `SetThreadPriority` funkcji.</span><span class="sxs-lookup"><span data-stu-id="9ff45-125">Thread priority level values are defined by the Win32 `SetThreadPriority` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ff45-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9ff45-126">Requirements</span></span>  
 <span data-ttu-id="9ff45-127">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ff45-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ff45-128">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9ff45-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9ff45-129">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9ff45-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9ff45-130">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ff45-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ff45-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9ff45-131">See also</span></span>

- [<span data-ttu-id="9ff45-132">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="9ff45-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="9ff45-133">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="9ff45-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="9ff45-134">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="9ff45-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="9ff45-135">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="9ff45-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
