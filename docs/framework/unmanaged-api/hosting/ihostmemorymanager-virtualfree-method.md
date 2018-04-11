---
title: IHostMemoryManager::VirtualFree — Metoda
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: reference
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
caps.latest.revision: 12
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 663c01d7e4b551ecf18bdd85a63aefc43f9750e2
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/10/2018
---
# <a name="ihostmemorymanagervirtualfree-method"></a><span data-ttu-id="1bc3e-102">IHostMemoryManager::VirtualFree — Metoda</span><span class="sxs-lookup"><span data-stu-id="1bc3e-102">IHostMemoryManager::VirtualFree Method</span></span>
<span data-ttu-id="1bc3e-103">Służy jako otoka logiczne dla odpowiedniej funkcji Win32.</span><span class="sxs-lookup"><span data-stu-id="1bc3e-103">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="1bc3e-104">Implementacja Win32 `VirtualFree` zwalnia, decommits, lub zwalnia i decommits region stron w wirtualnej przestrzeni adresowej procesu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="1bc3e-104">The Win32 implementation of `VirtualFree` releases, decommits, or releases and decommits a region of pages within the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1bc3e-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="1bc3e-105">Syntax</span></span>  
  
```  
HRESULT VirtualFree (  
    [in] LPVOID  lpAddress,  
    [in] SIZE_T  dwSize,  
    [in] DWORD   dwFreeType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1bc3e-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="1bc3e-106">Parameters</span></span>  
 `lpAddress`  
 <span data-ttu-id="1bc3e-107">[in] Wskaźnik do podstawowego adresu stron pamięci wirtualnej, która ma zostać zwolniony.</span><span class="sxs-lookup"><span data-stu-id="1bc3e-107">[in] A pointer to the base address of the virtual memory pages to be freed.</span></span>  
  
 `dwSize`  
 <span data-ttu-id="1bc3e-108">[in] Rozmiar w bajtach, region, który ma zostać zwolniony.</span><span class="sxs-lookup"><span data-stu-id="1bc3e-108">[in] The size, in bytes, of the region to be freed.</span></span>  
  
 `dwFreeType`  
 <span data-ttu-id="1bc3e-109">[in] Typ zwalnianie operacji.</span><span class="sxs-lookup"><span data-stu-id="1bc3e-109">[in] The type of freeing operation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1bc3e-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1bc3e-110">Return Value</span></span>  
  
|<span data-ttu-id="1bc3e-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1bc3e-111">HRESULT</span></span>|<span data-ttu-id="1bc3e-112">Opis</span><span class="sxs-lookup"><span data-stu-id="1bc3e-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1bc3e-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="1bc3e-113">S_OK</span></span>|<span data-ttu-id="1bc3e-114">`VirtualFree` zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="1bc3e-114">`VirtualFree` returned successfully.</span></span>|  
|<span data-ttu-id="1bc3e-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1bc3e-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1bc3e-116">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="1bc3e-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1bc3e-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1bc3e-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1bc3e-118">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="1bc3e-118">The call timed out.</span></span>|  
|<span data-ttu-id="1bc3e-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1bc3e-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1bc3e-120">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="1bc3e-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1bc3e-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1bc3e-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1bc3e-122">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="1bc3e-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1bc3e-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1bc3e-123">E_FAIL</span></span>|<span data-ttu-id="1bc3e-124">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="1bc3e-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1bc3e-125">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="1bc3e-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1bc3e-126">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="1bc3e-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="1bc3e-127">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="1bc3e-127">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="1bc3e-128">Nastąpiła próba zwolnienia pamięci, która nie została przydzielona za pośrednictwem hosta.</span><span class="sxs-lookup"><span data-stu-id="1bc3e-128">An attempt was made to free memory that was not allocated through the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1bc3e-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1bc3e-129">Remarks</span></span>  
 <span data-ttu-id="1bc3e-130">`VirtualFree` zwalnia stron pamięci wirtualnej skojarzone z `lpAddress` parametru za pomocą wcześniejszych wywołania do [IHostMemoryManager::VirtualAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualalloc-method.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="1bc3e-130">`VirtualFree` frees virtual memory pages associated with the `lpAddress` parameter through an earlier call to the [IHostMemoryManager::VirtualAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualalloc-method.md) function.</span></span> <span data-ttu-id="1bc3e-131">Próbuje zwolnić pamięć, która nie została przydzielona za pośrednictwem hosta powinien zwrócić HOST_E_INVALIDOPERATION.</span><span class="sxs-lookup"><span data-stu-id="1bc3e-131">Attempts to free memory that was not allocated through the host should return HOST_E_INVALIDOPERATION.</span></span>  
  
 <span data-ttu-id="1bc3e-132">Semantyka są identyczne z implementacji Win32 `VirtualFree`.</span><span class="sxs-lookup"><span data-stu-id="1bc3e-132">The semantics are identical to those of the Win32 implementation of `VirtualFree`.</span></span> <span data-ttu-id="1bc3e-133">Aby uzyskać więcej informacji zobacz dokumentację platformy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="1bc3e-133">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1bc3e-134">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1bc3e-134">Requirements</span></span>  
 <span data-ttu-id="1bc3e-135">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1bc3e-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1bc3e-136">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1bc3e-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1bc3e-137">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1bc3e-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1bc3e-138">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1bc3e-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bc3e-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1bc3e-139">See Also</span></span>  
 [<span data-ttu-id="1bc3e-140">IHostMemoryManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="1bc3e-140">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 [<span data-ttu-id="1bc3e-141">IHostMalloc, interfejs</span><span class="sxs-lookup"><span data-stu-id="1bc3e-141">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
