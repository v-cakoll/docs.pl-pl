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
ms.openlocfilehash: 5c772f67b8ac09e2383aff335d9f164c2e048cbd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59145096"
---
# <a name="ihostcrstenter-method"></a><span data-ttu-id="a6681-102">IHostCrst::Enter — Metoda</span><span class="sxs-lookup"><span data-stu-id="a6681-102">IHostCrst::Enter Method</span></span>
<span data-ttu-id="a6681-103">Wprowadza sekcję krytyczną, która jest reprezentowana przez bieżącą [ihostcrst —](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="a6681-103">Enters the critical section that is represented by the current [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6681-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a6681-104">Syntax</span></span>  
  
```  
HRESULT Enter (  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a6681-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a6681-105">Parameters</span></span>  
 `option`  
 <span data-ttu-id="a6681-106">[in] Jedną z [wait_option —](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) wartości, wskazując akcję host powinien wykonać, jeśli bloki operacji.</span><span class="sxs-lookup"><span data-stu-id="a6681-106">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values, indicating what action the host should take if the operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a6681-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a6681-107">Return Value</span></span>  
  
|<span data-ttu-id="a6681-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a6681-108">HRESULT</span></span>|<span data-ttu-id="a6681-109">Opis</span><span class="sxs-lookup"><span data-stu-id="a6681-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a6681-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="a6681-110">S_OK</span></span>|<span data-ttu-id="a6681-111">`Enter` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="a6681-111">`Enter` returned successfully.</span></span>|  
|<span data-ttu-id="a6681-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a6681-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a6681-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="a6681-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a6681-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a6681-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a6681-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="a6681-115">The call timed out.</span></span>|  
|<span data-ttu-id="a6681-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a6681-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a6681-117">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="a6681-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a6681-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a6681-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a6681-119">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="a6681-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a6681-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a6681-120">E_FAIL</span></span>|<span data-ttu-id="a6681-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="a6681-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a6681-122">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="a6681-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a6681-123">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a6681-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a6681-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a6681-124">Remarks</span></span>  
 <span data-ttu-id="a6681-125">`Enter` odzwierciedla Win32 `EnterCriticalSection` funkcji.</span><span class="sxs-lookup"><span data-stu-id="a6681-125">`Enter` mirrors the Win32 `EnterCriticalSection` function.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a6681-126">Ta metoda nie zwraca dopóki nie zostanie wprowadzona sekcję krytyczną.</span><span class="sxs-lookup"><span data-stu-id="a6681-126">This method does not return until the critical section is entered.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6681-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a6681-127">Requirements</span></span>  
 <span data-ttu-id="a6681-128">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6681-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6681-129">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a6681-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a6681-130">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a6681-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a6681-131">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6681-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6681-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a6681-132">See also</span></span>

- [<span data-ttu-id="a6681-133">ICLRSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="a6681-133">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="a6681-134">IHostCrst, interfejs</span><span class="sxs-lookup"><span data-stu-id="a6681-134">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)
- [<span data-ttu-id="a6681-135">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="a6681-135">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
