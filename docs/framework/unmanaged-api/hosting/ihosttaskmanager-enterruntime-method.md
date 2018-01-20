---
title: "IHostTaskManager::EnterRuntime — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTaskManager.EnterRuntime
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTaskManager::EnterRuntime
helpviewer_keywords:
- IHostTaskManager::EnterRuntime method [.NET Framework hosting]
- EnterRuntime method [.NET Framework hosting]
ms.assetid: 1aa7a4b1-636a-4f5e-b834-b406d72f7120
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 70c9e83311fd7427895e1957d3511a45c47434e6
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="ihosttaskmanagerenterruntime-method"></a><span data-ttu-id="32a01-102">IHostTaskManager::EnterRuntime — Metoda</span><span class="sxs-lookup"><span data-stu-id="32a01-102">IHostTaskManager::EnterRuntime Method</span></span>
<span data-ttu-id="32a01-103">Powiadamia hosta, czy wywołanie do metody niezarządzanych, takich jak platforma wywołania metody, jest zwracany Kontrola wykonywania do środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="32a01-103">Notifies the host that a call to an unmanaged method, such as a platform invoke method, is returning execution control to the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32a01-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="32a01-104">Syntax</span></span>  
  
```  
HRESULT EnterRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="32a01-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="32a01-105">Return Value</span></span>  
  
|<span data-ttu-id="32a01-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="32a01-106">HRESULT</span></span>|<span data-ttu-id="32a01-107">Opis</span><span class="sxs-lookup"><span data-stu-id="32a01-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="32a01-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="32a01-108">S_OK</span></span>|<span data-ttu-id="32a01-109">`EnterRuntime`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="32a01-109">`EnterRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="32a01-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="32a01-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="32a01-111">Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="32a01-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="32a01-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="32a01-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="32a01-113">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="32a01-113">The call timed out.</span></span>|  
|<span data-ttu-id="32a01-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="32a01-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="32a01-115">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="32a01-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="32a01-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="32a01-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="32a01-117">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="32a01-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="32a01-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="32a01-118">E_FAIL</span></span>|<span data-ttu-id="32a01-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="32a01-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="32a01-120">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="32a01-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="32a01-121">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="32a01-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="32a01-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="32a01-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="32a01-123">Za mało pamięci nie była dostępna do wykonania żądanej alokacji.</span><span class="sxs-lookup"><span data-stu-id="32a01-123">Not enough memory was available to complete the requested allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="32a01-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="32a01-124">Remarks</span></span>  
 <span data-ttu-id="32a01-125">`EnterRuntime`jest wywoływana w celu powiadomienia hosta który niezarządzanej funkcji, dla którego wcześniej wywołanie [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md) — metoda została wprowadzona, zakończono wykonywanie i zwraca Kontrola wykonywania do środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="32a01-125">`EnterRuntime` is called to notify the host that an unmanaged function, for which an earlier call to the [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md) method was made, has finished executing, and is returning execution control to the runtime.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="32a01-126">[ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md) jest wywoływana w celu powiadomienia hosta który niezarządzanej funkcji, dla którego wcześniej wywołanie `LeaveRuntime` została wprowadzona, jest wywołania wewnątrz kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="32a01-126">[ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md) is called to notify the host that an unmanaged function, for which an earlier call to `LeaveRuntime` was made, is making a call into managed code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32a01-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="32a01-127">Requirements</span></span>  
 <span data-ttu-id="32a01-128">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32a01-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32a01-129">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="32a01-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="32a01-130">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="32a01-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="32a01-131">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32a01-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32a01-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="32a01-132">See Also</span></span>  
 [<span data-ttu-id="32a01-133">Współdziałanie COM zaawansowane</span><span class="sxs-lookup"><span data-stu-id="32a01-133">Advanced COM Interoperability</span></span>](http://msdn.microsoft.com/library/3ada36e5-2390-4d70-b490-6ad8de92f2fb)  
 [<span data-ttu-id="32a01-134">Instrukcje: wywoływanie natywnych bibliotek DLL z kodu zarządzanego za pomocą funkcji PInvoke</span><span class="sxs-lookup"><span data-stu-id="32a01-134">How to: Call Native DLLs from Managed Code Using PInvoke</span></span>](/cpp/dotnet/how-to-call-native-dlls-from-managed-code-using-pinvoke)  
 [<span data-ttu-id="32a01-135">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="32a01-135">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="32a01-136">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="32a01-136">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="32a01-137">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="32a01-137">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="32a01-138">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="32a01-138">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="32a01-139">LeaveRuntime, metoda</span><span class="sxs-lookup"><span data-stu-id="32a01-139">LeaveRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)
