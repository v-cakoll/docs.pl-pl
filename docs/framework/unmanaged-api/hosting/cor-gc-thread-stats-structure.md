---
title: COR_GC_THREAD_STATS — Struktura
ms.date: 03/30/2017
api_name:
- COR_GC_THREAD_STATS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_GC_THREAD_STATS
helpviewer_keywords:
- COR_GC_THREAD_STATS structure [.NET Framework hosting]
ms.assetid: 01f9a59b-7679-4d42-9ced-4a8981625c3d
topic_type:
- apiref
ms.openlocfilehash: 37da471aaa8e9f802a8430d7b3289b375ff1b40a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136987"
---
# <a name="cor_gc_thread_stats-structure"></a><span data-ttu-id="bf059-102">COR_GC_THREAD_STATS — Struktura</span><span class="sxs-lookup"><span data-stu-id="bf059-102">COR_GC_THREAD_STATS Structure</span></span>
<span data-ttu-id="bf059-103">Zawiera statystyki poszczególnych wątków dotyczące wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="bf059-103">Contains per-thread statistics pertaining to garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf059-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bf059-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_GC_THREAD_STATS {  
    ULONGLONG  PerThreadAllocation;   
    ULONG      Flags;   
} COR_GC_THREAD_STATS;  
```  
  
## <a name="members"></a><span data-ttu-id="bf059-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="bf059-105">Members</span></span>  
  
|<span data-ttu-id="bf059-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="bf059-106">Member</span></span>|<span data-ttu-id="bf059-107">Opis</span><span class="sxs-lookup"><span data-stu-id="bf059-107">Description</span></span>|  
|------------|-----------------|  
|`PerThreadAllocation`|<span data-ttu-id="bf059-108">Liczba bajtów pamięci przydzieloną w wątku, który jest skojarzony z bieżącym wystąpieniem `COR_GC_THREAD_STATS`.</span><span class="sxs-lookup"><span data-stu-id="bf059-108">The number of bytes of memory allocated on the thread that is associated with the current `COR_GC_THREAD_STATS` instance.</span></span> <span data-ttu-id="bf059-109">Ta liczba jest wyczyszczona do zera za każdym razem, gdy wystąpi wyrzucanie elementów bezużytecznych generacji.</span><span class="sxs-lookup"><span data-stu-id="bf059-109">This number is cleared to zero each time a generation-zero garbage collection occurs.</span></span>|  
|`Flags`|<span data-ttu-id="bf059-110">Liczba bajtów, które mają zostać podwyższone do wyższej generacji przy ostatnim wyrzucaniu elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="bf059-110">The number of bytes promoted to a higher generation at the most recent garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bf059-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bf059-111">Remarks</span></span>  
 <span data-ttu-id="bf059-112">[ICLRTask:: GetMemStats —](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md) przyjmuje parametr wyjściowy typu `COR_GC_THREAD_STATS`.</span><span class="sxs-lookup"><span data-stu-id="bf059-112">[ICLRTask::GetMemStats](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md) takes an output parameter of type `COR_GC_THREAD_STATS`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf059-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bf059-113">Requirements</span></span>  
 <span data-ttu-id="bf059-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf059-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf059-115">**Nagłówek:** GCHost. idl</span><span class="sxs-lookup"><span data-stu-id="bf059-115">**Header:** GCHost.idl</span></span>  
  
 <span data-ttu-id="bf059-116">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="bf059-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bf059-117">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf059-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf059-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bf059-118">See also</span></span>

- [<span data-ttu-id="bf059-119">Hosting, struktury</span><span class="sxs-lookup"><span data-stu-id="bf059-119">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [<span data-ttu-id="bf059-120">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="bf059-120">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
