---
title: "IHostMemoryManager::VirtualAlloc — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostMemoryManager.VirtualAlloc
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostMemoryManager::VirtualAlloc
helpviewer_keywords:
- VirtualAlloc method [.NET Framework hosting]
- IHostMemoryManager::VirtualAlloc method [.NET Framework hosting]
ms.assetid: 4dff3646-a050-4bd9-ac31-fe307e8637ec
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 761958c44ad374d522a52826929e320e65957ffa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ihostmemorymanagervirtualalloc-method"></a><span data-ttu-id="41fe4-102">IHostMemoryManager::VirtualAlloc — Metoda</span><span class="sxs-lookup"><span data-stu-id="41fe4-102">IHostMemoryManager::VirtualAlloc Method</span></span>
<span data-ttu-id="41fe4-103">Służy jako otoka logiczne dla odpowiedniej funkcji Win32.</span><span class="sxs-lookup"><span data-stu-id="41fe4-103">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="41fe4-104">Implementacja Win32 `VirtualAlloc` rezerwuje lub zatwierdza region stron w wirtualnej przestrzeni adresowej procesu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="41fe4-104">The Win32 implementation of `VirtualAlloc` reserves or commits a region of pages in the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41fe4-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="41fe4-105">Syntax</span></span>  
  
