---
title: IHostMemoryManager::VirtualAlloc — Metoda
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.VirtualAlloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::VirtualAlloc
helpviewer_keywords:
- VirtualAlloc method [.NET Framework hosting]
- IHostMemoryManager::VirtualAlloc method [.NET Framework hosting]
ms.assetid: 4dff3646-a050-4bd9-ac31-fe307e8637ec
topic_type:
- apiref
ms.openlocfilehash: de41b5e0aaf835ee2d4e4f32696fe104d5830b57
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804450"
---
# <a name="ihostmemorymanagervirtualalloc-method"></a><span data-ttu-id="3609e-102">IHostMemoryManager::VirtualAlloc — Metoda</span><span class="sxs-lookup"><span data-stu-id="3609e-102">IHostMemoryManager::VirtualAlloc Method</span></span>
<span data-ttu-id="3609e-103">Służy jako otoka logiczna dla odpowiadającej jej funkcji Win32.</span><span class="sxs-lookup"><span data-stu-id="3609e-103">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="3609e-104">Implementacja Win32 `VirtualAlloc` rezerwuje lub zatwierdza region stron w wirtualnej przestrzeni adresowej procesu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="3609e-104">The Win32 implementation of `VirtualAlloc` reserves or commits a region of pages in the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3609e-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="3609e-105">Syntax</span></span>  
  
