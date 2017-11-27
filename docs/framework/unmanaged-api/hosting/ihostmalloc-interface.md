---
title: "IHostMalloc — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostMAlloc
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostMAlloc
helpviewer_keywords: IHostMAlloc interface [.NET Framework hosting]
ms.assetid: e3c6643b-6fc7-4a99-959d-4b7b4e63fdee
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f788456065a5508441b9fec38ad4a7f531f9f303
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ihostmalloc-interface"></a><span data-ttu-id="e0e0d-102">IHostMalloc — Interfejs</span><span class="sxs-lookup"><span data-stu-id="e0e0d-102">IHostMalloc Interface</span></span>
<span data-ttu-id="e0e0d-103">Udostępnia metody, które umożliwiają środowisko uruchomieniowe języka wspólnego (CLR), aby zażądać szczegółowych alokacji sterty za pośrednictwem hosta.</span><span class="sxs-lookup"><span data-stu-id="e0e0d-103">Provides methods that allow the common language runtime (CLR) to request fine-grained allocations from the heap through the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e0e0d-104">Metody</span><span class="sxs-lookup"><span data-stu-id="e0e0d-104">Methods</span></span>  
  
|<span data-ttu-id="e0e0d-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="e0e0d-105">Method</span></span>|<span data-ttu-id="e0e0d-106">Opis</span><span class="sxs-lookup"><span data-stu-id="e0e0d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e0e0d-107">ALLOC — metoda</span><span class="sxs-lookup"><span data-stu-id="e0e0d-107">Alloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-alloc-method.md)|<span data-ttu-id="e0e0d-108">Żądania, że host przydzielić żądanej ilości pamięci sterty.</span><span class="sxs-lookup"><span data-stu-id="e0e0d-108">Requests that the host allocate the requested amount of memory from the heap.</span></span>|  
|[<span data-ttu-id="e0e0d-109">DebugAlloc — metoda</span><span class="sxs-lookup"><span data-stu-id="e0e0d-109">DebugAlloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-debugalloc-method.md)|<span data-ttu-id="e0e0d-110">Żąda przydzielić żądanej ilości pamięci sterty hosta, a ponadto śledzić, gdzie została przydzielona pamięć.</span><span class="sxs-lookup"><span data-stu-id="e0e0d-110">Requests that the host allocate the requested amount of memory from the heap, and additionally track where the memory was allocated.</span></span>|  
|[<span data-ttu-id="e0e0d-111">Free — metoda</span><span class="sxs-lookup"><span data-stu-id="e0e0d-111">Free Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-free-method.md)|<span data-ttu-id="e0e0d-112">Zwalnia pamięć, która została przydzielona przy użyciu `Alloc` metody.</span><span class="sxs-lookup"><span data-stu-id="e0e0d-112">Frees memory that was allocated by using the `Alloc` method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e0e0d-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e0e0d-113">Remarks</span></span>  
 <span data-ttu-id="e0e0d-114">Środowisko CLR pobiera wskaźnika interfejsu do `IHostMalloc` wystąpienia przez wywołanie metody [IHostMemoryManager::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="e0e0d-114">The CLR gets an interface pointer to an `IHostMalloc` instance by calling the [IHostMemoryManager::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0e0d-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e0e0d-115">Requirements</span></span>  
 <span data-ttu-id="e0e0d-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0e0d-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0e0d-117">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e0e0d-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e0e0d-118">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e0e0d-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e0e0d-119">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0e0d-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0e0d-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e0e0d-120">See Also</span></span>  
 [<span data-ttu-id="e0e0d-121">IHostMemoryManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="e0e0d-121">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 [<span data-ttu-id="e0e0d-122">Hosting — interfejsy</span><span class="sxs-lookup"><span data-stu-id="e0e0d-122">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
