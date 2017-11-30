---
title: "IHostMAlloc::Alloc — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostMAlloc.Alloc
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostMAlloc::Alloc
helpviewer_keywords:
- Alloc method, IHostMAlloc interface [.NET Framework hosting]
- IHostMAlloc::Alloc method [.NET Framework hosting]
ms.assetid: a3007f5e-d75d-4b37-842b-704e9edced5e
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9cc4447424d1594f6fa86e07be659a6ba97f0427
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ihostmallocalloc-method"></a><span data-ttu-id="228e1-102">IHostMAlloc::Alloc — Metoda</span><span class="sxs-lookup"><span data-stu-id="228e1-102">IHostMAlloc::Alloc Method</span></span>
<span data-ttu-id="228e1-103">Żądania, że host przydzielić określoną ilością pamięci sterty.</span><span class="sxs-lookup"><span data-stu-id="228e1-103">Requests that the host allocate the specified amount of memory from the heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="228e1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="228e1-104">Syntax</span></span>  
  
```  
HRESULT Alloc (  
    [in] SIZE_T  cbSize,   
    [in] EMemoryCriticalLevel dwCriticalLevel,   
    [out] void** ppMem  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="228e1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="228e1-105">Parameters</span></span>  
 `cbSize`  
 <span data-ttu-id="228e1-106">[in] Rozmiar w bajtach, bieżącego żądania alokacji pamięci.</span><span class="sxs-lookup"><span data-stu-id="228e1-106">[in] The size, in bytes, of the current memory allocation request.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="228e1-107">[in] Jeden z [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) wartości i wskazujący wpływ błąd alokacji.</span><span class="sxs-lookup"><span data-stu-id="228e1-107">[in] One of the [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) values, indicating the impact of an allocation failure.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="228e1-108">[out] Wskaźnik do alokacji pamięci lub wartość null, jeśli nie można ukończyć żądania.</span><span class="sxs-lookup"><span data-stu-id="228e1-108">[out] A pointer to the allocated memory, or null if the request could not be completed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="228e1-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="228e1-109">Return Value</span></span>  
  
|<span data-ttu-id="228e1-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="228e1-110">HRESULT</span></span>|<span data-ttu-id="228e1-111">Opis</span><span class="sxs-lookup"><span data-stu-id="228e1-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="228e1-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="228e1-112">S_OK</span></span>|<span data-ttu-id="228e1-113">`Alloc`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="228e1-113">`Alloc` returned successfully.</span></span>|  
|<span data-ttu-id="228e1-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="228e1-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="228e1-115">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="228e1-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="228e1-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="228e1-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="228e1-117">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="228e1-117">The call timed out.</span></span>|  
|<span data-ttu-id="228e1-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="228e1-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="228e1-119">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="228e1-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="228e1-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="228e1-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="228e1-121">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="228e1-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="228e1-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="228e1-122">E_FAIL</span></span>|<span data-ttu-id="228e1-123">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="228e1-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="228e1-124">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="228e1-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="228e1-125">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="228e1-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="228e1-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="228e1-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="228e1-127">Za mało pamięci nie była dostępna do wykonania żądania alokacji.</span><span class="sxs-lookup"><span data-stu-id="228e1-127">Not enough memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="228e1-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="228e1-128">Remarks</span></span>  
 <span data-ttu-id="228e1-129">Środowisko CLR pobiera wskaźnika interfejsu do `IHostMalloc` wystąpienia przez wywołanie metody [IHostMemoryManager::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="228e1-129">The CLR gets an interface pointer to an `IHostMalloc` instance by calling the [IHostMemoryManager::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="228e1-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="228e1-130">Requirements</span></span>  
 <span data-ttu-id="228e1-131">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="228e1-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="228e1-132">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="228e1-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="228e1-133">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="228e1-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="228e1-134">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="228e1-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="228e1-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="228e1-135">See Also</span></span>  
 [<span data-ttu-id="228e1-136">IHostMemoryManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="228e1-136">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 [<span data-ttu-id="228e1-137">IHostMalloc — interfejs</span><span class="sxs-lookup"><span data-stu-id="228e1-137">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
