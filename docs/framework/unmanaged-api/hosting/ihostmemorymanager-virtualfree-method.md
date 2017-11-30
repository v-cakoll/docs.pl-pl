---
title: "IHostMemoryManager::VirtualFree — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostMemoryManager.VirtualFree
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostMemoryManager::VirtualFree
helpviewer_keywords:
- IHostMemoryManager::VirtualFree method [.NET Framework hosting]
- VirtualFree method [.NET Framework hosting]
ms.assetid: 1a436e89-eb28-4d15-bcf1-a072f86dbd99
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 468228101403c7ce3c123401e906e3ccbe301e28
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ihostmemorymanagervirtualfree-method"></a><span data-ttu-id="40ee6-102">IHostMemoryManager::VirtualFree — Metoda</span><span class="sxs-lookup"><span data-stu-id="40ee6-102">IHostMemoryManager::VirtualFree Method</span></span>
<span data-ttu-id="40ee6-103">Służy jako otoka logiczne dla odpowiedniej funkcji Win32.</span><span class="sxs-lookup"><span data-stu-id="40ee6-103">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="40ee6-104">Implementacja Win32 `VirtualFree` zwalnia, decommits, lub zwalnia i decommits region stron w wirtualnej przestrzeni adresowej procesu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="40ee6-104">The Win32 implementation of `VirtualFree` releases, decommits, or releases and decommits a region of pages within the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40ee6-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="40ee6-105">Syntax</span></span>  
  
```  
HRESULT VirtualFree (  
    [in] LPVOID  lpAddress,  
    [in] SIZE_T  dwSize,  
    [in] DWORD   dwFreeType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="40ee6-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="40ee6-106">Parameters</span></span>  
 `lpAddress`  
 <span data-ttu-id="40ee6-107">[in] Wskaźnik do podstawowego adresu stron pamięci wirtualnej, która ma zostać zwolniony.</span><span class="sxs-lookup"><span data-stu-id="40ee6-107">[in] A pointer to the base address of the virtual memory pages to be freed.</span></span>  
  
 `dwSize`  
 <span data-ttu-id="40ee6-108">[in] Rozmiar w bajtach, region, który ma zostać zwolniony.</span><span class="sxs-lookup"><span data-stu-id="40ee6-108">[in] The size, in bytes, of the region to be freed.</span></span>  
  
 `dwFreeType`  
 <span data-ttu-id="40ee6-109">[in] Typ zwalnianie operacji.</span><span class="sxs-lookup"><span data-stu-id="40ee6-109">[in] The type of freeing operation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="40ee6-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="40ee6-110">Return Value</span></span>  
  
|<span data-ttu-id="40ee6-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="40ee6-111">HRESULT</span></span>|<span data-ttu-id="40ee6-112">Opis</span><span class="sxs-lookup"><span data-stu-id="40ee6-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="40ee6-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="40ee6-113">S_OK</span></span>|<span data-ttu-id="40ee6-114">`VirtualFree`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="40ee6-114">`VirtualFree` returned successfully.</span></span>|  
|<span data-ttu-id="40ee6-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="40ee6-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="40ee6-116">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="40ee6-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="40ee6-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="40ee6-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="40ee6-118">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="40ee6-118">The call timed out.</span></span>|  
|<span data-ttu-id="40ee6-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="40ee6-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="40ee6-120">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="40ee6-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="40ee6-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="40ee6-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="40ee6-122">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="40ee6-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="40ee6-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="40ee6-123">E_FAIL</span></span>|<span data-ttu-id="40ee6-124">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="40ee6-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="40ee6-125">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="40ee6-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="40ee6-126">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="40ee6-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="40ee6-127">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="40ee6-127">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="40ee6-128">Nastąpiła próba zwolnienia pamięci, która nie została przydzielona za pośrednictwem hosta.</span><span class="sxs-lookup"><span data-stu-id="40ee6-128">An attempt was made to free memory that was not allocated through the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="40ee6-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="40ee6-129">Remarks</span></span>  
 <span data-ttu-id="40ee6-130">`VirtualFree`zwalnia stron pamięci wirtualnej skojarzone z `lpAddress` parametru za pomocą wcześniejszych wywołania do [IHostMemoryManager::VirtualAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualalloc-method.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="40ee6-130">`VirtualFree` frees virtual memory pages associated with the `lpAddress` parameter through an earlier call to the [IHostMemoryManager::VirtualAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualalloc-method.md) function.</span></span> <span data-ttu-id="40ee6-131">Próbuje zwolnić pamięć, która nie została przydzielona za pośrednictwem hosta powinien zwrócić HOST_E_INVALIDOPERATION.</span><span class="sxs-lookup"><span data-stu-id="40ee6-131">Attempts to free memory that was not allocated through the host should return HOST_E_INVALIDOPERATION.</span></span>  
  
 <span data-ttu-id="40ee6-132">Semantyka są identyczne z implementacji Win32 `VirtualFree`.</span><span class="sxs-lookup"><span data-stu-id="40ee6-132">The semantics are identical to those of the Win32 implementation of `VirtualFree`.</span></span> <span data-ttu-id="40ee6-133">Aby uzyskać więcej informacji zobacz dokumentację platformy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="40ee6-133">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40ee6-134">Wymagania</span><span class="sxs-lookup"><span data-stu-id="40ee6-134">Requirements</span></span>  
 <span data-ttu-id="40ee6-135">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40ee6-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40ee6-136">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="40ee6-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="40ee6-137">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="40ee6-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="40ee6-138">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40ee6-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40ee6-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="40ee6-139">See Also</span></span>  
 [<span data-ttu-id="40ee6-140">IHostMemoryManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="40ee6-140">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 [<span data-ttu-id="40ee6-141">IHostMalloc — interfejs</span><span class="sxs-lookup"><span data-stu-id="40ee6-141">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
