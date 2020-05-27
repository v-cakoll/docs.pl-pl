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
ms.openlocfilehash: 4e7e76a4a3ab291ee97ad0912e3d6224cdf96fba
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804490"
---
# <a name="ihostmemorymanager-interface"></a><span data-ttu-id="a1ff2-102">IHostMemoryManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="a1ff2-102">IHostMemoryManager Interface</span></span>
<span data-ttu-id="a1ff2-103">Zapewnia metody, które umożliwiają środowisko uruchomieniowe języka wspólnego (CLR) do udostępniania żądań pamięci wirtualnej za pośrednictwem hosta, zamiast używać standardowych funkcji pamięci wirtualnej Win32.</span><span class="sxs-lookup"><span data-stu-id="a1ff2-103">Provides methods that allow the common language runtime (CLR) to make virtual memory requests through the host, instead of using the standard Win32 virtual memory functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a1ff2-104">Metody</span><span class="sxs-lookup"><span data-stu-id="a1ff2-104">Methods</span></span>  
  
|<span data-ttu-id="a1ff2-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="a1ff2-105">Method</span></span>|<span data-ttu-id="a1ff2-106">Opis</span><span class="sxs-lookup"><span data-stu-id="a1ff2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a1ff2-107">AcquiredVirtualAddressSpace, metoda</span><span class="sxs-lookup"><span data-stu-id="a1ff2-107">AcquiredVirtualAddressSpace Method</span></span>](ihostmemorymanager-acquiredvirtualaddressspace-method.md)|<span data-ttu-id="a1ff2-108">Powiadamia hosta, że środowisko uruchomieniowe języka wspólnego (CLR) uzyskało określoną ilość pamięci z systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="a1ff2-108">Notifies the host that the common language runtime (CLR) has acquired the specified memory from the operating system.</span></span>|  
|[<span data-ttu-id="a1ff2-109">CreateMAlloc, metoda</span><span class="sxs-lookup"><span data-stu-id="a1ff2-109">CreateMAlloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md)|<span data-ttu-id="a1ff2-110">Pobiera wskaźnik interfejsu do wystąpienia [IHostMAlloc](ihostmalloc-interface.md) , które jest używane do żądania alokacji pamięci ze sterty utworzonej przez hosta.</span><span class="sxs-lookup"><span data-stu-id="a1ff2-110">Gets an interface pointer to an [IHostMAlloc](ihostmalloc-interface.md) instance that is used to request memory allocations from a heap created by the host.</span></span>|  
|[<span data-ttu-id="a1ff2-111">GetMemoryLoad, metoda</span><span class="sxs-lookup"><span data-stu-id="a1ff2-111">GetMemoryLoad Method</span></span>](ihostmemorymanager-getmemoryload-method.md)|<span data-ttu-id="a1ff2-112">Pobiera ilość pamięci fizycznej, która jest aktualnie używana, zgłoszoną przez hosta.</span><span class="sxs-lookup"><span data-stu-id="a1ff2-112">Gets the amount of physical memory that is currently being used, as reported by the host.</span></span>|  
|[<span data-ttu-id="a1ff2-113">NeedsVirtualAddressSpace, metoda</span><span class="sxs-lookup"><span data-stu-id="a1ff2-113">NeedsVirtualAddressSpace Method</span></span>](ihostmemorymanager-needsvirtualaddressspace-method.md)|<span data-ttu-id="a1ff2-114">Powiadamia hosta, że środowisko CLR podejmie próbę użycia określonej pamięci.</span><span class="sxs-lookup"><span data-stu-id="a1ff2-114">Notifies the host that the CLR is going to attempt to use the specified memory.</span></span>|  
|[<span data-ttu-id="a1ff2-115">RegisterMemoryNotificationCallback, metoda</span><span class="sxs-lookup"><span data-stu-id="a1ff2-115">RegisterMemoryNotificationCallback Method</span></span>](ihostmemorymanager-registermemorynotificationcallback-method.md)|<span data-ttu-id="a1ff2-116">Rejestruje wskaźnik do funkcji wywołania zwrotnego, który jest wywoływany przez hosta w celu powiadomienia CLR o bieżącym obciążeniu pamięci na komputerze.</span><span class="sxs-lookup"><span data-stu-id="a1ff2-116">Registers a pointer to a callback function that the host invokes to notify the CLR of the current memory load on the computer.</span></span>|  
|[<span data-ttu-id="a1ff2-117">ReleasedVirtualAddressSpace, metoda</span><span class="sxs-lookup"><span data-stu-id="a1ff2-117">ReleasedVirtualAddressSpace Method</span></span>](ihostmemorymanager-releasedvirtualaddressspace-method.md)|<span data-ttu-id="a1ff2-118">Powiadamia hosta o zakończeniu środowiska CLR przy użyciu określonej pamięci.</span><span class="sxs-lookup"><span data-stu-id="a1ff2-118">Notifies the host that the CLR has finished using the specified memory.</span></span>|  
|[<span data-ttu-id="a1ff2-119">VirtualAlloc, metoda</span><span class="sxs-lookup"><span data-stu-id="a1ff2-119">VirtualAlloc Method</span></span>](ihostmemorymanager-virtualalloc-method.md)|<span data-ttu-id="a1ff2-120">Służy jako otoka logiczna dla odpowiedniej funkcji Win32, która rezerwuje lub zatwierdza region stron w wirtualnej przestrzeni adresowej procesu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="a1ff2-120">Serves as a logical wrapper for the corresponding Win32 function, which reserves or commits a region of pages in the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="a1ff2-121">VirtualFree, metoda</span><span class="sxs-lookup"><span data-stu-id="a1ff2-121">VirtualFree Method</span></span>](ihostmemorymanager-virtualfree-method.md)|<span data-ttu-id="a1ff2-122">Służy jako otoka logiczna dla odpowiedniej funkcji Win32, która zwalnia, anuluje lub zwalnia i determinuje region stron w wirtualnej przestrzeni adresowej procesu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="a1ff2-122">Serves as a logical wrapper for the corresponding Win32 function, which releases, decommits, or releases and decommits a region of pages within the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="a1ff2-123">VirtualProtect, metoda</span><span class="sxs-lookup"><span data-stu-id="a1ff2-123">VirtualProtect Method</span></span>](ihostmemorymanager-virtualprotect-method.md)|<span data-ttu-id="a1ff2-124">Służy jako otoka logiczna dla odpowiedniej funkcji Win32, która zmienia ochronę w regionie zatwierdzonych stron w wirtualnej przestrzeni adresowej procesu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="a1ff2-124">Serves as a logical wrapper for the corresponding Win32 function, which changes the protection on a region of committed pages in the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="a1ff2-125">VirtualQuery, metoda</span><span class="sxs-lookup"><span data-stu-id="a1ff2-125">VirtualQuery Method</span></span>](ihostmemorymanager-virtualquery-method.md)|<span data-ttu-id="a1ff2-126">Służy jako otoka logiczna dla odpowiedniej funkcji Win32, która pobiera informacje o zakresie stron w wirtualnej przestrzeni adresowej procesu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="a1ff2-126">Serves as a logical wrapper for the corresponding Win32 function, which retrieves information about a range of pages in the virtual address space of the calling process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a1ff2-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a1ff2-127">Remarks</span></span>  
 <span data-ttu-id="a1ff2-128">`IHostMemoryManager`Program udostępnia również metody dla środowiska CLR, w których można uzyskać wskaźnik, za pomocą którego należy wykonać żądania pamięci na stercie i uzyskać poziom ciśnienia pamięci w procesie, zgodnie z raportem hosta.</span><span class="sxs-lookup"><span data-stu-id="a1ff2-128">`IHostMemoryManager` also provides methods for the CLR to obtain a pointer through which to make memory requests on the heap and to get the level of memory pressure in the process, as reported by the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1ff2-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a1ff2-129">Requirements</span></span>  
 <span data-ttu-id="a1ff2-130">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1ff2-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1ff2-131">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a1ff2-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a1ff2-132">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a1ff2-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a1ff2-133">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1ff2-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1ff2-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a1ff2-134">See also</span></span>

- [<span data-ttu-id="a1ff2-135">IHostMalloc, interfejs</span><span class="sxs-lookup"><span data-stu-id="a1ff2-135">IHostMalloc Interface</span></span>](ihostmalloc-interface.md)
- [<span data-ttu-id="a1ff2-136">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="a1ff2-136">Hosting Interfaces</span></span>](hosting-interfaces.md)
