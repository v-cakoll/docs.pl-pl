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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59137361"
---
# <a name="ihostmemorymanager-interface"></a><span data-ttu-id="c3f38-102">IHostMemoryManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="c3f38-102">IHostMemoryManager Interface</span></span>
<span data-ttu-id="c3f38-103">Udostępnia metody, które umożliwiają środowisko uruchomieniowe języka wspólnego (CLR) do wysyłania żądań pamięci wirtualnej za pośrednictwem hosta, zamiast przy użyciu standardowych funkcji Win32 w pamięci wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="c3f38-103">Provides methods that allow the common language runtime (CLR) to make virtual memory requests through the host, instead of using the standard Win32 virtual memory functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c3f38-104">Metody</span><span class="sxs-lookup"><span data-stu-id="c3f38-104">Methods</span></span>  
  
|<span data-ttu-id="c3f38-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="c3f38-105">Method</span></span>|<span data-ttu-id="c3f38-106">Opis</span><span class="sxs-lookup"><span data-stu-id="c3f38-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c3f38-107">AcquiredVirtualAddressSpace, metoda</span><span class="sxs-lookup"><span data-stu-id="c3f38-107">AcquiredVirtualAddressSpace Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-acquiredvirtualaddressspace-method.md)|<span data-ttu-id="c3f38-108">Powiadamia hosta, że środowisko uruchomieniowe języka wspólnego (CLR) uzyskała określonego pamięci systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="c3f38-108">Notifies the host that the common language runtime (CLR) has acquired the specified memory from the operating system.</span></span>|  
|[<span data-ttu-id="c3f38-109">CreateMAlloc, metoda</span><span class="sxs-lookup"><span data-stu-id="c3f38-109">CreateMAlloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md)|<span data-ttu-id="c3f38-110">Pobiera wskaźnik interfejsu do [ihostmalloc —](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) wystąpienie, które służy do żądania alokacji pamięci ze stosu, utworzone przez hosta.</span><span class="sxs-lookup"><span data-stu-id="c3f38-110">Gets an interface pointer to an [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) instance that is used to request memory allocations from a heap created by the host.</span></span>|  
|[<span data-ttu-id="c3f38-111">GetMemoryLoad, metoda</span><span class="sxs-lookup"><span data-stu-id="c3f38-111">GetMemoryLoad Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-getmemoryload-method.md)|<span data-ttu-id="c3f38-112">Pobiera ilość pamięci fizycznej, który jest aktualnie używany, zgłoszonej przez hosta.</span><span class="sxs-lookup"><span data-stu-id="c3f38-112">Gets the amount of physical memory that is currently being used, as reported by the host.</span></span>|  
|[<span data-ttu-id="c3f38-113">NeedsVirtualAddressSpace, metoda</span><span class="sxs-lookup"><span data-stu-id="c3f38-113">NeedsVirtualAddressSpace Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-needsvirtualaddressspace-method.md)|<span data-ttu-id="c3f38-114">Powiadamia hosta, środowisko CLR jest zamierza podejmują próbę użycia określonego pamięci.</span><span class="sxs-lookup"><span data-stu-id="c3f38-114">Notifies the host that the CLR is going to attempt to use the specified memory.</span></span>|  
|[<span data-ttu-id="c3f38-115">RegisterMemoryNotificationCallback, metoda</span><span class="sxs-lookup"><span data-stu-id="c3f38-115">RegisterMemoryNotificationCallback Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md)|<span data-ttu-id="c3f38-116">Rejestruje wskaźnika do funkcji wywołania zwrotnego, która wywołuje hosta w celu powiadamiania CLR bieżące obciążenie pamięci na komputerze.</span><span class="sxs-lookup"><span data-stu-id="c3f38-116">Registers a pointer to a callback function that the host invokes to notify the CLR of the current memory load on the computer.</span></span>|  
|[<span data-ttu-id="c3f38-117">ReleasedVirtualAddressSpace, metoda</span><span class="sxs-lookup"><span data-stu-id="c3f38-117">ReleasedVirtualAddressSpace Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-releasedvirtualaddressspace-method.md)|<span data-ttu-id="c3f38-118">Powiadamia hosta, że CLR została zakończona, użycie pamięci określonej.</span><span class="sxs-lookup"><span data-stu-id="c3f38-118">Notifies the host that the CLR has finished using the specified memory.</span></span>|  
|[<span data-ttu-id="c3f38-119">VirtualAlloc, metoda</span><span class="sxs-lookup"><span data-stu-id="c3f38-119">VirtualAlloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualalloc-method.md)|<span data-ttu-id="c3f38-120">Służy jako logiczne otoki dla odpowiedniej funkcji Win32, która rezerwuje lub zwalnia region stron w wirtualnej przestrzeni adresowej procesu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="c3f38-120">Serves as a logical wrapper for the corresponding Win32 function, which reserves or commits a region of pages in the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="c3f38-121">VirtualFree, metoda</span><span class="sxs-lookup"><span data-stu-id="c3f38-121">VirtualFree Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualfree-method.md)|<span data-ttu-id="c3f38-122">Służy jako logiczne otoki dla odpowiedniej funkcji Win32, które zwalnia, anuluje, zwalnia lub anuluje region stron w wirtualnej przestrzeni adresowej procesu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="c3f38-122">Serves as a logical wrapper for the corresponding Win32 function, which releases, decommits, or releases and decommits a region of pages within the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="c3f38-123">VirtualProtect, metoda</span><span class="sxs-lookup"><span data-stu-id="c3f38-123">VirtualProtect Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualprotect-method.md)|<span data-ttu-id="c3f38-124">Służy jako logiczne otoki dla odpowiedniej funkcji Win32, która zmienia ochronę na region stron zadeklarowanej w wirtualnej przestrzeni adresowej procesu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="c3f38-124">Serves as a logical wrapper for the corresponding Win32 function, which changes the protection on a region of committed pages in the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="c3f38-125">VirtualQuery, metoda</span><span class="sxs-lookup"><span data-stu-id="c3f38-125">VirtualQuery Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualquery-method.md)|<span data-ttu-id="c3f38-126">Służy jako logiczne otoki dla odpowiedniej funkcji Win32, która pobiera informacje o zakres stron w wirtualnej przestrzeni adresowej procesu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="c3f38-126">Serves as a logical wrapper for the corresponding Win32 function, which retrieves information about a range of pages in the virtual address space of the calling process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c3f38-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c3f38-127">Remarks</span></span>  
 `IHostMemoryManager` <span data-ttu-id="c3f38-128">zapewnia także metody dla środowiska CLR można uzyskać wskaźnika za pomocą którego propozycji dotyczących pamięci na stosie i uzyskać poziom wykorzystania pamięci w procesie zgłoszonej przez hosta.</span><span class="sxs-lookup"><span data-stu-id="c3f38-128">also provides methods for the CLR to obtain a pointer through which to make memory requests on the heap and to get the level of memory pressure in the process, as reported by the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3f38-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c3f38-129">Requirements</span></span>  
 <span data-ttu-id="c3f38-130">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3f38-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3f38-131">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c3f38-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c3f38-132">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c3f38-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="c3f38-133">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="c3f38-133">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c3f38-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c3f38-134">See also</span></span>

- [<span data-ttu-id="c3f38-135">IHostMalloc — Interfejs</span><span class="sxs-lookup"><span data-stu-id="c3f38-135">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
- [<span data-ttu-id="c3f38-136">Hosting — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="c3f38-136">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
