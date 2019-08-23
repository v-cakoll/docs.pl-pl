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
ms.openlocfilehash: 8b2e8e636915b3921fcd727fc78a3fb18fc69104
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959040"
---
# <a name="ihosttaskmanagerleaveruntime-method"></a><span data-ttu-id="008bf-102">IHostTaskManager::LeaveRuntime — Metoda</span><span class="sxs-lookup"><span data-stu-id="008bf-102">IHostTaskManager::LeaveRuntime Method</span></span>
<span data-ttu-id="008bf-103">Powiadamia hosta, że aktualnie wykonywane zadanie ma opuścić środowisko uruchomieniowe języka wspólnego (CLR) i wprowadzić kod niezarządzany.</span><span class="sxs-lookup"><span data-stu-id="008bf-103">Notifies the host that the currently executing task is about to leave the common language runtime (CLR) and enter unmanaged code.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="008bf-104">Odpowiednie wywołanie [IHostTaskManager:: EnterRuntime —](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md) powiadamia hosta, że aktualnie wykonywane zadanie ponownie wprowadza kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="008bf-104">A corresponding call to [IHostTaskManager::EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md) notifies the host that the currently executing task is reentering managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="008bf-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="008bf-105">Syntax</span></span>  
  
```cpp  
HRESULT LeaveRuntime (  
    [in] SIZE_T target  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="008bf-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="008bf-106">Parameters</span></span>  
 `target`  
 <span data-ttu-id="008bf-107">podczas Adres w mapowanym przenośnym pliku wykonywalnym funkcji niezarządzanej, która ma zostać wywołana.</span><span class="sxs-lookup"><span data-stu-id="008bf-107">[in] The address within the mapped portable executable file of the unmanaged function to be called.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="008bf-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="008bf-108">Return Value</span></span>  
  
|<span data-ttu-id="008bf-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="008bf-109">HRESULT</span></span>|<span data-ttu-id="008bf-110">Opis</span><span class="sxs-lookup"><span data-stu-id="008bf-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="008bf-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="008bf-111">S_OK</span></span>|<span data-ttu-id="008bf-112">`LeaveRuntime`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="008bf-112">`LeaveRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="008bf-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="008bf-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="008bf-114">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="008bf-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="008bf-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="008bf-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="008bf-116">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="008bf-116">The call timed out.</span></span>|  
|<span data-ttu-id="008bf-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="008bf-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="008bf-118">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="008bf-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="008bf-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="008bf-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="008bf-120">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="008bf-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="008bf-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="008bf-121">E_FAIL</span></span>|<span data-ttu-id="008bf-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="008bf-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="008bf-123">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="008bf-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="008bf-124">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="008bf-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="008bf-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="008bf-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="008bf-126">Za mało dostępnej pamięci, aby zakończyć żądaną alokację.</span><span class="sxs-lookup"><span data-stu-id="008bf-126">Not enough memory is available to complete the requested allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="008bf-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="008bf-127">Remarks</span></span>  
 <span data-ttu-id="008bf-128">Sekwencje wywołań do i z kodu niezarządzanego mogą być zagnieżdżane.</span><span class="sxs-lookup"><span data-stu-id="008bf-128">Call sequences to and from unmanaged code can be nested.</span></span> <span data-ttu-id="008bf-129">Na przykład na poniższej `LeaveRuntime`liście opisano hipotetyczną sytuację, w której sekwencja wywołań do, [IHostTaskManager:: ReverseEnterRuntime —](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md), [IHostTaskManager:: ReverseLeaveRuntime —](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md), i `IHostTaskManager::EnterRuntime` umożliwia hostowi Zidentyfikuj zagnieżdżone warstwy.</span><span class="sxs-lookup"><span data-stu-id="008bf-129">For example, the list below describes a hypothetical situation in which the sequence of calls to `LeaveRuntime`, [IHostTaskManager::ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md), [IHostTaskManager::ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md), and `IHostTaskManager::EnterRuntime` allows the host to identify the nested layers.</span></span>  
  
|<span data-ttu-id="008bf-130">Akcja</span><span class="sxs-lookup"><span data-stu-id="008bf-130">Action</span></span>|<span data-ttu-id="008bf-131">Odpowiednie wywołanie metody</span><span class="sxs-lookup"><span data-stu-id="008bf-131">Corresponding Method Call</span></span>|  
|------------|-------------------------------|  
|<span data-ttu-id="008bf-132">Zarządzany Visual Basic plik wykonywalny wywołuje niezarządzaną funkcję zapisaną w C przy użyciu wywołania platformy.</span><span class="sxs-lookup"><span data-stu-id="008bf-132">A managed Visual Basic executable calls an unmanaged function written in C by using platform invoke.</span></span>|`IHostTaskManager::LeaveRuntime`|  
|<span data-ttu-id="008bf-133">Niezarządzana funkcja C wywołuje metodę w zarządzanej bibliotece DLL, C#która jest zapisywana.</span><span class="sxs-lookup"><span data-stu-id="008bf-133">The unmanaged C function calls a method in a managed DLL written in C#.</span></span>|`IHostTaskManager::ReverseEnterRuntime`|  
|<span data-ttu-id="008bf-134">Funkcja zarządza C# wywołuje inną niezarządzaną funkcję zapisaną w języku C, również przy użyciu wywołania platformy.</span><span class="sxs-lookup"><span data-stu-id="008bf-134">The managed C# function calls another unmanaged function written in C, also using platform invoke.</span></span>|`IHostTaskManager::LeaveRuntime`|  
|<span data-ttu-id="008bf-135">Druga niezarządzana funkcja zwraca wykonanie do C# funkcji.</span><span class="sxs-lookup"><span data-stu-id="008bf-135">The second unmanaged function returns execution to the C# function.</span></span>|`IHostTaskManager::EnterRuntime`|  
|<span data-ttu-id="008bf-136">C# Funkcja zwraca wykonanie do pierwszej niezarządzanej funkcji.</span><span class="sxs-lookup"><span data-stu-id="008bf-136">The C# function returns execution to the first unmanaged function.</span></span>|`IHostTaskManager::ReverseLeaveRuntime`|  
|<span data-ttu-id="008bf-137">Pierwsza niezarządzana funkcja zwraca wykonanie do programu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="008bf-137">The first unmanaged function returns execution to the Visual Basic program.</span></span>|`IHostTaskManager::EnterRuntime`|  
  
## <a name="requirements"></a><span data-ttu-id="008bf-138">Wymagania</span><span class="sxs-lookup"><span data-stu-id="008bf-138">Requirements</span></span>  
 <span data-ttu-id="008bf-139">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="008bf-139">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="008bf-140">**Nagłówki** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="008bf-140">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="008bf-141">**Biblioteki** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="008bf-141">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="008bf-142">**.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="008bf-142">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="008bf-143">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="008bf-143">See also</span></span>

- [<span data-ttu-id="008bf-144">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="008bf-144">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="008bf-145">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="008bf-145">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="008bf-146">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="008bf-146">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="008bf-147">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="008bf-147">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
