---
title: IHostTask::Join — Metoda
ms.date: 03/30/2017
api_name:
- IHostTask.Join
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::Join
helpviewer_keywords:
- IHostTask::Join method [.NET Framework hosting]
- Join method, IHostTask interface [.NET Framework hosting]
ms.assetid: 2cffcc52-19e0-4ced-a440-fc7375078ac9
topic_type:
- apiref
ms.openlocfilehash: 8fa59e065042565b4a543106fff714558cef42ec
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842247"
---
# <a name="ihosttaskjoin-method"></a><span data-ttu-id="0b967-102">IHostTask::Join — Metoda</span><span class="sxs-lookup"><span data-stu-id="0b967-102">IHostTask::Join Method</span></span>
<span data-ttu-id="0b967-103">Blokuje zadanie wywołujące do momentu zakończenia zadania reprezentowanego przez bieżące wystąpienie [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) , upłynie określony przedział czasu lub [IHostTask:: Alert](ihosttask-alert-method.md) .</span><span class="sxs-lookup"><span data-stu-id="0b967-103">Blocks the calling task until the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance completes, the specified time interval elapses, or [IHostTask::Alert](ihosttask-alert-method.md) is called.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b967-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0b967-104">Syntax</span></span>  
  
```cpp  
HRESULT Join (  
    [in] DWORD milliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0b967-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0b967-105">Parameters</span></span>  
 `milliseconds`  
 <span data-ttu-id="0b967-106">podczas Interwał czasu (w milisekundach) oczekiwania na zakończenie zadania.</span><span class="sxs-lookup"><span data-stu-id="0b967-106">[in] The time interval, in milliseconds, to wait for the task to terminate.</span></span> <span data-ttu-id="0b967-107">Jeśli ten interwał upłynie przed zakończeniem zadania, odblokowuje zadanie wywołujące.</span><span class="sxs-lookup"><span data-stu-id="0b967-107">If this interval elapses before the task terminates, the calling task unblocks.</span></span>  
  
 `option`  
 <span data-ttu-id="0b967-108">podczas Jedna z wartości [WAIT_OPTION](wait-option-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="0b967-108">[in] One of the [WAIT_OPTION](wait-option-enumeration.md) values.</span></span> <span data-ttu-id="0b967-109">Wartość WAIT_ALERTABLE powoduje, że host wznowi zadanie, jeśli `Alert` jest wywoływana przed `milliseconds` upływem czasu.</span><span class="sxs-lookup"><span data-stu-id="0b967-109">A value of WAIT_ALERTABLE instructs the host to wake the task if `Alert` is called before `milliseconds` elapses.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0b967-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="0b967-110">Return Value</span></span>  
  
|<span data-ttu-id="0b967-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0b967-111">HRESULT</span></span>|<span data-ttu-id="0b967-112">Opis</span><span class="sxs-lookup"><span data-stu-id="0b967-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0b967-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="0b967-113">S_OK</span></span>|<span data-ttu-id="0b967-114">`Join`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="0b967-114">`Join` returned successfully.</span></span>|  
|<span data-ttu-id="0b967-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0b967-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0b967-116">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="0b967-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0b967-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0b967-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0b967-118">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="0b967-118">The call timed out.</span></span>|  
|<span data-ttu-id="0b967-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0b967-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0b967-120">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="0b967-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0b967-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0b967-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0b967-122">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna albo bieżące `IHostTask` wystąpienie nie jest skojarzone z zadaniem.</span><span class="sxs-lookup"><span data-stu-id="0b967-122">An event was canceled while a blocked thread or fiber was waiting on it, or the current `IHostTask` instance is not associated with a task.</span></span>|  
|<span data-ttu-id="0b967-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0b967-123">E_FAIL</span></span>|<span data-ttu-id="0b967-124">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="0b967-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0b967-125">Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="0b967-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0b967-126">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0b967-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0b967-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0b967-127">Requirements</span></span>  
 <span data-ttu-id="0b967-128">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b967-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b967-129">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0b967-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0b967-130">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="0b967-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0b967-131">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b967-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b967-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0b967-132">See also</span></span>

- [<span data-ttu-id="0b967-133">ICLRTask — Interfejs</span><span class="sxs-lookup"><span data-stu-id="0b967-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="0b967-134">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="0b967-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="0b967-135">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="0b967-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="0b967-136">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="0b967-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="0b967-137">WAIT_OPTION — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="0b967-137">WAIT_OPTION Enumeration</span></span>](wait-option-enumeration.md)
