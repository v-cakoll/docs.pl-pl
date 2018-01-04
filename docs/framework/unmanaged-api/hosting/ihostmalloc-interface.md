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
ms.workload: dotnet
ms.openlocfilehash: e1690f5fe8f1417e6547ed94db8c71f079ebf5e6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ihostmalloc-interface"></a><span data-ttu-id="6cd9b-102">IHostMalloc — Interfejs</span><span class="sxs-lookup"><span data-stu-id="6cd9b-102">IHostMalloc Interface</span></span>
<span data-ttu-id="6cd9b-103">Udostępnia metody, które umożliwiają środowisko uruchomieniowe języka wspólnego (CLR), aby zażądać szczegółowych alokacji sterty za pośrednictwem hosta.</span><span class="sxs-lookup"><span data-stu-id="6cd9b-103">Provides methods that allow the common language runtime (CLR) to request fine-grained allocations from the heap through the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6cd9b-104">Metody</span><span class="sxs-lookup"><span data-stu-id="6cd9b-104">Methods</span></span>  
  
|<span data-ttu-id="6cd9b-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="6cd9b-105">Method</span></span>|<span data-ttu-id="6cd9b-106">Opis</span><span class="sxs-lookup"><span data-stu-id="6cd9b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6cd9b-107">Alloc, metoda</span><span class="sxs-lookup"><span data-stu-id="6cd9b-107">Alloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-alloc-method.md)|<span data-ttu-id="6cd9b-108">Żądania, że host przydzielić żądanej ilości pamięci sterty.</span><span class="sxs-lookup"><span data-stu-id="6cd9b-108">Requests that the host allocate the requested amount of memory from the heap.</span></span>|  
|[<span data-ttu-id="6cd9b-109">DebugAlloc, metoda</span><span class="sxs-lookup"><span data-stu-id="6cd9b-109">DebugAlloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-debugalloc-method.md)|<span data-ttu-id="6cd9b-110">Żąda przydzielić żądanej ilości pamięci sterty hosta, a ponadto śledzić, gdzie została przydzielona pamięć.</span><span class="sxs-lookup"><span data-stu-id="6cd9b-110">Requests that the host allocate the requested amount of memory from the heap, and additionally track where the memory was allocated.</span></span>|  
|[<span data-ttu-id="6cd9b-111">Free, metoda</span><span class="sxs-lookup"><span data-stu-id="6cd9b-111">Free Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-free-method.md)|<span data-ttu-id="6cd9b-112">Zwalnia pamięć, która została przydzielona przy użyciu `Alloc` metody.</span><span class="sxs-lookup"><span data-stu-id="6cd9b-112">Frees memory that was allocated by using the `Alloc` method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6cd9b-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6cd9b-113">Remarks</span></span>  
 <span data-ttu-id="6cd9b-114">Środowisko CLR pobiera wskaźnika interfejsu do `IHostMalloc` wystąpienia przez wywołanie metody [IHostMemoryManager::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="6cd9b-114">The CLR gets an interface pointer to an `IHostMalloc` instance by calling the [IHostMemoryManager::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6cd9b-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6cd9b-115">Requirements</span></span>  
 <span data-ttu-id="6cd9b-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6cd9b-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6cd9b-117">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6cd9b-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6cd9b-118">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6cd9b-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6cd9b-119">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6cd9b-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cd9b-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6cd9b-120">See Also</span></span>  
 [<span data-ttu-id="6cd9b-121">IHostMemoryManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="6cd9b-121">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 [<span data-ttu-id="6cd9b-122">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="6cd9b-122">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
