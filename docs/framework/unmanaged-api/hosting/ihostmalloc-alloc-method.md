---
title: IHostMAlloc::Alloc — Metoda
ms.date: 03/30/2017
api_name:
- IHostMAlloc.Alloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMAlloc::Alloc
helpviewer_keywords:
- Alloc method, IHostMAlloc interface [.NET Framework hosting]
- IHostMAlloc::Alloc method [.NET Framework hosting]
ms.assetid: a3007f5e-d75d-4b37-842b-704e9edced5e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 32499e74e8af9a865347bd800d3db4c303a7344c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59126389"
---
# <a name="ihostmallocalloc-method"></a><span data-ttu-id="79e98-102">IHostMAlloc::Alloc — Metoda</span><span class="sxs-lookup"><span data-stu-id="79e98-102">IHostMAlloc::Alloc Method</span></span>
<span data-ttu-id="79e98-103">Żądania, że host przydzielić określonej ilości pamięci sterty.</span><span class="sxs-lookup"><span data-stu-id="79e98-103">Requests that the host allocate the specified amount of memory from the heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79e98-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="79e98-104">Syntax</span></span>  
  
```  
HRESULT Alloc (  
    [in] SIZE_T  cbSize,   
    [in] EMemoryCriticalLevel dwCriticalLevel,   
    [out] void** ppMem  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="79e98-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="79e98-105">Parameters</span></span>  
 `cbSize`  
 <span data-ttu-id="79e98-106">[in] Rozmiar w bajtach bieżąca żądania alokacji pamięci.</span><span class="sxs-lookup"><span data-stu-id="79e98-106">[in] The size, in bytes, of the current memory allocation request.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="79e98-107">[in] Jedną z [ememorycriticallevel —](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) wartości, wskazując wpływ wystąpił błąd alokacji.</span><span class="sxs-lookup"><span data-stu-id="79e98-107">[in] One of the [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) values, indicating the impact of an allocation failure.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="79e98-108">[out] Wskaźnik do przydzielonej pamięć, lub wartość null, jeśli nie można ukończyć żądania.</span><span class="sxs-lookup"><span data-stu-id="79e98-108">[out] A pointer to the allocated memory, or null if the request could not be completed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="79e98-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="79e98-109">Return Value</span></span>  
  
|<span data-ttu-id="79e98-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="79e98-110">HRESULT</span></span>|<span data-ttu-id="79e98-111">Opis</span><span class="sxs-lookup"><span data-stu-id="79e98-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="79e98-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="79e98-112">S_OK</span></span>|<span data-ttu-id="79e98-113">`Alloc` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="79e98-113">`Alloc` returned successfully.</span></span>|  
|<span data-ttu-id="79e98-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="79e98-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="79e98-115">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="79e98-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="79e98-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="79e98-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="79e98-117">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="79e98-117">The call timed out.</span></span>|  
|<span data-ttu-id="79e98-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="79e98-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="79e98-119">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="79e98-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="79e98-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="79e98-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="79e98-121">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="79e98-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="79e98-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="79e98-122">E_FAIL</span></span>|<span data-ttu-id="79e98-123">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="79e98-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="79e98-124">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="79e98-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="79e98-125">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="79e98-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="79e98-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="79e98-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="79e98-127">Za mało pamięci była dostępna do wykonania żądania alokacji.</span><span class="sxs-lookup"><span data-stu-id="79e98-127">Not enough memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="79e98-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="79e98-128">Remarks</span></span>  
 <span data-ttu-id="79e98-129">Środowisko CLR pobiera wskaźnik interfejsu do `IHostMalloc` wystąpienia, wywołując [ihostmemorymanager::createmalloc —](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="79e98-129">The CLR gets an interface pointer to an `IHostMalloc` instance by calling the [IHostMemoryManager::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79e98-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="79e98-130">Requirements</span></span>  
 <span data-ttu-id="79e98-131">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="79e98-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79e98-132">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="79e98-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="79e98-133">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="79e98-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="79e98-134">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79e98-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79e98-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="79e98-135">See also</span></span>

- [<span data-ttu-id="79e98-136">IHostMemoryManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="79e98-136">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="79e98-137">IHostMalloc, interfejs</span><span class="sxs-lookup"><span data-stu-id="79e98-137">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
