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
ms.openlocfilehash: dded37fdef02963f60883b289462aa6a96693b3d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176308"
---
# <a name="ihostmallocalloc-method"></a><span data-ttu-id="92618-102">IHostMAlloc::Alloc — Metoda</span><span class="sxs-lookup"><span data-stu-id="92618-102">IHostMAlloc::Alloc Method</span></span>
<span data-ttu-id="92618-103">Żąda, aby host przydzielić określoną ilość pamięci ze sterty.</span><span class="sxs-lookup"><span data-stu-id="92618-103">Requests that the host allocate the specified amount of memory from the heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92618-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="92618-104">Syntax</span></span>  
  
```cpp  
HRESULT Alloc (  
    [in] SIZE_T  cbSize,
    [in] EMemoryCriticalLevel dwCriticalLevel,
    [out] void** ppMem  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="92618-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="92618-105">Parameters</span></span>  
 `cbSize`  
 <span data-ttu-id="92618-106">[w] Rozmiar w bajtach bieżącego żądania alokacji pamięci.</span><span class="sxs-lookup"><span data-stu-id="92618-106">[in] The size, in bytes, of the current memory allocation request.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="92618-107">[w] Jedna z [wartości EMemoryCriticalLevel,](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) wskazująca wpływ błędu alokacji.</span><span class="sxs-lookup"><span data-stu-id="92618-107">[in] One of the [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) values, indicating the impact of an allocation failure.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="92618-108">[na zewnątrz] Wskaźnik do przydzielonej pamięci lub null, jeśli nie można ukończyć żądania.</span><span class="sxs-lookup"><span data-stu-id="92618-108">[out] A pointer to the allocated memory, or null if the request could not be completed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="92618-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="92618-109">Return Value</span></span>  
  
|<span data-ttu-id="92618-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="92618-110">HRESULT</span></span>|<span data-ttu-id="92618-111">Opis</span><span class="sxs-lookup"><span data-stu-id="92618-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="92618-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="92618-112">S_OK</span></span>|<span data-ttu-id="92618-113">`Alloc`zwrócono pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="92618-113">`Alloc` returned successfully.</span></span>|  
|<span data-ttu-id="92618-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="92618-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="92618-115">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchomić kod zarządzany lub proces wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="92618-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="92618-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="92618-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="92618-117">Limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="92618-117">The call timed out.</span></span>|  
|<span data-ttu-id="92618-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="92618-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="92618-119">Wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="92618-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="92618-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="92618-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="92618-121">Zdarzenie zostało anulowane, gdy czekał na niego zablokowany wątek lub włókno.</span><span class="sxs-lookup"><span data-stu-id="92618-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="92618-122">E_fail</span><span class="sxs-lookup"><span data-stu-id="92618-122">E_FAIL</span></span>|<span data-ttu-id="92618-123">Doszło do nieznanej katastrofalnej awarii.</span><span class="sxs-lookup"><span data-stu-id="92618-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="92618-124">Gdy metoda zwraca E_FAIL, CLR nie jest już użyteczny w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="92618-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="92618-125">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="92618-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="92618-126">E_outofmemory</span><span class="sxs-lookup"><span data-stu-id="92618-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="92618-127">Za mało pamięci było dostępne, aby zakończyć żądanie alokacji.</span><span class="sxs-lookup"><span data-stu-id="92618-127">Not enough memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="92618-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="92618-128">Remarks</span></span>  
 <span data-ttu-id="92618-129">Clr pobiera wskaźnik interfejsu `IHostMalloc` do wystąpienia, wywołując [IHostMemoryManager::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="92618-129">The CLR gets an interface pointer to an `IHostMalloc` instance by calling the [IHostMemoryManager::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92618-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="92618-130">Requirements</span></span>  
 <span data-ttu-id="92618-131">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92618-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92618-132">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="92618-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="92618-133">**Biblioteka:** Uwzględnione jako zasób w pliku MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="92618-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="92618-134">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92618-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92618-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="92618-135">See also</span></span>

- [<span data-ttu-id="92618-136">IHostMemoryManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="92618-136">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="92618-137">IHostMalloc, interfejs</span><span class="sxs-lookup"><span data-stu-id="92618-137">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
