---
title: "IHostMemoryManager — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IHostMemoryManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager
helpviewer_keywords:
- IHostMemoryManager interface [.NET Framework hosting]
ms.assetid: a945d439-3b34-4aa4-b575-8413dd7806ce
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b39a43874bc1808928f21e0a35638aae9a99ca8e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ihostmemorymanager-interface"></a><span data-ttu-id="d04fc-102">IHostMemoryManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="d04fc-102">IHostMemoryManager Interface</span></span>
<span data-ttu-id="d04fc-103">Udostępnia metody, które umożliwia środowisko uruchomieniowe języka wspólnego (CLR) do żądania pamięci wirtualnej za pośrednictwem hosta, zamiast używać standardowych funkcji Win32 w pamięci wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="d04fc-103">Provides methods that allow the common language runtime (CLR) to make virtual memory requests through the host, instead of using the standard Win32 virtual memory functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d04fc-104">Metody</span><span class="sxs-lookup"><span data-stu-id="d04fc-104">Methods</span></span>  
  
|<span data-ttu-id="d04fc-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="d04fc-105">Method</span></span>|<span data-ttu-id="d04fc-106">Opis</span><span class="sxs-lookup"><span data-stu-id="d04fc-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d04fc-107">AcquiredVirtualAddressSpace, metoda</span><span class="sxs-lookup"><span data-stu-id="d04fc-107">AcquiredVirtualAddressSpace Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-acquiredvirtualaddressspace-method.md)|<span data-ttu-id="d04fc-108">Powiadamia hosta, że środowisko uruchomieniowe języka wspólnego (CLR) uzyskał określonego pamięci systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="d04fc-108">Notifies the host that the common language runtime (CLR) has acquired the specified memory from the operating system.</span></span>|  
|[<span data-ttu-id="d04fc-109">CreateMAlloc, metoda</span><span class="sxs-lookup"><span data-stu-id="d04fc-109">CreateMAlloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md)|<span data-ttu-id="d04fc-110">Pobiera wskaźnika interfejsu do [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) wystąpienie, które jest używane do żądania alokacji pamięci z sterty utworzone przez hosta.</span><span class="sxs-lookup"><span data-stu-id="d04fc-110">Gets an interface pointer to an [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) instance that is used to request memory allocations from a heap created by the host.</span></span>|  
|[<span data-ttu-id="d04fc-111">GetMemoryLoad, metoda</span><span class="sxs-lookup"><span data-stu-id="d04fc-111">GetMemoryLoad Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-getmemoryload-method.md)|<span data-ttu-id="d04fc-112">Pobiera ilość pamięci fizycznej, która jest aktualnie używana, zgłoszonej przez hosta.</span><span class="sxs-lookup"><span data-stu-id="d04fc-112">Gets the amount of physical memory that is currently being used, as reported by the host.</span></span>|  
|[<span data-ttu-id="d04fc-113">NeedsVirtualAddressSpace, metoda</span><span class="sxs-lookup"><span data-stu-id="d04fc-113">NeedsVirtualAddressSpace Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-needsvirtualaddressspace-method.md)|<span data-ttu-id="d04fc-114">Powiadamia host czy CLR będzie próbować używać pamięci określony.</span><span class="sxs-lookup"><span data-stu-id="d04fc-114">Notifies the host that the CLR is going to attempt to use the specified memory.</span></span>|  
|[<span data-ttu-id="d04fc-115">RegisterMemoryNotificationCallback, metoda</span><span class="sxs-lookup"><span data-stu-id="d04fc-115">RegisterMemoryNotificationCallback Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md)|<span data-ttu-id="d04fc-116">Rejestruje wskaźnika do funkcji wywołania zwrotnego, która wywołuje hosta powiadomiono CLR bieżącego obciążenia pamięci na komputerze.</span><span class="sxs-lookup"><span data-stu-id="d04fc-116">Registers a pointer to a callback function that the host invokes to notify the CLR of the current memory load on the computer.</span></span>|  
|[<span data-ttu-id="d04fc-117">ReleasedVirtualAddressSpace, metoda</span><span class="sxs-lookup"><span data-stu-id="d04fc-117">ReleasedVirtualAddressSpace Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-releasedvirtualaddressspace-method.md)|<span data-ttu-id="d04fc-118">Powiadamia hosta CLR zostało zakończone, przy użyciu określonego pamięci.</span><span class="sxs-lookup"><span data-stu-id="d04fc-118">Notifies the host that the CLR has finished using the specified memory.</span></span>|  
|[<span data-ttu-id="d04fc-119">VirtualAlloc, metoda</span><span class="sxs-lookup"><span data-stu-id="d04fc-119">VirtualAlloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualalloc-method.md)|<span data-ttu-id="d04fc-120">Służy jako otoka logiczne dla odpowiedniej funkcji Win32, rezerwuje lub zatwierdza region stron w wirtualnej przestrzeni adresowej procesu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="d04fc-120">Serves as a logical wrapper for the corresponding Win32 function, which reserves or commits a region of pages in the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="d04fc-121">VirtualFree, metoda</span><span class="sxs-lookup"><span data-stu-id="d04fc-121">VirtualFree Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualfree-method.md)|<span data-ttu-id="d04fc-122">Służy jako otoka logiczne dla odpowiedniej funkcji Win32, co zwalnia, decommits, lub zwalnia i decommits region stron w wirtualnej przestrzeni adresowej procesu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="d04fc-122">Serves as a logical wrapper for the corresponding Win32 function, which releases, decommits, or releases and decommits a region of pages within the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="d04fc-123">VirtualProtect, metoda</span><span class="sxs-lookup"><span data-stu-id="d04fc-123">VirtualProtect Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualprotect-method.md)|<span data-ttu-id="d04fc-124">Służy jako otoka logiczne dla odpowiedniej funkcji Win32 zmienia ochrony obszaru zatwierdzone stron w wirtualnej przestrzeni adresowej procesu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="d04fc-124">Serves as a logical wrapper for the corresponding Win32 function, which changes the protection on a region of committed pages in the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="d04fc-125">VirtualQuery, metoda</span><span class="sxs-lookup"><span data-stu-id="d04fc-125">VirtualQuery Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualquery-method.md)|<span data-ttu-id="d04fc-126">Służy jako otoka logiczne dla odpowiedniej funkcji Win32 pobiera informacje o zakresie stron w wirtualnej przestrzeni adresowej procesu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="d04fc-126">Serves as a logical wrapper for the corresponding Win32 function, which retrieves information about a range of pages in the virtual address space of the calling process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d04fc-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d04fc-127">Remarks</span></span>  
 <span data-ttu-id="d04fc-128">`IHostMemoryManager`udostępnia metody dla CLR można uzyskać wskaźnika za pośrednictwem której na wysyłanie żądań pamięci na stosie, a także aby uzyskać poziom wykorzystania pamięci w procesie zgłoszonej przez hosta.</span><span class="sxs-lookup"><span data-stu-id="d04fc-128">`IHostMemoryManager` also provides methods for the CLR to obtain a pointer through which to make memory requests on the heap and to get the level of memory pressure in the process, as reported by the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d04fc-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d04fc-129">Requirements</span></span>  
 <span data-ttu-id="d04fc-130">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d04fc-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d04fc-131">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d04fc-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d04fc-132">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d04fc-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d04fc-133">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d04fc-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d04fc-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d04fc-134">See Also</span></span>  
 [<span data-ttu-id="d04fc-135">IHostMalloc, interfejs</span><span class="sxs-lookup"><span data-stu-id="d04fc-135">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)  
 [<span data-ttu-id="d04fc-136">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="d04fc-136">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
