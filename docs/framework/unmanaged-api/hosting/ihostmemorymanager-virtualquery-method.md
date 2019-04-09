---
title: IHostMemoryManager::VirtualQuery — Metoda
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.VirtualQuery
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::VirtualQuery
helpviewer_keywords:
- IHostMemoryManager::VirtualQuery method [.NET Framework hosting]
- VirtualQuery method [.NET Framework hosting]
ms.assetid: 757af1e6-b9e8-49e7-b5db-342be3aa205f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 028ca0b9cb917d3e6cc0242cbc8c3f4a5a19ab39
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59199625"
---
# <a name="ihostmemorymanagervirtualquery-method"></a><span data-ttu-id="c15c9-102">IHostMemoryManager::VirtualQuery — Metoda</span><span class="sxs-lookup"><span data-stu-id="c15c9-102">IHostMemoryManager::VirtualQuery Method</span></span>
<span data-ttu-id="c15c9-103">Służy jako logiczne otoki dla odpowiedniej funkcji Win32.</span><span class="sxs-lookup"><span data-stu-id="c15c9-103">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="c15c9-104">Implementacja Win32 `VirtualQuery` pobiera informacje o zakres stron w wirtualnej przestrzeni adresowej procesu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="c15c9-104">The Win32 implementation of `VirtualQuery` retrieves information about a range of pages in the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c15c9-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="c15c9-105">Syntax</span></span>  
  
```  
HRESULT VirtualQuery (  
    [in]  void*    lpAddress,  
    [out] void*    lpBuffer,  
    [in]  SIZE_T   dwLength,  
    [out] SIZE_T*  pResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c15c9-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="c15c9-106">Parameters</span></span>  
 `lpAddress`  
 <span data-ttu-id="c15c9-107">[in] Wskaźnik na adres pamięci wirtualnej, można wykonywać zapytania.</span><span class="sxs-lookup"><span data-stu-id="c15c9-107">[in] A pointer to the address in virtual memory to be queried.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="c15c9-108">[out] Wskaźnik do struktury, która zawiera informacje o pamięci w określonym regionie.</span><span class="sxs-lookup"><span data-stu-id="c15c9-108">[out] A pointer to a structure that contains information about the specified memory region.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="c15c9-109">[in] Rozmiar w bajtach rozmiar buforu, `lpBuffer` wskazuje.</span><span class="sxs-lookup"><span data-stu-id="c15c9-109">[in] The size, in bytes, of the buffer that `lpBuffer` points to.</span></span>  
  
 `pResult`  
 <span data-ttu-id="c15c9-110">[out] Wskaźnik do liczby bajtów zwróconych przez bufor informacji.</span><span class="sxs-lookup"><span data-stu-id="c15c9-110">[out] A pointer to the number of bytes returned by the information buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c15c9-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="c15c9-111">Return Value</span></span>  
  
|<span data-ttu-id="c15c9-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c15c9-112">HRESULT</span></span>|<span data-ttu-id="c15c9-113">Opis</span><span class="sxs-lookup"><span data-stu-id="c15c9-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c15c9-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="c15c9-114">S_OK</span></span>|`VirtualQuery` <span data-ttu-id="c15c9-115">pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="c15c9-115">returned successfully.</span></span>|  
|<span data-ttu-id="c15c9-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c15c9-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c15c9-117">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="c15c9-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c15c9-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c15c9-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c15c9-119">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="c15c9-119">The call timed out.</span></span>|  
|<span data-ttu-id="c15c9-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c15c9-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c15c9-121">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="c15c9-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c15c9-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c15c9-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c15c9-123">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="c15c9-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c15c9-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c15c9-124">E_FAIL</span></span>|<span data-ttu-id="c15c9-125">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="c15c9-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c15c9-126">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="c15c9-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c15c9-127">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c15c9-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c15c9-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c15c9-128">Remarks</span></span>  
 `VirtualQuery` <span data-ttu-id="c15c9-129">zawiera informacje dotyczące zakresu stron w wirtualnej przestrzeni adresowej procesu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="c15c9-129">provides information about a range of pages in the virtual address space of the calling process.</span></span> <span data-ttu-id="c15c9-130">Ta implementacja ustawia wartość `pResult` parametru, aby liczba bajtów zwracane w buforze informacji i zwraca wartość HRESULT.</span><span class="sxs-lookup"><span data-stu-id="c15c9-130">This implementation sets the value of the `pResult` parameter to the number of bytes returned in the information buffer, and returns an HRESULT value.</span></span> <span data-ttu-id="c15c9-131">W systemie Win32 `VirtualQuery` funkcji, wartość zwracana jest rozmiar buforu.</span><span class="sxs-lookup"><span data-stu-id="c15c9-131">In the Win32 `VirtualQuery` function, the return value is the buffer size.</span></span> <span data-ttu-id="c15c9-132">Aby uzyskać więcej informacji zobacz dokumentację platformy Windows.</span><span class="sxs-lookup"><span data-stu-id="c15c9-132">For more information, see the Windows Platform documentation.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c15c9-133">Wdrożenia systemu operacyjnego `VirtualQuery` nie są naliczane zakleszczeń i można uruchomić w celu ukończenia z losową wątkami w kodzie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="c15c9-133">The operating system's implementation of `VirtualQuery` does not incur deadlock and can run to completion with random threads suspended in user code.</span></span> <span data-ttu-id="c15c9-134">Ostrożność bardzo zaimplementowanie wersji hostowanych przez tę metodę.</span><span class="sxs-lookup"><span data-stu-id="c15c9-134">Use great caution when implementing a hosted version of this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c15c9-135">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c15c9-135">Requirements</span></span>  
 <span data-ttu-id="c15c9-136">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c15c9-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c15c9-137">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c15c9-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c15c9-138">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c15c9-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="c15c9-139">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="c15c9-139">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c15c9-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c15c9-140">See also</span></span>

- [<span data-ttu-id="c15c9-141">IHostMemoryManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="c15c9-141">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