```  
HRESULT VirtualAlloc (  
    [in]  void*   pAddress,  
    [in]  SIZE_T  dwSize,  
    [in]  DWORD   flAllocationType,  
    [in]  DWORD   flProtect,  
    [in]  EMemoryCriticalLevel dwCriticalLevel,  
    [out] void**  ppMem  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="41fe4-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="41fe4-106">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="41fe4-107">[in] Wskaźnik do regionu przydzielić adres początkowy.</span><span class="sxs-lookup"><span data-stu-id="41fe4-107">[in] A pointer to the starting address of the region to allocate.</span></span>  
  
 `dwSize`  
 <span data-ttu-id="41fe4-108">[in] Rozmiar w bajtach regionu.</span><span class="sxs-lookup"><span data-stu-id="41fe4-108">[in] The size, in bytes, of the region.</span></span>  
  
 `flAllocationType`  
 <span data-ttu-id="41fe4-109">[in] Typ alokacji pamięci.</span><span class="sxs-lookup"><span data-stu-id="41fe4-109">[in] The type of memory allocation.</span></span>  
  
 `flProtect`  
 <span data-ttu-id="41fe4-110">[in] Ochrona pamięci dla regionu stron do przydzielenia.</span><span class="sxs-lookup"><span data-stu-id="41fe4-110">[in] Memory protection for the region of pages to be allocated.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="41fe4-111">[in] [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) wartość, która wskazuje wpływ błąd alokacji.</span><span class="sxs-lookup"><span data-stu-id="41fe4-111">[in] An [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) value that indicates the impact of an allocation failure.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="41fe4-112">[out] Wskaźnik do adres początkowy alokacji pamięci lub wartość null, jeśli nie można spełnić żądania.</span><span class="sxs-lookup"><span data-stu-id="41fe4-112">[out] Pointer to the starting address of the allocated memory, or null if the request could not be satisfied.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="41fe4-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="41fe4-113">Return Value</span></span>  
  
|<span data-ttu-id="41fe4-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="41fe4-114">HRESULT</span></span>|<span data-ttu-id="41fe4-115">Opis</span><span class="sxs-lookup"><span data-stu-id="41fe4-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="41fe4-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="41fe4-116">S_OK</span></span>|<span data-ttu-id="41fe4-117">`VirtualAlloc`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="41fe4-117">`VirtualAlloc` returned successfully.</span></span>|  
|<span data-ttu-id="41fe4-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="41fe4-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="41fe4-119">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="41fe4-119">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="41fe4-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="41fe4-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="41fe4-121">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="41fe4-121">The call timed out.</span></span>|  
|<span data-ttu-id="41fe4-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="41fe4-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="41fe4-123">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="41fe4-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="41fe4-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="41fe4-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="41fe4-125">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="41fe4-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="41fe4-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="41fe4-126">E_FAIL</span></span>|<span data-ttu-id="41fe4-127">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="41fe4-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="41fe4-128">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="41fe4-128">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="41fe4-129">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="41fe4-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="41fe4-130">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="41fe4-130">E_OUTOFMEMORY</span></span>|<span data-ttu-id="41fe4-131">Za mało pamięci był dostępny do wykonania żądania alokacji</span><span class="sxs-lookup"><span data-stu-id="41fe4-131">Not enough memory was available to complete the allocation request</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="41fe4-132">Uwagi</span><span class="sxs-lookup"><span data-stu-id="41fe4-132">Remarks</span></span>  
 <span data-ttu-id="41fe4-133">Zarezerwować region przestrzeni adresowej procesu, wywołując `VirtualAlloc`.</span><span class="sxs-lookup"><span data-stu-id="41fe4-133">You reserve a region in the address space of your process by calling `VirtualAlloc`.</span></span> <span data-ttu-id="41fe4-134">`pAddress` Parametr zawiera początkowy adres ma bloku pamięci.</span><span class="sxs-lookup"><span data-stu-id="41fe4-134">The `pAddress` parameter contains the beginning address of the memory block you want.</span></span> <span data-ttu-id="41fe4-135">Ten parametr jest zwykle ustawiana na wartość null.</span><span class="sxs-lookup"><span data-stu-id="41fe4-135">This parameter is typically set to null.</span></span> <span data-ttu-id="41fe4-136">System operacyjny jest rejestrowana zakresy wolnego adresu dostępne dla procesu.</span><span class="sxs-lookup"><span data-stu-id="41fe4-136">The operating system keeps a record of free address ranges available to your process.</span></span> <span data-ttu-id="41fe4-137">A `pAddress` wartość null powoduje, że system do zarezerwowania region wszędzie tam, gdzie za stosowny.</span><span class="sxs-lookup"><span data-stu-id="41fe4-137">A `pAddress` value of null instructs the system to reserve the region wherever it sees fit.</span></span> <span data-ttu-id="41fe4-138">Alternatywnie możesz podać określony adres początkowy dla bloku pamięci.</span><span class="sxs-lookup"><span data-stu-id="41fe4-138">Alternatively, you can provide a specific starting address for the memory block.</span></span> <span data-ttu-id="41fe4-139">W obu przypadkach parametr wyjściowy `ppMem` jest zwracana jako wskaźnik do alokacji pamięci.</span><span class="sxs-lookup"><span data-stu-id="41fe4-139">In both cases, the output parameter `ppMem` is returned as a pointer to the allocated memory.</span></span> <span data-ttu-id="41fe4-140">Ta funkcja zwraca wartość HRESULT.</span><span class="sxs-lookup"><span data-stu-id="41fe4-140">The function itself returns an HRESULT value.</span></span>  
  
 <span data-ttu-id="41fe4-141">Win32 `VirtualAlloc` funkcja nie ma `ppMem` parametr, a zamiast tego zwraca wskaźnik do alokacji pamięci.</span><span class="sxs-lookup"><span data-stu-id="41fe4-141">The Win32 `VirtualAlloc` function does not have a `ppMem` parameter, and returns the pointer to the allocated memory instead.</span></span> <span data-ttu-id="41fe4-142">Aby uzyskać więcej informacji zobacz dokumentację platformy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="41fe4-142">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41fe4-143">Wymagania</span><span class="sxs-lookup"><span data-stu-id="41fe4-143">Requirements</span></span>  
 <span data-ttu-id="41fe4-144">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41fe4-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41fe4-145">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="41fe4-145">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="41fe4-146">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="41fe4-146">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="41fe4-147">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41fe4-147">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41fe4-148">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="41fe4-148">See Also</span></span>  
 [<span data-ttu-id="41fe4-149">IHostMemoryManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="41fe4-149">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
