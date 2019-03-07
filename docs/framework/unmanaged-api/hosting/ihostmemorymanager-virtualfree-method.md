---
title: IHostMemoryManager::VirtualFree — Metoda
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.VirtualFree
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::VirtualFree
helpviewer_keywords:
- IHostMemoryManager::VirtualFree method [.NET Framework hosting]
- VirtualFree method [.NET Framework hosting]
ms.assetid: 1a436e89-eb28-4d15-bcf1-a072f86dbd99
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: db84a45668fd4f4f1690290a96e26add05b1785e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57496342"
---
# <a name="ihostmemorymanagervirtualfree-method"></a><span data-ttu-id="24012-102">IHostMemoryManager::VirtualFree — Metoda</span><span class="sxs-lookup"><span data-stu-id="24012-102">IHostMemoryManager::VirtualFree Method</span></span>
<span data-ttu-id="24012-103">Służy jako logiczne otoki dla odpowiedniej funkcji Win32.</span><span class="sxs-lookup"><span data-stu-id="24012-103">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="24012-104">Implementacja Win32 `VirtualFree` zwalnia, anuluje, zwalnia lub anuluje region stron w wirtualnej przestrzeni adresowej procesu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="24012-104">The Win32 implementation of `VirtualFree` releases, decommits, or releases and decommits a region of pages within the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24012-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="24012-105">Syntax</span></span>  
  
```  
HRESULT VirtualFree (  
    [in] LPVOID  lpAddress,  
    [in] SIZE_T  dwSize,  
    [in] DWORD   dwFreeType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="24012-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="24012-106">Parameters</span></span>  
 `lpAddress`  
 <span data-ttu-id="24012-107">[in] Wskaźnik na adres bazowy stron pamięci wirtualnej, który ma zostać zwolniony.</span><span class="sxs-lookup"><span data-stu-id="24012-107">[in] A pointer to the base address of the virtual memory pages to be freed.</span></span>  
  
 `dwSize`  
 <span data-ttu-id="24012-108">[in] Rozmiar w bajtach, region, który ma zostać zwolniony.</span><span class="sxs-lookup"><span data-stu-id="24012-108">[in] The size, in bytes, of the region to be freed.</span></span>  
  
 `dwFreeType`  
 <span data-ttu-id="24012-109">[in] Typ zwalnianie operacji.</span><span class="sxs-lookup"><span data-stu-id="24012-109">[in] The type of freeing operation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="24012-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="24012-110">Return Value</span></span>  
  
|<span data-ttu-id="24012-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="24012-111">HRESULT</span></span>|<span data-ttu-id="24012-112">Opis</span><span class="sxs-lookup"><span data-stu-id="24012-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="24012-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="24012-113">S_OK</span></span>|<span data-ttu-id="24012-114">`VirtualFree` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="24012-114">`VirtualFree` returned successfully.</span></span>|  
|<span data-ttu-id="24012-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="24012-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="24012-116">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="24012-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="24012-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="24012-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="24012-118">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="24012-118">The call timed out.</span></span>|  
|<span data-ttu-id="24012-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="24012-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="24012-120">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="24012-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="24012-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="24012-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="24012-122">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="24012-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="24012-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="24012-123">E_FAIL</span></span>|<span data-ttu-id="24012-124">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="24012-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="24012-125">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="24012-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="24012-126">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="24012-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="24012-127">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="24012-127">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="24012-128">Nastąpiła próba, aby zwolnić pamięć, która nie została przydzielona za pośrednictwem hosta.</span><span class="sxs-lookup"><span data-stu-id="24012-128">An attempt was made to free memory that was not allocated through the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="24012-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="24012-129">Remarks</span></span>  
 <span data-ttu-id="24012-130">`VirtualFree` zwalnia strony pamięci wirtualnej skojarzone z `lpAddress` parametru za pomocą podczas wcześniejszego wywołania [ihostmemorymanager::VirtualAlloc —](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualalloc-method.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="24012-130">`VirtualFree` frees virtual memory pages associated with the `lpAddress` parameter through an earlier call to the [IHostMemoryManager::VirtualAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualalloc-method.md) function.</span></span> <span data-ttu-id="24012-131">Próbuje zwolnić pamięć, która nie została przydzielona za pośrednictwem hosta powinien zwrócić HOST_E_INVALIDOPERATION.</span><span class="sxs-lookup"><span data-stu-id="24012-131">Attempts to free memory that was not allocated through the host should return HOST_E_INVALIDOPERATION.</span></span>  
  
 <span data-ttu-id="24012-132">Semantyka są identyczne z tymi wdrożenia Win32 `VirtualFree`.</span><span class="sxs-lookup"><span data-stu-id="24012-132">The semantics are identical to those of the Win32 implementation of `VirtualFree`.</span></span> <span data-ttu-id="24012-133">Aby uzyskać więcej informacji zobacz dokumentację platformy Windows.</span><span class="sxs-lookup"><span data-stu-id="24012-133">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24012-134">Wymagania</span><span class="sxs-lookup"><span data-stu-id="24012-134">Requirements</span></span>  
 <span data-ttu-id="24012-135">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="24012-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24012-136">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="24012-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="24012-137">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="24012-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="24012-138">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24012-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24012-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="24012-139">See also</span></span>
- [<span data-ttu-id="24012-140">IHostMemoryManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="24012-140">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="24012-141">IHostMalloc, interfejs</span><span class="sxs-lookup"><span data-stu-id="24012-141">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
