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
ms.openlocfilehash: 76f216b12bccc950a34e2b23404ac305de519f4a
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762477"
---
# <a name="iclrtaskabort-method"></a><span data-ttu-id="ef031-102">ICLRTask::Abort — Metoda</span><span class="sxs-lookup"><span data-stu-id="ef031-102">ICLRTask::Abort Method</span></span>
<span data-ttu-id="ef031-103">Żąda, aby środowisko uruchomieniowe języka wspólnego (CLR) przerywał zadanie, które reprezentuje bieżące wystąpienie [ICLRTask](iclrtask-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="ef031-103">Requests that the common language runtime (CLR) abort the task that the current [ICLRTask](iclrtask-interface.md) instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef031-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ef031-104">Syntax</span></span>  
  
```cpp  
HRESULT Abort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="ef031-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ef031-105">Return Value</span></span>  
  
|<span data-ttu-id="ef031-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ef031-106">HRESULT</span></span>|<span data-ttu-id="ef031-107">Opis</span><span class="sxs-lookup"><span data-stu-id="ef031-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ef031-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="ef031-108">S_OK</span></span>|<span data-ttu-id="ef031-109">`Abort`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="ef031-109">`Abort` returned successfully.</span></span>|  
|<span data-ttu-id="ef031-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ef031-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ef031-111">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="ef031-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ef031-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ef031-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ef031-113">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="ef031-113">The call timed out.</span></span>|  
|<span data-ttu-id="ef031-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ef031-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ef031-115">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="ef031-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ef031-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ef031-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ef031-117">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="ef031-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ef031-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ef031-118">E_FAIL</span></span>|<span data-ttu-id="ef031-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="ef031-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ef031-120">Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="ef031-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ef031-121">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ef031-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ef031-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ef031-122">Remarks</span></span>  
 <span data-ttu-id="ef031-123">Środowisko CLR podnosi <xref:System.Threading.ThreadAbortException> czas, gdy jest wywoływany przez hosta `Abort` .</span><span class="sxs-lookup"><span data-stu-id="ef031-123">The CLR raises a <xref:System.Threading.ThreadAbortException> when the host calls `Abort`.</span></span> <span data-ttu-id="ef031-124">Zwraca natychmiast po zainicjowaniu informacji o wyjątku, bez czekania na wykonanie kodu użytkownika, takiego jak finalizatory lub mechanizmy obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="ef031-124">It returns immediately after the exception information is initialized, without waiting for user code, such as finalizers or exception handling mechanisms, to execute.</span></span> <span data-ttu-id="ef031-125">Wywołania w `Abort` ten sposób szybko zwracają.</span><span class="sxs-lookup"><span data-stu-id="ef031-125">Calls to `Abort` thus return quickly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef031-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ef031-126">Requirements</span></span>  
 <span data-ttu-id="ef031-127">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ef031-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef031-128">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ef031-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ef031-129">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ef031-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ef031-130">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef031-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef031-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ef031-131">See also</span></span>

- [<span data-ttu-id="ef031-132">ICLRTask — Interfejs</span><span class="sxs-lookup"><span data-stu-id="ef031-132">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="ef031-133">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="ef031-133">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="ef031-134">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="ef031-134">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="ef031-135">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="ef031-135">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
