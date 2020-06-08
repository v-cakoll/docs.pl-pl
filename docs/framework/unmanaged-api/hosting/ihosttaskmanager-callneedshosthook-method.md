---
title: IHostTaskManager::CallNeedsHostHook — Metoda
ms.date: 03/30/2017
api_name:
- IHostTaskManager.CallNeedsHostHook
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::CallNeedsHostHook
helpviewer_keywords:
- CallNeedsHostHook method [.NET Framework hosting]
- IHostTaskManager::CallNeedsHostHook method [.NET Framework hosting]
ms.assetid: b60f1f59-9825-4b57-961f-d2979518e6a7
topic_type:
- apiref
ms.openlocfilehash: 8cbac3b4ad25ba7dc01413f0c1b44541c43b3999
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503877"
---
# <a name="ihosttaskmanagercallneedshosthook-method"></a><span data-ttu-id="b8af8-102">IHostTaskManager::CallNeedsHostHook — Metoda</span><span class="sxs-lookup"><span data-stu-id="b8af8-102">IHostTaskManager::CallNeedsHostHook Method</span></span>
<span data-ttu-id="b8af8-103">Umożliwia hostowi określenie, czy środowisko uruchomieniowe języka wspólnego (CLR) może być wbudowane w określone wywołanie do niezarządzanej funkcji.</span><span class="sxs-lookup"><span data-stu-id="b8af8-103">Enables the host to specify whether the common language runtime (CLR) can inline the specified call to an unmanaged function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8af8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b8af8-104">Syntax</span></span>  
  
```cpp  
HRESULT CallNeedsHostHook (  
    [in]  SIZE_T target,
    [out] BOOL   *pbCallNeedsHostHook  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b8af8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b8af8-105">Parameters</span></span>  
 `target`  
 <span data-ttu-id="b8af8-106">podczas Adres w zamapowanym przenośnym pliku wykonywalnym (PE) niezarządzanej funkcji, która ma zostać wywołana.</span><span class="sxs-lookup"><span data-stu-id="b8af8-106">[in] The address within the mapped portable executable (PE) file of the unmanaged function that is to be called.</span></span>  
  
 `pbCallNeedsHostHook`  
 <span data-ttu-id="b8af8-107">określoną Wskaźnik do wartości logicznej wskazującej, czy host wymaga wywołania.</span><span class="sxs-lookup"><span data-stu-id="b8af8-107">[out] A pointer to a Boolean value that indicates whether the host requires the call to be hooked.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b8af8-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b8af8-108">Return Value</span></span>  
  
|<span data-ttu-id="b8af8-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b8af8-109">HRESULT</span></span>|<span data-ttu-id="b8af8-110">Opis</span><span class="sxs-lookup"><span data-stu-id="b8af8-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b8af8-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="b8af8-111">S_OK</span></span>|<span data-ttu-id="b8af8-112">`CallNeedsHostHook`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="b8af8-112">`CallNeedsHostHook` returned successfully.</span></span>|  
|<span data-ttu-id="b8af8-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b8af8-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b8af8-114">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="b8af8-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b8af8-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b8af8-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b8af8-116">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="b8af8-116">The call timed out.</span></span>|  
|<span data-ttu-id="b8af8-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b8af8-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b8af8-118">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="b8af8-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b8af8-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b8af8-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b8af8-120">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="b8af8-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b8af8-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b8af8-121">E_FAIL</span></span>|<span data-ttu-id="b8af8-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="b8af8-122">An unknown catastrophic failure has occurred.</span></span> <span data-ttu-id="b8af8-123">Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="b8af8-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b8af8-124">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b8af8-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b8af8-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b8af8-125">Remarks</span></span>  
 <span data-ttu-id="b8af8-126">Aby ułatwić optymalizację wykonywania kodu, środowisko CLR wykonuje analizę każdego wywołania wywołania platformy podczas kompilacji, aby określić, czy wywołanie może być wbudowane.</span><span class="sxs-lookup"><span data-stu-id="b8af8-126">To help optimize code execution, the CLR performs an analysis of each platform invoke call during compilation to determine whether the call can be inlined.</span></span> <span data-ttu-id="b8af8-127">`CallNeedsHostHook`umożliwia hostowi przesłonięcie tej decyzji przez wymaganie wywołania niezarządzanej funkcji.</span><span class="sxs-lookup"><span data-stu-id="b8af8-127">`CallNeedsHostHook` enables the host to override that decision by requiring that a call to an unmanaged function be hooked.</span></span> <span data-ttu-id="b8af8-128">Jeśli host wymaga elementu Hook, środowisko uruchomieniowe nie wywołuje wywołania.</span><span class="sxs-lookup"><span data-stu-id="b8af8-128">If the host requires a hook, the runtime does not inline the call.</span></span>  
  
 <span data-ttu-id="b8af8-129">Host zwykle wymaga punktu zaczepienia, w którym należy dostosować stan zmiennoprzecinkowy lub po odebraniu powiadomienia, że wywołanie przejdzie do stanu, w którym host nie może śledzić żądań dotyczących pamięci lub wszelkich wykonanych blokad.</span><span class="sxs-lookup"><span data-stu-id="b8af8-129">The host typically would require a hook where it must adjust a floating-point state, or upon receiving notification that a call is entering a state where the host cannot track the runtime's requests for memory or any locks taken.</span></span> <span data-ttu-id="b8af8-130">Gdy host wymaga, aby wywołanie było podłączane, środowisko uruchomieniowe powiadamia hosta przejść do i z kodu zarządzanego za pomocą wywołań do [EnterRuntime —](ihosttaskmanager-enterruntime-method.md), [LeaveRuntime —](ihosttaskmanager-leaveruntime-method.md), [ReverseEnterRuntime —](ihosttaskmanager-reverseenterruntime-method.md)i [ReverseLeaveRuntime —](ihosttaskmanager-reverseleaveruntime-method.md).</span><span class="sxs-lookup"><span data-stu-id="b8af8-130">When the host requires that the call be hooked, the runtime notifies the host of transitions to and from managed code by using calls to [EnterRuntime](ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](ihosttaskmanager-leaveruntime-method.md), [ReverseEnterRuntime](ihosttaskmanager-reverseenterruntime-method.md), and [ReverseLeaveRuntime](ihosttaskmanager-reverseleaveruntime-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8af8-131">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b8af8-131">Requirements</span></span>  
 <span data-ttu-id="b8af8-132">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8af8-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8af8-133">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b8af8-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b8af8-134">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b8af8-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b8af8-135">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8af8-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8af8-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b8af8-136">See also</span></span>

- [<span data-ttu-id="b8af8-137">ICLRTask — Interfejs</span><span class="sxs-lookup"><span data-stu-id="b8af8-137">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="b8af8-138">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="b8af8-138">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="b8af8-139">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="b8af8-139">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="b8af8-140">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="b8af8-140">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
