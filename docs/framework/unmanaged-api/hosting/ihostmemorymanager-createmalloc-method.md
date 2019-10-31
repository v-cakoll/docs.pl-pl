---
title: IHostMemoryManager::CreateMAlloc — Metoda
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.CreateMAlloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::CreateMAlloc
helpviewer_keywords:
- CreateAlloc method [.NET Framework hosting]
- IHostMemoryManager::CreateMAlloc method [.NET Framework hosting]
ms.assetid: 9ee6e052-bef7-4350-9e4f-edfffd99ad6f
topic_type:
- apiref
ms.openlocfilehash: 8bcb01f4a19e6043bd59fe6f1565cdf35ed1f77c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136725"
---
# <a name="ihostmemorymanagercreatemalloc-method"></a><span data-ttu-id="4849b-102">IHostMemoryManager::CreateMAlloc — Metoda</span><span class="sxs-lookup"><span data-stu-id="4849b-102">IHostMemoryManager::CreateMAlloc Method</span></span>
<span data-ttu-id="4849b-103">Pobiera wskaźnik interfejsu do wystąpienia [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) , które jest używane do tworzenia żądań alokacji ze sterty utworzonej przez hosta.</span><span class="sxs-lookup"><span data-stu-id="4849b-103">Gets an interface pointer to an [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) instance that is used to make allocation requests from a heap created by the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4849b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4849b-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateMalloc (  
    [in]  DWORD         dwMallocType,  
    [out] IHostMalloc **ppMalloc  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4849b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4849b-105">Parameters</span></span>  
 `dwMallocType`  
 <span data-ttu-id="4849b-106">podczas Kombinacja flag [MALLOC_TYPE](../../../../docs/framework/unmanaged-api/hosting/malloc-type-enumeration.md) , która określa charakterystykę przydzielenia pamięci.</span><span class="sxs-lookup"><span data-stu-id="4849b-106">[in] A combination of [MALLOC_TYPE](../../../../docs/framework/unmanaged-api/hosting/malloc-type-enumeration.md) flags that specifies the characteristics of the memory that is being allocated.</span></span>  
  
 `ppMAlloc`  
 <span data-ttu-id="4849b-107">określoną Wskaźnik do adresu `IHostMAlloc` wystąpienia dostarczonego przez hosta.</span><span class="sxs-lookup"><span data-stu-id="4849b-107">[out] A pointer to the address of an `IHostMAlloc` instance provided by the host.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4849b-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4849b-108">Return Value</span></span>  
  
|<span data-ttu-id="4849b-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4849b-109">HRESULT</span></span>|<span data-ttu-id="4849b-110">Opis</span><span class="sxs-lookup"><span data-stu-id="4849b-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4849b-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="4849b-111">S_OK</span></span>|<span data-ttu-id="4849b-112">`CreateMAlloc` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="4849b-112">`CreateMAlloc` returned successfully.</span></span>|  
|<span data-ttu-id="4849b-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4849b-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4849b-114">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="4849b-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4849b-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4849b-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4849b-116">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="4849b-116">The call timed out.</span></span>|  
|<span data-ttu-id="4849b-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4849b-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4849b-118">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="4849b-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4849b-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4849b-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4849b-120">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="4849b-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4849b-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4849b-121">E_FAIL</span></span>|<span data-ttu-id="4849b-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="4849b-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4849b-123">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="4849b-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4849b-124">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="4849b-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="4849b-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="4849b-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="4849b-126">Za mało dostępnej pamięci fizycznej, aby ukończyć żądanie alokacji.</span><span class="sxs-lookup"><span data-stu-id="4849b-126">Not enough physical memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4849b-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4849b-127">Remarks</span></span>  
 <span data-ttu-id="4849b-128">`CreateMAlloc` zwraca obiekt, który umożliwia CLR wykonywanie żądań alokacji za pośrednictwem hosta zamiast korzystania ze standardowych funkcji Win32.</span><span class="sxs-lookup"><span data-stu-id="4849b-128">`CreateMAlloc` returns an object that allows the CLR to make allocation requests through the host instead of using the standard Win32 functions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4849b-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4849b-129">Requirements</span></span>  
 <span data-ttu-id="4849b-130">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4849b-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4849b-131">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="4849b-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4849b-132">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4849b-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4849b-133">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4849b-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4849b-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4849b-134">See also</span></span>

- [<span data-ttu-id="4849b-135">IHostMalloc, interfejs</span><span class="sxs-lookup"><span data-stu-id="4849b-135">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
- [<span data-ttu-id="4849b-136">IHostMemoryManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="4849b-136">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
