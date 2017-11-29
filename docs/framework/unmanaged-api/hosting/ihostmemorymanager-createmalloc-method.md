---
title: "IHostMemoryManager::CreateMAlloc — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostMemoryManager.CreateMAlloc
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostMemoryManager::CreateMAlloc
helpviewer_keywords:
- CreateAlloc method [.NET Framework hosting]
- IHostMemoryManager::CreateMAlloc method [.NET Framework hosting]
ms.assetid: 9ee6e052-bef7-4350-9e4f-edfffd99ad6f
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 25b4f8a23d03b3d839aeab5d2f571cb4f98f1ec5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ihostmemorymanagercreatemalloc-method"></a><span data-ttu-id="c27fb-102">IHostMemoryManager::CreateMAlloc — Metoda</span><span class="sxs-lookup"><span data-stu-id="c27fb-102">IHostMemoryManager::CreateMAlloc Method</span></span>
<span data-ttu-id="c27fb-103">Pobiera wskaźnika interfejsu do [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) wystąpienie, które jest używane do obliczania żądań alokacji sterty utworzone przez hosta.</span><span class="sxs-lookup"><span data-stu-id="c27fb-103">Gets an interface pointer to an [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) instance that is used to make allocation requests from a heap created by the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c27fb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c27fb-104">Syntax</span></span>  
  
```  
HRESULT CreateMalloc (  
    [in]  DWORD         dwMallocType,  
    [out] IHostMalloc **ppMalloc  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c27fb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c27fb-105">Parameters</span></span>  
 `dwMallocType`  
 <span data-ttu-id="c27fb-106">[in] Kombinację [malloc_type —](../../../../docs/framework/unmanaged-api/hosting/malloc-type-enumeration.md) flagi, które określa charakterystykę pamięci, która jest przydzielane.</span><span class="sxs-lookup"><span data-stu-id="c27fb-106">[in] A combination of [MALLOC_TYPE](../../../../docs/framework/unmanaged-api/hosting/malloc-type-enumeration.md) flags that specifies the characteristics of the memory that is being allocated.</span></span>  
  
 `ppMAlloc`  
 <span data-ttu-id="c27fb-107">[out] Wskaźnik do adresu `IHostMAlloc` wystąpienia dostarczony przez hosta.</span><span class="sxs-lookup"><span data-stu-id="c27fb-107">[out] A pointer to the address of an `IHostMAlloc` instance provided by the host.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c27fb-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="c27fb-108">Return Value</span></span>  
  
|<span data-ttu-id="c27fb-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c27fb-109">HRESULT</span></span>|<span data-ttu-id="c27fb-110">Opis</span><span class="sxs-lookup"><span data-stu-id="c27fb-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c27fb-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="c27fb-111">S_OK</span></span>|<span data-ttu-id="c27fb-112">`CreateMAlloc`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="c27fb-112">`CreateMAlloc` returned successfully.</span></span>|  
|<span data-ttu-id="c27fb-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c27fb-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c27fb-114">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="c27fb-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c27fb-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c27fb-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c27fb-116">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="c27fb-116">The call timed out.</span></span>|  
|<span data-ttu-id="c27fb-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c27fb-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c27fb-118">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="c27fb-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c27fb-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c27fb-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c27fb-120">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="c27fb-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c27fb-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c27fb-121">E_FAIL</span></span>|<span data-ttu-id="c27fb-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="c27fb-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c27fb-123">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="c27fb-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c27fb-124">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c27fb-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="c27fb-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="c27fb-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="c27fb-126">Nie ma wystarczającej ilości pamięci fizycznej nie była dostępna do wykonania żądania alokacji.</span><span class="sxs-lookup"><span data-stu-id="c27fb-126">Not enough physical memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c27fb-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c27fb-127">Remarks</span></span>  
 <span data-ttu-id="c27fb-128">`CreateMAlloc`Zwraca obiekt, który umożliwia CLR na wysyłanie żądań alokacji za pośrednictwem hosta zamiast przy użyciu standardowych funkcji Win32.</span><span class="sxs-lookup"><span data-stu-id="c27fb-128">`CreateMAlloc` returns an object that allows the CLR to make allocation requests through the host instead of using the standard Win32 functions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c27fb-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c27fb-129">Requirements</span></span>  
 <span data-ttu-id="c27fb-130">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c27fb-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c27fb-131">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c27fb-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c27fb-132">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c27fb-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c27fb-133">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c27fb-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c27fb-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c27fb-134">See Also</span></span>  
 [<span data-ttu-id="c27fb-135">IHostMalloc — interfejs</span><span class="sxs-lookup"><span data-stu-id="c27fb-135">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)  
 [<span data-ttu-id="c27fb-136">IHostMemoryManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="c27fb-136">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
