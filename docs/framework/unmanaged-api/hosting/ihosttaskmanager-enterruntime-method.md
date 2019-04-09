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
ms.openlocfilehash: e4ef2971d9835070e9db72a5e5d370ff35c8edfe
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59106443"
---
# <a name="ihosttaskmanagerenterruntime-method"></a><span data-ttu-id="234a7-102">IHostTaskManager::EnterRuntime — Metoda</span><span class="sxs-lookup"><span data-stu-id="234a7-102">IHostTaskManager::EnterRuntime Method</span></span>
<span data-ttu-id="234a7-103">Powiadamia hosta, że wywołanie metody niezarządzanego, takie jak metody wywołania platformy zwraca Kontrola wykonywania na środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="234a7-103">Notifies the host that a call to an unmanaged method, such as a platform invoke method, is returning execution control to the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="234a7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="234a7-104">Syntax</span></span>  
  
```  
HRESULT EnterRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="234a7-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="234a7-105">Return Value</span></span>  
  
|<span data-ttu-id="234a7-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="234a7-106">HRESULT</span></span>|<span data-ttu-id="234a7-107">Opis</span><span class="sxs-lookup"><span data-stu-id="234a7-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="234a7-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="234a7-108">S_OK</span></span>|`EnterRuntime` <span data-ttu-id="234a7-109">pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="234a7-109">returned successfully.</span></span>|  
|<span data-ttu-id="234a7-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="234a7-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="234a7-111">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="234a7-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="234a7-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="234a7-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="234a7-113">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="234a7-113">The call timed out.</span></span>|  
|<span data-ttu-id="234a7-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="234a7-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="234a7-115">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="234a7-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="234a7-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="234a7-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="234a7-117">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="234a7-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="234a7-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="234a7-118">E_FAIL</span></span>|<span data-ttu-id="234a7-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="234a7-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="234a7-120">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="234a7-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="234a7-121">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="234a7-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="234a7-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="234a7-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="234a7-123">Za mało pamięci była dostępna do wykonania żądanej alokacji.</span><span class="sxs-lookup"><span data-stu-id="234a7-123">Not enough memory was available to complete the requested allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="234a7-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="234a7-124">Remarks</span></span>  
 `EnterRuntime` <span data-ttu-id="234a7-125">jest wywoływana w celu powiadomienia hosta, niezarządzanej funkcji, dla którego podczas wcześniejszego wywołania [leaveruntime —](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md) metoda została wprowadzona, zakończenia i zwraca Kontrola wykonywania do środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="234a7-125">is called to notify the host that an unmanaged function, for which an earlier call to the [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md) method was made, has finished executing, and is returning execution control to the runtime.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="234a7-126">[Reverseenterruntime —](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md) jest wywoływana w celu powiadomienia hosta, niezarządzanej funkcji, dla którego podczas wcześniejszego wywołania `LeaveRuntime` została wprowadzona, wywołuje element kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="234a7-126">[ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md) is called to notify the host that an unmanaged function, for which an earlier call to `LeaveRuntime` was made, is making a call into managed code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="234a7-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="234a7-127">Requirements</span></span>  
 <span data-ttu-id="234a7-128">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="234a7-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="234a7-129">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="234a7-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="234a7-130">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="234a7-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="234a7-131">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="234a7-131">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="234a7-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="234a7-132">See also</span></span>

- [<span data-ttu-id="234a7-133">Zaawansowane współdziałanie modeli COM</span><span class="sxs-lookup"><span data-stu-id="234a7-133">Advanced COM Interoperability</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx)
- [<span data-ttu-id="234a7-134">Instrukcje: Wywoływanie natywnych bibliotek DLL z kodu zarządzanego za pomocą funkcji PInvoke</span><span class="sxs-lookup"><span data-stu-id="234a7-134">How to: Call Native DLLs from Managed Code Using PInvoke</span></span>](/cpp/dotnet/how-to-call-native-dlls-from-managed-code-using-pinvoke)
- [<span data-ttu-id="234a7-135">ICLRTask — Interfejs</span><span class="sxs-lookup"><span data-stu-id="234a7-135">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="234a7-136">ICLRTaskManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="234a7-136">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="234a7-137">IHostTask — Interfejs</span><span class="sxs-lookup"><span data-stu-id="234a7-137">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="234a7-138">IHostTaskManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="234a7-138">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="234a7-139">LeaveRuntime, metoda</span><span class="sxs-lookup"><span data-stu-id="234a7-139">LeaveRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)
