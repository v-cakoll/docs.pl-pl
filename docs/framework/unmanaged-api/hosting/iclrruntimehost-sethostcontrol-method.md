---
title: ICLRRuntimeHost::SetHostControl — Metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.SetHostControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::SetHostControl
helpviewer_keywords:
- SetHostControl method [.NET Framework hosting]
- ICLRRuntimeHost::SetHostControl method [.NET Framework hosting]
ms.assetid: 6136be87-e631-4756-81ed-74b66581bad4
topic_type:
- apiref
ms.openlocfilehash: 68b06a2840de277bdaed1dc9ce0b51e6b363c897
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120449"
---
# <a name="iclrruntimehostsethostcontrol-method"></a><span data-ttu-id="4a436-102">ICLRRuntimeHost::SetHostControl — Metoda</span><span class="sxs-lookup"><span data-stu-id="4a436-102">ICLRRuntimeHost::SetHostControl Method</span></span>
<span data-ttu-id="4a436-103">Ustawia wskaźnik interfejsu, który może być używany przez środowisko uruchomieniowe języka wspólnego (CLR), aby uzyskać implementację [interfejsu IHostControl](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md).</span><span class="sxs-lookup"><span data-stu-id="4a436-103">Sets the interface pointer that the common language runtime (CLR) can use to get the host's implementation of [IHostControl Interface](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a436-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4a436-104">Syntax</span></span>  
  
```cpp  
HRESULT SetHostControl(  
    [in] IHostControl* pHostControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4a436-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4a436-105">Parameters</span></span>  
 `pHostControl`  
 <span data-ttu-id="4a436-106">podczas Wskaźnik interfejsu do implementacji [interfejsu IHostControl](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)hosta.</span><span class="sxs-lookup"><span data-stu-id="4a436-106">[in] An interface pointer to the host's implementation of [IHostControl Interface](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4a436-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4a436-107">Return Value</span></span>  
  
|<span data-ttu-id="4a436-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4a436-108">HRESULT</span></span>|<span data-ttu-id="4a436-109">Opis</span><span class="sxs-lookup"><span data-stu-id="4a436-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4a436-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="4a436-110">S_OK</span></span>|<span data-ttu-id="4a436-111">`SetHostControl` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="4a436-111">`SetHostControl` returned successfully.</span></span>|  
|<span data-ttu-id="4a436-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4a436-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4a436-113">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="4a436-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4a436-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4a436-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4a436-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="4a436-115">The call timed out.</span></span>|  
|<span data-ttu-id="4a436-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4a436-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4a436-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="4a436-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4a436-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4a436-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4a436-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="4a436-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4a436-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4a436-120">E_FAIL</span></span>|<span data-ttu-id="4a436-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="4a436-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4a436-122">Jeśli metoda zwraca wartość E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="4a436-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4a436-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="4a436-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="4a436-124">E_CLR_ALREADY_STARTED</span><span class="sxs-lookup"><span data-stu-id="4a436-124">E_CLR_ALREADY_STARTED</span></span>|<span data-ttu-id="4a436-125">Środowisko CLR zostało już zainicjowane.</span><span class="sxs-lookup"><span data-stu-id="4a436-125">The CLR has already been initialized.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4a436-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4a436-126">Remarks</span></span>  
 <span data-ttu-id="4a436-127">Musisz wywołać `SetHostControl` przed zainicjowaniem środowiska CLR, czyli przed wywołaniem [metody Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) lub użyciem dowolnego [interfejsu metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="4a436-127">You must call `SetHostControl` before the CLR is initialized, that is, before you call [Start Method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) or use any of the [Metadata Interfaces](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span></span> <span data-ttu-id="4a436-128">Zaleca się wywołanie `SetHostControl` natychmiast po wywołaniu [funkcji CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md) lub [funkcji CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md).</span><span class="sxs-lookup"><span data-stu-id="4a436-128">It is recommended that you call `SetHostControl` immediately after calling [CorBindToCurrentRuntime Function](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md) or [CorBindToRuntimeEx Function](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a436-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4a436-129">Requirements</span></span>  
 <span data-ttu-id="4a436-130">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a436-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a436-131">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="4a436-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4a436-132">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4a436-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4a436-133">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a436-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a436-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4a436-134">See also</span></span>

- [<span data-ttu-id="4a436-135">ICLRRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="4a436-135">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
- [<span data-ttu-id="4a436-136">IHostControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="4a436-136">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
