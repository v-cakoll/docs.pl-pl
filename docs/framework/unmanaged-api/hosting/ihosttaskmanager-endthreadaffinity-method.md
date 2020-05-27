---
title: IHostTaskManager::EndThreadAffinity — Metoda
ms.date: 03/30/2017
api_name:
- IHostTaskManager.EndThreadAffinity
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::EndThreadAffinity
helpviewer_keywords:
- EndThreadAffinity method [.NET Framework hosting]
- IHostTaskManager::EndThreadAffinity method [.NET Framework hosting]
ms.assetid: 7738a904-0cd7-4fde-a3eb-2323a5533157
topic_type:
- apiref
ms.openlocfilehash: 2e857f951a837e1385d02dfc810fc12cfefd0d2b
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/26/2020
ms.locfileid: "83841961"
---
# <a name="ihosttaskmanagerendthreadaffinity-method"></a><span data-ttu-id="1c2d5-102">IHostTaskManager::EndThreadAffinity — Metoda</span><span class="sxs-lookup"><span data-stu-id="1c2d5-102">IHostTaskManager::EndThreadAffinity Method</span></span>
<span data-ttu-id="1c2d5-103">Powiadamia hosta, że kod zarządzany kończy okres, w którym bieżące zadanie nie może zostać przeniesione do innego wątku systemu operacyjnego, po wcześniejszym wywołaniu [IHostTaskManager:: BeginThreadAffinity —](ihosttaskmanager-beginthreadaffinity-method.md).</span><span class="sxs-lookup"><span data-stu-id="1c2d5-103">Notifies the host that managed code is exiting the period in which the current task must not be moved to another operating system thread, following an earlier call to [IHostTaskManager::BeginThreadAffinity](ihosttaskmanager-beginthreadaffinity-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c2d5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1c2d5-104">Syntax</span></span>  
  
```cpp  
HRESULT EndThreadAffinity ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="1c2d5-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1c2d5-105">Return Value</span></span>  
  
|<span data-ttu-id="1c2d5-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1c2d5-106">HRESULT</span></span>|<span data-ttu-id="1c2d5-107">Opis</span><span class="sxs-lookup"><span data-stu-id="1c2d5-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1c2d5-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="1c2d5-108">S_OK</span></span>|<span data-ttu-id="1c2d5-109">`EndThreadAffinity`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="1c2d5-109">`EndThreadAffinity` returned successfully.</span></span>|  
|<span data-ttu-id="1c2d5-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1c2d5-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1c2d5-111">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="1c2d5-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1c2d5-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1c2d5-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1c2d5-113">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="1c2d5-113">The call timed out.</span></span>|  
|<span data-ttu-id="1c2d5-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1c2d5-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1c2d5-115">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="1c2d5-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1c2d5-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1c2d5-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1c2d5-117">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="1c2d5-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1c2d5-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1c2d5-118">E_FAIL</span></span>|<span data-ttu-id="1c2d5-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="1c2d5-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1c2d5-120">Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="1c2d5-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1c2d5-121">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="1c2d5-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="1c2d5-122">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="1c2d5-122">E_UNEXPECTED</span></span>|<span data-ttu-id="1c2d5-123">`EndThreadAffinity`został wywołany bez wcześniejszego wywołania do `BeginThreadAffinity` .</span><span class="sxs-lookup"><span data-stu-id="1c2d5-123">`EndThreadAffinity` was called without an earlier corresponding call to `BeginThreadAffinity`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1c2d5-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1c2d5-124">Remarks</span></span>  
 <span data-ttu-id="1c2d5-125">Środowisko CLR wykonuje odpowiednie wywołanie do `BeginThreadAffinity` bieżącego zadania przed wywołaniem `EndThreadAffinity` .</span><span class="sxs-lookup"><span data-stu-id="1c2d5-125">The CLR makes a corresponding call to `BeginThreadAffinity` on the current task before calling `EndThreadAffinity`.</span></span> <span data-ttu-id="1c2d5-126">W przypadku braku takiego wywołania implementacja hosta [IHostTaskManager](ihosttaskmanager-interface.md) powinna zwracać E_UNEXPECTED i nie podejmować żadnych działań.</span><span class="sxs-lookup"><span data-stu-id="1c2d5-126">In the absence of such a corresponding call, the host's implementation of [IHostTaskManager](ihosttaskmanager-interface.md) should return E_UNEXPECTED, and take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c2d5-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1c2d5-127">Requirements</span></span>  
 <span data-ttu-id="1c2d5-128">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c2d5-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c2d5-129">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="1c2d5-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1c2d5-130">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="1c2d5-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1c2d5-131">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c2d5-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c2d5-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1c2d5-132">See also</span></span>

- <xref:System.Threading>
- [<span data-ttu-id="1c2d5-133">ICLRTask — Interfejs</span><span class="sxs-lookup"><span data-stu-id="1c2d5-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="1c2d5-134">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="1c2d5-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="1c2d5-135">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="1c2d5-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="1c2d5-136">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="1c2d5-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
