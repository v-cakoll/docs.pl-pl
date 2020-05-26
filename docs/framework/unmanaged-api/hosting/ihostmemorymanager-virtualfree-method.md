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
ms.openlocfilehash: 4d37b7d803509ebfa861b7502d419f868bd12e11
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804387"
---
# <a name="ihostmemorymanagervirtualfree-method"></a><span data-ttu-id="11df0-102">IHostMemoryManager::VirtualFree — Metoda</span><span class="sxs-lookup"><span data-stu-id="11df0-102">IHostMemoryManager::VirtualFree Method</span></span>
<span data-ttu-id="11df0-103">Służy jako otoka logiczna dla odpowiadającej jej funkcji Win32.</span><span class="sxs-lookup"><span data-stu-id="11df0-103">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="11df0-104">Implementacja Win32 `VirtualFree` zwalnia, decommits lub releases i decommit region stron w wirtualnej przestrzeni adresowej procesu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="11df0-104">The Win32 implementation of `VirtualFree` releases, decommits, or releases and decommits a region of pages within the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11df0-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="11df0-105">Syntax</span></span>  
  
```cpp  
HRESULT VirtualFree (  
    [in] LPVOID  lpAddress,  
    [in] SIZE_T  dwSize,  
    [in] DWORD   dwFreeType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="11df0-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="11df0-106">Parameters</span></span>  
 `lpAddress`  
 <span data-ttu-id="11df0-107">podczas Wskaźnik na adres podstawowy stron pamięci wirtualnej, które mają zostać zwolnione.</span><span class="sxs-lookup"><span data-stu-id="11df0-107">[in] A pointer to the base address of the virtual memory pages to be freed.</span></span>  
  
 `dwSize`  
 <span data-ttu-id="11df0-108">podczas Rozmiar, w bajtach, regionu, który ma zostać zwolniony.</span><span class="sxs-lookup"><span data-stu-id="11df0-108">[in] The size, in bytes, of the region to be freed.</span></span>  
  
 `dwFreeType`  
 <span data-ttu-id="11df0-109">podczas Typ operacji zwalniania.</span><span class="sxs-lookup"><span data-stu-id="11df0-109">[in] The type of freeing operation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="11df0-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="11df0-110">Return Value</span></span>  
  
|<span data-ttu-id="11df0-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="11df0-111">HRESULT</span></span>|<span data-ttu-id="11df0-112">Opis</span><span class="sxs-lookup"><span data-stu-id="11df0-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="11df0-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="11df0-113">S_OK</span></span>|<span data-ttu-id="11df0-114">`VirtualFree`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="11df0-114">`VirtualFree` returned successfully.</span></span>|  
|<span data-ttu-id="11df0-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="11df0-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="11df0-116">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="11df0-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="11df0-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="11df0-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="11df0-118">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="11df0-118">The call timed out.</span></span>|  
|<span data-ttu-id="11df0-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="11df0-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="11df0-120">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="11df0-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="11df0-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="11df0-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="11df0-122">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="11df0-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="11df0-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="11df0-123">E_FAIL</span></span>|<span data-ttu-id="11df0-124">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="11df0-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="11df0-125">Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="11df0-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="11df0-126">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="11df0-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="11df0-127">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="11df0-127">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="11df0-128">Podjęto próbę zwolnienia pamięci, która nie została przyalokowana przez hosta.</span><span class="sxs-lookup"><span data-stu-id="11df0-128">An attempt was made to free memory that was not allocated through the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="11df0-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="11df0-129">Remarks</span></span>  
 <span data-ttu-id="11df0-130">`VirtualFree`zwalnia strony pamięci wirtualnej skojarzone z `lpAddress` parametrem za pomocą wcześniejszego wywołania funkcji [IHostMemoryManager:: funkcja VirtualAlloc](ihostmemorymanager-virtualalloc-method.md) .</span><span class="sxs-lookup"><span data-stu-id="11df0-130">`VirtualFree` frees virtual memory pages associated with the `lpAddress` parameter through an earlier call to the [IHostMemoryManager::VirtualAlloc](ihostmemorymanager-virtualalloc-method.md) function.</span></span> <span data-ttu-id="11df0-131">Próby zwolnienia pamięci, która nie została przydzielono za pomocą hosta, powinny zwrócić HOST_E_INVALIDOPERATION.</span><span class="sxs-lookup"><span data-stu-id="11df0-131">Attempts to free memory that was not allocated through the host should return HOST_E_INVALIDOPERATION.</span></span>  
  
 <span data-ttu-id="11df0-132">Semantyka jest taka sama jak w przypadku implementacji Win32 `VirtualFree` .</span><span class="sxs-lookup"><span data-stu-id="11df0-132">The semantics are identical to those of the Win32 implementation of `VirtualFree`.</span></span> <span data-ttu-id="11df0-133">Aby uzyskać więcej informacji, zobacz dokumentację platformy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="11df0-133">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11df0-134">Wymagania</span><span class="sxs-lookup"><span data-stu-id="11df0-134">Requirements</span></span>  
 <span data-ttu-id="11df0-135">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11df0-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11df0-136">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="11df0-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="11df0-137">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="11df0-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="11df0-138">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11df0-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11df0-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="11df0-139">See also</span></span>

- [<span data-ttu-id="11df0-140">IHostMemoryManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="11df0-140">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
- [<span data-ttu-id="11df0-141">IHostMalloc, interfejs</span><span class="sxs-lookup"><span data-stu-id="11df0-141">IHostMalloc Interface</span></span>](ihostmalloc-interface.md)
