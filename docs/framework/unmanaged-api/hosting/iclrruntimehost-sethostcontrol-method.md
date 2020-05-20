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
ms.openlocfilehash: 8d6a4e1ca934c748352b0c4f5120536a4dd24e0b
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703960"
---
# <a name="iclrruntimehostsethostcontrol-method"></a><span data-ttu-id="935db-102">ICLRRuntimeHost::SetHostControl — Metoda</span><span class="sxs-lookup"><span data-stu-id="935db-102">ICLRRuntimeHost::SetHostControl Method</span></span>
<span data-ttu-id="935db-103">Ustawia wskaźnik interfejsu, który może być używany przez środowisko uruchomieniowe języka wspólnego (CLR), aby uzyskać implementację [interfejsu IHostControl](ihostcontrol-interface.md).</span><span class="sxs-lookup"><span data-stu-id="935db-103">Sets the interface pointer that the common language runtime (CLR) can use to get the host's implementation of [IHostControl Interface](ihostcontrol-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="935db-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="935db-104">Syntax</span></span>  
  
```cpp  
HRESULT SetHostControl(  
    [in] IHostControl* pHostControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="935db-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="935db-105">Parameters</span></span>  
 `pHostControl`  
 <span data-ttu-id="935db-106">podczas Wskaźnik interfejsu do implementacji [interfejsu IHostControl](ihostcontrol-interface.md)hosta.</span><span class="sxs-lookup"><span data-stu-id="935db-106">[in] An interface pointer to the host's implementation of [IHostControl Interface](ihostcontrol-interface.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="935db-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="935db-107">Return Value</span></span>  
  
|<span data-ttu-id="935db-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="935db-108">HRESULT</span></span>|<span data-ttu-id="935db-109">Opis</span><span class="sxs-lookup"><span data-stu-id="935db-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="935db-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="935db-110">S_OK</span></span>|<span data-ttu-id="935db-111">`SetHostControl`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="935db-111">`SetHostControl` returned successfully.</span></span>|  
|<span data-ttu-id="935db-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="935db-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="935db-113">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="935db-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="935db-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="935db-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="935db-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="935db-115">The call timed out.</span></span>|  
|<span data-ttu-id="935db-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="935db-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="935db-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="935db-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="935db-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="935db-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="935db-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="935db-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="935db-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="935db-120">E_FAIL</span></span>|<span data-ttu-id="935db-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="935db-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="935db-122">Jeśli metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="935db-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="935db-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="935db-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="935db-124">E_CLR_ALREADY_STARTED</span><span class="sxs-lookup"><span data-stu-id="935db-124">E_CLR_ALREADY_STARTED</span></span>|<span data-ttu-id="935db-125">Środowisko CLR zostało już zainicjowane.</span><span class="sxs-lookup"><span data-stu-id="935db-125">The CLR has already been initialized.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="935db-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="935db-126">Remarks</span></span>  
 <span data-ttu-id="935db-127">Należy wywołać `SetHostControl` przed zainicjowaniem środowiska CLR, czyli przed wywołaniem [metody Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) lub użyciem dowolnego [interfejsu metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="935db-127">You must call `SetHostControl` before the CLR is initialized, that is, before you call [Start Method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) or use any of the [Metadata Interfaces](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span></span> <span data-ttu-id="935db-128">Zaleca się wywołanie `SetHostControl` natychmiast po wywołaniu [funkcji CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md) lub [funkcji CorBindToRuntimeEx](corbindtoruntimeex-function.md).</span><span class="sxs-lookup"><span data-stu-id="935db-128">It is recommended that you call `SetHostControl` immediately after calling [CorBindToCurrentRuntime Function](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md) or [CorBindToRuntimeEx Function](corbindtoruntimeex-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="935db-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="935db-129">Requirements</span></span>  
 <span data-ttu-id="935db-130">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="935db-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="935db-131">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="935db-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="935db-132">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="935db-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="935db-133">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="935db-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="935db-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="935db-134">See also</span></span>

- [<span data-ttu-id="935db-135">ICLRRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="935db-135">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
- [<span data-ttu-id="935db-136">IHostControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="935db-136">IHostControl Interface</span></span>](ihostcontrol-interface.md)
