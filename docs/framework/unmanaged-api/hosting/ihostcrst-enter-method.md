---
title: "IHostCrst::Enter — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostCrst.Enter
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostCrst::Enter
helpviewer_keywords:
- Enter method [.NET Framework hosting]
- IHostCrst::Enter method [.NET Framework hosting]
ms.assetid: 100dd7eb-7053-4295-9bb3-32ba47f6ec79
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 390f30c85dac494451af1ff82328c913dd9438ab
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ihostcrstenter-method"></a><span data-ttu-id="1bd23-102">IHostCrst::Enter — Metoda</span><span class="sxs-lookup"><span data-stu-id="1bd23-102">IHostCrst::Enter Method</span></span>
<span data-ttu-id="1bd23-103">Wprowadza sekcja krytyczna, reprezentowanego przez bieżący [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="1bd23-103">Enters the critical section that is represented by the current [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1bd23-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1bd23-104">Syntax</span></span>  
  
```  
HRESULT Enter (  
    [in] DWORD option  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1bd23-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1bd23-105">Parameters</span></span>  
 `option`  
 <span data-ttu-id="1bd23-106">[in] Jeden z [wait_option —](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) wartości i wskazujący akcję hosta może pobierać bloki operacji.</span><span class="sxs-lookup"><span data-stu-id="1bd23-106">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values, indicating what action the host should take if the operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1bd23-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1bd23-107">Return Value</span></span>  
  
|<span data-ttu-id="1bd23-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1bd23-108">HRESULT</span></span>|<span data-ttu-id="1bd23-109">Opis</span><span class="sxs-lookup"><span data-stu-id="1bd23-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1bd23-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="1bd23-110">S_OK</span></span>|<span data-ttu-id="1bd23-111">`Enter`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="1bd23-111">`Enter` returned successfully.</span></span>|  
|<span data-ttu-id="1bd23-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1bd23-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1bd23-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="1bd23-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1bd23-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1bd23-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1bd23-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="1bd23-115">The call timed out.</span></span>|  
|<span data-ttu-id="1bd23-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1bd23-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1bd23-117">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="1bd23-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1bd23-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1bd23-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1bd23-119">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="1bd23-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1bd23-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1bd23-120">E_FAIL</span></span>|<span data-ttu-id="1bd23-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="1bd23-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1bd23-122">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="1bd23-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1bd23-123">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="1bd23-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1bd23-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1bd23-124">Remarks</span></span>  
 <span data-ttu-id="1bd23-125">`Enter`odzwierciedla Win32 `EnterCriticalSection` funkcji.</span><span class="sxs-lookup"><span data-stu-id="1bd23-125">`Enter` mirrors the Win32 `EnterCriticalSection` function.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1bd23-126">Ta metoda nie zwraca aż do wprowadzenia jest sekcja krytyczna.</span><span class="sxs-lookup"><span data-stu-id="1bd23-126">This method does not return until the critical section is entered.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1bd23-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1bd23-127">Requirements</span></span>  
 <span data-ttu-id="1bd23-128">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1bd23-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1bd23-129">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1bd23-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1bd23-130">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1bd23-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1bd23-131">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1bd23-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bd23-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1bd23-132">See Also</span></span>  
 [<span data-ttu-id="1bd23-133">ICLRSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="1bd23-133">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="1bd23-134">IHostCrst, interfejs</span><span class="sxs-lookup"><span data-stu-id="1bd23-134">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)  
 [<span data-ttu-id="1bd23-135">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="1bd23-135">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
