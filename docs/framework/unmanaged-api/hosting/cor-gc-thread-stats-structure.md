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
ms.openlocfilehash: 88e81779fc9c20c506f3b0aa11ac2da3958dfe86
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616700"
---
# <a name="cor_gc_thread_stats-structure"></a><span data-ttu-id="4f903-102">COR_GC_THREAD_STATS — Struktura</span><span class="sxs-lookup"><span data-stu-id="4f903-102">COR_GC_THREAD_STATS Structure</span></span>
<span data-ttu-id="4f903-103">Zawiera statystyki poszczególnych wątków dotyczące wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="4f903-103">Contains per-thread statistics pertaining to garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f903-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4f903-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_GC_THREAD_STATS {  
    ULONGLONG  PerThreadAllocation;
    ULONG      Flags;
} COR_GC_THREAD_STATS;  
```  
  
## <a name="members"></a><span data-ttu-id="4f903-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="4f903-105">Members</span></span>  
  
|<span data-ttu-id="4f903-106">Członek</span><span class="sxs-lookup"><span data-stu-id="4f903-106">Member</span></span>|<span data-ttu-id="4f903-107">Opis</span><span class="sxs-lookup"><span data-stu-id="4f903-107">Description</span></span>|  
|------------|-----------------|  
|`PerThreadAllocation`|<span data-ttu-id="4f903-108">Liczba bajtów pamięci przydzieloną w wątku, który jest skojarzony z bieżącym `COR_GC_THREAD_STATS` wystąpieniem.</span><span class="sxs-lookup"><span data-stu-id="4f903-108">The number of bytes of memory allocated on the thread that is associated with the current `COR_GC_THREAD_STATS` instance.</span></span> <span data-ttu-id="4f903-109">Ta liczba jest wyczyszczona do zera za każdym razem, gdy wystąpi wyrzucanie elementów bezużytecznych generacji.</span><span class="sxs-lookup"><span data-stu-id="4f903-109">This number is cleared to zero each time a generation-zero garbage collection occurs.</span></span>|  
|`Flags`|<span data-ttu-id="4f903-110">Liczba bajtów, które mają zostać podwyższone do wyższej generacji przy ostatnim wyrzucaniu elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="4f903-110">The number of bytes promoted to a higher generation at the most recent garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4f903-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4f903-111">Remarks</span></span>  
 <span data-ttu-id="4f903-112">[ICLRTask:: GetMemStats —](iclrtask-getmemstats-method.md) pobiera parametr wyjściowy typu `COR_GC_THREAD_STATS` .</span><span class="sxs-lookup"><span data-stu-id="4f903-112">[ICLRTask::GetMemStats](iclrtask-getmemstats-method.md) takes an output parameter of type `COR_GC_THREAD_STATS`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f903-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4f903-113">Requirements</span></span>  
 <span data-ttu-id="4f903-114">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4f903-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f903-115">**Nagłówek:** GCHost. idl</span><span class="sxs-lookup"><span data-stu-id="4f903-115">**Header:** GCHost.idl</span></span>  
  
 <span data-ttu-id="4f903-116">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4f903-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4f903-117">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f903-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f903-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4f903-118">See also</span></span>

- [<span data-ttu-id="4f903-119">Hosting, struktury</span><span class="sxs-lookup"><span data-stu-id="4f903-119">Hosting Structures</span></span>](hosting-structures.md)
- [<span data-ttu-id="4f903-120">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="4f903-120">IHostTask Interface</span></span>](ihosttask-interface.md)
