---
title: IHostTaskManager::GetCurrentTask — Metoda
ms.date: 03/30/2017
api_name:
- IHostTaskManager.GetCurrentTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::GetCurrentTask
helpviewer_keywords:
- GetCurrentTask method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::GetCurrentTask method [.NET Framework hosting]
ms.assetid: f17bca49-90bd-4dee-a5e1-b9a57ea46f85
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2436288e2f2f241cab15b16abf4df99c73caec25
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789423"
---
# <a name="ihosttaskmanagergetcurrenttask-method"></a><span data-ttu-id="2f901-102">IHostTaskManager::GetCurrentTask — Metoda</span><span class="sxs-lookup"><span data-stu-id="2f901-102">IHostTaskManager::GetCurrentTask Method</span></span>
<span data-ttu-id="2f901-103">Pobiera wskaźnik interfejsu do zadania, które jest obecnie wykonywany w wątku systemu operacyjnego, w którym wykonano to wywołanie.</span><span class="sxs-lookup"><span data-stu-id="2f901-103">Gets an interface pointer to the task that is currently executing on the operating system thread from which this call is made.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f901-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2f901-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentTask (  
    [out] IHostTask **pTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2f901-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2f901-105">Parameters</span></span>  
 `pTask`  
 <span data-ttu-id="2f901-106">[out] Wskaźnik na adres [ihosttask —](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) wystąpienia, która reprezentuje aktualnie wykonywanego zadania lub wartość null, jeśli zadanie nie jest w trakcie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="2f901-106">[out] A pointer to the address of an [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance that represents the currently executing task, or null, if no task is currently executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2f901-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="2f901-107">Return Value</span></span>  
  
|<span data-ttu-id="2f901-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2f901-108">HRESULT</span></span>|<span data-ttu-id="2f901-109">Opis</span><span class="sxs-lookup"><span data-stu-id="2f901-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2f901-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="2f901-110">S_OK</span></span>|<span data-ttu-id="2f901-111">`GetCurrentTask` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="2f901-111">`GetCurrentTask` returned successfully.</span></span>|  
|<span data-ttu-id="2f901-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2f901-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2f901-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="2f901-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2f901-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2f901-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2f901-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="2f901-115">The call timed out.</span></span>|  
|<span data-ttu-id="2f901-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2f901-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2f901-117">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="2f901-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2f901-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2f901-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2f901-119">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="2f901-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2f901-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2f901-120">E_FAIL</span></span>|<span data-ttu-id="2f901-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="2f901-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2f901-122">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="2f901-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2f901-123">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="2f901-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="2f901-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="2f901-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="2f901-125">`GetCurrentTask` został wywołany w wątku systemu operacyjnego na zewnątrz kontrolki hosta.</span><span class="sxs-lookup"><span data-stu-id="2f901-125">`GetCurrentTask` was called on an operating system thread outside the control of the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2f901-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2f901-126">Remarks</span></span>  
 <span data-ttu-id="2f901-127">Hosta można również ustawić `pTask` parametru na wartość null, aby uniemożliwić wprowadzanie środowiska CLR przez klasę task, która nie została zainicjowana.</span><span class="sxs-lookup"><span data-stu-id="2f901-127">The host can also set the `pTask` parameter to null to prevent a task that it did not initiate from entering the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f901-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2f901-128">Requirements</span></span>  
 <span data-ttu-id="2f901-129">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2f901-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f901-130">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2f901-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2f901-131">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2f901-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2f901-132">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f901-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f901-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2f901-133">See also</span></span>

- [<span data-ttu-id="2f901-134">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="2f901-134">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="2f901-135">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="2f901-135">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="2f901-136">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="2f901-136">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="2f901-137">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="2f901-137">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
