---
title: IHostMAlloc::DebugAlloc — Metoda
ms.date: 03/30/2017
api_name:
- IHostMAlloc.DebugAlloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMAlloc::DebugAlloc
helpviewer_keywords:
- DebugAlloc method [.NET Framework hosting]
- IHostMAlloc::DebugAlloc method [.NET Framework hosting]
ms.assetid: 0bfbc527-bea2-43ce-b041-69186f4440dd
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6e089d133374f112dea13e91f9bd571bd2b5af07
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59132928"
---
# <a name="ihostmallocdebugalloc-method"></a><span data-ttu-id="e8c20-102">IHostMAlloc::DebugAlloc — Metoda</span><span class="sxs-lookup"><span data-stu-id="e8c20-102">IHostMAlloc::DebugAlloc Method</span></span>
<span data-ttu-id="e8c20-103">Żąda hosta przydzielić określonej ilości pamięci sterty i dodatkowo Śledź, gdzie pamięć została alokowana.</span><span class="sxs-lookup"><span data-stu-id="e8c20-103">Requests that the host allocate the specified amount of memory from the heap, and additionally track where the memory was allocated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8c20-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e8c20-104">Syntax</span></span>  
  
```  
HRESULT DebugAlloc (  
    [in]  SIZE_T  cbSize,   
    [in]  EMemoryCriticalLevel dwCriticalLevel,   
    [in]  char*   pszFileName,   
    [in]  int     iLineNo,   
    [out] void**  ppMem  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e8c20-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e8c20-105">Parameters</span></span>  
 `cbSize`  
 <span data-ttu-id="e8c20-106">[in] Rozmiar w bajtach bieżąca żądania alokacji pamięci.</span><span class="sxs-lookup"><span data-stu-id="e8c20-106">[in] The size, in bytes, of the current memory allocation request.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="e8c20-107">[in] Jedną z [ememorycriticallevel —](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) wartości, wskazując wpływ wystąpił błąd alokacji.</span><span class="sxs-lookup"><span data-stu-id="e8c20-107">[in] One of the [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) values, indicating the impact of an allocation failure.</span></span>  
  
 `pszFileName`  
 <span data-ttu-id="e8c20-108">[in] Plik kodu programu do debugowanego pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="e8c20-108">[in] The code file of the executable being debugged.</span></span>  
  
 `iLineNo`  
 <span data-ttu-id="e8c20-109">[in] Numer wiersza w `pszFileName` gdzie zażądano alokacji.</span><span class="sxs-lookup"><span data-stu-id="e8c20-109">[in] The line number in `pszFileName` where the allocation was requested.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="e8c20-110">[out] Wskaźnik do przydzielonej pamięć, lub wartość null, jeśli nie można ukończyć żądania.</span><span class="sxs-lookup"><span data-stu-id="e8c20-110">[out] A pointer to the allocated memory, or null if the request could not be completed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e8c20-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e8c20-111">Return Value</span></span>  
  
|<span data-ttu-id="e8c20-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e8c20-112">HRESULT</span></span>|<span data-ttu-id="e8c20-113">Opis</span><span class="sxs-lookup"><span data-stu-id="e8c20-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e8c20-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="e8c20-114">S_OK</span></span>|<span data-ttu-id="e8c20-115">`DebugAlloc` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="e8c20-115">`DebugAlloc` returned successfully.</span></span>|  
|<span data-ttu-id="e8c20-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e8c20-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e8c20-117">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="e8c20-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e8c20-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e8c20-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e8c20-119">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="e8c20-119">The call timed out.</span></span>|  
|<span data-ttu-id="e8c20-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e8c20-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e8c20-121">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="e8c20-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e8c20-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e8c20-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e8c20-123">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="e8c20-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e8c20-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e8c20-124">E_FAIL</span></span>|<span data-ttu-id="e8c20-125">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="e8c20-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e8c20-126">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="e8c20-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e8c20-127">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e8c20-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e8c20-128">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="e8c20-128">E_OUTOFMEMORY</span></span>|<span data-ttu-id="e8c20-129">Za mało pamięci była dostępna do wykonania żądania alokacji.</span><span class="sxs-lookup"><span data-stu-id="e8c20-129">Not enough memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e8c20-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e8c20-130">Remarks</span></span>  
 <span data-ttu-id="e8c20-131">Środowisko CLR pobiera wskaźnik interfejsu do [ihostmalloc —](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) wystąpienia, wywołując [ihostmemorymanager::createmalloc —](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="e8c20-131">The CLR gets an interface pointer to an [IHostMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) instance by calling the [IHostMemoryManager::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) method.</span></span> <span data-ttu-id="e8c20-132">`DebugAlloc` Umożliwia środowiska uruchomieniowego uzyskać informacje o pliku kod do użycia podczas debugowania.</span><span class="sxs-lookup"><span data-stu-id="e8c20-132">`DebugAlloc` allows the runtime to get code file information for use during debugging.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8c20-133">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e8c20-133">Requirements</span></span>  
 <span data-ttu-id="e8c20-134">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e8c20-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8c20-135">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e8c20-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e8c20-136">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e8c20-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e8c20-137">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8c20-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8c20-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e8c20-138">See also</span></span>

- [<span data-ttu-id="e8c20-139">IHostMemoryManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="e8c20-139">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="e8c20-140">IHostMalloc, interfejs</span><span class="sxs-lookup"><span data-stu-id="e8c20-140">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
