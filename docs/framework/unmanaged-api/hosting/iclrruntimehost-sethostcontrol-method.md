---
title: "ICLRRuntimeHost::SetHostControl — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9727144e9504a5a3ad7ae2529286440d07633b2a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iclrruntimehostsethostcontrol-method"></a><span data-ttu-id="25617-102">ICLRRuntimeHost::SetHostControl — Metoda</span><span class="sxs-lookup"><span data-stu-id="25617-102">ICLRRuntimeHost::SetHostControl Method</span></span>
<span data-ttu-id="25617-103">Ustawia wskaźnik interfejsu używanego przez środowisko uruchomieniowe języka wspólnego (CLR) Aby uzyskać implementację hosta [IHostControl — interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md).</span><span class="sxs-lookup"><span data-stu-id="25617-103">Sets the interface pointer that the common language runtime (CLR) can use to get the host's implementation of [IHostControl Interface](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25617-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="25617-104">Syntax</span></span>  
  
```  
HRESULT SetHostControl(  
    [in] IHostControl* pHostControl  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="25617-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="25617-105">Parameters</span></span>  
 `pHostControl`  
 <span data-ttu-id="25617-106">[in] Wskaźnik interfejsu do wdrożenia hosta [IHostControl — interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md).</span><span class="sxs-lookup"><span data-stu-id="25617-106">[in] An interface pointer to the host's implementation of [IHostControl Interface](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="25617-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="25617-107">Return Value</span></span>  
  
|<span data-ttu-id="25617-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="25617-108">HRESULT</span></span>|<span data-ttu-id="25617-109">Opis</span><span class="sxs-lookup"><span data-stu-id="25617-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="25617-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="25617-110">S_OK</span></span>|<span data-ttu-id="25617-111">`SetHostControl`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="25617-111">`SetHostControl` returned successfully.</span></span>|  
|<span data-ttu-id="25617-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="25617-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="25617-113">Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="25617-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="25617-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="25617-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="25617-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="25617-115">The call timed out.</span></span>|  
|<span data-ttu-id="25617-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="25617-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="25617-117">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="25617-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="25617-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="25617-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="25617-119">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="25617-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="25617-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="25617-120">E_FAIL</span></span>|<span data-ttu-id="25617-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="25617-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="25617-122">Jeśli metoda zwraca E_FAIL, CLR nie będzie już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="25617-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="25617-123">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="25617-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="25617-124">E_CLR_ALREADY_STARTED</span><span class="sxs-lookup"><span data-stu-id="25617-124">E_CLR_ALREADY_STARTED</span></span>|<span data-ttu-id="25617-125">Środowisko CLR został już zainicjowany.</span><span class="sxs-lookup"><span data-stu-id="25617-125">The CLR has already been initialized.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="25617-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="25617-126">Remarks</span></span>  
 <span data-ttu-id="25617-127">Należy wywołać `SetHostControl` przed środowiska CLR został zainicjowany, oznacza to, że przed wywołaniem [Metoda Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) lub użyć innych [interfejsy metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="25617-127">You must call `SetHostControl` before the CLR is initialized, that is, before you call [Start Method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) or use any of the [Metadata Interfaces](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span></span> <span data-ttu-id="25617-128">Zalecane jest telefoniczne skontaktowanie się z `SetHostControl` natychmiast po wywołaniu [CorBindToCurrentRuntime — funkcja](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md) lub [CorBindToRuntimeEx — funkcja](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md).</span><span class="sxs-lookup"><span data-stu-id="25617-128">It is recommended that you call `SetHostControl` immediately after calling [CorBindToCurrentRuntime Function](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md) or [CorBindToRuntimeEx Function](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25617-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="25617-129">Requirements</span></span>  
 <span data-ttu-id="25617-130">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25617-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25617-131">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="25617-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="25617-132">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="25617-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="25617-133">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25617-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25617-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="25617-134">See Also</span></span>  
 [<span data-ttu-id="25617-135">ICLRRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="25617-135">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)  
 [<span data-ttu-id="25617-136">IHostControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="25617-136">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
