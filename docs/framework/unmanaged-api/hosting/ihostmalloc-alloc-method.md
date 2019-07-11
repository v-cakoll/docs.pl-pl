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
ms.openlocfilehash: e38d1f3cfe78b7f47a37c12c84282196f4385fbb
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780745"
---
# <a name="ihostmallocalloc-method"></a><span data-ttu-id="abd13-102">IHostMAlloc::Alloc — Metoda</span><span class="sxs-lookup"><span data-stu-id="abd13-102">IHostMAlloc::Alloc Method</span></span>
<span data-ttu-id="abd13-103">Żądania, że host przydzielić określonej ilości pamięci sterty.</span><span class="sxs-lookup"><span data-stu-id="abd13-103">Requests that the host allocate the specified amount of memory from the heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abd13-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="abd13-104">Syntax</span></span>  
  
```cpp  
HRESULT Alloc (  
    [in] SIZE_T  cbSize,   
    [in] EMemoryCriticalLevel dwCriticalLevel,   
    [out] void** ppMem  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="abd13-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="abd13-105">Parameters</span></span>  
 `cbSize`  
 <span data-ttu-id="abd13-106">[in] Rozmiar w bajtach bieżąca żądania alokacji pamięci.</span><span class="sxs-lookup"><span data-stu-id="abd13-106">[in] The size, in bytes, of the current memory allocation request.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="abd13-107">[in] Jedną z [ememorycriticallevel —](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) wartości, wskazując wpływ wystąpił błąd alokacji.</span><span class="sxs-lookup"><span data-stu-id="abd13-107">[in] One of the [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) values, indicating the impact of an allocation failure.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="abd13-108">[out] Wskaźnik do przydzielonej pamięć, lub wartość null, jeśli nie można ukończyć żądania.</span><span class="sxs-lookup"><span data-stu-id="abd13-108">[out] A pointer to the allocated memory, or null if the request could not be completed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="abd13-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="abd13-109">Return Value</span></span>  
  
|<span data-ttu-id="abd13-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="abd13-110">HRESULT</span></span>|<span data-ttu-id="abd13-111">Opis</span><span class="sxs-lookup"><span data-stu-id="abd13-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="abd13-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="abd13-112">S_OK</span></span>|<span data-ttu-id="abd13-113">`Alloc` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="abd13-113">`Alloc` returned successfully.</span></span>|  
|<span data-ttu-id="abd13-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="abd13-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="abd13-115">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="abd13-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="abd13-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="abd13-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="abd13-117">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="abd13-117">The call timed out.</span></span>|  
|<span data-ttu-id="abd13-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="abd13-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="abd13-119">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="abd13-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="abd13-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="abd13-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="abd13-121">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="abd13-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="abd13-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="abd13-122">E_FAIL</span></span>|<span data-ttu-id="abd13-123">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="abd13-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="abd13-124">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="abd13-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="abd13-125">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="abd13-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="abd13-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="abd13-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="abd13-127">Za mało pamięci była dostępna do wykonania żądania alokacji.</span><span class="sxs-lookup"><span data-stu-id="abd13-127">Not enough memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="abd13-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="abd13-128">Remarks</span></span>  
 <span data-ttu-id="abd13-129">Środowisko CLR pobiera wskaźnik interfejsu do `IHostMalloc` wystąpienia, wywołując [ihostmemorymanager::createmalloc —](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="abd13-129">The CLR gets an interface pointer to an `IHostMalloc` instance by calling the [IHostMemoryManager::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="abd13-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="abd13-130">Requirements</span></span>  
 <span data-ttu-id="abd13-131">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="abd13-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="abd13-132">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="abd13-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="abd13-133">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="abd13-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="abd13-134">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="abd13-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abd13-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="abd13-135">See also</span></span>

- [<span data-ttu-id="abd13-136">IHostMemoryManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="abd13-136">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="abd13-137">IHostMalloc, interfejs</span><span class="sxs-lookup"><span data-stu-id="abd13-137">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