```cpp  
HRESULT VirtualAlloc (  
    [in]  void*   pAddress,  
    [in]  SIZE_T  dwSize,  
    [in]  DWORD   flAllocationType,  
    [in]  DWORD   flProtect,  
    [in]  EMemoryCriticalLevel dwCriticalLevel,  
    [out] void**  ppMem  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3609e-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="3609e-106">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="3609e-107">podczas Wskaźnik do adresu początkowego regionu do przydzielenia.</span><span class="sxs-lookup"><span data-stu-id="3609e-107">[in] A pointer to the starting address of the region to allocate.</span></span>  
  
 `dwSize`  
 <span data-ttu-id="3609e-108">podczas Rozmiar, w bajtach, regionu.</span><span class="sxs-lookup"><span data-stu-id="3609e-108">[in] The size, in bytes, of the region.</span></span>  
  
 `flAllocationType`  
 <span data-ttu-id="3609e-109">podczas Typ alokacji pamięci.</span><span class="sxs-lookup"><span data-stu-id="3609e-109">[in] The type of memory allocation.</span></span>  
  
 `flProtect`  
 <span data-ttu-id="3609e-110">podczas Ochrona pamięci dla regionu stron do przydzielenia.</span><span class="sxs-lookup"><span data-stu-id="3609e-110">[in] Memory protection for the region of pages to be allocated.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="3609e-111">podczas Wartość [EMemoryCriticalLevel —](ememorycriticallevel-enumeration.md) , która wskazuje wpływ błędu alokacji.</span><span class="sxs-lookup"><span data-stu-id="3609e-111">[in] An [EMemoryCriticalLevel](ememorycriticallevel-enumeration.md) value that indicates the impact of an allocation failure.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="3609e-112">określoną Wskaźnik na adres początkowy przydzieloną pamięć lub wartość null, jeśli nie można spełnić żądania.</span><span class="sxs-lookup"><span data-stu-id="3609e-112">[out] Pointer to the starting address of the allocated memory, or null if the request could not be satisfied.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3609e-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="3609e-113">Return Value</span></span>  
  
|<span data-ttu-id="3609e-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3609e-114">HRESULT</span></span>|<span data-ttu-id="3609e-115">Opis</span><span class="sxs-lookup"><span data-stu-id="3609e-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3609e-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="3609e-116">S_OK</span></span>|<span data-ttu-id="3609e-117">`VirtualAlloc`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="3609e-117">`VirtualAlloc` returned successfully.</span></span>|  
|<span data-ttu-id="3609e-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3609e-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3609e-119">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="3609e-119">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3609e-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3609e-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3609e-121">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="3609e-121">The call timed out.</span></span>|  
|<span data-ttu-id="3609e-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3609e-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3609e-123">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="3609e-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3609e-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3609e-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3609e-125">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="3609e-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3609e-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3609e-126">E_FAIL</span></span>|<span data-ttu-id="3609e-127">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="3609e-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3609e-128">Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="3609e-128">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3609e-129">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="3609e-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="3609e-130">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="3609e-130">E_OUTOFMEMORY</span></span>|<span data-ttu-id="3609e-131">Za mało dostępnej pamięci, aby ukończyć żądanie alokacji</span><span class="sxs-lookup"><span data-stu-id="3609e-131">Not enough memory was available to complete the allocation request</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3609e-132">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3609e-132">Remarks</span></span>  
 <span data-ttu-id="3609e-133">Zarezerwuj region w przestrzeni adresowej procesu przez wywołanie `VirtualAlloc` .</span><span class="sxs-lookup"><span data-stu-id="3609e-133">You reserve a region in the address space of your process by calling `VirtualAlloc`.</span></span> <span data-ttu-id="3609e-134">`pAddress`Parametr zawiera początkowy adres żądanego bloku pamięci.</span><span class="sxs-lookup"><span data-stu-id="3609e-134">The `pAddress` parameter contains the beginning address of the memory block you want.</span></span> <span data-ttu-id="3609e-135">Ten parametr ma zazwyczaj wartość null.</span><span class="sxs-lookup"><span data-stu-id="3609e-135">This parameter is typically set to null.</span></span> <span data-ttu-id="3609e-136">System operacyjny przechowuje rekord bezpłatnych zakresów adresów dostępnych dla danego procesu.</span><span class="sxs-lookup"><span data-stu-id="3609e-136">The operating system keeps a record of free address ranges available to your process.</span></span> <span data-ttu-id="3609e-137">`pAddress`Wartość null powoduje, że system rezerwuje region wszędzie tam, gdzie jest to zgodne.</span><span class="sxs-lookup"><span data-stu-id="3609e-137">A `pAddress` value of null instructs the system to reserve the region wherever it sees fit.</span></span> <span data-ttu-id="3609e-138">Alternatywnie można podać konkretny adres początkowy bloku pamięci.</span><span class="sxs-lookup"><span data-stu-id="3609e-138">Alternatively, you can provide a specific starting address for the memory block.</span></span> <span data-ttu-id="3609e-139">W obu przypadkach parametr wyjściowy `ppMem` jest zwracany jako wskaźnik do przydzieloną pamięci.</span><span class="sxs-lookup"><span data-stu-id="3609e-139">In both cases, the output parameter `ppMem` is returned as a pointer to the allocated memory.</span></span> <span data-ttu-id="3609e-140">Sama funkcja zwraca wartość HRESULT.</span><span class="sxs-lookup"><span data-stu-id="3609e-140">The function itself returns an HRESULT value.</span></span>  
  
 <span data-ttu-id="3609e-141">Funkcja Win32 nie `VirtualAlloc` ma `ppMem` parametru i zwraca zamiast niego wskaźnik do przydzieloną pamięci.</span><span class="sxs-lookup"><span data-stu-id="3609e-141">The Win32 `VirtualAlloc` function does not have a `ppMem` parameter, and returns the pointer to the allocated memory instead.</span></span> <span data-ttu-id="3609e-142">Aby uzyskać więcej informacji, zobacz dokumentację platformy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="3609e-142">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3609e-143">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3609e-143">Requirements</span></span>  
 <span data-ttu-id="3609e-144">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3609e-144">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3609e-145">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="3609e-145">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3609e-146">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="3609e-146">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3609e-147">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3609e-147">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3609e-148">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3609e-148">See also</span></span>

- [<span data-ttu-id="3609e-149">IHostMemoryManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="3609e-149">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
