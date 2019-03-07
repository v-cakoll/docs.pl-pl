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
ms.openlocfilehash: 2059657a6f4543ee29d795ecae7b93b72876fdf4
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57474634"
---
# <a name="ihosttaskmanagerleaveruntime-method"></a><span data-ttu-id="74ce7-102">IHostTaskManager::LeaveRuntime — Metoda</span><span class="sxs-lookup"><span data-stu-id="74ce7-102">IHostTaskManager::LeaveRuntime Method</span></span>
<span data-ttu-id="74ce7-103">Powiadamia hosta, że aktualnie wykonywane zadanie zostanie pozostaw środowisko uruchomieniowe języka wspólnego (CLR), a następnie wprowadź kod niezarządzany.</span><span class="sxs-lookup"><span data-stu-id="74ce7-103">Notifies the host that the currently executing task is about to leave the common language runtime (CLR) and enter unmanaged code.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="74ce7-104">Do odpowiedniego wywołania [ihosttaskmanager::enterruntime —](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md) powiadamia hosta, że aktualnie wykonywane zadanie ponownego wprowadzania kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="74ce7-104">A corresponding call to [IHostTaskManager::EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md) notifies the host that the currently executing task is reentering managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74ce7-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="74ce7-105">Syntax</span></span>  
  
```  
HRESULT LeaveRuntime (  
    [in] SIZE_T target  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="74ce7-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="74ce7-106">Parameters</span></span>  
 `target`  
 <span data-ttu-id="74ce7-107">[in] Adres w ramach zamapowanego przenośny plik wykonywalny niezarządzanej funkcji do wywołania.</span><span class="sxs-lookup"><span data-stu-id="74ce7-107">[in] The address within the mapped portable executable file of the unmanaged function to be called.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="74ce7-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="74ce7-108">Return Value</span></span>  
  
|<span data-ttu-id="74ce7-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="74ce7-109">HRESULT</span></span>|<span data-ttu-id="74ce7-110">Opis</span><span class="sxs-lookup"><span data-stu-id="74ce7-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="74ce7-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="74ce7-111">S_OK</span></span>|<span data-ttu-id="74ce7-112">`LeaveRuntime` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="74ce7-112">`LeaveRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="74ce7-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="74ce7-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="74ce7-114">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="74ce7-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="74ce7-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="74ce7-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="74ce7-116">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="74ce7-116">The call timed out.</span></span>|  
|<span data-ttu-id="74ce7-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="74ce7-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="74ce7-118">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="74ce7-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="74ce7-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="74ce7-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="74ce7-120">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="74ce7-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="74ce7-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="74ce7-121">E_FAIL</span></span>|<span data-ttu-id="74ce7-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="74ce7-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="74ce7-123">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="74ce7-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="74ce7-124">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="74ce7-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="74ce7-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="74ce7-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="74ce7-126">Nie ma wystarczającej ilości pamięci jest dostępny w celu zakończenia żądanej alokacji.</span><span class="sxs-lookup"><span data-stu-id="74ce7-126">Not enough memory is available to complete the requested allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="74ce7-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="74ce7-127">Remarks</span></span>  
 <span data-ttu-id="74ce7-128">Może być zagnieżdżona sekwencji wywołań do i z kodem niezarządzanym.</span><span class="sxs-lookup"><span data-stu-id="74ce7-128">Call sequences to and from unmanaged code can be nested.</span></span> <span data-ttu-id="74ce7-129">Na przykład poniższa lista zawiera hipotetyczny sytuacji, w którym Sekwencja wywołań `LeaveRuntime`, [ihosttaskmanager::reverseenterruntime —](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md), [ihosttaskmanager::reverseleaveruntime —](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md), i `IHostTaskManager::EnterRuntime` Zezwalaj hostowi na określenie zagnieżdżonych warstw.</span><span class="sxs-lookup"><span data-stu-id="74ce7-129">For example, the list below describes a hypothetical situation in which the sequence of calls to `LeaveRuntime`, [IHostTaskManager::ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md), [IHostTaskManager::ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md), and `IHostTaskManager::EnterRuntime` allows the host to identify the nested layers.</span></span>  
  
|<span data-ttu-id="74ce7-130">Akcja</span><span class="sxs-lookup"><span data-stu-id="74ce7-130">Action</span></span>|<span data-ttu-id="74ce7-131">Odpowiedniego wywołania metody</span><span class="sxs-lookup"><span data-stu-id="74ce7-131">Corresponding Method Call</span></span>|  
|------------|-------------------------------|  
|<span data-ttu-id="74ce7-132">Wywołaj niezarządzanej funkcji w języku C za pomocą platformy zarządzane wywołania pliku wykonywalnego języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="74ce7-132">A managed Visual Basic executable calls an unmanaged function written in C by using platform invoke.</span></span>|`IHostTaskManager::LeaveRuntime`|  
|<span data-ttu-id="74ce7-133">Niezarządzanej funkcji C wywołuje metodę w zarządzanej biblioteki DLL, napisany w C#.</span><span class="sxs-lookup"><span data-stu-id="74ce7-133">The unmanaged C function calls a method in a managed DLL written in C#.</span></span>|`IHostTaskManager::ReverseEnterRuntime`|  
|<span data-ttu-id="74ce7-134">Zarządzany C# funkcja wywołuje innej niezarządzanej funkcji w języku C, również przy użyciu platformy wywołania.</span><span class="sxs-lookup"><span data-stu-id="74ce7-134">The managed C# function calls another unmanaged function written in C, also using platform invoke.</span></span>|`IHostTaskManager::LeaveRuntime`|  
|<span data-ttu-id="74ce7-135">Druga funkcja niezarządzanych zwraca wykonanie do C# funkcji.</span><span class="sxs-lookup"><span data-stu-id="74ce7-135">The second unmanaged function returns execution to the C# function.</span></span>|`IHostTaskManager::EnterRuntime`|  
|<span data-ttu-id="74ce7-136">C# Funkcja zwraca wykonanie do pierwszej funkcji niezarządzanych.</span><span class="sxs-lookup"><span data-stu-id="74ce7-136">The C# function returns execution to the first unmanaged function.</span></span>|`IHostTaskManager::ReverseLeaveRuntime`|  
|<span data-ttu-id="74ce7-137">Pierwszy niezarządzanej funkcji zwraca wykonanie do programu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="74ce7-137">The first unmanaged function returns execution to the Visual Basic program.</span></span>|`IHostTaskManager::EnterRuntime`|  
  
## <a name="requirements"></a><span data-ttu-id="74ce7-138">Wymagania</span><span class="sxs-lookup"><span data-stu-id="74ce7-138">Requirements</span></span>  
 <span data-ttu-id="74ce7-139">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74ce7-139">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74ce7-140">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="74ce7-140">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="74ce7-141">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="74ce7-141">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="74ce7-142">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74ce7-142">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74ce7-143">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="74ce7-143">See also</span></span>
- [<span data-ttu-id="74ce7-144">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="74ce7-144">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="74ce7-145">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="74ce7-145">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="74ce7-146">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="74ce7-146">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="74ce7-147">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="74ce7-147">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
