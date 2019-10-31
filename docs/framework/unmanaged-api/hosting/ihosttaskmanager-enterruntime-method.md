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
ms.openlocfilehash: a3af57859c5284ff45681ffc2b5aa3ea3cf8fad6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133060"
---
# <a name="ihosttaskmanagerenterruntime-method"></a><span data-ttu-id="8ef19-102">IHostTaskManager::EnterRuntime — Metoda</span><span class="sxs-lookup"><span data-stu-id="8ef19-102">IHostTaskManager::EnterRuntime Method</span></span>
<span data-ttu-id="8ef19-103">Powiadamia hosta, że wywołanie metody niezarządzanej, takie jak metoda Invoke platformy, zwraca sterowanie wykonywaniem do środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="8ef19-103">Notifies the host that a call to an unmanaged method, such as a platform invoke method, is returning execution control to the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ef19-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8ef19-104">Syntax</span></span>  
  
```cpp  
HRESULT EnterRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="8ef19-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="8ef19-105">Return Value</span></span>  
  
|<span data-ttu-id="8ef19-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8ef19-106">HRESULT</span></span>|<span data-ttu-id="8ef19-107">Opis</span><span class="sxs-lookup"><span data-stu-id="8ef19-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8ef19-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="8ef19-108">S_OK</span></span>|<span data-ttu-id="8ef19-109">`EnterRuntime` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="8ef19-109">`EnterRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="8ef19-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8ef19-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8ef19-111">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="8ef19-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8ef19-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8ef19-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8ef19-113">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="8ef19-113">The call timed out.</span></span>|  
|<span data-ttu-id="8ef19-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8ef19-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8ef19-115">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="8ef19-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8ef19-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8ef19-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8ef19-117">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="8ef19-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8ef19-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8ef19-118">E_FAIL</span></span>|<span data-ttu-id="8ef19-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="8ef19-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8ef19-120">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="8ef19-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8ef19-121">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8ef19-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="8ef19-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="8ef19-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="8ef19-123">Za mało dostępnej pamięci, aby zakończyć żądaną alokację.</span><span class="sxs-lookup"><span data-stu-id="8ef19-123">Not enough memory was available to complete the requested allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8ef19-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8ef19-124">Remarks</span></span>  
 <span data-ttu-id="8ef19-125">`EnterRuntime` jest wywoływana w celu powiadomienia hosta, że funkcja niezarządzana, dla której wykonano wcześniejsze wywołanie metody [LeaveRuntime —](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md) , zakończyła wykonywanie i zwraca sterowanie wykonywaniem do środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="8ef19-125">`EnterRuntime` is called to notify the host that an unmanaged function, for which an earlier call to the [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md) method was made, has finished executing, and is returning execution control to the runtime.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8ef19-126">[ReverseEnterRuntime —](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md) jest wywoływana w celu powiadomienia hosta, że funkcja niezarządzana, dla której wykonano wcześniejsze wywołanie `LeaveRuntime`, wywołuje kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="8ef19-126">[ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md) is called to notify the host that an unmanaged function, for which an earlier call to `LeaveRuntime` was made, is making a call into managed code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ef19-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8ef19-127">Requirements</span></span>  
 <span data-ttu-id="8ef19-128">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ef19-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ef19-129">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8ef19-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8ef19-130">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="8ef19-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8ef19-131">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ef19-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ef19-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8ef19-132">See also</span></span>

- [<span data-ttu-id="8ef19-133">Zaawansowana współdziałanie COM</span><span class="sxs-lookup"><span data-stu-id="8ef19-133">Advanced COM Interoperability</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx)
- [<span data-ttu-id="8ef19-134">Instrukcje: wywoływanie natywnych bibliotek DLL z kodu zarządzanego za pomocą funkcji PInvoke</span><span class="sxs-lookup"><span data-stu-id="8ef19-134">How to: Call Native DLLs from Managed Code Using PInvoke</span></span>](/cpp/dotnet/how-to-call-native-dlls-from-managed-code-using-pinvoke)
- [<span data-ttu-id="8ef19-135">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="8ef19-135">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="8ef19-136">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="8ef19-136">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="8ef19-137">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="8ef19-137">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="8ef19-138">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="8ef19-138">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="8ef19-139">LeaveRuntime, metoda</span><span class="sxs-lookup"><span data-stu-id="8ef19-139">LeaveRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)
