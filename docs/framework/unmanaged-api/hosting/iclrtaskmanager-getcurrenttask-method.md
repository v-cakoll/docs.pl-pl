---
title: ICLRTaskManager::GetCurrentTask — Metoda
ms.date: 03/30/2017
api_name:
- ICLRTaskManager.GetCurrentTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::GetCurrentTask
helpviewer_keywords:
- GetCurrentTask method, ICLRTaskManager interface [.NET Framework hosting]
- ICLRTaskManager::GetCurrentTask method [.NET Framework hosting]
ms.assetid: c0b82a9f-edc6-4878-9c81-48de53c02142
topic_type:
- apiref
ms.openlocfilehash: 9cb97d9f383b7b54b431457042c4c4a7fc9cd876
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762836"
---
# <a name="iclrtaskmanagergetcurrenttask-method"></a><span data-ttu-id="5bc07-102">ICLRTaskManager::GetCurrentTask — Metoda</span><span class="sxs-lookup"><span data-stu-id="5bc07-102">ICLRTaskManager::GetCurrentTask Method</span></span>
<span data-ttu-id="5bc07-103">Pobiera wystąpienie [ICLRTask](iclrtask-interface.md) , które jest aktualnie uruchomione w wątku systemu operacyjnego, z którego pochodzi wywołanie metody.</span><span class="sxs-lookup"><span data-stu-id="5bc07-103">Gets the [ICLRTask](iclrtask-interface.md) instance that is currently running on the operating system thread from which the method call originated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5bc07-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5bc07-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentTask (  
    [out] ICLRTask **ppTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5bc07-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5bc07-105">Parameters</span></span>  
 `ppTask`  
 <span data-ttu-id="5bc07-106">określoną Wskaźnik do adresu `ICLRTask` wystąpienia, które jest aktualnie wykonywane w wątku systemu operacyjnego, z którego pochodzi wywołanie lub wartość null, jeśli żadne zadanie nie jest aktualnie wykonywane w tym wątku.</span><span class="sxs-lookup"><span data-stu-id="5bc07-106">[out] A pointer to the address of an `ICLRTask` instance that is currently executing on the operating system thread from which the call originated, or null if no task is currently executing on this thread.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5bc07-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="5bc07-107">Return Value</span></span>  
  
|<span data-ttu-id="5bc07-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5bc07-108">HRESULT</span></span>|<span data-ttu-id="5bc07-109">Opis</span><span class="sxs-lookup"><span data-stu-id="5bc07-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5bc07-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="5bc07-110">S_OK</span></span>|<span data-ttu-id="5bc07-111">Metoda została pomyślnie zwrócona.</span><span class="sxs-lookup"><span data-stu-id="5bc07-111">The method returned successfully.</span></span>|  
|<span data-ttu-id="5bc07-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5bc07-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5bc07-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="5bc07-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5bc07-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5bc07-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5bc07-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="5bc07-115">The call timed out.</span></span>|  
|<span data-ttu-id="5bc07-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5bc07-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5bc07-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="5bc07-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5bc07-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5bc07-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5bc07-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="5bc07-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5bc07-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5bc07-120">E_FAIL</span></span>|<span data-ttu-id="5bc07-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="5bc07-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5bc07-122">Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="5bc07-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5bc07-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="5bc07-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5bc07-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5bc07-124">Remarks</span></span>  
 <span data-ttu-id="5bc07-125">`ICLRTask`Wystąpienie, które `ppTask` wskazuje parametr, aby reprezentować aktualnie wykonywane zadanie dla środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="5bc07-125">The `ICLRTask` instance that the `ppTask` parameter points to represents the currently executing task for the CLR.</span></span> <span data-ttu-id="5bc07-126">`ICLRTask`Wystąpienie jest skojarzone z odpowiednim wystąpieniem [IHostTask](ihosttask-interface.md) , które reprezentuje zadanie dla hosta.</span><span class="sxs-lookup"><span data-stu-id="5bc07-126">The `ICLRTask` instance is associated with a corresponding [IHostTask](ihosttask-interface.md) instance that represents the task for the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5bc07-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5bc07-127">Requirements</span></span>  
 <span data-ttu-id="5bc07-128">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5bc07-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5bc07-129">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="5bc07-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5bc07-130">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="5bc07-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5bc07-131">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5bc07-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bc07-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5bc07-132">See also</span></span>

- [<span data-ttu-id="5bc07-133">ICLRTask — Interfejs</span><span class="sxs-lookup"><span data-stu-id="5bc07-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="5bc07-134">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="5bc07-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="5bc07-135">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="5bc07-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="5bc07-136">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="5bc07-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
