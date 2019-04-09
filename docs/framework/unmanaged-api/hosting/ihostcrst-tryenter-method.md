---
title: IHostCrst::TryEnter — Metoda
ms.date: 03/30/2017
api_name:
- IHostCrst.TryEnter
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst::TryEnter
helpviewer_keywords:
- IHostCrst::TryEnter method [.NET Framework hosting]
- TryEnter method [.NET Framework hosting]
ms.assetid: a922fa98-beab-4f09-a342-cc94fc65687f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 08e4c395026a743323b40e5b1ace3db64e368078
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59087267"
---
# <a name="ihostcrsttryenter-method"></a><span data-ttu-id="b065e-102">IHostCrst::TryEnter — Metoda</span><span class="sxs-lookup"><span data-stu-id="b065e-102">IHostCrst::TryEnter Method</span></span>
<span data-ttu-id="b065e-103">Próbuje wprowadzić sekcję krytyczną, reprezentowane przez bieżącą [ihostcrst —](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="b065e-103">Attempts to enter the critical section represented by the current [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b065e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b065e-104">Syntax</span></span>  
  
```  
HRESULT TryEnter (  
    [in]  DWORD  option,  
    [out] BOOL   *pbSucceeded  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b065e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b065e-105">Parameters</span></span>  
 `option`  
 <span data-ttu-id="b065e-106">[in] Jedną z [wait_option —](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) wartości, wskazując akcję host powinien wykonać, jeśli bloki operacji.</span><span class="sxs-lookup"><span data-stu-id="b065e-106">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values, indicating what action the host should take if the operation blocks.</span></span>  
  
 `pbSucceeded`  
 <span data-ttu-id="b065e-107">[out] `true` Jeśli sekcję krytyczną, można wprowadzić; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="b065e-107">[out] `true` if the critical section can be entered; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b065e-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b065e-108">Return Value</span></span>  
  
|<span data-ttu-id="b065e-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b065e-109">HRESULT</span></span>|<span data-ttu-id="b065e-110">Opis</span><span class="sxs-lookup"><span data-stu-id="b065e-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b065e-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="b065e-111">S_OK</span></span>|`TryEnter` <span data-ttu-id="b065e-112">pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="b065e-112">returned successfully.</span></span>|  
|<span data-ttu-id="b065e-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b065e-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b065e-114">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="b065e-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b065e-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b065e-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b065e-116">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="b065e-116">The call timed out.</span></span>|  
|<span data-ttu-id="b065e-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b065e-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b065e-118">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="b065e-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b065e-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b065e-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b065e-120">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="b065e-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b065e-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b065e-121">E_FAIL</span></span>|<span data-ttu-id="b065e-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="b065e-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b065e-123">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="b065e-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b065e-124">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b065e-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b065e-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b065e-125">Remarks</span></span>  
 `TryEnter` <span data-ttu-id="b065e-126">zwraca niezwłocznie i wskazuje, czy wątek wywołujący wprowadzony sekcję krytyczną.</span><span class="sxs-lookup"><span data-stu-id="b065e-126">returns immediately and indicates whether the calling thread entered the critical section.</span></span> <span data-ttu-id="b065e-127">Ta metoda odzwierciedla Wind32 `TryEnterCriticalSection` funkcji.</span><span class="sxs-lookup"><span data-stu-id="b065e-127">This method mirrors the Wind32 `TryEnterCriticalSection` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b065e-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b065e-128">Requirements</span></span>  
 <span data-ttu-id="b065e-129">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b065e-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b065e-130">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b065e-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b065e-131">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b065e-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="b065e-132">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="b065e-132">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b065e-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b065e-133">See also</span></span>

- [<span data-ttu-id="b065e-134">ICLRSyncManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="b065e-134">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="b065e-135">IHostCrst — Interfejs</span><span class="sxs-lookup"><span data-stu-id="b065e-135">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)
- [<span data-ttu-id="b065e-136">IHostSyncManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="b065e-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
