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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6e385744f1a9ecef2cbe1f6074501061dc2f15fe
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54602263"
---
# <a name="iclrruntimehostsethostcontrol-method"></a><span data-ttu-id="0d733-102">ICLRRuntimeHost::SetHostControl — Metoda</span><span class="sxs-lookup"><span data-stu-id="0d733-102">ICLRRuntimeHost::SetHostControl Method</span></span>
<span data-ttu-id="0d733-103">Ustawia wskaźnik interfejsu, używanego przez środowisko uruchomieniowe języka wspólnego (CLR) można pobrać wdrożenia hosta [ihostcontrol — interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md).</span><span class="sxs-lookup"><span data-stu-id="0d733-103">Sets the interface pointer that the common language runtime (CLR) can use to get the host's implementation of [IHostControl Interface](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d733-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0d733-104">Syntax</span></span>  
  
```  
HRESULT SetHostControl(  
    [in] IHostControl* pHostControl  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0d733-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0d733-105">Parameters</span></span>  
 `pHostControl`  
 <span data-ttu-id="0d733-106">[in] Wskaźnik interfejsu do wdrożenia hosta [ihostcontrol — interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md).</span><span class="sxs-lookup"><span data-stu-id="0d733-106">[in] An interface pointer to the host's implementation of [IHostControl Interface](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0d733-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="0d733-107">Return Value</span></span>  
  
|<span data-ttu-id="0d733-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0d733-108">HRESULT</span></span>|<span data-ttu-id="0d733-109">Opis</span><span class="sxs-lookup"><span data-stu-id="0d733-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0d733-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="0d733-110">S_OK</span></span>|<span data-ttu-id="0d733-111">`SetHostControl` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="0d733-111">`SetHostControl` returned successfully.</span></span>|  
|<span data-ttu-id="0d733-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0d733-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0d733-113">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="0d733-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0d733-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0d733-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0d733-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="0d733-115">The call timed out.</span></span>|  
|<span data-ttu-id="0d733-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0d733-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0d733-117">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="0d733-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0d733-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0d733-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0d733-119">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="0d733-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0d733-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0d733-120">E_FAIL</span></span>|<span data-ttu-id="0d733-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="0d733-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0d733-122">Jeśli metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="0d733-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0d733-123">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0d733-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="0d733-124">E_CLR_ALREADY_STARTED</span><span class="sxs-lookup"><span data-stu-id="0d733-124">E_CLR_ALREADY_STARTED</span></span>|<span data-ttu-id="0d733-125">Środowisko CLR został już zainicjowany.</span><span class="sxs-lookup"><span data-stu-id="0d733-125">The CLR has already been initialized.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0d733-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0d733-126">Remarks</span></span>  
 <span data-ttu-id="0d733-127">Należy wywołać `SetHostControl` przed środowisko CLR jest inicjowany, oznacza to, zanim wywołasz [Metoda Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) lub korzystających z [interfejsy metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="0d733-127">You must call `SetHostControl` before the CLR is initialized, that is, before you call [Start Method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) or use any of the [Metadata Interfaces](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span></span> <span data-ttu-id="0d733-128">Zalecane jest, należy wywołać `SetHostControl` natychmiast po wywołaniu [corbindtocurrentruntime — funkcja](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md) lub [corbindtoruntimeex — funkcja](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md).</span><span class="sxs-lookup"><span data-stu-id="0d733-128">It is recommended that you call `SetHostControl` immediately after calling [CorBindToCurrentRuntime Function](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md) or [CorBindToRuntimeEx Function](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d733-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0d733-129">Requirements</span></span>  
 <span data-ttu-id="0d733-130">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d733-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d733-131">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0d733-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0d733-132">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0d733-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0d733-133">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d733-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d733-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0d733-134">See also</span></span>
- [<span data-ttu-id="0d733-135">ICLRRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="0d733-135">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
- [<span data-ttu-id="0d733-136">IHostControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="0d733-136">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
