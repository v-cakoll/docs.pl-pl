---
title: IHostMemoryManager::VirtualProtect — Metoda
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.VirtualProtect
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::VirtualProtect
helpviewer_keywords:
- IHostMemoryManager::VirtualProtect method [.NET Framework hosting]
- VirtualProtect method [.NET Framework hosting]
ms.assetid: 13be0299-df0d-4951-aabf-0676a30b385f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 62aa6b1d9be86a9b60abf894d67555f706e6a8ac
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59139909"
---
# <a name="ihostmemorymanagervirtualprotect-method"></a><span data-ttu-id="70779-102">IHostMemoryManager::VirtualProtect — Metoda</span><span class="sxs-lookup"><span data-stu-id="70779-102">IHostMemoryManager::VirtualProtect Method</span></span>
<span data-ttu-id="70779-103">Służy jako logiczne otoki dla odpowiedniej funkcji Win32.</span><span class="sxs-lookup"><span data-stu-id="70779-103">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="70779-104">Implementacja Win32 `VirtualProtect` zmienia ochronę na region stron zadeklarowanej w wirtualnej przestrzeni adresowej procesu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="70779-104">The Win32 implementation of `VirtualProtect` changes the protection on a region of committed pages in the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70779-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="70779-105">Syntax</span></span>  
  
```  
HRESULT VirtualProtect (  
    [in]  void*   lpAddress,  
    [in]  SIZE_T  dwSize,  
    [in]  DWORD   flNewProtect,  
    [out] DWORD*  pflOldProtect  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="70779-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="70779-106">Parameters</span></span>  
 `lpAddress`  
 <span data-ttu-id="70779-107">[in] Wskaźnik na adres bazowy pamięci wirtualnej, w których atrybuty ochrony mają być zmienione.</span><span class="sxs-lookup"><span data-stu-id="70779-107">[in] A pointer to the base address of the virtual memory whose protection attributes are to be changed.</span></span>  
  
 `dwSize`  
 <span data-ttu-id="70779-108">[in] Rozmiar w bajtach, region stron pamięci, które mają być zmienione.</span><span class="sxs-lookup"><span data-stu-id="70779-108">[in] The size, in bytes, of the region of memory pages to be changed.</span></span>  
  
 `flNewProtect`  
 <span data-ttu-id="70779-109">[in] Typ ochrony pamięci w celu zastosowania.</span><span class="sxs-lookup"><span data-stu-id="70779-109">[in] The type of memory protection to apply.</span></span>  
  
 `pflOldProtect`  
 <span data-ttu-id="70779-110">[out] Wskaźnik do poprzedniej wartości ochrony pamięci.</span><span class="sxs-lookup"><span data-stu-id="70779-110">[out] A pointer to the previous memory protection value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="70779-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="70779-111">Return Value</span></span>  
  
|<span data-ttu-id="70779-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="70779-112">HRESULT</span></span>|<span data-ttu-id="70779-113">Opis</span><span class="sxs-lookup"><span data-stu-id="70779-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="70779-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="70779-114">S_OK</span></span>|`VirtualProtect` <span data-ttu-id="70779-115">pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="70779-115">returned successfully.</span></span>|  
|<span data-ttu-id="70779-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="70779-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="70779-117">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="70779-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="70779-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="70779-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="70779-119">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="70779-119">The call timed out.</span></span>|  
|<span data-ttu-id="70779-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="70779-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="70779-121">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="70779-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="70779-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="70779-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="70779-123">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="70779-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="70779-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="70779-124">E_FAIL</span></span>|<span data-ttu-id="70779-125">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="70779-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="70779-126">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="70779-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="70779-127">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="70779-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="70779-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="70779-128">Remarks</span></span>  
 <span data-ttu-id="70779-129">Ta implementacja `VirtualProtect` zwraca wartość HRESULT, gdy implementacja Win32 zwraca wartość niezerową, informując o powodzeniu i wartość zero, aby wskazać błąd.</span><span class="sxs-lookup"><span data-stu-id="70779-129">This implementation of `VirtualProtect` returns an HRESULT value, while the Win32 implementation returns a non-zero value to indicate success, and a zero value to indicate failure.</span></span> <span data-ttu-id="70779-130">Aby uzyskać więcej informacji zobacz dokumentację platformy Windows.</span><span class="sxs-lookup"><span data-stu-id="70779-130">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70779-131">Wymagania</span><span class="sxs-lookup"><span data-stu-id="70779-131">Requirements</span></span>  
 <span data-ttu-id="70779-132">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70779-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70779-133">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="70779-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="70779-134">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="70779-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="70779-135">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="70779-135">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="70779-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="70779-136">See also</span></span>

- [<span data-ttu-id="70779-137">IHostMemoryManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="70779-137">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
