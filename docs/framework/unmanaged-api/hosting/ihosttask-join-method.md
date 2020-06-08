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
ms.openlocfilehash: 20919bd9889408821cf57817082e3c7d5cebc240
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503926"
---
# <a name="ihosttaskjoin-method"></a><span data-ttu-id="328b8-102">IHostTask::Join — Metoda</span><span class="sxs-lookup"><span data-stu-id="328b8-102">IHostTask::Join Method</span></span>
<span data-ttu-id="328b8-103">Blokuje zadanie wywołujące do momentu zakończenia zadania reprezentowanego przez bieżące wystąpienie [IHostTask](ihosttask-interface.md) , upłynie określony przedział czasu lub [IHostTask:: Alert](ihosttask-alert-method.md) .</span><span class="sxs-lookup"><span data-stu-id="328b8-103">Blocks the calling task until the task represented by the current [IHostTask](ihosttask-interface.md) instance completes, the specified time interval elapses, or [IHostTask::Alert](ihosttask-alert-method.md) is called.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="328b8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="328b8-104">Syntax</span></span>  
  
```cpp  
HRESULT Join (  
    [in] DWORD milliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="328b8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="328b8-105">Parameters</span></span>  
 `milliseconds`  
 <span data-ttu-id="328b8-106">podczas Interwał czasu (w milisekundach) oczekiwania na zakończenie zadania.</span><span class="sxs-lookup"><span data-stu-id="328b8-106">[in] The time interval, in milliseconds, to wait for the task to terminate.</span></span> <span data-ttu-id="328b8-107">Jeśli ten interwał upłynie przed zakończeniem zadania, odblokowuje zadanie wywołujące.</span><span class="sxs-lookup"><span data-stu-id="328b8-107">If this interval elapses before the task terminates, the calling task unblocks.</span></span>  
  
 `option`  
 <span data-ttu-id="328b8-108">podczas Jedna z wartości [WAIT_OPTION](wait-option-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="328b8-108">[in] One of the [WAIT_OPTION](wait-option-enumeration.md) values.</span></span> <span data-ttu-id="328b8-109">Wartość WAIT_ALERTABLE powoduje, że host wznowi zadanie, jeśli `Alert` jest wywoływana przed `milliseconds` upływem czasu.</span><span class="sxs-lookup"><span data-stu-id="328b8-109">A value of WAIT_ALERTABLE instructs the host to wake the task if `Alert` is called before `milliseconds` elapses.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="328b8-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="328b8-110">Return Value</span></span>  
  
|<span data-ttu-id="328b8-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="328b8-111">HRESULT</span></span>|<span data-ttu-id="328b8-112">Opis</span><span class="sxs-lookup"><span data-stu-id="328b8-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="328b8-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="328b8-113">S_OK</span></span>|<span data-ttu-id="328b8-114">`Join`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="328b8-114">`Join` returned successfully.</span></span>|  
|<span data-ttu-id="328b8-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="328b8-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="328b8-116">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="328b8-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="328b8-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="328b8-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="328b8-118">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="328b8-118">The call timed out.</span></span>|  
|<span data-ttu-id="328b8-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="328b8-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="328b8-120">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="328b8-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="328b8-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="328b8-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="328b8-122">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna albo bieżące `IHostTask` wystąpienie nie jest skojarzone z zadaniem.</span><span class="sxs-lookup"><span data-stu-id="328b8-122">An event was canceled while a blocked thread or fiber was waiting on it, or the current `IHostTask` instance is not associated with a task.</span></span>|  
|<span data-ttu-id="328b8-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="328b8-123">E_FAIL</span></span>|<span data-ttu-id="328b8-124">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="328b8-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="328b8-125">Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="328b8-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="328b8-126">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="328b8-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="328b8-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="328b8-127">Requirements</span></span>  
 <span data-ttu-id="328b8-128">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="328b8-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="328b8-129">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="328b8-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="328b8-130">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="328b8-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="328b8-131">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="328b8-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="328b8-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="328b8-132">See also</span></span>

- [<span data-ttu-id="328b8-133">ICLRTask — Interfejs</span><span class="sxs-lookup"><span data-stu-id="328b8-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="328b8-134">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="328b8-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="328b8-135">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="328b8-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="328b8-136">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="328b8-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="328b8-137">WAIT_OPTION — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="328b8-137">WAIT_OPTION Enumeration</span></span>](wait-option-enumeration.md)
