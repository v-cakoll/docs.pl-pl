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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59126389"
---
# <a name="ihostmallocalloc-method"></a><span data-ttu-id="a9956-102">IHostMAlloc::Alloc — Metoda</span><span class="sxs-lookup"><span data-stu-id="a9956-102">IHostMAlloc::Alloc Method</span></span>
<span data-ttu-id="a9956-103">Żądania, że host przydzielić określonej ilości pamięci sterty.</span><span class="sxs-lookup"><span data-stu-id="a9956-103">Requests that the host allocate the specified amount of memory from the heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9956-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a9956-104">Syntax</span></span>  
  
```  
HRESULT Alloc (  
    [in] SIZE_T  cbSize,   
    [in] EMemoryCriticalLevel dwCriticalLevel,   
    [out] void** ppMem  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a9956-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a9956-105">Parameters</span></span>  
 `cbSize`  
 <span data-ttu-id="a9956-106">[in] Rozmiar w bajtach bieżąca żądania alokacji pamięci.</span><span class="sxs-lookup"><span data-stu-id="a9956-106">[in] The size, in bytes, of the current memory allocation request.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="a9956-107">[in] Jedną z [ememorycriticallevel —](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) wartości, wskazując wpływ wystąpił błąd alokacji.</span><span class="sxs-lookup"><span data-stu-id="a9956-107">[in] One of the [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) values, indicating the impact of an allocation failure.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="a9956-108">[out] Wskaźnik do przydzielonej pamięć, lub wartość null, jeśli nie można ukończyć żądania.</span><span class="sxs-lookup"><span data-stu-id="a9956-108">[out] A pointer to the allocated memory, or null if the request could not be completed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a9956-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a9956-109">Return Value</span></span>  
  
|<span data-ttu-id="a9956-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a9956-110">HRESULT</span></span>|<span data-ttu-id="a9956-111">Opis</span><span class="sxs-lookup"><span data-stu-id="a9956-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a9956-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="a9956-112">S_OK</span></span>|`Alloc` <span data-ttu-id="a9956-113">pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="a9956-113">returned successfully.</span></span>|  
|<span data-ttu-id="a9956-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a9956-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a9956-115">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="a9956-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a9956-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a9956-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a9956-117">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="a9956-117">The call timed out.</span></span>|  
|<span data-ttu-id="a9956-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a9956-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a9956-119">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="a9956-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a9956-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a9956-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a9956-121">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="a9956-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a9956-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a9956-122">E_FAIL</span></span>|<span data-ttu-id="a9956-123">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="a9956-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a9956-124">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="a9956-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a9956-125">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a9956-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="a9956-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="a9956-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="a9956-127">Za mało pamięci była dostępna do wykonania żądania alokacji.</span><span class="sxs-lookup"><span data-stu-id="a9956-127">Not enough memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a9956-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a9956-128">Remarks</span></span>  
 <span data-ttu-id="a9956-129">Środowisko CLR pobiera wskaźnik interfejsu do `IHostMalloc` wystąpienia, wywołując [ihostmemorymanager::createmalloc —](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="a9956-129">The CLR gets an interface pointer to an `IHostMalloc` instance by calling the [IHostMemoryManager::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9956-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a9956-130">Requirements</span></span>  
 <span data-ttu-id="a9956-131">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9956-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9956-132">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a9956-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a9956-133">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a9956-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="a9956-134">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="a9956-134">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a9956-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a9956-135">See also</span></span>

- [<span data-ttu-id="a9956-136">IHostMemoryManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="a9956-136">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="a9956-137">IHostMalloc — Interfejs</span><span class="sxs-lookup"><span data-stu-id="a9956-137">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
