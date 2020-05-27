---
title: IHostTaskManager::ReverseEnterRuntime — Metoda
ms.date: 03/30/2017
api_name:
- IHostTaskManager.ReverseEnterRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::ReverseEnterRuntime
helpviewer_keywords:
- IHostTaskManager::ReverseEnterRuntime method [.NET Framework hosting]
- ReverseEnterRuntime method [.NET Framework hosting]
ms.assetid: b1e26bff-d3ea-436e-9867-29720df999f4
topic_type:
- apiref
ms.openlocfilehash: 41955bd2f64d53e3620dede6b6da4cef2aab45f4
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842299"
---
# <a name="ihosttaskmanagerreverseenterruntime-method"></a><span data-ttu-id="ca690-102">IHostTaskManager::ReverseEnterRuntime — Metoda</span><span class="sxs-lookup"><span data-stu-id="ca690-102">IHostTaskManager::ReverseEnterRuntime Method</span></span>
<span data-ttu-id="ca690-103">Powiadamia hosta, że wywołanie jest nawiązywane w środowisku uruchomieniowym języka wspólnego (CLR) z kodu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="ca690-103">Notifies the host that a call is being made into the common language runtime (CLR) from unmanaged code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca690-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ca690-104">Syntax</span></span>  
  
```cpp  
HRESULT ReverseEnterRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="ca690-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ca690-105">Return Value</span></span>  
  
|<span data-ttu-id="ca690-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ca690-106">HRESULT</span></span>|<span data-ttu-id="ca690-107">Opis</span><span class="sxs-lookup"><span data-stu-id="ca690-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ca690-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="ca690-108">S_OK</span></span>|<span data-ttu-id="ca690-109">`ReverseEnterRuntime`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="ca690-109">`ReverseEnterRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="ca690-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ca690-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ca690-111">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="ca690-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ca690-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ca690-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ca690-113">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="ca690-113">The call timed out.</span></span>|  
|<span data-ttu-id="ca690-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ca690-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ca690-115">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="ca690-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ca690-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ca690-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ca690-117">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="ca690-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ca690-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ca690-118">E_FAIL</span></span>|<span data-ttu-id="ca690-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="ca690-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ca690-120">Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="ca690-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ca690-121">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ca690-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="ca690-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="ca690-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="ca690-123">Za mało dostępnej pamięci, aby zakończyć żądaną alokację zasobów.</span><span class="sxs-lookup"><span data-stu-id="ca690-123">Not enough memory is available to complete the requested resource allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ca690-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ca690-124">Remarks</span></span>  
 <span data-ttu-id="ca690-125">Jeśli wywołanie do środowiska CLR zostanie wykonane z sekwencji, która pochodzi z kodu zarządzanego, każde wywołanie `ReverseEnterRuntime` odpowiada wywołaniu [ReverseLeaveRuntime —](ihosttaskmanager-reverseleaveruntime-method.md).</span><span class="sxs-lookup"><span data-stu-id="ca690-125">If the call into the CLR is made from a sequence that originated in managed code, each call to `ReverseEnterRuntime` corresponds to a call to [ReverseLeaveRuntime](ihosttaskmanager-reverseleaveruntime-method.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ca690-126">Wywołania mogą pochodzić z niezarządzanego kodu bez zagnieżdżenia.</span><span class="sxs-lookup"><span data-stu-id="ca690-126">Calls can originate from unmanaged code without being nested.</span></span> <span data-ttu-id="ca690-127">W tym przypadku nie istnieje wywołanie metody [EnterRuntime —](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime —](ihosttaskmanager-leaveruntime-method.md)lub `ReverseLeaveRuntime` , a liczba wywołań `ReverseEnterRuntime` nie jest równa liczbie wywołań do `ReverseLeaveRuntime` .</span><span class="sxs-lookup"><span data-stu-id="ca690-127">In this case, there is no call to [EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](ihosttaskmanager-leaveruntime-method.md), or `ReverseLeaveRuntime`, and the number of calls to `ReverseEnterRuntime` does not equal the number of calls to `ReverseLeaveRuntime`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca690-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ca690-128">Requirements</span></span>  
 <span data-ttu-id="ca690-129">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca690-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca690-130">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ca690-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ca690-131">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ca690-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ca690-132">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca690-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca690-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ca690-133">See also</span></span>

- [<span data-ttu-id="ca690-134">ICLRTask — Interfejs</span><span class="sxs-lookup"><span data-stu-id="ca690-134">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="ca690-135">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="ca690-135">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="ca690-136">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="ca690-136">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="ca690-137">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="ca690-137">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
