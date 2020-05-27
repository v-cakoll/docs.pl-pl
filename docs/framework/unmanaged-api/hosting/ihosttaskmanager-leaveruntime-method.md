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
ms.openlocfilehash: 2939f13933c4681e7e2220e5290e019e10c2844e
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/26/2020
ms.locfileid: "83841922"
---
# <a name="ihosttaskmanagerleaveruntime-method"></a><span data-ttu-id="0759c-102">IHostTaskManager::LeaveRuntime — Metoda</span><span class="sxs-lookup"><span data-stu-id="0759c-102">IHostTaskManager::LeaveRuntime Method</span></span>
<span data-ttu-id="0759c-103">Powiadamia hosta, że aktualnie wykonywane zadanie ma opuścić środowisko uruchomieniowe języka wspólnego (CLR) i wprowadzić kod niezarządzany.</span><span class="sxs-lookup"><span data-stu-id="0759c-103">Notifies the host that the currently executing task is about to leave the common language runtime (CLR) and enter unmanaged code.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="0759c-104">Odpowiednie wywołanie [IHostTaskManager:: EnterRuntime —](ihosttaskmanager-enterruntime-method.md) powiadamia hosta, że aktualnie wykonywane zadanie ponownie wprowadza kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="0759c-104">A corresponding call to [IHostTaskManager::EnterRuntime](ihosttaskmanager-enterruntime-method.md) notifies the host that the currently executing task is reentering managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0759c-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="0759c-105">Syntax</span></span>  
  
```cpp  
HRESULT LeaveRuntime (  
    [in] SIZE_T target  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0759c-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="0759c-106">Parameters</span></span>  
 `target`  
 <span data-ttu-id="0759c-107">podczas Adres w mapowanym przenośnym pliku wykonywalnym funkcji niezarządzanej, która ma zostać wywołana.</span><span class="sxs-lookup"><span data-stu-id="0759c-107">[in] The address within the mapped portable executable file of the unmanaged function to be called.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0759c-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="0759c-108">Return Value</span></span>  
  
|<span data-ttu-id="0759c-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0759c-109">HRESULT</span></span>|<span data-ttu-id="0759c-110">Opis</span><span class="sxs-lookup"><span data-stu-id="0759c-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0759c-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="0759c-111">S_OK</span></span>|<span data-ttu-id="0759c-112">`LeaveRuntime`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="0759c-112">`LeaveRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="0759c-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0759c-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0759c-114">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="0759c-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0759c-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0759c-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0759c-116">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="0759c-116">The call timed out.</span></span>|  
|<span data-ttu-id="0759c-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0759c-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0759c-118">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="0759c-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0759c-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0759c-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0759c-120">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="0759c-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0759c-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0759c-121">E_FAIL</span></span>|<span data-ttu-id="0759c-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="0759c-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0759c-123">Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="0759c-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0759c-124">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0759c-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="0759c-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="0759c-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="0759c-126">Za mało dostępnej pamięci, aby zakończyć żądaną alokację.</span><span class="sxs-lookup"><span data-stu-id="0759c-126">Not enough memory is available to complete the requested allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0759c-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0759c-127">Remarks</span></span>  
 <span data-ttu-id="0759c-128">Sekwencje wywołań do i z kodu niezarządzanego mogą być zagnieżdżane.</span><span class="sxs-lookup"><span data-stu-id="0759c-128">Call sequences to and from unmanaged code can be nested.</span></span> <span data-ttu-id="0759c-129">Na przykład na poniższej liście opisano hipotetyczną sytuację, w której sekwencja wywołań do `LeaveRuntime` , [IHostTaskManager:: ReverseEnterRuntime —](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md), [IHostTaskManager:: ReverseLeaveRuntime —](ihosttaskmanager-reverseleaveruntime-method.md), i `IHostTaskManager::EnterRuntime` umożliwia hostowi zidentyfikowanie warstw zagnieżdżonych.</span><span class="sxs-lookup"><span data-stu-id="0759c-129">For example, the list below describes a hypothetical situation in which the sequence of calls to `LeaveRuntime`, [IHostTaskManager::ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md), [IHostTaskManager::ReverseLeaveRuntime](ihosttaskmanager-reverseleaveruntime-method.md), and `IHostTaskManager::EnterRuntime` allows the host to identify the nested layers.</span></span>  
  
|<span data-ttu-id="0759c-130">Akcja</span><span class="sxs-lookup"><span data-stu-id="0759c-130">Action</span></span>|<span data-ttu-id="0759c-131">Odpowiednie wywołanie metody</span><span class="sxs-lookup"><span data-stu-id="0759c-131">Corresponding Method Call</span></span>|  
|------------|-------------------------------|  
|<span data-ttu-id="0759c-132">Zarządzany Visual Basic plik wykonywalny wywołuje niezarządzaną funkcję zapisaną w C przy użyciu wywołania platformy.</span><span class="sxs-lookup"><span data-stu-id="0759c-132">A managed Visual Basic executable calls an unmanaged function written in C by using platform invoke.</span></span>|`IHostTaskManager::LeaveRuntime`|  
|<span data-ttu-id="0759c-133">Niezarządzana funkcja języka C wywołuje metodę w zarządzanej bibliotece DLL, która została zapisywana w języku C#.</span><span class="sxs-lookup"><span data-stu-id="0759c-133">The unmanaged C function calls a method in a managed DLL written in C#.</span></span>|`IHostTaskManager::ReverseEnterRuntime`|  
|<span data-ttu-id="0759c-134">Zarządzana funkcja języka C# wywołuje inną niezarządzaną funkcję zapisaną w języku C, również przy użyciu wywołania platformy.</span><span class="sxs-lookup"><span data-stu-id="0759c-134">The managed C# function calls another unmanaged function written in C, also using platform invoke.</span></span>|`IHostTaskManager::LeaveRuntime`|  
|<span data-ttu-id="0759c-135">Druga niezarządzana funkcja zwraca wykonanie do funkcji języka C#.</span><span class="sxs-lookup"><span data-stu-id="0759c-135">The second unmanaged function returns execution to the C# function.</span></span>|`IHostTaskManager::EnterRuntime`|  
|<span data-ttu-id="0759c-136">Funkcja języka C# zwraca wykonanie do pierwszej niezarządzanej funkcji.</span><span class="sxs-lookup"><span data-stu-id="0759c-136">The C# function returns execution to the first unmanaged function.</span></span>|`IHostTaskManager::ReverseLeaveRuntime`|  
|<span data-ttu-id="0759c-137">Pierwsza niezarządzana funkcja zwraca wykonanie do programu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="0759c-137">The first unmanaged function returns execution to the Visual Basic program.</span></span>|`IHostTaskManager::EnterRuntime`|  
  
## <a name="requirements"></a><span data-ttu-id="0759c-138">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0759c-138">Requirements</span></span>  
 <span data-ttu-id="0759c-139">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0759c-139">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0759c-140">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0759c-140">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0759c-141">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="0759c-141">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0759c-142">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0759c-142">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0759c-143">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0759c-143">See also</span></span>

- [<span data-ttu-id="0759c-144">ICLRTask — Interfejs</span><span class="sxs-lookup"><span data-stu-id="0759c-144">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="0759c-145">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="0759c-145">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="0759c-146">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="0759c-146">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="0759c-147">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="0759c-147">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
