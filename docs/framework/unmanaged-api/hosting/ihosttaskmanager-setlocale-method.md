---
title: IHostTaskManager::SetLocale — Metoda
ms.date: 03/30/2017
api_name:
- IHostTaskManager.SetLocale
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::SetLocale
helpviewer_keywords:
- SetLocale method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::SetLocale method [.NET Framework hosting]
ms.assetid: 747ee407-ee8c-484d-9583-25089236d2d1
topic_type:
- apiref
ms.openlocfilehash: 841827017262b731fd5e6f6bd0b5862fecaf2744
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/26/2020
ms.locfileid: "83841727"
---
# <a name="ihosttaskmanagersetlocale-method"></a><span data-ttu-id="49d88-102">IHostTaskManager::SetLocale — Metoda</span><span class="sxs-lookup"><span data-stu-id="49d88-102">IHostTaskManager::SetLocale Method</span></span>
<span data-ttu-id="49d88-103">Powiadamia hosta, że środowisko uruchomieniowe języka wspólnego (CLR) zmieniło ustawienia regionalne lub kulturę, w aktualnie wykonywanym zadaniu.</span><span class="sxs-lookup"><span data-stu-id="49d88-103">Notifies the host that the common language runtime (CLR) has changed the locale, or culture, on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49d88-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="49d88-104">Syntax</span></span>  
  
```cpp  
HRESULT SetLocale (  
    [in] LCID lcid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="49d88-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="49d88-105">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="49d88-106">podczas Wartość identyfikatora ustawień regionalnych, która jest mapowana na nowo przypisaną kulturę geograficzną i język.</span><span class="sxs-lookup"><span data-stu-id="49d88-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="49d88-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="49d88-107">Return Value</span></span>  
  
|<span data-ttu-id="49d88-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="49d88-108">HRESULT</span></span>|<span data-ttu-id="49d88-109">Opis</span><span class="sxs-lookup"><span data-stu-id="49d88-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="49d88-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="49d88-110">S_OK</span></span>|<span data-ttu-id="49d88-111">`SetLocale`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="49d88-111">`SetLocale` returned successfully.</span></span>|  
|<span data-ttu-id="49d88-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="49d88-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="49d88-113">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="49d88-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="49d88-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="49d88-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="49d88-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="49d88-115">The call timed out.</span></span>|  
|<span data-ttu-id="49d88-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="49d88-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="49d88-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="49d88-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="49d88-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="49d88-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="49d88-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="49d88-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="49d88-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="49d88-120">E_FAIL</span></span>|<span data-ttu-id="49d88-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="49d88-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="49d88-122">Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="49d88-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="49d88-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="49d88-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="49d88-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="49d88-124">E_NOTIMPL</span></span>|<span data-ttu-id="49d88-125">Host nie zezwala na modyfikowanie ustawień regionalnych przez zarządzany kod użytkownika.</span><span class="sxs-lookup"><span data-stu-id="49d88-125">The host does not allow managed user code to modify the locale.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="49d88-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="49d88-126">Remarks</span></span>  
 <span data-ttu-id="49d88-127">Wywołania środowiska uruchomieniowego, `SetLocale` gdy wartość <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> właściwości jest zmieniana przez kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="49d88-127">The runtime calls `SetLocale` when the value of the <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> property is changed by managed code.</span></span> <span data-ttu-id="49d88-128">Ta metoda zapewnia dla hosta możliwość wykonywania wszelkich mechanizmów, które mogą mieć na celu synchronizację ustawień regionalnych.</span><span class="sxs-lookup"><span data-stu-id="49d88-128">This method provides an opportunity for the host to execute any mechanisms it might have for synchronization of locales.</span></span> <span data-ttu-id="49d88-129">Jeśli host nie zezwala na zmianę ustawień regionalnych z kodu zarządzanego lub nie implementuje mechanizmu synchronizacji ustawień lokalnych, powinien zwrócić E_NOTIMPL z tej metody.</span><span class="sxs-lookup"><span data-stu-id="49d88-129">If a host does not allow the locale to be changed from managed code, or does not implement a mechanism to synchronize locales, it should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49d88-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="49d88-130">Requirements</span></span>  
 <span data-ttu-id="49d88-131">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="49d88-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49d88-132">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="49d88-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="49d88-133">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="49d88-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="49d88-134">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49d88-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49d88-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="49d88-135">See also</span></span>

- [<span data-ttu-id="49d88-136">ICLRTask — Interfejs</span><span class="sxs-lookup"><span data-stu-id="49d88-136">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="49d88-137">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="49d88-137">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="49d88-138">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="49d88-138">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="49d88-139">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="49d88-139">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="49d88-140">SetUILocale, metoda</span><span class="sxs-lookup"><span data-stu-id="49d88-140">SetUILocale Method</span></span>](ihosttaskmanager-setuilocale-method.md)
