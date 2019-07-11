---
title: IHostTaskManager::EnterRuntime — Metoda
ms.date: 03/30/2017
api_name:
- IHostTaskManager.EnterRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::EnterRuntime
helpviewer_keywords:
- IHostTaskManager::EnterRuntime method [.NET Framework hosting]
- EnterRuntime method [.NET Framework hosting]
ms.assetid: 1aa7a4b1-636a-4f5e-b834-b406d72f7120
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2a01779e6203ddfea32e72838b7e02996fd868c2
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67749612"
---
# <a name="ihosttaskmanagerenterruntime-method"></a><span data-ttu-id="52f88-102">IHostTaskManager::EnterRuntime — Metoda</span><span class="sxs-lookup"><span data-stu-id="52f88-102">IHostTaskManager::EnterRuntime Method</span></span>
<span data-ttu-id="52f88-103">Powiadamia hosta, że wywołanie metody niezarządzanego, takie jak metody wywołania platformy zwraca Kontrola wykonywania na środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="52f88-103">Notifies the host that a call to an unmanaged method, such as a platform invoke method, is returning execution control to the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52f88-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="52f88-104">Syntax</span></span>  
  
```cpp  
HRESULT EnterRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="52f88-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="52f88-105">Return Value</span></span>  
  
|<span data-ttu-id="52f88-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="52f88-106">HRESULT</span></span>|<span data-ttu-id="52f88-107">Opis</span><span class="sxs-lookup"><span data-stu-id="52f88-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="52f88-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="52f88-108">S_OK</span></span>|<span data-ttu-id="52f88-109">`EnterRuntime` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="52f88-109">`EnterRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="52f88-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="52f88-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="52f88-111">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="52f88-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="52f88-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="52f88-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="52f88-113">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="52f88-113">The call timed out.</span></span>|  
|<span data-ttu-id="52f88-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="52f88-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="52f88-115">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="52f88-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="52f88-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="52f88-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="52f88-117">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="52f88-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="52f88-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="52f88-118">E_FAIL</span></span>|<span data-ttu-id="52f88-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="52f88-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="52f88-120">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="52f88-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="52f88-121">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="52f88-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="52f88-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="52f88-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="52f88-123">Za mało pamięci była dostępna do wykonania żądanej alokacji.</span><span class="sxs-lookup"><span data-stu-id="52f88-123">Not enough memory was available to complete the requested allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="52f88-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="52f88-124">Remarks</span></span>  
 <span data-ttu-id="52f88-125">`EnterRuntime` jest wywoływana w celu powiadomienia hosta, niezarządzanej funkcji, dla którego podczas wcześniejszego wywołania [leaveruntime —](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md) metoda została wprowadzona, zakończenia i zwraca Kontrola wykonywania do środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="52f88-125">`EnterRuntime` is called to notify the host that an unmanaged function, for which an earlier call to the [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md) method was made, has finished executing, and is returning execution control to the runtime.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="52f88-126">[Reverseenterruntime —](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md) jest wywoływana w celu powiadomienia hosta, niezarządzanej funkcji, dla którego podczas wcześniejszego wywołania `LeaveRuntime` została wprowadzona, wywołuje element kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="52f88-126">[ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md) is called to notify the host that an unmanaged function, for which an earlier call to `LeaveRuntime` was made, is making a call into managed code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52f88-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="52f88-127">Requirements</span></span>  
 <span data-ttu-id="52f88-128">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="52f88-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52f88-129">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="52f88-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="52f88-130">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="52f88-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="52f88-131">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52f88-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52f88-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="52f88-132">See also</span></span>

- [<span data-ttu-id="52f88-133">Zaawansowane współdziałanie modeli COM</span><span class="sxs-lookup"><span data-stu-id="52f88-133">Advanced COM Interoperability</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx)
- [<span data-ttu-id="52f88-134">Instrukcje: wywoływanie natywnych bibliotek DLL z kodu zarządzanego za pomocą funkcji PInvoke</span><span class="sxs-lookup"><span data-stu-id="52f88-134">How to: Call Native DLLs from Managed Code Using PInvoke</span></span>](/cpp/dotnet/how-to-call-native-dlls-from-managed-code-using-pinvoke)
- [<span data-ttu-id="52f88-135">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="52f88-135">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="52f88-136">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="52f88-136">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="52f88-137">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="52f88-137">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="52f88-138">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="52f88-138">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="52f88-139">LeaveRuntime, metoda</span><span class="sxs-lookup"><span data-stu-id="52f88-139">LeaveRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)
