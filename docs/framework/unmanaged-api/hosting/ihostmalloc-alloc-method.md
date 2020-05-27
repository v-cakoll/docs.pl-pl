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
ms.openlocfilehash: 6f58e2290afa166d48306c0bbb50edd1df36888b
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804646"
---
# <a name="ihostmallocalloc-method"></a><span data-ttu-id="2ffb8-102">IHostMAlloc::Alloc — Metoda</span><span class="sxs-lookup"><span data-stu-id="2ffb8-102">IHostMAlloc::Alloc Method</span></span>
<span data-ttu-id="2ffb8-103">Żąda od sterty przydzielenia przez hosta określonej ilości pamięci.</span><span class="sxs-lookup"><span data-stu-id="2ffb8-103">Requests that the host allocate the specified amount of memory from the heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ffb8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2ffb8-104">Syntax</span></span>  
  
```cpp  
HRESULT Alloc (  
    [in] SIZE_T  cbSize,
    [in] EMemoryCriticalLevel dwCriticalLevel,
    [out] void** ppMem  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2ffb8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2ffb8-105">Parameters</span></span>  
 `cbSize`  
 <span data-ttu-id="2ffb8-106">podczas Rozmiar (w bajtach) bieżącego żądania alokacji pamięci.</span><span class="sxs-lookup"><span data-stu-id="2ffb8-106">[in] The size, in bytes, of the current memory allocation request.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="2ffb8-107">podczas Jedna z wartości [EMemoryCriticalLevel —](ememorycriticallevel-enumeration.md) , co wskazuje na wpływ błędu alokacji.</span><span class="sxs-lookup"><span data-stu-id="2ffb8-107">[in] One of the [EMemoryCriticalLevel](ememorycriticallevel-enumeration.md) values, indicating the impact of an allocation failure.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="2ffb8-108">określoną Wskaźnik do przydzieloną pamięci lub wartość null, jeśli nie można ukończyć żądania.</span><span class="sxs-lookup"><span data-stu-id="2ffb8-108">[out] A pointer to the allocated memory, or null if the request could not be completed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2ffb8-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="2ffb8-109">Return Value</span></span>  
  
|<span data-ttu-id="2ffb8-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2ffb8-110">HRESULT</span></span>|<span data-ttu-id="2ffb8-111">Opis</span><span class="sxs-lookup"><span data-stu-id="2ffb8-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2ffb8-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="2ffb8-112">S_OK</span></span>|<span data-ttu-id="2ffb8-113">`Alloc`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="2ffb8-113">`Alloc` returned successfully.</span></span>|  
|<span data-ttu-id="2ffb8-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2ffb8-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2ffb8-115">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="2ffb8-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2ffb8-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2ffb8-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2ffb8-117">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="2ffb8-117">The call timed out.</span></span>|  
|<span data-ttu-id="2ffb8-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2ffb8-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2ffb8-119">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="2ffb8-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2ffb8-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2ffb8-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2ffb8-121">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="2ffb8-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2ffb8-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2ffb8-122">E_FAIL</span></span>|<span data-ttu-id="2ffb8-123">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="2ffb8-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2ffb8-124">Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="2ffb8-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2ffb8-125">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="2ffb8-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="2ffb8-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="2ffb8-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="2ffb8-127">Za mało dostępnej pamięci, aby ukończyć żądanie alokacji.</span><span class="sxs-lookup"><span data-stu-id="2ffb8-127">Not enough memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2ffb8-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2ffb8-128">Remarks</span></span>  
 <span data-ttu-id="2ffb8-129">Środowisko CLR Pobiera wskaźnik interfejsu do `IHostMalloc` wystąpienia, wywołując metodę [IHostMemoryManager::](ihostmemorymanager-createmalloc-method.md) CreateInstance.</span><span class="sxs-lookup"><span data-stu-id="2ffb8-129">The CLR gets an interface pointer to an `IHostMalloc` instance by calling the [IHostMemoryManager::CreateMalloc](ihostmemorymanager-createmalloc-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ffb8-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2ffb8-130">Requirements</span></span>  
 <span data-ttu-id="2ffb8-131">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ffb8-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ffb8-132">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2ffb8-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2ffb8-133">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2ffb8-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2ffb8-134">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ffb8-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ffb8-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2ffb8-135">See also</span></span>

- [<span data-ttu-id="2ffb8-136">IHostMemoryManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="2ffb8-136">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
- [<span data-ttu-id="2ffb8-137">IHostMalloc, interfejs</span><span class="sxs-lookup"><span data-stu-id="2ffb8-137">IHostMalloc Interface</span></span>](ihostmalloc-interface.md)
