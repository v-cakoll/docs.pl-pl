---
title: "IHostTaskManager::GetCurrentTask — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTaskManager.GetCurrentTask
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTaskManager::GetCurrentTask
helpviewer_keywords:
- GetCurrentTask method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::GetCurrentTask method [.NET Framework hosting]
ms.assetid: f17bca49-90bd-4dee-a5e1-b9a57ea46f85
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 92b4ed0cd33d2e9d3399e409d2dba4eeb14a2f5e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ihosttaskmanagergetcurrenttask-method"></a><span data-ttu-id="e470e-102">IHostTaskManager::GetCurrentTask — Metoda</span><span class="sxs-lookup"><span data-stu-id="e470e-102">IHostTaskManager::GetCurrentTask Method</span></span>
<span data-ttu-id="e470e-103">Pobiera wskaźnika interfejsu do zadania, które jest obecnie wykonywane w wątku systemu operacyjnego, z której dokonywane jest to wywołanie.</span><span class="sxs-lookup"><span data-stu-id="e470e-103">Gets an interface pointer to the task that is currently executing on the operating system thread from which this call is made.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e470e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e470e-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentTask (  
    [out] IHostTask **pTask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e470e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e470e-105">Parameters</span></span>  
 `pTask`  
 <span data-ttu-id="e470e-106">[out] Wskaźnik do adresu [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) wystąpienia, który reprezentuje aktualnie wykonywanego zadania lub wartość null, jeśli zadanie nie jest aktualnie wykonywany.</span><span class="sxs-lookup"><span data-stu-id="e470e-106">[out] A pointer to the address of an [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance that represents the currently executing task, or null, if no task is currently executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e470e-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e470e-107">Return Value</span></span>  
  
|<span data-ttu-id="e470e-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e470e-108">HRESULT</span></span>|<span data-ttu-id="e470e-109">Opis</span><span class="sxs-lookup"><span data-stu-id="e470e-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e470e-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="e470e-110">S_OK</span></span>|<span data-ttu-id="e470e-111">`GetCurrentTask`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="e470e-111">`GetCurrentTask` returned successfully.</span></span>|  
|<span data-ttu-id="e470e-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e470e-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e470e-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="e470e-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e470e-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e470e-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e470e-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="e470e-115">The call timed out.</span></span>|  
|<span data-ttu-id="e470e-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e470e-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e470e-117">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="e470e-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e470e-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e470e-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e470e-119">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="e470e-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e470e-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e470e-120">E_FAIL</span></span>|<span data-ttu-id="e470e-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="e470e-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e470e-122">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="e470e-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e470e-123">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e470e-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e470e-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="e470e-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="e470e-125">`GetCurrentTask`została wywołana w wątku systemu operacyjnego poza kontrolą hosta.</span><span class="sxs-lookup"><span data-stu-id="e470e-125">`GetCurrentTask` was called on an operating system thread outside the control of the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e470e-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e470e-126">Remarks</span></span>  
 <span data-ttu-id="e470e-127">Hosta można również ustawić `pTask` parametru na wartość null, aby uniemożliwić wprowadzenie CLR zadań, która nie została zainicjowana.</span><span class="sxs-lookup"><span data-stu-id="e470e-127">The host can also set the `pTask` parameter to null to prevent a task that it did not initiate from entering the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e470e-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e470e-128">Requirements</span></span>  
 <span data-ttu-id="e470e-129">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e470e-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e470e-130">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e470e-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e470e-131">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e470e-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e470e-132">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e470e-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e470e-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e470e-133">See Also</span></span>  
 [<span data-ttu-id="e470e-134">ICLRTask — interfejs</span><span class="sxs-lookup"><span data-stu-id="e470e-134">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="e470e-135">ICLRTaskManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="e470e-135">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="e470e-136">IHostTask — interfejs</span><span class="sxs-lookup"><span data-stu-id="e470e-136">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="e470e-137">IHostTaskManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="e470e-137">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
