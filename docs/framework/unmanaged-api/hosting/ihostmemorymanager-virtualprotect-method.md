---
title: "IHostMemoryManager::VirtualProtect — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostMemoryManager.VirtualProtect
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostMemoryManager::VirtualProtect
helpviewer_keywords:
- IHostMemoryManager::VirtualProtect method [.NET Framework hosting]
- VirtualProtect method [.NET Framework hosting]
ms.assetid: 13be0299-df0d-4951-aabf-0676a30b385f
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 77e8e163a16752934d0a1d826cc8463b3d3281bd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ihostmemorymanagervirtualprotect-method"></a><span data-ttu-id="620c2-102">IHostMemoryManager::VirtualProtect — Metoda</span><span class="sxs-lookup"><span data-stu-id="620c2-102">IHostMemoryManager::VirtualProtect Method</span></span>
<span data-ttu-id="620c2-103">Służy jako otoka logiczne dla odpowiedniej funkcji Win32.</span><span class="sxs-lookup"><span data-stu-id="620c2-103">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="620c2-104">Implementacja Win32 `VirtualProtect` zmienia ochrony obszaru zatwierdzone stron w wirtualnej przestrzeni adresowej procesu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="620c2-104">The Win32 implementation of `VirtualProtect` changes the protection on a region of committed pages in the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="620c2-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="620c2-105">Syntax</span></span>  
  
```  
HRESULT VirtualProtect (  
    [in]  void*   lpAddress,  
    [in]  SIZE_T  dwSize,  
    [in]  DWORD   flNewProtect,  
    [out] DWORD*  pflOldProtect  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="620c2-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="620c2-106">Parameters</span></span>  
 `lpAddress`  
 <span data-ttu-id="620c2-107">[in] Wskaźnik do adresu podstawowego przestrzeni pamięci wirtualnej, w których atrybuty ochrony są zostanie zmieniony.</span><span class="sxs-lookup"><span data-stu-id="620c2-107">[in] A pointer to the base address of the virtual memory whose protection attributes are to be changed.</span></span>  
  
 `dwSize`  
 <span data-ttu-id="620c2-108">[in] Rozmiar w bajtach obszaru pamięci stron zostać zmienione.</span><span class="sxs-lookup"><span data-stu-id="620c2-108">[in] The size, in bytes, of the region of memory pages to be changed.</span></span>  
  
 `flNewProtect`  
 <span data-ttu-id="620c2-109">[in] Typ ochrony pamięci do zastosowania.</span><span class="sxs-lookup"><span data-stu-id="620c2-109">[in] The type of memory protection to apply.</span></span>  
  
 `pflOldProtect`  
 <span data-ttu-id="620c2-110">[out] Wskaźnik do poprzedniej wartości ochrony pamięci.</span><span class="sxs-lookup"><span data-stu-id="620c2-110">[out] A pointer to the previous memory protection value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="620c2-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="620c2-111">Return Value</span></span>  
  
|<span data-ttu-id="620c2-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="620c2-112">HRESULT</span></span>|<span data-ttu-id="620c2-113">Opis</span><span class="sxs-lookup"><span data-stu-id="620c2-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="620c2-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="620c2-114">S_OK</span></span>|<span data-ttu-id="620c2-115">`VirtualProtect`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="620c2-115">`VirtualProtect` returned successfully.</span></span>|  
|<span data-ttu-id="620c2-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="620c2-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="620c2-117">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="620c2-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="620c2-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="620c2-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="620c2-119">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="620c2-119">The call timed out.</span></span>|  
|<span data-ttu-id="620c2-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="620c2-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="620c2-121">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="620c2-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="620c2-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="620c2-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="620c2-123">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="620c2-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="620c2-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="620c2-124">E_FAIL</span></span>|<span data-ttu-id="620c2-125">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="620c2-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="620c2-126">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="620c2-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="620c2-127">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="620c2-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="620c2-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="620c2-128">Remarks</span></span>  
 <span data-ttu-id="620c2-129">Ta implementacja `VirtualProtect` zwraca wartość HRESULT, podczas gdy Win32 implementacja zwraca wartość inną niż zero, informując o powodzeniu i wartość zero do wskazania błędu.</span><span class="sxs-lookup"><span data-stu-id="620c2-129">This implementation of `VirtualProtect` returns an HRESULT value, while the Win32 implementation returns a non-zero value to indicate success, and a zero value to indicate failure.</span></span> <span data-ttu-id="620c2-130">Aby uzyskać więcej informacji zobacz dokumentację platformy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="620c2-130">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="620c2-131">Wymagania</span><span class="sxs-lookup"><span data-stu-id="620c2-131">Requirements</span></span>  
 <span data-ttu-id="620c2-132">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="620c2-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="620c2-133">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="620c2-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="620c2-134">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="620c2-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="620c2-135">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="620c2-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="620c2-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="620c2-136">See Also</span></span>  
 [<span data-ttu-id="620c2-137">IHostMemoryManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="620c2-137">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
