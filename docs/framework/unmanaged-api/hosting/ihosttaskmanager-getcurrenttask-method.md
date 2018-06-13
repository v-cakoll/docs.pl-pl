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
ms.openlocfilehash: 2420ddb5cf9be2cfb08f89d27d9aa277305e7ffb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33442695"
---
# <a name="ihosttaskmanagergetcurrenttask-method"></a><span data-ttu-id="f3976-102">IHostTaskManager::GetCurrentTask — Metoda</span><span class="sxs-lookup"><span data-stu-id="f3976-102">IHostTaskManager::GetCurrentTask Method</span></span>
<span data-ttu-id="f3976-103">Pobiera wskaźnika interfejsu do zadania, które jest obecnie wykonywane w wątku systemu operacyjnego, z której dokonywane jest to wywołanie.</span><span class="sxs-lookup"><span data-stu-id="f3976-103">Gets an interface pointer to the task that is currently executing on the operating system thread from which this call is made.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3976-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f3976-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentTask (  
    [out] IHostTask **pTask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f3976-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f3976-105">Parameters</span></span>  
 `pTask`  
 <span data-ttu-id="f3976-106">[out] Wskaźnik do adresu [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) wystąpienia, który reprezentuje aktualnie wykonywanego zadania lub wartość null, jeśli zadanie nie jest aktualnie wykonywany.</span><span class="sxs-lookup"><span data-stu-id="f3976-106">[out] A pointer to the address of an [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance that represents the currently executing task, or null, if no task is currently executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f3976-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f3976-107">Return Value</span></span>  
  
|<span data-ttu-id="f3976-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f3976-108">HRESULT</span></span>|<span data-ttu-id="f3976-109">Opis</span><span class="sxs-lookup"><span data-stu-id="f3976-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f3976-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="f3976-110">S_OK</span></span>|<span data-ttu-id="f3976-111">`GetCurrentTask` zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f3976-111">`GetCurrentTask` returned successfully.</span></span>|  
|<span data-ttu-id="f3976-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f3976-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f3976-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="f3976-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f3976-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f3976-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f3976-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="f3976-115">The call timed out.</span></span>|  
|<span data-ttu-id="f3976-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f3976-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f3976-117">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="f3976-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f3976-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f3976-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f3976-119">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="f3976-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f3976-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f3976-120">E_FAIL</span></span>|<span data-ttu-id="f3976-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="f3976-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f3976-122">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="f3976-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f3976-123">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f3976-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="f3976-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="f3976-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="f3976-125">`GetCurrentTask` została wywołana w wątku systemu operacyjnego poza kontrolą hosta.</span><span class="sxs-lookup"><span data-stu-id="f3976-125">`GetCurrentTask` was called on an operating system thread outside the control of the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f3976-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f3976-126">Remarks</span></span>  
 <span data-ttu-id="f3976-127">Hosta można również ustawić `pTask` parametru na wartość null, aby uniemożliwić wprowadzenie CLR zadań, która nie została zainicjowana.</span><span class="sxs-lookup"><span data-stu-id="f3976-127">The host can also set the `pTask` parameter to null to prevent a task that it did not initiate from entering the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3976-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f3976-128">Requirements</span></span>  
 <span data-ttu-id="f3976-129">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3976-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3976-130">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f3976-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f3976-131">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f3976-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f3976-132">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3976-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3976-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f3976-133">See Also</span></span>  
 [<span data-ttu-id="f3976-134">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="f3976-134">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="f3976-135">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="f3976-135">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="f3976-136">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="f3976-136">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="f3976-137">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="f3976-137">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
