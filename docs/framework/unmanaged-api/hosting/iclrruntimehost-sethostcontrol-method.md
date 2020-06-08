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
ms.openlocfilehash: 644b31ae8e8f0c51c08bcad57220a028406cfd3a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504078"
---
# <a name="iclrruntimehostsethostcontrol-method"></a><span data-ttu-id="ac5f9-102">ICLRRuntimeHost::SetHostControl — Metoda</span><span class="sxs-lookup"><span data-stu-id="ac5f9-102">ICLRRuntimeHost::SetHostControl Method</span></span>
<span data-ttu-id="ac5f9-103">Ustawia wskaźnik interfejsu, który może być używany przez środowisko uruchomieniowe języka wspólnego (CLR), aby uzyskać implementację [interfejsu IHostControl](ihostcontrol-interface.md).</span><span class="sxs-lookup"><span data-stu-id="ac5f9-103">Sets the interface pointer that the common language runtime (CLR) can use to get the host's implementation of [IHostControl Interface](ihostcontrol-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac5f9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ac5f9-104">Syntax</span></span>  
  
```cpp  
HRESULT SetHostControl(  
    [in] IHostControl* pHostControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ac5f9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ac5f9-105">Parameters</span></span>  
 `pHostControl`  
 <span data-ttu-id="ac5f9-106">podczas Wskaźnik interfejsu do implementacji [interfejsu IHostControl](ihostcontrol-interface.md)hosta.</span><span class="sxs-lookup"><span data-stu-id="ac5f9-106">[in] An interface pointer to the host's implementation of [IHostControl Interface](ihostcontrol-interface.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ac5f9-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ac5f9-107">Return Value</span></span>  
  
|<span data-ttu-id="ac5f9-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ac5f9-108">HRESULT</span></span>|<span data-ttu-id="ac5f9-109">Opis</span><span class="sxs-lookup"><span data-stu-id="ac5f9-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ac5f9-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="ac5f9-110">S_OK</span></span>|<span data-ttu-id="ac5f9-111">`SetHostControl`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="ac5f9-111">`SetHostControl` returned successfully.</span></span>|  
|<span data-ttu-id="ac5f9-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ac5f9-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ac5f9-113">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="ac5f9-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ac5f9-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ac5f9-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ac5f9-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="ac5f9-115">The call timed out.</span></span>|  
|<span data-ttu-id="ac5f9-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ac5f9-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ac5f9-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="ac5f9-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ac5f9-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ac5f9-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ac5f9-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="ac5f9-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ac5f9-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ac5f9-120">E_FAIL</span></span>|<span data-ttu-id="ac5f9-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="ac5f9-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ac5f9-122">Jeśli metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="ac5f9-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ac5f9-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ac5f9-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="ac5f9-124">E_CLR_ALREADY_STARTED</span><span class="sxs-lookup"><span data-stu-id="ac5f9-124">E_CLR_ALREADY_STARTED</span></span>|<span data-ttu-id="ac5f9-125">Środowisko CLR zostało już zainicjowane.</span><span class="sxs-lookup"><span data-stu-id="ac5f9-125">The CLR has already been initialized.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ac5f9-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ac5f9-126">Remarks</span></span>  
 <span data-ttu-id="ac5f9-127">Należy wywołać `SetHostControl` przed zainicjowaniem środowiska CLR, czyli przed wywołaniem [metody Start](iclrruntimehost-start-method.md) lub użyciem dowolnego [interfejsu metadanych](../metadata/metadata-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="ac5f9-127">You must call `SetHostControl` before the CLR is initialized, that is, before you call [Start Method](iclrruntimehost-start-method.md) or use any of the [Metadata Interfaces](../metadata/metadata-interfaces.md).</span></span> <span data-ttu-id="ac5f9-128">Zaleca się wywołanie `SetHostControl` natychmiast po wywołaniu [funkcji CorBindToCurrentRuntime](corbindtocurrentruntime-function.md) lub [funkcji CorBindToRuntimeEx](corbindtoruntimeex-function.md).</span><span class="sxs-lookup"><span data-stu-id="ac5f9-128">It is recommended that you call `SetHostControl` immediately after calling [CorBindToCurrentRuntime Function](corbindtocurrentruntime-function.md) or [CorBindToRuntimeEx Function](corbindtoruntimeex-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac5f9-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ac5f9-129">Requirements</span></span>  
 <span data-ttu-id="ac5f9-130">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac5f9-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac5f9-131">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ac5f9-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ac5f9-132">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ac5f9-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ac5f9-133">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac5f9-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac5f9-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ac5f9-134">See also</span></span>

- [<span data-ttu-id="ac5f9-135">ICLRRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="ac5f9-135">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
- [<span data-ttu-id="ac5f9-136">IHostControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="ac5f9-136">IHostControl Interface</span></span>](ihostcontrol-interface.md)
