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
ms.openlocfilehash: 68a9d6ad7470ffaf1143a4a8e3134f20edb9e3c5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33439221"
---
# <a name="ihostmemorymanagervirtualquery-method"></a><span data-ttu-id="9e7cf-102">IHostMemoryManager::VirtualQuery — Metoda</span><span class="sxs-lookup"><span data-stu-id="9e7cf-102">IHostMemoryManager::VirtualQuery Method</span></span>
<span data-ttu-id="9e7cf-103">Służy jako otoka logiczne dla odpowiedniej funkcji Win32.</span><span class="sxs-lookup"><span data-stu-id="9e7cf-103">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="9e7cf-104">Implementacja Win32 `VirtualQuery` pobiera informacje o zakresie stron w wirtualnej przestrzeni adresowej procesu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="9e7cf-104">The Win32 implementation of `VirtualQuery` retrieves information about a range of pages in the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e7cf-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="9e7cf-105">Syntax</span></span>  
  
```  
HRESULT VirtualQuery (  
    [in]  void*    lpAddress,  
    [out] void*    lpBuffer,  
    [in]  SIZE_T   dwLength,  
    [out] SIZE_T*  pResult  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9e7cf-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="9e7cf-106">Parameters</span></span>  
 `lpAddress`  
 <span data-ttu-id="9e7cf-107">[in] Wskaźnik do adresów pamięci wirtualnej, można wykonać zapytania.</span><span class="sxs-lookup"><span data-stu-id="9e7cf-107">[in] A pointer to the address in virtual memory to be queried.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="9e7cf-108">[out] Wskaźnik do struktury, zawierający informacje o pamięci określonego regionu.</span><span class="sxs-lookup"><span data-stu-id="9e7cf-108">[out] A pointer to a structure that contains information about the specified memory region.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="9e7cf-109">[in] Rozmiar w bajtach buforu, który `lpBuffer` wskazuje.</span><span class="sxs-lookup"><span data-stu-id="9e7cf-109">[in] The size, in bytes, of the buffer that `lpBuffer` points to.</span></span>  
  
 `pResult`  
 <span data-ttu-id="9e7cf-110">[out] Wskaźnik do liczba bajtów zwrócona przez bufor informacji.</span><span class="sxs-lookup"><span data-stu-id="9e7cf-110">[out] A pointer to the number of bytes returned by the information buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9e7cf-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="9e7cf-111">Return Value</span></span>  
  
|<span data-ttu-id="9e7cf-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9e7cf-112">HRESULT</span></span>|<span data-ttu-id="9e7cf-113">Opis</span><span class="sxs-lookup"><span data-stu-id="9e7cf-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9e7cf-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="9e7cf-114">S_OK</span></span>|<span data-ttu-id="9e7cf-115">`VirtualQuery` zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="9e7cf-115">`VirtualQuery` returned successfully.</span></span>|  
|<span data-ttu-id="9e7cf-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9e7cf-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9e7cf-117">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="9e7cf-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9e7cf-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9e7cf-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9e7cf-119">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="9e7cf-119">The call timed out.</span></span>|  
|<span data-ttu-id="9e7cf-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9e7cf-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9e7cf-121">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="9e7cf-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9e7cf-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9e7cf-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9e7cf-123">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="9e7cf-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9e7cf-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9e7cf-124">E_FAIL</span></span>|<span data-ttu-id="9e7cf-125">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="9e7cf-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9e7cf-126">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="9e7cf-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9e7cf-127">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9e7cf-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9e7cf-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9e7cf-128">Remarks</span></span>  
 <span data-ttu-id="9e7cf-129">`VirtualQuery` informacje na temat zakresu stron w wirtualnej przestrzeni adresowej procesu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="9e7cf-129">`VirtualQuery` provides information about a range of pages in the virtual address space of the calling process.</span></span> <span data-ttu-id="9e7cf-130">Ta implementacja ustawia wartość `pResult` parametr, aby liczba bajtów zwrócona w buforze informacji i zwraca wartość HRESULT.</span><span class="sxs-lookup"><span data-stu-id="9e7cf-130">This implementation sets the value of the `pResult` parameter to the number of bytes returned in the information buffer, and returns an HRESULT value.</span></span> <span data-ttu-id="9e7cf-131">W systemie Win32 `VirtualQuery` rozmiar buforu jest zwracana wartość funkcji.</span><span class="sxs-lookup"><span data-stu-id="9e7cf-131">In the Win32 `VirtualQuery` function, the return value is the buffer size.</span></span> <span data-ttu-id="9e7cf-132">Aby uzyskać więcej informacji zobacz dokumentację platformy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="9e7cf-132">For more information, see the Windows Platform documentation.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9e7cf-133">Wdrożenia systemu operacyjnego `VirtualQuery` nie wpływa negatywnie zakleszczenie i można uruchomić w celu ukończenia z losowe wątków w kodzie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="9e7cf-133">The operating system's implementation of `VirtualQuery` does not incur deadlock and can run to completion with random threads suspended in user code.</span></span> <span data-ttu-id="9e7cf-134">Należy zachować ostrożność dużą podczas wdrażania obsługiwane wersji tej metody.</span><span class="sxs-lookup"><span data-stu-id="9e7cf-134">Use great caution when implementing a hosted version of this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e7cf-135">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9e7cf-135">Requirements</span></span>  
 <span data-ttu-id="9e7cf-136">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e7cf-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e7cf-137">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9e7cf-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9e7cf-138">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9e7cf-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9e7cf-139">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e7cf-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e7cf-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9e7cf-140">See Also</span></span>  
 [<span data-ttu-id="9e7cf-141">IHostMemoryManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="9e7cf-141">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
