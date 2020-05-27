---
title: IHostTask::GetPriority — Metoda
ms.date: 03/30/2017
api_name:
- IHostTask.GetPriority
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::GetPriority
helpviewer_keywords:
- GetPriority method [.NET Framework hosting]
- IHostTask::GetPriority method [.NET Framework hosting]
ms.assetid: 4b463cd6-77c1-4f9a-8518-346ad8fc4b70
topic_type:
- apiref
ms.openlocfilehash: e41fcf2f03b024c1b4ae0032c0ff025d6e2aa1c3
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842507"
---
# <a name="ihosttaskgetpriority-method"></a><span data-ttu-id="2b0dc-102">IHostTask::GetPriority — Metoda</span><span class="sxs-lookup"><span data-stu-id="2b0dc-102">IHostTask::GetPriority Method</span></span>
<span data-ttu-id="2b0dc-103">Pobiera poziom priorytetu wątku zadania reprezentowanego przez bieżące wystąpienie [IHostTask](ihosttask-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="2b0dc-103">Gets the thread priority level of the task represented by the current [IHostTask](ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b0dc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2b0dc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPriority (  
    [out] int *pPriority  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2b0dc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2b0dc-105">Parameters</span></span>  
 `pPriority`  
 <span data-ttu-id="2b0dc-106">określoną Wskaźnik do liczby całkowitej, który wskazuje poziom priorytetu wątku zadania reprezentowanego przez bieżące `IHostTask` wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="2b0dc-106">[out] A pointer to an integer that indicates the thread priority level of the task represented by the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2b0dc-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="2b0dc-107">Return Value</span></span>  
  
|<span data-ttu-id="2b0dc-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2b0dc-108">HRESULT</span></span>|<span data-ttu-id="2b0dc-109">Opis</span><span class="sxs-lookup"><span data-stu-id="2b0dc-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2b0dc-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="2b0dc-110">S_OK</span></span>|<span data-ttu-id="2b0dc-111">`GetPriority`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="2b0dc-111">`GetPriority` returned successfully.</span></span>|  
|<span data-ttu-id="2b0dc-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2b0dc-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2b0dc-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="2b0dc-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2b0dc-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2b0dc-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2b0dc-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="2b0dc-115">The call timed out.</span></span>|  
|<span data-ttu-id="2b0dc-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2b0dc-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2b0dc-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="2b0dc-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2b0dc-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2b0dc-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2b0dc-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="2b0dc-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2b0dc-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2b0dc-120">E_FAIL</span></span>|<span data-ttu-id="2b0dc-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="2b0dc-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2b0dc-122">Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="2b0dc-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2b0dc-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="2b0dc-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2b0dc-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2b0dc-124">Remarks</span></span>  
 <span data-ttu-id="2b0dc-125">Wartości poziomu priorytetu wątku są definiowane przez `SetThreadPriority` funkcję Win32.</span><span class="sxs-lookup"><span data-stu-id="2b0dc-125">Thread priority level values are defined by the Win32 `SetThreadPriority` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b0dc-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2b0dc-126">Requirements</span></span>  
 <span data-ttu-id="2b0dc-127">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b0dc-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b0dc-128">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2b0dc-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2b0dc-129">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2b0dc-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2b0dc-130">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b0dc-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b0dc-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2b0dc-131">See also</span></span>

- [<span data-ttu-id="2b0dc-132">ICLRTask — Interfejs</span><span class="sxs-lookup"><span data-stu-id="2b0dc-132">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="2b0dc-133">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="2b0dc-133">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="2b0dc-134">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="2b0dc-134">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="2b0dc-135">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="2b0dc-135">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
