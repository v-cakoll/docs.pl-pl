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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 194e9b73610ccb7282babf266eea2968a4f035ac
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59179130"
---
# <a name="ihostmemorymanagercreatemalloc-method"></a><span data-ttu-id="42ca9-102">IHostMemoryManager::CreateMAlloc — Metoda</span><span class="sxs-lookup"><span data-stu-id="42ca9-102">IHostMemoryManager::CreateMAlloc Method</span></span>
<span data-ttu-id="42ca9-103">Pobiera wskaźnik interfejsu do [ihostmalloc —](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) wystąpienie, które służy do wysyłania żądań alokacji ze stosu, utworzone przez hosta.</span><span class="sxs-lookup"><span data-stu-id="42ca9-103">Gets an interface pointer to an [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) instance that is used to make allocation requests from a heap created by the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42ca9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="42ca9-104">Syntax</span></span>  
  
```  
HRESULT CreateMalloc (  
    [in]  DWORD         dwMallocType,  
    [out] IHostMalloc **ppMalloc  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="42ca9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="42ca9-105">Parameters</span></span>  
 `dwMallocType`  
 <span data-ttu-id="42ca9-106">[in] Kombinacji [MALLOC_TYPE](../../../../docs/framework/unmanaged-api/hosting/malloc-type-enumeration.md) flagi, które określa cechy są przydzielonej pamięci.</span><span class="sxs-lookup"><span data-stu-id="42ca9-106">[in] A combination of [MALLOC_TYPE](../../../../docs/framework/unmanaged-api/hosting/malloc-type-enumeration.md) flags that specifies the characteristics of the memory that is being allocated.</span></span>  
  
 `ppMAlloc`  
 <span data-ttu-id="42ca9-107">[out] Wskaźnik na adres `IHostMAlloc` wystąpienia udostępniane przez hosta.</span><span class="sxs-lookup"><span data-stu-id="42ca9-107">[out] A pointer to the address of an `IHostMAlloc` instance provided by the host.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="42ca9-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="42ca9-108">Return Value</span></span>  
  
|<span data-ttu-id="42ca9-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="42ca9-109">HRESULT</span></span>|<span data-ttu-id="42ca9-110">Opis</span><span class="sxs-lookup"><span data-stu-id="42ca9-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="42ca9-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="42ca9-111">S_OK</span></span>|<span data-ttu-id="42ca9-112">`CreateMAlloc` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="42ca9-112">`CreateMAlloc` returned successfully.</span></span>|  
|<span data-ttu-id="42ca9-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="42ca9-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="42ca9-114">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="42ca9-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="42ca9-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="42ca9-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="42ca9-116">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="42ca9-116">The call timed out.</span></span>|  
|<span data-ttu-id="42ca9-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="42ca9-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="42ca9-118">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="42ca9-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="42ca9-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="42ca9-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="42ca9-120">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="42ca9-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="42ca9-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="42ca9-121">E_FAIL</span></span>|<span data-ttu-id="42ca9-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="42ca9-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="42ca9-123">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="42ca9-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="42ca9-124">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="42ca9-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="42ca9-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="42ca9-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="42ca9-126">Nie ma wystarczającej ilości pamięci fizycznej była dostępna do wykonania żądania alokacji.</span><span class="sxs-lookup"><span data-stu-id="42ca9-126">Not enough physical memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="42ca9-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="42ca9-127">Remarks</span></span>  
 <span data-ttu-id="42ca9-128">`CreateMAlloc` Zwraca obiekt, który umożliwia wysyłanie żądań alokacji za pośrednictwem hosta zamiast przy użyciu standardowych funkcji Win32 w środowisku CLR.</span><span class="sxs-lookup"><span data-stu-id="42ca9-128">`CreateMAlloc` returns an object that allows the CLR to make allocation requests through the host instead of using the standard Win32 functions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42ca9-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="42ca9-129">Requirements</span></span>  
 <span data-ttu-id="42ca9-130">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42ca9-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42ca9-131">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="42ca9-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="42ca9-132">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="42ca9-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="42ca9-133">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42ca9-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42ca9-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="42ca9-134">See also</span></span>

- [<span data-ttu-id="42ca9-135">IHostMalloc, interfejs</span><span class="sxs-lookup"><span data-stu-id="42ca9-135">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
- [<span data-ttu-id="42ca9-136">IHostMemoryManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="42ca9-136">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
