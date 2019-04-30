---
title: IHostMalloc — Interfejs
ms.date: 03/30/2017
api_name:
- IHostMAlloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMAlloc
helpviewer_keywords:
- IHostMAlloc interface [.NET Framework hosting]
ms.assetid: e3c6643b-6fc7-4a99-959d-4b7b4e63fdee
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f2a7a29ef1dc85c2ad554995286e5137fcb104be
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61757641"
---
# <a name="ihostmalloc-interface"></a><span data-ttu-id="d2ad4-102">IHostMalloc — Interfejs</span><span class="sxs-lookup"><span data-stu-id="d2ad4-102">IHostMalloc Interface</span></span>
<span data-ttu-id="d2ad4-103">Udostępnia metody, które umożliwiają środowisko uruchomieniowe języka wspólnego (CLR), aby zażądać szczegółowych alokacji ze stosu za pośrednictwem hosta.</span><span class="sxs-lookup"><span data-stu-id="d2ad4-103">Provides methods that allow the common language runtime (CLR) to request fine-grained allocations from the heap through the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d2ad4-104">Metody</span><span class="sxs-lookup"><span data-stu-id="d2ad4-104">Methods</span></span>  
  
|<span data-ttu-id="d2ad4-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="d2ad4-105">Method</span></span>|<span data-ttu-id="d2ad4-106">Opis</span><span class="sxs-lookup"><span data-stu-id="d2ad4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d2ad4-107">Alloc, metoda</span><span class="sxs-lookup"><span data-stu-id="d2ad4-107">Alloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-alloc-method.md)|<span data-ttu-id="d2ad4-108">Żądania, że host przydzielić żądanej ilości pamięci sterty.</span><span class="sxs-lookup"><span data-stu-id="d2ad4-108">Requests that the host allocate the requested amount of memory from the heap.</span></span>|  
|[<span data-ttu-id="d2ad4-109">DebugAlloc, metoda</span><span class="sxs-lookup"><span data-stu-id="d2ad4-109">DebugAlloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-debugalloc-method.md)|<span data-ttu-id="d2ad4-110">Żądania alokacji żądanej ilości pamięci sterty hosta i dodatkowo Śledź, gdzie pamięć została alokowana.</span><span class="sxs-lookup"><span data-stu-id="d2ad4-110">Requests that the host allocate the requested amount of memory from the heap, and additionally track where the memory was allocated.</span></span>|  
|[<span data-ttu-id="d2ad4-111">Free, metoda</span><span class="sxs-lookup"><span data-stu-id="d2ad4-111">Free Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-free-method.md)|<span data-ttu-id="d2ad4-112">Zwalnia pamięć, która została przydzielona za pomocą `Alloc` metody.</span><span class="sxs-lookup"><span data-stu-id="d2ad4-112">Frees memory that was allocated by using the `Alloc` method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d2ad4-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d2ad4-113">Remarks</span></span>  
 <span data-ttu-id="d2ad4-114">Środowisko CLR pobiera wskaźnik interfejsu do `IHostMalloc` wystąpienia, wywołując [ihostmemorymanager::createmalloc —](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="d2ad4-114">The CLR gets an interface pointer to an `IHostMalloc` instance by calling the [IHostMemoryManager::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2ad4-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d2ad4-115">Requirements</span></span>  
 <span data-ttu-id="d2ad4-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d2ad4-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2ad4-117">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d2ad4-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d2ad4-118">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d2ad4-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d2ad4-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2ad4-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2ad4-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d2ad4-120">See also</span></span>

- [<span data-ttu-id="d2ad4-121">IHostMemoryManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="d2ad4-121">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="d2ad4-122">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="d2ad4-122">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
