---
title: ICLRTask::Abort — Metoda
ms.date: 03/30/2017
api_name:
- ICLRTask.Abort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::Abort
helpviewer_keywords:
- ICLRTask::Abort method [.NET Framework hosting]
- Abort method, ICLRTask interface [.NET Framework hosting]
ms.assetid: b3594b5f-2e41-4e36-9096-3586276a138c
topic_type:
- apiref
ms.openlocfilehash: 026d4c14abed030b80e8e1b3f8363fbd59ac05e4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124917"
---
# <a name="iclrtaskabort-method"></a><span data-ttu-id="d51b0-102">ICLRTask::Abort — Metoda</span><span class="sxs-lookup"><span data-stu-id="d51b0-102">ICLRTask::Abort Method</span></span>
<span data-ttu-id="d51b0-103">Żąda, aby środowisko uruchomieniowe języka wspólnego (CLR) przerywał zadanie, które reprezentuje bieżące wystąpienie [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="d51b0-103">Requests that the common language runtime (CLR) abort the task that the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d51b0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d51b0-104">Syntax</span></span>  
  
```cpp  
HRESULT Abort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="d51b0-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d51b0-105">Return Value</span></span>  
  
|<span data-ttu-id="d51b0-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d51b0-106">HRESULT</span></span>|<span data-ttu-id="d51b0-107">Opis</span><span class="sxs-lookup"><span data-stu-id="d51b0-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d51b0-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="d51b0-108">S_OK</span></span>|<span data-ttu-id="d51b0-109">`Abort` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="d51b0-109">`Abort` returned successfully.</span></span>|  
|<span data-ttu-id="d51b0-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d51b0-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d51b0-111">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="d51b0-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d51b0-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d51b0-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d51b0-113">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="d51b0-113">The call timed out.</span></span>|  
|<span data-ttu-id="d51b0-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d51b0-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d51b0-115">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="d51b0-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d51b0-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d51b0-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d51b0-117">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="d51b0-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d51b0-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d51b0-118">E_FAIL</span></span>|<span data-ttu-id="d51b0-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="d51b0-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d51b0-120">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="d51b0-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d51b0-121">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d51b0-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d51b0-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d51b0-122">Remarks</span></span>  
 <span data-ttu-id="d51b0-123">Środowisko CLR wywołuje <xref:System.Threading.ThreadAbortException>, gdy host wywoła `Abort`.</span><span class="sxs-lookup"><span data-stu-id="d51b0-123">The CLR raises a <xref:System.Threading.ThreadAbortException> when the host calls `Abort`.</span></span> <span data-ttu-id="d51b0-124">Zwraca natychmiast po zainicjowaniu informacji o wyjątku, bez czekania na wykonanie kodu użytkownika, takiego jak finalizatory lub mechanizmy obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="d51b0-124">It returns immediately after the exception information is initialized, without waiting for user code, such as finalizers or exception handling mechanisms, to execute.</span></span> <span data-ttu-id="d51b0-125">Wywołania `Abort` w ten sposób szybko zwracają.</span><span class="sxs-lookup"><span data-stu-id="d51b0-125">Calls to `Abort` thus return quickly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d51b0-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d51b0-126">Requirements</span></span>  
 <span data-ttu-id="d51b0-127">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d51b0-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d51b0-128">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d51b0-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d51b0-129">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d51b0-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d51b0-130">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d51b0-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d51b0-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d51b0-131">See also</span></span>

- [<span data-ttu-id="d51b0-132">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="d51b0-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="d51b0-133">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="d51b0-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="d51b0-134">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="d51b0-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="d51b0-135">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="d51b0-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
