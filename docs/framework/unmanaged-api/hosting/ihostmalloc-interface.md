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
ms.openlocfilehash: abc6cca185b318be016f92ac8c97d21f7af5940a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136780"
---
# <a name="ihostmalloc-interface"></a><span data-ttu-id="01cb2-102">IHostMalloc — Interfejs</span><span class="sxs-lookup"><span data-stu-id="01cb2-102">IHostMalloc Interface</span></span>
<span data-ttu-id="01cb2-103">Zapewnia metody, które umożliwiają środowisko uruchomieniowe języka wspólnego (CLR) żądania bardziej szczegółowych alokacji ze sterty za pośrednictwem hosta.</span><span class="sxs-lookup"><span data-stu-id="01cb2-103">Provides methods that allow the common language runtime (CLR) to request fine-grained allocations from the heap through the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="01cb2-104">Metody</span><span class="sxs-lookup"><span data-stu-id="01cb2-104">Methods</span></span>  
  
|<span data-ttu-id="01cb2-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="01cb2-105">Method</span></span>|<span data-ttu-id="01cb2-106">Opis</span><span class="sxs-lookup"><span data-stu-id="01cb2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="01cb2-107">Alloc, metoda</span><span class="sxs-lookup"><span data-stu-id="01cb2-107">Alloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-alloc-method.md)|<span data-ttu-id="01cb2-108">Żąda od sterty przydzielenia przez hosta żądaną ilość pamięci.</span><span class="sxs-lookup"><span data-stu-id="01cb2-108">Requests that the host allocate the requested amount of memory from the heap.</span></span>|  
|[<span data-ttu-id="01cb2-109">DebugAlloc, metoda</span><span class="sxs-lookup"><span data-stu-id="01cb2-109">DebugAlloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-debugalloc-method.md)|<span data-ttu-id="01cb2-110">Żąda, aby Host przydzielił żądaną ilość pamięci ze sterty, a także śledzić miejsce przydzielenia pamięci.</span><span class="sxs-lookup"><span data-stu-id="01cb2-110">Requests that the host allocate the requested amount of memory from the heap, and additionally track where the memory was allocated.</span></span>|  
|[<span data-ttu-id="01cb2-111">Free, metoda</span><span class="sxs-lookup"><span data-stu-id="01cb2-111">Free Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-free-method.md)|<span data-ttu-id="01cb2-112">Zwalnia pamięć przydzieloną przy użyciu metody `Alloc`.</span><span class="sxs-lookup"><span data-stu-id="01cb2-112">Frees memory that was allocated by using the `Alloc` method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="01cb2-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="01cb2-113">Remarks</span></span>  
 <span data-ttu-id="01cb2-114">Środowisko CLR Pobiera wskaźnik interfejsu do wystąpienia `IHostMalloc`, wywołując metodę [IHostMemoryManager::](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) CreateInstance.</span><span class="sxs-lookup"><span data-stu-id="01cb2-114">The CLR gets an interface pointer to an `IHostMalloc` instance by calling the [IHostMemoryManager::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01cb2-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="01cb2-115">Requirements</span></span>  
 <span data-ttu-id="01cb2-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01cb2-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01cb2-117">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="01cb2-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="01cb2-118">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="01cb2-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="01cb2-119">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01cb2-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01cb2-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="01cb2-120">See also</span></span>

- [<span data-ttu-id="01cb2-121">IHostMemoryManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="01cb2-121">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="01cb2-122">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="01cb2-122">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
