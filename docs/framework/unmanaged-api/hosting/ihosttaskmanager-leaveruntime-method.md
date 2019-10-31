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
ms.openlocfilehash: 8ac1c18d094deca50d461ef9ff0933a4f87176e0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132991"
---
# <a name="ihosttaskmanagerleaveruntime-method"></a><span data-ttu-id="13e30-102">IHostTaskManager::LeaveRuntime — Metoda</span><span class="sxs-lookup"><span data-stu-id="13e30-102">IHostTaskManager::LeaveRuntime Method</span></span>
<span data-ttu-id="13e30-103">Powiadamia hosta, że aktualnie wykonywane zadanie ma opuścić środowisko uruchomieniowe języka wspólnego (CLR) i wprowadzić kod niezarządzany.</span><span class="sxs-lookup"><span data-stu-id="13e30-103">Notifies the host that the currently executing task is about to leave the common language runtime (CLR) and enter unmanaged code.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="13e30-104">Odpowiednie wywołanie [IHostTaskManager:: EnterRuntime —](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md) powiadamia hosta, że aktualnie wykonywane zadanie ponownie wprowadza kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="13e30-104">A corresponding call to [IHostTaskManager::EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md) notifies the host that the currently executing task is reentering managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13e30-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="13e30-105">Syntax</span></span>  
  
```cpp  
HRESULT LeaveRuntime (  
    [in] SIZE_T target  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="13e30-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="13e30-106">Parameters</span></span>  
 `target`  
 <span data-ttu-id="13e30-107">podczas Adres w mapowanym przenośnym pliku wykonywalnym funkcji niezarządzanej, która ma zostać wywołana.</span><span class="sxs-lookup"><span data-stu-id="13e30-107">[in] The address within the mapped portable executable file of the unmanaged function to be called.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="13e30-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="13e30-108">Return Value</span></span>  
  
|<span data-ttu-id="13e30-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="13e30-109">HRESULT</span></span>|<span data-ttu-id="13e30-110">Opis</span><span class="sxs-lookup"><span data-stu-id="13e30-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="13e30-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="13e30-111">S_OK</span></span>|<span data-ttu-id="13e30-112">`LeaveRuntime` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="13e30-112">`LeaveRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="13e30-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="13e30-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="13e30-114">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="13e30-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="13e30-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="13e30-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="13e30-116">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="13e30-116">The call timed out.</span></span>|  
|<span data-ttu-id="13e30-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="13e30-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="13e30-118">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="13e30-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="13e30-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="13e30-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="13e30-120">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="13e30-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="13e30-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="13e30-121">E_FAIL</span></span>|<span data-ttu-id="13e30-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="13e30-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="13e30-123">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="13e30-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="13e30-124">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="13e30-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="13e30-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="13e30-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="13e30-126">Za mało dostępnej pamięci, aby zakończyć żądaną alokację.</span><span class="sxs-lookup"><span data-stu-id="13e30-126">Not enough memory is available to complete the requested allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="13e30-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="13e30-127">Remarks</span></span>  
 <span data-ttu-id="13e30-128">Sekwencje wywołań do i z kodu niezarządzanego mogą być zagnieżdżane.</span><span class="sxs-lookup"><span data-stu-id="13e30-128">Call sequences to and from unmanaged code can be nested.</span></span> <span data-ttu-id="13e30-129">Na przykład na poniższej liście opisano hipotetyczną sytuację, w której sekwencja wywołań `LeaveRuntime`, [IHostTaskManager:: ReverseEnterRuntime —](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md), [IHostTaskManager:: ReverseLeaveRuntime —](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md)i `IHostTaskManager::EnterRuntime` umożliwia hostowi zidentyfikowanie zagnieżdżone warstwy.</span><span class="sxs-lookup"><span data-stu-id="13e30-129">For example, the list below describes a hypothetical situation in which the sequence of calls to `LeaveRuntime`, [IHostTaskManager::ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md), [IHostTaskManager::ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md), and `IHostTaskManager::EnterRuntime` allows the host to identify the nested layers.</span></span>  
  
|<span data-ttu-id="13e30-130">Akcja</span><span class="sxs-lookup"><span data-stu-id="13e30-130">Action</span></span>|<span data-ttu-id="13e30-131">Odpowiednie wywołanie metody</span><span class="sxs-lookup"><span data-stu-id="13e30-131">Corresponding Method Call</span></span>|  
|------------|-------------------------------|  
|<span data-ttu-id="13e30-132">Zarządzany Visual Basic plik wykonywalny wywołuje niezarządzaną funkcję zapisaną w C przy użyciu wywołania platformy.</span><span class="sxs-lookup"><span data-stu-id="13e30-132">A managed Visual Basic executable calls an unmanaged function written in C by using platform invoke.</span></span>|`IHostTaskManager::LeaveRuntime`|  
|<span data-ttu-id="13e30-133">Niezarządzana funkcja C wywołuje metodę w zarządzanej bibliotece DLL, C#która jest zapisywana.</span><span class="sxs-lookup"><span data-stu-id="13e30-133">The unmanaged C function calls a method in a managed DLL written in C#.</span></span>|`IHostTaskManager::ReverseEnterRuntime`|  
|<span data-ttu-id="13e30-134">Funkcja zarządza C# wywołuje inną niezarządzaną funkcję zapisaną w języku C, również przy użyciu wywołania platformy.</span><span class="sxs-lookup"><span data-stu-id="13e30-134">The managed C# function calls another unmanaged function written in C, also using platform invoke.</span></span>|`IHostTaskManager::LeaveRuntime`|  
|<span data-ttu-id="13e30-135">Druga niezarządzana funkcja zwraca wykonanie do C# funkcji.</span><span class="sxs-lookup"><span data-stu-id="13e30-135">The second unmanaged function returns execution to the C# function.</span></span>|`IHostTaskManager::EnterRuntime`|  
|<span data-ttu-id="13e30-136">C# Funkcja zwraca wykonanie do pierwszej niezarządzanej funkcji.</span><span class="sxs-lookup"><span data-stu-id="13e30-136">The C# function returns execution to the first unmanaged function.</span></span>|`IHostTaskManager::ReverseLeaveRuntime`|  
|<span data-ttu-id="13e30-137">Pierwsza niezarządzana funkcja zwraca wykonanie do programu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="13e30-137">The first unmanaged function returns execution to the Visual Basic program.</span></span>|`IHostTaskManager::EnterRuntime`|  
  
## <a name="requirements"></a><span data-ttu-id="13e30-138">Wymagania</span><span class="sxs-lookup"><span data-stu-id="13e30-138">Requirements</span></span>  
 <span data-ttu-id="13e30-139">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13e30-139">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13e30-140">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="13e30-140">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="13e30-141">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="13e30-141">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="13e30-142">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13e30-142">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13e30-143">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="13e30-143">See also</span></span>

- [<span data-ttu-id="13e30-144">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="13e30-144">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="13e30-145">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="13e30-145">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="13e30-146">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="13e30-146">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="13e30-147">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="13e30-147">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
