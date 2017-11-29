---
title: "IHostCrst::TryEnter — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostCrst.TryEnter
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostCrst::TryEnter
helpviewer_keywords:
- IHostCrst::TryEnter method [.NET Framework hosting]
- TryEnter method [.NET Framework hosting]
ms.assetid: a922fa98-beab-4f09-a342-cc94fc65687f
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c6b622666c3bda806c77329d0d0a10726b4838c6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ihostcrsttryenter-method"></a><span data-ttu-id="6312d-102">IHostCrst::TryEnter — Metoda</span><span class="sxs-lookup"><span data-stu-id="6312d-102">IHostCrst::TryEnter Method</span></span>
<span data-ttu-id="6312d-103">Próbuje wprowadź sekcja krytyczna reprezentowany przez bieżący [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="6312d-103">Attempts to enter the critical section represented by the current [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6312d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6312d-104">Syntax</span></span>  
  
```  
HRESULT TryEnter (  
    [in]  DWORD  option,  
    [out] BOOL   *pbSucceeded  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6312d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6312d-105">Parameters</span></span>  
 `option`  
 <span data-ttu-id="6312d-106">[in] Jeden z [wait_option —](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) wartości i wskazujący akcję hosta może pobierać bloki operacji.</span><span class="sxs-lookup"><span data-stu-id="6312d-106">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values, indicating what action the host should take if the operation blocks.</span></span>  
  
 `pbSucceeded`  
 <span data-ttu-id="6312d-107">[out] `true` Jeśli sekcja krytyczna można wprowadzić; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="6312d-107">[out] `true` if the critical section can be entered; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6312d-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6312d-108">Return Value</span></span>  
  
|<span data-ttu-id="6312d-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6312d-109">HRESULT</span></span>|<span data-ttu-id="6312d-110">Opis</span><span class="sxs-lookup"><span data-stu-id="6312d-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6312d-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="6312d-111">S_OK</span></span>|<span data-ttu-id="6312d-112">`TryEnter`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="6312d-112">`TryEnter` returned successfully.</span></span>|  
|<span data-ttu-id="6312d-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6312d-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6312d-114">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="6312d-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6312d-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6312d-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6312d-116">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="6312d-116">The call timed out.</span></span>|  
|<span data-ttu-id="6312d-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6312d-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6312d-118">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="6312d-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6312d-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6312d-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6312d-120">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="6312d-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6312d-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6312d-121">E_FAIL</span></span>|<span data-ttu-id="6312d-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="6312d-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6312d-123">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="6312d-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6312d-124">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="6312d-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6312d-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6312d-125">Remarks</span></span>  
 <span data-ttu-id="6312d-126">`TryEnter`Zwraca natychmiast i wskazuje, czy wątek wywołujący wprowadzony sekcja krytyczna.</span><span class="sxs-lookup"><span data-stu-id="6312d-126">`TryEnter` returns immediately and indicates whether the calling thread entered the critical section.</span></span> <span data-ttu-id="6312d-127">Ta metoda odzwierciedla Wind32 `TryEnterCriticalSection` funkcji.</span><span class="sxs-lookup"><span data-stu-id="6312d-127">This method mirrors the Wind32 `TryEnterCriticalSection` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6312d-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6312d-128">Requirements</span></span>  
 <span data-ttu-id="6312d-129">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6312d-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6312d-130">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6312d-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6312d-131">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6312d-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6312d-132">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6312d-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6312d-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6312d-133">See Also</span></span>  
 [<span data-ttu-id="6312d-134">ICLRSyncManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="6312d-134">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="6312d-135">IHostCrst — interfejs</span><span class="sxs-lookup"><span data-stu-id="6312d-135">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)  
 [<span data-ttu-id="6312d-136">IHostSyncManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="6312d-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
