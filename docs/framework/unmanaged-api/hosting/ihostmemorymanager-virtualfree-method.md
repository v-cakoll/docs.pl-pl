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
ms.openlocfilehash: b53c0bb38922ae8de048c131807eb32f97423d6c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128589"
---
# <a name="ihostmemorymanagervirtualfree-method"></a><span data-ttu-id="4dbd9-102">IHostMemoryManager::VirtualFree — Metoda</span><span class="sxs-lookup"><span data-stu-id="4dbd9-102">IHostMemoryManager::VirtualFree Method</span></span>
<span data-ttu-id="4dbd9-103">Służy jako otoka logiczna dla odpowiadającej jej funkcji Win32.</span><span class="sxs-lookup"><span data-stu-id="4dbd9-103">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="4dbd9-104">Implementacja Win32 `VirtualFree` zwalnia, decommits lub zwalnia i anuluje region stron w wirtualnej przestrzeni adresowej procesu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="4dbd9-104">The Win32 implementation of `VirtualFree` releases, decommits, or releases and decommits a region of pages within the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4dbd9-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="4dbd9-105">Syntax</span></span>  
  
```cpp  
HRESULT VirtualFree (  
    [in] LPVOID  lpAddress,  
    [in] SIZE_T  dwSize,  
    [in] DWORD   dwFreeType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4dbd9-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="4dbd9-106">Parameters</span></span>  
 `lpAddress`  
 <span data-ttu-id="4dbd9-107">podczas Wskaźnik na adres podstawowy stron pamięci wirtualnej, które mają zostać zwolnione.</span><span class="sxs-lookup"><span data-stu-id="4dbd9-107">[in] A pointer to the base address of the virtual memory pages to be freed.</span></span>  
  
 `dwSize`  
 <span data-ttu-id="4dbd9-108">podczas Rozmiar, w bajtach, regionu, który ma zostać zwolniony.</span><span class="sxs-lookup"><span data-stu-id="4dbd9-108">[in] The size, in bytes, of the region to be freed.</span></span>  
  
 `dwFreeType`  
 <span data-ttu-id="4dbd9-109">podczas Typ operacji zwalniania.</span><span class="sxs-lookup"><span data-stu-id="4dbd9-109">[in] The type of freeing operation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4dbd9-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4dbd9-110">Return Value</span></span>  
  
|<span data-ttu-id="4dbd9-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4dbd9-111">HRESULT</span></span>|<span data-ttu-id="4dbd9-112">Opis</span><span class="sxs-lookup"><span data-stu-id="4dbd9-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4dbd9-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="4dbd9-113">S_OK</span></span>|<span data-ttu-id="4dbd9-114">`VirtualFree` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="4dbd9-114">`VirtualFree` returned successfully.</span></span>|  
|<span data-ttu-id="4dbd9-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4dbd9-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4dbd9-116">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="4dbd9-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4dbd9-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4dbd9-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4dbd9-118">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="4dbd9-118">The call timed out.</span></span>|  
|<span data-ttu-id="4dbd9-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4dbd9-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4dbd9-120">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="4dbd9-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4dbd9-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4dbd9-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4dbd9-122">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="4dbd9-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4dbd9-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4dbd9-123">E_FAIL</span></span>|<span data-ttu-id="4dbd9-124">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="4dbd9-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4dbd9-125">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="4dbd9-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4dbd9-126">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="4dbd9-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="4dbd9-127">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="4dbd9-127">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="4dbd9-128">Podjęto próbę zwolnienia pamięci, która nie została przyalokowana przez hosta.</span><span class="sxs-lookup"><span data-stu-id="4dbd9-128">An attempt was made to free memory that was not allocated through the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4dbd9-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4dbd9-129">Remarks</span></span>  
 <span data-ttu-id="4dbd9-130">`VirtualFree` zwalnia strony pamięci wirtualnej skojarzone z parametrem `lpAddress` za pomocą wcześniejszego wywołania funkcji [IHostMemoryManager:: funkcja VirtualAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualalloc-method.md) .</span><span class="sxs-lookup"><span data-stu-id="4dbd9-130">`VirtualFree` frees virtual memory pages associated with the `lpAddress` parameter through an earlier call to the [IHostMemoryManager::VirtualAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualalloc-method.md) function.</span></span> <span data-ttu-id="4dbd9-131">Próby zwolnienia pamięci, która nie została przydzielono za pomocą hosta, powinny zwrócić HOST_E_INVALIDOPERATION.</span><span class="sxs-lookup"><span data-stu-id="4dbd9-131">Attempts to free memory that was not allocated through the host should return HOST_E_INVALIDOPERATION.</span></span>  
  
 <span data-ttu-id="4dbd9-132">Semantyka jest taka sama jak w przypadku implementacji Win32 `VirtualFree`.</span><span class="sxs-lookup"><span data-stu-id="4dbd9-132">The semantics are identical to those of the Win32 implementation of `VirtualFree`.</span></span> <span data-ttu-id="4dbd9-133">Aby uzyskać więcej informacji, zobacz dokumentację platformy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="4dbd9-133">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4dbd9-134">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4dbd9-134">Requirements</span></span>  
 <span data-ttu-id="4dbd9-135">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4dbd9-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4dbd9-136">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="4dbd9-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4dbd9-137">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4dbd9-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4dbd9-138">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4dbd9-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4dbd9-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4dbd9-139">See also</span></span>

- [<span data-ttu-id="4dbd9-140">IHostMemoryManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="4dbd9-140">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="4dbd9-141">IHostMalloc, interfejs</span><span class="sxs-lookup"><span data-stu-id="4dbd9-141">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
