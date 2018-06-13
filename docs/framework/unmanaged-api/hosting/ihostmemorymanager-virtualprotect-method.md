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
ms.openlocfilehash: bada01e910397adcf0fe59286d90774a0ab24ffa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33439879"
---
# <a name="ihostmemorymanagervirtualprotect-method"></a><span data-ttu-id="7367e-102">IHostMemoryManager::VirtualProtect — Metoda</span><span class="sxs-lookup"><span data-stu-id="7367e-102">IHostMemoryManager::VirtualProtect Method</span></span>
<span data-ttu-id="7367e-103">Służy jako otoka logiczne dla odpowiedniej funkcji Win32.</span><span class="sxs-lookup"><span data-stu-id="7367e-103">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="7367e-104">Implementacja Win32 `VirtualProtect` zmienia ochrony obszaru zatwierdzone stron w wirtualnej przestrzeni adresowej procesu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="7367e-104">The Win32 implementation of `VirtualProtect` changes the protection on a region of committed pages in the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7367e-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="7367e-105">Syntax</span></span>  
  
```  
HRESULT VirtualProtect (  
    [in]  void*   lpAddress,  
    [in]  SIZE_T  dwSize,  
    [in]  DWORD   flNewProtect,  
    [out] DWORD*  pflOldProtect  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7367e-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="7367e-106">Parameters</span></span>  
 `lpAddress`  
 <span data-ttu-id="7367e-107">[in] Wskaźnik do adresu podstawowego przestrzeni pamięci wirtualnej, w których atrybuty ochrony są zostanie zmieniony.</span><span class="sxs-lookup"><span data-stu-id="7367e-107">[in] A pointer to the base address of the virtual memory whose protection attributes are to be changed.</span></span>  
  
 `dwSize`  
 <span data-ttu-id="7367e-108">[in] Rozmiar w bajtach obszaru pamięci stron zostać zmienione.</span><span class="sxs-lookup"><span data-stu-id="7367e-108">[in] The size, in bytes, of the region of memory pages to be changed.</span></span>  
  
 `flNewProtect`  
 <span data-ttu-id="7367e-109">[in] Typ ochrony pamięci do zastosowania.</span><span class="sxs-lookup"><span data-stu-id="7367e-109">[in] The type of memory protection to apply.</span></span>  
  
 `pflOldProtect`  
 <span data-ttu-id="7367e-110">[out] Wskaźnik do poprzedniej wartości ochrony pamięci.</span><span class="sxs-lookup"><span data-stu-id="7367e-110">[out] A pointer to the previous memory protection value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7367e-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="7367e-111">Return Value</span></span>  
  
|<span data-ttu-id="7367e-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7367e-112">HRESULT</span></span>|<span data-ttu-id="7367e-113">Opis</span><span class="sxs-lookup"><span data-stu-id="7367e-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7367e-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="7367e-114">S_OK</span></span>|<span data-ttu-id="7367e-115">`VirtualProtect` zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="7367e-115">`VirtualProtect` returned successfully.</span></span>|  
|<span data-ttu-id="7367e-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7367e-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7367e-117">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="7367e-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7367e-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7367e-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7367e-119">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="7367e-119">The call timed out.</span></span>|  
|<span data-ttu-id="7367e-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7367e-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7367e-121">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="7367e-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7367e-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7367e-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7367e-123">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="7367e-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7367e-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7367e-124">E_FAIL</span></span>|<span data-ttu-id="7367e-125">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="7367e-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7367e-126">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="7367e-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7367e-127">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="7367e-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7367e-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7367e-128">Remarks</span></span>  
 <span data-ttu-id="7367e-129">Ta implementacja `VirtualProtect` zwraca wartość HRESULT, podczas gdy Win32 implementacja zwraca wartość inną niż zero, informując o powodzeniu i wartość zero do wskazania błędu.</span><span class="sxs-lookup"><span data-stu-id="7367e-129">This implementation of `VirtualProtect` returns an HRESULT value, while the Win32 implementation returns a non-zero value to indicate success, and a zero value to indicate failure.</span></span> <span data-ttu-id="7367e-130">Aby uzyskać więcej informacji zobacz dokumentację platformy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="7367e-130">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7367e-131">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7367e-131">Requirements</span></span>  
 <span data-ttu-id="7367e-132">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7367e-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7367e-133">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7367e-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7367e-134">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7367e-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7367e-135">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7367e-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7367e-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7367e-136">See Also</span></span>  
 [<span data-ttu-id="7367e-137">IHostMemoryManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="7367e-137">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
