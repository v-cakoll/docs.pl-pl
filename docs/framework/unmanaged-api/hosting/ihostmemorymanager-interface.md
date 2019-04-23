---
title: IHostMemoryManager — Interfejs
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 57f34ed1796f6fa411d31fca83baeff693f85d70
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59137361"
---
# <a name="ihostmemorymanager-interface"></a><span data-ttu-id="01500-102">IHostMemoryManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="01500-102">IHostMemoryManager Interface</span></span>
<span data-ttu-id="01500-103">Udostępnia metody, które umożliwiają środowisko uruchomieniowe języka wspólnego (CLR) do wysyłania żądań pamięci wirtualnej za pośrednictwem hosta, zamiast przy użyciu standardowych funkcji Win32 w pamięci wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="01500-103">Provides methods that allow the common language runtime (CLR) to make virtual memory requests through the host, instead of using the standard Win32 virtual memory functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="01500-104">Metody</span><span class="sxs-lookup"><span data-stu-id="01500-104">Methods</span></span>  
  
|<span data-ttu-id="01500-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="01500-105">Method</span></span>|<span data-ttu-id="01500-106">Opis</span><span class="sxs-lookup"><span data-stu-id="01500-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="01500-107">AcquiredVirtualAddressSpace, metoda</span><span class="sxs-lookup"><span data-stu-id="01500-107">AcquiredVirtualAddressSpace Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-acquiredvirtualaddressspace-method.md)|<span data-ttu-id="01500-108">Powiadamia hosta, że środowisko uruchomieniowe języka wspólnego (CLR) uzyskała określonego pamięci systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="01500-108">Notifies the host that the common language runtime (CLR) has acquired the specified memory from the operating system.</span></span>|  
|[<span data-ttu-id="01500-109">CreateMAlloc, metoda</span><span class="sxs-lookup"><span data-stu-id="01500-109">CreateMAlloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md)|<span data-ttu-id="01500-110">Pobiera wskaźnik interfejsu do [ihostmalloc —](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) wystąpienie, które służy do żądania alokacji pamięci ze stosu, utworzone przez hosta.</span><span class="sxs-lookup"><span data-stu-id="01500-110">Gets an interface pointer to an [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) instance that is used to request memory allocations from a heap created by the host.</span></span>|  
|[<span data-ttu-id="01500-111">GetMemoryLoad, metoda</span><span class="sxs-lookup"><span data-stu-id="01500-111">GetMemoryLoad Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-getmemoryload-method.md)|<span data-ttu-id="01500-112">Pobiera ilość pamięci fizycznej, który jest aktualnie używany, zgłoszonej przez hosta.</span><span class="sxs-lookup"><span data-stu-id="01500-112">Gets the amount of physical memory that is currently being used, as reported by the host.</span></span>|  
|[<span data-ttu-id="01500-113">NeedsVirtualAddressSpace, metoda</span><span class="sxs-lookup"><span data-stu-id="01500-113">NeedsVirtualAddressSpace Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-needsvirtualaddressspace-method.md)|<span data-ttu-id="01500-114">Powiadamia hosta, środowisko CLR jest zamierza podejmują próbę użycia określonego pamięci.</span><span class="sxs-lookup"><span data-stu-id="01500-114">Notifies the host that the CLR is going to attempt to use the specified memory.</span></span>|  
|[<span data-ttu-id="01500-115">RegisterMemoryNotificationCallback, metoda</span><span class="sxs-lookup"><span data-stu-id="01500-115">RegisterMemoryNotificationCallback Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md)|<span data-ttu-id="01500-116">Rejestruje wskaźnika do funkcji wywołania zwrotnego, która wywołuje hosta w celu powiadamiania CLR bieżące obciążenie pamięci na komputerze.</span><span class="sxs-lookup"><span data-stu-id="01500-116">Registers a pointer to a callback function that the host invokes to notify the CLR of the current memory load on the computer.</span></span>|  
|[<span data-ttu-id="01500-117">ReleasedVirtualAddressSpace, metoda</span><span class="sxs-lookup"><span data-stu-id="01500-117">ReleasedVirtualAddressSpace Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-releasedvirtualaddressspace-method.md)|<span data-ttu-id="01500-118">Powiadamia hosta, że CLR została zakończona, użycie pamięci określonej.</span><span class="sxs-lookup"><span data-stu-id="01500-118">Notifies the host that the CLR has finished using the specified memory.</span></span>|  
|[<span data-ttu-id="01500-119">VirtualAlloc, metoda</span><span class="sxs-lookup"><span data-stu-id="01500-119">VirtualAlloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualalloc-method.md)|<span data-ttu-id="01500-120">Służy jako logiczne otoki dla odpowiedniej funkcji Win32, która rezerwuje lub zwalnia region stron w wirtualnej przestrzeni adresowej procesu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="01500-120">Serves as a logical wrapper for the corresponding Win32 function, which reserves or commits a region of pages in the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="01500-121">VirtualFree, metoda</span><span class="sxs-lookup"><span data-stu-id="01500-121">VirtualFree Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualfree-method.md)|<span data-ttu-id="01500-122">Służy jako logiczne otoki dla odpowiedniej funkcji Win32, które zwalnia, anuluje, zwalnia lub anuluje region stron w wirtualnej przestrzeni adresowej procesu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="01500-122">Serves as a logical wrapper for the corresponding Win32 function, which releases, decommits, or releases and decommits a region of pages within the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="01500-123">VirtualProtect, metoda</span><span class="sxs-lookup"><span data-stu-id="01500-123">VirtualProtect Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualprotect-method.md)|<span data-ttu-id="01500-124">Służy jako logiczne otoki dla odpowiedniej funkcji Win32, która zmienia ochronę na region stron zadeklarowanej w wirtualnej przestrzeni adresowej procesu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="01500-124">Serves as a logical wrapper for the corresponding Win32 function, which changes the protection on a region of committed pages in the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="01500-125">VirtualQuery, metoda</span><span class="sxs-lookup"><span data-stu-id="01500-125">VirtualQuery Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualquery-method.md)|<span data-ttu-id="01500-126">Służy jako logiczne otoki dla odpowiedniej funkcji Win32, która pobiera informacje o zakres stron w wirtualnej przestrzeni adresowej procesu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="01500-126">Serves as a logical wrapper for the corresponding Win32 function, which retrieves information about a range of pages in the virtual address space of the calling process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="01500-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="01500-127">Remarks</span></span>  
 <span data-ttu-id="01500-128">`IHostMemoryManager` zapewnia także metody dla środowiska CLR można uzyskać wskaźnika za pomocą którego propozycji dotyczących pamięci na stosie i uzyskać poziom wykorzystania pamięci w procesie zgłoszonej przez hosta.</span><span class="sxs-lookup"><span data-stu-id="01500-128">`IHostMemoryManager` also provides methods for the CLR to obtain a pointer through which to make memory requests on the heap and to get the level of memory pressure in the process, as reported by the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01500-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="01500-129">Requirements</span></span>  
 <span data-ttu-id="01500-130">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01500-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01500-131">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="01500-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="01500-132">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="01500-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="01500-133">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01500-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01500-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="01500-134">See also</span></span>

- [<span data-ttu-id="01500-135">IHostMalloc, interfejs</span><span class="sxs-lookup"><span data-stu-id="01500-135">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
- [<span data-ttu-id="01500-136">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="01500-136">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
