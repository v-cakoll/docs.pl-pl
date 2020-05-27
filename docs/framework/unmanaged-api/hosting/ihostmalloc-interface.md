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
ms.openlocfilehash: 8f4e1cd7586df7d8e2a577d26f06eaed6b2c8bb7
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804602"
---
# <a name="ihostmalloc-interface"></a><span data-ttu-id="e011c-102">IHostMalloc — Interfejs</span><span class="sxs-lookup"><span data-stu-id="e011c-102">IHostMalloc Interface</span></span>
<span data-ttu-id="e011c-103">Zapewnia metody, które umożliwiają środowisko uruchomieniowe języka wspólnego (CLR) żądania bardziej szczegółowych alokacji ze sterty za pośrednictwem hosta.</span><span class="sxs-lookup"><span data-stu-id="e011c-103">Provides methods that allow the common language runtime (CLR) to request fine-grained allocations from the heap through the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e011c-104">Metody</span><span class="sxs-lookup"><span data-stu-id="e011c-104">Methods</span></span>  
  
|<span data-ttu-id="e011c-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="e011c-105">Method</span></span>|<span data-ttu-id="e011c-106">Opis</span><span class="sxs-lookup"><span data-stu-id="e011c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e011c-107">Alloc, metoda</span><span class="sxs-lookup"><span data-stu-id="e011c-107">Alloc Method</span></span>](ihostmalloc-alloc-method.md)|<span data-ttu-id="e011c-108">Żąda od sterty przydzielenia przez hosta żądaną ilość pamięci.</span><span class="sxs-lookup"><span data-stu-id="e011c-108">Requests that the host allocate the requested amount of memory from the heap.</span></span>|  
|[<span data-ttu-id="e011c-109">DebugAlloc, metoda</span><span class="sxs-lookup"><span data-stu-id="e011c-109">DebugAlloc Method</span></span>](ihostmalloc-debugalloc-method.md)|<span data-ttu-id="e011c-110">Żąda, aby Host przydzielił żądaną ilość pamięci ze sterty, a także śledzić miejsce przydzielenia pamięci.</span><span class="sxs-lookup"><span data-stu-id="e011c-110">Requests that the host allocate the requested amount of memory from the heap, and additionally track where the memory was allocated.</span></span>|  
|[<span data-ttu-id="e011c-111">Free, metoda</span><span class="sxs-lookup"><span data-stu-id="e011c-111">Free Method</span></span>](ihostmalloc-free-method.md)|<span data-ttu-id="e011c-112">Zwalnia pamięć przydzieloną przy użyciu `Alloc` metody.</span><span class="sxs-lookup"><span data-stu-id="e011c-112">Frees memory that was allocated by using the `Alloc` method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e011c-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e011c-113">Remarks</span></span>  
 <span data-ttu-id="e011c-114">Środowisko CLR Pobiera wskaźnik interfejsu do `IHostMalloc` wystąpienia, wywołując metodę [IHostMemoryManager::](ihostmemorymanager-createmalloc-method.md) CreateInstance.</span><span class="sxs-lookup"><span data-stu-id="e011c-114">The CLR gets an interface pointer to an `IHostMalloc` instance by calling the [IHostMemoryManager::CreateMalloc](ihostmemorymanager-createmalloc-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e011c-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e011c-115">Requirements</span></span>  
 <span data-ttu-id="e011c-116">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e011c-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e011c-117">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e011c-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e011c-118">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e011c-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e011c-119">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e011c-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e011c-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e011c-120">See also</span></span>

- [<span data-ttu-id="e011c-121">IHostMemoryManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="e011c-121">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
- [<span data-ttu-id="e011c-122">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="e011c-122">Hosting Interfaces</span></span>](hosting-interfaces.md)
