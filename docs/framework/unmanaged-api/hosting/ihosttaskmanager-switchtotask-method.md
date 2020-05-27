---
title: IHostTaskManager::SwitchToTask — Metoda
ms.date: 03/30/2017
api_name:
- IHostTaskManager.SwitchToTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::SwitchToTask
helpviewer_keywords:
- IHostTaskManager::SwitchToTask method [.NET Framework hosting]
- SwitchToTask method [.NET Framework hosting]
ms.assetid: 35d0c27e-4b14-49ce-810d-7ab2120177e8
topic_type:
- apiref
ms.openlocfilehash: 7d1511924fc70c42252881a46f8aebb437a3f4f7
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/26/2020
ms.locfileid: "83841948"
---
# <a name="ihosttaskmanagerswitchtotask-method"></a><span data-ttu-id="a9dcd-102">IHostTaskManager::SwitchToTask — Metoda</span><span class="sxs-lookup"><span data-stu-id="a9dcd-102">IHostTaskManager::SwitchToTask Method</span></span>
<span data-ttu-id="a9dcd-103">Powiadamia hosta o konieczności przełączenia bieżącego zadania.</span><span class="sxs-lookup"><span data-stu-id="a9dcd-103">Notifies the host that it should switch out the current task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9dcd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a9dcd-104">Syntax</span></span>  
  
```cpp  
HRESULT SwitchToTask (  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a9dcd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a9dcd-105">Parameters</span></span>  
 `option`  
 <span data-ttu-id="a9dcd-106">podczas Jedna z wartości wyliczenia [WAIT_OPTION](wait-option-enumeration.md) wskazująca akcję, którą powinien wykonać host, jeśli żądane bloki operacji.</span><span class="sxs-lookup"><span data-stu-id="a9dcd-106">[in] One of the [WAIT_OPTION](wait-option-enumeration.md) enumeration values, indicating the action the host should take if the requested operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a9dcd-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a9dcd-107">Return Value</span></span>  
  
|<span data-ttu-id="a9dcd-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a9dcd-108">HRESULT</span></span>|<span data-ttu-id="a9dcd-109">Opis</span><span class="sxs-lookup"><span data-stu-id="a9dcd-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a9dcd-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="a9dcd-110">S_OK</span></span>|<span data-ttu-id="a9dcd-111">`SwitchToTask`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="a9dcd-111">`SwitchToTask` returned successfully.</span></span>|  
|<span data-ttu-id="a9dcd-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a9dcd-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a9dcd-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="a9dcd-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a9dcd-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a9dcd-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a9dcd-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="a9dcd-115">The call timed out.</span></span>|  
|<span data-ttu-id="a9dcd-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a9dcd-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a9dcd-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="a9dcd-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a9dcd-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a9dcd-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a9dcd-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="a9dcd-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a9dcd-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a9dcd-120">E_FAIL</span></span>|<span data-ttu-id="a9dcd-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="a9dcd-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a9dcd-122">Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="a9dcd-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a9dcd-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a9dcd-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a9dcd-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a9dcd-124">Remarks</span></span>  
 <span data-ttu-id="a9dcd-125">Host może przełączać się w innym zadaniu odpowiednio do potrzeb lub w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="a9dcd-125">The host can switch in another task as desired or needed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a9dcd-126">`SwitchToTask`nie określa, które zadanie powinno zostać przełączone do hosta; określa tylko zadanie, z którego ma zostać przełączone.</span><span class="sxs-lookup"><span data-stu-id="a9dcd-126">`SwitchToTask` does not specify which task the host should switch to; it specifies only the task that it should switch from.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9dcd-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a9dcd-127">Requirements</span></span>  
 <span data-ttu-id="a9dcd-128">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9dcd-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9dcd-129">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a9dcd-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a9dcd-130">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a9dcd-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a9dcd-131">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9dcd-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9dcd-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a9dcd-132">See also</span></span>

- [<span data-ttu-id="a9dcd-133">ICLRTask — Interfejs</span><span class="sxs-lookup"><span data-stu-id="a9dcd-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="a9dcd-134">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="a9dcd-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="a9dcd-135">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="a9dcd-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="a9dcd-136">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="a9dcd-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
