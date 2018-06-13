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
ms.openlocfilehash: 46cfaa5870d7bbc7edcbe438ddf57fe5f70ad938
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434968"
---
# <a name="iclrruntimehostsethostcontrol-method"></a><span data-ttu-id="6047c-102">ICLRRuntimeHost::SetHostControl — Metoda</span><span class="sxs-lookup"><span data-stu-id="6047c-102">ICLRRuntimeHost::SetHostControl Method</span></span>
<span data-ttu-id="6047c-103">Ustawia wskaźnik interfejsu używanego przez środowisko uruchomieniowe języka wspólnego (CLR) Aby uzyskać implementację hosta [IHostControl — interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md).</span><span class="sxs-lookup"><span data-stu-id="6047c-103">Sets the interface pointer that the common language runtime (CLR) can use to get the host's implementation of [IHostControl Interface](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6047c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6047c-104">Syntax</span></span>  
  
```  
HRESULT SetHostControl(  
    [in] IHostControl* pHostControl  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6047c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6047c-105">Parameters</span></span>  
 `pHostControl`  
 <span data-ttu-id="6047c-106">[in] Wskaźnik interfejsu do wdrożenia hosta [IHostControl — interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md).</span><span class="sxs-lookup"><span data-stu-id="6047c-106">[in] An interface pointer to the host's implementation of [IHostControl Interface](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6047c-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6047c-107">Return Value</span></span>  
  
|<span data-ttu-id="6047c-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6047c-108">HRESULT</span></span>|<span data-ttu-id="6047c-109">Opis</span><span class="sxs-lookup"><span data-stu-id="6047c-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6047c-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="6047c-110">S_OK</span></span>|<span data-ttu-id="6047c-111">`SetHostControl` zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="6047c-111">`SetHostControl` returned successfully.</span></span>|  
|<span data-ttu-id="6047c-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6047c-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6047c-113">Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="6047c-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6047c-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6047c-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6047c-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="6047c-115">The call timed out.</span></span>|  
|<span data-ttu-id="6047c-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6047c-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6047c-117">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="6047c-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6047c-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6047c-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6047c-119">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="6047c-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6047c-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6047c-120">E_FAIL</span></span>|<span data-ttu-id="6047c-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="6047c-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6047c-122">Jeśli metoda zwraca E_FAIL, CLR nie będzie już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="6047c-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6047c-123">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="6047c-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="6047c-124">E_CLR_ALREADY_STARTED</span><span class="sxs-lookup"><span data-stu-id="6047c-124">E_CLR_ALREADY_STARTED</span></span>|<span data-ttu-id="6047c-125">Środowisko CLR został już zainicjowany.</span><span class="sxs-lookup"><span data-stu-id="6047c-125">The CLR has already been initialized.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6047c-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6047c-126">Remarks</span></span>  
 <span data-ttu-id="6047c-127">Należy wywołać `SetHostControl` przed środowiska CLR został zainicjowany, oznacza to, że przed wywołaniem [Metoda Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) lub użyć innych [interfejsy metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="6047c-127">You must call `SetHostControl` before the CLR is initialized, that is, before you call [Start Method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) or use any of the [Metadata Interfaces](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span></span> <span data-ttu-id="6047c-128">Zalecane jest telefoniczne skontaktowanie się z `SetHostControl` natychmiast po wywołaniu [CorBindToCurrentRuntime — funkcja](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md) lub [CorBindToRuntimeEx — funkcja](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md).</span><span class="sxs-lookup"><span data-stu-id="6047c-128">It is recommended that you call `SetHostControl` immediately after calling [CorBindToCurrentRuntime Function](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md) or [CorBindToRuntimeEx Function](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6047c-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6047c-129">Requirements</span></span>  
 <span data-ttu-id="6047c-130">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6047c-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6047c-131">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6047c-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6047c-132">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6047c-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6047c-133">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6047c-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6047c-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6047c-134">See Also</span></span>  
 [<span data-ttu-id="6047c-135">ICLRRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="6047c-135">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)  
 [<span data-ttu-id="6047c-136">IHostControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="6047c-136">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
