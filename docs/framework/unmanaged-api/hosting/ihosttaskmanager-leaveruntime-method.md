---
title: IHostTaskManager::LeaveRuntime — Metoda
ms.date: 03/30/2017
api_name:
- IHostTaskManager.LeaveRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::LeaveRuntime
helpviewer_keywords:
- IHostTaskManager::LeaveRuntime method [.NET Framework hosting]
- LeaveRuntime method [.NET Framework hosting]
ms.assetid: 43689cc4-e48e-46e5-a22d-bafd768b8759
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3d31c5c1b95d250f90b202b391d908f9c12afb84
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="ihosttaskmanagerleaveruntime-method"></a><span data-ttu-id="6ceb1-102">IHostTaskManager::LeaveRuntime — Metoda</span><span class="sxs-lookup"><span data-stu-id="6ceb1-102">IHostTaskManager::LeaveRuntime Method</span></span>
<span data-ttu-id="6ceb1-103">Powiadamia hosta aktualnie wykonywanego zadania o zbliżającym się pozostaw środowisko uruchomieniowe języka wspólnego (CLR), a następnie wprowadź kod niezarządzany.</span><span class="sxs-lookup"><span data-stu-id="6ceb1-103">Notifies the host that the currently executing task is about to leave the common language runtime (CLR) and enter unmanaged code.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6ceb1-104">Do odpowiedniego wywołania [IHostTaskManager::EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md) powiadamia hosta, czy aktualnie wykonywanego zadania ponownego wprowadzania kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="6ceb1-104">A corresponding call to [IHostTaskManager::EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md) notifies the host that the currently executing task is reentering managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ceb1-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="6ceb1-105">Syntax</span></span>  
  
```  
HRESULT LeaveRuntime (  
    [in] SIZE_T target  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6ceb1-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="6ceb1-106">Parameters</span></span>  
 `target`  
 <span data-ttu-id="6ceb1-107">[in] Adres w mapowanej przenośny plik wykonywalny niezarządzanej funkcji do wywołania.</span><span class="sxs-lookup"><span data-stu-id="6ceb1-107">[in] The address within the mapped portable executable file of the unmanaged function to be called.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6ceb1-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6ceb1-108">Return Value</span></span>  
  
|<span data-ttu-id="6ceb1-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6ceb1-109">HRESULT</span></span>|<span data-ttu-id="6ceb1-110">Opis</span><span class="sxs-lookup"><span data-stu-id="6ceb1-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6ceb1-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="6ceb1-111">S_OK</span></span>|<span data-ttu-id="6ceb1-112">`LeaveRuntime` zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="6ceb1-112">`LeaveRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="6ceb1-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6ceb1-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6ceb1-114">Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="6ceb1-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6ceb1-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6ceb1-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6ceb1-116">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="6ceb1-116">The call timed out.</span></span>|  
|<span data-ttu-id="6ceb1-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6ceb1-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6ceb1-118">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="6ceb1-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6ceb1-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6ceb1-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6ceb1-120">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="6ceb1-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6ceb1-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6ceb1-121">E_FAIL</span></span>|<span data-ttu-id="6ceb1-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="6ceb1-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6ceb1-123">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="6ceb1-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6ceb1-124">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="6ceb1-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="6ceb1-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="6ceb1-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="6ceb1-126">Do zakończenia żądanej alokacji jest za mało pamięci.</span><span class="sxs-lookup"><span data-stu-id="6ceb1-126">Not enough memory is available to complete the requested allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6ceb1-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6ceb1-127">Remarks</span></span>  
 <span data-ttu-id="6ceb1-128">Może być zagnieżdżone sekwencje wywołania do i z kodu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="6ceb1-128">Call sequences to and from unmanaged code can be nested.</span></span> <span data-ttu-id="6ceb1-129">Na przykład na poniższej liście opisano fikcyjnej sytuacji, w którym sekwencję wywołań `LeaveRuntime`, [IHostTaskManager::ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md), [IHostTaskManager::ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md), i `IHostTaskManager::EnterRuntime` umożliwia hosta do identyfikowania zagnieżdżone warstwy.</span><span class="sxs-lookup"><span data-stu-id="6ceb1-129">For example, the list below describes a hypothetical situation in which the sequence of calls to `LeaveRuntime`, [IHostTaskManager::ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md), [IHostTaskManager::ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md), and `IHostTaskManager::EnterRuntime` allows the host to identify the nested layers.</span></span>  
  
|<span data-ttu-id="6ceb1-130">Akcja</span><span class="sxs-lookup"><span data-stu-id="6ceb1-130">Action</span></span>|<span data-ttu-id="6ceb1-131">Odpowiedniego wywołania — metoda</span><span class="sxs-lookup"><span data-stu-id="6ceb1-131">Corresponding Method Call</span></span>|  
|------------|-------------------------------|  
|<span data-ttu-id="6ceb1-132">Wywołania funkcji niezarządzanej napisana w języku C przy użyciu platformy zarządzanych wywołania wykonywalne języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="6ceb1-132">A managed Visual Basic executable calls an unmanaged function written in C by using platform invoke.</span></span>|`IHostTaskManager::LeaveRuntime`|  
|<span data-ttu-id="6ceb1-133">Niezarządzanej funkcji C wywołuje metodę w zarządzanej biblioteki DLL napisane w języku C#.</span><span class="sxs-lookup"><span data-stu-id="6ceb1-133">The unmanaged C function calls a method in a managed DLL written in C#.</span></span>|`IHostTaskManager::ReverseEnterRuntime`|  
|<span data-ttu-id="6ceb1-134">Zarządzane C# wywołań funkcji wywołanie innego niezarządzanej funkcji napisane w języku C, również przy użyciu platformy.</span><span class="sxs-lookup"><span data-stu-id="6ceb1-134">The managed C# function calls another unmanaged function written in C, also using platform invoke.</span></span>|`IHostTaskManager::LeaveRuntime`|  
|<span data-ttu-id="6ceb1-135">Drugi niezarządzanej funkcji zwraca wykonanie funkcji języka C#.</span><span class="sxs-lookup"><span data-stu-id="6ceb1-135">The second unmanaged function returns execution to the C# function.</span></span>|`IHostTaskManager::EnterRuntime`|  
|<span data-ttu-id="6ceb1-136">Funkcja języka C# zwraca wykonanie pierwszej funkcji niezarządzanej.</span><span class="sxs-lookup"><span data-stu-id="6ceb1-136">The C# function returns execution to the first unmanaged function.</span></span>|`IHostTaskManager::ReverseLeaveRuntime`|  
|<span data-ttu-id="6ceb1-137">Pierwszy niezarządzanej funkcji zwraca wykonanie do programu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="6ceb1-137">The first unmanaged function returns execution to the Visual Basic program.</span></span>|`IHostTaskManager::EnterRuntime`|  
  
## <a name="requirements"></a><span data-ttu-id="6ceb1-138">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6ceb1-138">Requirements</span></span>  
 <span data-ttu-id="6ceb1-139">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6ceb1-139">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ceb1-140">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6ceb1-140">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6ceb1-141">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6ceb1-141">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6ceb1-142">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ceb1-142">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ceb1-143">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6ceb1-143">See Also</span></span>  
 [<span data-ttu-id="6ceb1-144">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="6ceb1-144">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="6ceb1-145">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="6ceb1-145">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="6ceb1-146">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="6ceb1-146">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="6ceb1-147">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="6ceb1-147">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
