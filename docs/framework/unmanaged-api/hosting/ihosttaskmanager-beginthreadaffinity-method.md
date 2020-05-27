---
title: IHostTaskManager::BeginThreadAffinity — Metoda
ms.date: 03/30/2017
api_name:
- IHostTaskManager.BeginThreadAffinity
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::BeginThreadAffinity
helpviewer_keywords:
- IHostTaskManager::BeginThreadAffinity method [.NET Framework hosting]
- BeginThreadAffinity method [.NET Framework hosting]
ms.assetid: fea3ab88-ce41-4c5a-847b-bb78cd748da6
topic_type:
- apiref
ms.openlocfilehash: 90ae790603f0e41a20993ffef88654211a3168d9
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842364"
---
# <a name="ihosttaskmanagerbeginthreadaffinity-method"></a><span data-ttu-id="9cda6-102">IHostTaskManager::BeginThreadAffinity — Metoda</span><span class="sxs-lookup"><span data-stu-id="9cda6-102">IHostTaskManager::BeginThreadAffinity Method</span></span>
<span data-ttu-id="9cda6-103">Powiadamia hosta, że kod zarządzany wprowadza okres, w którym bieżące zadanie nie może zostać przeniesione do innego wątku systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="9cda6-103">Notifies the host that managed code is entering a period in which the current task must not be moved to another operating system thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9cda6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9cda6-104">Syntax</span></span>  
  
```cpp  
HRESULT BeginThreadAffinity ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="9cda6-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="9cda6-105">Return Value</span></span>  
  
|<span data-ttu-id="9cda6-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9cda6-106">HRESULT</span></span>|<span data-ttu-id="9cda6-107">Opis</span><span class="sxs-lookup"><span data-stu-id="9cda6-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9cda6-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="9cda6-108">S_OK</span></span>|<span data-ttu-id="9cda6-109">`BeginThreadAffinity`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="9cda6-109">`BeginThreadAffinity` returned successfully.</span></span>|  
|<span data-ttu-id="9cda6-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9cda6-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9cda6-111">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="9cda6-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9cda6-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9cda6-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9cda6-113">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="9cda6-113">The call timed out.</span></span>|  
|<span data-ttu-id="9cda6-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9cda6-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9cda6-115">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="9cda6-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9cda6-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9cda6-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9cda6-117">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="9cda6-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9cda6-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9cda6-118">E_FAIL</span></span>|<span data-ttu-id="9cda6-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="9cda6-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9cda6-120">Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="9cda6-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9cda6-121">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9cda6-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9cda6-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9cda6-122">Remarks</span></span>  
 <span data-ttu-id="9cda6-123">Środowisko CLR zwykle wywołuje `IHostTaskManager::BeginThreadAffinity` w kontekście wywołania do <xref:System.Threading.Thread.BeginThreadAffinity%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="9cda6-123">The CLR typically calls `IHostTaskManager::BeginThreadAffinity` in the context of a call to <xref:System.Threading.Thread.BeginThreadAffinity%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="9cda6-124">Nie można ponownie zaplanować bieżącego zadania, dopóki nie zostanie wykonane odpowiednie wywołanie do [IHostTaskManager:: EndThreadAffinity —](ihosttaskmanager-endthreadaffinity-method.md).</span><span class="sxs-lookup"><span data-stu-id="9cda6-124">The current task must not be rescheduled until a corresponding call is made to [IHostTaskManager::EndThreadAffinity](ihosttaskmanager-endthreadaffinity-method.md).</span></span> <span data-ttu-id="9cda6-125">Zadania mogą być przełączane, ale po ich przełączeniu do programu muszą być przypisane do tego samego wątku systemu operacyjnego, z którego zostały przełączone. Zagnieżdżone wywołania `BeginThreadAffinity` nie mają wpływu, ponieważ wywołanie odwołuje się do bieżącego zadania.</span><span class="sxs-lookup"><span data-stu-id="9cda6-125">Tasks can be switched out, but when they are switched back in, they must be assigned to the same operating system thread from which they were switched out. Nested calls to `BeginThreadAffinity` have no effect, because the call refers to the current task.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9cda6-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9cda6-126">Requirements</span></span>  
 <span data-ttu-id="9cda6-127">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9cda6-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9cda6-128">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9cda6-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9cda6-129">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9cda6-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9cda6-130">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9cda6-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cda6-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9cda6-131">See also</span></span>

- [<span data-ttu-id="9cda6-132">ICLRTask — Interfejs</span><span class="sxs-lookup"><span data-stu-id="9cda6-132">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="9cda6-133">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="9cda6-133">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="9cda6-134">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="9cda6-134">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="9cda6-135">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="9cda6-135">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
