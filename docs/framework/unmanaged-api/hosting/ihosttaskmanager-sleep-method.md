---
title: IHostTaskManager::Sleep — Metoda
ms.date: 03/30/2017
api_name:
- IHostTaskManager.Sleep
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::Sleep
helpviewer_keywords:
- IHostTaskManager::Sleep method [.NET Framework hosting]
- Sleep method, IHostTaskManager interface [.NET Framework hosting]
ms.assetid: f67d25f3-9199-4c5f-b1e8-1c819243cfd5
topic_type:
- apiref
ms.openlocfilehash: bb12547155383bb410f592018232ca6f688bab8a
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/26/2020
ms.locfileid: "83841909"
---
# <a name="ihosttaskmanagersleep-method"></a><span data-ttu-id="586c0-102">IHostTaskManager::Sleep — Metoda</span><span class="sxs-lookup"><span data-stu-id="586c0-102">IHostTaskManager::Sleep Method</span></span>
<span data-ttu-id="586c0-103">Powiadamia hosta, że bieżące zadanie przechodzi w stan uśpienia.</span><span class="sxs-lookup"><span data-stu-id="586c0-103">Notifies the host that the current task is going to sleep.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="586c0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="586c0-104">Syntax</span></span>  
  
```cpp  
HRESULT Sleep (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="586c0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="586c0-105">Parameters</span></span>  
 `dwMilliseconds`  
 <span data-ttu-id="586c0-106">podczas Przedział czasu (w milisekundach), przez który wątek będzie uśpiony.</span><span class="sxs-lookup"><span data-stu-id="586c0-106">[in] The time interval, in milliseconds, that the thread will sleep.</span></span>  
  
 `option`  
 <span data-ttu-id="586c0-107">podczas Jedna z wartości wyliczenia [WAIT_OPTION](wait-option-enumeration.md) wskazująca, jaka akcja powinna być wykonywana przez hosta, jeśli ta akcja jest blokowana.</span><span class="sxs-lookup"><span data-stu-id="586c0-107">[in] One of the [WAIT_OPTION](wait-option-enumeration.md) enumeration values, indicating what action the host should take if this action blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="586c0-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="586c0-108">Return Value</span></span>  
  
|<span data-ttu-id="586c0-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="586c0-109">HRESULT</span></span>|<span data-ttu-id="586c0-110">Opis</span><span class="sxs-lookup"><span data-stu-id="586c0-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="586c0-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="586c0-111">S_OK</span></span>|<span data-ttu-id="586c0-112">`Sleep`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="586c0-112">`Sleep` returned successfully.</span></span>|  
|<span data-ttu-id="586c0-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="586c0-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="586c0-114">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="586c0-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="586c0-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="586c0-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="586c0-116">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="586c0-116">The call timed out.</span></span>|  
|<span data-ttu-id="586c0-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="586c0-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="586c0-118">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="586c0-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="586c0-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="586c0-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="586c0-120">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="586c0-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="586c0-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="586c0-121">E_FAIL</span></span>|<span data-ttu-id="586c0-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="586c0-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="586c0-123">Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="586c0-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="586c0-124">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="586c0-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="586c0-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="586c0-125">Remarks</span></span>  
 <span data-ttu-id="586c0-126">Środowisko CLR zwykle wywołuje `IHostTaskManager::Sleep` metodę, gdy <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> jest wywoływana z kodu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="586c0-126">The CLR typically calls `IHostTaskManager::Sleep` when <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> is called from user code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="586c0-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="586c0-127">Requirements</span></span>  
 <span data-ttu-id="586c0-128">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="586c0-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="586c0-129">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="586c0-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="586c0-130">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="586c0-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="586c0-131">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="586c0-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="586c0-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="586c0-132">See also</span></span>

- [<span data-ttu-id="586c0-133">ICLRTask — Interfejs</span><span class="sxs-lookup"><span data-stu-id="586c0-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="586c0-134">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="586c0-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="586c0-135">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="586c0-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="586c0-136">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="586c0-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
