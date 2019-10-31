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
ms.openlocfilehash: bc05d76795f20d28d6d2899d61dc4674ebfdca8c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128646"
---
# <a name="ihostmemorymanager-interface"></a><span data-ttu-id="8c2e4-102">IHostMemoryManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="8c2e4-102">IHostMemoryManager Interface</span></span>
<span data-ttu-id="8c2e4-103">Zapewnia metody, które umożliwiają środowisko uruchomieniowe języka wspólnego (CLR) do udostępniania żądań pamięci wirtualnej za pośrednictwem hosta, zamiast używać standardowych funkcji pamięci wirtualnej Win32.</span><span class="sxs-lookup"><span data-stu-id="8c2e4-103">Provides methods that allow the common language runtime (CLR) to make virtual memory requests through the host, instead of using the standard Win32 virtual memory functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8c2e4-104">Metody</span><span class="sxs-lookup"><span data-stu-id="8c2e4-104">Methods</span></span>  
  
|<span data-ttu-id="8c2e4-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="8c2e4-105">Method</span></span>|<span data-ttu-id="8c2e4-106">Opis</span><span class="sxs-lookup"><span data-stu-id="8c2e4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8c2e4-107">AcquiredVirtualAddressSpace, metoda</span><span class="sxs-lookup"><span data-stu-id="8c2e4-107">AcquiredVirtualAddressSpace Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-acquiredvirtualaddressspace-method.md)|<span data-ttu-id="8c2e4-108">Powiadamia hosta, że środowisko uruchomieniowe języka wspólnego (CLR) uzyskało określoną ilość pamięci z systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="8c2e4-108">Notifies the host that the common language runtime (CLR) has acquired the specified memory from the operating system.</span></span>|  
|[<span data-ttu-id="8c2e4-109">CreateMAlloc, metoda</span><span class="sxs-lookup"><span data-stu-id="8c2e4-109">CreateMAlloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md)|<span data-ttu-id="8c2e4-110">Pobiera wskaźnik interfejsu do wystąpienia [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) , które jest używane do żądania alokacji pamięci ze sterty utworzonej przez hosta.</span><span class="sxs-lookup"><span data-stu-id="8c2e4-110">Gets an interface pointer to an [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) instance that is used to request memory allocations from a heap created by the host.</span></span>|  
|[<span data-ttu-id="8c2e4-111">GetMemoryLoad, metoda</span><span class="sxs-lookup"><span data-stu-id="8c2e4-111">GetMemoryLoad Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-getmemoryload-method.md)|<span data-ttu-id="8c2e4-112">Pobiera ilość pamięci fizycznej, która jest aktualnie używana, zgłoszoną przez hosta.</span><span class="sxs-lookup"><span data-stu-id="8c2e4-112">Gets the amount of physical memory that is currently being used, as reported by the host.</span></span>|  
|[<span data-ttu-id="8c2e4-113">NeedsVirtualAddressSpace, metoda</span><span class="sxs-lookup"><span data-stu-id="8c2e4-113">NeedsVirtualAddressSpace Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-needsvirtualaddressspace-method.md)|<span data-ttu-id="8c2e4-114">Powiadamia hosta, że środowisko CLR podejmie próbę użycia określonej pamięci.</span><span class="sxs-lookup"><span data-stu-id="8c2e4-114">Notifies the host that the CLR is going to attempt to use the specified memory.</span></span>|  
|[<span data-ttu-id="8c2e4-115">RegisterMemoryNotificationCallback, metoda</span><span class="sxs-lookup"><span data-stu-id="8c2e4-115">RegisterMemoryNotificationCallback Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md)|<span data-ttu-id="8c2e4-116">Rejestruje wskaźnik do funkcji wywołania zwrotnego, który jest wywoływany przez hosta w celu powiadomienia CLR o bieżącym obciążeniu pamięci na komputerze.</span><span class="sxs-lookup"><span data-stu-id="8c2e4-116">Registers a pointer to a callback function that the host invokes to notify the CLR of the current memory load on the computer.</span></span>|  
|[<span data-ttu-id="8c2e4-117">ReleasedVirtualAddressSpace, metoda</span><span class="sxs-lookup"><span data-stu-id="8c2e4-117">ReleasedVirtualAddressSpace Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-releasedvirtualaddressspace-method.md)|<span data-ttu-id="8c2e4-118">Powiadamia hosta o zakończeniu środowiska CLR przy użyciu określonej pamięci.</span><span class="sxs-lookup"><span data-stu-id="8c2e4-118">Notifies the host that the CLR has finished using the specified memory.</span></span>|  
|[<span data-ttu-id="8c2e4-119">VirtualAlloc, metoda</span><span class="sxs-lookup"><span data-stu-id="8c2e4-119">VirtualAlloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualalloc-method.md)|<span data-ttu-id="8c2e4-120">Służy jako otoka logiczna dla odpowiedniej funkcji Win32, która rezerwuje lub zatwierdza region stron w wirtualnej przestrzeni adresowej procesu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="8c2e4-120">Serves as a logical wrapper for the corresponding Win32 function, which reserves or commits a region of pages in the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="8c2e4-121">VirtualFree, metoda</span><span class="sxs-lookup"><span data-stu-id="8c2e4-121">VirtualFree Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualfree-method.md)|<span data-ttu-id="8c2e4-122">Służy jako otoka logiczna dla odpowiedniej funkcji Win32, która zwalnia, anuluje lub zwalnia i determinuje region stron w wirtualnej przestrzeni adresowej procesu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="8c2e4-122">Serves as a logical wrapper for the corresponding Win32 function, which releases, decommits, or releases and decommits a region of pages within the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="8c2e4-123">VirtualProtect, metoda</span><span class="sxs-lookup"><span data-stu-id="8c2e4-123">VirtualProtect Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualprotect-method.md)|<span data-ttu-id="8c2e4-124">Służy jako otoka logiczna dla odpowiedniej funkcji Win32, która zmienia ochronę w regionie zatwierdzonych stron w wirtualnej przestrzeni adresowej procesu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="8c2e4-124">Serves as a logical wrapper for the corresponding Win32 function, which changes the protection on a region of committed pages in the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="8c2e4-125">VirtualQuery, metoda</span><span class="sxs-lookup"><span data-stu-id="8c2e4-125">VirtualQuery Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualquery-method.md)|<span data-ttu-id="8c2e4-126">Służy jako otoka logiczna dla odpowiedniej funkcji Win32, która pobiera informacje o zakresie stron w wirtualnej przestrzeni adresowej procesu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="8c2e4-126">Serves as a logical wrapper for the corresponding Win32 function, which retrieves information about a range of pages in the virtual address space of the calling process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8c2e4-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8c2e4-127">Remarks</span></span>  
 <span data-ttu-id="8c2e4-128">`IHostMemoryManager` udostępnia również metody środowiska CLR do uzyskania wskaźnika, za pomocą którego należy wykonać żądania pamięci na stercie i uzyskać poziom ciśnienia pamięci w procesie, zgodnie z raportem hosta.</span><span class="sxs-lookup"><span data-stu-id="8c2e4-128">`IHostMemoryManager` also provides methods for the CLR to obtain a pointer through which to make memory requests on the heap and to get the level of memory pressure in the process, as reported by the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c2e4-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8c2e4-129">Requirements</span></span>  
 <span data-ttu-id="8c2e4-130">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c2e4-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c2e4-131">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8c2e4-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8c2e4-132">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="8c2e4-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8c2e4-133">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c2e4-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c2e4-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8c2e4-134">See also</span></span>

- [<span data-ttu-id="8c2e4-135">IHostMalloc, interfejs</span><span class="sxs-lookup"><span data-stu-id="8c2e4-135">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
- [<span data-ttu-id="8c2e4-136">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="8c2e4-136">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
