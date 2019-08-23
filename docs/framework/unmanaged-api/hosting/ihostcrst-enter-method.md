---
title: IHostCrst::Enter — Metoda
ms.date: 03/30/2017
api_name:
- IHostCrst.Enter
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst::Enter
helpviewer_keywords:
- Enter method [.NET Framework hosting]
- IHostCrst::Enter method [.NET Framework hosting]
ms.assetid: 100dd7eb-7053-4295-9bb3-32ba47f6ec79
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bdc597e741023af1c7cc1f48e378083157dd4a5d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937741"
---
# <a name="ihostcrstenter-method"></a><span data-ttu-id="5ff48-102">IHostCrst::Enter — Metoda</span><span class="sxs-lookup"><span data-stu-id="5ff48-102">IHostCrst::Enter Method</span></span>
<span data-ttu-id="5ff48-103">Wprowadza sekcję krytyczną, która jest reprezentowana przez bieżące wystąpienie [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="5ff48-103">Enters the critical section that is represented by the current [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ff48-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5ff48-104">Syntax</span></span>  
  
```cpp  
HRESULT Enter (  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5ff48-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5ff48-105">Parameters</span></span>  
 `option`  
 <span data-ttu-id="5ff48-106">podczas Jedna z wartości [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) , wskazująca, jaka akcja powinna być wykonywana przez hosta, jeśli operacja jest blokowana.</span><span class="sxs-lookup"><span data-stu-id="5ff48-106">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values, indicating what action the host should take if the operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5ff48-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="5ff48-107">Return Value</span></span>  
  
|<span data-ttu-id="5ff48-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5ff48-108">HRESULT</span></span>|<span data-ttu-id="5ff48-109">Opis</span><span class="sxs-lookup"><span data-stu-id="5ff48-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5ff48-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="5ff48-110">S_OK</span></span>|<span data-ttu-id="5ff48-111">`Enter`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="5ff48-111">`Enter` returned successfully.</span></span>|  
|<span data-ttu-id="5ff48-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5ff48-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5ff48-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="5ff48-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5ff48-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5ff48-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5ff48-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="5ff48-115">The call timed out.</span></span>|  
|<span data-ttu-id="5ff48-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5ff48-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5ff48-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="5ff48-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5ff48-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5ff48-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5ff48-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="5ff48-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5ff48-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5ff48-120">E_FAIL</span></span>|<span data-ttu-id="5ff48-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="5ff48-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5ff48-122">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="5ff48-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5ff48-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="5ff48-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5ff48-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5ff48-124">Remarks</span></span>  
 <span data-ttu-id="5ff48-125">`Enter`odzwierciedla funkcję Win32 `EnterCriticalSection` .</span><span class="sxs-lookup"><span data-stu-id="5ff48-125">`Enter` mirrors the Win32 `EnterCriticalSection` function.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5ff48-126">Ta metoda nie jest zwracana do momentu wprowadzenia sekcji krytycznej.</span><span class="sxs-lookup"><span data-stu-id="5ff48-126">This method does not return until the critical section is entered.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ff48-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5ff48-127">Requirements</span></span>  
 <span data-ttu-id="5ff48-128">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ff48-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ff48-129">**Nagłówki** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="5ff48-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5ff48-130">**Biblioteki** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="5ff48-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5ff48-131">**.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ff48-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ff48-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5ff48-132">See also</span></span>

- [<span data-ttu-id="5ff48-133">ICLRSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="5ff48-133">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="5ff48-134">IHostCrst, interfejs</span><span class="sxs-lookup"><span data-stu-id="5ff48-134">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)
- [<span data-ttu-id="5ff48-135">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="5ff48-135">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
