---
title: ICLRTask::RudeAbort — Metoda
ms.date: 03/30/2017
api_name:
- ICLRTask.RudeAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::RudeAbort
helpviewer_keywords:
- RudeAbort method, ICLRTask interface [.NET Framework hosting]
- ICLRTask::RudeAbort method [.NET Framework hosting]
ms.assetid: b5785468-fcd7-4cc3-8a5d-8796337b53fc
topic_type:
- apiref
ms.openlocfilehash: 69e3ecfc82985d52bd5b14e9faf2566e395b622b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124655"
---
# <a name="iclrtaskrudeabort-method"></a><span data-ttu-id="c9436-102">ICLRTask::RudeAbort — Metoda</span><span class="sxs-lookup"><span data-stu-id="c9436-102">ICLRTask::RudeAbort Method</span></span>
<span data-ttu-id="c9436-103">Instruuje środowisko uruchomieniowe języka wspólnego (CLR), aby przerwać zadanie reprezentowane przez bieżące wystąpienie [interfejsu ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) od razu i bezwarunkowo.</span><span class="sxs-lookup"><span data-stu-id="c9436-103">Instructs the common language runtime (CLR) to abort the task represented by the current [ICLRTask Interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance immediately and unconditionally.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9436-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c9436-104">Syntax</span></span>  
  
```cpp  
HRESULT RudeAbort ();   
```  
  
## <a name="return-value"></a><span data-ttu-id="c9436-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="c9436-105">Return Value</span></span>  
  
|<span data-ttu-id="c9436-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c9436-106">HRESULT</span></span>|<span data-ttu-id="c9436-107">Opis</span><span class="sxs-lookup"><span data-stu-id="c9436-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c9436-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="c9436-108">S_OK</span></span>|<span data-ttu-id="c9436-109">`RudeAbort` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="c9436-109">`RudeAbort` returned successfully.</span></span>|  
|<span data-ttu-id="c9436-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c9436-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c9436-111">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="c9436-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c9436-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c9436-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c9436-113">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="c9436-113">The call timed out.</span></span>|  
|<span data-ttu-id="c9436-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c9436-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c9436-115">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="c9436-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c9436-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c9436-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c9436-117">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="c9436-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c9436-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c9436-118">E_FAIL</span></span>|<span data-ttu-id="c9436-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="c9436-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c9436-120">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="c9436-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c9436-121">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c9436-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c9436-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c9436-122">Remarks</span></span>  
 <span data-ttu-id="c9436-123">Host wywołuje `RudeAbort`, aby natychmiast przerwać zadanie.</span><span class="sxs-lookup"><span data-stu-id="c9436-123">A host calls `RudeAbort` to abort a task immediately.</span></span> <span data-ttu-id="c9436-124">Finalizatory i procedury obsługi wyjątków nie są gwarantowane.</span><span class="sxs-lookup"><span data-stu-id="c9436-124">Finalizers and exception handling routines are not guaranteed to be executed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9436-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c9436-125">Requirements</span></span>  
 <span data-ttu-id="c9436-126">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9436-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9436-127">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c9436-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c9436-128">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c9436-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c9436-129">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9436-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9436-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c9436-130">See also</span></span>

- [<span data-ttu-id="c9436-131">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="c9436-131">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="c9436-132">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="c9436-132">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="c9436-133">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="c9436-133">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="c9436-134">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="c9436-134">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
