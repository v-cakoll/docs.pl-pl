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
ms.openlocfilehash: 3a54135a0daff3f207d1365d2c27335440f7f1fb
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67763779"
---
# <a name="ihostcrstenter-method"></a><span data-ttu-id="e9f56-102">IHostCrst::Enter — Metoda</span><span class="sxs-lookup"><span data-stu-id="e9f56-102">IHostCrst::Enter Method</span></span>
<span data-ttu-id="e9f56-103">Wprowadza sekcję krytyczną, która jest reprezentowana przez bieżącą [ihostcrst —](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="e9f56-103">Enters the critical section that is represented by the current [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9f56-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e9f56-104">Syntax</span></span>  
  
```cpp  
HRESULT Enter (  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e9f56-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9f56-105">Parameters</span></span>  
 `option`  
 <span data-ttu-id="e9f56-106">[in] Jedną z [wait_option —](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) wartości, wskazując akcję host powinien wykonać, jeśli bloki operacji.</span><span class="sxs-lookup"><span data-stu-id="e9f56-106">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values, indicating what action the host should take if the operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e9f56-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e9f56-107">Return Value</span></span>  
  
|<span data-ttu-id="e9f56-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e9f56-108">HRESULT</span></span>|<span data-ttu-id="e9f56-109">Opis</span><span class="sxs-lookup"><span data-stu-id="e9f56-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e9f56-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="e9f56-110">S_OK</span></span>|<span data-ttu-id="e9f56-111">`Enter` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="e9f56-111">`Enter` returned successfully.</span></span>|  
|<span data-ttu-id="e9f56-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e9f56-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e9f56-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="e9f56-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e9f56-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e9f56-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e9f56-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="e9f56-115">The call timed out.</span></span>|  
|<span data-ttu-id="e9f56-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e9f56-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e9f56-117">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="e9f56-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e9f56-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e9f56-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e9f56-119">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="e9f56-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e9f56-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e9f56-120">E_FAIL</span></span>|<span data-ttu-id="e9f56-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="e9f56-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e9f56-122">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="e9f56-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e9f56-123">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e9f56-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e9f56-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e9f56-124">Remarks</span></span>  
 <span data-ttu-id="e9f56-125">`Enter` odzwierciedla Win32 `EnterCriticalSection` funkcji.</span><span class="sxs-lookup"><span data-stu-id="e9f56-125">`Enter` mirrors the Win32 `EnterCriticalSection` function.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e9f56-126">Ta metoda nie zwraca dopóki nie zostanie wprowadzona sekcję krytyczną.</span><span class="sxs-lookup"><span data-stu-id="e9f56-126">This method does not return until the critical section is entered.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9f56-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e9f56-127">Requirements</span></span>  
 <span data-ttu-id="e9f56-128">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9f56-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9f56-129">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e9f56-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e9f56-130">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e9f56-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e9f56-131">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9f56-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9f56-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e9f56-132">See also</span></span>

- [<span data-ttu-id="e9f56-133">ICLRSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="e9f56-133">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="e9f56-134">IHostCrst, interfejs</span><span class="sxs-lookup"><span data-stu-id="e9f56-134">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)
- [<span data-ttu-id="e9f56-135">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="e9f56-135">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
